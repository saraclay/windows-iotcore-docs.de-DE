---
title: Entwickeln von vordergrundanwendungen
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zu den Sprachen und app-Typen, die von IoT Core unterstützt werden.
keywords: Windows Iot, Sprachen, app-Typen, UWP, unterstützt
ms.openlocfilehash: 7d330ff2961ba83d969861bbecd1536b02a4833a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513609"
---
# <a name="developing-foreground-applications"></a><span data-ttu-id="3f99a-104">Entwickeln von vordergrundanwendungen</span><span class="sxs-lookup"><span data-stu-id="3f99a-104">Developing foreground applications</span></span>
<span data-ttu-id="3f99a-105">Informationen Sie zu den Sprachen, die auf Windows 10 IoT Core als auch für die UWP unterstützt werden und nicht-UWP-app-Typen, die unter IoT Core unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="3f99a-105">Learn about the languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported on IoT Core.</span></span>


> [!NOTE]
> <span data-ttu-id="3f99a-106">Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="3f99a-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="application-types"></a><span data-ttu-id="3f99a-107">Anwendungstypen</span><span class="sxs-lookup"><span data-stu-id="3f99a-107">Application Types</span></span>
___

### <a name="universal-windows-platform-uwp-apps"></a><span data-ttu-id="3f99a-108">Apps der universellen Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="3f99a-108">Universal Windows Platform (UWP) Apps</span></span>
<span data-ttu-id="3f99a-109">IoT Core ist ein UWP-orientierte-Betriebssystem und UWP-apps sind die primären app-Typ.</span><span class="sxs-lookup"><span data-stu-id="3f99a-109">IoT Core is a UWP centric OS and UWP apps are its primary app type.</span></span>

<span data-ttu-id="3f99a-110">Universelle Windows-Plattform (UWP) ist eine allgemeine app-Plattform in allen Versionen des Windows 10, einschließlich Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="3f99a-110">Universal Windows Platform (UWP) is a common app platform across all version of Windows 10, including Windows 10 IoT Core.</span></span>  <span data-ttu-id="3f99a-111">UWP wird eine Weiterentwicklung der Windows-Runtime (WinRT).</span><span class="sxs-lookup"><span data-stu-id="3f99a-111">UWP is an evolution of Windows Runtime (WinRT).</span></span> <span data-ttu-id="3f99a-112">Sie finden weitere Informationen und eine Übersicht über UWP [hier](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span><span class="sxs-lookup"><span data-stu-id="3f99a-112">You can find more information and an overview to UWP [here](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

<span data-ttu-id="3f99a-113">Visual Studio ist das wichtigste Tool für das Schreiben von UWP-apps, IoT Core und im Allgemeinen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-113">Visual Studio is the primary tool for writing UWP apps for IoT Core and in general.</span></span> <span data-ttu-id="3f99a-114">Sie finden eine ausführliche Liste der Anforderungen an die die Kompatibilität für Visual Studio [hier](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span><span class="sxs-lookup"><span data-stu-id="3f99a-114">You can find a detailed listing of the compatibility requirements for Visual Studio [here](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>


### <a name="traditional-uwp-apps"></a><span data-ttu-id="3f99a-115">Herkömmliche UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="3f99a-115">Traditional UWP Apps</span></span>
<span data-ttu-id="3f99a-116">UWP-apps funktionieren nur unter IoT Core, einfach wie auf anderen Editionen von Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3f99a-116">UWP apps just work on IoT Core, just as they do on other Windows 10 editions.</span></span> <span data-ttu-id="3f99a-117">Eine einfache, leere Xaml-app in Visual Studio wird ordnungsgemäß auf Ihrem IoT Core-Gerät bereitstellen, genau wie auf einem Smartphone oder Windows 10-PCs.</span><span class="sxs-lookup"><span data-stu-id="3f99a-117">A simple, blank Xaml app in Visual Studio will properly deploy to your IoT Core device just as it would on a phone or Windows 10 PC.</span></span> <span data-ttu-id="3f99a-118">Alle standard-UWP-Sprachen und Projektvorlagen sind vollständig unter IoT Core unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-118">All of the standard UWP languages and project templates are fully supported on IoT Core.</span></span>

<span data-ttu-id="3f99a-119">Es gibt einige Ergänzungen zu der herkömmlichen UWP-app-Modell IoT-Szenarien zu unterstützen, und alle UWP-app, die von ihnen nutzt, benötigen die entsprechende Informationen des Manifests hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-119">There are a few additions to the traditional UWP app-model to support IoT scenarios and any UWP app that takes advantage of them will need the corresponding information added to their manifest.</span></span> <span data-ttu-id="3f99a-120">Insbesondere muss der "Iot"-Namespace im Manifest dieser standard UWP-Apps hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3f99a-120">In particular the "iot" namespace needs to be added to the manifest of these standard UWP apps.</span></span> 

<span data-ttu-id="3f99a-121">In der <Package> Attribut des Manifests müssen Sie die Iot-Xmlns definieren und die IgnorableNamespaces-Liste hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-121">Inside the <Package> attribute of the manifest, you need to define the iot xmlns and add it to the IgnorableNamespaces list.</span></span> <span data-ttu-id="3f99a-122">Der endgültige XML-Code sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="3f99a-122">The final xml should look like this:</span></span> 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a><span data-ttu-id="3f99a-123">Hintergrund-Apps</span><span class="sxs-lookup"><span data-stu-id="3f99a-123">Background Apps</span></span>
<span data-ttu-id="3f99a-124">Zusätzlich zu der herkömmlichen Anwendungsbenutzeroberflächen wurde IoT Core einen neuen UWP-app-Typ namens "Hintergrundanwendungen" hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-124">In addition to the traditional UI apps, IoT Core has added a new UWP app type called "Background Applications".</span></span> <span data-ttu-id="3f99a-125">Diese Anwendungen müssen sich nicht auf eine UI-Komponente, sondern müssen stattdessen eine Klasse, die "IBackgroundTask"-Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="3f99a-125">These applications do not have a UI component, but instead have a class that implements the "IBackgroundTask" interface.</span></span> <span data-ttu-id="3f99a-126">Sie registrieren dann diese Klasse als eine "StartupTask" beim Systemstart ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-126">They then register that class as a "StartupTask" to run at system boot.</span></span> <span data-ttu-id="3f99a-127">Da sie immer noch UWP-apps sind, werden sie haben Zugriff auf den gleichen Satz von APIs und werden in derselben Sprache unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-127">Since they are still UWP apps, they have access to the same set of APIs and are supported from the same language.</span></span> <span data-ttu-id="3f99a-128">Der einzige Unterschied ist, dass kein Einstiegspunkt für Benutzeroberfläche vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3f99a-128">The only difference is that there is no UI entry point.</span></span>

<span data-ttu-id="3f99a-129">Jede Art von IBackgroundTask Ruft eine eigene Ressourcenrichtlinie ab.</span><span class="sxs-lookup"><span data-stu-id="3f99a-129">Each type of IBackgroundTask gets its own resource policy.</span></span> <span data-ttu-id="3f99a-130">Dies ist in der Regel restriktive zur Verbesserung der Akku Leben und -Computer-Ressourcen auf Geräten, in denen sekundäre Komponenten der Vordergrund-UI-apps sind diese Hintergrund-apps.</span><span class="sxs-lookup"><span data-stu-id="3f99a-130">This is usually restrictive to improve battery life and machine resources on devices where these background apps are secondary components of foreground UI apps.</span></span> <span data-ttu-id="3f99a-131">Hintergrund-Apps sind häufig die primäre Funktion des Geräts und und diese StartupTasks eine Ressourcenrichtlinie, spiegelt die Vordergrund-UI-apps auf anderen Geräten, auf IoT-Geräten.</span><span class="sxs-lookup"><span data-stu-id="3f99a-131">On IoT devices, Background Apps are often the primary function of the device and so these StartupTasks get a resource policy that mirrors foreground UI apps on other devices.</span></span>

<span data-ttu-id="3f99a-132">Das folgende Beispiel zeigt den Code zum Erstellen einer C# Hintergrund-App, die eine LED blinkt:</span><span class="sxs-lookup"><span data-stu-id="3f99a-132">The following sample shows the code necessary to build a C# Background App that blinks an LED:</span></span>

```C#
namespace BlinkyHeadlessCS
{
    public sealed class StartupTask : IBackgroundTask
    {
        BackgroundTaskDeferral deferral;
        private GpioPinValue value = GpioPinValue.High;
        private const int LED_PIN = 5;
        private GpioPin pin;
        private ThreadPoolTimer timer;

        public void Run(IBackgroundTaskInstance taskInstance)        {
            deferral = taskInstance.GetDeferral();
            InitGPIO();
            timer = ThreadPoolTimer.CreatePeriodicTimer(Timer_Tick, TimeSpan.FromMilliseconds(500));

        }
        private void InitGPIO()
        {
            pin = GpioController.GetDefault().OpenPin(LED_PIN);
            pin.Write(GpioPinValue.High);
            pin.SetDriveMode(GpioPinDriveMode.Output);
        }

        private void Timer_Tick(ThreadPoolTimer timer)
        {
            value = (value == GpioPinValue.High) ? GpioPinValue.Low : GpioPinValue.High;
            pin.Write(value);
        }
    }
}
```

<span data-ttu-id="3f99a-133">Ausführliche Informationen zum Hintergrund-apps finden Sie [hier](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span><span class="sxs-lookup"><span data-stu-id="3f99a-133">You can find in-depth information on Background apps [here](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

### <a name="non-uwp-apps"></a><span data-ttu-id="3f99a-134">Nicht-UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="3f99a-134">Non-UWP Apps</span></span>
<span data-ttu-id="3f99a-135">IoT Core unterstützt bestimmte herkömmliche Win32-app-Typen wie z. B. Win32-Konsolen-Apps und NT-Dienste.</span><span class="sxs-lookup"><span data-stu-id="3f99a-135">IoT Core supports certain traditional Win32 app types such as Win32 Console Apps and NT Services.</span></span> <span data-ttu-id="3f99a-136">Diese apps werden erstellt, und führen Sie die gleiche Weise wie auf Windows 10 Desktop.</span><span class="sxs-lookup"><span data-stu-id="3f99a-136">These apps are built and run the same way as on Windows 10 Desktop.</span></span> <span data-ttu-id="3f99a-137">Darüber hinaus ist ein IoT Core C++ Konsole-Projektvorlage zu erleichtern, solche apps mithilfe von Visual Studio zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-137">Additionally, there is an IoT Core C++ Console project template to make it easy to build such apps using Visual Studio.</span></span>

<span data-ttu-id="3f99a-138">Es gibt zwei wichtigsten Einschränkungen für diese nicht-UWP-Anwendungen:</span><span class="sxs-lookup"><span data-stu-id="3f99a-138">There are two main limitations on these non-UWP applications:</span></span>
1. <span data-ttu-id="3f99a-139">*Keine ältere Win32-Benutzeroberflächenautomatisierungs-Unterstützung:* IoT Core enthält keine APIs, um klassische (HWND) Windows zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-139">*No legacy Win32 UI support:* IoT Core does not contain APIs to create classic (HWND) Windows.</span></span> <span data-ttu-id="3f99a-140">Legacy-Methoden wie z. B. CreateWindow() und CreateWindowEx() oder andere Methoden, die Windows-Handles (HWNDs) betreffen, sind nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3f99a-140">Legacy methods such as CreateWindow() and CreateWindowEx() or any other methods that deal with Windows handles (HWNDs) are not available.</span></span> <span data-ttu-id="3f99a-141">Anschließend werden Frameworks, die von solchen APIs wie MFC, Windows Forms und WPF, abhängen unter IoT Core nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="3f99a-141">Subsequently, frameworks that depend on such APIs including MFC, Windows Forms and WPF, are not supported on IoT Core</span></span>
2. <span data-ttu-id="3f99a-142">*C++Nur Apps:* Derzeit nur C++ wird für die Entwicklung von Win32-apps unter IoT Core unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-142">*C++ Apps Only:* Currently, only C++ is supported for developing Win32 apps on IoT Core.</span></span>

## <a name="programming-languages"></a><span data-ttu-id="3f99a-143">Programmiersprachen</span><span class="sxs-lookup"><span data-stu-id="3f99a-143">Programming Languages</span></span>
___

<span data-ttu-id="3f99a-144">IoT Core unterstützt eine Vielzahl von Programmiersprachen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-144">IoT Core supports a wide range of programming languages.</span></span>

### <a name="in-box-languages"></a><span data-ttu-id="3f99a-145">In-Box-Sprachen</span><span class="sxs-lookup"><span data-stu-id="3f99a-145">In-Box languages</span></span>
<span data-ttu-id="3f99a-146">Herkömmliche UWP-Sprachen, die mit der Unterstützung in Visual Studio standardmäßig geliefert werden.</span><span class="sxs-lookup"><span data-stu-id="3f99a-146">Traditional UWP languages ship with support in Visual Studio by default.</span></span> <span data-ttu-id="3f99a-147">Alle Sprachen In-Box-Unterstützung, Benutzeroberfläche und Hintergrundanwendungen</span><span class="sxs-lookup"><span data-stu-id="3f99a-147">All of the In-Box languages support both UI and Background Applications</span></span>
 
* <span data-ttu-id="3f99a-148">Sprachen</span><span class="sxs-lookup"><span data-stu-id="3f99a-148">Languages</span></span>
  * <span data-ttu-id="3f99a-149">C#</span><span class="sxs-lookup"><span data-stu-id="3f99a-149">C#</span></span>
  * <span data-ttu-id="3f99a-150">C++</span><span class="sxs-lookup"><span data-stu-id="3f99a-150">C++</span></span>
  * <span data-ttu-id="3f99a-151">Javascript</span><span class="sxs-lookup"><span data-stu-id="3f99a-151">Javascript</span></span>
  * <span data-ttu-id="3f99a-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f99a-152">Visual Basic</span></span>

### <a name="arduino-wiring"></a><span data-ttu-id="3f99a-153">Arduino-verknüpfen</span><span class="sxs-lookup"><span data-stu-id="3f99a-153">Arduino Wiring</span></span>
 <span data-ttu-id="3f99a-154">Verknüpfen von Arduino erfordert den Download der "Windows IoT Core-Projektvorlagen" von Visual Studio **-Tools > Erweiterungen und Updates** Manager.</span><span class="sxs-lookup"><span data-stu-id="3f99a-154">Arduino Wiring requires the download of the "Windows IoT Core Project Templates" from the Visual Studio **Tools->Extensions and Updates** manager.</span></span>  <span data-ttu-id="3f99a-155">Verknüpfen von Arduino unterstützt nur die Hintergrund-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-155">Arduino Wiring supports only Background Applications.</span></span> <span data-ttu-id="3f99a-156">Sie können auch erstellen *Windows-Runtime-Komponenten* mit C#, C++,- oder Visual Basic und verweisen Sie dann die Bibliotheken aus einer beliebigen anderen Sprache.</span><span class="sxs-lookup"><span data-stu-id="3f99a-156">You can also build *Windows Runtime Components* using C#, C++, or Visual Basic and then reference those libraries from any other language.</span></span>

### <a name="c-and-visual-basic-vb"></a><span data-ttu-id="3f99a-157">C#und Visual Basic (VB)</span><span class="sxs-lookup"><span data-stu-id="3f99a-157">C# and Visual Basic (VB)</span></span>
<span data-ttu-id="3f99a-158">C#VB sowohl als UWP-apps unterstützt werden und haben Zugriff auf den Teil des .net Framework für UWP-Anwendungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3f99a-158">C# and VB are both supported as UWP apps and have access to the portion of the .Net Framework available to UWP applications.</span></span> <span data-ttu-id="3f99a-159">UI-apps mit Xaml als auch von Hintergrund-Apps unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3f99a-159">They support UI apps built with Xaml as well as Background Apps.</span></span> <span data-ttu-id="3f99a-160">Sie können auch erstellen *Windows-Runtime-Komponenten* , die von anderen unterstützten Sprachen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3f99a-160">You can also build *Windows Runtime Components* that can be used from other supported languages.</span></span>

<span data-ttu-id="3f99a-161">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="3f99a-161">Samples:</span></span>


* [<span data-ttu-id="3f99a-162">C#Hauptverkaufsargument monitorlose mit der vollständigen Dokumentation</span><span class="sxs-lookup"><span data-stu-id="3f99a-162">C# Blinky Headless with Full Documentation</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground)
* [<span data-ttu-id="3f99a-163">C#Nur Hauptverkaufsargument monitorlose Code</span><span class="sxs-lookup"><span data-stu-id="3f99a-163">C# Blinky Headless Code Only</span></span>](https://github.com/ms-iot/samples/tree/develop/HelloBlinkyBackground/CS)
* [<span data-ttu-id="3f99a-164">VB Hauptverkaufsargument monitorlose nur Code</span><span class="sxs-lookup"><span data-stu-id="3f99a-164">VB Blinky Headless Code Only</span></span>](https://github.com/ms-iot/samples/tree/develop/HelloBlinkyBackground/VB)
* [<span data-ttu-id="3f99a-165">C#Hauptverkaufsargument UI-App</span><span class="sxs-lookup"><span data-stu-id="3f99a-165">C# Blinky UI App</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)


### <a name="javascript"></a><span data-ttu-id="3f99a-166">Javascript</span><span class="sxs-lookup"><span data-stu-id="3f99a-166">Javascript</span></span>
<span data-ttu-id="3f99a-167">Sie können Javascript verwenden, um sowohl UI und Hintergrund-Apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-167">You can use Javascript to build both UI and Background Apps.</span></span> <span data-ttu-id="3f99a-168">Die UI-apps funktionieren, die auf alle UWP-Editionen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-168">The UI apps work the same way they do on all UWP editions.</span></span> <span data-ttu-id="3f99a-169">Die Hintergrund-Apps sind neue IoT Core aber sehr einfach.</span><span class="sxs-lookup"><span data-stu-id="3f99a-169">The Background Apps are new for IoT Core but are very simple.</span></span> <span data-ttu-id="3f99a-170">Der folgende Code zeigt die Ausgabe des einen der *JS-Vorlage für neue Projekte*:</span><span class="sxs-lookup"><span data-stu-id="3f99a-170">The following sample code shows the output of a the *JS New Project Template*:</span></span>

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a><span data-ttu-id="3f99a-171">C++</span><span class="sxs-lookup"><span data-stu-id="3f99a-171">C++</span></span>
<span data-ttu-id="3f99a-172">Mit C++ Xaml oder DirectX-UI-apps sowie UWP-Hintergrund-Projekte können erstellen und *nicht-UI* Win32-apps.</span><span class="sxs-lookup"><span data-stu-id="3f99a-172">With C++ you can build Xaml or DirectX UI apps, as well as UWP Background projects and *non-UI* Win32 apps.</span></span>

<span data-ttu-id="3f99a-173">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="3f99a-173">Samples:</span></span>

* [<span data-ttu-id="3f99a-174">Hauptverkaufsargument monitorlose</span><span class="sxs-lookup"><span data-stu-id="3f99a-174">Blinky Headless</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [<span data-ttu-id="3f99a-175">Hauptverkaufsargument Spitzen</span><span class="sxs-lookup"><span data-stu-id="3f99a-175">Blinky Headed</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [<span data-ttu-id="3f99a-176">Konsolen-App</span><span class="sxs-lookup"><span data-stu-id="3f99a-176">Console App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus)

> [!NOTE]
> <span data-ttu-id="3f99a-177">Für diejenigen, die beabsichtigen, Schreiben ihre app in C++, müssen Sie überprüfen die UWP C++ Kontrollkästchen beim Herunterladen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-177">For those who are planning to write their app in C++, you'll need to check the UWP C++ checkbox upon downloading.</span></span>

![C++für Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a><span data-ttu-id="3f99a-179">Arduino-verknüpfen</span><span class="sxs-lookup"><span data-stu-id="3f99a-179">Arduino Wiring</span></span>
<span data-ttu-id="3f99a-180">Verknüpfen von Arduino-Unterstützung können Sie apps in der Arduino verknüpfen für viele häufig verwendete Komponenten und Peripheriegeräte im IoT-Ökosystem erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-180">With Arduino Wiring support you can build apps in Arduino Wiring for many popular components and peripherals in the IoT ecosystem.</span></span>

<span data-ttu-id="3f99a-181">Unsere [Arduino verknüpfen Projektberater](../learn-about-hardware/ArduinoWiringProjectGuide.md) enthält umfassende Anweisungen zum Festlegen, dass diese apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-181">Our [Arduino Wiring Project Guide](../learn-about-hardware/ArduinoWiringProjectGuide.md) provides full instructions on how to get set up to build these apps.</span></span> <span data-ttu-id="3f99a-182">Die Beispiele, die kopiert und aus dem Link unten können Sie erste Schritte zum Erstellen einer eigenen.</span><span class="sxs-lookup"><span data-stu-id="3f99a-182">The samples copied and linked below will help you get started building your own.</span></span>  <span data-ttu-id="3f99a-183">Sie können sogar [Erstellen von WinRT-Komponenten in der Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) , klicken Sie dann in anderen Sprachen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3f99a-183">You can even [build WinRT components in Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) that can then be used from other languages.</span></span> 

<span data-ttu-id="3f99a-184">*Hauptverkaufsargument Beispielcode* die vollständige [Beispielcode und -Dokumentation](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB) stehen auf unserer Beispiele Seite, und Sie finden den vollständigen Code unten:</span><span class="sxs-lookup"><span data-stu-id="3f99a-184">*Blinky Sample Code* The full [sample code and docs](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB) are available on our samples page and you can find the full code below:</span></span>

```C++
void setup()
{
    // put your setup code here, to run once:

    pinMode(GPIO5, OUTPUT);
}

void loop()
{
    // put your main code here, to run repeatedly:

    digitalWrite(GPIO5, LOW);
    delay(500);
    digitalWrite(GPIO5, HIGH);
    delay(500);
}
```
