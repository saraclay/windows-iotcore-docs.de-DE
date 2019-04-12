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
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="7859a-104">Dragonboard Stiftzuordnungen</span><span class="sxs-lookup"><span data-stu-id="7859a-104">Dragonboard Pin Mappings</span></span>

![Dragonboard Pin-Header](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="7859a-106">Hardwareschnittstellen für die Dragonboard werden über die 40-Pin-Header auf dem Board verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="7859a-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="7859a-107">Funktionalität umfasst:</span><span class="sxs-lookup"><span data-stu-id="7859a-107">Functionality includes:</span></span>

* <span data-ttu-id="7859a-108">**11 X** -GPIO-Pins</span><span class="sxs-lookup"><span data-stu-id="7859a-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="7859a-109">**2 X** -serielle UARTs</span><span class="sxs-lookup"><span data-stu-id="7859a-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="7859a-110">**1 X** -SPI-Bus</span><span class="sxs-lookup"><span data-stu-id="7859a-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="7859a-111">**2 X** -I2C-Bus</span><span class="sxs-lookup"><span data-stu-id="7859a-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="7859a-112">**1 X** -5V-Power-Pin</span><span class="sxs-lookup"><span data-stu-id="7859a-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="7859a-113">**1 X** –® 1,8 v Power-Pin</span><span class="sxs-lookup"><span data-stu-id="7859a-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="7859a-114">**4 X** -erden Pins</span><span class="sxs-lookup"><span data-stu-id="7859a-114">**4x** - Ground pins</span></span>

<span data-ttu-id="7859a-115">Beachten Sie, dass die Dragonboard® 1,8 v Logik Ebenen auf alle e/a-Pins.</span><span class="sxs-lookup"><span data-stu-id="7859a-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="7859a-116">GPIO-Pins</span><span class="sxs-lookup"><span data-stu-id="7859a-116">GPIO Pins</span></span>

<span data-ttu-id="7859a-117">Wir sehen uns die GPIO-LED auf diesem Gerät zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="7859a-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="7859a-118">GPIO-Pin-Tabelle</span><span class="sxs-lookup"><span data-stu-id="7859a-118">GPIO Pin Table</span></span>

<span data-ttu-id="7859a-119">Die folgenden GPIO-Pins, die über APIs zugänglich sind:</span><span class="sxs-lookup"><span data-stu-id="7859a-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="7859a-120">GPIO#</span><span class="sxs-lookup"><span data-stu-id="7859a-120">GPIO#</span></span> | <span data-ttu-id="7859a-121">Header-Pin</span><span class="sxs-lookup"><span data-stu-id="7859a-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="7859a-122">36</span><span class="sxs-lookup"><span data-stu-id="7859a-122">36</span></span>    | <span data-ttu-id="7859a-123">23</span><span class="sxs-lookup"><span data-stu-id="7859a-123">23</span></span>                 |
> | <span data-ttu-id="7859a-124">12</span><span class="sxs-lookup"><span data-stu-id="7859a-124">12</span></span>    | <span data-ttu-id="7859a-125">24</span><span class="sxs-lookup"><span data-stu-id="7859a-125">24</span></span>                 |
> | <span data-ttu-id="7859a-126">13</span><span class="sxs-lookup"><span data-stu-id="7859a-126">13</span></span>    | <span data-ttu-id="7859a-127">25</span><span class="sxs-lookup"><span data-stu-id="7859a-127">25</span></span>                 |
> | <span data-ttu-id="7859a-128">69</span><span class="sxs-lookup"><span data-stu-id="7859a-128">69</span></span>    | <span data-ttu-id="7859a-129">26</span><span class="sxs-lookup"><span data-stu-id="7859a-129">26</span></span>                 |
> | <span data-ttu-id="7859a-130">115</span><span class="sxs-lookup"><span data-stu-id="7859a-130">115</span></span>   | <span data-ttu-id="7859a-131">27</span><span class="sxs-lookup"><span data-stu-id="7859a-131">27</span></span>                 |
> | <span data-ttu-id="7859a-132">24</span><span class="sxs-lookup"><span data-stu-id="7859a-132">24</span></span>    | <span data-ttu-id="7859a-133">29</span><span class="sxs-lookup"><span data-stu-id="7859a-133">29</span></span>                 |
> | <span data-ttu-id="7859a-134">25</span><span class="sxs-lookup"><span data-stu-id="7859a-134">25</span></span>    | <span data-ttu-id="7859a-135">30</span><span class="sxs-lookup"><span data-stu-id="7859a-135">30</span></span>                 |
> | <span data-ttu-id="7859a-136">35</span><span class="sxs-lookup"><span data-stu-id="7859a-136">35</span></span>    | <span data-ttu-id="7859a-137">31</span><span class="sxs-lookup"><span data-stu-id="7859a-137">31</span></span>                 |
> | <span data-ttu-id="7859a-138">34</span><span class="sxs-lookup"><span data-stu-id="7859a-138">34</span></span>    | <span data-ttu-id="7859a-139">32</span><span class="sxs-lookup"><span data-stu-id="7859a-139">32</span></span>                 |
> | <span data-ttu-id="7859a-140">28</span><span class="sxs-lookup"><span data-stu-id="7859a-140">28</span></span>    | <span data-ttu-id="7859a-141">33</span><span class="sxs-lookup"><span data-stu-id="7859a-141">33</span></span>                 |
> | <span data-ttu-id="7859a-142">33</span><span class="sxs-lookup"><span data-stu-id="7859a-142">33</span></span>    | <span data-ttu-id="7859a-143">34</span><span class="sxs-lookup"><span data-stu-id="7859a-143">34</span></span>                 |
> | <span data-ttu-id="7859a-144">21</span><span class="sxs-lookup"><span data-stu-id="7859a-144">21</span></span>    | <span data-ttu-id="7859a-145">Benutzer-LED 1</span><span class="sxs-lookup"><span data-stu-id="7859a-145">User LED 1</span></span>         | 
> | <span data-ttu-id="7859a-146">120</span><span class="sxs-lookup"><span data-stu-id="7859a-146">120</span></span>   | <span data-ttu-id="7859a-147">Benutzer-LED 2</span><span class="sxs-lookup"><span data-stu-id="7859a-147">User LED 2</span></span>         |         


<span data-ttu-id="7859a-148">Als Beispiel den folgenden code wird **GPIO 35** als Ausgabe und schreibt eine digitale "**1**" Out bei der Pin:</span><span class="sxs-lookup"><span data-stu-id="7859a-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="7859a-149">GPIO-Probleme</span><span class="sxs-lookup"><span data-stu-id="7859a-149">GPIO Issues</span></span>

* <span data-ttu-id="7859a-150">Ausgabe funktioniert nicht auf GPIO 24.</span><span class="sxs-lookup"><span data-stu-id="7859a-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="7859a-151">Eingabe funktioniert.</span><span class="sxs-lookup"><span data-stu-id="7859a-151">Input works fine.</span></span>
* <span data-ttu-id="7859a-152">Pins werden beim Start als InputPullDown konfiguriert, aber ändert sich in der Eingabe (unverankert) beim ersten Öffnen werden</span><span class="sxs-lookup"><span data-stu-id="7859a-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="7859a-153">Pins nicht auf ihren Standardzustand zurückgesetzt, wenn geschlossen zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="7859a-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="7859a-154">Vermeidbare Interrupts können auftreten, wenn es sich bei Unterbrechungen auf mehrere Pins aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="7859a-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="7859a-155">Serielle UART</span><span class="sxs-lookup"><span data-stu-id="7859a-155">Serial UART</span></span>

<span data-ttu-id="7859a-156">Es stehen zwei serielle UARTS der Dragonboard **UART0** und **UART1**</span><span class="sxs-lookup"><span data-stu-id="7859a-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="7859a-157">**UART0** hat den Standard **UART0 TX** und **UART0 RX** Zeilen zusammen mit Flow steuern Signale **UART0 CTS** und **UART0 RTS**.</span><span class="sxs-lookup"><span data-stu-id="7859a-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="7859a-158">Pin 5  - **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="7859a-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="7859a-159">Anheften von 7 – **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="7859a-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="7859a-160">Anheften von 3 – **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="7859a-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="7859a-161">Anheften von 9 – **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="7859a-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="7859a-162">**UART1** enthält nur die **UART1 TX** und **UART1 RX** Zeilen.</span><span class="sxs-lookup"><span data-stu-id="7859a-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="7859a-163">Pin 11  - **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="7859a-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="7859a-164">Pin 13  - **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="7859a-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="7859a-165">Im Beispiel unten initialisiert **UART1** und führt einen Schreibvorgang, gefolgt von einem Lesevorgang:</span><span class="sxs-lookup"><span data-stu-id="7859a-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="7859a-166">Visual Studio 2017 weist ein bekanntes Problem im Manifest-Designer (visuellen Editor für die Appxmanifest-Dateien), die die Funktion Serialcommunication betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="7859a-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="7859a-167">Wenn es sich bei Ihrem Appxmanifest Serialcommunication Funktion hinzugefügt wird, wird durch das Ändern Ihrer Appxmanifest mit dem Designer Ihrem Appxmanifest beschädigt (untergeordneten XML-Gerät verloren).</span><span class="sxs-lookup"><span data-stu-id="7859a-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="7859a-168">Sie können dieses Problem umgehen von Hand bearbeitet die appxmanifest-Datei mit der rechten Maustaste in Ihrem Appxmanifest, und wählen im Kontextmenü auf Code anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7859a-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="7859a-169">Sie müssen die folgende Funktion zum Hinzufügen der **"Package.appxmanifest"** Datei in Ihre UWP-Projekt, um serielle UART Code auszuführen:</span><span class="sxs-lookup"><span data-stu-id="7859a-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="7859a-170">I2C Bus</span><span class="sxs-lookup"><span data-stu-id="7859a-170">I2C Bus</span></span>

<span data-ttu-id="7859a-171">Sehen wir uns die I2C-Bussen verfügbar auf diesem Gerät an.</span><span class="sxs-lookup"><span data-stu-id="7859a-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="7859a-172">I2C-Pins</span><span class="sxs-lookup"><span data-stu-id="7859a-172">I2C Pins</span></span>

<span data-ttu-id="7859a-173">**I2C0** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL-Bewertung**</span><span class="sxs-lookup"><span data-stu-id="7859a-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="7859a-174">Heften Sie 17 – **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="7859a-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="7859a-175">15: anheften **I2C0 SCL-Bewertung**</span><span class="sxs-lookup"><span data-stu-id="7859a-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="7859a-176">**I2C1** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL-Bewertung**</span><span class="sxs-lookup"><span data-stu-id="7859a-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="7859a-177">Anheften von 21: **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="7859a-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="7859a-178">Anheften von 19 – **I2C1 SCL-Bewertung**</span><span class="sxs-lookup"><span data-stu-id="7859a-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="7859a-179">I2C-Beispiel</span><span class="sxs-lookup"><span data-stu-id="7859a-179">I2C Sample</span></span>

<span data-ttu-id="7859a-180">Im Beispiel unten initialisiert **I2C0** und schreibt Daten in eine I2C-Gerät mit der Adresse **0 x 40**:</span><span class="sxs-lookup"><span data-stu-id="7859a-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="7859a-181">SPI-Bus</span><span class="sxs-lookup"><span data-stu-id="7859a-181">SPI Bus</span></span>

<span data-ttu-id="7859a-182">Sehen wir uns den SPI-Bus verfügbare auf diesem Gerät an.</span><span class="sxs-lookup"><span data-stu-id="7859a-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="7859a-183">SPI-Pins</span><span class="sxs-lookup"><span data-stu-id="7859a-183">SPI Pins</span></span>

<span data-ttu-id="7859a-184">Es ist ein SPI-Controller **SPI0** auf die Datenbank verfügbar</span><span class="sxs-lookup"><span data-stu-id="7859a-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="7859a-185">Heften Sie 10 – **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="7859a-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="7859a-186">Anheften von 14 – **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="7859a-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="7859a-187">Anheften von 8 – **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="7859a-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="7859a-188">Anheften von 12: **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="7859a-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="7859a-189">SPI-Probleme</span><span class="sxs-lookup"><span data-stu-id="7859a-189">SPI Issues</span></span>

<span data-ttu-id="7859a-190">Die Uhr SPI ist 4.8 MHz fest.</span><span class="sxs-lookup"><span data-stu-id="7859a-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="7859a-191">Die angeforderte SPI-Uhr wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="7859a-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="7859a-192">SPI-Beispiel</span><span class="sxs-lookup"><span data-stu-id="7859a-192">SPI Sample</span></span>

<span data-ttu-id="7859a-193">Schreiben Sie ein Beispiel zum Ausführen einer SPI auf Bus **SPI0** ist unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="7859a-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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
