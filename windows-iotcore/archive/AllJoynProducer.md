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
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="alljoyn-producers"></a>AllJoyn Producers

AllJoyn, erstellt die [AllSeen Alliance](https://allseenalliance.org/), bietet ein hervorragendes Framework aus, für die optimal für die Verwendung von AllJoyn mit verbundenen Geräten und apps in einem nächsten Netzwerk, und Windows stellt bereit. die [AllJoyn-Studio ](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) -Erweiterung für Visual Studio.  Unsere Tools excel über das Erstellen von apps für Producer und Consumer, kann ein neues AllJoyn-Gerät ganz von vorn beginnen Recht verwirrend sein.

Wenn Sie eine Idee für das nächste großartige verbundenen Gerät oder ein neues Spielzeug mit Basteln und zu durchsuchen, das, Sie haben verwenden die Standardschnittstellen angeboten, die von der AllSeen Alliance möglicherweise nicht.  Wenn dies der Fall ist, müssen Sie zum Erstellen eines neuen AllJoyn Producers.

Muss ein Entwickler, die möchten, stellen einen neuen AllJoyn Producer eigene Introspection XML zu erstellen, aber benötigt die entsprechenden Fachkenntnisse und verfügt über eine erhebliche Lernkurve für neue Entwickler Introspection XML erstellen.  Diesem Blogbeitrag werden die Lernkurve senken, indem Sie unterteilen die verschiedenen Komponenten der Introspection-XML, beschreibt den Zweck und die Einschränkungen der einzelnen Komponenten und bereitstellen, gute Beispiele für intuitiv ausgedrückt werden kann.

## <a name="existing-documentation"></a>Vorhandene Dokumentation

Eine oberflächliche Untersuchung die folgenden Ressourcen zusammen mit diesem Blogbeitrag sollten Entwickler beschleunigen des Introspection XML-Codes zu verstehen:

1. [Dass AllJoyn-Ereignisse und Aktionen für die-API](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn Implementierungsdetails und (Übersicht).
2. [AllJoyn Benutzeroberflächen-Entwurfsrichtlinien für Review Board](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -strenge strukturieren und für AllJoyn Introspection XML-Spezifikation.
3. [D-Bus-Spezifikation](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn verwendet als Basis für Introspection XML in dieser Spezifikation.

__Die drei Typen von Introspection-XML__

Wie Sie genau, dass AllJoyn-Dokumentation durchlesen, finden Sie drei Arten von Introspection XML:

1. D-Bus-Spezifikation XML: mit geringem Verwaltungsaufwand, prozessübergreifende Kommunikation mit einem Typformat zur Darstellung von Daten.
2. AllJoyn Introspection XML: erweitert die D-Bus-Spezifikation XML mit XML-Tags zur Aufnahme von textbeschreibungen beim Anwenden der AllJoyn Prinzipien auch mit der Spezifikation.
3. Erweiterte AllJoyn Introspection XML: Entwicklung von klassischen Einführung in der Introspection-XML-benannte Typen für Strukturen und Wörterbücher.

AllJoyn Studio unterstützt derzeit die XML-Spezifikation der D-Bus "und" AllJoyn Introspection XML; Dieser Blog bestimmen, das Erstellen, und dass AllJoyn Introspection XML zu bilden.  Der AllSeen-Allianz Schnittstelle Review Board (IRB) verwendet die neue erweiterte AllJoyn Introspection als Format für formale Übermittlungen für die Überprüfung der Standardisierung aber arbeitet an einem einheitlichen Introspection XML-Format für die nahe Zukunft.

## <a name="introspection-high-level-overview"></a>Allgemeiner Überblick über Introspection

Jede AllJoyn Producer kündigt öffentlich Introspection XML, auf der Producer die unterstützten Funktionen – Schnittstellen als beschrieben über Signale, Eigenschaften und Methoden.  Lösungen mit Code Generation, wie in der Erweiterung AllJoyn Studio basieren auf Introspection-XML mit den erforderlichen Code zum Beschleunigen der Entwicklung zu erstellen.  Introspection XML beschreibt die Funktionalität von einem Producer in eine nicht-mehrdeutigen, lesbare Möglichkeit, so, dass zwei unterschiedlicher Hersteller den XML-Code verwenden können, um ein Producer mit denselben Funktionen zu implementieren.  Mithilfe desselben Tokens, sollten Entwickler ohne vorherige Kenntnis von einem Producer AllJoyn, basierend auf der XML-Producer verwenden können.

__Dass AllJoyn-Schnittstellen__

AllJoyn erreicht dies durch die Aufteilung von Introspection XML in verschiedenen "Interfaces", die verschiedene logische Gruppierungen von Verhalten und die Funktionen darstellen.  Dass AllJoyn-Schnittstellen werden mithilfe einer Reverse-DNS-Konvention benannt. Die Schnittstelle "Foo"-Schnittstelle, die von Contoso Ltd., der die Domäne "contoso.com" besitzt, erstellt würde beispielsweise folgendermaßen geschrieben werden:

    <interface name="com.contoso.Foo">

Ein Producer kann eine beliebige Anzahl von Schnittstellen implementieren, aber Sie müssen jede Komponente einer Schnittstelle, die sie ankündigen implementieren.  Um zu unterscheiden, und erweitern Verhaltensweisen, unterstützten AllJoyn erstellen neue Schnittstellen in Bezug auf eine vorhandene Schnittstellenhierarchie d. h. `com.contoso.Foo.Bar` definiert neue Funktionen für die Schritte unter der `Foo.Bar` Kategorie jedoch keine expliziten Abhängigkeiten nicht auf die `com.contoso.Foo` Schnittstelle. 

Beispielsweise haben wir zwei Schnittstellen: `com.contoso.Sensor` und `com.contoso.Sensor.Humidity` – "Luftfeuchtigkeit" wird logisch unter der Kategorie "Sensor" liegt.  Jemand die Entwicklung von einem Producer Luftfeuchtigkeit können unterstützen nur die `com.contoso.Sensor.Humdity` -Schnittstelle, aber sie können auch zur Unterstützung der `com.contoso.Sensor` Schnittstelle.  Unabhängig davon, wenn sie eine Schnittstelle ankündigen, müssen Producer alle zugehörigen Funktionen unterstützen.

Die `<description>` Tag wird verwendet, um die Schnittstellen, Funktionen und Argumente zu beschreiben und für verschiedene Sprachen lokalisiert werden kann.  Der großzügigen Verwendung von der `<description>` Tag stellt den XML-Code leichter verständlich und Mehrdeutigkeiten entfernt.

Standardverfahren bestimmt die Verwendung der `org.alljoyn.Bus.Secure` Anmerkung für eine Schnittstelle für die Sicherheit und Authentifizierung zu aktivieren.  Verwenden Sie für eine strenge Authentifizierung einem vorinstallierten Schlüssel (PSK) oder ein Zertifikat Schlüsselaustausch (ECDSA) aus.  Andernfalls wird eine "null"-Authentifizierung das Standardverhalten.  **Der tatsächliche Authentifizierungsmechanismus geschieht in der Implementierung nicht die Deklaration**. Diese Anmerkung bietet Sicherheit aber keinen der angegebenen verwendeten Sicherheitstyp oder wie sie implementiert werden.

___Beispiel___

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

Dieses Beispiel zeigt eine Schnittstelle, die von einem Gerät verfügbar gemacht werden: `com.example.Door.PrivateDoor`. Im Bereich der Schnittstelle ist alles, was wir Sorgen machen, ob die Kommunikation geschützt werden sollen, wenn es sich bei Verwendung dieser Schnittstelle, welche Art von Mechanismus nicht verwendet wird.

__Interface-Funktionen__

Schnittstellen deklarieren, deren Funktionen mit drei Schnittstellenmember: Methoden, Eigenschaften oder Signale. Introspection XML unterstützt auch Anmerkungen, die zusätzliche Funktionen oder Einschränkungen zu beschreiben.  Diese Funktionen verwenden UpperCamelCase-Notation, während Argumente LowerCamelCase Notation verwenden.

### <a name="argument-types"></a>Argumenttypen

Schnittstellenmember senden und Empfangen von Argumenten, die durch ein ASCII-Typ-Code gekennzeichnet.  Je nach Art der Schnittstellenmember, Argumente können haben werden gesendet, um den Producer vom Consumer (Richtung "out" =) oder auf der Producer-Consumer (Direction = "ins").  Die folgende Tabelle enthält eine Kurzübersicht über häufig verwendete Typen:

> | *Herkömmliche Name* | *Type-Code* | *Verwendung* |
> |----------------- |---------| --- |
> |**BOOLEAN** | b) | "True" (1) oder "false" (0) darstellt. Für einfache binäre Informationen oder Zustände verwendet. |
> |**BYTE** | y | Integer-Wert von 0 bis 255. Beim Umgang mit kleinen positive Zahlen verwendet. |
> |**UINT16** | q | Ganzzahliger Wert zwischen 0 und 2 ^ 16-1 |
> |**UINT32** | u | Ganzzahliger Wert zwischen 0 und 2 ^ 32-1 |
> |**UINT64** | n | Ganzzahliger Wert zwischen 0 und 2 ^ 64-1 |
> |**INT16** | m | Ganzzahliger Wert zwischen –(2^15) und 2 ^ 15-1 |
> |**INT32** | i | Ganzzahliger Wert zwischen –(2^31) und 2 ^ 31-1 |
> |**INT64** | x | Ganzzahliger Wert zwischen –(2^63) und 2 ^ 63-1 |
> |**DOUBLE-WERT** | d | Genauigkeit Gleitkommazahlen aus –(2^127) auf 2 ^ 127-1 |
> |**ZEICHENFOLGE** | s | UTF-8-Zeichenfolge |
 
Einen umfassenderen Überblick über alle unterstützten Typen finden Sie unter [hier](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).

Während ich dies schreibe, verwenden Sie SI-Einheiten, wenn möglich, und kennzeichnen Sie beabsichtigte Einheiten klar zu. Wählen Sie wenn möglich, den den Typcode für Ihr Szenario am stärksten einschränkende; z. B. Wenn Sie einer Person-Alter in Jahren darstellen, verwenden Sie BYTE, nicht UINT16 oder Int16-Wert, da niemand eine negative Alter oder mehr als 255 Jahre alt sein wird.  Führen Sie immer die neueste Version [AllJoyn Schnittstelle Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) Richtlinien.

In der folgende Tabelle werden allgemeine Einheiten zusammengefasst:


> |*Anzahl* | *Einheit*|
> |-------- | ---- |
> |**Absoluten Zeitpunkt (Datum und Uhrzeit)** | Sekunden seit der UNIX-Epoche (00: 00:00 auf 1. Januar 1970) |
> |**Tageszeit** | Sekunden seit Mitternacht |
> |**Zeitintervall** | Sekunden |
> |**Bandbreite** | Bits pro Sekunde |
> |**Datengröße** | Bytes |
 
### <a name="methods"></a>Methoden

Consumer Methoden aufrufen, um den Status von einem Producer ändern, und ihre Namen sollten mit einem Verb beginnen, da sie die Anforderungen der Producer zum Ausführen einer Aktion darstellen.  Methoden können Eingabe- und Ausgabe der Argumente. Wenden Sie in der Fall, den keine Antwortnachricht zurückgesendet werden muss die Anmerkung "org.freedesktop.DBus.Method.NoReply".  Allerdings zurückgeben AllJoyn Methoden normalerweise eine SuccessResult oder eine FailureResult, haben Kunden-Feedback über den Methodenaufruf.  Der Typ der Argumente muss einhalten, die [D-Bus-Spezifikation](http://dbus.freedesktop.org/doc/dbus-specification.html). 

___Beispiel (mit Ausnahme von Informationen der Einfachheit halber Schnittstelle)___

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

*Hinweis: In den meisten Fällen Eigenschaften sollten Sie zum anstelle von Methoden des Herstellers Zustand zugreifen (z. B. eine Color-Eigenschaft anstelle einer GetColor-Methode verwenden).*

### <a name="properties"></a>Eigenschaften

Eigenschaften können vor allem den Zugriff auf ein Producer Zustand.  Während Eigenschaften technisch Zugriffswerte haben "gelesen", "Readwrite" oder "Schreiben", Status ändernden Funktionen in der Regel gehört, auf Methoden – daher, Entwickler sollten sich bemühen, behalten Sie die Eigenschaften als "Lesen" und "Readwrite" nur, wenn der Status dargestellt Somit ist die Eigenschaft unabhängig von allen anderen Eigenschaften.  Eigenschaften sollten nie einfach "write" – Ändern des Zustands ohne Beobachtung ist die Rolle der Methoden.

Eigenschaften müssen für Warnung Consumer gekennzeichnet werden, wenn sich ihre Werte ändern (optional Eigenschaften können diese Anmerkung von erben ihre übergeordnete Schnittstelle).  Die Anmerkung `org.freedesktop.DBus.Property.EmitsChangedSignal` kann vier Werte haben:

* Wenn die Eigenschaft geändert wird, wird der Producer "true" – ein Signal, das die geänderte Eigenschaft und den neuen Wert, der angibt ausgeben. In den Eigenschaften, die häufig verwendet werden und erfordern active Aufsicht, wie z. B. eine "LockState" für eine Tür verwendet.
* "ungültig" – bei der Änderung der Eigenschaft, der Producer ein Signal, der angibt, aber nicht der neue Wert der geänderten Eigenschaft ausgibt. Für Eigenschaften verwendet, die keine hohe Aufsicht (z. B. die "WashMode" von einem Trockner Kleidung) erfordern oder einen Großteil der Daten, z. B. einen Container darstellen.
* Wenn die Eigenschaft geändert wird, gibt der Producer "false" – kein Signal aus. Für Eigenschaften verwendet, die schnell, wie z. B. eine Eigenschaft "TransitCounter" ein Ausfall von u-Bahn-Drehkreuz, das Verwalten von Personen, die den Ausfall von u-Bahn boarding aktualisieren. Falls nicht angegeben, verwendet dass AllJoyn-Eigenschaften als standardmäßig.
* "const": die Eigenschaft Wert nie ändern und niemals ausgeben ein Signals geändertes wird. Dies wird in der Version AllJoyn 16.04; eingeführt wurden Verwenden Sie bis dahin "true".

___Beispiel___

Erweitern auf dem vorherigen Beispiel, haben wir der XML-Code enthalten Eigenschaften, die (mit Ausnahme der Methoden aus Gründen der Übersichtlichkeit) geändert.

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

### <a name="signals"></a>Signale

Verwendung signalisiert Consumer eines Ereignisses zu informieren, die sie durch Abfragen den Producer nicht ermitteln konnte.  Eine Tür geöffnet wird durch ein Producer DoorOpen-Eigenschaft mit einer Anmerkung für "true" EmitsChangedProperty vermittelt werden.  Ein Benutzer die Haustür übergeben kann nicht jedoch von alle eigenschaftenänderungen, abgeleitet werden, damit dies ein guter eigenständige Signal machen würden.  Wir bezeichnen diese Art der Ereignisse bei dem "zustandslosen".  Da Signale vom Producer an Consumer unidirektional sind, können sie nur "out" Argumente enthalten.

___Beispiele___ 

(mit Ausnahme Methoden und Eigenschaften der Einfachheit halber):

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

Da Signale solche eine eng gefasste Gültigkeitsbereich haben, angezeigt werden in der Regel nur wenige in ein Producer XML-Datei.

### <a name="containers"></a>Container

Kombinieren Sie mehrere Argumente nicht in eine komplexe Sammlung wie eine serialisierte JSON-Zeichenfolge. Die D-Bus-Spezifikation stellt visueller Hinweise für den Container für Daten: die Struktur "," ARRAY "," VARIANT "und" DICT_ENTRY.  Verwenden Sie diese Option, um Argumente zu übergeben, die mehr als grundlegende Typen erfordern.

___VARIANT___

Varianten werden vom Typ "V" gekennzeichnet und können nicht enthalten [vollständige Typ](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type). Allerdings sollten Varianten nach Möglichkeit vermieden werden, da sie die Mehrdeutigkeit zu XML-Definitionen hinzufügen.

___STRUKTUR___

Verwenden von Strukturen "(" und ")" zur Angabe der Anfang und Ende einer Datenstruktur – nur vollständig ein.  Diese Datenstrukturen können geschachtelt werden.

Beispiele:

Ein Typ von "(Iii)" gibt an, eine Struktur von drei ganzen Zahlen; "(i(ii))" gibt an, eine Struktur einer ganzen Zahl und eine Struktur von zwei ganzen Zahlen, die aus dem Typ unterscheidet, ist "((Ii) ich)".

___ARRAY___

ARRAYs verwenden, den den Typcode "a" und muss nur vollständige ein folgen.  ARRAYs müssen nicht Satz Länge und, damit sie sich auf eine Datenstruktur Liste ähneln. ARRAYs stellen einen einzelnen vollständigen Typ dar.

Beispiele:

Ein Typ von "Ai" stellt ein ARRAY von ganzen Zahlen dar, während "Aai" ein ARRAY eines Arrays von ganzen Zahlen darstellt.  Ein ARRAY kann auch mit Strukturen verwendet werden: "lebender".

___DICT_ENTRY___

DICT_ENTRYs-Funktion, die auf eine Struktur mit mehr Einschränkungen ähnlich wie: Verwenden sie "{" und "}" kann nur auftreten, als einen Elementtyp des Arrays und müssen genau zwei Typen in den geschweiften Klammern abzuschließen.  Der erste Typ stellt einen "Schlüssel" in einer Datenstruktur Wörterbuch und die Sekunde darstellt, die "Value" in das Wörterbuch der Schlüssel / Wert-Paar.  Ein Schlüssel sollte in einem Wörterbuch eindeutig sein.

Beispiel:

Ein Typ von einem {Sy} gibt ein Wörterbuch mit Zeichenfolgenschlüsseln und Byte-Werte an.  Verwendung <description> die Tags auf gültige Schlüssel und Werte beschrieben werden. 

__Letzte Beispiel und ajxmlcop__

Das Konzept von Containern verbessert die Funktionen von den vorhandenen XML-bereit sowie eine Möglichkeit für neue nützlich Schnittstellenmember.

Sobald Sie fertig sind, der XML-Code schreiben, verwenden Sie das Befehlszeilentool ajxmlcop.exe (verfügbar unter der AllJoyn [Git Source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) oder [hier](https://github.com/MS-brock/AllJoynToasterDemo)) zum Überprüfen des XML-Codes.  Ajxmlcop.exe mit Ihrer XML-Datei als das Eingabeargument verwenden (z. B. `C:\>ajxmlcop.exe doorExample.xml`) zum Empfangen von Fehler-, Warn- und informationsmeldungen.  Dieses Tool bietet wertvolles Feedback hinsichtlich der Struktur und die XML-Format und Verwendung von Signalen, Eigenschaften und Methoden.

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

