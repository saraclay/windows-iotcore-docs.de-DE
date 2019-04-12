---
title: Verknüpfen der Leitfaden zur Portierung Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zu Änderungen und häufige Probleme, die wieder bei der Bereitstellung von Projekten Arduino verknüpfen.
keywords: Portieren von Windows Iot, Arduino, verknüpfen, Visual Studio
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512418"
---
# <a name="arduino-wiring-porting-guide"></a><span data-ttu-id="8c693-104">Verknüpfen der Leitfaden zur Portierung Arduino</span><span class="sxs-lookup"><span data-stu-id="8c693-104">Arduino Wiring Porting Guide</span></span>

<span data-ttu-id="8c693-105">Verknüpfen von Arduino Skizzen und Bibliotheken können auf Raspberry Pi 2- oder Raspberry Pi 3 mit Minnowboard Max in einem Projekt verknüpfen Arduino in Visual Studio kopiert und eingefügt und ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8c693-105">Arduino Wiring sketches and libraries can be copy/pasted into an Arduino Wiring project inside Visual Studio and run on Raspberry Pi 2, Raspberry Pi 3 or Minnowboard Max.</span></span> <span data-ttu-id="8c693-106">Es gibt gelegentlich geringfügige Änderungen, die auf diese Dateien vorgenommen werden, damit sie besser kompatibel mit der Windows-Umgebung können müssen, oder das Board, mit denen, dem Sie arbeiten werden.</span><span class="sxs-lookup"><span data-stu-id="8c693-106">Sometimes there are slight modifications that need to be made to these files in order to make them more compatible with the Windows environment, or the board you are working with.</span></span> <span data-ttu-id="8c693-107">Dieses Handbuch befasst sich diese Änderungen sowie häufige Probleme, denen Sie stoßen eventuell bei der Bereitstellung von Projekten Arduino zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="8c693-107">This guide will cover those modifications as well as common issues that you may run into when deploying Arduino Wiring projects.</span></span>

## <a name="porting"></a><span data-ttu-id="8c693-108">Portieren</span><span class="sxs-lookup"><span data-stu-id="8c693-108">Porting</span></span>

### <a name="updating-pins"></a><span data-ttu-id="8c693-109">Aktualisieren die Pins</span><span class="sxs-lookup"><span data-stu-id="8c693-109">Updating Pins</span></span>

<span data-ttu-id="8c693-110">Es versteht wechseln kann, aber viele Skizzen und Bibliotheken (insbesondere über diejenigen für Arduino-Shields) enthält Verweise auf bestimmte Anschlussstifte für Arduino-Geräte.</span><span class="sxs-lookup"><span data-stu-id="8c693-110">It might go without saying, but many sketches and libraries (especially those for arduino shields) may contain references to specific connector pins for Arduino devices.</span></span> <span data-ttu-id="8c693-111">Sie sollten zum Anpassen Ihrer Skizzen, um die entsprechenden Connector Pins zu verwenden, für das Gerät, dem Sie bearbeiten und die Konfiguration, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="8c693-111">You'll want to customize your sketches to use the appropriate connector pins for the device you are working on and the configuration you are using.</span></span>

<span data-ttu-id="8c693-112">Verknüpfen von Arduino erfordert eine Pin-Nummer des physischen Connector letztlich für alle Funktionen, die auf "Pins" verweisen.</span><span class="sxs-lookup"><span data-stu-id="8c693-112">Arduino Wiring ultimately requires a physical connector pin number for any functions that refer to 'pins'.</span></span> <span data-ttu-id="8c693-113">Sie können diese Werte direkt verwenden, aber haben wir auch einige vordefinierte Pin-Namen die Anschlussstifte auf bestimmte Boards entsprechen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8c693-113">You can use these numbers directly, but we've also provided some pre-defined pin names which correspond to connector pins on specific boards.</span></span>

<span data-ttu-id="8c693-114">Die physischen Connector-Pin-29 auf einem Raspberry Pi 2 und 3 ist z. B. auch bekannt als `GPIO5`.</span><span class="sxs-lookup"><span data-stu-id="8c693-114">For example, the physical connector pin 29 on a Raspberry Pi 2 and 3 is also known as `GPIO5`.</span></span> <span data-ttu-id="8c693-115">Sie können GPIO-Pins 5 auf einem Raspberry Pi 2 und 3 in einen Zustand hoch festlegen, mithilfe der folgenden Befehle:</span><span class="sxs-lookup"><span data-stu-id="8c693-115">You may set GPIO pin 5 to a HIGH state on a Raspberry Pi 2 and 3 by using either of the following commands:</span></span>
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

<span data-ttu-id="8c693-116">oder</span><span class="sxs-lookup"><span data-stu-id="8c693-116">or</span></span>

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

<span data-ttu-id="8c693-117">Die vordefinierte Pin-Namen finden Sie im [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) und integriert in jedem Projekt Arduino verknüpfen, aber da es verschiedene physische Anschlussstifte abhängig von der Hardware-Einrichtung stehen für Sie erstellen, haben wir ebenfalls enthalten, eine Tabelle zum Beschreiben der Pin-Namen für jedes Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8c693-117">The pre-defined pin names can be found in [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) and included in every Arduino Wiring project, but since there will be different physical connector pins available depending on the hardware setup you are building for, we've also included a table here to describe which pin names are available for each device.</span></span>

#### <a name="raspberry-pi-2-and-3"></a><span data-ttu-id="8c693-118">Raspberry Pi 2 und 3</span><span class="sxs-lookup"><span data-stu-id="8c693-118">Raspberry Pi 2 and 3</span></span>

![Pinouts-Diagramm](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="8c693-120">Definieren Sie die PIN</span><span class="sxs-lookup"><span data-stu-id="8c693-120">Pin Define</span></span> | <span data-ttu-id="8c693-121">Zugehörige Pin-Nummer</span><span class="sxs-lookup"><span data-stu-id="8c693-121">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="8c693-122">LED_BUILTIN</span><span class="sxs-lookup"><span data-stu-id="8c693-122">LED_BUILTIN</span></span> | *<span data-ttu-id="8c693-123">Integrieren der LED</span><span class="sxs-lookup"><span data-stu-id="8c693-123">onboard LED</span></span>* |
> | <span data-ttu-id="8c693-124">GPIO \* _, in denen \* bezieht sich auf [0, 27]_</span><span class="sxs-lookup"><span data-stu-id="8c693-124">GPIO\* _where \* refers to [0, 27]_</span></span> | *<span data-ttu-id="8c693-125">Pinouts Diagramm finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="8c693-125">refer to pinout diagram</span></span>* |
> | <span data-ttu-id="8c693-126">GCLK</span><span class="sxs-lookup"><span data-stu-id="8c693-126">GCLK</span></span> | <span data-ttu-id="8c693-127">7</span><span class="sxs-lookup"><span data-stu-id="8c693-127">7</span></span> |
> | <span data-ttu-id="8c693-128">GEN \* _, in denen \* bezieht sich auf [0, 5]_</span><span class="sxs-lookup"><span data-stu-id="8c693-128">GEN\* _where \* refers to [0, 5]_</span></span> | <span data-ttu-id="8c693-129">\* finden Sie unter Pinouts-Diagramm</span><span class="sxs-lookup"><span data-stu-id="8c693-129">\*refer to pinout diagram</span></span> |
> | <span data-ttu-id="8c693-130">SCL1</span><span class="sxs-lookup"><span data-stu-id="8c693-130">SCL1</span></span> | <span data-ttu-id="8c693-131">5</span><span class="sxs-lookup"><span data-stu-id="8c693-131">5</span></span> |
> | <span data-ttu-id="8c693-132">SDA1</span><span class="sxs-lookup"><span data-stu-id="8c693-132">SDA1</span></span> | <span data-ttu-id="8c693-133">3</span><span class="sxs-lookup"><span data-stu-id="8c693-133">3</span></span> |
> | <span data-ttu-id="8c693-134">CS0 (oder CE0 oder SS)</span><span class="sxs-lookup"><span data-stu-id="8c693-134">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="8c693-135">24</span><span class="sxs-lookup"><span data-stu-id="8c693-135">24</span></span> |
> | <span data-ttu-id="8c693-136">CS1 (oder CE1)</span><span class="sxs-lookup"><span data-stu-id="8c693-136">CS1 (or CE1)</span></span> | <span data-ttu-id="8c693-137">26</span><span class="sxs-lookup"><span data-stu-id="8c693-137">26</span></span> |
> | <span data-ttu-id="8c693-138">SCLK (oder SCK)</span><span class="sxs-lookup"><span data-stu-id="8c693-138">SCLK (or SCK)</span></span> | <span data-ttu-id="8c693-139">23</span><span class="sxs-lookup"><span data-stu-id="8c693-139">23</span></span> |
> | <span data-ttu-id="8c693-140">MISO</span><span class="sxs-lookup"><span data-stu-id="8c693-140">MISO</span></span> | <span data-ttu-id="8c693-141">21</span><span class="sxs-lookup"><span data-stu-id="8c693-141">21</span></span> |
> | <span data-ttu-id="8c693-142">MOSI</span><span class="sxs-lookup"><span data-stu-id="8c693-142">MOSI</span></span> | <span data-ttu-id="8c693-143">19</span><span class="sxs-lookup"><span data-stu-id="8c693-143">19</span></span> |
> | <span data-ttu-id="8c693-144">RXD</span><span class="sxs-lookup"><span data-stu-id="8c693-144">RXD</span></span> | <span data-ttu-id="8c693-145">10</span><span class="sxs-lookup"><span data-stu-id="8c693-145">10</span></span> |
> | <span data-ttu-id="8c693-146">TXD</span><span class="sxs-lookup"><span data-stu-id="8c693-146">TXD</span></span> | <span data-ttu-id="8c693-147">8</span><span class="sxs-lookup"><span data-stu-id="8c693-147">8</span></span> |

#### <a name="minnowboard-max"></a><span data-ttu-id="8c693-148">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="8c693-148">Minnowboard Max</span></span>

![Pinouts-Diagramm](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="8c693-150">Definieren Sie die PIN</span><span class="sxs-lookup"><span data-stu-id="8c693-150">Pin Define</span></span> | <span data-ttu-id="8c693-151">Zugehörige Pin-Nummer</span><span class="sxs-lookup"><span data-stu-id="8c693-151">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="8c693-152">GPIO \* _, in denen \* bezieht sich auf [0, 9]_</span><span class="sxs-lookup"><span data-stu-id="8c693-152">GPIO\* _where \* refers to [0, 9]_</span></span>  | *<span data-ttu-id="8c693-153">Pinouts Diagramm finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="8c693-153">refer to pinout diagram</span></span>* |
> | <span data-ttu-id="8c693-154">SCL</span><span class="sxs-lookup"><span data-stu-id="8c693-154">SCL</span></span> | <span data-ttu-id="8c693-155">13</span><span class="sxs-lookup"><span data-stu-id="8c693-155">13</span></span> |
> | <span data-ttu-id="8c693-156">SDA</span><span class="sxs-lookup"><span data-stu-id="8c693-156">SDA</span></span> | <span data-ttu-id="8c693-157">15</span><span class="sxs-lookup"><span data-stu-id="8c693-157">15</span></span> |
> | <span data-ttu-id="8c693-158">CS0 (oder CE0 oder SS)</span><span class="sxs-lookup"><span data-stu-id="8c693-158">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="8c693-159">5</span><span class="sxs-lookup"><span data-stu-id="8c693-159">5</span></span> |
> | <span data-ttu-id="8c693-160">SCLK (oder SCK)</span><span class="sxs-lookup"><span data-stu-id="8c693-160">SCLK  (or SCK)</span></span>| <span data-ttu-id="8c693-161">11</span><span class="sxs-lookup"><span data-stu-id="8c693-161">11</span></span> |
> | <span data-ttu-id="8c693-162">MISO</span><span class="sxs-lookup"><span data-stu-id="8c693-162">MISO</span></span> |<span data-ttu-id="8c693-163">7</span><span class="sxs-lookup"><span data-stu-id="8c693-163">7</span></span> |
> | <span data-ttu-id="8c693-164">MOSI</span><span class="sxs-lookup"><span data-stu-id="8c693-164">MOSI</span></span> | <span data-ttu-id="8c693-165">9</span><span class="sxs-lookup"><span data-stu-id="8c693-165">9</span></span> |
> | <span data-ttu-id="8c693-166">CTS1</span><span class="sxs-lookup"><span data-stu-id="8c693-166">CTS1</span></span> | <span data-ttu-id="8c693-167">10</span><span class="sxs-lookup"><span data-stu-id="8c693-167">10</span></span> |
> | <span data-ttu-id="8c693-168">RTS1</span><span class="sxs-lookup"><span data-stu-id="8c693-168">RTS1</span></span> | <span data-ttu-id="8c693-169">12</span><span class="sxs-lookup"><span data-stu-id="8c693-169">12</span></span> |
> | <span data-ttu-id="8c693-170">RX1</span><span class="sxs-lookup"><span data-stu-id="8c693-170">RX1</span></span> | <span data-ttu-id="8c693-171">8</span><span class="sxs-lookup"><span data-stu-id="8c693-171">8</span></span> |
> | <span data-ttu-id="8c693-172">TX1</span><span class="sxs-lookup"><span data-stu-id="8c693-172">TX1</span></span> | <span data-ttu-id="8c693-173">6</span><span class="sxs-lookup"><span data-stu-id="8c693-173">6</span></span> |
> | <span data-ttu-id="8c693-174">RX2</span><span class="sxs-lookup"><span data-stu-id="8c693-174">RX2</span></span> | <span data-ttu-id="8c693-175">19</span><span class="sxs-lookup"><span data-stu-id="8c693-175">19</span></span> |
> | <span data-ttu-id="8c693-176">TX2</span><span class="sxs-lookup"><span data-stu-id="8c693-176">TX2</span></span> | <span data-ttu-id="8c693-177">17</span><span class="sxs-lookup"><span data-stu-id="8c693-177">17</span></span> |


## <a name="common-problems"></a><span data-ttu-id="8c693-178">Häufige Probleme</span><span class="sxs-lookup"><span data-stu-id="8c693-178">Common Problems</span></span>

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a><span data-ttu-id="8c693-179">Wurde nicht gefunden "Arduino verknüpfen die Anwendung" Visual C++ Projektvorlage in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8c693-179">Can't find "Arduino Wiring Application" Visual C++ project template in Visual Studio</span></span>

<span data-ttu-id="8c693-180">**Ursache**: Die Projektvorlagen für Windows-IoT-Erweiterung für Visual Studio ist nicht installiert.</span><span class="sxs-lookup"><span data-stu-id="8c693-180">**Cause**: The Windows IoT Project Templates extension for Visual Studio is not installed.</span></span>

<span data-ttu-id="8c693-181">**Lösung**: Sie müssen die Visual Studio-Erweiterung für Windows IoT-Projektvorlagen installieren, bevor Sie Verknüpfen von Arduino-Projekte in Visual Studio erstellen können.</span><span class="sxs-lookup"><span data-stu-id="8c693-181">**Solution**: You must install the Visual Studio Extension for Windows IoT Project Templates before you can create Arduino Wiring projects in Visual Studio.</span></span> <span data-ttu-id="8c693-182">Wechseln Sie zu [Windows IoT Core-Projektvorlagen-Erweiterungsseite](https://go.microsoft.com/fwlink/?linkid=847472) auf die Erweiterung von Visual Studio Gallery herunterladen!</span><span class="sxs-lookup"><span data-stu-id="8c693-182">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>

### <a name="error-identifier-not-found-when-calling-a-function"></a><span data-ttu-id="8c693-183">Fehler: "Bezeichner wurde nicht gefunden" beim Aufrufen einer Funktion</span><span class="sxs-lookup"><span data-stu-id="8c693-183">ERROR: "identifier not found" when calling a function</span></span>

<span data-ttu-id="8c693-184">**Ursache**: Dieser Fehler tritt während des Prozesses der Linker auf, wenn eine Funktion aufgerufen wird, die noch nicht im Dokument deklariert wurde.</span><span class="sxs-lookup"><span data-stu-id="8c693-184">**Cause**: This error occurs during the linker process when a function is invoked that has not yet been declared in the document.</span></span>

<span data-ttu-id="8c693-185">**Lösung**: In C++, alle Funktionen müssen deklariert werden, bevor sie aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8c693-185">**Solution**: In C++, all functions must be declared before they are invoked.</span></span> <span data-ttu-id="8c693-186">Wenn Sie eine neue Funktion in der Sketch-Datei definiert haben, muss entweder der Deklaration oder die gesamte Implementierung der Funktion über alle Versuche für die aufzurufende (in der Regel am oberen Rand des Dokuments) sein.</span><span class="sxs-lookup"><span data-stu-id="8c693-186">If you have defined a new function in your sketch file, either the declaration or the entire implementation of the function must be above any attempts to invoke it (typically at the top of the document).</span></span>

<span data-ttu-id="8c693-187">**Beispiel**:</span><span class="sxs-lookup"><span data-stu-id="8c693-187">**Example**:</span></span>

<span data-ttu-id="8c693-188">Der folgende Codeblock löst den Fehler ""MyFunction": Bezeichner wurde nicht gefunden"</span><span class="sxs-lookup"><span data-stu-id="8c693-188">The following block of code will raise the error "'myFunction': identifier not found"</span></span>

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

<span data-ttu-id="8c693-189">Es gibt zwei Lösungen.</span><span class="sxs-lookup"><span data-stu-id="8c693-189">There are two solutions.</span></span> <span data-ttu-id="8c693-190">Zunächst können Sie die Funktion über alle Aufrufe deklarieren.</span><span class="sxs-lookup"><span data-stu-id="8c693-190">First, you may declare the function above any invocations.</span></span> <span data-ttu-id="8c693-191">Diese Deklaration ist in der Regel am Anfang der Datei durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="8c693-191">Typically, this declaration is done at the top of the file.</span></span>

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

<span data-ttu-id="8c693-192">Alternativ können Sie die gesamte Implementierung der Funktion über alle Aufrufe verschieben.</span><span class="sxs-lookup"><span data-stu-id="8c693-192">Alternatively, you can move the entire implementation of the function above any invocations.</span></span> <span data-ttu-id="8c693-193">Dies wirkt sich das Deklarieren und Definieren der Funktion zur gleichen Zeit aus.</span><span class="sxs-lookup"><span data-stu-id="8c693-193">This has the effect of both declaring and defining the function at the same time.</span></span>

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a><span data-ttu-id="8c693-194">Meine Lösung hängt, unendlich, bei der Initialisierung</span><span class="sxs-lookup"><span data-stu-id="8c693-194">My solution hangs infinitely when being initialized</span></span>

<span data-ttu-id="8c693-195">Es ist ein bekanntes Problem kann dadurch eine C++ Lösung unendlich, nicht mehr reagiert (Deadlocks), bei der Initialisierung.</span><span class="sxs-lookup"><span data-stu-id="8c693-195">There is a known issue which can cause a C++ solution to hang infinitely (deadlock) when being initialized.</span></span> <span data-ttu-id="8c693-196">Sie können diese Art von Problem auftreten, wenn Sie feststellen, dass Ihre Projektmappe befindet sich ewig und Sie nicht den Debugger zu verwenden, um "jede Anweisung in den Abschnitten setup() oder loop() Ihrer Anwendung Arduino verknüpfen".</span><span class="sxs-lookup"><span data-stu-id="8c693-196">You may be experiencing this type of issue if you find that your solution appears to hang forever and you are unable to use the debugger to 'break in' to any statement in the setup() or loop() sections of your Arduino Wiring application.</span></span>

<span data-ttu-id="8c693-197">**Ursache**: Ein Objekt erstellt wird, oder eine Funktion wird aufgerufen wird, was zu einer Aktion für den asynchronen führt, bevor die Projektmappe vollständig initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="8c693-197">**Cause**: An object is being created or a function is being called which leads to an asyncronous action before the solution has finished initializing.</span></span> <span data-ttu-id="8c693-198">Es wird wahrscheinlich von eines Objekts-Konstruktor aufrufen einer API-Funktion wie verursacht `pinMode`.</span><span class="sxs-lookup"><span data-stu-id="8c693-198">It is likely caused from an object's constructor calling an API function like `pinMode`.</span></span>

<span data-ttu-id="8c693-199">**Lösung**: Verschieben Sie keine Objektkonstruktoren und Funktionsaufrufe von Abschnitts für Initialisierung von Code und in der `setup()` Block.</span><span class="sxs-lookup"><span data-stu-id="8c693-199">**Solution**: Move any object constructors and function calls away from the initialization section of code and into the `setup()` block.</span></span>

<span data-ttu-id="8c693-200">**Beispiel 1**:</span><span class="sxs-lookup"><span data-stu-id="8c693-200">**Example 1**:</span></span>

<span data-ttu-id="8c693-201">Die Ausführung von dieser Version aufruft, eine Funktion namens `setPinModes()` vor die Lösung selbst initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="8c693-201">The execution of this sketch calls a function called `setPinModes()` before the solution itself has been initialized.</span></span> <span data-ttu-id="8c693-202">Die Lösung scheinbar, ausführen, jedoch wird unendlich hängen.</span><span class="sxs-lookup"><span data-stu-id="8c693-202">The solution will appear to execute but will hang infinitely.</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="8c693-203">Die Lösung unterschreitet, haben wir einfach die Ausführung von verschoben `setPinModes()` auf die `setup()` Funktion:</span><span class="sxs-lookup"><span data-stu-id="8c693-203">The solution is below, we've simply moved the execution of `setPinModes()` to the `setup()` function:</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="8c693-204">**Beispiel 2**:</span><span class="sxs-lookup"><span data-stu-id="8c693-204">**Example 2**:</span></span>

<span data-ttu-id="8c693-205">Die Ausführung von dieser Version erstellt ein Objekt, auf dem Stapel vor dem `setup()` aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8c693-205">The execution of this sketch creates an object on the stack before `setup()` has been called.</span></span> <span data-ttu-id="8c693-206">Da die Aufrufe `pinMode` in seinem Konstruktor, wird dies auch einen Deadlock verursachen.</span><span class="sxs-lookup"><span data-stu-id="8c693-206">Since the object calls `pinMode` in its constructor, this will also cause a deadlock.</span></span> <span data-ttu-id="8c693-207">Dies ist ungewöhnlich, dass Problem, aber aus bestimmten Bibliotheken mit Objekten auftreten (z. B. die Arduino `LiquidCrystal` Bibliothek).</span><span class="sxs-lookup"><span data-stu-id="8c693-207">This is an uncommon issue, but may occur with objects from certain libraries (like the Arduino `LiquidCrystal` library).</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

<span data-ttu-id="8c693-208">Die Lösung ist unten.</span><span class="sxs-lookup"><span data-stu-id="8c693-208">The solution is below.</span></span> <span data-ttu-id="8c693-209">Wir haben das Objekt in einen Objektzeiger geändert und die Initialisierung des Objekts, das verschoben `setup()`.</span><span class="sxs-lookup"><span data-stu-id="8c693-209">We've changed the object to an object pointer and moved the initialization of the object to `setup()`.</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a><span data-ttu-id="8c693-210">Mithilfe von `Serial.print()` und `Serial.println()`</span><span class="sxs-lookup"><span data-stu-id="8c693-210">Using `Serial.print()` and `Serial.println()`</span></span>

<span data-ttu-id="8c693-211">Verwenden Sie viele Arduino Skizzen `Serial` Daten mit der seriellen Konsole drucken (wenn geöffnet) oder auf die serielle Zeilen (USB oder tx/Rx) zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="8c693-211">Many Arduino sketches use `Serial` to print data to the serial console (if opened) or to write to the serial lines (USB or tx/rx).</span></span> <span data-ttu-id="8c693-212">In früheren Versionen des SDK Lightning Hardware `Serial` Support nicht enthalten war, dazu, dass wir bereitgestellt ein `Log()` Funktion, die an den Debugger druckt Ausgabefenster in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c693-212">In prior versions of the Lightning SDK, Hardware `Serial` support wasn't included, so we provided a `Log()` function which will print to the debugger output window in Visual Studio.</span></span> `Serial.print*()` <span data-ttu-id="8c693-213">oder `Serial.write()` hatten, entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8c693-213">or `Serial.write()` had to be removed.</span></span>

<span data-ttu-id="8c693-214">Dabei ist jedoch _Lightning SDK 1.1.0_, haben wir hinzugefügt `Hardware Serial` Unterstützung und die beiden `Serial.print*()` oder `Serial.write()` Funktionen werden vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8c693-214">However, starting with _Lightning SDK v1.1.0_, we've added `Hardware Serial` support and both `Serial.print*()` or `Serial.write()` functions are fully supported.</span></span> <span data-ttu-id="8c693-215">Wenn Sie eine Skizze für die einem arduino-Board kopieren, müssen Sie also nicht diese serielle Verweise in der Windows-IoT-Version der Skizze ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8c693-215">So, if you are copying a sketch built for an Arduino, you won't need to replace any of these Serial references in the Windows IoT version of the sketch.</span></span>

<span data-ttu-id="8c693-216">Darüber hinaus haben wir die Funktionalität des erweiterten `Serial.print()` und `Serial.println()`, zum Debuggerfenster ausgegeben, wenn ein Debugger, zusätzlich zum Schreiben in die seriellen Anschlüsse des Hardware angefügt ist-.</span><span class="sxs-lookup"><span data-stu-id="8c693-216">Furthermore, we've extended the functionality of `Serial.print()` and `Serial.println()`, to output to the debugger window when a debugger is attached - in addition to writing to the hardware serial pins.</span></span>
<span data-ttu-id="8c693-217">Die Debugausgabe Drucken wird ausgeführt als der Standard seit lesen, dass die Ausgabe ist, welche die meisten Benutzer sollten beim Festlegen ihrer Skizzen.</span><span class="sxs-lookup"><span data-stu-id="8c693-217">The debug output printing is set as the default since reading that output is what most users would want when running their sketches.</span></span> <span data-ttu-id="8c693-218">Diese Funktionalität kann jedoch auch deaktiviert werden. z. B. zur Verbesserung der Leistung einfach aufrufen `Serial.enablePrintDebugOutput(false);` Sie ihn in Ihre Sketch deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="8c693-218">However, that functionality can be disabled as well; e.g. to improve performance, simply call `Serial.enablePrintDebugOutput(false);` to disable it in your sketch.</span></span> <span data-ttu-id="8c693-219">Um es erneut zu aktivieren, rufen Sie `Serial.enablePrintDebugOutput(true);`.</span><span class="sxs-lookup"><span data-stu-id="8c693-219">To re-enable it, call `Serial.enablePrintDebugOutput(true);`.</span></span> <span data-ttu-id="8c693-220">Das Schreiben in die Hardware serielle Pins wird durch diese Aufrufe nicht beeinflusst.</span><span class="sxs-lookup"><span data-stu-id="8c693-220">Writing to the hardware serial pins is not affected by those calls.</span></span>

<span data-ttu-id="8c693-221">Beachten Sie, dass Sie nicht benötigen, können Sie die serielle Pins wie z. B. eine FTDI, Ausgabe gesendet, um das Debuggerfenster zu alle Peripheriegeräte zuordnen.</span><span class="sxs-lookup"><span data-stu-id="8c693-221">Note, you do NOT need to attach any peripheral to your serial pins such as an FTDI, to get output sent to the debugger window.</span></span> <span data-ttu-id="8c693-222">Allerdings müssen Sie sicherstellen, dass der Debuggerfenster geöffnet ist, während die Anwendung im Debugmodus befindet.</span><span class="sxs-lookup"><span data-stu-id="8c693-222">However, you'll need to make sure the debugger window is open while your application is being debugged.</span></span>

![Ausgabe des Debuggers](../media/ArduinoWiringPortingGuide/debugger_output.png)

<span data-ttu-id="8c693-224">Die Projektvorlagen auf aktualisiert wurden die [Windows IoT Core-Projektvorlagen-Erweiterungsseite](https://go.microsoft.com/fwlink/?linkid=847472) zum ermöglichen der Verwendung von Hardware `Serial` standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="8c693-224">The project templates have been updated on the [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to enable using Hardware `Serial` out of the box.</span></span> <span data-ttu-id="8c693-225">Aber wenn Ihre Anwendung verknüpfen Arduino bereits mit einer älteren Version von Project-Vorlage erstellt wurde, Sie müssen (1) auf das neueste Lightning-SDK, aktualisieren Sie das Projekt 1.1.0 oder höher, und (2) fügen Sie die erforderliche Hardware seriellen Gerät Möglichkeit, Ihre AppxManifest verwenden, können `Serial`.</span><span class="sxs-lookup"><span data-stu-id="8c693-225">However, if your Arduino Wiring application has already been created using an older project template version, you'll need to 1) Upgrade your project to the latest Lightning SDK, v1.1.0 or later, and 2) add the required Hardware Serial device capability to your AppxManifest to be able to use `Serial`.</span></span>

### <a name="hardware-serial-device-capability-requirements"></a><span data-ttu-id="8c693-226">Hardwareanforderungen für seriellen Gerät-Funktion</span><span class="sxs-lookup"><span data-stu-id="8c693-226">Hardware Serial device capability requirements</span></span>

<span data-ttu-id="8c693-227">Serielle Hardware-Funktionalität in Windows 10 IoT Core erfordert Gerät Deklarationen der Funktionen, die das AppX-Manifest hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8c693-227">Hardware Serial functionality in Windows 10 IoT Core requires device capability declarations added to the AppX manifest.</span></span>

<span data-ttu-id="8c693-228">Suchen Sie die Datei `Package.appxmanifest` in Ihrem Projekt, indem Sie Sie im Projektmappen-Explorer den Dateinamen eingeben.</span><span class="sxs-lookup"><span data-stu-id="8c693-228">Find the file `Package.appxmanifest` in your project, by typing the file name in the solution explorer.</span></span> <span data-ttu-id="8c693-229">Klicken Sie dann, klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie "Öffnen mit...".</span><span class="sxs-lookup"><span data-stu-id="8c693-229">Then, right click the file and choose 'Open With...'.</span></span> <span data-ttu-id="8c693-230">Wählen Sie "XML (Text)-Editor" aus, und klicken Sie auf "OK".</span><span class="sxs-lookup"><span data-stu-id="8c693-230">Choose 'XML (Text) Editor' and click 'OK'.</span></span>

![Aktualisieren die Datei "Package.appxmanifest"](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

<span data-ttu-id="8c693-232">Fügen Sie in die Appx-manifest-Datei-Editor, der `serialcommunication` DeviceCapability zu Ihrem Projekt wie in den folgenden XML-Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="8c693-232">In the appx manifest file editor, add the `serialcommunication` DeviceCapability to your project as in the following XML snippet:</span></span>

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a><span data-ttu-id="8c693-233">Aktualisieren Sie das Projekt auf das neueste Lightning-SDK</span><span class="sxs-lookup"><span data-stu-id="8c693-233">Upgrade your project to the latest Lightning SDK</span></span>

<span data-ttu-id="8c693-234">Abhängig von die Projekten Arduino Verknüpfen der [Lightning-SDK-Nuget-Paket](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) die erforderliche verknüpfen Arduino-Funktionen und Deklarationen als auch mit dem Treiber Lightning-Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="8c693-234">The Arduino Wiring projects depend on the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) to implement the required Arduino Wiring functions and declarations as well as interface with the Lightning driver.</span></span> <span data-ttu-id="8c693-235">Das neueste Lightning-SDK enthält die neuesten Verbesserungen und Fehlerbehebungen.</span><span class="sxs-lookup"><span data-stu-id="8c693-235">The latest Lightning SDK will contain the latest improvements and bug fixes.</span></span> <span data-ttu-id="8c693-236">Um auf das neueste Lightning-SDK zu aktualisieren, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="8c693-236">To upgrade to the latest Lightning SDK, follow these steps:</span></span>

- <span data-ttu-id="8c693-237">Klicken Sie im Projektmappen-Explorer klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf "Nuget-Pakete verwalten"</span><span class="sxs-lookup"><span data-stu-id="8c693-237">In the Solution Explorer, right click on your project and click 'Manage Nuget Packages...'</span></span>
- <span data-ttu-id="8c693-238">In den NuGet Package Manager, wechseln Sie zur Registerkarte "Installiert". Sie sollte das Microsoft.IoT.Lightning-Paket installiert angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8c693-238">In the NuGet Package Manager, go to the 'Installed' tab. You should see the Microsoft.IoT.Lightning package installed</span></span>
- <span data-ttu-id="8c693-239">Verfügbare Versionen werden in der Combobox 'Version' aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="8c693-239">Available versions will be listed inside the 'Version' combobox.</span></span>
- <span data-ttu-id="8c693-240">Wählen Sie die neueste Version aus, und klicken Sie auf 'Aktualisieren', um das Paket zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8c693-240">Choose the latest version, and click 'Update' to update your package.</span></span>
- <span data-ttu-id="8c693-241">Upgrade auf einer Vorabversion, beachten Sie unbedingt auch Kontrollkästchen "Vorabversion einbeziehen" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8c693-241">Notice, to upgrade to a prerelease version, make sure to check the 'Include prerelease' checkbox as well.</span></span>

![NuGet-Paket-manager](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
