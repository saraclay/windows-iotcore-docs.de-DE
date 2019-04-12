---
title: Entwickeln einer app für Ihr Gerät
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: Erfahren Sie mehr über das Hinzufügen und Entwickeln von apps für Ihr Gerät
keywords: Windows 10 IoT Core, erste Schritte, Entwickeln von apps, apps
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513945"
---
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="25d7f-104">Entwickeln einer app für Ihr Gerät</span><span class="sxs-lookup"><span data-stu-id="25d7f-104">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="25d7f-105">Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="25d7f-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="25d7f-106">Nun, da Sie ein Gerät für die Arbeit mit ausgeführte Standard-app verfügen, sollten Sie Ihr Gerät auf die nächste Stufe zu nutzen, indem entwickeln und Bereitstellen einer app auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="25d7f-106">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="25d7f-107">Bevor näher auf Beispiele, müssen Sie zum Herunterladen [Visual Studio 2017](https://www.visualstudio.com/downloads/) für die Anwendungsentwicklung.</span><span class="sxs-lookup"><span data-stu-id="25d7f-107">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="25d7f-108">Wenn Sie planen, verwenden Sie C++ für Ihre Projekte, beim Herunterladen von Visual Studio 2017, überprüfen Sie die Felder die gleiche Weise wie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="25d7f-108">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![Grundlegende Informationen für die C++ und Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="25d7f-110">Wenn Sie im Hintergrund, Arduino verknüpfen oder konsolenanwendungen in Zukunft entwickeln möchten, sollten Sie auch Projektvorlagen aus Herunterladen der [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span><span class="sxs-lookup"><span data-stu-id="25d7f-110">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="25d7f-111">Es wird empfohlen, um mit einer app betriebsbereit zu machen, eine vorgeschlagene Starter-Beispiel unten ab.</span><span class="sxs-lookup"><span data-stu-id="25d7f-111">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="25d7f-112">Aber wenn Sie zum Bereitstellen Ihrer eigenen app bereit sind, haben wir auch nützliche Links im Abschnitt nach bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="25d7f-112">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="25d7f-113">Vorgeschlagene Starter-Beispielen</span><span class="sxs-lookup"><span data-stu-id="25d7f-113">Suggested starter samples</span></span>

* [<span data-ttu-id="25d7f-114">Hello Blinky</span><span class="sxs-lookup"><span data-stu-id="25d7f-114">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="25d7f-115">Hello World</span><span class="sxs-lookup"><span data-stu-id="25d7f-115">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="25d7f-116">IoT-Start-App-Beispiel</span><span class="sxs-lookup"><span data-stu-id="25d7f-116">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="25d7f-117">RPi Cognitive Service-Beispiel</span><span class="sxs-lookup"><span data-stu-id="25d7f-117">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="25d7f-118">Nach dem Bereitstellen Ihrer app - Herzlichen Glückwunsch, haben Sie diese Quickstarter wurde abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="25d7f-118">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="25d7f-119">Weiter experimentieren oder, wenn man ein paar Ideen rund um die im Kopf, springenden sehen Sie sich unsere Dokumentation zu commercializing mit Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="25d7f-119">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="25d7f-120">Entwicklungsressourcen für Apps</span><span class="sxs-lookup"><span data-stu-id="25d7f-120">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="25d7f-121">Thema</span><span class="sxs-lookup"><span data-stu-id="25d7f-121">Topic</span></span></th>
<th align="left"><span data-ttu-id="25d7f-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="25d7f-122">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)"><span data-ttu-id="25d7f-123">Entwickeln von vordergrundanwendungen</span><span class="sxs-lookup"><span data-stu-id="25d7f-123">Developing foreground applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="25d7f-124">Informationen Sie zu den verschiedenen Sprachen, die auf Windows 10 IoT Core als auch für die UWP unterstützt werden und nicht-UWP-app-Typen, die unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="25d7f-124">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)"><span data-ttu-id="25d7f-125">Entwickeln von hintergrundanwendungen</span><span class="sxs-lookup"><span data-stu-id="25d7f-125">Developing background applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="25d7f-126">Informationen Sie zu den verschiedenen Sprachen, die auf Windows 10 IoT Core als auch für die UWP unterstützt werden und nicht-UWP-app-Typen, die unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="25d7f-126">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)"><span data-ttu-id="25d7f-127">Bereitstellen einer App mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="25d7f-127">Deploy an App with Visual Studio</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="25d7f-128">Erfahren Sie, wie Ihre anderen apps mit Visual Studio auf Ihrem Windows 10 IoT Core-Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="25d7f-128">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)"><span data-ttu-id="25d7f-129">Debuggen einer app mithilfe von Remote Console App Debuggen</span><span class="sxs-lookup"><span data-stu-id="25d7f-129">Debug your app using Remote Console App Debugging</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="25d7f-130">Erfahren Sie, wie Sie Ihre apps mit Remote Console App Debuggen in Visual Studio zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="25d7f-130">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)"><span data-ttu-id="25d7f-131">Installieren der app auf Ihrem Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="25d7f-131">Install your app on your Windows 10 IoT Core device</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="25d7f-132">Erfahren Sie, wie Sie Ihre app auf Ihrem Windows 10 IoT Core-Gerät zu installieren.</span><span class="sxs-lookup"><span data-stu-id="25d7f-132">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
