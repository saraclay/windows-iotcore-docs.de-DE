---
title: Übersicht über IoT-Shell
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie die IoT-Shell zum Navigieren zwischen Navigationen hinweg auf Ihrem Gerät nutzen können.
keywords: Windows Iot core IoT-Shell "," Anwendungen "," vordergrundanwendungen "," Programme im Hintergrund
ms.openlocfilehash: be72fabc91fc5748a029b61ebd9a306deb23f726
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513329"
---
# <a name="iot-shell-overview"></a><span data-ttu-id="a6e8d-104">Übersicht über IoT-Shell</span><span class="sxs-lookup"><span data-stu-id="a6e8d-104">IoT Shell Overview</span></span>

<span data-ttu-id="a6e8d-105">In diesem Dokument wird beschrieben, die IoT-Shell Vordergrund und Hintergrund-Anwendungen und zum Navigieren zwischen diesen Anwendungen auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-105">This document covers the IoT Shell, foreground and background applications, and how to navigate between these applications on your device.</span></span>

## <a name="iot-shell-foreground-and-background-apps"></a><span data-ttu-id="a6e8d-106">IoT-Shell, Vordergrund und Hintergrund-Apps</span><span class="sxs-lookup"><span data-stu-id="a6e8d-106">IoT Shell, Foreground, and Background Apps</span></span>

<span data-ttu-id="a6e8d-107">Ihr Gerät IoT Core ausgeführt wird, die IoT-Shell.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-107">Your IoT Core device runs the IoT Shell.</span></span> <span data-ttu-id="a6e8d-108">Er hat viele Aufgaben, aber die primäre Aufgabe besteht darin, sicherzustellen, dass apps für registrierte beim Start gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-108">It has many responsibilities, but its primary job is to make sure registered startup apps are launched.</span></span> <span data-ttu-id="a6e8d-109">Es verfügt über zwei Modi: Multi-Monitor "und" monitorlose ".</span><span class="sxs-lookup"><span data-stu-id="a6e8d-109">It has two modes: Headed and Headless.</span></span> <span data-ttu-id="a6e8d-110">Im Modus "Headed" wird die IoT-Shell zu eine einzelnen registrierten Start-app starten, die anzeigt, die Benutzeroberfläche im Vollbildmodus (auch bekannt als eine Headed-app).</span><span class="sxs-lookup"><span data-stu-id="a6e8d-110">In Headed mode, the IoT Shell will launch a single registered startup app that will show its UI in full screen (also known as a Headed app).</span></span> <span data-ttu-id="a6e8d-111">Modus wird angenommen, Sie einen Bildschirm verbunden haben und zeigt die Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-111">Headed mode assumes you have a screen connected and shows UI.</span></span> <span data-ttu-id="a6e8d-112">Im monitorlosen Modus (ausführlich [hier](../learn-about-hardware/HeadlessMode.md)), wird keine Benutzeroberfläche angezeigt, die IoT-Shell startet nur die hintergrundanwendungen.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-112">In Headless mode (explained in detail [here](../learn-about-hardware/HeadlessMode.md)), there is no UI; the IoT Shell launches background applications only.</span></span>

<span data-ttu-id="a6e8d-113">Hier sind die Hauptunterschiede zwischen Vordergrund-und hintergrundanwendungen:</span><span class="sxs-lookup"><span data-stu-id="a6e8d-113">Here are the main differences between foreground and background applications:</span></span>

- <span data-ttu-id="a6e8d-114">**Vordergrundanwendungen** eine Benutzeroberfläche haben.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-114">**Foreground applications** have a UI.</span></span> <span data-ttu-id="a6e8d-115">Eine davon wird beim Start gestartet, wenn das Gerät im Modus befindet.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-115">One of these is launched at startup when the device is in headed mode.</span></span> <span data-ttu-id="a6e8d-116">Alle Foreground-apps werden auf dem Gerät registriert, und der Benutzer zwischen Vordergrund-apps während der Gerätevorgang wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-116">All foreground apps are registered on the device and the user can switch between foreground apps during device operation.</span></span>

- <span data-ttu-id="a6e8d-117">**Anwendungen im Hintergrund** keine Benutzeroberfläche aufweisen, und sparen somit Geräteressourcen durch Deaktivieren des UI-Stapels.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-117">**Background applications** have no UI and thus save device resources by turning off the UI stack.</span></span> <span data-ttu-id="a6e8d-118">Programme im Hintergrund wird häufig aus der Startdatei kontinuierlich ausgeführt und werden häufig verwendet, um das Gerät zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-118">Background applications often run continuously from startup and are often used to monitor the device.</span></span>

## <a name="switching-between-apps-with-a-home-app"></a><span data-ttu-id="a6e8d-119">Wechseln zwischen apps mit einer Home-App</span><span class="sxs-lookup"><span data-stu-id="a6e8d-119">Switching between apps with a Home App</span></span>

<span data-ttu-id="a6e8d-120">Im Moment ermöglicht die Start-App Ihnen die Erstellung eine home-app für Windows 10 IoT Core, dem Sie zwischen verschiedenen vordergrundanwendungen wechseln können.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-120">At the moment, the Startup App allows you to create a home app for Windows 10 IoT Core, which allows you to switch between different foreground applications.</span></span> 

<span data-ttu-id="a6e8d-121">Die **IoT-Start-App** ([Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp) eine simple-starttasks-app, die Listet die installierten apps auf Ihrem Gerät, und startet eine mithilfe der PackageManager-APIs darstellt.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-121">The **IoT Startup App** ([sample](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp) represents a simple startup app that lists the installed apps on your device, then launches one using the PackageManager APIs.</span></span>

## <a name="switching-between-apps-with-hid-injection-keys"></a><span data-ttu-id="a6e8d-122">Wechseln zwischen apps mit HID-Injection-Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="a6e8d-122">Switching between apps with HID Injection Keys</span></span>

<span data-ttu-id="a6e8d-123">Die folgenden Anweisungen zeigen, wie Sie Hotkey-Unterstützung durch Einträge in der Registrierung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-123">The below instructions show you how to turn on Hotkey support through entries to the registry.</span></span> <span data-ttu-id="a6e8d-124">Wenn Sie Ihr eigenes Image Erstellen und unterstützen möchten die folgenden Tastaturbefehle ("Home", "Vorherige app, und" nächste app ") ohne die Registrierung zugreifen, können Sie ein optionales Feature-Paket, das diese Schritte für Sie verarbeitet einschließen.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-124">If you are building your own image and want to support the below hotkeys (Home, previous app, and next app) without needing to access the registry, you can include an optional feature package that handles these steps for you.</span></span>

<span data-ttu-id="a6e8d-125">Wird aufgerufen, die zu suchende Featurepaket: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** und das Feature heißt **IOT_SHELL_HOTKEY_SUPPORT**.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-125">The feature package to look for is called: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** and the feature is called **IOT_SHELL_HOTKEY_SUPPORT**.</span></span> <span data-ttu-id="a6e8d-126">Finden Sie unter den [Settings.HotKey-Beispielpaket](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) verdeutlicht.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-126">See the [Settings.HotKey sample package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) for an example.</span></span>

<span data-ttu-id="a6e8d-127">Der Rest dieses Dokuments wird beschrieben, wie diese Funktion manuell zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-127">The rest of this document covers how to implement this feature manually.</span></span>

### <a name="return-home"></a><span data-ttu-id="a6e8d-128">Return-Startseite</span><span class="sxs-lookup"><span data-stu-id="a6e8d-128">Return Home</span></span>

<span data-ttu-id="a6e8d-129">Unterstützt der IoT-Shell mit dem Windows 10 IoT Anniversary Update (1607) das Standardfenster für die Anwendung in den Vordergrund bringen, wenn eine andere Anwendung ausgeführt wird, mit der Taste "GO HOME", die auf die Version der Windows-Schaltfläche auf einer Standardtastatur festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-129">With the Windows 10 IoT Anniversary Update (1607), the IoT Shell supports bringing the default application window to the foreground when another application is running by pressing the "GO HOME" key, which is set to the release of the Windows Button on a keyboard.</span></span> <span data-ttu-id="a6e8d-130">Wenn Sie eine Tastatur auf Ihrem IoT-Gerät besitzen, und Tastaturereignisse auf niedriger Ebene, durch einfügen müssen [HID-Injektion](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), oder wenn Sie nur die Funktionen "GO HOME" zu einem anderen Schlüssel in Ihrer app neu zuordnen möchten, können Sie anpassen, dass den Schlüsselwert in der die Registrierung.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-130">If you don't have a keyboard on your IoT Device and need to inject low-level keyboard events through [HID Injection](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), or if you just want to re-map the "GO HOME" functionality to a different key in your app, you can adjust the key value in the registry.</span></span> <span data-ttu-id="a6e8d-131">Z. B. um aktivieren Drücken der ESC-Taste (0x1B) Geben Sie auf "GO HOME" den folgenden Befehl in der Registrierung:</span><span class="sxs-lookup"><span data-stu-id="a6e8d-131">For example, to enable pressing the ESCAPE key (0x1B) to "GO HOME", enter the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

<span data-ttu-id="a6e8d-132">Als REG-Datei sieht dies wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a6e8d-132">As a REG file, this looks as follows:</span></span>

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a><span data-ttu-id="a6e8d-133">Wechseln zwischen Apps</span><span class="sxs-lookup"><span data-stu-id="a6e8d-133">Switch Between Apps</span></span>

<span data-ttu-id="a6e8d-134">Auch wenn Sie zwischen die Vordergrund-apps wechseln möchten, Sie können einrichten Alt + Tab (nächste app) und Umschalt-Alt-Tab (vorherige app) Funktionen in Ihrem Image mithilfe des folgenden Befehls in der Registrierung:</span><span class="sxs-lookup"><span data-stu-id="a6e8d-134">Alternatively, if you want to switch between your foreground apps, you can set up Alt-Tab (next app) and Shift-Alt-Tab (previous app) functionality in your image by entering the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

<span data-ttu-id="a6e8d-135">Als REG-Datei sieht dies wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a6e8d-135">As a REG file, this looks as follows:</span></span>
``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a><span data-ttu-id="a6e8d-136">Bit-Verschiebung</span><span class="sxs-lookup"><span data-stu-id="a6e8d-136">Bit Translation</span></span>

<span data-ttu-id="a6e8d-137">Die oben genannten REG-Dateieinträge Decodieren von links nach rechts, wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a6e8d-137">The above REG file entries decode left to right as follows:</span></span>

- <span data-ttu-id="a6e8d-138">Bits 0 bis 15: Virtueller Tastencode (d. h. 1 b, 00 für ESCAPEZEICHEN).</span><span class="sxs-lookup"><span data-stu-id="a6e8d-138">Bits 0-15: Virtual Key Code (i.e. 1B,00 for ESCAPE).</span></span> <span data-ttu-id="a6e8d-139">Finden Sie unter [virtueller Tastencode](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) für die vollständige Liste der Werte für Schlüssel</span><span class="sxs-lookup"><span data-stu-id="a6e8d-139">See [Virtual Key Code](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) for the complete list of key code values</span></span>
- <span data-ttu-id="a6e8d-140">Bits 16.-19.: Losgelassene Zusatztaste.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-140">Bits 16-19: Modifier Key.</span></span> <span data-ttu-id="a6e8d-141">0 x 0 = kein Modifizierer, 0 x 1 = ALT, 0 x 2 = STRG, und 0 x 4 = UMSCHALTTASTE.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-141">0x0 = No Modifier, 0x1 = ALT, 0x2 = CTRL, and 0x4 = SHIFT.</span></span> <span data-ttu-id="a6e8d-142">Kombinieren von Schlüsseln addiert die Werte (d. h., ALT + UMSCHALT ist 0 x 5)</span><span class="sxs-lookup"><span data-stu-id="a6e8d-142">Combining keys adds the values together (i.e. ALT+SHIFT is 0x5)</span></span>
- <span data-ttu-id="a6e8d-143">Bits 20: 47: Für die zukünftige Verwendung reserviert. 0 muss sein.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-143">Bits 20-47: Reserved for future use; must be 0</span></span>
- <span data-ttu-id="a6e8d-144">Bits 48-62:  Aktion</span><span class="sxs-lookup"><span data-stu-id="a6e8d-144">Bits 48-62:  Action</span></span>
    - <span data-ttu-id="a6e8d-145">0 = home</span><span class="sxs-lookup"><span data-stu-id="a6e8d-145">0 = Home</span></span>
    - <span data-ttu-id="a6e8d-146">1 = die vorherige Ansicht (funktioniert möglicherweise nicht in zukünftigen Versionen)</span><span class="sxs-lookup"><span data-stu-id="a6e8d-146">1 = Previous View (may not work in future releases)</span></span>
    - <span data-ttu-id="a6e8d-147">2 = nächste Ansicht (funktioniert möglicherweise nicht in zukünftigen Versionen)</span><span class="sxs-lookup"><span data-stu-id="a6e8d-147">2 = Next View (may not work in future releases)</span></span>
- <span data-ttu-id="a6e8d-148">Bit 63: Reserviert. 0 muss sein.</span><span class="sxs-lookup"><span data-stu-id="a6e8d-148">Bit 63: Reserved; must be 0</span></span>

