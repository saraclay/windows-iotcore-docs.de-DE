---
title: Windows 10 IoT Core Dashboard
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über die Funktionsweise von Windows 10 IoT Core Dashboard und zu den ersten Schritten zu erhalten.
keywords: Windows Iot, Windows 10 Iot Core Dashboard, Windows Iot-Dashboard, Geräte
ms.openlocfilehash: d21b67dad15d510564ec7fae28a2431d28faf8be
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513721"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="ab65e-104">Windows 10 IoT Core Dashboard</span><span class="sxs-lookup"><span data-stu-id="ab65e-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="ab65e-105">Windows 10 IoT Core Dashboard ist die beste Möglichkeit zum Herunterladen einrichten und verbinden Sie Ihre Windows 10 IoT Core-Geräte, die alle von Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="ab65e-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="ab65e-106">Sie können die [IoT Core Dashboard](http://go.microsoft.com/fwlink/?LinkID=708576).</span><span class="sxs-lookup"><span data-stu-id="ab65e-106">You can download the [IoT Core Dashboard here](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="ab65e-107">Wenn Sie erkennen, dass Sie einen weißen Bildschirm optimal nutzen, wenn nach dem Herunterladen der IoT-Dashboard zu öffnen, wird es aufgrund eines Problems Treiber.</span><span class="sxs-lookup"><span data-stu-id="ab65e-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may due to a driver issue.</span></span> <span data-ttu-id="ab65e-108">Um dieses Problem zu umgehen, müssen Sie zum Herunterladen der [Zip-Format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) von der Intel-Grafiktreiber und den Treiber manuell installieren.</span><span class="sxs-lookup"><span data-stu-id="ab65e-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="ab65e-109">Einrichten eines neuen Geräts</span><span class="sxs-lookup"><span data-stu-id="ab65e-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="ab65e-110">Dashboard kann nicht verwendet, um den Raspberry Pi 3 b + setup verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ab65e-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="ab65e-111">Wenn Sie eine 3 b +-Gerät verfügen, müssen Sie verwenden die [technical Preview 3 b +](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="ab65e-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="ab65e-112">Lesen Sie die [bekannte Einschränkungen](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) der technical Preview zu bestimmen, ob dies für die Entwicklung geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="ab65e-112">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="ab65e-113">Es ist derzeit ein bekanntes Problem, in denen das Betriebssystem die Partitionen auf die SD-Karte durchläuft und werden aufgefordert, eine "Format"...</span><span class="sxs-lookup"><span data-stu-id="ab65e-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="ab65e-114">Meldung für eine bestimmte Daten-Partition, die nicht mit einem beliebigen Dateisystem enthält.</span><span class="sxs-lookup"><span data-stu-id="ab65e-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="ab65e-115">Bitte ignorieren Sie diese Aufforderung, indem Sie auf "Abbrechen".</span><span class="sxs-lookup"><span data-stu-id="ab65e-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="ab65e-116">Während wir an einer Lösung arbeiten, es wird jedoch empfohlen, wenn Sie auf "Jetzt Format" klicken, Sie die SD-Karte mit dem Image FFU erneut als die Format-Aktion Auswirkungen auf werkseinstellungen zurücksetzen, die den Aktualisierungsprozess und das Gerät nicht aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ab65e-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="ab65e-117">Die IoT-Dashboard vereinfacht, um ein neues Gerät einzurichten.</span><span class="sxs-lookup"><span data-stu-id="ab65e-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="ab65e-118">Ausführliche Anweisungen zum Einstieg finden Sie unter den [Einstieg](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) Seite.</span><span class="sxs-lookup"><span data-stu-id="ab65e-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) page.</span></span>

![IoT-Dashboard-Seite "Setup"](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="ab65e-120">SD-Karte</span><span class="sxs-lookup"><span data-stu-id="ab65e-120">SD card</span></span>
<span data-ttu-id="ab65e-121">Typ, Marke und Modell des von der SD-Karte erheblich wirkt sich auf die Leistung und die Qualität der IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab65e-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="ab65e-122">Eine langsame Karte dauert bis zu fünf Mal länger als starten unsere [Karten empfohlen](../learn-about-hardware/hardwarecompatlist.md).</span><span class="sxs-lookup"><span data-stu-id="ab65e-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="ab65e-123">Ältere, weniger zuverlässig SD-Karten funktioniert möglicherweise nicht selbst.</span><span class="sxs-lookup"><span data-stu-id="ab65e-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="ab65e-124">Wenn Sie bei der Installation Probleme auftreten weiterhin, beachten Sie, und Ersetzen Sie dabei die SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="ab65e-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="ab65e-125">Gerätename</span><span class="sxs-lookup"><span data-stu-id="ab65e-125">Device Name</span></span>
<span data-ttu-id="ab65e-126">Der Standardname für das Gerät ist Minwinpc.</span><span class="sxs-lookup"><span data-stu-id="ab65e-126">The default device name is minwinpc.</span></span> <span data-ttu-id="ab65e-127">Es wird empfohlen, mit einem eindeutigen Element zu ändern, da dies das Gerät im Netzwerk suchen vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="ab65e-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="ab65e-128">Der Gerätename dürfen höchstens 15 Zeichen lang sein und kann Buchstaben, Zahlen und folgenden Zeichen enthalten: @ # $ % ^ & ') (.</span><span class="sxs-lookup"><span data-stu-id="ab65e-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="ab65e-129">-_ {} ~ Wenn Sie den Gerätenamen im IoT-Dashboard ändern, wenn Sie Ihr Gerät einrichten, erfolgt ein automatischer Neustart der erstmaligen, wenn Sie Power, auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="ab65e-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="ab65e-130">Kennwort</span><span class="sxs-lookup"><span data-stu-id="ab65e-130">Password</span></span>
<span data-ttu-id="ab65e-131">Kennwort ist ein Pflichtfeld und muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="ab65e-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="ab65e-132">Festlegen eines Kennworts in IoT-Dashboard ändert das Kennwort für Administrator-Benutzer, die in der Standardeinstellung ist "p@ssw0rd".</span><span class="sxs-lookup"><span data-stu-id="ab65e-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="ab65e-133">Wi-Fi-Verbindung</span><span class="sxs-lookup"><span data-stu-id="ab65e-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="ab65e-134">IoT-Dashboard zeigt alle verfügbaren Netzwerke, denen Ihren PC mit zuvor verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="ab65e-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="ab65e-135">Wenn Sie das gewünschte Wi-Fi-Netzwerk in der Liste nicht angezeigt wird, stellen Sie sicher, dass Sie es auf Ihrem PC verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="ab65e-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="ab65e-136">Wenn Sie das Kontrollkästchen deaktivieren, müssen Sie ein Ethernet-Kabel an das Board nach blinken verbinden.</span><span class="sxs-lookup"><span data-stu-id="ab65e-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="ab65e-137">Ersten Start</span><span class="sxs-lookup"><span data-stu-id="ab65e-137">First boot</span></span>
<span data-ttu-id="ab65e-138">Der erste Start dauert immer länger als alle nachfolgenden Startvorgängen.</span><span class="sxs-lookup"><span data-stu-id="ab65e-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="ab65e-139">Das Betriebssystem dauert einige Zeit zum Installieren und Verbinden mit Ihrem Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="ab65e-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="ab65e-140">Startzeit kann variieren erheblich entsprechend Ihrem SD-Karte.</span><span class="sxs-lookup"><span data-stu-id="ab65e-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="ab65e-141">Beispielsweise hat ein Raspberry Pi 3 ausgeführt wird, auf unsere empfohlenen SD-Karte 3 und 4 Minuten für den ersten Start.</span><span class="sxs-lookup"><span data-stu-id="ab65e-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="ab65e-142">Auf dem gleichen Pi durch eine schlechte Qualität SD-Karte haben wir gesehen, Boot Mal länger als 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="ab65e-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="ab65e-143">Herstellen einer Verbindung mit dem internet</span><span class="sxs-lookup"><span data-stu-id="ab65e-143">Connecting to the internet</span></span>
<span data-ttu-id="ab65e-144">Ihre IoT Core-Geräts mit dem Internet verbunden ist von wesentlicher Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="ab65e-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="ab65e-145">Viele der neueren Boards verfügen über integrierte in Wi-Fi-Adaptern.</span><span class="sxs-lookup"><span data-stu-id="ab65e-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="ab65e-146">Wenn Sie Probleme beim Herstellen einer Verbindung mit Ihrem Netzwerk haben, versuchen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ab65e-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="ab65e-147">Neustarten des Geräts</span><span class="sxs-lookup"><span data-stu-id="ab65e-147">Rebooting the device</span></span>
* <span data-ttu-id="ab65e-148">Unter Verwendung der Ethernet-Kabel</span><span class="sxs-lookup"><span data-stu-id="ab65e-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="ab65e-149">Ein Monitor auf dem Gerät anschließen.</span><span class="sxs-lookup"><span data-stu-id="ab65e-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="ab65e-150">Hier erfahren Sie, Diagnoseinformationen zu Ihrem Gerät</span><span class="sxs-lookup"><span data-stu-id="ab65e-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="ab65e-151">Der offizielle Raspberry Pi 2 Wi-Fi-Adapter kann instabil werden bei der Wi-Fi-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="ab65e-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="ab65e-152">Meine Geräte</span><span class="sxs-lookup"><span data-stu-id="ab65e-152">My Devices</span></span>
___
<span data-ttu-id="ab65e-153">Nachdem Ihr Gerät mit dem Internet verbunden ist, erkennt der IoT-Dashboard automatisch Ihr Gerät.</span><span class="sxs-lookup"><span data-stu-id="ab65e-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="ab65e-154">Um Ihr Gerät zu suchen, wechseln Sie zu **meine Geräte**.</span><span class="sxs-lookup"><span data-stu-id="ab65e-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="ab65e-155">Wenn Ihr Gerät nicht aufgeführt ist, versuchen Sie, einen Neustart des Geräts.</span><span class="sxs-lookup"><span data-stu-id="ab65e-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="ab65e-156">Stellen Sie sicher, dass, wenn es mehrere Geräte im Netzwerk sind, jeweils einen eindeutigen Namen haben.</span><span class="sxs-lookup"><span data-stu-id="ab65e-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="ab65e-157">Stellen Sie außerdem sicher, dass Ihre **windows10iotcoredashboard.exe** ist zulässig, durch die Windows-Firewall zu kommunizieren, durch die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="ab65e-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="ab65e-158">Open **Netzwerk- und Freigabecenter** und suchen Sie dann auf den Typ des Netzwerks (Domäne/privat/öffentlich), die mit Ihrem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="ab65e-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="ab65e-159">Open **Systemsteuerung** , und klicken Sie auf **System und Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="ab65e-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="ab65e-160">Klicken Sie auf **eine app durch die Windows-Firewall zulassen** unter **Windows-Firewall**.</span><span class="sxs-lookup"><span data-stu-id="ab65e-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="ab65e-161">Klicken Sie auf **Ändern der Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ab65e-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="ab65e-162">Suchen **windows10iotcoredashboard.exe** in **zugelassene apps und Features** und aktivieren Sie dann das Kontrollkästchen für die entsprechende Netzwerk (d. h. den Netzwerktyp, die Sie in Schritt 1 gefunden).</span><span class="sxs-lookup"><span data-stu-id="ab65e-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="ab65e-163">Herstellen einer Verbindung Ihres Geräts mit</span><span class="sxs-lookup"><span data-stu-id="ab65e-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="ab65e-164">Wenn Sie nicht, um Ihr Gerät auf dem Dashboard finden können, versuchen Sie es eingeben Ihrer [IP-Adresse] und [: 8080] in den Browser, um die Windows Device Portal betriebsbereit zu machen.</span><span class="sxs-lookup"><span data-stu-id="ab65e-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="ab65e-165">Versuchen Sie einen Neustart Ihres Geräts aus, rufen Sie Ihr Gerät im Dashboard angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab65e-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="ab65e-166">Klicken Sie mit der rechten Maustaste auf, und wählen Sie **im Device Portal geöffnet**.</span><span class="sxs-lookup"><span data-stu-id="ab65e-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="ab65e-167">Hierdurch wird die [Windows Device Portal](../manage-your-device/DevicePortal.md) Seite und ist die beste Möglichkeit zum interagieren mit und verwalten Ihr Gerät.</span><span class="sxs-lookup"><span data-stu-id="ab65e-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![Geräte IoTDashboard anzeigen](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="ab65e-169">Sie können auch mithilfe von Windows PowerShell mit dem Gerät verbinden.</span><span class="sxs-lookup"><span data-stu-id="ab65e-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="ab65e-170">Verbinden mit Azure</span><span class="sxs-lookup"><span data-stu-id="ab65e-170">Connect to Azure</span></span>
___
<span data-ttu-id="ab65e-171">IoT-Dashboard können Sie IoT Core-Geräte mit Azure IoT Hub bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ab65e-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="ab65e-172">Weitere Informationen finden sie unter dieser [Blogbeitrag](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span><span class="sxs-lookup"><span data-stu-id="ab65e-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="ab65e-173">Erfahren Sie, wie Sie mit der IoT-Dashboard mit Azure</span><span class="sxs-lookup"><span data-stu-id="ab65e-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="ab65e-174">Beispiele für schnelle ausführen</span><span class="sxs-lookup"><span data-stu-id="ab65e-174">Quick Run Samples</span></span>
___

<span data-ttu-id="ab65e-175">Führen Sie schnell Beispiele erfordern keine Codekompilierung, Visual Studio-Installation oder SDK herunterladen.</span><span class="sxs-lookup"><span data-stu-id="ab65e-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="ab65e-176">Sie eignen sich hervorragend für schnell überprüfen, wie IoT Core verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ab65e-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="ab65e-177">3D Netzwerkdrucker</span><span class="sxs-lookup"><span data-stu-id="ab65e-177">Network 3D Printer</span></span>
<span data-ttu-id="ab65e-178">Verwenden Sie das Beispiel Netzwerk 3D Drucker auf dem die Verbindung Ihrer 3D-Druckern können sie über Ihr privates Netzwerk auffindbar.</span><span class="sxs-lookup"><span data-stu-id="ab65e-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![IoTDashboard Netzwerkdrucker 3D](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="ab65e-180">Internet-radio</span><span class="sxs-lookup"><span data-stu-id="ab65e-180">Internet radio</span></span>
<span data-ttu-id="ab65e-181">Aktivieren Sie Ihr Windows 10 IoT Core-Gerät in einem Internetradio, die von überall in Ihrem Haus gesteuert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ab65e-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard Internet-radio](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="ab65e-183">IoT Core Blockly</span><span class="sxs-lookup"><span data-stu-id="ab65e-183">IoT Core Blockly</span></span>
<span data-ttu-id="ab65e-184">IoT Core Blockly Beispiel können Ihr Programm eine Raspberry Pi2 "3" und eine Raspberry Pi Sinn Hat mit einem "Block"-Editor in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="ab65e-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
