---
title: Windows 10 IoT Core API Porting Tool
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie die Windows 10 IoT Core API Porting Tool zu verwenden, um das Portieren Kosten schätzen.
keywords: Windows Iot, API porting Tool, API-portieren, Binärdateien
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513009"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="f2c2d-104">Windows 10 IoT Core API Porting Tool</span><span class="sxs-lookup"><span data-stu-id="f2c2d-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="f2c2d-105">Windows 10 IoT Core unterstützt nur eine Teilmenge der Win32- und .net API-Oberfläche zur Verfügung, auf verschiedene frühere Versionen von Windows.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-105">Windows 10 IoT Core only supports a subset of the Win32 and .Net API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="f2c2d-106">Dieses Tool scannt die Binärdateien und erhalten Sie einen Bericht über die APIs diese Binärdateien verwenden, die nicht zur Verfügung, und geben Sie die Vorschläge für mögliche Ersetzungen.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="f2c2d-107">Dies wird sowohl als Hilfe bei der Schätzung der Kosten für einen Port für IoT Core als auch helfen Ihnen dabei.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="f2c2d-108">Verwendung</span><span class="sxs-lookup"><span data-stu-id="f2c2d-108">Usage</span></span>

<span data-ttu-id="f2c2d-109">Die Windows 10 IoT Core API Porting Tool finden Sie in der [ms-Iot/Iot-Utilities](https://github.com/ms-iot/iot-utilities) Github-Repository.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github repository.</span></span>  <span data-ttu-id="f2c2d-110">Herunterladen der [Repository Zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) und kopieren Sie den IoTAPIPortingTool-Ordner auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="f2c2d-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 und erstellen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="f2c2d-112">Dadurch wird `IotAPIPortingTool.exe`.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="f2c2d-113">Sie können das Tool verwenden, indem Sie Ausführung `IoTAPIPortingTool.exe <Application path> [-os]`.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  `<Application path>` <span data-ttu-id="f2c2d-114">EXE-Datei der Anwendung, die für die Portierung Tool verwendet wird</span><span class="sxs-lookup"><span data-stu-id="f2c2d-114">exe of application that porting tool is used for</span></span>

*  `-os` <span data-ttu-id="f2c2d-115">muss angegeben werden, wenn Sie nicht beabsichtigen, die UWP zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-115">should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="f2c2d-116">Standardmäßig überprüft das Tool die Binärdateien für die Windows-UWP-Plattform.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE] 
> <span data-ttu-id="f2c2d-117">IoTAPIPortingTool.exe muss aus einer Visual Studio Developer-Eingabeaufforderung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="f2c2d-118">Sie müssen zu dem Ordner zu navigieren, die die IotAPIPortingTool.exe enthält.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span> 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a><span data-ttu-id="f2c2d-119">Ausgabe</span><span class="sxs-lookup"><span data-stu-id="f2c2d-119">Output</span></span>

<span data-ttu-id="f2c2d-120">Das Tool generiert eine Datei mit kommagetrennten Werten (Csv) in demselben Ordner, enthält die `IotAPIPortingTool.exe`.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-120">The tool will generate a comma separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="f2c2d-121">Die Datei heißt `IoTAPIPortingTool.csv` (oder `IoTAPIPortingToolOS.csv` - Betriebssystem angegeben ist) und eine Zusammenfassung wird in der Befehlszeile angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="f2c2d-122">Öffnen der `.csv` -Datei in Excel zum Analysieren der Ausgabe abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="f2c2d-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
