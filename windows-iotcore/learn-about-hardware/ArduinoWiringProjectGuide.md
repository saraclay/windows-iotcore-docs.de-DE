---
title: Arduino verknüpfen Projektberater
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, bis die Erstellung, Setup und Bereitstellung eines Arduino verknüpfen mithilfe von Windows IoT Core-Projekts.
keywords: Windows Iot, Arduino, Arduino verknüpfen, Lightning Leistung zu erzielen, Visual Studio
ms.openlocfilehash: baa904d1d5f23db15fd1dacd05c749449dc91213
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512873"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="9170d-104">Arduino verknüpfen Projektberater</span><span class="sxs-lookup"><span data-stu-id="9170d-104">Arduino Wiring Project Guide</span></span>

<span data-ttu-id="9170d-105">Dieses Handbuch führt durch die Erstellung, Setup und Bereitstellung eines Arduino verknüpfen mithilfe von Windows IoT Core-Projekts.</span><span class="sxs-lookup"><span data-stu-id="9170d-105">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="9170d-106">Verknüpfen von Arduino-Projekte die vertrauten, benutzerfreundlichen Arduino verknüpfen-API nutzen mit Windows IoT Lightning DMAP Treiber: ein Treiber, die mithilfe von direkten Speicherzuordnung zu erheblichen [mindestgeschwindigkeiten für die Leistung](../develop-your-app/LightningPerformance.md).</span><span class="sxs-lookup"><span data-stu-id="9170d-106">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="9170d-107">Sie können kopieren & einfügen Arduino Skizzen und Bibliotheken in Ihre Projekte IoT Core Arduino verknüpfen und führen Sie sie in der unterstützten IoT Core-Geräte, einschließlich Raspberry Pi2, 3 "und" Minnowboard Max!</span><span class="sxs-lookup"><span data-stu-id="9170d-107">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="9170d-108">Finden Sie im Abschnitt zum Entwickeln dieser Seite finden Sie weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="9170d-108">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="9170d-109">Installieren Sie die Microsoft IoT-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="9170d-109">Install the Microsoft IoT Templates</span></span>

<span data-ttu-id="9170d-110">Wir haben Visual Studio-Erweiterung bereitgestellt, die automatisch eine Visual Studio-Vorlage für die Projekte Arduino verknüpfen sowie anderen Microsoft IoT-Projekttypen installiert wird.</span><span class="sxs-lookup"><span data-stu-id="9170d-110">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="9170d-111">Wechseln Sie zu [Windows IoT Core-Projektvorlagen-Erweiterungsseite](https://go.microsoft.com/fwlink/?linkid=847472) auf die Erweiterung von Visual Studio Gallery herunterladen!</span><span class="sxs-lookup"><span data-stu-id="9170d-111">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="9170d-112">Die Erweiterung installieren und starten Sie Visual Studio neu, wenn er wurde bereits geöffnet</span><span class="sxs-lookup"><span data-stu-id="9170d-112">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="9170d-113">Ändern Sie den Standard-Controller-Treiber</span><span class="sxs-lookup"><span data-stu-id="9170d-113">Change the Default Controller Driver</span></span>

<span data-ttu-id="9170d-114">Sie müssen den direkten Speicher zugeordnet Treiber zum Verknüpfen der Arduino-Lösungen zu schreiben, ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9170d-114">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="9170d-115">Finden Sie in der [Lightning-Installationshandbuch](../develop-your-app/LightningSetup.md) Anweisungen!</span><span class="sxs-lookup"><span data-stu-id="9170d-115">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="9170d-116">Entwicklung</span><span class="sxs-lookup"><span data-stu-id="9170d-116">Develop</span></span>
<span data-ttu-id="9170d-117">Führen Sie eines der Beispiele "Verknüpfen" auf die [Beispielseite](https://developer.microsoft.com/en-us/windows/iot/samples), oder Erstellen Ihres eigenen Projekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="9170d-117">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="9170d-118">Eines der Beispiele, die wir erstellt haben, die geschrieben werden, dass mit Arduino verknüpfen aufgeführt werden wie folgt: [Hauptverkaufsargument (Verknüpfen)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span><span class="sxs-lookup"><span data-stu-id="9170d-118">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="9170d-119">Hauptverkaufsargument, das Cononical "Hello World"-Projekt für IoT-Projekte, eignet sich hervorragend für Ihr erstes Projekt zu starten!</span><span class="sxs-lookup"><span data-stu-id="9170d-119">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="9170d-120">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="9170d-120">Create a new Project</span></span>
1. <span data-ttu-id="9170d-121">Öffnen Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9170d-121">Open Visual Studio.</span></span>

2. <span data-ttu-id="9170d-122">Wählen Sie die Datei -> Neu -> Projekt...</span><span class="sxs-lookup"><span data-stu-id="9170d-122">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="9170d-123">Das Dialogfeld, das angezeigt wird, zur Auswahl:</span><span class="sxs-lookup"><span data-stu-id="9170d-123">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="9170d-124">Visual C++ -> Windows -> Windows IoT Core-Anwendung für Windows IoT Core verknüpfen Arduino >.</span><span class="sxs-lookup"><span data-stu-id="9170d-124">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="9170d-125">(stattdessen scheinen als)</span><span class="sxs-lookup"><span data-stu-id="9170d-125">(might appear instead as)</span></span>  
<span data-ttu-id="9170d-126">Visual C++ -> Windows IoT Core-Anwendung für Windows IoT Core verknüpfen Arduino >.</span><span class="sxs-lookup"><span data-stu-id="9170d-126">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![App erstellen](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="9170d-128">Portieren</span><span class="sxs-lookup"><span data-stu-id="9170d-128">Porting</span></span>

<span data-ttu-id="9170d-129">Der Arduino-verknüpfen-API wurde sorgfältig implementiert, um zum Kopieren/Bibliotheken und einen groben Entwurf in einem Projekt verknüpfen Arduino einfügen können.</span><span class="sxs-lookup"><span data-stu-id="9170d-129">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="9170d-130">Trotzdem sind vorhanden, in einigen Fällen kleine Änderungen notwendig, die Sie möglicherweise an Ihre Skizzen oder Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="9170d-130">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="9170d-131">Wir erstellten ein einfach zu folgen [Arduino verknüpfen: Portierungsanleitung](ArduinoWiringPortingGuide.md) dieser potenziellen Probleme zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="9170d-131">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="9170d-132">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="9170d-132">Build and Deploy</span></span>

- <span data-ttu-id="9170d-133">Visual Studio stellen Sie sicher, dass "Remotecomputer" als Bereitstellungsziel ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="9170d-133">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="9170d-134">Stellen Sie außerdem sicher, dass die Architektur festgelegt ist, auf das Board entsprechen, das Sie auf das Projekt ausführen.</span><span class="sxs-lookup"><span data-stu-id="9170d-134">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="9170d-135">Für die Raspberry Pi 2- oder 3 für den Minnowboard maximalen, wählen Sie "X86" und wählen Sie "ARM".</span><span class="sxs-lookup"><span data-stu-id="9170d-135">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![Remotecomputer](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="9170d-137">Öffnen Sie die Projektmappeneigenschaften finden Sie im Kontextmenü "Debuggen" in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9170d-137">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![Projektmappeneigenschaften](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="9170d-139">Suchen Sie den IP-Adresse oder den Computer den Namen Ihres Geräts aus.</span><span class="sxs-lookup"><span data-stu-id="9170d-139">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="9170d-140">Verwenden Sie die Windows 10 IoT Core Dashboard-Anwendung oder verknüpfen Sie Ihr Gerät auf einen Monitor.</span><span class="sxs-lookup"><span data-stu-id="9170d-140">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="9170d-141">Geben Sie den Namen des Computers (Minwinpc standardmäßig) oder die IP-Adresse des Remotecomputers in das Feld "Computername" an.</span><span class="sxs-lookup"><span data-stu-id="9170d-141">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="9170d-142">Wenn Sie Ihr Gerät in einen umbenannt haben, neben "Minwinpc" diesen Namen in das Feld für die Anmeldung verwenden.</span><span class="sxs-lookup"><span data-stu-id="9170d-142">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="9170d-143">Stellen Sie sicher, dass der Authentican-Typ ist: Universell (unverschlüsseltes Protokoll)</span><span class="sxs-lookup"><span data-stu-id="9170d-143">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![Projektmappeneigenschaften](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="9170d-145">Drücken Sie F5, um Ihr Projekt auf Ihrem Gerät erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9170d-145">Press F5 to build and deploy your project on your device.</span></span>
