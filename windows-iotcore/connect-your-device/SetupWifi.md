---
title: Mithilfe von WLAN auf Ihrem Windows 10 IoT Core-Gerät
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum verwenden, einrichten und Konfigurieren von WLAN auf Ihrem Windows 10 IoT Core-Gerät.
keywords: Windows Iot, Wifi, Setup, Geräte
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513401"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="26ab1-104">Mithilfe von WLAN auf Ihrem Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="26ab1-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="26ab1-105">WLAN ist auf Windows 10 IoT Core-Geräten durch die Verwendung von einem USB-WLAN-Adapter unterstützt.</span><span class="sxs-lookup"><span data-stu-id="26ab1-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="26ab1-106">Mithilfe von WLAN bietet alle Funktionen einer Kabelverbindung, einschließlich [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), und Anwendungsdebuggen und Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="26ab1-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="26ab1-107">Eine verkabelte Ethernet-Kabel anschließen überschreibt WiFi wie die Standard-Netzwerkschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="26ab1-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="26ab1-108">Unterstützte Adapter</span><span class="sxs-lookup"><span data-stu-id="26ab1-108">Supported Adapters</span></span>
<span data-ttu-id="26ab1-109">Eine Liste der WLAN-Adapter, die auf Windows 10 IoT Core getestet wurden finden Sie auf unserer [Hardware unterstützt](../learn-about-hardware/HardwareCompatList.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="26ab1-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="26ab1-110">WLAN-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="26ab1-110">Configuring WiFi</span></span>
<span data-ttu-id="26ab1-111">Um WiFi verwenden zu können, müssen Sie Windows 10 IoT Core mit Anmeldeinformationen für das WLAN-Netzwerk zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="26ab1-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="26ab1-112">Neben der Dokumentation zum Companion-app und WPS benutzerdefinierte Lösungen zu erstellen sind eine Reihe von Optionen dafür daher unten aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="26ab1-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="26ab1-113">Benutzerdefinierte Companion-App und WPS Wi-Fi-Onboarding-Beispiele</span><span class="sxs-lookup"><span data-stu-id="26ab1-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="26ab1-114">Derzeit bieten wir eine Reihe von Möglichkeiten für Entwickler zum Erstellen einer benutzerdefinierten Wifi-Onboarding-Lösung für ihr Gerät.</span><span class="sxs-lookup"><span data-stu-id="26ab1-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="26ab1-115">Proben</span><span class="sxs-lookup"><span data-stu-id="26ab1-115">Samples</span></span> | <span data-ttu-id="26ab1-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="26ab1-116">Description</span></span> | <span data-ttu-id="26ab1-117">Vorteile</span><span class="sxs-lookup"><span data-stu-id="26ab1-117">Benefits</span></span>  |  <span data-ttu-id="26ab1-118">Drawbacks</span><span class="sxs-lookup"><span data-stu-id="26ab1-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="26ab1-119">Companion-App</span><span class="sxs-lookup"><span data-stu-id="26ab1-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="26ab1-120">Erstellen einer einfachen Xamarin-app, die WLAN-Ihres Geräts konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="26ab1-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="26ab1-121">Einfach zu verwenden. Multi-Monitor "oder" monitorlose IoT Core "; Clients funktioniert plattformübergreifend.</span><span class="sxs-lookup"><span data-stu-id="26ab1-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="26ab1-122">Developer ist ein eigenes Protokoll erstellen; fordert Entwickler, die zum Implementieren der Sicherheit</span><span class="sxs-lookup"><span data-stu-id="26ab1-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="26ab1-123">IoT-Integration mit Bluetooth-RFCOMM</span><span class="sxs-lookup"><span data-stu-id="26ab1-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="26ab1-124">Erstellen der Lösung zum Konfigurieren Ihres monitorlose IoT-Geräts mit Ihrem WLAN-Verbindung mithilfe von Bluetooth RFCOMM.</span><span class="sxs-lookup"><span data-stu-id="26ab1-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="26ab1-125">Relevante Spitzen oder monitorlosen Geräten; Verwendet vertrauten Technologien und Konzepte. Erfordert keine IoT-Geräte, um eine SoftAP zu starten. Muss keine Firewall-Einstellungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="26ab1-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="26ab1-126">Erfordert die Bluetooth-Unterstützung für Client und Server Geräte; Beispiel gibt nur die Client-app für Windows 10. Server app pre-defines/hartcodierung die Namen der dem Client-Gerät.</span><span class="sxs-lookup"><span data-stu-id="26ab1-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="26ab1-127">IoT-Integration mit AllJoyn</span><span class="sxs-lookup"><span data-stu-id="26ab1-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="26ab1-128">Verknüpfen Sie Remote Ihre monitorlose IoT-Geräte mit Ihrem WLAN-Heimnetzwerk.</span><span class="sxs-lookup"><span data-stu-id="26ab1-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="26ab1-129">Funktioniert mit AllJoyn</span><span class="sxs-lookup"><span data-stu-id="26ab1-129">Works with AllJoyn</span></span> | <span data-ttu-id="26ab1-130">Unterstützung für AllJoyn ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="26ab1-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="26ab1-131">Wi-Fi Protected Setup (WPS) APIs für Geräte</span><span class="sxs-lookup"><span data-stu-id="26ab1-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="26ab1-132">Führen Sie WPS-Ermittlung für das Abfragen der WPS-Methoden, die über das Netzwerk unterstützt.</span><span class="sxs-lookup"><span data-stu-id="26ab1-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="26ab1-133">Nutzen Sie einfach die [WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) und [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) Methoden wi-Fi-Geräte auf bestimmte Netzwerke zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="26ab1-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="26ab1-134">Sie müssen mit diesen APIs ihrer Nutzung vertraut.; nur kompatibel mit WPS-fähigen Routern</span><span class="sxs-lookup"><span data-stu-id="26ab1-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="26ab1-135">Kopfzeilen-Optionen:</span><span class="sxs-lookup"><span data-stu-id="26ab1-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="26ab1-136">Option 1: Startkonfiguration</span><span class="sxs-lookup"><span data-stu-id="26ab1-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="26ab1-137">**Voraussetzung:** Das Windows 10 IoT Core-Gerät benötigt eine Maus, Tastatur, anzeigen und USB-WLAN-Adapter angeschlossen</span><span class="sxs-lookup"><span data-stu-id="26ab1-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="26ab1-138">Beim ersten Starten von Windows 10 IoT Core mit einem unterstützten USB-WLAN-Adapter wird mit einem Konfigurationsbildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="26ab1-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="26ab1-139">Wählen Sie das WLAN-Netzwerk, die, das Sie zum Herstellen einer Verbindung mit und das Kennwort angeben möchten, auf den Bildschirm "Konfiguration".</span><span class="sxs-lookup"><span data-stu-id="26ab1-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="26ab1-140">Klicken Sie auf **verbinden** zum Initiieren der Verbindung.</span><span class="sxs-lookup"><span data-stu-id="26ab1-140">Click **connect** to initiate the connection.</span></span>

![Startbildschirm für WLAN-Konfiguration](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="26ab1-142">Option 2: Standard-App-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="26ab1-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="26ab1-143">**Voraussetzung:** Das Windows 10 IoT Core-Gerät benötigt eine Maus, Tastatur, anzeigen und USB-WLAN-Adapter angeschlossen</span><span class="sxs-lookup"><span data-stu-id="26ab1-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="26ab1-144">Eine alternative Möglichkeit zum Konfigurieren von WLAN ist die Verwendung die Standard-app.</span><span class="sxs-lookup"><span data-stu-id="26ab1-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="26ab1-145">Sie können dies verwenden, konfigurieren oder WiFi-Einstellungen ändern, nachdem das Gerät gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="26ab1-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="26ab1-146">Klicken Sie auf das Symbol für Einstellungen geformten Zahnradsymbol auf der Startseite</span><span class="sxs-lookup"><span data-stu-id="26ab1-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="26ab1-147">Wählen Sie **Netzwerk- und Wi-Fi** im linken Bereich</span><span class="sxs-lookup"><span data-stu-id="26ab1-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="26ab1-148">Klicken Sie auf das WLAN-Netzwerk herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="26ab1-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="26ab1-149">Geben Sie das Kennwort, wenn Sie aufgefordert werden, und klicken Sie auf **verbinden**</span><span class="sxs-lookup"><span data-stu-id="26ab1-149">Supply the password if prompted, and click **Connect**</span></span>

![Standard-App-WLAN-Konfiguration](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="26ab1-151">Monitorlose Optionen:</span><span class="sxs-lookup"><span data-stu-id="26ab1-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="26ab1-152">Option 1: Web-basierten Konfiguration</span><span class="sxs-lookup"><span data-stu-id="26ab1-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="26ab1-153">**Voraussetzung:** Ihr Gerät bereits mit Ihrem lokalen Netzwerk über Ethernet verbunden sein müssen und soll haben einen USB-WLAN-Adapter angeschlossen</span><span class="sxs-lookup"><span data-stu-id="26ab1-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="26ab1-154">Gerät eine mit keine Benutzeroberfläche, Anzeige oder Eingabegeräte, können Sie dennoch konfigurieren über die [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="26ab1-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="26ab1-155">In **Windows 10 IoT Core Dashboard**, *klicken Sie auf* auf die **im Device Portal geöffnet** Symbol für Ihr Gerät.</span><span class="sxs-lookup"><span data-stu-id="26ab1-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="26ab1-156">Geben Sie **Administrator** für den Benutzernamen, und geben Sie Ihr Kennwort (p@ssw0rd standardmäßig)</span><span class="sxs-lookup"><span data-stu-id="26ab1-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="26ab1-157">Klicken Sie auf **Netzwerk** im linken Bereich</span><span class="sxs-lookup"><span data-stu-id="26ab1-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="26ab1-158">Klicken Sie unter **verfügbaren Netzwerke**auf Netzwerk, Sie möchten eine Verbindung herstellen, und geben Sie Anmeldeinformationen für die Verbindung.</span><span class="sxs-lookup"><span data-stu-id="26ab1-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="26ab1-159">Klicken Sie auf **Connect** zum Initiieren der Verbindung</span><span class="sxs-lookup"><span data-stu-id="26ab1-159">Click **Connect** to initiate the connection</span></span>

![Web-basierten WLAN-Konfiguration](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="26ab1-161">Option 2: Herstellen einer Verbindung mit WLAN-Profile</span><span class="sxs-lookup"><span data-stu-id="26ab1-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="26ab1-162">**Voraussetzung:** Ihr Gerät bereits mit Ihrem lokalen Netzwerk über Ethernet verbunden sein müssen und soll haben einen USB-WLAN-Adapter angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="26ab1-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="26ab1-163">Außerdem benötigen Sie einen Windows-PC mit WiFi-Funktion.</span><span class="sxs-lookup"><span data-stu-id="26ab1-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="26ab1-164">WLAN-Profilen mit WiFi einrichten, wird in Windows 10 IoT Core unterstützt.</span><span class="sxs-lookup"><span data-stu-id="26ab1-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="26ab1-165">Finden Sie unter [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) ausführliche Informationen und Beispiele.</span><span class="sxs-lookup"><span data-stu-id="26ab1-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="26ab1-166">Verbinden Sie den Windows-PC mit dem gewünschten drahtlosen Netzwerk aus, und Erstellen von WLAN-Profil-XML-Datei mit den folgenden Befehlen:</span><span class="sxs-lookup"><span data-stu-id="26ab1-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * `netsh wlan show profiles` <span data-ttu-id="26ab1-167">-> Suchen Sie den Namen des Profils, das Sie gerade hinzugefügt haben</span><span class="sxs-lookup"><span data-stu-id="26ab1-167">-> find the name of the profile you just added</span></span>

    * `netsh wlan export profile name=<your profilename>`<span data-ttu-id="26ab1-168">.</span><span class="sxs-lookup"><span data-stu-id="26ab1-168">.</span></span> <span data-ttu-id="26ab1-169">Dadurch wird das Profil in eine XML-Datei exportiert.</span><span class="sxs-lookup"><span data-stu-id="26ab1-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="26ab1-170">Öffnen Sie eine **Datei-Explorer** Fenster und in der Adressleiste `\\<TARGET_DEVICE>\C$\` , und klicken Sie dann EINGABETASTE drücken.</span><span class="sxs-lookup"><span data-stu-id="26ab1-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="26ab1-171">In diesem speziellen Fall `<TARGET_DEVICE>` ist entweder der Name oder die IP-Adresse Ihres Windows 10 IoT Core-Geräts:</span><span class="sxs-lookup"><span data-stu-id="26ab1-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![SMB mit Datei-Explorer](../media/SetupWifi/smb1.png)

    <span data-ttu-id="26ab1-173">Wenn Sie für einen Benutzernamen und Kennwort aufgefordert werden, verwenden Sie die folgenden Anmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="26ab1-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![SMB mit Datei-Explorer](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="26ab1-175">Es ist **dringend empfohlen,** , das Standardkennwort für das Administratorkonto zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="26ab1-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="26ab1-176">Führen Sie die Anweisungen [hier](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="26ab1-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="26ab1-177">Kopieren Sie die exportierte WLAN-Profil-XML-Datei aus dem Windows-PC auf Ihrem Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="26ab1-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="26ab1-178">Verbindung zu Ihrem Gerät [PowerShell](../connect-your-device/PowerShell.md) und fügen Sie das neue WLAN-Profil auf Ihrem Gerät, indem Sie die folgenden Befehle ausführen</span><span class="sxs-lookup"><span data-stu-id="26ab1-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="26ab1-179">Verbinden Sie das Windows 10 IoT Core-Gerät mit drahtlosen Netzwerk über NETSH erleichtert</span><span class="sxs-lookup"><span data-stu-id="26ab1-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="26ab1-180">Stellen Sie sicher, dass Ihr Gerät mit dem Drahtlosnetzwerk verbunden ist und dem Internet erreichen</span><span class="sxs-lookup"><span data-stu-id="26ab1-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="26ab1-181">Herstellen einer Verbindung zu WPA2-PSK persönliche Netzwerke</span><span class="sxs-lookup"><span data-stu-id="26ab1-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="26ab1-182">Wenn Sie mit einem persönlichen WPA2-PSK-WLAN-Netzwerk verbinden möchten, zuerst folgen Sie den obigen Anweisungen, aber nehmen Sie folgende Änderungen in der XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="26ab1-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="26ab1-183">Der einzige Unterschied ist, dass es sich bei Ihrem Windows-PC XML exportiert das Kennwort verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="26ab1-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="26ab1-184">Dadurch wird die Verbindung unsicher.</span><span class="sxs-lookup"><span data-stu-id="26ab1-184">This will make your connection insecure.</span></span>

<span data-ttu-id="26ab1-185">Profil-XML exportiert von Windows-PC:</span><span class="sxs-lookup"><span data-stu-id="26ab1-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="26ab1-186">Änderungen, die auf Windows 10 IoT Core benötigt werden:</span><span class="sxs-lookup"><span data-stu-id="26ab1-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
