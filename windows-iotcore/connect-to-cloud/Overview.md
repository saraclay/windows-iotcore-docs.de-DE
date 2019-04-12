---
title: Übersicht über IoT in der Cloud
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über messaging, Sicherheit und geräteverwaltung, mit der Cloud mithilfe von Azure IoT.
keywords: Windows Iot, Cloud, Azure, Azure IoT Hub, messaging, UWP, universelle Windows-Plattform
ms.openlocfilehash: 4f38a45836e7c474655819988e447137249c2a7f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513562"
---
# <a name="overview-of-iot-on-the-cloud"></a>Übersicht über IoT in der Cloud

Das Internet der Dinge baut auf Cloud computing. Die Möglichkeit, mit der Cloud kommunizieren, und leiten Erkenntnisse aus den Daten ist ein wesentlicher Bestandteil jeder IoT-Projekt.

## <a name="messaging"></a>Messaging

Kommunizieren in der Regel IoT-Geräte mit der Cloud oder in anderen, durch Senden und Empfangen von Nachrichten. Die Nutzlast einer Nachricht, die vom Gerät gesendet werden, in der cloud sind so klein wie ein Wert von einem Sensor und so groß wie eine Videodatei. Eine Cloud, Gerät-Nachricht ist in der Regel einen Befehl, der das Gerät anweisen, eine Aktion auszuführen.


Message-Passing-Kommunikationsmuster Komplexität, die von einfachen unidirektionales messaging, komplexer Protokolle wie Anforderung-Antwort oder transaktional Protokolle wie z. B. das Zweiphasen-Commit bis hin variieren.

## <a name="security"></a>Sicherheit

Sicherheit ist ein wesentlicher Bestandteil des IoT. Für jede Nachricht müssen wir sicherstellen, dass es stammt (oder von empfangen wird) ein vertrauenswürdiges Gerät und nicht manipuliert wird. Die Daten können Informationen enthalten, die verschlüsselt werden müssen.

## <a name="azure-iot-hub"></a>Azure IoT Hub

[Azure IoT-Hub](https://azure.microsoft.com/services/iot-hub/) ist Azure-Clouddienst, bietet zuverlässige und sichere Gerät-zu-Cloud und Cloud-zu-Gerät-messaging, die für Millionen von Geräten skaliert werden kann. Es bietet eine optimierte-Programmiermodell, mit der Sie erste Schritte mit minimalem Aufwand und skalieren Sie Ihre Lösung die Anforderungen zunehmen.

