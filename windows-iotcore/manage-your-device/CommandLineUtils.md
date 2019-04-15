---
title: Windows 10 IoT Core-Befehlszeilen-Hilfsprogramme
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, die Befehlszeilen-Hilfsprogramme mit PowreShell verwendet werden soll, nachdem eine Verbindung mit Ihrem Gerät.
keywords: Windows Iot, über die Befehlszeile, Befehlszeilen-Hilfsprogramme mit PowerShell
ms.openlocfilehash: 2fb009115dc929540c30d5403c1877051f6b7037
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513338"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Windows 10 IoT Core-Befehlszeile "utils"

Möchten Sie um einige der Einstellungen auf dem Gerät zu konfigurieren? Die folgenden Tools stehen zur Verfügung. Verwenden von PowerShell zum Ausführen dieser Befehle nach [an Ihr Gerät anschließen](../connect-your-device/PowerShell.md).

> [!NOTE]
> Diese Tools werden nicht vorab geladen – müssen Sie die entsprechenden Feature-IDs, rufen Sie diese Tools im Image enthalten.

## <a name="iot-core-specific-command-line-utils"></a>IoT Core-spezifischen über die Befehlszeile "utils"

### **<a name="setting-startup-app"></a>Start-app festlegen:**
Verwenden Sie den Start-Editor, um beim Start von apps auf Ihrem Gerät Windows IoT Core zu konfigurieren. Führen Sie `IotStartup` mit einem der folgenden Optionen:

* `IotStartup list` Listet alle installierten Anwendungen
* `IotStartup list headed` installierten Listen Spitzen Anwendungen
* `IotStartup list headless` Listet alle installierten monitorlose Anwendungen
* `IotStartup list [MyApp]` Auflisten installierter Anwendungen, die mit dem Muster übereinstimmen `MyApp`
* `IotStartup add` Fügt der Kopfzeilen und monitorlose-Anwendungen
* `IotStartup add headed [MyApp]` Fügt der Kopfzeilen Anwendungen mit dem Muster `MyApp`.  Nur eine Anwendung muss mit Muster übereinstimmen.
* `IotStartup add headless [Task1]` Fügt der monitorlose Anwendungen, die mit dem Muster übereinstimmen `Task1`
* `IotStartup remove` entfernt, die Spitzen und monitorlose Anwendungen
* `IotStartup remove headed [MyApp]` entfernt Spitzen Anwendungen, die mit dem Muster übereinstimmen `MyApp`
* `IotStartup remove headless [Task1]` Entfernt die monitorlose Anwendungen, die mit dem Muster übereinstimmen `Task1`
* `IotStartup startup` Listen, die Spitzen und monitorlose Anwendungen, die für den Start registriert
* `IotStartup startup [MyApp]` Listen, Spitzen und monitorlose Anwendungen registriert für den Start dieser Muster `MyApp`
* `IotStartup startup headed [MyApp]` Listen mit Anwendungen, die für den Start registriert, die mit übereinstimmen Spitzen. `MyApp`
* `IotStartup startup headless [Task1]` Listet monitorlose Anwendungen für den Start registriert, die mit übereinstimmen `Task1`

    * Um weitere Hilfe zu erhalten versuchen Sie es `IotStartup help`
    
### **<a name="change-settings-for-region-and-user-or-speech-language"></a>Ändern der Einstellungen für die Region "und" Benutzer "oder" Speech Sprache:**

Die `IoTSettings` Tool ändert, Region, die Standardsprache für Benutzer oder Sprache. Dies ist ein Befehlszeilentool, das von einer Anwendung mithilfe der ProcessLauncher-API aufgerufen werden kann. Diese Befehle müssen als Standardkonto, nicht als Administrator ausgeführt werden.

* `IotSettings del account {all | username}` Löscht alle Account, MSA oder AAD-Konten auf dem System oder ein bestimmtes Konto.  Bestimmte Konten werden in der form username@provider.com
* `IotSettings del diagnostics` Löscht die Diagnoseinformationen in der Cloud für das aktuelle Gerät.  Beachten Sie, dass dadurch die Versionsgeschichte bis zum Zeitpunkt des Aufrufs wird entfernt.  Neue Diagnose-Informationen werden weiterhin protokolliert werden.
* `IotSettings list account` Listet alle Account, MSA oder AAD-Konten, die auf dem Gerät signiert wurden.
* `IotSettings list uilanguage` Listet alle UI-Sprachen
* `IotSettings list speechlanguage` Listet alle Sprachen für Sprachausgabe
* `IotSettings get uilanguage` Zeigt die aktuelle Sprache der Benutzeroberfläche
* `IotSettings get speechlanguage` Zeigt die Sprache der aktuellen Sprache an
* `IotSettings get region` Zeigt die aktuelle region
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` Legt die Standardsprache Französisch (Kanada))
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` Legt fest, der Sprache Französisch (Kanada))
* `IotSettings set region region\_code - (e.g. CA)` Legt die Standardregion, Kanada)
* `IotSettings set bluetoothpref {sink | source}` Gibt an, das die Einstellung für Bluetooth-Rolle auswählen, wenn die Geräte, die mit Funktionen sowohl IOT_BLUETOOTH_A2DP_SOURCE und IOT_BLUETOOTH_A2DP_SINK erstellt auf ein anderes Gerät verbinden, die auch beide Rollen unterstützt.
* `IotSettings get bluetoothpref` Gibt die aktuelle Bluetooth-Voreinstellung für die Rolle für Geräte, die mit IOT_BLUETOOTH_A2DP_SOURCE und IOT_BLUETOOTH_A2DP_SINK erstellt.  Der Standardwert ist die Quelle.

> [!TIP]
> `IoTSettings -list uiLanguage` (in der Version des Windows IoT Core-Images, die, denen Sie für bereits ausgeführt wurde) wird wieder die Liste der unterstützten Sprache der Benutzeroberfläche bieten.
    
### **<a name="change-default-audio-device-and-volume"></a>Ändern Sie Standard-Audiogeräts "und" Volume:**

Die `IoTCoreAudioControlTool` Tool steuert audio verwandte Optionen, z. B. die Erfassung und Wiedergabe Geräte festlegen und Ändern der Lautstärke. Führen Sie für eine vollständige Liste von Parametern, `IoTCoreAudioControlTool h`.

### **<a name="manually-installing-appx-files"></a>Manuell zu installieren. APPX-Dateien:**
DeployAppx ermöglicht installieren und Entfernen von. APPX-Paketen in Entwicklungsszenarios.  Die richtige Methode für die Installation. APPX-Paketen in Produktions-Images ist die Verwendung ein Bereitstellungspakets dokumentiert sind die [Installieren der app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) Betreff.  DeployAppx unterstützt auch Abfragen. APPX-Paket-Informationen.

*  `DeployAppx install MyApp.appx` installiert die. APPX und das Zertifikat mit dem gleichen Namen wenn gefunden.
* `DeployAppx install force MyApp.appx` Erzwingt, dass den aktuell installierten deinstallieren. APPX mit dem gleichen Paket zu benennen, wenn vor der Installation der neuen gefunden. APPX.  Dies ist nützlich für die Installation ein. APPX mit der Anzahl dieselbe oder eine niedrigere Version als die derzeit installierten. APPX.
* `DeployAppx install retry MyApp.appx` eine erneute Installation der. APPX-10-Mal bei einem Fehler mit 2 Sekunden Verzögerung zwischen den Wiederholungsversuchen.
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` Deinstallieren der AppX-Datei mit den entsprechenden vollständigen Paketnamen an.
*  `DeployAppx uninstall MyApp.appx` Deinstallieren Sie eine beliebige vorhandene aus. APPX mit einem übereinstimmenden Namen der Paket-Familie.
* `DeployAppx getpackages` Listet alle installierten vollständigen Paketnamen.
* `DeployAppx getpackageid IotCoreDefaultApp.appx` Gibt den Paketnamen, den paketfamiliennamen und das Paket für die vollständigen Namen der. APPX.
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` nicht unterstützt


## <a name="general-command-line-utils"></a>Allgemein über die Befehlszeile "utils"

### **<a name="update-account-password"></a>Aktualisieren Sie Kontokennwort:**

Es wird dringend empfohlen, dass Sie das Standardkennwort für das Administratorkonto aktualisieren. Zu diesem Zweck können Sie den folgenden Befehl ausgeben: `net user Administrator [new password]` , in denen `[new password]` stellt ein sicheres Kennwort Ihrer Wahl.

### **<a name="create-local-user-accounts"></a>Erstellen Sie lokale Benutzerkonten:**

Wenn Sie anderen Benutzern Zugriff auf Ihr Gerät Windows IoT Core gewähren möchten, können Sie zusätzliche lokale Benutzerkonten, die mit PS durch Eingabe erstellen `net user [username] [password] /add`. Wenn Sie diesen Benutzer zu anderen Gruppen, z.B. die Gruppe "Administrator" hinzufügen möchten, verwenden `net localgroup Administrators [username] /add`.

### **<a name="set-password"></a>Legen Sie das Kennwort ein:**

Führen Sie zum Ändern des Kennworts für ein Konto auf Ihrem Gerät `net user [account-username] [new-password]` das Kontokennwort zu ändern.

### **<a name="query-and-set-device-name"></a>Abfragen aus, und Festlegen von Gerätename:**

Um den Namen des aktuellen Geräts zu identifizieren, geben Sie einfach `hostname`. Um den Namen Ihres Windows IoT Core-Geräts zu ändern, geben `SetComputerName [new machinename]`. Sie müssen das Gerät die Namensänderung wirksam wird neu gestartet.

### **<a name="basic-network-configuration"></a>Grundlegende Netzwerkkonfiguration:**

Viele der grundlegenden Konfiguration Netzwerkdienstprogramme bereits kennen Sie möglicherweise mit sind verfügbar in Windows IoT Core, einschließlich Befehle wie z. B. `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, und `arp.exe`.

### **<a name="copy-utilities"></a>Kopieren Sie die Dienstprogramme:**

Microsoft bietet vertraute Tools, einschließlich `sfpcopy.exe` sowie `xcopy.exe`.

### **<a name="process-management"></a>Prozessmanagement:**

Um derzeit ausgeführte Prozesse anzuzeigen, können Sie versuchen, entweder `get-process` Alternativ `tlist.exe`. Um einen laufenden Prozess zu beenden, geben `kill.exe [pid or process name]`.


### **<a name="set-boot-option-headless-vs-headed-boot"></a>Legen Sie die Option "Start" (monitorlose im Vergleich zu Multi-Monitor starten):**

Windows IoT Core-Geräte zu Kopfzeilen festgelegt werden, (wenn es sich um eine Anzeigefunktionen erforderlich sind) oder (bei eine Anzeige nicht erforderlich oder verfügbar ist) monitorlose "Gerät". Verwenden Sie zum Ändern dieser Einstellung `setbootoption.exe [headed | headless]`.

> [!NOTE]
> Das Ändern dieser Einstellung müssen einen Neustart damit die Änderung wirksam wird.

### **<a name="task-scheduler"></a>Der aufgabenplanung:**

Um die aktuelle Liste der geplanten Aufgaben anzuzeigen, verwenden Sie die `schtasks.exe` Befehl. Sie können neue Vorgänge mit erstellen die `/create` wechseln, oder führen Sie bei Bedarf Aufgaben mit der `/run` wechseln. Verwenden Sie für eine vollständige Liste der unterstützten Parameter `schtasks.exe /?`

### **<a name="device-drivers"></a>Gerätetreiber:**

Das Gerät Konsole-Hilfsprogramm ist hilfreich bei der Identifizierung und Verwaltung von installierten Geräten und Treibern. Verwenden Sie für eine vollständige Liste von Parametern `devcon.exe /?`

### **<a name="registry-access"></a>Zugriff auf die Registrierung:**

Wenn Sie Zugriff auf die Registrierung zu anzeigen oder ändern Sie die Einstellungen zu verwenden, müssen die `reg.exe /?` -Befehl für die vollständige Liste der unterstützten Parameter.

### **<a name="services"></a>Dienste:**

Verwalten von Windows-Diensten kann erreicht werden, über die `net.exe` Befehl. Geben Sie zum Anzeigen einer Liste mit den ausgeführten Diensten `net start`. Geben Sie zum Starten oder Beenden eines bestimmten Diensts, `net [start | stop] [service name]`. Alternativ können Sie auch über den dienststeuerungs-Manager verwenden `sc.exe` Befehl.

### **<a name="boot-configuration"></a>Startkonfiguration:**

Sie können die Startkonfiguration Ihres Geräts für die Windows IoT Core Änderungen vornehmen, mithilfe von `bcdedit.exe`. Sie können z. B. Testsigning mit `bcdedit –set testsigning on` Befehl.

### **<a name="shutdownrestart-device"></a>Herunterfahren/Neustarten des Geräts:**

Geben Sie Ihr Gerät Herunterfahren `shutdown /s /t 0`. Verwenden Sie zum Neustarten des Geräts die `/r` wechseln Sie stattdessen mit dem Befehl `shutdown /r /t 0`.

### **<a name="viewing-and-changing-display-settings"></a>Anzeigen und Ändern von Anzeigeeinstellungen**
Das Tool SetDisplayResolution kann verwendet werden, zum Auflisten der der aktuellen Anzeigeeinstellungen und um die Liste der unterstützten Werte anzuzeigen.  Es kann weiter verwendet werden, zum Anpassen der Anzeige Auflösung, Aktualisierungsrate und/oder Ausrichtung mit Werten, die von Ihrer Plattform unterstützt werden.  Das Hilfsprogramm akzeptiert die folgenden Befehlszeilenargumente:

* `SetDisplayResolution` Listet die aktuellen Resoltuion anzeigen.
* `SetDisplayResolution -list` Liste der unterstützten displayauflösungen.
* `SetDisplayResolution -orientation:[n]` Ändern der anzeigeausrichtung, wobei n = 0, 90, 180 oder 270 Grad.
* `SetDisplayResolution [width] [height]` Ändern Sie die Breite und Höhe in Pixel 
* `SetDisplayResolution [width] [height] [refreshrate]` Breite, Höhe und Aktualisierung Änderungsrate, Breite und Höhe in Pixel und "RefreshRate" in Hz sind 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` Ändern Sie Breite, Höhe, "RefreshRate" und Bildschirm-Ausrichtung, Breite und Höhe in Pixel "RefreshRate" in Hz und Ausrichtung eines 0, 90, 180 oder 270.

### **<a name="take-screenshot"></a>Erstellen eines Screenshots:**

Schalten Sie den Screenshot Ihres Geräts für die Windows-IoTCore, indem `ScreenCapture.exe`. Führen Sie z. B. `ScreenCapture c:\folder\screencap.jpg` Screenshot übernimmt und in screencap.jpg-Datei zu speichern.

### **<a name="get-information-about-network-adapters"></a>Abrufen von Informationen über Netzwerkadapter:**

Führen Sie zum Anzeigen der Liste aller verfügbaren Netzwerkadapter `GetAdapterInfo` Tool.

### **<a name="set-folder-permissions-for-uwp-apps"></a>Legen Sie Berechtigungen für die UWP-apps:**

Nicht alle Ordner auf Ihrem Gerät sind zugegriffen werden kann, von universellen Windows-Apps. Um einen Ordner zugegriffen werden kann zu einer UWP-app zu machen, können Sie `FolderPermissions` Tool. Führen Sie z. B. `FolderPermissions c:\test -e` um UWP-apps Zugriff auf `c:\test` Ordner. Beachten Sie, dass dies nur mit systemeigenen Win32-apis für z. B. funktionieren. CreateFile2 und nicht mit WinRT-apis wie "storagefolder", "storagefile" usw.

### **<a name="work-with-serial-ports"></a>Arbeiten Sie mit seriellen Anschlüssen:**
[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) können Sie mit der seriellen Anschlüsse über die Befehlszeile zu arbeiten. Es wird als ein Beispielprojekt im ms-Iot-Samples-Repository bereitgestellt. 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```


