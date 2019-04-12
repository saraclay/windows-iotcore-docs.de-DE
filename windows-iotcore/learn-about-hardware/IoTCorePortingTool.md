---
title: Windows 10 IoT Core API Porting Tool
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie die Windows 10 IoT Core API Porting Tool zu verwenden, um das Portieren Kosten schätzen.
keywords: Windows Iot, API porting Tool, API-portieren, Binärdateien
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513009"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT Core API Porting Tool

Windows 10 IoT Core unterstützt nur eine Teilmenge der Win32- und .net API-Oberfläche zur Verfügung, auf verschiedene frühere Versionen von Windows. Dieses Tool scannt die Binärdateien und erhalten Sie einen Bericht über die APIs diese Binärdateien verwenden, die nicht zur Verfügung, und geben Sie die Vorschläge für mögliche Ersetzungen. Dies wird sowohl als Hilfe bei der Schätzung der Kosten für einen Port für IoT Core als auch helfen Ihnen dabei.


## <a name="usage"></a>Verwendung

Die Windows 10 IoT Core API Porting Tool finden Sie in der [ms-Iot/Iot-Utilities](https://github.com/ms-iot/iot-utilities) Github-Repository.  Herunterladen der [Repository Zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) und kopieren Sie den IoTAPIPortingTool-Ordner auf Ihrem lokalen Computer.  Open **IoTAPIPortingTool.sln** in Visual Studio 2017 und erstellen Sie das Projekt.  Dadurch wird `IotAPIPortingTool.exe`.

Sie können das Tool verwenden, indem Sie Ausführung `IoTAPIPortingTool.exe <Application path> [-os]`.

*  `<Application path>` EXE-Datei der Anwendung, die für die Portierung Tool verwendet wird

*  `-os` muss angegeben werden, wenn Sie nicht beabsichtigen, die UWP zu verwenden.  Standardmäßig überprüft das Tool die Binärdateien für die Windows-UWP-Plattform.

> [!NOTE] 
> IoTAPIPortingTool.exe muss aus einer Visual Studio Developer-Eingabeaufforderung ausgeführt werden. Sie müssen zu dem Ordner zu navigieren, die die IotAPIPortingTool.exe enthält. 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>Ausgabe

Das Tool generiert eine Datei mit kommagetrennten Werten (Csv) in demselben Ordner, enthält die `IotAPIPortingTool.exe`. Die Datei heißt `IoTAPIPortingTool.csv` (oder `IoTAPIPortingToolOS.csv` - Betriebssystem angegeben ist) und eine Zusammenfassung wird in der Befehlszeile angegeben werden. Öffnen der `.csv` -Datei in Excel zum Analysieren der Ausgabe abgeschlossen.
