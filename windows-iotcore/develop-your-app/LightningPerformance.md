---
title: Lightning-Leistungstests
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zu Windows IoT Lightning-Funktionalität und ein-/ausschalten Häufigkeit für verschiedene Plattformen und Sprachen.
keywords: Windows Iot "," Lightning-Leistung "," Lightning-Funktionalität, GPIO
ms.openlocfilehash: 65f6732dd945b199902bb7eb4a9e0cc41aac2131
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513586"
---
# <a name="windows-iot-lightning-performance-testing"></a>Extrem Testen der Leistung von Windows IoT

Die GPIO-Leistung wurde getestet, für die Windows IoT Lightning-Funktionalität, die über eine einfache app der GPIO-ein-/ausschalten, [verfügbar](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite). Die Tests wurden durch Umschalten von GPIO 5 zwischen 0 und 1 auf der maximalen Geschwindigkeit ausgeführt. Die Häufigkeit der Umschaltfläche für jeden Fall wurde mit einem Tektronix TPS 2024 Oszilloskop gemessen.

Die folgenden Ergebnisse wurden aus der Analyse abgerufen:

> | Plattform getestet                     | Sprache        | Frequenz     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino-Sketches  | 75.06 kHz     |
> | Windows 10 IoT Core Native Stack    | C#              | 239 kHz       |
> | Windows 10 IoT Core Native Stack    | C++/CX          | 278 kHz       |
> | Windows 10 IoT Core Native Stack    | WinJS           | 34 kHz        |
> | Windows 10 IoT Core Arduino verknüpfen  | Arduino-verknüpfen  | **7.36 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | C#              | **1,76 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | C++/CX          | **Macht 3,78 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | WinJS           | 42 kHz        |

Windows 10 IoT Core-Tests wurden auf einem Raspberry Pi 3 mit Windows 10 IoT Core Insider Preview Build 15026 (Codename Redstone 2) ausgeführt und mithilfe von Microsoft IoT Lightning SDK 1.1.0 erstellt.
