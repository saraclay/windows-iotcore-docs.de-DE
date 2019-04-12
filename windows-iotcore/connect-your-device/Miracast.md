---
title: Miracast unter IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: Erfahren Sie, wie Miracast-Funktionen auf Ihrem Gerät auswählen
keywords: Windows Iot, Miracast, Verbindungen
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514117"
---
# <a name="miracast-on-iot-core"></a>Miracast unter IoT Core

In diesem Dokument werden Sie Miracast Funktionen auf Ihrem Gerät IoT Core erläutert.

> [!IMPORTANT]
> Dieses Feature ist nur verfügbar, auf Insider-Build 17093 und höher

## <a name="miracast-overview"></a>Miracast-Übersicht

Eine Miracast-Verbindung besteht aus zwei Komponenten: die Quelle und Senke. Die **Miracast-Quelle** sendet den Inhalt, der **Miracast-Senke**, wird angezeigt, die den Inhalt. Um die Verbindung zu erstellen, kündigt die Senke selbst mit dem verbundenen Wi-Fi-Netzwerk. Die Quelle verwendet die **Gerät Auswahl** , wählen Sie die Senke, und fordern Sie eine Verbindung. Nachdem die Verbindung angefordert wird, erhält ein Benutzer auf die Senke eine Warnung, dass die Quelle versucht, eine Verbindung herstellen und muss sicherstellen, dass die Verbindung ausgeführt werden soll. Wenn dies passiert, beginnt die Quelle Umwandlung in die Senke, bis entweder die Quelle bricht die Verbindung ab oder die Senke beendet die Werbung.

## <a name="hardware-requirements"></a>Hardwareanforderungen

Sowohl Quell-als auch Senke-Geräte erfordern Miracast-kompatiblen Wi-Fi "und" Grafiktreiber und Chipsätzen ordnungsgemäß funktioniert. Um herauszufinden, ob Ihr Gerät mit Miracast kompatible Hardware hat, führen Sie Folgendes aus: 
```
netsh wlan show driver
```
das Gerät die Eingabeaufforderung.

Wenn das Gerät Miracast unterstützt, sollte die folgende Ausgabe angezeigt werden:

![Kompatibles Gerät-Ausgabe](../media/Miracast/CompatibleDevice.png)

Die folgende Tabelle zeigt Miracast-Kompatibilität für die IoT Core Verweis Plattformen:

| Board | SoC | WiFi-Treiber vorhanden. | Grafiktreiber vorhanden. | Miracast-Compatible |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410c | Snapdragon 410 | Ja | Ja | Ja |
| Raspberry Pi 2/3 | Broadcom BCM283x | Ja | Nein | Nein |
| Minnowboard Max | Intel Atom E3825 | Ja | Nein | Nein |
| BIS Quadrat | Intel Celeron N3350 | Ja | Ja | Ja |


### <a name="wi-fi"></a>WLAN

Wi-Fi-Treiber und -Chipsatz, für das Gerät müssen neben anderen Funktionen zur Unterstützung von Miracast Wi-Fi Direct, unterstützen. Wenn Ihr Gerät nicht über diese Features verfügt, können Sie stattdessen einen USB-WLAN-Dongle. Wir empfehlen die [300 M drahtlose USB-Adapter](http://a.co/fdhEhV9).

### <a name="graphics"></a>Grafiken

Der Grafiktreiber und Chipset müssen h. 264 codieren und Decodieren von Miracast-Unterstützung unterstützen. Wenn Ihr Gerät nicht über eine kompatible Treiber und/oder Chipsatz verfügt, müssen Sie ein neues Gerät auszuwählen. Wenden Sie die oben genannten Matrix, bei der Auswahl eines Geräts Miracast kompatible.

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT als Senke Miracast

Um Ihr Gerät als Senke Miracast zu aktivieren, müssen Sie die app "Verbinden" auf Ihrem Gerät zu aktivieren, und Miracast in der Registrierung zu aktivieren.

### <a name="enable-the-connect-app"></a>Aktivieren Sie das Verbinden der App

Um die app "Verbinden" zu aktivieren, müssen Sie enthalten die **IOT_MIRACAST_RX_APP** Feature zu Ihrem Image. Sie müssen außerdem umfassen **Microsoft-Connect-Package.cab** und **Microsoft Connect Package_Lang_XXXX.cab** in Ihrem Image (XXXX steht für eine Sprache, d. h. "EnUS"). 

Finden Sie unter [auf dieser Seite](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) für Weitere Informationen zur Vorgehensweise beim Hinzufügen von Funktionen und Pakete zu Ihrem Image. Sie können auch sideloading das Paket und die Funktionen zu bestehenden Images anhand [diese Anweisungen](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage). Bedenken Sie, die dieses Feature sideloading von Empfang von Updates verhindert wird.


### <a name="enable-miracast"></a>Miracast aktivieren

Herstellen einer Verbindung Ihres Geräts über mit [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) oder [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) , und führen Sie die folgenden Befehle aus:
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
Dadurch können Miracast ohne eine zustimmungsbenachrichtigung, nur in sicheren Netzwerken, und nur an die Stromversorgung angeschlossen. Dies ist die empfohlene Methode zum Empfänger Miracast unter IoT Core ausgeführt wird.

## <a name="windows-iot-as-a-miracast-source"></a>Windows IoT als Quelle Miracast

> [!IMPORTANT]
> Vor dem Versuch, Ihr Gerät als Quelle Miracast verwenden, deaktivieren Sie die app IoTOnboardingTask aus der [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) wie unten gezeigt das müssen Sie nur einmal ausgeführt werden: ![Deaktivieren Sie IoTOnboardingTask-app](../media/Miracast/IoTOnboardingOff.gif)
>
> Anschließend können Sie Neustarten des Geräts

Sie können Miracast-Umwandlung einrichten, auf Ihrem Gerät über öffentliche APIs aus der `Windows.Media.Casting` Namespace in Ihrer app.

Um diese APIs in Aktion zu sehen, laden die [BasicMediaCasting UWP Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) und führen Sie es auf Ihrem Gerät. Die APIs im Beispiel behandelt die folgenden Szenarien, die auf Geräten mit Miracast kompatible IoT Core ausgeführt werden:
1. Grundlegende Media-Umwandlung, die die integrierte Umwandlung verwendet wird, um Inhalt an Miracast, DLNA und Bluetooth-Geräte senden.
2. Umwandlung, die über die Auswahl umwandeln, in dem Sie die Auswahl des Geräts weiter anpassen können
3. Über eine benutzerdefinierte Auswahl umwandeln, wird veranschaulicht, die wie benutzerdefinierte Benutzeroberfläche erstellen, für die Auswahl von Geräten

> [!NOTE]
> Einige Miracast senken (Surface Laptop, Surface Hub-PC mit einem Wireless-Anzeige-Adapter) sind nicht kompatibel mit IoT Core Umwandlung Geräten. Es wird empfohlen, die [Microsoft Wireless-Grafikkarte](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) mit einem kompatiblen Monitor als Ihre Miracast-Senke.
