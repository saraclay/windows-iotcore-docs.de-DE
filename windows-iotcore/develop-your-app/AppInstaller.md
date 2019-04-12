---
title: Installieren der app auf ein Gerät IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Ihre app mithilfe der Windows Device Portal oder im Rahmen der IoT-core-Image.
keywords: Windows Iot, app-Installation, Windows Device Portal-,-Geräte
ms.openlocfilehash: 6e188eaef6551548c6c71ac50859516d4cbe7e9c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513033"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="c9bf8-104">Installieren der app auf ein Gerät IoT Core</span><span class="sxs-lookup"><span data-stu-id="c9bf8-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="c9bf8-105">Sie können Ihre app mit einer der beiden Methoden, die unten aufgeführten installieren.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="c9bf8-106">Die Methode mithilfe der Windows Device Portal ist nur für entwicklerszenarien.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-106">The method using the Windows Device Portal is only for developer scenarios.</span></span> <span data-ttu-id="c9bf8-107">Die anderen beiden Methoden sind für Produktionsszenarien.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-107">The other two methods are for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="c9bf8-108">Mithilfe von Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c9bf8-108">Using Windows Device Portal</span></span>

<span data-ttu-id="c9bf8-109">Für diese Methode müssen Sie sicherstellen, dass Sie mit dem Internet verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-109">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="c9bf8-110">Wenn Sie keinen Zugriff auf das Internet haben, haben Sie auch, eine Peer-zu-Peer-Ethernet-Verbindung zwischen dem Gerät und einem Clientcomputer, die einen Pfad für den Zugriff auf das offene Internet nicht enthält.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-110">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="c9bf8-111">Laufende über die zweite Möglichkeit wird die app installieren, jedoch kann nicht gestartet werden, wenn die app Store angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-111">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="c9bf8-112">Zum Installieren die Anwendung auf dem Gerät führen Sie die folgenden:</span><span class="sxs-lookup"><span data-stu-id="c9bf8-112">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="c9bf8-113">Öffnen der [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) für Ihr IoT-Gerät.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-113">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="c9bf8-114">In der *Apps* im Menü Ihrer app zu installieren, indem Sie das app-Paket wird hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-114">In the *Apps* menu, install your app by uploading the app package.</span></span>
 ![Installieren der App](../media/AppInstaller/install-app.gif)

3. <span data-ttu-id="c9bf8-116">Bereitstellen der app an.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-116">Deploy the app.</span></span>

4. <span data-ttu-id="c9bf8-117">Die Anwendung wird jetzt in der Liste der Anwendungen auf Ihrem Gerät angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-117">The application will now be visible on the list of applications on your device.</span></span>
 ![App-Liste](../media/AppInstaller/AppList.png)


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="c9bf8-119">Verwenden die Bereitstellung eines Pakets aus WCD</span><span class="sxs-lookup"><span data-stu-id="c9bf8-119">Using provisioning package from WCD</span></span>
<span data-ttu-id="c9bf8-120">Sie können ein Bereitstellungspaket erstellen, mit der app und das Paket auf dem Gerät installieren.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-120">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="c9bf8-121">Diese Methode funktioniert auch auf Geräten, die nicht über eine Internetverbindung verfügen, und ist die bevorzugte Methode für die Installation der Lizenzdatei Store.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-121">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="c9bf8-122">Beispielsweise kann diese Factory-Szenarien, in dem das Gerät nicht mit dem Internet verbunden ist, aber die primäre app ist eine UWP-app Store angemeldet.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-122">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="c9bf8-123">Die Package Family Name (PFN) finden Sie im Windows Dev Center unter **App-Verwaltung > App-Identität**</span><span class="sxs-lookup"><span data-stu-id="c9bf8-123">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="c9bf8-124">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="c9bf8-124">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="c9bf8-125">Wählen Sie **Erweiterte Bereitstellung**, geben Sie den Namen des Projekts und einer Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c9bf8-125">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="c9bf8-126">Wählen Sie Windows 10 IoT Core, für die projekteinstellungen, und überspringen Sie die Bereitstellung paketimports</span><span class="sxs-lookup"><span data-stu-id="c9bf8-126">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="c9bf8-127">Erweitern Sie auf der linken Seite **Laufzeiteinstellungen** und klicken Sie auf **Universal-App installieren > Benutzer Kontext-App**</span><span class="sxs-lookup"><span data-stu-id="c9bf8-127">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="c9bf8-128">Geben Sie den Paketfamiliennamen Ihrer app und klicken Sie auf **hinzufügen**</span><span class="sxs-lookup"><span data-stu-id="c9bf8-128">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="c9bf8-129">Unter den neu hinzugefügten PFN</span><span class="sxs-lookup"><span data-stu-id="c9bf8-129">Under the newly added PFN</span></span>
    - <span data-ttu-id="c9bf8-130">Fügen Sie die AppX-Datei und die zugehörigen Abhängigkeiten hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-130">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="c9bf8-131">Legen Sie die DeploymentOptions "-Force-Ziel Anwendung schließen"</span><span class="sxs-lookup"><span data-stu-id="c9bf8-131">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="c9bf8-132">Für Store apps signiert wird, müssen Sie die Lizenz an.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-132">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="c9bf8-133">Unter UserContextAppLicense,</span><span class="sxs-lookup"><span data-stu-id="c9bf8-133">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="c9bf8-134">Hinzufügen von LicenseProductID (als LicenseID in der XML-Lizenzdatei verfügbar)</span><span class="sxs-lookup"><span data-stu-id="c9bf8-134">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="c9bf8-135">Ändern Sie die Lizenz XML-Erweiterung zum *.ms-Windows-Store-License*.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-135">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="c9bf8-136">Wählen Sie die Lizenz-Produkt-ID auf der linken Seite, und navigieren Sie Ihrer Lizenzdatei, um LicenseInstall Feld zuweisen</span><span class="sxs-lookup"><span data-stu-id="c9bf8-136">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="c9bf8-137">Für signierte nicht über den Store-apps müssen Sie zum Hinzufügen der Datei app.cer unter **Zertifikate > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="c9bf8-137">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="c9bf8-138">Das Paket exportieren</span><span class="sxs-lookup"><span data-stu-id="c9bf8-138">Export the package</span></span>

10. <span data-ttu-id="c9bf8-139">Kopieren Sie die exportierte ppkg-Datei _C:\Windows\Provisioning\Packages_ auf dem IoT-Gerät mit [SSH](../connect-your-device/SSH.md) oder [Powershell](../connect-your-device/powershell.md)) und neu starten.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-139">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="c9bf8-140">Wenn das Gerät neu gestartet, wird das Paket verarbeitet, und die app installiert ist.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-140">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-to-the-iot-core-imageffu"></a><span data-ttu-id="c9bf8-141">Das IoT Core image(.ffu) hinzufügen</span><span class="sxs-lookup"><span data-stu-id="c9bf8-141">Add to the IoT core image(.ffu)</span></span>   
<span data-ttu-id="c9bf8-142">Sie können die app als Teil des IoT Core-Images sich selbst hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-142">You can add the app to be part of the IoT Core image itself.</span></span> <span data-ttu-id="c9bf8-143">Dies ist die weit verbreitete Mechanismus für OEMs.</span><span class="sxs-lookup"><span data-stu-id="c9bf8-143">This is the widely used mechanism for OEMs.</span></span> 

<span data-ttu-id="c9bf8-144">Finden Sie unter Vorgehensweise [Hinzufügen einer app zu Ihrem Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) und [Beispiel-app-Paket](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="c9bf8-144">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
