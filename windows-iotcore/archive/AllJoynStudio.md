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
> <span data-ttu-id="beb5a-104">Sie zeigen die archivierte Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="beb5a-104">You are viewing archived documentation.</span></span> <span data-ttu-id="beb5a-105">AllJoyn wird nicht mehr von Windows 10 IoT unterstützt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="beb5a-106">Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="beb5a-107">Mithilfe der AllJoyn-Studio-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="beb5a-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="beb5a-108">Die [AllSeen Alliance](https://allseenalliance.org/) erstellt AllJoyn, um das Internet der Dinge zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="beb5a-109">Windows 10 verfügt über AllJoyn-nativ in die Plattform integriert, sodass Entwickler problemlos AllJoyn "IoT-Enable" Ihren Windows 10-Apps nutzen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="beb5a-110">In diesem Artikel wird beschrieben, die erforderlichen Schritte zum Erstellen von apps für Windows 10 mithilfe der universellen Windows-Plattform (UWP) AllJoyn-APIs und das Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="beb5a-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="beb5a-111">Grundlegendes zu AllJoyn-UWP-App-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="beb5a-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="beb5a-112">Drei wesentliche Komponenten bilden AllJoyn-UWP-apps:</span><span class="sxs-lookup"><span data-stu-id="beb5a-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="beb5a-113">App-Layout und Entwurf (XAML oder HTML) und Klasse-Komponenten (C#, JavaScript, C++, oder. VB).</span><span class="sxs-lookup"><span data-stu-id="beb5a-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="beb5a-114">Der AllJoyn-Kern-APIs: AllJoyn Standard Client API (C) und Windows.Devices.AllJoyn-API (WinRT) in Windows 10-SDKS verfügbar.</span><span class="sxs-lookup"><span data-stu-id="beb5a-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="beb5a-115">Eine oder mehrere UWP Windows-Runtime-Komponenten (die generiert dieser Code von AllJoyn-Schnittstellen).</span><span class="sxs-lookup"><span data-stu-id="beb5a-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="beb5a-116">Das folgende Diagramm zeigt die Architektur einer typischen AllJoyn UWP-Projekt:</span><span class="sxs-lookup"><span data-stu-id="beb5a-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="beb5a-118">Dass AllJoyn-fähige UWP-apps können entweder Producer sein (zu implementieren und Bereitstellen von Schnittstellen, in der Regel auf einem Gerät), Consumer (verwenden Sie Schnittstellen, die in der Regel apps), oder beides.</span><span class="sxs-lookup"><span data-stu-id="beb5a-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="beb5a-119">Consumer und Producer teilen die gleichen Schritte ab, in die Details der Implementierung nur Auseinanderlaufende.</span><span class="sxs-lookup"><span data-stu-id="beb5a-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="beb5a-120">Erstellen eine dass AllJoyn-fähige UWP-app</span><span class="sxs-lookup"><span data-stu-id="beb5a-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="beb5a-121">Führen Sie folgende Schritte dass AllJoyn-fähige UWP-apps für Windows 10 entwickeln: (weiter unten in diesem Dokument erläutert)</span><span class="sxs-lookup"><span data-stu-id="beb5a-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="beb5a-122">Vorbereiten der Buildumgebung an.</span><span class="sxs-lookup"><span data-stu-id="beb5a-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="beb5a-123">Bestimmen Sie, welche AllJoyn Schnittstellen verwendet werden soll, und erhalten oder erforderlichen Introspection XML zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="beb5a-124">Erstellen Sie ein AllJoyn-App-Projekt und wählen Sie dann Introspection-XML und die gewünschten Schnittstellen für die codegenerierung.</span><span class="sxs-lookup"><span data-stu-id="beb5a-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="beb5a-125">Implementieren von Producer oder Ponsumer-Code in Ihrer app mithilfe von APIs, die über die generierten UWP-Windows-Runtime-Komponenten verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="beb5a-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="beb5a-126">Erstellen Sie Ihre Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="beb5a-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="beb5a-127">Vorbereiten der Umgebung erstellen</span><span class="sxs-lookup"><span data-stu-id="beb5a-127">Preparing your Build Environment</span></span>

<span data-ttu-id="beb5a-128">Die Windows 10-Build und die zugehörigen Tools umfassen alle Ressourcen, die Sie benötigen, dass AllJoyn-fähige UWP-apps zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="beb5a-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="beb5a-129">Hier ist Sie benötigen Folgendes durchführen müssen, bevor Sie beginnen, das Schreiben von Code:</span><span class="sxs-lookup"><span data-stu-id="beb5a-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="beb5a-130">Installieren Sie [Windows 10](https://www.microsoft.com/windows/) auf einem PC</span><span class="sxs-lookup"><span data-stu-id="beb5a-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="beb5a-131">Installieren Sie [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (eine Express-Edition nicht verwenden)</span><span class="sxs-lookup"><span data-stu-id="beb5a-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="beb5a-132">Herunterladen der [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) -Erweiterung von Visual Studio Gallery.</span><span class="sxs-lookup"><span data-stu-id="beb5a-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="beb5a-133">Abrufen von Introspection XML für AllJoyn-Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="beb5a-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="beb5a-134">Es gibt drei Möglichkeiten, die Sie die Schnittstellendefinitionen AllJoyn, die Sie benötigen abrufen können, um Ihr Projekt zu starten:</span><span class="sxs-lookup"><span data-stu-id="beb5a-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="beb5a-135">Extrahieren der Introspection-XML-Code über AllJoyn Producer in Ihrem Netzwerk zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="beb5a-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="beb5a-136">Abrufen der Introspection-XML-Dokumentation; Beispiel: [Dokumentation zu Service-Framework (LSF) Beleuchtung](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) von der AllSeen-Allianz.</span><span class="sxs-lookup"><span data-stu-id="beb5a-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="beb5a-137">Erstellen Sie Ihr eigenes Introspection-XML, die mit der AllJoyn kompatibel ist /[D-Bus Introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) Format.</span><span class="sxs-lookup"><span data-stu-id="beb5a-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="beb5a-138">Dieser Artikel behandelt die ersten beiden Möglichkeiten – AllJoyn® Studio nativ unterstützt das Netzwerk AllJoyn Producer Abfragen und Extrahieren des XML als auch Introspection XML-Dateien hochladen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="beb5a-139">Erfahren Sie, wie zum Erstellen eines eigenen [hier](AllJoynProducer.md).</span><span class="sxs-lookup"><span data-stu-id="beb5a-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="beb5a-140">Ein Toaster dass AllJoyn-fähige Geräte dient wie im Beispiel für diesen Beitrag.</span><span class="sxs-lookup"><span data-stu-id="beb5a-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="beb5a-141">Diese Toaster stellt Steuerelemente zum Starten und beenden toasting Zeichenfolge, die Einstellung der "Dunkelheit", und Benachrichtigungen, wenn der Toast Musikwiedergabeliste ist.</span><span class="sxs-lookup"><span data-stu-id="beb5a-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="beb5a-143">Der Toaster stellt die folgenden XML-Code:</span><span class="sxs-lookup"><span data-stu-id="beb5a-143">The toaster exposes the following XML:</span></span>

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

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="beb5a-144">Erstellen eines AllJoyn-Projekts</span><span class="sxs-lookup"><span data-stu-id="beb5a-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="beb5a-145">Erstellen Sie ein Projekt wie gewohnt: Klicken Sie auf `File->New->New Project` zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="beb5a-147">Anstelle von Navigieren zu einer Windows-Universal-Vorlage, wählen Sie die Vorlage "AllJoyn-App" für Ihre Zielsprache aus, die mit der Erweiterung installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="beb5a-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="beb5a-148">Benennen Sie Ihr Projekt, und wählen Sie einen Dateispeicherort zum Einstieg in die Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="beb5a-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="beb5a-150">Unmittelbar nach der Auswahl einer AllJoyn App Template, fordert Visual Studio Ihnen die Auswahl der AllJoyn-Schnittstellen, Sie in Ihr Projekt einbinden möchten.</span><span class="sxs-lookup"><span data-stu-id="beb5a-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__<span data-ttu-id="beb5a-152">Extrahieren Schnittstellen, von einem Gerät im Netzwerk</span><span class="sxs-lookup"><span data-stu-id="beb5a-152">Extracting interfaces from a device on the network</span></span>__

<span data-ttu-id="beb5a-153">Wenn Sie Ihr AllJoyn-Gerät oder eine Schnittstelle im Netzwerk nicht finden, führen Sie die [dieses Handbuch](AllJoynTroubleshooting.md) behandeln.</span><span class="sxs-lookup"><span data-stu-id="beb5a-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="beb5a-155">Wählen Sie die "Hersteller im Netzwerk" im linken Bereich, zum Abfragen Ihres Netzwerks für den verfügbar gemachten Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="beb5a-156">Dies findet AllJoyn Hersteller für das Netzwerk und die Liste die Schnittstellen, die sie unterstützen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="beb5a-158">Wählen Sie die Schnittstellen, die, angegeben in Ihrem Projekt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="beb5a-159">In diesem Fall sind wir nur die Toaster-Schnittstelle verwenden, also wir einfach die "org.alljoyn.example.Toaster"-Schnittstelle wählen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="beb5a-161">Die Spalte "Aktionen" beschreibt die ausstehenden Änderungen in das Projekt "Hinzufügen" für neu ausgewählten Schnittstellen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="beb5a-162">Hier haben wir erhalten der Schnittstelle den Anzeigenamen "ToasterLibrary", wodurch die Aktion "Umbenennen" angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="beb5a-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__<span data-ttu-id="beb5a-164">Laden von XML aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="beb5a-164">Loading an XML from a File</span></span>__

<span data-ttu-id="beb5a-165">Wählen Sie eine beliebige Anzahl von Introspection-XML-Dateien über "Durchsuchen", um die enthaltenen Transportadapters finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="beb5a-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="beb5a-167">Navigieren Sie zu, und wählen Sie die entsprechende XML ein (hier verwenden wir toaster.xml).</span><span class="sxs-lookup"><span data-stu-id="beb5a-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="beb5a-169">Einmal AllJoyn® Studio lädt das XML, analysiert er die verschiedenen Schnittstellen, und die Beschreibungen enthaltenen, sodass Sie auswählen, welche Schnittstellen, die Sie unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="beb5a-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="beb5a-171">Die Spalte "Aktionen" beschreibt die ausstehenden Änderungen in das Projekt "Hinzufügen" für neu ausgewählten Schnittstellen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="beb5a-173">Hier haben wir uns entschieden, die Schnittstelle "org.alljoyn.example.Toaster" enthalten und haben, die von dem Anzeigenamen "ToasterLibrary", werden ihm Auslösen der Aktion "Umbenennen" angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="beb5a-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__<span data-ttu-id="beb5a-175">Hinzufügen und Entfernen von Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="beb5a-175">Adding and Removing Interfaces</span></span>__

<span data-ttu-id="beb5a-176">Nach Abschluss dieser Schritte, die generierten Dateien werden automatisch hinzugefügt eine C++ Komponente für Windows-Runtime mit dem Anzeigenamen von oben und als Verweis auf die Anwendung Projekt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="beb5a-177">Der Stamm-Namespace ist jedoch weiterhin die gleichen "org.alljoyn.example.Toaster" als von der Schnittstelle definiert.</span><span class="sxs-lookup"><span data-stu-id="beb5a-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="beb5a-178">Alle Klassen, die Zugriff auf diese Komponenten müssen eine "using"-Klausel für die Komponente des Stammnamespace aufweisen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_<span data-ttu-id="beb5a-180">TIPP: Erstellen Sie jetzt die generierte Komponenten, um die von IntelliSense profitieren.</span><span class="sxs-lookup"><span data-stu-id="beb5a-180">TIP: Build the generated components now in order to benefit from IntelliSense.</span></span>_

<span data-ttu-id="beb5a-181">Nachdem Sie Ihre Lösung AllJoyn-App erstellt haben, können Sie zurückgehen und ändern die Schnittstellen, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="beb5a-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="beb5a-182">Klicken Sie auf der Hauptmenüleiste auf "AllJoyn ->-Schnittstellen hinzufügen/entfernen..." um die Schnittstellen-Manager zu starten.</span><span class="sxs-lookup"><span data-stu-id="beb5a-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="beb5a-184">Von hier aus können Sie "Durchsuchen..." klicken. Um weitere XML-Dateien hinzufügen, oder heben die vorhandenen Transportadapters.</span><span class="sxs-lookup"><span data-stu-id="beb5a-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="beb5a-185">Deaktivieren Sie das Kontrollkästchen einer Benutzeroberfläche Updates die Aktion für "Entfernen", und klicken Sie auf die Schaltfläche "Ok" wird die zugeordnete Windows-Runtime-Komponente aus der Projektmappe entfernt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="beb5a-187">Betrachten im Projektmappen-Explorer aus, wurde der Windows-Runtime-Komponente entfernt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="beb5a-189">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="beb5a-189">Next Steps</span></span>

<span data-ttu-id="beb5a-190">Wenn AllJoyn-Funktionalität zu implementieren, achten Sie stets einschließen "Windows.Devices.AllJoyn"-Namespace sowie den Namespace über die Schnittstelle, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="beb5a-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__<span data-ttu-id="beb5a-192">Implementieren einer AllJoyn-Consumers</span><span class="sxs-lookup"><span data-stu-id="beb5a-192">Implementing an AllJoyn Consumer</span></span>__

<span data-ttu-id="beb5a-193">Der Code für die Schnittstellen enthält eine Watcher und Consumer-Klasse, die zum Suchen und dann einen Producer steuern verwendet.</span><span class="sxs-lookup"><span data-stu-id="beb5a-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="beb5a-194">Die Watcher durch das Erstellen einer neuen AllJoynBusAttachment implementieren, die Watcher mit diesem AllJoynBusAttachment zu initialisieren, registrieren Sie sich für den Watcher Suchen von einem Producer (das "Added"-Ereignis), und Starten der Watcher.</span><span class="sxs-lookup"><span data-stu-id="beb5a-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="beb5a-196">Die ToasterWatcher_Added Ereignis wird ausgelöst, wenn der Monitor einen Producer sucht.</span><span class="sxs-lookup"><span data-stu-id="beb5a-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="beb5a-197">Verwenden Sie dieses Ereignis, um einen Consumer zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="beb5a-197">Use this event to register a consumer.</span></span> <span data-ttu-id="beb5a-198">Beachten Sie, dass Visual Studio die erforderlichen Shell-Methode, über die Schnellaktionen generiert wird.</span><span class="sxs-lookup"><span data-stu-id="beb5a-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="beb5a-200">Generieren die Methode führt die folgenden Shellcode:</span><span class="sxs-lookup"><span data-stu-id="beb5a-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="beb5a-202">Füllen der Shellcode mit der richtigen Logik ermöglicht das Registrieren des Consumers.</span><span class="sxs-lookup"><span data-stu-id="beb5a-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="beb5a-204">Beachten Sie, dass dieses Ereignis löst jedes Mal, wenn der Monitor einen Producer ermittelt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="beb5a-205">Wenn Sie erwarten, dass mehrere Producer zu finden, behalten eine Datenstruktur des Consumers aus, wenn ein Consumer für jede Producer fallen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="beb5a-206">Registrieren von Ereignissen für die verschiedenen Signale der Producer gibt – geänderten Eigenschaft Signale sind direkte Mitglieder der Consumerklasse, aber andere Signale sind Member der Klasse Signale (nur wie zuvor, legen Sie die Schnellaktionen zum Generieren des Shell-Codes für diese Ereignisse).</span><span class="sxs-lookup"><span data-stu-id="beb5a-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="beb5a-208">Verwenden Sie das Consumerobjekt, um das Lesen und Schreiben von Eigenschaften als auch Methoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="beb5a-210">Implementieren ein AllJoyn-Hersteller</span><span class="sxs-lookup"><span data-stu-id="beb5a-210">Implementing an AllJoyn Producer</span></span>

__<span data-ttu-id="beb5a-211">Implementieren des Diensts</span><span class="sxs-lookup"><span data-stu-id="beb5a-211">Implementing the Service</span></span>__

<span data-ttu-id="beb5a-212">Producer implementieren ein Diensts, die ihre Schnittstellen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="beb5a-213">Um einen Producer zu implementieren, müssen Sie zuerst erstellen Sie eine Klasse für den Dienst.</span><span class="sxs-lookup"><span data-stu-id="beb5a-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="beb5a-215">Fügen Sie den Namespace für die Schnittstelle, die "using-Anweisungen aus, und klicken Sie dann erben Sie die textshell-Schnittstelle, die für den Dienst generiert, und verwenden Sie die schnelle Aktion, um die Klasse implementiert.</span><span class="sxs-lookup"><span data-stu-id="beb5a-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="beb5a-217">Hier werden die erforderlichen Komponenten die schnelle Aktion ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="beb5a-219">Aller erforderlichen Bestandteile des Codes können funktionieren, aber Sie weiterhin die eigentliche Logik für jeden Aufruf der Methode und Eigenschaft implementieren müssen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="beb5a-221">Nehmen die SetDarknessLevelAsync als Beispiel an, verwenden wir eine Aufgabe zum Ergebnis Success zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="beb5a-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span><span class="sxs-lookup"><span data-stu-id="beb5a-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="beb5a-224">Implementieren Sie den Rest der Methode und Eigenschaft Aufrufe des Diensts fertig zu stellen.</span><span class="sxs-lookup"><span data-stu-id="beb5a-224">Implement the rest of the method and property calls to finish the service.</span></span>

__<span data-ttu-id="beb5a-225">Implementieren von Producer</span><span class="sxs-lookup"><span data-stu-id="beb5a-225">Implementing the Producer</span></span>__

<span data-ttu-id="beb5a-226">Den Producer-Erstellung ist unkompliziert – erstellen Sie eine neue AllJoynBusAttachment, initialisieren Sie einen Producer mit diesem AllJoynBusAttachment, initialisieren Sie den neu erstellten Dienst für den Hersteller, und starten Sie den Producer.</span><span class="sxs-lookup"><span data-stu-id="beb5a-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="beb5a-228">Da der Dienst den Großteil der Logik enthält, werden die wichtigste Funktionen, die zum Implementieren die Signale für eigenschaftenänderungen und diskrete Signale für nicht-Ereignisse zu senden.</span><span class="sxs-lookup"><span data-stu-id="beb5a-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="beb5a-229">Implementieren Sie diese durch Methodenaufrufen nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="beb5a-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__<span data-ttu-id="beb5a-231">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="beb5a-231">More Information</span></span>__

<span data-ttu-id="beb5a-232">Wenn Sie alle Anweisungen in diesem Dokument ordnungsgemäß abgeschlossen haben, können Sie beginnen, dass AllJoyn-Code in Ihrer app zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="beb5a-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="beb5a-233">Zu Referenzzwecken finden Sie zu den Beispielen AllJoyn universelle Windows-Apps auf der Microsoft-Beispiel GitHub [AllJoyn Producer](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) und [AllJoyn Consumer](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span><span class="sxs-lookup"><span data-stu-id="beb5a-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="beb5a-234">Schauen Sie für eine ausführliche exemplarische Vorgehensweise zum Erstellen einer app AllJoyn sich die Sitzung AllJoyn 623:</span><span class="sxs-lookup"><span data-stu-id="beb5a-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="beb5a-235">Beachten Sie, dass AllJoyn-Kommunikation zwischen zwei UWP-apps auf dem gleichen Computer von der Windows-Richtlinie deaktiviert ist, es sei denn, sie z. B. wenn eine Loopback-Ausnahme aktiviert haben werden direkt aus Visual Studio bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="beb5a-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="beb5a-236">Ausführliche Anweisungen zum Aktivieren der Loopback-Ausnahme finden Sie unter [hier](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span><span class="sxs-lookup"><span data-stu-id="beb5a-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



