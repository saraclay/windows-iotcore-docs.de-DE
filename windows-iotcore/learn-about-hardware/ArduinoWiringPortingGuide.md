---
title: Verknüpfen der Leitfaden zur Portierung Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zu Änderungen und häufige Probleme, die wieder bei der Bereitstellung von Projekten Arduino verknüpfen.
keywords: Portieren von Windows Iot, Arduino, verknüpfen, Visual Studio
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512418"
---
# <a name="arduino-wiring-porting-guide"></a>Verknüpfen der Leitfaden zur Portierung Arduino

Verknüpfen von Arduino Skizzen und Bibliotheken können auf Raspberry Pi 2- oder Raspberry Pi 3 mit Minnowboard Max in einem Projekt verknüpfen Arduino in Visual Studio kopiert und eingefügt und ausgeführt werden. Es gibt gelegentlich geringfügige Änderungen, die auf diese Dateien vorgenommen werden, damit sie besser kompatibel mit der Windows-Umgebung können müssen, oder das Board, mit denen, dem Sie arbeiten werden. Dieses Handbuch befasst sich diese Änderungen sowie häufige Probleme, denen Sie stoßen eventuell bei der Bereitstellung von Projekten Arduino zu verknüpfen.

## <a name="porting"></a>Portieren

### <a name="updating-pins"></a>Aktualisieren die Pins

Es versteht wechseln kann, aber viele Skizzen und Bibliotheken (insbesondere über diejenigen für Arduino-Shields) enthält Verweise auf bestimmte Anschlussstifte für Arduino-Geräte. Sie sollten zum Anpassen Ihrer Skizzen, um die entsprechenden Connector Pins zu verwenden, für das Gerät, dem Sie bearbeiten und die Konfiguration, die Sie verwenden.

Verknüpfen von Arduino erfordert eine Pin-Nummer des physischen Connector letztlich für alle Funktionen, die auf "Pins" verweisen. Sie können diese Werte direkt verwenden, aber haben wir auch einige vordefinierte Pin-Namen die Anschlussstifte auf bestimmte Boards entsprechen bereitgestellt.

Die physischen Connector-Pin-29 auf einem Raspberry Pi 2 und 3 ist z. B. auch bekannt als `GPIO5`. Sie können GPIO-Pins 5 auf einem Raspberry Pi 2 und 3 in einen Zustand hoch festlegen, mithilfe der folgenden Befehle:
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

oder

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

Die vordefinierte Pin-Namen finden Sie im [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) und integriert in jedem Projekt Arduino verknüpfen, aber da es verschiedene physische Anschlussstifte abhängig von der Hardware-Einrichtung stehen für Sie erstellen, haben wir ebenfalls enthalten, eine Tabelle zum Beschreiben der Pin-Namen für jedes Gerät verfügbar sind.

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 und 3

![Pinouts-Diagramm](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | Definieren Sie die PIN | Zugehörige Pin-Nummer|
> |-------------|----------|
> | LED_BUILTIN | *Integrieren der LED* |
> | GPIO * _, in denen * bezieht sich auf [0, 27]_ | *Pinouts Diagramm finden Sie unter* |
> | GCLK | 7 |
> | GEN * _, in denen * bezieht sich auf [0, 5]_ | * finden Sie unter Pinouts-Diagramm |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (oder CE0 oder SS) | 24 |
> | CS1 (oder CE1) | 26 |
> | SCLK (oder SCK) | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard Max

![Pinouts-Diagramm](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | Definieren Sie die PIN | Zugehörige Pin-Nummer|
> |-------------|----------|
> | GPIO * _, in denen * bezieht sich auf [0, 9]_  | *Pinouts Diagramm finden Sie unter* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 (oder CE0 oder SS) | 5 |
> | SCLK (oder SCK)| 11 |
> | MISO |7 |
> | MOSI | 9 |
> | CTS1 | 10 |
> | RTS1 | 12 |
> | RX1 | 8 |
> | TX1 | 6 |
> | RX2 | 19 |
> | TX2 | 17 |


## <a name="common-problems"></a>Häufige Probleme

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>Wurde nicht gefunden "Arduino verknüpfen die Anwendung" Visual C++ Projektvorlage in Visual Studio

**Ursache**: Die Projektvorlagen für Windows-IoT-Erweiterung für Visual Studio ist nicht installiert.

**Lösung**: Sie müssen die Visual Studio-Erweiterung für Windows IoT-Projektvorlagen installieren, bevor Sie Verknüpfen von Arduino-Projekte in Visual Studio erstellen können. Wechseln Sie zu [Windows IoT Core-Projektvorlagen-Erweiterungsseite](https://go.microsoft.com/fwlink/?linkid=847472) auf die Erweiterung von Visual Studio Gallery herunterladen!

### <a name="error-identifier-not-found-when-calling-a-function"></a>Fehler: "Bezeichner wurde nicht gefunden" beim Aufrufen einer Funktion

**Ursache**: Dieser Fehler tritt während des Prozesses der Linker auf, wenn eine Funktion aufgerufen wird, die noch nicht im Dokument deklariert wurde.

**Lösung**: In C++, alle Funktionen müssen deklariert werden, bevor sie aufgerufen werden. Wenn Sie eine neue Funktion in der Sketch-Datei definiert haben, muss entweder der Deklaration oder die gesamte Implementierung der Funktion über alle Versuche für die aufzurufende (in der Regel am oberen Rand des Dokuments) sein.

**Beispiel**:

Der folgende Codeblock löst den Fehler ""MyFunction": Bezeichner wurde nicht gefunden"

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

Es gibt zwei Lösungen. Zunächst können Sie die Funktion über alle Aufrufe deklarieren. Diese Deklaration ist in der Regel am Anfang der Datei durchgeführt.

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

Alternativ können Sie die gesamte Implementierung der Funktion über alle Aufrufe verschieben. Dies wirkt sich das Deklarieren und Definieren der Funktion zur gleichen Zeit aus.

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>Meine Lösung hängt, unendlich, bei der Initialisierung

Es ist ein bekanntes Problem kann dadurch eine C++ Lösung unendlich, nicht mehr reagiert (Deadlocks), bei der Initialisierung. Sie können diese Art von Problem auftreten, wenn Sie feststellen, dass Ihre Projektmappe befindet sich ewig und Sie nicht den Debugger zu verwenden, um "jede Anweisung in den Abschnitten setup() oder loop() Ihrer Anwendung Arduino verknüpfen".

**Ursache**: Ein Objekt erstellt wird, oder eine Funktion wird aufgerufen wird, was zu einer Aktion für den asynchronen führt, bevor die Projektmappe vollständig initialisiert wurde. Es wird wahrscheinlich von eines Objekts-Konstruktor aufrufen einer API-Funktion wie verursacht `pinMode`.

**Lösung**: Verschieben Sie keine Objektkonstruktoren und Funktionsaufrufe von Abschnitts für Initialisierung von Code und in der `setup()` Block.

**Beispiel 1**:

Die Ausführung von dieser Version aufruft, eine Funktion namens `setPinModes()` vor die Lösung selbst initialisiert wurde. Die Lösung scheinbar, ausführen, jedoch wird unendlich hängen.

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

Die Lösung unterschreitet, haben wir einfach die Ausführung von verschoben `setPinModes()` auf die `setup()` Funktion:

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

**Beispiel 2**:

Die Ausführung von dieser Version erstellt ein Objekt, auf dem Stapel vor dem `setup()` aufgerufen wurde. Da die Aufrufe `pinMode` in seinem Konstruktor, wird dies auch einen Deadlock verursachen. Dies ist ungewöhnlich, dass Problem, aber aus bestimmten Bibliotheken mit Objekten auftreten (z. B. die Arduino `LiquidCrystal` Bibliothek).

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

Die Lösung ist unten. Wir haben das Objekt in einen Objektzeiger geändert und die Initialisierung des Objekts, das verschoben `setup()`.

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a>Mithilfe von `Serial.print()` und `Serial.println()`

Verwenden Sie viele Arduino Skizzen `Serial` Daten mit der seriellen Konsole drucken (wenn geöffnet) oder auf die serielle Zeilen (USB oder tx/Rx) zu schreiben. In früheren Versionen des SDK Lightning Hardware `Serial` Support nicht enthalten war, dazu, dass wir bereitgestellt ein `Log()` Funktion, die an den Debugger druckt Ausgabefenster in Visual Studio. `Serial.print*()` oder `Serial.write()` hatten, entfernt werden soll.

Dabei ist jedoch _Lightning SDK 1.1.0_, haben wir hinzugefügt `Hardware Serial` Unterstützung und die beiden `Serial.print*()` oder `Serial.write()` Funktionen werden vollständig unterstützt. Wenn Sie eine Skizze für die einem arduino-Board kopieren, müssen Sie also nicht diese serielle Verweise in der Windows-IoT-Version der Skizze ersetzen.

Darüber hinaus haben wir die Funktionalität des erweiterten `Serial.print()` und `Serial.println()`, zum Debuggerfenster ausgegeben, wenn ein Debugger, zusätzlich zum Schreiben in die seriellen Anschlüsse des Hardware angefügt ist-.
Die Debugausgabe Drucken wird ausgeführt als der Standard seit lesen, dass die Ausgabe ist, welche die meisten Benutzer sollten beim Festlegen ihrer Skizzen. Diese Funktionalität kann jedoch auch deaktiviert werden. z. B. zur Verbesserung der Leistung einfach aufrufen `Serial.enablePrintDebugOutput(false);` Sie ihn in Ihre Sketch deaktivieren. Um es erneut zu aktivieren, rufen Sie `Serial.enablePrintDebugOutput(true);`. Das Schreiben in die Hardware serielle Pins wird durch diese Aufrufe nicht beeinflusst.

Beachten Sie, dass Sie nicht benötigen, können Sie die serielle Pins wie z. B. eine FTDI, Ausgabe gesendet, um das Debuggerfenster zu alle Peripheriegeräte zuordnen. Allerdings müssen Sie sicherstellen, dass der Debuggerfenster geöffnet ist, während die Anwendung im Debugmodus befindet.

![Ausgabe des Debuggers](../media/ArduinoWiringPortingGuide/debugger_output.png)

Die Projektvorlagen auf aktualisiert wurden die [Windows IoT Core-Projektvorlagen-Erweiterungsseite](https://go.microsoft.com/fwlink/?linkid=847472) zum ermöglichen der Verwendung von Hardware `Serial` standardmäßig. Aber wenn Ihre Anwendung verknüpfen Arduino bereits mit einer älteren Version von Project-Vorlage erstellt wurde, Sie müssen (1) auf das neueste Lightning-SDK, aktualisieren Sie das Projekt 1.1.0 oder höher, und (2) fügen Sie die erforderliche Hardware seriellen Gerät Möglichkeit, Ihre AppxManifest verwenden, können `Serial`.

### <a name="hardware-serial-device-capability-requirements"></a>Hardwareanforderungen für seriellen Gerät-Funktion

Serielle Hardware-Funktionalität in Windows 10 IoT Core erfordert Gerät Deklarationen der Funktionen, die das AppX-Manifest hinzugefügt.

Suchen Sie die Datei `Package.appxmanifest` in Ihrem Projekt, indem Sie Sie im Projektmappen-Explorer den Dateinamen eingeben. Klicken Sie dann, klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie "Öffnen mit...". Wählen Sie "XML (Text)-Editor" aus, und klicken Sie auf "OK".

![Aktualisieren die Datei "Package.appxmanifest"](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

Fügen Sie in die Appx-manifest-Datei-Editor, der `serialcommunication` DeviceCapability zu Ihrem Projekt wie in den folgenden XML-Codeausschnitt:

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>Aktualisieren Sie das Projekt auf das neueste Lightning-SDK

Abhängig von die Projekten Arduino Verknüpfen der [Lightning-SDK-Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) die erforderliche verknüpfen Arduino-Funktionen und Deklarationen als auch mit dem Treiber Lightning-Schnittstelle implementieren. Das neueste Lightning-SDK enthält die neuesten Verbesserungen und Fehlerbehebungen. Um auf das neueste Lightning-SDK zu aktualisieren, gehen Sie folgendermaßen vor:

- Klicken Sie im Projektmappen-Explorer klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf "Nuget-Pakete verwalten"
- In den NuGet Package Manager, wechseln Sie zur Registerkarte "Installiert". Sie sollte das Microsoft.IoT.Lightning-Paket installiert angezeigt.
- Verfügbare Versionen werden in der Combobox 'Version' aufgelistet.
- Wählen Sie die neueste Version aus, und klicken Sie auf 'Aktualisieren', um das Paket zu aktualisieren.
- Upgrade auf einer Vorabversion, beachten Sie unbedingt auch Kontrollkästchen "Vorabversion einbeziehen" aktivieren.

![NuGet-Paket-manager](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
