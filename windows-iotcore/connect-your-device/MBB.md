---
title: Mobile Breitbandverbindung
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Erfahren Sie, wie Sie mit der mobilen Breitband-Verbindung für Windows 10 IoT Core.
keywords: Windows Iot, MBB, mobile Breitbandverbindung
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513577"
---
## <a name="mobile-broadband-connection"></a><span data-ttu-id="48e7a-104">Mobile Breitbandverbindung</span><span class="sxs-lookup"><span data-stu-id="48e7a-104">Mobile Broadband Connection</span></span>

<span data-ttu-id="48e7a-105">Mobile Breitbandverbindung wird unterstützt, auf [Windows 10 IoT Core](http://windowsondevices.com).</span><span class="sxs-lookup"><span data-stu-id="48e7a-105">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="48e7a-106">Wenn Ihre IoT-Gateway über das Modem für mobiles Breitband-Modul unterstützt, können Sie mithilfe der `MBBConnect` Tool, das setupkonfigurationen für mobile Breitbandverbindung im IoT Core hilft.</span><span class="sxs-lookup"><span data-stu-id="48e7a-106">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help setup configurations for mobile broadband connection in IoT Core.</span></span>

`MBBConnect` <span data-ttu-id="48e7a-107">Ruft die Daten zu verbinden, z. B. Abonnenten-ID, SIM Chipkarte-ID, Schnittstellenname, und home Anbietername usw. ab. Anschließend erstellen sie das Verbindungsprofil.</span><span class="sxs-lookup"><span data-stu-id="48e7a-107">retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="48e7a-108">Alles, was Sie tun müssen APN bereitstellen ist und es wird die Verbindung automatisch einrichten.</span><span class="sxs-lookup"><span data-stu-id="48e7a-108">The only thing you’ll need to do is to provide APN, and it’ll setup connection automatically.</span></span>

`MBBConnect` <span data-ttu-id="48e7a-109">entwickelt und getestet mit MinnowBoard Max-basiertes führt IoT Core Version 16299 und dem mobilen Breitband-Modem-Modul mit der SIM-Karte von wichtigen Telekommunikationsanbieters in Taiwan IoT-Gateway.</span><span class="sxs-lookup"><span data-stu-id="48e7a-109">is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="48e7a-110">Verwendung</span><span class="sxs-lookup"><span data-stu-id="48e7a-110">Usage</span></span>

1. <span data-ttu-id="48e7a-111">Kopie `MBBConnect.exe` IoT-Gateway.</span><span class="sxs-lookup"><span data-stu-id="48e7a-111">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="48e7a-112">FTP</span><span class="sxs-lookup"><span data-stu-id="48e7a-112">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="48e7a-113">Verbinden Sie über Powershell oder die SSH-Gateways.</span><span class="sxs-lookup"><span data-stu-id="48e7a-113">Connect gateway by Powershell or SSH.</span></span>

   * [<span data-ttu-id="48e7a-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="48e7a-114">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="48e7a-115">SSH</span><span class="sxs-lookup"><span data-stu-id="48e7a-115">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="48e7a-116">Wechseln Sie zu dem Ordner, in denen `MBBConnect.exe` befindet.</span><span class="sxs-lookup"><span data-stu-id="48e7a-116">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="48e7a-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="48e7a-117">Example</span></span>
<span data-ttu-id="48e7a-118">Im folgenden Beispiel wird die MBBConnect.exe in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48e7a-118">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="48e7a-119">Verwenden Sie z. B. ist der APN der SIM-Karte "Internet", `MBBConnect.exe Internet` eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="48e7a-119">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="48e7a-120">Die ausgehende Nachricht wird den Flow angezeigt:</span><span class="sxs-lookup"><span data-stu-id="48e7a-120">The output message will show the flow:</span></span>

* <span data-ttu-id="48e7a-121">Der Status ist nicht verbunden, verbunden geändert.</span><span class="sxs-lookup"><span data-stu-id="48e7a-121">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="48e7a-122">WWAN Netzwerk wurde erfolgreich konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="48e7a-122">WWAN network is configured successfully.</span></span>

<span data-ttu-id="48e7a-123">Testen Sie das Beispiel für Mobile Breitbandverbindung [hier](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span><span class="sxs-lookup"><span data-stu-id="48e7a-123">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
