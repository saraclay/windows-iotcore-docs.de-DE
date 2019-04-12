---
title: Ereignisablaufverfolgung für Windows IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Ereignisse schreiben und Verarbeiten von Ereignissen für die Windows IoT Core mit Event Tracing.
keywords: Windows Iot, Ereignis-Ablaufverfolgung, ETW-ereignisablaufverfolgung für Windows Geräte
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514053"
---
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="a77e1-104">Ereignisablaufverfolgung für Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="a77e1-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="a77e1-105">Event Tracing for Windows (ETW) bietet Entwicklern die Möglichkeit zum Starten und Beenden von ereignisablaufverfolgungs-Sitzungen, Instrumentieren einer Anwendung Ablaufverfolgungsereignisse bereitstellen und Nutzen von Ablaufverfolgungsereignissen.</span><span class="sxs-lookup"><span data-stu-id="a77e1-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="a77e1-106">ETW auf Geräten mit Windows IoT Core unterstützt sowohl die Manifest-basiertes als auch die klassischen Ereignisse und funktioniert genauso wie andere Windows 10-Geräte.</span><span class="sxs-lookup"><span data-stu-id="a77e1-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="a77e1-107">In diesem Abschnitt bieten hilfreiche Links zu den Grundlagen des Schreibens und Nutzen von Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="a77e1-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="a77e1-108">Finden Sie weitere ausführliche Informationen über die [Seite Windows-Ereignisablaufverfolgung](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a77e1-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="a77e1-109">Schreiben von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="a77e1-109">Writing Events</span></span>

<span data-ttu-id="a77e1-110">Suchen eine UWP Beispieldaten, die implementiert, die verschiedenen Methoden zum Schreiben von Ereignissen im Rahmen der [Windows Universal-Samples-Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span><span class="sxs-lookup"><span data-stu-id="a77e1-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="a77e1-111">Dies wird auf Geräten mit Windows IoT Core ausgeführt und ist auch ein Verweis von großartigem Code.</span><span class="sxs-lookup"><span data-stu-id="a77e1-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="a77e1-112">Ausführliche Anleitung zum Schreiben von Ereignissen und das Abrufen der GUIDs finden Sie [hier](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a77e1-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="a77e1-113">Nutzen von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="a77e1-113">Consuming Events</span></span>

<span data-ttu-id="a77e1-114">Ereignisse werden entweder in einer ETL-Datei gespeichert oder in Echtzeit erfasst.</span><span class="sxs-lookup"><span data-stu-id="a77e1-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="a77e1-115">Verwendung [FTP](../connect-your-device/FTP.md) oder [Windows-Dateifreigabe](../manage-your-device/WindowsFileSharing.md) , ETL-Dateien von Windows IoT Core-Geräten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a77e1-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="a77e1-116">Verwenden der Tools im Windows Assessment and Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="a77e1-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="a77e1-117">Windows Assessment and Deployment Kit enthält 3 Tools zum Erfassen und Analysieren von Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="a77e1-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="a77e1-118">Zum Herunterladen hier klicken</span><span class="sxs-lookup"><span data-stu-id="a77e1-118">Click here to download</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="a77e1-119">**Windows Performance Analyzer** visualisiert die ETL-Dateien auf dem Desktop mit einer Schritt-für-Schritt-Anleitung [hier](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a77e1-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="a77e1-120">**Xperf-Befehlszeilentool** Ereignisse in Echtzeit erfasst und schreibt sie in einer ETL-Datei.</span><span class="sxs-lookup"><span data-stu-id="a77e1-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="a77e1-121">Dieses Tool ist bereits auf Windows IoT Core-Geräte, führen Sie einfach die folgenden Befehle auf den Geräten installiert werden:</span><span class="sxs-lookup"><span data-stu-id="a77e1-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="a77e1-122">**Befehlszeilenprogramm Tracerpt** ETL-Dateien in XML-Dateien konvertiert.</span><span class="sxs-lookup"><span data-stu-id="a77e1-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="a77e1-123">Gerät mithilfe des Portals</span><span class="sxs-lookup"><span data-stu-id="a77e1-123">Use Device Portal</span></span>

<span data-ttu-id="a77e1-124">Device-Portal kann Erfassen von Ereignissen in Echtzeit mit Anweisungen [hier](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span><span class="sxs-lookup"><span data-stu-id="a77e1-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="a77e1-125">Diese Methode führt nicht zu einer ETL-Datei zur weiteren Analyse, erfordert jedoch nur ein kleines Setup.</span><span class="sxs-lookup"><span data-stu-id="a77e1-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="a77e1-126">Verwenden Sie die Funktionsaufrufe</span><span class="sxs-lookup"><span data-stu-id="a77e1-126">Use Function Calls</span></span>

<span data-ttu-id="a77e1-127">Aktivieren einer Anwendung zur Verarbeitung von Ereignissen aus einer ETL-Datei oder in Echtzeit mithilfe von Funktionsaufrufen.</span><span class="sxs-lookup"><span data-stu-id="a77e1-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="a77e1-128">Erfahren Sie, wie Sie diese Funktionen verwenden [hier](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a77e1-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
