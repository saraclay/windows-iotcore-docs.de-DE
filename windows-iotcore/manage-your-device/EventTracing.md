---
title: Ereignisablaufverfolgung für Windows IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Ereignisse schreiben und Verarbeiten von Ereignissen für die Windows IoT Core mit Event Tracing.
keywords: Windows Iot, Ereignis-Ablaufverfolgung, ETW-ereignisablaufverfolgung für Windows Geräte
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514053"
---
# <a name="event-tracing-for-windows-iot-core"></a>Ereignisablaufverfolgung für Windows IoT Core

Event Tracing for Windows (ETW) bietet Entwicklern die Möglichkeit zum Starten und Beenden von ereignisablaufverfolgungs-Sitzungen, Instrumentieren einer Anwendung Ablaufverfolgungsereignisse bereitstellen und Nutzen von Ablaufverfolgungsereignissen.
ETW auf Geräten mit Windows IoT Core unterstützt sowohl die Manifest-basiertes als auch die klassischen Ereignisse und funktioniert genauso wie andere Windows 10-Geräte.

In diesem Abschnitt bieten hilfreiche Links zu den Grundlagen des Schreibens und Nutzen von Ereignissen. Finden Sie weitere ausführliche Informationen über die [Seite Windows-Ereignisablaufverfolgung](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).

## <a name="writing-events"></a>Schreiben von Ereignissen

Suchen eine UWP Beispieldaten, die implementiert, die verschiedenen Methoden zum Schreiben von Ereignissen im Rahmen der [Windows Universal-Samples-Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).
Dies wird auf Geräten mit Windows IoT Core ausgeführt und ist auch ein Verweis von großartigem Code.

Ausführliche Anleitung zum Schreiben von Ereignissen und das Abrufen der GUIDs finden Sie [hier](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).

## <a name="consuming-events"></a>Nutzen von Ereignissen

Ereignisse werden entweder in einer ETL-Datei gespeichert oder in Echtzeit erfasst.
Verwendung [FTP](../connect-your-device/FTP.md) oder [Windows-Dateifreigabe](../manage-your-device/WindowsFileSharing.md) , ETL-Dateien von Windows IoT Core-Geräten abzurufen.

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>Verwenden der Tools im Windows Assessment and Deployment Kit

Windows Assessment and Deployment Kit enthält 3 Tools zum Erfassen und Analysieren von Ereignissen. [Zum Herunterladen hier klicken](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. **Windows Performance Analyzer** visualisiert die ETL-Dateien auf dem Desktop mit einer Schritt-für-Schritt-Anleitung [hier](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).

2. **Xperf-Befehlszeilentool** Ereignisse in Echtzeit erfasst und schreibt sie in einer ETL-Datei. Dieses Tool ist bereits auf Windows IoT Core-Geräte, führen Sie einfach die folgenden Befehle auf den Geräten installiert werden:

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Befehlszeilenprogramm Tracerpt** ETL-Dateien in XML-Dateien konvertiert.

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>Gerät mithilfe des Portals

Device-Portal kann Erfassen von Ereignissen in Echtzeit mit Anweisungen [hier](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).

> [!NOTE]
> Diese Methode führt nicht zu einer ETL-Datei zur weiteren Analyse, erfordert jedoch nur ein kleines Setup.

## <a name="use-function-calls"></a>Verwenden Sie die Funktionsaufrufe

Aktivieren einer Anwendung zur Verarbeitung von Ereignissen aus einer ETL-Datei oder in Echtzeit mithilfe von Funktionsaufrufen.
Erfahren Sie, wie Sie diese Funktionen verwenden [hier](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).
