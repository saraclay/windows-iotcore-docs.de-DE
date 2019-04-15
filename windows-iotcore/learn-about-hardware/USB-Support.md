---
title: Eine Übersicht über das USB-Unterstützung und Doppelrolle für Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: Erfahren Sie, wie USB-Unterstützung und Doppelrolle ist, sowie wie Sie dies für Ihre Windows 10 IoT Core-Geräte anpassen.
keywords: Windows Iot, USB-Unterstützung, Doppelrolle, USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512857"
---
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="6b83b-104">Übersicht über USB-Unterstützung und Dual-Rolle</span><span class="sxs-lookup"><span data-stu-id="6b83b-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="6b83b-105">Ein serieller Bus USB (Universal) bietet eine serielle erweiterbar, hot-Plug-Plug & Play-Schnittstelle, die eine kostengünstige Verbindung für Peripheriegeräte, z. B. Tastaturen, Mäuse, Joysticks, Drucker, Scanner, Speichergeräte, Modems und Video standard stellt sicher Webkonferenzen-Kameras.</span><span class="sxs-lookup"><span data-stu-id="6b83b-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="6b83b-106">Wenn wir über USB-Geräte sprechen, der USB-funktionsstapel bezieht sich auf eine Gruppe von Treibern, die aufgelistet werden, und der Plug & Play-Manager geladen, und einem zusammengesetzten USB-Gerät kann mehrere Schnittstellen in einer einzelnen Konfiguration unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6b83b-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="6b83b-107">Wenngleich die meisten was wir in diesem sprechen Artikel bezieht sich auf die Doppelrolle für USB-2.0, besser bekannt als USB-auf dem laufenden oder USB OTG oder OTG, es ist auch hilfreich zu wissen, über USB 3.0 und wie es USB 2.0 unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="6b83b-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="6b83b-108">Die USB OTG definiert zwei Rollen für Geräte: OTG-A-Gerät und OTG-B-Gerät, Netzteile angeben welcher Seite auf die Verknüpfung und ist dem zunächst den Host.</span><span class="sxs-lookup"><span data-stu-id="6b83b-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="6b83b-109">Da jeder Controller OTG beide Rollen unterstützt, werden sie häufig "Dual-Rolle" Controller anstelle von "OTG-Controller." bezeichnet</span><span class="sxs-lookup"><span data-stu-id="6b83b-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="6b83b-110">USB-3.0 können dagegen auf Geräten in Hosts oder Peripheriegeräte vornehmen.</span><span class="sxs-lookup"><span data-stu-id="6b83b-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="6b83b-111">Einige Geräte sind beide Rollen je nach Art am anderen Ende erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="6b83b-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="6b83b-112">Diese Arten von Ports werden als Dual-Rolle-Daten (DRD) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="6b83b-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="6b83b-113">Wenn zwei solche Geräte verbunden sind, die Rollen werden nach dem Zufallsprinzip zugewiesen, aber ein Austausch kann von beiden Enden so sein.</span><span class="sxs-lookup"><span data-stu-id="6b83b-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="6b83b-114">Architektur der USB-Funktion in Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="6b83b-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="6b83b-115">Wenn die Windows 10 IoT-Plattform wie USB-Gerät fungiert, wird eine von mehreren Konfigurationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="6b83b-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="6b83b-116">Jede Konfiguration verfügt über eine oder mehrere USB-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="6b83b-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="6b83b-117">Um USB OTG ordnungsgemäß auf Windows 10 IoT zu unterstützen, müssen einige Dinge geregelt werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="6b83b-118">Komponenten OEMs müssen bereitstellen</span><span class="sxs-lookup"><span data-stu-id="6b83b-118">Components OEMs have to supply</span></span>

<span data-ttu-id="6b83b-119">OEMs müssen Komponenten auf beiden Seiten – für die USB-Gerät-Seite und möglicherweise auch der USB-Hostseite angeben.</span><span class="sxs-lookup"><span data-stu-id="6b83b-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![Stellt für ein OEM-Komponenten](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="6b83b-121">OEMs unterstützen für beide Seiten</span><span class="sxs-lookup"><span data-stu-id="6b83b-121">OEMs support for both sides</span></span>

<span data-ttu-id="6b83b-122">Alle USB-Gerät verfügt über eindeutige Anbieter-ID und PID, die es zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="6b83b-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="6b83b-123">Ein OEM, muss als Hersteller eines USB-basierte Windows IoT-Geräts, die angeben.</span><span class="sxs-lookup"><span data-stu-id="6b83b-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="6b83b-124">OEMs können gelten für das USB-Consortium und Abrufen von Unternehmens VID (sofern sie noch keine besitzen) und wählen Sie dann eine PID, die für das jeweilige Produkt eindeutig werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="6b83b-125">Wenn Windows 10 IoT mit USBFN-Funktionalität auf einem PC verbunden ist fungiert es als USB-Gerät (der alle Funktionen, wählen Sie im myUSBFN.sys gesetzt), mit diesen "VID_nnn" und "PID_NNN".</span><span class="sxs-lookup"><span data-stu-id="6b83b-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="6b83b-126">Diese Kombination von Anbieter-ID und die PID wird dann durch den Host-PC zum finden Sie die entsprechenden Treiber (myUSB.sys) geladen.</span><span class="sxs-lookup"><span data-stu-id="6b83b-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![Zusammenkommen, wie USB-Funktionen](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="6b83b-128">Unterstützung von der Geräteseite</span><span class="sxs-lookup"><span data-stu-id="6b83b-128">Supporting from the device side</span></span>

_<span data-ttu-id="6b83b-129">Funktionen mit USBFN aktiviert für die Generierung einer Bildvorschau im FFU einschließen</span><span class="sxs-lookup"><span data-stu-id="6b83b-129">Features to include in FFU for image generation with USBFN enabled</span></span>_
* <span data-ttu-id="6b83b-130">Der IoT-Abbildung muss die erforderlichen Pakete, nämlich ufx01000.sys und usbfnclx.sys enthalten.</span><span class="sxs-lookup"><span data-stu-id="6b83b-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="6b83b-131">Beide verfügen über das folgende Paket `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span><span class="sxs-lookup"><span data-stu-id="6b83b-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="6b83b-132">OEMs müssen ein richtigen "Feature" Tags in ihren XML-Datei verwenden, die alle Funktionen der FFU aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="6b83b-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="6b83b-133">Z. B. in der Datei BoardTestOEMInput.xml fallen in der folgende Eintrag <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> unter enthalten <Microsoft> ein Abschnitt mit Funktionen.</span><span class="sxs-lookup"><span data-stu-id="6b83b-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

_<span data-ttu-id="6b83b-134">Rollenwechsel für USB-Treiber</span><span class="sxs-lookup"><span data-stu-id="6b83b-134">USB Role Switching driver</span></span>_
* <span data-ttu-id="6b83b-135">Für die USB OTG, müssen OEMs Geben Sie den richtigen ACPI-Tabelleneintrag (*MyOTGacpi*) für den Rollenwechsel USB-Treiber und der Treiber selbst (\* myURS.sys).</span><span class="sxs-lookup"><span data-stu-id="6b83b-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

_<span data-ttu-id="6b83b-136">Treiber für den Speichercontroller USB-Funktion</span><span class="sxs-lookup"><span data-stu-id="6b83b-136">USB Function Controller Driver</span></span>_
* <span data-ttu-id="6b83b-137">Dies hängt von der Hardware, durch OEMs verwendet.</span><span class="sxs-lookup"><span data-stu-id="6b83b-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="6b83b-138">Microsoft stellt die USB-Funktion-Controller-Treiber für zwei gängige USB OTG-Chipsätzen - Synopsys und ChipIdea bereit.</span><span class="sxs-lookup"><span data-stu-id="6b83b-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="6b83b-139">Wenn ein OEM entscheidet sich für ein anderes USB OTG-Chipsatz verwenden, die OEM-Abhängige muss ihre eigenen USB-Funktion Controller Hardware angeben (*myfunctioncontroller.sys*).</span><span class="sxs-lookup"><span data-stu-id="6b83b-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

_<span data-ttu-id="6b83b-140">Function-Klasse für USB-Treiber</span><span class="sxs-lookup"><span data-stu-id="6b83b-140">USB Function Class drivers</span></span>_
* <span data-ttu-id="6b83b-141">Mindestens ein USB-Funktion-Klassentreiber muss angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="6b83b-142">Dieser Treiber implementiert bestimmte Funktion von USB-Geräts.</span><span class="sxs-lookup"><span data-stu-id="6b83b-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="6b83b-143">Es bestimmt, was auf das Gerät angezeigt wird wie auf dem Host aus, auch als It-Administrator tun.</span><span class="sxs-lookup"><span data-stu-id="6b83b-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="6b83b-144">Angenommen, entsteht möglicherweise der Eindruck als seriellen Gerät oder als ein Massenspeichergerät oder ein Gerät vollständig benutzerdefinierten Typ (*myUSBFN.sys*).</span><span class="sxs-lookup"><span data-stu-id="6b83b-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

_<span data-ttu-id="6b83b-145">Konfigurieren der USB-Funktion-Gerät</span><span class="sxs-lookup"><span data-stu-id="6b83b-145">Configuring USB Function Device</span></span>_
* <span data-ttu-id="6b83b-146">Wenn die IoT-Plattform im USB-Gerät-Modus ist, kann es unter einer oder mehreren Konfigurationen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="6b83b-147">Jede Konfiguration verwendet, muss hinzugefügt werden, und seine Eigenschaften müssen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-147">Each configuration in use must be added and have its properties specified.</span></span>

_<span data-ttu-id="6b83b-148">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="6b83b-148">Common Properties</span></span>_
* <span data-ttu-id="6b83b-149">Es gibt gemeinsame Eigenschaften für alle Konfigurationen mit USB-Funktion der IoT-Plattform.</span><span class="sxs-lookup"><span data-stu-id="6b83b-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="6b83b-150">Letztlich handelt es sich bis zu den OEM an der standard-USB-Deskriptor-Einträge wie Anbieter-ID, PID, Geräteklasse, DeviceProtocol, Manufacturerer-Zeichenfolge, die Seriennummer usw.</span><span class="sxs-lookup"><span data-stu-id="6b83b-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="6b83b-151">Diese gemeinsamen Eigenschaften werden in der Registrierung an folgendem Speicherort festgelegt werden:</span><span class="sxs-lookup"><span data-stu-id="6b83b-151">These common properties are set in registry in the following location:</span></span> `HKLM\System\ControlSet001\Control\USBFN\default`

```
BcdDevice=0x1 
bDeviceClass=0x0 
bDeviceProtocol=0x0 
bDeviceSubClass= 0x0 
idProduct= 0xc0c0 
idVendor=0x045e 
iManufacturer=1 
iSerialNumber=3 
ManufacturerString=OEMname 
ProductString="Windows IOT" 
SerialNumberString=0x123 
```
> [!IMPORTANT]
> <span data-ttu-id="6b83b-152">Die oben angegebenen Werte werden nur zu Demonstrationszwecken und können nicht in einem Produkt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="6b83b-153">Die OEM-Abhängige ersetzen diese Platzhalter-Felder mit *Istwerte* in jedem der oben aufgeführten Einträge.</span><span class="sxs-lookup"><span data-stu-id="6b83b-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

_<span data-ttu-id="6b83b-154">Pro-Konfigurationseigenschaften</span><span class="sxs-lookup"><span data-stu-id="6b83b-154">Per configuration properties</span></span>_

<span data-ttu-id="6b83b-155">Konfigurationen werden in einer Registrierung unter folgendem Registrierungsschlüssel gespeichert:</span><span class="sxs-lookup"><span data-stu-id="6b83b-155">Configurations are stored in a registry under the following key:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

<span data-ttu-id="6b83b-156">Es wird standardmäßig eine leere USB-Funktion Standardkonfiguration enthalten in der FFU festgelegt:</span><span class="sxs-lookup"><span data-stu-id="6b83b-156">By default, there is an empty default USB function configuration included in the FFU, as set in:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

<span data-ttu-id="6b83b-157">Diese leere standardmäßig führt dazu, die IoT-Plattform als Windows IoT-Gerät für die angezeigt werden, es ist kein Treiber auf dem Host installiert.</span><span class="sxs-lookup"><span data-stu-id="6b83b-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![Konfigurationen für USBFN](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="6b83b-159">Jede Konfiguration muss bestimmte Eigenschaften, z. B. die Liste der Benutzeroberfläche angeben.</span><span class="sxs-lookup"><span data-stu-id="6b83b-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="6b83b-160">Die IoT-Plattform kann als USB-Geräte mit unterschiedlichen Konfigurationen verwendet werden, die freigabena von USB-Schnittstellen definiert, die von USB-Gerät, USB-Host bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="6b83b-161">Derzeit ist die ausgewählte Konfiguration, die bei der die hot-USB-Verbindung aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="6b83b-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_<span data-ttu-id="6b83b-162">Beispiele für Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="6b83b-162">Examples of configurations</span></span>_

1. <span data-ttu-id="6b83b-163">Einmalige Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6b83b-163">Single configuration</span></span>
   1. <span data-ttu-id="6b83b-164">Muss mindestens eine Schnittstelle enthalten</span><span class="sxs-lookup"><span data-stu-id="6b83b-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="6b83b-165">Eine standardmäßige Konfiguration kann sein werden.</span><span class="sxs-lookup"><span data-stu-id="6b83b-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="6b83b-166">Wenn auf einem PC verbunden ist, wird die IoT-Plattform wie dieser Typ von USB-Gerät (z. B. Modem oder Speicher) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6b83b-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`<span data-ttu-id="6b83b-167">,</span><span class="sxs-lookup"><span data-stu-id="6b83b-167">,</span></span> `InterfaceList = "MODEM\0MTP"`

2. <span data-ttu-id="6b83b-168">Zusammengesetzte Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6b83b-168">Composite configuration</span></span>
   1. <span data-ttu-id="6b83b-169">Enthält eine Liste der Schnittstellen mit zusätzlichen Parametern</span><span class="sxs-lookup"><span data-stu-id="6b83b-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="6b83b-170">Wenn auf einem PC verbunden ist, wird die IoT-Plattform als eine zusammengesetzte USB-Gerät mit mehreren Einheiten darin (d. h. MTP-Gerät, seriellen Gerät, benutzerdefiniertes Gerät) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6b83b-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`<span data-ttu-id="6b83b-171">,</span><span class="sxs-lookup"><span data-stu-id="6b83b-171">,</span></span> `InterfaceList = "MODEM\0MTP"`

<span data-ttu-id="6b83b-172">USBFN Schnittstellen werden in der Registrierung unter dem folgenden Schlüssel aufgezählt:</span><span class="sxs-lookup"><span data-stu-id="6b83b-172">USBFN Interfaces are enumerated in registry under the following key:</span></span>
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

<span data-ttu-id="6b83b-173">Jeder Eintrag der USB-Schnittstelle muss es sich um eine Schnittstelle-Deskriptor-Wert und eine Schnittstelle GUID enthalten.</span><span class="sxs-lookup"><span data-stu-id="6b83b-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="6b83b-174">Auf der Hostseite unterstützen</span><span class="sxs-lookup"><span data-stu-id="6b83b-174">Supporting from the host side</span></span>

<span data-ttu-id="6b83b-175">Wenn ein OEM auswählt (z. B. alle standardmäßige USB-Schnittstelle zu implementieren  Massenspeicher) auf dem Gerät, klicken Sie dann ein Host-PCs können integrierte Windows-Treiber für diese Art von USB-Gerät.</span><span class="sxs-lookup"><span data-stu-id="6b83b-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="6b83b-176">Wenn ein OEM eine beliebige benutzerdefinierte USB-Schnittstelle auf Geräteseite implementiert, ist es erforderlich, für den OEM um einen Windows-Host-Treiber für das benutzerdefinierte Funktion von USB-Gerät zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="6b83b-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
