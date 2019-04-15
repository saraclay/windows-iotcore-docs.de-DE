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
# <a name="overview-of-usb-support-and-dual-role"></a>Übersicht über USB-Unterstützung und Dual-Rolle

Ein serieller Bus USB (Universal) bietet eine serielle erweiterbar, hot-Plug-Plug & Play-Schnittstelle, die eine kostengünstige Verbindung für Peripheriegeräte, z. B. Tastaturen, Mäuse, Joysticks, Drucker, Scanner, Speichergeräte, Modems und Video standard stellt sicher Webkonferenzen-Kameras.  
Wenn wir über USB-Geräte sprechen, der USB-funktionsstapel bezieht sich auf eine Gruppe von Treibern, die aufgelistet werden, und der Plug & Play-Manager geladen, und einem zusammengesetzten USB-Gerät kann mehrere Schnittstellen in einer einzelnen Konfiguration unterstützen. Wenngleich die meisten was wir in diesem sprechen Artikel bezieht sich auf die Doppelrolle für USB-2.0, besser bekannt als USB-auf dem laufenden oder USB OTG oder OTG, es ist auch hilfreich zu wissen, über USB 3.0 und wie es USB 2.0 unterscheidet. Die USB OTG definiert zwei Rollen für Geräte: OTG-A-Gerät und OTG-B-Gerät, Netzteile angeben welcher Seite auf die Verknüpfung und ist dem zunächst den Host. Da jeder Controller OTG beide Rollen unterstützt, werden sie häufig "Dual-Rolle" Controller anstelle von "OTG-Controller." bezeichnet USB-3.0 können dagegen auf Geräten in Hosts oder Peripheriegeräte vornehmen. Einige Geräte sind beide Rollen je nach Art am anderen Ende erkannt wird. Diese Arten von Ports werden als Dual-Rolle-Daten (DRD) bezeichnet. Wenn zwei solche Geräte verbunden sind, die Rollen werden nach dem Zufallsprinzip zugewiesen, aber ein Austausch kann von beiden Enden so sein. 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>Architektur der USB-Funktion in Windows 10 IoT Core

Wenn die Windows 10 IoT-Plattform wie USB-Gerät fungiert, wird eine von mehreren Konfigurationen verwendet. Jede Konfiguration verfügt über eine oder mehrere USB-Schnittstellen. Um USB OTG ordnungsgemäß auf Windows 10 IoT zu unterstützen, müssen einige Dinge geregelt werden.  

## <a name="components-oems-have-to-supply"></a>Komponenten OEMs müssen bereitstellen

OEMs müssen Komponenten auf beiden Seiten – für die USB-Gerät-Seite und möglicherweise auch der USB-Hostseite angeben.  

![Stellt für ein OEM-Komponenten](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>OEMs unterstützen für beide Seiten

Alle USB-Gerät verfügt über eindeutige Anbieter-ID und PID, die es zu identifizieren. Ein OEM, muss als Hersteller eines USB-basierte Windows IoT-Geräts, die angeben.  OEMs können gelten für das USB-Consortium und Abrufen von Unternehmens VID (sofern sie noch keine besitzen) und wählen Sie dann eine PID, die für das jeweilige Produkt eindeutig werden. Wenn Windows 10 IoT mit USBFN-Funktionalität auf einem PC verbunden ist fungiert es als USB-Gerät (der alle Funktionen, wählen Sie im myUSBFN.sys gesetzt), mit diesen "VID_nnn" und "PID_NNN". Diese Kombination von Anbieter-ID und die PID wird dann durch den Host-PC zum finden Sie die entsprechenden Treiber (myUSB.sys) geladen. 

![Zusammenkommen, wie USB-Funktionen](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>Unterstützung von der Geräteseite

_Funktionen mit USBFN aktiviert für die Generierung einer Bildvorschau im FFU einschließen_
* Der IoT-Abbildung muss die erforderlichen Pakete, nämlich ufx01000.sys und usbfnclx.sys enthalten. Beide verfügen über das folgende Paket `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`. OEMs müssen ein richtigen "Feature" Tags in ihren XML-Datei verwenden, die alle Funktionen der FFU aufgeführt sind. Z. B. in der Datei BoardTestOEMInput.xml fallen in der folgende Eintrag <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> unter enthalten <Microsoft> ein Abschnitt mit Funktionen. 

_Rollenwechsel für USB-Treiber_
* Für die USB OTG, müssen OEMs Geben Sie den richtigen ACPI-Tabelleneintrag (*MyOTGacpi*) für den Rollenwechsel USB-Treiber und der Treiber selbst (* myURS.sys).

_Treiber für den Speichercontroller USB-Funktion_
* Dies hängt von der Hardware, durch OEMs verwendet. Microsoft stellt die USB-Funktion-Controller-Treiber für zwei gängige USB OTG-Chipsätzen - Synopsys und ChipIdea bereit.
* Wenn ein OEM entscheidet sich für ein anderes USB OTG-Chipsatz verwenden, die OEM-Abhängige muss ihre eigenen USB-Funktion Controller Hardware angeben (*myfunctioncontroller.sys*).

_Function-Klasse für USB-Treiber_
* Mindestens ein USB-Funktion-Klassentreiber muss angegeben werden.
* Dieser Treiber implementiert bestimmte Funktion von USB-Geräts. Es bestimmt, was auf das Gerät angezeigt wird wie auf dem Host aus, auch als It-Administrator tun.
Angenommen, entsteht möglicherweise der Eindruck als seriellen Gerät oder als ein Massenspeichergerät oder ein Gerät vollständig benutzerdefinierten Typ (*myUSBFN.sys*).

_Konfigurieren der USB-Funktion-Gerät_
* Wenn die IoT-Plattform im USB-Gerät-Modus ist, kann es unter einer oder mehreren Konfigurationen ausgeführt werden. Jede Konfiguration verwendet, muss hinzugefügt werden, und seine Eigenschaften müssen angegeben werden.

_Allgemeine Eigenschaften_
* Es gibt gemeinsame Eigenschaften für alle Konfigurationen mit USB-Funktion der IoT-Plattform. Letztlich handelt es sich bis zu den OEM an der standard-USB-Deskriptor-Einträge wie Anbieter-ID, PID, Geräteklasse, DeviceProtocol, Manufacturerer-Zeichenfolge, die Seriennummer usw.
* Diese gemeinsamen Eigenschaften werden in der Registrierung an folgendem Speicherort festgelegt werden: `HKLM\System\ControlSet001\Control\USBFN\default`

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
> Die oben angegebenen Werte werden nur zu Demonstrationszwecken und können nicht in einem Produkt verwendet werden. Die OEM-Abhängige ersetzen diese Platzhalter-Felder mit *Istwerte* in jedem der oben aufgeführten Einträge.

_Pro-Konfigurationseigenschaften_

Konfigurationen werden in einer Registrierung unter folgendem Registrierungsschlüssel gespeichert: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

Es wird standardmäßig eine leere USB-Funktion Standardkonfiguration enthalten in der FFU festgelegt: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

Diese leere standardmäßig führt dazu, die IoT-Plattform als Windows IoT-Gerät für die angezeigt werden, es ist kein Treiber auf dem Host installiert.

![Konfigurationen für USBFN](../media/USB-Support/config-screenshot.png)

Jede Konfiguration muss bestimmte Eigenschaften, z. B. die Liste der Benutzeroberfläche angeben. Die IoT-Plattform kann als USB-Geräte mit unterschiedlichen Konfigurationen verwendet werden, die freigabena von USB-Schnittstellen definiert, die von USB-Gerät, USB-Host bereitgestellt werden.

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

Derzeit ist die ausgewählte Konfiguration, die bei der die hot-USB-Verbindung aktiviert werden: `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_Beispiele für Konfigurationen_

1. Einmalige Konfiguration
   1. Muss mindestens eine Schnittstelle enthalten
   2. Eine standardmäßige Konfiguration kann sein werden.
   3. Wenn auf einem PC verbunden ist, wird die IoT-Plattform wie dieser Typ von USB-Gerät (z. B. Modem oder Speicher) angezeigt.
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`

2. Zusammengesetzte Konfiguration
   1. Enthält eine Liste der Schnittstellen mit zusätzlichen Parametern
   2. Wenn auf einem PC verbunden ist, wird die IoT-Plattform als eine zusammengesetzte USB-Gerät mit mehreren Einheiten darin (d. h. MTP-Gerät, seriellen Gerät, benutzerdefiniertes Gerät) angezeigt.
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`

USBFN Schnittstellen werden in der Registrierung unter dem folgenden Schlüssel aufgezählt:
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

Jeder Eintrag der USB-Schnittstelle muss es sich um eine Schnittstelle-Deskriptor-Wert und eine Schnittstelle GUID enthalten.

### <a name="supporting-from-the-host-side"></a>Auf der Hostseite unterstützen

Wenn ein OEM auswählt (z. B. alle standardmäßige USB-Schnittstelle zu implementieren  Massenspeicher) auf dem Gerät, klicken Sie dann ein Host-PCs können integrierte Windows-Treiber für diese Art von USB-Gerät. Wenn ein OEM eine beliebige benutzerdefinierte USB-Schnittstelle auf Geräteseite implementiert, ist es erforderlich, für den OEM um einen Windows-Host-Treiber für das benutzerdefinierte Funktion von USB-Gerät zu entwickeln. 
