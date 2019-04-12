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
# <a name="windows-10-iot-core-dashboard"></a>Windows 10 IoT Core Dashboard

Windows 10 IoT Core Dashboard ist die beste Möglichkeit zum Herunterladen einrichten und verbinden Sie Ihre Windows 10 IoT Core-Geräte, die alle von Ihrem PC.

Sie können die [IoT Core Dashboard](http://go.microsoft.com/fwlink/?LinkID=708576).

> [!NOTE]
> Wenn Sie erkennen, dass Sie einen weißen Bildschirm optimal nutzen, wenn nach dem Herunterladen der IoT-Dashboard zu öffnen, wird es aufgrund eines Problems Treiber. Um dieses Problem zu umgehen, müssen Sie zum Herunterladen der [Zip-Format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) von der Intel-Grafiktreiber und den Treiber manuell installieren. 

## <a name="set-up-a-new-device"></a>Einrichten eines neuen Geräts

> [!NOTE]
> Dashboard kann nicht verwendet, um den Raspberry Pi 3 b + setup verwendet werden. Wenn Sie eine 3 b +-Gerät verfügen, müssen Sie verwenden die [technical Preview 3 b +](https://www.microsoft.com/en-us/software-download/windowsiot). Lesen Sie die [bekannte Einschränkungen](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) der technical Preview zu bestimmen, ob dies für die Entwicklung geeignet ist.

> [!NOTE]
> Es ist derzeit ein bekanntes Problem, in denen das Betriebssystem die Partitionen auf die SD-Karte durchläuft und werden aufgefordert, eine "Format"... Meldung für eine bestimmte Daten-Partition, die nicht mit einem beliebigen Dateisystem enthält. Bitte ignorieren Sie diese Aufforderung, indem Sie auf "Abbrechen". Während wir an einer Lösung arbeiten, es wird jedoch empfohlen, wenn Sie auf "Jetzt Format" klicken, Sie die SD-Karte mit dem Image FFU erneut als die Format-Aktion Auswirkungen auf werkseinstellungen zurücksetzen, die den Aktualisierungsprozess und das Gerät nicht aktualisieren.


Die IoT-Dashboard vereinfacht, um ein neues Gerät einzurichten. Ausführliche Anweisungen zum Einstieg finden Sie unter den [Einstieg](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) Seite.

![IoT-Dashboard-Seite "Setup"](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>SD-Karte
Typ, Marke und Modell des von der SD-Karte erheblich wirkt sich auf die Leistung und die Qualität der IoT Core.
Eine langsame Karte dauert bis zu fünf Mal länger als starten unsere [Karten empfohlen](../learn-about-hardware/hardwarecompatlist.md).
Ältere, weniger zuverlässig SD-Karten funktioniert möglicherweise nicht selbst. Wenn Sie bei der Installation Probleme auftreten weiterhin, beachten Sie, und Ersetzen Sie dabei die SD-Karte.

### <a name="device-name"></a>Gerätename
Der Standardname für das Gerät ist Minwinpc. Es wird empfohlen, mit einem eindeutigen Element zu ändern, da dies das Gerät im Netzwerk suchen vereinfacht. Der Gerätename dürfen höchstens 15 Zeichen lang sein und kann Buchstaben, Zahlen und folgenden Zeichen enthalten: @ # $ % ^ & ') (. -_ {} ~ Wenn Sie den Gerätenamen im IoT-Dashboard ändern, wenn Sie Ihr Gerät einrichten, erfolgt ein automatischer Neustart der erstmaligen, wenn Sie Power, auf dem Gerät.

### <a name="password"></a>Kennwort
Kennwort ist ein Pflichtfeld und muss festgelegt werden. Festlegen eines Kennworts in IoT-Dashboard ändert das Kennwort für Administrator-Benutzer, die in der Standardeinstellung ist "p@ssw0rd".

### <a name="wi-fi-network-connection"></a>Wi-Fi-Verbindung
IoT-Dashboard zeigt alle verfügbaren Netzwerke, denen Ihren PC mit zuvor verbunden ist. Wenn Sie das gewünschte Wi-Fi-Netzwerk in der Liste nicht angezeigt wird, stellen Sie sicher, dass Sie es auf Ihrem PC verbunden sind.
Wenn Sie das Kontrollkästchen deaktivieren, müssen Sie ein Ethernet-Kabel an das Board nach blinken verbinden.

### <a name="first-boot"></a>Ersten Start
Der erste Start dauert immer länger als alle nachfolgenden Startvorgängen. Das Betriebssystem dauert einige Zeit zum Installieren und Verbinden mit Ihrem Netzwerk.
Startzeit kann variieren erheblich entsprechend Ihrem SD-Karte. Beispielsweise hat ein Raspberry Pi 3 ausgeführt wird, auf unsere empfohlenen SD-Karte 3 und 4 Minuten für den ersten Start. Auf dem gleichen Pi durch eine schlechte Qualität SD-Karte haben wir gesehen, Boot Mal länger als 15 Minuten.

### <a name="connecting-to-the-internet"></a>Herstellen einer Verbindung mit dem internet
Ihre IoT Core-Geräts mit dem Internet verbunden ist von wesentlicher Bedeutung. Viele der neueren Boards verfügen über integrierte in Wi-Fi-Adaptern. Wenn Sie Probleme beim Herstellen einer Verbindung mit Ihrem Netzwerk haben, versuchen Sie Folgendes:

* Neustarten des Geräts
* Unter Verwendung der Ethernet-Kabel
* Ein Monitor auf dem Gerät anschließen. Hier erfahren Sie, Diagnoseinformationen zu Ihrem Gerät

> [!NOTE]
> Der offizielle Raspberry Pi 2 Wi-Fi-Adapter kann instabil werden bei der Wi-Fi-Verbindung.


## <a name="my-devices"></a>Meine Geräte
___
Nachdem Ihr Gerät mit dem Internet verbunden ist, erkennt der IoT-Dashboard automatisch Ihr Gerät.
Um Ihr Gerät zu suchen, wechseln Sie zu **meine Geräte**. Wenn Ihr Gerät nicht aufgeführt ist, versuchen Sie, einen Neustart des Geräts. Stellen Sie sicher, dass, wenn es mehrere Geräte im Netzwerk sind, jeweils einen eindeutigen Namen haben. Stellen Sie außerdem sicher, dass Ihre **windows10iotcoredashboard.exe** ist zulässig, durch die Windows-Firewall zu kommunizieren, durch die folgenden Schritte aus:

1. Open **Netzwerk- und Freigabecenter** und suchen Sie dann auf den Typ des Netzwerks (Domäne/privat/öffentlich), die mit Ihrem PC verbunden ist.
2. Open **Systemsteuerung** , und klicken Sie auf **System und Sicherheit**.
3. Klicken Sie auf **eine app durch die Windows-Firewall zulassen** unter **Windows-Firewall**.
4. Klicken Sie auf **Ändern der Einstellungen**.
5. Suchen **windows10iotcoredashboard.exe** in **zugelassene apps und Features** und aktivieren Sie dann das Kontrollkästchen für die entsprechende Netzwerk (d. h. den Netzwerktyp, die Sie in Schritt 1 gefunden).


### <a name="connect-to-your-device"></a>Herstellen einer Verbindung Ihres Geräts mit

> [!NOTE]
> Wenn Sie nicht, um Ihr Gerät auf dem Dashboard finden können, versuchen Sie es eingeben Ihrer [IP-Adresse] und [: 8080] in den Browser, um die Windows Device Portal betriebsbereit zu machen. Versuchen Sie einen Neustart Ihres Geräts aus, rufen Sie Ihr Gerät im Dashboard angezeigt.


Klicken Sie mit der rechten Maustaste auf, und wählen Sie **im Device Portal geöffnet**. Hierdurch wird die [Windows Device Portal](../manage-your-device/DevicePortal.md) Seite und ist die beste Möglichkeit zum interagieren mit und verwalten Ihr Gerät.

![Geräte IoTDashboard anzeigen](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

Sie können auch mithilfe von Windows PowerShell mit dem Gerät verbinden.

## <a name="connect-to-azure"></a>Verbinden mit Azure
___
IoT-Dashboard können Sie IoT Core-Geräte mit Azure IoT Hub bereitstellen. Weitere Informationen finden sie unter dieser [Blogbeitrag](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).

[Erfahren Sie, wie Sie mit der IoT-Dashboard mit Azure](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>Beispiele für schnelle ausführen
___

Führen Sie schnell Beispiele erfordern keine Codekompilierung, Visual Studio-Installation oder SDK herunterladen. Sie eignen sich hervorragend für schnell überprüfen, wie IoT Core verwenden können.

### <a name="network-3d-printer"></a>3D Netzwerkdrucker
Verwenden Sie das Beispiel Netzwerk 3D Drucker auf dem die Verbindung Ihrer 3D-Druckern können sie über Ihr privates Netzwerk auffindbar. 

![IoTDashboard Netzwerkdrucker 3D](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>Internet-radio
Aktivieren Sie Ihr Windows 10 IoT Core-Gerät in einem Internetradio, die von überall in Ihrem Haus gesteuert werden kann.

![IoTDashboard Internet-radio](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT Core Blockly
IoT Core Blockly Beispiel können Ihr Programm eine Raspberry Pi2 "3" und eine Raspberry Pi Sinn Hat mit einem "Block"-Editor in Ihrem Browser.

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
