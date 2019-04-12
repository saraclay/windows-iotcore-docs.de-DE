---
title: Eingebetteten Modus
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Informationen Sie zum Konfigurieren von Windows um eingebetteten Modus aktivieren hintergrundanwendungen und andere Funktionen zu ermöglichen.
keywords: Windows Iot, eingebetteten Modus, Programme im Hintergrund
ms.openlocfilehash: 1944cec09400cff4d895bb9e55b89b3b19a3f5f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512321"
---
# <a name="embedded-mode"></a><span data-ttu-id="237f2-104">Eingebetteten Modus</span><span class="sxs-lookup"><span data-stu-id="237f2-104">Embedded mode</span></span>

<span data-ttu-id="237f2-105">Eingebetteter Modus wird unter Windows IoT Core und Windows IoT Enterprise unterstützt.</span><span class="sxs-lookup"><span data-stu-id="237f2-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="237f2-106">Eingebetteter Modus ermöglicht:</span><span class="sxs-lookup"><span data-stu-id="237f2-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="237f2-107">Programme im Hintergrund (Weitere Informationen)</span><span class="sxs-lookup"><span data-stu-id="237f2-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="237f2-108">Verwenden der LowLevelDevice-Funktion</span><span class="sxs-lookup"><span data-stu-id="237f2-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="237f2-109">Verwenden der Management-Funktion</span><span class="sxs-lookup"><span data-stu-id="237f2-109">Use of systemManagement capability</span></span>

<span data-ttu-id="237f2-110">Eingebetteter Modus ist immer auf Fenster IoT Core aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="237f2-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="237f2-111">Eingebetteter Modus muss aktiviert werden, indem Sie die folgenden Schritte auf Windows IoT Enterprise.</span><span class="sxs-lookup"><span data-stu-id="237f2-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="237f2-112">Programme im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="237f2-112">Background Applications</span></span>

<span data-ttu-id="237f2-113">Hintergrundanwendungen werden mit die Hintergrundanwendung (IoT)-Vorlage in Visual Studio erstellt.</span><span class="sxs-lookup"><span data-stu-id="237f2-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="237f2-114">Weitere Informationen zum Erstellen [Hintergrundanwendungen](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span><span class="sxs-lookup"><span data-stu-id="237f2-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="237f2-115">Programme im Hintergrund ausführen, ohne Unterbrechung und ohne Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="237f2-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="237f2-116">Auch wenn die hintergrundanwendung aus irgendeinem Grund beendet wird, und eingebettete aktiviert ist die hintergrundanwendung wird durch das System neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="237f2-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="237f2-117">Während das System automatisch hintergrundanwendungen neu gestartet wird, müssen zum Sperren von Systemfunktionen zu verhindern, dass Benutzer beenden oder beeinträchtigt den Betrieb von Hintergrundanwendungen aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="237f2-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowleveldevice-capability"></a><span data-ttu-id="237f2-118">LowLevelDevice-Funktion</span><span class="sxs-lookup"><span data-stu-id="237f2-118">lowLevelDevice Capability</span></span>

<span data-ttu-id="237f2-119">Die Funktion LowLevelDevice ermöglicht den Zugriff auf Low-Level Hardwareschnittstellen wie GPIO, I2C und SPI.</span><span class="sxs-lookup"><span data-stu-id="237f2-119">The lowLevelDevice Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="237f2-120">Hauptverkaufsargument Sample(GPIO)</span><span class="sxs-lookup"><span data-stu-id="237f2-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="237f2-121">Beschleunigungsmesserbeispiel</span><span class="sxs-lookup"><span data-stu-id="237f2-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

## <a name="systemmanagment-capability"></a><span data-ttu-id="237f2-122">SystemManagment-Funktion</span><span class="sxs-lookup"><span data-stu-id="237f2-122">systemManagment Capability</span></span>

<span data-ttu-id="237f2-123">Wenn Sie die SystemManagment-Funktionen für Ihre Anwendung aktivieren, ist dies den Satz von APIs, die nicht gesperrte abruft:</span><span class="sxs-lookup"><span data-stu-id="237f2-123">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="237f2-124">Windows.System.ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="237f2-124">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="237f2-125">Windows.System.TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="237f2-125">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="237f2-126">Windows.System.ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="237f2-126">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="237f2-127">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="237f2-127">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="237f2-128">Debuggen von Hintergrundanwendungen</span><span class="sxs-lookup"><span data-stu-id="237f2-128">Debugging Background Applications</span></span>

<span data-ttu-id="237f2-129">Wenn Debuggen auf einem Gerät, auf denen nicht Windows IoT Core ausgeführt wird, und Sie eine der folgenden Fehlermeldungen sehen müssen Sie sicherstellen, dass AllowEmbeddedMode auf dem Gerät aktiviert ist und der eingebetteten Modus-Dienst ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="237f2-129">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="237f2-130">Es sind keine weiteren Endpunkte von der endpunktzuordnung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="237f2-130">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="237f2-131">Dieses Programm ist durch Gruppenrichtlinien blockiert.</span><span class="sxs-lookup"><span data-stu-id="237f2-131">This program is blocked by group policy.</span></span> <span data-ttu-id="237f2-132">Weitere Informationen wenden Sie sich an Ihren Systemadministrator.</span><span class="sxs-lookup"><span data-stu-id="237f2-132">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="237f2-133">Modus ändern</span><span class="sxs-lookup"><span data-stu-id="237f2-133">Changing the mode</span></span>
<span data-ttu-id="237f2-134">Um eingebetteten Modus zu aktivieren, Sie müssen ein Bereitstellungspaket erstellen, in der Abbilderstellung und der Configuration Designer (Windows ICD), die AllowEmbeddedMode festlegt = 1.</span><span class="sxs-lookup"><span data-stu-id="237f2-134">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="237f2-135">ICD installieren, müssen Sie zum Herunterladen und installieren das Windows ADK für Windows 10.</span><span class="sxs-lookup"><span data-stu-id="237f2-135">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="237f2-136">Das Windows ADK für Windows 10 herunterladen</span><span class="sxs-lookup"><span data-stu-id="237f2-136">Download the Windows ADK for Windows 10</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [<span data-ttu-id="237f2-137">Erfahren Sie mehr über die Neuigkeiten in das Windows ADK für Windows 10</span><span class="sxs-lookup"><span data-stu-id="237f2-137">Learn about what's new in the Windows ADK for Windows 10</span></span>](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. <span data-ttu-id="237f2-138">Wenn das ADK installieren auswählen **Abbilderstellung und der Configuration Designer (Windows ICD)**</span><span class="sxs-lookup"><span data-stu-id="237f2-138">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="237f2-139">Führen Sie nach der Installation Windows Imaging und Konfigurations-Designer (WICD).</span><span class="sxs-lookup"><span data-stu-id="237f2-139">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![Symbol "WICD"](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="237f2-141">Klicken Sie auf **Erweiterte Bereitstellung**.</span><span class="sxs-lookup"><span data-stu-id="237f2-141">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="237f2-142">Nennen Sie das Projekt **AllowEmbeddedMode** , und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="237f2-142">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    ![Schritt 3](../media/EmbeddedMode/Step3.png)

4. <span data-ttu-id="237f2-144">Wählen Sie **üblich, alle Editionen von Windows** dann **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="237f2-144">Choose **Common to all Windows editions** then **Next**.</span></span>
    ![Schritt 4](../media/EmbeddedMode/Step4.png)

5. <span data-ttu-id="237f2-146">Klicken Sie auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="237f2-146">Click **Finish**.</span></span>

    ![Schritt 5](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="237f2-148">Klicken Sie in das Suchfeld **EmbeddedMode** , und klicken Sie dann auf **AllowEmbeddedMode**.</span><span class="sxs-lookup"><span data-stu-id="237f2-148">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![Schritt 6](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="237f2-150">Legen Sie den Wert des in der Mitte Bereich **AllowEmbeddedMode** zu **Ja** ![Step7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="237f2-150">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="237f2-151">Klicken Sie auf Exportieren > Bereitstellungspaket</span><span class="sxs-lookup"><span data-stu-id="237f2-151">Click Export > Provisioning Package</span></span>

    ![Step8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="237f2-153">Klicken Sie auf Weiter.</span><span class="sxs-lookup"><span data-stu-id="237f2-153">Click Next.</span></span>

    ![Step9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="237f2-155">Klicken Sie auf Weiter.</span><span class="sxs-lookup"><span data-stu-id="237f2-155">Click Next.</span></span>

    ![Step10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="237f2-157">Klicken Sie auf Weiter.</span><span class="sxs-lookup"><span data-stu-id="237f2-157">Click Next.</span></span>

    ![Step11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="237f2-159">Klicken Sie auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="237f2-159">Click Build.</span></span>

    ![Schritt12 fort](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="237f2-161">Um die eingebetteten Modus zu installieren. PPKG unter Windows IoT Enterprise Doppelklicken Sie auf der. PPKG.</span><span class="sxs-lookup"><span data-stu-id="237f2-161">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="237f2-162">Klicken Sie auf **Ja, hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="237f2-162">Click **Yes, add it**.</span></span>
    <span data-ttu-id="237f2-163">Klicken Sie auf Ja, auf das Dialogfeld "LUA", wenn es angezeigt wird, und klicken Sie auf **Ja, hinzufügen** auf die unten gezeigte Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="237f2-163">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="237f2-165">Hintergrundanwendung für die Ausführung konfigurieren automatisch</span><span class="sxs-lookup"><span data-stu-id="237f2-165">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="237f2-166">Hintergrundanwendung automatisch bei der Ausführung zu konfigurieren, müssen Sie die Anweisungen zum [MinnowBoardMax SD-Karten erstellen](https://developer.microsoft.com/en-us/windows/iot/getstarted) , und kopieren Sie `D:\windows\system32\iotstartup.exe` (wobei "d:" der SD-Karte ist).</span><span class="sxs-lookup"><span data-stu-id="237f2-166">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="237f2-167">So erhalten Sie eine Liste der installierten Programme im Hintergrund-Typ:</span><span class="sxs-lookup"><span data-stu-id="237f2-167">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="237f2-168">Die Ausgabe sollte den vollständigen Namen der einzelnen installierten Anwendungen Hintergrund enthalten, das wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="237f2-168">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="237f2-169">So konfigurieren Sie diese app auf Starttyp ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="237f2-169">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="237f2-170">Wenn der Hintergrund-Anwendung wurde erfolgreich zur Startliste hinzugefügt wurde sollte Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="237f2-170">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="237f2-171">Neustarten des eingebetteten Modus-Geräts:</span><span class="sxs-lookup"><span data-stu-id="237f2-171">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="237f2-172">Sobald das Gerät neu gestartet wurde, wird der Hintergrund-Anwendung automatisch gestartet.</span><span class="sxs-lookup"><span data-stu-id="237f2-172">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="237f2-173">Der eingebetteten Modus-Dienst, der Hintergrundanwendungen verwaltet dauert einige Minuten, um zu starten.</span><span class="sxs-lookup"><span data-stu-id="237f2-173">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="237f2-174">Der Dienst eingebetteten Modus Hintergrundanwendungen auf Startliste zu überwachen, und stellen Sie sicher, dass sie neu gestartet zu erhalten, wenn sie beendet wird.</span><span class="sxs-lookup"><span data-stu-id="237f2-174">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="237f2-175">Wenn Hintergrundanwendung mehrere Male in kurzer Zeit beendet wird, wird sie nicht mehr gestartet.</span><span class="sxs-lookup"><span data-stu-id="237f2-175">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="237f2-176">So entfernen Sie die Hintergrund-Anwendung aus der Liste Starttyp:</span><span class="sxs-lookup"><span data-stu-id="237f2-176">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="237f2-177">Wenn der Hintergrund-Anwendung aus der Startliste entfernt wird, wird die Ausgabe wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="237f2-177">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
