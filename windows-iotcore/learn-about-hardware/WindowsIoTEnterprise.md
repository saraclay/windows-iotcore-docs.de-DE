---
title: Übersicht über die Windows 10 IoT Enterprise
author: saraclay
ms.author: saclayt
ms.date: 01/18/2017
ms.topic: article
description: Erfahren Sie, was Windows 10 IoT Enterprise und was Sie damit tun können.
keywords: Windows 10 IoT Enterprise, Enterprise, binär, Windows
ms.openlocfilehash: 1f13c4df2c40dcc4449f2e6cdd16005b1bc0069f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513170"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Eine Übersicht über Windows 10 IoT Enterprise

## <a name="what-is-windows-10-iot-enterprise"></a>Was ist Windows 10 IoT Enterprise?
Windows 10 IoT Enterprise ist eine Vollversion von Windows 10, die Enterprise-Verwaltbarkeit und Sicherheit für IoT-Lösungen bietet. Dies ist eine Binärdatei gleichbedeutend mit Windows 10 Enterprise, wenn Sie bereits Funktionsweise von Windows 10 Enterprise wissen, ein Großteil dieses Wissen auf Windows 10 IoT Enterprise übertragbar ist. Wenn es sich um lizenzierungs- und Verteilung geht, unterscheiden sich jedoch der Desktopversion und die IoT-Version. 

## <a name="getting-started"></a>Erste Schritte 
Bevor Sie sich an einem eingebetteten/IoT-Händler wenden, empfehlen wir Ihnen, arbeiten mit einer der [diese Geräte](https://solutionsdirectory.intel.com/solutions-directory/processors/736/processors/766/processors/782/processors/788/processors/869/processors/879/processors/883/processors/888/processors/1053/processors/1058/processors/1103/processors/1107/processors/1110/processors/1117/processors/1133/processors/1135/processors/1139/processors/1141/processors/1175/processors/1192/processors/1344/processors/1348/processors/1349/processors/1371/processors/1392/processors/1729/processors/2284).  Sie können Ihrem PC oder -Gerät mit empfohlenen Laden einer [Evaluierungsversion](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise) von Windows 10 Enterprise, um sofort mit der prototyperstellung beginnt.

Um Ihre Journey in der Produktion mit Windows 10 IoT Enterprise zu starten, müssen Sie einen Verteiler aus erreichen [dieser Liste](http://wincom.blob.core.windows.net/documents/Windows_IoT_Distributor_Information.pdf). 

## <a name="fixed-purpose-devices"></a>Feste Geräten 

> [!TIP]
> Ihres Lizenzvertrags für die vollständige Anleitung auf alle Windows 10 IoT Enterprise Verwendungsszenarien angezeigt.

Die Windows 10 IoT Enterprise Edition wird lizenziert, Sie feste Zweck Geräte wie Thin Clients, Geldautomaten, Point-of-Sale Terminals, industrielle Automatisierungssysteme usw. erstellen können.  Es gibt bestimmte Beschränkungen und Einschränkungen in den Lizenzvertrag an. 

Im Allgemeinen ein fester Zweck Gerät unterscheidet sich von einem Gerät universell auf folgende Weise:  
* Das Gerät ist gesperrt wird, auf eine einzelne Anwendung oder fester Satz von Anwendungen über die Funktionen für zugewiesenen Zugriff oder die Shell-Startprogramm.  
* Das Gerät auch bei sofort die Erfahrung, wenn der Endkunde empfängt. Dies erfolgt durch Konfigurieren von Image des Geräts, um den normalen Windows-Out-of-Box-Erfahrungen zu überspringen.
* Tastaturen, USB-Anschlüsse und Geräterichtlinien sind gesperrt, sodass um das Gerät nur in den festen Zweck verwendet werden zu beschränken.  
* Die OEM-Abhängige das Gerät für den Benutzer mit der Software des Geräts als vollständige Produkt-Lizenzen und durchläuft bestimmte Windows-Ausdrücke in ihren eigenen angezeigt.

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Unterschiede zwischen Windows 10 IoT Core und Windows 10 IoT Enterprise
Während Windows 10 IoT Core und Windows 10 IoT Enterprise in Namen ähnlich sind, unterscheiden sich was diese bieten, und was sie unterstützen. Im folgenden finden eine Liste der Funktionen, die Edition Unterschiede hervorhebt.

Mindestanforderung Details, finden Sie auf [der Windows-Hardware-Website](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

> |             | Windows 10 IoT Core  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | Benutzererfahrung | Einzelne UWP-app, die beim Start mit Unterstützung von Hintergrund-apps und Dienste ausgeführt wird. | Herkömmliche Windows-Shell mit erweiterten Lockdown-Funktionen |
> | Monitorlose unterstützt | Ja | Ja |
> | Unterstützte App-Architektur | Nur UWP | UWP und Win32 |
> | Cortana | *Cortana-SDK* | Ja |
> | Domänenbeitritt | Nur AAD | AAD und herkömmliche |
> | Management | MDM | MDM |
> | Gerät-Sicherheitstechnologien | TPM, der sichere Start, BitLocker, Integritätsnachweis für Geräte und Device Guard für IoT | TPM, der sichere Start, BitLocker, Device Guard, Defender ATP und Integritätsnachweis für Geräte |
> | Unterstützung für CPU-Architektur | X86 X64 und ARM | X86 X64 und ARM64 |
> | Lizenzierung | Online-Lizenzierung Vereinbarung und eingebettete OEM-Verträge, lizenzgebührenfreie | Direkte und indirekte eingebettete OEM-Vereinbarungen |
> | Verwendungsszenarien | Digitalen Beschilderung "," Smart Building "," IoT-Gateway "," HMI, intelligente Home, tragbare Geräte | Industry-Tablets, POS, Kiosk, digitalen Beschilderung, Geldautomaten, medizinische Geräte, Herstellungsgeräte, Thin Clients |

## <a name="helpful-resources"></a>Hilfreiche Ressourcen
> [!NOTE]
> Möglicherweise ist zusätzliche Ressourcen zur Verfügung, vom Verteiler zum Windows EPKEA OEM-Aktivierung wird erläutert, und Sie erhalten Hilfestellung beim Generieren der Produktion einsetzbaren Windows IoT Enterprise [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) Bildtyp.

* [Desktop Produktionskalender](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
* [Vereinheitlichter Schreibfilter für Windows 10](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Zugewiesenen Zugriff für Enterprise und SQL Server Pro](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Shell-Startprogramm für die Editionen Enterprise und Education](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [Sperren von Ressourcen](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Aktivieren von eingebetteten Modus, und Verwenden von Hintergrundtasks unter Windows IoT Enterprise](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [Konfigurieren der Windows-Telemetrie in Ihrer Organisation](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Konfigurieren Sie Kiosk und freigegebene Geräte mit Windows-Desktopeditionen](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
