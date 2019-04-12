---
title: Spitzen und monitorlose-Geräte
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Windows IoT Core Spitzen oder monitorlosen Modus für die Geräte zu konfigurieren.
keywords: Windows Iot, Bildschirme, Spitzen, monitorlose UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513298"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="cf9c4-104">Spitzen und monitorlose-Geräte</span><span class="sxs-lookup"><span data-stu-id="cf9c4-104">Headed and Headless devices</span></span>

<span data-ttu-id="cf9c4-105">Windows 10 IoT Core kann konfiguriert werden, entweder *Spitzen* oder *monitorlose* Modus.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="cf9c4-106">Modus</span><span class="sxs-lookup"><span data-stu-id="cf9c4-106">Headed mode</span></span>
<span data-ttu-id="cf9c4-107">Modus wird durch das Vorhandensein der Benutzeroberfläche definiert.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="cf9c4-108">In *Spitzen* Modus eine einzelne app für die Benutzeroberfläche beim Systemstart gestartet, und es kann außerdem werden 0 oder mehr "Hintergrund-Apps" (StartupTasks).</span><span class="sxs-lookup"><span data-stu-id="cf9c4-108">In *headed* mode a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="cf9c4-109">Monitorlosen Modus</span><span class="sxs-lookup"><span data-stu-id="cf9c4-109">Headless mode</span></span>
<span data-ttu-id="cf9c4-110">Monitorlosen Modus besitzt keine Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-110">Headless mode has no UI.</span></span>  <span data-ttu-id="cf9c4-111">Geräte, die Funktionen der Benutzeroberfläche nicht benötigen, können so festgelegt werden *monitorlose* Modus.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="cf9c4-112">Der UI-Stapel ist deaktiviert, und UI-apps nicht gestartet.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="cf9c4-113">Dies reduziert die Menge an Systemressourcen verwendet.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="cf9c4-114">Wenn Sie einen Monitor an Ihr Gerät anfügen, wird der Bildschirm schwarze sein.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="cf9c4-115">Wenn Sie Ihr Gerät in monitorlosen Modus zu versetzen, können Sie die Windows 10 IoT Core Dashboard-Anwendung, unten, um die IP-Adresse finden verwenden.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="cf9c4-116">Modus ändern</span><span class="sxs-lookup"><span data-stu-id="cf9c4-116">Changing the mode</span></span>
<span data-ttu-id="cf9c4-117">Sie können den Spitzen monitorlose/Status Ihres Geräts aus einer Windows PowerShell-Sitzung oder einer SSH-Sitzung ändern.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="cf9c4-118">Weitere Informationen zu PowerShell finden Sie unter den [PowerShell IoT Core](../connect-your-device/PowerShell.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="cf9c4-119">Weitere Informationen zu SSH finden Sie unter den [SSH für IoT Core](../connect-your-device/SSH.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="cf9c4-120">Um den aktuellen Status des Geräts anzuzeigen, verwenden Sie die `setbootoption` Hilfsprogramm:</span><span class="sxs-lookup"><span data-stu-id="cf9c4-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="cf9c4-121">Um den Status Ihres Geräts monitorlosen Modus zu ändern, verwenden die `setbootoption` -Hilfsprogramm mit der `headless` Arg:</span><span class="sxs-lookup"><span data-stu-id="cf9c4-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="cf9c4-122">Verwenden Sie zum Ändern der Status des Geräts zu, die Spitzen im Aktivierungsmodus der `setbootoption` -Hilfsprogramm mit der `headed` Arg:</span><span class="sxs-lookup"><span data-stu-id="cf9c4-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="cf9c4-123">Suchen Ihr Gerät monitorlose</span><span class="sxs-lookup"><span data-stu-id="cf9c4-123">Finding your headless device</span></span>

<span data-ttu-id="cf9c4-124">Ein IoT Core-Geräts, das im monitorlosen Modus kann ermittelt werden, mithilfe der **Windows 10 IoT Core Dashboard** Anwendung.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="cf9c4-125">Informationen zum Herunterladen der IoT-Dashboard finden Sie unter den [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) Seite.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-125">To download the IoT Dashboard, see the [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="cf9c4-126">Bei der Ausführung wird die Anwendung wartet auf Ping-Nachrichten von jedem IoT Core-Geräten im lokalen Netzwerk und zeigt die Geräteinformationen, z. B. den Namen, IP-Adresse und mehr.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Windows 10 IoT Core Dashboard](../media/HeadlessMode/selectDevice.png)
