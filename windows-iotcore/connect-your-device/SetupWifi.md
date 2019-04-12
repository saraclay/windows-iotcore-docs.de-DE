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
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a>Mithilfe von WLAN auf Ihrem Windows 10 IoT Core-Gerät

WLAN ist auf Windows 10 IoT Core-Geräten durch die Verwendung von einem USB-WLAN-Adapter unterstützt. Mithilfe von WLAN bietet alle Funktionen einer Kabelverbindung, einschließlich [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), und Anwendungsdebuggen und Bereitstellung.

> [!NOTE]
> Eine verkabelte Ethernet-Kabel anschließen überschreibt WiFi wie die Standard-Netzwerkschnittstelle.

### <a name="supported-adapters"></a>Unterstützte Adapter
Eine Liste der WLAN-Adapter, die auf Windows 10 IoT Core getestet wurden finden Sie auf unserer [Hardware unterstützt](../learn-about-hardware/HardwareCompatList.md) Seite.

### <a name="configuring-wifi"></a>WLAN-Konfiguration
Um WiFi verwenden zu können, müssen Sie Windows 10 IoT Core mit Anmeldeinformationen für das WLAN-Netzwerk zur Verfügung. Neben der Dokumentation zum Companion-app und WPS benutzerdefinierte Lösungen zu erstellen sind eine Reihe von Optionen dafür daher unten aufgeführt.

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a>Benutzerdefinierte Companion-App und WPS Wi-Fi-Onboarding-Beispiele

Derzeit bieten wir eine Reihe von Möglichkeiten für Entwickler zum Erstellen einer benutzerdefinierten Wifi-Onboarding-Lösung für ihr Gerät. 

> | Proben | Beschreibung | Vorteile  |  Drawbacks  |
> |-------------|----------|---------|---------|
> | [Companion-App](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | Erstellen einer einfachen Xamarin-app, die WLAN-Ihres Geräts konfigurieren können. |  Einfach zu verwenden. Multi-Monitor "oder" monitorlose IoT Core "; Clients funktioniert plattformübergreifend. | Developer ist ein eigenes Protokoll erstellen; fordert Entwickler, die zum Implementieren der Sicherheit |
> | [IoT-Integration mit Bluetooth-RFCOMM](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | Erstellen der Lösung zum Konfigurieren Ihres monitorlose IoT-Geräts mit Ihrem WLAN-Verbindung mithilfe von Bluetooth RFCOMM.  | Relevante Spitzen oder monitorlosen Geräten; Verwendet vertrauten Technologien und Konzepte. Erfordert keine IoT-Geräte, um eine SoftAP zu starten. Muss keine Firewall-Einstellungen anpassen. | Erfordert die Bluetooth-Unterstützung für Client und Server Geräte; Beispiel gibt nur die Client-app für Windows 10. Server app pre-defines/hartcodierung die Namen der dem Client-Gerät. |
> | [IoT-Integration mit AllJoyn](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | Verknüpfen Sie Remote Ihre monitorlose IoT-Geräte mit Ihrem WLAN-Heimnetzwerk. | Funktioniert mit AllJoyn | Unterstützung für AllJoyn ist veraltet. |
> | Wi-Fi Protected Setup (WPS) APIs für Geräte | Führen Sie WPS-Ermittlung für das Abfragen der WPS-Methoden, die über das Netzwerk unterstützt. | Nutzen Sie einfach die [WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) und [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) Methoden wi-Fi-Geräte auf bestimmte Netzwerke zu verbinden. | Sie müssen mit diesen APIs ihrer Nutzung vertraut.; nur kompatibel mit WPS-fähigen Routern|

## <a name="headed-options"></a>Kopfzeilen-Optionen:

### <a name="option-1-startup-configuration"></a>Option 1: Startkonfiguration
**Voraussetzung:** Das Windows 10 IoT Core-Gerät benötigt eine Maus, Tastatur, anzeigen und USB-WLAN-Adapter angeschlossen

Beim ersten Starten von Windows 10 IoT Core mit einem unterstützten USB-WLAN-Adapter wird mit einem Konfigurationsbildschirm angezeigt werden.
Wählen Sie das WLAN-Netzwerk, die, das Sie zum Herstellen einer Verbindung mit und das Kennwort angeben möchten, auf den Bildschirm "Konfiguration". Klicken Sie auf **verbinden** zum Initiieren der Verbindung.

![Startbildschirm für WLAN-Konfiguration](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a>Option 2: Standard-App-Konfiguration
**Voraussetzung:** Das Windows 10 IoT Core-Gerät benötigt eine Maus, Tastatur, anzeigen und USB-WLAN-Adapter angeschlossen

Eine alternative Möglichkeit zum Konfigurieren von WLAN ist die Verwendung die Standard-app. Sie können dies verwenden, konfigurieren oder WiFi-Einstellungen ändern, nachdem das Gerät gestartet wurde.

1. Klicken Sie auf das Symbol für Einstellungen geformten Zahnradsymbol auf der Startseite
2. Wählen Sie **Netzwerk- und Wi-Fi** im linken Bereich
3. Klicken Sie auf das WLAN-Netzwerk herstellen möchten. Geben Sie das Kennwort, wenn Sie aufgefordert werden, und klicken Sie auf **verbinden**

![Standard-App-WLAN-Konfiguration](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a>Monitorlose Optionen:




### <a name="option-1-web-based-configuration"></a>Option 1: Web-basierten Konfiguration
**Voraussetzung:** Ihr Gerät bereits mit Ihrem lokalen Netzwerk über Ethernet verbunden sein müssen und soll haben einen USB-WLAN-Adapter angeschlossen

Gerät eine mit keine Benutzeroberfläche, Anzeige oder Eingabegeräte, können Sie dennoch konfigurieren über die [Windows Device Portal](../manage-your-device/DevicePortal.md).
In **Windows 10 IoT Core Dashboard**, *klicken Sie auf* auf die **im Device Portal geöffnet** Symbol für Ihr Gerät.

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. Geben Sie **Administrator** für den Benutzernamen, und geben Sie Ihr Kennwort (p@ssw0rd standardmäßig)
2. Klicken Sie auf **Netzwerk** im linken Bereich
3. Klicken Sie unter **verfügbaren Netzwerke**auf Netzwerk, Sie möchten eine Verbindung herstellen, und geben Sie Anmeldeinformationen für die Verbindung. Klicken Sie auf **Connect** zum Initiieren der Verbindung

![Web-basierten WLAN-Konfiguration](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a>Option 2: Herstellen einer Verbindung mit WLAN-Profile

**Voraussetzung:** Ihr Gerät bereits mit Ihrem lokalen Netzwerk über Ethernet verbunden sein müssen und soll haben einen USB-WLAN-Adapter angeschlossen. Außerdem benötigen Sie einen Windows-PC mit WiFi-Funktion.

WLAN-Profilen mit WiFi einrichten, wird in Windows 10 IoT Core unterstützt. Finden Sie unter [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) ausführliche Informationen und Beispiele.

1. Verbinden Sie den Windows-PC mit dem gewünschten drahtlosen Netzwerk aus, und Erstellen von WLAN-Profil-XML-Datei mit den folgenden Befehlen:

    * `netsh wlan show profiles` -> Suchen Sie den Namen des Profils, das Sie gerade hinzugefügt haben

    * `netsh wlan export profile name=<your profilename>`. Dadurch wird das Profil in eine XML-Datei exportiert.

2. Öffnen Sie eine **Datei-Explorer** Fenster und in der Adressleiste `\\<TARGET_DEVICE>\C$\` , und klicken Sie dann EINGABETASTE drücken.  In diesem speziellen Fall `<TARGET_DEVICE>` ist entweder der Name oder die IP-Adresse Ihres Windows 10 IoT Core-Geräts:

    ![SMB mit Datei-Explorer](../media/SetupWifi/smb1.png)

    Wenn Sie für einen Benutzernamen und Kennwort aufgefordert werden, verwenden Sie die folgenden Anmeldeinformationen:

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![SMB mit Datei-Explorer](../media/SetupWifi/cred1.png)

> [!NOTE]
> Es ist **dringend empfohlen,** , das Standardkennwort für das Administratorkonto zu aktualisieren.  Führen Sie die Anweisungen [hier](../connect-your-device/PowerShell.md).

3. Kopieren Sie die exportierte WLAN-Profil-XML-Datei aus dem Windows-PC auf Ihrem Windows 10 IoT Core-Gerät

4. Verbindung zu Ihrem Gerät [PowerShell](../connect-your-device/PowerShell.md) und fügen Sie das neue WLAN-Profil auf Ihrem Gerät, indem Sie die folgenden Befehle ausführen

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. Verbinden Sie das Windows 10 IoT Core-Gerät mit drahtlosen Netzwerk über NETSH erleichtert

    * `netsh wlan connect name=<profile name>`

6. Stellen Sie sicher, dass Ihr Gerät mit dem Drahtlosnetzwerk verbunden ist und dem Internet erreichen

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a>Herstellen einer Verbindung zu WPA2-PSK persönliche Netzwerke

Wenn Sie mit einem persönlichen WPA2-PSK-WLAN-Netzwerk verbinden möchten, zuerst folgen Sie den obigen Anweisungen, aber nehmen Sie folgende Änderungen in der XML-Datei. Der einzige Unterschied ist, dass es sich bei Ihrem Windows-PC XML exportiert das Kennwort verschlüsselt.

> [!WARNING] 
> Dadurch wird die Verbindung unsicher.

Profil-XML exportiert von Windows-PC:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


Änderungen, die auf Windows 10 IoT Core benötigt werden:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
