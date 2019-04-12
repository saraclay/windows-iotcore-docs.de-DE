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
# <a name="driver-deployment"></a><span data-ttu-id="1a55b-104">Gerätetreiber</span><span class="sxs-lookup"><span data-stu-id="1a55b-104">Driver deployment</span></span>

<span data-ttu-id="1a55b-105">Stellen Sie einen Treiber auf Windows 10 IoT Core mit Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="1a55b-105">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span> 

<span data-ttu-id="1a55b-106">Konfigurieren Sie Visual Studio-Treiber-Projekt so, dass Sie kompilieren und ein Treibers für eine bestimmte Plattform während der Entwicklungsphase Treiber bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-106">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span> 

<span data-ttu-id="1a55b-107">Für diese Übung können Sie die [Gpiokmdfdemo Beispieltreiber](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span><span class="sxs-lookup"><span data-stu-id="1a55b-107">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="1a55b-108">Wenn Sie einen Treiber zu einem Bild hinzufügen möchten, besuchen Sie die Anweisungen in unserer [Manufacturing für IoT](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span><span class="sxs-lookup"><span data-stu-id="1a55b-108">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1--setup"></a><span data-ttu-id="1a55b-109">Schritt 1: Setup</span><span class="sxs-lookup"><span data-stu-id="1a55b-109">Step 1 : Setup</span></span> 
___

### <a name="on-the-device"></a><span data-ttu-id="1a55b-110">Auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="1a55b-110">On the device</span></span>

* <span data-ttu-id="1a55b-111">Stellen Sie sicher, dass das Gerät ein IoTCore-Image installiert wird, indem Sie die folgenden verfügt über die [erste-Schritte-Anleitungen](https://go.microsoft.com/fwlink/?linkid=860461).</span><span class="sxs-lookup"><span data-stu-id="1a55b-111">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="1a55b-112">Herstellen einer Verbindung Ihres Geräts über mit [Powershell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="1a55b-112">Connect to your device via [Powershell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="1a55b-113">Auf dem PC</span><span class="sxs-lookup"><span data-stu-id="1a55b-113">On the PC</span></span>

* <span data-ttu-id="1a55b-114">Stellen Sie sicher, dass Sie Visual Studio 2017 installiert haben.</span><span class="sxs-lookup"><span data-stu-id="1a55b-114">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="1a55b-115">Installieren Sie die [Windows-Treiberkit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span><span class="sxs-lookup"><span data-stu-id="1a55b-115">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="1a55b-116">Sie müssen das SDK und die WDK zu installieren.</span><span class="sxs-lookup"><span data-stu-id="1a55b-116">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="1a55b-117">Installieren Sie die Zertifikate aus, sodass der Treiber ordnungsgemäß signiert ist und auf Ihrem Gerät ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="1a55b-117">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="1a55b-118">Führen Sie eine Eingabeaufforderung mit erhöhten Rechten die unten aufgeführten Befehle ein:</span><span class="sxs-lookup"><span data-stu-id="1a55b-118">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* <span data-ttu-id="1a55b-119">Anwenden von Visual Studio die F5-Bereitstellung zu beheben.</span><span class="sxs-lookup"><span data-stu-id="1a55b-119">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="1a55b-120">Führen Sie in der Eingabeaufforderung mit erhöhten Rechten die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="1a55b-120">In the elevated command prompt, execute the following commands:</span></span>

    1.  `cd %TEMP%` <span data-ttu-id="1a55b-121">(Wechseln Sie Verzeichnis `c:\users\<usernsme>\Appdata\Local\Temp`)</span><span class="sxs-lookup"><span data-stu-id="1a55b-121">( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="1a55b-122">`md “WdkTempFiles”` Erstellen Sie manuell eine "WdkTempFiles" Verzeichnis Dies ist eine problemumgehung für einen Fehler in den Tools und ausgeführt werden muss *nur einmal* auf dem PC.</span><span class="sxs-lookup"><span data-stu-id="1a55b-122">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2--provision-device-with-visual-studio"></a><span data-ttu-id="1a55b-123">Schritt 2: Bereitstellen eines Geräts mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1a55b-123">Step 2 : Provision device with Visual Studio</span></span> 
___
* <span data-ttu-id="1a55b-124">Öffnen Sie Visual Studio, und wählen Sie **Treiber > Test > Geräte konfigurieren > Neues Gerät hinzufügen**</span><span class="sxs-lookup"><span data-stu-id="1a55b-124">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="1a55b-125">Wenn die Treiber-Option nicht angezeigt wird, überprüfen Sie, ob SDK installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1a55b-125">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="1a55b-126">In der **Gerätekonfiguration** Dialogfeld</span><span class="sxs-lookup"><span data-stu-id="1a55b-126">In the **Device Configuration** dialog,</span></span> 
    * <span data-ttu-id="1a55b-127">Geben Sie einen Benutzer benutzerfreundlichen Anzeigenamen für das Zielgerät</span><span class="sxs-lookup"><span data-stu-id="1a55b-127">Enter a user friendly Display Name for your target device</span></span>
    * <span data-ttu-id="1a55b-128">Wählen Sie Gerätetyp = mobiles Gerät</span><span class="sxs-lookup"><span data-stu-id="1a55b-128">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="1a55b-129">Sortieren Sie in der Liste angezeigt wird, indem IP-Adresse, und suchen Sie die Adresse für den IoT-Geräte, und wählen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-129">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="1a55b-130">Wenn zwei Einträge vorhanden sind, wählen Sie diejenige mit dem NULL-GUID.</span><span class="sxs-lookup"><span data-stu-id="1a55b-130">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="1a55b-131">Stellen Sie sicher, dass die Zeile ausgewählt ist: Es sollte blau hervorgehoben</span><span class="sxs-lookup"><span data-stu-id="1a55b-131">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="1a55b-132">Sind Sie am unteren Rand des Dialogfelds zwei Optionsfelder aus.</span><span class="sxs-lookup"><span data-stu-id="1a55b-132">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="1a55b-133">Wählen Sie diejenige, die besagt, dass **Gerät bereitstellen, und wählen Sie die Debuggereinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-133">Select the one which says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="1a55b-134">Wählen Sie **weiter**</span><span class="sxs-lookup"><span data-stu-id="1a55b-134">Select **Next**</span></span>

* <span data-ttu-id="1a55b-135">Auf der **konfigurieren Sie die Debuggereinstellungen**, legen Sie die entsprechenden Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-135">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="1a55b-136">Beachten Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="1a55b-136">Note the following:</span></span>
   * <span data-ttu-id="1a55b-137">Die MinnowBoardMax kann über das Netzwerk für das Debuggen verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-137">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="1a55b-138">Verwenden Sie Verbindungstyp **Netzwerk**</span><span class="sxs-lookup"><span data-stu-id="1a55b-138">Use connection type **Network**</span></span>
       * <span data-ttu-id="1a55b-139">Wählen Sie einige Port: Standard kann verwendet werden</span><span class="sxs-lookup"><span data-stu-id="1a55b-139">Select some port – default can be used</span></span>
       * <span data-ttu-id="1a55b-140">Wählen Sie einen Schlüssel: Standard kann verwendet werden</span><span class="sxs-lookup"><span data-stu-id="1a55b-140">Select some key – default can be used</span></span>
       * <span data-ttu-id="1a55b-141">Wählen Sie die Host-IP des Computers mit visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a55b-141">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="1a55b-142">Verwenden Sie nicht die Autonetadresse (169.xxx).</span><span class="sxs-lookup"><span data-stu-id="1a55b-142">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="1a55b-143">Wählen Sie **weiter**</span><span class="sxs-lookup"><span data-stu-id="1a55b-143">Select **Next**</span></span>
       
  ![Konfigurieren von Einstellungen zum Debuggen](../media/DriverDeployment/confdbgsettings.png)
       
    * <span data-ttu-id="1a55b-145">Der Raspberry Pi verwendet für das Kerneldebuggen seriellen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-145">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="1a55b-146">Das Kabel des entsprechenden serielle Debuggen auf dem PI und dem Hostcomputer</span><span class="sxs-lookup"><span data-stu-id="1a55b-146">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="1a55b-147">Wählen Sie **seriellen** für den Verbindungstyp</span><span class="sxs-lookup"><span data-stu-id="1a55b-147">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="1a55b-148">Füllen Sie die restlichen Parameter nach Bedarf für den Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="1a55b-148">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="1a55b-149">Wählen Sie **weiter**</span><span class="sxs-lookup"><span data-stu-id="1a55b-149">Select **Next**</span></span>

* <span data-ttu-id="1a55b-150">Das WDK, mithilfe von VS, wird jetzt das IoT-Geräte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-150">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="1a55b-151">TAEF und WDTF auf dem Gerät installiert werden, und das Gerät wird für die Livekernel-Debuggingfunktion gemäß den oben angegebenen Einstellungen eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-151">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="1a55b-152">Nach Abschluss des Vorgangs wird das Gerät möglicherweise neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="1a55b-152">When complete, the device may reboot.</span></span>  <span data-ttu-id="1a55b-153">Die Fortschrittsanzeige auf der **Gerätekonfiguration** Status bietet, und wird abgeschlossen, wenn es sich bei der IoT-Geräte die Installation abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="1a55b-153">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="1a55b-154">Drücken Sie **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-154">Press **Finish**.</span></span>

![Konfigurieren von Status](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="1a55b-156">Das Gerät ist jetzt bereitgestellt und die **Test Gerätekonfiguration** Status wird **für treibertests konfiguriert**</span><span class="sxs-lookup"><span data-stu-id="1a55b-156">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a><span data-ttu-id="1a55b-158">Schritt 3: Konfigurieren von Visual Studio-Treiber-Projekt</span><span class="sxs-lookup"><span data-stu-id="1a55b-158">Step 3 : Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="1a55b-159">Starten Sie Visual Studio im Administratormodus, und öffnen Sie visual Studio-Treiber-Projekt.</span><span class="sxs-lookup"><span data-stu-id="1a55b-159">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="1a55b-160">Stellen Sie sicher, dass die Version der Zielplattform das SDK auf Ihrem Entwicklungscomputer installiert übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="1a55b-160">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="1a55b-161">Wählen Sie Projekteigenschaften im Projektmappen-Explorer-Fenster.</span><span class="sxs-lookup"><span data-stu-id="1a55b-161">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="1a55b-162">Wählen Sie unter Allgemeine Konfigurationseigenschaften stellen sicher, dass die Version der Zielplattform-Übereinstimmungen, die das SDK auf Ihrem Entwicklungscomputer installiert.</span><span class="sxs-lookup"><span data-stu-id="1a55b-162">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="1a55b-163">Sehen Sie die Version des SDK von der **Systemsteuerung > Programme > Programme und Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-163">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="1a55b-164">Klicken Sie unter **Projekt > Neues Element hinzufügen > Visual C++ > Windows-Treiber**Option **Paketmanifest** , und drücken Sie **hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-164">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` <span data-ttu-id="1a55b-166">Datei wird dem Projekt hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-166">file will be added to the project.</span></span> <span data-ttu-id="1a55b-167">Geben Sie in dieser Datei die Besitzer-Plattform, Komponente und Unterkomponente-Tags ein.</span><span class="sxs-lookup"><span data-stu-id="1a55b-167">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span> 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. <span data-ttu-id="1a55b-169">Legen Sie die Versionsnummer des Pakets an **Projekteigenschaften > PackageGen > Version**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-169">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="1a55b-170">Beachten Sie, dass jedes Mal, wenn Sie eine Installation/Neuinstallation des Treibers durchführen müssen, ist diese Versionsnummer sollte inkrementiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="1a55b-170">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="1a55b-172">Klicken Sie unter **Projekteigenschaften > Treibersignierung > Testzertifikat**, zu testen (Phone OEM-testen-Zertifikat)</span><span class="sxs-lookup"><span data-stu-id="1a55b-172">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="1a55b-174">Wechseln Sie zu **Treiber installieren** , und wählen Sie **Bereitstellung**</span><span class="sxs-lookup"><span data-stu-id="1a55b-174">Go to **Driver Install** and select **Deployment**</span></span>

![InstallOptions](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="1a55b-176">Von der **Zielgerätname** Dropdownliste, wählen das Ziel, die oben in der im Rahmen des Bereitstellungsprozesses erstellt.</span><span class="sxs-lookup"><span data-stu-id="1a55b-176">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="1a55b-177">Beachten Sie, dass die beiden Optionen für **installieren / Reinstall** und **schnell installieren**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-177">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="1a55b-178">Wählen Sie eine Option, und klicken Sie auf **Ok**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-178">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="1a55b-179">**Installieren Sie / Reinstall** wird für die Erstinstallation eines Treibers für das Ziel verwendet.</span><span class="sxs-lookup"><span data-stu-id="1a55b-179">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="1a55b-180">Dies das Verwenden des Windows Update-Stapels Treiberpaket installiert und kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="1a55b-180">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="1a55b-181">Dies muss verwendet werden, jedes Mal, wenn die INF-Datei geändert wird.</span><span class="sxs-lookup"><span data-stu-id="1a55b-181">This must be used every time the INF file is changed.</span></span> 
    
> [!TIP]
> <span data-ttu-id="1a55b-182">Jedes Mal, wenn diese Option verwendet wird, um einen Treiber nach der ersten Installation installieren, muss die paketversionsnummer erhöht.</span><span class="sxs-lookup"><span data-stu-id="1a55b-182">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="1a55b-183">**Schnelle Reinstall** kann verwendet werden, nachdem Sie ein Treiber installiert wurde, und es sind keine weiteren Änderungen der Treiber-INF-Datei die Auswirkungen der Registrierung auf.</span><span class="sxs-lookup"><span data-stu-id="1a55b-183">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file which affect the registry.</span></span>  <span data-ttu-id="1a55b-184">Diese Methode umgeht den Installationsvorgang zu, alle Devnodes im Zusammenhang mit dem Treiber fährt, kopiert den Treiber und der Devnode Neustart.</span><span class="sxs-lookup"><span data-stu-id="1a55b-184">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="1a55b-185">Dies dauert ein Paar (< 20) Sekunden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-185">This takes a few (<20) seconds.</span></span>

    
> [!WARNING]
> <span data-ttu-id="1a55b-186">Diese Methode ist nicht erfolgreich ausgeführt werden kann – garantiert, wenn aus irgendeinem Grund ein Devnode Herunterfahren auf, um die Version des Treibers kann sein, der Vorgang fehl.</span><span class="sxs-lookup"><span data-stu-id="1a55b-186">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="1a55b-187">Dies kann aufgrund von fehlerhafte Hardware oder einer fehlerhaften anfänglichen Implementierung des Treibers sein.</span><span class="sxs-lookup"><span data-stu-id="1a55b-187">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="1a55b-188">Die Option zur Installation/Neuinstallation muss in diesem Fall verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-188">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="1a55b-189">Visual Studio-Projekt kann jetzt zum Erstellen und Bereitstellen eines Treibers auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="1a55b-189">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="1a55b-190">Wenn Sie den Beispiel-Gpiokmdfdemo-Treiber verwenden, Sie ACPI-Tabelle und die Kopie auf dem Zielgerät zu generieren müssen, und befolgen Sie dann die Schritte im [Erstellen des Treibers in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span><span class="sxs-lookup"><span data-stu-id="1a55b-190">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4--build-and-deploy-driver"></a><span data-ttu-id="1a55b-191">Schritt 4: Erstellen und Bereitstellen der Treiber</span><span class="sxs-lookup"><span data-stu-id="1a55b-191">Step 4 : Build and deploy driver</span></span>
___
<span data-ttu-id="1a55b-192">Dies kann auf zwei Arten, mit der **F5** Schlüssel- und unter Verwendung der **bereitstellen** Option.</span><span class="sxs-lookup"><span data-stu-id="1a55b-192">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="1a55b-193">Auf beide Arten der Treiber erstellt und bereitgestellt werden (d. h. installiert sie auf dem Gerät) und die F5 fügt Visual Studio-Kernel-Debugger an den Treiber installiert und geladen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-193">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span> 

<span data-ttu-id="1a55b-194">Manche Benutzer bevorzugen die Verwendung der **bereitstellen** Funktionalität, und fügen Sie einen anderen Kernel-Debugger, z. B. WinDBG oder KD.</span><span class="sxs-lookup"><span data-stu-id="1a55b-194">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="1a55b-195">Dadurch kann höhere Flexibilität als die Verwendung von Visual Studio-Debugger bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-195">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="1a55b-196">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="1a55b-196">Deploy</span></span>
1.  <span data-ttu-id="1a55b-197">Mit der rechten Maustaste auf das Projekt im Projektmappen-explorer</span><span class="sxs-lookup"><span data-stu-id="1a55b-197">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="1a55b-198">Wählen Sie **bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="1a55b-198">Select **Deploy**</span></span>

![Bereitstellen](../media/DriverDeployment/deploy.png) 

3.  <span data-ttu-id="1a55b-200">Der Bereitstellungsprozess fortgesetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1a55b-200">The deployment process should proceed.</span></span>  <span data-ttu-id="1a55b-201">Das IoT-Geräte nach der Bereitstellung neu gestartet wird, und den Bildschirm "Gears" sollte angezeigt werden, während der Installation ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1a55b-201">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="1a55b-202">Erstellen Sie Ausgabe ist der **Ausgabe** Fenster Bereitstellung Status auch in das Fenster "Ausgabe" bei der Installation wird abgeschlossen ist, das Gerät wird erneut neu gestartet und die Visual Studio-Ausgabefenster wird Erfolg oder Fehlschlag anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-202">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="1a55b-203">F5</span><span class="sxs-lookup"><span data-stu-id="1a55b-203">F5</span></span>

1.  <span data-ttu-id="1a55b-204">Fenster Vergewissern Sie sich, dass die Konfigurationen richtig sind – der aktuelle Build-Arch identisch mit der Ziel-Gerät-Arch ist.</span><span class="sxs-lookup"><span data-stu-id="1a55b-204">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="1a55b-205">Dies ist, in denen die Arch in den Zielnamen nützlich ist.</span><span class="sxs-lookup"><span data-stu-id="1a55b-205">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="1a55b-206">Das Ziel wird in das Feld Ansichtsname in der Menüleiste in Visual Studio auf der oberen mittleren rechten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-206">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="1a55b-207">Drücken Sie **F5**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-207">Press **F5**.</span></span>  <span data-ttu-id="1a55b-208">Das Ziel wird erstellt, bereitgestellt und an der Visual Studio-Kernel-Debugger angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-208">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="1a55b-209">Nach dem Neustart, stellen Sie sicher, dass PowerShell noch, verbunden ist, andernfalls erneut herstellen einer Verbindung mit dem Zielgerät mithilfe von PowerShell `enter-pssession` Befehl...</span><span class="sxs-lookup"><span data-stu-id="1a55b-209">After the reboot, make sure PowerShell is still connected to it, otherwise, re-connect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="1a55b-210">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="1a55b-210">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="1a55b-211">Fehler bei der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="1a55b-211">Provisioning Errors</span></span>
<span data-ttu-id="1a55b-212">Eine Racebedingung während der Interaktion mit MinnowBoardMax kann zu einem gemeldeten Fehler während der Bereitstellung führen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-212">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="1a55b-213">In der Tat erfolgreich die Bereitstellung in den meisten Fällen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-213">In fact, the provisioning most likely succeeded.</span></span>

**<span data-ttu-id="1a55b-214">Liste von Fehlern:</span><span class="sxs-lookup"><span data-stu-id="1a55b-214">List of Errors:</span></span>**
 
* <span data-ttu-id="1a55b-215">FEHLER: Task "Registrierung WDTF" konnte nicht erfolgreich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="1a55b-215">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="1a55b-216">FEHLER: Task "Konfigurieren von Kernel-Debugger-Einstellungen (mögliche Neustart)" konnte nicht erfolgreich abgeschlossen</span><span class="sxs-lookup"><span data-stu-id="1a55b-216">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="1a55b-217">**Problemumgehung:** Dieser Fehler kann sicherlich ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="1a55b-217">**Workaround:** These error can almost certainly be ignored.</span></span>

**<span data-ttu-id="1a55b-218">Details:</span><span class="sxs-lookup"><span data-stu-id="1a55b-218">Details:</span></span>**

<span data-ttu-id="1a55b-219">Die folgende Fehlermeldung angezeigt, die der **Device Configuration Konfigurationsstatus** Dialogfeld:</span><span class="sxs-lookup"><span data-stu-id="1a55b-219">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

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

<span data-ttu-id="1a55b-220">An diesem Punkt sicher klicken Sie auf die **Fertig stellen** und klicken Sie dann die **übernehmen** und **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a55b-220">At this point you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="1a55b-221">Dies ist eine unkritisch gebildet, indem eine Racebedingung verursacht ein Ergebnis Protokoll fehlerhaft zu sein.</span><span class="sxs-lookup"><span data-stu-id="1a55b-221">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="1a55b-222">Dies kann anhand der Protokolldatei in den folgenden Bereich überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="1a55b-222">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="1a55b-223">Öffnen Sie eine FTP-Verbindung auf die IP-Adresse des Geräts (wie auf dem Bildschirm gezeigt) die `Data/test/bin/DriverTest/Run` Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="1a55b-223">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="1a55b-224">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1a55b-224">e.g.</span></span>
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. <span data-ttu-id="1a55b-225">Kopieren der `Configuring_computer_settings_(possible_reboot)_identifier.wtl` Datei auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="1a55b-225">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="1a55b-226">Beachten Sie, dass der Name der Protokolldatei der Name der fehlerhaften Aufgabe entspricht.</span><span class="sxs-lookup"><span data-stu-id="1a55b-226">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="1a55b-227">Öffnen Sie die Datei im Editor</span><span class="sxs-lookup"><span data-stu-id="1a55b-227">Open the file in notepad</span></span>
4. <span data-ttu-id="1a55b-228">Führen Sie einen Bildlauf zum Ende des Protokolls.</span><span class="sxs-lookup"><span data-stu-id="1a55b-228">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="1a55b-229">Der folgende Text werden vorhanden ist, gibt an, dass die Bereitstellung erfolgreich ist.</span><span class="sxs-lookup"><span data-stu-id="1a55b-229">The following text will be present, indicating that the provisioning is successful.</span></span>

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

