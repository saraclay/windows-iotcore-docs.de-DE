---
title: Raspberry Pi 2 und 3-Stiftzuordnungen
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über die Funktionalität des Pin-Zuordnungen, für die Raspberry Pi 2 und 3.
keywords: Windows Iot, Rasperry Pi 2, Raspberry Pi 3, anheften, Zuordnungen, GPIO
ms.openlocfilehash: 86e641bdcc6b4895161c6509ca7529b0dd55fad9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512874"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Raspberry Pi 2 und 3-Stiftzuordnungen

![Raspberry Pi 2 und 3-Pin-Header](../../media/PinMappingsRPI/RP2_Pinout.png)

Hardwareschnittstellen für die Raspberry Pi 2 und Raspberry Pi 3 werden durch die 40-Pin-Header verfügbar gemacht **J8** auf dem Board. Funktionalität umfasst:

* **24 X** -GPIO-Pins
* **1 X** -serielle UARTs (RPi3 enthält nur Mini UART)
* **2 X** -SPI-Bus
* **1 X** -I2C-Bus
* **2 X** -5V-Power-Pins
* **2 X** – 3,3 v power Pins
* **8 X** -erden Pins

## <a name="gpio-pins"></a>GPIO-Pins

Wir sehen uns die GPIO-LED auf diesem Gerät zur Verfügung.

### <a name="gpio-pin-overview"></a>Übersicht über die GPIO-Pin

Die folgenden GPIO-Pins, die über APIs zugänglich sind:

> | GPIO# | Einschalten von Pull | Alternative Funktionen | Header-Pin         |
> |-------|---------------|---------------------|--------------------|
> | 2     | PullUp        | I2C1 SDA            | 3                  |
> | 3     | PullUp        | I2C1 SCL            | 5                  |
> | 4     | PullUp        |                     | 7                  |
> | 5     | PullUp        |                     | 29                 |
> | 6     | PullUp        |                     | 31                 |
> | 7     | PullUp        | SPI0 CS1            | 26                 |
> | 8     | PullUp        | SPI0 CS0            | 24                 |
> | 9     | PullDown      | SPI0 MISO           | 21                 |
> | 10    | PullDown      | SPI0 MOSI           | 19                 |
> | 11    | PullDown      | SPI0 SCLK           | 23                 |
> | 12    | PullDown      |                     | 32                 |
> | 13    | PullDown      |                     | 33                 |
> | 16    | PullDown      | SPI1 CS0            | 36                 |
> | 17    | PullDown      |                     | 11                 |
> | 18    | PullDown      |                     | 12                 |
> | 19    | PullDown      | SPI1 MISO           | 35                 |
> | 20    | PullDown      | SPI1 MOSI           | 38                 |
> | 21    | PullDown      | SPI1 SCLK           | 40                 |
> | 22    | PullDown      |                     | 15                 |
> | 23    | PullDown      |                     | 16                 |
> | 24    | PullDown      |                     | 18                 |
> | 25    | PullDown      |                     | 22                 |
> | 26    | PullDown      |                     | 37                 |
> | 27    | PullDown      |                     | 13                 |
> | 35*   | PullUp        |                     | Rote Betriebsanzeige-LED      |
> | 47*   | PullUp        |                     | Grüne LED-Aktivität |

\* = NUR Raspberry Pi 2. GPIO 35 & 47 sind nicht verfügbar, auf dem Raspberry Pi 3.

### <a name="gpio-sample"></a>GPIO-Beispiel

Als Beispiel den folgenden code wird **GPIO 5** als Ausgabe und schreibt eine digitale "**1**' Out bei der Pin:

```csharp
using Windows.Devices.Gpio;

public void GPIO()
{
    // Get the default GPIO controller on the system
    GpioController gpio = GpioController.GetDefault();
    if (gpio == null)
        return; // GPIO not available on this system

    // Open GPIO 5
    using (GpioPin pin = gpio.OpenPin(5))
    {
        // Latch HIGH value first. This ensures a default value when the pin is set as output
        pin.Write(GpioPinValue.High);

        // Set the IO direction as output
        pin.SetDriveMode(GpioPinDriveMode.Output);

    } // Close pin - will revert to its power-on state
}
```

Wenn Sie eine Pin öffnen, werden im Zustand einschalten, die eine Pull-Widerstand enthalten kann. So trennen Sie die Pull-Widerstände, und erhalten eine hohe-Impedance-Eingabe, legen Sie die Laufwerkmodus auf GpioPinDriveMode.Input ein:

    pin.SetDriveMode(GpioPinDriveMode.Input);

Wenn eine Pin geschlossen wird, wird es einschalten Zustand zurückgesetzt.

### <a name="pin-muxing"></a>PIN-Muxing

Einige GPIO-Pins können mehrere Funktionen ausführen. Standardmäßig sind Pins als GPIO-Eingaben konfiguriert. Wenn Sie eine Funktion durch den Aufruf öffnen `I2cDevice.FromIdAsync()` oder `SpiDevice.FromIdAsync()` , die Pins, die von der Funktion erforderlich sind, automatisch aktiviert ("(gemischt)"), die ordnungsgemäße Funktion. Wenn das Gerät durch den Aufruf geschlossen `I2cDevice.Dispose()` oder `SpiDevice.Dispose()`, die Pins zu ihrer Standardfunktion zurückkehren. Wenn Sie versuchen, eine Pin für zwei verschiedene Funktionen auf einmal zu verwenden, wird eine Ausnahme ausgelöst werden, wenn Sie versuchen, die in Konflikt stehende Funktion geöffnet. Beispiel:

```csharp
var controller = GpioController.GetDefault();
var gpio2 = controller.OpenPin(2);      // open GPIO2, shared with I2C1 SDA

var dis = await DeviceInformation.FindAllAsync(I2cDevice.GetDeviceSelector());
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // exception thrown because GPIO2 is open

gpio2.Dispose(); // close GPIO2
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // succeeds because gpio2 is now available

var gpio2 = controller.OpenPin(2); // throws exception because GPIO2 is in use as SDA1

i2cDevice.Dispose(); // release I2C device
var gpio2 = controller.OpenPin(2); // succeeds now that GPIO2 is available
```

## <a name="serial-uart"></a>Serielle UART

Auf dem RPi2/3 ist eine serielle UART verfügbar: **UART0**

* Pin 8  - **UART0 TX**
* Pin 10  - **UART0 RX**

Im Beispiel unten initialisiert **UART0** und führt einen Schreibvorgang, gefolgt von einem Lesevorgang:


```csharp
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART0");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;                                             /* mini UART: only standard baudrates */
    SerialPort.Parity = SerialParity.None;                                  /* mini UART: no parities */  
    SerialPort.StopBits = SerialStopBitCount.One;                           /* mini UART: 1 stop bit */
    SerialPort.DataBits = 8;

    /* Write a string out over serial */
    string txBuffer = "Hello Serial";
    DataWriter dataWriter = new DataWriter();
    dataWriter.WriteString(txBuffer);
    uint bytesWritten = await SerialPort.OutputStream.WriteAsync(dataWriter.DetachBuffer());

    /* Read data in from the serial port */
    const uint maxReadLength = 1024;
    DataReader dataReader = new DataReader(SerialPort.InputStream);
    uint bytesToRead = await dataReader.LoadAsync(maxReadLength);
    string rxBuffer = dataReader.ReadString(bytesToRead);
}
```

Beachten Sie, dass Sie die folgende Funktion zum Hinzufügen, müssen die **"Package.appxmanifest"** Datei in Ihre UWP-Projekt, um serielle UART Code auszuführen:

Visual Studio 2017 weist ein bekanntes Problem im Manifest-Designer (visuellen Editor für die Appxmanifest-Dateien), die die Funktion Serialcommunication betroffen sind.  Wenn es sich bei Ihrem Appxmanifest Serialcommunication Funktion hinzugefügt wird, wird durch das Ändern Ihrer Appxmanifest mit dem Designer Ihrem Appxmanifest beschädigt (untergeordneten XML-Gerät verloren).  Sie können dieses Problem umgehen von Hand bearbeitet die appxmanifest-Datei mit der rechten Maustaste in Ihrem Appxmanifest, und wählen im Kontextmenü auf Code anzeigen.

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a>I2C Bus

Sehen wir uns die I2C-Bus verfügbare auf diesem Gerät an.

### <a name="i2c-overview"></a>Übersicht über die I2C

Es ist ein I2C-Controller **I2C1** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL**. 1.8 K&#x2126; interne Pull-Up-Widerstände bereits auf dem Board nach diesem Bus installiert sind.

> | Signalname | Header-Pin-Nummer | GPIO-Anzahl |
> |-------------|-------------------|-------------|
> | SDA         | 3                 | 2           |
> | SCL         | 5                 | 3           |

Im Beispiel unten initialisiert **I2C1** und schreibt Daten in eine I2C-Gerät mit der Adresse **0 x 40**:

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Create an I2cDevice with the specified I2C settings
    var controller = await I2cController.GetDefaultAsync();

    using (I2cDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

## <a name="spi-bus"></a>SPI-Bus

Auf dem RPi2/3 sind zwei SPI-Controller verfügbar.

### <a name="spi0"></a>SPI0

> | Signalname | Header-Pin-Nummer | GPIO-Anzahl |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | MISO        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | Signalname | Header-Pin-Nummer | GPIO-Anzahl |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | MISO        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>SPI-Beispiel

Ein Beispiel zum Durchführen einer SPI Schreiben auf Bus **SPI0** mit Chip Select, 0, wird im folgenden dargestellt:

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz 
    settings.ClockFrequency = 10000000;

    // Get a selector string that will return our wanted SPI controller
    string aqs = SpiDevice.GetDeviceSelector("SPI0");
    
    // Find the SPI bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);
    
    // Create an SpiDevice with our selected bus controller and Spi settings
    using (SpiDevice device = await SpiDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

