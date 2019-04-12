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
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>Verwenden WiFi Direct auf Ihrem Windows 10 IoT Core-Gerät

WiFi Direct wird unterstützt, auf Windows 10 IoT Core aktiviert Geräte durch die Verwendung einer WiFi Direct USB-WLAN-Adapter. Müssen auf "true" sein, um sicherzustellen, dass WiFi Direct aktiviert zwei Dinge:
* die Hardware des USB-WLAN-Adapters muss WiFi Direct unterstützen,
* der entsprechende Treiber des USB-WLAN-Adapters muss WiFi Direct zu unterstützen. 

WiFi Direct bietet eine Lösung für die WiFi-Gerät-zu-Gerät-Konnektivität ohne die Notwendigkeit entweder einen drahtlosen Zugriffspunkt (WAP), um die Verbindung einzurichten. Sehen Sie sich die UWP-APIs zur Verfügung, in der [Windows.Devices.WiFiDirect Namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) angezeigt, was mit WiFiDirect möglich.

## <a name="supported-adapters"></a>Unterstützte Adapter

Eine Liste der WLAN-Adapter, die auf Windows 10 IoT Core getestet wurden finden Sie auf unserer [Hardware unterstützt](../learn-about-hardware/HardwareCompatList.md) Seite. 

## <a name="basic-sample-for-wifi-direct"></a>Einfaches Beispiel für WiFi Direct

Sie können ganz einfach testen, die WiFi Direct-Funktionalität mit WiFi Direct UWP [Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect). Wir verwenden die C# Version und führen Sie das Beispiel zwei Geräte.

### <a name="set-up-the-two-devices"></a>Die beiden Geräte einrichten
* MinnowBoardMax (MBM) unter Windows 10 IoT Core (Siehe Anweisungen), mit einem CanaKit WiFi-Dongle
* Herstellen einer Verbindung die MBM mit Monitor, Tastatur und Maus
* Ein Windows-10-PC mit der neuesten Windows 10 Anniversary Update. Der PC (oder Laptop) müssen WiFi Direct (z. B. einem Microsoft Surface-) zu unterstützen.
* Installieren Sie Visual Studio 2017 auf Ihrem Windows 10-PC.
* Klonen oder Herunterladen der WiFi Direct UWP [Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(Stamm der GitHub-Repository ist [hier](https://github.com/Microsoft/Windows-universal-samples)).
* Laden der C# -Version des Beispiels WiFi Direct UWP in Visual Studio 2017

#### <a name="run-the-sample-on-the-two-devices"></a>Führen Sie das Beispiel für die beiden Geräte
* Kompilieren Sie das Beispiel, und klicken Sie mit der sie auf die MBM bereitstellen/ausführen:

    * Legen Sie das Kombinationsfeld "Projektmappenplattformen", "X86"
    * Wählen Sie "Remotecomputer" aus der Dropdownliste "Ausführen"
    * Starten Sie das Beispiel für die MBM ohne Debuggen (drücken Sie STRG + F5 oder durch Auswählen von "Starten ohne Debuggen" im Menü "Debug")
    * Das WiFi Direct-Beispiel, das ausgeführt wird, auf dem Überwachungsserver verbunden werden, um die MBM sollte angezeigt werden.
* Kompilieren Sie das Beispiel, und klicken Sie mit der sie auf dem Windows 10-PC bereitstellen/ausführen:
    * Legen Sie das Kombinationsfeld "Projektmappenplattformen", "X86"
    * Wählen Sie "Local", aus der Dropdownliste "Ausführen"
    * Starten Sie das Beispiel aus (F5 oder STRG + F5)
    * Das WiFi Direct-Beispiel auf Ihrem Windows 10-PC ausführen sollte angezeigt werden.

### <a name="set-up-advertiser-and-connector"></a>Einrichten von Werbetreibenden und -Connector
* Klicken Sie auf die MBM wählen Sie aus (1) "Werbetreibenden", und drücken Sie die Schaltfläche "Start-Ankündigungen"

    * Die MBM wird beginnen mit der Ankündigung selbst auf dem WiFi Direct-Kanal

        ![Bildschirm für die Konfiguration von Werbetreibenden](../media/SetupWiFiDirect/Advertiser01.png)

        Beachten Sie das Banner "Ankündigungsstatus" am unteren Rand der app ein.
    
* Klicken Sie auf der Windows 10-PCs wählen Sie aus (2) "-Connector", und drücken Sie die Schaltfläche "Start-Watcher" 

    * Die Windows 10-PC startet verfügbaren WiFi Direct-Verbindungen werden gesucht
    * Wenn die Überprüfung abgeschlossen ist, sollte der Name des Ihre MBM in der Liste "Geräte ermittelt" angezeigt werden.

        ![Connector-Konfigurationsbildschirm](../media/SetupWiFiDirect/Connector01.png)

        Sehen Sie zwei Geräte aufgeführt (Wir würden gern "Ale-mbm01"), und der Meldung "DeviceWatcher Enumeration wurde abgeschlossen".

### <a name="pair-the-devices"></a>Koppeln Sie die Geräte
* Klicken Sie auf den Windows 10-PC wählen Sie die MBM ("Ale-mbm01" in unserem Beispiel) aus der Liste "Ermittelte Geräte", und drücken Sie die Schaltfläche "Verbinden"
* Drücken Sie auf der Windows 10-PCs "Ja", um die Kopplung initiieren

    ![Connector-Start Kopplung](../media/SetupWiFiDirect/Connector02.png)

* Auf dem Überwachungsserver MBM sollten Sie eine Nachricht mit der PIN

    ![PIN-Dialog Werbetreibenden](../media/SetupWiFiDirect/Advertiser02.png)

* Auf der Windows 10-PCs sollte ein Dialogfeld angezeigt, in denen Sie die PIN eingeben müssen

    ![PIN-Connector-Dialogfeld](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>Auf dem Kanal kommunizieren
* Die beiden Geräte müssen verbunden sein. Sie sollte eine zufällig generierte Geräte-Id (in unserem Beispiel "hqffpzhz.ggg") auf beiden Bildschirmen in der Liste "Verbundene Geräte" angezeigt.

    ![Werbetreibenden verbundenes Gerät](../media/SetupWiFiDirect/Advertiser03.png)

    ![Connector verbundenes Gerät](../media/SetupWiFiDirect/Connector04.png)

* Sie verfügen jetzt über einen Vollduplex-Kanal (oder Socket) einrichten

    * Wählen Sie auf die MBM das Gerät ("hqffpzhz.ggg") aus der Liste "Verbundene Geräte"
    * Geben Sie eine Nachricht in das Textfeld "Geben Sie eine Nachricht"
    * Klicken Sie auf die Schaltfläche "Senden"
    * die von der Windows 10-PCs empfangene Meldung sollte angezeigt werden.
    * Versuchen Sie es Senden von Nachrichten von der Windows 10-PCs, die MBM
