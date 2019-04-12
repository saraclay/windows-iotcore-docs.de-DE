---
title: Untersuchung von Speicherverlusten
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: Erfahren Sie, wie Sie Speicherverluste genauer zu untersuchen.
keywords: Windows Iot, Visual Studio Speicherverluste, Problembehandlung
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512745"
---
# <a name="investigating-memory-leaks"></a>Untersuchen von Speicherlecks

Das beste Tool zum Untersuchen von Speicherlecks unter Windows IoT Core mit Visual Studio ist die integrierte [Diagnosetools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)

![Diagnosetools](../media/MemoryLeaks/DiagnosticTools.PNG)

Vordergrundanwendungen können [befolgen Sie die Dokumentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).

Diese Tools funktionieren jedoch nicht direkt mit einem Windows IoT Core **Hintergrundanwendung**. Eine Möglichkeit, Profile für Code in einer hintergrundanwendung verwendet wird, es in einer Vordergrund-app für die Analyse zu umschließen:

1. Hinzufügen einer **leere App** auf die **Hintergrund App** Lösung
2. Mit der rechten Maustaste die **leere App** verweist, und fügen einen Verweis auf die **Hintergrund-App**
3. Ändern der **Hintergrund App** Run()-Methode überprüfen, ob der TaskInstance-Parameter null ist, und behandeln diese Fälle unterschiedlich.
4. Von der **leere App** BackgroundApp::Run(null) aufrufen
5. Legen Sie einen Haltepunkt beim Aufruf von BackgroundApp::Run
6. Wenn der Haltepunkt erreicht wird, finden die **Diagnosetools** Windows, und klicken Sie auf die ![Momentaufnahme](../media/MemoryLeaks/Snapshot.PNG) Schaltfläche.

8. Das Problem reproduzieren
9. Erstellen Sie eine andere Momentaufnahme
10. Verwenden der **Diagnosetools** Fenster aus, um den Verlust zu diagnostizieren.

## <a name="create-a-test-app"></a>Erstellen Sie eine Test-app

Wir beginnen mit einer Anwendung, die belegt Speicher und nicht um einen Speicherverlust zu simulieren, freizugeben.
Beginnen Sie durch Erstellen eines neuen C# Anwendung im Hintergrund: [Entwickeln von Hintergrundanwendungen](./BackgroundApplications.md)

Ersetzen Sie den Code in StartupTask.cs dabei
```C#
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Threading;
using Windows.ApplicationModel.Background;
using Windows.System;

namespace LeakyBackgroundApp
{
    public sealed class StartupTask : IBackgroundTask
    {
        private Timer timer;
        private BackgroundTaskDeferral deferral;
        List<byte[]> buffer = new List<byte[]>();
        private const ulong minRemaining = 300 * 1024 * 1024;

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            deferral = taskInstance.GetDeferral();
            timer = new Timer(Timer_Tick, null, 500, 500);
        }

        private void Timer_Tick(object state)
        {
            ulong remaining = (MemoryManager.AppMemoryUsageLimit - MemoryManager.AppMemoryUsage);
            ulong chunkSize = remaining / 100;

            try
            {
                if (remaining > minRemaining)
                {
                    var chunk = new byte[chunkSize];

                    // force virtual memory to be commited by writing to it
                    for (int i = 0; i < chunk.Length; i += 4096)
                    {
                        chunk[i] = 0xDA;
                    }

                    // "leak" memory by adding it to the list
                    buffer.Add(chunk);
                    Debug.WriteLine(String.Format("Allocated {0} chunk(s)", buffer.Count));
                }
                else
                {
                    timer.Change(Timeout.Infinite, Timeout.Infinite);
                }
            }
            catch (OutOfMemoryException ex)
            {
                Debug.Write(ex.Message);
                timer.Change(Timeout.Infinite, Timeout.Infinite);
            }
        }
    }
}
```

Wenn Sie die hintergrundanwendung auf Ihrem IoT-Gerät ausführen sollte es an diesem Punkt eine große Zahl von Arbeitsspeicher verwenden und nie freizugeben. Wenn Sie versuchen, verwenden Sie die Diagnosetools sehen an diesem Punkt Sie etwas wie dies ähnliches, da es sich bei Verwendung der Tools mit Hintergrund-apps derzeit nicht unterstützt wird.

![Diagnosetools-Hintergrund-App](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

Um dieses Problem umgehen, werden wir eine Vordergrund-app zur Projektmappe hinzuzufügen. In der **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektmappenordner, und wählen Sie dann **Add.New Projekt**.

![Neues Projekt hinzufügen](../media/MemoryLeaks/AddNewProject.png)

Wählen Sie **Visual C#> Windows Universal > leere App** als Projekttyp, benennen Sie Ihr Projekt, und klicken Sie auf **OK**.

![Neues Projekt hinzufügen](../media/MemoryLeaks/NewForegroundApp.PNG)

Mit der rechten Maustaste auf den neuen Vordergrund-app-Projekts **Verweise** Knoten, und wählen **Verweis hinzufügen...**

![Neues Projekt hinzufügen](../media/MemoryLeaks/AddReference.PNG)

In der **Verweis-Manager** wählen Sie Dialogfeld **Projekte** im linken Bereich.  Klicken Sie im mittleren Bereich eine Prüfung in das Kontrollkästchen neben Ihrem Hintergrund-Anwendungsprojekt hinzufügen, und klicken Sie auf **OK**.

![Neues Projekt hinzufügen](../media/MemoryLeaks/AddReferenceDialog.PNG)

Als Nächstes mit der rechten Maustaste in des Vordergrund-app-Projekts, und klicken Sie auf **als Startprojekt festlegen**.

![Neues Projekt hinzufügen](../media/MemoryLeaks/SetAsStartup.PNG)

Fügen Sie Code, um eine Instanz des Anwendungsobjekts Hintergrund erstellen und ausführen und Null als einzigem Parameter aufrufen.
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

Klicken Sie dann ist bei der Ausführung von Ihrer app Hintergrund Methode stellen Sie sicher, dass TaskInstance, nicht null vor der Verwendung.

```C#
public void Run(IBackgroundTaskInstance taskInstance)
{
    if (taskInstance != null)
    {
        deferral = taskInstance.GetDeferral();
    }

    timer = new Timer(Timer_Tick, null, 500, 500);
}
```

1. Legen Sie einen Haltepunkt beim Aufruf von Task. Run(null).
2. Legen Sie einen weiteren Haltepunkt auf Zeitgeber. Änderung (Timeout.Infinite, Timeout.Infinite) in der "timer_tick" in StartupTask.cs.
3. Drücken Sie F5, um Debuggen zu beginnen.
4. Wenn Sie das erste Haltepunkt Drücken der Schaltfläche "Momentaufnahme" festlegen die Baseline zu vergleichende erreicht

![Momentaufnahme](../media/MemoryLeaks/Snapshot.PNG)

5. Drücken Sie F5
6. Wenn Sie den zweiten Haltepunkt drücken Sie die Schaltfläche "Momentaufnahme" erneut aus, um den aktuellen Zustand erfassen erreichen.

Die Diagnosetools sollte nun ein Diagramm mit zunehmenden Speicherbedarf und 2 Momentaufnahme wie folgt anzeigen:

![Diagnosetools beim Speicherverluste](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

Suchen Sie in Zeile 2 in der Spalte für die Größe des Heaps. Klicken Sie auf die zweite Zahl mit dem Pluszeichen und Pfeil nach oben. Es sollte etwa Folgendes angezeigt werden:

![Momentaufnahmetabelle](../media/MemoryLeaks/Snapshot2_1.PNG)

Sortieren nach Größenunterschied, damit die größte Zahl im oberen Bereich ist. Klicken Sie dann auf die oberste Zeile. Klicken Sie oberhalb der zweiten Detailtabelle auf **referenzierte Typen**.  Die zweite Tabelle sollte nun angezeigt werden **Liste\<Byte []\>**  als Quelle für die speicherauslastung.

![Momentaufnahmetabelle](../media/MemoryLeaks/Snapshot2_2.PNG)
