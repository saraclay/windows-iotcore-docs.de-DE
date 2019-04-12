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
# <a name="bus-providers"></a>Bus-Anbieter

Ab Windows 10, umfasst Windows integrierte UWP-APIs, die direkten Zugriff auf Gpio, Spi, ermöglichen oder I2c-Bussen befindet sich auf SOC Dies kann sehr einfach auf diese Hardware von einer hohen Ebene API. Es gibt jedoch auch oft ein möchte, dass ein Gerätehersteller einen deaktiviert Soc-Controller zu verwenden, um einen Bus zuzugreifen. Es kann sein, so einfach wie eine günstige Chip, der 16 GPIO-Pins hinzugefügt oder so umfangreich wie eine vollständige MCU (z. B. einem arduino-Board), die nicht nur I2C, SPI und Gpio-Pins fügt, sondern auch PWM und ADC unterstützt. Mit dem "Bus" Providermodell bieten wir Entwicklern den Zugriff auf diese aus Soc Bussen anzubringen, die mithilfe der integrierten APIs mithilfe eines Anbieters im Benutzermodus, Bridges die Lücke zu. 

Ein Benutzer das Erstellen eines Anbieters implementiert einen Satz von Schnittstellen in einer UWP-Klassenbibliothek, und klicken Sie dann alle Entwickler, die die zu sprechen, dass Hardware einfach die Komponente enthält und die integrierte APIs darüber informiert. Wenn Sie sich an den Beispielcode ansehen der [Remote Arduino Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) sehen Sie, wie einfach es ist zum Konfigurieren des Anbieters und nach dem Festlegen als Standardanbieter für diese app der Rest des Codes in die Client-app ist identisch mit dem Code erforderlich, um eine Zugriff einem auf Soc-Bus.  

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

## <a name="available-providers"></a>Verfügbare Anbieter

Wir haben gerade eine Anzahl von Anbietern, die auf die [Bus Anbieter](https://github.com/ms-iot/BusProviders) Github-Repository. Zusätzlich zu den Code für den Anbieter verfügt jeder Anbieter eine beispiellösung für das Visual Studio, die veranschaulicht, wie ein Client diesen Anbieter verwenden würden. 

* ADC ** Ads1x15 ** Mcp3008 ** Remote Arduino
* PWM ** PCA9685 ** simuliert mit Gpio ** Remote Arduino
* GPIO, SPI, I2c ** Remote Arduino

Zusätzlich zu den Anbieter, die Sie Zugriff auf echter Hardware erhalten, haben wir erstellt eine [Anbieter simuliert](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) , die angewendet wird, wenn es einen Inifitely-fähige-Anbieter und entwickelt wurde, mit dem Schreiben und Debuggen Sie Ihre Anwendungen ohne zuerst bereitstellen Sie auf einem Gerät arbeiten. Für eine umfangreichere Benutzeroberfläche verwenden können Sie darauf, um die tatsächliche Hardware simulieren anpassen. Zum Beispiel: die I2c-Anbieter zurückgegeben wird aktualisiert. das Ergebnis "75" zurück, wenn Sie den Befehl für ein Temperaturwert auf einem Gerät mit der angegebenen untergeordneten Adresse senden. 
