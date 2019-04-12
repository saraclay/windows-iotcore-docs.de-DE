---
title: USB-Peripheriegeräte Treiber installieren
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie ein Treiberpaket erstellen, und Installieren von Drittanbieter-Treiber auf Ihren Geräten.
keywords: Windows Iot, USB-Treiber, Peripheriegeräten, USB
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513585"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="b8d0f-104">USB-Peripheriegeräte Treiber installieren</span><span class="sxs-lookup"><span data-stu-id="b8d0f-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="b8d0f-105">Führen Sie die folgenden Schritte zum Hinzufügen von Drittanbieter-Treiber (Usb) für Peripheriegeräte, z. B. USB-Mobile breitbandverbindungen Modems, Drucker, Scanner usw. aus.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-105">Follow the steps below to add third-party drivers (usb) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span> 

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="b8d0f-106">Schritt 1: Abrufen von Treibern auf PC</span><span class="sxs-lookup"><span data-stu-id="b8d0f-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="b8d0f-107">Der Schritt zum Abrufen der X86 ist Version der Treiber von PC.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="b8d0f-108">Wenden Sie für ARM sich an den Lieferanten des Peripheriegerät rufen Sie die Sys/INF-Dateien.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="b8d0f-109">Verbinden des Geräts mit der Windows-PCs</span><span class="sxs-lookup"><span data-stu-id="b8d0f-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="b8d0f-110">Installieren Sie den Treiber für das Gerät, auf dem PC</span><span class="sxs-lookup"><span data-stu-id="b8d0f-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="b8d0f-111">Wechseln Sie zum Geräte-Manager, wählen Sie dieses Gerät aus (siehe unter USB-Controller) und klicken Sie mit der rechten Maustaste auf ein, und wählen Sie Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="b8d0f-112">Wechseln Sie zur Registerkarte "Treiber" im Eigenschaftenfenster angezeigt, und klicken Sie auf Details zu den Treibern.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="b8d0f-113">Beachten Sie die Sys-Dateien aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="b8d0f-114">Kopieren Sie die Sys-Dateien aus `C:\Windows\system32` und auch die zugehörigen inf-Datei aus `C:\Windows\Inf`.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="b8d0f-115">Sie finden die inf-Datei von führen für das Sys Dateiverweis in der `.inf` Dateien.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-115">You can find the inf file by searcing for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="b8d0f-116">Müssen Sie möglicherweise zusätzliche Dateien, die in der INF-Datei aufgelisteten kopieren und diese werden in der inf_filelist.txt-Datei erstellt, wenn aufgelistet `inf2pkg.cmd` im nächsten Schritt.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="b8d0f-117">Schritt 2: Erstellen eines Treiberpakets</span><span class="sxs-lookup"><span data-stu-id="b8d0f-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="b8d0f-118">Das Treiberpaket enthält die Verweise (InfSource) auf die Inf-Datei für den Treiber und auch eine Liste aller Dateien in der Inf-Datei verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="b8d0f-119">Sie können den Treiber erstellen. mithilfe von wm.xml [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span><span class="sxs-lookup"><span data-stu-id="b8d0f-119">You can author the driver .wm.xml using [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="b8d0f-120">[Neue IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) die Paket-XML-Datei erstellt und auch direkt baut die Cab-Datei.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="b8d0f-121">Windows IoT Core unterstützt nur [Universal INF "und" Universal Treiber](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span><span class="sxs-lookup"><span data-stu-id="b8d0f-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="b8d0f-122">Siehe auch: [Beispiel-Treiberpaket](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="b8d0f-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span> 

## <a name="step-3-install-on-device"></a><span data-ttu-id="b8d0f-123">Schritt 3: Installieren Sie auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="b8d0f-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="b8d0f-124">Verbinden mit dem Gerät ([mithilfe von SSH](../connect-your-device/ssh.md) oder [mithilfe von Powershell](../connect-your-device/powershell.md))</span><span class="sxs-lookup"><span data-stu-id="b8d0f-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using Powershell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="b8d0f-125">Kopieren der <filename>CAB-Datei an das Gerät in einem Verzeichnis sagen C:\OemInstall</span><span class="sxs-lookup"><span data-stu-id="b8d0f-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="b8d0f-126">Initiieren Sie das Paket mit Staging `applyupdate -stage C:\OemInstall\<filename>.cab`.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="b8d0f-127">Beachten Sie, dass dieser Schritt wiederholt werden für jedes Paket, wenn Sie mehrere Pakete installiert haben.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="b8d0f-128">Die Pakete mithilfe von Commit `applyupdate -commit`.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="b8d0f-129">Das Gerät wird neu gestartet, in dem Aktualisieren der Betriebssystemversion (mit Gears) zum Installieren der Pakete und wird neu zu Hauptbetriebssystems erneut gestartet.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="b8d0f-130">Dieser Vorgang kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="b8d0f-131">Schritt 4: Überprüfen des Status des Treibers</span><span class="sxs-lookup"><span data-stu-id="b8d0f-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="b8d0f-132">Starten Sie den [Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="b8d0f-132">Launch the [Powershell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="b8d0f-133">Sie können den Status der installierten Treiber über die folgenden Powershell-Cmdlets abrufen.</span><span class="sxs-lookup"><span data-stu-id="b8d0f-133">You can get the status of the installed drivers using the following Powershell commandlets</span></span>

    * [<span data-ttu-id="b8d0f-134">Get-PnpDevice</span><span class="sxs-lookup"><span data-stu-id="b8d0f-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [<span data-ttu-id="b8d0f-135">Get-PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="b8d0f-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
