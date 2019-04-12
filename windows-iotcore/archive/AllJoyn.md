---
title: Übersicht über die AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie mehr über AllJoyn, ein gemeinsames Protokoll für IoT-Geräte und wie sie andere Erweiterungen und Features mit Windows IoT ermöglicht.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 6655cf5e8584a9c7046301cda24b10348a704d6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512378"
---
> [!NOTE]
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="alljoyn"></a>AllJoyn

AllJoyn ermöglicht das Internet der Dinge. AllJoyn definiert ein gemeinsames Protokoll für Geräte und Anwendungen erkennen und miteinander kommunizieren, unabhängig von Transport-Technologie, Plattform oder Hersteller.  AllJoyn ist ein open Source-standard hängt von der [AllSeen Alliance](https://allseenalliance.org/), ein Kreuz Branchenkonsortium dedizierte zu ermöglichen die Interoperabilität von Milliarden von Geräten, Diensten und Anwendungen für das Internet der Dinge.

Microsoft kam die Alliance AllSeen 2014 und AllJoyn als Komponente in Windows 10 hinzugefügt. Mit der integrierten [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), Entwickler können sich, dass AllJoyn-fähige Anwendungen zu schreiben, die auf die Windows 10-Geräte einschließlich PCs, Tablets, Smartphones, Xbox sowie Geräte, die mithilfe von Windows IoT Core ausgeführt. Neben der plattformunterstützung für für AllJoyn Microsoft veröffentlicht [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), Visual Studio-Erweiterung, die AllJoyn Entwicklung beschleunigt, indem Sie die codegenerierung mit vorgefertigten Anwendungsvorlagen kombinieren. AllJoyn Studio können Entwickler profitieren von der Leistungsfähigkeit von AllJoyn ohne umständliche Einrichtung und Konfiguration.

Begeistert AllJoyn ein? Sehen Sie sich [dies](AllJoynStudio.md) Blogbeitrag zum Einstieg in AllJoyn auf Windows.


## <a name="developer-resources-and-tools"></a>Ressourcen für Entwickler und Tools

**Gerät-System-Bridge**

AllJoyn [Gerät System Bridge](AllJoynDSB.md) ermöglicht nicht AllJoyn-Geräten für die Interaktion mit dem AllJoyn-Ökosystem mit AllJoyn als einheitliche Sprache.

Features:
* Erstellt virtuelle Geräte für jedes nicht-AllJoyn-Gerät, von dem Adapter verfügbar gemacht werden
* Automatisierte Runtime Generierung der Benutzeroberfläche von Adapter-Gerät
* Unterstützt die LSF, Systemsteuerung Basisdienste, erweiterbar, um weitere Dienste hinzufügen
* Universal app-Vorlagen (C#, C++) für Desktop-UI-Anwendungen und Windows IoT-starttasks
* Als open Source verfügbar

Weitere Informationen finden Sie auf die [Gerät System Bridge Seite](AllJoynDSB.md).


**AllJoyn Studio**

[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) ist eine Erweiterung für Visual Studio entwickelt von Microsoft, über die AllJoyn® Entwicklung beschleunigt die codegenerierung und die WinRT-API mit automatisierten Projektmanagement und vordefinierte Anwendungsvorlagen kombiniert. Sie ermöglicht Entwicklern, profitieren von der Leistungsfähigkeit von AllJoyn ohne umständliche Einrichtung und Konfiguration.

Features:
* Universal app-Vorlagen (C#, JavaScript, C++, Visual Basic)
* Automatisierte Verwaltung und -Projekt die Dienstverweiskonfiguration
* Hinzufügen/Entfernen von Schnittstellen in einer Projektmappe
* Einfacher Zugriff auf die Projekt-Management über das Menü "AllJoyn®"
* Laden von Schnittstellen aus Introspection XML-Dateien
* Ermittlung von Schnittstellen von Herstellern auf die network1

AllJoyn Studio installiert werden kann, über Visual Studio-Tools -> Erweiterungen und Updates... Online -> im Feld "Suche" Typ "AllJoyn" ->

Weitere Details zur Verwendung von AllJoyn Studio stehen [hier](AllJoynStudio.md).

**IoT-Explorer für AllJoyn (AllJoyn-Explorer)**

Das IoT-Explorer für AllJoyn (vormals bekannt als AllJoyn-Explorer) ist eine universelle Windows-Anwendung, für die Interaktion mit AllJoyn Geräten im lokalen NEAR-Netzwerk. Entwickler können Auflisten aller verfügbaren AllJoyn-Geräte, überprüfen die Struktur ihrer Schnittstellen-Objekt, als auch Signale empfangen, festlegen und Abrufen von Eigenschaften und Methoden aufrufen.

* [IoT-Explorer für AllJoyn-Store-App](https://www.microsoft.com/store/apps/9nblggh6gpxl): Dies ist der offizielle app-Speicherort.
* [AllJoyn Explorer 1.0.1.11 (Vorgängerversion)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): Diese ZIP-Datei enthält das AllJoyn Explorer AppX-Paket auf einem Entwicklercomputer quergeladen werden. Dies ist eine frühere Version des IoT-Explorers für AllJoyn-Anwendung.
* [Installationshandbuch für AllJoyn Explorer](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): Diese PDF-Datei enthält die Dokumentation für den AllJoyn Explorer bereitstellen.
* [Dass AllJoyn-Explorer-Benutzerhandbuch](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): Diese PDF-Datei enthält die Dokumentation für die Verwendung der AllJoyn-Explorer.


### <a name="additional-resources"></a>Zusätzliche Ressourcen

* [Mithilfe der AllJoyn-Studio-Erweiterung](AllJoynStudio.md)
* [Dass AllJoyn-Producer und AllJoyn Introspection erstellen](AllJoynProducer.md)
* [Problembehandlung bei AllJoyn mit Windows 10](AllJoynTroubleshooting.md)

**Videos**

* [//build 2015 AllJoyn Technical Session](https://channel9.msdn.com/Events/Build/2015/2-623)
* [WinHEC 2015 AllJoyn technischen Sitzung](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**Proben**

* [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [Dass AllJoyn-Consumer](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [Dass AllJoyn-UWP-Beispielen (MSDN)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**Referenz**

* [Dass AllJoyn-APIs unter Windows 10 (MSDN)](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [Erläutert, dass AllJoyn-Architektur (Allseen Alliance)](https://allseenalliance.org/developers/learn/)
* [Entwicklerressourcen für AllJoyn (Allseen Alliance)](https://allseenalliance.org/developers/develop/)
* [AllJoyn C-API-Referenzhandbuch (Allseen Alliance)](https://allseenalliance.org/docs/api/c/index.html)

