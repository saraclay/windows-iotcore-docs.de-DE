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
# <a name="release-notes-for-raspberry-pi-3b"></a>Anmerkungen zu dieser Version für Raspberry Pi 3 b

&copy; 2018 Microsoft Corporation. Alle Rechte vorbehalten.

> [!NOTE]
> Diese Version für die Raspberry Pi 3 b + ist eine nicht unterstützte technical Preview-Version. Begrenzt überprüft und die Aktivierung abgeschlossen wurde. Die aktuelle Version finden Sie [hier](https://www.microsoft.com/en-us/software-download/windowsiot). Treten Sie für eine bessere Evaluierung auf, und für alle kommerziellen Produkten, verwenden Sie den Raspberry Pi 3-b oder andere Geräte mit unterstützten Intel, Qualcomm oder NXP SoCs. Zur Behandlung von Problemen mit dem Raspberry Pi 3 b aus, informieren Sie sich unsere Handbuch zur Problembehandlung [hier](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues). 

## <a name="whats-new-in-this-build"></a>Was ist neu in diesem Build: 
* Allgemeine Fehlerbehebungen

## <a name="known-issues-in-this-build"></a>Bekannte Probleme im Build:
* Dieses Image ist nur für RPi3B vorgesehen und werden nicht auf RPi2 gestartet. 
* F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter IoT Core. 
* Integrieren WLAN- und Bluetooth funktionieren auf RPI3B + nicht. 
* Ft5406 Touch Bildschirm Treiber ist für RPi3B + deaktiviert. 
* SD-Karte Aktivität LED ist deaktiviert. 


### <a name="display-resolution-is-monitor-is-disconnected"></a>Bildschirmauflösung ist, dass der Monitor getrennt ist
Der Raspberry Pi 3 b + kann nicht Bildschirmauflösung verwalten Monitor wird die Verbindung getrennt. Die EDID des Monitors wird verwendet, um die Auflösung des Systems festgelegt, wenn ein solches angeschlossen ist. Wenn getrennt, wird standardmäßig die Firmware wird die "config.txt" im Stammverzeichnis der SD-Karte. 


### <a name="video-performance"></a>Video-Leistung
Leistung der Videowiedergabe auf der Plattform ist nicht optimiert.  Animiert die Benutzer, die Elemente, einschließlich XAML-basierte Dropdownmenüs weniger als eine optimale Leistung aufweisen können.  

### <a name="camera-support"></a>Kameraunterstützung
Unterstützung für Peripheriegeräte Kamera ist eingeschränkt. Das PiCam-Gerät direkt mit der integrierten Kamera-Bus verbunden wird nicht unterstützt, aufgrund von Einschränkungen in der Plattform, moderne D3D-USB-Webcams erzeugen-Datenströme zu unterstützen, die auf dem USB-Hostcontroller äußerst anspruchsvollen sind.  Selbst bei Verwendung mit niedriger Auflösung Einstellungen Webcams erfordert zusätzliche USB-Optimierung und spezielle Logik des Steuerelements.  


### <a name="mouse-pointer-disappears-while-debugging"></a>Mauszeiger verschwindet während des Debuggens
Klicken Sie in einigen Fällen der Mauszeiger nach dem Bereitstellen oder Debuggen von apps mit Visual Studio nicht sichtbar ist, der Mauszeiger sollte wieder angezeigt, wenn Sie den Fokus mit der Tastatur (Registerkarte) (8038595) ändern.

### <a name="server-applications-with-softap"></a>Server-Anwendungen mit SoftAP
Wenn die SoftAP Clients nicht den Zugriff auf Inhalte von UAP-apps verfügbar gemacht werden können. Die folgenden Änderungen müssen über die Konsole auf dem Gerät (8111807) vorgenommen werden, um über SoftAP UAP-Anwendungen verfügbar zu machen:  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

Starten Sie neu.

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Sensor-Treiber-Konflikt im vorgefertigten FFUs 
In der bereitgestellten FFUs vorliegt ein Sensor-Treiber-Konflikt. Das Remote-Sensor-Framework werden die Treiber für Kompass, Magnetometer, Beschleunigungsmesser und Gyrometer installiert. Die UWP-APIs für den Zugriff auf diese aus einer Anwendung wird davon ausgegangen, dass nur eine installiert ist. Wenn Sie einen Treiber für ein physisch angeschlossenen Gerät entwickeln, vorausgesetzt die remote-Treiber auf der Microsoft FFUs in Konflikt steht.  

Um für dieses Problem zu lösen, kann der in Konflikt stehenden Treiber durch Herstellen einer Verbindung mit dem Gerät über SSH oder Powershell, und verwenden das Tool devcon.exe Entfernen des remote-Sensor-Treibers durch Eingabe entfernt werden: 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

Der remote-Sensor-Treiber hat keine Auswirkungen auf die OEM-Abhängige FFUs erstellt. 


### <a name="default-administrator-user-name-and-password"></a>Standard-Administratorbenutzernamen und das Kennwort
Die Standard-Administratorbenutzernamen und das Kennwort sind fest codiert, in das Windows 10 IoT Core-Image. Dies ist ein Sicherheitsrisiko für das Gerät, und es nicht verfügbar gemacht werden, eine Internetverbindung geöffnet, bis das Kennwort geändert wurde. 

### <a name="volume-controls"></a>Lautstärkeregler
Hardware-Volume-Steuerelemente für USB-Mikrofone und Lautsprecher, die auf Windows-System so ändern Sie den Systemdatenträger abhängig sind, werden auf Windows 10 IoT Core derzeit nicht unterstützt. 

### <a name="usb-keyboards"></a>USB-Tastatur
Einige USB-Tastaturen und Mäusen funktioniert möglicherweise nicht unter IoT Core. Verwenden einer anderen Tastatur oder Maus. Eine Liste der überprüften Peripheriegeräten finden Sie in der Dokumentation [hier](http://go.microsoft.com/fwlink/?LinkId=619428).
 
### <a name="screen-orientation"></a>Bildschirmausrichtung
Die Ausrichtung auf "Hochformat" festlegen kann nicht in einer universellen App berücksichtigt werden.

### <a name="referencing-adapters-with-alljoyn-templates"></a>Verweisen Netzwerkkarten mit AllJoyn-Vorlagen
Es wird versucht, Verweise auf AllJoyn Adapter Projekte hinzufügen kann zu Fehlern führen, wenn Sie bestimmte SDK-Versionen verwenden.  Um diese Fehler zu beheben, ändern Visual Studio-Zielplattform entsprechend die aktuelle SDK-Version, und Laden Sie das Projekt.  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a>WiFi Direct-Einschränkungen für Windows 10 IoT Core
1. Die Windows 10 IoT Core, die Gerät das verbindende Gerät – werden muss sie als Werbung Gerät mit einem anderen Gerät Initiieren der Verbindung funktioniert nicht.   
2. Erweiterte Kopplung muss verwendet werden.  Die Beispiel-app veranschaulicht, wie die erweiterte ereignispaarbildung-APIs zu verwenden, um die Geräte vor dem Herstellen einer Verbindung zu koppeln. 
3. Nicht alle Drahtlosadapter unterstützen WiFi Direct. Wir getestet und überprüft, die "Realtek RTL8188EU w-Lan 802. 11n USB 2.0 Network Adapter" funktioniert, aber anderen Adaptern, die möglicherweise nicht mehr unterstützt. 

### <a name="non-default-drive-mode-3890679"></a>Nicht standardmäßiges Laufwerk-Modus (3890679) 
Auf Raspberry Pi und Dragonboard kann der Wechsel von einem Nichtstandard-Laufwerk-Modus zu einem anderen Nichtstandard-Laufwerk-Modus eine Störung auf den GPIO-Pin generieren. Zur Umgehung dieses Problem, Laufwerk-Modus einmal am Anfang der Anwendung festlegen. 

### <a name="application-already-running-1244550"></a>Anwendung wird bereits ausgeführt (1244550) 
Die Standard-Start-app kann mit sich selbst in Konflikt stehen, wenn sie auch in Visual Studio bereitgestellt wird. PROBLEMUMGEHUNG Ändern Sie die Standard-Start-app zu einer Anwendung, die andere als die Sie bereitstellen möchten. 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a>BackgroundMediaPlayer.MessageReceivedFromForeground (2199869) stürzt möglicherweise ab. 
Die folgende Codezeile stürzt möglicherweise ab: 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

Um den Absturz zu verhindern, fügen Sie folgenden Code, sodass er zuerst ausgeführt wird:
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a>Azure Active Directory-Authentifizierungsunterstützung (4266261) 
Die Azure Active Directory-Authentifizierungsbibliothek funktioniert nicht unter Windows 10 IoT Core.  

### <a name="shell-management-of-application-crashes"></a>Shell-Verwaltung von Anwendungsabstürzen
IoT Core-Shell-Infrastruktur überwacht APPX-Type-Anwendungen, die auf dem Gerät für Abstürze und Anwendungen neu gestartet wird, wenn Abstürze auftreten.  Wenn die neu gestarteten Anwendungen abstürzt weiterhin, wird die Shell nutzen eine Failfast – einen kritischen Systemprozess, der einem schwerwiegenden Fehler verursacht und neu starten, Versuch zum Wiederherstellen.  Vergleichbare Logik und Verarbeitung werden Tasks und Foreground-Anwendungen in einer Konfiguration mit Multi-Monitor im Hintergrund.   Absturz Fehlerbehandlung und Wiederholungslogik Logik wird unten erfasst:

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

Warten Sie, bis die Verzögerung, und starten Sie die app erneut.

#### <a name="dragonboard-spi-runs-at-48mhz"></a>Dragonboard SPI ausgeführt wird, mit 4,8 Mhz
Die SPI auf die Dragonboard ignoriert die angeforderten Geschwindigkeit und mit 4,8 Mhz immer ausgeführt.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard verbundenen Standbymodus 
Verbundenen Standby ist nicht auf die Qualcomm Dragonboard standardmäßig aktiviert.  Zum Aktivieren von verbundenen Standbymodus auf DragonBoard muss der folgenden Registrierungsschlüssel auf "1" festgelegt werden.


### <a name="time-synchronization"></a>Zeitsynchronisierung
Wenn zeitsynchronisierung tritt ein Fehler oder ein Timeout erfolgt dies möglicherweise aufgrund von nicht erreichbar ist oder ein entfernten Zeitserver Folgendes können ausgeführt werden, um zusätzliche oder der lokale Server hinzufügen. 
 
1. Über die Befehlszeile auf dem Gerät (z. b. SSH, Powershell).
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. Sie können auch diese Erweiterungen in die Registrierung über ein Skript starten, oder ein Konfigurationspaket für die benutzerdefinierte Laufzeit, die als Teil des Prozesses der imageerstellung bei Bedarf enthalten. 

### <a name="starting-the-ftp-server"></a>Starten Sie den FTP-Server 
* Einmalig - melden Sie sich mit SSH\PS, und führen Sie diesen Befehl aus, um FTP zu starten:  

```
start ftpd.exe 
```

* Um auf jedem Neustart auszuführen, sollten Benutzer erstellen Sie eine Aufgabe für Scheduler - melden Sie sich mit SSH\PS und erstellen Sie einen Task Scheduler:

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a>Partition größenanforderungen für Update 
Sicherstellen Sie, dass Datenpartition genügend Speicherplatz für die Update-Funktionalität verwaltet.  Es wird empfohlen, 1GB kostenlos für vollständige Update-Funktionalität.  Wenn Datenpartition nicht genügend Speicherplatz verfügt, schlägt die Updates in der Phase der Installation fehl. 

### <a name="powershell-log-generation-on-iot-core"></a>PowerShell-protokollgenerierung unter IoT Core 
PowerShell unter Iot Core möglicherweise Protokolldateien in der Standardeinstellung, die viel Raum einnimmt, auf das Dateisystem generieren. Auch wenn die Größe der Log-Dateien beschränkt sind, kann es dauern Speicherplatz, was ggf. zu wenig Speicherplatz Situation, unter anderem bei der Aktualisierung Fehler führen kann. Ereignis der EVTX-Protokolldateien haben eine vordefinierte maximale Größe von 20 MB. Sie können die Dateien, um eine andere maximale Größe über Registrierung haben einzeln begrenzen. Geben Sie beispielsweise Folgendes ein, um security.evtx bei maximalen Größe von 10 MB zu halten: 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a>Schtasks limitation  
"SCHTASKS" unterstützt nicht/XML-Schalter verwenden. Zum Beispiel: 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
Dies wird unter IoT Core fehl. Ausführen des Befehls wird den Fehler generiert: FEHLER: Die angegebene Prozedur konnte nicht gefunden werden. 
