---
title: Verwalten Sie die Windows-Geräte mit Azure IoT Hub
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Erfahren Sie, wie Sie Ihre Windows-Geräte mit Azure IoT Hub verwalten.
keywords: Windows Iot, Azure, DM, geräteverwaltung, Azure IoT Hub, Iothub, Integrität für Geräte
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513154"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a>Verwalten Sie die Windows-Geräte mit Azure IoT Hub

## <a name="overview"></a>Übersicht
Geräteverwaltung (DM) ermöglicht den Operatoren, Remote zu konfigurieren und gleichzeitig sehr großen Mengen von IoT-Geräten zu überwachen.

Konfiguration für die Geräte kann auf Geräten per Push übertragen werden, ob die Zielgeräte online oder offline sind. Wenn das Gerät offline ist übernehmen es die neue Konfiguration die beim erneuten Herstellen der Verbindung. Gerät-Operatoren können auch abrufen, den Status eines jeden Geräts, z. B., ob Updates für die Konfiguration von Geräten erfolgreich oder nicht angewendet wurden.

Aktivieren diese Funktionen für IoT-Geräte erfordert eine Central, robust, und zuverlässigen Mechanismus zum Speichern die Konfigurationsdaten bereitstellen, die Zielgeräte und Gerätestatus überwachen – nach Maß.

Eine vollständige Lösung benötigen Sie Folgendes:

* Zuverlässig/skalierbare Cloud-Dienst in die gewünschten und gemeldeten Status der verschiedenen Geräte zu speichern.
  * Azure IoT Hub und Azure-Geräteverwaltung bieten einen hochgradig skalierbaren und effizienten Cloud-Dienst für die Verwaltung von Millionen von Geräten.

* Ein Client, der auf dem Gerät ausgeführt wird und anwenden die gewünschte Konfiguration und kann den Status des Geräts zu melden.
  * Die Windows IoT Azure DM-Client (eine Open-source-SDK und Runtime) in Verbindung mit Azure IoT Hub-Instanz, anwenden und melden kann einen großen Satz allgemeiner, manchmal kritisch, Windows-Konfigurationen.

* Ein Portal oder eine Anwendung, die durch den Operator zum Konfigurieren und Abfragen der Geräte per Remotezugriff verwendet werden.
  * Dies muss für Geräte, die vom Gerät OEM oder Operator angepasst werden. Als Teil dieser Lösung wir außerdem Geben Sie ein open-Source-Datenmodell und Beispiel-Implementierung für die einfachere Interaktion mit der IoT Hub-Speicher und der Windows-IoT-Client.

Weitere Informationen zur geräteverwaltung für Windows-Geräte finden Sie auf der Hauptseite [Geräteverwaltungsclient Repository](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).
