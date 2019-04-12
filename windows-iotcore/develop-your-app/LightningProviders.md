---
title: Lightning-Anbieter
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Hier erfahren Sie, wie Sie die Lightning-Anbieter für Microsoft-Bibliothek verwenden können.
keywords: Windows Iot, Lightning-Anbieter, Lightning Leistungstests, Bussen
ms.openlocfilehash: 8f290bf741f64e07b7b048287128e1ae42ef6b9e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513625"
---
# <a name="working-with-lightning-providers"></a>Arbeiten mit Lightning-Anbieter
Die Microsoft.IoT.Lightning.Providers-Bibliothek enthält einen Satz der Anbieter eine Verbindung mit dem on-Board Controller Busse über die Lightning zugeordneten Memory-Treiber (DMAP) weiterzuleiten.


## <a name="about-the-direct-memory-mapped-driver-dmap"></a>Informationen zu den direkte Speicher zugeordnet Treiber (DMAP)

Der Treiber DMAP handelt es sich um eine in der Entwicklung-Treiber, der GPIO-leistungsverbesserungen über den Posteingang Standardtreiber ermöglicht. Weitere Informationen zu diesen-Leistungssteigerungen finden Sie unter den [Lightning Leistungstests](../develop-your-app/LightningPerformance.md) Seite.

Beim DMAP Treiber Angebot GPIO leistungsverbesserungen über den Posteingang-Treiber sind Controller-Befehle für jeden Controller an den Treiber DMAP über Benutzermodus im Speicher abgebildete Adressen gesendet. Eine app, die nur die Lightning Anbieter-APIs oder Microsoft.IoT.Lightning.Providers verwendet. Eine böswillige Anwendung wäre jedoch direkt für den Speicher schreiben und Hardware-/Sicherheitsprobleme verursachen können. Auf einem Computer mit nur vertrauenswürdige apps ist die DMAP verwenden im Allgemeinen sicher.   

## <a name="obtaining-the-library"></a>Abrufen der Bibliotheks

Die Bibliothek wird bereitgestellt, als Teil der [Lightning-SDK-Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.Lightning) mit Quellcode zur Verfügung, auf [ms-Iot/Lightning GitHub-Repository](https://github.com/ms-iot/lightning/).

Darüber hinaus finden Beispiele, die zeigt, wie mit den verschiedenen Anbietern stehen auf [ms-Iot/BusProviders GitHub-Repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).

## <a name="adding-the-library-to-your-application"></a>Hinzufügen der Bibliothek zu Ihrer Anwendung

### <a name="option-1-starting-from-an-existing-sample"></a>Option 1: Beginnend mit einem vorhandenen Beispiel
Eine schnelle Möglichkeit zum beginnen mit dem Programmieren, verwenden die Lightning-Anbieter wird gestartet mit einem der in den Beispielen in den [ms-Iot/BusProviders GitHub-Repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).

Jedes der Beispiele verweist auf das SDK Lightning und ordnungsgemäß konfiguriert ist und die Lightning-Anbieter-Bibliothek verwenden.

**Beachten Sie**, um das Ausführen der Beispiele, DMAP Treiber müssen mit dem Webportal für Windows-Geräte aktiviert werden. Finden Sie in der [Lightning-Installationshandbuch](LightningSetup.md) für ausführliche Informationen zu aktivieren.

### <a name="option-2-referencing-the-library"></a>Option 2: Verweis auf die Bibliothek

Darüber hinaus ist es einfach, fügen Sie den erforderlichen Lightning Providers Nuget-Verweis, und um eine neue oder vorhandene Anwendungen zu unterstützen. Führen Sie die unten beschriebenen Schritte aus.

1. Klicken Sie in der Anwendung klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf der "NuGet Pakete verwalten..." Menüelement ![UWP-Projekt](../media/LightningProviders/manage-nuget-project.png)

2. Die NuGet-Paket-Manager wird geöffnet. Suchen Sie in der Registerkarte "Durchsuchen" für das "Lightning SDK", sodass Sie sicher, dass das Kontrollkästchen "Vorabversion einbeziehen" aktivieren.

3. Wählen Sie die neueste Version aus, und klicken Sie auf "Installieren", um das Lightning-SDK Ihrem Projekt hinzufügen. 
![NuGet-Paket-Manager](../media/LightningProviders/nuget-package-manager.png)

4. Befolgen Sie alle auf dem Bildschirm Anweisungen bei Bedarf. Wenn die Installation abgeschlossen ist, wird ein Verweis auf das Lightning-SDK zu Ihrem Projekt hinzugefügt werden.

![Lightning-SDK-Referenz](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. Fügen Sie den folgenden Code auf Ihrem manifest-Datei "Package.appxmanifest" hinzu.

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* Die erste ist eine Funktion, mit die die Anwendung auf benutzerdefinierte Geräte zugreifen kann.
* Die zweite ist die Geräte-Guid-Id für die Lightning-Schnittstelle

Beide Funktionen müssen hinzugefügt werden, um die AppX-Datei des Projekts unter manifest die `<Capabilities>` Knoten. Stellen Sie außerdem sicherstellen, dass die erforderlichen Namespaces in Ihr Manifest hinzugefügt werden, wenn erforderlich.

![AppX-Manifests Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a>Aktualisieren Ihren Code, um die Lightning-Anbieter verwenden

### <a name="checking-for-the-lightning-dmap-driver"></a>Überprüfen für den Treiber Lightning (DMAP)

Zum Überprüfen, ob Lightning aktiviert ist, die `LightningProvider.IsLightningEnabled` Eigenschaft sollte verwendet werden. Im Allgemeinen empfiehlt es sich bewährt, überprüfen, ob der Lightning-Treiber aktiviert ist, bevor Lightning Anbieter-APIs verwenden. 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a>Allgemeine Verwendungsmuster

Die einfachste Möglichkeit, die Anbieter verwenden ist den Lightning-Anbieter wird standardmäßig in Ihrer app festgelegt. 

Der Code unten, wenn der Lightning-Anbieter verfügbar ist, ist festgelegt `Microsoft.IoT.Lightning.Providers.LightningProvider` als Standardanbieter. Andernfalls, wenn kein Standardanbieter explizit festgelegt wurde, greift der verschiedenen Bussen auf den Standardwert zurück.
``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
if (LightningProvider.IsLightningEnabled)
{
    LowLevelDevicesController.DefaultProvider = LightningProvider.GetAggregateProvider();
}

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
spiController = await SpiController.GetDefaultAsync();
```

Nachdem Sie einen Controller für den gewünschten Bus haben, können Sie ihn wie gewohnt verwenden. 

### <a name="using-lightning-for-individual-buses"></a>Verwenden für einzelne Busse Lightning

Wenn Sie einen anderen Standardwert-Anbieter verwenden möchten, zeigen in den folgenden Abschnitten, wie Sie die Lightning-Anbieter für einzelne Bussen verwenden können. 

#### <a name="for-gpio-bus-controller"></a>Für den Bus GPIO-Controller:

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.Gpio;

if (LightningProvider.IsLightningEnabled)
{
    GpioController gpioController = (await GpioController.GetControllersAsync(LightningGpioProvider.GetGpioProvider()))[0];
    GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);
}
```

#### <a name="for-i2c-bus-controller"></a>Für I2C-Bus-Controller:

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.I2c;

if (LightningProvider.IsLightningEnabled)
{
    I2cController controller =  (await I2cController.GetControllersAsync(LightningI2cProvider.GetI2cProvider()))[0];
    I2cDevice sensor = controller.GetDevice(new I2cConnectionSettings(0x40));
}
```

#### <a name="for-spi-bus-controller"></a>Für SPI-Bus-Controller:
Verwenden von Microsoft.IoT.Lightning.Providers; verwenden die "Windows.Devices"; Verwenden von Windows.Devices.Spi;

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a>Beispiele für Tabellenprofilanbieter Lightning

Die folgenden Beispiele veranschaulichen die Verwendung des Anbieter-Lightning mit unterstützten Bustypen:

* [(UI) mit Lightning Anbieter Hauptverkaufsargument](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) veranschaulicht GPIO mit Lightning-Anbieter in einer Anwendung im Vordergrund

* [BlinkyHeadless mit Lightning Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) GPIO mit Lightning-Anbieter in einer Anwendung monitorlose veranschaulicht

* [SPIDisplay mit Lightning Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) veranschaulicht die Verwendung der API zum Steuern eines Geräts mithilfe des SPI mit Lightning-Anbieter
 
* [WeatherStation mit Lightning Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) Interaktion mit einem Gerät mithilfe von I2C mit Lightning-Anbieter

## <a name="build-requirements"></a>Erstellen von Anforderungen



### <a name="windows-sdk-update"></a>Windows SDK-Update

Windows-SDKS, die zum Erstellen und Verwenden der Bibliotheks erforderlich ist, 10.0.10586.0 oder höher herunterladen können aus [hier](https://dev.windows.com/en-US/downloads/windows-10-sdk).

Weitere Informationen zu alles einrichten, finden Sie unter [unserer erste-Schritte.](https://developer.microsoft.com/en-us/windows/iot/getstarted).

### <a name="nuget-package-dependencies"></a>NuGet-Paketabhängigkeiten

Hängt von die Lightning-Anbieterbibliothek der [Microsoft.IoT.Lightning Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.Lightning), welche wiederum hängt von der [Arduino-SDK-Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino). Beide Nuget-Pakete auf die in der Library-Projekten verwiesen wird, und aus "NuGet.org" verfügbar sind.

Bei Bedarf Quellcode für die einzelnen steht auch auf GitHub unter den [Lightning](https://github.com/ms-iot/lightning) und [Arduino SDK](https://github.com/ms-iot/arduino-sdk) Repositorys.

Derzeit ist Microsoft.IoT.Lightning Nuget noch Vorabversion, damit von Nuget.org, aktualisiert werden soll, wenn neuere Versionen verfügbar sind.

Stellen Sie sicher, dass die Option "Vorabversion einbeziehen" in der Nuget-Paket-Manager festgelegt Schritte aus, um installieren (aktuellen) Vorabversion Microsoft.IoT.Lightning Nuget-Pakets als auch für diese Aktualisierungen des Pakets Lightning erhalten.

1. Rechtsklick in Ihrem Projekt Verweise
1. Klicken Sie auf "Nuget-Pakete verwalten"
1. Wählen Sie für Lightning-Nuget-Paketquellen
1. Klicken Sie auf "Vorabversion einbeziehen".
1. Klicken Sie auf "Installieren", um das Nuget-Paket zu Ihrem Projekt zu installieren.

![Paket-Manager-Konfiguration](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a>Laufzeitanforderungen

### <a name="windows-iot-core-fall-update-required"></a>Windows IoT Core Herbst Update erforderlich
Lightning-Anbieter, die derzeit in Fall Update unterstützt wird, erstellt Windows IoT Core.
Sie können ein Windows 10 IoT Core-Image aus unserem [Downloadseite](https://developer.microsoft.com/windows/iot/Downloads). Klicken Sie auf "Herunterladen von Insider Preview" auf, um für Ihren Gerätetyp.

### <a name="direct-memory-mapped-driver-must-be-enabled"></a>Treiber für den direkten zugewiesenem Speicher muss aktiviert sein
 
Die in der Bibliothek Lightning-Anbieter-APIs erfordern den Lightning Direct Memory-Mapped-Treiber auf dem Gerät aktiviert sein. Sowohl Raspberry Pi 2/3-MinnowBoard Max haben Sie den Treiber verfügbar, aber nicht standardmäßig aktiviert.

Der Treiber kann mit dem Webportal für Windows-Geräte aktiviert werden. Finden Sie in der [Lightning-Installationshandbuch](LightningSetup.md) ausführliche Informationen zum Aktivieren des Lightning-Treibers.

![Seite "Geräte"](../media/LightningProviders/dmap4.png)

Der Treiber kann auch mit dem Befehl DmapUtil aktiviert werden:

DmapUtil: Hilfsprogramm, um beim DMAP direct-Memory-Mapper-Treiber zu aktivieren, oder die Nutzung: dmaputil.exe-Status | aktivieren | deaktivierungszustand [-V] Drucken von, ob Dmap derzeit aktiviert ist. Übergeben Sie das Flag "- V" detaillierte Informationen zur Konfiguration.
Enable Dmap beim nächsten Systemstart zu aktivieren.
Disable Dmap beim nächsten Systemstart zu deaktivieren.
