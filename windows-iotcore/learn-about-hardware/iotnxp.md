---
title: Windows IoT und NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: Lernen Sie Windows 10 IoT Core und NXP i.MX SoCs
keywords: Windows 10 IoT Core, erste Schritte, i.MX, NXP
ms.openlocfilehash: 2dc212fa403e2d8d4c32bffbae3c8bcd97b5b022
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512658"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core "und" NXP i.MX SoCs

2018 Microsoft NXP eine private Vorschauversion von Windows 10 IoT Core NXP i.MX 6 und 7-i.MX Silicon angekündigt und auf die i.MX 8 Min. des Arbeitsbeginns SoCs. Hunderte von professionellen Entwickler, Forscher und Entwickler erklärte, die die Kombination von 10 Jahren von Windows-Sicherheitsupdates und die Flexibilität und Zuverlässigkeit von NXP Silicon. 
 
Während der Vorschau für Techniker von Microsoft und NXP Tausende von Stunden, während denen optimieren und verbessern die BSP von denen Auswertung der lösungs anhand einer Eingabe aufgewendet wurde. Wir haben mit Kunden, die zur Modernisierung von legacy-Industrie möchten Domänencontroller, entwickeln neue Cloud Erstellen von automatisierungslösungen verbunden und Gateways mit der Klasse führende Sicherheit, z. B. [e/a trusted](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).
 
Basierend auf der überwältigenden Interesse an der Lösung, sind Microsoft und NXP jetzt BSPs für die i.MX 6 i.MX 7 und 8 Min. Produktfamilie SoCs i.MX als öffentliche Vorschau nicht gewinnorientierte zur Verfügung. Aufgrund der langjährige Microsoft und NXP haben in der eingebettete und IoT Märkte, wir wissen, dass die Notwendigkeit für Flexibilität beim Entwerfen. Aus diesem Grund werden neben dem mehrere einzelne Board Computer und auf Modul Lösungen, Microsoft, NXP und unsere Hardware, die Partnern aktiviert haben, die i.MX 6, 7-i.MX und i.MX 8 Min. BSPs unter open-Source-Lizenzierung bereitgestellt. Jetzt werden alle Benutzer auf den vollständigen BSP-Inhalt für die i.MX 6 i.MX 7 und i.MX 8 Min. Produktfamilien für die Verwendung der Auswertung auf ihrer Hardware zusammen mit der Oktober 2018-Version von Windows 10 IoT Core zugreifen können.


## <a name="bsp-access"></a>BSP-Zugriff

Wenn Sie zum Aktivieren der Unterstützung für Ihre eigene Hardware i.MX BSP-Quelle und Dokumentation auf Sie zugegriffen [Github]( https://github.com/ms-iot/imx-iotcore). Sofern nicht angegeben, wird der Großteil der Quelle unter MIT-Lizenz bereitgestellt. Der Code ist noch in Entwicklung. Nicht alle Features der Plattform werden vollständig aktiviert oder optimiert. Der Code ist derzeit für nichtkommerzielle Entwicklung nur zum Zeitpunkt der Zeit bestimmt. Eine kommerzielle qualitätsanforderungen wird weiter unten in 2019 erwartet.

Wenn Sie NXP Hardware/BSP verwandte Fragen oder Feedback dazu, wie die BSP die entsprechende Projektmappe besser unterstützen kann, den Beitrag bitte an den [NXP Community](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D). Verwenden Sie für alle Windows-Fragen, die [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).


## <a name="ecosystem-resources"></a>Ökosystem von Ressourcen

Mehrere Partner von Microsoft und NXP kommerziellen i.MX 6, 7,-i.MX aktiviert haben, und i.MX 8 Min. Geräte mit Unterstützung für Windows 10 IoT Core. Wenden Sie sich an den Partner, direkt für Hardware und eine Plattform-Image.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Gerät</th>
<th align="left">Contact</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></p></td>
<td align="left"><p><p><a href="mailto:davidhung@aaeon.com.tw">David Hung</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></p></td>
<td align="left"><p><p><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></p></td>
<td align="left"><p><p><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> oder <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></p></td>
<td align="left"><p><p><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> oder <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">KA-Ro Electronics TX6UL, TX6S, TX6DL und TX6Q</a></p></td>
<td align="left"><p><p><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://wce.keith-koep.com/en/products/pconxs-ff/">Keith & amp pConXS</a> mit <a href="http://wce.keith-koep.com/en/products/trizeps7-i.MX6/">Trizeps VII</a></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></p></td>
<td align="left"><p><p><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://phytec.com/product/phyboard-imx7-development-kit/">PhyBOARD-i.MX 7 Development Kit</a></p></td>
<td align="left"><p><p><a href="mailto:sales@phytec.com">Fernando Benitez</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Führen Sie Hummingboard Edge Durchgezogen</a></p></td>
<td align="left"><p><p><a href="mailto:ilya@solid-run.com">Ilya Viten</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></p></td>
<td align="left"><p><p><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> oder <a href="mailto:dreamku@via.com.tw">träumen Ku</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></p></td>
<td align="left"><p><p><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
