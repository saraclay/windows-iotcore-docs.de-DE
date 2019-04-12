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
# <a name="window-10-iot-core-and-nxp-imx-socs"></a><span data-ttu-id="455a5-104">Windows 10 IoT Core "und" NXP i.MX SoCs</span><span class="sxs-lookup"><span data-stu-id="455a5-104">Window 10 IoT Core and NXP i.MX SoCs</span></span>

<span data-ttu-id="455a5-105">2018 Microsoft NXP eine private Vorschauversion von Windows 10 IoT Core NXP i.MX 6 und 7-i.MX Silicon angekündigt und auf die i.MX 8 Min. des Arbeitsbeginns SoCs.</span><span class="sxs-lookup"><span data-stu-id="455a5-105">In 2018, Microsoft and NXP announced a private preview of Windows 10 IoT Core on NXP i.MX 6 and i.MX 7 silicon and began work on the i.MX 8M SoCs.</span></span> <span data-ttu-id="455a5-106">Hunderte von professionellen Entwickler, Forscher und Entwickler erklärte, die die Kombination von 10 Jahren von Windows-Sicherheitsupdates und die Flexibilität und Zuverlässigkeit von NXP Silicon.</span><span class="sxs-lookup"><span data-stu-id="455a5-106">Hundreds of commercial developers, researchers, and Makers expressed their interest in the combination of 10 years of Windows security updates and the flexibility and reliability of NXP silicon.</span></span> 
 
<span data-ttu-id="455a5-107">Während der Vorschau für Techniker von Microsoft und NXP Tausende von Stunden, während denen optimieren und verbessern die BSP von denen Auswertung der lösungs anhand einer Eingabe aufgewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="455a5-107">During the preview, Microsoft and NXP engineers spent thousands of hours tuning and improving the BSP based on input from those evaluating the solution.</span></span> <span data-ttu-id="455a5-108">Wir haben mit Kunden, die zur Modernisierung von legacy-Industrie möchten Domänencontroller, entwickeln neue Cloud Erstellen von automatisierungslösungen verbunden und Gateways mit der Klasse führende Sicherheit, z. B. [e/a trusted](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).</span><span class="sxs-lookup"><span data-stu-id="455a5-108">We worked with customers interested in modernizing legacy industrial controllers, developing new cloud connected building automation solutions, and gateways with class leading security such as [trusted I/O](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).</span></span>
 
<span data-ttu-id="455a5-109">Basierend auf der überwältigenden Interesse an der Lösung, sind Microsoft und NXP jetzt BSPs für die i.MX 6 i.MX 7 und 8 Min. Produktfamilie SoCs i.MX als öffentliche Vorschau nicht gewinnorientierte zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="455a5-109">Based on the overwhelming interest in the solution, Microsoft and NXP are now making BSPs for the i.MX 6, i.MX 7, and i.MX 8M family of SoCs available as a non-commercial public preview.</span></span> <span data-ttu-id="455a5-110">Aufgrund der langjährige Microsoft und NXP haben in der eingebettete und IoT Märkte, wir wissen, dass die Notwendigkeit für Flexibilität beim Entwerfen.</span><span class="sxs-lookup"><span data-stu-id="455a5-110">Because of the long history Microsoft and NXP have in the embedded and IoT markets, we understand the need for design flexibility.</span></span> <span data-ttu-id="455a5-111">Aus diesem Grund werden neben dem mehrere einzelne Board Computer und auf Modul Lösungen, Microsoft, NXP und unsere Hardware, die Partnern aktiviert haben, die i.MX 6, 7-i.MX und i.MX 8 Min. BSPs unter open-Source-Lizenzierung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="455a5-111">Therefore, in addition to the multiple single board computers and system on module solutions Microsoft, NXP, and our hardware partners have enabled, the i.MX 6, i.MX 7, and i.MX 8M BSPs are provided under open source licensing.</span></span> <span data-ttu-id="455a5-112">Jetzt werden alle Benutzer auf den vollständigen BSP-Inhalt für die i.MX 6 i.MX 7 und i.MX 8 Min. Produktfamilien für die Verwendung der Auswertung auf ihrer Hardware zusammen mit der Oktober 2018-Version von Windows 10 IoT Core zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="455a5-112">Now, everyone will be able to access the complete BSP contents for the i.MX 6, i.MX 7, and i.MX 8M product families for evaluation use on their hardware along with the October 2018 release of Windows 10 IoT Core.</span></span>


## <a name="bsp-access"></a><span data-ttu-id="455a5-113">BSP-Zugriff</span><span class="sxs-lookup"><span data-stu-id="455a5-113">BSP Access</span></span>

<span data-ttu-id="455a5-114">Wenn Sie zum Aktivieren der Unterstützung für Ihre eigene Hardware i.MX BSP-Quelle und Dokumentation auf Sie zugegriffen [Github]( https://github.com/ms-iot/imx-iotcore).</span><span class="sxs-lookup"><span data-stu-id="455a5-114">If you are interested to enable support for your own i.MX hardware, please access the BSP source and documentation on [Github]( https://github.com/ms-iot/imx-iotcore).</span></span> <span data-ttu-id="455a5-115">Sofern nicht angegeben, wird der Großteil der Quelle unter MIT-Lizenz bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="455a5-115">Unless noted, the majority of the source is provided under MIT license.</span></span> <span data-ttu-id="455a5-116">Der Code ist noch in Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="455a5-116">The code is still under development.</span></span> <span data-ttu-id="455a5-117">Nicht alle Features der Plattform werden vollständig aktiviert oder optimiert.</span><span class="sxs-lookup"><span data-stu-id="455a5-117">Not all platform features are fully enabled or optimized.</span></span> <span data-ttu-id="455a5-118">Der Code ist derzeit für nichtkommerzielle Entwicklung nur zum Zeitpunkt der Zeit bestimmt.</span><span class="sxs-lookup"><span data-stu-id="455a5-118">The code is currently intended for non-commercial development only at time time.</span></span> <span data-ttu-id="455a5-119">Eine kommerzielle qualitätsanforderungen wird weiter unten in 2019 erwartet.</span><span class="sxs-lookup"><span data-stu-id="455a5-119">A commercial quality release is expected later in 2019.</span></span>

<span data-ttu-id="455a5-120">Wenn Sie NXP Hardware/BSP verwandte Fragen oder Feedback dazu, wie die BSP die entsprechende Projektmappe besser unterstützen kann, den Beitrag bitte an den [NXP Community](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D).</span><span class="sxs-lookup"><span data-stu-id="455a5-120">If you have NXP hardware/BSP releated questions or feedback on how the BSP can better support your targeted solution, please post to the [NXP Community](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D).</span></span> <span data-ttu-id="455a5-121">Verwenden Sie für alle Windows-Fragen, die [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).</span><span class="sxs-lookup"><span data-stu-id="455a5-121">For any Windows related questions, please use the [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).</span></span>


## <a name="ecosystem-resources"></a><span data-ttu-id="455a5-122">Ökosystem von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="455a5-122">Ecosystem Resources</span></span>

<span data-ttu-id="455a5-123">Mehrere Partner von Microsoft und NXP kommerziellen i.MX 6, 7,-i.MX aktiviert haben, und i.MX 8 Min. Geräte mit Unterstützung für Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="455a5-123">Several Microsoft and NXP partners have enabled commercial i.MX 6, i.MX 7, and i.MX 8M devices with support for Windows 10 IoT Core.</span></span> <span data-ttu-id="455a5-124">Wenden Sie sich an den Partner, direkt für Hardware und eine Plattform-Image.</span><span class="sxs-lookup"><span data-stu-id="455a5-124">Please contact the partner directly for hardware and a platform image.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="455a5-125">Gerät</span><span class="sxs-lookup"><span data-stu-id="455a5-125">Device</span></span></th>
<th align="left"><span data-ttu-id="455a5-126">Contact</span><span class="sxs-lookup"><span data-stu-id="455a5-126">Contact</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/"><span data-ttu-id="455a5-127">Aaeon PICO-IMX6</span><span class="sxs-lookup"><span data-stu-id="455a5-127">Aaeon PICO-IMX6</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:davidhung@aaeon.com.tw"><span data-ttu-id="455a5-128">David Hung</span><span class="sxs-lookup"><span data-stu-id="455a5-128">David Hung</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858"><span data-ttu-id="455a5-129">Advantech RSB-4411</span><span class="sxs-lookup"><span data-stu-id="455a5-129">Advantech RSB-4411</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/"><span data-ttu-id="455a5-130">Compulab IoT-Gate</span><span class="sxs-lookup"><span data-stu-id="455a5-130">Compulab IoT-Gate</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:igor@compulab.co.il"><span data-ttu-id="455a5-131">Igor Vaisbein</span><span class="sxs-lookup"><span data-stu-id="455a5-131">Igor Vaisbein</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx6q-q7/"><span data-ttu-id="455a5-132">Geniatech SoM-iMX6Q-Q7</span><span class="sxs-lookup"><span data-stu-id="455a5-132">Geniatech SoM-iMX6Q-Q7</span></span></a></p></td>
<td align="left"><p><p><span data-ttu-id="455a5-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> oder <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span><span class="sxs-lookup"><span data-stu-id="455a5-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx7d/"><span data-ttu-id="455a5-134">Geniatech SoM-iMX7D</span><span class="sxs-lookup"><span data-stu-id="455a5-134">Geniatech SoM-iMX7D</span></span></a></p></td>
<td align="left"><p><p><span data-ttu-id="455a5-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> oder <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span><span class="sxs-lookup"><span data-stu-id="455a5-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.karo-electronics.de/tx-standard.html?&L=1"><span data-ttu-id="455a5-136">KA-Ro Electronics TX6UL, TX6S, TX6DL und TX6Q</span><span class="sxs-lookup"><span data-stu-id="455a5-136">Ka-Ro Electronics TX6UL, TX6S, TX6DL, and TX6Q</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:us@karo-electronics.de"><span data-ttu-id="455a5-137">Uwe Steinkohl</span><span class="sxs-lookup"><span data-stu-id="455a5-137">Uwe Steinkohl</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="455a5-138"><a href="http://wce.keith-koep.com/en/products/pconxs-ff/">Keith & amp pConXS</a> mit <a href="http://wce.keith-koep.com/en/products/trizeps7-i.MX6/">Trizeps VII</a></span><span class="sxs-lookup"><span data-stu-id="455a5-138"><a href="http://wce.keith-koep.com/en/products/pconxs-ff/">Keith & Koep pConXS</a> with <a href="http://wce.keith-koep.com/en/products/trizeps7-i.MX6/">Trizeps VII</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html"><span data-ttu-id="455a5-139">Kontron SMARC-sAMX6i</span><span class="sxs-lookup"><span data-stu-id="455a5-139">Kontron SMARC-sAMX6i</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:martin.unverdorben@kontron.com"><span data-ttu-id="455a5-140">Martin Unverdorben</span><span class="sxs-lookup"><span data-stu-id="455a5-140">Martin Unverdorben</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://phytec.com/product/phyboard-imx7-development-kit/"><span data-ttu-id="455a5-141">PhyBOARD-i.MX 7 Development Kit</span><span class="sxs-lookup"><span data-stu-id="455a5-141">phyBOARD-i.MX 7 Development Kit</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:sales@phytec.com"><span data-ttu-id="455a5-142">Fernando Benitez</span><span class="sxs-lookup"><span data-stu-id="455a5-142">Fernando Benitez</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.solid-run.com/imx6-win-10-iot-core/"><span data-ttu-id="455a5-143">Führen Sie Hummingboard Edge Durchgezogen</span><span class="sxs-lookup"><span data-stu-id="455a5-143">Solid Run Hummingboard Edge</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:ilya@solid-run.com"><span data-ttu-id="455a5-144">Ilya Viten</span><span class="sxs-lookup"><span data-stu-id="455a5-144">Ilya Viten</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/"><span data-ttu-id="455a5-145">VIA VAB-820</span><span class="sxs-lookup"><span data-stu-id="455a5-145">VIA VAB-820</span></span></a></p></td>
<td align="left"><p><p><span data-ttu-id="455a5-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> oder <a href="mailto:dreamku@via.com.tw">träumen Ku</span><span class="sxs-lookup"><span data-stu-id="455a5-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> or <a href="mailto:dreamku@via.com.tw">Dream Ku</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK"><span data-ttu-id="455a5-147">MCIMX6ULL-EVK</span><span class="sxs-lookup"><span data-stu-id="455a5-147">MCIMX6ULL-EVK</span></span></a></p></td>
<td align="left"><p><p><a href="mailto:Wei.A.Wang@nxp.com"><span data-ttu-id="455a5-148">Wei Wang</span><span class="sxs-lookup"><span data-stu-id="455a5-148">Wei Wang</span></span></a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK"><span data-ttu-id="455a5-149">MCIMX8M-EVK</span><span class="sxs-lookup"><span data-stu-id="455a5-149">MCIMX8M-EVK</span></span></a></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.nxp.com/imx8mminievk"><span data-ttu-id="455a5-150">MCIMX8MMINI-EVK</span><span class="sxs-lookup"><span data-stu-id="455a5-150">MCIMX8MMINI-EVK</span></span></a></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
