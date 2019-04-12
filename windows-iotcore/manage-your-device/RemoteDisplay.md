---
title: Remote-Anzeige
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Anzeigen und steuern Ihre Windows 10 IoT Core UWP-Anwendungen Remote.
keywords: Windows Iot, UWP, remote-Anzeige, remote, UWP-Anwendungen
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513370"
---
# <a name="remote-display"></a><span data-ttu-id="72d71-104">Remote-Anzeige</span><span class="sxs-lookup"><span data-stu-id="72d71-104">Remote display</span></span>
<span data-ttu-id="72d71-105">Zeigen Sie an und steuern Sie Ihre Windows 10 IoT Core UWP-Anwendungen Remote von einem Windows 10-desktop-PC, Tablet oder Telefon</span><span class="sxs-lookup"><span data-stu-id="72d71-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="72d71-106">Windows IoT-Remote-Client ist eine Entwickler-nur-Funktion.</span><span class="sxs-lookup"><span data-stu-id="72d71-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="72d71-107">Es ist nicht vorgesehen, oder für Produktionsgeräte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="72d71-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72d71-108">Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="72d71-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="72d71-109">Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.</span><span class="sxs-lookup"><span data-stu-id="72d71-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="72d71-110">Übersicht</span><span class="sxs-lookup"><span data-stu-id="72d71-110">Overview</span></span>
___
<span data-ttu-id="72d71-111">Die remote-Anzeige-Erfahrung ist ein Tool für Entwickler verwendet, um Remote auf einem Gerät Windows 10 IoT Core ausgeführten UWP-Anwendungen zu steuern.</span><span class="sxs-lookup"><span data-stu-id="72d71-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="72d71-112">Setup</span><span class="sxs-lookup"><span data-stu-id="72d71-112">Setup</span></span>
___
<span data-ttu-id="72d71-113">Informationen zum Einstieg müssen Sie zum Einrichten eines Windows 10 IoT Core-Geräts mit dem neuesten Build von Windows 10 – besuchen die [Einstieg](https://developer.microsoft.com/en-us/windows/iot/getstarted) Seite, um das Board einzurichten.</span><span class="sxs-lookup"><span data-stu-id="72d71-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="72d71-114">Setup kann schnell und einfach – führen Sie die drei Schritte unten aus, um die Anzeige der remote-Technologie verwenden.</span><span class="sxs-lookup"><span data-stu-id="72d71-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="72d71-115">Sicherstellen Sie, dass Ihrem IoT Core Geräte- und entwicklungssicherheit Computer auf dem gleichen Netzwerk und n einer sicheren Umgebung.</span><span class="sxs-lookup"><span data-stu-id="72d71-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="72d71-116">Eine Methode ist zum Verbinden Ihres Geräts direkt mit Ihrem Laptop, der mit einem USB-Ethernet-Adapter für der automatische Crossover unterstützt.</span><span class="sxs-lookup"><span data-stu-id="72d71-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter which supports automatic crossover.</span></span>

1. <span data-ttu-id="72d71-117">Aktivieren Sie die remote-Anzeige-Funktionalität auf Ihrem Windows 10 IoT Core-Gerät.</span><span class="sxs-lookup"><span data-stu-id="72d71-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="72d71-118">Verbinden Ihres Geräts mit dem Internet, und Verbinden mit Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="72d71-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="72d71-119">Wählen Sie die Seite "Remote" aus den Optionen auf der linken Seite, und markieren Sie das Kontrollkästchen "Aktivieren Sie im Fenster IoT-Remoteserver".</span><span class="sxs-lookup"><span data-stu-id="72d71-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="72d71-120">Ihr Gerät ist jetzt für remote anzeigen aktiviert.</span><span class="sxs-lookup"><span data-stu-id="72d71-120">Your device is now enabled for remote display experience.</span></span>
    ![Aktivieren Sie remote anzeigen](../media/RemoteDisplay/enable-remote.png)

1. <span data-ttu-id="72d71-122">Installieren der Windows IoT-Remote-Client auf Ihrem begleitende Windows 10-Gerät.</span><span class="sxs-lookup"><span data-stu-id="72d71-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="72d71-123">Um Windows 10-Gerät für die Verbindung mit Ihrem Windows 10 IoT Core-Gerät zu aktivieren, müssen Sie die Store-Anwendung zu installieren.</span><span class="sxs-lookup"><span data-stu-id="72d71-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="72d71-124">Die Windows IoT-Remote-Client-app ist durch Link nur verfügbar, und finden Sie [hier](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span><span class="sxs-lookup"><span data-stu-id="72d71-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![Installieren von Client-app](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="72d71-126">Verbinden Sie mit Ihrem Windows 10 IoT Core-Gerät über die installierte Anwendung.</span><span class="sxs-lookup"><span data-stu-id="72d71-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="72d71-127">Führen Sie die Windows IoT-Remote-Client-Anwendung auf Ihrem Windows 10-Gerät Companion.</span><span class="sxs-lookup"><span data-stu-id="72d71-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="72d71-128">Geben Sie die IP-Adresse Ihres Geräts, auf dem Bildschirm "Verbinden".</span><span class="sxs-lookup"><span data-stu-id="72d71-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="72d71-129">Die beiden Geräte eine Verbindung herstellen soll, Remoting die Benutzeroberfläche des Windows 10 IoT Core-Geräts auf das begleitgerät.</span><span class="sxs-lookup"><span data-stu-id="72d71-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="72d71-130">Sie sind nun verbunden.</span><span class="sxs-lookup"><span data-stu-id="72d71-130">You're now connected!</span></span> <span data-ttu-id="72d71-131">An diesem Punkt weiterleiten, touch, und klicken Sie auf Eingabe auf der Begleit-Windows 10-Gerät verwendet werden kann, um die Windows 10 IoT Core UWP-Anwendung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="72d71-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![Gerät verbinden](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="72d71-133">Kompatibilität und Bereich</span><span class="sxs-lookup"><span data-stu-id="72d71-133">Compatibility and scope</span></span>
___
<span data-ttu-id="72d71-134">Damit der IoT-Remote-Client verwenden zu können, müssen Sie den neuesten Build von Windows 10 IoT Core auf dem Zielgerät und die aktuelle Clientanwendung aus dem Store ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="72d71-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="72d71-135">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="72d71-135">Troubleshooting</span></span>
___
<span data-ttu-id="72d71-136">Mithilfe der remote-Anzeige-Technologie ist schnell und einfach, aber es gibt noch einige Probleme, die Benutzer auftreten können.</span><span class="sxs-lookup"><span data-stu-id="72d71-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="72d71-137">Stellen Sie sicher, dass das Setup führen die obigen Anweisungen unten eng - Wenn weiterhin Probleme auftreten, überprüfen.</span><span class="sxs-lookup"><span data-stu-id="72d71-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="72d71-138">Wenn ich versuche, eine Verbindung herstellen, wird die Client-app, um einen weißen Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="72d71-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="72d71-139">Verbindungsfehler können durch eine Reihe von Problemen verursacht werden, aber wir haben ein paar weitere häufige Probleme auftreten:</span><span class="sxs-lookup"><span data-stu-id="72d71-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="72d71-140">Stellen Sie sicher, dass Sie den neuesten Insider-Version von Windows 10 IoT Core und die IoT-Remote-Client-Anwendung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="72d71-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="72d71-141">Stellen Sie zunächst sicher, dass Ihre IoT-Geräte auf dem gleichen Netzwerk wie Ihr begleitgerät ist.</span><span class="sxs-lookup"><span data-stu-id="72d71-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="72d71-142">Überprüfen Sie, dass Sie mit dem IoT-Remoteserver Windows aktiviert den neuesten Insider-Build von Windows 10 IoT Core ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="72d71-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="72d71-143">Wenn dies nicht das Problem ist, versuchen Sie es ändern, die Auflösung von Ihrem Gerät, um etwas, das wir zur Unterstützung garantiert sind befolgen Sie die Anweisungen in Schritt 1 von den Setup-Abschnitt oben zum Navigieren auf Webserver Ihres Geräts.</span><span class="sxs-lookup"><span data-stu-id="72d71-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="72d71-144">Bleiben Sie auf der Seite "Home" anstelle von "Remote" im Menü auf der linken Seite, und scrollen Sie nach unten, um Lösung zu finden.</span><span class="sxs-lookup"><span data-stu-id="72d71-144">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="72d71-145">Versuchen Sie es 800 x 600.</span><span class="sxs-lookup"><span data-stu-id="72d71-145">Try 800x600.</span></span>
1. <span data-ttu-id="72d71-146">Wenn dies noch nicht zu Ihrem Problem beheben, müssen Sie möglicherweise ein Problem, das ist, verbinden Ihr Gerät nicht an einen externen Monitor.</span><span class="sxs-lookup"><span data-stu-id="72d71-146">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="72d71-147">Dadurch wird das Gerät selbst als rein monitorlose vorstellen.</span><span class="sxs-lookup"><span data-stu-id="72d71-147">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="72d71-148">So beheben Sie dieses Problem</span><span class="sxs-lookup"><span data-stu-id="72d71-148">To fix this:</span></span>
    * <span data-ttu-id="72d71-149">Werfen Sie die MicroSD-Karte, und fügen Sie in Ihrem computer</span><span class="sxs-lookup"><span data-stu-id="72d71-149">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="72d71-150">Bearbeiten Sie die</span><span class="sxs-lookup"><span data-stu-id="72d71-150">Edit the</span></span> `<MicroSD card drive>:\config.txt`
    * <span data-ttu-id="72d71-151">Fügen Sie die folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="72d71-151">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
