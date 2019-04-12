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
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="02ae9-104">Mithilfe des vereinheitlichte Schreibfilters (, UWF) auf Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="02ae9-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="02ae9-105">Der dynamische Datenträger wird für die UWF nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="02ae9-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="02ae9-106">Die Unified Write Filter (, UWF) ist eine Funktion, die physischen Medien vor datenschreibvorgänge schützt.</span><span class="sxs-lookup"><span data-stu-id="02ae9-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="02ae9-107">UWF fängt alle Schreibversuche für ein geschütztes Volume ab und leitet diese zu einer virtuellen Überlagerung weiter.</span><span class="sxs-lookup"><span data-stu-id="02ae9-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="02ae9-108">Dies verbessert die Zuverlässigkeit und Stabilität des Geräts und schont Geräte, die sich durch Schreibvorgänge abnutzen, z. B. Medien mit Flashspeicher wie Solid-State-Laufwerke.</span><span class="sxs-lookup"><span data-stu-id="02ae9-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="02ae9-109">Lesen Sie unsere Dokumentation auf der [vereinheitlichte Schreibfilter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="02ae9-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="02ae9-110">Wie Sie UWF installieren auf einem Gerät mit Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="02ae9-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="02ae9-111">Wenn Sie nicht die aktuelle Version des Windows 10 IoT Core Kits noch verfügen, herunterladen und Installieren der [Windows 10 IoT Core Pakete](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span><span class="sxs-lookup"><span data-stu-id="02ae9-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="02ae9-112">Basierend auf Ihrem Gerätearchitektur, kopieren Sie UWF-Pakete ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` und `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) von Ihrem PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) auf dem Gerät (z. B. mit [Windows-Dateifreigabe](../manage-your-device/WindowsFileSharing.md)).</span><span class="sxs-lookup"><span data-stu-id="02ae9-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="02ae9-113">Starten Sie [SSH](../connect-your-device/SSH.md) oder [Powershell](../connect-your-device/PowerShell.md) und greifen Sie auf Ihrem Gerät Windows 10 IoT Core ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="02ae9-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="02ae9-114">Führen Sie über SSH oder mit Powershell folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="02ae9-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="02ae9-115">Wechseln Sie zum Verzeichnis, in dem Sie die Dateien kopiert haben</span><span class="sxs-lookup"><span data-stu-id="02ae9-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="02ae9-116">Führen Sie diese Befehle zum Installieren der Pakete in Ihr IoT-geräteimage System:</span><span class="sxs-lookup"><span data-stu-id="02ae9-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="02ae9-117">Das Gerät wird gestartet wird, um die Betriebssystemversion aktualisieren, UWF Features installieren und neu starten, um die MainOS.</span><span class="sxs-lookup"><span data-stu-id="02ae9-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="02ae9-118">Sobald das Gerät wieder auf die MainOS verfügbar ist, ist die UWF-Funktion bereit und zur Verwendung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="02ae9-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="02ae9-119">Dies kann durch Eingabe überprüft werden ```uwfmgr.exe``` in Ihre Powershell- oder SSH-Fenster.</span><span class="sxs-lookup"><span data-stu-id="02ae9-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![uwfmgr.exe on Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="02ae9-121">Wie Sie Ihre benutzerdefinierten FFU UWF einschließt</span><span class="sxs-lookup"><span data-stu-id="02ae9-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="02ae9-122">Hinzufügen **IOT_UNIFIED_WRITE_FILTER** Funktions-Id an den OEM-Eingabedatei</span><span class="sxs-lookup"><span data-stu-id="02ae9-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="02ae9-123">Erstellen Sie die Image\FFU.</span><span class="sxs-lookup"><span data-stu-id="02ae9-123">Create the image\FFU.</span></span> <span data-ttu-id="02ae9-124">Lesen [erstellen Sie eine Basis-Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="02ae9-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="02ae9-125">Wie Sie mit UWF</span><span class="sxs-lookup"><span data-stu-id="02ae9-125">How to Use UWF</span></span>

<span data-ttu-id="02ae9-126">UWF kann mit dem Tool uwfmgr.exe über eine Powershell- oder SSH-Sitzung konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="02ae9-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="02ae9-127">Lesen [ `uwfmgr.exe` Tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) für die verfügbaren Optionen mit Ausnahme von einigen unten aufgeführten Befehle, die nicht IoT Core unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="02ae9-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="02ae9-128">Prüfen Sie die Standardeinstellungen der Überlagerung Konfigurationen und Ihren Anforderungen entsprechend angepasst.</span><span class="sxs-lookup"><span data-stu-id="02ae9-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="02ae9-129">UWF kann auch konfiguriert werden, über die Verwaltung mobiler Geräte mithilfe von Channel [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span><span class="sxs-lookup"><span data-stu-id="02ae9-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="02ae9-130">Beispielsweise die folgende Kombination von Befehlen Uwfmgr aktivieren und konfigurieren, dass Sie um Laufwerk C zu schützen.</span><span class="sxs-lookup"><span data-stu-id="02ae9-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  `uwfmgr.exe filter enable`      <span data-ttu-id="02ae9-131">Ermöglicht den Schreibfilter</span><span class="sxs-lookup"><span data-stu-id="02ae9-131">Enables the write filter</span></span>
  <br>
  `uwfmgr.exe volume protect c:`  <span data-ttu-id="02ae9-132">Wird das Volume C</span><span class="sxs-lookup"><span data-stu-id="02ae9-132">Protects the Volume C</span></span>
  <br>
  `shutdown /r /t 0`              <span data-ttu-id="02ae9-133">Neustart des Geräts, damit die Write-filtereinstellungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="02ae9-133">Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="02ae9-134">*Starten Sie neu* ist erforderlich, um alle Uwfmgr Einstellungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="02ae9-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="02ae9-135">Schützen eines Datenvolumes</span><span class="sxs-lookup"><span data-stu-id="02ae9-135">Protecting a Data Volume</span></span>

<span data-ttu-id="02ae9-136">Unter Verwendung der GUID für das Volume kann die Datenmenge im IoT Core geschützt werden.</span><span class="sxs-lookup"><span data-stu-id="02ae9-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="02ae9-137">Die GUID für den verfügbaren Volumes finden Sie über den folgenden Befehl aus</span><span class="sxs-lookup"><span data-stu-id="02ae9-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Schützen von Volumes auf Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="02ae9-139">Empfohlene Ausschlüsse</span><span class="sxs-lookup"><span data-stu-id="02ae9-139">Recommended Exclusions</span></span>
<span data-ttu-id="02ae9-140">Wenn das Volumen für Daten zu schützen, empfehlen wir, dass Sie hinzufügen, die für die Wartung und Protokollierung-Ordner, die von Windows-OS-Dienst zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="02ae9-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="02ae9-141">Die Ausschlüsse hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="02ae9-141">To add the exclusions:</span></span> `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="02ae9-142">UWF-Wartung geschützte Geräte</span><span class="sxs-lookup"><span data-stu-id="02ae9-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="02ae9-143">Ab Windows 10 IoT Core-Version 1709, 16299-Version, die wichtigsten BS-Volume ("c:"\) mit UWF geschützt und verarbeitet werden können *automatisch* ohne spezielle Schritte.</span><span class="sxs-lookup"><span data-stu-id="02ae9-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="02ae9-144">Die folgenden Schritte sind erforderlich, um den Dienst UWF geschützte Geräte mit Volumes von geschützten Daten.</span><span class="sxs-lookup"><span data-stu-id="02ae9-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* `uwfmgr.exe filter disable` <span data-ttu-id="02ae9-145">UWF deaktivieren</span><span class="sxs-lookup"><span data-stu-id="02ae9-145">Disable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="02ae9-146">Neustart-Gerät für UWF deaktivieren</span><span class="sxs-lookup"><span data-stu-id="02ae9-146">Reboot device to disable UWF</span></span>
* <span data-ttu-id="02ae9-147">Aktivieren Sie die Wartung (mit Bereitstellung Paket oder MDM updaterichtlinie festlegen)</span><span class="sxs-lookup"><span data-stu-id="02ae9-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="02ae9-148">Beachten Sie, die das Gerät automatisch neu, zum Ausführen der Wartung gestartet wird aktualisiert</span><span class="sxs-lookup"><span data-stu-id="02ae9-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* `uwfmgr.exe filter enable` <span data-ttu-id="02ae9-149">UWF aktivieren</span><span class="sxs-lookup"><span data-stu-id="02ae9-149">Enable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="02ae9-150">Neustart-Gerät für UWF aktivieren</span><span class="sxs-lookup"><span data-stu-id="02ae9-150">Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="02ae9-151">Nicht unterstützte uwfmgr.exe-Befehle</span><span class="sxs-lookup"><span data-stu-id="02ae9-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="02ae9-152">**UWF-Wartung Modus** wird in IoT Core nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="02ae9-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

`uwfmgr.exe` <span data-ttu-id="02ae9-153">auf Windows 10 IoT Core unterstützt keine Befehle, die unten aufgeführten.</span><span class="sxs-lookup"><span data-stu-id="02ae9-153">on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
