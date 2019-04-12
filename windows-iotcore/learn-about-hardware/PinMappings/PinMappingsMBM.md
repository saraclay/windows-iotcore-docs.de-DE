---
title: Minnowboard maximale Pin-Zuordnungen
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über die Funktionalität des Pin-Zuordnungen, für den Minnowboard maximalen.
keywords: Windows Iot, Minnowboard Max, stiftzuordnungen, GPIO
ms.openlocfilehash: 884d9ee0d93167a13f39a28b28454daccb2eebad
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513385"
---
# <a name="minnowboard-max-pin-mappings"></a>MinnowBoard maximale Pin-Zuordnungen

> [!NOTE] 
> Um diese Zuordnung Pin auf neuere Versionen von der Minnowboard vergleichen zu können, finden Sie Dokumentation [hier](https://minnowboard.org/minnowboard-turbot/documentation).

## <a name="overview"></a>Übersicht

![MinnowBoard Max Pin Header](../../media/PinMappingsMBM/MBM_Pinout.png)

Hardwareschnittstellen für das MinnowBoard Max werden durch den 26-poligen Header verfügbar gemacht **JP1** auf dem Board. Funktionalität umfasst:

* **10 X** -GPIO-Pins
* **2 X** -serielle UARTs
* **1 X** -SPI-Bus
* **1 X** -I2C-Bus
* **1 X** -5V-Power-Pin
* **1 X** – 3.3V Pin des Power
* **2 X** -erden Pins

Die MinnowBoard Max verwendet 3,3 v Logik Ebenen auf alle e/a-Pins. Darüber hinaus werden alle von gepuffert [TXS0104E](http://www.ti.com/product/txs0104e) Ebene Umschalter, mit Ausnahme von Strom- und gemahlen Pins.
Diese Ebene Umschalter angezeigt werden, als open-Sammlung von Ausgaben mit einer **10K&#x2126; magnetisierungsresistent Pull-Up, und die Pull-Up ist vorhanden, unabhängig davon, ob die e/a zu Eingabe- oder Ausgabeparameter festgelegt ist.**
 
Die Open-Collector-Art bedeutet, dass die Ebene Umschalter ist, dass die Pins "0"stark, aber nur schwach 1 "Ausgabe" ausgeben können. Dies ist wichtig zu bedenken, beim Anfügen von Geräten der aktuellen von der Pins (z. B. eine LED) gezeichnet werden soll. Finden Sie unter den [Hauptverkaufsargument Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) für die richtige Methode, die eine LED MinnowBoard maximale Schnittstelle.

## <a name="gpio-pins"></a>GPIO-Pins

Die folgenden GPIO-Pins, die über APIs zugänglich sind:

> | GPIO# | Header-Pin         |
> |-------|--------------------|
> | 0     | 21                 |
> | 1     | 23                 |
> | 2     | 25                 |
> | 3     | 14                 |
> | 4     | 16                 |
> | 5     | 18                 |
> | 6     | 20                 |
> | 7     | 22                 |
> | 8     | 24                 |
> | 9     | 26                 |

**Hinweis**: **GPIO 4** und **GPIO 5** werden das MinnowBoard Max als Bootstrapkonfiguration Pins für das BIOS verwendet.
Stellen Sie sicher, dass es sich bei angeschlossene Geräte nicht diese GPIO niedrige während des Starts, gesteuert, wie dies die MBM am Starten hindern könnte.
Nachdem die MBM direkt hinter das BIOS gestartet wurde, kann diese GPIO normalerweise verwendet werden.
     
## <a name="gpio-sample"></a>GPIO-Beispiel

Als Beispiel den folgenden code wird **GPIO 5** als Ausgabe und schreibt eine digitale "**1**' Out bei der Pin:
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(5);        /* Open GPIO 5                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

## <a name="serial-uart"></a>Serielle UART

Es stehen zwei serielle UARTS MBM: **UART1** und **UART2**

**UART1** hat den Standard **UART1 TX** und **UART1 RX** Zeilen zusammen mit Flow steuern Signale **UART1 CTS** und **UART1 RTS**.

* Pin 6  - **UART1 TX**
* Anheften von 8 – **UART1 RX**
* Heften Sie 10 – **UART1 CTS**
* Anheften von 12: **UART1 RTS**

UART1 funktioniert nicht im Build 10240. Verwenden Sie UART2 oder einen USB-Seriell-Konverter.

**UART2** enthält nur die **UART2 TX** und **UART2 RX** Zeilen.

* Pin 17  - **UART2 TX**
* Anheften von 19 – **UART2 RX**

UART2 unterstützt keine flusssteuerung, damit eine Ausnahme ausgelöst wird, den Zugriff auf die folgenden Eigenschaften der SerialDevice führen kann:

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * Handshake - nur SerialHandshake.None wird unterstützt.

Im Beispiel unten initialisiert **UART2** und führt einen Schreibvorgang, gefolgt von einem Lesevorgang:

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART2");                   /* Find the selector string for the serial device   */
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

Beachten Sie, dass Sie die folgende Funktion zum Hinzufügen, müssen die **"Package.appxmanifest"** Datei in Ihre UWP-Projekt, um serielle UART Code auszuführen:

Visual Studio 2017 weist ein bekanntes Problem im Manifest-Designer (visuellen Editor für die Appxmanifest-Dateien), die die Funktion Serialcommunication betroffen sind.  Wenn es sich bei Ihrem Appxmanifest Serialcommunication Funktion hinzugefügt wird, wird durch das Ändern Ihrer Appxmanifest mit dem Designer Ihrem Appxmanifest beschädigt (untergeordneten XML-Gerät verloren).  Sie können dieses Problem umgehen von Hand bearbeitet die appxmanifest-Datei mit der rechten Maustaste in Ihrem Appxmanifest, und wählen im Kontextmenü auf Code anzeigen.

```
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

Es ist ein I2C-Controller **I2C5** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL**. 10K&#x2126; interne Pull-Up-Widerstände sind bereits in diesen Zeilen vorhanden.

* 15: anheften **I2C5 SDA**
* 13: anheften **I2C5 SCL-Bewertung**

### <a name="i2c-sample"></a>I2C-Beispiel

Im Beispiel unten initialisiert **I2C5** und schreibt Daten in eine I2C-Gerät mit der Adresse **0 x 40**:

```C#
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

### <a name="i2c-issues"></a>I2C-Probleme

Das MinnowBoard Max hat es sich um ein bekanntes Problem mit dem I2C-Bus wodurch Kommunikationsprobleme mit bestimmten I2C-Geräten. Ein I2C-Gerät, in der Regel wird die Adresse während einer Anforderung Bus bestätigt.
Jedoch unter bestimmten Bedingungen dieser Bestätigung ein Fehler auftritt, durch die Servicelevel Umschalter auf der MBM weitergegeben werden, und daher die CPU davon aus, das Gerät hat nicht geantwortet und bricht die Bus-Transaktion ab.
Das Problem scheint in Bezug auf die [TXS0104E](http://www.ti.com/product/txs0104e) Ebene Umschalter auf der e/a-Pins, die vorzeitig aufgrund von Spannungsspitzen in der Zeile auslösen können.
Die aktuelle problemumgehung ist zum Einfügen von einer 100-Ohm-Widerstand in Reihe mit der I2C SCK-Zeile, die Ihnen hilft, Spitzen zu unterdrücken. Nicht alle Geräte betroffen sind, damit diese problemumgehung nur ist erforderlich, wenn Sie eine Antwort der Bus erhält Probleme auftreten. Ein Gerät, das bekannt ist, müssen diese problemumgehung ist das HTU21D.

## <a name="spi-bus"></a>SPI-Bus

Sehen wir uns den SPI-Bus verfügbare auf diesem Gerät an.

### <a name="spi-overview"></a>Übersicht über die SPI

Es ist ein SPI-Controller **SPI0** MBM verfügbar:

* Anheften von 9 – **SPI0 MOSI**
* Anheften von 7 – **SPI0 MISO**
* Anheften von 11 – **SPI0 SCLK**
* Heften Sie 5 – **SPI0 CS0**


### <a name="spi-sample"></a>SPI-Beispiel

Schreiben Sie ein Beispiel zum Ausführen einer SPI auf Bus **SPI0** ist unten dargestellt:

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz
    settings.ClockFrequency = 10000000;

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

