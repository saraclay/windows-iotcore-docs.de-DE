---
title: Bus-Anbieter
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zu den verschiedenen Anbietern, die über Windows 10 IoT Core zur Verfügung.
keywords: Windows Iot "," Anbieter "," Bus-Anbieter, UWP, Gpio, Spi
ms.openlocfilehash: 63e62e649aa6f54576e47419fe0be86ae5e5f096
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513161"
---
# <a name="bus-providers"></a><span data-ttu-id="e34bb-104">Bus-Anbieter</span><span class="sxs-lookup"><span data-stu-id="e34bb-104">Bus Providers</span></span>

<span data-ttu-id="e34bb-105">Ab Windows 10, umfasst Windows integrierte UWP-APIs, die direkten Zugriff auf Gpio, Spi, ermöglichen oder I2c-Bussen befindet sich auf SOC Dies kann sehr einfach auf diese Hardware von einer hohen Ebene API.</span><span class="sxs-lookup"><span data-stu-id="e34bb-105">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="e34bb-106">Es gibt jedoch auch oft ein möchte, dass ein Gerätehersteller einen deaktiviert Soc-Controller zu verwenden, um einen Bus zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="e34bb-106">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="e34bb-107">Es kann sein, so einfach wie eine günstige Chip, der 16 GPIO-Pins hinzugefügt oder so umfangreich wie eine vollständige MCU (z. B. einem arduino-Board), die nicht nur I2C, SPI und Gpio-Pins fügt, sondern auch PWM und ADC unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e34bb-107">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="e34bb-108">Mit dem "Bus" Providermodell bieten wir Entwicklern den Zugriff auf diese aus Soc Bussen anzubringen, die mithilfe der integrierten APIs mithilfe eines Anbieters im Benutzermodus, Bridges die Lücke zu.</span><span class="sxs-lookup"><span data-stu-id="e34bb-108">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span> 

<span data-ttu-id="e34bb-109">Ein Benutzer das Erstellen eines Anbieters implementiert einen Satz von Schnittstellen in einer UWP-Klassenbibliothek, und klicken Sie dann alle Entwickler, die die zu sprechen, dass Hardware einfach die Komponente enthält und die integrierte APIs darüber informiert.</span><span class="sxs-lookup"><span data-stu-id="e34bb-109">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="e34bb-110">Wenn Sie sich an den Beispielcode ansehen der [Remote Arduino Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) sehen Sie, wie einfach es ist zum Konfigurieren des Anbieters und nach dem Festlegen als Standardanbieter für diese app der Rest des Codes in die Client-app ist identisch mit dem Code erforderlich, um eine Zugriff einem auf Soc-Bus.</span><span class="sxs-lookup"><span data-stu-id="e34bb-110">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>  

```
ArduinoProviders.ArduinoProvider.Configuration = 
    new ArduinoProviders.ArduinoConnectionConfiguration("VID_2341", "PID_0043", 57600);
Windows.Devices.LowLevelDevicesController.DefaultProvider =  new ArduinoProviders.ArduinoProvider();

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
adcController = await AdcController.GetDefaultAsync();
pwmController = await PwmController.GetDefaultAsync();

GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);`
```

## <a name="available-providers"></a><span data-ttu-id="e34bb-111">Verfügbare Anbieter</span><span class="sxs-lookup"><span data-stu-id="e34bb-111">Available Providers</span></span>

<span data-ttu-id="e34bb-112">Wir haben gerade eine Anzahl von Anbietern, die auf die [Bus Anbieter](https://github.com/ms-iot/BusProviders) Github-Repository.</span><span class="sxs-lookup"><span data-stu-id="e34bb-112">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="e34bb-113">Zusätzlich zu den Code für den Anbieter verfügt jeder Anbieter eine beispiellösung für das Visual Studio, die veranschaulicht, wie ein Client diesen Anbieter verwenden würden.</span><span class="sxs-lookup"><span data-stu-id="e34bb-113">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

* <span data-ttu-id="e34bb-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="e34bb-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span></span>
* <span data-ttu-id="e34bb-115">PWM \*\* PCA9685 \*\* simuliert mit Gpio \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="e34bb-115">PWM \*\* PCA9685 \*\* Simulated with Gpio \*\* Remote Arduino</span></span>
* <span data-ttu-id="e34bb-116">GPIO, SPI, I2c \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="e34bb-116">Gpio, SPI, I2c \*\* Remote Arduino</span></span>

<span data-ttu-id="e34bb-117">Zusätzlich zu den Anbieter, die Sie Zugriff auf echter Hardware erhalten, haben wir erstellt eine [Anbieter simuliert](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) , die angewendet wird, wenn es einen Inifitely-fähige-Anbieter und entwickelt wurde, mit dem Schreiben und Debuggen Sie Ihre Anwendungen ohne zuerst bereitstellen Sie auf einem Gerät arbeiten.</span><span class="sxs-lookup"><span data-stu-id="e34bb-117">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="e34bb-118">Für eine umfangreichere Benutzeroberfläche verwenden können Sie darauf, um die tatsächliche Hardware simulieren anpassen.</span><span class="sxs-lookup"><span data-stu-id="e34bb-118">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="e34bb-119">Zum Beispiel: die I2c-Anbieter zurückgegeben wird aktualisiert. das Ergebnis "75" zurück, wenn Sie den Befehl für ein Temperaturwert auf einem Gerät mit der angegebenen untergeordneten Adresse senden.</span><span class="sxs-lookup"><span data-stu-id="e34bb-119">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span> 
