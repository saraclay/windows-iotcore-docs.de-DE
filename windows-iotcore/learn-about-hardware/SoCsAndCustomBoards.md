---
title: SoCs und benutzerdefinierte Boards für Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zu Hardware-Features für eine Vielzahl von vorgeschlagenen Boards und Community-Geräte.
keywords: Windows Iot, Development-Geräte, Beratungsgremien, SOC, SOM, System Chips, Raspberry Pi 2 "," Raspberry Pi 3 "," Minnowboard Max "," DragonBoard
ms.openlocfilehash: 7b3839a222c8e15e006f03ca5d125d81f175b46e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513242"
---
# <a name="socs-and-custom-boards"></a>SoCs und benutzerdefinierte boards

## <a name="microsoft-enabled-socs"></a>Microsoft-fähigen SoCs

Microsoft arbeitet zusammen mit Broadcom, Intel, NXP und Qualcomm, um die Unterstützung für Windows 10 IoT Core-System von mehreren Anbietern auf einem Chip (SoCs) prüfen. Diese IoT Core-gestützte SoCs werden in Hunderten von verschiedenen Geräten verwendet werden, können Sie einen Prototyp verwenden und Ihre Idee kommerziell.

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Intel® Atom® Prozessor E3900-Serie (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016)](https://www.qualcomm.com/products/snapdragon/processors/410) | [i.MX 6 Familie](http://aka.ms/iotnxp) |
| BCM2836 | [Intel® Celeron® Prozessor N3350 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009)](https://www.qualcomm.com/products/snapdragon/processors/212) | [i.MX 7 Familie](http://aka.ms/iotnxp)     |
|         | [Intel® Pentium® N4200 Prozessorplattform (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [i.MX 8 Min.-Familie](http://aka.ms/iotnxp) |
|         | [Intel® Pentium® und Celeron® Prozessor N3000 Serie (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Intel® Atom® X5 E8000 Prozessor (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Intel® Atom® X5 Z8350 Prozessor (Cherry-Trail)](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Intel® Atom® Prozessor E3800-Produktfamilie (Bay-Trail-ich)](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Intel® Pentium® und Celeron® Prozessor N und J-Series (Bay-Trail-M/D)](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

Die SoC gewählten übernehmen richtet sich nach Überlegungen wie z. B. leistungsanforderungen, Energieprofil, Kosten, physische Konnektivitätsoptionen, long Term Support und betriebsbedingungen.

Sie müssen auch müssen entscheiden, ob Sie eine sofort einsetzbare Board oder ein Gerät verwenden möchten erstellen ein benutzerdefiniertes Gerät mithilfe eines vom System auf ein Modul (SoM) sowie eine benutzerdefinierte Netzbetreiber-Board, oder Erstellen einer vollständigen benutzerdefinierten Board. Kosten und den Grad der Anpassung sind Schlüsselfaktoren bei dieser Entscheidung, mit der sowohl in der Regel erhöhen, da Sie weiter anpassen.

## <a name="windows-10-iot-core-features-by-processor-family"></a>Windows 10 IoT Core-Features von Prozessorfamilie

> [!NOTE]
> Diese Liste berücksichtigt die Überlegung Prozessoren, die in der öffentlichen Vorschau nicht gewinnorientierte sind.

Damit können Sie die richtige Plattform für Ihr Gerät auswählen, zeigt die folgende Tabelle die Funktionen, die von der Prozessorfamilie mit Windows 10 IoT Core unterstützt werden. Alle unten aufgeführten Funktionen werden in Windows 10 IoT Core, unterstützt, jedoch einige SoCs möglicherweise nicht die spezifische IP-Adresse in ihren Entwurf enthalten und sind z. B. mit "N/v" gekennzeichnet. In solchen Fällen kann eine 3rd Party-Lösung in den Entwurf zum Bereitstellen der erforderlichen Funktionen umfassen sein.  In einer begrenzten Anzahl von Fällen, in denen ein Windows 10 IoT Core-Feature nicht auf einem Prozessor implementiert wird, wird der Eintrag leer gelassen.

> |    | Intel  |  Qualcomm  | NXP i.MX6 | NXP i.MX7 | NXP i.MX8M | Broadcom |
> |----|--------|------------|-----------|-----------|------------|----------|
> | Audio | x | x | x | x | x | x |
> | GPIO | x | x | x | x | x | x |
> | I2C | x | x | x | x | x | x |
> | Ethernet | x | Nicht zutreffend | x | x | x | x |
> | SPI | x | x | x | x | x | x |
> | Anzeige | x | x | x | x | x | x |
> | UART | x | x | x | x | x | x |
> | USB | x | x | x | x | x | x |
> | PCIe | x | Nicht zutreffend | x | In der Entwicklung | In der Entwicklung | Nicht zutreffend |
> |MIPI-CSI | Nicht zutreffend | x | Nicht zutreffend | Nicht zutreffend | Nicht zutreffend | Nicht zutreffend |
> | Grafiken/Video | x | x | Software-rendered | Software-rendered | Software-rendered | Software-rendered |
> | GPS | Nicht zutreffend | x | Nicht zutreffend | Nicht zutreffend | Nicht zutreffend | Nicht zutreffend |
> | Wi-Fi/BT | Nicht zutreffend | x | Nicht zutreffend | Nicht zutreffend | Nicht zutreffend | Nicht zutreffend |
> | Vertrauenswürdige e/a | Nicht zutreffend | Nicht zutreffend | x | x | x | Nicht zutreffend |
> | Energieverwaltung |  | x | x | x | In der Entwicklung | |
> | TPM | x | x | x | x | x | Nicht zutreffend |
> | Sicherer Start | x | x | In der Entwicklung | In der Entwicklung | In der Entwicklung | |
> | Ruhezustand | x | | | | | | 
> | PWM | x | Nicht zutreffend | x | x | x | |
> | JTAG | x | Nicht zutreffend | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>Benutzerdefinierte boards

Ist eine sofort einsetzbare Gerät in einer Form, die die Konnektivitätsoptionen "" enthält, die für Ihre Szenarien geeignet, wird das häufig die Auswahl der am häufigsten und Zeit-kostengünstiger sein.  

Für die meisten Benutzer würde Entwicklung einen vollständigen benutzerdefinierten Board sinnvoll sein, wenn das Produkt erwartungsgemäß in Volumes "größer als die Dutzende oder sogar Hunderte, Tausende von Einheiten" verkauft werden. Für kleinere Volumes können mithilfe einer SoM und Entwerfen einer benutzerdefinierten Netzbetreiber-Board, statt ein völlig neues Board, Entwerfen Ihre Kosten und die Zeit bis zur markteinführung, als auch die sorgen für eine rationelle Softwareentwicklung und die Integration erheblich.

Alle Plattformen verfügt über eindeutige Quirks, die Aufmerksamkeit während der Implementierung.  Im folgenden sind einige Vorschläge zu den ersten Schritten zu erhalten. Und es gibt, zwar viele Unternehmen, die auf Windows 10 IoT Core erstellen ist hier eine Liste mit einigen, die Erfahrung mit Windows 10 IoT Core bewährt haben:

* __[Raspberry Pi](#raspberry-pi-derived-custom-design)__
* __[Intel](#intel-based-custom-design)__
* __[Qualcomm](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*Wenn Sie ein SoM-Anbieter oder eine ODM und die unten aufgeführte Liste hinzugefügt werden soll, senden Sie eine e-Mail zu [ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com) oder direkt auf dieser Seite bearbeiten und einen Pull Request zu übermitteln.*

*Viele Unternehmen, die hier aufgeführten sind umfangreicher und komplexer.  Wenn Sie Probleme, die die richtige Person erreicht haben, senden Sie eine e-Mail [ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com) und nun führen wir unsere besten zum Herstellen einer Verbindung mit der richtigen Personen.*

### **<a name="raspberry-pi-derived-custom-design"></a>Raspberry Pi abgeleiteten benutzerdefinierten Entwurf entwickeln**

[Element 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service) Angebote board Anpassung-Dienst, damit Raspberry Pi können Sie zum Hinzufügen oder entfernen die Verbindungsoptionen. Wenn Sie auch die BSP Anpassungen vornehmen müssen, können Sie nutzen die [BSP-Quellcode auf Github öffnen](https://github.com/ms-iot/rpi-iotcore).

### **<a name="intel-based-custom-design"></a>Intel-basierten benutzerdefinierten Entwurf**

Es ist ein dynamisches Ökosystem von [aufgetreten Intel-Gerät-Generatoren](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349) für Windows Sie arbeiten können. Eine Intel-Geräts, die zum Ausführen von Windows 10 IoT Core entwickelt hat eine Reihe von unterschieden, die von der häufigeren PCs:

1. Wenn Sie Benutzermoduszugriff universelle Windows-Plattform (UWP)-API auf einfache Busse wie GPIO, I2C und SPI bereitstellen müssen, müssen Sie sicherstellen, dass der ACPI-Tabelle in der UEFI-Firmware entsprechenden Einträge für RHProxy enthält. Näheres [Benutzermoduszugriff](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) für Weitere Informationen.
2. Sie müssen sicherstellen, dass in der Firmware SMBIOS Informationen enthält, gemäß [OEM Lizenzanforderungen](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements).

Wenn Sie Ihr eigenes Board erstellen, wenden Sie sich an den BIOS-Anbieter bei Bedarf Anleitungen ACPI oder dem SMBIOS-Änderungen.

#### *<a name="experienced-partners"></a>Erfahrene Partner*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech](http://www.advantech.com/) - buy@advantech.tw
* [Kontron](http://www.kontron.com/) - martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### **<a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>Qualcomm DragonBoard 410c (APQ8016)-basierten benutzerdefinierten Entwurf entwickeln**

Binäre BSP für DragonBoard 410c (basierend auf Qualcomm AQP8016 SoC) kann heruntergeladen werden [Qualcomm Developer Network](https://developer.qualcomm.com/hardware/dragonboard-410c/software).

Das BSP-Paket enthält den Quellcode für den ACPI um einfache hardwareanpassungen zu ermöglichen, die nur ACPI Änderungen erfordern.  

> [!IMPORTANT] 
> Wenn Sie zusätzliche hardwareanpassungen benötigen, zeigen Sie z. B. die Verwendung einer bestimmten MIPI-DSI Bereich Plattform sicheren Start zu aktivieren, RF Kalibrierung und Zertifizierung (z. b. FCC, CE), Sie müssen ein Code-Lizenznehmer von Qualcomm BSP Quelle werden müssen oder für die Arbeit mit einem Anbieter, der Zugriff hat (siehe unten aufgeführten erfahrene Partner).

Empfehlungen:

1. Arbeiten Sie wenn möglich, ein erfahrener SoM-Anbieter, um benutzerdefinierte entwerfen.
2. Wenn Sie einen benutzerdefinierten Board erstellen, arbeiten mit einem SoM-Anbieter oder ein erfahrener Qualcomm BSP Anpassung Dienstanbieter, wie z. B. [derzeit](https://www.intrinsyc.com/) oder [Thundersoft](http://www.thundersoft.com/) um BSP-Anpassung und Design-Unterstützung zu erhalten.
3. Wenn Sie erwarten, dass sehr viele (Millionen), [wenden Sie sich an Qualcomm](https://assets.qualcomm.com/contact-sales-iot.html).

#### *<a name="experienced-partners"></a>Erfahrene Partner*

* [Derzeit](https://www.intrinsyc.com/computing-platforms/410-som/) -Mark Waldenberg (mwaldenberg@intrinsyc.com)
* [Keith & amp](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/) - contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) - welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) -Sam (saml@tw.ute.com); Perry (perryt@te.ute.com)

### **<a name="nxp-preview"></a>NXP-Vorschau**

NXP-Unterstützung für Windows 10 IoT Core befindet sich in der öffentlichen Vorschau. Weitere Informationen, die den Zugriff der BSP oder Suche nach einem Hardwarepartner, wechseln Sie zu der [NXP SoC-Seite](http://aka.ms/iotnxp).

Sie können auch erreichen, um Partnern dabei arbeiten wir:

* Advantech [RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) - buy@advantech.tw
* Keith & amp [pConXS](http://wce.keith-koep.com/en/products/pconxs-ff/) mit [Trizeps VII](http://wce.keith-koep.com/en/products/trizeps7-i.MX6/) - contact@keith-koep.com
* Kontron [SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) -Martin Unverdorben (martin.unverdorben@kontron.com)
* Führen Sie Solid [Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/ )-Ilya Viten (ilya@solid-run.com)
* Geniatech [SoM-iMX6Q-Q7](https://www.geniatech.com/product/som-imx6q-q7/) & [SoM-iMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike Decker (mike.decker@geniatech.com) oder Fang Jijun (Fjj@geniatech.com)
* ÜBER [VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) – Michael Fox (MichaelFox@via.com.tw) oder träumen Ku (dreamku@via.com.tw)
* Phytec [PhyBOARD-i.MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com)


## <a name="other-options"></a>Weitere Optionen

Wenn Sie feststellen, dass Sie weiterhin einen benutzerdefinierten Board erstellen möchten, haben wir bereitgestellt, dass einige Vorschläge von Herstellern und darunter Planungsdokumente und das Layout für ein Board helfen können.

* [Alle Leiterplatte](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [JLC PCB](https://jlcpcb.com/)
* [Myro PCB](http://www.myropcb.com/)
* [OSH PARK](https://oshpark.com/)
* [Seeed studio](https://www.seeedstudio.com/)
