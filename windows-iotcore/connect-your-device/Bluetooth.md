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
# <a name="bluetooth-support"></a><span data-ttu-id="24b0f-104">Bluetooth-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="24b0f-104">Bluetooth Support</span></span>
<span data-ttu-id="24b0f-105">Windows 10 IoT Core unterstützt die Bluetooth-4.0.</span><span class="sxs-lookup"><span data-stu-id="24b0f-105">Windows 10 IoT Core supports Bluetooth 4.0.</span></span> <span data-ttu-id="24b0f-106">Eine Liste der unterstützten Bluetooth-Dongles befinden sich die [Hardware-Kompatibilitätsliste](../learn-about-hardware/HardwareCompatList.md).</span><span class="sxs-lookup"><span data-stu-id="24b0f-106">A list of supported Bluetooth dongles can be found in the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span></span>

## <a name="about-bluetooth"></a><span data-ttu-id="24b0f-107">Informationen über Bluetooth</span><span class="sxs-lookup"><span data-stu-id="24b0f-107">About Bluetooth</span></span>
<span data-ttu-id="24b0f-108">Es gibt zwei verschiedene Bluetooth-Technologien, die Sie auswählen können, um in Ihrer app zu implementieren:</span><span class="sxs-lookup"><span data-stu-id="24b0f-108">There are two different bluetooth technologies that you can choose to implement in your app:</span></span>

* <span data-ttu-id="24b0f-109">Klassische Bluetooth (RFCOMM) vor dem Bluetooth LE, verwendeten Geräte dieses Protokoll für die Kommunikation über Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="24b0f-109">Classic Bluetooth (RFCOMM) Before Bluetooth LE, devices commonly used this protocol to communicate using Bluetooth.</span></span> <span data-ttu-id="24b0f-110">Dieses einfache Protokoll eignet sich für die Kommunikation von Gerät zu Gerät, wenn keine Energie gespart werden muss.</span><span class="sxs-lookup"><span data-stu-id="24b0f-110">This protocol is simple and useful for device-to-device communication without the need of energy savings.</span></span> <span data-ttu-id="24b0f-111">-Verbindungen erfordern die Kopplung.</span><span class="sxs-lookup"><span data-stu-id="24b0f-111">Connectivity requires pairing.</span></span>

* <span data-ttu-id="24b0f-112">Energiesparendes Bluetooth (BLE/LE) Bluetooth Low Energy (LE) ist eine Spezifikation, die Protokolle für die Ermittlung und Kommunikation zwischen Geräten, die eine effiziente Nutzung Energiebedarf definiert.</span><span class="sxs-lookup"><span data-stu-id="24b0f-112">Bluetooth Low-Energy (BLE/LE) Bluetooth Low Energy (LE) is a specification that defines protocols for discovery and communication between devices that have an efficient energy usage requirement.</span></span> <span data-ttu-id="24b0f-113">Weitere Informationen, einschließlich Codebeispielen, gemäß der letzten Builds kann ein Gerät mit einem BLE-Gerät ohne Kopplung verbinden.</span><span class="sxs-lookup"><span data-stu-id="24b0f-113">For more information including code samples, As per recent builds, a device can connect to a BLE device without pairing.</span></span>

## <a name="supported-bluetooth-profiles"></a><span data-ttu-id="24b0f-114">Unterstützte Bluetooth-Profile</span><span class="sxs-lookup"><span data-stu-id="24b0f-114">Supported Bluetooth Profiles</span></span>
<span data-ttu-id="24b0f-115">Windows 10 IoT Core unterstützt die folgenden Bluetooth-Profile:</span><span class="sxs-lookup"><span data-stu-id="24b0f-115">Windows 10 IoT Core supports the following Bluetooth profiles:</span></span>

1.  <span data-ttu-id="24b0f-116">**Human Interface Device Profile Konzepte (HID)** eine HID-Gerät wird von einer Person und zeigt die Ausgabe für Menschen Consumpation.</span><span class="sxs-lookup"><span data-stu-id="24b0f-116">**Human Interface Device Profiles Concepts (HID)** An HID device takes input from a human and presents output for human consumpation.</span></span> <span data-ttu-id="24b0f-117">Beispiele sind die Tastatur, Maus, Gamecontroller, Barcodeleser, LED und alphanumerische Anzeige.</span><span class="sxs-lookup"><span data-stu-id="24b0f-117">Examples are keyboard, mouse, game controller, barcode reader, LED, and alphanumeric display.</span></span> <span data-ttu-id="24b0f-118">Ein Windows 10 IoT Core-Gerät kann mit einem HID-Gerät über Bluetooth verbinden.</span><span class="sxs-lookup"><span data-stu-id="24b0f-118">A Windows 10 IoT Core device can connect to an HID device over Bluetooth.</span></span> <span data-ttu-id="24b0f-119">Finden Sie allgemeine zu HID in der Windows-Kontext: [Einführung in die HID-Konzepte](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span><span class="sxs-lookup"><span data-stu-id="24b0f-119">See the general topic about HID in the Windows context: [Introduction to HID Concepts](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span></span> 

2.  <span data-ttu-id="24b0f-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM ist der zugrunde liegenden serielle Kommunikation von klassischen Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="24b0f-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM is the underlying serial communications for Classic Bluetooth.</span></span> <span data-ttu-id="24b0f-121">Mit UWP-apps werden die folgenden RFCOMM-Dienste unterstützt:</span><span class="sxs-lookup"><span data-stu-id="24b0f-121">With UWP apps, the following RFCOMM services are supported:</span></span>

* <span data-ttu-id="24b0f-122">serialPort</span><span class="sxs-lookup"><span data-stu-id="24b0f-122">serialPort</span></span>
* <span data-ttu-id="24b0f-123">obexObjectPush</span><span class="sxs-lookup"><span data-stu-id="24b0f-123">obexObjectPush</span></span>
* <span data-ttu-id="24b0f-124">obexFileTransfer</span><span class="sxs-lookup"><span data-stu-id="24b0f-124">obexFileTransfer</span></span>
* <span data-ttu-id="24b0f-125">phoneBookAccessPce</span><span class="sxs-lookup"><span data-stu-id="24b0f-125">phoneBookAccessPce</span></span>
* <span data-ttu-id="24b0f-126">phoneBookAccessPse</span><span class="sxs-lookup"><span data-stu-id="24b0f-126">phoneBookAccessPse</span></span>
* <span data-ttu-id="24b0f-127">genericFileTransfer</span><span class="sxs-lookup"><span data-stu-id="24b0f-127">genericFileTransfer</span></span>

3. <span data-ttu-id="24b0f-128">**Profil GATT-(generisches Attribut)** finden Sie unter den [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) Thema.</span><span class="sxs-lookup"><span data-stu-id="24b0f-128">**Generic Attribute Profile (GATT)** See the [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) topic.</span></span> 

> [!NOTE]
> <span data-ttu-id="24b0f-129">Sie müssen manuell die RFCOMM-Dienste in der AppManifest angeben.</span><span class="sxs-lookup"><span data-stu-id="24b0f-129">You will need to manually specify the RFCOMM services in the AppManifest.</span></span>  <span data-ttu-id="24b0f-130">Finden Sie unter den [UWP-Bluetooth-RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) Thema.</span><span class="sxs-lookup"><span data-stu-id="24b0f-130">See the [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) topic.</span></span> <span data-ttu-id="24b0f-131">Siehe auch die [UWP-Bluetooth Rfcomm-Chat-Beispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) Thema.</span><span class="sxs-lookup"><span data-stu-id="24b0f-131">Also see the [UWP-Bluetooth Rfcomm Chat Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) topic.</span></span>

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a><span data-ttu-id="24b0f-132">Verbinden von Bluetooth-Geräten mithilfe des Device portal</span><span class="sxs-lookup"><span data-stu-id="24b0f-132">Connecting Bluetooth devices using the device portal</span></span>
<span data-ttu-id="24b0f-133">Bei Verwendung einer der der [Release-Image von Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth-Geräte können mit dem mithilfe des Device Portal Windows IoT Core-Gerät gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="24b0f-133">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth devices can be paired with the Windows IoT Core device using the device portal.</span></span> <span data-ttu-id="24b0f-134">Beim Navigieren zur Registerkarte "Bluetooth" wird das Gerät nach Bluetooth-Geräte sucht und wird auch für andere Bluetooth-Geräte erkennbar sein.</span><span class="sxs-lookup"><span data-stu-id="24b0f-134">When navigating to the Bluetooth tab the device will look for Bluetooth devices and will also be discoverable to other Bluetooth devices.</span></span> <span data-ttu-id="24b0f-135">Die folgende Abbildung zeigt eine eingehende Anforderung für die Kopplung.</span><span class="sxs-lookup"><span data-stu-id="24b0f-135">The picture below shows an incoming pairing request.</span></span> 

![Bluetooth-eingehenden Kopplung](../media/Bluetooth/Portal_BT_2.png)

<span data-ttu-id="24b0f-137">Nachdem das Gerät erfolgreicher Kopplung wird wird es aufgeführt Abschnitt gekoppeltes Gerät</span><span class="sxs-lookup"><span data-stu-id="24b0f-137">After the device is successfully paired it will be listed under the paired device section</span></span> 

![Bluetooth-eingehenden Kopplung](../media/Bluetooth/Portal_BT_3.png)
