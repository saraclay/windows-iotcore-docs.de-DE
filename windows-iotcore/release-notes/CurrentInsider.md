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
# <a name="release-notes-for-build-17744"></a>Anmerkungen zu dieser Version erstellen 17744
_Buildnummer 17744. August 2018._

&copy; 2018 Microsoft Corporation. Alle Rechte vorbehalten.

Dieses Dokument enthält aktuelle oder andere Informationen, die die Dokumentation zu den Windows 10 IoT Core zu ergänzen.

Vielen Dank für das Herunterladen von Windows 10 IoT Core. Windows 10 IoT Core ist die Version von Windows 10 für die Entwicklung von eingebetteten oder dedizierten Geräten und die Auswahl für die Maker-Community vorgesehen. Die Pakete in dieser Version enthalten Tools und Inhalten, die zum Installieren von Windows 10 IoT Core auf Minnowboard Max-Plattform basierend auf Intel Atom Einzelprozessorcomputer, Raspberry Pi 2/3-basierend auf Broadcom 2836/2837 und Dragonboard 410 c basierend auf Qualcomm Snapdragon 400-Serie Prozessoren.


## <a name="privacy-statement"></a>Datenschutzbestimmungen

Die Datenschutzbestimmungen für diese Version des Windows-Betriebssystems angezeigt werden kann [hier](http://go.microsoft.com/fwlink/?LinkId=506737).

Sie können verknüpfte Bedingungen überprüfen, indem Sie dem Forwardlink in das Browserfenster einfügen.

## <a name="whats-new-in-this-build"></a>Was ist neu in diesem Build: 
* Allgemeine Fehlerbehebungen 


## <a name="additional-information"></a>Weitere Informationen
* Die für das Abbild Dragon Board verwendete BSP-Version ist 2118.0.0.0. 


## <a name="known-issues-in-this-build"></a>Bekannte Probleme im Build:
* F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter IoT Core.
* Geräte, die über NOOBS installiert wurden, können nicht das Bcdedit-Tool zum Aktivieren des Kernel-Debuggers ausgeführt. Dies kann erreicht werden, mit der folgenden problemumgehung: ** einbinden die SD-Karte auf Ihrem PC ** finden Sie die Datenträgerpartition EFIESP Zahl mit Diskpart oder die Datenträgerverwaltung (z. B. ist "M:") ** führen Sie den Befehl "Bcdedit/store M:\EFI\Microsoft\boot\bcd/Set {Default} debug ' Ja'" **  Aufheben der Bereitstellung der SD-Karte.
Sie sollten jetzt auf den Debugger wie gewohnt eine Verbindung herstellen können
* PSSession unterbricht gelegentlich beim Senden von Befehlen auf IoT-Geräten.
* RPi3 wird nicht koppeln, BT + BTLE integrieren Bluetooth.
* Keine Verbindung zum Internet über WLAN-Verbindung mit SoftAp von Up2.
* UWF gelegentlich tritt ein Fehler auf.
* Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi. Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.


## <a name="iot-core-general-known-issues-and-work-arounds"></a>IoT Core allgemein bekannte Probleme und problemumgehungen für Arbeitsaufgaben

### <a name="for-raspberry-pi"></a>Für Raspberry Pi

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Raspberry Pi-Bildschirmauflösung Monitor wird die Verbindung getrennt 
Der Raspberry Pi kann die Auflösung nicht verwalten, Monitor wird die Verbindung getrennt. Die EDID des Monitors wird verwendet, um die Auflösung des Systems festgelegt, wenn ein solches angeschlossen ist. Wenn getrennt, wird standardmäßig die Raspberry Pi-Firmware, was in der "config.txt" im Stammverzeichnis der SD-Karte ist. 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi-Video-Leistung 
Videowiedergabe Leistung auf dem Raspberry Pi-Plattform wird nicht optimiert.  Animiert die Benutzer, die Elemente, einschließlich XAML-basierte Dropdownmenüs weniger als eine optimale Leistung aufweisen können. 
 
#### <a name="raspberry-pi-camera-support"></a>Kameraunterstützung Raspberry Pi 
Unterstützung für Peripheriegeräte Kamera ist eingeschränkt. Das PiCam-Gerät direkt mit der integrierten Kamera-Bus verbunden wird nicht unterstützt, aufgrund von Einschränkungen in der Plattform, moderne D3D-USB-Webcams erzeugen-Datenströme zu unterstützen, die auf dem USB-Hostcontroller äußerst anspruchsvollen sind.  Selbst bei Verwendung mit niedriger Auflösung Einstellungen Webcams erfordert zusätzliche USB-Optimierung und spezielle Logik des Steuerelements. 

#### <a name="raspberry-pi3-bluetooth-support"></a>Raspberry Pi3 Bluetooth-Unterstützung 
Der Raspberry Pi3 integrierte Bluetooth-Treiber unterstützt nur Geräte mit geringer Bandbreite. 

#### <a name="serial-port-usage-and-access-on-rpi2"></a>Serieller Anschluss-Nutzung und den Zugriff auf RPi2 
Raspberry Pi 2 unterstützt die seriellen Transport für die Kommunikation über die PL011 UART.  Dies wird im Kernel Debugszenarien standardmäßig festgelegt.  Eine Anwendung oder einen Gerätetreiber können die PL011 UART zum Senden und Empfangen von Daten mit dem PL011 Gerätetreiber, die durch das Deaktivieren des Debuggers mit den folgenden Befehl aus:

```
bcdedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a>Datenhaltepunkte wurden auf dem Raspberry Pi2 deaktiviert
Keine problemumgehung zu diesem Zeitpunkt.

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a>Deaktivieren die Onboarding-Adapter für Raspberry Pi 3
Der Raspberry Pi 3 verfügt über integrierte Bluetooth der deaktiviert werden muss, um einen anderen Dongle zu verwenden, um beim Onboarding Bluetooth deaktivieren, öffnen Sie eine Telnet/ssh-Sitzung, und führen Sie: 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

Sie können die WiFi mit dem folgenden Befehl deaktivieren: 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragonboard"></a>Für DragonBoard

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c Herunterfahren
Befehl zum Herunterfahren eines wird für das Board auf die DragonBoard nicht ausschalten. Das System wird neu gestartet. Melden Sie schalten Sie das Board von abschalten.

#### <a name="dragonboard-and-windbg"></a>DragonBoard und windbg
Die integrierte GPIO/I2C/SPI/UART-Treiber werden beim Verbinden mit der DragonBoard mit Windbg deaktiviert.

#### <a name="dragonboard-headset--microphone-jack"></a>DragonBoard Kopfhörer & Mikrofon jack
Die Dragonboard BSP Treiber für die Kopfhörer Jack und Mikrofon Jack, aber nicht eine der folgenden Jacks hinzufügen.  

#### <a name="dragonboard-spi-runs-at-48mhz"></a>DragonBoard SPI ausgeführt wird, mit 4,8 Mhz
Die SPI auf die Dragonboard ignoriert die angeforderten Geschwindigkeit und mit 4,8 Mhz immer ausgeführt.  

#### <a name="dragonboard-connected-standby"></a>DragonBoard verbundenen Standbymodus 
Verbundenen Standby ist nicht auf die Qualcomm Dragonboard standardmäßig aktiviert.  Zum Aktivieren von verbundenen Standbymodus auf DragonBoard muss der folgenden Registrierungsschlüssel auf "1" festgelegt werden:

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> Nicht alle Plattformen ist die Unterstützung für den verbundenen Standbymodus.  Dies funktioniert möglicherweise nicht auf allen Plattformen.    


### <a name="for-minnowboard"></a>Für MinnowBoard
#### <a name="minnowboard-max-boot-and-firmware-update"></a>Minnowboard Max Boot und Firmware-Update 
Das MinnowBoard Max werden nicht gestartet werden, es sei denn, die Firmware Version.092 ist oder höher. Die empfohlene Mindestversion der Firmware ist "MinnowBoard MAX 0.92 32-Bit". Firmwareupdates werden heruntergeladen von [hier](http://go.microsoft.com/fwlink/?LinkId=708613).

#### <a name="minnow-board-peripheral-support"></a>Minnow Board-Unterstützung für Peripheriegeräte
Das Windows 10 IoT Core-Image in dieser Dropdownliste enthalten unterstützt die Peripheriegeräten, die verfügbar gemacht werden, auf dem Board MinnowBoard MAX. Anschließend Intel&reg; bieten Unterstützung für den vollständigen Featuresatz Baytrail Prozessoren der Intel-Celeron einschließlich&trade; Prozessoren J1900/N2930/N2807 und Intel Atom&trade; Prozessoren E38XX.


### <a name="for-all-platforms"></a>Für alle Plattformen 

#### <a name="mouse-pointer-disappears-while-debugging"></a>Mauszeiger verschwindet während des Debuggens 
Klicken Sie in einigen Fällen der Mauszeiger nach dem Bereitstellen oder Debuggen von apps mit Visual Studio nicht sichtbar ist, der Mauszeiger sollte wieder angezeigt, wenn Sie den Fokus mit der Tastatur (Registerkarte) ändern.


#### <a name="server-applications-with-softap"></a>Server-Anwendungen mit SoftAP
Wenn die SoftAP Clients nicht den Zugriff auf Inhalte von UAP-apps verfügbar gemacht werden können.  
Die folgenden Änderungen müssen über die Konsole auf dem Gerät vorgenommen werden, um über SoftAP UAP-Anwendungen verfügbar zu machen:  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
```

Zum Beispiel:  
```
checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym
```
Neustart 


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Sensor-Treiber-Konflikt im vorgefertigten FFUs 
In der bereitgestellten FFUs vorliegt ein Sensor-Treiber-Konflikt. Das Remote-Sensor-Framework werden die Treiber für Kompass, Magnetometer, Beschleunigungsmesser und Gyrometer installiert. Die UWP-APIs für den Zugriff auf diese aus einer Anwendung gehen davon aus, nur 1 installiert ist. Wenn Sie einen Treiber für ein physisch angeschlossenen Gerät entwickeln, vorausgesetzt die remote-Treiber auf der Microsoft FFUs in Konflikt steht.

Lösung: Der in Konflikt stehenden Treiber entfernt werden kann, durch die Verbindung mit dem Gerät über SSH oder Powershell, und verwenden das Tool devcon.exe Entfernen des remote-Sensor-Treibers durch Eingabe "devcon.exe entfernen @" ROOT\REMOTESENSORDRIVER *". Der remote-Sensor-Treiber hat keine Auswirkungen auf die OEM-Abhängige FFUs erstellt.


#### <a name="default-administrator-user-name-and-password"></a>Standard-Administratorbenutzernamen und das Kennwort
Die Standard-Administratorbenutzernamen und das Kennwort sind fest codiert, in das Windows 10 IoT Core-Image. Dies ist ein Sicherheitsrisiko für das Gerät, und es nicht verfügbar gemacht werden, eine Internetverbindung geöffnet, bis das Kennwort geändert wurde.

#### <a name="volume-controls"></a>Lautstärkeregler
Hardware-Volume-Steuerelemente für USB-Mikrofone und Lautsprecher, die auf Windows-System so ändern Sie den Systemdatenträger abhängig sind, werden auf Windows 10 IoT Core derzeit nicht unterstützt. 

#### <a name="usb-keyboards"></a>USB-Tastatur  
Einige USB-Tastaturen und Mäusen funktioniert möglicherweise nicht unter IoT Core. Verwenden einer anderen Tastatur oder Maus. Eine Liste der überprüften Peripheriegeräte befinden sich die [Dokumentation](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist).


#### <a name="screen-orientation"></a>Bildschirmausrichtung
Die Ausrichtung auf "Hochformat" festlegen kann nicht in einer universellen App berücksichtigt werden.

#### <a name="referencing-adapters-with-alljoyn-templates"></a>Verweisen Netzwerkkarten mit AllJoyn-Vorlagen
Es wird versucht, Verweise auf AllJoyn Adapter Projekte hinzufügen kann zu Fehlern führen, wenn Sie bestimmte SDK-Versionen verwenden.  Um diese Fehler zu beheben, ändern Visual Studio-Zielplattform entsprechend die aktuelle SDK-Version, und Laden Sie das Projekt.

#### <a name="wifi-direct-limitations-on-iotcore"></a>WiFi Direct-Einschränkungen für IoTCore
* Das IoTCore-Gerät muss das verbindende Gerät zu sein – es funktioniert nicht als Ankündigung Gerät mit einem anderen Gerät die Verbindung initiiert.   
* Erweiterte Kopplung muss verwendet werden.  Die Beispiel-app veranschaulicht, wie die erweiterte ereignispaarbildung-APIs zu verwenden, um die Geräte vor dem Herstellen einer Verbindung zu koppeln. 
* Nicht alle Drahtlosadapter unterstützen WiFi Direct. Wir getestet und überprüft, die "Realtek RTL8188EU w-Lan 802. 11n USB 2.0 Network Adapter" funktioniert, aber anderen Adaptern, die möglicherweise nicht mehr unterstützt. 


#### <a name="non-default-drive-mode"></a>Nicht standardmäßiges Laufwerk-Modus
Auf Raspberry Pi und Dragonboard kann der Wechsel von einem Nichtstandard-Laufwerk-Modus zu einem anderen Nichtstandard-Laufwerk-Modus eine Störung auf den GPIO-Pin generieren. PROBLEMUMGEHUNG Laufwerkmodus einmal am Anfang der Anwendung festgelegt.

#### <a name="application-already-running"></a>Anwendung wird bereits ausgeführt
Die Standard-Start-app kann mit sich selbst in Konflikt stehen, wenn sie auch in Visual Studio bereitgestellt wird. PROBLEMUMGEHUNG Ändern Sie die Standard-Start-app zu einer Anwendung, die andere als die Sie bereitstellen möchten. 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground stürzt möglicherweise ab.
Die folgende Codezeile stürzt möglicherweise ab: “BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;”. Um den Absturz zu verhindern, fügen Sie folgenden Code, damit es zuerst ausgeführt wird "Var Player BackgroundMediaPlayer.Current; =" 

#### <a name="azure-active-directory-authentication-support"></a>Unterstützung für Azure Active Directory-Authentifizierung
Die Azure Active Directory-Authentifizierungsbibliothek funktioniert nicht unter Windows 10 IoT Core.  

#### <a name="shell-management-of-application-crashes"></a>Shell-Verwaltung von Anwendungsabstürzen
IoT Core-Shell-Infrastruktur überwacht APPX-Type-Anwendungen, die auf dem Gerät für Abstürze und Anwendungen neu gestartet wird, wenn Abstürze auftreten.  Wenn die neu gestarteten Anwendungen abstürzt weiterhin, wird die Shell nutzen eine __failfast – einen kritischen Systemprozess, der einem schwerwiegenden Fehler verursacht und neu starten, Versuch zum Wiederherstellen.  Vergleichbare Logik und Verarbeitung werden Tasks und Foreground-Anwendungen in einer Konfiguration mit Multi-Monitor im Hintergrund.   Abstürze behandeln, und wiederholen Sie die Logik ist unten erfasst:

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

Wenn Abstürze der app erkannt wird: 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

Warten, Verzögerung und starten Sie die app dann erneut. 


#### <a name="time-synchronization"></a>Zeitsynchronisierung  
Wenn zeitsynchronisierung tritt ein Fehler oder ein Timeout erfolgt dies möglicherweise aufgrund von nicht erreichbar ist oder ein entfernten Zeitserver Folgendes können ausgeführt werden, um zusätzliche oder der lokale Server hinzufügen. 

1) Über die Befehlszeile auf dem Gerät (z. b. SSH, Powershell) w32tm/config / Befehl /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2. etwas anderes,..." 

2) Sie können auch diese Erweiterungen in die Registrierung über ein Skript starten, oder ein Konfigurationspaket für die benutzerdefinierte Laufzeit, die als Teil des Prozesses der imageerstellung bei Bedarf enthalten. Weitere Informationen finden Sie unter: 

* [Hinzufügen einer Datei und die Einstellung in der Registrierung zu einem Bild](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)


### <a name="starting-the-ftp-server"></a>Starten Sie den FTP-Server 
Der FTP-Server ausgeführt wird nicht mehr standardmäßig beim Start 

Einmal ausgeführt wird: Melden Sie sich mit SSH\PS, und führen Sie diese Befehl, um FTP zu starten:  
```
start ftpd.exe 
```

Führen Sie auf jedem Start Benutzer sollte eine Scheduler-Aufgabe zu erstellen: Melden Sie sich mit SSH\PS, und erstellen Sie einen Task Scheduler: 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```
