---
title: Dass Alljoyn-Brücke System Device - API-Handbuch
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, wie für die Zuordnung von Bridge Benutzeroberflächenobjekte zu AllJoyn mit einer IAdapter, die den Controller für ein System von einem oder mehreren Geräten, die an den Bus AllJoyn zuordnen darstellt.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 7c928ee0359ba705a4255d309339c48aa8d000a4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513921"
---
> [!NOTE]
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="mapping-bridge-interface-objects-to-alljoyn"></a>Zuordnung Bridge Benutzeroberflächenobjekte, dass AllJoyn

### <a name="i-iadapter"></a>I. IAdapter

Aus der Bridge Perspektive stellt eine IAdapter den Controller für ein System von einem oder mehreren Geräten, die den AllJoyn-Bus zugeordnet.  IAdapter deklariert Schnittstellen erforderlich, die Support-Geräteenumeration, allgemeine Konfiguration und Verwaltung des Anwendungslebenszyklus.  Es wird deklariert, Methoden, die Interaktion mit einem Gerät oder Geräte-Eigenschaften, Methoden und signalisiert wird. 

Um Ihre Geräte, als dass AllJoyn-Dienst verfügbar zu machen, ist es erforderlich, eine konkrete Klasse zu implementieren, die von IAdapter erbt.  Wie jede Schnittstelle implementiert wird, hängt von der Art der die Geräte, die Sie, dass AllJoyn anpassen ab. 

Der Adapter wird angezeigt, auf dem Bus AllJoyn als ein AllJoyn Dienst angekündigt, mit dem folgenden Namen: 

```
<ExposedAdapterPrefix>.DeviceSystemBridge.<AdapterName> 
```

Jeder Adapter macht zwei `com.microsoft.alljoynmanagement.config` Schnittstellen für die Unterstützung Bridge und die Adapter-Konfiguration: 

```
/AdapterConfig 

/BusConfig
```
Die IAdapter Schnittstelle deklariert, bestimmte Eigenschaften, die implementiert werden müssen.  In der folgende Tabelle werden die Eigenschaften und deren AllJoyn Zuordnung beschrieben:

>  IAdapter-Eigenschaft | Beschreibung | Bridge-Zuordnung |
> | :---------------- | :---------- | :------------- |
> | AdapterName       | Modell des Adapters.  Auch das Suffix für angekündigten Namen des Adapters verwendet. (Siehe ExposedAdapterPrefix.) | AllJoyn zu Modellnummer Daten |
> | ExposedAdapterPrefix |Das Präfix verwendet, wenn diese Brücke den angekündigten Namen auf dem Bus AllJoyn zu erstellen.  Der Adapter wird verfügbar gemacht werden, mit dem folgenden Namen: {ExposedAdapterPrefix}. DeviceSystemBridge. {AdapterName}. | Die Anlage AllJoyn-Bus angekündigt, Namen |
> | ExposedApplciationGUID | Eine GUID, gebotenen des Adapters, der diesem Adapter eindeutig identifiziert.  Diese GUID gilt auch für die Daten für alle Geräte, die von diesem Adapter verwaltet.|AllJoyn zu Daten Anwendungs-ID für diesen Adapter und alle Geräte, die von diesem Adapter verfügbar gemacht werden. |
> | ExposedApplicationName | Ein Anzeigename-Name, der von diesem Adapter verfügbar gemacht wird.  Dieser Name gilt auch für alle Geräte, die von diesem Adapter verwaltet. | AllJoyn zu Daten Anwendungsname für diesen Adapter und alle Geräte, die von diesem Adapter verfügbar gemacht werden. |
> | Hersteller | Herstellername des Adapters | AllJoyn zum Daten-Hersteller |
> | Version | Die Softwareversion des Adapters | AllJoyn Daten SW-Version |

#### <a name="iadapterinitialize"></a>IAdapter::Initialize

Initialisiert den Adapter. Dies kann verwendet werden, müssen Sie trotzdem.  Beispielsweise konnte ein Hintergrundthread gestartet werden, um geräteerkennung zu starten.  Dies wird in der Regel auch verwendet, zum Erstellen eines Geräts Eingang und Entfernung Gerätesignale. 

#### <a name="iadaptergetsetconfig"></a>IAdapter::Get/SetConfig

Dieses Paar von Methoden werden verwendet, für den Zugriff auf Konfigurationsdaten des Adapters.  In der Regel werden diese Einstellungen bestehen aus Einstellungen für die Kommunikation, die der Adapter für Geräteenumeration benötigt, jedoch sind sie nicht zu diesem Zweck beschränkt.  

Die Bridge macht die Konfigurationsdaten für Adapter, dass AllJoyn über die Schnittstelle "com.microsoft.alljoynmanagement.config" verfügbar.  Aus Sicht der Bridge adapterkonfigurationseinstellungen Daten sind beliebig und werden mit dem Adapter als einfache Bytearray ausgetauscht.  Intern an den Adapter, können Sie diese Einstellungen wie gewünscht speichern.   

#### <a name="iadapterenumdevices"></a>IAdapter::EnumDevices

Diese Methode bietet die Brücke mit Informationen zu verfügbaren Geräte auf Ihre Bus.  Die Liste der Geräte, die an die Bridge zurückgegeben werden als einzelne AllJoyn-Dienste an den Bus AllJoyn hinzugefügt. 

Eine Liste mit dieser Methode zurückgegeben werden muss, wenn die Enumeration eine IAdapterIoRequest noch nicht abgeschlossen wurde jedoch möglicherweise auch hier zurückgegeben werden.  Dazu wird die Bridge wartet, bis der Adapter die IAdapterIoRequest Geräteenumeration abgeschlossen signalisiert.   
### <a name="ii-iadapterdevice"></a>II. IAdapterDevice

Aus Sicht von der Bridge steht ein Gerät ein Gerät, das, die Adapter-Implementierung, an den Bus AllJoyn als AllJoyn Service verfügbar gemacht werden sollen.  Eigenschaften, Methoden und Signale, die das Gerät an den Bus macht gibt Sie als Ausführender der, aber dies wäre in der Regel eine direkte Zuordnung von Eigenschaften, Methoden und Signalen, die die Geräte oder Geräte grundsätzlich über ihre systemeigenen Kommunikationsnetzwerk verfügbar machen . 

Jede IAdapterDevice ist angekündigt für Alljoyn mit dem folgenden Namen: 

    {ExposedAdapterPrefix}.{AdapterName}.{Name} 

Jedes Gerät stellt eine einzelne Alljoyn-Schnittstelle verfügbar zu machen, alle Eigenschaften, die Methode und die Signale, die vom Gerät gekapselt.  Der Name der Alljoyn-Schnittstelle ist: 

    {ExposedAdapterPrefix}.{AdapterName}.{Name}.MainInterface 

Ähnlich wie ein IAdapter, ist jede IAdapterDevice erforderlich, um Eigenschaften zu implementieren, die die Bridge verwendet, um Ihr Gerät AllJoyn verfügbar zu machen.  Die folgende Tabelle beschreibt jede Eigenschaft, und wie die Brücke AllJoyn zugeordnet. 

> | IAdapterDevice-Eigenschaft | Beschreibung | Bridge-Zuordnung |
> | :---------------------- | :---------- | :------------- |
> | ControlPanelHandler     | Eine Steuerelement-Bereich, der dieses Gerät ausgeführt werden kann. | Als ein org.alljoyn.ControlPanel.ControlPanel unter einem /ControlPanel-Bus-Objekt verfügbar gemacht werden |
> | Beschreibung             | Eine Beschreibung dieses Geräts. | AllJoyn zur Datenbeschreibung |
> | FirmwareVersion         | Softwareversion dieses Geräts | AllJoyn zum Daten-Firmwareversion |
> | Icon                    | Ein Symbol, der dieses Gerät, dass Alljoyn verfügbar macht. Dies ist null, wenn kein Symbol vorhanden ist. |     Als eine standardmäßige AllJoyn-zu-Symbol verfügbar gemacht werden |
> | Methoden                 | Dies ist der Satz alle Methoden, die Ihr Gerät AllJoyn zur Verfügung stellt. | Dies kann leer sein, wenn keine Methoden vorhanden sind. Als Methoden, die unter der MainInterface mit dem Namen der jeweiligen Methode verfügbar gemacht werden. Nicht eindeutige Namen werden mit einer eindeutigen ID angefügt. |
> | Modell                   | Modell für dieses Gerät | Anzahl der AllJoyn-Bus-Datenmodell |
> | Name                      | Der Name dieses Geräts AllJoyn zu Gerätename Daten. | Dies wird auch für das Suffix für diese angekündigte Gerätenamen verwendet: {ExposedAdapterPrefix}. {AdapterName}. {Name} |
> | Eigenschaften              | Dies ist der Satz aller Eigenschaften, die Ihr Gerät, dass AllJoyn verfügbar macht. Dies kann leer, wenn es sind keine Eigenschaften, aber wenn dies nicht leer ist, und klicken Sie dann mindestens ein Signal, das Signal für die Änderung der Wert muss auch unterstützt werden. | Finden Sie unter IProperty |
> | SerialNumber            | Die Seriennummer von diesem Gerät | AllJoyn über Daten-Seriennummer |
> | Signale                 | Dies ist der Satz von alle Signale, die dieses Gerät, dass AllJoyn verfügbar macht. | Verfügbar gemacht werden, als dass AllJoyn-Signale |
> | Hersteller                  | Herstellername dieses Geräts | AllJoyn zum Daten-Hersteller |
> | Version                 | Softwareversion dieses Geräts | AllJoyn Daten SW-Version |


### <a name="iii-iadapterproperty"></a>III. IAdapterProperty

Aus Sicht von der Bridge stellt eine IAdapterProperty eine Auflistung von verknüpften Daten-Werte, die Sie dem Adapter Implementierer selbst, an den Bus AllJoyn für ein bestimmtes Gerät verfügbar machen möchten.  Jede Eigenschaft enthält einen Satz von ein oder mehrere IAdapterValues.  Jede IAdapterValue stellt eine einzelne Einheit von Daten, die von einem Client AllJoyn zugegriffen werden können.     

Jede IAdapterProperty wird wie folgt, dass Alljoyn als ein Bus-Objekt, mit dem Schnittstellennamen angekündigt: 

    /{PropertyName} 

    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName} 

Alternativ kann der Schnittstellenname durch die Eigenschaft auf eine bestimmte Schnittstellentyp zuordnen überschrieben werden.  In diesem Fall wird der Name der IAdapterProperty wie folgt als ein Bus-Objekt, mit dem Schnittstellennamen angekündigt: 

    /{PropertyName} 

    {InterfaceHint} 

> | IAdapterProperty-Eigenschaften |   Beschreibung                        | Bridge-Zuordnung |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Attribute                |Sammlung von IAdapterAttributes    | Dass AllJoyn-Eigenschaften (Siehe IAdapterValue) |
> | InterfaceHint | Eine Überschreibung für diese Eigenschaft, die verwendet werden kann, um diese Eigenschaft zu einem anderen bekannten Schnittstellentyp zuzuordnen.  Zurückgeben Sie null, um das Standardverhalten verwenden | Dass AllJoyn-Interface-Name für diese Eigenschaft, die (falls angegeben) |
> | Name | Name der Eigenschaft | Dass AllJoyn-Eigenschaft |

### <a name="v-iadaptervalue"></a>V. IAdapterValue

Jede IAdapterValue wird als untergeordnetes Element einer AllJoyn-Eigenschaft mit dem folgenden Namen von Bus-Objekt und die Schnittstelle zur Verfügung gestellt:

    /{PropertyName}/{ValueName}
    
    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName}.{ValueName}

> | IAdapterValue-Eigenschaften    | Beschreibung                        | Bridge-Zuordnung                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Daten                          | Der tatsächliche Datenwert, eine Eigenschaft in einem Überbrückte Gerät.| Eine AllJoyn-Eigenschaft|
> | Name                        | Name des Werts                      | Name einer AllJoyn-Eigenschaft|

### <a name="iv-iadaptersignal"></a>IV. IAdapterSignal

Aus Sicht von der Bridge stellt eine ISignal ein Ereignis, das Ihr Gerät auslösen kann, wenn sich etwas ändert.  Alle Geräte verfügen in der Regel ein Ändern des Wert-Signal an.  Dieses Signal Warnungen AllJoyn-Clients, die eine oder mehrere Eigenschaften auf einem Gerät geändert haben. Zusätzliche Signale werden möglicherweise auch unterstützt.

Jede ISignal wird als gehosteten Sitzung Signal für ein Gerät mit der Signale Name, dass AllJoyn angekündigt.  
Die folgenden Eigenschaften müssen für eine ISignal implementiert werden

> | ISignal-Eigenschaften          | Beschreibung                        | Bridge-Zuordnung                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Name                          |Name des Signals                      | AllJoyn Signal |
> | params | Ein Satz von Objekten, die geändert und deren neue Werte oder Null, wenn dies eine reine Signal ist. | Zuordnungen, die ein Array von Alljoyn Signal Argumenten übergeben, die das Signal. |
