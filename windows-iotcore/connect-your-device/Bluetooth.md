---
title: Bluetooth-Unterstützung
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Bluetooth für Geräte unter Windows 10 IoT Core nutzen zu können.
keywords: Windows Iot, Bluetooth, Bluetooth-Unterstützung, Geräte, Device-portal
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513258"
---
# <a name="bluetooth-support"></a>Bluetooth-Unterstützung
Windows 10 IoT Core unterstützt die Bluetooth-4.0. Eine Liste der unterstützten Bluetooth-Dongles befinden sich die [Hardware-Kompatibilitätsliste](../learn-about-hardware/HardwareCompatList.md).

## <a name="about-bluetooth"></a>Informationen über Bluetooth
Es gibt zwei verschiedene Bluetooth-Technologien, die Sie auswählen können, um in Ihrer app zu implementieren:

* Klassische Bluetooth (RFCOMM) vor dem Bluetooth LE, verwendeten Geräte dieses Protokoll für die Kommunikation über Bluetooth. Dieses einfache Protokoll eignet sich für die Kommunikation von Gerät zu Gerät, wenn keine Energie gespart werden muss. -Verbindungen erfordern die Kopplung.

* Energiesparendes Bluetooth (BLE/LE) Bluetooth Low Energy (LE) ist eine Spezifikation, die Protokolle für die Ermittlung und Kommunikation zwischen Geräten, die eine effiziente Nutzung Energiebedarf definiert. Weitere Informationen, einschließlich Codebeispielen, gemäß der letzten Builds kann ein Gerät mit einem BLE-Gerät ohne Kopplung verbinden.

## <a name="supported-bluetooth-profiles"></a>Unterstützte Bluetooth-Profile
Windows 10 IoT Core unterstützt die folgenden Bluetooth-Profile:

1.  **Human Interface Device Profile Konzepte (HID)** eine HID-Gerät wird von einer Person und zeigt die Ausgabe für Menschen Consumpation. Beispiele sind die Tastatur, Maus, Gamecontroller, Barcodeleser, LED und alphanumerische Anzeige. Ein Windows 10 IoT Core-Gerät kann mit einem HID-Gerät über Bluetooth verbinden. Finden Sie allgemeine zu HID in der Windows-Kontext: [Einführung in die HID-Konzepte](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts). 

2.  **Radio Frequency Communication (RFCOMM)** RFCOMMM ist der zugrunde liegenden serielle Kommunikation von klassischen Bluetooth. Mit UWP-apps werden die folgenden RFCOMM-Dienste unterstützt:

* serialPort
* obexObjectPush
* obexFileTransfer
* phoneBookAccessPce
* phoneBookAccessPse
* genericFileTransfer

3. **Profil GATT-(generisches Attribut)** finden Sie unter den [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) Thema. 

> [!NOTE]
> Sie müssen manuell die RFCOMM-Dienste in der AppManifest angeben.  Finden Sie unter den [UWP-Bluetooth-RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) Thema. Siehe auch die [UWP-Bluetooth Rfcomm-Chat-Beispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) Thema.

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a>Verbinden von Bluetooth-Geräten mithilfe des Device portal
Bei Verwendung einer der der [Release-Image von Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth-Geräte können mit dem mithilfe des Device Portal Windows IoT Core-Gerät gekoppelt werden. Beim Navigieren zur Registerkarte "Bluetooth" wird das Gerät nach Bluetooth-Geräte sucht und wird auch für andere Bluetooth-Geräte erkennbar sein. Die folgende Abbildung zeigt eine eingehende Anforderung für die Kopplung. 

![Bluetooth-eingehenden Kopplung](../media/Bluetooth/Portal_BT_2.png)

Nachdem das Gerät erfolgreicher Kopplung wird wird es aufgeführt Abschnitt gekoppeltes Gerät 

![Bluetooth-eingehenden Kopplung](../media/Bluetooth/Portal_BT_3.png)
