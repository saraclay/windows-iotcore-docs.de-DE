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
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="2b77a-104">Raspberry Pi 2 und 3-Stiftzuordnungen</span><span class="sxs-lookup"><span data-stu-id="2b77a-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Raspberry Pi 2 und 3-Pin-Header](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="2b77a-106">Hardwareschnittstellen für die Raspberry Pi 2 und Raspberry Pi 3 werden durch die 40-Pin-Header verfügbar gemacht **J8** auf dem Board.</span><span class="sxs-lookup"><span data-stu-id="2b77a-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="2b77a-107">Funktionalität umfasst:</span><span class="sxs-lookup"><span data-stu-id="2b77a-107">Functionality includes:</span></span>

* <span data-ttu-id="2b77a-108">**24 X** -GPIO-Pins</span><span class="sxs-lookup"><span data-stu-id="2b77a-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="2b77a-109">**1 X** -serielle UARTs (RPi3 enthält nur Mini UART)</span><span class="sxs-lookup"><span data-stu-id="2b77a-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="2b77a-110">**2 X** -SPI-Bus</span><span class="sxs-lookup"><span data-stu-id="2b77a-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="2b77a-111">**1 X** -I2C-Bus</span><span class="sxs-lookup"><span data-stu-id="2b77a-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="2b77a-112">**2 X** -5V-Power-Pins</span><span class="sxs-lookup"><span data-stu-id="2b77a-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="2b77a-113">**2 X** – 3,3 v power Pins</span><span class="sxs-lookup"><span data-stu-id="2b77a-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="2b77a-114">**8 X** -erden Pins</span><span class="sxs-lookup"><span data-stu-id="2b77a-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="2b77a-115">GPIO-Pins</span><span class="sxs-lookup"><span data-stu-id="2b77a-115">GPIO Pins</span></span>

<span data-ttu-id="2b77a-116">Wir sehen uns die GPIO-LED auf diesem Gerät zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="2b77a-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="2b77a-117">Übersicht über die GPIO-Pin</span><span class="sxs-lookup"><span data-stu-id="2b77a-117">GPIO Pin Overview</span></span>

<span data-ttu-id="2b77a-118">Die folgenden GPIO-Pins, die über APIs zugänglich sind:</span><span class="sxs-lookup"><span data-stu-id="2b77a-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="2b77a-119">GPIO#</span><span class="sxs-lookup"><span data-stu-id="2b77a-119">GPIO#</span></span> | <span data-ttu-id="2b77a-120">Einschalten von Pull</span><span class="sxs-lookup"><span data-stu-id="2b77a-120">Power-on Pull</span></span> | <span data-ttu-id="2b77a-121">Alternative Funktionen</span><span class="sxs-lookup"><span data-stu-id="2b77a-121">Alternate Functions</span></span> | <span data-ttu-id="2b77a-122">Header-Pin</span><span class="sxs-lookup"><span data-stu-id="2b77a-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="2b77a-123">2</span><span class="sxs-lookup"><span data-stu-id="2b77a-123">2</span></span>     | <span data-ttu-id="2b77a-124">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-124">PullUp</span></span>        | <span data-ttu-id="2b77a-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="2b77a-125">I2C1 SDA</span></span>            | <span data-ttu-id="2b77a-126">3</span><span class="sxs-lookup"><span data-stu-id="2b77a-126">3</span></span>                  |
> | <span data-ttu-id="2b77a-127">3</span><span class="sxs-lookup"><span data-stu-id="2b77a-127">3</span></span>     | <span data-ttu-id="2b77a-128">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-128">PullUp</span></span>        | <span data-ttu-id="2b77a-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="2b77a-129">I2C1 SCL</span></span>            | <span data-ttu-id="2b77a-130">5</span><span class="sxs-lookup"><span data-stu-id="2b77a-130">5</span></span>                  |
> | <span data-ttu-id="2b77a-131">4</span><span class="sxs-lookup"><span data-stu-id="2b77a-131">4</span></span>     | <span data-ttu-id="2b77a-132">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-132">PullUp</span></span>        |                     | <span data-ttu-id="2b77a-133">7</span><span class="sxs-lookup"><span data-stu-id="2b77a-133">7</span></span>                  |
> | <span data-ttu-id="2b77a-134">5</span><span class="sxs-lookup"><span data-stu-id="2b77a-134">5</span></span>     | <span data-ttu-id="2b77a-135">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-135">PullUp</span></span>        |                     | <span data-ttu-id="2b77a-136">29</span><span class="sxs-lookup"><span data-stu-id="2b77a-136">29</span></span>                 |
> | <span data-ttu-id="2b77a-137">6</span><span class="sxs-lookup"><span data-stu-id="2b77a-137">6</span></span>     | <span data-ttu-id="2b77a-138">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-138">PullUp</span></span>        |                     | <span data-ttu-id="2b77a-139">31</span><span class="sxs-lookup"><span data-stu-id="2b77a-139">31</span></span>                 |
> | <span data-ttu-id="2b77a-140">7</span><span class="sxs-lookup"><span data-stu-id="2b77a-140">7</span></span>     | <span data-ttu-id="2b77a-141">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-141">PullUp</span></span>        | <span data-ttu-id="2b77a-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="2b77a-142">SPI0 CS1</span></span>            | <span data-ttu-id="2b77a-143">26</span><span class="sxs-lookup"><span data-stu-id="2b77a-143">26</span></span>                 |
> | <span data-ttu-id="2b77a-144">8</span><span class="sxs-lookup"><span data-stu-id="2b77a-144">8</span></span>     | <span data-ttu-id="2b77a-145">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-145">PullUp</span></span>        | <span data-ttu-id="2b77a-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="2b77a-146">SPI0 CS0</span></span>            | <span data-ttu-id="2b77a-147">24</span><span class="sxs-lookup"><span data-stu-id="2b77a-147">24</span></span>                 |
> | <span data-ttu-id="2b77a-148">9</span><span class="sxs-lookup"><span data-stu-id="2b77a-148">9</span></span>     | <span data-ttu-id="2b77a-149">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-149">PullDown</span></span>      | <span data-ttu-id="2b77a-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="2b77a-150">SPI0 MISO</span></span>           | <span data-ttu-id="2b77a-151">21</span><span class="sxs-lookup"><span data-stu-id="2b77a-151">21</span></span>                 |
> | <span data-ttu-id="2b77a-152">10</span><span class="sxs-lookup"><span data-stu-id="2b77a-152">10</span></span>    | <span data-ttu-id="2b77a-153">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-153">PullDown</span></span>      | <span data-ttu-id="2b77a-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="2b77a-154">SPI0 MOSI</span></span>           | <span data-ttu-id="2b77a-155">19</span><span class="sxs-lookup"><span data-stu-id="2b77a-155">19</span></span>                 |
> | <span data-ttu-id="2b77a-156">11</span><span class="sxs-lookup"><span data-stu-id="2b77a-156">11</span></span>    | <span data-ttu-id="2b77a-157">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-157">PullDown</span></span>      | <span data-ttu-id="2b77a-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="2b77a-158">SPI0 SCLK</span></span>           | <span data-ttu-id="2b77a-159">23</span><span class="sxs-lookup"><span data-stu-id="2b77a-159">23</span></span>                 |
> | <span data-ttu-id="2b77a-160">12</span><span class="sxs-lookup"><span data-stu-id="2b77a-160">12</span></span>    | <span data-ttu-id="2b77a-161">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-161">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-162">32</span><span class="sxs-lookup"><span data-stu-id="2b77a-162">32</span></span>                 |
> | <span data-ttu-id="2b77a-163">13</span><span class="sxs-lookup"><span data-stu-id="2b77a-163">13</span></span>    | <span data-ttu-id="2b77a-164">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-164">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-165">33</span><span class="sxs-lookup"><span data-stu-id="2b77a-165">33</span></span>                 |
> | <span data-ttu-id="2b77a-166">16</span><span class="sxs-lookup"><span data-stu-id="2b77a-166">16</span></span>    | <span data-ttu-id="2b77a-167">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-167">PullDown</span></span>      | <span data-ttu-id="2b77a-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="2b77a-168">SPI1 CS0</span></span>            | <span data-ttu-id="2b77a-169">36</span><span class="sxs-lookup"><span data-stu-id="2b77a-169">36</span></span>                 |
> | <span data-ttu-id="2b77a-170">17</span><span class="sxs-lookup"><span data-stu-id="2b77a-170">17</span></span>    | <span data-ttu-id="2b77a-171">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-171">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-172">11</span><span class="sxs-lookup"><span data-stu-id="2b77a-172">11</span></span>                 |
> | <span data-ttu-id="2b77a-173">18</span><span class="sxs-lookup"><span data-stu-id="2b77a-173">18</span></span>    | <span data-ttu-id="2b77a-174">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-174">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-175">12</span><span class="sxs-lookup"><span data-stu-id="2b77a-175">12</span></span>                 |
> | <span data-ttu-id="2b77a-176">19</span><span class="sxs-lookup"><span data-stu-id="2b77a-176">19</span></span>    | <span data-ttu-id="2b77a-177">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-177">PullDown</span></span>      | <span data-ttu-id="2b77a-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="2b77a-178">SPI1 MISO</span></span>           | <span data-ttu-id="2b77a-179">35</span><span class="sxs-lookup"><span data-stu-id="2b77a-179">35</span></span>                 |
> | <span data-ttu-id="2b77a-180">20</span><span class="sxs-lookup"><span data-stu-id="2b77a-180">20</span></span>    | <span data-ttu-id="2b77a-181">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-181">PullDown</span></span>      | <span data-ttu-id="2b77a-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="2b77a-182">SPI1 MOSI</span></span>           | <span data-ttu-id="2b77a-183">38</span><span class="sxs-lookup"><span data-stu-id="2b77a-183">38</span></span>                 |
> | <span data-ttu-id="2b77a-184">21</span><span class="sxs-lookup"><span data-stu-id="2b77a-184">21</span></span>    | <span data-ttu-id="2b77a-185">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-185">PullDown</span></span>      | <span data-ttu-id="2b77a-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="2b77a-186">SPI1 SCLK</span></span>           | <span data-ttu-id="2b77a-187">40</span><span class="sxs-lookup"><span data-stu-id="2b77a-187">40</span></span>                 |
> | <span data-ttu-id="2b77a-188">22</span><span class="sxs-lookup"><span data-stu-id="2b77a-188">22</span></span>    | <span data-ttu-id="2b77a-189">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-189">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-190">15</span><span class="sxs-lookup"><span data-stu-id="2b77a-190">15</span></span>                 |
> | <span data-ttu-id="2b77a-191">23</span><span class="sxs-lookup"><span data-stu-id="2b77a-191">23</span></span>    | <span data-ttu-id="2b77a-192">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-192">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-193">16</span><span class="sxs-lookup"><span data-stu-id="2b77a-193">16</span></span>                 |
> | <span data-ttu-id="2b77a-194">24</span><span class="sxs-lookup"><span data-stu-id="2b77a-194">24</span></span>    | <span data-ttu-id="2b77a-195">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-195">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-196">18</span><span class="sxs-lookup"><span data-stu-id="2b77a-196">18</span></span>                 |
> | <span data-ttu-id="2b77a-197">25</span><span class="sxs-lookup"><span data-stu-id="2b77a-197">25</span></span>    | <span data-ttu-id="2b77a-198">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-198">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-199">22</span><span class="sxs-lookup"><span data-stu-id="2b77a-199">22</span></span>                 |
> | <span data-ttu-id="2b77a-200">26</span><span class="sxs-lookup"><span data-stu-id="2b77a-200">26</span></span>    | <span data-ttu-id="2b77a-201">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-201">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-202">37</span><span class="sxs-lookup"><span data-stu-id="2b77a-202">37</span></span>                 |
> | <span data-ttu-id="2b77a-203">27</span><span class="sxs-lookup"><span data-stu-id="2b77a-203">27</span></span>    | <span data-ttu-id="2b77a-204">PullDown</span><span class="sxs-lookup"><span data-stu-id="2b77a-204">PullDown</span></span>      |                     | <span data-ttu-id="2b77a-205">13</span><span class="sxs-lookup"><span data-stu-id="2b77a-205">13</span></span>                 |
> | <span data-ttu-id="2b77a-206">35\*</span><span class="sxs-lookup"><span data-stu-id="2b77a-206">35\*</span></span>   | <span data-ttu-id="2b77a-207">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-207">PullUp</span></span>        |                     | <span data-ttu-id="2b77a-208">Rote Betriebsanzeige-LED</span><span class="sxs-lookup"><span data-stu-id="2b77a-208">Red Power LED</span></span>      |
> | <span data-ttu-id="2b77a-209">47\*</span><span class="sxs-lookup"><span data-stu-id="2b77a-209">47\*</span></span>   | <span data-ttu-id="2b77a-210">PullUp</span><span class="sxs-lookup"><span data-stu-id="2b77a-210">PullUp</span></span>        |                     | <span data-ttu-id="2b77a-211">Grüne LED-Aktivität</span><span class="sxs-lookup"><span data-stu-id="2b77a-211">Green Activity LED</span></span> |

<span data-ttu-id="2b77a-212">\* = NUR Raspberry Pi 2.</span><span class="sxs-lookup"><span data-stu-id="2b77a-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="2b77a-213">GPIO 35 & 47 sind nicht verfügbar, auf dem Raspberry Pi 3.</span><span class="sxs-lookup"><span data-stu-id="2b77a-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="2b77a-214">GPIO-Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b77a-214">GPIO Sample</span></span>

<span data-ttu-id="2b77a-215">Als Beispiel den folgenden code wird **GPIO 5** als Ausgabe und schreibt eine digitale "**1**' Out bei der Pin:</span><span class="sxs-lookup"><span data-stu-id="2b77a-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="2b77a-216">Wenn Sie eine Pin öffnen, werden im Zustand einschalten, die eine Pull-Widerstand enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="2b77a-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="2b77a-217">So trennen Sie die Pull-Widerstände, und erhalten eine hohe-Impedance-Eingabe, legen Sie die Laufwerkmodus auf GpioPinDriveMode.Input ein:</span><span class="sxs-lookup"><span data-stu-id="2b77a-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>

    pin.SetDriveMode(GpioPinDriveMode.Input);

<span data-ttu-id="2b77a-218">Wenn eine Pin geschlossen wird, wird es einschalten Zustand zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="2b77a-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="2b77a-219">PIN-Muxing</span><span class="sxs-lookup"><span data-stu-id="2b77a-219">Pin Muxing</span></span>

<span data-ttu-id="2b77a-220">Einige GPIO-Pins können mehrere Funktionen ausführen.</span><span class="sxs-lookup"><span data-stu-id="2b77a-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="2b77a-221">Standardmäßig sind Pins als GPIO-Eingaben konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="2b77a-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="2b77a-222">Wenn Sie eine Funktion durch den Aufruf öffnen `I2cDevice.FromIdAsync()` oder `SpiDevice.FromIdAsync()` , die Pins, die von der Funktion erforderlich sind, automatisch aktiviert ("(gemischt)"), die ordnungsgemäße Funktion.</span><span class="sxs-lookup"><span data-stu-id="2b77a-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="2b77a-223">Wenn das Gerät durch den Aufruf geschlossen `I2cDevice.Dispose()` oder `SpiDevice.Dispose()`, die Pins zu ihrer Standardfunktion zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2b77a-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="2b77a-224">Wenn Sie versuchen, eine Pin für zwei verschiedene Funktionen auf einmal zu verwenden, wird eine Ausnahme ausgelöst werden, wenn Sie versuchen, die in Konflikt stehende Funktion geöffnet.</span><span class="sxs-lookup"><span data-stu-id="2b77a-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="2b77a-225">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="2b77a-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="2b77a-226">Serielle UART</span><span class="sxs-lookup"><span data-stu-id="2b77a-226">Serial UART</span></span>

<span data-ttu-id="2b77a-227">Auf dem RPi2/3 ist eine serielle UART verfügbar: **UART0**</span><span class="sxs-lookup"><span data-stu-id="2b77a-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="2b77a-228">Pin 8  - **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="2b77a-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="2b77a-229">Pin 10  - **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="2b77a-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="2b77a-230">Im Beispiel unten initialisiert **UART0** und führt einen Schreibvorgang, gefolgt von einem Lesevorgang:</span><span class="sxs-lookup"><span data-stu-id="2b77a-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="2b77a-231">Beachten Sie, dass Sie die folgende Funktion zum Hinzufügen, müssen die **"Package.appxmanifest"** Datei in Ihre UWP-Projekt, um serielle UART Code auszuführen:</span><span class="sxs-lookup"><span data-stu-id="2b77a-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="2b77a-232">Visual Studio 2017 weist ein bekanntes Problem im Manifest-Designer (visuellen Editor für die Appxmanifest-Dateien), die die Funktion Serialcommunication betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="2b77a-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="2b77a-233">Wenn es sich bei Ihrem Appxmanifest Serialcommunication Funktion hinzugefügt wird, wird durch das Ändern Ihrer Appxmanifest mit dem Designer Ihrem Appxmanifest beschädigt (untergeordneten XML-Gerät verloren).</span><span class="sxs-lookup"><span data-stu-id="2b77a-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="2b77a-234">Sie können dieses Problem umgehen von Hand bearbeitet die appxmanifest-Datei mit der rechten Maustaste in Ihrem Appxmanifest, und wählen im Kontextmenü auf Code anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2b77a-234">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="2b77a-235">I2C Bus</span><span class="sxs-lookup"><span data-stu-id="2b77a-235">I2C Bus</span></span>

<span data-ttu-id="2b77a-236">Sehen wir uns die I2C-Bus verfügbare auf diesem Gerät an.</span><span class="sxs-lookup"><span data-stu-id="2b77a-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="2b77a-237">Übersicht über die I2C</span><span class="sxs-lookup"><span data-stu-id="2b77a-237">I2C Overview</span></span>

<span data-ttu-id="2b77a-238">Es ist ein I2C-Controller **I2C1** verfügbar gemacht werden, für den Pin-Header mit nur zwei Zeilen **SDA** und **SCL**.</span><span class="sxs-lookup"><span data-stu-id="2b77a-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="2b77a-239">1.8 K&#x2126; interne Pull-Up-Widerstände bereits auf dem Board nach diesem Bus installiert sind.</span><span class="sxs-lookup"><span data-stu-id="2b77a-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="2b77a-240">Signalname</span><span class="sxs-lookup"><span data-stu-id="2b77a-240">Signal Name</span></span> | <span data-ttu-id="2b77a-241">Header-Pin-Nummer</span><span class="sxs-lookup"><span data-stu-id="2b77a-241">Header Pin Number</span></span> | <span data-ttu-id="2b77a-242">GPIO-Anzahl</span><span class="sxs-lookup"><span data-stu-id="2b77a-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="2b77a-243">SDA</span><span class="sxs-lookup"><span data-stu-id="2b77a-243">SDA</span></span>         | <span data-ttu-id="2b77a-244">3</span><span class="sxs-lookup"><span data-stu-id="2b77a-244">3</span></span>                 | <span data-ttu-id="2b77a-245">2</span><span class="sxs-lookup"><span data-stu-id="2b77a-245">2</span></span>           |
> | <span data-ttu-id="2b77a-246">SCL</span><span class="sxs-lookup"><span data-stu-id="2b77a-246">SCL</span></span>         | <span data-ttu-id="2b77a-247">5</span><span class="sxs-lookup"><span data-stu-id="2b77a-247">5</span></span>                 | <span data-ttu-id="2b77a-248">3</span><span class="sxs-lookup"><span data-stu-id="2b77a-248">3</span></span>           |

<span data-ttu-id="2b77a-249">Im Beispiel unten initialisiert **I2C1** und schreibt Daten in eine I2C-Gerät mit der Adresse **0 x 40**:</span><span class="sxs-lookup"><span data-stu-id="2b77a-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="2b77a-250">SPI-Bus</span><span class="sxs-lookup"><span data-stu-id="2b77a-250">SPI Bus</span></span>

<span data-ttu-id="2b77a-251">Auf dem RPi2/3 sind zwei SPI-Controller verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2b77a-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="2b77a-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="2b77a-252">SPI0</span></span>

> | <span data-ttu-id="2b77a-253">Signalname</span><span class="sxs-lookup"><span data-stu-id="2b77a-253">Signal Name</span></span> | <span data-ttu-id="2b77a-254">Header-Pin-Nummer</span><span class="sxs-lookup"><span data-stu-id="2b77a-254">Header Pin Number</span></span> | <span data-ttu-id="2b77a-255">GPIO-Anzahl</span><span class="sxs-lookup"><span data-stu-id="2b77a-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="2b77a-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="2b77a-256">MOSI</span></span>        | <span data-ttu-id="2b77a-257">19</span><span class="sxs-lookup"><span data-stu-id="2b77a-257">19</span></span>                | <span data-ttu-id="2b77a-258">10</span><span class="sxs-lookup"><span data-stu-id="2b77a-258">10</span></span>          |
> | <span data-ttu-id="2b77a-259">MISO</span><span class="sxs-lookup"><span data-stu-id="2b77a-259">MISO</span></span>        | <span data-ttu-id="2b77a-260">21</span><span class="sxs-lookup"><span data-stu-id="2b77a-260">21</span></span>                | <span data-ttu-id="2b77a-261">9</span><span class="sxs-lookup"><span data-stu-id="2b77a-261">9</span></span>           |
> | <span data-ttu-id="2b77a-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="2b77a-262">SCLK</span></span>        | <span data-ttu-id="2b77a-263">23</span><span class="sxs-lookup"><span data-stu-id="2b77a-263">23</span></span>                | <span data-ttu-id="2b77a-264">11</span><span class="sxs-lookup"><span data-stu-id="2b77a-264">11</span></span>          |
> | <span data-ttu-id="2b77a-265">CS0</span><span class="sxs-lookup"><span data-stu-id="2b77a-265">CS0</span></span>         | <span data-ttu-id="2b77a-266">24</span><span class="sxs-lookup"><span data-stu-id="2b77a-266">24</span></span>                | <span data-ttu-id="2b77a-267">8</span><span class="sxs-lookup"><span data-stu-id="2b77a-267">8</span></span>           |
> | <span data-ttu-id="2b77a-268">CS1</span><span class="sxs-lookup"><span data-stu-id="2b77a-268">CS1</span></span>         | <span data-ttu-id="2b77a-269">26</span><span class="sxs-lookup"><span data-stu-id="2b77a-269">26</span></span>                | <span data-ttu-id="2b77a-270">7</span><span class="sxs-lookup"><span data-stu-id="2b77a-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="2b77a-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="2b77a-271">SPI1</span></span>

> | <span data-ttu-id="2b77a-272">Signalname</span><span class="sxs-lookup"><span data-stu-id="2b77a-272">Signal Name</span></span> | <span data-ttu-id="2b77a-273">Header-Pin-Nummer</span><span class="sxs-lookup"><span data-stu-id="2b77a-273">Header Pin Number</span></span> | <span data-ttu-id="2b77a-274">GPIO-Anzahl</span><span class="sxs-lookup"><span data-stu-id="2b77a-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="2b77a-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="2b77a-275">MOSI</span></span>        | <span data-ttu-id="2b77a-276">38</span><span class="sxs-lookup"><span data-stu-id="2b77a-276">38</span></span>                | <span data-ttu-id="2b77a-277">20</span><span class="sxs-lookup"><span data-stu-id="2b77a-277">20</span></span>          |
> | <span data-ttu-id="2b77a-278">MISO</span><span class="sxs-lookup"><span data-stu-id="2b77a-278">MISO</span></span>        | <span data-ttu-id="2b77a-279">35</span><span class="sxs-lookup"><span data-stu-id="2b77a-279">35</span></span>                | <span data-ttu-id="2b77a-280">19</span><span class="sxs-lookup"><span data-stu-id="2b77a-280">19</span></span>          |
> | <span data-ttu-id="2b77a-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="2b77a-281">SCLK</span></span>        | <span data-ttu-id="2b77a-282">40</span><span class="sxs-lookup"><span data-stu-id="2b77a-282">40</span></span>                | <span data-ttu-id="2b77a-283">21</span><span class="sxs-lookup"><span data-stu-id="2b77a-283">21</span></span>          |
> | <span data-ttu-id="2b77a-284">CS0</span><span class="sxs-lookup"><span data-stu-id="2b77a-284">CS0</span></span>         | <span data-ttu-id="2b77a-285">36</span><span class="sxs-lookup"><span data-stu-id="2b77a-285">36</span></span>                | <span data-ttu-id="2b77a-286">16</span><span class="sxs-lookup"><span data-stu-id="2b77a-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="2b77a-287">SPI-Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b77a-287">SPI Sample</span></span>

<span data-ttu-id="2b77a-288">Ein Beispiel zum Durchführen einer SPI Schreiben auf Bus **SPI0** mit Chip Select, 0, wird im folgenden dargestellt:</span><span class="sxs-lookup"><span data-stu-id="2b77a-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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

