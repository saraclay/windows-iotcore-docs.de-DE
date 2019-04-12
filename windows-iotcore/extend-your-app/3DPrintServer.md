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
# <a name="network-3d-printer-with-windows-10-iot-core"></a><span data-ttu-id="7eac6-104">3D Netzwerkdrucker mit Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7eac6-104">Network 3D Printer with Windows 10 IoT Core</span></span>

<span data-ttu-id="7eac6-105">Verwandeln Sie Ihr Windows 10 IoT Core-Gerät in einem Druckserver und Herstellen Sie Ihre 3D-Druckern.</span><span class="sxs-lookup"><span data-stu-id="7eac6-105">Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.</span></span> <span data-ttu-id="7eac6-106">Sie werden auf den Drucker Drahtlos auf anderen Geräten zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="7eac6-106">You will be able to access your printer wirelessly from other devices.</span></span>

## <a name="1-install-windows-10-iot-core-on-your-device"></a><span data-ttu-id="7eac6-107">1. Installieren von Windows 10 IoT Core auf Ihrem Gerät</span><span class="sxs-lookup"><span data-stu-id="7eac6-107">1. Install Windows 10 IoT Core on your device</span></span>
___
<span data-ttu-id="7eac6-108">Bevor Sie beginnen, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7eac6-108">Before you start, you will need:</span></span>

* <span data-ttu-id="7eac6-109">Ein Board mit der neuesten Version von Windows 10 IoT Core Insider Preview installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="7eac6-109">A board with the latest version of Windows 10 IoT Core Insider Preview installed.</span></span> <span data-ttu-id="7eac6-110">Führen Sie die [erste Schritte-Handbuch](https://developer.microsoft.com/en-us/windows/iot/getstarted) zum Abrufen der IoT-Dashboard-app, und installieren Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7eac6-110">Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.</span></span>
* <span data-ttu-id="7eac6-111">Eine 3D-Druckern mit unserem Netzwerk 3D Drucker app kompatibel:</span><span class="sxs-lookup"><span data-stu-id="7eac6-111">A 3D Printer compatible with our Network 3D Printer app:</span></span>

    * <span data-ttu-id="7eac6-112">Lulzbot Taz 6</span><span class="sxs-lookup"><span data-stu-id="7eac6-112">Lulzbot Taz 6</span></span>
    * <span data-ttu-id="7eac6-113">Makergear M2</span><span class="sxs-lookup"><span data-stu-id="7eac6-113">Makergear M2</span></span>
    * <span data-ttu-id="7eac6-114">Printrbot Wiedergabe, Plus und einfach</span><span class="sxs-lookup"><span data-stu-id="7eac6-114">Printrbot Play, Plus and Simple</span></span>
    * <span data-ttu-id="7eac6-115">Prusa i3 Mk2</span><span class="sxs-lookup"><span data-stu-id="7eac6-115">Prusa i3 Mk2</span></span>
    * <span data-ttu-id="7eac6-116">Ultimaker Original und ursprüngliche +</span><span class="sxs-lookup"><span data-stu-id="7eac6-116">Ultimaker Original and Original+</span></span>
    * <span data-ttu-id="7eac6-117">Ultimaker 2 und 2 +</span><span class="sxs-lookup"><span data-stu-id="7eac6-117">Ultimaker 2 and 2+</span></span>
    * <span data-ttu-id="7eac6-118">Ultimaker 2 erweiterte und erweiterte +</span><span class="sxs-lookup"><span data-stu-id="7eac6-118">Ultimaker 2 Extended and Extended+</span></span>
    * <span data-ttu-id="7eac6-119">CraftBot 2</span><span class="sxs-lookup"><span data-stu-id="7eac6-119">CraftBot 2</span></span>
    * <span data-ttu-id="7eac6-120">CraftBot PLUS</span><span class="sxs-lookup"><span data-stu-id="7eac6-120">CraftBot PLUS</span></span>
    * <span data-ttu-id="7eac6-121">LulzBot Mini</span><span class="sxs-lookup"><span data-stu-id="7eac6-121">LulzBot Mini</span></span>
    * <span data-ttu-id="7eac6-122">Velleman K8200</span><span class="sxs-lookup"><span data-stu-id="7eac6-122">Velleman K8200</span></span>

## <a name="2-connect-your-3d-printer-to-your-device"></a><span data-ttu-id="7eac6-123">2. Herstellen einer Verbindung Ihres Geräts mit Ihrem 3D-Druckern</span><span class="sxs-lookup"><span data-stu-id="7eac6-123">2. Connect your 3D Printer to your device</span></span>
___
* <span data-ttu-id="7eac6-124">-Plug-in Ihre 3D-Druckern auf Ihrem Windows 10 IoT Core-board verwenden das USB-Kabel.</span><span class="sxs-lookup"><span data-stu-id="7eac6-124">Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.</span></span>

    ![Herstellen einer Verbindung des Geräts mit Ihrem 3D-Druckern](../media/3DPrintServer/connect-3d-printer.png)

* <span data-ttu-id="7eac6-126">Öffnen Sie die IoT-Dashboard-app, und stellen Sie sicher, dass Ihr Gerät in angezeigt wird, wird die **meine Geräte** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="7eac6-126">Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.</span></span>

    ![Stellen Sie sicher, dass Ihr Gerät in IoT-Dashboard wird angezeigt](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a><span data-ttu-id="7eac6-128">3. Bereitstellen des Netzwerks 3D-Druckern-app</span><span class="sxs-lookup"><span data-stu-id="7eac6-128">3. Deploy the Network 3D Printer app</span></span>
___
* <span data-ttu-id="7eac6-129">IoT-Dashboard, klicken Sie auf die **einige Beispiele ausprobieren,** Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="7eac6-129">In IoT Dashboard, click on the **Try some samples** section.</span></span>
* <span data-ttu-id="7eac6-130">Wählen Sie die Netzwerk 3D Drucker-Beispiel-app.</span><span class="sxs-lookup"><span data-stu-id="7eac6-130">Select the Network 3D Printer sample app.</span></span>

   ![Installieren Sie 3D Netzwerkdrucker](../media/3dprintserver/dashboard-samples.png)

* <span data-ttu-id="7eac6-132">Wählen Sie Ihre 3D Druckermodell und drücken Sie die **bereitstellen und ausführen** Schaltfläche, um die app auf Ihrem Gerät IoT Core bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7eac6-132">Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.</span></span> 

    ![Installieren Sie 3D Netzwerkdrucker](../media/3dprintserver/dashboard-app.png)

    <span data-ttu-id="7eac6-134">[LulzBot TAZ 6-Image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) von [Aleph Objekte, Inc.](https://www.alephobjects.com/) unterliegt [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="7eac6-134">[LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>
    
    <span data-ttu-id="7eac6-135">Wenn Sie eine benutzerdefinierte Drucker wählen die "Option" Benutzerdefiniert"" aus der Liste der Drucker installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="7eac6-135">If you wish to install a custom printer select the "Custom" option from the list of Printers.</span></span> <span data-ttu-id="7eac6-136">Benutzerdefinierte 3d Drucker benötigen eine XML-Konfigurationsdatei wird aufgerufen, die PrintDeviceCapabilities.xml-Datei bereitgestellt werden, ordnungsgemäß eine Verbindung herstellen und auf dem 3D-Objekt Drucker zu drucken.</span><span class="sxs-lookup"><span data-stu-id="7eac6-136">Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer.</span></span> <span data-ttu-id="7eac6-137">Eine Beispieldatei für die PrintDeviceCapabilities.xml finden Sie hier https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span><span class="sxs-lookup"><span data-stu-id="7eac6-137">A sample PrintDeviceCapabilities.xml file can be found here https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span></span>
   
   <span data-ttu-id="7eac6-138">Minimale vorgenommenen Änderungen Sie in der XML-Datei müssen sind, in den folgenden Abschnitten durch die richtigen Werte, die spezifisch für Ihre-kompatiblen Drucker zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7eac6-138">The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.</span></span>

<span data-ttu-id="7eac6-139">Diese Werte geben die Drucken Bett Dimensionen des Druckers 3d zum Slicer aus, bei der Verarbeitung von 3D-Modell</span><span class="sxs-lookup"><span data-stu-id="7eac6-139">These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model</span></span>

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


<span data-ttu-id="7eac6-140">Der Wert in der XML-Tag Psk3dx:baudrate steuert die bestimmten Baudrate während der Kommunikation mit dem 3D-Druckern aus der Raspberry pi3 verwenden.</span><span class="sxs-lookup"><span data-stu-id="7eac6-140">The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3.</span></span> <span data-ttu-id="7eac6-141">Legen Sie die entsprechenden Baudrate bestimmte, auf Ihre 3D-Druckern.</span><span class="sxs-lookup"><span data-stu-id="7eac6-141">Set the appropriate baud rate specific to your 3d printer.</span></span> 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

<span data-ttu-id="7eac6-142">Die anderen Werte in der Xml PrintDeviceCapabilities werden zum Benachrichtigen des slicers in den 3d Druckertreiber optimieren die Funktionsweise mit Ihren Drucker kompatibel.</span><span class="sxs-lookup"><span data-stu-id="7eac6-142">The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.</span></span>
<span data-ttu-id="7eac6-143">Weitere Informationen zu allen diese Werte dienen [hier](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span><span class="sxs-lookup"><span data-stu-id="7eac6-143">More information on all these values are provided [here](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span></span>

    
    
## <a name="4-add-your-3d-printer"></a><span data-ttu-id="7eac6-144">4. Ihre 3D Drucker hinzufügen</span><span class="sxs-lookup"><span data-stu-id="7eac6-144">4. Add your 3D Printer</span></span>
___
* <span data-ttu-id="7eac6-145">Wechseln Sie zu Ihrem Windows 10-PC, und wechseln Sie zu **Einstellungen** -> **Geräte** -> **Drucker und Scanner**.</span><span class="sxs-lookup"><span data-stu-id="7eac6-145">Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.</span></span>
* <span data-ttu-id="7eac6-146">Drücken Sie **hinzufügen, Drucker oder Scanner**.</span><span class="sxs-lookup"><span data-stu-id="7eac6-146">Press **Add a printer or scanner**.</span></span>

     ![Windows-Einstellungen hinzufügen Gerät](../media/3dprintserver/add-printer.png)

* <span data-ttu-id="7eac6-148">Wählen Sie Ihre 3D Drucker, und drücken Sie **Add Device**.</span><span class="sxs-lookup"><span data-stu-id="7eac6-148">Select your 3D Printer and press **Add device**.</span></span> <span data-ttu-id="7eac6-149">Der Drucker wird automatisch installiert.</span><span class="sxs-lookup"><span data-stu-id="7eac6-149">The printer will install automatically.</span></span>

     ![Windows-Einstellungen hinzufügen Gerät](../media/3dprintserver/add-device.png)

<span data-ttu-id="7eac6-151">Herzlichen Glückwunsch, die Ihr Drucker jetzt installiert ist und verhält sich genau so, als wäre es mit einem USB-Kabel verbunden.</span><span class="sxs-lookup"><span data-stu-id="7eac6-151">Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.</span></span>
<span data-ttu-id="7eac6-152">Sie können nun mit Drucken [3D-Generator](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span><span class="sxs-lookup"><span data-stu-id="7eac6-152">You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span></span>
