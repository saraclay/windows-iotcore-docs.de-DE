---
title: Windows-Debugger
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Windows-Debugger zum Debuggen von Ihrem Geräts Windows IoT Core verwenden.
keywords: Windows Iot, Debugger, Debuggen, Windows-Debugger, Gerät, tools
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513305"
---
# <a name="windows-debugger-windbg"></a><span data-ttu-id="9a232-104">Windows Debugger (WinDbg)</span><span class="sxs-lookup"><span data-stu-id="9a232-104">Windows Debugger (WinDbg)</span></span>
<span data-ttu-id="9a232-105">Debuggen Sie Ihres Windows 10 IoT Core-Geräts mit dem leistungsfähige Windows-Debugger, WinDbg an.</span><span class="sxs-lookup"><span data-stu-id="9a232-105">Debug your Windows 10 IoT Core device using the powerful Windows debugger, WinDbg.</span></span>

<span data-ttu-id="9a232-106">In den folgenden Abschnitten wird beschrieben, wie die Verbindung wurde erfolgreich mit WinDbg auf einem Windows 10 IoT Core-Gerät für das Debuggen.</span><span class="sxs-lookup"><span data-stu-id="9a232-106">The following sections describe how to successfully connect with WinDbg to a Windows 10 IoT Core device for debugging purposes.</span></span>  <span data-ttu-id="9a232-107">Dies schließt eine Beschreibung der erforderlichen softwareeinstellungen auf dem Gerät als auch die physische Hardware-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="9a232-107">This includes a description of the necessary software settings on the device as well as the physical hardware connections.</span></span>  

<span data-ttu-id="9a232-108">WinDbg ist ein sehr leistungsfähigen Debugger, dem meisten Windows-Entwickler kennen.</span><span class="sxs-lookup"><span data-stu-id="9a232-108">WinDbg is a very powerful debugger that most Windows developers are familiar with.</span></span>  <span data-ttu-id="9a232-109">Aber wenn Sie gerade einsteigen erst und mehr über WinDbg erfahren möchten, besuchen Sie die folgenden Links:</span><span class="sxs-lookup"><span data-stu-id="9a232-109">However, if you are just getting started and would like to learn more about WinDbg, please visit the following links:</span></span>

* [<span data-ttu-id="9a232-110">Debugtools für Windows</span><span class="sxs-lookup"><span data-stu-id="9a232-110">Debugging Tools for Windows</span></span>](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [<span data-ttu-id="9a232-111">Erste Schritte mit Windows-Debuggen</span><span class="sxs-lookup"><span data-stu-id="9a232-111">Getting Started with Windows Debugging</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [<span data-ttu-id="9a232-112">Dump Absturzanalyse mit WinDbg</span><span class="sxs-lookup"><span data-stu-id="9a232-112">Crash Dump Analysis Using WinDbg</span></span>](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a><span data-ttu-id="9a232-113">MinnowBoard Max (MBM)</span><span class="sxs-lookup"><span data-stu-id="9a232-113">MinnowBoard Max (MBM)</span></span> 

<span data-ttu-id="9a232-114">Sie können WinDbg an das MinnowBoard Max-Gerät mit einer Netzwerkverbindung verbinden.</span><span class="sxs-lookup"><span data-stu-id="9a232-114">You can connect WinDbg to the MinnowBoard Max device using a network connection.</span></span>

### <a name="setup-network-connection"></a><span data-ttu-id="9a232-115">Netzwerk-einrichtungsverbindung</span><span class="sxs-lookup"><span data-stu-id="9a232-115">Setup network connection</span></span>

<span data-ttu-id="9a232-116">Um Kerneldebugging mit WinDbg über ein Netzwerk zu ermöglichen, sicher, dass folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="9a232-116">In order to enable kernel debugging with WinDbg over a network, ensure that:</span></span>

* <span data-ttu-id="9a232-117">Ein Ethernet-Kabel ist mit MinnowBoard Max-Gerät mit dem Netzwerk verbunden.</span><span class="sxs-lookup"><span data-stu-id="9a232-117">An Ethernet cable is connected to MinnowBoard Max device to your network</span></span> 

* <span data-ttu-id="9a232-118">Das MinnowBoard Max-Gerät verfügt über eine gültige IP-Adresse in Ihrem Netzwerk</span><span class="sxs-lookup"><span data-stu-id="9a232-118">The MinnowBoard Max device has a valid IP address in your network</span></span>

* <span data-ttu-id="9a232-119">Um das MinnowBoard Max-Gerät über eine aktive Verbindung [PowerShell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="9a232-119">An active connection to the MinnowBoard Max device via [PowerShell](../connect-your-device/PowerShell.md)</span></span> 

<span data-ttu-id="9a232-120">Verwenden die aktive Verbindung mit PowerShell, führen Sie die folgenden Befehle auf der MinnowBoard Max zum Aktivieren des Debuggens über das Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="9a232-120">Using the active PowerShell connection, execute the following commands on the MinnowBoard Max to enable debugging over the network.</span></span>

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * <span data-ttu-id="9a232-121">Dieser Befehl aktiviert das debugging über das Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="9a232-121">This command enables debugging over the network.</span></span>  <span data-ttu-id="9a232-122">Darüber hinaus gibt es die IP-Adresse des Computers, in denen WinDbg ausgeführt wird (DEV_PC_IP_ADDRESS), die netzwerkportnummer, die für die Verbindung ("port_num"), und einen eindeutigen Schlüssel verwenden, um zur Unterscheidung mehrerer Verbindungen (Schlüssel) verwendet werden</span><span class="sxs-lookup"><span data-stu-id="9a232-122">Additionally, it specifies the IP address of the PC where WinDbg will be running (DEV_PC_IP_ADDRESS), the network port number to use for the connection (PORT_NUM), and a unique key to be used to differentiate multiple connections (KEY)</span></span> 

    * <span data-ttu-id="9a232-123">Für "port_num" und den Schlüssel können Sie die folgenden Werte als Beispiele: 50045 und 1.2.3.4 kostenlos, obwohl Sie sind, nach Bedarf ändern</span><span class="sxs-lookup"><span data-stu-id="9a232-123">For PORT_NUM and KEY, you can use the following values as examples: 50045 and 1.2.3.4 respectively, although you are free to change them as you see fit</span></span>
    
* `bcdedit -debug on`

    * <span data-ttu-id="9a232-124">Dieser Befehl aktiviert das debugging, die auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="9a232-124">This command turns on debugging on the device</span></span> 

* <span data-ttu-id="9a232-125">Starten Sie WinDbg auf das Entwickler-PC mit der "port_num" und die Schlüsselwerte in den vorherigen Schritten angegeben sind, wie folgt: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span><span class="sxs-lookup"><span data-stu-id="9a232-125">On the developer PC, start WinDbg with the PORT_NUM and the KEY values provided in the previous steps as follows: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span></span>

> [!NOTE]
> <span data-ttu-id="9a232-126">Wenn Sie keines der Windows-Kits installiert haben, finden Sie möglicherweise WinDbg unter</span><span class="sxs-lookup"><span data-stu-id="9a232-126">If you have any of the Windows kits installed, you may find WinDbg under</span></span>
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* <span data-ttu-id="9a232-127">Neustart des Geräts IoTCore und zum an den Debugger erneut eine Verbindung herstellen</span><span class="sxs-lookup"><span data-stu-id="9a232-127">Reboot the IoTCore device to reconnect to the debugger</span></span>

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a><span data-ttu-id="9a232-128">Raspberry Pi 2 oder 3 (RPi2 oder RPi3)</span><span class="sxs-lookup"><span data-stu-id="9a232-128">Raspberry Pi 2 or 3 (RPi2 or RPi3)</span></span> 

<span data-ttu-id="9a232-129">Sie können WinDbg auf Raspberry Pi 2 oder 3, die über eine serielle Verbindung verbinden.</span><span class="sxs-lookup"><span data-stu-id="9a232-129">You can connect WinDbg to the Raspberry Pi 2 or 3 using a serial connection.</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="9a232-130">Serielle einrichtungsverbindung</span><span class="sxs-lookup"><span data-stu-id="9a232-130">Setup serial connection</span></span>

<span data-ttu-id="9a232-131">Um Kerneldebugging mit WinDbg über eine serielle Verbindung zu ermöglichen, sicher, dass folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="9a232-131">In order to enable kernel debugging with WinDbg over a serial connection, ensure that:</span></span>

* <span data-ttu-id="9a232-132">Sie haben ein Debug-Kabel, z. B. das USB-zu-Gültigkeitsdauer (TTL) für die serielle Kabel von [Adafruit](https://www.adafruit.com/product/954) oder [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span><span class="sxs-lookup"><span data-stu-id="9a232-132">You have a debug cable such as the USB-to-TTL Serial Cable from [Adafruit](https://www.adafruit.com/product/954) or [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span></span> 

* <span data-ttu-id="9a232-133">Ein Ethernet-Kabel oder aktive WiFi mit Ihrem Raspberry Pi 2 oder 3-Gerät Ihres Netzwerks (für IP-Verbindungen wie SSH oder PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9a232-133">An Ethernet cable or active WiFi connecting your Raspberry Pi 2 or 3 device to your network (for IP connections like SSH or PowerShell)</span></span>

* <span data-ttu-id="9a232-134">Der Raspberry Pi 2- oder 3-Gerät verfügt über eine gültige IP-Adresse in Ihrem Netzwerk</span><span class="sxs-lookup"><span data-stu-id="9a232-134">The Raspberry Pi 2 or 3 device has a valid IP address in your network</span></span>

* <span data-ttu-id="9a232-135">Eine aktive Verbindung mit dem Raspberry Pi 2- oder 3-Gerät über [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md)</span><span class="sxs-lookup"><span data-stu-id="9a232-135">An active connection to the Raspberry Pi 2 or 3 device via [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md)</span></span>

<span data-ttu-id="9a232-136">UART0 wird auf dem Raspberry Pi 2- oder 3-Gerät für die Kernel-debugging-Verbindung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9a232-136">UART0 will be used on the Raspberry Pi 2 or 3 device for the kernel debugging connection.</span></span>  <span data-ttu-id="9a232-137">Das folgende Beispiel zeigt die Pin-Zuordnungen, die für den Raspberry Pi 2- oder 3 sowie die seriellen Kabel:</span><span class="sxs-lookup"><span data-stu-id="9a232-137">The following shows the pin mappings for the Raspberry Pi 2 or 3 as well as the serial cables:</span></span> 

        Raspberry Pi 2 or 3 pins:
            Pin #6 : GND
            Pin #8 : UART0 TX (3.3V)
            pin #10: UART0 RX (3.3V)

        Adafruit Cable:
            Black  : GND
            White  : RX  (3.3V)
            Green  : TX  (3.3V)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
        
        FTDI Cable:
            Black  : GND
            Brown  : CTS (NOT USED)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
            Orange : TX  (3.3V)
            Yellow : RX  (3.3V)
            Green  : RTS (NOT USED)
            
<span data-ttu-id="9a232-138">Die grundlegende Idee zum Treffen der richtigen seriellen Verbindungen ist zu beachten, dass während der ein Gerät die TX verwendet, um Daten zu übertragen, das andere Gerät die RX verwendet, um die Daten zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="9a232-138">The basic idea for making the correct serial connections is to remember that while one device uses its TX to transmit data, the other device uses its RX to receive the data.</span></span>  <span data-ttu-id="9a232-139">Empfohlene Verbindungen sind nachfolgend aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="9a232-139">Recommended connections are listed below:</span></span>

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> <span data-ttu-id="9a232-140">Der EFIESP-Verbindung wird nicht mehr erstellt.</span><span class="sxs-lookup"><span data-stu-id="9a232-140">The EFIESP junction is no longer created.</span></span> <span data-ttu-id="9a232-141">Sie müssen ihn selbst bereitstellen, können Sie Mountvol-Befehl verwenden, um die GUID zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9a232-141">You'll have to mount it yourself,you can use mountvol command to get the GUID.</span></span>
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

<span data-ttu-id="9a232-142">Verwenden die aktive Verbindung mit PowerShell, führen Sie die folgenden Befehle auf Raspberry Pi 2 oder 3-Gerät über die serielle Verbindung Debuggen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9a232-142">Using the active PowerShell connection, execute the following commands on the Raspberry Pi 2 or 3 device to enable debugging over the serial connection.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * <span data-ttu-id="9a232-143">Der obige Befehl aktiviert die serielle Verbindung für das Debuggen</span><span class="sxs-lookup"><span data-stu-id="9a232-143">The above command enables the serial connection for debugging</span></span>
    * <span data-ttu-id="9a232-144">Die Baudrate für den Raspberry Pi 2- oder 3 ist hartcodiert, 921600, sodass Sie keine angegeben</span><span class="sxs-lookup"><span data-stu-id="9a232-144">The baud-rate for the Raspberry Pi 2 or 3 is hard-coded to 921600, so you don't have to specify it</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * <span data-ttu-id="9a232-145">Dieser Befehl aktiviert das debugging, die auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="9a232-145">This command turns on debugging on the device</span></span> 

<span data-ttu-id="9a232-146">Auf das Entwickler-PC Abrufen der der COM-Port-Number-PORT im System für das USB-zu-TTL-Kabel zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="9a232-146">On the developer PC, get the COM port number PORT assigned in the system for the USB-to-TTL cable.</span></span> <span data-ttu-id="9a232-147">Dies wird im Geräte-Manager unter "Anschlüsse (COM und LPT)" verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="9a232-147">This will be available in Device Manager under "Ports (COM & LPT)".</span></span>

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * <span data-ttu-id="9a232-148">Starten Sie WinDbg, mit der Portnummer</span><span class="sxs-lookup"><span data-stu-id="9a232-148">Start WinDbg with the PORT number</span></span>
    
> [!NOTE]
> <span data-ttu-id="9a232-149">Wenn Sie keines der Windows-Kits installiert haben, finden Sie möglicherweise WinDbg unter</span><span class="sxs-lookup"><span data-stu-id="9a232-149">If you have any of the Windows kits installed, you may find WinDbg under</span></span>
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* <span data-ttu-id="9a232-150">Neustart des Geräts IoTCore und zum an den Debugger erneut eine Verbindung herstellen</span><span class="sxs-lookup"><span data-stu-id="9a232-150">Reboot the IoTCore device to reconnect to the debugger</span></span>


## <a name="dragonboard-db"></a><span data-ttu-id="9a232-151">DragonBoard (DB)</span><span class="sxs-lookup"><span data-stu-id="9a232-151">DragonBoard (DB)</span></span> 
___

<span data-ttu-id="9a232-152">Sie können WinDbg auf den DragonBoard über eine serielle oder USB-Verbindung verbinden.</span><span class="sxs-lookup"><span data-stu-id="9a232-152">You can connect WinDbg to the DragonBoard using a serial or USB connection.</span></span>

<span data-ttu-id="9a232-153">Verwenden die aktive PowerShell- oder SSH-Verbindung mit Ihrem DragonBoard, führen Sie die folgenden Befehle zum Debuggen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9a232-153">Using the active PowerShell or SSH connection to your DragonBoard, execute the following commands to enable debugging.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * <span data-ttu-id="9a232-154">Ermöglicht dem debugger</span><span class="sxs-lookup"><span data-stu-id="9a232-154">Enables the debugger</span></span>

### <a name="setup-usb-connection"></a><span data-ttu-id="9a232-155">USB-Verbindung einrichten</span><span class="sxs-lookup"><span data-stu-id="9a232-155">Setup USB connection</span></span>
<span data-ttu-id="9a232-156">Standardmäßig werden die USB-Debugger-Einstellungen in die testbilder konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="9a232-156">By default the USB debugger settings are configured in the test images.</span></span> 

> [!NOTE]
> <span data-ttu-id="9a232-157">Sobald USB-Kernel-Debugger auf ist, funktionieren USB-Anschlüsse auf dem Gerät DragonBoard möglicherweise nicht (d. h. Tastatur, Usb-Ethernet-möglicherweise nicht funktionieren).</span><span class="sxs-lookup"><span data-stu-id="9a232-157">Once USB kernel debugger is on, USB ports on the DragonBoard device might not work (i.e. keyboard, usb ethernet might not work).</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="9a232-158">Serielle einrichtungsverbindung</span><span class="sxs-lookup"><span data-stu-id="9a232-158">Setup serial connection</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * <span data-ttu-id="9a232-159">Konfiguriert den seriellen Anschluss</span><span class="sxs-lookup"><span data-stu-id="9a232-159">Configures the serial port</span></span>

* <span data-ttu-id="9a232-160">Neustart des Geräts IoTCore und zum an den Debugger erneut eine Verbindung herstellen</span><span class="sxs-lookup"><span data-stu-id="9a232-160">Reboot the IoTCore device to reconnect to the debugger</span></span>
