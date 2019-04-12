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
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="35936-104">Aktivieren der sicheren Start, BitLocker und Device Guard auf Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="35936-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

## <a name="introduction"></a><span data-ttu-id="35936-105">Einführung</span><span class="sxs-lookup"><span data-stu-id="35936-105">Introduction</span></span>

<span data-ttu-id="35936-106">Mit der Version der Creators Update verbessert die Windows 10 IoT Core seine Sicherheit featureangebote zum sicheren UEFI-Start, BitLocker-Geräteverschlüsselung und Device Guard enthalten.</span><span class="sxs-lookup"><span data-stu-id="35936-106">With the release of Creators Update, Windows 10 IoT Core improves its security feature offerings to include UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="35936-107">Diese können die Gerät-Generatoren erstellen vollständig Windows IoT-Geräte, die auf viele verschiedene Arten von Angriffen stabil sind gesperrt.</span><span class="sxs-lookup"><span data-stu-id="35936-107">These will allow device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="35936-108">Zusammen bieten diese Funktionen den optimalen Schutz, der sicherstellt, dass eine Plattform definierte Weise gestartet wird, während Sperrung unbekannt und zum Schutz von Benutzerdaten durch die Verwendung von geräteverschlüsselung.</span><span class="sxs-lookup"><span data-stu-id="35936-108">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

### <a name="secure-boot"></a><span data-ttu-id="35936-109">Sicherer Start</span><span class="sxs-lookup"><span data-stu-id="35936-109">Secure Boot</span></span>

<span data-ttu-id="35936-110">Sichere UEFI-Start ist die erste Richtlinie Erzwingungspunkt, befindet sich in UEFI.</span><span class="sxs-lookup"><span data-stu-id="35936-110">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="35936-111">Sie schränkt das System, um die Ausführung von Binärdateien, die von einer angegebenen Stelle signiert nur zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="35936-111">It restricts the system to only allow execution of binaries signed by a specified authority.</span></span> <span data-ttu-id="35936-112">Dieses Feature verhindert unbekannten Code ausgeführt wird, auf der Plattform und potenzielle Beeinträchtigung Ihres Sicherheitsstatus es.</span><span class="sxs-lookup"><span data-stu-id="35936-112">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="35936-113">BitLocker-Geräteverschlüsselung</span><span class="sxs-lookup"><span data-stu-id="35936-113">BitLocker Device Encryption</span></span>

<span data-ttu-id="35936-114">Windows 10 IoT Core implementiert auch eine vereinfachte Version der BitLocker-Geräteverschlüsselung, IoT-Geräten vor Offlineangriffen schützen.</span><span class="sxs-lookup"><span data-stu-id="35936-114">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span>  <span data-ttu-id="35936-115">Diese Funktion ist in hohem Maße auf das Vorhandensein eines TPM auf der Plattform, einschließlich des erforderlichen preOS-Protokolls in UEFI, die der erforderlichen Messungen.</span><span class="sxs-lookup"><span data-stu-id="35936-115">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary preOS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="35936-116">Diesen preOS-Messungen stellen Sie sicher, dass das Betriebssystem später wurde der wie das Betriebssystem gestartet wurde; Es erzwingt allerdings keine Ausführung Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="35936-116">These preOS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="35936-117">BitLocker-Funktionalität auf Windows 10 IoT Core ermöglicht für die automatische Verschlüsselung des Betriebssystem auf NTFS basierende Volumes bei der alle verfügbaren NTFS-Datenvolumes an ihn binden.</span><span class="sxs-lookup"><span data-stu-id="35936-117">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span>  <span data-ttu-id="35936-118">Es ist erforderlich, um sicherzustellen, dass das Volume EFIESP GUID NA hodnotu nastaven _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span><span class="sxs-lookup"><span data-stu-id="35936-118">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="35936-119">Device Guard unter Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="35936-119">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="35936-120">Die meisten IoT-Geräte werden als Geräte mit festen Funktionen erstellt.</span><span class="sxs-lookup"><span data-stu-id="35936-120">Most IoT devices are built as fixed-function devices.</span></span>  <span data-ttu-id="35936-121">Dies bedeutet, dass Gerät-Generatoren wissen genau einer der Firmware, Betriebssystem, Treiber und Anwendungen auf einem Gerät ausgeführt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="35936-121">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span>  <span data-ttu-id="35936-122">Diese Informationen können wiederum sein verwendet, um vollständig Sperren ein IoT-Geräts nur die Ausführung von bekannten und vertrauenswürdigen Code erlaubt.</span><span class="sxs-lookup"><span data-stu-id="35936-122">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span>  <span data-ttu-id="35936-123">Device Guard auf Windows 10 IoT Core können IoT-Geräten zu schützen, sicherstellen, dass gesperrte Geräte Unbekannter oder nicht vertrauenswürdiger ausführbarer Code ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="35936-123">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="35936-124">Sperren Sie IoT-Geräte</span><span class="sxs-lookup"><span data-stu-id="35936-124">Locking-down IoT Devices</span></span>

<span data-ttu-id="35936-125">Die folgenden Überlegungen müssen vorgenommen werden, damit auf Sperrung einer Windows-IoT-Geräte...</span><span class="sxs-lookup"><span data-stu-id="35936-125">In order to lockdown a Windows IoT device, the following considerations must be made...</span></span>

### <a name="uefi-platform--secure-boot"></a><span data-ttu-id="35936-126">UEFI-Plattform und sicheren Start</span><span class="sxs-lookup"><span data-stu-id="35936-126">UEFI Platform & Secure Boot</span></span>

<span data-ttu-id="35936-127">Um Device Guard-Funktionen nutzen zu können, ist es erforderlich, um sicherzustellen, dass die Startbinärdateien von UEFI-Firmware angemeldet sind und nicht manipuliert sein.</span><span class="sxs-lookup"><span data-stu-id="35936-127">In order to leverage Device Guard capabilities, it is necessary to ensure that the boot binaries and UEFI firmware are signed and cannot be tampered with.</span></span>  <span data-ttu-id="35936-128">Sichere UEFI-Start ist die erste Richtlinie Erzwingungspunkt, befindet sich in UEFI.</span><span class="sxs-lookup"><span data-stu-id="35936-128">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="35936-129">Verhindert eine Manipulation, indem Sie einschränken, das System, um die Ausführung der Startbinärdateien, die von einer angegebenen Stelle signiert nur zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="35936-129">It prevents tampering by restricting the system to only allow execution of boot binaries signed by a specified authority.</span></span> <span data-ttu-id="35936-130">Weitere Informationen zu sicherer Start, zusammen mit schlüsselerstellung und Anleitung zur änderungsverwaltung, steht [hier](https://technet.microsoft.com/library/dn747883.aspx).</span><span class="sxs-lookup"><span data-stu-id="35936-130">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="configurable-code-integrity-cci"></a><span data-ttu-id="35936-131">Konfigurierbare Codeintegrität (CCI)</span><span class="sxs-lookup"><span data-stu-id="35936-131">Configurable Code Integrity (CCI)</span></span>

<span data-ttu-id="35936-132">Codeintegritätsrichtlinie (CI) erhöht die Sicherheit des Betriebssystems durch Überprüfen der Integrität eines Treibers oder einer Anwendung jedes Mal, wenn sie in den Arbeitsspeicher geladen wird.</span><span class="sxs-lookup"><span data-stu-id="35936-132">Code Integrity (CI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="35936-133">CI enthält zwei Hauptkomponenten – Kernel Mode Code Integrity (KMCI) und Gruppenrichtlinien-Verwaltungskonsole (User-Modus Code Integrity, UMCI).</span><span class="sxs-lookup"><span data-stu-id="35936-133">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="35936-134">Konfigurierbare Code Integrity (CCI) ist ein Feature in Windows 10, die ermöglicht das Gerät-Generatoren zum Sperren eines Geräts ist und nur ausführen, und führen Sie Code aus, die signiert und vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="35936-134">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="35936-135">Zu diesem Zweck können Gerät Generatoren erstellen Sie eine codeintegritätsrichtlinie auf ein "goldenes" Gerät (endgültige Version von Hardware und Software) und klicken Sie dann sichern und diese Richtlinie auf allen Geräten am Herstellerstandort anwenden.</span><span class="sxs-lookup"><span data-stu-id="35936-135">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="35936-136">Weitere Informationen zum Bereitstellen von codeintegritätsrichtlinien, Überwachung und Erzwingung, sehen Sie sich die aktuelle Technet-Dokumentation [hier](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span><span class="sxs-lookup"><span data-stu-id="35936-136">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="35936-137">Sofort einsetzbare Sicherheit unter IoT Core</span><span class="sxs-lookup"><span data-stu-id="35936-137">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="35936-138">Um einfache Aktivierung der wichtigsten Sicherheitsfeatures auf Geräten mit IoT Core zu erleichtern, stellt Microsoft eine sofort einsatzbereite "Security Package" bereit, die Geräte-Generatoren erstellen ermöglicht IoT-Geräte vollständig gesperrt.</span><span class="sxs-lookup"><span data-stu-id="35936-138">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a turnkey 'Security Package' that allows device builders to build fully locked down IoT devices.</span></span>  <span data-ttu-id="35936-139">Dieses Paket helfen:</span><span class="sxs-lookup"><span data-stu-id="35936-139">This package will help with:</span></span>

* <span data-ttu-id="35936-140">Bereitstellen sicherer Start-Schlüsseln und Aktivieren des Features auf unterstützten Plattformen für IoT</span><span class="sxs-lookup"><span data-stu-id="35936-140">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="35936-141">Setup und Konfiguration der geräteverschlüsselung, die die Verwendung von BitLocker</span><span class="sxs-lookup"><span data-stu-id="35936-141">Setup and configuration of device encryption using BitLocker</span></span> 
* <span data-ttu-id="35936-142">Initiieren die Gerätesperre nur und ermöglicht die Ausführung von signierten Anwendungen und Treibern</span><span class="sxs-lookup"><span data-stu-id="35936-142">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="35936-143">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="35936-143">Pre-requisites</span></span>

* <span data-ttu-id="35936-144">Einem PC mit Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="35936-144">A PC running Windows 10 Enterprise</span></span>
* <span data-ttu-id="35936-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) : erforderlich für die Generierung des Zertifikats</span><span class="sxs-lookup"><span data-stu-id="35936-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="35936-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) : erforderlich für die Generierung der CAB-Datei</span><span class="sxs-lookup"><span data-stu-id="35936-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="35936-147">Referenzplattform - Release-Hardware mit Protokollversand-Firmware, Betriebssystem, Treiber und Anwendungen erforderlich, damit der letzten Sperrung werden</span><span class="sxs-lookup"><span data-stu-id="35936-147">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="35936-148">Entwicklung, IoT-Geräte</span><span class="sxs-lookup"><span data-stu-id="35936-148">Development IoT Devices</span></span>

<span data-ttu-id="35936-149">Windows 10 IoT Core funktioniert mit verschiedenen Silicons, die in Hunderten von Geräten genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="35936-149">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="35936-150">Von der [vorgeschlagene Geräten für IoT-Entwicklung](../learn-about-hardware/SoCsAndCustomBoards.md), geben Sie die folgenden Firmware-TPM-Funktionalität standardmäßig zusammen mit den sicheren Start "," kontrollierter Start "," BitLocker "und" Device Guard-Funktionen:</span><span class="sxs-lookup"><span data-stu-id="35936-150">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="35936-151">Qualcomm DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="35936-151">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="35936-152">Um den sicheren Start zu aktivieren, kann es erforderlich, für die Bereitstellung RPMB sein.</span><span class="sxs-lookup"><span data-stu-id="35936-152">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="35936-153">Sobald die eMMC mit Windows 10 IoT Core per flashvorgang wurde hat (gemäß den Anweisungen [hier](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), drücken Sie [Power] + [Vol. +] + [Vol-] gleichzeitig auf dem Gerät, die beim Einschalten, und wählen Sie "Provision-RPMB" im Menü BDS.</span><span class="sxs-lookup"><span data-stu-id="35936-153">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> *<span data-ttu-id="35936-154">Beachten Sie, dass dies ein Schritt nicht rückgängig gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="35936-154">Please note that this is an irreversible step.</span></span>*

* <span data-ttu-id="35936-155">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="35936-155">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="35936-156">Für den Intel MinnowBoard maximalen, Firmwareversion muss 0.82 oder höher (Abrufen der [neueste Firmware](https://firmware.intel.com/projects/minnowboard-max)).</span><span class="sxs-lookup"><span data-stu-id="35936-156">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="35936-157">Um TPM-Funktionen zu aktivieren, schalten Sie das Board mit einer Tastatur & anzeigen angefügt, und drücken Sie F2, um UEFI-Setup.</span><span class="sxs-lookup"><span data-stu-id="35936-157">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="35936-158">Wechseln Sie zu _-Geräte-Manager -> System-Setup -> Konfiguration -> PTT_ und legen ihn auf  _&lt;aktivieren&gt;_.</span><span class="sxs-lookup"><span data-stu-id="35936-158">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="35936-159">Drücken Sie F10, um die Änderungen zu speichern, und fahren Sie fort mit einem Neustart der Plattform.</span><span class="sxs-lookup"><span data-stu-id="35936-159">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="35936-160">Raspberry Pi 2 und 3 unterstützen keine TPM, und wir können nicht so konfigurieren Sie Lockdown-Szenarien.</span><span class="sxs-lookup"><span data-stu-id="35936-160">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="35936-161">Lockdown-Pakete generieren</span><span class="sxs-lookup"><span data-stu-id="35936-161">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="35936-162">Herunterladen der [DeviceLockDown Skript](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) Paket, das alle zusätzlichen Tools und Skripts, die zum Konfigurieren und Geräte Sperren erforderlich enthält</span><span class="sxs-lookup"><span data-stu-id="35936-162">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="35936-163">Starten Sie eine Administrative PowerShell (PS)-Konsole auf Ihrem Windows 10-PC aus, und navigieren Sie zum Speicherort des heruntergeladenen Skripts.</span><span class="sxs-lookup"><span data-stu-id="35936-163">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="35936-164">Bereitstellen Sie Ihrer Hardware-Referenzplattform (das entsperrt Image ausführen) auf Ihren PC über das Netzwerk freigeben verwenden</span><span class="sxs-lookup"><span data-stu-id="35936-164">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="35936-165">Generieren von Schlüsseln für die Verwendung von Ihrem Gerät</span><span class="sxs-lookup"><span data-stu-id="35936-165">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="35936-166">Die Schlüssel und Zertifikate werden in der angegebene Ausgabeordner mit geeigneten Suffix generiert.</span><span class="sxs-lookup"><span data-stu-id="35936-166">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="35936-167">**Schützen Sie Ihre generierten Schlüssel** wie das Gerät Binärdateien vertrauen wird mit diesen Schlüsseln signiert sind, nur nach dem Sperren.</span><span class="sxs-lookup"><span data-stu-id="35936-167">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="35936-168">Sie können diesen Schritt überspringen und verwenden die vorab generierten Schlüssel nur zu Testzwecken</span><span class="sxs-lookup"><span data-stu-id="35936-168">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="35936-169">Installieren Sie die generierten PFX-Zertifikate, indem Sie durch Klicken auf die PFX-Dateien direkt oder über die folgenden Powershell-Befehl</span><span class="sxs-lookup"><span data-stu-id="35936-169">Install the generated .pfx certificates by clicking on the pfx files directly or using the below powershell command</span></span>

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. <span data-ttu-id="35936-170">Konfigurieren von _"Settings.xml"_</span><span class="sxs-lookup"><span data-stu-id="35936-170">Configure _settings.xml_</span></span>

    * <span data-ttu-id="35936-171">Abschnitt "Allgemein": Geben Sie die Paketverzeichnisse</span><span class="sxs-lookup"><span data-stu-id="35936-171">General section : Specify the package directories</span></span>
    * <span data-ttu-id="35936-172">Abschnitt "Tools": Legen Sie den Pfad für die tools</span><span class="sxs-lookup"><span data-stu-id="35936-172">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="35936-173">Windows10KitsRoot</span><span class="sxs-lookup"><span data-stu-id="35936-173">Windows10KitsRoot</span></span> `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * <span data-ttu-id="35936-174">WindowsSDKVersion</span><span class="sxs-lookup"><span data-stu-id="35936-174">WindowsSDKVersion</span></span> `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * <span data-ttu-id="35936-175">SDK-Version, die auf Ihrem Computer installiert ist, klicken Sie unter</span><span class="sxs-lookup"><span data-stu-id="35936-175">SDK version installed on your machine is under</span></span> `C:\Program Files (x86)\Windows Kits\10\`
    * <span data-ttu-id="35936-176">SecureBoot-Abschnitt: Geben Sie die Schlüssel, die für den sicheren Start (PK und SB-Schlüssel)</span><span class="sxs-lookup"><span data-stu-id="35936-176">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="35936-177">BitLocker-Abschnitt: Geben Sie ein Zertifikat für Bitlocker die datenwiederherstellung (DRA-Schlüssel)</span><span class="sxs-lookup"><span data-stu-id="35936-177">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="35936-178">SIPolicy-Abschnitt: Geben Sie die Zertifikate, die vertrauenswürdig sind</span><span class="sxs-lookup"><span data-stu-id="35936-178">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="35936-179">ScanPath: Pfad des Geräts für die Überprüfung von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="35936-179">ScanPath : Path of the device for scanning binaries ,</span></span> `\\a.b.c.d\C$`
        * <span data-ttu-id="35936-180">aktualisieren: Signaturgeber des der SIPolicy (PAUTH Schlüssel)</span><span class="sxs-lookup"><span data-stu-id="35936-180">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="35936-181">Benutzer: Benutzermodus-Zertifikate (UMCI Schlüssel)</span><span class="sxs-lookup"><span data-stu-id="35936-181">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="35936-182">Kernel   : Kernelmodus-Zertifikate (KMCI Schlüssel)</span><span class="sxs-lookup"><span data-stu-id="35936-182">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="35936-183">Verpacken: Geben Sie die Einstellungen für die Paket-Generierung</span><span class="sxs-lookup"><span data-stu-id="35936-183">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35936-184">Um Tests während des anfänglichen Entwicklungszyklus zu unterstützen, hat Microsoft vorab generierten Schlüssel und Zertifikate bei Bedarf bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="35936-184">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="35936-185">Dies bedeutet, dass Microsoft Test, Entwicklung und Pre-Release-Binärdateien als vertrauenswürdig eingestuft werden.</span><span class="sxs-lookup"><span data-stu-id="35936-185">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="35936-186">Während der Endprodukt-Erstellung und Generierung einer Bildvorschau werden Sie sicher, dass diese Zertifikaten zu entfernen und Ihre eigenen Schlüssel verwenden, um sicherzustellen, dass ein Gerät vollständig gesperrtes.</span><span class="sxs-lookup"><span data-stu-id="35936-186">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

> [!TIP]
> <span data-ttu-id="35936-187">Die von Microsoft App Store-apps können ihm erlaubt werden, durch das Microsoft Marketplace PCA 2011-Zertifikat in der Konfiguration einschließlich _"Settings.xml"_:</span><span class="sxs-lookup"><span data-stu-id="35936-187">The apps from Microsoft App Store can be allowed by including the Microsoft Marketplace PCA 2011 certificate in the configuration _settings.xml_:</span></span> 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

<span data-ttu-id="35936-188">6. Führen Sie 6. die folgenden Befehle zum Generieren der erforderlichen Pakete:</span><span class="sxs-lookup"><span data-stu-id="35936-188">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="35936-189">Testen Sie die Sperrung von Paketen</span><span class="sxs-lookup"><span data-stu-id="35936-189">Test Lockdown packages</span></span>
<span data-ttu-id="35936-190">Sie können die generierten Pakete testen, indem die manuell über die folgenden Schritte auf einem entsperrten Gerät installiert werden</span><span class="sxs-lookup"><span data-stu-id="35936-190">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="35936-191">Flash-das Gerät mit dem entsperrt Image (Image für die Überprüfung in den vorherigen Schritt verwendet).</span><span class="sxs-lookup"><span data-stu-id="35936-191">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="35936-192">Verbinden mit dem Gerät ([mithilfe von SSH](../connect-your-device/SSH.md) oder [Powershell](../connect-your-device/PowerShell.md))</span><span class="sxs-lookup"><span data-stu-id="35936-192">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="35936-193">Kopieren Sie die folgenden CAB-Dateien an das Gerät in einem Verzeichnis, z. B.</span><span class="sxs-lookup"><span data-stu-id="35936-193">Copy the following .cab files to the device under a directory e.g.</span></span> `c:\OemInstall`
    * <span data-ttu-id="35936-194">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="35936-194">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="35936-195">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="35936-195">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="35936-196">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="35936-196">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="35936-197">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="35936-197">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="35936-198">Bereitstellen der generierten Pakete von akustischen die folgenden Befehle zu initiieren</span><span class="sxs-lookup"><span data-stu-id="35936-198">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="35936-199">Wenn Sie benutzerdefinierte Images verwenden, müssen Sie *überspringen* diese Datei manuell bearbeiten, und wählen Sie die `c:\windows\system32\oemcustomization.cmd` mit dem Inhalt, die in verfügbaren `Output\OEMCustomization\OEMCustomization.cmd` Datei</span><span class="sxs-lookup"><span data-stu-id="35936-199">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="35936-200">Das Gerät wird neu gestartet, in dem Aktualisieren der Betriebssystemversion (mit Gears) zum Installieren der Pakete und wird neu zu Hauptbetriebssystems erneut gestartet.</span><span class="sxs-lookup"><span data-stu-id="35936-200">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="35936-201">Sobald das Gerät wieder MainOS neu gestartet, wird der sichere Start aktiviert werden und SIPolicy beauftragt werden soll.</span><span class="sxs-lookup"><span data-stu-id="35936-201">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="35936-202">Neustart des Geräts erneut aus, um die Bitlocker-Verschlüsselung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="35936-202">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="35936-203">Testen Sie die Sicherheitsfunktionen zu nutzen</span><span class="sxs-lookup"><span data-stu-id="35936-203">Test the security features</span></span>
    * <span data-ttu-id="35936-204">**SecureBoot** : versuchen Sie es `bcdedit /debug on` , erhalten Sie eine Fehlermeldung, dass der Wert von der Richtlinie für sicheren Start geschützt ist.</span><span class="sxs-lookup"><span data-stu-id="35936-204">**SecureBoot** : try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy.</span></span>
   * <span data-ttu-id="35936-205">**BitLocker** : Um zu überprüfen, Bitlocker Encryption abgeschlossen wurde, führen Sie</span><span class="sxs-lookup"><span data-stu-id="35936-205">**BitLocker** : To validate that bitlocker encryption has been completed, run</span></span><p>
        `sectask.exe -waitenableforcompletion 1`<p>
        <span data-ttu-id="35936-206">Wenn sie auf "0" zurückgibt, bedeutet, dass an, dass alle Laufwerke auf dem System Bitlockered erfolgreich gewesen.</span><span class="sxs-lookup"><span data-stu-id="35936-206">If it returns 0, that means all drives on the system have been bitlockered successfully.</span></span>  <span data-ttu-id="35936-207">Ein anderen Rückgabecode ist Fehler.</span><span class="sxs-lookup"><span data-stu-id="35936-207">Any other return code is failure.</span></span><p>
        *<span data-ttu-id="35936-208">Zusätzliche Syntax</span><span class="sxs-lookup"><span data-stu-id="35936-208">Additional Syntax</span></span>*<p>
         `-waitenableforcompletion [timeout]` <p>
        <span data-ttu-id="35936-209">= > Warten Sie, bis BitLocker-Verschlüsselung auf NTFS-Volumes abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="35936-209">=> Wait until BitLocker encryption is completed on all NTFS volumes.</span></span><p>
        <span data-ttu-id="35936-210">= > Timeout in Sekunden warten, aktivieren Sie zum Abschließen.</span><span class="sxs-lookup"><span data-stu-id="35936-210">=> Timeout in seconds to wait for enable to complete.</span></span><p>
        <span data-ttu-id="35936-211">= > Wenn das Timeout nicht angegeben ist, wartet er auf unbestimmte Zeit oder bis zum Abschluss aktivieren.</span><span class="sxs-lookup"><span data-stu-id="35936-211">=> If timeout not specified, it will wait indefinitely or until enable completes.</span></span><p>
        <span data-ttu-id="35936-212">Gibt zurück:</span><span class="sxs-lookup"><span data-stu-id="35936-212">Returns:</span></span> <p>
        <span data-ttu-id="35936-213">0 : BitLocker-Verschlüsselung wurde erfolgreich abgeschlossen wurde, ist Volume Bitlocker verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="35936-213">0 : BitLocker encryption successfully completed, volume is Bitlocker encrypted.</span></span><p>
        <span data-ttu-id="35936-214">ERROR_TIMEOUT: Timeout beim Warten auf Abschluss des Vorgangs Encryption noch in Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="35936-214">ERROR_TIMEOUT: Timeout waiting for completion, encryption still in progress.</span></span><p>
        <span data-ttu-id="35936-215">Fehler / andere Code: Gibt zurück, die vom Schließfach für Bit-Dienst zurückgegebene Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="35936-215">Failure/Other code: returns the failure error code returned by the bit locker service.</span></span>

    * <span data-ttu-id="35936-216">**DeviceGuard** : Führen Sie alle nicht signierten Binär- oder eine Binärdatei mit Zertifikat nicht in der Liste SIPolicy signiert, und bestätigen Sie, dass er nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="35936-216">**DeviceGuard** : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="35936-217">Generieren Sie Lockdown-Abbild</span><span class="sxs-lookup"><span data-stu-id="35936-217">Generate Lockdown image</span></span>

<span data-ttu-id="35936-218">Nach dem Überprüfen, dass die Sperrung Pakete gemäß den zuvor definierten Einstellungen arbeiten, kann Sie dann diese Pakete in das Abbild enthalten, anhand der unten angegebenen Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="35936-218">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="35936-219">Lesen [die Fertigung für IoT](https://aka.ms/iotcoreguide) Anweisungen für benutzerdefiniertes Image erstellen.</span><span class="sxs-lookup"><span data-stu-id="35936-219">Read [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="35936-220">Aktualisieren Sie in der arbeitsbereichsverzeichnis die folgenden Dateien aus dem obigen generierte Ausgabeverzeichnis</span><span class="sxs-lookup"><span data-stu-id="35936-220">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="35936-221">SecureBoot:</span><span class="sxs-lookup"><span data-stu-id="35936-221">SecureBoot :</span></span> `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * <span data-ttu-id="35936-222">SetVariable_db.bin</span><span class="sxs-lookup"><span data-stu-id="35936-222">SetVariable_db.bin</span></span>
      * <span data-ttu-id="35936-223">SetVariable_kek.bin</span><span class="sxs-lookup"><span data-stu-id="35936-223">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="35936-224">SetVariable_pk.bin</span><span class="sxs-lookup"><span data-stu-id="35936-224">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="35936-225">BitLocker:</span><span class="sxs-lookup"><span data-stu-id="35936-225">BitLocker :</span></span> `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * <span data-ttu-id="35936-226">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="35936-226">DETask.xml</span></span>
      * <span data-ttu-id="35936-227">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="35936-227">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="35936-228">setup.bitlocker.cmd</span><span class="sxs-lookup"><span data-stu-id="35936-228">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="35936-229">DeviceGuard:</span><span class="sxs-lookup"><span data-stu-id="35936-229">DeviceGuard :</span></span> `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * <span data-ttu-id="35936-230">SIPolicyOn.p7b</span><span class="sxs-lookup"><span data-stu-id="35936-230">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="35936-231">SIPolicyOff.p7b</span><span class="sxs-lookup"><span data-stu-id="35936-231">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="35936-232">Hinzufügen von RetailOEMInput.xml und TestOEMInput.xml unter dem Verzeichnis "ProductName" mit der Sperrung Paketkennung-Funktion</span><span class="sxs-lookup"><span data-stu-id="35936-232">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="35936-233">Image neu generieren</span><span class="sxs-lookup"><span data-stu-id="35936-233">Re-generate Image</span></span>
    * `buildpkg all` <span data-ttu-id="35936-234">(Dies generiert neue Lockdown-Pakete, die Grundlage der oben genannten Dateien für Gruppenrichtlinien)</span><span class="sxs-lookup"><span data-stu-id="35936-234">(this generates new lockdown packages based on above policy files)</span></span>
    * `buildimage ProductName test(or)retail`  <span data-ttu-id="35936-235">(Dies generiert neue Flash.ffu)</span><span class="sxs-lookup"><span data-stu-id="35936-235">(this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="35936-236">Das Gerät mit diesem neuen Flash.ffu Flash, und überprüfen Sie die Sicherheitsfunktionen zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="35936-236">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="35936-237">Finden Sie unter [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) als Beispiel für eine Sperrung Dragon Board-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="35936-237">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="35936-238">Sie können alternativ Sicherheitspakete der IoTCore Shell selbst generieren, finden Sie unter [hinzufügen Sicherheitspakete](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) Details.</span><span class="sxs-lookup"><span data-stu-id="35936-238">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="35936-239">Entwickeln mit CodeSigning Erzwingung aktiviert</span><span class="sxs-lookup"><span data-stu-id="35936-239">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="35936-240">Sobald die Pakete werden generiert, und Sperren aktiviert ist, müssen alle Binärdateien in das Image eingefügt werden, während der Entwicklung ordnungsgemäß signiert werden.</span><span class="sxs-lookup"><span data-stu-id="35936-240">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="35936-241">Stellen Sie sicher, dass die Binärdateien im Benutzermodus mit dem Schlüssel signiert sind _. \Keys\ \*\*\*-UMCI.pfx_.</span><span class="sxs-lookup"><span data-stu-id="35936-241">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="35936-242">Für die Kernelmodus-Signieren wie z. B. für Treiber, Sie müssen Ihre eigenen Signaturschlüssel geben an, und stellen Sie sicher, dass sind diese ebenfalls in der oben genannten SIPolicy enthalten.</span><span class="sxs-lookup"><span data-stu-id="35936-242">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="35936-243">Entsperren verschlüsselter Laufwerke</span><span class="sxs-lookup"><span data-stu-id="35936-243">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="35936-244">Beim Entwickeln und testen kann beim Lesen von Inhalt aus einer verschlüsselten Gerät offline (z. B. SD-Karte für MinnowBoardMax oder des DragonBoard eMMC über USB-Massenspeicher-Modus), "Diskpart" verwendet werden (wir MainOS und Datenvolumen einen Laufwerkbuchstaben zuweisen Nehmen wir v: MainOS und w für Daten).</span><span class="sxs-lookup"><span data-stu-id="35936-244">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="35936-245">Die Volumes werden als gesperrt angezeigt und müssen manuell entsperrt werden.</span><span class="sxs-lookup"><span data-stu-id="35936-245">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="35936-246">Dies kann erfolgen auf jedem Computer, die die OEM-DRA.pfx-Zertifikat installiert ist (in enthalten die [DeviceLockDown Beispiel](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span><span class="sxs-lookup"><span data-stu-id="35936-246">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="35936-247">Installieren Sie die PFX-Datei, und führen Sie die folgenden Befehle aus einer administrativen Eingabeaufforderung aus:</span><span class="sxs-lookup"><span data-stu-id="35936-247">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="35936-248">Wenn die Inhalte häufig offline zugegriffen werden kann müssen, kann BitLocker automatisches Entsperren für die Volumes eingerichtet werden nach der ersten entsperren mit den folgenden Befehlen:</span><span class="sxs-lookup"><span data-stu-id="35936-248">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="35936-249">Deaktivierung von BitLocker</span><span class="sxs-lookup"><span data-stu-id="35936-249">Disabling BitLocker</span></span>

<span data-ttu-id="35936-250">Muss vorübergehend deaktivieren, BitLocker, sollte es entstehen failovergruppe eine remote-PowerShell-Sitzung mit Ihrem IoT-Geräte und führen Sie den folgenden Befehl: `sectask.exe -disable`.</span><span class="sxs-lookup"><span data-stu-id="35936-250">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  
<span data-ttu-id="35936-251">**Hinweis**: Geräteverschlüsselung wird beim Start der nachfolgende Gerät erneut aktiviert, wenn die Verschlüsselung der geplanten Aufgabe deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="35936-251">**Note:** Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>

### <a name="disabling-device-guard"></a><span data-ttu-id="35936-252">Deaktivieren von Device Guard</span><span class="sxs-lookup"><span data-stu-id="35936-252">Disabling Device Guard</span></span>

<span data-ttu-id="35936-253">Das Skript sofort verwendbaren generiert SIPolicyOn.p7b und SIPolicyOff.p7b-Dateien im Ordner "".</span><span class="sxs-lookup"><span data-stu-id="35936-253">The turnkey security script generates SIPolicyOn.p7b and SIPolicyOff.p7b files in the folder.</span></span>
<span data-ttu-id="35936-254">Die wm.xml Pakete die SIPolicyOn.p7b und platziert ihn in das System als SIPolicy.p7b.</span><span class="sxs-lookup"><span data-stu-id="35936-254">The wm.xml packages the SIPolicyOn.p7b and places it on the system as SIPolicy.p7b.</span></span>

<span data-ttu-id="35936-255">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="35936-255">For example:</span></span>

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

<span data-ttu-id="35936-256">Wenn Sie ein Paket, akzeptiert die SIPolicyOff.p7b-Datei, und platziert es als ein Sipolicy.p7b, erstellen, Sie dieses Paket gilt und die Device Guard deaktiviert jetzt ist.</span><span class="sxs-lookup"><span data-stu-id="35936-256">If you create a package that takes the SIPolicyOff.p7b file and places it as a SIPolicy.p7b, it will apply this package and the Device Guard will be turned off.</span></span>



