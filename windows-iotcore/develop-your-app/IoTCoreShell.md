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
# <a name="iot-shell-overview"></a>Übersicht über IoT-Shell

In diesem Dokument wird beschrieben, die IoT-Shell Vordergrund und Hintergrund-Anwendungen und zum Navigieren zwischen diesen Anwendungen auf Ihrem Gerät.

## <a name="iot-shell-foreground-and-background-apps"></a>IoT-Shell, Vordergrund und Hintergrund-Apps

Ihr Gerät IoT Core ausgeführt wird, die IoT-Shell. Er hat viele Aufgaben, aber die primäre Aufgabe besteht darin, sicherzustellen, dass apps für registrierte beim Start gestartet werden. Es verfügt über zwei Modi: Multi-Monitor "und" monitorlose ". Im Modus "Headed" wird die IoT-Shell zu eine einzelnen registrierten Start-app starten, die anzeigt, die Benutzeroberfläche im Vollbildmodus (auch bekannt als eine Headed-app). Modus wird angenommen, Sie einen Bildschirm verbunden haben und zeigt die Benutzeroberfläche. Im monitorlosen Modus (ausführlich [hier](../learn-about-hardware/HeadlessMode.md)), wird keine Benutzeroberfläche angezeigt, die IoT-Shell startet nur die hintergrundanwendungen.

Hier sind die Hauptunterschiede zwischen Vordergrund-und hintergrundanwendungen:

- **Vordergrundanwendungen** eine Benutzeroberfläche haben. Eine davon wird beim Start gestartet, wenn das Gerät im Modus befindet. Alle Foreground-apps werden auf dem Gerät registriert, und der Benutzer zwischen Vordergrund-apps während der Gerätevorgang wechseln kann.

- **Anwendungen im Hintergrund** keine Benutzeroberfläche aufweisen, und sparen somit Geräteressourcen durch Deaktivieren des UI-Stapels. Programme im Hintergrund wird häufig aus der Startdatei kontinuierlich ausgeführt und werden häufig verwendet, um das Gerät zu überwachen.

## <a name="switching-between-apps-with-a-home-app"></a>Wechseln zwischen apps mit einer Home-App

Im Moment ermöglicht die Start-App Ihnen die Erstellung eine home-app für Windows 10 IoT Core, dem Sie zwischen verschiedenen vordergrundanwendungen wechseln können. 

Die **IoT-Start-App** ([Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp) eine simple-starttasks-app, die Listet die installierten apps auf Ihrem Gerät, und startet eine mithilfe der PackageManager-APIs darstellt.

## <a name="switching-between-apps-with-hid-injection-keys"></a>Wechseln zwischen apps mit HID-Injection-Schlüsseln

Die folgenden Anweisungen zeigen, wie Sie Hotkey-Unterstützung durch Einträge in der Registrierung zu aktivieren. Wenn Sie Ihr eigenes Image Erstellen und unterstützen möchten die folgenden Tastaturbefehle ("Home", "Vorherige app, und" nächste app ") ohne die Registrierung zugreifen, können Sie ein optionales Feature-Paket, das diese Schritte für Sie verarbeitet einschließen.

Wird aufgerufen, die zu suchende Featurepaket: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** und das Feature heißt **IOT_SHELL_HOTKEY_SUPPORT**. Finden Sie unter den [Settings.HotKey-Beispielpaket](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) verdeutlicht.

Der Rest dieses Dokuments wird beschrieben, wie diese Funktion manuell zu implementieren.

### <a name="return-home"></a>Return-Startseite

Unterstützt der IoT-Shell mit dem Windows 10 IoT Anniversary Update (1607) das Standardfenster für die Anwendung in den Vordergrund bringen, wenn eine andere Anwendung ausgeführt wird, mit der Taste "GO HOME", die auf die Version der Windows-Schaltfläche auf einer Standardtastatur festgelegt wird. Wenn Sie eine Tastatur auf Ihrem IoT-Gerät besitzen, und Tastaturereignisse auf niedriger Ebene, durch einfügen müssen [HID-Injektion](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), oder wenn Sie nur die Funktionen "GO HOME" zu einem anderen Schlüssel in Ihrer app neu zuordnen möchten, können Sie anpassen, dass den Schlüsselwert in der die Registrierung. Z. B. um aktivieren Drücken der ESC-Taste (0x1B) Geben Sie auf "GO HOME" den folgenden Befehl in der Registrierung:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

Als REG-Datei sieht dies wie folgt aus:

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>Wechseln zwischen Apps

Auch wenn Sie zwischen die Vordergrund-apps wechseln möchten, Sie können einrichten Alt + Tab (nächste app) und Umschalt-Alt-Tab (vorherige app) Funktionen in Ihrem Image mithilfe des folgenden Befehls in der Registrierung:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

Als REG-Datei sieht dies wie folgt aus:
``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>Bit-Verschiebung

Die oben genannten REG-Dateieinträge Decodieren von links nach rechts, wie folgt:

- Bits 0 bis 15: Virtueller Tastencode (d. h. 1 b, 00 für ESCAPEZEICHEN). Finden Sie unter [virtueller Tastencode](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) für die vollständige Liste der Werte für Schlüssel
- Bits 16.-19.: Losgelassene Zusatztaste. 0 x 0 = kein Modifizierer, 0 x 1 = ALT, 0 x 2 = STRG, und 0 x 4 = UMSCHALTTASTE. Kombinieren von Schlüsseln addiert die Werte (d. h., ALT + UMSCHALT ist 0 x 5)
- Bits 20: 47: Für die zukünftige Verwendung reserviert. 0 muss sein.
- Bits 48-62:  Aktion
    - 0 = home
    - 1 = die vorherige Ansicht (funktioniert möglicherweise nicht in zukünftigen Versionen)
    - 2 = nächste Ansicht (funktioniert möglicherweise nicht in zukünftigen Versionen)
- Bit 63: Reserviert. 0 muss sein.

