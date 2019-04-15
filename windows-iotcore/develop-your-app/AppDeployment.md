---
title: Bereitstellen einer App mit Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie eine app mithilfe der Visual Studio Remotedebuggen-Funktion bereitstellen.
keywords: Windows Iot, visual Studio, app-Bereitstellung, Remotedebuggen
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513241"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="793e8-104">Bereitstellen einer App mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="793e8-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="793e8-105">Bereitstellen und Debuggen Ihrer Anwendung ist ganz einfach mit Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="793e8-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="793e8-106">Wir verwenden die **Remotedebuggen** Feature zum Bereitstellen der app auf dem lokal verbundenen Windows 10 IoT Core-Gerät.</span><span class="sxs-lookup"><span data-stu-id="793e8-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="793e8-107">Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="793e8-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="793e8-108">Um Remotedebuggen zu verwenden, muss Ihre IoT Core-Geräts zunächst mit gleichen lokalen Netzwerk als Ihrem Entwicklungs-PC angeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="793e8-108">In order to use remote debugging, your IoT Core device must first be connected to same local network as your development PC.</span></span>  
><span data-ttu-id="793e8-109">Finden Sie unter den [Herstellen einer Verbindung mit einem Gerät](../connect-your-device/SetupWiFi.md) Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="793e8-109">See the [Connecting to a device](../connect-your-device/SetupWiFi.md) instructions.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="793e8-110">Bereitstellen einer C# app auf Ihrem Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="793e8-110">Deploy a C# app to your Windows 10 IoT Core device</span></span> 
___

1. <span data-ttu-id="793e8-111">Legen Sie mit der Anwendung in Visual Studio geöffnet ist die Architektur in der Dropdownliste der Symbolleiste aus.</span><span class="sxs-lookup"><span data-stu-id="793e8-111">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="793e8-112">Wenn Sie für den Minnowboard maximalen erstellen, wählen Sie `x86`.</span><span class="sxs-lookup"><span data-stu-id="793e8-112">If you're building for Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="793e8-113">Wenn Sie Raspberry Pi 2-oder Raspberry Pi 3 mit der Dragonboard erstellen, wählen Sie `ARM`.</span><span class="sxs-lookup"><span data-stu-id="793e8-113">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="793e8-114">Klicken Sie anschließend in der Visual Studio-Symbolleiste auf die `Local Machine` Dropdownliste, und wählen Sie `Remote Machine`.</span><span class="sxs-lookup"><span data-stu-id="793e8-114">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![Der Remotecomputer in Visual Studio](../media/AppDeployment/cs-remote-machine-debugging.png)

3. <span data-ttu-id="793e8-116">Visual Studio bietet nun die **Remoteverbindungen** Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="793e8-116">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="793e8-117">Wenn Sie zuvor [PowerShell](../connect-your-device/PowerShell.md) um einen eindeutigen Namen für Ihr Gerät festzulegen, können Sie ihn hier eingeben (in diesem Beispiel verwenden wir **mein Gerät**).</span><span class="sxs-lookup"><span data-stu-id="793e8-117">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="793e8-118">Verwenden Sie andernfalls die IP-Adresse Ihres Windows IoT Core-Geräts.</span><span class="sxs-lookup"><span data-stu-id="793e8-118">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="793e8-119">Wählen Sie nach dem Eingeben der Servername/IP-Geräts `Universal (Unencrypted Protocol)` Authentifizierungsmodus, klicken Sie dann auf **wählen**.</span><span class="sxs-lookup"><span data-stu-id="793e8-119">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![Universelle Authentifizierung](../media/AppDeployment/cs-remote-connections.png)

<span data-ttu-id="793e8-121">Sie überprüfen können, oder ändern Sie diese Werte durch Navigieren zu den Projekteigenschaften (Wählen Sie **Eigenschaften** im Projektmappen-Explorer) auswählen und die `Debug` links auf die Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="793e8-121">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![Registerkarte „Debuggen“](../media/AppDeployment/cs-debug-project-properties.png)

5. <span data-ttu-id="793e8-123">Jetzt sind wir bereit für die Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="793e8-123">Now we're ready to deploy.</span></span> <span data-ttu-id="793e8-124">Drücken Sie einfach F5 (oder die Option Debuggen \| Debuggen starten) zum Starten des Debuggings unsere app.</span><span class="sxs-lookup"><span data-stu-id="793e8-124">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="793e8-125">Daraufhin sollte die app auf dem Bildschirm des Geräts kommen.</span><span class="sxs-lookup"><span data-stu-id="793e8-125">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="793e8-126">Nach der Bereitstellung können Sie festlegen, Haltepunkte, finden Sie unter Variablenwerte usw. Drücken Sie die app auf die Schaltfläche "Debugging beenden" beendet (oder die Option Debuggen \| Debuggen beenden).</span><span class="sxs-lookup"><span data-stu-id="793e8-126">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="793e8-127">Ändern die Konfigurationen-Dropdownliste in Visual Studio-Symbolleiste aus, nach dem erfolgreichen Bereitstellen und Debuggen Ihrer UWP-Anwendung, erstellen eine Releaseversion - `Debug` zu `Release`.</span><span class="sxs-lookup"><span data-stu-id="793e8-127">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="793e8-128">Sie können jetzt erstellen und Bereitstellen Ihrer app auf Ihrem Gerät durch Auswählen von Build \| Projektmappe neu erstellen "und" Build \| Projektmappe bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="793e8-128">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="793e8-129">Bereitstellen einer C++ app auf Ihrem Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="793e8-129">Deploy a C++ app to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="793e8-130">Legen Sie mit der Anwendung in Visual Studio geöffnet ist die Architektur in der Dropdownliste der Symbolleiste aus.</span><span class="sxs-lookup"><span data-stu-id="793e8-130">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="793e8-131">Wenn Sie für den Minnowboard maximalen erstellen, wählen Sie `86`.</span><span class="sxs-lookup"><span data-stu-id="793e8-131">If you're building for Minnowboard Max, select `86`.</span></span> <span data-ttu-id="793e8-132">Wenn Sie für die Raspberry Pi 2- oder 3 erstellen, wählen Sie `ARM`.</span><span class="sxs-lookup"><span data-stu-id="793e8-132">If you're building for Raspberry Pi 2 or 3, select `ARM`.</span></span>

2. <span data-ttu-id="793e8-133">Klicken Sie anschließend in der Visual Studio-Symbolleiste auf die `Local Machine` Dropdownliste, und wählen Sie</span><span class="sxs-lookup"><span data-stu-id="793e8-133">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select</span></span> `Remote Machine`

![Lokalen Computer mit Visual Studio](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. <span data-ttu-id="793e8-135">Als Nächstes der rechten Maustaste auf das Projekt in der **Projektmappen-Explorer** Bereich.</span><span class="sxs-lookup"><span data-stu-id="793e8-135">Next, right click on your project in the **Solution Explorer** pane.</span></span> <span data-ttu-id="793e8-136">Wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="793e8-136">Select **Properties**.</span></span> 

![Eigenschaften in Visual Studio](../media/AppDeployment/cpp-project-properties.png)

4. <span data-ttu-id="793e8-138">Klicken Sie unter **Konfigurationseigenschaften -> Debugging**, ändern Sie die folgenden Felder:</span><span class="sxs-lookup"><span data-stu-id="793e8-138">Under **Configuration Properties -> Debugging**, modify the following fields:</span></span>

    * <span data-ttu-id="793e8-139">**Computername**: Wenn Sie zuvor [PowerShell](../connect-your-device/PowerShell.md) um einen eindeutigen Namen für Ihr Gerät festzulegen, können Sie ihn hier eingeben (in diesem Beispiel verwenden wir **mein Gerät**).</span><span class="sxs-lookup"><span data-stu-id="793e8-139">**Machine Name**: If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my-device**).</span></span> <span data-ttu-id="793e8-140">Verwenden Sie andernfalls die IP-Adresse Ihres Windows IoT Core-Geräts.</span><span class="sxs-lookup"><span data-stu-id="793e8-140">Otherwise, use the IP address of your Windows IoT Core device.</span></span>
    * <span data-ttu-id="793e8-141">**Authentifizierungsmodus**: Legen Sie auf **universell (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="793e8-141">**Authentication Mode**: Set to **Universal (Unencrypted Protocol)**</span></span>
    
![Universelle Authentifizierung](../media/AppDeployment/cpp-debug-project-properties.png)

5. <span data-ttu-id="793e8-143">Jetzt sind wir bereit für die Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="793e8-143">Now we're ready to deploy.</span></span> <span data-ttu-id="793e8-144">Drücken Sie einfach F5 (oder die Option Debuggen \| Debuggen starten) zum Starten des Debuggings unsere app.</span><span class="sxs-lookup"><span data-stu-id="793e8-144">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="793e8-145">Daraufhin sollte die app im Windows IoT Core Gerätebildschirm kommen.</span><span class="sxs-lookup"><span data-stu-id="793e8-145">You should see the app come up in Windows IoT Core device screen.</span></span>

6. <span data-ttu-id="793e8-146">Nach der Bereitstellung können Sie festlegen, Haltepunkte, finden Sie unter Variablenwerte usw. Drücken Sie auf die Schaltfläche "Debugging beenden", um die app zu beenden (oder die Option Debuggen \| Debuggen beenden).</span><span class="sxs-lookup"><span data-stu-id="793e8-146">Once deployed, you can set breakpoints, see variable values, etc. To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="793e8-147">Erfolgreich bereitgestellt und Debuggen Ihrer UWP-Anwendung, erstellen Sie eine Releaseversion: ändern die Konfigurationen-Dropdownliste in Visual Studio-Symbolleiste von `Debug` zu `Release`.</span><span class="sxs-lookup"><span data-stu-id="793e8-147">Having successfully deployed and debugged your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="793e8-148">Sie können jetzt erstellen und Bereitstellen Ihrer app auf Ihrem Gerät durch Auswählen von Build \| Projektmappe neu erstellen "und" Build \| Projektmappe bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="793e8-148">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

