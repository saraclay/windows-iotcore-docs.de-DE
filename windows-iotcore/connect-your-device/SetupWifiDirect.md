---
title: Verwenden WiFi Direct auf Ihrem Windows 10 Iot Core-Gerät
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Einrichten, testen und Wifi Direct auf Geräten mit einem aktivierten USB-WLAN-Adapter verwenden.
keywords: Windows Iot Wifi direct "," Setup "," Wifi ","-Geräte
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513402"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="20386-104">Verwenden WiFi Direct auf Ihrem Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="20386-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="20386-105">WiFi Direct wird unterstützt, auf Windows 10 IoT Core aktiviert Geräte durch die Verwendung einer WiFi Direct USB-WLAN-Adapter.</span><span class="sxs-lookup"><span data-stu-id="20386-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="20386-106">Müssen auf "true" sein, um sicherzustellen, dass WiFi Direct aktiviert zwei Dinge:</span><span class="sxs-lookup"><span data-stu-id="20386-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="20386-107">die Hardware des USB-WLAN-Adapters muss WiFi Direct unterstützen,</span><span class="sxs-lookup"><span data-stu-id="20386-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="20386-108">der entsprechende Treiber des USB-WLAN-Adapters muss WiFi Direct zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="20386-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="20386-109">WiFi Direct bietet eine Lösung für die WiFi-Gerät-zu-Gerät-Konnektivität ohne die Notwendigkeit entweder einen drahtlosen Zugriffspunkt (WAP), um die Verbindung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="20386-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="20386-110">Sehen Sie sich die UWP-APIs zur Verfügung, in der [Windows.Devices.WiFiDirect Namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) angezeigt, was mit WiFiDirect möglich.</span><span class="sxs-lookup"><span data-stu-id="20386-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="20386-111">Unterstützte Adapter</span><span class="sxs-lookup"><span data-stu-id="20386-111">Supported Adapters</span></span>

<span data-ttu-id="20386-112">Eine Liste der WLAN-Adapter, die auf Windows 10 IoT Core getestet wurden finden Sie auf unserer [Hardware unterstützt](../learn-about-hardware/HardwareCompatList.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="20386-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="20386-113">Einfaches Beispiel für WiFi Direct</span><span class="sxs-lookup"><span data-stu-id="20386-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="20386-114">Sie können ganz einfach testen, die WiFi Direct-Funktionalität mit WiFi Direct UWP [Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span><span class="sxs-lookup"><span data-stu-id="20386-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="20386-115">Wir verwenden die C# Version und führen Sie das Beispiel zwei Geräte.</span><span class="sxs-lookup"><span data-stu-id="20386-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="20386-116">Die beiden Geräte einrichten</span><span class="sxs-lookup"><span data-stu-id="20386-116">Set up the two devices</span></span>
* <span data-ttu-id="20386-117">MinnowBoardMax (MBM) unter Windows 10 IoT Core (Siehe Anweisungen), mit einem CanaKit WiFi-Dongle</span><span class="sxs-lookup"><span data-stu-id="20386-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="20386-118">Herstellen einer Verbindung die MBM mit Monitor, Tastatur und Maus</span><span class="sxs-lookup"><span data-stu-id="20386-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="20386-119">Ein Windows-10-PC mit der neuesten Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="20386-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="20386-120">Der PC (oder Laptop) müssen WiFi Direct (z. B. einem Microsoft Surface-) zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="20386-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="20386-121">Installieren Sie Visual Studio 2017 auf Ihrem Windows 10-PC.</span><span class="sxs-lookup"><span data-stu-id="20386-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="20386-122">Klonen oder Herunterladen der WiFi Direct UWP [Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(Stamm der GitHub-Repository ist [hier](https://github.com/Microsoft/Windows-universal-samples)).</span><span class="sxs-lookup"><span data-stu-id="20386-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="20386-123">Laden der C# -Version des Beispiels WiFi Direct UWP in Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="20386-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="20386-124">Führen Sie das Beispiel für die beiden Geräte</span><span class="sxs-lookup"><span data-stu-id="20386-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="20386-125">Kompilieren Sie das Beispiel, und klicken Sie mit der sie auf die MBM bereitstellen/ausführen:</span><span class="sxs-lookup"><span data-stu-id="20386-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="20386-126">Legen Sie das Kombinationsfeld "Projektmappenplattformen", "X86"</span><span class="sxs-lookup"><span data-stu-id="20386-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="20386-127">Wählen Sie "Remotecomputer" aus der Dropdownliste "Ausführen"</span><span class="sxs-lookup"><span data-stu-id="20386-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="20386-128">Starten Sie das Beispiel für die MBM ohne Debuggen (drücken Sie STRG + F5 oder durch Auswählen von "Starten ohne Debuggen" im Menü "Debug")</span><span class="sxs-lookup"><span data-stu-id="20386-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="20386-129">Das WiFi Direct-Beispiel, das ausgeführt wird, auf dem Überwachungsserver verbunden werden, um die MBM sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="20386-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="20386-130">Kompilieren Sie das Beispiel, und klicken Sie mit der sie auf dem Windows 10-PC bereitstellen/ausführen:</span><span class="sxs-lookup"><span data-stu-id="20386-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="20386-131">Legen Sie das Kombinationsfeld "Projektmappenplattformen", "X86"</span><span class="sxs-lookup"><span data-stu-id="20386-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="20386-132">Wählen Sie "Local", aus der Dropdownliste "Ausführen"</span><span class="sxs-lookup"><span data-stu-id="20386-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="20386-133">Starten Sie das Beispiel aus (F5 oder STRG + F5)</span><span class="sxs-lookup"><span data-stu-id="20386-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="20386-134">Das WiFi Direct-Beispiel auf Ihrem Windows 10-PC ausführen sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="20386-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="20386-135">Einrichten von Werbetreibenden und -Connector</span><span class="sxs-lookup"><span data-stu-id="20386-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="20386-136">Klicken Sie auf die MBM wählen Sie aus (1) "Werbetreibenden", und drücken Sie die Schaltfläche "Start-Ankündigungen"</span><span class="sxs-lookup"><span data-stu-id="20386-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="20386-137">Die MBM wird beginnen mit der Ankündigung selbst auf dem WiFi Direct-Kanal</span><span class="sxs-lookup"><span data-stu-id="20386-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        ![Bildschirm für die Konfiguration von Werbetreibenden](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="20386-139">Beachten Sie das Banner "Ankündigungsstatus" am unteren Rand der app ein.</span><span class="sxs-lookup"><span data-stu-id="20386-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="20386-140">Klicken Sie auf der Windows 10-PCs wählen Sie aus (2) "-Connector", und drücken Sie die Schaltfläche "Start-Watcher"</span><span class="sxs-lookup"><span data-stu-id="20386-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="20386-141">Die Windows 10-PC startet verfügbaren WiFi Direct-Verbindungen werden gesucht</span><span class="sxs-lookup"><span data-stu-id="20386-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="20386-142">Wenn die Überprüfung abgeschlossen ist, sollte der Name des Ihre MBM in der Liste "Geräte ermittelt" angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="20386-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![Connector-Konfigurationsbildschirm](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="20386-144">Sehen Sie zwei Geräte aufgeführt (Wir würden gern "Ale-mbm01"), und der Meldung "DeviceWatcher Enumeration wurde abgeschlossen".</span><span class="sxs-lookup"><span data-stu-id="20386-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="20386-145">Koppeln Sie die Geräte</span><span class="sxs-lookup"><span data-stu-id="20386-145">Pair the devices</span></span>
* <span data-ttu-id="20386-146">Klicken Sie auf den Windows 10-PC wählen Sie die MBM ("Ale-mbm01" in unserem Beispiel) aus der Liste "Ermittelte Geräte", und drücken Sie die Schaltfläche "Verbinden"</span><span class="sxs-lookup"><span data-stu-id="20386-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="20386-147">Drücken Sie auf der Windows 10-PCs "Ja", um die Kopplung initiieren</span><span class="sxs-lookup"><span data-stu-id="20386-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![Connector-Start Kopplung](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="20386-149">Auf dem Überwachungsserver MBM sollten Sie eine Nachricht mit der PIN</span><span class="sxs-lookup"><span data-stu-id="20386-149">On the MBM monitor you should a message with the PIN</span></span>

    ![PIN-Dialog Werbetreibenden](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="20386-151">Auf der Windows 10-PCs sollte ein Dialogfeld angezeigt, in denen Sie die PIN eingeben müssen</span><span class="sxs-lookup"><span data-stu-id="20386-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![PIN-Connector-Dialogfeld](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="20386-153">Auf dem Kanal kommunizieren</span><span class="sxs-lookup"><span data-stu-id="20386-153">Talk on the channel</span></span>
* <span data-ttu-id="20386-154">Die beiden Geräte müssen verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="20386-154">The two devices should be connected.</span></span> <span data-ttu-id="20386-155">Sie sollte eine zufällig generierte Geräte-Id (in unserem Beispiel "hqffpzhz.ggg") auf beiden Bildschirmen in der Liste "Verbundene Geräte" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="20386-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![Werbetreibenden verbundenes Gerät](../media/SetupWiFiDirect/Advertiser03.png)

    ![Connector verbundenes Gerät](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="20386-158">Sie verfügen jetzt über einen Vollduplex-Kanal (oder Socket) einrichten</span><span class="sxs-lookup"><span data-stu-id="20386-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="20386-159">Wählen Sie auf die MBM das Gerät ("hqffpzhz.ggg") aus der Liste "Verbundene Geräte"</span><span class="sxs-lookup"><span data-stu-id="20386-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="20386-160">Geben Sie eine Nachricht in das Textfeld "Geben Sie eine Nachricht"</span><span class="sxs-lookup"><span data-stu-id="20386-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="20386-161">Klicken Sie auf die Schaltfläche "Senden"</span><span class="sxs-lookup"><span data-stu-id="20386-161">press the "Send" button</span></span>
    * <span data-ttu-id="20386-162">die von der Windows 10-PCs empfangene Meldung sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="20386-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="20386-163">Versuchen Sie es Senden von Nachrichten von der Windows 10-PCs, die MBM</span><span class="sxs-lookup"><span data-stu-id="20386-163">try sending a message from the Windows 10 PC to the MBM</span></span>
