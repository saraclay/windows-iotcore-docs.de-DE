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
# <a name="developing-foreground-applications"></a>Entwickeln von vordergrundanwendungen
Informationen Sie zu den Sprachen, die auf Windows 10 IoT Core als auch für die UWP unterstützt werden und nicht-UWP-app-Typen, die unter IoT Core unterstützt werden.


> [!NOTE]
> Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.

## <a name="application-types"></a>Anwendungstypen
___

### <a name="universal-windows-platform-uwp-apps"></a>Apps der universellen Windows-Plattform (UWP)
IoT Core ist ein UWP-orientierte-Betriebssystem und UWP-apps sind die primären app-Typ.

Universelle Windows-Plattform (UWP) ist eine allgemeine app-Plattform in allen Versionen des Windows 10, einschließlich Windows 10 IoT Core.  UWP wird eine Weiterentwicklung der Windows-Runtime (WinRT). Sie finden weitere Informationen und eine Übersicht über UWP [hier](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

Visual Studio ist das wichtigste Tool für das Schreiben von UWP-apps, IoT Core und im Allgemeinen. Sie finden eine ausführliche Liste der Anforderungen an die die Kompatibilität für Visual Studio [hier](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).


### <a name="traditional-uwp-apps"></a>Herkömmliche UWP-Apps
UWP-apps funktionieren nur unter IoT Core, einfach wie auf anderen Editionen von Windows 10. Eine einfache, leere Xaml-app in Visual Studio wird ordnungsgemäß auf Ihrem IoT Core-Gerät bereitstellen, genau wie auf einem Smartphone oder Windows 10-PCs. Alle standard-UWP-Sprachen und Projektvorlagen sind vollständig unter IoT Core unterstützt.

Es gibt einige Ergänzungen zu der herkömmlichen UWP-app-Modell IoT-Szenarien zu unterstützen, und alle UWP-app, die von ihnen nutzt, benötigen die entsprechende Informationen des Manifests hinzugefügt. Insbesondere muss der "Iot"-Namespace im Manifest dieser standard UWP-Apps hinzugefügt werden. 

In der <Package> Attribut des Manifests müssen Sie die Iot-Xmlns definieren und die IgnorableNamespaces-Liste hinzuzufügen. Der endgültige XML-Code sollte wie folgt aussehen: 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a>Hintergrund-Apps
Zusätzlich zu der herkömmlichen Anwendungsbenutzeroberflächen wurde IoT Core einen neuen UWP-app-Typ namens "Hintergrundanwendungen" hinzugefügt. Diese Anwendungen müssen sich nicht auf eine UI-Komponente, sondern müssen stattdessen eine Klasse, die "IBackgroundTask"-Schnittstelle implementiert. Sie registrieren dann diese Klasse als eine "StartupTask" beim Systemstart ausgeführt. Da sie immer noch UWP-apps sind, werden sie haben Zugriff auf den gleichen Satz von APIs und werden in derselben Sprache unterstützt. Der einzige Unterschied ist, dass kein Einstiegspunkt für Benutzeroberfläche vorhanden ist.

Jede Art von IBackgroundTask Ruft eine eigene Ressourcenrichtlinie ab. Dies ist in der Regel restriktive zur Verbesserung der Akku Leben und -Computer-Ressourcen auf Geräten, in denen sekundäre Komponenten der Vordergrund-UI-apps sind diese Hintergrund-apps. Hintergrund-Apps sind häufig die primäre Funktion des Geräts und und diese StartupTasks eine Ressourcenrichtlinie, spiegelt die Vordergrund-UI-apps auf anderen Geräten, auf IoT-Geräten.

Das folgende Beispiel zeigt den Code zum Erstellen einer C# Hintergrund-App, die eine LED blinkt:

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

Ausführliche Informationen zum Hintergrund-apps finden Sie [hier](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).

### <a name="non-uwp-apps"></a>Nicht-UWP-Apps
IoT Core unterstützt bestimmte herkömmliche Win32-app-Typen wie z. B. Win32-Konsolen-Apps und NT-Dienste. Diese apps werden erstellt, und führen Sie die gleiche Weise wie auf Windows 10 Desktop. Darüber hinaus ist ein IoT Core C++ Konsole-Projektvorlage zu erleichtern, solche apps mithilfe von Visual Studio zu erstellen.

Es gibt zwei wichtigsten Einschränkungen für diese nicht-UWP-Anwendungen:
1. *Keine ältere Win32-Benutzeroberflächenautomatisierungs-Unterstützung:* IoT Core enthält keine APIs, um klassische (HWND) Windows zu erstellen. Legacy-Methoden wie z. B. CreateWindow() und CreateWindowEx() oder andere Methoden, die Windows-Handles (HWNDs) betreffen, sind nicht verfügbar. Anschließend werden Frameworks, die von solchen APIs wie MFC, Windows Forms und WPF, abhängen unter IoT Core nicht unterstützt
2. *C++Nur Apps:* Derzeit nur C++ wird für die Entwicklung von Win32-apps unter IoT Core unterstützt.

## <a name="programming-languages"></a>Programmiersprachen
___

IoT Core unterstützt eine Vielzahl von Programmiersprachen.

### <a name="in-box-languages"></a>In-Box-Sprachen
Herkömmliche UWP-Sprachen, die mit der Unterstützung in Visual Studio standardmäßig geliefert werden. Alle Sprachen In-Box-Unterstützung, Benutzeroberfläche und Hintergrundanwendungen
 
* Sprachen
  * C#
  * C++
  * Javascript
  * Visual Basic

### <a name="arduino-wiring"></a>Arduino-verknüpfen
 Verknüpfen von Arduino erfordert den Download der "Windows IoT Core-Projektvorlagen" von Visual Studio **-Tools > Erweiterungen und Updates** Manager.  Verknüpfen von Arduino unterstützt nur die Hintergrund-Anwendungen. Sie können auch erstellen *Windows-Runtime-Komponenten* mit C#, C++,- oder Visual Basic und verweisen Sie dann die Bibliotheken aus einer beliebigen anderen Sprache.

### <a name="c-and-visual-basic-vb"></a>C#und Visual Basic (VB)
C#VB sowohl als UWP-apps unterstützt werden und haben Zugriff auf den Teil des .net Framework für UWP-Anwendungen verfügbar. UI-apps mit Xaml als auch von Hintergrund-Apps unterstützt. Sie können auch erstellen *Windows-Runtime-Komponenten* , die von anderen unterstützten Sprachen verwendet werden kann.

Beispiele:


* [C#Hauptverkaufsargument monitorlose mit der vollständigen Dokumentation](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground)
* [C#Nur Hauptverkaufsargument monitorlose Code](https://github.com/ms-iot/samples/tree/develop/HelloBlinkyBackground/CS)
* [VB Hauptverkaufsargument monitorlose nur Code](https://github.com/ms-iot/samples/tree/develop/HelloBlinkyBackground/VB)
* [C#Hauptverkaufsargument UI-App](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)


### <a name="javascript"></a>Javascript
Sie können Javascript verwenden, um sowohl UI und Hintergrund-Apps zu erstellen. Die UI-apps funktionieren, die auf alle UWP-Editionen. Die Hintergrund-Apps sind neue IoT Core aber sehr einfach. Der folgende Code zeigt die Ausgabe des einen der *JS-Vorlage für neue Projekte*:

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a>C++
Mit C++ Xaml oder DirectX-UI-apps sowie UWP-Hintergrund-Projekte können erstellen und *nicht-UI* Win32-apps.

Beispiele:

* [Hauptverkaufsargument monitorlose](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [Hauptverkaufsargument Spitzen](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [Konsolen-App](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus)

> [!NOTE]
> Für diejenigen, die beabsichtigen, Schreiben ihre app in C++, müssen Sie überprüfen die UWP C++ Kontrollkästchen beim Herunterladen.

![C++für Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a>Arduino-verknüpfen
Verknüpfen von Arduino-Unterstützung können Sie apps in der Arduino verknüpfen für viele häufig verwendete Komponenten und Peripheriegeräte im IoT-Ökosystem erstellen.

Unsere [Arduino verknüpfen Projektberater](../learn-about-hardware/ArduinoWiringProjectGuide.md) enthält umfassende Anweisungen zum Festlegen, dass diese apps zu erstellen. Die Beispiele, die kopiert und aus dem Link unten können Sie erste Schritte zum Erstellen einer eigenen.  Sie können sogar [Erstellen von WinRT-Komponenten in der Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) , klicken Sie dann in anderen Sprachen verwendet werden kann. 

*Hauptverkaufsargument Beispielcode* die vollständige [Beispielcode und -Dokumentation](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB) stehen auf unserer Beispiele Seite, und Sie finden den vollständigen Code unten:

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
