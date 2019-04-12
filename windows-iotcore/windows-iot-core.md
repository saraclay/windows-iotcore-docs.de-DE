---
title: Übersicht über die Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Erfahren Sie, was Windows 10 IoT Core und was Sie damit tun können.
keywords: Windows 10 IoT Core, kompakte monitorlose
ms.openlocfilehash: 1be159b685ffed30effbb2ae8abc80ded8edd879
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512297"
---
# <a name="windows-10-iot-core"></a>Windows 10 IoT Core

## <a name="what-is-windows-10-iot-core"></a>Was ist Windows 10 IoT Core?
Windows 10 IoT Core ist eine Version von Windows 10, die für kleinere Geräte mit oder ohne eine Anzeige, die auf sowohl ARM ausgeführt und X86/X64 Geräte optimiert ist. Die Windows IoT Core-Dokumentation enthält Informationen für eine Verbindung herstellen, verwalten, aktualisieren, sichern Ihre Geräte und vieles mehr. 

## <a name="getting-started"></a>Erste Schritte
Um den ersten Schritten mit Windows 10 IoT Core erstellten eine [Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md) lassen sich schnell mit der Plattform vertraut machen. 

Von dort aus können Sie weiterhin Experimentieren mit der Plattform, indem Sie Ihre eigene Anwendung zu entwickeln oder starten das Erstellen von Plänen, Ihr Gerät auf den Markt zu bringen oder Ihr Gerät kommerziell. Um den ersten Schritten mit commercializing finden Sie unter Bring eines Geräts auf den Abschnitt im Markt der [Artikel mit den ersten Schritten](https://docs.microsoft.com/windows/iot-core/getstarted).

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Unterschiede zwischen Windows 10 Desktop und Windows 10 IoT Core

### <a name="different-features-available-on-desktop-and-iot-core"></a>Verschiedene Funktionen, die auf dem Desktop und IoT Core verfügbar

* Inbox Cortana ist seit Version 1809 (17763) nicht mehr auf Windows 10 IoT Core verfügbar. Wenn Sie einer VCD-Gerät auf den Markt schnell bringen möchten, können Sie Cortana-Unterstützung integrieren, in dem Gerät mit der [Vorschau des Cortana Devices SDK](https://developer.microsoft.com/en-us/cortana/devices).
* Die [FileOpenPicker-API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) wird in Windows 10 IoT Core nicht unterstützt. Um den Zugriff auf lokale Laufwerke oder Wechselmedien können Sie dies in Ihrer eigenen Anwendung implementieren.
* Das Windows 10 IoT Core-Gerät wird gestartet, um die [Standard-app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) anstelle eines Desktops-PCs. Der Zweck dieser Anwendung ist nicht nur für die Sie mit einer benutzerfreundlichen Shell beim ersten Start zu interagieren, sondern auch verwendet werden Geben Sie die [Open Source-Code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) für diese Anwendung, damit Sie diese Funktionen verwenden können, um die Plug & play- Ihre eigenen benutzerdefinierten Anwendungen.

### <a name="differences-in-driver-supported-areas"></a>Unterschiede in Bereichen Driver-Unterstützung

* Windows 10 Desktop-Treiber verfügt über mehr als Windows 10 IoT Core unterstützt werden. Um den gleichen funktionieren Gerät(e) auf Windows 10 IoT Core wie auf Desktop, müssen Sie möglicherweise einen Treiber aus der Quelle für ein Windows 10 IoT Core-Gerät erstellen oder finden eine weitere Möglichkeit, vor allem für ARM-Architektur.
* Es ist kein Out-of-the-Box-Treiber für Libusb für Windows 10 IoT Core (ARM) – Sie müssen von der Quelle zum Ziel der ARM-Architektur zu erstellen.

### <a name="differences-in-available-registry-set"></a>Unterschiede in der Gruppe der verfügbare Registrierungsspeicher

* Auf Desktop besteht die Option auf "Automatisch ausblenden Bildlaufleisten in Windows", die auf off festgelegt sein können. Es wird durch den folgenden Registrierungseintrag gesteuert: 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* Es ist keine solche Registrierung auf Geräten mit Windows 10 IoT Core standardmäßig ein. Sie müssen ein Register "Dynamische Bildlaufleisten" nach Bedarf hinzufügen.
* Zum Ausblenden von Bildlaufleisten automatisch in eine UWP-Anwendung zu aktivieren, können Sie hinzufügen, die "DynamicScrollbars" registrieren, und legen Sie den Wert auf "1" wie folgt:

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* Der Registrierungsschlüssel muss aus dem Standard-Konto festgelegt werden. Wenn das ScrollViewer-Elements XAML-Einstellung auf "Visible" ist, erzwingt die nDer registrierungseinstellung 0 die Bildlaufleiste Regardlss, der angibt, ob angezeigt werden Inhalt vorhanden ist ausreichend, haben den Bildlauf in der Benutzeroberfläche angezeigt werden. Eine registrierungseinstellung 1 bleibt die Bildlaufleiste ausgeblendet, bis genügend Inhalt vorhanden ist.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* Schließlich ist die ScrollViewer XAMLs Einstellung "Auto" zeigt klicken Sie dann die registrierungseinstellung 0 die vollständige Bildlaufleiste nur wenn genügend Inhalte die Bildlaufleiste angezeigt. Wenn die Einstellung der Registrierung 1 ist, wird die Bildlaufleiste angezeigt, und klicken Sie dann bei genügend Inhalte oder ausgeblendet, wenn kein Inhalt vorhanden ist.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>Andere unterstützte Befehle

* Der Remove-AppxPackage des PowerShell-Befehl funktioniert auf tritt jedoch nicht auf Windows 10 IoT Core.
* Nicht alle Ordner auf Ihrem Gerät sind universelle Windows-Apps zugreifen können. Auf Windows 10 IoT Core können Sie die FolderPermissions-Tool verwenden, um einen Ordner in einer UWP-app zugänglich zu machen. Führen Sie z. B. FolderPermissions c:\test -e, um UWP-apps den Zugriff auf Ordner "c:\test" ein. Dies ist jedoch nicht auf den Desktop verfügbar.

Alle Unterschiede, die in diesem Beitrag beschriebenen gültig in der Zukunft möglicherweise nicht, da Windows 10 IoT Core ständig aktualisiert wird.

## <a name="helpful-resources"></a>Hilfreiche Ressourcen
[Lesen Sie unsere Dokumentation](https://docs.microsoft.com/windows/iot-core/) Weitere Informationen zu Windows 10 IoT Core.
