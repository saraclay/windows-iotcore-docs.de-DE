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
# <a name="windows-debugger-windbg"></a>Windows Debugger (WinDbg)
Debuggen Sie Ihres Windows 10 IoT Core-Geräts mit dem leistungsfähige Windows-Debugger, WinDbg an.

In den folgenden Abschnitten wird beschrieben, wie die Verbindung wurde erfolgreich mit WinDbg auf einem Windows 10 IoT Core-Gerät für das Debuggen.  Dies schließt eine Beschreibung der erforderlichen softwareeinstellungen auf dem Gerät als auch die physische Hardware-Verbindungen.  

WinDbg ist ein sehr leistungsfähigen Debugger, dem meisten Windows-Entwickler kennen.  Aber wenn Sie gerade einsteigen erst und mehr über WinDbg erfahren möchten, besuchen Sie die folgenden Links:

* [Debugtools für Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [Erste Schritte mit Windows-Debuggen](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [Dump Absturzanalyse mit WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

Sie können WinDbg an das MinnowBoard Max-Gerät mit einer Netzwerkverbindung verbinden.

### <a name="setup-network-connection"></a>Netzwerk-einrichtungsverbindung

Um Kerneldebugging mit WinDbg über ein Netzwerk zu ermöglichen, sicher, dass folgende Aktionen ausführen:

* Ein Ethernet-Kabel ist mit MinnowBoard Max-Gerät mit dem Netzwerk verbunden. 

* Das MinnowBoard Max-Gerät verfügt über eine gültige IP-Adresse in Ihrem Netzwerk

* Um das MinnowBoard Max-Gerät über eine aktive Verbindung [PowerShell](../connect-your-device/PowerShell.md) 

Verwenden die aktive Verbindung mit PowerShell, führen Sie die folgenden Befehle auf der MinnowBoard Max zum Aktivieren des Debuggens über das Netzwerk.

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * Dieser Befehl aktiviert das debugging über das Netzwerk.  Darüber hinaus gibt es die IP-Adresse des Computers, in denen WinDbg ausgeführt wird (DEV_PC_IP_ADDRESS), die netzwerkportnummer, die für die Verbindung ("port_num"), und einen eindeutigen Schlüssel verwenden, um zur Unterscheidung mehrerer Verbindungen (Schlüssel) verwendet werden 

    * Für "port_num" und den Schlüssel können Sie die folgenden Werte als Beispiele: 50045 und 1.2.3.4 kostenlos, obwohl Sie sind, nach Bedarf ändern
    
* `bcdedit -debug on`

    * Dieser Befehl aktiviert das debugging, die auf dem Gerät 

* Starten Sie WinDbg auf das Entwickler-PC mit der "port_num" und die Schlüsselwerte in den vorherigen Schritten angegeben sind, wie folgt: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> Wenn Sie keines der Windows-Kits installiert haben, finden Sie möglicherweise WinDbg unter
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* Neustart des Geräts IoTCore und zum an den Debugger erneut eine Verbindung herstellen

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 oder 3 (RPi2 oder RPi3) 

Sie können WinDbg auf Raspberry Pi 2 oder 3, die über eine serielle Verbindung verbinden.

### <a name="setup-serial-connection"></a>Serielle einrichtungsverbindung

Um Kerneldebugging mit WinDbg über eine serielle Verbindung zu ermöglichen, sicher, dass folgende Aktionen ausführen:

* Sie haben ein Debug-Kabel, z. B. das USB-zu-Gültigkeitsdauer (TTL) für die serielle Kabel von [Adafruit](https://www.adafruit.com/product/954) oder [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105). 

* Ein Ethernet-Kabel oder aktive WiFi mit Ihrem Raspberry Pi 2 oder 3-Gerät Ihres Netzwerks (für IP-Verbindungen wie SSH oder PowerShell)

* Der Raspberry Pi 2- oder 3-Gerät verfügt über eine gültige IP-Adresse in Ihrem Netzwerk

* Eine aktive Verbindung mit dem Raspberry Pi 2- oder 3-Gerät über [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md)

UART0 wird auf dem Raspberry Pi 2- oder 3-Gerät für die Kernel-debugging-Verbindung verwendet werden.  Das folgende Beispiel zeigt die Pin-Zuordnungen, die für den Raspberry Pi 2- oder 3 sowie die seriellen Kabel: 

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
            
Die grundlegende Idee zum Treffen der richtigen seriellen Verbindungen ist zu beachten, dass während der ein Gerät die TX verwendet, um Daten zu übertragen, das andere Gerät die RX verwendet, um die Daten zu empfangen.  Empfohlene Verbindungen sind nachfolgend aufgeführt:

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> Der EFIESP-Verbindung wird nicht mehr erstellt. Sie müssen ihn selbst bereitstellen, können Sie Mountvol-Befehl verwenden, um die GUID zu erhalten.
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

Verwenden die aktive Verbindung mit PowerShell, führen Sie die folgenden Befehle auf Raspberry Pi 2 oder 3-Gerät über die serielle Verbindung Debuggen zu aktivieren.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * Der obige Befehl aktiviert die serielle Verbindung für das Debuggen
    * Die Baudrate für den Raspberry Pi 2- oder 3 ist hartcodiert, 921600, sodass Sie keine angegeben

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * Dieser Befehl aktiviert das debugging, die auf dem Gerät 

Auf das Entwickler-PC Abrufen der der COM-Port-Number-PORT im System für das USB-zu-TTL-Kabel zugewiesen. Dies wird im Geräte-Manager unter "Anschlüsse (COM und LPT)" verfügbar sein.

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * Starten Sie WinDbg, mit der Portnummer
    
> [!NOTE]
> Wenn Sie keines der Windows-Kits installiert haben, finden Sie möglicherweise WinDbg unter
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* Neustart des Geräts IoTCore und zum an den Debugger erneut eine Verbindung herstellen


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

Sie können WinDbg auf den DragonBoard über eine serielle oder USB-Verbindung verbinden.

Verwenden die aktive PowerShell- oder SSH-Verbindung mit Ihrem DragonBoard, führen Sie die folgenden Befehle zum Debuggen zu aktivieren.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * Ermöglicht dem debugger

### <a name="setup-usb-connection"></a>USB-Verbindung einrichten
Standardmäßig werden die USB-Debugger-Einstellungen in die testbilder konfiguriert. 

> [!NOTE]
> Sobald USB-Kernel-Debugger auf ist, funktionieren USB-Anschlüsse auf dem Gerät DragonBoard möglicherweise nicht (d. h. Tastatur, Usb-Ethernet-möglicherweise nicht funktionieren).

### <a name="setup-serial-connection"></a>Serielle einrichtungsverbindung

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * Konfiguriert den seriellen Anschluss

* Neustart des Geräts IoTCore und zum an den Debugger erneut eine Verbindung herstellen
