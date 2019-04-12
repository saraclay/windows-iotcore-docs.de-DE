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
# <a name="network-packet-capture"></a>Erfassung von Netzwerkpaketen

Sie können [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) zum Erfassen, anzeigen und Analysieren der Protokoll-Datenverkehr auf Ihrem Windows 10 IoT Core-Gerät-messaging.

![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>Vorraussetzungen

Verwenden von PowerShell-Verbindung (Schritt 1 bis 8 finden Sie unter [PowerShell](../connect-your-device/PowerShell.md).

## <a name="set-up-your-device"></a>Richten Ihres Geräts ein

Um auf Ihr Gerät mithilfe von Message Analyzer eine Verbindung herzustellen, müssen Sie zunächst Ihr Gerät umbenennen.  Dies kann erfolgen über [SSH](../connect-your-device/SSH.md) oder [PowerShell](../connect-your-device/PowerShell.md) mithilfe der `setcomputername` Befehl.

![PowerShell-Rename-Gerät](../media/NetworkPacketCapture/powershell-rename-device.png)

Nachdem Sie Ihr Gerät umbenennen, neu starten des Geräts, um die Änderung zu übernehmen.

## <a name="turn-off-the-firewall"></a>Die Firewall ausschalten

Herstellen einer Verbindung Ihres Geräts mithilfe von PowerShell oder SSH mit ein, und führen Sie den folgenden Befehl zum Deaktivieren der Firewalls.
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>Herstellen einer Verbindung Ihres Geräts mithilfe von Message Analyzer mit

Nun, dass Ihr Gerät haben eingerichtet, lassen Sie uns eine Verbindung mit Microsoft Message Analyzer.

1. Herunterladen der [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).
2. Öffnen Sie die Nachrichtenanalyse.
3. Klicken Sie auf `New Session`.

    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. Klicken Sie im Fenster, das geöffnet wird, auf die `Live Trace` Schaltfläche.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. Klicken Sie auf die `Edit...` Schaltfläche.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. Ersetzen Sie "localhost" durch den Namen Ihres IoT-Geräts ein, und geben Sie den Administratorbenutzernamen und das Kennwort.  Klicken Sie dann auf `OK`.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. Klicken Sie auf die `Select a trace scenario` Dropdownliste, und wählen Sie `Local Network Interfaces`.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. Klicken Sie auf die `Start` Schaltfläche.
9. Starten Sie die Nachrichten durchlaufen die Netzwerkschnittstellen auf Ihrem Gerät anzeigen.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)
10. Nach die Ablaufverfolgung über Message Analyzer Start können Sie auch die ETW-Nachrichten aus dem Treiber des Packet Capture in Ihres Geräts anzeigen [Weboberfläche](DevicePortal.md).  Zu diesem Zweck finden Sie unter der Registerkarte "ETW" die Weboberfläche `Microsoft-Windows-NDIS-PacketCapture` aus der `Registered providers` Dropdown-Menü, und klicken Sie auf die `Enable` Schaltfläche.
    ![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)    
