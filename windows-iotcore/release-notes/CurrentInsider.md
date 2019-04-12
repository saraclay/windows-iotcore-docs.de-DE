---
title: Anmerkungen zu dieser Version erstellen 17744
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/24/2018
ms.topic: article
description: Lesen Sie aus, und erfahren Sie mehr über die Neuigkeiten in Windows-Insider erstellen Anzahl 17744.
keywords: Windows Iot, Windows-Insider-Anmerkungen zu dieser Version
ms.openlocfilehash: 3f78aa22f6edd4692d1e7956edc30856eeed2e7c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512785"
---
# <a name="release-notes-for-build-17744"></a><span data-ttu-id="87f5f-104">Anmerkungen zu dieser Version erstellen 17744</span><span class="sxs-lookup"><span data-stu-id="87f5f-104">Release Notes for Build 17744</span></span>
_<span data-ttu-id="87f5f-105">Buildnummer 17744.</span><span class="sxs-lookup"><span data-stu-id="87f5f-105">Build Number 17744.</span></span> <span data-ttu-id="87f5f-106">August 2018.</span><span class="sxs-lookup"><span data-stu-id="87f5f-106">August 2018.</span></span>_

<span data-ttu-id="87f5f-107">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="87f5f-107">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="87f5f-108">Alle Rechte vorbehalten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-108">All rights reserved.</span></span>

<span data-ttu-id="87f5f-109">Dieses Dokument enthält aktuelle oder andere Informationen, die die Dokumentation zu den Windows 10 IoT Core zu ergänzen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-109">This document provides late-breaking or other information that supplements the documentation included with the Windows 10 IoT Core.</span></span>

<span data-ttu-id="87f5f-110">Vielen Dank für das Herunterladen von Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="87f5f-110">Thank you for downloading Windows 10 IoT Core.</span></span> <span data-ttu-id="87f5f-111">Windows 10 IoT Core ist die Version von Windows 10 für die Entwicklung von eingebetteten oder dedizierten Geräten und die Auswahl für die Maker-Community vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-111">Windows 10 IoT Core is the version of Windows 10 intended for development of embedded or dedicated purpose devices and the choice for the Maker community.</span></span> <span data-ttu-id="87f5f-112">Die Pakete in dieser Version enthalten Tools und Inhalten, die zum Installieren von Windows 10 IoT Core auf Minnowboard Max-Plattform basierend auf Intel Atom Einzelprozessorcomputer, Raspberry Pi 2/3-basierend auf Broadcom 2836/2837 und Dragonboard 410 c basierend auf Qualcomm Snapdragon 400-Serie Prozessoren.</span><span class="sxs-lookup"><span data-stu-id="87f5f-112">The packages within this release contain tools and content needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processers, Raspberry Pi 2/3 based on Broadcom 2836/2837, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>


## <a name="privacy-statement"></a><span data-ttu-id="87f5f-113">Datenschutzbestimmungen</span><span class="sxs-lookup"><span data-stu-id="87f5f-113">Privacy Statement</span></span>

<span data-ttu-id="87f5f-114">Die Datenschutzbestimmungen für diese Version des Windows-Betriebssystems angezeigt werden kann [hier](http://go.microsoft.com/fwlink/?LinkId=506737).</span><span class="sxs-lookup"><span data-stu-id="87f5f-114">The privacy statement for this version of the Windows operating system can be viewed [here](http://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

<span data-ttu-id="87f5f-115">Sie können verknüpfte Bedingungen überprüfen, indem Sie dem Forwardlink in das Browserfenster einfügen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-115">You can review linked terms by pasting the forward link into your browser window.</span></span>

## <a name="whats-new-in-this-build"></a><span data-ttu-id="87f5f-116">Was ist neu in diesem Build:</span><span class="sxs-lookup"><span data-stu-id="87f5f-116">What's new in this build:</span></span> 
* <span data-ttu-id="87f5f-117">Allgemeine Fehlerbehebungen</span><span class="sxs-lookup"><span data-stu-id="87f5f-117">General bug fixes</span></span> 


## <a name="additional-information"></a><span data-ttu-id="87f5f-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="87f5f-118">Additional Information</span></span>
* <span data-ttu-id="87f5f-119">Die für das Abbild Dragon Board verwendete BSP-Version ist 2118.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="87f5f-119">The BSP version used for our Dragon Board image is 2118.0.0.0.</span></span> 


## <a name="known-issues-in-this-build"></a><span data-ttu-id="87f5f-120">Bekannte Probleme im Build:</span><span class="sxs-lookup"><span data-stu-id="87f5f-120">Known issues in this build:</span></span>
* <span data-ttu-id="87f5f-121">F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter IoT Core.</span><span class="sxs-lookup"><span data-stu-id="87f5f-121">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span>
* <span data-ttu-id="87f5f-122">Geräte, die über NOOBS installiert wurden, können nicht das Bcdedit-Tool zum Aktivieren des Kernel-Debuggers ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-122">Devices that were installed via NOOBS cannot run the bcdedit tool to enable the kernel debugger.</span></span> <span data-ttu-id="87f5f-123">Dies kann erreicht werden, mit der folgenden problemumgehung: \*\* einbinden die SD-Karte auf Ihrem PC \*\* finden Sie die Datenträgerpartition EFIESP Zahl mit Diskpart oder die Datenträgerverwaltung (z. B. ist "M:") \*\* führen Sie den Befehl "Bcdedit/store M:\EFI\Microsoft\boot\bcd/Set {Default} debug ' Ja'" \*\*  Aufheben der Bereitstellung der SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="87f5f-123">This can be achieved with the following workaround: \*\*  Mount the SD card on your PC \*\*  Find the EFIESP drive partition number with diskpart or Disk Management (say it’s “M:”) \*\*  Run the command “bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug yes” \*\*  Unmount the SD card.</span></span>
<span data-ttu-id="87f5f-124">Sie sollten jetzt auf den Debugger wie gewohnt eine Verbindung herstellen können</span><span class="sxs-lookup"><span data-stu-id="87f5f-124">\*\*  You should now be able to connect the debugger as usual</span></span>
* <span data-ttu-id="87f5f-125">PSSession unterbricht gelegentlich beim Senden von Befehlen auf IoT-Geräten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-125">On occasion, PSSession will break when sending commands to IoT devices.</span></span>
* <span data-ttu-id="87f5f-126">RPi3 wird nicht koppeln, BT + BTLE integrieren Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="87f5f-126">RPi3 will not pair BT + BTLE with onboard Bluetooth.</span></span>
* <span data-ttu-id="87f5f-127">Keine Verbindung zum Internet über WLAN-Verbindung mit SoftAp von Up2.</span><span class="sxs-lookup"><span data-stu-id="87f5f-127">Unable to connect to internet through WIFI connection with SoftAp of Up2.</span></span>
* <span data-ttu-id="87f5f-128">UWF gelegentlich tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="87f5f-128">UWF is failing intermittently.</span></span>
* <span data-ttu-id="87f5f-129">Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="87f5f-129">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="87f5f-130">Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.</span><span class="sxs-lookup"><span data-stu-id="87f5f-130">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>


## <a name="iot-core-general-known-issues-and-work-arounds"></a><span data-ttu-id="87f5f-131">IoT Core allgemein bekannte Probleme und problemumgehungen für Arbeitsaufgaben</span><span class="sxs-lookup"><span data-stu-id="87f5f-131">IoT Core general known issues and work arounds</span></span>

### <a name="for-raspberry-pi"></a><span data-ttu-id="87f5f-132">Für Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="87f5f-132">For Raspberry Pi</span></span>

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="87f5f-133">Raspberry Pi-Bildschirmauflösung Monitor wird die Verbindung getrennt</span><span class="sxs-lookup"><span data-stu-id="87f5f-133">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="87f5f-134">Der Raspberry Pi kann die Auflösung nicht verwalten, Monitor wird die Verbindung getrennt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-134">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="87f5f-135">Die EDID des Monitors wird verwendet, um die Auflösung des Systems festgelegt, wenn ein solches angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="87f5f-135">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="87f5f-136">Wenn getrennt, wird standardmäßig die Raspberry Pi-Firmware, was in der "config.txt" im Stammverzeichnis der SD-Karte ist.</span><span class="sxs-lookup"><span data-stu-id="87f5f-136">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="87f5f-137">Raspberry Pi-Video-Leistung</span><span class="sxs-lookup"><span data-stu-id="87f5f-137">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="87f5f-138">Videowiedergabe Leistung auf dem Raspberry Pi-Plattform wird nicht optimiert.</span><span class="sxs-lookup"><span data-stu-id="87f5f-138">Video playback performance on the Raspberry Pi platform is not optimized.</span></span><span data-ttu-id="87f5f-139">  Animiert die Benutzer, die Elemente, einschließlich XAML-basierte Dropdownmenüs weniger als eine optimale Leistung aufweisen können.</span><span class="sxs-lookup"><span data-stu-id="87f5f-139">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 
 
#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="87f5f-140">Kameraunterstützung Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="87f5f-140">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="87f5f-141">Unterstützung für Peripheriegeräte Kamera ist eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-141">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="87f5f-142">Das PiCam-Gerät direkt mit der integrierten Kamera-Bus verbunden wird nicht unterstützt, aufgrund von Einschränkungen in der Plattform, moderne D3D-USB-Webcams erzeugen-Datenströme zu unterstützen, die auf dem USB-Hostcontroller äußerst anspruchsvollen sind.</span><span class="sxs-lookup"><span data-stu-id="87f5f-142">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="87f5f-143">  Selbst bei Verwendung mit niedriger Auflösung Einstellungen Webcams erfordert zusätzliche USB-Optimierung und spezielle Logik des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="87f5f-143">  Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span> 

#### <a name="raspberry-pi3-bluetooth-support"></a><span data-ttu-id="87f5f-144">Raspberry Pi3 Bluetooth-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="87f5f-144">Raspberry Pi3 Bluetooth support</span></span> 
<span data-ttu-id="87f5f-145">Der Raspberry Pi3 integrierte Bluetooth-Treiber unterstützt nur Geräte mit geringer Bandbreite.</span><span class="sxs-lookup"><span data-stu-id="87f5f-145">The Raspberry Pi3 built-in Bluetooth driver only supports low bandwidth devices.</span></span> 

#### <a name="serial-port-usage-and-access-on-rpi2"></a><span data-ttu-id="87f5f-146">Serieller Anschluss-Nutzung und den Zugriff auf RPi2</span><span class="sxs-lookup"><span data-stu-id="87f5f-146">Serial Port Usage and Access on RPi2</span></span> 
<span data-ttu-id="87f5f-147">Raspberry Pi 2 unterstützt die seriellen Transport für die Kommunikation über die PL011 UART.</span><span class="sxs-lookup"><span data-stu-id="87f5f-147">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="87f5f-148">  Dies wird im Kernel Debugszenarien standardmäßig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-148">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="87f5f-149">  Eine Anwendung oder einen Gerätetreiber können die PL011 UART zum Senden und Empfangen von Daten mit dem PL011 Gerätetreiber, die durch das Deaktivieren des Debuggers mit den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="87f5f-149">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:</span></span>

```
bcdedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a><span data-ttu-id="87f5f-150">Datenhaltepunkte wurden auf dem Raspberry Pi2 deaktiviert</span><span class="sxs-lookup"><span data-stu-id="87f5f-150">Data breakpoints have been disabled on the Raspberry Pi2</span></span>
<span data-ttu-id="87f5f-151">Keine problemumgehung zu diesem Zeitpunkt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-151">No workaround at this time.</span></span>

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a><span data-ttu-id="87f5f-152">Deaktivieren die Onboarding-Adapter für Raspberry Pi 3</span><span class="sxs-lookup"><span data-stu-id="87f5f-152">Disabling the onboard adapters for Raspberry Pi 3</span></span>
<span data-ttu-id="87f5f-153">Der Raspberry Pi 3 verfügt über integrierte Bluetooth der deaktiviert werden muss, um einen anderen Dongle zu verwenden, um beim Onboarding Bluetooth deaktivieren, öffnen Sie eine Telnet/ssh-Sitzung, und führen Sie:</span><span class="sxs-lookup"><span data-stu-id="87f5f-153">The Raspberry Pi 3 has onboard Bluetooth which must be disabled to use a different dongle to disable to onboard Bluetooth, open a telnet/ssh session and run:</span></span> 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

<span data-ttu-id="87f5f-154">Sie können die WiFi mit dem folgenden Befehl deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="87f5f-154">You may disable WiFi with the following command:</span></span> 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragonboard"></a><span data-ttu-id="87f5f-155">Für DragonBoard</span><span class="sxs-lookup"><span data-stu-id="87f5f-155">For DragonBoard</span></span>

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="87f5f-156">Dragonboard 410c Herunterfahren</span><span class="sxs-lookup"><span data-stu-id="87f5f-156">Dragonboard 410c Shutdown</span></span>
<span data-ttu-id="87f5f-157">Befehl zum Herunterfahren eines wird für das Board auf die DragonBoard nicht ausschalten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-157">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="87f5f-158">Das System wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="87f5f-158">The system will restart.</span></span> <span data-ttu-id="87f5f-159">Melden Sie schalten Sie das Board von abschalten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-159">Please power off the board by disconnecting the power.</span></span>

#### <a name="dragonboard-and-windbg"></a><span data-ttu-id="87f5f-160">DragonBoard und windbg</span><span class="sxs-lookup"><span data-stu-id="87f5f-160">DragonBoard and windbg</span></span>
<span data-ttu-id="87f5f-161">Die integrierte GPIO/I2C/SPI/UART-Treiber werden beim Verbinden mit der DragonBoard mit Windbg deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="87f5f-161">The GPIO/I2C/SPI/UART drivers will be disabled when connecting to the DragonBoard with windbg.</span></span>

#### <a name="dragonboard-headset--microphone-jack"></a><span data-ttu-id="87f5f-162">DragonBoard Kopfhörer & Mikrofon jack</span><span class="sxs-lookup"><span data-stu-id="87f5f-162">DragonBoard headset & microphone jack</span></span>
<span data-ttu-id="87f5f-163">Die Dragonboard BSP Treiber für die Kopfhörer Jack und Mikrofon Jack, aber nicht eine der folgenden Jacks hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-163">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="87f5f-164">DragonBoard SPI ausgeführt wird, mit 4,8 Mhz</span><span class="sxs-lookup"><span data-stu-id="87f5f-164">DragonBoard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="87f5f-165">Die SPI auf die Dragonboard ignoriert die angeforderten Geschwindigkeit und mit 4,8 Mhz immer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-165">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="87f5f-166">DragonBoard verbundenen Standbymodus</span><span class="sxs-lookup"><span data-stu-id="87f5f-166">DragonBoard Connected Standby</span></span> 
<span data-ttu-id="87f5f-167">Verbundenen Standby ist nicht auf die Qualcomm Dragonboard standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="87f5f-167">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="87f5f-168">Zum Aktivieren von verbundenen Standbymodus auf DragonBoard muss der folgenden Registrierungsschlüssel auf "1" festgelegt werden:</span><span class="sxs-lookup"><span data-stu-id="87f5f-168">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”:</span></span>

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> <span data-ttu-id="87f5f-169">Nicht alle Plattformen ist die Unterstützung für den verbundenen Standbymodus.</span><span class="sxs-lookup"><span data-stu-id="87f5f-169">Not all platforms have support for Connected Standby.</span></span>  <span data-ttu-id="87f5f-170">Dies funktioniert möglicherweise nicht auf allen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-170">This may not work on all platforms.</span></span>    


### <a name="for-minnowboard"></a><span data-ttu-id="87f5f-171">Für MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="87f5f-171">For MinnowBoard</span></span>
#### <a name="minnowboard-max-boot-and-firmware-update"></a><span data-ttu-id="87f5f-172">Minnowboard Max Boot und Firmware-Update</span><span class="sxs-lookup"><span data-stu-id="87f5f-172">Minnowboard Max Boot and Firmware Update</span></span> 
<span data-ttu-id="87f5f-173">Das MinnowBoard Max werden nicht gestartet werden, es sei denn, die Firmware Version.092 ist oder höher.</span><span class="sxs-lookup"><span data-stu-id="87f5f-173">The MinnowBoard Max will not boot unless the firmware is version .092 or later.</span></span> <span data-ttu-id="87f5f-174">Die empfohlene Mindestversion der Firmware ist "MinnowBoard MAX 0.92 32-Bit".</span><span class="sxs-lookup"><span data-stu-id="87f5f-174">The minimum recommended version of the firmware is “MinnowBoard MAX 0.92 32-Bit”.</span></span> <span data-ttu-id="87f5f-175">Firmwareupdates werden heruntergeladen von [hier](http://go.microsoft.com/fwlink/?LinkId=708613).</span><span class="sxs-lookup"><span data-stu-id="87f5f-175">Firmware updates can be downloaded from [here](http://go.microsoft.com/fwlink/?LinkId=708613).</span></span>

#### <a name="minnow-board-peripheral-support"></a><span data-ttu-id="87f5f-176">Minnow Board-Unterstützung für Peripheriegeräte</span><span class="sxs-lookup"><span data-stu-id="87f5f-176">Minnow Board Peripheral Support</span></span>
<span data-ttu-id="87f5f-177">Das Windows 10 IoT Core-Image in dieser Dropdownliste enthalten unterstützt die Peripheriegeräten, die verfügbar gemacht werden, auf dem Board MinnowBoard MAX.</span><span class="sxs-lookup"><span data-stu-id="87f5f-177">The Windows 10 IoT Core image included in this drop supports the peripherals that are exposed on the MinnowBoard MAX board.</span></span> <span data-ttu-id="87f5f-178">Anschließend Intel&reg; bieten Unterstützung für den vollständigen Featuresatz Baytrail Prozessoren der Intel-Celeron einschließlich&trade; Prozessoren J1900/N2930/N2807 und Intel Atom&trade; Prozessoren E38XX.</span><span class="sxs-lookup"><span data-stu-id="87f5f-178">Subsequently, Intel&reg; will provide support of the full feature set of the Baytrail processors including the Intel Celeron&trade; Processors J1900/N2930/N2807 and Intel Atom&trade; Processors E38XX.</span></span>


### <a name="for-all-platforms"></a><span data-ttu-id="87f5f-179">Für alle Plattformen</span><span class="sxs-lookup"><span data-stu-id="87f5f-179">For All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="87f5f-180">Mauszeiger verschwindet während des Debuggens</span><span class="sxs-lookup"><span data-stu-id="87f5f-180">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="87f5f-181">Klicken Sie in einigen Fällen der Mauszeiger nach dem Bereitstellen oder Debuggen von apps mit Visual Studio nicht sichtbar ist, der Mauszeiger sollte wieder angezeigt, wenn Sie den Fokus mit der Tastatur (Registerkarte) ändern.</span><span class="sxs-lookup"><span data-stu-id="87f5f-181">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab).</span></span>


#### <a name="server-applications-with-softap"></a><span data-ttu-id="87f5f-182">Server-Anwendungen mit SoftAP</span><span class="sxs-lookup"><span data-stu-id="87f5f-182">Server Applications with SoftAP</span></span>
<span data-ttu-id="87f5f-183">Wenn die SoftAP Clients nicht den Zugriff auf Inhalte von UAP-apps verfügbar gemacht werden können.</span><span class="sxs-lookup"><span data-stu-id="87f5f-183">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span>  
<span data-ttu-id="87f5f-184">Die folgenden Änderungen müssen über die Konsole auf dem Gerät vorgenommen werden, um über SoftAP UAP-Anwendungen verfügbar zu machen:</span><span class="sxs-lookup"><span data-stu-id="87f5f-184">To expose UAP applications via SoftAP the following changes must be made from the console on the device:</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
```

<span data-ttu-id="87f5f-185">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="87f5f-185">For example:</span></span>  
```
checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym
```
<span data-ttu-id="87f5f-186">Neustart</span><span class="sxs-lookup"><span data-stu-id="87f5f-186">Reboot</span></span> 


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="87f5f-187">Sensor-Treiber-Konflikt im vorgefertigten FFUs</span><span class="sxs-lookup"><span data-stu-id="87f5f-187">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="87f5f-188">In der bereitgestellten FFUs vorliegt ein Sensor-Treiber-Konflikt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-188">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="87f5f-189">Das Remote-Sensor-Framework werden die Treiber für Kompass, Magnetometer, Beschleunigungsmesser und Gyrometer installiert.</span><span class="sxs-lookup"><span data-stu-id="87f5f-189">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="87f5f-190">Die UWP-APIs für den Zugriff auf diese aus einer Anwendung gehen davon aus, nur 1 installiert ist.</span><span class="sxs-lookup"><span data-stu-id="87f5f-190">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="87f5f-191">Wenn Sie einen Treiber für ein physisch angeschlossenen Gerät entwickeln, vorausgesetzt die remote-Treiber auf der Microsoft FFUs in Konflikt steht.</span><span class="sxs-lookup"><span data-stu-id="87f5f-191">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>

<span data-ttu-id="87f5f-192">Lösung: Der in Konflikt stehenden Treiber entfernt werden kann, durch die Verbindung mit dem Gerät über SSH oder Powershell, und verwenden das Tool devcon.exe Entfernen des remote-Sensor-Treibers durch Eingabe "devcon.exe entfernen @" ROOT\REMOTESENSORDRIVER \*".</span><span class="sxs-lookup"><span data-stu-id="87f5f-192">Resolution: The conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="87f5f-193">Der remote-Sensor-Treiber hat keine Auswirkungen auf die OEM-Abhängige FFUs erstellt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-193">The remote sensor driver does not affect OEM created FFUs.</span></span>


#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="87f5f-194">Standard-Administratorbenutzernamen und das Kennwort</span><span class="sxs-lookup"><span data-stu-id="87f5f-194">Default Administrator User Name and Password</span></span>
<span data-ttu-id="87f5f-195">Die Standard-Administratorbenutzernamen und das Kennwort sind fest codiert, in das Windows 10 IoT Core-Image.</span><span class="sxs-lookup"><span data-stu-id="87f5f-195">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="87f5f-196">Dies ist ein Sicherheitsrisiko für das Gerät, und es nicht verfügbar gemacht werden, eine Internetverbindung geöffnet, bis das Kennwort geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="87f5f-196">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span>

#### <a name="volume-controls"></a><span data-ttu-id="87f5f-197">Lautstärkeregler</span><span class="sxs-lookup"><span data-stu-id="87f5f-197">Volume Controls</span></span>
<span data-ttu-id="87f5f-198">Hardware-Volume-Steuerelemente für USB-Mikrofone und Lautsprecher, die auf Windows-System so ändern Sie den Systemdatenträger abhängig sind, werden auf Windows 10 IoT Core derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-198">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

#### <a name="usb-keyboards"></a><span data-ttu-id="87f5f-199">USB-Tastatur</span><span class="sxs-lookup"><span data-stu-id="87f5f-199">USB Keyboards</span></span>  
<span data-ttu-id="87f5f-200">Einige USB-Tastaturen und Mäusen funktioniert möglicherweise nicht unter IoT Core.</span><span class="sxs-lookup"><span data-stu-id="87f5f-200">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="87f5f-201">Verwenden einer anderen Tastatur oder Maus.</span><span class="sxs-lookup"><span data-stu-id="87f5f-201">Use a different keyboard or mouse.</span></span> <span data-ttu-id="87f5f-202">Eine Liste der überprüften Peripheriegeräte befinden sich die [Dokumentation](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist).</span><span class="sxs-lookup"><span data-stu-id="87f5f-202">A list of validated peripheral devices can be found in the [documentation here](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist).</span></span>


#### <a name="screen-orientation"></a><span data-ttu-id="87f5f-203">Bildschirmausrichtung</span><span class="sxs-lookup"><span data-stu-id="87f5f-203">Screen Orientation</span></span>
<span data-ttu-id="87f5f-204">Die Ausrichtung auf "Hochformat" festlegen kann nicht in einer universellen App berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="87f5f-204">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="87f5f-205">Verweisen Netzwerkkarten mit AllJoyn-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="87f5f-205">Referencing Adapters with AllJoyn Templates</span></span>
<span data-ttu-id="87f5f-206">Es wird versucht, Verweise auf AllJoyn Adapter Projekte hinzufügen kann zu Fehlern führen, wenn Sie bestimmte SDK-Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="87f5f-206">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="87f5f-207">Um diese Fehler zu beheben, ändern Visual Studio-Zielplattform entsprechend die aktuelle SDK-Version, und Laden Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-207">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>

#### <a name="wifi-direct-limitations-on-iotcore"></a><span data-ttu-id="87f5f-208">WiFi Direct-Einschränkungen für IoTCore</span><span class="sxs-lookup"><span data-stu-id="87f5f-208">WiFi Direct limitations on IoTCore</span></span>
* <span data-ttu-id="87f5f-209">Das IoTCore-Gerät muss das verbindende Gerät zu sein – es funktioniert nicht als Ankündigung Gerät mit einem anderen Gerät die Verbindung initiiert.</span><span class="sxs-lookup"><span data-stu-id="87f5f-209">The IoTCore device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
* <span data-ttu-id="87f5f-210">Erweiterte Kopplung muss verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="87f5f-210">Advanced pairing must be used.</span></span>  <span data-ttu-id="87f5f-211">Die Beispiel-app veranschaulicht, wie die erweiterte ereignispaarbildung-APIs zu verwenden, um die Geräte vor dem Herstellen einer Verbindung zu koppeln.</span><span class="sxs-lookup"><span data-stu-id="87f5f-211">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
* <span data-ttu-id="87f5f-212">Nicht alle Drahtlosadapter unterstützen WiFi Direct.</span><span class="sxs-lookup"><span data-stu-id="87f5f-212">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="87f5f-213">Wir getestet und überprüft, die "Realtek RTL8188EU w-Lan 802. 11n USB 2.0 Network Adapter" funktioniert, aber anderen Adaptern, die möglicherweise nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-213">We have tested and validated that the “Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter” works, but other adapters may not be supported.</span></span> 


#### <a name="non-default-drive-mode"></a><span data-ttu-id="87f5f-214">Nicht standardmäßiges Laufwerk-Modus</span><span class="sxs-lookup"><span data-stu-id="87f5f-214">Non-default drive mode</span></span>
<span data-ttu-id="87f5f-215">Auf Raspberry Pi und Dragonboard kann der Wechsel von einem Nichtstandard-Laufwerk-Modus zu einem anderen Nichtstandard-Laufwerk-Modus eine Störung auf den GPIO-Pin generieren.</span><span class="sxs-lookup"><span data-stu-id="87f5f-215">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="87f5f-216">PROBLEMUMGEHUNG Laufwerkmodus einmal am Anfang der Anwendung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="87f5f-216">WORKAROUND: Set drive mode once at the beginning of the application.</span></span>

#### <a name="application-already-running"></a><span data-ttu-id="87f5f-217">Anwendung wird bereits ausgeführt</span><span class="sxs-lookup"><span data-stu-id="87f5f-217">Application already running</span></span>
<span data-ttu-id="87f5f-218">Die Standard-Start-app kann mit sich selbst in Konflikt stehen, wenn sie auch in Visual Studio bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="87f5f-218">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="87f5f-219">PROBLEMUMGEHUNG Ändern Sie die Standard-Start-app zu einer Anwendung, die andere als die Sie bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-219">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="87f5f-220">BackgroundMediaPlayer.MessageReceivedFromForeground stürzt möglicherweise ab.</span><span class="sxs-lookup"><span data-stu-id="87f5f-220">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>
<span data-ttu-id="87f5f-221">Die folgende Codezeile stürzt möglicherweise ab: “BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;”.</span><span class="sxs-lookup"><span data-stu-id="87f5f-221">The following line of code may crash: “BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;”.</span></span> <span data-ttu-id="87f5f-222">Um den Absturz zu verhindern, fügen Sie folgenden Code, damit es zuerst ausgeführt wird "Var Player BackgroundMediaPlayer.Current; ="</span><span class="sxs-lookup"><span data-stu-id="87f5f-222">To prevent the crash, add this code so that it is executed first “var player = BackgroundMediaPlayer.Current;”</span></span> 

#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="87f5f-223">Unterstützung für Azure Active Directory-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="87f5f-223">Azure Active Directory Authentication Support</span></span>
<span data-ttu-id="87f5f-224">Die Azure Active Directory-Authentifizierungsbibliothek funktioniert nicht unter Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="87f5f-224">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="87f5f-225">Shell-Verwaltung von Anwendungsabstürzen</span><span class="sxs-lookup"><span data-stu-id="87f5f-225">Shell Management of Application Crashes</span></span>
<span data-ttu-id="87f5f-226">IoT Core-Shell-Infrastruktur überwacht APPX-Type-Anwendungen, die auf dem Gerät für Abstürze und Anwendungen neu gestartet wird, wenn Abstürze auftreten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-226">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="87f5f-227">Wenn die neu gestarteten Anwendungen abstürzt weiterhin, wird die Shell nutzen eine __failfast – einen kritischen Systemprozess, der einem schwerwiegenden Fehler verursacht und neu starten, Versuch zum Wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-227">If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="87f5f-228">Vergleichbare Logik und Verarbeitung werden Tasks und Foreground-Anwendungen in einer Konfiguration mit Multi-Monitor im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="87f5f-228">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="87f5f-229">Abstürze behandeln, und wiederholen Sie die Logik ist unten erfasst:</span><span class="sxs-lookup"><span data-stu-id="87f5f-229">Crash handing and retry logic is captured below:</span></span>

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

<span data-ttu-id="87f5f-230">Wenn Abstürze der app erkannt wird:</span><span class="sxs-lookup"><span data-stu-id="87f5f-230">When app crash is detected:</span></span> 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

<span data-ttu-id="87f5f-231">Warten, Verzögerung und starten Sie die app dann erneut.</span><span class="sxs-lookup"><span data-stu-id="87f5f-231">Wait for delay and relaunch app</span></span> 


#### <a name="time-synchronization"></a><span data-ttu-id="87f5f-232">Zeitsynchronisierung</span><span class="sxs-lookup"><span data-stu-id="87f5f-232">Time Synchronization</span></span>  
<span data-ttu-id="87f5f-233">Wenn zeitsynchronisierung tritt ein Fehler oder ein Timeout erfolgt dies möglicherweise aufgrund von nicht erreichbar ist oder ein entfernten Zeitserver Folgendes können ausgeführt werden, um zusätzliche oder der lokale Server hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87f5f-233">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 

1) <span data-ttu-id="87f5f-234">Über die Befehlszeile auf dem Gerät (z. b.</span><span class="sxs-lookup"><span data-stu-id="87f5f-234">From a command line on the device (eg.</span></span> <span data-ttu-id="87f5f-235">SSH, Powershell) w32tm/config / Befehl /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2. etwas anderes,..."</span><span class="sxs-lookup"><span data-stu-id="87f5f-235">SSH, Powershell) w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 

2) <span data-ttu-id="87f5f-236">Sie können auch diese Erweiterungen in die Registrierung über ein Skript starten, oder ein Konfigurationspaket für die benutzerdefinierte Laufzeit, die als Teil des Prozesses der imageerstellung bei Bedarf enthalten.</span><span class="sxs-lookup"><span data-stu-id="87f5f-236">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> <span data-ttu-id="87f5f-237">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="87f5f-237">For more details, see:</span></span> 

* [<span data-ttu-id="87f5f-238">Hinzufügen einer Datei und die Einstellung in der Registrierung zu einem Bild</span><span class="sxs-lookup"><span data-stu-id="87f5f-238">Adding a file and registry setting to an image</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)


### <a name="starting-the-ftp-server"></a><span data-ttu-id="87f5f-239">Starten Sie den FTP-Server</span><span class="sxs-lookup"><span data-stu-id="87f5f-239">Starting the FTP Server</span></span> 
<span data-ttu-id="87f5f-240">Der FTP-Server ausgeführt wird nicht mehr standardmäßig beim Start</span><span class="sxs-lookup"><span data-stu-id="87f5f-240">The FTP Server no longer runs by default at start-up</span></span> 

<span data-ttu-id="87f5f-241">Einmal ausgeführt wird: Melden Sie sich mit SSH\PS, und führen Sie diese Befehl, um FTP zu starten:</span><span class="sxs-lookup"><span data-stu-id="87f5f-241">To run once: Login with SSH\PS and run this command to start FTP:</span></span>  
```
start ftpd.exe 
```

<span data-ttu-id="87f5f-242">Führen Sie auf jedem Start Benutzer sollte eine Scheduler-Aufgabe zu erstellen: Melden Sie sich mit SSH\PS, und erstellen Sie einen Task Scheduler:</span><span class="sxs-lookup"><span data-stu-id="87f5f-242">To run on every boot Users should create a scheduler task: Login with SSH\PS and create a scheduler task:</span></span> 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```
