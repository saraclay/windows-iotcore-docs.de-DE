---
title: Übersicht über die AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie mehr über AllJoyn, ein gemeinsames Protokoll für IoT-Geräte und wie sie andere Erweiterungen und Features mit Windows IoT ermöglicht.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 6655cf5e8584a9c7046301cda24b10348a704d6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512378"
---
> [!NOTE]
> <span data-ttu-id="fcbc8-104">Sie zeigen die archivierte Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-104">You are viewing archived documentation.</span></span> <span data-ttu-id="fcbc8-105">AllJoyn wird nicht mehr von Windows 10 IoT unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="fcbc8-106">Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn"></a><span data-ttu-id="fcbc8-107">AllJoyn</span><span class="sxs-lookup"><span data-stu-id="fcbc8-107">AllJoyn</span></span>

<span data-ttu-id="fcbc8-108">AllJoyn ermöglicht das Internet der Dinge.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-108">AllJoyn empowers the Internet of Things.</span></span> <span data-ttu-id="fcbc8-109">AllJoyn definiert ein gemeinsames Protokoll für Geräte und Anwendungen erkennen und miteinander kommunizieren, unabhängig von Transport-Technologie, Plattform oder Hersteller.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-109">AllJoyn defines a common protocol for devices and applications to discover and communicate with each other regardless of transport technology, platform or manufacturer.</span></span>  <span data-ttu-id="fcbc8-110">AllJoyn ist ein open Source-standard hängt von der [AllSeen Alliance](https://allseenalliance.org/), ein Kreuz Branchenkonsortium dedizierte zu ermöglichen die Interoperabilität von Milliarden von Geräten, Diensten und Anwendungen für das Internet der Dinge.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-110">AllJoyn is an open source standard driven by the [AllSeen Alliance](https://allseenalliance.org/), a cross-industry consortium dedicated to enabling the interoperability of billions of devices, services and applications for the Internet of Things.</span></span>

<span data-ttu-id="fcbc8-111">Microsoft kam die Alliance AllSeen 2014 und AllJoyn als Komponente in Windows 10 hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-111">Microsoft joined the AllSeen Alliance in 2014 and added AllJoyn as a core component in Windows 10.</span></span> <span data-ttu-id="fcbc8-112">Mit der integrierten [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), Entwickler können sich, dass AllJoyn-fähige Anwendungen zu schreiben, die auf die Windows 10-Geräte einschließlich PCs, Tablets, Smartphones, Xbox sowie Geräte, die mithilfe von Windows IoT Core ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-112">With the built-in [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), developers are free to write AllJoyn capable applications that run on any of the Windows 10 devices including PCs, tablets, phones, Xbox as well as devices using Windows IoT Core.</span></span> <span data-ttu-id="fcbc8-113">Neben der plattformunterstützung für für AllJoyn Microsoft veröffentlicht [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), Visual Studio-Erweiterung, die AllJoyn Entwicklung beschleunigt, indem Sie die codegenerierung mit vorgefertigten Anwendungsvorlagen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-113">In addition to the platform support for AllJoyn, Microsoft released [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), a Visual Studio extension that accelerates AllJoyn development by combining code generation with ready-made application templates.</span></span> <span data-ttu-id="fcbc8-114">AllJoyn Studio können Entwickler profitieren von der Leistungsfähigkeit von AllJoyn ohne umständliche Einrichtung und Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-114">AllJoyn Studio allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="fcbc8-115">Begeistert AllJoyn ein?</span><span class="sxs-lookup"><span data-stu-id="fcbc8-115">Excited about AllJoyn?</span></span> <span data-ttu-id="fcbc8-116">Sehen Sie sich [dies](AllJoynStudio.md) Blogbeitrag zum Einstieg in AllJoyn auf Windows.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-116">Have a look at [this](AllJoynStudio.md) blog post on how to get started with AllJoyn on Windows.</span></span>


## <a name="developer-resources-and-tools"></a><span data-ttu-id="fcbc8-117">Ressourcen für Entwickler und Tools</span><span class="sxs-lookup"><span data-stu-id="fcbc8-117">Developer Resources and Tools</span></span>

**<span data-ttu-id="fcbc8-118">Gerät-System-Bridge</span><span class="sxs-lookup"><span data-stu-id="fcbc8-118">Device System Bridge</span></span>**

<span data-ttu-id="fcbc8-119">AllJoyn [Gerät System Bridge](AllJoynDSB.md) ermöglicht nicht AllJoyn-Geräten für die Interaktion mit dem AllJoyn-Ökosystem mit AllJoyn als einheitliche Sprache.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-119">AllJoyn [Device System Bridge](AllJoynDSB.md) enables non-AllJoyn devices to interact with the AllJoyn ecosystem using AllJoyn as their common language.</span></span>

<span data-ttu-id="fcbc8-120">Features:</span><span class="sxs-lookup"><span data-stu-id="fcbc8-120">Features:</span></span>
* <span data-ttu-id="fcbc8-121">Erstellt virtuelle Geräte für jedes nicht-AllJoyn-Gerät, von dem Adapter verfügbar gemacht werden</span><span class="sxs-lookup"><span data-stu-id="fcbc8-121">Creates virtual devices for each non-AllJoyn device exposed by Adapter</span></span>
* <span data-ttu-id="fcbc8-122">Automatisierte Runtime Generierung der Benutzeroberfläche von Adapter-Gerät</span><span class="sxs-lookup"><span data-stu-id="fcbc8-122">Automated runtime interface generation from Adapter device</span></span>
* <span data-ttu-id="fcbc8-123">Unterstützt die LSF, Systemsteuerung Basisdienste, erweiterbar, um weitere Dienste hinzufügen</span><span class="sxs-lookup"><span data-stu-id="fcbc8-123">Supports LSF, Control Panel base services, extensible to add more services</span></span>
* <span data-ttu-id="fcbc8-124">Universal app-Vorlagen (C#, C++) für Desktop-UI-Anwendungen und Windows IoT-starttasks</span><span class="sxs-lookup"><span data-stu-id="fcbc8-124">Universal app templates (C#, C++), for Desktop UI applications and Windows IoT startup tasks</span></span>
* <span data-ttu-id="fcbc8-125">Als open Source verfügbar</span><span class="sxs-lookup"><span data-stu-id="fcbc8-125">Available as open source</span></span>

<span data-ttu-id="fcbc8-126">Weitere Informationen finden Sie auf die [Gerät System Bridge Seite](AllJoynDSB.md).</span><span class="sxs-lookup"><span data-stu-id="fcbc8-126">More details can be found on the [Device System Bridge page](AllJoynDSB.md).</span></span>


**<span data-ttu-id="fcbc8-127">AllJoyn Studio</span><span class="sxs-lookup"><span data-stu-id="fcbc8-127">AllJoyn Studio</span></span>**

<span data-ttu-id="fcbc8-128">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) ist eine Erweiterung für Visual Studio entwickelt von Microsoft, über die AllJoyn® Entwicklung beschleunigt die codegenerierung und die WinRT-API mit automatisierten Projektmanagement und vordefinierte Anwendungsvorlagen kombiniert.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-128">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) is an extension to Visual Studio developed by Microsoft that accelerates AllJoyn® development by combining code generation and the WinRT API with automated project management and ready-made application templates.</span></span> <span data-ttu-id="fcbc8-129">Sie ermöglicht Entwicklern, profitieren von der Leistungsfähigkeit von AllJoyn ohne umständliche Einrichtung und Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-129">It allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="fcbc8-130">Features:</span><span class="sxs-lookup"><span data-stu-id="fcbc8-130">Features:</span></span>
* <span data-ttu-id="fcbc8-131">Universal app-Vorlagen (C#, JavaScript, C++, Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-131">Universal app templates (C#, JavaScript, C++, Visual Basic)</span></span>
* <span data-ttu-id="fcbc8-132">Automatisierte Verwaltung und -Projekt die Dienstverweiskonfiguration</span><span class="sxs-lookup"><span data-stu-id="fcbc8-132">Automated reference management and project configuration</span></span>
* <span data-ttu-id="fcbc8-133">Hinzufügen/Entfernen von Schnittstellen in einer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="fcbc8-133">Adding/removing interfaces to/from a solution</span></span>
* <span data-ttu-id="fcbc8-134">Einfacher Zugriff auf die Projekt-Management über das Menü "AllJoyn®"</span><span class="sxs-lookup"><span data-stu-id="fcbc8-134">Easy access to project management via the AllJoyn® menu</span></span>
* <span data-ttu-id="fcbc8-135">Laden von Schnittstellen aus Introspection XML-Dateien</span><span class="sxs-lookup"><span data-stu-id="fcbc8-135">Loading interfaces from introspection XML file(s)</span></span>
* <span data-ttu-id="fcbc8-136">Ermittlung von Schnittstellen von Herstellern auf die network1</span><span class="sxs-lookup"><span data-stu-id="fcbc8-136">Discovering interfaces from producer(s) on the network1</span></span>

<span data-ttu-id="fcbc8-137">AllJoyn Studio installiert werden kann, über Visual Studio-Tools -> Erweiterungen und Updates...</span><span class="sxs-lookup"><span data-stu-id="fcbc8-137">AllJoyn Studio can be installed through Visual Studio Tools -> Extensions and Updates …</span></span> <span data-ttu-id="fcbc8-138">Online -> im Feld "Suche" Typ "AllJoyn" -></span><span class="sxs-lookup"><span data-stu-id="fcbc8-138">-> Online -> In the "Search" field type "AllJoyn"</span></span>

<span data-ttu-id="fcbc8-139">Weitere Details zur Verwendung von AllJoyn Studio stehen [hier](AllJoynStudio.md).</span><span class="sxs-lookup"><span data-stu-id="fcbc8-139">More detail about how to use AllJoyn Studio are available [here](AllJoynStudio.md).</span></span>

**<span data-ttu-id="fcbc8-140">IoT-Explorer für AllJoyn (AllJoyn-Explorer)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-140">IoT Explorer for AllJoyn (AllJoyn Explorer)</span></span>**

<span data-ttu-id="fcbc8-141">Das IoT-Explorer für AllJoyn (vormals bekannt als AllJoyn-Explorer) ist eine universelle Windows-Anwendung, für die Interaktion mit AllJoyn Geräten im lokalen NEAR-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-141">The IoT Explorer for AllJoyn (previously known as AllJoyn Explorer) is a Windows Universal Application for interacting with AllJoyn devices on the local proximity network.</span></span> <span data-ttu-id="fcbc8-142">Entwickler können Auflisten aller verfügbaren AllJoyn-Geräte, überprüfen die Struktur ihrer Schnittstellen-Objekt, als auch Signale empfangen, festlegen und Abrufen von Eigenschaften und Methoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-142">Developers can list all available AllJoyn devices, inspect their interface and object structure, as well as receive signals, set and get properties, and call methods.</span></span>

* <span data-ttu-id="fcbc8-143">[IoT-Explorer für AllJoyn-Store-App](https://www.microsoft.com/store/apps/9nblggh6gpxl): Dies ist der offizielle app-Speicherort.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-143">[IoT Explorer for AllJoyn Store App](https://www.microsoft.com/store/apps/9nblggh6gpxl): This is the official store app location.</span></span>
* <span data-ttu-id="fcbc8-144">[AllJoyn Explorer 1.0.1.11 (Vorgängerversion)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): Diese ZIP-Datei enthält das AllJoyn Explorer AppX-Paket auf einem Entwicklercomputer quergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-144">[AllJoyn Explorer 1.0.1.11 (previous release)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): This zip contains the AllJoyn Explorer AppX bundle to be side-loaded on a developer machine.</span></span> <span data-ttu-id="fcbc8-145">Dies ist eine frühere Version des IoT-Explorers für AllJoyn-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-145">This is a previously released version of the IoT Explorer for AllJoyn application.</span></span>
* <span data-ttu-id="fcbc8-146">[Installationshandbuch für AllJoyn Explorer](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): Diese PDF-Datei enthält die Dokumentation für den AllJoyn Explorer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-146">[AllJoyn Explorer Setup Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): This pdf contains the documentation for how to deploy the AllJoyn Explorer.</span></span>
* <span data-ttu-id="fcbc8-147">[Dass AllJoyn-Explorer-Benutzerhandbuch](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): Diese PDF-Datei enthält die Dokumentation für die Verwendung der AllJoyn-Explorer.</span><span class="sxs-lookup"><span data-stu-id="fcbc8-147">[AllJoyn Explorer User Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): This pdf contains the documentation for how to use the AllJoyn Explorer.</span></span>


### <a name="additional-resources"></a><span data-ttu-id="fcbc8-148">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="fcbc8-148">Additional Resources</span></span>

* [<span data-ttu-id="fcbc8-149">Mithilfe der AllJoyn-Studio-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="fcbc8-149">Using the AllJoyn Studio extension</span></span>](AllJoynStudio.md)
* [<span data-ttu-id="fcbc8-150">Dass AllJoyn-Producer und AllJoyn Introspection erstellen</span><span class="sxs-lookup"><span data-stu-id="fcbc8-150">AllJoyn Producer and Authoring AllJoyn Introspection</span></span>](AllJoynProducer.md)
* [<span data-ttu-id="fcbc8-151">Problembehandlung bei AllJoyn mit Windows 10</span><span class="sxs-lookup"><span data-stu-id="fcbc8-151">Troubleshooting AllJoyn with Windows 10</span></span>](AllJoynTroubleshooting.md)

**<span data-ttu-id="fcbc8-152">Videos</span><span class="sxs-lookup"><span data-stu-id="fcbc8-152">Videos</span></span>**

* [<span data-ttu-id="fcbc8-153">//build 2015 AllJoyn Technical Session</span><span class="sxs-lookup"><span data-stu-id="fcbc8-153">//build 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/Build/2015/2-623)
* [<span data-ttu-id="fcbc8-154">WinHEC 2015 AllJoyn technischen Sitzung</span><span class="sxs-lookup"><span data-stu-id="fcbc8-154">WinHEC 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**<span data-ttu-id="fcbc8-155">Proben</span><span class="sxs-lookup"><span data-stu-id="fcbc8-155">Samples</span></span>**

* [<span data-ttu-id="fcbc8-156">AllJoyn Producers</span><span class="sxs-lookup"><span data-stu-id="fcbc8-156">AllJoyn Producers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [<span data-ttu-id="fcbc8-157">Dass AllJoyn-Consumer</span><span class="sxs-lookup"><span data-stu-id="fcbc8-157">AllJoyn Consumers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [<span data-ttu-id="fcbc8-158">Dass AllJoyn-UWP-Beispielen (MSDN)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-158">AllJoyn UWP Samples (MSDN)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**<span data-ttu-id="fcbc8-159">Referenz</span><span class="sxs-lookup"><span data-stu-id="fcbc8-159">Reference</span></span>**

* [<span data-ttu-id="fcbc8-160">Dass AllJoyn-APIs unter Windows 10 (MSDN)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-160">AllJoyn APIs in Windows 10 (MSDN)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [<span data-ttu-id="fcbc8-161">Erläutert, dass AllJoyn-Architektur (Allseen Alliance)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-161">AllJoyn Architecture Details (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/learn/)
* [<span data-ttu-id="fcbc8-162">Entwicklerressourcen für AllJoyn (Allseen Alliance)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-162">AllJoyn Developer Resources (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/develop/)
* [<span data-ttu-id="fcbc8-163">AllJoyn C-API-Referenzhandbuch (Allseen Alliance)</span><span class="sxs-lookup"><span data-stu-id="fcbc8-163">AllJoyn C API Reference Manual (Allseen Alliance)</span></span>](https://allseenalliance.org/docs/api/c/index.html)

