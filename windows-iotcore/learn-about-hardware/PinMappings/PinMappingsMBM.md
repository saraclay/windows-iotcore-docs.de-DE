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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="e95e9-104">MinnowBoard maximale Pin-Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="e95e9-104">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="e95e9-105">Um diese Zuordnung Pin auf neuere Versionen von der Minnowboard vergleichen zu können, finden Sie Dokumentation [hier](https://minnowboard.org/minnowboard-turbot/documentation).</span><span class="sxs-lookup"><span data-stu-id="e95e9-105">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="e95e9-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="e95e9-106">Overview</span></span>

![MinnowBoard Max Pin Header](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="e95e9-108">Hardwareschnittstellen für das MinnowBoard Max werden durch den 26-poligen Header verfügbar gemacht **JP1** auf dem Board.</span><span class="sxs-lookup"><span data-stu-id="e95e9-108">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="e95e9-109">Funktionalität umfasst:</span><span class="sxs-lookup"><span data-stu-id="e95e9-109">Functionality includes:</span></span>

* <span data-ttu-id="e95e9-110">**10 X** -GPIO-Pins</span><span class="sxs-lookup"><span data-stu-id="e95e9-110">**10x** - GPIO pins</span></span>
* <span data-ttu-id="e95e9-111">**2 X** -serielle UARTs</span><span class="sxs-lookup"><span data-stu-id="e95e9-111">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="e95e9-112">**1 X** -SPI-Bus</span><span class="sxs-lookup"><span data-stu-id="e95e9-112">**1x** - SPI bus</span></span>
* <span data-ttu-id="e95e9-113">**1 X** -I2C-Bus</span><span class="sxs-lookup"><span data-stu-id="e95e9-113">**1x** - I2C bus</span></span>
* <span data-ttu-id="e95e9-114">**1 X** -5V-Power-Pin</span><span class="sxs-lookup"><span data-stu-id="e95e9-114">**1x** - 5V power pin</span></span>
* <span data-ttu-id="e95e9-115">**1 X** – 3.3V Pin des Power</span><span class="sxs-lookup"><span data-stu-id="e95e9-115">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="e95e9-116">**2 X** -erden Pins</span><span class="sxs-lookup"><span data-stu-id="e95e9-116">**2x** - Ground pins</span></span>

<span data-ttu-id="e95e9-117">Die MinnowBoard Max verwendet 3,3 v Logik Ebenen auf alle e/a-Pins.</span><span class="sxs-lookup"><span data-stu-id="e95e9-117">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="e95e9-118">Darüber hinaus werden alle von gepuffert [TXS0104E](http://www.ti.com/product/txs0104e) Ebene Umschalter, mit Ausnahme von Strom- und gemahlen Pins.</span><span class="sxs-lookup"><span data-stu-id="e95e9-118">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="e95e9-119">Diese Ebene Umschalter angezeigt werden, als open-Sammlung von Ausgaben mit einer **10K&#x2126; magnetisierungsresistent Pull-Up, und die Pull-Up ist vorhanden, unabhängig davon, ob die e/a zu Eingabe- oder Ausgabeparameter festgelegt ist.**</span><span class="sxs-lookup"><span data-stu-id="e95e9-119">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="e95e9-120">Die Open-Collector-Art bedeutet, dass die Ebene Umschalter ist, dass die Pins "0"stark, aber nur schwach 1 "Ausgabe" ausgeben können.</span><span class="sxs-lookup"><span data-stu-id="e95e9-120">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="e95e9-121">Dies ist wichtig zu bedenken, beim Anfügen von Geräten der aktuellen von der Pins (z. B. eine LED) gezeichnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e95e9-121">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="e95e9-122">Finden Sie unter den [Hauptverkaufsargument Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) für die richtige Methode, die eine LED MinnowBoard maximale Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="e95e9-122">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="e95e9-123">GPIO-Pins</span><span class="sxs-lookup"><span data-stu-id="e95e9-123">GPIO Pins</span></span>

<span data-ttu-id="e95e9-124">Die folgenden GPIO-Pins, die über APIs zugänglich sind:</span><span class="sxs-lookup"><span data-stu-id="e95e9-124">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="e95e9-125">GPIO#</span><span class="sxs-lookup"><span data-stu-id="e95e9-125">GPIO#</span></span> | <span data-ttu-id="e95e9-126">Header-Pin</span><span class="sxs-lookup"><span data-stu-id="e95e9-126">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="e95e9-127">0</span><span class="sxs-lookup"><span data-stu-id="e95e9-127">0</span></span>     | <span data-ttu-id="e95e9-128">21</span><span class="sxs-lookup"><span data-stu-id="e95e9-128">21</span></span>                 |
> | <span data-ttu-id="e95e9-129">1</span><span class="sxs-lookup"><span data-stu-id="e95e9-129">1</span></span>     | <span data-ttu-id="e95e9-130">23</span><span class="sxs-lookup"><span data-stu-id="e95e9-130">23</span></span>                 |
> | <span data-ttu-id="e95e9-131">2</span><span class="sxs-lookup"><span data-stu-id="e95e9-131">2</span></span>     | <span data-ttu-id="e95e9-132">25</span><span class="sxs-lookup"><span data-stu-id="e95e9-132">25</span></span>                 |
> | <span data-ttu-id="e95e9-133">3</span><span class="sxs-lookup"><span data-stu-id="e95e9-133">3</span></span>     | <span data-ttu-id="e95e9-134">14</span><span class="sxs-lookup"><span data-stu-id="e95e9-134">14</span></span>                 |
> | <span data-ttu-id="e95e9-135">4</span><span class="sxs-lookup"><span data-stu-id="e95e9-135">4</span></span>     | <span data-ttu-id="e95e9-136">16</span><span class="sxs-lookup"><span data-stu-id="e95e9-136">16</span></span>                 |
> | <span data-ttu-id="e95e9-137">5</span><span class="sxs-lookup"><span data-stu-id="e95e9-137">5</span></span>     | <span data-ttu-id="e95e9-138">18</span><span class="sxs-lookup"><span data-stu-id="e95e9-138">18</span></span>                 |
> | <span data-ttu-id="e95e9-139">6</span><span class="sxs-lookup"><span data-stu-id="e95e9-139">6</span></span>     | <span data-ttu-id="e95e9-140">20</span><span class="sxs-lookup"><span data-stu-id="e95e9-140">20</span></span>                 |
> | <span data-ttu-id="e95e9-141">7</span><span class="sxs-lookup"><span data-stu-id="e95e9-141">7</span></span>     | <span data-ttu-id="e95e9-142">22</span><span class="sxs-lookup"><span data-stu-id="e95e9-142">22</span></span>                 |
> | <span data-ttu-id="e95e9-143">8</span><span class="sxs-lookup"><span data-stu-id="e95e9-143">8</span></span>     | <span data-ttu-id="e95e9-144">24</span><span class="sxs-lookup"><span data-stu-id="e95e9-144">24</span></span>                 |
> | <span data-ttu-id="e95e9-145">9</span><span class="sxs-lookup"><span data-stu-id="e95e9-145">9</span></span>     | <span data-ttu-id="e95e9-146">26</span><span class="sxs-lookup"><span data-stu-id="e95e9-146">26</span></span>                 |

<span data-ttu-id="e95e9-147">**Hinweis**: **GPIO 4** und **GPIO 5** werden das MinnowBoard Max als Bootstrapkonfiguration Pins für das BIOS verwendet.</span><span class="sxs-lookup"><span data-stu-id="e95e9-147">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="e95e9-148">Stellen Sie sicher, dass es sich bei angeschlossene Geräte nicht diese GPIO niedrige während des Starts, gesteuert, wie dies die MBM am Starten hindern könnte.</span><span class="sxs-lookup"><span data-stu-id="e95e9-148">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="e95e9-149">Nachdem die MBM direkt hinter das BIOS gestartet wurde, kann diese GPIO normalerweise verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e95e9-149">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="e95e9-150">GPIO-Beispiel</span><span class="sxs-lookup"><span data-stu-id="e95e9-150">GPIO Sample</span></span>

<span data-ttu-id="e95e9-151">Als Beispiel den folgenden code wird **GPIO 5** als Ausgabe und schreibt eine digitale "**1**' Out bei der Pin:</span><span class="sxs-lookup"><span data-stu-id="e95e9-151">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="e95e9-152">Serielle UART</span><span class="sxs-lookup"><span data-stu-id="e95e9-152">Serial UART</span></span>

<span data-ttu-id="e95e9-153">Es stehen zwei serielle UARTS MBM: **UART1** und **UART2**</span><span class="sxs-lookup"><span data-stu-id="e95e9-153">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="e95e9-154">**UART1** hat den Standard **UART1 TX** und **UART1 RX** Zeilen zusammen mit Flow steuern Signale **UART1 CTS** und **UART1 RTS**.</span><span class="sxs-lookup"><span data-stu-id="e95e9-154">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="e95e9-155">Pin 6  - **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="e95e9-155">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="e95e9-156">Anheften von 8 – **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="e95e9-156">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="e95e9-157">Heften Sie 10 – **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="e95e9-157">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="e95e9-158">Anheften von 12: **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="e95e9-158">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="e95e9-159">UART1 funktioniert nicht im Build 10240.</span><span class="sxs-lookup"><span data-stu-id="e95e9-159">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="e95e9-160">Verwenden Sie UART2 oder einen USB-Seriell-Konverter.</span><span class="sxs-lookup"><span data-stu-id="e95e9-160">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="e95e9-161">**UART2** enthält nur die **UART2 TX** und **UART2 RX** Zeilen.</span><span class="sxs-lookup"><span data-stu-id="e95e9-161">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="e95e9-162">Pin 17  - **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="e95e9-162">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="e95e9-163">Anheften von 19 – **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="e95e9-163">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="e95e9-164">UART2 unterstützt keine flusssteuerung, damit eine Ausnahme ausgelöst wird, den Zugriff auf die folgenden Eigenschaften der SerialDevice führen kann:</span><span class="sxs-lookup"><span data-stu-id="e95e9-164">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="e95e9-165">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="e95e9-165">BreakSignalState</span></span>
 * <span data-ttu-id="e95e9-166">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="e95e9-166">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="e95e9-167">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="e95e9-167">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="e95e9-168">Handshake - nur SerialHandshake.None wird unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e95e9-168">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="e95e9-169">Im Beispiel unten initialisiert **UART2** und führt einen Schreibvorgang, gefolgt von einem Lesevorgang:</span><span class="sxs-lookup"><span data-stu-id="e95e9-169">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="e95e9-170">Beachten Sie, dass Sie die folgende Funktion zum Hinzufügen, müssen die **"Package.appxmanifest"** Datei in Ihre UWP-Projekt, um serielle UART Code auszuführen:</span><span class="sxs-lookup"><span data-stu-id="e95e9-170">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="e95e9-171">Visual Studio 2017 weist ein bekanntes Problem im Manifest-Designer (visuellen Editor für die Appxmanifest-Dateien), die die Funktion Serialcommunication betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="e95e9-171">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="e95e9-172">Wenn es sich bei Ihrem Appxmanifest Serialcommunication Funktion hinzugefügt wird, wird durch das Ändern Ihrer Appxmanifest mit dem Designer Ihrem Appxmanifest beschädigt (untergeordneten XML-Gerät verloren).</span><span class="sxs-lookup"><span data-stu-id="e95e9-172">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="e95e9-173">Sie können dieses Problem umgehen von Hand bearbeitet die appxmanifest-Datei mit der rechten Maustaste in Ihrem Appxmanifest, und wählen im Kontextmenü auf Code anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e95e9-173">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="e95e9-174">I2C Bus</span><span class="sxs-lookup"><span data-stu-id="e95e9-174">I2C Bus</span></span>

<span data-ttu-id="e95e9-175">Sehen wir uns die I2C-Bus verfügbare auf diesem Gerät an.</span><span class="sxs-lookup"><span data-stu-id="e95e9-175">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="e95e9-176">Übersicht über die I2C</span><span class="sxs-lookup"><span data-stu-id="e95e9-176">I2C Overview</span></span>

<span data-ttu-id="e95e9-177">Es ist ein I2C-Controller **I2C5** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL**.</span><span class="sxs-lookup"><span data-stu-id="e95e9-177">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="e95e9-178">10K&#x2126; interne Pull-Up-Widerstände sind bereits in diesen Zeilen vorhanden.</span><span class="sxs-lookup"><span data-stu-id="e95e9-178">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="e95e9-179">15: anheften **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="e95e9-179">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="e95e9-180">13: anheften **I2C5 SCL-Bewertung**</span><span class="sxs-lookup"><span data-stu-id="e95e9-180">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="e95e9-181">I2C-Beispiel</span><span class="sxs-lookup"><span data-stu-id="e95e9-181">I2C Sample</span></span>

<span data-ttu-id="e95e9-182">Im Beispiel unten initialisiert **I2C5** und schreibt Daten in eine I2C-Gerät mit der Adresse **0 x 40**:</span><span class="sxs-lookup"><span data-stu-id="e95e9-182">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="e95e9-183">I2C-Probleme</span><span class="sxs-lookup"><span data-stu-id="e95e9-183">I2C Issues</span></span>

<span data-ttu-id="e95e9-184">Das MinnowBoard Max hat es sich um ein bekanntes Problem mit dem I2C-Bus wodurch Kommunikationsprobleme mit bestimmten I2C-Geräten.</span><span class="sxs-lookup"><span data-stu-id="e95e9-184">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="e95e9-185">Ein I2C-Gerät, in der Regel wird die Adresse während einer Anforderung Bus bestätigt.</span><span class="sxs-lookup"><span data-stu-id="e95e9-185">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="e95e9-186">Jedoch unter bestimmten Bedingungen dieser Bestätigung ein Fehler auftritt, durch die Servicelevel Umschalter auf der MBM weitergegeben werden, und daher die CPU davon aus, das Gerät hat nicht geantwortet und bricht die Bus-Transaktion ab.</span><span class="sxs-lookup"><span data-stu-id="e95e9-186">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="e95e9-187">Das Problem scheint in Bezug auf die [TXS0104E](http://www.ti.com/product/txs0104e) Ebene Umschalter auf der e/a-Pins, die vorzeitig aufgrund von Spannungsspitzen in der Zeile auslösen können.</span><span class="sxs-lookup"><span data-stu-id="e95e9-187">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="e95e9-188">Die aktuelle problemumgehung ist zum Einfügen von einer 100-Ohm-Widerstand in Reihe mit der I2C SCK-Zeile, die Ihnen hilft, Spitzen zu unterdrücken.</span><span class="sxs-lookup"><span data-stu-id="e95e9-188">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="e95e9-189">Nicht alle Geräte betroffen sind, damit diese problemumgehung nur ist erforderlich, wenn Sie eine Antwort der Bus erhält Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="e95e9-189">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="e95e9-190">Ein Gerät, das bekannt ist, müssen diese problemumgehung ist das HTU21D.</span><span class="sxs-lookup"><span data-stu-id="e95e9-190">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="e95e9-191">SPI-Bus</span><span class="sxs-lookup"><span data-stu-id="e95e9-191">SPI Bus</span></span>

<span data-ttu-id="e95e9-192">Sehen wir uns den SPI-Bus verfügbare auf diesem Gerät an.</span><span class="sxs-lookup"><span data-stu-id="e95e9-192">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="e95e9-193">Übersicht über die SPI</span><span class="sxs-lookup"><span data-stu-id="e95e9-193">SPI Overview</span></span>

<span data-ttu-id="e95e9-194">Es ist ein SPI-Controller **SPI0** MBM verfügbar:</span><span class="sxs-lookup"><span data-stu-id="e95e9-194">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="e95e9-195">Anheften von 9 – **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="e95e9-195">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="e95e9-196">Anheften von 7 – **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="e95e9-196">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="e95e9-197">Anheften von 11 – **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="e95e9-197">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="e95e9-198">Heften Sie 5 – **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="e95e9-198">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="e95e9-199">SPI-Beispiel</span><span class="sxs-lookup"><span data-stu-id="e95e9-199">SPI Sample</span></span>

<span data-ttu-id="e95e9-200">Schreiben Sie ein Beispiel zum Ausführen einer SPI auf Bus **SPI0** ist unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="e95e9-200">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

