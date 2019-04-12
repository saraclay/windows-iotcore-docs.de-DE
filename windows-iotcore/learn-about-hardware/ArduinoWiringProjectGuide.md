---
title: Arduino verknüpfen Projektberater
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, bis die Erstellung, Setup und Bereitstellung eines Arduino verknüpfen mithilfe von Windows IoT Core-Projekts.
keywords: Windows Iot, Arduino, Arduino verknüpfen, Lightning Leistung zu erzielen, Visual Studio
ms.openlocfilehash: baa904d1d5f23db15fd1dacd05c749449dc91213
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512873"
---
# <a name="arduino-wiring-project-guide"></a>Arduino verknüpfen Projektberater

Dieses Handbuch führt durch die Erstellung, Setup und Bereitstellung eines Arduino verknüpfen mithilfe von Windows IoT Core-Projekts.

Verknüpfen von Arduino-Projekte die vertrauten, benutzerfreundlichen Arduino verknüpfen-API nutzen mit Windows IoT Lightning DMAP Treiber: ein Treiber, die mithilfe von direkten Speicherzuordnung zu erheblichen [mindestgeschwindigkeiten für die Leistung](../develop-your-app/LightningPerformance.md). Sie können kopieren & einfügen Arduino Skizzen und Bibliotheken in Ihre Projekte IoT Core Arduino verknüpfen und führen Sie sie in der unterstützten IoT Core-Geräte, einschließlich Raspberry Pi2, 3 "und" Minnowboard Max! Finden Sie im Abschnitt zum Entwickeln dieser Seite finden Sie weitere Informationen.

## <a name="install-the-microsoft-iot-templates"></a>Installieren Sie die Microsoft IoT-Vorlagen

Wir haben Visual Studio-Erweiterung bereitgestellt, die automatisch eine Visual Studio-Vorlage für die Projekte Arduino verknüpfen sowie anderen Microsoft IoT-Projekttypen installiert wird. 

- Wechseln Sie zu [Windows IoT Core-Projektvorlagen-Erweiterungsseite](https://go.microsoft.com/fwlink/?linkid=847472) auf die Erweiterung von Visual Studio Gallery herunterladen!
- Die Erweiterung installieren und starten Sie Visual Studio neu, wenn er wurde bereits geöffnet

## <a name="change-the-default-controller-driver"></a>Ändern Sie den Standard-Controller-Treiber

Sie müssen den direkten Speicher zugeordnet Treiber zum Verknüpfen der Arduino-Lösungen zu schreiben, ausgeführt werden. Finden Sie in der [Lightning-Installationshandbuch](../develop-your-app/LightningSetup.md) Anweisungen!

## <a name="develop"></a>Entwicklung
Führen Sie eines der Beispiele "Verknüpfen" auf die [Beispielseite](https://developer.microsoft.com/en-us/windows/iot/samples), oder Erstellen Ihres eigenen Projekts verwenden. Eines der Beispiele, die wir erstellt haben, die geschrieben werden, dass mit Arduino verknüpfen aufgeführt werden wie folgt: [Hauptverkaufsargument (Verknüpfen)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring). Hauptverkaufsargument, das Cononical "Hello World"-Projekt für IoT-Projekte, eignet sich hervorragend für Ihr erstes Projekt zu starten!

### <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
1. Öffnen Sie Visual Studio.

2. Wählen Sie die Datei -> Neu -> Projekt...

3. Das Dialogfeld, das angezeigt wird, zur Auswahl:  
Visual C++ -> Windows -> Windows IoT Core-Anwendung für Windows IoT Core verknüpfen Arduino >.  
(stattdessen scheinen als)  
Visual C++ -> Windows IoT Core-Anwendung für Windows IoT Core verknüpfen Arduino >. 


![App erstellen](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>Portieren

Der Arduino-verknüpfen-API wurde sorgfältig implementiert, um zum Kopieren/Bibliotheken und einen groben Entwurf in einem Projekt verknüpfen Arduino einfügen können. Trotzdem sind vorhanden, in einigen Fällen kleine Änderungen notwendig, die Sie möglicherweise an Ihre Skizzen oder Bibliotheken. Wir erstellten ein einfach zu folgen [Arduino verknüpfen: Portierungsanleitung](ArduinoWiringPortingGuide.md) dieser potenziellen Probleme zu behandeln.

## <a name="build-and-deploy"></a>Erstellen und bereitstellen

- Visual Studio stellen Sie sicher, dass "Remotecomputer" als Bereitstellungsziel ausgewählt ist.
- Stellen Sie außerdem sicher, dass die Architektur festgelegt ist, auf das Board entsprechen, das Sie auf das Projekt ausführen. Für die Raspberry Pi 2- oder 3 für den Minnowboard maximalen, wählen Sie "X86" und wählen Sie "ARM".

![Remotecomputer](../media/ArduinoWiring/wiringapp_remotemachine.png)

- Öffnen Sie die Projektmappeneigenschaften finden Sie im Kontextmenü "Debuggen" in Visual Studio.

![Projektmappeneigenschaften](../media/ArduinoWiring/wiringapp_properties.png)

- Suchen Sie den IP-Adresse oder den Computer den Namen Ihres Geräts aus. Verwenden Sie die Windows 10 IoT Core Dashboard-Anwendung oder verknüpfen Sie Ihr Gerät auf einen Monitor.
- Geben Sie den Namen des Computers (Minwinpc standardmäßig) oder die IP-Adresse des Remotecomputers in das Feld "Computername" an. Wenn Sie Ihr Gerät in einen umbenannt haben, neben "Minwinpc" diesen Namen in das Feld für die Anmeldung verwenden.
- Stellen Sie sicher, dass der Authentican-Typ ist: Universell (unverschlüsseltes Protokoll)

![Projektmappeneigenschaften](../media/ArduinoWiring/wiringapp_properties2.png)

- Drücken Sie F5, um Ihr Projekt auf Ihrem Gerät erstellen und bereitstellen.
