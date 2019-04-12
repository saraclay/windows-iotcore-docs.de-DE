---
title: Programme im Hintergrund
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum hintergrundanwendungen für Ihre IoT-Geräte zu entwickeln.
keywords: Windows Iot, Programme im Hintergrund
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512914"
---
# <a name="developing-background-applications"></a>Entwickeln von Hintergrundanwendungen

> [!NOTE]
> Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.

Hintergrundanwendungen sind Anwendungen, die keine direkte Benutzeroberfläche haben. Nach der Bereitstellung und Konfiguration werden diese Anwendungen beim Start des Computers zu starten und ausführen, ohne alle Prozesslebensdauer-Ressource verwenden Sie Einschränkungen kontinuierlich. Falls sie abstürzt oder beendet wird das System automatisch diese neu gestartet.
Diese Programme im Hintergrund haben eine sehr einfache Ausführung-Modell. Die Vorlagen erstellen eine Klasse, die "IBackgroundTask"-Schnittstelle implementiert und generiert die Methode leer "ausführen". Diese Methode "Run" ist der Einstiegspunkt der Anwendung.

![Hintergrundaufgabe](../media/BackgroundApplications/backgroundTaskScreenshot.png)

Es gibt einen wichtigen Punkt beachten: standardmäßig die Anwendung wird heruntergefahren, wenn die run-Methode abgeschlossen ist. Dies bedeutet, dass apps, die die allgemeine IoT-Muster der Ausführung von eines Servers, die darauf warten, für die Eingabe oder auf einem Zeitgeber und führen Sie die app beenden vorzeitig finden. Um dies zu verhindern, müssen Sie die "GetDeferral"-Methode, um zu verhindern, dass die Anwendung beendet wird aufrufen. Sie finden weitere Informationen zum Muster für die Verzögerung [hier](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).

## <a name="where-can-background-applications-be-installed-from"></a>Wo kann Hintergrundanwendungen aus werden installiert? 

Sie können auch herunterladen und installieren Sie IoT-Vorlagen, um das Hintergrund-Anwendungen aus der Visual Studio Gallery können [hier](https://go.microsoft.com/fwlink/?linkid=847472).  Alternativ können die Vorlagen gefunden werden, durch Suchen nach `Windows IoT Core Project Templates` in die [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) oder direkt aus Visual Studio im Dialogfeld "Erweiterungen und Updates" (Extras > Erweiterungen und Updates > Online).

## <a name="what-languages-are-available"></a>Welche Sprachen verfügbar sind?

**Anwendung (IoT) im Hintergrund** Vorlagen für befinden:

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>Wie werden Programme im Hintergrund verwendet? 

Erstellen einer hintergrundanwendung ist sehr ähnlich ist, erstellen Sie eine Hintergrundaufgabe.  Wenn die Hintergrundanwendung gestartet wird, wird die Run-Methode aufgerufen:

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

Wenn die Run-Methode beendet, es sei denn, ein Deferral-Objekt erstellt wird, wird der hintergrundanwendung beendet. Die allgemeinen Brauch werden, für die asynchrone Programmierung ist zu einer Verzögerung wie folgt:

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

Nachdem eine Verzögerung ausgeführt wird, wird die hintergrundanwendung fortgesetzt, bis vollständige Methode für das Deferral-Objekt aufgerufen wird.

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>Wie beginne hintergrundanwendungen?

Diese Frage kann in der Bereitstellung und Aufrufs unterteilt werden.  

Um einen hintergrundanwendung bereitzustellen, ist Folgendes möglich:

* Verwenden Sie Visual Studio F5 (das Erstellen, bereitstellen und aufrufen wird).  Weitere Informationen finden Sie unserem [Hello World-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) , in dem wir beschreiben, wie zum Bereitstellen und starten Sie Visual Studio.

> [!NOTE]
> Dadurch wird nicht konfiguriert, dass die hintergrundanwendung beim start des Geräts gestartet wird.

* Erstellen Sie eine AppX-Datei durch Auswählen des Projekts in Visual Studio > Store > App-Pakete erstellen.  Nachdem Sie eine AppX-Datei erstellt haben, können Sie [Windows Device Portal](../manage-your-device/DevicePortal.md) für Ihr Windows 10 IoT Core-Gerät bereitstellen.

Um hintergrundanwendung aufzurufen, ist Folgendes möglich:

* Wie oben erwähnt, wird Visual Studio die F5-Funktion bereitstellen und die Hintergrund-Anwendung sofort starten.

> [!NOTE]
> Dadurch wird nicht konfiguriert, dass die hintergrundanwendung beim start des Geräts gestartet wird.

* Für einen hintergrundanwendung, die auf einem IoT-Gerät bereitgestellt wurde, können Sie das Hilfsprogramm iotstartup.exe so konfigurieren Sie Ihre hintergrundanwendung gestartet, wenn das Gerät gestartet wird.  Gehen Sie zum Angeben der hintergrundanwendung als ein Start-App (**ersetzen Sie den Namen Ihrer app** für `BackgroundApplication1` unten):

1. Starten Sie eine PowerShell (PS)-Sitzung mit Ihrem Gerät Windows IoT Core, wie beschrieben [hier](../connect-your-device/PowerShell.md).

2. Geben Sie die PS-Sitzung ein:
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. Der vollständige Name der hintergrundanwendung sollte etwa wie z. B. angezeigt werden:

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. Das Hilfsprogramm bestätigt, dass die hintergrundanwendung eine "monitorlose"-Anwendung ist und ordnungsgemäß installiert ist.  Sie sehen wahrscheinlich auch einen Headed-Eintrag für Ihre Anwendungen Hintergrund, aber dies ignoriert werden kann.

5. Jetzt ist es einfach, diese app als "Start-App" festzulegen. Geben Sie einfach den Befehl ein:

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. Das Hilfsprogramm wird bestätigen Sie, dass die Liste der monitorlose "Start-Apps" die hintergrundanwendung hinzugefügt wurde:

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. Fahren Sie fort, und starten Sie Ihr Windows IoT Core-Gerät neu. In der PS-Sitzung können Sie den Befehl "Herunterfahren" ausgeben:

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. Nach dem Neustart des Geräts die hintergrundanwendung wird automatisch gestartet, und Windows 10 IoT Core sicherzustellen, dass sie jedes Mal, wenn es beendet, neu gestartet wird.  

> [!NOTE]
> Sobald eine Hintergrund-app registriert wird, führen Sie automatisch, wenn die app beendet wird oder stürzt ab, wird es automatisch neu gestartet werden.  Die app ist nicht über den Grund informiert, gestartet wird oder in der so neu gestartet werden, wenn ein Neustart besondere Aktionen Sie den Status der app in Ihrer app überwachen müssen möchten.

9. Sie können Ihre hintergrundanwendung aus der Liste der monitorlose Startup-Apps entfernen, durch Eingabe des Befehls:

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. Das Hilfsprogramm wird bestätigt, dass die hintergrundanwendung aus der Liste der monitorlose "Start-Apps" entfernt wurde:

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a>Siehe auch
So fügen Sie einen Hintergrund-app hinzu, beim Erstellen eines benutzerdefinierten Images finden Sie unter [erstellen Sie ein Appx-Paket](../build-your-image/createinstallpackage.md)
