---
title: Creators Update - Build 15063
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/28/2017
ms.topic: article
description: Lesen Sie aus, und erfahren Sie mehr über die Neuigkeiten in dem Creators Update.
keywords: Anmerkungen zur Version von Windows Iot, Creators Update
ms.openlocfilehash: 73be3f48ce1051d98aa9ebce06dbdc4682fff0fa
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513529"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Creators Update-Anmerkungen zu dieser Version für Windows 10 IoT Core
Buildnummer 15063. April 2017

Windows 10 IoT Core ermöglicht die Entwicklung von eingebetteten oder dedizierte Zwecke Geräte und ist die Wahl für die OEMs und die Entwicklung von Windows-Lösungen für kleine Geräte.

Dieses Dokument enthält Informationen, die anderen Inhalt und die Dokumentation für diese Version von Windows 10 IoT Core ergänzen.

Die Pakete in dieser Version enthalten Tools und Komponenten, die zum Installieren von Windows 10 IoT Core auf Minnowboard Max-Plattform basierend auf Intel Atom Einzelprozessorcomputer, Raspberry Pi 2 basierend auf ARM Cortex-A7 und Dragonboard 410 c basierend auf Qualcomm Snapdragon 400-Serie Prozessoren.   

[Andere Plattformen und Prozessoren](../../learn-about-hardware/SoCsAndCustomBoards.md) möglicherweise von Partnern zur Verfügung.

## <a name="privacy-statement"></a>Datenschutzbestimmungen

Die Datenschutzbestimmungen für diese Version des Windows-Betriebssystems angezeigt werden kann [hier](http://go.microsoft.com/fwlink/?LinkId=506737).

## <a name="whats-new"></a>Neuigkeiten
* Veröffentlichte Windows 10 IoT Core-Version. 
   * Azure Unterstützung für die Geräte-Management - OEMs die Windows IoT Azure-Clientbibliothek können Sie ihre Azure IoT Hub verbundenen Geräte Verwaltungsfunktionen für Geräte hinzugefügt.
   * Zusätzliche Silicon-Unterstützung
      * Unterstützung für Windows 10 IoT Core auf Intel Joule, Intel Pentium N4200, Intel Celeron N3350, bevorstehende Atom X5 E39xx Prozessoren (früher Apollo Lake) überprüft und Raspberry Pi 3 SOMs.
      * Allwinner wurde Unterstützung für ihre Kiefer 64 und Banane-Pi-Geräte, die mit SOC A64 Allwinner aktiviert. 
   * Ermitteln Ihrer Remotegeräte – keine spezielle Software ist erforderlich, um Ihre Geräte zu ermitteln, die mit Ihrem Microsoft Account angemeldet sind.
   * Neue UWP-APIs und Steuerelemente für die schwingungen, Helligkeit, moderne verbundenen Standby, energieverwaltung, Akkukapazität und NFC (HCE). 
   * Neue Bussen und -Funktionen für ARM-PCIe, USB-Funktion-Modus, Wi-Fi Direct und GPIO Interrupt-API gezählt. 
   * Neuer Features für den eingebetteten in zurücksetzen/für die Wiederherstellung auf SOC PWM und automatische USB-Bereitstellung 
   * Verbesserte Tools - Visual Studio Code, IoT-Dashboard und Windows Device Portal Unterstützung neuer Funktionen, Visual Studio 2017.
   * Cortana unter Windows IoT Core – Cortana ist jetzt auf Windows 10 IoT Core verfügbar. Stellen Sie Cortana eine Frage.
   * Verbesserungen der IoT-Dashboard – neue Features und Fehlerkorrekturen für Stabilität
      * Windows Insider Preview-builds für Raspberry Pi und Minnowboard 
      * Windows IoT-Remote-Client mit Gerät verbinden 
      * IPv6-Adressen in der Ermittlung von Geräten 
      * Hochladen von geräteprotokollen beim Senden von feedback
   *  Neuer hoher Genauigkeit GPIO-APIs – neue APIs (Windows.Devices.Gpio.GpioInterruptBuffer) für die genaue und effiziente Messung der Pulse breiten mit GPIO Hardwareinterrupts benötigt hat.  GPIO-Anbietern gehören neue Interrupt-Puffer-Schnittstelle, um hohe Genauigkeit Interrupt zeitliche Steuerung für Anwendungen wie z. B. drehende-Encodern und dem Abstand Messgeräte zu ermöglichen
   * Device Guard für IoT - Geräte, die jetzt vollständig von Generatoren sperren können nach-unten-IoT-Geräte, und profitieren Sie von erweiterten Schutz vor Schadsoftware für neue und unbekannte Malware-Varianten.  Dies kann erfolgen, durch Angeben der Signatur Behörden für zulässige Anwendungen und Treiber, die auf dem Gerät ausgeführt werden soll, während der Ausführung von unbekannten oder nicht vertrauenswürdigen Code zu verhindern.  Dies bedeutet höhere Sicherheit vor Malware und zero-Day-Angriffe. 
   * Andere Updates umfassen Folgendes: 
      * Verbesserte Unterstützung für 
      * Azure-Gateway-SDK-Unterstützung 
      * USB-Laufwerk basierte automatische Bereitstellung 
      * Neuentwurf von Gerät-Portal 
      * 64-Bit-Images unterstützt nun bis zu 16.384 MB Arbeitsspeicher 
      * Ihr Telefon Vibrieren WinRT-APIs 
      * Verbesserte sprachunterstützung 
   * Sonstiges  
      * Um die Standardeinstellungen für die BCD wurde eine Änderung vorgenommen wurde, um zu verhindern, dass Geräte versuchen, in den Wiederherstellungsmodus zu starten, wenn Wiederherstellungsmodus nicht vorhanden ist. 
      * IOT_POWER_SETTINGS umfasst nun powercfg.exe. Dies ist für alle Architekturen (ARM32, X86- und X64) verfügbar. 
      * Applyupdate.exe wurden geändert, dass die Flags Blockrebooton/Blockrebootoff hinzufügen 
      * Die Klassenerweiterungen für Hardware-Benachrichtigung (Hwnclx) und USB-Funktion (Usbfnclx) wurden auf den Standardwert IoT Core-Images hinzugefügt

## <a name="known-issues"></a>Bekannte Probleme

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Raspberry Pi-Bildschirmauflösung Monitor wird die Verbindung getrennt 
Der Raspberry Pi kann die Auflösung nicht verwalten, Monitor wird die Verbindung getrennt. Die EDID des Monitors wird verwendet, um die Auflösung des Systems festgelegt, wenn ein solches angeschlossen ist.  
Wenn getrennt, wird standardmäßig die Raspberry Pi-Firmware, was in der "config.txt" im Stammverzeichnis der SD-Karte ist. 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi-Video-Leistung 
Videowiedergabe Leistung auf dem Raspberry Pi-Plattform wurde nicht optimiert.  Animiert die Benutzer, die Elemente, einschließlich XAML-basierte Dropdownmenüs weniger als eine optimale Leistung aufweisen können. 

#### <a name="raspberry-pi-camera-support"></a>Kameraunterstützung Raspberry Pi 
Windows 10 IoT Core-Unterstützung für Kamera Peripheriegeräten, bei denen mit Raspberry Pi-Geräten ist eingeschränkt. Das PiCam-Gerät direkt mit der integrierten Kamera-Bus verbunden wird derzeit nicht unterstützt, da GPU-Dienste erforderlich ist, die nicht auf dem Raspberry Pi derzeit verfügbar sind, da der DirectX-Treiber nicht implementiert ist. Moderne USB-Webcams erzeugen Datenströme, die auf den USB-Hostcontroller äußerst anspruchsvollen sind.  Selbst bei Verwendung mit niedriger Auflösung Einstellungen Webcams erfordert zusätzliche USB-Optimierung und spezielle Logik des Steuerelements.  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Raspberry Pi 3 Bluetooth-Unterstützung 
Der Raspberry Pi3 integrierte Bluetooth-Treiber unterstützt nur mit geringer Bandbreite von Geräten  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Serieller Anschluss-Nutzung und den Zugriff auf Raspberry Pi 2 
Raspberry Pi 2 unterstützt die seriellen Transport für die Kommunikation über die PL011 UART.  Dies wird im Kernel Debugszenarien standardmäßig festgelegt.  Eine Anwendung oder einen Gerätetreiber können die PL011 UART zum Senden und Empfangen von Daten mit dem PL011 Gerätetreiber, die durch das Deaktivieren des Debuggers mit den folgenden Befehl aus:   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>Dragon-Board 

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c Herunterfahren 
Befehl zum Herunterfahren eines wird für das Board auf die DragonBoard nicht ausschalten. Das System wird neu gestartet. Melden Sie schalten Sie das Board von abschalten. 

#### <a name="dragon-board-headset--microphone-jack"></a>Dragon Board Kopfhörer & Mikrofon jack  
Die Dragonboard BSP Treiber für die Kopfhörer Jack und Mikrofon Jack, aber nicht eine der folgenden Jacks hinzufügen.  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>Dragonboard SPI, die Geschwindigkeit der Sperre wird ausgeführt  
Die SPI auf die Dragonboard ignoriert die angeforderten Geschwindigkeit und mit einer vorkonfigurierten Geschwindigkeit immer ausgeführt.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard verbundenen Standbymodus 
Verbundenen Standby ist nicht auf die Qualcomm Dragonboard standardmäßig aktiviert.  Um verbundenen Standbymodus auf DragonBoard zu aktivieren, muss der folgenden Registrierungsschlüssel auf "1" festgelegt werden 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
Beachten Sie, dass nicht alle Plattformen verfügen über Unterstützung für CS, damit dies möglicherweise nicht auf anderen Plattformen funktionieren.    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>Ihr Telefon Vibrieren API funktioniert möglicherweise nicht auf einigen Plattformen Qualcomm 
Die vorgeschlagene problemumgehung ist den folgenden Registrierungsschlüssel hinzufügen: 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
Bestätigung / Überprüfung auf einem vorhandenen Image Herstellen einer Verbindung mit SSH oder PowerShell, und führen Sie den folgenden Befehl: 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Minnowboard Max-Firmware-Update 
Das MinnowBoard Max werden nicht gestartet werden, es sei denn, die Firmware Version.092 ist oder höher.  
Es gibt möglicherweise Netzwerkkonnektivitätsfehler Max (MBM) Firmwareversion 0.93 MinnowBoard.   Das Problem wurde in der Firmwareversion 0.94 behoben.)  Die empfohlene Mindestversion der Firmware ist "MinnowBoard MAX 0.94 32-Bit". Firmwareupdates werden heruntergeladen von [hier](http://go.microsoft.com/fwlink/?LinkId=708613).
  
 
### <a name="all-platforms"></a>Alle Plattformen 

#### <a name="mouse-pointer-disappears-while-debugging"></a>Mauszeiger verschwindet während des Debuggens 
In einigen Fällen der Mauszeiger nach dem Bereitstellen oder Debuggen von apps mit Visual Studio nicht sichtbar ist, der Mauszeiger sollte wieder angezeigt, wenn Sie den Fokus mit der Tastatur (Registerkarte) ändern  

#### <a name="server-applications-with-softap"></a>Server-Anwendungen mit SoftAP  
Wenn die SoftAP Clients nicht den Zugriff auf Inhalte von UAP-apps verfügbar gemacht werden können.  
Die folgenden Änderungen müssen über die Konsole auf dem Gerät vorgenommen werden, um über SoftAP UAP-Anwendungen verfügbar zu machen:  
<br>
`reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 `
<br>
`checknetisolation loopbackexempt -a -n=<AppID for SoftAP App>`
<br>
`checknetisolation loopbackexempt -a -n=<AppID for Additional App> `
<br>
`For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym`
<br>
`Reboot`

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Sensor-Treiber-Konflikt im vorgefertigten FFUs 
In der bereitgestellten FFUs vorliegt ein Sensor-Treiber-Konflikt. Das Remote-Sensor-Framework werden die Treiber für Kompass, Magnetometer, Beschleunigungsmesser und Gyrometer installiert. Die UWP-APIs für den Zugriff auf diese aus einer Anwendung gehen davon aus, nur 1 installiert ist. Wenn Sie einen Treiber für ein physisch angeschlossenen Gerät entwickeln, vorausgesetzt die remote-Treiber auf der Microsoft FFUs in Konflikt steht.  
Lösung: Der in Konflikt stehenden Treiber entfernt werden kann, durch die Verbindung mit dem Gerät über SSH oder PowerShell, und verwenden das Tool devcon.exe Entfernen des remote-Sensor-Treibers durch Eingabe "devcon.exe entfernen @" ROOT\REMOTESENSORDRIVER *". Der remote-Sensor-Treiber hat keine Auswirkungen auf die OEM-Abhängige FFUs erstellt. 
 
#### <a name="default-administrator-user-name-and-password"></a>Standard-Administratorbenutzernamen und das Kennwort 
Die Standard-Administratorbenutzernamen und das Kennwort sind fest codiert, in das Windows 10 IoT Core-Image. Dies ist ein Sicherheitsrisiko für das Gerät, und es nicht verfügbar gemacht werden, eine Internetverbindung geöffnet, bis das Kennwort geändert wurde. 
 
#### <a name="volume-controls"></a>Lautstärkeregler 
Hardware-Volume-Steuerelemente für USB-Mikrofone und Lautsprecher, die auf Windows-System so ändern Sie den Systemdatenträger abhängig sind, werden auf Windows 10 IoT Core derzeit nicht unterstützt. 
 
#### <a name="usb-keyboards"></a>USB-Tastatur  
Einige USB-Tastaturen und Mäusen funktioniert möglicherweise nicht unter IoT Core. Verwenden einer anderen Tastatur oder Maus. Eine Liste der überprüften Peripheriegeräten finden [hier](../../learn-about-hardware/HardwareCompatList.md).  
 
#### <a name="screen-orientation"></a>Bildschirmausrichtung 
Festlegen der Ausrichtung auf "Hochformat" kann nicht in einer universellen App berücksichtigt 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>Verweisen Netzwerkkarten mit AllJoyn-Vorlagen 
Es wird versucht, Verweise auf AllJoyn Adapter Projekte hinzufügen kann zu Fehlern führen, wenn Sie bestimmte SDK-Versionen verwenden.  Um diese Fehler zu beheben, ändern Visual Studio-Zielplattform entsprechend die aktuelle SDK-Version, und Laden Sie das Projekt. 

#### <a name="non-default-drive-mode"></a>Nicht standardmäßiges Laufwerk-Modus  
Auf Raspberry Pi und Dragonboard kann der Wechsel von einem Nichtstandard-Laufwerk-Modus zu einem anderen Nichtstandard-Laufwerk-Modus eine Störung auf den GPIO-Pin generieren. PROBLEMUMGEHUNG Laufwerkmodus einmal am Anfang der Anwendung festgelegt. 
 
#### <a name="application-already-running"></a>Anwendung wird bereits ausgeführt  
Die Standard-Start-app kann mit sich selbst in Konflikt stehen, wenn sie auch in Visual Studio bereitgestellt wird. PROBLEMUMGEHUNG Ändern Sie die Standard-Start-app zu einer Anwendung, die andere als die Sie bereitstellen möchten. 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground stürzt möglicherweise ab.  
Die folgende Codezeile stürzt möglicherweise ab: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.
<br>
Um den Absturz zu verhindern, fügen Sie folgenden Code, damit es zuerst ausgeführt wird `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Unterstützung für Azure Active Directory-Authentifizierung  
Die Azure Active Directory-Authentifizierungsbibliothek funktioniert nicht unter Windows 10 IoT Core.  
 
#### <a name="shell-management-of-application-crashes"></a>Shell-Verwaltung von Anwendungsabstürzen 
IoT Core-Shell-Infrastruktur überwacht APPX-Type-Anwendungen, die auf dem Gerät für Abstürze und Anwendungen neu gestartet wird, wenn Abstürze auftreten.  Wenn die neu gestarteten Anwendungen abstürzt weiterhin, wird die Shell nutzen eine __failfast – einen kritischen Systemprozess, der bewirkt, eine fehlerüberprüfung dass und neu starten, Versuch zum Wiederherstellen.  Vergleichbare Logik und Verarbeitung werden Tasks und Foreground-Anwendungen in einer Konfiguration mit Multi-Monitor im Hintergrund.   

Abstürze behandeln, und wiederholen Sie die Logik ist unten erfasst: 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig (oder ForegroundAppConfig für Spitzen) 
* QWORD: "FailureResetIntervalMs" – Länge der Zeit-app wurde erfolgreich ausgeführt werden, um die Fehler angezeigt, die auf 0 zurückgesetzt. – Der Standardwert ist 0x00000000000493E0 == 5 Minuten. 
* QWORD: "BaseRetryDelayMs"--Warten Zeit Koeffizienten.  Der Standardwert ist 0xa.
* DWORD: "MaxFailureCount". Standardwert ist 10.
* DWord: "FallbackExponentNumerator", der Standardwert ist 31.
* DWORD: "FallbackExponentDenominator", der Standardwert ist 20.
 
```C#
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator;
// default is 1.55
When app crash is detected:
    if time_since_last_crash > failureresetinterval then crashes_seen = 1
    else ++crashes_seen;

if crashes_seen > MaxFailureCount then __failfast;

else

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent))
// wait for delay and relaunch app
```
 
#### <a name="time-synchronization"></a>Zeitsynchronisierung  
Wenn zeitsynchronisierung tritt ein Fehler oder ein Timeout erfolgt dies möglicherweise aufgrund von nicht erreichbar ist oder ein entfernten Zeitserver Folgendes können ausgeführt werden, um zusätzliche oder der lokale Server hinzufügen. 
 
* Über die Befehlszeile auf dem Gerät (z. b. SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 
* Sie können auch diese Erweiterungen in die Registrierung über ein Skript starten, oder ein Konfigurationspaket für die benutzerdefinierte Laufzeit, die als Teil des Prozesses der imageerstellung bei Bedarf enthalten. 
Weitere Informationen finden Sie unter: 
* [Eine Datei und eine registrierungseinstellung auf ein Bild hinzufügen](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Abbilderstellung für Windows 10 IoT Core](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>Starten Sie den FTP-Server 
Der FTP-Server ausgeführt wird nicht mehr standardmäßig beim Start 
<br>
Einmal ausgeführt wird: 
`Login with SSH\PS` Führen Sie diesen Befehl aus, um FTP zu starten:  
`start ftpd.exe` 
  
Führen Sie auf jedem Start sollten Benutzer einen Task Scheduler erstellen. 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>Copyright-Informationen 

© Microsoft. Alle Rechte vorbehalten. 
 
Dieses Dokument wird im vorliegenden Zustand bereitgestellt.  Informationen und Stellungnahmen in diesem Dokument einschließlich URLs und anderer Websiteverweise können ohne vorherige Ankündigung ändern. 

Einige Beispiele dienen lediglich der Anschauung und sind frei erfunden.  Ähnlichkeiten mit real existierenden Personen, Unternehmen oder Szenarien sind weder beabsichtigt noch ableitbar.  

Dieses Dokument bietet keine keine Rechte an geistigem Eigentum in Microsoft-Produkten.  In diesem Dokument für interne Verweise verwendet werden dürfen Zwecke. 
  
Microsoft übernimmt keine ausdrückliche oder konkludente GEWÄHRLEISTUNGEN.  

Eine Liste von markenrechtlich geschützten Produkten finden Sie im Microsoft Trademarks. 

Alle anderen Marken sind Eigentum der jeweiligen Inhaber.  

UPnP™ ist eine Zertifizierungsmarke der UPnP™ Implementers Corporation. 

Bluetooth® ist eine Marke, die im Besitz von Bluetooth SIG, Inc. USA und an die Microsoft Corporation lizenziert. 

Intel ist eine eingetragene Marke der Intel Corporation. 

Itanium ist eine eingetragene Marke der Intel Corporation.
 
Teile dieser Software werden basierend auf MCSA Mosaic, vom National Center for Supercomputing Applications der University of Illinois in Urbana-Champaign entwickelt, verteilt, die unter einem Lizenzvertrag mit Spyglass, Inc. 

Dieses Produkt enthält lizenzierte Sicherheitssoftware von RSA Data Security, Inc. 
