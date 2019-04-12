---
title: Mithilfe des vereinheitlichte Schreibfilters
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Unified Write Filter, die zum Schützen von physischen Medien vor datenschreibvorgänge verwenden.
keywords: Sicherheit von Windows Iot, Unified Write Filter, Arbeitsspeicher, Speichermedien
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514141"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>Mithilfe des vereinheitlichte Schreibfilters (, UWF) auf Windows 10 IoT Core

> [!WARNING]
> Der dynamische Datenträger wird für die UWF nicht unterstützt.

Die Unified Write Filter (, UWF) ist eine Funktion, die physischen Medien vor datenschreibvorgänge schützt. UWF fängt alle Schreibversuche für ein geschütztes Volume ab und leitet diese zu einer virtuellen Überlagerung weiter. Dies verbessert die Zuverlässigkeit und Stabilität des Geräts und schont Geräte, die sich durch Schreibvorgänge abnutzen, z. B. Medien mit Flashspeicher wie Solid-State-Laufwerke.

Lesen Sie unsere Dokumentation auf der [vereinheitlichte Schreibfilter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) für Weitere Informationen.

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>Wie Sie UWF installieren auf einem Gerät mit Windows 10 IoT Core

* Wenn Sie nicht die aktuelle Version des Windows 10 IoT Core Kits noch verfügen, herunterladen und Installieren der [Windows 10 IoT Core Pakete](https://www.microsoft.com/en-us/software-download/windows10iotcore).
* Basierend auf Ihrem Gerätearchitektur, kopieren Sie UWF-Pakete ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` und `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) von Ihrem PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) auf dem Gerät (z. B. mit [Windows-Dateifreigabe](../manage-your-device/WindowsFileSharing.md)).
* Starten Sie [SSH](../connect-your-device/SSH.md) oder [Powershell](../connect-your-device/PowerShell.md) und greifen Sie auf Ihrem Gerät Windows 10 IoT Core ausgeführt.
* Führen Sie über SSH oder mit Powershell folgende Schritte aus:
  * Wechseln Sie zum Verzeichnis, in dem Sie die Dateien kopiert haben
    * `cd C:\<dir>`
  * Führen Sie diese Befehle zum Installieren der Pakete in Ihr IoT-geräteimage System:
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* Das Gerät wird gestartet wird, um die Betriebssystemversion aktualisieren, UWF Features installieren und neu starten, um die MainOS.
* Sobald das Gerät wieder auf die MainOS verfügbar ist, ist die UWF-Funktion bereit und zur Verwendung zur Verfügung. Dies kann durch Eingabe überprüft werden ```uwfmgr.exe``` in Ihre Powershell- oder SSH-Fenster.

  ![uwfmgr.exe on Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>Wie Sie Ihre benutzerdefinierten FFU UWF einschließt 

* Hinzufügen **IOT_UNIFIED_WRITE_FILTER** Funktions-Id an den OEM-Eingabedatei 
* Erstellen Sie die Image\FFU. Lesen [erstellen Sie eine Basis-Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) Anweisungen.


## <a name="how-to-use-uwf"></a>Wie Sie mit UWF

UWF kann mit dem Tool uwfmgr.exe über eine Powershell- oder SSH-Sitzung konfiguriert werden.
Lesen [ `uwfmgr.exe` Tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) für die verfügbaren Optionen mit Ausnahme von einigen unten aufgeführten Befehle, die nicht IoT Core unterstützt werden.
Prüfen Sie die Standardeinstellungen der Überlagerung Konfigurationen und Ihren Anforderungen entsprechend angepasst.

UWF kann auch konfiguriert werden, über die Verwaltung mobiler Geräte mithilfe von Channel [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).


* Beispielsweise die folgende Kombination von Befehlen Uwfmgr aktivieren und konfigurieren, dass Sie um Laufwerk C zu schützen.

  `uwfmgr.exe filter enable`      Ermöglicht den Schreibfilter
  <br>
  `uwfmgr.exe volume protect c:`  Wird das Volume C
  <br>
  `shutdown /r /t 0`              Neustart des Geräts, damit die Write-filtereinstellungen wirksam werden.

*Starten Sie neu* ist erforderlich, um alle Uwfmgr Einstellungen wirksam werden. 


## <a name="protecting-a-data-volume"></a>Schützen eines Datenvolumes

Unter Verwendung der GUID für das Volume kann die Datenmenge im IoT Core geschützt werden. Die GUID für den verfügbaren Volumes finden Sie über den folgenden Befehl aus

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Schützen von Volumes auf Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>Empfohlene Ausschlüsse
Wenn das Volumen für Daten zu schützen, empfehlen wir, dass Sie hinzufügen, die für die Wartung und Protokollierung-Ordner, die von Windows-OS-Dienst zugegriffen werden.

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

Die Ausschlüsse hinzufügen: `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>UWF-Wartung geschützte Geräte

> [!Note]
> Ab Windows 10 IoT Core-Version 1709, 16299-Version, die wichtigsten BS-Volume ("c:"\) mit UWF geschützt und verarbeitet werden können *automatisch* ohne spezielle Schritte.

Die folgenden Schritte sind erforderlich, um den Dienst UWF geschützte Geräte mit Volumes von geschützten Daten.

* `uwfmgr.exe filter disable` UWF deaktivieren
* `shutdown /r /t 0` Neustart-Gerät für UWF deaktivieren
* Aktivieren Sie die Wartung (mit Bereitstellung Paket oder MDM updaterichtlinie festlegen)
   * Beachten Sie, die das Gerät automatisch neu, zum Ausführen der Wartung gestartet wird aktualisiert
* `uwfmgr.exe filter enable` UWF aktivieren
* `shutdown /r /t 0` Neustart-Gerät für UWF aktivieren

## <a name="unsupported-uwfmgrexe-commands"></a>Nicht unterstützte uwfmgr.exe-Befehle

**UWF-Wartung Modus** wird in IoT Core nicht unterstützt.

`uwfmgr.exe` auf Windows 10 IoT Core unterstützt keine Befehle, die unten aufgeführten.

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
