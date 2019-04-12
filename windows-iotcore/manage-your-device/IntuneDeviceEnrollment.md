---
title: Windows IoT Core-Geräte in Intune registrieren
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Weitere Informationen zum Verwalten Ihrer Geräte mit Microsoft Intune-Geräteverwaltung und Windows IoT.
keywords: Windows Iot, Azure IoT Device Management in Intune, geräteverwaltung
ms.openlocfilehash: 5d75c64813a3e61f60630abd87185949b63e178b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512361"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="a51c5-104">Registrieren von Windows IoT Core-Geräten in Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="a51c5-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="a51c5-105">Ihr Unternehmen kann es sich um Geräte IoT Core, zusammen mit alle anderen verwalteten Geräte verwalten.</span><span class="sxs-lookup"><span data-stu-id="a51c5-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="a51c5-106">Dies bietet Ihnen eine einheitliche Methode zum IoT Core, IoT-Unternehmen und andere Windows-Geräten mit Intune zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a51c5-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="a51c5-107">Wie registriere ich ein IoT Core-Geräts bei Intune?</span><span class="sxs-lookup"><span data-stu-id="a51c5-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="a51c5-108">Intune-Registrierung eines IoT Core-Geräts erfolgt mithilfe von Windows IoT Core Dashboard zum Vorbereiten des Geräts, und klicken Sie dann mithilfe von Windows Configuration Designer zum Erstellen eines Bereitstellungspakets.</span><span class="sxs-lookup"><span data-stu-id="a51c5-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="a51c5-109">Ändern Sie den Intune-MDM-Benutzerbereich in Azure AD</span><span class="sxs-lookup"><span data-stu-id="a51c5-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="a51c5-110">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com), und wählen Sie dann **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="a51c5-111">Wählen Sie **Mobilität (MDM und MAM)**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-111">Select **Mobility (MDM and MAM)**.</span></span>


~~~
 ![Selecting Mobility and Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)
~~~
1. <span data-ttu-id="a51c5-112">Wählen Sie **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-112">Select **Microsoft Intune**.</span></span> <span data-ttu-id="a51c5-113">Auf der **Konfigurieren von Microsoft Intune** Seite neben **MDM-Benutzerbereich**Option **alle**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-113">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="a51c5-114">Dadurch kann Ihre IoT Core Benutzer des Geräts bei Intune registriert werden, nach dem Beitritt zu Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a51c5-114">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="a51c5-115">Erstellen Sie eine Setup-SD-Karte für das Gerät IoT Core</span><span class="sxs-lookup"><span data-stu-id="a51c5-115">Create a setup SD card for the IoT Core device</span></span>
1. <span data-ttu-id="a51c5-116">Fügen Sie eine MicroSD-Karte in den Smartcardleser auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="a51c5-116">Insert a microSD card into the card reader on your PC.</span></span> 
     > [!NOTE]
     > <span data-ttu-id="a51c5-117">Die MicroSD-Karte wird während dieses Vorgangs formatiert sein, damit alle Daten auf der Karte werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="a51c5-117">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="a51c5-118">Wechseln Sie zu [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) herunterladen und installieren das Dashboard.</span><span class="sxs-lookup"><span data-stu-id="a51c5-118">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="a51c5-119">Nach der Installation des Dashboards öffnen, und wählen **richten Sie ein neues Gerät**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-119">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Windows IoT Core Dashboard](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="a51c5-121">Geben Sie einen **Gerätename**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-121">Type a **Device name**.</span></span>
5. <span data-ttu-id="a51c5-122">Geben Sie ein neues Administratorkennwort ein.</span><span class="sxs-lookup"><span data-stu-id="a51c5-122">Enter a new administrator password.</span></span> 
6. <span data-ttu-id="a51c5-123">Wenn Sie Wi-Fi für das Gerät aktivieren möchten, wählen Sie die **Wi-Fi-Verbindung** Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="a51c5-123">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="a51c5-124">Überspringen Sie dies aus, wenn das Gerät nur eine Ethernet-Netzwerkverbindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="a51c5-124">Skip this if the device will use an ethernet network connection only.</span></span>

     ![Wi-Fi-Kontrollkästchen auf dem IoT-dashboard](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="a51c5-126">Wählen Sie die **ich akzeptiere die Lizenzbedingungen der Software** Kontrollkästchen, und wählen Sie dann **herunterladen und installieren**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-126">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="a51c5-127">Wenn die bestätigungsmeldung angezeigt wird, wählen Sie die Option **Format** SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="a51c5-127">When the confirmation message appears, select the option to **Format** the SD Card.</span></span> 
     > [!NOTE]
     > <span data-ttu-id="a51c5-128">Sehen Sie sich für die **Format** bestätigungsmeldung während des Setups.</span><span class="sxs-lookup"><span data-stu-id="a51c5-128">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="a51c5-129">Die Nachricht von einer anderen open-Anwendung ausgeblendet werden kann, aber es ist wichtig, die Format-Option ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="a51c5-129">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="a51c5-130">Wenn das Laufwerk ordnungsgemäß formatiert ist nicht, schlägt der Start fehl.</span><span class="sxs-lookup"><span data-stu-id="a51c5-130">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="a51c5-131">Die Nachricht **der SD-Karte kann** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a51c5-131">The message **Your SD card is ready** appears.</span></span>

     ![SD-Karte bereit Nachricht](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="a51c5-133">Minimieren Sie diese Seite.</span><span class="sxs-lookup"><span data-stu-id="a51c5-133">Minimize this page.</span></span>  <span data-ttu-id="a51c5-134">Sie werden darauf später zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a51c5-134">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="a51c5-135">Erstellen eines Bereitstellungspakets für Intune-Registrierung</span><span class="sxs-lookup"><span data-stu-id="a51c5-135">Create a provisioning package for Intune enrollment</span></span>
1. <span data-ttu-id="a51c5-136">Installieren die Windows-Konfigurationsentwurf app anhand der Schritte in [Installieren von Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span><span class="sxs-lookup"><span data-stu-id="a51c5-136">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="a51c5-137">Öffnen der **Windows Imaging- und Konfigurations-Designer**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-137">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="a51c5-138">Wählen Sie **Desktopgeräte bereitstellen** zum Erstellen eines Projekts</span><span class="sxs-lookup"><span data-stu-id="a51c5-138">Choose **Provision desktop devices** to create a project</span></span> 

     ![Auswählen von Desktops Bereitstellen von Diensten](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="a51c5-140">Geben Sie die **Projektdetails** je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="a51c5-140">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="a51c5-141">Wählen Sie dann **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-141">Then select **Finish**.</span></span>
5. <span data-ttu-id="a51c5-142">Wechseln Sie zu der **Kontoverwaltung** Seite und wählen Sie **bei Azure AD registrieren**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-142">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
      > [!NOTE]
     > <span data-ttu-id="a51c5-143">Installieren der app aus dem Microsoft Store oder das Windows Assessment und Deployment Kit (ADK) ist in Ordnung.</span><span class="sxs-lookup"><span data-stu-id="a51c5-143">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![In Azure AD registrieren auswählen](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="a51c5-145">Neben **Massentokens**, geben Sie ein Massenladen Ablauf des Tokens.</span><span class="sxs-lookup"><span data-stu-id="a51c5-145">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="a51c5-146">Wählen Sie **Tokenabruf Bulk**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-146">Select **Get Bulk Token**.</span></span> <span data-ttu-id="a51c5-147">Für die Verbindung mit Azure AD wird eine Meldung-Anmeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a51c5-147">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD-Anmeldeseite](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="a51c5-149">Geben Sie den Benutzernamen des Mandanten (z. B. john@mycompany.onmicrosoft.com) und das Kennwort ein.</span><span class="sxs-lookup"><span data-stu-id="a51c5-149">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>   
9. <span data-ttu-id="a51c5-150">Stimmen Sie die Konfigurationsentwurf für Windows-app auf Ihrem Azure AD die Informationen zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="a51c5-150">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span> 
10. <span data-ttu-id="a51c5-151">Eine Nachricht auf der Seite zeigt, dass das Bulk-AAD-Token wurde erfolgreich abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="a51c5-151">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![BULK-token-erfolgreich-Meldung](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="a51c5-153">Wählen Sie **wechseln Sie zur erweiterten Editor**, und wählen Sie dann *Ja*.</span><span class="sxs-lookup"><span data-stu-id="a51c5-153">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![Wechseln Sie zur erweiterten Editor-Seite "Bestätigung"](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="a51c5-155">Unter **ausgewählt Anpassungen**, lassen Sie die **Konto** Einstellungen, aber alle anderen Einstellungen entfernen:</span><span class="sxs-lookup"><span data-stu-id="a51c5-155">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="a51c5-156">Wählen Sie **OOBE**, und wählen Sie dann **entfernen**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-156">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="a51c5-157">Wenn **SharedPC** ist aufgeführt, wählen Sie ihn, und wählen Sie dann **entfernen**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-157">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![Entfernen von Anpassungen](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="a51c5-159">Wählen Sie **exportieren**, und wählen Sie dann **Bereitstellung Paket**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-159">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![Bereitstellung Paket auswählen](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="a51c5-161">Klicken Sie auf der nächsten Seite die Standardeinstellungen übernehmen, und wählen **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-161">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="a51c5-162">In diesem Fall auf der nächsten Seite übernehmen Sie die Standardeinstellungen, und klicken Sie auf Weiter.</span><span class="sxs-lookup"><span data-stu-id="a51c5-162">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="a51c5-163">Ändern der **Bereitstellung Paket** Ziel oder lassen Sie den Standardpfad, und drücken Sie **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-163">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="a51c5-164">Wählen Sie **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-164">Select **Build**.</span></span>
20. <span data-ttu-id="a51c5-165">Wählen Sie die **Ausgabespeicherort** verknüpfen, sodass Sie die ppkg-Datei zugreifen können, wenn er bereit ist.</span><span class="sxs-lookup"><span data-stu-id="a51c5-165">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![Speicherort der ausgabeverknüpfungen](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="a51c5-167">Wählen Sie **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="a51c5-167">Select **Finish**.</span></span>
22. <span data-ttu-id="a51c5-168">Wechseln Sie zur Datei-Explorer aus, und kopieren Sie das Paket auf Ihrem Gerät IoT Core.</span><span class="sxs-lookup"><span data-stu-id="a51c5-168">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="a51c5-169">Speichern Sie es auf der MicroSD-Karte unter dem **MainOS** Laufwerk in der **c:\windows\provisioning\packages** Ordner.</span><span class="sxs-lookup"><span data-stu-id="a51c5-169">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="a51c5-170">Sie müssen zum Gewähren von Berechtigungen zum Speichern der Datei in diesem Ordner.</span><span class="sxs-lookup"><span data-stu-id="a51c5-170">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="a51c5-171">Bereitstellen Sie und registrieren Sie des IoT Core-Geräts bei Intune</span><span class="sxs-lookup"><span data-stu-id="a51c5-171">Provision and enroll the IoT Core device in Intune</span></span>
1. <span data-ttu-id="a51c5-172">Legen Sie die MicroSD-Karte in Ihrer IoT Core-Geräts ein.</span><span class="sxs-lookup"><span data-stu-id="a51c5-172">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="a51c5-173">Aktivieren Sie auf Ihrem Gerät IoT Core, und warten sie beim Starten und den standardmäßigen Bildschirm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a51c5-173">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span> 
3. <span data-ttu-id="a51c5-174">Geben Sie auf der Microsoft Intune-Konsole im Azure-Portal zurück.</span><span class="sxs-lookup"><span data-stu-id="a51c5-174">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="a51c5-175">Ihr Gerät sollte in der Liste der Geräte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a51c5-175">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="a51c5-176">Registrierung kann es sich um 15 Minuten oder mehr dauern.</span><span class="sxs-lookup"><span data-stu-id="a51c5-176">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Liste der Intune-Geräte](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="a51c5-178">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="a51c5-178">Next steps</span></span>
- <span data-ttu-id="a51c5-179">[Anzeigen von Gerätedetails in Intune](https://docs.microsoft.com/intune/device-inventory).</span><span class="sxs-lookup"><span data-stu-id="a51c5-179">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="a51c5-180">[Das Gerät, rufen Sie die neuesten Richtlinien und Aktionen mit Intune synchronisieren,](https://docs.microsoft.com/intune/device-sync).</span><span class="sxs-lookup"><span data-stu-id="a51c5-180">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="a51c5-181">[Starten Sie das Gerät bei Intune Remote neu](https://docs.microsoft.com/intune/device-restart).</span><span class="sxs-lookup"><span data-stu-id="a51c5-181">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
