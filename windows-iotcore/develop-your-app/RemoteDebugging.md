---
title: Debuggen einer app mithilfe von Remote Console App Debuggen
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: Erfahren Sie, wie Sie Ihre IoT-Core-Konsolenanwendung Remote in Visual Studio Remote Debuggen.
keywords: Windows Iot, visual Studio, app-Bereitstellung, Remotedebuggen
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512890"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>Debuggen einer app mithilfe von Remote Console App Debuggen

Hier ist Ihre IoT-Core-Konsolenanwendung in Visual Studio Remote Debuggen:

* Sie müssen zuerst den Remotedebugger auf Ihrem Gerät Windows IoT Core einrichten. Führen Sie zuerst die Schritte [hier](AppDeployment.md) jede andere universelle Windows-Anwendung auf Ihrem Gerät (versuchen Sie das HelloWorld-Projekt) bereitstellen. Dadurch werden alle erforderlichen Binärdateien auf Ihrem Gerät kopiert. 

* Um den Remotedebugger auf Ihrem Gerät zu starten, öffnen Sie einen Webbrowser auf Ihrem PC, und zeigen Sie damit `http://<device name/IP address>:8080` starten [Windows Device Portal](../manage-your-device/DevicePortal.md). Klicken Sie im Dialogfeld "Anmeldeinformationen" verwenden, den Standard-Benutzernamen und das Kennwort: `Administrator`, `p@ssw0rd`. Windows-Geräteverwaltung sollte starten, und der Web-Management-Startseite angezeigt.

* Nun wechseln Sie zu dem Abschnitt der Debug-Einstellungen von Windows Device Portal, und klicken Sie unter Starten Sie Visual Studio Remote Debugger auf die Schaltfläche "Start". 

    ![WindowsDevicePortalDebugSettings Start-Remotedebugger](../media/Console/device_portal_start_debugger.png)

* Dies Popup Anzeigen eines Meldungsfelds und bieten Ihnen die Verbindungsinformationen. 

*  In Visual Studio können Sie Ihr Ziel konfigurieren, indem Sie den Eigenschaften Ihres Projekts (Achten Sie darauf, alle von den hervorgehobenen Änderungen vor, je nach Namen\noder IP-Adresse des Boards) bearbeiten:

    ![Projekteinstellungen für ConsoleApplication Remote-Computer](../media/Console/console_project_settings.png)
    
> [!NOTE]
> Wenn Sie nicht in der Abbildung oben angezeigt werden, finden Sie unter "Projektmappen-Explorer" im Kontextmenü, und wechseln Sie zu "Project Properties". Sie finden weitere Informationen zu Projekteigenschaften [hier](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).

> [!TIP]
> Sie können die IP-Adresse anstelle des Gerätenamens Windows IoT Core verwenden.

* Die Konfiguration des Projekts muss zum Aktivieren der Bereitstellung geändert werden.  Zu diesem Zweck öffnen Sie den Konfigurations-Manager durch Auswählen der Konfigurations-Manager aus der Konfiguration der Projektmappe Dropdown-Menü auf der Symbolleiste aus.

    ![ConsoleApplication SolutionConfiguration](../media/Console/configuration_management.png)

    Vom Configuration Manager, stellen Sie sicher, dass das Kontrollkästchen für die Bereitstellung für die Projektkonfiguration ausgewählt ist (Wenn diese Option deaktiviert ist, ist es wahrscheinlich, dass die Optionen für die nicht vollständig in den Projekteigenschaften die Registerkarte "Debuggen" vorgenommen wurden)

    ![Projekteinstellungen für ConsoleApplication Remote-Computer](../media/Console/deploy_checkbox.png)

* Wir nun können mit dem Remotegerät für Windows IoT Core bereitstellen. Drücken Sie einfach F5 (oder die Option Debuggen \| Debuggen starten) zum Starten des Debuggings unsere app. Sie können auch Build \| Projektmappe bereitstellen, um die Anwendung einfach bereitzustellen, ohne eine Debugsitzung starten.

> [!NOTE]
> Wenn in Visual Studio ausführen, die Ausgabe nicht an einer beliebigen Stelle zeigt, aber Sie können Haltepunkte festgelegt werden, finden Sie unter usw. Variablenwerte.

* Drücken Sie auf die Schaltfläche "Debugging beenden", um die app zu beenden (oder die Option Debuggen \| Debuggen beenden).

* Sie können jetzt die Anwendung ausführen.  Öffnen Sie einfach eine PowerShell/SSH-Verbindung (Anweisungen finden Sie [hier, um PowerShell](../connect-your-device/PowerShell.md) und [hier, um SSH](../connect-your-device/SSH.md)), und geben Sie den oben angegebenen Remotebefehl.

    ![ConsoleApplication-Ausgabe](../media/Console/console_output.png)

* Sobald Sie fertig sind Debuggen Ihrer Anwendung, denken Sie daran, den Remotedebugger auf dem Gerät Windows IoT Core zu beenden. Dazu können Sie zum Debuggen von im Einstellungsabschnitt Windows Device Portal navigieren und durch Klicken auf die Schaltfläche mit den Remotedebugger beenden.

    ![WindowsDevicePortalDebugSettings Stop-Remotedebugger](../media/Console/device_portal_stop_debugger.PNG)

