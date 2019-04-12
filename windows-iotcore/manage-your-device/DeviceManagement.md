---
title: Verwalten von Geräten für Windows IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über die verschiedenen Methoden zum Verwalten von Geräten mit Windows 10 IoT Core.
keywords: Windows Iot, geräteverwaltung, Iot mit Windows, Azure-Geräteverwaltung, Azure-Hub, Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513713"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="bfcb6-104">Verwalten von Geräten für Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="bfcb6-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="bfcb6-105">Windows 10 IoT Core-Geräte können verwaltet werden, mithilfe eines herkömmlichen OMA-DM-MDM-Servers, das zertifikatbasierte Anmeldung unterstützt, oder verwenden Azure IoT Hub-Geräteverwaltung.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 _<span data-ttu-id="bfcb6-106">Weitere Informationen zu Verwaltung mobiler Geräte und Windows 10 [hier](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="bfcb6-106">Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx).</span></span>_  

<span data-ttu-id="bfcb6-107">Richten Sie die MDM-Richtlinien für Windows 10 IoT Core mit den Richtlinien, die in anderen Editionen von Windows 10 unterstützt, für Geräte, die mit einem OMA DM-Server verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="bfcb6-108">Um weitere Informationen zu Richtlinien und als ein Element auf IoT-Core-Geräte verwaltet werden können, finden Sie unter Konfigurationsdienstanbieter-Referenz für Windows 10 [hier](https://aka.ms/csplist).</span><span class="sxs-lookup"><span data-stu-id="bfcb6-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="bfcb6-109">Die MDM-Unterstützung in Windows 10 basiert auf Open Mobile Alliance (OMA) Device Management (DM) 1.2.1-Protokollspezifikation.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="bfcb6-110">Wie registriere ich ein Gerät IoT Core in einer MDM?</span><span class="sxs-lookup"><span data-stu-id="bfcb6-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="bfcb6-111">MDM-Registrierung eines IoT Core-Geräts erfolgt mithilfe eines Pakets für die Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="bfcb6-112">Bereitstellung der Pakete kann mithilfe von Windows-Image-Konfiguration und -Designer (WICD) erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="bfcb6-113">Probieren Sie die Registrierung eines Geräts in einer Verwaltung mobiler Geräte.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="bfcb6-114">Erstellen eines Pakets für die Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="bfcb6-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="bfcb6-115">Microsoft System Center Configuration Manager (eigenständig oder SCCM + Intune-Hybridlösung)</span><span class="sxs-lookup"><span data-stu-id="bfcb6-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="bfcb6-116">Öffnen Sie die Configuration Manager-Verwaltungskonsole (Configuration Manager-Konsole)</span><span class="sxs-lookup"><span data-stu-id="bfcb6-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="bfcb6-117">Navigieren Sie zu _Bestand und Kompatibilität > Kompatibilitätseinstellungen > Zugriff auf Unternehmensressourcen > Zertifikatprofile_
   ![Zertifikatprofile](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="bfcb6-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="bfcb6-118">Klicken Sie auf **Zertifikatprofil erstellen**</span><span class="sxs-lookup"><span data-stu-id="bfcb6-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="bfcb6-119">Geben Sie einen Namen und Beschreibung für das Profil</span><span class="sxs-lookup"><span data-stu-id="bfcb6-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="bfcb6-120">Name: ConfigMgr-Beispiel vertrauenswürdiges Stammzertifikat</span><span class="sxs-lookup"><span data-stu-id="bfcb6-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="bfcb6-121">Der Typ des Zertifikatprofils an: Vertrauenswürdiges Zertifikat der Zertifizierungsstelle</span><span class="sxs-lookup"><span data-stu-id="bfcb6-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![Vertrauenswürdiger Zertifizierungsstellen](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="bfcb6-123">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-123">Click **Next**.</span></span>

6. <span data-ttu-id="bfcb6-124">Importieren Sie die Zertifikatdatei ein.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-124">Import the certificate file.</span></span>

7. <span data-ttu-id="bfcb6-125">Wählen Sie **Computerzertifikatspeicher – Stamm** für die **Ziel Store**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="bfcb6-126">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-126">Click **Next**.</span></span>

9. <span data-ttu-id="bfcb6-127">Wählen Sie **wählen Sie alle** für unterstützte Plattformen ![unterstützte Plattformen](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="bfcb6-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="bfcb6-128">Klicken Sie auf **Zusammenfassung "," Weiter, und schließen** um den Assistenten zu beenden.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="bfcb6-129">Mit der rechten Maustaste auf das soeben erstellte Profil, und klicken Sie auf **exportieren**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="bfcb6-130">Klicken Sie auf **Durchsuchen**, suchen Sie einen Standort, in dem die ppkg-Datei exportiert werden sollen, und klicken Sie dann auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="bfcb6-131">Klicken Sie auf **exportieren** , und klicken Sie auf **OK** um den Assistenten zu beenden.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="bfcb6-132">Andere MDM-Server</span><span class="sxs-lookup"><span data-stu-id="bfcb6-132">Other MDM Servers</span></span>

1. <span data-ttu-id="bfcb6-133">Herunterladen und Installieren der [Windows-Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span><span class="sxs-lookup"><span data-stu-id="bfcb6-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="bfcb6-134">Öffnen Sie Windows-Abbilderstellung und Konfigurations-Designer (WICD).</span><span class="sxs-lookup"><span data-stu-id="bfcb6-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   ![Windows Bildverarbeitungs- und Konfigurations-Designer](../media/ManagingDevices/WICD-Start-Page.png)

3. <span data-ttu-id="bfcb6-136">Wählen Sie **Erweiterte Bereitstellung**</span><span class="sxs-lookup"><span data-stu-id="bfcb6-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="bfcb6-137">Legen Sie einen Namen für Ihr Paket.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-137">Set a name for your package.</span></span>

5. <span data-ttu-id="bfcb6-138">Wählen Sie die gemeinsame Einstellungen für Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="bfcb6-139">Überspringen Sie den Schritt Paket importieren.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-139">Skip the Import Package step.</span></span>
   ![<span data-ttu-id="bfcb6-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import</span><span class="sxs-lookup"><span data-stu-id="bfcb6-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import</span></span>](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. <span data-ttu-id="bfcb6-141">Navigieren Sie zu dem Arbeitsplatz -> Registrierungen.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="bfcb6-142">Geben Sie in das Feld "UPN" das Konto, das zum Registrieren Ihres Geräts unter werden sollen (d. h. trmck@contoso.co), und klicken Sie auf **hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![Workplace Registrierungen gefüllt](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="bfcb6-144">AuthPolicy zur Wahl zwischen Benutzername-Kennwort-basierte Authentifizierung (lokalem System) oder zertifikatbasierte Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="bfcb6-145">Geben Sie die Discovery-Dienst-URL für Ihre MDM-Server ein.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="bfcb6-146">Dienst-URL für Registrierung und Gruppenrichtlinie-Dienst-URL sind optional.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="bfcb6-147">Für den geheimen EINGABETASTE</span><span class="sxs-lookup"><span data-stu-id="bfcb6-147">For the Secret enter</span></span>  
    - <span data-ttu-id="bfcb6-148">Lokalem System: Das Kennwort für das Konto, dem Sie sich registrieren können</span><span class="sxs-lookup"><span data-stu-id="bfcb6-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="bfcb6-149">Zertifikat: Den Fingerabdruck des Zertifikats</span><span class="sxs-lookup"><span data-stu-id="bfcb6-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![Ausgefüllte OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="bfcb6-151">Klicken Sie am oberen Fensterrand WICD auf **Exportieren > Bereitstellung Paket**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="bfcb6-152">Geben Sie einen Namen und die Version für Ihr Paket, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="bfcb6-153">Achten Sie darauf, dass Sie erhöht die Versionsnummer, um sicherzustellen, dass ein aktualisiertes Paket ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="bfcb6-154">Klicken Sie auf **Weiter** auf die **Details-Seite "Sicherheit"**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="bfcb6-155">Wählen Sie den Speicherort, an dem das Paket exportiert werden, auf dem lokalen Computer und auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="bfcb6-156">Klicken Sie auf **erstellen** und dann **Fertig stellen** um den Assistenten zu beenden.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="bfcb6-157">Installieren des Pakets für die Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="bfcb6-157">Installing the Provisioning package</span></span>

<span data-ttu-id="bfcb6-158">Es gibt einige Möglichkeiten, die in denen ein Paket für die Bereitstellung auf einem IoT-Gerät bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="bfcb6-159">Es ist möglich, das Bereitstellen eines Pakets durch Kopieren des Pakets auf dem Gerät oder das Paket während des imageerstellungsprozesses auf das Bild hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="bfcb6-160">Kopieren des Pakets auf Gerät</span><span class="sxs-lookup"><span data-stu-id="bfcb6-160">Copying package to device</span></span>

<span data-ttu-id="bfcb6-161">Nehmen Sie die Bereitstellung-Paket, das aus SCCM oder WICD exportiert wurde, und kopieren Sie die ppkg-Datei `C:\Windows\Provisioning\Packages` Verzeichnis auf dem IoT-Gerät.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="bfcb6-162">Bei einem Neustart des Geräts wird das Paket ausgeführt werden, und das Gerät wird die Registrierung zu starten.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="bfcb6-163">Hinzufügen des Pakets zu Bild</span><span class="sxs-lookup"><span data-stu-id="bfcb6-163">Adding package to image</span></span>

<span data-ttu-id="bfcb6-164">Finden Sie unter [fügen Sie ein Bereitstellungspaket zu einem Bild](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span><span class="sxs-lookup"><span data-stu-id="bfcb6-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="bfcb6-165">Beim ersten Start wird das Gerät das Paket ausführen und den Registrierungsprozess starten.</span><span class="sxs-lookup"><span data-stu-id="bfcb6-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
