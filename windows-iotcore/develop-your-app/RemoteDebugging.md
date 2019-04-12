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
# <a name="debug-your-app-using-remote-console-app-debugging"></a><span data-ttu-id="5c320-104">Debuggen einer app mithilfe von Remote Console App Debuggen</span><span class="sxs-lookup"><span data-stu-id="5c320-104">Debug your app using Remote Console App Debugging</span></span>

<span data-ttu-id="5c320-105">Hier ist Ihre IoT-Core-Konsolenanwendung in Visual Studio Remote Debuggen:</span><span class="sxs-lookup"><span data-stu-id="5c320-105">Here's how to debug your IoT Core console application remotely in Visual Studio:</span></span>

* <span data-ttu-id="5c320-106">Sie müssen zuerst den Remotedebugger auf Ihrem Gerät Windows IoT Core einrichten.</span><span class="sxs-lookup"><span data-stu-id="5c320-106">You will first need to setup the Remote Debugger on your Windows IoT Core device.</span></span> <span data-ttu-id="5c320-107">Führen Sie zuerst die Schritte [hier](AppDeployment.md) jede andere universelle Windows-Anwendung auf Ihrem Gerät (versuchen Sie das HelloWorld-Projekt) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5c320-107">First follow the steps [here](AppDeployment.md) to deploy any other Universal Windows Application on your device (try the HelloWorld project).</span></span> <span data-ttu-id="5c320-108">Dadurch werden alle erforderlichen Binärdateien auf Ihrem Gerät kopiert.</span><span class="sxs-lookup"><span data-stu-id="5c320-108">This will copy all the required binaries to your device.</span></span> 

* <span data-ttu-id="5c320-109">Um den Remotedebugger auf Ihrem Gerät zu starten, öffnen Sie einen Webbrowser auf Ihrem PC, und zeigen Sie damit `http://<device name/IP address>:8080` starten [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="5c320-109">To start the remote debugger on your device, open a Web Browser on your PC and point it to `http://<device name/IP address>:8080` to launch [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="5c320-110">Klicken Sie im Dialogfeld "Anmeldeinformationen" verwenden, den Standard-Benutzernamen und das Kennwort: `Administrator`, `p@ssw0rd`.</span><span class="sxs-lookup"><span data-stu-id="5c320-110">In the credentials dialog, use the default username and password: `Administrator`, `p@ssw0rd`.</span></span> <span data-ttu-id="5c320-111">Windows-Geräteverwaltung sollte starten, und der Web-Management-Startseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5c320-111">Windows Device Management should launch and display the web management home screen.</span></span>

* <span data-ttu-id="5c320-112">Nun wechseln Sie zu dem Abschnitt der Debug-Einstellungen von Windows Device Portal, und klicken Sie unter Starten Sie Visual Studio Remote Debugger auf die Schaltfläche "Start".</span><span class="sxs-lookup"><span data-stu-id="5c320-112">Now navigate to the Debug settings section of Windows Device Portal and click the Start button under Start Visual Studio Remote Debugger.</span></span> 

    ![WindowsDevicePortalDebugSettings Start-Remotedebugger](../media/Console/device_portal_start_debugger.png)

* <span data-ttu-id="5c320-114">Dies Popup Anzeigen eines Meldungsfelds und bieten Ihnen die Verbindungsinformationen.</span><span class="sxs-lookup"><span data-stu-id="5c320-114">This will show pop-up a message box and give you the connection information.</span></span> 

*  <span data-ttu-id="5c320-115">In Visual Studio können Sie Ihr Ziel konfigurieren, indem Sie den Eigenschaften Ihres Projekts (Achten Sie darauf, alle von den hervorgehobenen Änderungen vor, je nach Namen\noder IP-Adresse des Boards) bearbeiten:</span><span class="sxs-lookup"><span data-stu-id="5c320-115">In Visual Studio, you can configure your target by editing your project's properties (be sure to make all of the highlighted changes as appropriate to your board's name or IP address):</span></span>

    ![Projekteinstellungen für ConsoleApplication Remote-Computer](../media/Console/console_project_settings.png)
    
> [!NOTE]
> <span data-ttu-id="5c320-117">Wenn Sie nicht in der Abbildung oben angezeigt werden, finden Sie unter "Projektmappen-Explorer" im Kontextmenü, und wechseln Sie zu "Project Properties".</span><span class="sxs-lookup"><span data-stu-id="5c320-117">If you're not seeing the image above, please go to the "Solution Explorer" in the context menu, and go to "Project Properties".</span></span> <span data-ttu-id="5c320-118">Sie finden weitere Informationen zu Projekteigenschaften [hier](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span><span class="sxs-lookup"><span data-stu-id="5c320-118">You can find more information for project properties [here](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span></span>

> [!TIP]
> <span data-ttu-id="5c320-119">Sie können die IP-Adresse anstelle des Gerätenamens Windows IoT Core verwenden.</span><span class="sxs-lookup"><span data-stu-id="5c320-119">You can use the IP address instead of the Windows IoT Core device name.</span></span>

* <span data-ttu-id="5c320-120">Die Konfiguration des Projekts muss zum Aktivieren der Bereitstellung geändert werden.</span><span class="sxs-lookup"><span data-stu-id="5c320-120">The project configuration needs to be modified to enable deployment.</span></span>  <span data-ttu-id="5c320-121">Zu diesem Zweck öffnen Sie den Konfigurations-Manager durch Auswählen der Konfigurations-Manager aus der Konfiguration der Projektmappe Dropdown-Menü auf der Symbolleiste aus.</span><span class="sxs-lookup"><span data-stu-id="5c320-121">To do this, open the Configuration Manager by selecting the Configuration manger from the Solution Configuration drop-down menu on the toolbar.</span></span>

    ![ConsoleApplication SolutionConfiguration](../media/Console/configuration_management.png)

    <span data-ttu-id="5c320-123">Vom Configuration Manager, stellen Sie sicher, dass das Kontrollkästchen für die Bereitstellung für die Projektkonfiguration ausgewählt ist (Wenn diese Option deaktiviert ist, ist es wahrscheinlich, dass die Optionen für die nicht vollständig in den Projekteigenschaften die Registerkarte "Debuggen" vorgenommen wurden)</span><span class="sxs-lookup"><span data-stu-id="5c320-123">From the Configuration Manager, ensure that the Deploy checkbox is selected for your project configuration (if this options is disabled, it is likely that the deployment options have not been fully entered into the Debugging tab of the project properties)</span></span>

    ![Projekteinstellungen für ConsoleApplication Remote-Computer](../media/Console/deploy_checkbox.png)

* <span data-ttu-id="5c320-125">Wir nun können mit dem Remotegerät für Windows IoT Core bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5c320-125">Now we're ready to deploy to the remote Windows IoT Core device.</span></span> <span data-ttu-id="5c320-126">Drücken Sie einfach F5 (oder die Option Debuggen \| Debuggen starten) zum Starten des Debuggings unsere app.</span><span class="sxs-lookup"><span data-stu-id="5c320-126">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="5c320-127">Sie können auch Build \| Projektmappe bereitstellen, um die Anwendung einfach bereitzustellen, ohne eine Debugsitzung starten.</span><span class="sxs-lookup"><span data-stu-id="5c320-127">You can also use Build \| Deploy Solution to simply deploy your application without starting a debug session.</span></span>

> [!NOTE]
> <span data-ttu-id="5c320-128">Wenn in Visual Studio ausführen, die Ausgabe nicht an einer beliebigen Stelle zeigt, aber Sie können Haltepunkte festgelegt werden, finden Sie unter usw. Variablenwerte.</span><span class="sxs-lookup"><span data-stu-id="5c320-128">When run from Visual Studio, the output will not display anywhere, but you will be able to set breakpoints, see variable values, etc.</span></span>

* <span data-ttu-id="5c320-129">Drücken Sie auf die Schaltfläche "Debugging beenden", um die app zu beenden (oder die Option Debuggen \| Debuggen beenden).</span><span class="sxs-lookup"><span data-stu-id="5c320-129">To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

* <span data-ttu-id="5c320-130">Sie können jetzt die Anwendung ausführen.</span><span class="sxs-lookup"><span data-stu-id="5c320-130">You can now run the application.</span></span>  <span data-ttu-id="5c320-131">Öffnen Sie einfach eine PowerShell/SSH-Verbindung (Anweisungen finden Sie [hier, um PowerShell](../connect-your-device/PowerShell.md) und [hier, um SSH](../connect-your-device/SSH.md)), und geben Sie den oben angegebenen Remotebefehl.</span><span class="sxs-lookup"><span data-stu-id="5c320-131">Simply open a PowerShell/SSH connection (instructions can be found [here for PowerShell](../connect-your-device/PowerShell.md) and [here for SSH](../connect-your-device/SSH.md)) and enter the Remote Command you specified above.</span></span>

    ![ConsoleApplication-Ausgabe](../media/Console/console_output.png)

* <span data-ttu-id="5c320-133">Sobald Sie fertig sind Debuggen Ihrer Anwendung, denken Sie daran, den Remotedebugger auf dem Gerät Windows IoT Core zu beenden.</span><span class="sxs-lookup"><span data-stu-id="5c320-133">Once you are done debugging your application, remember to stop the remote debugger on the Windows IoT Core device.</span></span> <span data-ttu-id="5c320-134">Dazu können Sie zum Debuggen von im Einstellungsabschnitt Windows Device Portal navigieren und durch Klicken auf die Schaltfläche mit den Remotedebugger beenden.</span><span class="sxs-lookup"><span data-stu-id="5c320-134">You can do this by navigating to Debug settings section of Windows Device Portal and clicking on the Stop Remote Debugger button.</span></span>

    ![WindowsDevicePortalDebugSettings Stop-Remotedebugger](../media/Console/device_portal_stop_debugger.PNG)

