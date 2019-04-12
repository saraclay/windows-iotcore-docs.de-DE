---
title: Gerätetreiber
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Informationen Sie zum Erstellen und Bereitstellen eines Treibers mithilfe von Visual Studio.
keywords: Windows 10 IoT Core, Gerätetreiber
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513753"
---
# <a name="driver-deployment"></a>Gerätetreiber

Stellen Sie einen Treiber auf Windows 10 IoT Core mit Visual Studio bereit. 

Konfigurieren Sie Visual Studio-Treiber-Projekt so, dass Sie kompilieren und ein Treibers für eine bestimmte Plattform während der Entwicklungsphase Treiber bereitstellen. 

Für diese Übung können Sie die [Gpiokmdfdemo Beispieltreiber](https://github.com/ms-iot/samples/tree/develop/DriverSamples).

Wenn Sie einen Treiber zu einem Bild hinzufügen möchten, besuchen Sie die Anweisungen in unserer [Manufacturing für IoT](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).

## <a name="step-1--setup"></a>Schritt 1: Setup 
___

### <a name="on-the-device"></a>Auf dem Gerät

* Stellen Sie sicher, dass das Gerät ein IoTCore-Image installiert wird, indem Sie die folgenden verfügt über die [erste-Schritte-Anleitungen](https://go.microsoft.com/fwlink/?linkid=860461).
* Herstellen einer Verbindung Ihres Geräts über mit [Powershell](../connect-your-device/PowerShell.md).

### <a name="on-the-pc"></a>Auf dem PC

* Stellen Sie sicher, dass Sie Visual Studio 2017 installiert haben.
* Installieren Sie die [Windows-Treiberkit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).  Sie müssen das SDK und die WDK zu installieren.
* Installieren Sie die Zertifikate aus, sodass der Treiber ordnungsgemäß signiert ist und auf Ihrem Gerät ausführen kann. Führen Sie eine Eingabeaufforderung mit erhöhten Rechten die unten aufgeführten Befehle ein:

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* Anwenden von Visual Studio die F5-Bereitstellung zu beheben. Führen Sie in der Eingabeaufforderung mit erhöhten Rechten die folgenden Befehle aus:

    1.  `cd %TEMP%` (Wechseln Sie Verzeichnis `c:\users\<usernsme>\Appdata\Local\Temp`)
    2.  `md “WdkTempFiles”` Erstellen Sie manuell eine "WdkTempFiles" Verzeichnis Dies ist eine problemumgehung für einen Fehler in den Tools und ausgeführt werden muss *nur einmal* auf dem PC.


## <a name="step-2--provision-device-with-visual-studio"></a>Schritt 2: Bereitstellen eines Geräts mit Visual Studio 
___
* Öffnen Sie Visual Studio, und wählen Sie **Treiber > Test > Geräte konfigurieren > Neues Gerät hinzufügen**
    * Wenn die Treiber-Option nicht angezeigt wird, überprüfen Sie, ob SDK installiert ist.

* In der **Gerätekonfiguration** Dialogfeld 
    * Geben Sie einen Benutzer benutzerfreundlichen Anzeigenamen für das Zielgerät
    * Wählen Sie Gerätetyp = mobiles Gerät
    * Sortieren Sie in der Liste angezeigt wird, indem IP-Adresse, und suchen Sie die Adresse für den IoT-Geräte, und wählen. Wenn zwei Einträge vorhanden sind, wählen Sie diejenige mit dem NULL-GUID.  Stellen Sie sicher, dass die Zeile ausgewählt ist: Es sollte blau hervorgehoben
    * Sind Sie am unteren Rand des Dialogfelds zwei Optionsfelder aus.  Wählen Sie diejenige, die besagt, dass **Gerät bereitstellen, und wählen Sie die Debuggereinstellungen**.  Wählen Sie **weiter**

* Auf der **konfigurieren Sie die Debuggereinstellungen**, legen Sie die entsprechenden Einstellungen.  Beachten Sie Folgendes:
   * Die MinnowBoardMax kann über das Netzwerk für das Debuggen verwenden.
       * Verwenden Sie Verbindungstyp **Netzwerk**
       * Wählen Sie einige Port: Standard kann verwendet werden
       * Wählen Sie einen Schlüssel: Standard kann verwendet werden
       * Wählen Sie die Host-IP des Computers mit visual Studio.  Verwenden Sie nicht die Autonetadresse (169.xxx).
       * Wählen Sie **weiter**
       
  ![Konfigurieren von Einstellungen zum Debuggen](../media/DriverDeployment/confdbgsettings.png)
       
    * Der Raspberry Pi verwendet für das Kerneldebuggen seriellen.
       *  Das Kabel des entsprechenden serielle Debuggen auf dem PI und dem Hostcomputer
       *  Wählen Sie **seriellen** für den Verbindungstyp
       *  Füllen Sie die restlichen Parameter nach Bedarf für den Raspberry Pi.
       *  Wählen Sie **weiter**

* Das WDK, mithilfe von VS, wird jetzt das IoT-Geräte bereitstellen.  TAEF und WDTF auf dem Gerät installiert werden, und das Gerät wird für die Livekernel-Debuggingfunktion gemäß den oben angegebenen Einstellungen eingerichtet werden.

* Nach Abschluss des Vorgangs wird das Gerät möglicherweise neu gestartet.  Die Fortschrittsanzeige auf der **Gerätekonfiguration** Status bietet, und wird abgeschlossen, wenn es sich bei der IoT-Geräte die Installation abgeschlossen ist. Drücken Sie **Fertig stellen**.

![Konfigurieren von Status](../media/DriverDeployment/confprogress.png)

* Das Gerät ist jetzt bereitgestellt und die **Test Gerätekonfiguration** Status wird **für treibertests konfiguriert**

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a>Schritt 3: Konfigurieren von Visual Studio-Treiber-Projekt
___    
1. Starten Sie Visual Studio im Administratormodus, und öffnen Sie visual Studio-Treiber-Projekt.
2. Stellen Sie sicher, dass die Version der Zielplattform das SDK auf Ihrem Entwicklungscomputer installiert übereinstimmt. Wählen Sie Projekteigenschaften im Projektmappen-Explorer-Fenster.  Wählen Sie unter Allgemeine Konfigurationseigenschaften stellen sicher, dass die Version der Zielplattform-Übereinstimmungen, die das SDK auf Ihrem Entwicklungscomputer installiert.  Sehen Sie die Version des SDK von der **Systemsteuerung > Programme > Programme und Funktionen**.
3. Klicken Sie unter **Projekt > Neues Element hinzufügen > Visual C++ > Windows-Treiber**Option **Paketmanifest** , und drücken Sie **hinzufügen**.

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` Datei wird dem Projekt hinzugefügt werden. Geben Sie in dieser Datei die Besitzer-Plattform, Komponente und Unterkomponente-Tags ein. 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. Legen Sie die Versionsnummer des Pakets an **Projekteigenschaften > PackageGen > Version**. Beachten Sie, dass jedes Mal, wenn Sie eine Installation/Neuinstallation des Treibers durchführen müssen, ist diese Versionsnummer sollte inkrementiert werden soll.

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. Klicken Sie unter **Projekteigenschaften > Treibersignierung > Testzertifikat**, zu testen (Phone OEM-testen-Zertifikat)

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. Wechseln Sie zu **Treiber installieren** , und wählen Sie **Bereitstellung**

![InstallOptions](../media/DriverDeployment/installOptions.png)

* Von der **Zielgerätname** Dropdownliste, wählen das Ziel, die oben in der im Rahmen des Bereitstellungsprozesses erstellt. Beachten Sie, dass die beiden Optionen für **installieren / Reinstall** und **schnell installieren**. Wählen Sie eine Option, und klicken Sie auf **Ok**.
* **Installieren Sie / Reinstall** wird für die Erstinstallation eines Treibers für das Ziel verwendet.  Dies das Verwenden des Windows Update-Stapels Treiberpaket installiert und kann einige Minuten dauern. Dies muss verwendet werden, jedes Mal, wenn die INF-Datei geändert wird. 
    
> [!TIP]
> Jedes Mal, wenn diese Option verwendet wird, um einen Treiber nach der ersten Installation installieren, muss die paketversionsnummer erhöht.

* **Schnelle Reinstall** kann verwendet werden, nachdem Sie ein Treiber installiert wurde, und es sind keine weiteren Änderungen der Treiber-INF-Datei die Auswirkungen der Registrierung auf.  Diese Methode umgeht den Installationsvorgang zu, alle Devnodes im Zusammenhang mit dem Treiber fährt, kopiert den Treiber und der Devnode Neustart.  Dies dauert ein Paar (< 20) Sekunden.

    
> [!WARNING]
> Diese Methode ist nicht erfolgreich ausgeführt werden kann – garantiert, wenn aus irgendeinem Grund ein Devnode Herunterfahren auf, um die Version des Treibers kann sein, der Vorgang fehl.  Dies kann aufgrund von fehlerhafte Hardware oder einer fehlerhaften anfänglichen Implementierung des Treibers sein.  Die Option zur Installation/Neuinstallation muss in diesem Fall verwendet werden.


Visual Studio-Projekt kann jetzt zum Erstellen und Bereitstellen eines Treibers auf dem Zielgerät. Wenn Sie den Beispiel-Gpiokmdfdemo-Treiber verwenden, Sie ACPI-Tabelle und die Kopie auf dem Zielgerät zu generieren müssen, und befolgen Sie dann die Schritte im [Erstellen des Treibers in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).


## <a name="step-4--build-and-deploy-driver"></a>Schritt 4: Erstellen und Bereitstellen der Treiber
___
Dies kann auf zwei Arten, mit der **F5** Schlüssel- und unter Verwendung der **bereitstellen** Option. Auf beide Arten der Treiber erstellt und bereitgestellt werden (d. h. installiert sie auf dem Gerät) und die F5 fügt Visual Studio-Kernel-Debugger an den Treiber installiert und geladen. 

Manche Benutzer bevorzugen die Verwendung der **bereitstellen** Funktionalität, und fügen Sie einen anderen Kernel-Debugger, z. B. WinDBG oder KD.  Dadurch kann höhere Flexibilität als die Verwendung von Visual Studio-Debugger bereitstellen.

### <a name="deploy"></a>Bereitstellen
1.  Mit der rechten Maustaste auf das Projekt im Projektmappen-explorer
2.  Wählen Sie **bereitstellen**

![Bereitstellen](../media/DriverDeployment/deploy.png) 

3.  Der Bereitstellungsprozess fortgesetzt werden soll.  Das IoT-Geräte nach der Bereitstellung neu gestartet wird, und den Bildschirm "Gears" sollte angezeigt werden, während der Installation ausgeführt wird.

Erstellen Sie Ausgabe ist der **Ausgabe** Fenster Bereitstellung Status auch in das Fenster "Ausgabe" bei der Installation wird abgeschlossen ist, das Gerät wird erneut neu gestartet und die Visual Studio-Ausgabefenster wird Erfolg oder Fehlschlag anzeigen.

### <a name="f5"></a>F5

1.  Fenster Vergewissern Sie sich, dass die Konfigurationen richtig sind – der aktuelle Build-Arch identisch mit der Ziel-Gerät-Arch ist.  Dies ist, in denen die Arch in den Zielnamen nützlich ist.  Das Ziel wird in das Feld Ansichtsname in der Menüleiste in Visual Studio auf der oberen mittleren rechten angezeigt werden.
2.  Drücken Sie **F5**.  Das Ziel wird erstellt, bereitgestellt und an der Visual Studio-Kernel-Debugger angefügt werden.

* Nach dem Neustart, stellen Sie sicher, dass PowerShell noch, verbunden ist, andernfalls erneut herstellen einer Verbindung mit dem Zielgerät mithilfe von PowerShell `enter-pssession` Befehl...


## <a name="known-issues"></a>Bekannte Probleme
___

### <a name="provisioning-errors"></a>Fehler bei der Bereitstellung
Eine Racebedingung während der Interaktion mit MinnowBoardMax kann zu einem gemeldeten Fehler während der Bereitstellung führen.  In der Tat erfolgreich die Bereitstellung in den meisten Fällen.

**Liste von Fehlern:**
 
* FEHLER: Task "Registrierung WDTF" konnte nicht erfolgreich abgeschlossen.
* FEHLER: Task "Konfigurieren von Kernel-Debugger-Einstellungen (mögliche Neustart)" konnte nicht erfolgreich abgeschlossen

**Problemumgehung:** Dieser Fehler kann sicherlich ignoriert werden.

**Details:**

Die folgende Fehlermeldung angezeigt, die der **Device Configuration Konfigurationsstatus** Dialogfeld:

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully 
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

An diesem Punkt sicher klicken Sie auf die **Fertig stellen** und klicken Sie dann die **übernehmen** und **OK**.

Dies ist eine unkritisch gebildet, indem eine Racebedingung verursacht ein Ergebnis Protokoll fehlerhaft zu sein. Dies kann anhand der Protokolldatei in den folgenden Bereich überprüft werden:

1. Öffnen Sie eine FTP-Verbindung auf die IP-Adresse des Geräts (wie auf dem Bildschirm gezeigt) die `Data/test/bin/DriverTest/Run` Verzeichnis.
Beispiel:
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. Kopieren der `Configuring_computer_settings_(possible_reboot)_identifier.wtl` Datei auf Ihrem lokalen Computer.  Beachten Sie, dass der Name der Protokolldatei der Name der fehlerhaften Aufgabe entspricht.
3. Öffnen Sie die Datei im Editor
4. Führen Sie einen Bildlauf zum Ende des Protokolls.  Der folgende Text werden vorhanden ist, gibt an, dass die Bereitstellung erfolgreich ist.

```
<PFRollup 
    Total="1" 
    Passed="1" 
    Failed="0" 
    Blocked="0" 
    Warned="0" 
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```

