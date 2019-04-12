---
title: Problembehandlung für AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, so dass AllJoyn-Technologie, die mithilfe dieses umfassenden Handbuchs deckt die bekannten Probleme und Problembehandlung von Einstellungen zu beheben.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512481"
---
> [!NOTE]
> <span data-ttu-id="4e914-104">Sie zeigen die archivierte Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="4e914-104">You are viewing archived documentation.</span></span> <span data-ttu-id="4e914-105">AllJoyn wird nicht mehr von Windows 10 IoT unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4e914-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="4e914-106">Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.</span><span class="sxs-lookup"><span data-stu-id="4e914-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-troubleshooting"></a><span data-ttu-id="4e914-107">Problembehandlung für AllJoyn</span><span class="sxs-lookup"><span data-stu-id="4e914-107">AllJoyn Troubleshooting</span></span>

<span data-ttu-id="4e914-108">[AllJoyn](https://allseenalliance.org/developers/learn) ist eine Technologie, ermöglicht IoT-Geräten und Anwendungen erkennen und miteinander interagieren.</span><span class="sxs-lookup"><span data-stu-id="4e914-108">[AllJoyn](https://allseenalliance.org/developers/learn) is a technology that enables IoT devices and applications to discover and interact with each other.</span></span> <span data-ttu-id="4e914-109">Da AllJoyn in Windows 10 und Windows 10 SDK integriert ist, ist es einfach, dass AllJoyn mit der universellen Windows-Plattform (UWP) zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="4e914-109">Since AllJoyn is built into Windows 10 and the Windows 10 SDK, it's easy to take advantage of AllJoyn using the Universal Windows Platform (UWP).</span></span>

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

<span data-ttu-id="4e914-111">In diesem Blogbeitrag können Sie konfigurieren, dass AllJoyn und der Geräte und auch Schritte zur Problembehandlung befolgt werden, wenn etwas nicht wie erwartet funktioniert.</span><span class="sxs-lookup"><span data-stu-id="4e914-111">This blog post will help you configure your AllJoyn network and devices, and also provide troubleshooting steps to follow when things don't work as expected.</span></span> <span data-ttu-id="4e914-112">Der primäre Fokus dieses Artikels wird die Kommunikation zwischen UWP AllJoyn-Client-apps (AllJoyn Verbraucher) und dass AllJoyn-Geräten (AllJoyn Producer) aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-112">The primary focus of this article will be enabling communication between UWP AllJoyn client apps (AllJoyn consumers) and AllJoyn devices (AllJoyn producers).</span></span> <span data-ttu-id="4e914-113">Viele der gleichen Konfigurationsschritte sind erforderlich, um die Kommunikation mit AllJoyn-Producer UWP-apps zu ermöglichen, aber weitere Details zu zukünftigen Blogbeiträge und Artikel bleiben werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-113">Many of the same configuration steps are required to enable communication with UWP AllJoyn Producer apps, but further details will be left to future blog posts and articles.</span></span>

### <a name="app-development-checklist"></a><span data-ttu-id="4e914-114">App-Development-Prüfliste</span><span class="sxs-lookup"><span data-stu-id="4e914-114">App Development Checklist</span></span>

<span data-ttu-id="4e914-115">Wenn Sie für Windows 10 UWP-apps schreiben, sollten Sie sicherstellen, dass:</span><span class="sxs-lookup"><span data-stu-id="4e914-115">If you are writing UWP apps for Windows 10, you should make sure that:</span></span>

1. <span data-ttu-id="4e914-116">Sie haben die Funktion "AllJoyn" in Ihrer app-Manifest (Hinweis zur Groß-und Kleinschreibung) deklariert.</span><span class="sxs-lookup"><span data-stu-id="4e914-116">You've declared the 'allJoyn' capability in your app's manifest (note casing).</span></span>
2. <span data-ttu-id="4e914-117">Sie haben die spezifische Architektur ausgewählt, die das Ziel sein müssen.</span><span class="sxs-lookup"><span data-stu-id="4e914-117">You've selected the specific architecture that you'll be targeting.</span></span> <span data-ttu-id="4e914-118">(In einigen Fällen erforderlich, weil es sich bei Windows-Runtime-Komponenten mit "Any CPU" nicht erstellt werden können, erstellt ein bekanntes Problem mit einigen Visual Studio 2017).</span><span class="sxs-lookup"><span data-stu-id="4e914-118">(Required in some cases because Windows Runtime Components cannot be built using 'Any CPU', a known issue with some Visual Studio 2017 builds).</span></span>

<span data-ttu-id="4e914-119">Wenn Sie eine app oder Gerät Software, die sich nicht um eine UWP-basierte Anwendung für Windows 10 ist schreiben, prüfen Sie die folgende Checkliste zum Sicherstellen der Kompatibilität mit AllJoyn unter Windows 10:</span><span class="sxs-lookup"><span data-stu-id="4e914-119">If you are writing an app or device software that is not a UWP-based application for Windows 10, you should review the following checklist to ensure compatibility with AllJoyn in Windows 10:</span></span>

1. <span data-ttu-id="4e914-120">Wenn einen Producer zu implementieren, stellen sicher, dass die Info-Schnittstelle und Info-basierte Ankündigung/Discovery verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-120">If implementing a Producer, ensure that the About interface and About-based advertisement/discovery are being used.</span></span> <span data-ttu-id="4e914-121">Die Info-Schnittstelle ist [dokumentiert, die auf der Website AllSeen Alliance](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span><span class="sxs-lookup"><span data-stu-id="4e914-121">The About interface is [documented at the AllSeen Alliance website](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span></span>
2. <span data-ttu-id="4e914-122">Verwenden Sie für optimale Ergebnisse die 15.04 AllJoyn Codebasis, verfügbar in der [Codedownloads](https://allseenalliance.org/developers/download) der AllSeen Alliance-Website.</span><span class="sxs-lookup"><span data-stu-id="4e914-122">For best results, use the 15.04 AllJoyn code base, available in the [downloads section](https://allseenalliance.org/developers/download) of the AllSeen Alliance website.</span></span>

### <a name="network-setup-and-troubleshooting"></a><span data-ttu-id="4e914-123">Netzwerkeinrichtung und Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="4e914-123">Network Setup and Troubleshooting</span></span>

<span data-ttu-id="4e914-124">Dass AllJoyn-Geräte in der Lage, um zu ermitteln und miteinander interagieren müssen die Netzwerkkonfiguration und die Einstellungen für jedes Gerät Folgendes erfüllen:</span><span class="sxs-lookup"><span data-stu-id="4e914-124">For AllJoyn devices to be able to discover and interact with each other, the network configuration and settings for each device must satisfy the following:</span></span>

1. <span data-ttu-id="4e914-125">Alle AllJoyn-Geräte, die mit dem gleichen Netzwerk verbunden sind, und Sie werden im gleichen Subnetz.</span><span class="sxs-lookup"><span data-stu-id="4e914-125">All AllJoyn devices are connected to the same network, and are on the same subnet.</span></span>
2. <span data-ttu-id="4e914-126">Windows 10 PC: "Suchen, Geräte und Inhalte" ist für das Netzwerk mit AllJoyn aktiviert (gilt nicht für Phone).</span><span class="sxs-lookup"><span data-stu-id="4e914-126">Windows 10 PC: "Find devices and content" is enabled for the network in use with AllJoyn (does not apply for Phone).</span></span>

<span data-ttu-id="4e914-127">Auf einem PC können Sie die Ablaufverfolgung-Route-Befehl über eine cmd- oder PowerShell-Fenster um zu überprüfen, ob eine andere Computer/Gerät sich im gleichen Subnetz wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4e914-127">On a PC you can use the trace route command from a CMD or PowerShell window to check if another machine/device is on the same subnet as follows:</span></span>

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

<span data-ttu-id="4e914-128">Die erste Zahl Ausgabe hier ist die Anzahl der Hops, und da dieser Wert "1" ist. Dies bedeutet, dass beide Computer im gleichen Subnetz befinden.</span><span class="sxs-lookup"><span data-stu-id="4e914-128">The first number output here is the number of hops, and since that value is "1" it means that both machines are on the same subnet.</span></span>

<span data-ttu-id="4e914-129">Im folgenden finden Sie ein Beispiel für eine typische AllJoyn netzwerkeinrichtung.</span><span class="sxs-lookup"><span data-stu-id="4e914-129">Below is an example of a typical AllJoyn network setup.</span></span> <span data-ttu-id="4e914-130">In diesem Beispiel wäre aller angezeigten Geräte ermitteln und interagieren untereinander über AllJoyn, vorausgesetzt, dass sich diese im gleichen Subnetz befinden.</span><span class="sxs-lookup"><span data-stu-id="4e914-130">In this example, all of the devices shown would be able to discover and interact with each other using AllJoyn assuming they were on the same subnet.</span></span>

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

<span data-ttu-id="4e914-132">Wenn Sie Ihre Windows 10-PCs mit AllJoyn-Geräten mit dem Netzwerk verbinden, müssen Sie auf "Ja" klicken, wenn ein Dialogfeld in Bezug auf das Suchen nach Geräten und PCs im Netzwerk angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4e914-132">When you connect your Windows 10 PC to the network with AllJoyn devices, you'll need to click "Yes" if a dialog is displayed regarding finding devices and PCs on the network.</span></span> <span data-ttu-id="4e914-133">(Anmerkung: Dies gilt nicht, wenn Netzwerke von Windows 10 Phone verknüpfen, wie es kein solcher Dialogfeld ist).</span><span class="sxs-lookup"><span data-stu-id="4e914-133">(Note: This does not apply when joining networks from Windows 10 Phone as there is no such dialog).</span></span>

<span data-ttu-id="4e914-134">Sie können diese Einstellung auf der Seite "Erweiterte Einstellungen" im WLAN-Einstellungen auch dann verwalten, wie hier gezeigt: (auf dieser Seite möglicherweise geringfügig je nachdem welche Windows 10 Insider-Builds, die Sie verwenden)</span><span class="sxs-lookup"><span data-stu-id="4e914-134">You can also manage this setting in the "Advanced Settings" page in Wi-Fi settings as shown here: (this page may look slightly different depending on which Windows 10 Insider build you are using)</span></span>

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

<span data-ttu-id="4e914-136">Die Umschaltfläche "Find-Geräte und Inhalt" sollte in der Position "Auf" um AllJoyn-Funktionalität zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4e914-136">The toggle for "Find devices and content" should be in the "On" position in order to enable AllJoyn functionality.</span></span>

<span data-ttu-id="4e914-137">Für die vorhandenen Netzwerkverbindungen können Sie problemlos überprüfen, ob diese Option ordnungsgemäß konfiguriert ist, indem Sie "Get-NetConnectionProfile" Powershell-Cmdlet ausführen.</span><span class="sxs-lookup"><span data-stu-id="4e914-137">For existing network connections, you can easily validate whether this option is configured properly by running the "Get-NetConnectionProfile" Powershell cmdlet .</span></span> <span data-ttu-id="4e914-138">(Beachten Sie, dass dies nicht für Windows 10 Phone gilt.)</span><span class="sxs-lookup"><span data-stu-id="4e914-138">(Note that this does not apply for Windows 10 Phone).</span></span>

<span data-ttu-id="4e914-139">Get-NetConnectionProfile-Beispielausgabe:</span><span class="sxs-lookup"><span data-stu-id="4e914-139">Example Get-NetConnectionProfile output:</span></span>

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


<span data-ttu-id="4e914-140">Ist der Wert "-NetworkCategory" auf "Private" (siehe oben), dies bedeutet, dass Sie eine richtig konfigurierte haben Ihre Netzwerkverbindung für AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="4e914-140">If the "NetworkCategory" value is "Private" (as shown above), this indicates that you have a properly configured your network connection for AllJoyn.</span></span>

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a><span data-ttu-id="4e914-141">Informationen zu Ankündigungen und Problembehandlung bei der Ermittlung mit Getajxml.exe</span><span class="sxs-lookup"><span data-stu-id="4e914-141">About Advertisement and Troubleshooting Discovery with Getajxml.exe</span></span>

<span data-ttu-id="4e914-142">AllJoyn Producer Geräte oder dass AllJoyn Windows 10-UWP-apps-apps erkannt werden muss über-basierte Ermittlung ordnungsgemäß implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-142">For AllJoyn producer devices or apps to be discoverable by Windows 10 UWP AllJoyn apps, About-based discovery must be properly implemented.</span></span> <span data-ttu-id="4e914-143">Dies kann problemlos mit dem Tool GetAjXml.exe überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-143">This can be easily verified with the GetAjXml.exe tool.</span></span> <span data-ttu-id="4e914-144">Zum Herunterladen und Verwendungsinformationen, die im Zusammenhang mit GetAjXml.exe zu suchen, sehen Sie sich [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span><span class="sxs-lookup"><span data-stu-id="4e914-144">To find download and usage information related to GetAjXml.exe, check out [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span></span>

<span data-ttu-id="4e914-145">Das folgende Beispiel zeigt GetAjXml.exe-Ausgabe für eine Beispiel-Gerät, das zur-basierte Ermittlung unterstützt:</span><span class="sxs-lookup"><span data-stu-id="4e914-145">The following shows GetAjXml.exe output for an example device that supports About-based discovery:</span></span>

    ----------------------------------------------------------------------
    Discovery   : About Announcement
    Manufacturer: Microsoft
    Model #     : 070773
    Device Name : Raspberry Pi Toaster
    Device ID   : 41d9a124-6913-40c5-a20a-9d1b20f8121b
    App Name   : Toaster Producer
          Bus Name                       Port Object Path
          ============================== ===== ===============================
          :3yZG_wu1.2                       25 /emergency
          :3yZG_wu1.2                       25 /info
          :3yZG_wu1.2                       25 /notificationDismisser
          :3yZG_wu1.2                       25 /notificationProducer
          :3yZG_wu1.2                       25 /toaster
          :3yZG_wu1.2                       25 /warning


<span data-ttu-id="4e914-146">Im obigen Beispiel da `Discovery   : About Announcement` enthalten war in dieser Ausgabe ist wird dieser AllJoyn-Hersteller von Windows 10 AllJoyn UWP-apps erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-146">In the above example, since `Discovery   : About Announcement` was included in this output, this AllJoyn producer will be discoverable by Windows 10 AllJoyn UWP apps.</span></span> <span data-ttu-id="4e914-147">Wenn Sie diese Ausgabe für einen bestimmten AllJoyn-Hersteller nicht angezeigt wird, müssen Sie die Discovery-Implementierung auf dem Gerät (Producer) untersuchen.</span><span class="sxs-lookup"><span data-stu-id="4e914-147">If you don't see this output for a particular AllJoyn producer, you will need to investigate the discovery implementation on the device (Producer) side.</span></span>

### <a name="advanced-troubleshooting-with-etw-log-output"></a><span data-ttu-id="4e914-148">Erweiterte Problembehandlung mit ETW-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="4e914-148">Advanced Troubleshooting with ETW Log Output</span></span>

<span data-ttu-id="4e914-149">Ereignisablaufverfolgung für Windows (ETW) können Sie erweiterte Debuginformationen für viele andere Features in Windows.</span><span class="sxs-lookup"><span data-stu-id="4e914-149">Event Tracing for Windows (ETW) can help you get advanced debugging information for many different features in Windows.</span></span> <span data-ttu-id="4e914-150">Zum Glück ist AllJoyn, eine der Funktionen mit ETW-Protokollierung-Unterstützung, damit in diesem Abschnitt ich Ihnen zeige ETW-Protokollierung für AllJoyn zu aktivieren, und wie Sie die Protokolle zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4e914-150">Fortunately AllJoyn is one of the features with ETW logging support, so in this section I'll show you how to enable ETW logging for AllJoyn, and how to access logs.</span></span>

1. <span data-ttu-id="4e914-151">Starten der Ereignisanzeige durch Eingabe von "Ereignisprotokolle" in das Suchtextfeld Menü "Start", "Ereignisprotokolle anzeigen" auswählen.</span><span class="sxs-lookup"><span data-stu-id="4e914-151">Launch the Event Viewer by typing "Event Logs" into the Start Menu search textbox, select "View Event Logs".</span></span>
2. <span data-ttu-id="4e914-152">Stellen Sie sicher, dass "Zeigen analytische und Debugprotokolle" aktiviert ist, klicken Sie im Menü "Ansicht".</span><span class="sxs-lookup"><span data-stu-id="4e914-152">In the "View" menu, ensure that "Show Analytic and Debug Logs" is checked.</span></span>
3. <span data-ttu-id="4e914-153">Navigieren der Strukturansicht im linken Navigationsbereich auf "Anwendungen und Dienste Protokolle > Microsoft > Windows > AllJoyn" in der Ordneransicht und der debugkanal und den Betriebskanal aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4e914-153">Navigate the tree view in the left navigation to "Applications and Services Logs > Microsoft > Windows > AllJoyn" in the folder view, and enable both the Debug channel and the Operational channel.</span></span> <span data-ttu-id="4e914-154">(Siehe rotes Kästchen im folgenden Screenshot).</span><span class="sxs-lookup"><span data-stu-id="4e914-154">(see red box in screenshot below).</span></span>
4. <span data-ttu-id="4e914-155">Reproduzieren Sie das Problem, das Sie mit AllJoyn auftreten.</span><span class="sxs-lookup"><span data-stu-id="4e914-155">Reproduce the problem that you are experiencing with AllJoyn.</span></span>
5. <span data-ttu-id="4e914-156">Klicken Sie auf der Leiste der richtigen "Aktionen" auf "Aktualisieren", und suchen Sie das Betriebsereignisprotokoll und das Debuggen Kanäle in der linken Navigationsleiste unter dem Ordner "AllJoyn".</span><span class="sxs-lookup"><span data-stu-id="4e914-156">Click on "Refresh" in the right "Actions" bar, then check the Operational and Debug channels from the left navigation bar under the "AllJoyn" folder.</span></span>

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

<span data-ttu-id="4e914-158">AllJoyn-ETW-ablaufverfolgungen werden wie folgt partitioniert:</span><span class="sxs-lookup"><span data-stu-id="4e914-158">AllJoyn ETW traces are partitioned as follows:</span></span>

- <span data-ttu-id="4e914-159">Debug-Kanal: Ausführliche, nicht-Fehler/nur zu Informationszwecken ablaufverfolgungen</span><span class="sxs-lookup"><span data-stu-id="4e914-159">Debug channel: Verbose, non-error/informational traces</span></span>
- <span data-ttu-id="4e914-160">Betriebskanal: Fehlerablaufverfolgungen, Fehler werden nur die Ausgabe auf den Betriebskanal</span><span class="sxs-lookup"><span data-stu-id="4e914-160">Operational channel: Error traces, errors are only output on the operational channel</span></span>

<span data-ttu-id="4e914-161">Um Informationen über ETW-Einträge zu extrahieren, können Sie mit der rechten Maustaste auf einen Eintrag in der Listenansicht für einen bestimmten Kanal, und wählen Sie dann auf "Kopieren" und klicken Sie dann auf "Details als Text kopieren".</span><span class="sxs-lookup"><span data-stu-id="4e914-161">In order to extract information from ETW entries, you can right-click on an entry in the list view for a given channel, and then select "Copy" and then "Copy Details as Text".</span></span> <span data-ttu-id="4e914-162">Wenn Sie dann den entsprechenden Text in einem Text-Editor einfügen, müssen Sie die Details, wie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4e914-162">If you then paste the corresponding text into a text editor, you'll have detail like the example below:</span></span>


    Log Name:       Microsoft-Windows-AllJoyn/Operational
    Source:         Microsoft-Windows-AllJoyn
    Date:           6/1/2015 3:57:45 PM
    Event ID:     2
    Task Category: AJ
    Level:         Error
    Keywords:      (70368744177664),AJ
    User:         LOCAL SERVICE
    Computer:       <computer name>
     
    Description:
    AllJoyn encountered an error 0x902D in module UDP, file ..\udptransport.cc, at line number 10809. See the event user data for more information.
    Event Xml:
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
    <System>
       <Provider Name="Microsoft-Windows-AllJoyn" Guid="{2ED299D2-2F6B-411D-8D15-F4CC6FDE0C70}" />
        <EventID>2</EventID>
        <Version>0</Version>
        <Level>2</Level>
        <Task>1</Task>
        <Opcode>10</Opcode>
        <Keywords>0x8000400000000001</Keywords>
       <TimeCreated SystemTime="2015-06-01T22:57:45.626729500Z" />
        <EventRecordID>16</EventRecordID>
       <Correlation />
       <Execution ProcessID="1392" ThreadID="5768" />
       <Channel>Microsoft-Windows-AllJoyn/Operational</Channel>
        <Computer>computer name</Computer>
       <Security UserID="SID" />
    </System>
    <UserData>
       <AJErrorData xmlns="http://manifests.microsoft.com/win/2005/08/windows/alljoyn/events">
           <QStatus>0x902d</QStatus>
           <Message>UDPTransport::DisbleDiscovery(): Not running or stopping; exiting</Message>
           <Module>UDP</Module>
           <File>..\udptransport.cc</File>
           <Line>10809</Line>
        </AJErrorData>
    </UserData>
    </Event>


<span data-ttu-id="4e914-163">Diese Informationen können helfen, dass AllJoyn Probleme aufzuspüren, und Unterstützung beim Melden von Problemen an Microsoft oder anderen Partnern ins Detail.</span><span class="sxs-lookup"><span data-stu-id="4e914-163">This information can help track down AllJoyn issues, or assist in providing detail when reporting issues to Microsoft or other partners.</span></span> <span data-ttu-id="4e914-164">Erfahren Sie mehr über [-ETW-ablaufverfolgungen und der Ereignisanzeige auf MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span><span class="sxs-lookup"><span data-stu-id="4e914-164">You can learn more about [ETW traces and the Event Viewer on MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span></span>

### <a name="known-issues-and-limitations"></a><span data-ttu-id="4e914-165">Bekannte Probleme und Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="4e914-165">Known Issues and Limitations</span></span>

<span data-ttu-id="4e914-166">Standardmäßig Einschränkungen für AllJoyn unter Windows 10:</span><span class="sxs-lookup"><span data-stu-id="4e914-166">By-Design limitations for AllJoyn in Windows 10:</span></span>

- <span data-ttu-id="4e914-167">Der AllJoyn-Router-Knoten ist kein von AllJoyn-Geräten oder apps im Netzwerk automatisch gestarteten Wenn keine apps auf Windows 10-PC ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4e914-167">The AllJoyn Router Node is not auto-started by AllJoyn devices or apps on the network when no apps are running on the Windows 10 PC.</span></span> <span data-ttu-id="4e914-168">Den Knoten für Windows 10-Router kann aus einer Eingabeaufforderung mit erhöhten Rechten oder Powershell-Sitzung gestartet werden, indem Sie den Befehl "net Start Ajrouter" ausführen.</span><span class="sxs-lookup"><span data-stu-id="4e914-168">The Windows 10 Router Node can be started from an elevated command prompt or Powershell session by running the command "net start ajrouter".</span></span>
- <span data-ttu-id="4e914-169">AllJoyn-UWP-apps nicht anzeigen oder interagieren mit anderen AllJoyn-UWP-apps oder dass AllJoyn-desktop-apps, die auf dem gleichen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4e914-169">AllJoyn UWP apps can't discover or interact with other AllJoyn UWP apps or AllJoyn desktop apps running on the same machine.</span></span> <span data-ttu-id="4e914-170">Dies ist ein Teil der app-Isolation Zusicherung, die für UWP-apps unter Windows 10 implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="4e914-170">This is a part of the app isolation promise that is implemented in Windows 10 for UWP apps.</span></span> 
  - <span data-ttu-id="4e914-171">Wenn Sie eine AllJoyn UWP-app aus Visual Studio bereitstellen, wird app-Isolation Isolierung für die app umgangen (Dies ist eine Ausnahme"Loopback" bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="4e914-171">If you deploy an AllJoyn UWP app from Visual Studio, app isolation app isolation is bypassed for that app (this is called a "loopback exemption ").</span></span> <span data-ttu-id="4e914-172">Jede UWP-app, die in Visual Studio bereitgestellt wird werden ermitteln und mit anderen Loopback-Ausnahme für UWP-apps und desktop-apps interagieren, solange diese apps über basierende Ankündigung/Discovery verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e914-172">Each UWP app that is deployed from Visual Studio will be able to discover and interact with other loopback-exempt UWP apps and desktop apps as long as those apps use About-based advertisement/discovery.</span></span> <span data-ttu-id="4e914-173">Wenn Sie Windows 10 IoT Core im "Eingebetteten Modus" ausführen, diese Loopback-Ausnahme automatisch angewendet wird, nicht etwas, das Sie konfigurieren müssen.</span><span class="sxs-lookup"><span data-stu-id="4e914-173">If you are running Windows 10 IoT Core in "Embedded Mode", this loopback exception is automatically applied, it's not something that you need to configure.</span></span> <span data-ttu-id="4e914-174">Erfahren Sie mehr über die Loopback-Ausnahmen [auf MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span><span class="sxs-lookup"><span data-stu-id="4e914-174">You can read more about loopback exceptions [on MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>

