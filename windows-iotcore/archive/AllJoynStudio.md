---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Weitere Informationen zum Erstellen einer AllJoyn-UWP-App mithilfe der universellen Windows-Plattform (UWP) AllJoyn-APIs und Visual Studio 2017.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513722"
---
> [!NOTE]
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="using-the-alljoyn-studio-extension"></a>Mithilfe der AllJoyn-Studio-Erweiterung

Die [AllSeen Alliance](https://allseenalliance.org/) erstellt AllJoyn, um das Internet der Dinge zu ermöglichen. Windows 10 verfügt über AllJoyn-nativ in die Plattform integriert, sodass Entwickler problemlos AllJoyn "IoT-Enable" Ihren Windows 10-Apps nutzen. In diesem Artikel wird beschrieben, die erforderlichen Schritte zum Erstellen von apps für Windows 10 mithilfe der universellen Windows-Plattform (UWP) AllJoyn-APIs und das Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Erweiterung.

## <a name="understanding-alljoyn-uwp-app-development"></a>Grundlegendes zu AllJoyn-UWP-App-Entwicklung

Drei wesentliche Komponenten bilden AllJoyn-UWP-apps:

1. App-Layout und Entwurf (XAML oder HTML) und Klasse-Komponenten (C#, JavaScript, C++, oder. VB).
2. Der AllJoyn-Kern-APIs: AllJoyn Standard Client API (C) und Windows.Devices.AllJoyn-API (WinRT) in Windows 10-SDKS verfügbar.
3. Eine oder mehrere UWP Windows-Runtime-Komponenten (die generiert dieser Code von AllJoyn-Schnittstellen).

Das folgende Diagramm zeigt die Architektur einer typischen AllJoyn UWP-Projekt:

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

Dass AllJoyn-fähige UWP-apps können entweder Producer sein (zu implementieren und Bereitstellen von Schnittstellen, in der Regel auf einem Gerät), Consumer (verwenden Sie Schnittstellen, die in der Regel apps), oder beides. Consumer und Producer teilen die gleichen Schritte ab, in die Details der Implementierung nur Auseinanderlaufende.

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>Erstellen eine dass AllJoyn-fähige UWP-app

Führen Sie folgende Schritte dass AllJoyn-fähige UWP-apps für Windows 10 entwickeln: (weiter unten in diesem Dokument erläutert)

1. Vorbereiten der Buildumgebung an.
2. Bestimmen Sie, welche AllJoyn Schnittstellen verwendet werden soll, und erhalten oder erforderlichen Introspection XML zu erstellen.
3. Erstellen Sie ein AllJoyn-App-Projekt und wählen Sie dann Introspection-XML und die gewünschten Schnittstellen für die codegenerierung.
4. Implementieren von Producer oder Ponsumer-Code in Ihrer app mithilfe von APIs, die über die generierten UWP-Windows-Runtime-Komponenten verfügbar gemacht.
5. Erstellen Sie Ihre Benutzeroberfläche.

## <a name="preparing-your-build-environment"></a>Vorbereiten der Umgebung erstellen

Die Windows 10-Build und die zugehörigen Tools umfassen alle Ressourcen, die Sie benötigen, dass AllJoyn-fähige UWP-apps zu schreiben.

Hier ist Sie benötigen Folgendes durchführen müssen, bevor Sie beginnen, das Schreiben von Code:

* Installieren Sie [Windows 10](https://www.microsoft.com/windows/) auf einem PC
* Installieren Sie [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (eine Express-Edition nicht verwenden)
* Herunterladen der [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) -Erweiterung von Visual Studio Gallery. 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>Abrufen von Introspection XML für AllJoyn-Schnittstellen

Es gibt drei Möglichkeiten, die Sie die Schnittstellendefinitionen AllJoyn, die Sie benötigen abrufen können, um Ihr Projekt zu starten:

1. Extrahieren der Introspection-XML-Code über AllJoyn Producer in Ihrem Netzwerk zur Laufzeit.
2. Abrufen der Introspection-XML-Dokumentation; Beispiel: [Dokumentation zu Service-Framework (LSF) Beleuchtung](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) von der AllSeen-Allianz.
3. Erstellen Sie Ihr eigenes Introspection-XML, die mit der AllJoyn kompatibel ist /[D-Bus Introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) Format.

Dieser Artikel behandelt die ersten beiden Möglichkeiten – AllJoyn® Studio nativ unterstützt das Netzwerk AllJoyn Producer Abfragen und Extrahieren des XML als auch Introspection XML-Dateien hochladen.  Erfahren Sie, wie zum Erstellen eines eigenen [hier](AllJoynProducer.md).

Ein Toaster dass AllJoyn-fähige Geräte dient wie im Beispiel für diesen Beitrag. Diese Toaster stellt Steuerelemente zum Starten und beenden toasting Zeichenfolge, die Einstellung der "Dunkelheit", und Benachrichtigungen, wenn der Toast Musikwiedergabeliste ist.

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

Der Toaster stellt die folgenden XML-Code:

``` xml
<node name="/toaster">
  <interface name="org.alljoyn.example.Toaster">
    <annotation name="org.alljoyn.Bus.Secure" value="true"/>
    <description language="en">Example interface for controlling a toaster appliance</description>
    <description language="fr">Interface Exemple de commande d'un appareil de grille-pain</description>
    <property name="Version" type="q" access="read">
      <description>Interface version</description>
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="const"/>
    </property>
    <signal name="ToastBurnt" sessioncast="true">
      <description language="en">Toast is burnt</description>
      <description language="fr">Toast est brûlé</description>
    </signal>
    <method name="StartToasting">
      <description language="en">Start toasting</description>
      <description language="fr">Lancer grillage</description>
    </method>
    <method name="StopToasting">
      <description language="en">Stop toasting</description>
      <description language="fr">Arrêtez de grillage</description>
    </method>
    <property name="DarknessLevel" type="y" access="readwrite">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">Toasting darkness level</description>
      <description language="fr">Grillage niveau de l'obscurité</description>
    </property>
  </interface>
</node>
```

## <a name="creating-an-alljoyn-project"></a>Erstellen eines AllJoyn-Projekts

Erstellen Sie ein Projekt wie gewohnt: Klicken Sie auf `File->New->New Project` zu beginnen.

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

Anstelle von Navigieren zu einer Windows-Universal-Vorlage, wählen Sie die Vorlage "AllJoyn-App" für Ihre Zielsprache aus, die mit der Erweiterung installiert wurde.  Benennen Sie Ihr Projekt, und wählen Sie einen Dateispeicherort zum Einstieg in die Entwicklung.

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

Unmittelbar nach der Auswahl einer AllJoyn App Template, fordert Visual Studio Ihnen die Auswahl der AllJoyn-Schnittstellen, Sie in Ihr Projekt einbinden möchten. 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__Extrahieren Schnittstellen, von einem Gerät im Netzwerk__

Wenn Sie Ihr AllJoyn-Gerät oder eine Schnittstelle im Netzwerk nicht finden, führen Sie die [dieses Handbuch](AllJoynTroubleshooting.md) behandeln. 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

Wählen Sie die "Hersteller im Netzwerk" im linken Bereich, zum Abfragen Ihres Netzwerks für den verfügbar gemachten Schnittstellen. Dies findet AllJoyn Hersteller für das Netzwerk und die Liste die Schnittstellen, die sie unterstützen.

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

Wählen Sie die Schnittstellen, die, angegeben in Ihrem Projekt werden sollen.  In diesem Fall sind wir nur die Toaster-Schnittstelle verwenden, also wir einfach die "org.alljoyn.example.Toaster"-Schnittstelle wählen.

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

Die Spalte "Aktionen" beschreibt die ausstehenden Änderungen in das Projekt "Hinzufügen" für neu ausgewählten Schnittstellen angezeigt. Hier haben wir erhalten der Schnittstelle den Anzeigenamen "ToasterLibrary", wodurch die Aktion "Umbenennen" angewendet werden.

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__Laden von XML aus einer Datei__

Wählen Sie eine beliebige Anzahl von Introspection-XML-Dateien über "Durchsuchen", um die enthaltenen Transportadapters finden Sie unter.

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

Navigieren Sie zu, und wählen Sie die entsprechende XML ein (hier verwenden wir toaster.xml).

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

Einmal AllJoyn® Studio lädt das XML, analysiert er die verschiedenen Schnittstellen, und die Beschreibungen enthaltenen, sodass Sie auswählen, welche Schnittstellen, die Sie unterstützen möchten.

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

Die Spalte "Aktionen" beschreibt die ausstehenden Änderungen in das Projekt "Hinzufügen" für neu ausgewählten Schnittstellen angezeigt.

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

Hier haben wir uns entschieden, die Schnittstelle "org.alljoyn.example.Toaster" enthalten und haben, die von dem Anzeigenamen "ToasterLibrary", werden ihm Auslösen der Aktion "Umbenennen" angewendet werden.

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__Hinzufügen und Entfernen von Schnittstellen__

Nach Abschluss dieser Schritte, die generierten Dateien werden automatisch hinzugefügt eine C++ Komponente für Windows-Runtime mit dem Anzeigenamen von oben und als Verweis auf die Anwendung Projekt hinzugefügt.  Der Stamm-Namespace ist jedoch weiterhin die gleichen "org.alljoyn.example.Toaster" als von der Schnittstelle definiert.  Alle Klassen, die Zugriff auf diese Komponenten müssen eine "using"-Klausel für die Komponente des Stammnamespace aufweisen.

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_TIPP: Erstellen Sie jetzt die generierte Komponenten, um die von IntelliSense profitieren._

Nachdem Sie Ihre Lösung AllJoyn-App erstellt haben, können Sie zurückgehen und ändern die Schnittstellen, die Sie verwenden. Klicken Sie auf der Hauptmenüleiste auf "AllJoyn ->-Schnittstellen hinzufügen/entfernen..." um die Schnittstellen-Manager zu starten.

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

Von hier aus können Sie "Durchsuchen..." klicken. Um weitere XML-Dateien hinzufügen, oder heben die vorhandenen Transportadapters. Deaktivieren Sie das Kontrollkästchen einer Benutzeroberfläche Updates die Aktion für "Entfernen", und klicken Sie auf die Schaltfläche "Ok" wird die zugeordnete Windows-Runtime-Komponente aus der Projektmappe entfernt.

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

Betrachten im Projektmappen-Explorer aus, wurde der Windows-Runtime-Komponente entfernt.

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>Nächste Schritte

Wenn AllJoyn-Funktionalität zu implementieren, achten Sie stets einschließen "Windows.Devices.AllJoyn"-Namespace sowie den Namespace über die Schnittstelle, die Sie verwenden möchten.

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__Implementieren einer AllJoyn-Consumers__

Der Code für die Schnittstellen enthält eine Watcher und Consumer-Klasse, die zum Suchen und dann einen Producer steuern verwendet. Die Watcher durch das Erstellen einer neuen AllJoynBusAttachment implementieren, die Watcher mit diesem AllJoynBusAttachment zu initialisieren, registrieren Sie sich für den Watcher Suchen von einem Producer (das "Added"-Ereignis), und Starten der Watcher.

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

Die ToasterWatcher_Added Ereignis wird ausgelöst, wenn der Monitor einen Producer sucht.  Verwenden Sie dieses Ereignis, um einen Consumer zu registrieren. Beachten Sie, dass Visual Studio die erforderlichen Shell-Methode, über die Schnellaktionen generiert wird.

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

Generieren die Methode führt die folgenden Shellcode:

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

Füllen der Shellcode mit der richtigen Logik ermöglicht das Registrieren des Consumers.

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

Beachten Sie, dass dieses Ereignis löst jedes Mal, wenn der Monitor einen Producer ermittelt.  Wenn Sie erwarten, dass mehrere Producer zu finden, behalten eine Datenstruktur des Consumers aus, wenn ein Consumer für jede Producer fallen.

Registrieren von Ereignissen für die verschiedenen Signale der Producer gibt – geänderten Eigenschaft Signale sind direkte Mitglieder der Consumerklasse, aber andere Signale sind Member der Klasse Signale (nur wie zuvor, legen Sie die Schnellaktionen zum Generieren des Shell-Codes für diese Ereignisse).

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

Verwenden Sie das Consumerobjekt, um das Lesen und Schreiben von Eigenschaften als auch Methoden aufrufen.

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>Implementieren ein AllJoyn-Hersteller

__Implementieren des Diensts__

Producer implementieren ein Diensts, die ihre Schnittstellen verfügbar machen.  Um einen Producer zu implementieren, müssen Sie zuerst erstellen Sie eine Klasse für den Dienst.

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

Fügen Sie den Namespace für die Schnittstelle, die "using-Anweisungen aus, und klicken Sie dann erben Sie die textshell-Schnittstelle, die für den Dienst generiert, und verwenden Sie die schnelle Aktion, um die Klasse implementiert.

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

Hier werden die erforderlichen Komponenten die schnelle Aktion ausfüllen.

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

Aller erforderlichen Bestandteile des Codes können funktionieren, aber Sie weiterhin die eigentliche Logik für jeden Aufruf der Methode und Eigenschaft implementieren müssen.

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

Nehmen die SetDarknessLevelAsync als Beispiel an, verwenden wir eine Aufgabe zum Ergebnis Success zu erstellen.  In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

Implementieren Sie den Rest der Methode und Eigenschaft Aufrufe des Diensts fertig zu stellen.

__Implementieren von Producer__

Den Producer-Erstellung ist unkompliziert – erstellen Sie eine neue AllJoynBusAttachment, initialisieren Sie einen Producer mit diesem AllJoynBusAttachment, initialisieren Sie den neu erstellten Dienst für den Hersteller, und starten Sie den Producer.

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

Da der Dienst den Großteil der Logik enthält, werden die wichtigste Funktionen, die zum Implementieren die Signale für eigenschaftenänderungen und diskrete Signale für nicht-Ereignisse zu senden.  Implementieren Sie diese durch Methodenaufrufen nach Bedarf.

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__Weitere Informationen__

Wenn Sie alle Anweisungen in diesem Dokument ordnungsgemäß abgeschlossen haben, können Sie beginnen, dass AllJoyn-Code in Ihrer app zu schreiben.

Zu Referenzzwecken finden Sie zu den Beispielen AllJoyn universelle Windows-Apps auf der Microsoft-Beispiel GitHub [AllJoyn Producer](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) und [AllJoyn Consumer](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).

Schauen Sie für eine ausführliche exemplarische Vorgehensweise zum Erstellen einer app AllJoyn sich die Sitzung AllJoyn 623:

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

Beachten Sie, dass AllJoyn-Kommunikation zwischen zwei UWP-apps auf dem gleichen Computer von der Windows-Richtlinie deaktiviert ist, es sei denn, sie z. B. wenn eine Loopback-Ausnahme aktiviert haben werden direkt aus Visual Studio bereitgestellt.  Ausführliche Anweisungen zum Aktivieren der Loopback-Ausnahme finden Sie unter [hier](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).



