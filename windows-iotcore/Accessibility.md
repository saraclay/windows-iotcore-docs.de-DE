---
title: Barrierefreiheit für Windows 10 IoT
author: saraclay
ms.author: saclayt
ms.date: 03/8/2018
ms.topic: article
description: Informationen Sie zur Barrierefreiheit und wie diese Erkenntnisse auf Ihre nächste Anwendung oder ein Gerät angewendet.
keywords: Windows 10 IoT Core, Windows 10 IoT Enterprise, Barrierefreiheit, Farbe, Kontrast
ms.openlocfilehash: 149c47fc9cae7fb99eb6aa190055c13284c3e197
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513306"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>Einen Überblick über die Barrierefreiheit für Windows IoT 
 
## <a name="introduction"></a>Einführung 
Barrierefreiheit kann von allen Fähigkeiten intuitiver und effizienter, alle Funktionen nutzen, die Ihr Angebot Anwendungen oder Geräten unabhängig von einer Person mit Ihren Anwendungen oder Geräten interagieren. 
 
Es ist wichtig, dass Eingabehilfen während der Entwurfsphase des Produkts berücksichtigt wird, wie dies viele potenzielle Fehler in Bezug auf Barrierefreiheit vermieden wird. Z. B. während der Entwurfsphase können berücksichtigt, um die verwendeten Farben und die Größe von Text (und wie diese vom Benutzer angepasst werden können) eine große Kundenzahl. Und für Geräte mit einer Tastatur, während der Entwurfsphase Aspekt Bezug die Tastatur verwendet werden kann, um alle Funktionen in das Produkt und wie Sie Zugriff auf die häufig verwendete Funktionen, mit der geringsten Anzahl von Tastatureingaben zu nutzen.  
 
Für Entwickler aus Implementierungssicht ist die gute Nachricht, Windows, wie eine Plattform bereits viel Arbeit, um einige der Barrierefreiheit werden standardmäßig bieten. Standardsteuerelemente sind beispielsweise standardmäßig über die Benutzeroberflächenautomatisierung (UIA) API programmgesteuert zugegriffen werden kann. Wenn Sie kein Standardsteuerelement verwenden und stattdessen benutzerdefinierte Benutzeroberfläche erstellen, kann die Arbeit erforderlich, um den Zugriff auf Benutzeroberfläche wesentlich mehr Zeit, über das einfache Erstellen von apps, die mit standardmäßigen Steuerelementen, die von der Plattform bereitgestellt sein. 

## <a name="accessibility-testing"></a>Barrierefreiheitstests
Im folgenden finden Sie Tools, mit denen, die wir empfehlen die Verwendung beim Erstellen der Anwendung. Während diese Tools helfen bei der Überwachung Ihrer eigenen Entwürfe, beachten Sie, dass Sie weiterhin benötigen, um Features wie z. B. hoher Kontrast "und" Text-Anforderungen zu berücksichtigen.

### <a name="accscope"></a>EH-Viewer (AccScope)
Die [AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) Tool können Entwickler und Tester, den Zugriff auf ihre app während der Entwicklung und Design der app ausgewertet, potenziell in früher Prototyp Phasen, sondern in den späten Testphase des einer app Entwicklungszyklus. Das Hauptziel besteht im Testen von Barrierefreiheitsszenarien in Verbindung mit der Sprachausgabe für die App.

### <a name="inspect"></a>Inspect
[Überprüfen Sie](https://msdn.microsoft.com/library/windows/desktop/Dd318521) ermöglicht es Ihnen, wählen ein UI-Element, und zeigen die barrierefreiheitsdaten. Sie können Eigenschaften und Steuerelementmuster der Microsoft-Benutzeroberflächenautomatisierung anzeigen und die Navigationsstruktur der Automatisierungselemente im Benutzeroberflächenautomatisierungs-Baum testen. Verwenden Sie prüfen, bei der Entwicklung die Benutzeroberfläche, um zu überprüfen, wie-Attribute als Eingabehilfe in der Benutzeroberflächenautomatisierung verfügbar gemacht werden. In einigen Fällen stammen die Attribute aus der Unterstützung der Benutzeroberflächenautomatisierung, die für Standard-XAML-Steuerelemente bereits implementiert wurde. In anderen Fällen stammen die Attribute von speziellen Werte, die Sie in Ihrem XAML-Markup festgelegt haben, wie AutomationProperties Eigenschaften angefügte.

Weitere Informationen zum Testen der Barrierefreiheit erfahren möchten? Lesen der [Barrierefreiheit testen Artikel](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect) für die vollständige Liste.
 
 
## <a name="accessibility-in-uwp-apps"></a>Barrierefreiheit in UWP-apps 
Das UWP-Team bei Microsoft hat ein umfassendes Handbuch über die Barrierefreiheit für UWP-app-Design und Entwicklung zusammengestellt. Der Einfachheit halber haben wir die unten aufgeführte Liste enthalten, aber Sie können auch weitere unserer [Übersicht über die Barrierefreiheit](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview). 
 
Darüber hinaus ist eine Einführung in die UI Automation API und einige Tools, die zur Verfügung, über die programmgesteuerte Darstellung der Benutzeroberfläche vertraut zu machen unten verfügbar. 
 
> [!VIDEO https://www.youtube.com/embed/6b0K2883rXA]

 
| Artikel | Beschreibung | 
|---------|-------------| 
| [Entwerfen von barrierefreier Software](https://docs.microsoft.com/windows/uwp/design/accessibility/designing-inclusive-software) | Erfahren Sie mehr über das Entwerfen inklusiver UWP-Apps für Windows 10.  Entwerfen und erstellen Sie inklusive Software unter Berücksichtigung der Barrierefreiheit. | 
| [Entwickeln von barrierefreien Windows-Apps](https://docs.microsoft.com/windows/uwp/design/accessibility/developing-inclusive-windows-apps) | Dieser Artikel dient als Orientierungshilfe bei der Entwicklung barrierefreier UWP-Apps. | 
| [Prüfliste für die Barrierefreiheit](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-checklist) | Enthält eine Prüfliste, mit der Sie sicherstellen können, dass Ihre UWP-App barrierefrei ist. | 
| [Verfügbarmachen von grundlegenden Informationen zur Barrierefreiheit](https://docs.microsoft.com/windows/uwp/design/accessibility/basic-accessibility-information) | Grundlegende Informationen zur Barrierefreiheit werden häufig in die Kategorien Name, Rolle und Wert unterteilt. In diesem Thema wird der Code beschrieben, mit dem Ihre App die grundlegenden Informationen verfügbar machen kann, die für Hilfstechnologien erforderlich sind. | 
| [Barrierefreiheit der Tastaturnavigation](https://docs.microsoft.com/windows/uwp/design/accessibility/keyboard-accessibility) | Wenn Ihre App keine barrierefreie Bedienung mit der Tastatur ermöglicht, können Benutzer, die blind oder in ihrer Beweglichkeit eingeschränkt sind, Schwierigkeiten bei der Verwendung Ihrer App haben oder Ihre App möglicherweise überhaupt nicht nutzen. | 
| [Designs mit hohem Kontrast](https://docs.microsoft.com/windows/uwp/design/accessibility/high-contrast-themes) | Beschreibt die Schritte, mit denen Sie die Bedienbarkeit Ihrer UWP-App sicherstellen können, wenn ein Design mit hohem Kontrast aktiviert ist. | 
| [Anforderungen für barrierefreien Text](https://docs.microsoft.com/windows/uwp/design/accessibility/accessible-text-requirements) | In diesem Thema werden die bewährten Methoden für barrierefreien Text in Apps beschrieben. Damit stellen Sie sicher, dass der Kontrast zwischen Farben und Hintergründen ausreichend hoch ist. Außerdem werden in diesem Thema die Rollen der Microsoft-Benutzeroberflächenautomatisierung, die für Textelemente in einer UWP-App verwendet werden können, sowie bewährte Methoden für Text in Grafiken erläutert. | 
| [Nicht empfehlenswerte Praktiken für die Barrierefreiheit](https://docs.microsoft.com/windows/uwp/design/accessibility/practices-to-avoid) | Es werden die Praktiken aufgeführt, die Sie vermeiden sollten, wenn Sie eine barrierefreie UWP-App erstellen möchten. | 
| [Benutzerdefinierte Automatisierungspeers](https://docs.microsoft.com/windows/uwp/design/accessibility/custom-automation-peers) | Beschreibt das Konzept von Automatisierungspeers für die Microsoft-Benutzeroberflächenautomatisierung und erläutert, wie Sie eine Unterstützung der Benutzeroberflächenautomatisierung für eine eigene benutzerdefinierte UI-Klasse bereitstellen können. | 
 
