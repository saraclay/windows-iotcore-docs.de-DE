---
title: Verbinden Sie Ihre app in die cloud
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Ihre app in die Cloud zu verbinden.
keywords: Windows Iot, Cloud, Azure, Azure IoT Hub
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513353"
---
# <a name="connect-your-app-to-the-cloud"></a><span data-ttu-id="aab0e-104">Verbinden Sie Ihre app in die cloud</span><span class="sxs-lookup"><span data-stu-id="aab0e-104">Connect your app to the cloud</span></span>

<span data-ttu-id="aab0e-105">Diese schrittweise Anleitung können Sie machen Sie sich mit Windows 10 IoT Core, richten Sie Ihr Gerät aus, und Erstellen Ihrer ersten Anwendung, die mit Azure IoT Hub verbindet.</span><span class="sxs-lookup"><span data-stu-id="aab0e-105">This step-by-step guide will allow you to familiarize yourself with Windows 10 IoT Core, set up your device and create your first application that connects to Azure IoT Hub.</span></span>

## <a name="step-1-prepare-your-device"></a><span data-ttu-id="aab0e-106">Schritt 1: Bereiten Sie Ihr Gerät vor.</span><span class="sxs-lookup"><span data-stu-id="aab0e-106">Step 1: Prepare your device</span></span>

<span data-ttu-id="aab0e-107">Anweisungen finden Sie Anleitungen zum Vorbereiten Ihres Geräts auf die [Seite für erste Schritte](https://developer.microsoft.com/en-us/windows/iot/getstarted) stellen Sie sicher, dass Sie [die Trusted Platform Module auf Ihrem Gerät bereitstellen](../connect-to-cloud/ConnectDeviceToCloud.md)</span><span class="sxs-lookup"><span data-stu-id="aab0e-107">You can find instructions on how to prepare your device on the [Get Started Page](https://developer.microsoft.com/en-us/windows/iot/getstarted) Make sure you [provision the TPM of your device](../connect-to-cloud/ConnectDeviceToCloud.md)</span></span>

## <a name="step-2-install-visual-studio-2017-and-tools"></a><span data-ttu-id="aab0e-108">Schritt 2: Installieren von Visual Studio 2017 und tools</span><span class="sxs-lookup"><span data-stu-id="aab0e-108">Step 2: Install Visual Studio 2017 and tools</span></span>

<span data-ttu-id="aab0e-109">Installieren Sie [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span><span class="sxs-lookup"><span data-stu-id="aab0e-109">Install [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span></span> <span data-ttu-id="aab0e-110">Sie können eine beliebige Edition von Visual Studio, einschließlich der kostenlosen communityedition installieren.</span><span class="sxs-lookup"><span data-stu-id="aab0e-110">You can install any edition of Visual Studio, including the free Community edition.</span></span>

<span data-ttu-id="aab0e-111">Achten Sie darauf, wählen Sie die **Entwicklungstools für universelle Windows-App**, die Komponente, die für das Schreiben von Windows 10-apps erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="aab0e-111">Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:</span></span>

![Entwicklungstools für universelle Windows-Apps](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a><span data-ttu-id="aab0e-113">Schritt 3: Installieren Sie die verbundenen Dienste für Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="aab0e-113">Step 3: Install the Connected Services for Azure IoT Hub</span></span>

<span data-ttu-id="aab0e-114">Die verbundene Dienste für Azure IoT Hub Visual Studio-Erweiterung können Sie eine Verbindung herstellen und Interaktion mit Azure IoT Hub in weniger als einer Minute.</span><span class="sxs-lookup"><span data-stu-id="aab0e-114">The Connected Services for Azure IoT Hub Visual Studio extension allows you to connect and start interacting with Azure IoT Hub in less than a minute.</span></span>

<span data-ttu-id="aab0e-115">Sie können die Erweiterung von installieren die [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span><span class="sxs-lookup"><span data-stu-id="aab0e-115">You can install the extension from the [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span></span>

## <a name="step-4-create-a-visual-studio-uwp-solution"></a><span data-ttu-id="aab0e-116">Schritt 4: Erstellen Sie eine Visual Studio-UWP-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="aab0e-116">Step 4: Create a Visual Studio UWP solution</span></span>

<span data-ttu-id="aab0e-117">Zum Erstellen einer UWP-Lösung in Visual Studio auf die **Datei** Menü klicken Sie auf **neu** dann **Projekt**:</span><span class="sxs-lookup"><span data-stu-id="aab0e-117">To create a UWP solution in Visual Studio, on the **File** menu, click **New** then **Project**:</span></span>

![Erstellung eines neuen Projekts](../media/ConnectAppToCloud/new_project_menu.png)

<span data-ttu-id="aab0e-119">Wählen Sie im Dialogfeld für neue Projekte, die angezeigt wird, **leere App (Universelles Windows) Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="aab0e-119">In the New Project dialog that comes up, select **Blank App (Universal Windows) Visual C#**.</span></span> <span data-ttu-id="aab0e-120">Geben Sie Ihrem Projekt einen Namen (e-Mail-Domäne(n)</span><span class="sxs-lookup"><span data-stu-id="aab0e-120">Give your project a name (e.x.</span></span> <span data-ttu-id="aab0e-121">**MyFirstIoTCoreApp**):</span><span class="sxs-lookup"><span data-stu-id="aab0e-121">**MyFirstIoTCoreApp**):</span></span>

![Dialogfeld "neue Projektmappe"](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a><span data-ttu-id="aab0e-123">Verwenden Sie das verbundene Dienste für Azure IoT Hub für die Verbindung mit Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="aab0e-123">Use the Connected Services for Azure IoT Hub to connect to Azure IoT Hub</span></span>

<span data-ttu-id="aab0e-124">Befolgen Sie die Anweisungen aus den [Tool für verbundene Dienste](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) um Ihr Projekt mit Azure IoT Hub zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="aab0e-124">Follow the instructions from the [Connected Services tool](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) to connect your project to Azure IoT Hub.</span></span> <span data-ttu-id="aab0e-125">Das Tool generiert zwei Funktionen, `SendDeviceToCloudMessageAsync` und `ReceiveCloudToDeviceMessageAsync` , die Sie an einer beliebigen Stelle in Ihrer app aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="aab0e-125">The tool will generate two functions, `SendDeviceToCloudMessageAsync` and `ReceiveCloudToDeviceMessageAsync` that you can invoke anywhere in your app.</span></span> <span data-ttu-id="aab0e-126">Sie können diese Funktionen ändern, nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="aab0e-126">You can modify these functions as you see fit.</span></span>  

