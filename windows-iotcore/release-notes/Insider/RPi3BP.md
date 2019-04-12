---
title: Anmerkungen zu dieser Version für Raspberry Pi 3 b
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 05/16/2018
ms.topic: article
description: Lesen Sie aus, und erfahren Sie mehr über die neuerungen in den Build für Raspberry Pi 3 b +.
keywords: Windows Iot, Windows-Insider, Anmerkungen zu dieser Version, Raspberry Pi 3 b +
ms.openlocfilehash: f9a1bf98e6ef53ff7f96d35cb34af9527f1c6de1
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512698"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="d1beb-104">Anmerkungen zu dieser Version für Raspberry Pi 3 b</span><span class="sxs-lookup"><span data-stu-id="d1beb-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="d1beb-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="d1beb-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="d1beb-106">Alle Rechte vorbehalten.</span><span class="sxs-lookup"><span data-stu-id="d1beb-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="d1beb-107">Diese Version für die Raspberry Pi 3 b + ist eine nicht unterstützte technical Preview-Version.</span><span class="sxs-lookup"><span data-stu-id="d1beb-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="d1beb-108">Begrenzt überprüft und die Aktivierung abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="d1beb-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="d1beb-109">Die aktuelle Version finden Sie [hier](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="d1beb-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="d1beb-110">Treten Sie für eine bessere Evaluierung auf, und für alle kommerziellen Produkten, verwenden Sie den Raspberry Pi 3-b oder andere Geräte mit unterstützten Intel, Qualcomm oder NXP SoCs.</span><span class="sxs-lookup"><span data-stu-id="d1beb-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="d1beb-111">Zur Behandlung von Problemen mit dem Raspberry Pi 3 b aus, informieren Sie sich unsere Handbuch zur Problembehandlung [hier](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="d1beb-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="d1beb-112">Was ist neu in diesem Build:</span><span class="sxs-lookup"><span data-stu-id="d1beb-112">What's new in this build:</span></span> 
* <span data-ttu-id="d1beb-113">Allgemeine Fehlerbehebungen</span><span class="sxs-lookup"><span data-stu-id="d1beb-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="d1beb-114">Bekannte Probleme im Build:</span><span class="sxs-lookup"><span data-stu-id="d1beb-114">Known issues in this build:</span></span>
* <span data-ttu-id="d1beb-115">Dieses Image ist nur für RPi3B vorgesehen und werden nicht auf RPi2 gestartet.</span><span class="sxs-lookup"><span data-stu-id="d1beb-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="d1beb-116">F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d1beb-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="d1beb-117">Integrieren WLAN- und Bluetooth funktionieren auf RPI3B + nicht.</span><span class="sxs-lookup"><span data-stu-id="d1beb-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="d1beb-118">Ft5406 Touch Bildschirm Treiber ist für RPi3B + deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="d1beb-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="d1beb-119">SD-Karte Aktivität LED ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="d1beb-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="d1beb-120">Bildschirmauflösung ist, dass der Monitor getrennt ist</span><span class="sxs-lookup"><span data-stu-id="d1beb-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="d1beb-121">Der Raspberry Pi 3 b + kann nicht Bildschirmauflösung verwalten Monitor wird die Verbindung getrennt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="d1beb-122">Die EDID des Monitors wird verwendet, um die Auflösung des Systems festgelegt, wenn ein solches angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="d1beb-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="d1beb-123">Wenn getrennt, wird standardmäßig die Firmware wird die "config.txt" im Stammverzeichnis der SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="d1beb-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="d1beb-124">Video-Leistung</span><span class="sxs-lookup"><span data-stu-id="d1beb-124">Video performance</span></span>
<span data-ttu-id="d1beb-125">Leistung der Videowiedergabe auf der Plattform ist nicht optimiert.</span><span class="sxs-lookup"><span data-stu-id="d1beb-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="d1beb-126">Animiert die Benutzer, die Elemente, einschließlich XAML-basierte Dropdownmenüs weniger als eine optimale Leistung aufweisen können.</span><span class="sxs-lookup"><span data-stu-id="d1beb-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="d1beb-127">Kameraunterstützung</span><span class="sxs-lookup"><span data-stu-id="d1beb-127">Camera support</span></span>
<span data-ttu-id="d1beb-128">Unterstützung für Peripheriegeräte Kamera ist eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="d1beb-129">Das PiCam-Gerät direkt mit der integrierten Kamera-Bus verbunden wird nicht unterstützt, aufgrund von Einschränkungen in der Plattform, moderne D3D-USB-Webcams erzeugen-Datenströme zu unterstützen, die auf dem USB-Hostcontroller äußerst anspruchsvollen sind.</span><span class="sxs-lookup"><span data-stu-id="d1beb-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="d1beb-130">Selbst bei Verwendung mit niedriger Auflösung Einstellungen Webcams erfordert zusätzliche USB-Optimierung und spezielle Logik des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="d1beb-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="d1beb-131">Mauszeiger verschwindet während des Debuggens</span><span class="sxs-lookup"><span data-stu-id="d1beb-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="d1beb-132">Klicken Sie in einigen Fällen der Mauszeiger nach dem Bereitstellen oder Debuggen von apps mit Visual Studio nicht sichtbar ist, der Mauszeiger sollte wieder angezeigt, wenn Sie den Fokus mit der Tastatur (Registerkarte) (8038595) ändern.</span><span class="sxs-lookup"><span data-stu-id="d1beb-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="d1beb-133">Server-Anwendungen mit SoftAP</span><span class="sxs-lookup"><span data-stu-id="d1beb-133">Server applications with SoftAP</span></span>
<span data-ttu-id="d1beb-134">Wenn die SoftAP Clients nicht den Zugriff auf Inhalte von UAP-apps verfügbar gemacht werden können.</span><span class="sxs-lookup"><span data-stu-id="d1beb-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="d1beb-135">Die folgenden Änderungen müssen über die Konsole auf dem Gerät (8111807) vorgenommen werden, um über SoftAP UAP-Anwendungen verfügbar zu machen:</span><span class="sxs-lookup"><span data-stu-id="d1beb-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="d1beb-136">Starten Sie neu.</span><span class="sxs-lookup"><span data-stu-id="d1beb-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="d1beb-137">Sensor-Treiber-Konflikt im vorgefertigten FFUs</span><span class="sxs-lookup"><span data-stu-id="d1beb-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="d1beb-138">In der bereitgestellten FFUs vorliegt ein Sensor-Treiber-Konflikt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="d1beb-139">Das Remote-Sensor-Framework werden die Treiber für Kompass, Magnetometer, Beschleunigungsmesser und Gyrometer installiert.</span><span class="sxs-lookup"><span data-stu-id="d1beb-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="d1beb-140">Die UWP-APIs für den Zugriff auf diese aus einer Anwendung wird davon ausgegangen, dass nur eine installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d1beb-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="d1beb-141">Wenn Sie einen Treiber für ein physisch angeschlossenen Gerät entwickeln, vorausgesetzt die remote-Treiber auf der Microsoft FFUs in Konflikt steht.</span><span class="sxs-lookup"><span data-stu-id="d1beb-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="d1beb-142">Um für dieses Problem zu lösen, kann der in Konflikt stehenden Treiber durch Herstellen einer Verbindung mit dem Gerät über SSH oder Powershell, und verwenden das Tool devcon.exe Entfernen des remote-Sensor-Treibers durch Eingabe entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="d1beb-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="d1beb-143">Der remote-Sensor-Treiber hat keine Auswirkungen auf die OEM-Abhängige FFUs erstellt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="d1beb-144">Standard-Administratorbenutzernamen und das Kennwort</span><span class="sxs-lookup"><span data-stu-id="d1beb-144">Default administrator user name and password</span></span>
<span data-ttu-id="d1beb-145">Die Standard-Administratorbenutzernamen und das Kennwort sind fest codiert, in das Windows 10 IoT Core-Image.</span><span class="sxs-lookup"><span data-stu-id="d1beb-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="d1beb-146">Dies ist ein Sicherheitsrisiko für das Gerät, und es nicht verfügbar gemacht werden, eine Internetverbindung geöffnet, bis das Kennwort geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="d1beb-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="d1beb-147">Lautstärkeregler</span><span class="sxs-lookup"><span data-stu-id="d1beb-147">Volume controls</span></span>
<span data-ttu-id="d1beb-148">Hardware-Volume-Steuerelemente für USB-Mikrofone und Lautsprecher, die auf Windows-System so ändern Sie den Systemdatenträger abhängig sind, werden auf Windows 10 IoT Core derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="d1beb-149">USB-Tastatur</span><span class="sxs-lookup"><span data-stu-id="d1beb-149">USB keyboards</span></span>
<span data-ttu-id="d1beb-150">Einige USB-Tastaturen und Mäusen funktioniert möglicherweise nicht unter IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d1beb-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="d1beb-151">Verwenden einer anderen Tastatur oder Maus.</span><span class="sxs-lookup"><span data-stu-id="d1beb-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="d1beb-152">Eine Liste der überprüften Peripheriegeräten finden Sie in der Dokumentation [hier](http://go.microsoft.com/fwlink/?LinkId=619428).</span><span class="sxs-lookup"><span data-stu-id="d1beb-152">A list of validated peripheral devices can be found in the documentation [here](http://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="d1beb-153">Bildschirmausrichtung</span><span class="sxs-lookup"><span data-stu-id="d1beb-153">Screen orientation</span></span>
<span data-ttu-id="d1beb-154">Die Ausrichtung auf "Hochformat" festlegen kann nicht in einer universellen App berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="d1beb-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="d1beb-155">Verweisen Netzwerkkarten mit AllJoyn-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="d1beb-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="d1beb-156">Es wird versucht, Verweise auf AllJoyn Adapter Projekte hinzufügen kann zu Fehlern führen, wenn Sie bestimmte SDK-Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1beb-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="d1beb-157">Um diese Fehler zu beheben, ändern Visual Studio-Zielplattform entsprechend die aktuelle SDK-Version, und Laden Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="d1beb-158">WiFi Direct-Einschränkungen für Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="d1beb-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="d1beb-159">Die Windows 10 IoT Core, die Gerät das verbindende Gerät – werden muss sie als Werbung Gerät mit einem anderen Gerät Initiieren der Verbindung funktioniert nicht.</span><span class="sxs-lookup"><span data-stu-id="d1beb-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="d1beb-160">Erweiterte Kopplung muss verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d1beb-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="d1beb-161">Die Beispiel-app veranschaulicht, wie die erweiterte ereignispaarbildung-APIs zu verwenden, um die Geräte vor dem Herstellen einer Verbindung zu koppeln.</span><span class="sxs-lookup"><span data-stu-id="d1beb-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="d1beb-162">Nicht alle Drahtlosadapter unterstützen WiFi Direct.</span><span class="sxs-lookup"><span data-stu-id="d1beb-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="d1beb-163">Wir getestet und überprüft, die "Realtek RTL8188EU w-Lan 802. 11n USB 2.0 Network Adapter" funktioniert, aber anderen Adaptern, die möglicherweise nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="d1beb-164">Nicht standardmäßiges Laufwerk-Modus (3890679)</span><span class="sxs-lookup"><span data-stu-id="d1beb-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="d1beb-165">Auf Raspberry Pi und Dragonboard kann der Wechsel von einem Nichtstandard-Laufwerk-Modus zu einem anderen Nichtstandard-Laufwerk-Modus eine Störung auf den GPIO-Pin generieren.</span><span class="sxs-lookup"><span data-stu-id="d1beb-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="d1beb-166">Zur Umgehung dieses Problem, Laufwerk-Modus einmal am Anfang der Anwendung festlegen.</span><span class="sxs-lookup"><span data-stu-id="d1beb-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="d1beb-167">Anwendung wird bereits ausgeführt (1244550)</span><span class="sxs-lookup"><span data-stu-id="d1beb-167">Application already running (1244550)</span></span> 
<span data-ttu-id="d1beb-168">Die Standard-Start-app kann mit sich selbst in Konflikt stehen, wenn sie auch in Visual Studio bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d1beb-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="d1beb-169">PROBLEMUMGEHUNG Ändern Sie die Standard-Start-app zu einer Anwendung, die andere als die Sie bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="d1beb-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="d1beb-170">BackgroundMediaPlayer.MessageReceivedFromForeground (2199869) stürzt möglicherweise ab.</span><span class="sxs-lookup"><span data-stu-id="d1beb-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="d1beb-171">Die folgende Codezeile stürzt möglicherweise ab:</span><span class="sxs-lookup"><span data-stu-id="d1beb-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="d1beb-172">Um den Absturz zu verhindern, fügen Sie folgenden Code, sodass er zuerst ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="d1beb-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="d1beb-173">Azure Active Directory-Authentifizierungsunterstützung (4266261)</span><span class="sxs-lookup"><span data-stu-id="d1beb-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="d1beb-174">Die Azure Active Directory-Authentifizierungsbibliothek funktioniert nicht unter Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d1beb-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="d1beb-175">Shell-Verwaltung von Anwendungsabstürzen</span><span class="sxs-lookup"><span data-stu-id="d1beb-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="d1beb-176">IoT Core-Shell-Infrastruktur überwacht APPX-Type-Anwendungen, die auf dem Gerät für Abstürze und Anwendungen neu gestartet wird, wenn Abstürze auftreten.</span><span class="sxs-lookup"><span data-stu-id="d1beb-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="d1beb-177">Wenn die neu gestarteten Anwendungen abstürzt weiterhin, wird die Shell nutzen eine Failfast – einen kritischen Systemprozess, der einem schwerwiegenden Fehler verursacht und neu starten, Versuch zum Wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="d1beb-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="d1beb-178">Vergleichbare Logik und Verarbeitung werden Tasks und Foreground-Anwendungen in einer Konfiguration mit Multi-Monitor im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="d1beb-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="d1beb-179">Absturz Fehlerbehandlung und Wiederholungslogik Logik wird unten erfasst:</span><span class="sxs-lookup"><span data-stu-id="d1beb-179">Crash handling and retry logic is captured below:</span></span>

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
  Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
  Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
  Dword:"MaxFailureCount". Default is 10 
  DWord:"FallbackExponentNumerator", default is 31. 
  Dword:"FallbackExponentDenominator", default is 20 
  
  
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
When app crash is detected: 
    if time_since_last_crash > failureresetinterval then crashes_seen = 1 
    else ++crashes_seen; 
  
if crashes_seen > MaxFailureCount then __failfast; 
  
else  
  
delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

<span data-ttu-id="d1beb-180">Warten Sie, bis die Verzögerung, und starten Sie die app erneut.</span><span class="sxs-lookup"><span data-stu-id="d1beb-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="d1beb-181">Dragonboard SPI ausgeführt wird, mit 4,8 Mhz</span><span class="sxs-lookup"><span data-stu-id="d1beb-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="d1beb-182">Die SPI auf die Dragonboard ignoriert die angeforderten Geschwindigkeit und mit 4,8 Mhz immer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="d1beb-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="d1beb-183">Dragonboard verbundenen Standbymodus</span><span class="sxs-lookup"><span data-stu-id="d1beb-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="d1beb-184">Verbundenen Standby ist nicht auf die Qualcomm Dragonboard standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="d1beb-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="d1beb-185">Zum Aktivieren von verbundenen Standbymodus auf DragonBoard muss der folgenden Registrierungsschlüssel auf "1" festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="d1beb-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="d1beb-186">Zeitsynchronisierung</span><span class="sxs-lookup"><span data-stu-id="d1beb-186">Time synchronization</span></span>
<span data-ttu-id="d1beb-187">Wenn zeitsynchronisierung tritt ein Fehler oder ein Timeout erfolgt dies möglicherweise aufgrund von nicht erreichbar ist oder ein entfernten Zeitserver Folgendes können ausgeführt werden, um zusätzliche oder der lokale Server hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d1beb-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="d1beb-188">Über die Befehlszeile auf dem Gerät (z. b.</span><span class="sxs-lookup"><span data-stu-id="d1beb-188">From a command line on the device (eg.</span></span> <span data-ttu-id="d1beb-189">SSH, Powershell).</span><span class="sxs-lookup"><span data-stu-id="d1beb-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="d1beb-190">Sie können auch diese Erweiterungen in die Registrierung über ein Skript starten, oder ein Konfigurationspaket für die benutzerdefinierte Laufzeit, die als Teil des Prozesses der imageerstellung bei Bedarf enthalten.</span><span class="sxs-lookup"><span data-stu-id="d1beb-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="d1beb-191">Starten Sie den FTP-Server</span><span class="sxs-lookup"><span data-stu-id="d1beb-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="d1beb-192">Einmalig - melden Sie sich mit SSH\PS, und führen Sie diesen Befehl aus, um FTP zu starten:</span><span class="sxs-lookup"><span data-stu-id="d1beb-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="d1beb-193">Um auf jedem Neustart auszuführen, sollten Benutzer erstellen Sie eine Aufgabe für Scheduler - melden Sie sich mit SSH\PS und erstellen Sie einen Task Scheduler:</span><span class="sxs-lookup"><span data-stu-id="d1beb-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="d1beb-194">Partition größenanforderungen für Update</span><span class="sxs-lookup"><span data-stu-id="d1beb-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="d1beb-195">Sicherstellen Sie, dass Datenpartition genügend Speicherplatz für die Update-Funktionalität verwaltet.</span><span class="sxs-lookup"><span data-stu-id="d1beb-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="d1beb-196">  Es wird empfohlen, 1GB kostenlos für vollständige Update-Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="d1beb-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="d1beb-197"> Wenn Datenpartition nicht genügend Speicherplatz verfügt, schlägt die Updates in der Phase der Installation fehl.</span><span class="sxs-lookup"><span data-stu-id="d1beb-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="d1beb-198">PowerShell-protokollgenerierung unter IoT Core</span><span class="sxs-lookup"><span data-stu-id="d1beb-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="d1beb-199">PowerShell unter Iot Core möglicherweise Protokolldateien in der Standardeinstellung, die viel Raum einnimmt, auf das Dateisystem generieren.</span><span class="sxs-lookup"><span data-stu-id="d1beb-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="d1beb-200">Auch wenn die Größe der Log-Dateien beschränkt sind, kann es dauern Speicherplatz, was ggf. zu wenig Speicherplatz Situation, unter anderem bei der Aktualisierung Fehler führen kann.</span><span class="sxs-lookup"><span data-stu-id="d1beb-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="d1beb-201">Ereignis der EVTX-Protokolldateien haben eine vordefinierte maximale Größe von 20 MB.</span><span class="sxs-lookup"><span data-stu-id="d1beb-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="d1beb-202">Sie können die Dateien, um eine andere maximale Größe über Registrierung haben einzeln begrenzen.</span><span class="sxs-lookup"><span data-stu-id="d1beb-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="d1beb-203">Geben Sie beispielsweise Folgendes ein, um security.evtx bei maximalen Größe von 10 MB zu halten:</span><span class="sxs-lookup"><span data-stu-id="d1beb-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="d1beb-204">Schtasks limitation</span><span class="sxs-lookup"><span data-stu-id="d1beb-204">Schtasks limitation</span></span>  
<span data-ttu-id="d1beb-205">"SCHTASKS" unterstützt nicht/XML-Schalter verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1beb-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="d1beb-206">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1beb-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="d1beb-207">Dies wird unter IoT Core fehl.</span><span class="sxs-lookup"><span data-stu-id="d1beb-207">This will fail on IoT Core.</span></span> <span data-ttu-id="d1beb-208">Ausführen des Befehls wird den Fehler generiert: FEHLER: Die angegebene Prozedur konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d1beb-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
