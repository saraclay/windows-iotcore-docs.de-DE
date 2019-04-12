---
title: Windows 10 IoT Core, Standard-App
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Erfahren Sie mehr über die Windows 10 IoT Core Standard-App und zugehörigen Funktionen.
keywords: Windows Iot, Windows 10 Iot Core, Standard-app
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512409"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="19b86-104">Übersicht über die App von Windows 10 IoT Core, Standard</span><span class="sxs-lookup"><span data-stu-id="19b86-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="19b86-105">Wenn Sie feststellen, dass Sie eine Funktion, die hinzugefügt werden, um diese Beispiel-app finden Sie unter möchten [eröffnen Sie ein Problem](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) auf GitHub, um uns zu informieren.</span><span class="sxs-lookup"><span data-stu-id="19b86-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="19b86-106">Wenn Sie einen Fehler einreichen möchten, befolgen Sie die Anweisungen für die Feedback-Hub [hier](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span><span class="sxs-lookup"><span data-stu-id="19b86-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="19b86-107">Wenn Sie zunächst auf Windows 10 IoT Core flash, Sie mit der Windows 10 IoT Core Standard-App beim Start, erhält der so aussieht:</span><span class="sxs-lookup"><span data-stu-id="19b86-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![Screenshot der standardmäßige IoT Core-App](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="19b86-109">Der Zweck dieser Anwendung ist nicht nur für bieten Ihnen eine benutzerfreundliche Shell zu interagieren, wenn Sie Windows 10 IoT Core das zuerst gestartet, aber wir haben Open Source-Code für diese Anwendung [hier](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) , damit Sie mit diesen Plug-and-Play-können Features auf Ihren eigenen benutzerdefinierten Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="19b86-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="19b86-110">In diesem Artikel erhalten Sie einen Überblick über die verschiedenen Funktionen, die die Windows 10 IoT Core Standard-App bietet auch, wie Sie diese verschiedenen Funktionen für Ihre eigenen Anwendungen nutzen können.</span><span class="sxs-lookup"><span data-stu-id="19b86-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="19b86-111">Nutzen die standardmäßige IoT Core-App</span><span class="sxs-lookup"><span data-stu-id="19b86-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="19b86-112">Verwenden Sie Maker Images nicht für gewerbliche Nutzung aus.</span><span class="sxs-lookup"><span data-stu-id="19b86-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="19b86-113">Wenn Sie ein Gerät commercializing sind, müssen Sie eine benutzerdefinierte FFU für optimale Sicherheit verwenden.</span><span class="sxs-lookup"><span data-stu-id="19b86-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="19b86-114">Weitere Informationen finden Sie [hier](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="19b86-114">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="19b86-115">Die IoT Core-Standard-App angepasst und erweitert werden können, oder Sie können den Quellcode als Beispiel für Ihre eigene app.</span><span class="sxs-lookup"><span data-stu-id="19b86-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="19b86-116">Um dies selbst auszuprobieren, laden Sie die ZIP-Datei mit unserer Beispiele, oder sehen Sie sich den Code für die IoT Core-Standard-App [hier](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="19b86-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="19b86-117">Fragen, ein Problem melden auf unsere-beispielrepository [hier](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span><span class="sxs-lookup"><span data-stu-id="19b86-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="19b86-118">Siehe unter der [Abschnitt "Einstellungen"](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) im folgenden, in einigen Fällen Sie möglicherweise konfigurieren Standardeinstellungen und Features auf Ihrem Kundensystem im Namen des Endbenutzers.</span><span class="sxs-lookup"><span data-stu-id="19b86-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="19b86-119">Aber wenn Sie aktivieren, diese Einstellungen und Features auf standardmäßig oder wenn die Diagnose über die Einstellung "Grundlegend" befinden, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="19b86-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="19b86-120">Der Endbenutzer zu benachrichtigen, dass diese Funktionen aktiviert wurden, und geben den Endbenutzer mit dem Link zur Webseite von Microsoft Datenschutzbestimmungen [hier](http://go.microsoft.com/fwlink/?LinkId=521839).</span><span class="sxs-lookup"><span data-stu-id="19b86-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="19b86-121">Sichern Sie Ihre Zustimmung, aus dem entsprechenden Benutzer Funktionen zu aktivieren, wird standardmäßig (falls erforderlich, durch das anwendbare Recht).</span><span class="sxs-lookup"><span data-stu-id="19b86-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="19b86-122">Geben Sie Endbenutzern die Möglichkeit, der die diagnoseeinstellung an der Einstellung "Grundlegend" zu ändern.</span><span class="sxs-lookup"><span data-stu-id="19b86-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="19b86-123">Wenn Sie die Microsoft-Accounts aktivieren, und Zugriff auf die Endbenutzerdaten, haben Wenn der Endbenutzer die Microsoft Account löscht, müssen Sie die gleichzeitigen löschen alle des Endbenutzers, Microsoft Account Daten auf dem Gerät aktivieren.</span><span class="sxs-lookup"><span data-stu-id="19b86-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="19b86-124">Out-of-Box-Experience (OOBE)</span><span class="sxs-lookup"><span data-stu-id="19b86-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="19b86-125">Die Out-of-Box-Experience für die IoT Core-Standard-App ist als lean, wie es abruft.</span><span class="sxs-lookup"><span data-stu-id="19b86-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="19b86-126">Die ersten Seiten werden für eine Sprache und WLAN-Einstellungen der Standardrichtlinie gefragt.</span><span class="sxs-lookup"><span data-stu-id="19b86-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="19b86-127">Von dort in der Reihenfolge für Ihre app auf DSGVO-Kompatibilität, benötigen Sie einen Bildschirm für diagnostische Daten und, wenn Sie planen, Speicherort nachzuverfolgen, müssen Sie einen Speicherort-berechtigungenbildschirm zu verfügen.</span><span class="sxs-lookup"><span data-stu-id="19b86-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="19b86-128">Beispiele für beide sind unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="19b86-128">Examples of both are shown below.</span></span> 

![<span data-ttu-id="19b86-129">Einstellungen für den Speicherort für OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![diagnoseeinstellungen für OOBE</span><span class="sxs-lookup"><span data-stu-id="19b86-129">Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE</span></span>](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a><span data-ttu-id="19b86-130">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="19b86-130">Command Bar</span></span>
<span data-ttu-id="19b86-131">Die Befehlsleiste ist der permanente Horizonatal-Leiste am unteren Rand des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="19b86-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="19b86-132">Dies bietet einfachen Zugriff auf die folgende Funktionalität:</span><span class="sxs-lookup"><span data-stu-id="19b86-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="19b86-133">Vorwärts und rückwärts navigieren</span><span class="sxs-lookup"><span data-stu-id="19b86-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="19b86-134">Grundlegende Geräteinformationen, ohne die aktuelle Seite</span><span class="sxs-lookup"><span data-stu-id="19b86-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="19b86-135">Aktivieren oder Deaktivieren von Vollbildmodus</span><span class="sxs-lookup"><span data-stu-id="19b86-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="19b86-136">Erweiterten Verknüpfungen</span><span class="sxs-lookup"><span data-stu-id="19b86-136">Advance shortcuts</span></span>
- <span data-ttu-id="19b86-137">Bestimmte Seite-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="19b86-137">Page specific buttons</span></span>

<span data-ttu-id="19b86-138">Es gibt viele Schaltflächen auf der Befehlsleiste, und manchmal dieser Schaltflächen verwirrend oder ausgeblendet werden können.</span><span class="sxs-lookup"><span data-stu-id="19b86-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="19b86-139">Auf der Befehlsleiste zu erweitern, Zugriff auf diese Schaltflächen, und drücken Sie die Menüschaltfläche, in der unteren rechten Ecke:</span><span class="sxs-lookup"><span data-stu-id="19b86-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![Wie Sie die Befehlsleiste zu erweitern](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="19b86-141">Startmenü - Play</span><span class="sxs-lookup"><span data-stu-id="19b86-141">Start Menu - Play</span></span>

<span data-ttu-id="19b86-142">Im Menü Start werden die meisten Features von Plug & Play gespeichert.</span><span class="sxs-lookup"><span data-stu-id="19b86-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="19b86-143">Wetter</span><span class="sxs-lookup"><span data-stu-id="19b86-143">Weather</span></span>
<span data-ttu-id="19b86-144">Verwenden die Daten von der National Weather Service, rendert die Seite "Weather" Wetterdaten in Ihrem aktuellen Standort.</span><span class="sxs-lookup"><span data-stu-id="19b86-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="19b86-145">Webbrowser</span><span class="sxs-lookup"><span data-stu-id="19b86-145">Web Browser</span></span>
<span data-ttu-id="19b86-146">Der Webbrowser können Sie sich die meisten Websites aus dem Web abrufen.</span><span class="sxs-lookup"><span data-stu-id="19b86-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="19b86-147">Musik</span><span class="sxs-lookup"><span data-stu-id="19b86-147">Music</span></span>
<span data-ttu-id="19b86-148">Auf dieser Seite spielen MP3 und WAV-Dateien aus der **Musikbibliothek**, können auf das über die [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="19b86-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="19b86-149">Zum Hochladen von Dateien für den Musikplayer müssen Sie navigieren zu den Windows Device Portal, klicken auf die Dropdownliste "Apps", navigieren zu "Datei-Explorer", "Music" auswählen und Hochladen von Dateien von dort aus.</span><span class="sxs-lookup"><span data-stu-id="19b86-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![Gewusst wie: Hochladen von Musikdateien](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="19b86-151">Slideshow</span><span class="sxs-lookup"><span data-stu-id="19b86-151">Slideshow</span></span>
<span data-ttu-id="19b86-152">Auf dieser Seite zeigt alle PNG- oder JPEG-Bild-Dateien aus der **Bildbibliothek**, können auf das über die [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="19b86-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="19b86-153">Zum Hochladen von Bildern in der Diaschau, müssen Sie navigieren zu den Windows Device Portal, klicken auf die Dropdownliste "Apps", navigieren zu "Datei-Explorer", wählen Sie "Bilder" und Hochladen von Dateien von dort aus.</span><span class="sxs-lookup"><span data-stu-id="19b86-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![Gewusst wie: Hochladen von Musikdateien](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="19b86-155">Draw</span><span class="sxs-lookup"><span data-stu-id="19b86-155">Draw</span></span>
<span data-ttu-id="19b86-156">Auf dieser Seite können Sie Windows 10 IoT Core Freihandfunktionen zu testen.</span><span class="sxs-lookup"><span data-stu-id="19b86-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="19b86-157">Startmenü - erkunden</span><span class="sxs-lookup"><span data-stu-id="19b86-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="19b86-158">Apps</span><span class="sxs-lookup"><span data-stu-id="19b86-158">Apps</span></span> 
<span data-ttu-id="19b86-159">Auf dieser Seite können Sie zum Starten von anderen Foreground-Anwendungen, die auf dem Gerät installiert.</span><span class="sxs-lookup"><span data-stu-id="19b86-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="19b86-160">Starten einer Anwendung wird angehalten, IoT Core Standard-App, die erneut gestartet werden kann, mit dem App-Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="19b86-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="19b86-161">Keine besonderen ist erforderlich, um die vordergrundanwendung, die auf der Seite aufgeführt sind, einfach verfügen [installieren](AppInstaller.md) oder [bereitstellen](AppDeployment.md) der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="19b86-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="19b86-162">Navigieren Sie nach der erfolgreichen Installation oder Bereitstellung erneut auf die Seite "Apps", um die Liste der Anwendungen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="19b86-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="19b86-163">Beachten Sie, dass es eine Reihe von automatisch generierten OS beziehen Anwendungen, die Sie filtern, finden Sie die Liste der app-Namen [hier](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span><span class="sxs-lookup"><span data-stu-id="19b86-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="19b86-164">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="19b86-164">Notifications</span></span>
<span data-ttu-id="19b86-165">Auf dieser Seite listet die letzten 20 Benachrichtigungen, da IoT Core-Standard-App gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="19b86-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="19b86-166">Wenn IoT Core-Standard-App im Debugmodus ausgeführt wird, werden erstellt, die von testbenachrichtigungen Schaltflächen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="19b86-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="19b86-167">Protokolldateien</span><span class="sxs-lookup"><span data-stu-id="19b86-167">Logs</span></span>
<span data-ttu-id="19b86-168">Auf dieser Seite listet alle automatisch generierten Abstürze oder Fehler Protokolle, die dann aus dem Gerät genommen und analysiert werden können.</span><span class="sxs-lookup"><span data-stu-id="19b86-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="19b86-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="19b86-169">GitHub</span></span>
<span data-ttu-id="19b86-170">Diese Seite gelangen Sie auf den Open Source-GitHub-Speicherort des Codes IoT Core-Standard-App.</span><span class="sxs-lookup"><span data-stu-id="19b86-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="19b86-171">Starten Sie Windows Device Portal-Menü –</span><span class="sxs-lookup"><span data-stu-id="19b86-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="19b86-172">Die Seiten in diesem Abschnitt nutzen Sie die Windows Device Portal REST-APIs, sich mit Ihren Windows Device Portal-Anmeldeinformationen anmelden müssen.</span><span class="sxs-lookup"><span data-stu-id="19b86-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="19b86-173">Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="19b86-173">Device Information</span></span>

<span data-ttu-id="19b86-174">Auf dieser Seite können Sie die verschiedenen Features für Ihr Gerät wie z.B. Ethernet-OS-Version, verbundenen Geräten und mehr finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="19b86-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="19b86-175">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="19b86-175">Command Line</span></span>

<span data-ttu-id="19b86-176">Auf dieser Seite können Sie Befehle direkt auf Ihrem Gerät ausführen.</span><span class="sxs-lookup"><span data-stu-id="19b86-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="19b86-177">Zum Aktivieren dieses Features müssen Sie einen Registrierungsschlüssel festlegen, damit die app die Befehle ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="19b86-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="19b86-178">Beim ersten Versuch zum Ausführen eines Befehls sehen Sie eine Verknüpfung, die Sie den Registrierungsschlüssel, die über einen Aufruf an die Windows Device Portal festlegen können.</span><span class="sxs-lookup"><span data-stu-id="19b86-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="19b86-179">Klicken Sie auf den Link, um Ihr Gerät zum Ausführen von Befehlen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="19b86-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="19b86-180">Einige Befehle erfordern Administratorzugriff.</span><span class="sxs-lookup"><span data-stu-id="19b86-180">Some commands require administrator access.</span></span> <span data-ttu-id="19b86-181">Aus Sicherheitsgründen verwendet die app wird standardmäßig ein nicht-Administratorkonto zum Ausführen von Befehlen an.</span><span class="sxs-lookup"><span data-stu-id="19b86-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="19b86-182">Wenn Sie einen Befehl als Administrator ausführen möchten. Sie können eingeben "RunAsAdmin <your command>" in der Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="19b86-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="19b86-183">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="19b86-183">Settings</span></span>
<span data-ttu-id="19b86-184">Sie werden eine Reihe von einschließlich Wi-Fi, Bluetooth, Power-Optionen und weitere Einstellungen konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="19b86-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="19b86-185">App-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="19b86-185">App Settings</span></span>
<span data-ttu-id="19b86-186">Die **Anwendungseinstellungen** Abschnitt können Sie verschiedene Einstellungen für Seiten in der app zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="19b86-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="19b86-187">Sind einige der Einstellungen, die Sie anpassen können:</span><span class="sxs-lookup"><span data-stu-id="19b86-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="19b86-188">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="19b86-188">General Settings</span></span>
* <span data-ttu-id="19b86-189">Legen Sie die Standardseite, die angezeigt wird, wenn die app gestartet wird</span><span class="sxs-lookup"><span data-stu-id="19b86-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="19b86-190">Aktivieren/Deaktivieren des Bildschirmschoners</span><span class="sxs-lookup"><span data-stu-id="19b86-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="19b86-191">Wetter-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="19b86-191">Weather Settings</span></span>
* <span data-ttu-id="19b86-192">Ändern Sie den Speicherort</span><span class="sxs-lookup"><span data-stu-id="19b86-192">Change the location</span></span>
  > <span data-ttu-id="19b86-193">Dieses Feature ist nur aktiviert, wenn Sie einen gültigen angegeben haben [Bing Map-Diensts Token](https://msdn.microsoft.com/library/ff428642.aspx).</span><span class="sxs-lookup"><span data-stu-id="19b86-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="19b86-194">Um das Token an die app zu übergeben, erstellen eine **MapToken.config** Datei im Ordner "LocalState" der app (z. B. C:\Data\USERS\\[Benutzerkonto] \AppData\Packages\\[Vollständiger Paketname] \LocalState\ MapToken.config) und die app neu starten.</span><span class="sxs-lookup"><span data-stu-id="19b86-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="19b86-195">Erweitern Sie die Karte</span><span class="sxs-lookup"><span data-stu-id="19b86-195">Expand the map</span></span>
* <span data-ttu-id="19b86-196">Aktivieren/deaktivieren, damit die Zuordnung und der Wetter-Schalter wird in regelmäßigen Abständen zum Bildschirm Burn-in zu verhindern, dass zuordnen kippen</span><span class="sxs-lookup"><span data-stu-id="19b86-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="19b86-197">Webbrowser-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="19b86-197">Web Browser Settings</span></span>
* <span data-ttu-id="19b86-198">Legen Sie auf der Startseite für den Webbrowser</span><span class="sxs-lookup"><span data-stu-id="19b86-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="19b86-199">Diaschau-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="19b86-199">Slideshow Settings</span></span>
* <span data-ttu-id="19b86-200">Legen Sie das Intervall Bildschirmpräsentation</span><span class="sxs-lookup"><span data-stu-id="19b86-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="19b86-201">Darstellung</span><span class="sxs-lookup"><span data-stu-id="19b86-201">Appearance</span></span>
* <span data-ttu-id="19b86-202">Verwenden von MDL2 Objekte anstelle von Emojis für die Kachel "-Symbole</span><span class="sxs-lookup"><span data-stu-id="19b86-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="19b86-203">Legen Sie die Kachel Breite und Höhe</span><span class="sxs-lookup"><span data-stu-id="19b86-203">Set the tile width and height</span></span>
* <span data-ttu-id="19b86-204">Skalierung von UI - Festlegen der automatischen Skalierung wird standardmäßig festgelegt</span><span class="sxs-lookup"><span data-stu-id="19b86-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="19b86-205">Legen Sie die kachelfarbe</span><span class="sxs-lookup"><span data-stu-id="19b86-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="19b86-206">System</span><span class="sxs-lookup"><span data-stu-id="19b86-206">System</span></span>
<span data-ttu-id="19b86-207">Ändern Sie die Sprache, Tastaturlayout und Zeitzone.</span><span class="sxs-lookup"><span data-stu-id="19b86-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="19b86-208">Netzwerk und WLAN</span><span class="sxs-lookup"><span data-stu-id="19b86-208">Network & Wi-Fi</span></span>
<span data-ttu-id="19b86-209">Zeigen Sie der Eigenschaften des Netzwerkadapters an, oder eine Verbindung mit einem verfügbaren Wi-Fi-Netzwerk herstellen.</span><span class="sxs-lookup"><span data-stu-id="19b86-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="19b86-210">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="19b86-210">Bluetooth</span></span>
<span data-ttu-id="19b86-211">Mit einem Bluetooth-Gerät koppeln.</span><span class="sxs-lookup"><span data-stu-id="19b86-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="19b86-212">App-Updates</span><span class="sxs-lookup"><span data-stu-id="19b86-212">App Updates</span></span>
<span data-ttu-id="19b86-213">Überprüfen Sie nach app-Updates oder Ändern von Einstellungen für automatische Updates.</span><span class="sxs-lookup"><span data-stu-id="19b86-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="19b86-214">Energieoptionen</span><span class="sxs-lookup"><span data-stu-id="19b86-214">Power Options</span></span>
<span data-ttu-id="19b86-215">Neustarten oder Herunterfahren des Geräts.</span><span class="sxs-lookup"><span data-stu-id="19b86-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="19b86-216">Diagnose</span><span class="sxs-lookup"><span data-stu-id="19b86-216">Diagnostics</span></span>
<span data-ttu-id="19b86-217">Wählen Sie den Zeitraum von Diagnosedaten, die Sie Microsoft zur Verfügung stellen möchten.</span><span class="sxs-lookup"><span data-stu-id="19b86-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="19b86-218">Wir empfehlen, dass Benutzer abonnieren **vollständige** Diagnosedaten können Probleme schnell diagnostizieren und nehmen Sie Verbesserungen für das Produkt.</span><span class="sxs-lookup"><span data-stu-id="19b86-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="19b86-219">Einfach</span><span class="sxs-lookup"><span data-stu-id="19b86-219">Basic</span></span> 
<span data-ttu-id="19b86-220">Senden Sie nur Informationen zu Ihrem Gerät, dessen Einstellungen und Funktionen, und gibt an, ob er ordnungsgemäß arbeitet.</span><span class="sxs-lookup"><span data-stu-id="19b86-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="19b86-221">Vollständig</span><span class="sxs-lookup"><span data-stu-id="19b86-221">Full</span></span>
<span data-ttu-id="19b86-222">Senden Sie alle grundlegende Diagnosedaten und Informationen zu Websites, die Sie durchsuchen und die Verwendung von apps und Features sowie zusätzliche Informationen über die Integrität für Geräte,, Geräteaktivität und verbesserte Fehlerberichterstattung.</span><span class="sxs-lookup"><span data-stu-id="19b86-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="19b86-223">Pfad</span><span class="sxs-lookup"><span data-stu-id="19b86-223">Location</span></span>
<span data-ttu-id="19b86-224">Zulassen oder Ablehnen des app Zugriffs auf Ihren Standort.</span><span class="sxs-lookup"><span data-stu-id="19b86-224">Allow or deny the app access to your location.</span></span>
