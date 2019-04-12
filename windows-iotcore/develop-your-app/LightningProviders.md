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
# <a name="working-with-lightning-providers"></a><span data-ttu-id="f6712-104">Arbeiten mit Lightning-Anbieter</span><span class="sxs-lookup"><span data-stu-id="f6712-104">Working with lightning providers</span></span>
<span data-ttu-id="f6712-105">Die Microsoft.IoT.Lightning.Providers-Bibliothek enthält einen Satz der Anbieter eine Verbindung mit dem on-Board Controller Busse über die Lightning zugeordneten Memory-Treiber (DMAP) weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="f6712-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="f6712-106">Informationen zu den direkte Speicher zugeordnet Treiber (DMAP)</span><span class="sxs-lookup"><span data-stu-id="f6712-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="f6712-107">Der Treiber DMAP handelt es sich um eine in der Entwicklung-Treiber, der GPIO-leistungsverbesserungen über den Posteingang Standardtreiber ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f6712-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="f6712-108">Weitere Informationen zu diesen-Leistungssteigerungen finden Sie unter den [Lightning Leistungstests](../develop-your-app/LightningPerformance.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="f6712-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="f6712-109">Beim DMAP Treiber Angebot GPIO leistungsverbesserungen über den Posteingang-Treiber sind Controller-Befehle für jeden Controller an den Treiber DMAP über Benutzermodus im Speicher abgebildete Adressen gesendet.</span><span class="sxs-lookup"><span data-stu-id="f6712-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="f6712-110">Eine app, die nur die Lightning Anbieter-APIs oder Microsoft.IoT.Lightning.Providers verwendet.</span><span class="sxs-lookup"><span data-stu-id="f6712-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="f6712-111">Eine böswillige Anwendung wäre jedoch direkt für den Speicher schreiben und Hardware-/Sicherheitsprobleme verursachen können.</span><span class="sxs-lookup"><span data-stu-id="f6712-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="f6712-112">Auf einem Computer mit nur vertrauenswürdige apps ist die DMAP verwenden im Allgemeinen sicher.</span><span class="sxs-lookup"><span data-stu-id="f6712-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="f6712-113">Abrufen der Bibliotheks</span><span class="sxs-lookup"><span data-stu-id="f6712-113">Obtaining the library</span></span>

<span data-ttu-id="f6712-114">Die Bibliothek wird bereitgestellt, als Teil der [Lightning-SDK-Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.Lightning) mit Quellcode zur Verfügung, auf [ms-Iot/Lightning GitHub-Repository](https://github.com/ms-iot/lightning/).</span><span class="sxs-lookup"><span data-stu-id="f6712-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="f6712-115">Darüber hinaus finden Beispiele, die zeigt, wie mit den verschiedenen Anbietern stehen auf [ms-Iot/BusProviders GitHub-Repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span><span class="sxs-lookup"><span data-stu-id="f6712-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="f6712-116">Hinzufügen der Bibliothek zu Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="f6712-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="f6712-117">Option 1: Beginnend mit einem vorhandenen Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6712-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="f6712-118">Eine schnelle Möglichkeit zum beginnen mit dem Programmieren, verwenden die Lightning-Anbieter wird gestartet mit einem der in den Beispielen in den [ms-Iot/BusProviders GitHub-Repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span><span class="sxs-lookup"><span data-stu-id="f6712-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="f6712-119">Jedes der Beispiele verweist auf das SDK Lightning und ordnungsgemäß konfiguriert ist und die Lightning-Anbieter-Bibliothek verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6712-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="f6712-120">**Beachten Sie**, um das Ausführen der Beispiele, DMAP Treiber müssen mit dem Webportal für Windows-Geräte aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="f6712-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="f6712-121">Finden Sie in der [Lightning-Installationshandbuch](LightningSetup.md) für ausführliche Informationen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f6712-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="f6712-122">Option 2: Verweis auf die Bibliothek</span><span class="sxs-lookup"><span data-stu-id="f6712-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="f6712-123">Darüber hinaus ist es einfach, fügen Sie den erforderlichen Lightning Providers Nuget-Verweis, und um eine neue oder vorhandene Anwendungen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f6712-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="f6712-124">Führen Sie die unten beschriebenen Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="f6712-124">Follow the steps below:</span></span>

1. <span data-ttu-id="f6712-125">Klicken Sie in der Anwendung klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf der "NuGet Pakete verwalten..." Menüelement ![UWP-Projekt</span><span class="sxs-lookup"><span data-stu-id="f6712-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item ![UWP Project</span></span>](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="f6712-126">Die NuGet-Paket-Manager wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="f6712-126">The NuGet Package Manager will open.</span></span> <span data-ttu-id="f6712-127">Suchen Sie in der Registerkarte "Durchsuchen" für das "Lightning SDK", sodass Sie sicher, dass das Kontrollkästchen "Vorabversion einbeziehen" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f6712-127">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="f6712-128">Wählen Sie die neueste Version aus, und klicken Sie auf "Installieren", um das Lightning-SDK Ihrem Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f6712-128">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
![NuGet-Paket-Manager](../media/LightningProviders/nuget-package-manager.png)

4. <span data-ttu-id="f6712-130">Befolgen Sie alle auf dem Bildschirm Anweisungen bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="f6712-130">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="f6712-131">Wenn die Installation abgeschlossen ist, wird ein Verweis auf das Lightning-SDK zu Ihrem Projekt hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f6712-131">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![Lightning-SDK-Referenz](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="f6712-133">Fügen Sie den folgenden Code auf Ihrem manifest-Datei "Package.appxmanifest" hinzu.</span><span class="sxs-lookup"><span data-stu-id="f6712-133">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="f6712-134">Die erste ist eine Funktion, mit die die Anwendung auf benutzerdefinierte Geräte zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="f6712-134">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="f6712-135">Die zweite ist die Geräte-Guid-Id für die Lightning-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f6712-135">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="f6712-136">Beide Funktionen müssen hinzugefügt werden, um die AppX-Datei des Projekts unter manifest die `<Capabilities>` Knoten.</span><span class="sxs-lookup"><span data-stu-id="f6712-136">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="f6712-137">Stellen Sie außerdem sicherstellen, dass die erforderlichen Namespaces in Ihr Manifest hinzugefügt werden, wenn erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f6712-137">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![AppX-Manifests Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="f6712-139">Aktualisieren Ihren Code, um die Lightning-Anbieter verwenden</span><span class="sxs-lookup"><span data-stu-id="f6712-139">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="f6712-140">Überprüfen für den Treiber Lightning (DMAP)</span><span class="sxs-lookup"><span data-stu-id="f6712-140">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="f6712-141">Zum Überprüfen, ob Lightning aktiviert ist, die `LightningProvider.IsLightningEnabled` Eigenschaft sollte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f6712-141">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="f6712-142">Im Allgemeinen empfiehlt es sich bewährt, überprüfen, ob der Lightning-Treiber aktiviert ist, bevor Lightning Anbieter-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6712-142">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="f6712-143">Allgemeine Verwendungsmuster</span><span class="sxs-lookup"><span data-stu-id="f6712-143">General usage pattern</span></span>

<span data-ttu-id="f6712-144">Die einfachste Möglichkeit, die Anbieter verwenden ist den Lightning-Anbieter wird standardmäßig in Ihrer app festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f6712-144">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="f6712-145">Der Code unten, wenn der Lightning-Anbieter verfügbar ist, ist festgelegt `Microsoft.IoT.Lightning.Providers.LightningProvider` als Standardanbieter.</span><span class="sxs-lookup"><span data-stu-id="f6712-145">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="f6712-146">Andernfalls, wenn kein Standardanbieter explizit festgelegt wurde, greift der verschiedenen Bussen auf den Standardwert zurück.</span><span class="sxs-lookup"><span data-stu-id="f6712-146">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
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

<span data-ttu-id="f6712-147">Nachdem Sie einen Controller für den gewünschten Bus haben, können Sie ihn wie gewohnt verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6712-147">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="f6712-148">Verwenden für einzelne Busse Lightning</span><span class="sxs-lookup"><span data-stu-id="f6712-148">Using Lightning for individual buses</span></span>

<span data-ttu-id="f6712-149">Wenn Sie einen anderen Standardwert-Anbieter verwenden möchten, zeigen in den folgenden Abschnitten, wie Sie die Lightning-Anbieter für einzelne Bussen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f6712-149">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="f6712-150">Für den Bus GPIO-Controller:</span><span class="sxs-lookup"><span data-stu-id="f6712-150">For GPIO bus controller:</span></span>

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

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="f6712-151">Für I2C-Bus-Controller:</span><span class="sxs-lookup"><span data-stu-id="f6712-151">For I2C bus controller:</span></span>

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

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="f6712-152">Für SPI-Bus-Controller:</span><span class="sxs-lookup"><span data-stu-id="f6712-152">For SPI bus controller:</span></span>
<span data-ttu-id="f6712-153">Verwenden von Microsoft.IoT.Lightning.Providers; verwenden die "Windows.Devices"; Verwenden von Windows.Devices.Spi;</span><span class="sxs-lookup"><span data-stu-id="f6712-153">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="f6712-154">Beispiele für Tabellenprofilanbieter Lightning</span><span class="sxs-lookup"><span data-stu-id="f6712-154">Lightning Provider Samples</span></span>

<span data-ttu-id="f6712-155">Die folgenden Beispiele veranschaulichen die Verwendung des Anbieter-Lightning mit unterstützten Bustypen:</span><span class="sxs-lookup"><span data-stu-id="f6712-155">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="f6712-156">[(UI) mit Lightning Anbieter Hauptverkaufsargument](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) veranschaulicht GPIO mit Lightning-Anbieter in einer Anwendung im Vordergrund</span><span class="sxs-lookup"><span data-stu-id="f6712-156">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="f6712-157">[BlinkyHeadless mit Lightning Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) GPIO mit Lightning-Anbieter in einer Anwendung monitorlose veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="f6712-157">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="f6712-158">[SPIDisplay mit Lightning Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) veranschaulicht die Verwendung der API zum Steuern eines Geräts mithilfe des SPI mit Lightning-Anbieter</span><span class="sxs-lookup"><span data-stu-id="f6712-158">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="f6712-159">[WeatherStation mit Lightning Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) Interaktion mit einem Gerät mithilfe von I2C mit Lightning-Anbieter</span><span class="sxs-lookup"><span data-stu-id="f6712-159">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="f6712-160">Erstellen von Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f6712-160">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="f6712-161">Windows SDK-Update</span><span class="sxs-lookup"><span data-stu-id="f6712-161">Windows SDK Update</span></span>

<span data-ttu-id="f6712-162">Windows-SDKS, die zum Erstellen und Verwenden der Bibliotheks erforderlich ist, 10.0.10586.0 oder höher herunterladen können aus [hier](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="f6712-162">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="f6712-163">Weitere Informationen zu alles einrichten, finden Sie unter [unserer erste-Schritte.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span><span class="sxs-lookup"><span data-stu-id="f6712-163">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="f6712-164">NuGet-Paketabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="f6712-164">Nuget Package Dependencies</span></span>

<span data-ttu-id="f6712-165">Hängt von die Lightning-Anbieterbibliothek der [Microsoft.IoT.Lightning Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.Lightning), welche wiederum hängt von der [Arduino-SDK-Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span><span class="sxs-lookup"><span data-stu-id="f6712-165">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="f6712-166">Beide Nuget-Pakete auf die in der Library-Projekten verwiesen wird, und aus "NuGet.org" verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="f6712-166">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="f6712-167">Bei Bedarf Quellcode für die einzelnen steht auch auf GitHub unter den [Lightning](https://github.com/ms-iot/lightning) und [Arduino SDK](https://github.com/ms-iot/arduino-sdk) Repositorys.</span><span class="sxs-lookup"><span data-stu-id="f6712-167">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="f6712-168">Derzeit ist Microsoft.IoT.Lightning Nuget noch Vorabversion, damit von Nuget.org, aktualisiert werden soll, wenn neuere Versionen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="f6712-168">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="f6712-169">Stellen Sie sicher, dass die Option "Vorabversion einbeziehen" in der Nuget-Paket-Manager festgelegt Schritte aus, um installieren (aktuellen) Vorabversion Microsoft.IoT.Lightning Nuget-Pakets als auch für diese Aktualisierungen des Pakets Lightning erhalten.</span><span class="sxs-lookup"><span data-stu-id="f6712-169">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="f6712-170">Rechtsklick in Ihrem Projekt Verweise</span><span class="sxs-lookup"><span data-stu-id="f6712-170">Right click References in your project</span></span>
1. <span data-ttu-id="f6712-171">Klicken Sie auf "Nuget-Pakete verwalten"</span><span class="sxs-lookup"><span data-stu-id="f6712-171">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="f6712-172">Wählen Sie für Lightning-Nuget-Paketquellen</span><span class="sxs-lookup"><span data-stu-id="f6712-172">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="f6712-173">Klicken Sie auf "Vorabversion einbeziehen".</span><span class="sxs-lookup"><span data-stu-id="f6712-173">Click "Include prerelease".</span></span>
1. <span data-ttu-id="f6712-174">Klicken Sie auf "Installieren", um das Nuget-Paket zu Ihrem Projekt zu installieren.</span><span class="sxs-lookup"><span data-stu-id="f6712-174">Click "Install" to install the nuget package to your project</span></span>

![Paket-Manager-Konfiguration](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="f6712-176">Laufzeitanforderungen</span><span class="sxs-lookup"><span data-stu-id="f6712-176">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="f6712-177">Windows IoT Core Herbst Update erforderlich</span><span class="sxs-lookup"><span data-stu-id="f6712-177">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="f6712-178">Lightning-Anbieter, die derzeit in Fall Update unterstützt wird, erstellt Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f6712-178">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="f6712-179">Sie können ein Windows 10 IoT Core-Image aus unserem [Downloadseite](https://developer.microsoft.com/windows/iot/Downloads).</span><span class="sxs-lookup"><span data-stu-id="f6712-179">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="f6712-180">Klicken Sie auf "Herunterladen von Insider Preview" auf, um für Ihren Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="f6712-180">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="f6712-181">Treiber für den direkten zugewiesenem Speicher muss aktiviert sein</span><span class="sxs-lookup"><span data-stu-id="f6712-181">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="f6712-182">Die in der Bibliothek Lightning-Anbieter-APIs erfordern den Lightning Direct Memory-Mapped-Treiber auf dem Gerät aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="f6712-182">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="f6712-183">Sowohl Raspberry Pi 2/3-MinnowBoard Max haben Sie den Treiber verfügbar, aber nicht standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="f6712-183">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="f6712-184">Der Treiber kann mit dem Webportal für Windows-Geräte aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="f6712-184">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="f6712-185">Finden Sie in der [Lightning-Installationshandbuch](LightningSetup.md) ausführliche Informationen zum Aktivieren des Lightning-Treibers.</span><span class="sxs-lookup"><span data-stu-id="f6712-185">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![Seite "Geräte"](../media/LightningProviders/dmap4.png)

<span data-ttu-id="f6712-187">Der Treiber kann auch mit dem Befehl DmapUtil aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="f6712-187">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="f6712-188">DmapUtil: Hilfsprogramm, um beim DMAP direct-Memory-Mapper-Treiber zu aktivieren, oder die Nutzung: dmaputil.exe-Status | aktivieren | deaktivierungszustand [-V] Drucken von, ob Dmap derzeit aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f6712-188">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="f6712-189">Übergeben Sie das Flag "- V" detaillierte Informationen zur Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f6712-189">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="f6712-190">Enable Dmap beim nächsten Systemstart zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f6712-190">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="f6712-191">Disable Dmap beim nächsten Systemstart zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="f6712-191">disable       Disable dmap on next boot.</span></span>
