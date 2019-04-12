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
# <a name="investigating-memory-leaks"></a><span data-ttu-id="2bc7e-104">Untersuchen von Speicherlecks</span><span class="sxs-lookup"><span data-stu-id="2bc7e-104">Investigating Memory Leaks</span></span>

<span data-ttu-id="2bc7e-105">Das beste Tool zum Untersuchen von Speicherlecks unter Windows IoT Core mit Visual Studio ist die integrierte [Diagnosetools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span><span class="sxs-lookup"><span data-stu-id="2bc7e-105">The best tool for investigating memory leaks on Windows IoT Core with Visual Studio is the integrated [Diagnostic Tools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span></span>

![Diagnosetools](../media/MemoryLeaks/DiagnosticTools.PNG)

<span data-ttu-id="2bc7e-107">Vordergrundanwendungen können [befolgen Sie die Dokumentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span><span class="sxs-lookup"><span data-stu-id="2bc7e-107">For foreground applications you can [follow the documentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span></span>

<span data-ttu-id="2bc7e-108">Diese Tools funktionieren jedoch nicht direkt mit einem Windows IoT Core **Hintergrundanwendung**.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-108">However, these tools don't work directly with a Windows IoT Core **Background Application**.</span></span> <span data-ttu-id="2bc7e-109">Eine Möglichkeit, Profile für Code in einer hintergrundanwendung verwendet wird, es in einer Vordergrund-app für die Analyse zu umschließen:</span><span class="sxs-lookup"><span data-stu-id="2bc7e-109">One way to profile code used in a background application is to wrap it in a foreground app for analysis:</span></span>

1. <span data-ttu-id="2bc7e-110">Hinzufügen einer **leere App** auf die **Hintergrund App** Lösung</span><span class="sxs-lookup"><span data-stu-id="2bc7e-110">Add a **Blank App** to the **Background App** solution</span></span>
2. <span data-ttu-id="2bc7e-111">Mit der rechten Maustaste die **leere App** verweist, und fügen einen Verweis auf die **Hintergrund-App**</span><span class="sxs-lookup"><span data-stu-id="2bc7e-111">Right-click the **Blank App** references and add a reference to the **Background App**</span></span>
3. <span data-ttu-id="2bc7e-112">Ändern der **Hintergrund App** Run()-Methode überprüfen, ob der TaskInstance-Parameter null ist, und behandeln diese Fälle unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-112">Change the **Background App** Run() method to check if the taskInstance parameter is null and handle those cases differently.</span></span>
4. <span data-ttu-id="2bc7e-113">Von der **leere App** BackgroundApp::Run(null) aufrufen</span><span class="sxs-lookup"><span data-stu-id="2bc7e-113">From the **BlankApp** call BackgroundApp::Run(null)</span></span>
5. <span data-ttu-id="2bc7e-114">Legen Sie einen Haltepunkt beim Aufruf von BackgroundApp::Run</span><span class="sxs-lookup"><span data-stu-id="2bc7e-114">Set a breakpoint on the call to BackgroundApp::Run</span></span>
6. <span data-ttu-id="2bc7e-115">Wenn der Haltepunkt erreicht wird, finden die **Diagnosetools** Windows, und klicken Sie auf die ![Momentaufnahme](../media/MemoryLeaks/Snapshot.PNG) Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-115">When the breakpoint is hit find the **Diagnostic Tools** windows and click the ![Snapshot](../media/MemoryLeaks/Snapshot.PNG) button.</span></span>

8. <span data-ttu-id="2bc7e-116">Das Problem reproduzieren</span><span class="sxs-lookup"><span data-stu-id="2bc7e-116">Reproduce the problem</span></span>
9. <span data-ttu-id="2bc7e-117">Erstellen Sie eine andere Momentaufnahme</span><span class="sxs-lookup"><span data-stu-id="2bc7e-117">Take another snapshot</span></span>
10. <span data-ttu-id="2bc7e-118">Verwenden der **Diagnosetools** Fenster aus, um den Verlust zu diagnostizieren.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-118">Use the **Diagnostic Tools** window to diagnose the leak.</span></span>

## <a name="create-a-test-app"></a><span data-ttu-id="2bc7e-119">Erstellen Sie eine Test-app</span><span class="sxs-lookup"><span data-stu-id="2bc7e-119">Create a test app</span></span>

<span data-ttu-id="2bc7e-120">Wir beginnen mit einer Anwendung, die belegt Speicher und nicht um einen Speicherverlust zu simulieren, freizugeben.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-120">Let's start with an application that allocates memory and doesn't free it to simulate a leak.</span></span>
<span data-ttu-id="2bc7e-121">Beginnen Sie durch Erstellen eines neuen C# Anwendung im Hintergrund: [Entwickeln von Hintergrundanwendungen](./BackgroundApplications.md)</span><span class="sxs-lookup"><span data-stu-id="2bc7e-121">Begin by creating a new C# Background application: [Developing Background Applications](./BackgroundApplications.md)</span></span>

<span data-ttu-id="2bc7e-122">Ersetzen Sie den Code in StartupTask.cs dabei</span><span class="sxs-lookup"><span data-stu-id="2bc7e-122">Replace the code in StartupTask.cs with this</span></span>
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

<span data-ttu-id="2bc7e-123">Wenn Sie die hintergrundanwendung auf Ihrem IoT-Gerät ausführen sollte es an diesem Punkt eine große Zahl von Arbeitsspeicher verwenden und nie freizugeben.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-123">At this point if you run the background application on your IoT device it should use up a lot of memory and never free it.</span></span> <span data-ttu-id="2bc7e-124">Wenn Sie versuchen, verwenden Sie die Diagnosetools sehen an diesem Punkt Sie etwas wie dies ähnliches, da es sich bei Verwendung der Tools mit Hintergrund-apps derzeit nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-124">If you try to use the diagnostic tools at this point you will see something that looks like this, because using the tools with background apps is currently unsupported.</span></span>

![Diagnosetools-Hintergrund-App](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

<span data-ttu-id="2bc7e-126">Um dieses Problem umgehen, werden wir eine Vordergrund-app zur Projektmappe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-126">To work around this we are going to add a foreground app to the solution.</span></span> <span data-ttu-id="2bc7e-127">In der **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektmappenordner, und wählen Sie dann **Add.New Projekt**.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-127">In the **Solution Explorer** right-click on the solution folder and then select **Add.New Project**.</span></span>

![Neues Projekt hinzufügen](../media/MemoryLeaks/AddNewProject.png)

<span data-ttu-id="2bc7e-129">Wählen Sie **Visual C#> Windows Universal > leere App** als Projekttyp, benennen Sie Ihr Projekt, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-129">Choose **Visual C#>Windows Universal>Blank App** as the project type, name your project and click **OK**.</span></span>

![Neues Projekt hinzufügen](../media/MemoryLeaks/NewForegroundApp.PNG)

<span data-ttu-id="2bc7e-131">Mit der rechten Maustaste auf den neuen Vordergrund-app-Projekts **Verweise** Knoten, und wählen **Verweis hinzufügen...**</span><span class="sxs-lookup"><span data-stu-id="2bc7e-131">Right-click on the new foreground app project's **References** node and select **Add Reference...**</span></span>

![Neues Projekt hinzufügen](../media/MemoryLeaks/AddReference.PNG)

<span data-ttu-id="2bc7e-133">In der **Verweis-Manager** wählen Sie Dialogfeld **Projekte** im linken Bereich.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-133">In the **Reference Manager** dialog choose **Projects** in the left-hand pane.</span></span>  <span data-ttu-id="2bc7e-134">Klicken Sie im mittleren Bereich eine Prüfung in das Kontrollkästchen neben Ihrem Hintergrund-Anwendungsprojekt hinzufügen, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-134">In the center pane add a check in the checkbox next to your background application project and click **OK**.</span></span>

![Neues Projekt hinzufügen](../media/MemoryLeaks/AddReferenceDialog.PNG)

<span data-ttu-id="2bc7e-136">Als Nächstes mit der rechten Maustaste in des Vordergrund-app-Projekts, und klicken Sie auf **als Startprojekt festlegen**.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-136">Next right-click the foreground app project and click **Set as StartUp Project**.</span></span>

![Neues Projekt hinzufügen](../media/MemoryLeaks/SetAsStartup.PNG)

<span data-ttu-id="2bc7e-138">Fügen Sie Code, um eine Instanz des Anwendungsobjekts Hintergrund erstellen und ausführen und Null als einzigem Parameter aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-138">Add code to create an instance of your background application object and call Run passing in null as the only parameter.</span></span>
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

<span data-ttu-id="2bc7e-139">Klicken Sie dann ist bei der Ausführung von Ihrer app Hintergrund Methode stellen Sie sicher, dass TaskInstance, nicht null vor der Verwendung.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-139">Then in your background app's Run method check to make sure taskInstance is not null before using it.</span></span>

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

1. <span data-ttu-id="2bc7e-140">Legen Sie einen Haltepunkt beim Aufruf von Task. Run(null).</span><span class="sxs-lookup"><span data-stu-id="2bc7e-140">Set a breakpoint on the call to task.Run(null).</span></span>
2. <span data-ttu-id="2bc7e-141">Legen Sie einen weiteren Haltepunkt auf Zeitgeber. Änderung (Timeout.Infinite, Timeout.Infinite) in der "timer_tick" in StartupTask.cs.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-141">Set another breakpoint on timer.Change(Timeout.Infinite, Timeout.Infinite) in Timer_Tick in StartupTask.cs.</span></span>
3. <span data-ttu-id="2bc7e-142">Drücken Sie F5, um Debuggen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-142">Press F5 to begin debugging</span></span>
4. <span data-ttu-id="2bc7e-143">Wenn Sie das erste Haltepunkt Drücken der Schaltfläche "Momentaufnahme" festlegen die Baseline zu vergleichende erreicht</span><span class="sxs-lookup"><span data-stu-id="2bc7e-143">When you hit the first breakpoint press the snapshot button to set the baseline to compare against</span></span>

![Momentaufnahme](../media/MemoryLeaks/Snapshot.PNG)

5. <span data-ttu-id="2bc7e-145">Drücken Sie F5</span><span class="sxs-lookup"><span data-stu-id="2bc7e-145">Press F5</span></span>
6. <span data-ttu-id="2bc7e-146">Wenn Sie den zweiten Haltepunkt drücken Sie die Schaltfläche "Momentaufnahme" erneut aus, um den aktuellen Zustand erfassen erreichen.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-146">When you hit the second breakpoint press the snapshot button again to capture the current state.</span></span>

<span data-ttu-id="2bc7e-147">Die Diagnosetools sollte nun ein Diagramm mit zunehmenden Speicherbedarf und 2 Momentaufnahme wie folgt anzeigen:</span><span class="sxs-lookup"><span data-stu-id="2bc7e-147">Now the diagnostic tools should show a graph with increasing memory use and 2 snapshot like this:</span></span>

![Diagnosetools beim Speicherverluste](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

<span data-ttu-id="2bc7e-149">Suchen Sie in Zeile 2 in der Spalte für die Größe des Heaps.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-149">Look at row 2 in the Heap Size column.</span></span> <span data-ttu-id="2bc7e-150">Klicken Sie auf die zweite Zahl mit dem Pluszeichen und Pfeil nach oben.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-150">Click the second number with the plus sign and up arrow.</span></span> <span data-ttu-id="2bc7e-151">Es sollte etwa Folgendes angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="2bc7e-151">You should see something like this:</span></span>

![Momentaufnahmetabelle](../media/MemoryLeaks/Snapshot2_1.PNG)

<span data-ttu-id="2bc7e-153">Sortieren nach Größenunterschied, damit die größte Zahl im oberen Bereich ist. Klicken Sie dann auf die oberste Zeile.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-153">Sort by size diff so that the largest number is at the top, then click the top row.</span></span> <span data-ttu-id="2bc7e-154">Klicken Sie oberhalb der zweiten Detailtabelle auf **referenzierte Typen**.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-154">Above the second detail table click **Referenced Types**.</span></span>  <span data-ttu-id="2bc7e-155">Die zweite Tabelle sollte nun angezeigt werden **Liste\<Byte []\>**  als Quelle für die speicherauslastung.</span><span class="sxs-lookup"><span data-stu-id="2bc7e-155">The second table should now show **List\<Byte[]\>** as the source of all the memory usage.</span></span>

![Momentaufnahmetabelle](../media/MemoryLeaks/Snapshot2_2.PNG)
