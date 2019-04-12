---
title: Mithilfe von DISM in Windows 10 IoT Core flash
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie DISM verwenden, um Windows 10 IoT Core auf eine Micro SD-Karte zu aktualisieren.
keywords: Windows Iot – DISM, Wartung Imageverwaltung, SD-Karte, Flash, Betriebssystem
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514109"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a><span data-ttu-id="eaf99-104">Mithilfe von DISM in Windows 10 IoT Core flash</span><span class="sxs-lookup"><span data-stu-id="eaf99-104">Use DISM to flash Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="eaf99-105">Offlinewartung DISM wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eaf99-105">DISM offline servicing isn't supported.</span></span> <span data-ttu-id="eaf99-106">Sie erhalten die folgende Fehlermeldung angezeigt, wenn Sie versuchen, eine FFU IoT Core bereitstellen: Die Anforderung wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eaf99-106">You will receive the error below if you try to mount an FFU for IoT Core: The request is not supported.</span></span>
> <span data-ttu-id="eaf99-107">Das Image verfügt nicht über einen Namen, und es ist wahrscheinlich eine Mobile/Onecore-FFU, dies wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eaf99-107">The image doesn't have a name and it's likely to be a Mobile/Onecore FFU, which is currently not supported.</span></span>
> <span data-ttu-id="eaf99-108">Fehler 0 x 80070032 FfuMountImage #160.</span><span class="sxs-lookup"><span data-stu-id="eaf99-108">FfuMountImage#160 failed with 0x80070032.</span></span>

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a><span data-ttu-id="eaf99-109">Eine alternative Methode zum IoT-Dashboard zum Blinken eine FFU</span><span class="sxs-lookup"><span data-stu-id="eaf99-109">An alternative method to IoT Dashboard for Flashing a FFU</span></span>

<span data-ttu-id="eaf99-110">Sie können Deployment Image Servicing and Management(Dism.exe) verwenden, um Windows 10 IoT Core auf die SD-Karte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="eaf99-110">You can use Deployment Image Servicing and Management(Dism.exe) to flash Windows 10 IoT Core on your SD card.</span></span> <span data-ttu-id="eaf99-111">Sie benötigen eine FFU-Bilddatei, die den Typ Ihres Geräts entspricht.</span><span class="sxs-lookup"><span data-stu-id="eaf99-111">You will need a FFU image file corresponding to your device type.</span></span> 

* <span data-ttu-id="eaf99-112">Öffnen Sie eine administratoreingabeaufforderung, und navigieren Sie zu dem Ordner, die mit Ihrer lokalen flash.ffu-Datei.</span><span class="sxs-lookup"><span data-stu-id="eaf99-112">Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.</span></span>

* <span data-ttu-id="eaf99-113">-Plug-in Ihrer SD-Karte auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="eaf99-113">Plug-in your SD card to your machine.</span></span> 

* <span data-ttu-id="eaf99-114">Suchen Sie die Anzahl der Datenträger, die die SD-Karte auf Ihrem Computer ist.</span><span class="sxs-lookup"><span data-stu-id="eaf99-114">Find the disk number that your SD card is on your computer.</span></span>  <span data-ttu-id="eaf99-115">Dies wird verwendet, wenn das Abbild, im nächsten Schritt angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="eaf99-115">This will be used when the image is applied in the next step.</span></span>  <span data-ttu-id="eaf99-116">Zu diesem Zweck können Sie den Diskpart-Hilfsprogramm verwenden.</span><span class="sxs-lookup"><span data-stu-id="eaf99-116">To do this, you can use the diskpart utility.</span></span>  <span data-ttu-id="eaf99-117">Führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="eaf99-117">Run the following commands:</span></span>

        c:\FFUFolder>diskpart

        DISKPART>list disk

    <span data-ttu-id="eaf99-118">Es sollten alle Speichergeräte, die an den Computer angeschlossen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="eaf99-118">It should list all the storage devices attached to the computer.</span></span> 

    ![Datenträger der DISM-Liste](../media/Dism/DiskpartListDisk.png)

    <span data-ttu-id="eaf99-120">Beachten Sie die Anzahl der Datenträger, und geben Sie beenden, Beenden von Diskpart.</span><span class="sxs-lookup"><span data-stu-id="eaf99-120">Note the disk number and type exit to exit diskpart.</span></span> 

        DISKPART>exit

* <span data-ttu-id="eaf99-121">Die Eingabeaufforderung mit Administratorberechtigungen aus, wenden Sie das Abbild auf die SD-Karte, indem Sie den folgenden Befehl ausführen (PhysicalDriveN mit dem Wert ersetzen Sie Sie finden Sie im vorherigen Schritt, zum Beispiel, in diesem Fall ist die SD-Karte Datenträgernummer 4, daher verwenden wir `/ApplyDrive:\\.\PhysicalDrive4` Siehe unten)</span><span class="sxs-lookup"><span data-stu-id="eaf99-121">Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use  `/ApplyDrive:\\.\PhysicalDrive4` below)</span></span>

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* <span data-ttu-id="eaf99-122">Klicken Sie auf das Symbol "Hardware sicher entfernen" in Ihrer Taskleiste, und wählen Sie den USB-SD-Kartenleser sicher aus dem System entfernen.</span><span class="sxs-lookup"><span data-stu-id="eaf99-122">Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system.</span></span>  <span data-ttu-id="eaf99-123">Dies unterlassen, kann eine Beschädigung des Images führen.</span><span class="sxs-lookup"><span data-stu-id="eaf99-123">Failing to do this can cause corruption of the image.</span></span>
