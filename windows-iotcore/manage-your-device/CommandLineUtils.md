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
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="f8089-104">Windows 10 IoT Core-Befehlszeile "utils"</span><span class="sxs-lookup"><span data-stu-id="f8089-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="f8089-105">Möchten Sie um einige der Einstellungen auf dem Gerät zu konfigurieren?</span><span class="sxs-lookup"><span data-stu-id="f8089-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="f8089-106">Die folgenden Tools stehen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="f8089-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="f8089-107">Verwenden von PowerShell zum Ausführen dieser Befehle nach [an Ihr Gerät anschließen](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="f8089-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f8089-108">Diese Tools werden nicht vorab geladen – müssen Sie die entsprechenden Feature-IDs, rufen Sie diese Tools im Image enthalten.</span><span class="sxs-lookup"><span data-stu-id="f8089-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="f8089-109">IoT Core-spezifischen über die Befehlszeile "utils"</span><span class="sxs-lookup"><span data-stu-id="f8089-109">IoT Core-specific Command Line Utils</span></span>

### **<a name="setting-startup-app"></a><span data-ttu-id="f8089-110">Start-app festlegen:</span><span class="sxs-lookup"><span data-stu-id="f8089-110">Setting startup app:</span></span>**
<span data-ttu-id="f8089-111">Verwenden Sie den Start-Editor, um beim Start von apps auf Ihrem Gerät Windows IoT Core zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f8089-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="f8089-112">Führen Sie `IotStartup` mit einem der folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="f8089-112">Run `IotStartup` with any of the following options:</span></span>

* `IotStartup list` <span data-ttu-id="f8089-113">Listet alle installierten Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f8089-113">lists installed applications</span></span>
* `IotStartup list headed` <span data-ttu-id="f8089-114">installierten Listen Spitzen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f8089-114">lists installed headed applications</span></span>
* `IotStartup list headless` <span data-ttu-id="f8089-115">Listet alle installierten monitorlose Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f8089-115">lists installed headless applications</span></span>
* `IotStartup list [MyApp]` <span data-ttu-id="f8089-116">Auflisten installierter Anwendungen, die mit dem Muster übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="f8089-116">list installed applications that match pattern</span></span> `MyApp`
* `IotStartup add` <span data-ttu-id="f8089-117">Fügt der Kopfzeilen und monitorlose-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f8089-117">adds headed and headless applications</span></span>
* `IotStartup add headed [MyApp]` <span data-ttu-id="f8089-118">Fügt der Kopfzeilen Anwendungen mit dem Muster `MyApp`.</span><span class="sxs-lookup"><span data-stu-id="f8089-118">adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="f8089-119">Nur eine Anwendung muss mit Muster übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="f8089-119">Pattern must match only one application.</span></span>
* `IotStartup add headless [Task1]` <span data-ttu-id="f8089-120">Fügt der monitorlose Anwendungen, die mit dem Muster übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="f8089-120">adds headless applications that match pattern</span></span> `Task1`
* `IotStartup remove` <span data-ttu-id="f8089-121">entfernt, die Spitzen und monitorlose Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f8089-121">removes headed and headless applications</span></span>
* `IotStartup remove headed [MyApp]` <span data-ttu-id="f8089-122">entfernt Spitzen Anwendungen, die mit dem Muster übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="f8089-122">removes headed applications that match pattern</span></span> `MyApp`
* `IotStartup remove headless [Task1]` <span data-ttu-id="f8089-123">Entfernt die monitorlose Anwendungen, die mit dem Muster übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="f8089-123">removes headless applications that match pattern</span></span> `Task1`
* `IotStartup startup` <span data-ttu-id="f8089-124">Listen, die Spitzen und monitorlose Anwendungen, die für den Start registriert</span><span class="sxs-lookup"><span data-stu-id="f8089-124">lists headed and headless applications registered for startup</span></span>
* `IotStartup startup [MyApp]` <span data-ttu-id="f8089-125">Listen, Spitzen und monitorlose Anwendungen registriert für den Start dieser Muster</span><span class="sxs-lookup"><span data-stu-id="f8089-125">lists headed and headless applications registered for startup that match pattern</span></span> `MyApp`
* `IotStartup startup headed [MyApp]` <span data-ttu-id="f8089-126">Listen mit Anwendungen, die für den Start registriert, die mit übereinstimmen Spitzen.</span><span class="sxs-lookup"><span data-stu-id="f8089-126">lists headed applications registered for startup that match</span></span> `MyApp`
* `IotStartup startup headless [Task1]` <span data-ttu-id="f8089-127">Listet monitorlose Anwendungen für den Start registriert, die mit übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="f8089-127">lists headless applications registered for startup that match</span></span> `Task1`

    * <span data-ttu-id="f8089-128">Um weitere Hilfe zu erhalten versuchen Sie es</span><span class="sxs-lookup"><span data-stu-id="f8089-128">For further help, try</span></span> `IotStartup help`
    
### **<a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="f8089-129">Ändern der Einstellungen für die Region "und" Benutzer "oder" Speech Sprache:</span><span class="sxs-lookup"><span data-stu-id="f8089-129">Change settings for region and user or speech language:</span></span>**

<span data-ttu-id="f8089-130">Die `IoTSettings` Tool ändert, Region, die Standardsprache für Benutzer oder Sprache.</span><span class="sxs-lookup"><span data-stu-id="f8089-130">The `IoTSettings` tool changes region, user language or speech language.</span></span> <span data-ttu-id="f8089-131">Dies ist ein Befehlszeilentool, das von einer Anwendung mithilfe der ProcessLauncher-API aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f8089-131">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="f8089-132">Diese Befehle müssen als Standardkonto, nicht als Administrator ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f8089-132">These commands must be run as default account, not administrator.</span></span>

* `IotSettings del account {all | username}` <span data-ttu-id="f8089-133">Löscht alle Account, MSA oder AAD-Konten auf dem System oder ein bestimmtes Konto.</span><span class="sxs-lookup"><span data-stu-id="f8089-133">deletes all MSA or AAD accounts on the system or a specific account.</span></span>  <span data-ttu-id="f8089-134">Bestimmte Konten werden in der form username@provider.com</span><span class="sxs-lookup"><span data-stu-id="f8089-134">Specific accounts take the form username@provider.com</span></span>
* `IotSettings del diagnostics` <span data-ttu-id="f8089-135">Löscht die Diagnoseinformationen in der Cloud für das aktuelle Gerät.</span><span class="sxs-lookup"><span data-stu-id="f8089-135">deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="f8089-136">Beachten Sie, dass dadurch die Versionsgeschichte bis zum Zeitpunkt des Aufrufs wird entfernt.</span><span class="sxs-lookup"><span data-stu-id="f8089-136">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="f8089-137">Neue Diagnose-Informationen werden weiterhin protokolliert werden.</span><span class="sxs-lookup"><span data-stu-id="f8089-137">New diagnostics information will continue to be logged.</span></span>
* `IotSettings list account` <span data-ttu-id="f8089-138">Listet alle Account, MSA oder AAD-Konten, die auf dem Gerät signiert wurden.</span><span class="sxs-lookup"><span data-stu-id="f8089-138">lists all MSA or AAD accounts that have been signed into the device.</span></span>
* `IotSettings list uilanguage` <span data-ttu-id="f8089-139">Listet alle UI-Sprachen</span><span class="sxs-lookup"><span data-stu-id="f8089-139">lists all UI languages</span></span>
* `IotSettings list speechlanguage` <span data-ttu-id="f8089-140">Listet alle Sprachen für Sprachausgabe</span><span class="sxs-lookup"><span data-stu-id="f8089-140">lists all speech languages</span></span>
* `IotSettings get uilanguage` <span data-ttu-id="f8089-141">Zeigt die aktuelle Sprache der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="f8089-141">displays current UI language</span></span>
* `IotSettings get speechlanguage` <span data-ttu-id="f8089-142">Zeigt die Sprache der aktuellen Sprache an</span><span class="sxs-lookup"><span data-stu-id="f8089-142">displays current speech language</span></span>
* `IotSettings get region` <span data-ttu-id="f8089-143">Zeigt die aktuelle region</span><span class="sxs-lookup"><span data-stu-id="f8089-143">displays current region</span></span>
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="f8089-144">Legt die Standardsprache Französisch (Kanada))</span><span class="sxs-lookup"><span data-stu-id="f8089-144">sets default UI language French Canadian)</span></span>
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="f8089-145">Legt fest, der Sprache Französisch (Kanada))</span><span class="sxs-lookup"><span data-stu-id="f8089-145">sets speech language French Canadian)</span></span>
* `IotSettings set region region\_code - (e.g. CA)` <span data-ttu-id="f8089-146">Legt die Standardregion, Kanada)</span><span class="sxs-lookup"><span data-stu-id="f8089-146">sets default region to Canada)</span></span>
* `IotSettings set bluetoothpref {sink | source}` <span data-ttu-id="f8089-147">Gibt an, das die Einstellung für Bluetooth-Rolle auswählen, wenn die Geräte, die mit Funktionen sowohl IOT_BLUETOOTH_A2DP_SOURCE und IOT_BLUETOOTH_A2DP_SINK erstellt auf ein anderes Gerät verbinden, die auch beide Rollen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f8089-147">Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* `IotSettings get bluetoothpref` <span data-ttu-id="f8089-148">Gibt die aktuelle Bluetooth-Voreinstellung für die Rolle für Geräte, die mit IOT_BLUETOOTH_A2DP_SOURCE und IOT_BLUETOOTH_A2DP_SINK erstellt.</span><span class="sxs-lookup"><span data-stu-id="f8089-148">returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="f8089-149">Der Standardwert ist die Quelle.</span><span class="sxs-lookup"><span data-stu-id="f8089-149">The default is source.</span></span>

> [!TIP]
> `IoTSettings -list uiLanguage` <span data-ttu-id="f8089-150">(in der Version des Windows IoT Core-Images, die, denen Sie für bereits ausgeführt wurde) wird wieder die Liste der unterstützten Sprache der Benutzeroberfläche bieten.</span><span class="sxs-lookup"><span data-stu-id="f8089-150">will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### **<a name="change-default-audio-device-and-volume"></a><span data-ttu-id="f8089-151">Ändern Sie Standard-Audiogeräts "und" Volume:</span><span class="sxs-lookup"><span data-stu-id="f8089-151">Change default audio device and volume:</span></span>**

<span data-ttu-id="f8089-152">Die `IoTCoreAudioControlTool` Tool steuert audio verwandte Optionen, z. B. die Erfassung und Wiedergabe Geräte festlegen und Ändern der Lautstärke.</span><span class="sxs-lookup"><span data-stu-id="f8089-152">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="f8089-153">Führen Sie für eine vollständige Liste von Parametern, `IoTCoreAudioControlTool h`.</span><span class="sxs-lookup"><span data-stu-id="f8089-153">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### **<a name="manually-installing-appx-files"></a><span data-ttu-id="f8089-154">Manuell zu installieren. APPX-Dateien:</span><span class="sxs-lookup"><span data-stu-id="f8089-154">Manually installing .APPX files:</span></span>**
<span data-ttu-id="f8089-155">DeployAppx ermöglicht installieren und Entfernen von. APPX-Paketen in Entwicklungsszenarios.</span><span class="sxs-lookup"><span data-stu-id="f8089-155">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="f8089-156">Die richtige Methode für die Installation. APPX-Paketen in Produktions-Images ist die Verwendung ein Bereitstellungspakets dokumentiert sind die [Installieren der app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) Betreff.</span><span class="sxs-lookup"><span data-stu-id="f8089-156">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="f8089-157">DeployAppx unterstützt auch Abfragen. APPX-Paket-Informationen.</span><span class="sxs-lookup"><span data-stu-id="f8089-157">DeployAppx also supports querying .APPX package information.</span></span>

*  `DeployAppx install MyApp.appx` <span data-ttu-id="f8089-158">installiert die. APPX und das Zertifikat mit dem gleichen Namen wenn gefunden.</span><span class="sxs-lookup"><span data-stu-id="f8089-158">installs the .APPX and the certificate of the same name if found.</span></span>
* `DeployAppx install force MyApp.appx` <span data-ttu-id="f8089-159">Erzwingt, dass den aktuell installierten deinstallieren. APPX mit dem gleichen Paket zu benennen, wenn vor der Installation der neuen gefunden. APPX.</span><span class="sxs-lookup"><span data-stu-id="f8089-159">forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="f8089-160">Dies ist nützlich für die Installation ein. APPX mit der Anzahl dieselbe oder eine niedrigere Version als die derzeit installierten. APPX.</span><span class="sxs-lookup"><span data-stu-id="f8089-160">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* `DeployAppx install retry MyApp.appx` <span data-ttu-id="f8089-161">eine erneute Installation der. APPX-10-Mal bei einem Fehler mit 2 Sekunden Verzögerung zwischen den Wiederholungsversuchen.</span><span class="sxs-lookup"><span data-stu-id="f8089-161">retry installing the .APPX 10 times on failure with 2 second delay between attempts.</span></span>
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` <span data-ttu-id="f8089-162">Deinstallieren der AppX-Datei mit den entsprechenden vollständigen Paketnamen an.</span><span class="sxs-lookup"><span data-stu-id="f8089-162">uninstall the .appx with the matching package full name.</span></span>
*  `DeployAppx uninstall MyApp.appx` <span data-ttu-id="f8089-163">Deinstallieren Sie eine beliebige vorhandene aus. APPX mit einem übereinstimmenden Namen der Paket-Familie.</span><span class="sxs-lookup"><span data-stu-id="f8089-163">uninstall any installed .APPX with a matching package family name.</span></span>
* `DeployAppx getpackages` <span data-ttu-id="f8089-164">Listet alle installierten vollständigen Paketnamen.</span><span class="sxs-lookup"><span data-stu-id="f8089-164">lists installed package full names.</span></span>
* `DeployAppx getpackageid IotCoreDefaultApp.appx` <span data-ttu-id="f8089-165">Gibt den Paketnamen, den paketfamiliennamen und das Paket für die vollständigen Namen der. APPX.</span><span class="sxs-lookup"><span data-stu-id="f8089-165">prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` <span data-ttu-id="f8089-166">nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="f8089-166">unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="f8089-167">Allgemein über die Befehlszeile "utils"</span><span class="sxs-lookup"><span data-stu-id="f8089-167">General Command Line Utils</span></span>

### **<a name="update-account-password"></a><span data-ttu-id="f8089-168">Aktualisieren Sie Kontokennwort:</span><span class="sxs-lookup"><span data-stu-id="f8089-168">Update account password:</span></span>**

<span data-ttu-id="f8089-169">Es wird dringend empfohlen, dass Sie das Standardkennwort für das Administratorkonto aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f8089-169">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="f8089-170">Zu diesem Zweck können Sie den folgenden Befehl ausgeben: `net user Administrator [new password]` , in denen `[new password]` stellt ein sicheres Kennwort Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="f8089-170">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### **<a name="create-local-user-accounts"></a><span data-ttu-id="f8089-171">Erstellen Sie lokale Benutzerkonten:</span><span class="sxs-lookup"><span data-stu-id="f8089-171">Create local user accounts:</span></span>**

<span data-ttu-id="f8089-172">Wenn Sie anderen Benutzern Zugriff auf Ihr Gerät Windows IoT Core gewähren möchten, können Sie zusätzliche lokale Benutzerkonten, die mit PS durch Eingabe erstellen `net user [username] [password] /add`.</span><span class="sxs-lookup"><span data-stu-id="f8089-172">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="f8089-173">Wenn Sie diesen Benutzer zu anderen Gruppen, z.B. die Gruppe "Administrator" hinzufügen möchten, verwenden `net localgroup Administrators [username] /add`.</span><span class="sxs-lookup"><span data-stu-id="f8089-173">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### **<a name="set-password"></a><span data-ttu-id="f8089-174">Legen Sie das Kennwort ein:</span><span class="sxs-lookup"><span data-stu-id="f8089-174">Set password:</span></span>**

<span data-ttu-id="f8089-175">Führen Sie zum Ändern des Kennworts für ein Konto auf Ihrem Gerät `net user [account-username] [new-password]` das Kontokennwort zu ändern.</span><span class="sxs-lookup"><span data-stu-id="f8089-175">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### **<a name="query-and-set-device-name"></a><span data-ttu-id="f8089-176">Abfragen aus, und Festlegen von Gerätename:</span><span class="sxs-lookup"><span data-stu-id="f8089-176">Query and set device name:</span></span>**

<span data-ttu-id="f8089-177">Um den Namen des aktuellen Geräts zu identifizieren, geben Sie einfach `hostname`.</span><span class="sxs-lookup"><span data-stu-id="f8089-177">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="f8089-178">Um den Namen Ihres Windows IoT Core-Geräts zu ändern, geben `SetComputerName [new machinename]`.</span><span class="sxs-lookup"><span data-stu-id="f8089-178">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="f8089-179">Sie müssen das Gerät die Namensänderung wirksam wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="f8089-179">You may need to restart your device for the name change to take effect.</span></span>

### **<a name="basic-network-configuration"></a><span data-ttu-id="f8089-180">Grundlegende Netzwerkkonfiguration:</span><span class="sxs-lookup"><span data-stu-id="f8089-180">Basic network configuration:</span></span>**

<span data-ttu-id="f8089-181">Viele der grundlegenden Konfiguration Netzwerkdienstprogramme bereits kennen Sie möglicherweise mit sind verfügbar in Windows IoT Core, einschließlich Befehle wie z. B. `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, und `arp.exe`.</span><span class="sxs-lookup"><span data-stu-id="f8089-181">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### **<a name="copy-utilities"></a><span data-ttu-id="f8089-182">Kopieren Sie die Dienstprogramme:</span><span class="sxs-lookup"><span data-stu-id="f8089-182">Copy utilities:</span></span>**

<span data-ttu-id="f8089-183">Microsoft bietet vertraute Tools, einschließlich `sfpcopy.exe` sowie `xcopy.exe`.</span><span class="sxs-lookup"><span data-stu-id="f8089-183">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### **<a name="process-management"></a><span data-ttu-id="f8089-184">Prozessmanagement:</span><span class="sxs-lookup"><span data-stu-id="f8089-184">Process Management:</span></span>**

<span data-ttu-id="f8089-185">Um derzeit ausgeführte Prozesse anzuzeigen, können Sie versuchen, entweder `get-process` Alternativ `tlist.exe`.</span><span class="sxs-lookup"><span data-stu-id="f8089-185">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="f8089-186">Um einen laufenden Prozess zu beenden, geben `kill.exe [pid or process name]`.</span><span class="sxs-lookup"><span data-stu-id="f8089-186">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### **<a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="f8089-187">Legen Sie die Option "Start" (monitorlose im Vergleich zu Multi-Monitor starten):</span><span class="sxs-lookup"><span data-stu-id="f8089-187">Set Boot Option (Headless vs. headed boot):</span></span>**

<span data-ttu-id="f8089-188">Windows IoT Core-Geräte zu Kopfzeilen festgelegt werden, (wenn es sich um eine Anzeigefunktionen erforderlich sind) oder (bei eine Anzeige nicht erforderlich oder verfügbar ist) monitorlose "Gerät".</span><span class="sxs-lookup"><span data-stu-id="f8089-188">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="f8089-189">Verwenden Sie zum Ändern dieser Einstellung `setbootoption.exe [headed | headless]`.</span><span class="sxs-lookup"><span data-stu-id="f8089-189">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="f8089-190">Das Ändern dieser Einstellung müssen einen Neustart damit die Änderung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="f8089-190">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### **<a name="task-scheduler"></a><span data-ttu-id="f8089-191">Der aufgabenplanung:</span><span class="sxs-lookup"><span data-stu-id="f8089-191">Task scheduler:</span></span>**

<span data-ttu-id="f8089-192">Um die aktuelle Liste der geplanten Aufgaben anzuzeigen, verwenden Sie die `schtasks.exe` Befehl.</span><span class="sxs-lookup"><span data-stu-id="f8089-192">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="f8089-193">Sie können neue Vorgänge mit erstellen die `/create` wechseln, oder führen Sie bei Bedarf Aufgaben mit der `/run` wechseln.</span><span class="sxs-lookup"><span data-stu-id="f8089-193">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="f8089-194">Verwenden Sie für eine vollständige Liste der unterstützten Parameter</span><span class="sxs-lookup"><span data-stu-id="f8089-194">For a full list of supported parameters, use</span></span> `schtasks.exe /?`

### **<a name="device-drivers"></a><span data-ttu-id="f8089-195">Gerätetreiber:</span><span class="sxs-lookup"><span data-stu-id="f8089-195">Device drivers:</span></span>**

<span data-ttu-id="f8089-196">Das Gerät Konsole-Hilfsprogramm ist hilfreich bei der Identifizierung und Verwaltung von installierten Geräten und Treibern.</span><span class="sxs-lookup"><span data-stu-id="f8089-196">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="f8089-197">Verwenden Sie für eine vollständige Liste von Parametern</span><span class="sxs-lookup"><span data-stu-id="f8089-197">For a full list of parameters, use</span></span> `devcon.exe /?`

### **<a name="registry-access"></a><span data-ttu-id="f8089-198">Zugriff auf die Registrierung:</span><span class="sxs-lookup"><span data-stu-id="f8089-198">Registry Access:</span></span>**

<span data-ttu-id="f8089-199">Wenn Sie Zugriff auf die Registrierung zu anzeigen oder ändern Sie die Einstellungen zu verwenden, müssen die `reg.exe /?` -Befehl für die vollständige Liste der unterstützten Parameter.</span><span class="sxs-lookup"><span data-stu-id="f8089-199">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### **<a name="services"></a><span data-ttu-id="f8089-200">Dienste:</span><span class="sxs-lookup"><span data-stu-id="f8089-200">Services:</span></span>**

<span data-ttu-id="f8089-201">Verwalten von Windows-Diensten kann erreicht werden, über die `net.exe` Befehl.</span><span class="sxs-lookup"><span data-stu-id="f8089-201">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="f8089-202">Geben Sie zum Anzeigen einer Liste mit den ausgeführten Diensten `net start`.</span><span class="sxs-lookup"><span data-stu-id="f8089-202">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="f8089-203">Geben Sie zum Starten oder Beenden eines bestimmten Diensts, `net [start | stop] [service name]`.</span><span class="sxs-lookup"><span data-stu-id="f8089-203">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="f8089-204">Alternativ können Sie auch über den dienststeuerungs-Manager verwenden `sc.exe` Befehl.</span><span class="sxs-lookup"><span data-stu-id="f8089-204">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### **<a name="boot-configuration"></a><span data-ttu-id="f8089-205">Startkonfiguration:</span><span class="sxs-lookup"><span data-stu-id="f8089-205">Boot configuration:</span></span>**

<span data-ttu-id="f8089-206">Sie können die Startkonfiguration Ihres Geräts für die Windows IoT Core Änderungen vornehmen, mithilfe von `bcdedit.exe`.</span><span class="sxs-lookup"><span data-stu-id="f8089-206">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="f8089-207">Sie können z. B. Testsigning mit `bcdedit –set testsigning on` Befehl.</span><span class="sxs-lookup"><span data-stu-id="f8089-207">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### **<a name="shutdownrestart-device"></a><span data-ttu-id="f8089-208">Herunterfahren/Neustarten des Geräts:</span><span class="sxs-lookup"><span data-stu-id="f8089-208">Shutdown/restart device:</span></span>**

<span data-ttu-id="f8089-209">Geben Sie Ihr Gerät Herunterfahren `shutdown /s /t 0`.</span><span class="sxs-lookup"><span data-stu-id="f8089-209">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="f8089-210">Verwenden Sie zum Neustarten des Geräts die `/r` wechseln Sie stattdessen mit dem Befehl `shutdown /r /t 0`.</span><span class="sxs-lookup"><span data-stu-id="f8089-210">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### **<a name="viewing-and-changing-display-settings"></a><span data-ttu-id="f8089-211">Anzeigen und Ändern von Anzeigeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="f8089-211">Viewing and changing display settings</span></span>**
<span data-ttu-id="f8089-212">Das Tool SetDisplayResolution kann verwendet werden, zum Auflisten der der aktuellen Anzeigeeinstellungen und um die Liste der unterstützten Werte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f8089-212">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="f8089-213">Es kann weiter verwendet werden, zum Anpassen der Anzeige Auflösung, Aktualisierungsrate und/oder Ausrichtung mit Werten, die von Ihrer Plattform unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="f8089-213">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="f8089-214">Das Hilfsprogramm akzeptiert die folgenden Befehlszeilenargumente:</span><span class="sxs-lookup"><span data-stu-id="f8089-214">The utility accepts the following command line arguments:</span></span>

* `SetDisplayResolution` <span data-ttu-id="f8089-215">Listet die aktuellen Resoltuion anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f8089-215">Lists the current display resoltuion.</span></span>
* `SetDisplayResolution -list` <span data-ttu-id="f8089-216">Liste der unterstützten displayauflösungen.</span><span class="sxs-lookup"><span data-stu-id="f8089-216">Lists supported display resolutions.</span></span>
* `SetDisplayResolution -orientation:[n]` <span data-ttu-id="f8089-217">Ändern der anzeigeausrichtung, wobei n = 0, 90, 180 oder 270 Grad.</span><span class="sxs-lookup"><span data-stu-id="f8089-217">Change the display orientation, where n=0,90,180 or 270.</span></span>
* `SetDisplayResolution [width] [height]` <span data-ttu-id="f8089-218">Ändern Sie die Breite und Höhe in Pixel</span><span class="sxs-lookup"><span data-stu-id="f8089-218">Change the width and height in pixels</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate]` <span data-ttu-id="f8089-219">Breite, Höhe und Aktualisierung Änderungsrate, Breite und Höhe in Pixel und "RefreshRate" in Hz sind</span><span class="sxs-lookup"><span data-stu-id="f8089-219">Change width, height and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` <span data-ttu-id="f8089-220">Ändern Sie Breite, Höhe, "RefreshRate" und Bildschirm-Ausrichtung, Breite und Höhe in Pixel "RefreshRate" in Hz und Ausrichtung eines 0, 90, 180 oder 270.</span><span class="sxs-lookup"><span data-stu-id="f8089-220">Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### **<a name="take-screenshot"></a><span data-ttu-id="f8089-221">Erstellen eines Screenshots:</span><span class="sxs-lookup"><span data-stu-id="f8089-221">Take screenshot:</span></span>**

<span data-ttu-id="f8089-222">Schalten Sie den Screenshot Ihres Geräts für die Windows-IoTCore, indem `ScreenCapture.exe`.</span><span class="sxs-lookup"><span data-stu-id="f8089-222">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="f8089-223">Führen Sie z. B. `ScreenCapture c:\folder\screencap.jpg` Screenshot übernimmt und in screencap.jpg-Datei zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f8089-223">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### **<a name="get-information-about-network-adapters"></a><span data-ttu-id="f8089-224">Abrufen von Informationen über Netzwerkadapter:</span><span class="sxs-lookup"><span data-stu-id="f8089-224">Get information about Network Adapters:</span></span>**

<span data-ttu-id="f8089-225">Führen Sie zum Anzeigen der Liste aller verfügbaren Netzwerkadapter `GetAdapterInfo` Tool.</span><span class="sxs-lookup"><span data-stu-id="f8089-225">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### **<a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="f8089-226">Legen Sie Berechtigungen für die UWP-apps:</span><span class="sxs-lookup"><span data-stu-id="f8089-226">Set folder permissions for UWP apps:</span></span>**

<span data-ttu-id="f8089-227">Nicht alle Ordner auf Ihrem Gerät sind zugegriffen werden kann, von universellen Windows-Apps.</span><span class="sxs-lookup"><span data-stu-id="f8089-227">Not all folders on your device are accesible by Universal Windows Apps.</span></span> <span data-ttu-id="f8089-228">Um einen Ordner zugegriffen werden kann zu einer UWP-app zu machen, können Sie `FolderPermissions` Tool.</span><span class="sxs-lookup"><span data-stu-id="f8089-228">To make a folder accesible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="f8089-229">Führen Sie z. B. `FolderPermissions c:\test -e` um UWP-apps Zugriff auf `c:\test` Ordner.</span><span class="sxs-lookup"><span data-stu-id="f8089-229">For example run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="f8089-230">Beachten Sie, dass dies nur mit systemeigenen Win32-apis für z. B. funktionieren.</span><span class="sxs-lookup"><span data-stu-id="f8089-230">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="f8089-231">CreateFile2 und nicht mit WinRT-apis wie "storagefolder", "storagefile" usw.</span><span class="sxs-lookup"><span data-stu-id="f8089-231">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### **<a name="work-with-serial-ports"></a><span data-ttu-id="f8089-232">Arbeiten Sie mit seriellen Anschlüssen:</span><span class="sxs-lookup"><span data-stu-id="f8089-232">Work with Serial Ports:</span></span>**
<span data-ttu-id="f8089-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) können Sie mit der seriellen Anschlüsse über die Befehlszeile zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="f8089-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="f8089-234">Es wird als ein Beispielprojekt im ms-Iot-Samples-Repository bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f8089-234">It is provided as a sample project in the ms-iot samples repo.</span></span> 

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


