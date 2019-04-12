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
# <a name="remote-display"></a>Remote-Anzeige
Zeigen Sie an und steuern Sie Ihre Windows 10 IoT Core UWP-Anwendungen Remote von einem Windows 10-desktop-PC, Tablet oder Telefon

> [!WARNING]
> Windows IoT-Remote-Client ist eine Entwickler-nur-Funktion. Es ist nicht vorgesehen, oder für Produktionsgeräte unterstützt.

> [!IMPORTANT]
> Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi. Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.

## <a name="overview"></a>Übersicht
___
Die remote-Anzeige-Erfahrung ist ein Tool für Entwickler verwendet, um Remote auf einem Gerät Windows 10 IoT Core ausgeführten UWP-Anwendungen zu steuern.   

## <a name="setup"></a>Setup
___
Informationen zum Einstieg müssen Sie zum Einrichten eines Windows 10 IoT Core-Geräts mit dem neuesten Build von Windows 10 – besuchen die [Einstieg](https://developer.microsoft.com/en-us/windows/iot/getstarted) Seite, um das Board einzurichten.

Setup kann schnell und einfach – führen Sie die drei Schritte unten aus, um die Anzeige der remote-Technologie verwenden.

1. Sicherstellen Sie, dass Ihrem IoT Core Geräte- und entwicklungssicherheit Computer auf dem gleichen Netzwerk und n einer sicheren Umgebung.

    Eine Methode ist zum Verbinden Ihres Geräts direkt mit Ihrem Laptop, der mit einem USB-Ethernet-Adapter für der automatische Crossover unterstützt.

1. Aktivieren Sie die remote-Anzeige-Funktionalität auf Ihrem Windows 10 IoT Core-Gerät.
  
    Verbinden Ihres Geräts mit dem Internet, und Verbinden mit Windows Device Portal.
  
    Wählen Sie die Seite "Remote" aus den Optionen auf der linken Seite, und markieren Sie das Kontrollkästchen "Aktivieren Sie im Fenster IoT-Remoteserver".  Ihr Gerät ist jetzt für remote anzeigen aktiviert.
    ![Aktivieren Sie remote anzeigen](../media/RemoteDisplay/enable-remote.png)

1. Installieren der Windows IoT-Remote-Client auf Ihrem begleitende Windows 10-Gerät.
  
    Um Windows 10-Gerät für die Verbindung mit Ihrem Windows 10 IoT Core-Gerät zu aktivieren, müssen Sie die Store-Anwendung zu installieren.  Die Windows IoT-Remote-Client-app ist durch Link nur verfügbar, und finden Sie [hier](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).
    
    ![Installieren von Client-app](../media/RemoteDisplay/store-app.png)


1. Verbinden Sie mit Ihrem Windows 10 IoT Core-Gerät über die installierte Anwendung.
  
    Führen Sie die Windows IoT-Remote-Client-Anwendung auf Ihrem Windows 10-Gerät Companion.  Geben Sie die IP-Adresse Ihres Geräts, auf dem Bildschirm "Verbinden". Die beiden Geräte eine Verbindung herstellen soll, Remoting die Benutzeroberfläche des Windows 10 IoT Core-Geräts auf das begleitgerät.
    
    Sie sind nun verbunden. An diesem Punkt weiterleiten, touch, und klicken Sie auf Eingabe auf der Begleit-Windows 10-Gerät verwendet werden kann, um die Windows 10 IoT Core UWP-Anwendung zu steuern.  
    ![Gerät verbinden](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>Kompatibilität und Bereich
___
Damit der IoT-Remote-Client verwenden zu können, müssen Sie den neuesten Build von Windows 10 IoT Core auf dem Zielgerät und die aktuelle Clientanwendung aus dem Store ausgeführt werden. 
    
  
## <a name="troubleshooting"></a>Problembehandlung
___
Mithilfe der remote-Anzeige-Technologie ist schnell und einfach, aber es gibt noch einige Probleme, die Benutzer auftreten können.  Stellen Sie sicher, dass das Setup führen die obigen Anweisungen unten eng - Wenn weiterhin Probleme auftreten, überprüfen.

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>Wenn ich versuche, eine Verbindung herstellen, wird die Client-app, um einen weißen Bildschirm.
Verbindungsfehler können durch eine Reihe von Problemen verursacht werden, aber wir haben ein paar weitere häufige Probleme auftreten:

1. Stellen Sie sicher, dass Sie den neuesten Insider-Version von Windows 10 IoT Core und die IoT-Remote-Client-Anwendung ausgeführt werden.
1. Stellen Sie zunächst sicher, dass Ihre IoT-Geräte auf dem gleichen Netzwerk wie Ihr begleitgerät ist.
    Überprüfen Sie, dass Sie mit dem IoT-Remoteserver Windows aktiviert den neuesten Insider-Build von Windows 10 IoT Core ausgeführt werden.
1. Wenn dies nicht das Problem ist, versuchen Sie es ändern, die Auflösung von Ihrem Gerät, um etwas, das wir zur Unterstützung garantiert sind befolgen Sie die Anweisungen in Schritt 1 von den Setup-Abschnitt oben zum Navigieren auf Webserver Ihres Geräts.  Bleiben Sie auf der Seite "Home" anstelle von "Remote" im Menü auf der linken Seite, und scrollen Sie nach unten, um Lösung zu finden.  Versuchen Sie es 800 x 600.
1. Wenn dies noch nicht zu Ihrem Problem beheben, müssen Sie möglicherweise ein Problem, das ist, verbinden Ihr Gerät nicht an einen externen Monitor.
    Dadurch wird das Gerät selbst als rein monitorlose vorstellen.  So beheben Sie dieses Problem
    * Werfen Sie die MicroSD-Karte, und fügen Sie in Ihrem computer
    * Bearbeiten Sie die `<MicroSD card drive>:\config.txt`
    * Fügen Sie die folgenden Zeilen hinzu:
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
