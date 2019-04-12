---
title: AllJoyn Producers
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, wie ein Producer AllJoyn zu machen, indem Sie erlernen und Erstellen der Introspection-XML und anderen Features.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512825"
---
> [!NOTE]
> <span data-ttu-id="1349d-104">Sie zeigen die archivierte Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="1349d-104">You are viewing archived documentation.</span></span> <span data-ttu-id="1349d-105">AllJoyn wird nicht mehr von Windows 10 IoT unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1349d-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="1349d-106">Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.</span><span class="sxs-lookup"><span data-stu-id="1349d-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="1349d-107">AllJoyn Producers</span><span class="sxs-lookup"><span data-stu-id="1349d-107">AllJoyn Producers</span></span>

<span data-ttu-id="1349d-108">AllJoyn, erstellt die [AllSeen Alliance](https://allseenalliance.org/), bietet ein hervorragendes Framework aus, für die optimal für die Verwendung von AllJoyn mit verbundenen Geräten und apps in einem nächsten Netzwerk, und Windows stellt bereit. die [AllJoyn-Studio ](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) -Erweiterung für Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1349d-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="1349d-109">Unsere Tools excel über das Erstellen von apps für Producer und Consumer, kann ein neues AllJoyn-Gerät ganz von vorn beginnen Recht verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="1349d-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="1349d-110">Wenn Sie eine Idee für das nächste großartige verbundenen Gerät oder ein neues Spielzeug mit Basteln und zu durchsuchen, das, Sie haben verwenden die Standardschnittstellen angeboten, die von der AllSeen Alliance möglicherweise nicht.</span><span class="sxs-lookup"><span data-stu-id="1349d-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="1349d-111">Wenn dies der Fall ist, müssen Sie zum Erstellen eines neuen AllJoyn Producers.</span><span class="sxs-lookup"><span data-stu-id="1349d-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="1349d-112">Muss ein Entwickler, die möchten, stellen einen neuen AllJoyn Producer eigene Introspection XML zu erstellen, aber benötigt die entsprechenden Fachkenntnisse und verfügt über eine erhebliche Lernkurve für neue Entwickler Introspection XML erstellen.</span><span class="sxs-lookup"><span data-stu-id="1349d-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="1349d-113">Diesem Blogbeitrag werden die Lernkurve senken, indem Sie unterteilen die verschiedenen Komponenten der Introspection-XML, beschreibt den Zweck und die Einschränkungen der einzelnen Komponenten und bereitstellen, gute Beispiele für intuitiv ausgedrückt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1349d-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="1349d-114">Vorhandene Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1349d-114">Existing documentation</span></span>

<span data-ttu-id="1349d-115">Eine oberflächliche Untersuchung die folgenden Ressourcen zusammen mit diesem Blogbeitrag sollten Entwickler beschleunigen des Introspection XML-Codes zu verstehen:</span><span class="sxs-lookup"><span data-stu-id="1349d-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="1349d-116">[Dass AllJoyn-Ereignisse und Aktionen für die-API](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn Implementierungsdetails und (Übersicht).</span><span class="sxs-lookup"><span data-stu-id="1349d-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="1349d-117">[AllJoyn Benutzeroberflächen-Entwurfsrichtlinien für Review Board](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -strenge strukturieren und für AllJoyn Introspection XML-Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="1349d-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="1349d-118">[D-Bus-Spezifikation](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn verwendet als Basis für Introspection XML in dieser Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="1349d-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

__<span data-ttu-id="1349d-119">Die drei Typen von Introspection-XML</span><span class="sxs-lookup"><span data-stu-id="1349d-119">The three types of Introspection XML</span></span>__

<span data-ttu-id="1349d-120">Wie Sie genau, dass AllJoyn-Dokumentation durchlesen, finden Sie drei Arten von Introspection XML:</span><span class="sxs-lookup"><span data-stu-id="1349d-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="1349d-121">D-Bus-Spezifikation XML: mit geringem Verwaltungsaufwand, prozessübergreifende Kommunikation mit einem Typformat zur Darstellung von Daten.</span><span class="sxs-lookup"><span data-stu-id="1349d-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="1349d-122">AllJoyn Introspection XML: erweitert die D-Bus-Spezifikation XML mit XML-Tags zur Aufnahme von textbeschreibungen beim Anwenden der AllJoyn Prinzipien auch mit der Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="1349d-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="1349d-123">Erweiterte AllJoyn Introspection XML: Entwicklung von klassischen Einführung in der Introspection-XML-benannte Typen für Strukturen und Wörterbücher.</span><span class="sxs-lookup"><span data-stu-id="1349d-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="1349d-124">AllJoyn Studio unterstützt derzeit die XML-Spezifikation der D-Bus "und" AllJoyn Introspection XML; Dieser Blog bestimmen, das Erstellen, und dass AllJoyn Introspection XML zu bilden.</span><span class="sxs-lookup"><span data-stu-id="1349d-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="1349d-125">Der AllSeen-Allianz Schnittstelle Review Board (IRB) verwendet die neue erweiterte AllJoyn Introspection als Format für formale Übermittlungen für die Überprüfung der Standardisierung aber arbeitet an einem einheitlichen Introspection XML-Format für die nahe Zukunft.</span><span class="sxs-lookup"><span data-stu-id="1349d-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="1349d-126">Allgemeiner Überblick über Introspection</span><span class="sxs-lookup"><span data-stu-id="1349d-126">Introspection High Level Overview</span></span>

<span data-ttu-id="1349d-127">Jede AllJoyn Producer kündigt öffentlich Introspection XML, auf der Producer die unterstützten Funktionen – Schnittstellen als beschrieben über Signale, Eigenschaften und Methoden.</span><span class="sxs-lookup"><span data-stu-id="1349d-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="1349d-128">Lösungen mit Code Generation, wie in der Erweiterung AllJoyn Studio basieren auf Introspection-XML mit den erforderlichen Code zum Beschleunigen der Entwicklung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1349d-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="1349d-129">Introspection XML beschreibt die Funktionalität von einem Producer in eine nicht-mehrdeutigen, lesbare Möglichkeit, so, dass zwei unterschiedlicher Hersteller den XML-Code verwenden können, um ein Producer mit denselben Funktionen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="1349d-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="1349d-130">Mithilfe desselben Tokens, sollten Entwickler ohne vorherige Kenntnis von einem Producer AllJoyn, basierend auf der XML-Producer verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1349d-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

__<span data-ttu-id="1349d-131">Dass AllJoyn-Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="1349d-131">AllJoyn Interfaces</span></span>__

<span data-ttu-id="1349d-132">AllJoyn erreicht dies durch die Aufteilung von Introspection XML in verschiedenen "Interfaces", die verschiedene logische Gruppierungen von Verhalten und die Funktionen darstellen.</span><span class="sxs-lookup"><span data-stu-id="1349d-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="1349d-133">Dass AllJoyn-Schnittstellen werden mithilfe einer Reverse-DNS-Konvention benannt.</span><span class="sxs-lookup"><span data-stu-id="1349d-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="1349d-134">Die Schnittstelle "Foo"-Schnittstelle, die von Contoso Ltd., der die Domäne "contoso.com" besitzt, erstellt würde beispielsweise folgendermaßen geschrieben werden:</span><span class="sxs-lookup"><span data-stu-id="1349d-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="1349d-135">Ein Producer kann eine beliebige Anzahl von Schnittstellen implementieren, aber Sie müssen jede Komponente einer Schnittstelle, die sie ankündigen implementieren.</span><span class="sxs-lookup"><span data-stu-id="1349d-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="1349d-136">Um zu unterscheiden, und erweitern Verhaltensweisen, unterstützten AllJoyn erstellen neue Schnittstellen in Bezug auf eine vorhandene Schnittstellenhierarchie d. h. `com.contoso.Foo.Bar` definiert neue Funktionen für die Schritte unter der `Foo.Bar` Kategorie jedoch keine expliziten Abhängigkeiten nicht auf die `com.contoso.Foo` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="1349d-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="1349d-137">Beispielsweise haben wir zwei Schnittstellen: `com.contoso.Sensor` und `com.contoso.Sensor.Humidity` – "Luftfeuchtigkeit" wird logisch unter der Kategorie "Sensor" liegt.</span><span class="sxs-lookup"><span data-stu-id="1349d-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="1349d-138">Jemand die Entwicklung von einem Producer Luftfeuchtigkeit können unterstützen nur die `com.contoso.Sensor.Humdity` -Schnittstelle, aber sie können auch zur Unterstützung der `com.contoso.Sensor` Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="1349d-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="1349d-139">Unabhängig davon, wenn sie eine Schnittstelle ankündigen, müssen Producer alle zugehörigen Funktionen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1349d-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="1349d-140">Die `<description>` Tag wird verwendet, um die Schnittstellen, Funktionen und Argumente zu beschreiben und für verschiedene Sprachen lokalisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1349d-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="1349d-141">Der großzügigen Verwendung von der `<description>` Tag stellt den XML-Code leichter verständlich und Mehrdeutigkeiten entfernt.</span><span class="sxs-lookup"><span data-stu-id="1349d-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="1349d-142">Standardverfahren bestimmt die Verwendung der `org.alljoyn.Bus.Secure` Anmerkung für eine Schnittstelle für die Sicherheit und Authentifizierung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1349d-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="1349d-143">Verwenden Sie für eine strenge Authentifizierung einem vorinstallierten Schlüssel (PSK) oder ein Zertifikat Schlüsselaustausch (ECDSA) aus.</span><span class="sxs-lookup"><span data-stu-id="1349d-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="1349d-144">Andernfalls wird eine "null"-Authentifizierung das Standardverhalten.</span><span class="sxs-lookup"><span data-stu-id="1349d-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="1349d-145">**Der tatsächliche Authentifizierungsmechanismus geschieht in der Implementierung nicht die Deklaration**.</span><span class="sxs-lookup"><span data-stu-id="1349d-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="1349d-146">Diese Anmerkung bietet Sicherheit aber keinen der angegebenen verwendeten Sicherheitstyp oder wie sie implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="1349d-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

___<span data-ttu-id="1349d-147">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1349d-147">Example</span></span>___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <annotation name="org.allJoyn.Bus.Secure" value="true" />
 
    <description language="en">
 
      Private interface for a Door the consumer owns. 
 
    </description>
 
  </interface>
 
</node>
```

<span data-ttu-id="1349d-148">Dieses Beispiel zeigt eine Schnittstelle, die von einem Gerät verfügbar gemacht werden: `com.example.Door.PrivateDoor`.</span><span class="sxs-lookup"><span data-stu-id="1349d-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="1349d-149">Im Bereich der Schnittstelle ist alles, was wir Sorgen machen, ob die Kommunikation geschützt werden sollen, wenn es sich bei Verwendung dieser Schnittstelle, welche Art von Mechanismus nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1349d-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

__<span data-ttu-id="1349d-150">Interface-Funktionen</span><span class="sxs-lookup"><span data-stu-id="1349d-150">Interface Capabilities</span></span>__

<span data-ttu-id="1349d-151">Schnittstellen deklarieren, deren Funktionen mit drei Schnittstellenmember: Methoden, Eigenschaften oder Signale.</span><span class="sxs-lookup"><span data-stu-id="1349d-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="1349d-152">Introspection XML unterstützt auch Anmerkungen, die zusätzliche Funktionen oder Einschränkungen zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="1349d-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="1349d-153">Diese Funktionen verwenden UpperCamelCase-Notation, während Argumente LowerCamelCase Notation verwenden.</span><span class="sxs-lookup"><span data-stu-id="1349d-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="1349d-154">Argumenttypen</span><span class="sxs-lookup"><span data-stu-id="1349d-154">Argument Types</span></span>

<span data-ttu-id="1349d-155">Schnittstellenmember senden und Empfangen von Argumenten, die durch ein ASCII-Typ-Code gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="1349d-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="1349d-156">Je nach Art der Schnittstellenmember, Argumente können haben werden gesendet, um den Producer vom Consumer (Richtung "out" =) oder auf der Producer-Consumer (Direction = "ins").</span><span class="sxs-lookup"><span data-stu-id="1349d-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="1349d-157">Die folgende Tabelle enthält eine Kurzübersicht über häufig verwendete Typen:</span><span class="sxs-lookup"><span data-stu-id="1349d-157">The following table provides a brief overview of commonly used types:</span></span>

> | *<span data-ttu-id="1349d-158">Herkömmliche Name</span><span class="sxs-lookup"><span data-stu-id="1349d-158">Conventional Name</span></span>* | *<span data-ttu-id="1349d-159">Type-Code</span><span class="sxs-lookup"><span data-stu-id="1349d-159">Type-Code</span></span>* | *<span data-ttu-id="1349d-160">Verwendung</span><span class="sxs-lookup"><span data-stu-id="1349d-160">Use</span></span>* |
> |----------------- |---------| --- |
> |**<span data-ttu-id="1349d-161">BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="1349d-161">BOOLEAN</span></span>** | <span data-ttu-id="1349d-162">b)</span><span class="sxs-lookup"><span data-stu-id="1349d-162">b</span></span> | <span data-ttu-id="1349d-163">"True" (1) oder "false" (0) darstellt.</span><span class="sxs-lookup"><span data-stu-id="1349d-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="1349d-164">Für einfache binäre Informationen oder Zustände verwendet.</span><span class="sxs-lookup"><span data-stu-id="1349d-164">Used for simple binary information or states.</span></span> |
> |**<span data-ttu-id="1349d-165">BYTE</span><span class="sxs-lookup"><span data-stu-id="1349d-165">BYTE</span></span>** | <span data-ttu-id="1349d-166">y</span><span class="sxs-lookup"><span data-stu-id="1349d-166">y</span></span> | <span data-ttu-id="1349d-167">Integer-Wert von 0 bis 255.</span><span class="sxs-lookup"><span data-stu-id="1349d-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="1349d-168">Beim Umgang mit kleinen positive Zahlen verwendet.</span><span class="sxs-lookup"><span data-stu-id="1349d-168">Used when dealing with small positive numbers.</span></span> |
> |**<span data-ttu-id="1349d-169">UINT16</span><span class="sxs-lookup"><span data-stu-id="1349d-169">UINT16</span></span>** | <span data-ttu-id="1349d-170">q</span><span class="sxs-lookup"><span data-stu-id="1349d-170">q</span></span> | <span data-ttu-id="1349d-171">Ganzzahliger Wert zwischen 0 und 2 ^ 16-1</span><span class="sxs-lookup"><span data-stu-id="1349d-171">Integer value from 0 to 2^16 - 1</span></span> |
> |**<span data-ttu-id="1349d-172">UINT32</span><span class="sxs-lookup"><span data-stu-id="1349d-172">UINT32</span></span>** | <span data-ttu-id="1349d-173">u</span><span class="sxs-lookup"><span data-stu-id="1349d-173">u</span></span> | <span data-ttu-id="1349d-174">Ganzzahliger Wert zwischen 0 und 2 ^ 32-1</span><span class="sxs-lookup"><span data-stu-id="1349d-174">Integer value from 0 to 2^32 - 1</span></span> |
> |**<span data-ttu-id="1349d-175">UINT64</span><span class="sxs-lookup"><span data-stu-id="1349d-175">UINT64</span></span>** | <span data-ttu-id="1349d-176">n</span><span class="sxs-lookup"><span data-stu-id="1349d-176">t</span></span> | <span data-ttu-id="1349d-177">Ganzzahliger Wert zwischen 0 und 2 ^ 64-1</span><span class="sxs-lookup"><span data-stu-id="1349d-177">Integer value from 0 to 2^64 - 1</span></span> |
> |**<span data-ttu-id="1349d-178">INT16</span><span class="sxs-lookup"><span data-stu-id="1349d-178">INT16</span></span>** | <span data-ttu-id="1349d-179">m</span><span class="sxs-lookup"><span data-stu-id="1349d-179">n</span></span> | <span data-ttu-id="1349d-180">Ganzzahliger Wert zwischen –(2^15) und 2 ^ 15-1</span><span class="sxs-lookup"><span data-stu-id="1349d-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |**<span data-ttu-id="1349d-181">INT32</span><span class="sxs-lookup"><span data-stu-id="1349d-181">INT32</span></span>** | <span data-ttu-id="1349d-182">i</span><span class="sxs-lookup"><span data-stu-id="1349d-182">i</span></span> | <span data-ttu-id="1349d-183">Ganzzahliger Wert zwischen –(2^31) und 2 ^ 31-1</span><span class="sxs-lookup"><span data-stu-id="1349d-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |**<span data-ttu-id="1349d-184">INT64</span><span class="sxs-lookup"><span data-stu-id="1349d-184">INT64</span></span>** | <span data-ttu-id="1349d-185">x</span><span class="sxs-lookup"><span data-stu-id="1349d-185">x</span></span> | <span data-ttu-id="1349d-186">Ganzzahliger Wert zwischen –(2^63) und 2 ^ 63-1</span><span class="sxs-lookup"><span data-stu-id="1349d-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |**<span data-ttu-id="1349d-187">DOUBLE-WERT</span><span class="sxs-lookup"><span data-stu-id="1349d-187">DOUBLE</span></span>** | <span data-ttu-id="1349d-188">d</span><span class="sxs-lookup"><span data-stu-id="1349d-188">d</span></span> | <span data-ttu-id="1349d-189">Genauigkeit Gleitkommazahlen aus –(2^127) auf 2 ^ 127-1</span><span class="sxs-lookup"><span data-stu-id="1349d-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |**<span data-ttu-id="1349d-190">ZEICHENFOLGE</span><span class="sxs-lookup"><span data-stu-id="1349d-190">STRING</span></span>** | <span data-ttu-id="1349d-191">s</span><span class="sxs-lookup"><span data-stu-id="1349d-191">s</span></span> | <span data-ttu-id="1349d-192">UTF-8-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="1349d-192">UTF-8 string</span></span> |
 
<span data-ttu-id="1349d-193">Einen umfassenderen Überblick über alle unterstützten Typen finden Sie unter [hier](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span><span class="sxs-lookup"><span data-stu-id="1349d-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="1349d-194">Während ich dies schreibe, verwenden Sie SI-Einheiten, wenn möglich, und kennzeichnen Sie beabsichtigte Einheiten klar zu.</span><span class="sxs-lookup"><span data-stu-id="1349d-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="1349d-195">Wählen Sie wenn möglich, den den Typcode für Ihr Szenario am stärksten einschränkende; z. B. Wenn Sie einer Person-Alter in Jahren darstellen, verwenden Sie BYTE, nicht UINT16 oder Int16-Wert, da niemand eine negative Alter oder mehr als 255 Jahre alt sein wird.</span><span class="sxs-lookup"><span data-stu-id="1349d-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="1349d-196">Führen Sie immer die neueste Version [AllJoyn Schnittstelle Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="1349d-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="1349d-197">In der folgende Tabelle werden allgemeine Einheiten zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="1349d-197">The following table summarizes common units:</span></span>


> |*<span data-ttu-id="1349d-198">Anzahl</span><span class="sxs-lookup"><span data-stu-id="1349d-198">Quantity</span></span>* | *<span data-ttu-id="1349d-199">Einheit</span><span class="sxs-lookup"><span data-stu-id="1349d-199">Unit</span></span>*|
> |-------- | ---- |
> |**<span data-ttu-id="1349d-200">Absoluten Zeitpunkt (Datum und Uhrzeit)</span><span class="sxs-lookup"><span data-stu-id="1349d-200">Absolute time (date & time)</span></span>** | <span data-ttu-id="1349d-201">Sekunden seit der UNIX-Epoche (00: 00:00 auf 1. Januar 1970)</span><span class="sxs-lookup"><span data-stu-id="1349d-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |**<span data-ttu-id="1349d-202">Tageszeit</span><span class="sxs-lookup"><span data-stu-id="1349d-202">Time of Day</span></span>** | <span data-ttu-id="1349d-203">Sekunden seit Mitternacht</span><span class="sxs-lookup"><span data-stu-id="1349d-203">Seconds since midnight</span></span> |
> |**<span data-ttu-id="1349d-204">Zeitintervall</span><span class="sxs-lookup"><span data-stu-id="1349d-204">Time interval</span></span>** | <span data-ttu-id="1349d-205">Sekunden</span><span class="sxs-lookup"><span data-stu-id="1349d-205">Seconds</span></span> |
> |**<span data-ttu-id="1349d-206">Bandbreite</span><span class="sxs-lookup"><span data-stu-id="1349d-206">Bandwidth</span></span>** | <span data-ttu-id="1349d-207">Bits pro Sekunde</span><span class="sxs-lookup"><span data-stu-id="1349d-207">Bits per second</span></span> |
> |**<span data-ttu-id="1349d-208">Datengröße</span><span class="sxs-lookup"><span data-stu-id="1349d-208">Data size</span></span>** | <span data-ttu-id="1349d-209">Bytes</span><span class="sxs-lookup"><span data-stu-id="1349d-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="1349d-210">Methoden</span><span class="sxs-lookup"><span data-stu-id="1349d-210">Methods</span></span>

<span data-ttu-id="1349d-211">Consumer Methoden aufrufen, um den Status von einem Producer ändern, und ihre Namen sollten mit einem Verb beginnen, da sie die Anforderungen der Producer zum Ausführen einer Aktion darstellen.</span><span class="sxs-lookup"><span data-stu-id="1349d-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="1349d-212">Methoden können Eingabe- und Ausgabe der Argumente. Wenden Sie in der Fall, den keine Antwortnachricht zurückgesendet werden muss die Anmerkung "org.freedesktop.DBus.Method.NoReply".</span><span class="sxs-lookup"><span data-stu-id="1349d-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="1349d-213">Allerdings zurückgeben AllJoyn Methoden normalerweise eine SuccessResult oder eine FailureResult, haben Kunden-Feedback über den Methodenaufruf.</span><span class="sxs-lookup"><span data-stu-id="1349d-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="1349d-214">Der Typ der Argumente muss einhalten, die [D-Bus-Spezifikation](http://dbus.freedesktop.org/doc/dbus-specification.html).</span><span class="sxs-lookup"><span data-stu-id="1349d-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

___<span data-ttu-id="1349d-215">Beispiel (mit Ausnahme von Informationen der Einfachheit halber Schnittstelle)</span><span class="sxs-lookup"><span data-stu-id="1349d-215">Example (excluding interface information for convenience)</span></span>___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!-- Method showing arguments with only directions in -->
 
    <method name="SetPasscode">
 
      <description language="en">
 
        Allows owner of the door to change the code needed to unlock it.
 
      </description>
 
      <argument name="currentPasscode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="newPasscode" type="u" direction="in">
 
        <description language="en">
 
          New code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!-- Method showing both arguments in and out -->
 
    <method name="UnlockDoor">
 
      <description language="en">
 
        Allows guests with the code to unlock the door.
 
      </description>
 
      <argument name="passcode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="welcomeMessage" type="s" direction="out">
 
        <description language="en">
 
          Message from the owner of the door.
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
</node>
```

*<span data-ttu-id="1349d-216">Hinweis: In den meisten Fällen Eigenschaften sollten Sie zum anstelle von Methoden des Herstellers Zustand zugreifen (z. B. eine Color-Eigenschaft anstelle einer GetColor-Methode verwenden).</span><span class="sxs-lookup"><span data-stu-id="1349d-216">Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).</span></span>*

### <a name="properties"></a><span data-ttu-id="1349d-217">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="1349d-217">Properties</span></span>

<span data-ttu-id="1349d-218">Eigenschaften können vor allem den Zugriff auf ein Producer Zustand.</span><span class="sxs-lookup"><span data-stu-id="1349d-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="1349d-219">Während Eigenschaften technisch Zugriffswerte haben "gelesen", "Readwrite" oder "Schreiben", Status ändernden Funktionen in der Regel gehört, auf Methoden – daher, Entwickler sollten sich bemühen, behalten Sie die Eigenschaften als "Lesen" und "Readwrite" nur, wenn der Status dargestellt Somit ist die Eigenschaft unabhängig von allen anderen Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="1349d-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="1349d-220">Eigenschaften sollten nie einfach "write" – Ändern des Zustands ohne Beobachtung ist die Rolle der Methoden.</span><span class="sxs-lookup"><span data-stu-id="1349d-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="1349d-221">Eigenschaften müssen für Warnung Consumer gekennzeichnet werden, wenn sich ihre Werte ändern (optional Eigenschaften können diese Anmerkung von erben ihre übergeordnete Schnittstelle).</span><span class="sxs-lookup"><span data-stu-id="1349d-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="1349d-222">Die Anmerkung `org.freedesktop.DBus.Property.EmitsChangedSignal` kann vier Werte haben:</span><span class="sxs-lookup"><span data-stu-id="1349d-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="1349d-223">Wenn die Eigenschaft geändert wird, wird der Producer "true" – ein Signal, das die geänderte Eigenschaft und den neuen Wert, der angibt ausgeben.</span><span class="sxs-lookup"><span data-stu-id="1349d-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="1349d-224">In den Eigenschaften, die häufig verwendet werden und erfordern active Aufsicht, wie z. B. eine "LockState" für eine Tür verwendet.</span><span class="sxs-lookup"><span data-stu-id="1349d-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="1349d-225">"ungültig" – bei der Änderung der Eigenschaft, der Producer ein Signal, der angibt, aber nicht der neue Wert der geänderten Eigenschaft ausgibt.</span><span class="sxs-lookup"><span data-stu-id="1349d-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="1349d-226">Für Eigenschaften verwendet, die keine hohe Aufsicht (z. B. die "WashMode" von einem Trockner Kleidung) erfordern oder einen Großteil der Daten, z. B. einen Container darstellen.</span><span class="sxs-lookup"><span data-stu-id="1349d-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="1349d-227">Wenn die Eigenschaft geändert wird, gibt der Producer "false" – kein Signal aus.</span><span class="sxs-lookup"><span data-stu-id="1349d-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="1349d-228">Für Eigenschaften verwendet, die schnell, wie z. B. eine Eigenschaft "TransitCounter" ein Ausfall von u-Bahn-Drehkreuz, das Verwalten von Personen, die den Ausfall von u-Bahn boarding aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1349d-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="1349d-229">Falls nicht angegeben, verwendet dass AllJoyn-Eigenschaften als standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="1349d-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="1349d-230">"const": die Eigenschaft Wert nie ändern und niemals ausgeben ein Signals geändertes wird.</span><span class="sxs-lookup"><span data-stu-id="1349d-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="1349d-231">Dies wird in der Version AllJoyn 16.04; eingeführt wurden Verwenden Sie bis dahin "true".</span><span class="sxs-lookup"><span data-stu-id="1349d-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

___<span data-ttu-id="1349d-232">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1349d-232">Example</span></span>___

<span data-ttu-id="1349d-233">Erweitern auf dem vorherigen Beispiel, haben wir der XML-Code enthalten Eigenschaften, die (mit Ausnahme der Methoden aus Gründen der Übersichtlichkeit) geändert.</span><span class="sxs-lookup"><span data-stu-id="1349d-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Read property that sends a signal when the value changes -->
 
    <property name="IsLocked" type="b" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door may freely lock and unlock the door.
 
      </description>
 
    </property>  
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!—- Read-only property that never sends a signal and never changes -->
 
    <property name="Owner" type="s" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door is public knowledge.
 
      </description>
 
    </property>
 
  </interface>
 
</node>
```

### <a name="signals"></a><span data-ttu-id="1349d-234">Signale</span><span class="sxs-lookup"><span data-stu-id="1349d-234">Signals</span></span>

<span data-ttu-id="1349d-235">Verwendung signalisiert Consumer eines Ereignisses zu informieren, die sie durch Abfragen den Producer nicht ermitteln konnte.</span><span class="sxs-lookup"><span data-stu-id="1349d-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="1349d-236">Eine Tür geöffnet wird durch ein Producer DoorOpen-Eigenschaft mit einer Anmerkung für "true" EmitsChangedProperty vermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="1349d-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="1349d-237">Ein Benutzer die Haustür übergeben kann nicht jedoch von alle eigenschaftenänderungen, abgeleitet werden, damit dies ein guter eigenständige Signal machen würden.</span><span class="sxs-lookup"><span data-stu-id="1349d-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="1349d-238">Wir bezeichnen diese Art der Ereignisse bei dem "zustandslosen".</span><span class="sxs-lookup"><span data-stu-id="1349d-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="1349d-239">Da Signale vom Producer an Consumer unidirektional sind, können sie nur "out" Argumente enthalten.</span><span class="sxs-lookup"><span data-stu-id="1349d-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

___<span data-ttu-id="1349d-240">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1349d-240">Examples</span></span>___ 

<span data-ttu-id="1349d-241">(mit Ausnahme Methoden und Eigenschaften der Einfachheit halber):</span><span class="sxs-lookup"><span data-stu-id="1349d-241">(excluding methods and properties for convenience):</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Signals may contain arguments about non-state information -->
 
    <signal name="ThresholdCrossed" sessioncast="true">
 
      <description>
 
        Signal to notify owner whenever anyone passes through the door.
 
      </description>
 
      <argument name="crossedInward" type="b" direction="out">
 
        If true, someone entered; if false, someone left.
 
      </argument>
 
    </signal>
 
  </interface>
 
</node>
```

<span data-ttu-id="1349d-242">Da Signale solche eine eng gefasste Gültigkeitsbereich haben, angezeigt werden in der Regel nur wenige in ein Producer XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="1349d-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="1349d-243">Container</span><span class="sxs-lookup"><span data-stu-id="1349d-243">Containers</span></span>

<span data-ttu-id="1349d-244">Kombinieren Sie mehrere Argumente nicht in eine komplexe Sammlung wie eine serialisierte JSON-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="1349d-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="1349d-245">Die D-Bus-Spezifikation stellt visueller Hinweise für den Container für Daten: die Struktur "," ARRAY "," VARIANT "und" DICT_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="1349d-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="1349d-246">Verwenden Sie diese Option, um Argumente zu übergeben, die mehr als grundlegende Typen erfordern.</span><span class="sxs-lookup"><span data-stu-id="1349d-246">Use these to pass arguments that require more than basic types.</span></span>

___<span data-ttu-id="1349d-247">VARIANT</span><span class="sxs-lookup"><span data-stu-id="1349d-247">VARIANT</span></span>___

<span data-ttu-id="1349d-248">Varianten werden vom Typ "V" gekennzeichnet und können nicht enthalten [vollständige Typ](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span><span class="sxs-lookup"><span data-stu-id="1349d-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="1349d-249">Allerdings sollten Varianten nach Möglichkeit vermieden werden, da sie die Mehrdeutigkeit zu XML-Definitionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1349d-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

___<span data-ttu-id="1349d-250">STRUKTUR</span><span class="sxs-lookup"><span data-stu-id="1349d-250">STRUCT</span></span>___

<span data-ttu-id="1349d-251">Verwenden von Strukturen "(" und ")" zur Angabe der Anfang und Ende einer Datenstruktur – nur vollständig ein.</span><span class="sxs-lookup"><span data-stu-id="1349d-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="1349d-252">Diese Datenstrukturen können geschachtelt werden.</span><span class="sxs-lookup"><span data-stu-id="1349d-252">These data structures may be nested.</span></span>

<span data-ttu-id="1349d-253">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="1349d-253">Examples:</span></span>

<span data-ttu-id="1349d-254">Ein Typ von "(Iii)" gibt an, eine Struktur von drei ganzen Zahlen; "(i(ii))" gibt an, eine Struktur einer ganzen Zahl und eine Struktur von zwei ganzen Zahlen, die aus dem Typ unterscheidet, ist "((Ii) ich)".</span><span class="sxs-lookup"><span data-stu-id="1349d-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

___<span data-ttu-id="1349d-255">ARRAY</span><span class="sxs-lookup"><span data-stu-id="1349d-255">ARRAY</span></span>___

<span data-ttu-id="1349d-256">ARRAYs verwenden, den den Typcode "a" und muss nur vollständige ein folgen.</span><span class="sxs-lookup"><span data-stu-id="1349d-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="1349d-257">ARRAYs müssen nicht Satz Länge und, damit sie sich auf eine Datenstruktur Liste ähneln.</span><span class="sxs-lookup"><span data-stu-id="1349d-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="1349d-258">ARRAYs stellen einen einzelnen vollständigen Typ dar.</span><span class="sxs-lookup"><span data-stu-id="1349d-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="1349d-259">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="1349d-259">Examples:</span></span>

<span data-ttu-id="1349d-260">Ein Typ von "Ai" stellt ein ARRAY von ganzen Zahlen dar, während "Aai" ein ARRAY eines Arrays von ganzen Zahlen darstellt.</span><span class="sxs-lookup"><span data-stu-id="1349d-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="1349d-261">Ein ARRAY kann auch mit Strukturen verwendet werden: "lebender".</span><span class="sxs-lookup"><span data-stu-id="1349d-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

___<span data-ttu-id="1349d-262">DICT_ENTRY</span><span class="sxs-lookup"><span data-stu-id="1349d-262">DICT_ENTRY</span></span>___

<span data-ttu-id="1349d-263">DICT_ENTRYs-Funktion, die auf eine Struktur mit mehr Einschränkungen ähnlich wie: Verwenden sie "{" und "}" kann nur auftreten, als einen Elementtyp des Arrays und müssen genau zwei Typen in den geschweiften Klammern abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="1349d-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="1349d-264">Der erste Typ stellt einen "Schlüssel" in einer Datenstruktur Wörterbuch und die Sekunde darstellt, die "Value" in das Wörterbuch der Schlüssel / Wert-Paar.</span><span class="sxs-lookup"><span data-stu-id="1349d-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="1349d-265">Ein Schlüssel sollte in einem Wörterbuch eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="1349d-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="1349d-266">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1349d-266">Example:</span></span>

<span data-ttu-id="1349d-267">Ein Typ von einem {Sy} gibt ein Wörterbuch mit Zeichenfolgenschlüsseln und Byte-Werte an.</span><span class="sxs-lookup"><span data-stu-id="1349d-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="1349d-268">Verwendung</span><span class="sxs-lookup"><span data-stu-id="1349d-268">Use</span></span> <description> <span data-ttu-id="1349d-269">die Tags auf gültige Schlüssel und Werte beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="1349d-269">tags to describe valid keys and values.</span></span> 

__<span data-ttu-id="1349d-270">Letzte Beispiel und ajxmlcop</span><span class="sxs-lookup"><span data-stu-id="1349d-270">Final Example and ajxmlcop</span></span>__

<span data-ttu-id="1349d-271">Das Konzept von Containern verbessert die Funktionen von den vorhandenen XML-bereit sowie eine Möglichkeit für neue nützlich Schnittstellenmember.</span><span class="sxs-lookup"><span data-stu-id="1349d-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="1349d-272">Sobald Sie fertig sind, der XML-Code schreiben, verwenden Sie das Befehlszeilentool ajxmlcop.exe (verfügbar unter der AllJoyn [Git Source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) oder [hier](https://github.com/MS-brock/AllJoynToasterDemo)) zum Überprüfen des XML-Codes.</span><span class="sxs-lookup"><span data-stu-id="1349d-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="1349d-273">Ajxmlcop.exe mit Ihrer XML-Datei als das Eingabeargument verwenden (z. B. `C:\>ajxmlcop.exe doorExample.xml`) zum Empfangen von Fehler-, Warn- und informationsmeldungen.</span><span class="sxs-lookup"><span data-stu-id="1349d-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="1349d-274">Dieses Tool bietet wertvolles Feedback hinsichtlich der Struktur und die XML-Format und Verwendung von Signalen, Eigenschaften und Methoden.</span><span class="sxs-lookup"><span data-stu-id="1349d-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

``` xml
<node>
  <interface name="com.example.Door.PrivateDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door.  Private interface that can only be used by the producer’s owner.
    </description>
    <method name="SetPasscode">
      <description language="en">
        Change the code needed to unlock the door.
      </description>
      <argument name="currentPasscode" type="u" direction="in">
        <description language="en">
          Current code needed to unlock door
        </description>
      </argument>
      <argument name="newPasscode" type="u" direction="in">
        <description language="en">
          New code needed to unlock door
        </description>
      </argument>
    </method>
    <method name="UpdateGuestRatings">
      <description language="en">
        Update the list of guests and their personality scores.
      </description>
      <annotation name="org.freedesktop.DBus.Method.NoReply" value="true" />
      <argument name="guestName" type="s">
        <description language="en">
          The name of the guest being entered.
        </description>
      </argument>
      <argument name="qualityScores" type="a{sy}">
        <description language="en">
          DICTIONARY[Key:(string)guestQuality, Value:(byte)score]
          KEYs: "Friendly", "Social", "Punctual" 
          VALUEs: [0-10]
          The qualities of the guest, scored appropriately. If the guestName matches an existing entry, this updates that entry.
        </description>
      </argument>
    </method>
    <method name="SetDoorSecurity">
      <description language="en">
        Close and lock the door or unlock the door.
      </description>
      <argument name="secured" type="b" direction="in">
        <description language="en">
          If TRUE, shut and lock the door.
          If FALSE, unlock the door.
        </description>
      </argument>
    </method>
    <property name="MessageBook" type="a(ss)" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="invalidates"/>
      <description language="en">
        (struct)[(string)guestName, (string)message]
        A list of names of people and the messages they have left.
      </description>
    </property>
    <property name="GuestRatings" type="a(sa{sy})" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        ARRAY[(string)guestName, DICTIONARY(Key:(string)guestQuality, Value:(byte)score)]
        KEYs: "Friendly", "Social", "Punctual"
        VALUEs: [0-10]
        A collection of the previous guests and their scored qualities.
      </description>
    </property>
    <property name="IsLocked" type="b" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">
        Owner of the door may freely lock and unlock the door.
      </description>
    </property>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <signal name="ThresholdCrossed" sessioncast="true">
      <description>
        Signal to notify owner whenever anyone passes through the door.
      </description>
      <argument name="crossedInwards" type="b" direction="out">
        If true, someone entered; if false, someone left.
      </argument>    
    </signal>
  </interface>
  <interface name="com.example.Door.PublicDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door. Public interface that can be used by any consumer.
    </description>
    <method name="UnlockDoor">
      <description language="en">
        Allows guests with the code to unlock the door.
      </description>
      <argument name="passcode" type="u" direction="in">
        <description language="en">
          Current code (00000000 to 99999999) needed to unlock door
        </description>
      </argument>
      <argument name="welcomeMessage" type="s" direction="out">
        <description language="en">
          Message from the owner of the door.
        </description>
      </argument>
    </method>
    <method name="LeaveMessage">
      <description language="en">
        Leave a message for the owner of the door.
      </description>
      <argument name="guestName" type="s" direction="in">
        <description language="en">
          Name of guest leaving a message
        </description>
      </argument>
      <argument name="message" type="s" direction="in">
        <description language="en">
          Message left for owner of the door
        </description>
      </argument>
    </method>
    <method name="AnnouncePresence">
      <description language="en">
        Send a message to the owner of the door.
      </description>
      <argument name="announcingGuest" type="s" direction="in">
        <description language="en">
          Name of the guest announcing their presence.
        </description>
      </argument>
      <argument name="forcefulnessOfAnnouncment" type="y" direction="in">
        <description language="en">
          Degree to which the guest attempts to make their presence known, on bounds [1:10], where 1 is softly and 10 is aggressively.
        </description>
      </argument>
    </method>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <property name="Owner" type="s" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Owner of the door is public knowledge.
      </description>
    </property>
  </interface>
</node>
```

