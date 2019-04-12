---
title: Virtuelle Windows-Shields Arduino-Übersicht
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Informationen Sie zum Einrichten von virtuellen Windows-Shields für Arduino, und Erstellen Ihrer ersten Windows 10 IoT Core-app.
keywords: Windows Iot, WVSA, Windows Virtual Shields, Arduino-app
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513177"
---
> [!NOTE]
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="set-up-windows-virtual-shields-for-arduino"></a>Richten Sie virtuelle Windows-Shields für Arduino

## <a name="overview"></a>Übersicht
Wenn Sie verwendet haben eine [Arduino](https://www.arduino.cc), mit dem Konzept von einem Schild vertraut. Jede Shield verfügt über einen speziellen Zweck (z. B. eine Temperatur Shield, eine Beschleunigungsmesser Schild) kann, und erstellen ein Gerät mit mehreren Shields komplexe teuer und Speicherplatz – ineffizient. Stellen Sie sich nun vor, dass Sie einem kostengünstigen Windows Lumia-Telefon als eines kompakten Satzes von Greg verwenden können. Ihr Arduino-Sketches wäre auf Hunderte von Dollar sollte von Sensoren und -Funktionen in Ihrer Windows Phone über Aufrufe der leicht zu bedienenden Bibliothek zugreifen können.

Dies ist genau das, was für Entwickler der Windows virtuellen Shields für Arduino-Bibliothek aktiviert. Und das ist nicht das beste daran: Diese Technologie funktioniert auf allen Windows 10-Geräten, sodass Sie die Sensoren und Funktionen auf Ihrem PC oder Surface ebenfalls verwenden können. Darüber hinaus kann die Arduino rechenintensive Aufgaben wie die Spracherkennung und Analyse auf das Windows 10-begleitgerät Web Auslagern!

Erfahren Sie, wie Sie Hardware und Software zum Arbeiten mit virtuellen Windows-Shields für Arduino einrichten.


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1. Bereiten Sie Ihr Windows 10-Gerät für die Entwicklung von Projekten mithilfe von virtuellen Windows-Shields für Arduino.

Klicken Sie in diesem Abschnitt des Tutorials bereiten Sie ein Windows 10-Gerät Ihrer Wahl durch das Laden es mit der Windows virtuellen Shields für Arduino-Anwendung – diese universellen Windows-Anwendung können Sie Ihr Gerät als ein Schild"virtuellen" für ein Arduino-Board zu verwenden.  Dies führt einige leistungsstarken Möglichkeiten für Entwickler, nutzen die Spracherkennung, sodass touch Bildschirme und die rechenleistung von Windows mit relativ einfach.

### <a name="hardware"></a>Hardware
Der Windows virtuellen Shields für Arduino-Anwendung kann auf jedem Windows 10-Gerät ausgeführt, aber in diesem Tutorial wird erläutert, Setup mit einem Windows Phone.

*Was Sie* Windows Phone-Ausführen von Windows 10 – es wird empfohlen die [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) oder [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).

*Richten Sie Ihre Windows Phone*

Wenn Ihr Telefon nicht bereits Windows 10 ausgeführt wird, stehen die Optionen zum Installieren der Preview-Versionen der Software.  Windows Phone 8-Benutzern gelangen, die Microsoft Store-app, die Anwendung "Windows-Insider" herunterzuladen: Diese app kann der Benutzer zum Abonnieren von Windows 10 Technical Preview-Versionen als Updates empfangen.  Befolgen Sie die Anweisungen beim Öffnen der app, und fortsetzen Sie, sobald Ihr Telefon wurde erfolgreich auf Windows 10 ausgeführt wird.

### <a name="software"></a>Software

Es gibt zwei Optionen zur Installation der Windows virtuellen Shields für Arduino-UWP-app auf Ihrem Windows Phone.  Herunterladen der app ist die Wahl einfacher, schneller.

* Die app aus dem Microsoft Store herunterladen
* Sideloaden der app mit einem PC und Visual Studio

*Option 1: Die app aus dem Microsoft Store herunterladen*

Gehen Sie folgendermaßen vor [Link](https://www.microsoft.com/store/apps/9nblgggz0mld) klicken Sie auf der Seite der Microsoft Store für virtuelle Windows-Shields für Arduino, laden Sie die Anwendung, und installieren. Sie können dann öffnen, die Anwendung aus, um sicherzustellen, dass es ordnungsgemäß ausgeführt wird.  Ihr Gerät ist nun dafür eingerichtet, als ein Schild"virtual", die für einem arduino-Board verwendet werden.  Sie können mit der nächsten Seite fortfahren.

*Option 2: Sideloaden der app mit einem PC und Visual Studio*
_Voraussetzungen_
* Visual Studio 2017 zum querladen der Windows virtuellen Shields für Arduino-app auf einem Telefon Developer entsperrt.
* Dies [Repository](https://github.com/ms-iot/virtual-shields-universal) , die den Code für den virtuellen Windows-Shields für Arduino-Anwendung.  Klonen Sie das Repository oder Herunterladen Sie als ZIP-Datei auf dem lokalen Datenträger.  Wenn Sie nicht mit Git und möchten, führen Sie einen Klon der entsprechenden vertraut sind, befolgen Sie die Anweisungen [hier](https://help.github.com/articles/cloning-a-repository).

_Richten Sie Visual Studio 2017_
1. Installieren von Visual Studio 2017 mit dem Windows 10 Developer Preview-Tools von [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).  Es wird empfohlen, die kostenlose Community-Version von Visual Studio, jedoch als Enterprise und Professional würde auch funktionieren.  Wenn Sie bereits Visual Studio installiert haben, fahren Sie mit der im nächsten Schritt fort.
2. In Visual Studio laden die Shield.sln aus dem Repository heruntergeladen haben, in der "Voraussetzungen" weiter oben.
3. Stellen Sie sicher, dass Ihr Windows 10-Gerät (in diesem Fall eine Windows Phone) Developer entsperrt ist. [Auf dieser Seite](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) wird erläutert, wie zum Entsperren von Windows Phone 8.1, 8 und 7.1; allerdings die Schritte sind identisch für Windows 10-Smartphones.
4. Schließen Sie Ihr Windows 10-Gerät an Ihren Computer und Bereitstellen Sie des Programms Shield.sln auf Ihrem Gerät.  Zu diesem Zweck stellen für einen "Lokaler Computer", und achten Sie darauf, dass Sie die Architektur des Geräts wie "ARM" fest.
5. Führen Sie den neu installierten war virtuellen Windows-Shields für Arduino-Anwendung auf Ihrem Telefon, um sicherzustellen, dass die Bereitstellung erfolgreich.  Windows 10-Geräten ist nun dafür eingerichtet, als ein virtuelles Schild verwendet werden soll.

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2. Richten Sie Ihre Arduino, um der Windows virtuellen Shields für Arduino-Bibliothek verwenden 
Mit unserer begleitgerät für die Windows 10 ordnungsgemäß eingerichtet kommen wir unsere Arduino der Windows virtuellen Shields für Arduino-Bibliothek zu verwenden. Sie können eine Verbindung zwischen Ihrem Arduino und Ihren Windows 10 "virtuellen Schild" über USB, Bluetooth oder WLAN-einrichten. Dieses Lernprogramm wird erläutert, wie Sie das Setup über eine Bluetooth-Verbindung abgeschlossen, aber gerne Experimentieren mit den anderen Optionen.

### <a name="hardware"></a>Hardware
*Was Sie benötigen*
* Arduino Uno oder ein kompatibles Gerät
* Drähten
* Einen PC mit dem Ihr Arduino-Skizzen hochgeladen
* Standard A Standard B-USB - erforderlich, um einen groben Entwurf auf Ihrem Arduino-Gerät hochzuladen.
* Optional: Bluetooth-Modul – nur erforderlich, wenn Sie für die Verbindung von Bluetooth.
* Optional: Wi-Fi-Modul – nur erforderlich, wenn Sie wi-Fi-Verbindung herstellen möchten.

* Richten Sie Ihre Arduino
* Bereiten Sie die Bluetooth-Modul vor, bei Bedarf (das Bluetooth-Modul möglicherweise Header angelöteter).
* Mit Ausnahme der anderen unten aufgeführten, des Bluetooth-Moduls mit dem Arduino pro verbunden [im Diagramm verknüpfen](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).

  * Unterschied: Verwenden Sie anstelle von 2 und 3 Pins 0 und 1:
    * Die Bluetooth-TX PIN 0 (Arduino-RX oder RX0) eine Verbindung herstellen soll.
    * Die Bluetooth-RX PIN 1 (Arduino TX oder TX1) eine Verbindung herstellen soll.

### <a name="software"></a>Software
*Was Sie benötigen*
* Arduino IDE 1.6 oder höher
* ArduinoJSON-Bibliothek
* [Dieses Repository](https://github.com/ms-iot/virtual-shields-arduino), enthält die Beispiel-Skizze die auf der Arduino ausgeführt wird.

*Richten Sie Ihrer Arduino-IDE ein*
* Herunterladen und Installieren der Arduino-IDE, und starten Sie das Programm.
* Stellen Sie sicher, dass Sie die richtige Arduino-Board unter ausgewählt haben *Tools > Board*.
* Stellen Sie sicher, dass Sie den richtigen COM-Anschluss unter ausgewählt haben *Tools > Port*. Der Name des Boards, sollte neben jeder Option erleichtert, wählen Sie die richtige Option angezeigt werden.

*Einrichten der ArduinoJSON-Bibliothek*
* Von der [ArduinoJson Repository](https://github.com/bblanchon/ArduinoJson), ein Repository Klonen oder Herunterladen der ZIP-Datei.
* Platzieren Sie das gesamte Repository in Ihrem Ordner "Bibliotheken" (d. h. `Documents\Arduino\libraries\ArduinoJson\`).

*Einrichten der Windows virtuellen Shields für Arduino-Bibliothek*
* Klon [dieses Repository](https://github.com/ms-iot/virtual-shields-arduino) oder Laden Sie die ZIP-Datei herunter. Wenn Sie nicht mit Git und möchten, führen Sie einen Klon der entsprechenden vertraut sind, befolgen Sie die Anweisungen [hier](https://help.github.com/articles/cloning-a-repository/).
* Kopieren Sie den Ordner "VirtualShield", finden Sie in den Ordner "Arduino\Libraries" des Repositorys, die Sie gerade heruntergeladen, klicken Sie auf Ihrem Arduino-Ordner "Library haben" (d. h. `Documents\Arduino\libraries\VirtualShield\`).

*Ihre Einrichtung testen*
* Die Arduino-IDE, wechseln Sie zum Menüelement *Datei -> Beispiele für virtuelle Shield -> -> "HelloWorld"-Speech-Ereignisse*. Dadurch sollte der Spracherkennung basierend Hello World-Beispiel geladen, das wir für dieses Tutorial verwenden.
* Vor dem Hochladen der Skizze auf Ihrem Arduino, müssen entfernen Sie die Bluetooth-TX- und RX-verbindet vorübergehend aus der Arduino (ist nur eine serieller Anschluss, der die USB und Bluetooth - die Bluetooth gemeinsam mit dem Upload beeinträchtigt).
* Hochladen der Skizze durch Drücken der Schaltfläche "Upload" in der IDE.
* Ersetzen Sie den Bluetooth-TX- und RX einfach in die Arduino-Pins (Bluetooth TX Arduino RX (oder RX0) und Bluetooth RX Arduino TX oder (TX1)).
* Auf das Telefon (oder andere Windows-Geräte), die Sie auf der vorherigen Seite, mit dem Bluetooth-Gerät auf Ihrem Arduino in den Bluetooth-Einstellungen vorbereitet haben. Wenn Sie die BlueSMiRF verwenden, ist der Standard-Pin-Codes 1234. 

> [!NOTE]
> Die rote blinkende LED auf dem BlueSMiRF weiterhin nach einer erfolgreichen Kopplung rot blinken zu lassen. Dies ist das erwartungsgemäße Verhalten. Es wird nur Grün, nach der eine Verbindung mit der Windows virtuellen Shields für Arduino-Anwendung.


## <a name="3-write-your-first-app-hello-blinky"></a>3. Schreiben Sie Ihre erste app: Hello, Hauptverkaufsargument! 

### <a name="hello-world-speech-enabled-led-example"></a>Hello World-fähige Sprache LED-Beispiel
Mit Ihrer Windows Phone (oder möglicherweise alle Windows 10-Geräte) und Ihre Arduino, wie in den vorherigen Schritten in diesem Tutorial vorbereitet, nun können Sie unser Beispiel zu testen.

1. Bereiten Sie das Arduino-Board, indem Sie eine LED mit einem Widerstand PIN 8 einbinden.
2. Stellen Sie sicher, dass Ihre Arduino weiterhin mit dem Beispiel für die HelloWorld-Speech-Ereignisse hochgeladen wurde, und schließen Sie die Arduino an eine Stromversorgung.
3. Führen Sie die virtuellen Windows-Shields für Arduino-app, auf der Windows Phone, die Sie zuvor erstellt.
4. Wenn alles ordnungsgemäß eingerichtet wurde, sollte Ihr Telefon mit einem Arduino-Sketch verbinden und freuen uns, Sie mit einen audiohinweis. Sie können jetzt auf Ihrem Windows 10-Gerät wechseln die LED auf Ihrem Arduino zwischen ein- und ausschalten 'on' oder 'off' sagen!

### <a name="arduino-wiring-sketch-hello-world-example"></a>Arduino Sketch verknüpfen: Hello World-Beispiel

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


