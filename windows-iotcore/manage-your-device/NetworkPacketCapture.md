---
title: Erfassung von Netzwerkpaketen
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Microsoft Message Analyzer, die zum Aktivieren der Erfassung von Netzwerkpaketen verwenden
keywords: Windows Iot, Netzwerkpaket, Erfassung von Netzwerkpaketen, Microsoft Message Analyzer, PowerShell
ms.openlocfilehash: 1880b6502099c50653e9e60ebc3d4ff3cd926450
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512666"
---
# <a name="network-packet-capture"></a><span data-ttu-id="2464f-104">Erfassung von Netzwerkpaketen</span><span class="sxs-lookup"><span data-stu-id="2464f-104">Network packet capture</span></span>

<span data-ttu-id="2464f-105">Sie können [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) zum Erfassen, anzeigen und Analysieren der Protokoll-Datenverkehr auf Ihrem Windows 10 IoT Core-Gerät-messaging.</span><span class="sxs-lookup"><span data-stu-id="2464f-105">You can use [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="2464f-107">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2464f-107">Prerequisites</span></span>

<span data-ttu-id="2464f-108">Verwenden von PowerShell-Verbindung (Schritt 1 bis 8 finden Sie unter [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="2464f-108">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="2464f-109">Richten Ihres Geräts ein</span><span class="sxs-lookup"><span data-stu-id="2464f-109">Set up your device</span></span>

<span data-ttu-id="2464f-110">Um auf Ihr Gerät mithilfe von Message Analyzer eine Verbindung herzustellen, müssen Sie zunächst Ihr Gerät umbenennen.</span><span class="sxs-lookup"><span data-stu-id="2464f-110">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="2464f-111">Dies kann erfolgen über [SSH](../connect-your-device/SSH.md) oder [PowerShell](../connect-your-device/PowerShell.md) mithilfe der `setcomputername` Befehl.</span><span class="sxs-lookup"><span data-stu-id="2464f-111">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![PowerShell-Rename-Gerät](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="2464f-113">Nachdem Sie Ihr Gerät umbenennen, neu starten des Geräts, um die Änderung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="2464f-113">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="2464f-114">Die Firewall ausschalten</span><span class="sxs-lookup"><span data-stu-id="2464f-114">Turn off the firewall</span></span>

<span data-ttu-id="2464f-115">Herstellen einer Verbindung Ihres Geräts mithilfe von PowerShell oder SSH mit ein, und führen Sie den folgenden Befehl zum Deaktivieren der Firewalls.</span><span class="sxs-lookup"><span data-stu-id="2464f-115">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="2464f-116">Herstellen einer Verbindung Ihres Geräts mithilfe von Message Analyzer mit</span><span class="sxs-lookup"><span data-stu-id="2464f-116">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="2464f-117">Nun, dass Ihr Gerät haben eingerichtet, lassen Sie uns eine Verbindung mit Microsoft Message Analyzer.</span><span class="sxs-lookup"><span data-stu-id="2464f-117">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="2464f-118">Herunterladen der [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).</span><span class="sxs-lookup"><span data-stu-id="2464f-118">Download the [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="2464f-119">Öffnen Sie die Nachrichtenanalyse.</span><span class="sxs-lookup"><span data-stu-id="2464f-119">Open Message Analyzer.</span></span>
3. <span data-ttu-id="2464f-120">Klicken Sie auf `New Session`.</span><span class="sxs-lookup"><span data-stu-id="2464f-120">Click on `New Session`.</span></span>

    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="2464f-122">Klicken Sie im Fenster, das geöffnet wird, auf die `Live Trace` Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="2464f-122">In the window that opens, click on the `Live Trace` button.</span></span>
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. <span data-ttu-id="2464f-124">Klicken Sie auf die `Edit...` Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="2464f-124">Click on the `Edit...` button.</span></span>
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. <span data-ttu-id="2464f-126">Ersetzen Sie "localhost" durch den Namen Ihres IoT-Geräts ein, und geben Sie den Administratorbenutzernamen und das Kennwort.</span><span class="sxs-lookup"><span data-stu-id="2464f-126">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="2464f-127">Klicken Sie dann auf `OK`.</span><span class="sxs-lookup"><span data-stu-id="2464f-127">Then click `OK`.</span></span>
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. <span data-ttu-id="2464f-129">Klicken Sie auf die `Select a trace scenario` Dropdownliste, und wählen Sie `Local Network Interfaces`.</span><span class="sxs-lookup"><span data-stu-id="2464f-129">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. <span data-ttu-id="2464f-131">Klicken Sie auf die `Start` Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="2464f-131">Click the `Start` button.</span></span>
9. <span data-ttu-id="2464f-132">Starten Sie die Nachrichten durchlaufen die Netzwerkschnittstellen auf Ihrem Gerät anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2464f-132">You should start to see the messages going through the network interfaces on your device.</span></span>
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)
10. <span data-ttu-id="2464f-134">Nach die Ablaufverfolgung über Message Analyzer Start können Sie auch die ETW-Nachrichten aus dem Treiber des Packet Capture in Ihres Geräts anzeigen [Weboberfläche](DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="2464f-134">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="2464f-135">Zu diesem Zweck finden Sie unter der Registerkarte "ETW" die Weboberfläche `Microsoft-Windows-NDIS-PacketCapture` aus der `Registered providers` Dropdown-Menü, und klicken Sie auf die `Enable` Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="2464f-135">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    ![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)    
