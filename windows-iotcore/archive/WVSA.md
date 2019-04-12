---
title: Virtuelle Windows-Shields Arduino-Übersicht
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Informationen Sie zum Einrichten von virtuellen Windows-Shields für Arduino, und Erstellen Ihrer ersten Windows 10 IoT Core-app.
keywords: Windows Iot, WVSA, Windows Virtual Shields, Arduino-app
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513177"
---
> [!NOTE]
> <span data-ttu-id="e1c87-104">Sie zeigen die archivierte Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e1c87-104">You are viewing archived documentation.</span></span> <span data-ttu-id="e1c87-105">AllJoyn wird nicht mehr von Windows 10 IoT unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e1c87-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="e1c87-106">Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.</span><span class="sxs-lookup"><span data-stu-id="e1c87-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="e1c87-107">Richten Sie virtuelle Windows-Shields für Arduino</span><span class="sxs-lookup"><span data-stu-id="e1c87-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="e1c87-108">Übersicht</span><span class="sxs-lookup"><span data-stu-id="e1c87-108">Overview</span></span>
<span data-ttu-id="e1c87-109">Wenn Sie verwendet haben eine [Arduino](https://www.arduino.cc), mit dem Konzept von einem Schild vertraut.</span><span class="sxs-lookup"><span data-stu-id="e1c87-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="e1c87-110">Jede Shield verfügt über einen speziellen Zweck (z. B. eine Temperatur Shield, eine Beschleunigungsmesser Schild) kann, und erstellen ein Gerät mit mehreren Shields komplexe teuer und Speicherplatz – ineffizient.</span><span class="sxs-lookup"><span data-stu-id="e1c87-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="e1c87-111">Stellen Sie sich nun vor, dass Sie einem kostengünstigen Windows Lumia-Telefon als eines kompakten Satzes von Greg verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e1c87-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="e1c87-112">Ihr Arduino-Sketches wäre auf Hunderte von Dollar sollte von Sensoren und -Funktionen in Ihrer Windows Phone über Aufrufe der leicht zu bedienenden Bibliothek zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="e1c87-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="e1c87-113">Dies ist genau das, was für Entwickler der Windows virtuellen Shields für Arduino-Bibliothek aktiviert.</span><span class="sxs-lookup"><span data-stu-id="e1c87-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="e1c87-114">Und das ist nicht das beste daran: Diese Technologie funktioniert auf allen Windows 10-Geräten, sodass Sie die Sensoren und Funktionen auf Ihrem PC oder Surface ebenfalls verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e1c87-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="e1c87-115">Darüber hinaus kann die Arduino rechenintensive Aufgaben wie die Spracherkennung und Analyse auf das Windows 10-begleitgerät Web Auslagern!</span><span class="sxs-lookup"><span data-stu-id="e1c87-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="e1c87-116">Erfahren Sie, wie Sie Hardware und Software zum Arbeiten mit virtuellen Windows-Shields für Arduino einrichten.</span><span class="sxs-lookup"><span data-stu-id="e1c87-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="e1c87-117">1. Bereiten Sie Ihr Windows 10-Gerät für die Entwicklung von Projekten mithilfe von virtuellen Windows-Shields für Arduino.</span><span class="sxs-lookup"><span data-stu-id="e1c87-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="e1c87-118">Klicken Sie in diesem Abschnitt des Tutorials bereiten Sie ein Windows 10-Gerät Ihrer Wahl durch das Laden es mit der Windows virtuellen Shields für Arduino-Anwendung – diese universellen Windows-Anwendung können Sie Ihr Gerät als ein Schild"virtuellen" für ein Arduino-Board zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1c87-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="e1c87-119">Dies führt einige leistungsstarken Möglichkeiten für Entwickler, nutzen die Spracherkennung, sodass touch Bildschirme und die rechenleistung von Windows mit relativ einfach.</span><span class="sxs-lookup"><span data-stu-id="e1c87-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="e1c87-120">Hardware</span><span class="sxs-lookup"><span data-stu-id="e1c87-120">Hardware</span></span>
<span data-ttu-id="e1c87-121">Der Windows virtuellen Shields für Arduino-Anwendung kann auf jedem Windows 10-Gerät ausgeführt, aber in diesem Tutorial wird erläutert, Setup mit einem Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="e1c87-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="e1c87-122">*Was Sie* Windows Phone-Ausführen von Windows 10 – es wird empfohlen die [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) oder [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span><span class="sxs-lookup"><span data-stu-id="e1c87-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

*<span data-ttu-id="e1c87-123">Richten Sie Ihre Windows Phone</span><span class="sxs-lookup"><span data-stu-id="e1c87-123">Set up your Windows Phone</span></span>*

<span data-ttu-id="e1c87-124">Wenn Ihr Telefon nicht bereits Windows 10 ausgeführt wird, stehen die Optionen zum Installieren der Preview-Versionen der Software.</span><span class="sxs-lookup"><span data-stu-id="e1c87-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="e1c87-125">Windows Phone 8-Benutzern gelangen, die Microsoft Store-app, die Anwendung "Windows-Insider" herunterzuladen: Diese app kann der Benutzer zum Abonnieren von Windows 10 Technical Preview-Versionen als Updates empfangen.</span><span class="sxs-lookup"><span data-stu-id="e1c87-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="e1c87-126">Befolgen Sie die Anweisungen beim Öffnen der app, und fortsetzen Sie, sobald Ihr Telefon wurde erfolgreich auf Windows 10 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e1c87-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="e1c87-127">Software</span><span class="sxs-lookup"><span data-stu-id="e1c87-127">Software</span></span>

<span data-ttu-id="e1c87-128">Es gibt zwei Optionen zur Installation der Windows virtuellen Shields für Arduino-UWP-app auf Ihrem Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="e1c87-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="e1c87-129">Herunterladen der app ist die Wahl einfacher, schneller.</span><span class="sxs-lookup"><span data-stu-id="e1c87-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="e1c87-130">Die app aus dem Microsoft Store herunterladen</span><span class="sxs-lookup"><span data-stu-id="e1c87-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="e1c87-131">Sideloaden der app mit einem PC und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1c87-131">Sideload the app using a PC and Visual Studio</span></span>

*<span data-ttu-id="e1c87-132">Option 1: Die app aus dem Microsoft Store herunterladen</span><span class="sxs-lookup"><span data-stu-id="e1c87-132">Option 1: Download the app from the Microsoft Store</span></span>*

<span data-ttu-id="e1c87-133">Gehen Sie folgendermaßen vor [Link](https://www.microsoft.com/store/apps/9nblgggz0mld) klicken Sie auf der Seite der Microsoft Store für virtuelle Windows-Shields für Arduino, laden Sie die Anwendung, und installieren.</span><span class="sxs-lookup"><span data-stu-id="e1c87-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="e1c87-134">Sie können dann öffnen, die Anwendung aus, um sicherzustellen, dass es ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e1c87-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="e1c87-135">Ihr Gerät ist nun dafür eingerichtet, als ein Schild"virtual", die für einem arduino-Board verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e1c87-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="e1c87-136">Sie können mit der nächsten Seite fortfahren.</span><span class="sxs-lookup"><span data-stu-id="e1c87-136">You can proceed to the next page.</span></span>

<span data-ttu-id="e1c87-137">*Option 2: Sideloaden der app mit einem PC und Visual Studio*
_Voraussetzungen_</span><span class="sxs-lookup"><span data-stu-id="e1c87-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="e1c87-138">Visual Studio 2017 zum querladen der Windows virtuellen Shields für Arduino-app auf einem Telefon Developer entsperrt.</span><span class="sxs-lookup"><span data-stu-id="e1c87-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="e1c87-139">Dies [Repository](https://github.com/ms-iot/virtual-shields-universal) , die den Code für den virtuellen Windows-Shields für Arduino-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="e1c87-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="e1c87-140">Klonen Sie das Repository oder Herunterladen Sie als ZIP-Datei auf dem lokalen Datenträger.</span><span class="sxs-lookup"><span data-stu-id="e1c87-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="e1c87-141">Wenn Sie nicht mit Git und möchten, führen Sie einen Klon der entsprechenden vertraut sind, befolgen Sie die Anweisungen [hier](https://help.github.com/articles/cloning-a-repository).</span><span class="sxs-lookup"><span data-stu-id="e1c87-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

_<span data-ttu-id="e1c87-142">Richten Sie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e1c87-142">Set up Visual Studio 2017</span></span>_
1. <span data-ttu-id="e1c87-143">Installieren von Visual Studio 2017 mit dem Windows 10 Developer Preview-Tools von [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="e1c87-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="e1c87-144">Es wird empfohlen, die kostenlose Community-Version von Visual Studio, jedoch als Enterprise und Professional würde auch funktionieren.</span><span class="sxs-lookup"><span data-stu-id="e1c87-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="e1c87-145">Wenn Sie bereits Visual Studio installiert haben, fahren Sie mit der im nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="e1c87-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="e1c87-146">In Visual Studio laden die Shield.sln aus dem Repository heruntergeladen haben, in der "Voraussetzungen" weiter oben.</span><span class="sxs-lookup"><span data-stu-id="e1c87-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="e1c87-147">Stellen Sie sicher, dass Ihr Windows 10-Gerät (in diesem Fall eine Windows Phone) Developer entsperrt ist.</span><span class="sxs-lookup"><span data-stu-id="e1c87-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="e1c87-148">[Auf dieser Seite](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) wird erläutert, wie zum Entsperren von Windows Phone 8.1, 8 und 7.1; allerdings die Schritte sind identisch für Windows 10-Smartphones.</span><span class="sxs-lookup"><span data-stu-id="e1c87-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="e1c87-149">Schließen Sie Ihr Windows 10-Gerät an Ihren Computer und Bereitstellen Sie des Programms Shield.sln auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="e1c87-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="e1c87-150">Zu diesem Zweck stellen für einen "Lokaler Computer", und achten Sie darauf, dass Sie die Architektur des Geräts wie "ARM" fest.</span><span class="sxs-lookup"><span data-stu-id="e1c87-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="e1c87-151">Führen Sie den neu installierten war virtuellen Windows-Shields für Arduino-Anwendung auf Ihrem Telefon, um sicherzustellen, dass die Bereitstellung erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="e1c87-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="e1c87-152">Windows 10-Geräten ist nun dafür eingerichtet, als ein virtuelles Schild verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e1c87-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="e1c87-153">2. Richten Sie Ihre Arduino, um der Windows virtuellen Shields für Arduino-Bibliothek verwenden</span><span class="sxs-lookup"><span data-stu-id="e1c87-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="e1c87-154">Mit unserer begleitgerät für die Windows 10 ordnungsgemäß eingerichtet kommen wir unsere Arduino der Windows virtuellen Shields für Arduino-Bibliothek zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1c87-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="e1c87-155">Sie können eine Verbindung zwischen Ihrem Arduino und Ihren Windows 10 "virtuellen Schild" über USB, Bluetooth oder WLAN-einrichten.</span><span class="sxs-lookup"><span data-stu-id="e1c87-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="e1c87-156">Dieses Lernprogramm wird erläutert, wie Sie das Setup über eine Bluetooth-Verbindung abgeschlossen, aber gerne Experimentieren mit den anderen Optionen.</span><span class="sxs-lookup"><span data-stu-id="e1c87-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="e1c87-157">Hardware</span><span class="sxs-lookup"><span data-stu-id="e1c87-157">Hardware</span></span>
*<span data-ttu-id="e1c87-158">Was Sie benötigen</span><span class="sxs-lookup"><span data-stu-id="e1c87-158">What you need</span></span>*
* <span data-ttu-id="e1c87-159">Arduino Uno oder ein kompatibles Gerät</span><span class="sxs-lookup"><span data-stu-id="e1c87-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="e1c87-160">Drähten</span><span class="sxs-lookup"><span data-stu-id="e1c87-160">Connecting wires</span></span>
* <span data-ttu-id="e1c87-161">Einen PC mit dem Ihr Arduino-Skizzen hochgeladen</span><span class="sxs-lookup"><span data-stu-id="e1c87-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="e1c87-162">Standard A Standard B-USB - erforderlich, um einen groben Entwurf auf Ihrem Arduino-Gerät hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="e1c87-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="e1c87-163">Optional: Bluetooth-Modul – nur erforderlich, wenn Sie für die Verbindung von Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="e1c87-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="e1c87-164">Optional: Wi-Fi-Modul – nur erforderlich, wenn Sie wi-Fi-Verbindung herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="e1c87-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="e1c87-165">Richten Sie Ihre Arduino</span><span class="sxs-lookup"><span data-stu-id="e1c87-165">Set up your Arduino</span></span>
* <span data-ttu-id="e1c87-166">Bereiten Sie die Bluetooth-Modul vor, bei Bedarf (das Bluetooth-Modul möglicherweise Header angelöteter).</span><span class="sxs-lookup"><span data-stu-id="e1c87-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="e1c87-167">Mit Ausnahme der anderen unten aufgeführten, des Bluetooth-Moduls mit dem Arduino pro verbunden [im Diagramm verknüpfen](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span><span class="sxs-lookup"><span data-stu-id="e1c87-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="e1c87-168">Unterschied: Verwenden Sie anstelle von 2 und 3 Pins 0 und 1:</span><span class="sxs-lookup"><span data-stu-id="e1c87-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="e1c87-169">Die Bluetooth-TX PIN 0 (Arduino-RX oder RX0) eine Verbindung herstellen soll.</span><span class="sxs-lookup"><span data-stu-id="e1c87-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="e1c87-170">Die Bluetooth-RX PIN 1 (Arduino TX oder TX1) eine Verbindung herstellen soll.</span><span class="sxs-lookup"><span data-stu-id="e1c87-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="e1c87-171">Software</span><span class="sxs-lookup"><span data-stu-id="e1c87-171">Software</span></span>
*<span data-ttu-id="e1c87-172">Was Sie benötigen</span><span class="sxs-lookup"><span data-stu-id="e1c87-172">What you need</span></span>*
* <span data-ttu-id="e1c87-173">Arduino IDE 1.6 oder höher</span><span class="sxs-lookup"><span data-stu-id="e1c87-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="e1c87-174">ArduinoJSON-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e1c87-174">ArduinoJSON library</span></span>
* <span data-ttu-id="e1c87-175">[Dieses Repository](https://github.com/ms-iot/virtual-shields-arduino), enthält die Beispiel-Skizze die auf der Arduino ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e1c87-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

*<span data-ttu-id="e1c87-176">Richten Sie Ihrer Arduino-IDE ein</span><span class="sxs-lookup"><span data-stu-id="e1c87-176">Set up your Arduino IDE</span></span>*
* <span data-ttu-id="e1c87-177">Herunterladen und Installieren der Arduino-IDE, und starten Sie das Programm.</span><span class="sxs-lookup"><span data-stu-id="e1c87-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="e1c87-178">Stellen Sie sicher, dass Sie die richtige Arduino-Board unter ausgewählt haben *Tools > Board*.</span><span class="sxs-lookup"><span data-stu-id="e1c87-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="e1c87-179">Stellen Sie sicher, dass Sie den richtigen COM-Anschluss unter ausgewählt haben *Tools > Port*.</span><span class="sxs-lookup"><span data-stu-id="e1c87-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="e1c87-180">Der Name des Boards, sollte neben jeder Option erleichtert, wählen Sie die richtige Option angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e1c87-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

*<span data-ttu-id="e1c87-181">Einrichten der ArduinoJSON-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e1c87-181">Set up the ArduinoJSON library</span></span>*
* <span data-ttu-id="e1c87-182">Von der [ArduinoJson Repository](https://github.com/bblanchon/ArduinoJson), ein Repository Klonen oder Herunterladen der ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="e1c87-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="e1c87-183">Platzieren Sie das gesamte Repository in Ihrem Ordner "Bibliotheken" (d. h. `Documents\Arduino\libraries\ArduinoJson\`).</span><span class="sxs-lookup"><span data-stu-id="e1c87-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

*<span data-ttu-id="e1c87-184">Einrichten der Windows virtuellen Shields für Arduino-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e1c87-184">Set up the Windows Virtual Shields for Arduino Library</span></span>*
* <span data-ttu-id="e1c87-185">Klon [dieses Repository](https://github.com/ms-iot/virtual-shields-arduino) oder Laden Sie die ZIP-Datei herunter.</span><span class="sxs-lookup"><span data-stu-id="e1c87-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="e1c87-186">Wenn Sie nicht mit Git und möchten, führen Sie einen Klon der entsprechenden vertraut sind, befolgen Sie die Anweisungen [hier](https://help.github.com/articles/cloning-a-repository/).</span><span class="sxs-lookup"><span data-stu-id="e1c87-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="e1c87-187">Kopieren Sie den Ordner "VirtualShield", finden Sie in den Ordner "Arduino\Libraries" des Repositorys, die Sie gerade heruntergeladen, klicken Sie auf Ihrem Arduino-Ordner "Library haben" (d. h. `Documents\Arduino\libraries\VirtualShield\`).</span><span class="sxs-lookup"><span data-stu-id="e1c87-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

*<span data-ttu-id="e1c87-188">Ihre Einrichtung testen</span><span class="sxs-lookup"><span data-stu-id="e1c87-188">Test your setup</span></span>*
* <span data-ttu-id="e1c87-189">Die Arduino-IDE, wechseln Sie zum Menüelement *Datei -> Beispiele für virtuelle Shield -> -> "HelloWorld"-Speech-Ereignisse*.</span><span class="sxs-lookup"><span data-stu-id="e1c87-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="e1c87-190">Dadurch sollte der Spracherkennung basierend Hello World-Beispiel geladen, das wir für dieses Tutorial verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1c87-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="e1c87-191">Vor dem Hochladen der Skizze auf Ihrem Arduino, müssen entfernen Sie die Bluetooth-TX- und RX-verbindet vorübergehend aus der Arduino (ist nur eine serieller Anschluss, der die USB und Bluetooth - die Bluetooth gemeinsam mit dem Upload beeinträchtigt).</span><span class="sxs-lookup"><span data-stu-id="e1c87-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="e1c87-192">Hochladen der Skizze durch Drücken der Schaltfläche "Upload" in der IDE.</span><span class="sxs-lookup"><span data-stu-id="e1c87-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="e1c87-193">Ersetzen Sie den Bluetooth-TX- und RX einfach in die Arduino-Pins (Bluetooth TX Arduino RX (oder RX0) und Bluetooth RX Arduino TX oder (TX1)).</span><span class="sxs-lookup"><span data-stu-id="e1c87-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="e1c87-194">Auf das Telefon (oder andere Windows-Geräte), die Sie auf der vorherigen Seite, mit dem Bluetooth-Gerät auf Ihrem Arduino in den Bluetooth-Einstellungen vorbereitet haben.</span><span class="sxs-lookup"><span data-stu-id="e1c87-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="e1c87-195">Wenn Sie die BlueSMiRF verwenden, ist der Standard-Pin-Codes 1234.</span><span class="sxs-lookup"><span data-stu-id="e1c87-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="e1c87-196">Die rote blinkende LED auf dem BlueSMiRF weiterhin nach einer erfolgreichen Kopplung rot blinken zu lassen.</span><span class="sxs-lookup"><span data-stu-id="e1c87-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="e1c87-197">Dies ist das erwartungsgemäße Verhalten.</span><span class="sxs-lookup"><span data-stu-id="e1c87-197">This is expected.</span></span> <span data-ttu-id="e1c87-198">Es wird nur Grün, nach der eine Verbindung mit der Windows virtuellen Shields für Arduino-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="e1c87-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="e1c87-199">3. Schreiben Sie Ihre erste app: Hello, Hauptverkaufsargument!</span><span class="sxs-lookup"><span data-stu-id="e1c87-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="e1c87-200">Hello World-fähige Sprache LED-Beispiel</span><span class="sxs-lookup"><span data-stu-id="e1c87-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="e1c87-201">Mit Ihrer Windows Phone (oder möglicherweise alle Windows 10-Geräte) und Ihre Arduino, wie in den vorherigen Schritten in diesem Tutorial vorbereitet, nun können Sie unser Beispiel zu testen.</span><span class="sxs-lookup"><span data-stu-id="e1c87-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="e1c87-202">Bereiten Sie das Arduino-Board, indem Sie eine LED mit einem Widerstand PIN 8 einbinden.</span><span class="sxs-lookup"><span data-stu-id="e1c87-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="e1c87-203">Stellen Sie sicher, dass Ihre Arduino weiterhin mit dem Beispiel für die HelloWorld-Speech-Ereignisse hochgeladen wurde, und schließen Sie die Arduino an eine Stromversorgung.</span><span class="sxs-lookup"><span data-stu-id="e1c87-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="e1c87-204">Führen Sie die virtuellen Windows-Shields für Arduino-app, auf der Windows Phone, die Sie zuvor erstellt.</span><span class="sxs-lookup"><span data-stu-id="e1c87-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="e1c87-205">Wenn alles ordnungsgemäß eingerichtet wurde, sollte Ihr Telefon mit einem Arduino-Sketch verbinden und freuen uns, Sie mit einen audiohinweis.</span><span class="sxs-lookup"><span data-stu-id="e1c87-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="e1c87-206">Sie können jetzt auf Ihrem Windows 10-Gerät wechseln die LED auf Ihrem Arduino zwischen ein- und ausschalten 'on' oder 'off' sagen!</span><span class="sxs-lookup"><span data-stu-id="e1c87-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="e1c87-207">Arduino Sketch verknüpfen: Hello World-Beispiel</span><span class="sxs-lookup"><span data-stu-id="e1c87-207">Arduino Wiring Sketch: Hello World example</span></span>

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


