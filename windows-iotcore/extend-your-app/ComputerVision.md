---
title: Maschinelles sehen
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Microsoft Cognitive Services und OpenCV für Ihr IoT-Gerät verwenden.
keywords: Windows Iot, maschinelles sehen, Cognitive Services, OpenCV
ms.openlocfilehash: f6d10024f0f52f7219eb3a63dcefa7fd2b4a6fe3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512681"
---
# <a name="computer-vision"></a>Maschinelles sehen

Menschen wahrnehmen in unserem dreidimensionalen relativ einfach. Beginnend mit frühen Alter, können unsere Köpfe und wertvolle Einblicke, wie z.B. Feature Kennung Hindernis Avoidance, Koordination, Wahrnehmung der Tiefe und vielen anderen visuellen Effekte sammeln. Maschinelles sehen wird versucht, die Prozessoren und Kameras verwenden, um das gleiche tun. Er hat unzählige Anwendungen für Geräte. Eine drohne können sie schnell erkennen und Hindernisse während des Flugs vermeiden. eine Factory, die es verwenden kann, um kosmetische Fehlern in den kleinsten Komponenten am Fließband zu erkennen; und eine Person können sie seine Herzfrequenz ohne Verwendung eines Monitors oder der Doktor Ausrüstung zu erkennen. Datenschwerpunkt in unserem wurde Computer, die einen Bereich sehr aktiv geforscht für maschinelles sehen. Unternehmen nutzen es gibt Möglichkeiten, die als unwahrscheinlich sogar zehn Jahren. Wie der Computer, Kameras und Daten wird mehr in unsere Gesellschaft verankert, soll Tools für maschinelles sehen die interessantesten Funktionen nutzen erfolgen einfach darauf zugreifen und wie möglich verwenden. Windows 10 IoT Core wird versucht, diese Anforderung über die Kompatibilität mit zwei Angebote zu erfüllen: Microsoft Cognitive Services und OpenCV.

## <a name="services"></a>Dienste
___

### <a name="cognitive-services"></a>Cognitive Services

#### <a name="overview"></a>Übersicht
Cognitive Services, ursprünglich ein Microsoft Research-Projekt namens Project Oxford, ist eine Sammlung von APIs, die allgemeine "kognitive" Aufgaben. Diese APIs rufen Sie Einblicke in Ihre Daten basierend auf hoch trainiert Machine learning-Modelle basierend auf jahrelangen untersuchungs-und Entwicklungsphase von Microsoft Research.

Cognitive Services besteht aus 5 Kategorien: Bildanalyse, Spracherkennung, Sprachen, wissen und Suche.

Sie finden weitere Informationen zu Cognitive Services für die Cognitive Services [Website](https://www.microsoft.com/cognitive-services).

Die maschinelles sehen-Kategorie die wertvollsten Kategorie für Anwendungen für Computer Vision, enthält vier APIs: Maschinelles sehen, Emotions-, Gesichts- und Video. Diese APIs bieten folgende Funktionen:
- Gesichtserkennung
- Bewegungserkennung
- Zur Erkennung von Emotionen
- Videostabilisierungs
- Bildanalyse-Inhalt

Cognitive Services eignen sich hervorragend für die Arbeit mit großen Anteil der Daten, den Zugriff auf Microsoft Azure und erheblich reduzieren Sie der Anwendung Zeit bis zur markteinführung, wie oft die maschinelles sehen-APIs sich als zeitaufwändig, die unabhängig entwickelt werden. Diese APIs verwendete Modell ist gut ausgebildetem und umfassende Dank die bestrebungen von Microsoft Research. Auf der anderen Seite der Anforderung an die Cloud Konnektivität reduziert die Systemleistung und erstellt die Anforderung für eine Internetverbindung besteht.

#### <a name="pricing"></a>Preise
Jedes API-Abonnement enthält eine Reihe von kostenlose Transaktionen jedes Monats (300 zu 30.000, abhängig von der API). Kommen nach diesem anfänglichen den Grenzwert übersteigt, die Dienste mit einem vernünftigen Preis. Beispielsweise wird der Emotionen-API stellt die ersten 30.000 Transaktionen zur freien und erfordert 0,10 US-Dollar oder geben Sie jede Transaktion 1000, je nach Abonnement 0,25 USD.

Weitere Informationen zu den Preisen von Cognitive Services befindet sich auf ihre [Website](https://www.microsoft.com/cognitive-services/en-us/pricing).

#### <a name="get-started"></a>Erste Schritte
Um die Cognitive Services verwenden zu können, müssen Benutzer auf der Cognitive Services-Website registrieren Sie sich zum Empfangen von API-Schlüssel. Nachdem Sie einen API-Schlüssel für Cognitive Services haben, können Benutzer die APIs in im Abschnitt "Preise" beschriebenen Einschränkungen aufrufen.

Dokumentation für jede API finden Sie auf der Cognitive Services [Website](https://www.microsoft.com/cognitive-services/en-us/documentation).

Alle Cognitive Services-APIs können implementiert werden, auf jeder Plattform mit Hardware C#.

Cognitive Services auf Ihrem IoT-Gerät ausgeführt werden soll? Besuchen Sie unsere [Tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices) für den Einstieg.

### <a name="opencv"></a>OpenCV

OpenCV ist ein open-Source-maschinelles sehen und Machine learning-Softwarebibliothek für Compute-Effizienz und echtzeitanwendungen entwickelt wurde. Es ist häufig gängige für Entwickler und in der Branche, aufgrund dessen noch nie da gewesene Effizienz, die vielseitige Tools, die Unterstützung für eine Vielzahl von Plattformen und sehr aktives online-Community von Entwicklern. Es ist bei weitem der am häufigsten verwendeten open Source Computer Vision-Tool. OpenCV-Bibliotheken stehen für C /C++, Java und C#.

Die OpenCV [Website](http://opencv.org/) finden Sie weitere Details.

OpenCV-Features:
- Lokales Image und Verarbeitung von Videoinhalten und-Analyse
- Real-Time-Objekt-ID, Abgleich und Nachverfolgen
- Real-Time-gesichtserkennung
- Abstand Bestimmung aus Image und in Echtzeit
- 3D Zuordnung/Modellierung/Rekonstruktion
- Bild bearbeiten (z. B. Zusammensetzung und Farbe ändern)

OpenCV bietet eine Reihe von Vorteilen. Es ist sehr effizient, für die lokale Verarbeitung von Daten aufgrund des optimierten C /C++ Interna und den Zugriff auf die GPU mithilfe von OpenCL (sofern aktiviert). Sie enthält die meisten, wenn nicht sogar alle Computer Vision-Funktion ist derzeit verfügbar. Die Langlebigkeit und das Dienstprogramm verfügt über eine umfangreiche und erfahrene online-Community, die neuen Benutzer mit der Anwendung oder Bibliothek Probleme kann gebildet. Andererseits, besteht eine steile Lernkurve aufgrund der komplexen Code und Bibliothek Setup sowie die Inkonsistenzen in den Tutorials und Beispielcode.

So funktioniert derzeit OpenCV mit IoT Core nur auf, wenn der Benutzer die Source-Bibliothek erstellen, die sehr zeitraubend sein kann. Aus diesem Grund sind wir aktiv daran, um OpenCV unter IoT Core einrichten, indem eine Auflistung von NuGet-Pakete für sie erstellen zu vereinfachen. Ein NuGet-Paket, dem Cognitive Services verwendet wird, kann Entwickler eine vorgefertigte Bibliothek in ihrer Anwendung, die vollständige Funktionalität bereitgestellt, mit wenigen Klicks zu importieren. Die Anwendung, die mithilfe des NuGet-Pakets wird weiterhin von einem dedizierten Server Library-Updates zu erhalten; der Benutzer muss sich nicht um neue Quellcode bei öffentliche Änderungen für die open-Source-Software neu zu erstellen. Das Paket muss auch den Speicherplatz auf Geräten, die nur über Teile der Bibliothek.

Dies ist derzeit noch In Bearbeitung, sodass WindowsOnDevices.com eine Suche nach Updates zu halten.

Um die Bibliothek aus der Quelle für ARM erstellen, in der Zwischenzeit finden Sie auf die [GitHub-Repository](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM).

OpenCV auf Ihrem Gerät IoT Core ausgeführt werden soll? Besuchen Sie unsere [Tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/opencv) für den Einstieg.

## <a name="comparing-opencv-and-cognitive-services"></a>Vergleichen von OpenCV und Cognitive Services

> |        |Microsoft Cognitive Services|OpenCV|
> |---------------------|--------|------|
> |Einfach zu verwenden, auf Windows|Ja|Nein |
> |Architekturunterstützung|ARM, x86, x64 | ARM, x86, x64|
> |Gesichtserkennung und -nachverfolgung| Ja | Ja|
> |Zur Erkennung von Emotionen| Ja | Ja|
> |3D Wiederaufbau und Zuordnung| Nein | Ja|
> |Erkennung von Inhalt| Erkennt bestimmte Objekte, anstatt allgemeine Funktionen | Ja|
> |Videostabilisierungs| Ja | Ja|
> |Bewegungserkennung| Ja | Ja|
> |Community| Cognitive Services ist vielen aktive Benutzern über mehrere Branchen und einige beliebte Websites, einschließlich How-old.NET und celebslike.me | OpenCV ist ein sehr beliebtes Open Source-Projekt. Tausende von Personen beigetragen haben, und es beibehalten|
> |Dokumentation| Cognitive Services verfügt insgesamt über klare und ausführliche Dokumentation | Es sind viele Beispiele online verfügbar, aber jedes Beispiel wird von einer anderen Person geschrieben und daher kann inkonsistent gelegentlich|
> |Free| Ja, um einen Block den Wert (Weitere Details [hier](https://azure.microsoft.com/pricing/details/cognitive-services/)) | Ja|
> |Leistung| Alle Vorgänge und API-Aufrufe benötigen Zugriff auf Daten in der cloud | Alle Algorithmen sind optimiert und lokalen sowie mit C++ statt Python Geschwindigkeit sogar noch weiter erhöht|
> |Unterstützte Kameras/hardware| Alle USB- oder embedded Kamera | Alle USB- oder embedded Kamera|
> |Unterstützte Sprachen bzw. frameworks| C#, UWP | C /C++, Python, Java, C#, UWP|
> |Startzeit| Benutzer können Codebeispiele mit intuitiven APIs direkt in der Dokumentation verwenden. | Der OpenCV Leistungsfähigkeit und Flexibilität bedeutet, dass es sich bei es sind auch viele der Konfiguration und der Code für komplexe Vorgänge erforderlich|
> |Links| [Beispielprogramm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [Beispielprogramm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [Cognitive Services-Website](https://azure.microsoft.com/services/cognitive-services/) |  [OpenCV-Website](http://opencv.org/)


