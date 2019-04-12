---
title: Übersicht über die AllJoyn-Gerät-System-Bridge
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, bis der AllJoyn Gerät System Bridge, die nicht AllJoyn-Geräte für das Ökosystem AllJoyn für eine umfassendere Interoperabilität passt.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512466"
---
> [!NOTE]
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="alljoyn-device-system-bridge"></a>AllJoyn Device System Bridge

AllJoyn bietet Entwicklern die Flexibilität, die eine Vielzahl von Plattformen und Technologien für Verbindung verwenden, um Geräte für das AllJoyn-Ökosystem zu erstellen.  Allerdings haben viele Gerätehersteller vorhandene Lösungen für die Geräte in ihren Portfolios an. In diesen Situationen hat Microsoft das Gerät (SBG System Bridge, angenommene). SBG angenommene passt nicht AllJoyn-Geräte, auf das Ökosystem AllJoyn, damit die angepasste Geräte mit AllJoyn als einheitliche Sprache interagieren können. Microsoft DSB Unterstützung Automation-Systeme, z. B. Zigbee und Z-Wave home und unterstützen sogar industriellen automatisierungssystemen wie z. B. BACnet erstellen können.  Darüber hinaus ist der Quellcode für die Anpassung zur Unterstützung von anderen Technologies zur Verfügung.

## <a name="how-dsb-works"></a>Funktionsweise von SBG angenommene

Die entscheidendes Merkmal von einem SBG angenommene ist die Erstellung eine virtuelle Repräsentation der Geräte auf dem Bus AllJoyn. Also diese Geräte, was auch immer ihre systemeigene Verbindung oder ein Gerät-Ökosystem ist, wird angezeigt und als AllJoyn Geräte zugegriffen werden. In der Abbildung unten zwei DSBs ist eine für die Z-Wave und eine für ZigBee virtuelle Darstellung der zwei Z-Wave und eine ZigBee Geräte auf dem Bus AllJoyn erstellen. Mit diesem alle Geräte auf die AllJoyn kann Standort miteinander kommunizieren. Da die Z-Wave und ZigBee-Geräte, auf dem Bus AllJoyn sie jetzt auch kommunizieren können.

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

Eine andere Schlüsselelement des Entwurfs SBG angenommene ist, dass keine Änderungen am AllJoyn oder nicht-AllJoyn-Gerät-System erforderlich ist. Alle erforderlichen uneinheitlich erfolgen in SBG angenommene.

Wie auch der Abbildung wird verdeutlicht, besteht keine Zuordnung von AllJoyn-Geräten auf die Seite nicht AllJoyn. Das Ziel SBG angenommene werden Geräte, die in das Ökosystem AllJoyn zu bringen. Aktivieren die einzige Möglichkeit, vereinfacht die Entwicklung. Sie verringert auch das Risiko, dass AllJoyn Sicherheitsfunktionen, die vom System Gerät potenziell unsicherer nicht AllJoyn abgeschwächt werden.

## <a name="dsb-architecture"></a>SBG angenommene-Architektur

Microsoft vorgeschlagen, dass SBG angenommene Architektur besteht aus drei Hauptkomponenten: den Access-Netzwerkstapel, Adapter und Bridge. Die folgende Abbildung zeigt den allgemeinen Überblick über diese Architektur.

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>Bridge
* Stellt jedes interne Geräte-Objekt dar, als dass AllJoyn-Gerät, separate Bus Anlage für jedes Gerät
* Geräte werden dynamisch hinzugefügt oder aus dem Bus AllJoyn entfernt
* Konfiguration verwaltet Geräte Sichtbarkeit und Sicherheit
* Bus-Anlage für die Brücke und der Adapter eine Konfigurationsschnittstelle erstellt
* Bridge-Code ist unabhängig von der internen Gerätetypen und wiederverwendbaren für jeden Typ

### <a name="adapter"></a>Adapter
* Instanziiert und verwaltet virtuelle Geräte für jedes Gerät über das Netzwerk nicht AllJoyn
* Gerät Schemas werden in internen Geräteobjekte übersetzt.
* Verwaltet von Netzwerkressourcen, z. B. speicherzugriffsschlüssel zu Anmeldeinformationen

### <a name="network-access-stack"></a>Access-Netzwerkstapel
* Zugriff auf AllJoyn Netzwerklaufwerke spezifisch ist, z. B. die Z-Wave-stack

## <a name="adapter-classes"></a>Adapterklassen

Das folgende Diagramm zeigen die Klassen, die Entwickler verwenden, werden in der Microsoft DSB-Vorlage, um eine Abstraktion der systemeigenen Geräte zu erstellen, die in AllJoyn überbrückt werden müssen. Die Bridge wird die Instanz der Adapterklasse verwenden, um die Bus-Anlagen für jedes Gerät in der Liste Adapter.devices erstellen zu können.
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>Spezielle Handler

AllJoyn gibt mehrere Basisdienste zur Verfügung und Standardschnittstellen-Frameworks wie z. B. LSF, HAE oder die Systemsteuerung. SBG angenommene können mit bestimmten Handler verfügbar macht. Die aktuelle Version der Vorlage SBG angenommene enthält Implementierungen der Schnittstellen LSF und Systemsteuerung. Entwickler werden ihren Code an die Rückruffunktionen für LSF und Systemsteuerung Schnittstellen in der Bridge verbunden werden.

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>SBG angenommene-Ressourcen

### <a name="visual-studio-dsb-template"></a>Visual Studio SBG angenommene-Vorlage

Visual Studio SBG angenommene-Vorlage ist eine Erweiterung für Visual Studio, die Sie ganz einfach neue SBG angenommene-Projekte erstellen können. Das Projekt erstellt alle erforderlichen Komponenten wie z. B. der Bridge, eine Shell-Projekt für den Adapter und alle Projektmappendateien SBG angenommene als Spitzen oder monitorlose Gerät zu erstellen. Diese Visual Studio-Erweiterung enthält sowohl die Native und verwaltete AllJoyn Gerät System Bridge-Vorlagen.

SBG angenommene-Vorlage in diesen Speicherorten herunterladen:

* [SBG angenommene-Vorlage für Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* [SBG angenommene-Vorlage für Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_SBG angenommene Vorlage kann auch installiert werden, über Visual Studio-Tools-Erweiterungen und Updates... > Online -> im Feld "Suche" Typ "SBG angenommene" ->._

Die [AllJoyn SBG angenommene Objekte zuordnen](AlljoynDsbApiGuide.md) Dokument beschreibt die wichtige Schnittstellen und Methoden verwendet, um die Alljoyn-System-Brücke zu erstellen.

### <a name="sample-dsbs"></a>Beispiel-DSBs

* [AllJoyn SBG angenommene Mock Adapter Tutorials und Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * Dieses Tutorial veranschaulicht, wie die Geräte-System-Brücken-app zu verwenden, um Ihre Geräte IoT Core zum Modellieren BACnet Geräte verbinden.
* [AllJoyn SBG angenommene Z-Wave Adapter Tutorials und Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * Dieses Tutorial veranschaulicht, wie die Geräte-System-Brücken-app zu verwenden, um Ihre IoT-Core-Geräte mit Z-Wave-Geräte verbinden.
* [AllJoyn DSB GPIO Adapter Tutorial C++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * In diesem Tutorial wird veranschaulicht, wie die AllJoyn Gerät System Bridge-Vorlage verwenden, erstellen Sie ein Beispiel für C++ app, die das Gerät GPIO ausführt.
* [AllJoyn SBG angenommene GPIO-Adapter-TutorialC#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * In diesem Tutorial wird veranschaulicht, wie die AllJoyn Gerät System Bridge-Vorlage verwenden, um verwaltete Beispiel-app zu erstellen, die das Gerät GPIO ausführt wird.
* [AllJoyn SBG angenommene ZigBee Adapter Tutorials und Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * Dieses Tutorial veranschaulicht, wie die Geräte-System-Brücken-app zu verwenden, um Ihre IoT-Core-Geräte mit ZigBee Geräte verbinden.
* [AllJoyn SBG angenommene BACnet Adapter Tutorials und Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * Dieses Tutorial veranschaulicht, wie die Geräte-System-Brücken-app zu verwenden, um Ihre IoT-Core-Geräte mit BACnet Geräte verbinden.
* [AllJoyn.JS Tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * In diesem Tutorial veranschaulicht die anwendungsausführung AllJoyn.JS von Allseen Alliance als Windows 10-Anwendung entwickelt wurde. AllJoyn.JS können Sie zum Schreiben von JavaScript zum Erstellen, überwachen und kontrollieren, dass AllJoyn-Geräte.
* [AllJoyn SBG angenommene OIC Adapter Tutorials und Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * Dieses Tutorial veranschaulicht, wie die Geräte-System-Brücken-app zu verwenden, um Ihre IoT-Core-Geräte mit IoTivity/OIC Geräte verbinden.
