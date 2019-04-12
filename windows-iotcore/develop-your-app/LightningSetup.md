---
title: Lightning-Installationshandbuch
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie den Standard-Controller-Treiber an den Treiber Lightning DMAP auf einem Gerät zu ändern.
keywords: Windows Iot "," Lightning "," Setup "," Lightning-Setup, Windows Device Portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513201"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="da11c-104">Lightning-Installationshandbuch</span><span class="sxs-lookup"><span data-stu-id="da11c-104">Lightning Setup Guide</span></span>

<span data-ttu-id="da11c-105">Dieses Handbuch führt Sie durch die erforderlichen Schritte zum Ändern des Standard-Controller-Treibers an den Treiber Lightning direct Memory Access-zugeordnet (DMAP), auf einem Windows IoT Core-Gerät.</span><span class="sxs-lookup"><span data-stu-id="da11c-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="da11c-106">Dies ermöglicht die Verwendung von Lightning-fähigen Anwendungen auf diesem Gerät.</span><span class="sxs-lookup"><span data-stu-id="da11c-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="da11c-107">Ändern Sie den Standard-Controller-Treiber</span><span class="sxs-lookup"><span data-stu-id="da11c-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="da11c-108">Wir möchten die Windows Device Portal zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="da11c-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="da11c-109">Suchen Sie die IP-Adresse Ihres Geräts, indem Sie entweder mithilfe der Windows 10 IoT Core Dashboard-Anwendung oder das Board zu einem Monitor einbinden.</span><span class="sxs-lookup"><span data-stu-id="da11c-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="da11c-110">Öffnen Sie auf dem lokalen Computer der Webseite für Windows-Geräte-Portal durch Eingabe von dieser Adresse http://{BoardIPAddress}:8080/ in Ihrem Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="da11c-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   ![Windows-Geräte-Portal](../media/LightningSetup/dmap1.png)

3. <span data-ttu-id="da11c-112">Die Windows-Geräte-Portalseite Fragen Sie Ihre Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="da11c-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="da11c-113">Der Standardbenutzername lautet `Administrator` und das Kennwort `p@ssw0rd` Beachten Sie, dass nach der Eingabe von Benutzername und Kennwort, das Portal fragt Sie, ob Sie das Kennwort ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="da11c-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="da11c-114">Es ist immer empfiehlt sich, ihn zu ändern.</span><span class="sxs-lookup"><span data-stu-id="da11c-114">It's always a good practice to change it.</span></span>
   ![Portal Anmeldeinformationen für die Windows-Geräte](../media/LightningSetup/dmap2.png)

4. <span data-ttu-id="da11c-116">Klicken Sie im Navigationsmenü öffnen Sie die Seite "Geräte" auf Geräten ![Seite "Geräte"](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="da11c-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="da11c-117">Die Seite "Geräte" listet die verfügbaren Controller-Treiber.</span><span class="sxs-lookup"><span data-stu-id="da11c-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="da11c-118">Standardmäßig wird der Treiber für Posteingang in das aktuelle festgelegt.</span><span class="sxs-lookup"><span data-stu-id="da11c-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="da11c-119">Wechseln Sie zu der Lightning-Treiber, durch den direkten Speicher zugeordnet Treiber aus dem Dropdownmenü auswählen, und klicken Sie auf die Schaltfläche "Treiber aktualisieren"</span><span class="sxs-lookup"><span data-stu-id="da11c-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   ![Wählen Sie zugeordneter Direct-Memory-Treiber](../media/LightningSetup/dmap4.png)

7. <span data-ttu-id="da11c-121">Warten Sie, bis die Seite können Sie wissen, wann die Installation des Treibers abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="da11c-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   ![Treiberinstallation abgeschlossen](../media/LightningSetup/dmap5.png)

8. <span data-ttu-id="da11c-123">Wenn ein Neustart erforderlich ist, wird die Seite Sie auch zu informieren.</span><span class="sxs-lookup"><span data-stu-id="da11c-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="da11c-124">Sie können neu starten, mit der Schaltfläche "Neustart" am oberen Rand der Seite.</span><span class="sxs-lookup"><span data-stu-id="da11c-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="da11c-125">Nun können Sie zum Erstellen und verwenden verwenden Anwendungen sorgen dafür, des Treibers Lightning direkte Arbeitsspeicher zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="da11c-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
