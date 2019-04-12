---
title: 3D Netzwerkdrucker mit Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: Erfahren Sie, wie Ihr Windows 10 IoT Core-Gerät zu einem Druckerserver und Ihre 3D-Druckern herstellen.
keywords: Windows Iot, 3D, 3D-Druckern, Druckserver, 3D Netzwerkdrucker
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512377"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>3D Netzwerkdrucker mit Windows 10 IoT Core

Verwandeln Sie Ihr Windows 10 IoT Core-Gerät in einem Druckserver und Herstellen Sie Ihre 3D-Druckern. Sie werden auf den Drucker Drahtlos auf anderen Geräten zugreifen können.

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1. Installieren von Windows 10 IoT Core auf Ihrem Gerät
___
Bevor Sie beginnen, benötigen Sie Folgendes:

* Ein Board mit der neuesten Version von Windows 10 IoT Core Insider Preview installiert werden soll. Führen Sie die [erste Schritte-Handbuch](https://developer.microsoft.com/en-us/windows/iot/getstarted) zum Abrufen der IoT-Dashboard-app, und installieren Windows 10 IoT Core.
* Eine 3D-Druckern mit unserem Netzwerk 3D Drucker app kompatibel:

    * Lulzbot Taz 6
    * Makergear M2
    * Printrbot Wiedergabe, Plus und einfach
    * Prusa i3 Mk2
    * Ultimaker Original und ursprüngliche +
    * Ultimaker 2 und 2 +
    * Ultimaker 2 erweiterte und erweiterte +
    * CraftBot 2
    * CraftBot PLUS
    * LulzBot Mini
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2. Herstellen einer Verbindung Ihres Geräts mit Ihrem 3D-Druckern
___
* -Plug-in Ihre 3D-Druckern auf Ihrem Windows 10 IoT Core-board verwenden das USB-Kabel.

    ![Herstellen einer Verbindung des Geräts mit Ihrem 3D-Druckern](../media/3DPrintServer/connect-3d-printer.png)

* Öffnen Sie die IoT-Dashboard-app, und stellen Sie sicher, dass Ihr Gerät in angezeigt wird, wird die **meine Geräte** Registerkarte.

    ![Stellen Sie sicher, dass Ihr Gerät in IoT-Dashboard wird angezeigt](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3. Bereitstellen des Netzwerks 3D-Druckern-app
___
* IoT-Dashboard, klicken Sie auf die **einige Beispiele ausprobieren,** Abschnitt.
* Wählen Sie die Netzwerk 3D Drucker-Beispiel-app.

   ![Installieren Sie 3D Netzwerkdrucker](../media/3dprintserver/dashboard-samples.png)

* Wählen Sie Ihre 3D Druckermodell und drücken Sie die **bereitstellen und ausführen** Schaltfläche, um die app auf Ihrem Gerät IoT Core bereitstellen. 

    ![Installieren Sie 3D Netzwerkdrucker](../media/3dprintserver/dashboard-app.png)

    [LulzBot TAZ 6-Image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) von [Aleph Objekte, Inc.](https://www.alephobjects.com/) unterliegt [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/).
    
    Wenn Sie eine benutzerdefinierte Drucker wählen die "Option" Benutzerdefiniert"" aus der Liste der Drucker installieren möchten. Benutzerdefinierte 3d Drucker benötigen eine XML-Konfigurationsdatei wird aufgerufen, die PrintDeviceCapabilities.xml-Datei bereitgestellt werden, ordnungsgemäß eine Verbindung herstellen und auf dem 3D-Objekt Drucker zu drucken. Eine Beispieldatei für die PrintDeviceCapabilities.xml finden Sie hier https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   Minimale vorgenommenen Änderungen Sie in der XML-Datei müssen sind, in den folgenden Abschnitten durch die richtigen Werte, die spezifisch für Ihre-kompatiblen Drucker zu aktualisieren.

Diese Werte geben die Drucken Bett Dimensionen des Druckers 3d zum Slicer aus, bei der Verarbeitung von 3D-Modell

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


Der Wert in der XML-Tag Psk3dx:baudrate steuert die bestimmten Baudrate während der Kommunikation mit dem 3D-Druckern aus der Raspberry pi3 verwenden. Legen Sie die entsprechenden Baudrate bestimmte, auf Ihre 3D-Druckern. 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

Die anderen Werte in der Xml PrintDeviceCapabilities werden zum Benachrichtigen des slicers in den 3d Druckertreiber optimieren die Funktionsweise mit Ihren Drucker kompatibel.
Weitere Informationen zu allen diese Werte dienen [hier](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).

    
    
## <a name="4-add-your-3d-printer"></a>4. Ihre 3D Drucker hinzufügen
___
* Wechseln Sie zu Ihrem Windows 10-PC, und wechseln Sie zu **Einstellungen** -> **Geräte** -> **Drucker und Scanner**.
* Drücken Sie **hinzufügen, Drucker oder Scanner**.

     ![Windows-Einstellungen hinzufügen Gerät](../media/3dprintserver/add-printer.png)

* Wählen Sie Ihre 3D Drucker, und drücken Sie **Add Device**. Der Drucker wird automatisch installiert.

     ![Windows-Einstellungen hinzufügen Gerät](../media/3dprintserver/add-device.png)

Herzlichen Glückwunsch, die Ihr Drucker jetzt installiert ist und verhält sich genau so, als wäre es mit einem USB-Kabel verbunden.
Sie können nun mit Drucken [3D-Generator](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).
