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
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="alljoyn-troubleshooting"></a>Problembehandlung für AllJoyn

[AllJoyn](https://allseenalliance.org/developers/learn) ist eine Technologie, ermöglicht IoT-Geräten und Anwendungen erkennen und miteinander interagieren. Da AllJoyn in Windows 10 und Windows 10 SDK integriert ist, ist es einfach, dass AllJoyn mit der universellen Windows-Plattform (UWP) zu nutzen.

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

In diesem Blogbeitrag können Sie konfigurieren, dass AllJoyn und der Geräte und auch Schritte zur Problembehandlung befolgt werden, wenn etwas nicht wie erwartet funktioniert. Der primäre Fokus dieses Artikels wird die Kommunikation zwischen UWP AllJoyn-Client-apps (AllJoyn Verbraucher) und dass AllJoyn-Geräten (AllJoyn Producer) aktiviert werden. Viele der gleichen Konfigurationsschritte sind erforderlich, um die Kommunikation mit AllJoyn-Producer UWP-apps zu ermöglichen, aber weitere Details zu zukünftigen Blogbeiträge und Artikel bleiben werden.

### <a name="app-development-checklist"></a>App-Development-Prüfliste

Wenn Sie für Windows 10 UWP-apps schreiben, sollten Sie sicherstellen, dass:

1. Sie haben die Funktion "AllJoyn" in Ihrer app-Manifest (Hinweis zur Groß-und Kleinschreibung) deklariert.
2. Sie haben die spezifische Architektur ausgewählt, die das Ziel sein müssen. (In einigen Fällen erforderlich, weil es sich bei Windows-Runtime-Komponenten mit "Any CPU" nicht erstellt werden können, erstellt ein bekanntes Problem mit einigen Visual Studio 2017).

Wenn Sie eine app oder Gerät Software, die sich nicht um eine UWP-basierte Anwendung für Windows 10 ist schreiben, prüfen Sie die folgende Checkliste zum Sicherstellen der Kompatibilität mit AllJoyn unter Windows 10:

1. Wenn einen Producer zu implementieren, stellen sicher, dass die Info-Schnittstelle und Info-basierte Ankündigung/Discovery verwendet werden. Die Info-Schnittstelle ist [dokumentiert, die auf der Website AllSeen Alliance](https://allseenalliance.org/developers/learn/core/about-announcement/interface).
2. Verwenden Sie für optimale Ergebnisse die 15.04 AllJoyn Codebasis, verfügbar in der [Codedownloads](https://allseenalliance.org/developers/download) der AllSeen Alliance-Website.

### <a name="network-setup-and-troubleshooting"></a>Netzwerkeinrichtung und Problembehandlung

Dass AllJoyn-Geräte in der Lage, um zu ermitteln und miteinander interagieren müssen die Netzwerkkonfiguration und die Einstellungen für jedes Gerät Folgendes erfüllen:

1. Alle AllJoyn-Geräte, die mit dem gleichen Netzwerk verbunden sind, und Sie werden im gleichen Subnetz.
2. Windows 10 PC: "Suchen, Geräte und Inhalte" ist für das Netzwerk mit AllJoyn aktiviert (gilt nicht für Phone).

Auf einem PC können Sie die Ablaufverfolgung-Route-Befehl über eine cmd- oder PowerShell-Fenster um zu überprüfen, ob eine andere Computer/Gerät sich im gleichen Subnetz wie folgt:

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

Die erste Zahl Ausgabe hier ist die Anzahl der Hops, und da dieser Wert "1" ist. Dies bedeutet, dass beide Computer im gleichen Subnetz befinden.

Im folgenden finden Sie ein Beispiel für eine typische AllJoyn netzwerkeinrichtung. In diesem Beispiel wäre aller angezeigten Geräte ermitteln und interagieren untereinander über AllJoyn, vorausgesetzt, dass sich diese im gleichen Subnetz befinden.

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

Wenn Sie Ihre Windows 10-PCs mit AllJoyn-Geräten mit dem Netzwerk verbinden, müssen Sie auf "Ja" klicken, wenn ein Dialogfeld in Bezug auf das Suchen nach Geräten und PCs im Netzwerk angezeigt wird. (Anmerkung: Dies gilt nicht, wenn Netzwerke von Windows 10 Phone verknüpfen, wie es kein solcher Dialogfeld ist).

Sie können diese Einstellung auf der Seite "Erweiterte Einstellungen" im WLAN-Einstellungen auch dann verwalten, wie hier gezeigt: (auf dieser Seite möglicherweise geringfügig je nachdem welche Windows 10 Insider-Builds, die Sie verwenden)

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

Die Umschaltfläche "Find-Geräte und Inhalt" sollte in der Position "Auf" um AllJoyn-Funktionalität zu aktivieren.

Für die vorhandenen Netzwerkverbindungen können Sie problemlos überprüfen, ob diese Option ordnungsgemäß konfiguriert ist, indem Sie "Get-NetConnectionProfile" Powershell-Cmdlet ausführen. (Beachten Sie, dass dies nicht für Windows 10 Phone gilt.)

Get-NetConnectionProfile-Beispielausgabe:

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


Ist der Wert "-NetworkCategory" auf "Private" (siehe oben), dies bedeutet, dass Sie eine richtig konfigurierte haben Ihre Netzwerkverbindung für AllJoyn.

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a>Informationen zu Ankündigungen und Problembehandlung bei der Ermittlung mit Getajxml.exe

AllJoyn Producer Geräte oder dass AllJoyn Windows 10-UWP-apps-apps erkannt werden muss über-basierte Ermittlung ordnungsgemäß implementiert werden. Dies kann problemlos mit dem Tool GetAjXml.exe überprüft werden. Zum Herunterladen und Verwendungsinformationen, die im Zusammenhang mit GetAjXml.exe zu suchen, sehen Sie sich [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).

Das folgende Beispiel zeigt GetAjXml.exe-Ausgabe für eine Beispiel-Gerät, das zur-basierte Ermittlung unterstützt:

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


Im obigen Beispiel da `Discovery   : About Announcement` enthalten war in dieser Ausgabe ist wird dieser AllJoyn-Hersteller von Windows 10 AllJoyn UWP-apps erkannt werden. Wenn Sie diese Ausgabe für einen bestimmten AllJoyn-Hersteller nicht angezeigt wird, müssen Sie die Discovery-Implementierung auf dem Gerät (Producer) untersuchen.

### <a name="advanced-troubleshooting-with-etw-log-output"></a>Erweiterte Problembehandlung mit ETW-Ausgabe

Ereignisablaufverfolgung für Windows (ETW) können Sie erweiterte Debuginformationen für viele andere Features in Windows. Zum Glück ist AllJoyn, eine der Funktionen mit ETW-Protokollierung-Unterstützung, damit in diesem Abschnitt ich Ihnen zeige ETW-Protokollierung für AllJoyn zu aktivieren, und wie Sie die Protokolle zugreifen.

1. Starten der Ereignisanzeige durch Eingabe von "Ereignisprotokolle" in das Suchtextfeld Menü "Start", "Ereignisprotokolle anzeigen" auswählen.
2. Stellen Sie sicher, dass "Zeigen analytische und Debugprotokolle" aktiviert ist, klicken Sie im Menü "Ansicht".
3. Navigieren der Strukturansicht im linken Navigationsbereich auf "Anwendungen und Dienste Protokolle > Microsoft > Windows > AllJoyn" in der Ordneransicht und der debugkanal und den Betriebskanal aktivieren. (Siehe rotes Kästchen im folgenden Screenshot).
4. Reproduzieren Sie das Problem, das Sie mit AllJoyn auftreten.
5. Klicken Sie auf der Leiste der richtigen "Aktionen" auf "Aktualisieren", und suchen Sie das Betriebsereignisprotokoll und das Debuggen Kanäle in der linken Navigationsleiste unter dem Ordner "AllJoyn".

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

AllJoyn-ETW-ablaufverfolgungen werden wie folgt partitioniert:

- Debug-Kanal: Ausführliche, nicht-Fehler/nur zu Informationszwecken ablaufverfolgungen
- Betriebskanal: Fehlerablaufverfolgungen, Fehler werden nur die Ausgabe auf den Betriebskanal

Um Informationen über ETW-Einträge zu extrahieren, können Sie mit der rechten Maustaste auf einen Eintrag in der Listenansicht für einen bestimmten Kanal, und wählen Sie dann auf "Kopieren" und klicken Sie dann auf "Details als Text kopieren". Wenn Sie dann den entsprechenden Text in einem Text-Editor einfügen, müssen Sie die Details, wie im folgenden Beispiel:


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


Diese Informationen können helfen, dass AllJoyn Probleme aufzuspüren, und Unterstützung beim Melden von Problemen an Microsoft oder anderen Partnern ins Detail. Erfahren Sie mehr über [-ETW-ablaufverfolgungen und der Ereignisanzeige auf MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).

### <a name="known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen

Standardmäßig Einschränkungen für AllJoyn unter Windows 10:

- Der AllJoyn-Router-Knoten ist kein von AllJoyn-Geräten oder apps im Netzwerk automatisch gestarteten Wenn keine apps auf Windows 10-PC ausgeführt werden. Den Knoten für Windows 10-Router kann aus einer Eingabeaufforderung mit erhöhten Rechten oder Powershell-Sitzung gestartet werden, indem Sie den Befehl "net Start Ajrouter" ausführen.
- AllJoyn-UWP-apps nicht anzeigen oder interagieren mit anderen AllJoyn-UWP-apps oder dass AllJoyn-desktop-apps, die auf dem gleichen Computer ausgeführt wird. Dies ist ein Teil der app-Isolation Zusicherung, die für UWP-apps unter Windows 10 implementiert wird. 
  - Wenn Sie eine AllJoyn UWP-app aus Visual Studio bereitstellen, wird app-Isolation Isolierung für die app umgangen (Dies ist eine Ausnahme"Loopback" bezeichnet). Jede UWP-app, die in Visual Studio bereitgestellt wird werden ermitteln und mit anderen Loopback-Ausnahme für UWP-apps und desktop-apps interagieren, solange diese apps über basierende Ankündigung/Discovery verwenden. Wenn Sie Windows 10 IoT Core im "Eingebetteten Modus" ausführen, diese Loopback-Ausnahme automatisch angewendet wird, nicht etwas, das Sie konfigurieren müssen. Erfahren Sie mehr über die Loopback-Ausnahmen [auf MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).

