---
title: Übersicht über die Windows 10 IoT Enterprise
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Erfahren Sie, was Windows 10 IoT Enterprise und was Sie damit tun können.
keywords: Windows 10 IoT Enterprise, Enterprise, binär, Windows
ms.openlocfilehash: 029c98dc7652269aceaa97b820f2a190850eb1d3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512961"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Eine Übersicht über Windows 10 IoT Enterprise

## <a name="what-is-windows-10-iot-enterprise"></a>Was ist Windows 10 IoT Enterprise?
Windows 10 IoT Enterprise ist eine Vollversion von Windows 10, die Enterprise-Verwaltbarkeit und Sicherheit für IoT-Lösungen bietet. Windows 10 IoT Enterprise gibt alle Vorteile der weltweiten Windows-Umgebung. Es ist eine Binärdatei gleichbedeutend mit Windows 10 Enterprise, sodass Sie die gleichen vertrauten Entwicklungs- und Verwaltungstools wie Client-PCs und Laptops verwenden können.  Wenn es sich um lizenzierungs- und Verteilung geht, unterscheiden sich jedoch die Desktopversion und die IoT-Versionen. Beachten Sie, dass Windows 10 IoT Enterprise sowohl für langfristigen Wartungskanal (LTSC) (Halbjährlicher Kanal, SAC) Optionen bietet. OEMs können die Version auswählen, die sie für ihre Geräte benötigen.

## <a name="getting-started"></a>Erste Schritte 

Weitere Informationen zu Windows 10 IoT Enterprise Fertigung, empfehlen wir Ihnen [Windows 10 IoT Enterprise Produktions-Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview).  

## <a name="fixed-purpose-devices"></a>Feste Geräten 

> [!TIP]
> Ihres Lizenzvertrags für die vollständige Anleitung auf alle Windows 10 IoT Enterprise Verwendungsszenarien angezeigt. Wenn Sie nicht über diese Lizenzvertrag verfügen, wenden Sie sich den OEM, dass Sie für die geschäftliche Vereinbarung zusammenarbeiten. 

Windows ist bekannt als die Betriebssysteme auf Laptops und Desktops, die von Verbrauchern und Unternehmen weltweit verwendet.  Weniger gut bekannt ist, dass jahrelang Windows auch viele Geldautomaten, POS-Terminals, industriellen Automation-Systeme, thin Clients, vitro-Diagnostik, digitalen Beschilderung, Kiosks und andere Geräte festen Zwecke einschalten.  Windows 10 IoT Enterprise können Sie feste Geräten mit bestimmten Beschränkungen und Einschränkungen des Lizenzvertrags zu erstellen.  

Ein fester Zweck Gerät unterscheidet sich von einem Gerät universell gibt folgenden Möglichkeiten:  
* Das Gerät ist gesperrt wird, auf eine einzelne Anwendung oder fester Satz von Anwendungen über die Funktionen für zugewiesenen Zugriff oder die Shell-Startprogramm.  
* Die Oberfläche des Geräts erfolgt sofort, wenn der Kunde auch einmaliges Anmelden. Dies erfolgt durch Konfigurieren von Image des Geräts, um den normalen Windows-Out-of-Box-Erfahrungen zu überspringen. 
* Tastaturen, USB-Anschlüsse und Geräterichtlinien sind gesperrt, sodass um das Gerät nur in den festen Zweck verwendet werden zu beschränken.  
* Die OEM-Abhängige das Gerät für den Benutzer mit der Software des Geräts als vollständige Produkt-Lizenzen und durchläuft bestimmte Windows-Ausdrücke in ihren eigenen angezeigt.
* Die OEM-Abhängige bietet Kunden Unterstützung für das vollständige Produkt, einschließlich der Funktionen, die vom Betriebssystem ausgeführt.

## <a name="long-term-servicing-channel-ltsc"></a>Langfristiger Wartungskanal (LTSC)

Spezialisierte Systeme, wie etwa PCs, die steuern, medizinischer Geräte, POS-Systeme und Geldautomaten, erfordern häufig eine mehr Service Option aufgrund von ihren Zweck. Diese Geräte führen in der Regel eine einzelne wichtige Aufgabe aus und benötigen weniger häufig Funktionsupdates als andere Geräte in der Organisation. Es ist noch wichtiger ist, dass diese Geräte als stabil und sicher wie möglich als, dass sie sich auf dem neuesten Stand mit Änderungen an der Benutzeroberfläche beibehalten werden. Das LTSC servicing-Modell wird verhindert, dass Geräte mit Windows 10 Enterprise LTSB die üblichen Featureupdates und bietet nur qualitätsupdates um sicherzustellen, dass die gerätesicherheit auf dem neuesten Stand bleibt. In diesem Sinn qualitätsupdates sind für Windows 10 Enterprise LTSB Clients weiterhin sofort verfügbar, aber Kunden können sie mithilfe eines der Wartung in der Wartung-Abschnitt "Tools" genannten Tools verzögern.

* [Erfahren Sie mehr über LTSC](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)

## <a name="long-term-support-silicon-details"></a>Informationen zum Silicon von Long-term Support

Die Herbst-2018-Version von Windows 10 IoT Enterprise werden auch einer LTSC-Versionen. Die folgende Liste umfasst alle Prozessoren, die auf die Herbst-2018-Version unterstützt werden soll. Wenn Sie eine frühere Version von Windows 10 IoT Enterprise verwenden möchten, finden Sie Details auf der prozessorunterstützung [hier](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processor-table).

> | Windows 10 IoT Enterprise  |
> |-------------|
> | AMD® 6. Generation Prozessoren Reihe Ax-8xxx, E-Serie Ex-8xxx & FX - 870 K | 
> | AMD® 7. Generation Prozessoren Reihe Ax-9xxx-Serie, E-Serie Ex-9xxx-Serie & FX-9xxx-Serie | 
> | AMD® Ryzen™ 3/5/7 1xxx | 
> | AMD® Ryzen™ 3/5/7 2xxx | 
> | AMD® G-Serie | 
> | AMD® R-Serie | 
> | AMD® V1xxx | 
> | ™ von Intel® Core Prozessoren der 4. generation | 
> | ™ von Intel® Core Prozessoren der 5. generation |
> | 6. Prozessoren der Intel® Core™ generation |
> | 7. Prozessoren der Intel® Core™ generation |
> | 8. Prozessoren der Intel® Core™ generation |
> | Intel® Atom™ Prozessor E3900-Serie |
> | Intel® Atom™ X5 E8000 Prozessor |
> | Intel® Atom™ X5 Z8350 Prozessor |
> | Intel® Atom™ Prozessor E3800-Produktfamilie |
> | Intel® Pentium® und Celeron® Prozessor N und J-Series |

## <a name="helpful-resources"></a>Hilfreiche Ressourcen
> [!NOTE]
> Möglicherweise ist zusätzliche Ressourcen zur Verfügung, aus Ihren Distributor, um Windows EPKEA OEM-Aktivierung wird erläutert, und Sie erhalten Hilfestellung beim Generieren der Produktion einsetzbaren Windows IoT Enterprise [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) Bildtyp.

* [Anpassungen für Unternehmens-Desktops](https://docs.microsoft.com/windows-hardware/customize/enterprise/enterprise-custom-portal)
* [Vereinheitlichter Schreibfilter für Windows 10](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Zugewiesenen Zugriff für Enterprise und SQL Server Pro](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Shell-Startprogramm für die Editionen Enterprise und Education](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [Sperren von Ressourcen](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Aktivieren von eingebetteten Modus, und Verwenden von Hintergrundtasks unter Windows IoT Enterprise](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [Konfigurieren der Windows-Telemetrie in Ihrer Organisation](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Konfigurieren Sie Kiosk und freigegebene Geräte mit Windows-Desktopeditionen](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
* [Desktop Produktionskalender](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
