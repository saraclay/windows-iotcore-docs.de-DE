---
title: Aktivieren der sicheren Start, BitLocker und Device Guard auf Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Aktivieren der sicheren Start, BitLocker und Device Guard auf Windows 10 IoT Core
keywords: Windows Iot, sicherer Start, BitLocker, Device Guard "," Sicherheit "," schlüsselfertige Sicherheit
ms.openlocfilehash: 68698a1b440b297eb9bfa9223bd324ce330386b9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513601"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>Aktivieren der sicheren Start, BitLocker und Device Guard auf Windows 10 IoT Core

## <a name="introduction"></a>Einführung

Mit der Version der Creators Update verbessert die Windows 10 IoT Core seine Sicherheit featureangebote zum sicheren UEFI-Start, BitLocker-Geräteverschlüsselung und Device Guard enthalten.  Diese können die Gerät-Generatoren erstellen vollständig Windows IoT-Geräte, die auf viele verschiedene Arten von Angriffen stabil sind gesperrt.  Zusammen bieten diese Funktionen den optimalen Schutz, der sicherstellt, dass eine Plattform definierte Weise gestartet wird, während Sperrung unbekannt und zum Schutz von Benutzerdaten durch die Verwendung von geräteverschlüsselung.

### <a name="secure-boot"></a>Sicherer Start

Sichere UEFI-Start ist die erste Richtlinie Erzwingungspunkt, befindet sich in UEFI.  Sie schränkt das System, um die Ausführung von Binärdateien, die von einer angegebenen Stelle signiert nur zu ermöglichen. Dieses Feature verhindert unbekannten Code ausgeführt wird, auf der Plattform und potenzielle Beeinträchtigung Ihres Sicherheitsstatus es.

### <a name="bitlocker-device-encryption"></a>BitLocker-Geräteverschlüsselung

Windows 10 IoT Core implementiert auch eine vereinfachte Version der BitLocker-Geräteverschlüsselung, IoT-Geräten vor Offlineangriffen schützen.  Diese Funktion ist in hohem Maße auf das Vorhandensein eines TPM auf der Plattform, einschließlich des erforderlichen preOS-Protokolls in UEFI, die der erforderlichen Messungen. Diesen preOS-Messungen stellen Sie sicher, dass das Betriebssystem später wurde der wie das Betriebssystem gestartet wurde; Es erzwingt allerdings keine Ausführung Einschränkungen.

> [!TIP]
> BitLocker-Funktionalität auf Windows 10 IoT Core ermöglicht für die automatische Verschlüsselung des Betriebssystem auf NTFS basierende Volumes bei der alle verfügbaren NTFS-Datenvolumes an ihn binden.  Es ist erforderlich, um sicherzustellen, dass das Volume EFIESP GUID NA hodnotu nastaven _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.

### <a name="device-guard-on-windows-iot-core"></a>Device Guard unter Windows IoT Core

Die meisten IoT-Geräte werden als Geräte mit festen Funktionen erstellt.  Dies bedeutet, dass Gerät-Generatoren wissen genau einer der Firmware, Betriebssystem, Treiber und Anwendungen auf einem Gerät ausgeführt werden sollen.  Diese Informationen können wiederum sein verwendet, um vollständig Sperren ein IoT-Geräts nur die Ausführung von bekannten und vertrauenswürdigen Code erlaubt.  Device Guard auf Windows 10 IoT Core können IoT-Geräten zu schützen, sicherstellen, dass gesperrte Geräte Unbekannter oder nicht vertrauenswürdiger ausführbarer Code ausgeführt werden kann.

## <a name="locking-down-iot-devices"></a>Sperren Sie IoT-Geräte

Die folgenden Überlegungen müssen vorgenommen werden, damit auf Sperrung einer Windows-IoT-Geräte...

### <a name="uefi-platform--secure-boot"></a>UEFI-Plattform und sicheren Start

Um Device Guard-Funktionen nutzen zu können, ist es erforderlich, um sicherzustellen, dass die Startbinärdateien von UEFI-Firmware angemeldet sind und nicht manipuliert sein.  Sichere UEFI-Start ist die erste Richtlinie Erzwingungspunkt, befindet sich in UEFI.  Verhindert eine Manipulation, indem Sie einschränken, das System, um die Ausführung der Startbinärdateien, die von einer angegebenen Stelle signiert nur zu ermöglichen. Weitere Informationen zu sicherer Start, zusammen mit schlüsselerstellung und Anleitung zur änderungsverwaltung, steht [hier](https://technet.microsoft.com/library/dn747883.aspx).

### <a name="configurable-code-integrity-cci"></a>Konfigurierbare Codeintegrität (CCI)

Codeintegritätsrichtlinie (CI) erhöht die Sicherheit des Betriebssystems durch Überprüfen der Integrität eines Treibers oder einer Anwendung jedes Mal, wenn sie in den Arbeitsspeicher geladen wird. CI enthält zwei Hauptkomponenten – Kernel Mode Code Integrity (KMCI) und Gruppenrichtlinien-Verwaltungskonsole (User-Modus Code Integrity, UMCI).

Konfigurierbare Code Integrity (CCI) ist ein Feature in Windows 10, die ermöglicht das Gerät-Generatoren zum Sperren eines Geräts ist und nur ausführen, und führen Sie Code aus, die signiert und vertraut ist.  Zu diesem Zweck können Gerät Generatoren erstellen Sie eine codeintegritätsrichtlinie auf ein "goldenes" Gerät (endgültige Version von Hardware und Software) und klicken Sie dann sichern und diese Richtlinie auf allen Geräten am Herstellerstandort anwenden.

Weitere Informationen zum Bereitstellen von codeintegritätsrichtlinien, Überwachung und Erzwingung, sehen Sie sich die aktuelle Technet-Dokumentation [hier](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).

## <a name="turnkey-security-on-iot-core"></a>Sofort einsetzbare Sicherheit unter IoT Core

Um einfache Aktivierung der wichtigsten Sicherheitsfeatures auf Geräten mit IoT Core zu erleichtern, stellt Microsoft eine sofort einsatzbereite "Security Package" bereit, die Geräte-Generatoren erstellen ermöglicht IoT-Geräte vollständig gesperrt.  Dieses Paket helfen:

* Bereitstellen sicherer Start-Schlüsseln und Aktivieren des Features auf unterstützten Plattformen für IoT
* Setup und Konfiguration der geräteverschlüsselung, die die Verwendung von BitLocker 
* Initiieren die Gerätesperre nur und ermöglicht die Ausführung von signierten Anwendungen und Treibern

### <a name="pre-requisites"></a>Voraussetzungen

* Einem PC mit Windows 10 Enterprise
* [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) : erforderlich für die Generierung des Zertifikats
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) : erforderlich für die Generierung der CAB-Datei
* Referenzplattform - Release-Hardware mit Protokollversand-Firmware, Betriebssystem, Treiber und Anwendungen erforderlich, damit der letzten Sperrung werden

### <a name="development-iot-devices"></a>Entwicklung, IoT-Geräte

Windows 10 IoT Core funktioniert mit verschiedenen Silicons, die in Hunderten von Geräten genutzt werden. Von der [vorgeschlagene Geräten für IoT-Entwicklung](../learn-about-hardware/SoCsAndCustomBoards.md), geben Sie die folgenden Firmware-TPM-Funktionalität standardmäßig zusammen mit den sicheren Start "," kontrollierter Start "," BitLocker "und" Device Guard-Funktionen:

* Qualcomm DragonBoard 410c

    Um den sicheren Start zu aktivieren, kann es erforderlich, für die Bereitstellung RPMB sein. Sobald die eMMC mit Windows 10 IoT Core per flashvorgang wurde hat (gemäß den Anweisungen [hier](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), drücken Sie [Power] + [Vol. +] + [Vol-] gleichzeitig auf dem Gerät, die beim Einschalten, und wählen Sie "Provision-RPMB" im Menü BDS. *Beachten Sie, dass dies ein Schritt nicht rückgängig gemacht werden.*

* Intel MinnowBoardMax

    Für den Intel MinnowBoard maximalen, Firmwareversion muss 0.82 oder höher (Abrufen der [neueste Firmware](https://firmware.intel.com/projects/minnowboard-max)). Um TPM-Funktionen zu aktivieren, schalten Sie das Board mit einer Tastatur & anzeigen angefügt, und drücken Sie F2, um UEFI-Setup. Wechseln Sie zu _-Geräte-Manager -> System-Setup -> Konfiguration -> PTT_ und legen ihn auf  _&lt;aktivieren&gt;_. Drücken Sie F10, um die Änderungen zu speichern, und fahren Sie fort mit einem Neustart der Plattform.

> [!NOTE]
> Raspberry Pi 2 und 3 unterstützen keine TPM, und wir können nicht so konfigurieren Sie Lockdown-Szenarien.

### <a name="generate-lockdown-packages"></a>Lockdown-Pakete generieren

1. Herunterladen der [DeviceLockDown Skript](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) Paket, das alle zusätzlichen Tools und Skripts, die zum Konfigurieren und Geräte Sperren erforderlich enthält
2. Starten Sie eine Administrative PowerShell (PS)-Konsole auf Ihrem Windows 10-PC aus, und navigieren Sie zum Speicherort des heruntergeladenen Skripts.
3. Bereitstellen Sie Ihrer Hardware-Referenzplattform (das entsperrt Image ausführen) auf Ihren PC über das Netzwerk freigeben verwenden

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. Generieren von Schlüsseln für die Verwendung von Ihrem Gerät

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * Die Schlüssel und Zertifikate werden in der angegebene Ausgabeordner mit geeigneten Suffix generiert.
    * **Schützen Sie Ihre generierten Schlüssel** wie das Gerät Binärdateien vertrauen wird mit diesen Schlüsseln signiert sind, nur nach dem Sperren.
    * Sie können diesen Schritt überspringen und verwenden die vorab generierten Schlüssel nur zu Testzwecken

5. Installieren Sie die generierten PFX-Zertifikate, indem Sie durch Klicken auf die PFX-Dateien direkt oder über die folgenden Powershell-Befehl

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. Konfigurieren von _"Settings.xml"_

    * Abschnitt "Allgemein": Geben Sie die Paketverzeichnisse
    * Abschnitt "Tools": Legen Sie den Pfad für die tools
        * Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * SDK-Version, die auf Ihrem Computer installiert ist, klicken Sie unter `C:\Program Files (x86)\Windows Kits\10\`
    * SecureBoot-Abschnitt: Geben Sie die Schlüssel, die für den sicheren Start (PK und SB-Schlüssel)
    * BitLocker-Abschnitt: Geben Sie ein Zertifikat für Bitlocker die datenwiederherstellung (DRA-Schlüssel)
    * SIPolicy-Abschnitt: Geben Sie die Zertifikate, die vertrauenswürdig sind
        * ScanPath: Pfad des Geräts für die Überprüfung von Binärdateien `\\a.b.c.d\C$`
        * aktualisieren: Signaturgeber des der SIPolicy (PAUTH Schlüssel)
        * Benutzer: Benutzermodus-Zertifikate (UMCI Schlüssel) 
        * Kernel   : Kernelmodus-Zertifikate (KMCI Schlüssel)
    * Verpacken: Geben Sie die Einstellungen für die Paket-Generierung

> [!IMPORTANT]
> Um Tests während des anfänglichen Entwicklungszyklus zu unterstützen, hat Microsoft vorab generierten Schlüssel und Zertifikate bei Bedarf bereitgestellt.  Dies bedeutet, dass Microsoft Test, Entwicklung und Pre-Release-Binärdateien als vertrauenswürdig eingestuft werden.  Während der Endprodukt-Erstellung und Generierung einer Bildvorschau werden Sie sicher, dass diese Zertifikaten zu entfernen und Ihre eigenen Schlüssel verwenden, um sicherzustellen, dass ein Gerät vollständig gesperrtes.

> [!TIP]
> Die von Microsoft App Store-apps können ihm erlaubt werden, durch das Microsoft Marketplace PCA 2011-Zertifikat in der Konfiguration einschließlich _"Settings.xml"_: 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

6. Führen Sie 6. die folgenden Befehle zum Generieren der erforderlichen Pakete:

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a>Testen Sie die Sperrung von Paketen
Sie können die generierten Pakete testen, indem die manuell über die folgenden Schritte auf einem entsperrten Gerät installiert werden

1. Flash-das Gerät mit dem entsperrt Image (Image für die Überprüfung in den vorherigen Schritt verwendet).
2. Verbinden mit dem Gerät ([mithilfe von SSH](../connect-your-device/SSH.md) oder [Powershell](../connect-your-device/PowerShell.md))
3. Kopieren Sie die folgenden CAB-Dateien an das Gerät in einem Verzeichnis, z. B. `c:\OemInstall`
    * OEM.Custom.Cmd.cab
    * OEM.Security.BitLocker.cab
    * OEM.Security.SecureBoot.cab
    * OEM.Security.DeviceGuard.cab
4. Bereitstellen der generierten Pakete von akustischen die folgenden Befehle zu initiieren

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    Wenn Sie benutzerdefinierte Images verwenden, müssen Sie *überspringen* diese Datei manuell bearbeiten, und wählen Sie die `c:\windows\system32\oemcustomization.cmd` mit dem Inhalt, die in verfügbaren `Output\OEMCustomization\OEMCustomization.cmd` Datei

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. Das Gerät wird neu gestartet, in dem Aktualisieren der Betriebssystemversion (mit Gears) zum Installieren der Pakete und wird neu zu Hauptbetriebssystems erneut gestartet.  Sobald das Gerät wieder MainOS neu gestartet, wird der sichere Start aktiviert werden und SIPolicy beauftragt werden soll.
7. Neustart des Geräts erneut aus, um die Bitlocker-Verschlüsselung zu aktivieren.
8. Testen Sie die Sicherheitsfunktionen zu nutzen
    * **SecureBoot** : versuchen Sie es `bcdedit /debug on` , erhalten Sie eine Fehlermeldung, dass der Wert von der Richtlinie für sicheren Start geschützt ist.
   * **BitLocker** : Um zu überprüfen, Bitlocker Encryption abgeschlossen wurde, führen Sie<p>
        `sectask.exe -waitenableforcompletion 1`<p>
        Wenn sie auf "0" zurückgibt, bedeutet, dass an, dass alle Laufwerke auf dem System Bitlockered erfolgreich gewesen.  Ein anderen Rückgabecode ist Fehler.<p>
        *Zusätzliche Syntax*<p>
         `-waitenableforcompletion [timeout]` <p>
        = > Warten Sie, bis BitLocker-Verschlüsselung auf NTFS-Volumes abgeschlossen ist.<p>
        = > Timeout in Sekunden warten, aktivieren Sie zum Abschließen.<p>
        = > Wenn das Timeout nicht angegeben ist, wartet er auf unbestimmte Zeit oder bis zum Abschluss aktivieren.<p>
        Gibt zurück: <p>
        0 : BitLocker-Verschlüsselung wurde erfolgreich abgeschlossen wurde, ist Volume Bitlocker verschlüsselt.<p>
        ERROR_TIMEOUT: Timeout beim Warten auf Abschluss des Vorgangs Encryption noch in Bearbeitung.<p>
        Fehler / andere Code: Gibt zurück, die vom Schließfach für Bit-Dienst zurückgegebene Fehlercode.

    * **DeviceGuard** : Führen Sie alle nicht signierten Binär- oder eine Binärdatei mit Zertifikat nicht in der Liste SIPolicy signiert, und bestätigen Sie, dass er nicht ausgeführt.

### <a name="generate-lockdown-image"></a>Generieren Sie Lockdown-Abbild

Nach dem Überprüfen, dass die Sperrung Pakete gemäß den zuvor definierten Einstellungen arbeiten, kann Sie dann diese Pakete in das Abbild enthalten, anhand der unten angegebenen Schritte aus. Lesen [die Fertigung für IoT](https://aka.ms/iotcoreguide) Anweisungen für benutzerdefiniertes Image erstellen.

1. Aktualisieren Sie in der arbeitsbereichsverzeichnis die folgenden Dateien aus dem obigen generierte Ausgabeverzeichnis
    * SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db.bin
      * SetVariable_kek.bin
      * SetVariable_pk.bin
    * BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask.xml
      * Security.Bitlocker.wm.xml
      * setup.bitlocker.cmd
    * DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn.p7b
      * SIPolicyOff.p7b
  
2. Hinzufügen von RetailOEMInput.xml und TestOEMInput.xml unter dem Verzeichnis "ProductName" mit der Sperrung Paketkennung-Funktion
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. Image neu generieren
    * `buildpkg all` (Dies generiert neue Lockdown-Pakete, die Grundlage der oben genannten Dateien für Gruppenrichtlinien)
    * `buildimage ProductName test(or)retail`  (Dies generiert neue Flash.ffu)
4. Das Gerät mit diesem neuen Flash.ffu Flash, und überprüfen Sie die Sicherheitsfunktionen zu nutzen.

Finden Sie unter [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) als Beispiel für eine Sperrung Dragon Board-Konfiguration.

Sie können alternativ Sicherheitspakete der IoTCore Shell selbst generieren, finden Sie unter [hinzufügen Sicherheitspakete](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) Details.


### <a name="developing-with-codesigning-enforcement-enabled"></a>Entwickeln mit CodeSigning Erzwingung aktiviert

Sobald die Pakete werden generiert, und Sperren aktiviert ist, müssen alle Binärdateien in das Image eingefügt werden, während der Entwicklung ordnungsgemäß signiert werden. Stellen Sie sicher, dass die Binärdateien im Benutzermodus mit dem Schlüssel signiert sind _. \Keys\ ***-UMCI.pfx_. Für die Kernelmodus-Signieren wie z. B. für Treiber, Sie müssen Ihre eigenen Signaturschlüssel geben an, und stellen Sie sicher, dass sind diese ebenfalls in der oben genannten SIPolicy enthalten.

### <a name="unlocking-encrypted-drives"></a>Entsperren verschlüsselter Laufwerke

Beim Entwickeln und testen kann beim Lesen von Inhalt aus einer verschlüsselten Gerät offline (z. B. SD-Karte für MinnowBoardMax oder des DragonBoard eMMC über USB-Massenspeicher-Modus), "Diskpart" verwendet werden (wir MainOS und Datenvolumen einen Laufwerkbuchstaben zuweisen Nehmen wir v: MainOS und w für Daten).
Die Volumes werden als gesperrt angezeigt und müssen manuell entsperrt werden. Dies kann erfolgen auf jedem Computer, die die OEM-DRA.pfx-Zertifikat installiert ist (in enthalten die [DeviceLockDown Beispiel](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)). Installieren Sie die PFX-Datei, und führen Sie die folgenden Befehle aus einer administrativen Eingabeaufforderung aus:

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

Wenn die Inhalte häufig offline zugegriffen werden kann müssen, kann BitLocker automatisches Entsperren für die Volumes eingerichtet werden nach der ersten entsperren mit den folgenden Befehlen:

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>Deaktivierung von BitLocker

Muss vorübergehend deaktivieren, BitLocker, sollte es entstehen failovergruppe eine remote-PowerShell-Sitzung mit Ihrem IoT-Geräte und führen Sie den folgenden Befehl: `sectask.exe -disable`.  
**Hinweis**: Geräteverschlüsselung wird beim Start der nachfolgende Gerät erneut aktiviert, wenn die Verschlüsselung der geplanten Aufgabe deaktiviert wird.

### <a name="disabling-device-guard"></a>Deaktivieren von Device Guard

Das Skript sofort verwendbaren generiert SIPolicyOn.p7b und SIPolicyOff.p7b-Dateien im Ordner "".
Die wm.xml Pakete die SIPolicyOn.p7b und platziert ihn in das System als SIPolicy.p7b.

Zum Beispiel:

```
C:\src\iot-adk-addonkit.db410c\TurnkeySecurity\QCDB\Output\DeviceGuard\Security.DeviceGuard.wm.xml
…
    <files>
        <file
            destinationDir="$(runtime.bootDrive)\efi\microsoft\boot"
            source="SIPolicyOn.p7b"
            name="SIPolicy.p7b" />
    </files>
..

```

Wenn Sie ein Paket, akzeptiert die SIPolicyOff.p7b-Datei, und platziert es als ein Sipolicy.p7b, erstellen, Sie dieses Paket gilt und die Device Guard deaktiviert jetzt ist.



