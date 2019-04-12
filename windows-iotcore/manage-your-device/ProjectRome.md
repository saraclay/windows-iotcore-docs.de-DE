---
title: Verwenden von Projekt "ROME" mit Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: Erfahren Sie, und verstehen Sie die Schritte in Ihrem Windows-IoT-Gerät auf den Markt zu.
keywords: Windows 10 IoT Core, Projekt "ROME", remote-Geräte
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513897"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="4b837-104">Verwenden von Projekt "ROME" mit Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="4b837-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="4b837-105">[Projekt "ROME"](https://developer.microsoft.com/en-us/windows/project-rome) können Sie Remote mit Geräten mit Windows 10 IoT Core unter Verwendung des RemoteSystems und AppServiceProvider-APIs arbeiten.</span><span class="sxs-lookup"><span data-stu-id="4b837-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="4b837-106">In diesem Artikel Gehe wir durch die Schritte zum Ermitteln,-Steuerelement, und eine Verbindung mit Geräten mit Windows 10 IoT Core mit Projekt "ROME".</span><span class="sxs-lookup"><span data-stu-id="4b837-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="4b837-107">Ermittlung von IoT-Core-Geräte mit dem RemoteSystem-APIs</span><span class="sxs-lookup"><span data-stu-id="4b837-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
_<span data-ttu-id="4b837-108">Setup:</span><span class="sxs-lookup"><span data-stu-id="4b837-108">Setup:</span></span>_
* <span data-ttu-id="4b837-109">Führen Sie das RemoteSystems-Beispiel auf einem Desktop, während Sie bei Ihrem Microsoft-Konto angemeldet.</span><span class="sxs-lookup"><span data-stu-id="4b837-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="4b837-110">Keine App auf IoT Core ausgeführt wird melden Sie sich bei Ihrem Microsoft-Konto dazu auf Cortana-Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="4b837-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="4b837-111">Schritte:</span><span class="sxs-lookup"><span data-stu-id="4b837-111">Steps:</span></span>_
1. <span data-ttu-id="4b837-112">Ausführen des RemoteSystems-Beispiels auf Ihrem desktop</span><span class="sxs-lookup"><span data-stu-id="4b837-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="4b837-113">Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen"</span><span class="sxs-lookup"><span data-stu-id="4b837-113">Under "1) Discovery," click "Search for systems"</span></span> 

![Zur Suche nach Systemen](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="4b837-115">IoT Core-Geräte mit RemoteSystems.LaunchUri steuern</span><span class="sxs-lookup"><span data-stu-id="4b837-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
_<span data-ttu-id="4b837-116">Setup:</span><span class="sxs-lookup"><span data-stu-id="4b837-116">Setup:</span></span>_
* <span data-ttu-id="4b837-117">Führen Sie die [RemoteSystems Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) auf etwas Desktop [bei Ihrem Microsoft-Konto angemeldet](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span><span class="sxs-lookup"><span data-stu-id="4b837-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="4b837-118">Keine App auf IoT Core ausgeführt wird melden Sie sich bei Ihrem Microsoft-Konto dazu auf Cortana-Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="4b837-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="4b837-119">Schritte:</span><span class="sxs-lookup"><span data-stu-id="4b837-119">Steps:</span></span>_
1. <span data-ttu-id="4b837-120">Aktivieren Sie die IoT Core-VM mit Cortana und Anmeldung bei Ihrem Microsoft-Konto von cortana erhalten.</span><span class="sxs-lookup"><span data-stu-id="4b837-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="4b837-121">Führen Sie das Beispiel RemoteSystems, auf dem Desktop.</span><span class="sxs-lookup"><span data-stu-id="4b837-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="4b837-122">Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen".</span><span class="sxs-lookup"><span data-stu-id="4b837-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="4b837-123">Klicken Sie unter "(2) Start-URI" Wählen Sie das IoT Core-Gerät, das Cortana ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4b837-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="4b837-124">Geben Sie diesen URI, und starten.</span><span class="sxs-lookup"><span data-stu-id="4b837-124">Enter this URI and launch.</span></span> 

![Starten des URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="4b837-126">Herstellen einer Verbindung mit dem App-Remotedienst auf IoT Core ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="4b837-126">Connecting to the Remote App Service running on IoT Core</span></span> 
_<span data-ttu-id="4b837-127">Setup:</span><span class="sxs-lookup"><span data-stu-id="4b837-127">Setup:</span></span>_
* <span data-ttu-id="4b837-128">Führen Sie die [RemoteSystems Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) auf etwas Desktop [bei Ihrem Microsoft-Konto angemeldet](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span><span class="sxs-lookup"><span data-stu-id="4b837-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="4b837-129">Stellen Sie sicher, damit die [AppServiceProvider-app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) bereitgestellt und auf mindestens ein Gerät von IoT Core ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4b837-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
_<span data-ttu-id="4b837-130">Schritte:</span><span class="sxs-lookup"><span data-stu-id="4b837-130">Steps:</span></span>_
1. <span data-ttu-id="4b837-131">Aktivieren Sie auf der IoT Core-VM mit Cortana, und melden Sie sich bei Ihrem Microsoft-Konto von cortana erhalten.</span><span class="sxs-lookup"><span data-stu-id="4b837-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="4b837-132">Die AppServiceProvider-app bereitstellen, einmal ausgeführt, und beenden sie Sie.</span><span class="sxs-lookup"><span data-stu-id="4b837-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="4b837-133">Führen Sie das Beispiel RemoteSystems, auf dem Desktop.</span><span class="sxs-lookup"><span data-stu-id="4b837-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="4b837-134">Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen".</span><span class="sxs-lookup"><span data-stu-id="4b837-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="4b837-135">Unter"(3) starten App-Dienste" auswählen, die der IoT core-Gerät, das die AppServiceProvider-app bereitgestellt wurde und der zuvor ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="4b837-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="4b837-136">Eine Zufallszahl zu generieren.</span><span class="sxs-lookup"><span data-stu-id="4b837-136">Generate a random number.</span></span>  

![Starten der App-Dienste](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="4b837-138">Steuern von anderen Geräten und app-Dienste über ein Gerät IoT Core</span><span class="sxs-lookup"><span data-stu-id="4b837-138">Controlling other devices and app services from an IoT Core device</span></span> 

_<span data-ttu-id="4b837-139">Setup:</span><span class="sxs-lookup"><span data-stu-id="4b837-139">Setup:</span></span>_
* <span data-ttu-id="4b837-140">Führen Sie die [RemoteSystems Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) auf ein Gerät IoT Core bereitgestellten [bei Ihrem Microsoft-Konto angemeldet](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) aus der Cortana-app.</span><span class="sxs-lookup"><span data-stu-id="4b837-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="4b837-141">Haben Sie einem Desktopcomputer mit der [AppServiceProvider-app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) bereitgestellt, und dass sich mindestens einmal ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="4b837-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
_<span data-ttu-id="4b837-142">Schritte:</span><span class="sxs-lookup"><span data-stu-id="4b837-142">Steps:</span></span>_
1. <span data-ttu-id="4b837-143">Ausführen des RemoteSystems-Beispiels.</span><span class="sxs-lookup"><span data-stu-id="4b837-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="4b837-144">Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen".</span><span class="sxs-lookup"><span data-stu-id="4b837-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="4b837-145">Klicken Sie unter "(2) Start-URI" Wählen Sie die Desktop-Computer und starten.</span><span class="sxs-lookup"><span data-stu-id="4b837-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="4b837-146">Klicken Sie unter "(3) starten App Services" Wählen Sie den desktop-Computer.</span><span class="sxs-lookup"><span data-stu-id="4b837-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="4b837-147">Beim ersten Versuch kann dies sehr lange dauern.</span><span class="sxs-lookup"><span data-stu-id="4b837-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="4b837-148">Versuchen Sie es erneut für eine viel schnellere Antwort.</span><span class="sxs-lookup"><span data-stu-id="4b837-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="4b837-149">Hilfreiche Links:</span><span class="sxs-lookup"><span data-stu-id="4b837-149">Helpful links:</span></span> 
* [<span data-ttu-id="4b837-150">Projekt "ROME" Dokumentation auf MSDN</span><span class="sxs-lookup"><span data-stu-id="4b837-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="4b837-151">Verwenden von Projekt "ROME" für UWP</span><span class="sxs-lookup"><span data-stu-id="4b837-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
