---
title: Dragonboard Stiftzuordnungen
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über die Funktionalität des Pin-Zuordnungen, für die Dragonboard.
keywords: Windows Iot, Dragonboard, stiftzuordnungen, GPIO
ms.openlocfilehash: f6df962c6d05aa912013f8f0819c0789bfc393ce
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513926"
---
# <a name="dragonboard-pin-mappings"></a>Dragonboard Stiftzuordnungen

![Dragonboard Pin-Header](../../media/PinMappingsDB/DB_Pinout.png)

Hardwareschnittstellen für die Dragonboard werden über die 40-Pin-Header auf dem Board verfügbar gemacht. Funktionalität umfasst:

* **11 X** -GPIO-Pins
* **2 X** -serielle UARTs
* **1 X** -SPI-Bus
* **2 X** -I2C-Bus
* **1 X** -5V-Power-Pin
* **1 X** –® 1,8 v Power-Pin
* **4 X** -erden Pins

Beachten Sie, dass die Dragonboard® 1,8 v Logik Ebenen auf alle e/a-Pins. 

## <a name="gpio-pins"></a>GPIO-Pins

Wir sehen uns die GPIO-LED auf diesem Gerät zur Verfügung.

### <a name="gpio-pin-table"></a>GPIO-Pin-Tabelle

Die folgenden GPIO-Pins, die über APIs zugänglich sind:

> | GPIO# | Header-Pin         |
> |-------|--------------------|
> | 36    | 23                 |
> | 12    | 24                 |
> | 13    | 25                 |
> | 69    | 26                 |
> | 115   | 27                 |
> | 24    | 29                 |
> | 25    | 30                 |
> | 35    | 31                 |
> | 34    | 32                 |
> | 28    | 33                 |
> | 33    | 34                 |
> | 21    | Benutzer-LED 1         | 
> | 120   | Benutzer-LED 2         |         


Als Beispiel den folgenden code wird **GPIO 35** als Ausgabe und schreibt eine digitale "**1**" Out bei der Pin:
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(35);       /* Open GPIO 35                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

### <a name="gpio-issues"></a>GPIO-Probleme

* Ausgabe funktioniert nicht auf GPIO 24. Eingabe funktioniert.
* Pins werden beim Start als InputPullDown konfiguriert, aber ändert sich in der Eingabe (unverankert) beim ersten Öffnen werden
* Pins nicht auf ihren Standardzustand zurückgesetzt, wenn geschlossen zurückgesetzt.
* Vermeidbare Interrupts können auftreten, wenn es sich bei Unterbrechungen auf mehrere Pins aktiviert sind


## <a name="serial-uart"></a>Serielle UART

Es stehen zwei serielle UARTS der Dragonboard **UART0** und **UART1**

**UART0** hat den Standard **UART0 TX** und **UART0 RX** Zeilen zusammen mit Flow steuern Signale **UART0 CTS** und **UART0 RTS**.

* Pin 5  - **UART0 TX**
* Anheften von 7 – **UART0 RX**
* Anheften von 3 – **UART0 CTS**
* Anheften von 9 – **UART0 RTS**


**UART1** enthält nur die **UART1 TX** und **UART1 RX** Zeilen.

* Pin 11  - **UART1 TX**
* Pin 13  - **UART1 RX**

Im Beispiel unten initialisiert **UART1** und führt einen Schreibvorgang, gefolgt von einem Lesevorgang:

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART1");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;
    SerialPort.Parity = SerialParity.None;         
    SerialPort.StopBits = SerialStopBitCount.One;
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
> [!NOTE]
> Visual Studio 2017 weist ein bekanntes Problem im Manifest-Designer (visuellen Editor für die Appxmanifest-Dateien), die die Funktion Serialcommunication betroffen sind.  Wenn es sich bei Ihrem Appxmanifest Serialcommunication Funktion hinzugefügt wird, wird durch das Ändern Ihrer Appxmanifest mit dem Designer Ihrem Appxmanifest beschädigt (untergeordneten XML-Gerät verloren).  Sie können dieses Problem umgehen von Hand bearbeitet die appxmanifest-Datei mit der rechten Maustaste in Ihrem Appxmanifest, und wählen im Kontextmenü auf Code anzeigen.

Sie müssen die folgende Funktion zum Hinzufügen der **"Package.appxmanifest"** Datei in Ihre UWP-Projekt, um serielle UART Code auszuführen:

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

Sehen wir uns die I2C-Bussen verfügbar auf diesem Gerät an.

### <a name="i2c-pins"></a>I2C-Pins

**I2C0** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL-Bewertung**

* Heften Sie 17 – **I2C0 SDA**
* 15: anheften **I2C0 SCL-Bewertung**

**I2C1** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL-Bewertung**

* Anheften von 21: **I2C1 SDA**
* Anheften von 19 – **I2C1 SCL-Bewertung**

### <a name="i2c-sample"></a>I2C-Beispiel

Im Beispiel unten initialisiert **I2C0** und schreibt Daten in eine I2C-Gerät mit der Adresse **0 x 40**:

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Get a selector string that will return our wanted I2C controller
    string aqs = I2cDevice.GetDeviceSelector("I2C0");
    
    // Find the I2C bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);

    // Create an I2cDevice with our selected bus controller and I2C settings 
    using (I2cDevice device = await I2cDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```


## <a name="spi-bus"></a>SPI-Bus

Sehen wir uns den SPI-Bus verfügbare auf diesem Gerät an.

### <a name="spi-pins"></a>SPI-Pins

Es ist ein SPI-Controller **SPI0** auf die Datenbank verfügbar

* Heften Sie 10 – **SPI0 MISO**
* Anheften von 14 – **SPI0 MOSI**
* Anheften von 8 – **SPI0 SCLK**
* Anheften von 12: **SPI0 CS0**

### <a name="spi-issues"></a>SPI-Probleme

Die Uhr SPI ist 4.8 MHz fest. Die angeforderte SPI-Uhr wird ignoriert. 


### <a name="spi-sample"></a>SPI-Beispiel

Schreiben Sie ein Beispiel zum Ausführen einer SPI auf Bus **SPI0** ist unten dargestellt:

```C3
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```
