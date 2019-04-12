---
title: Windows 10 IoT Core, Standard-App
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Erfahren Sie mehr über die Windows 10 IoT Core Standard-App und zugehörigen Funktionen.
keywords: Windows Iot, Windows 10 Iot Core, Standard-app
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512409"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Übersicht über die App von Windows 10 IoT Core, Standard

> [!TIP]
> Wenn Sie feststellen, dass Sie eine Funktion, die hinzugefügt werden, um diese Beispiel-app finden Sie unter möchten [eröffnen Sie ein Problem](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) auf GitHub, um uns zu informieren. Wenn Sie einen Fehler einreichen möchten, befolgen Sie die Anweisungen für die Feedback-Hub [hier](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).

Wenn Sie zunächst auf Windows 10 IoT Core flash, Sie mit der Windows 10 IoT Core Standard-App beim Start, erhält der so aussieht:

![Screenshot der standardmäßige IoT Core-App](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

Der Zweck dieser Anwendung ist nicht nur für bieten Ihnen eine benutzerfreundliche Shell zu interagieren, wenn Sie Windows 10 IoT Core das zuerst gestartet, aber wir haben Open Source-Code für diese Anwendung [hier](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) , damit Sie mit diesen Plug-and-Play-können Features auf Ihren eigenen benutzerdefinierten Anwendungen.

In diesem Artikel erhalten Sie einen Überblick über die verschiedenen Funktionen, die die Windows 10 IoT Core Standard-App bietet auch, wie Sie diese verschiedenen Funktionen für Ihre eigenen Anwendungen nutzen können.

## <a name="leveraging-the-iot-core-default-app"></a>Nutzen die standardmäßige IoT Core-App 

> [!IMPORTANT]
> Verwenden Sie Maker Images nicht für gewerbliche Nutzung aus. Wenn Sie ein Gerät commercializing sind, müssen Sie eine benutzerdefinierte FFU für optimale Sicherheit verwenden. Weitere Informationen finden Sie [hier](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

Die IoT Core-Standard-App angepasst und erweitert werden können, oder Sie können den Quellcode als Beispiel für Ihre eigene app. Um dies selbst auszuprobieren, laden Sie die ZIP-Datei mit unserer Beispiele, oder sehen Sie sich den Code für die IoT Core-Standard-App [hier](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp). Fragen, ein Problem melden auf unsere-beispielrepository [hier](https://github.com/Microsoft/Windows-iotcore-samples/issues).

Siehe unter der [Abschnitt "Einstellungen"](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) im folgenden, in einigen Fällen Sie möglicherweise konfigurieren Standardeinstellungen und Features auf Ihrem Kundensystem im Namen des Endbenutzers. Aber wenn Sie aktivieren, diese Einstellungen und Features auf standardmäßig oder wenn die Diagnose über die Einstellung "Grundlegend" befinden, müssen Sie:

* Der Endbenutzer zu benachrichtigen, dass diese Funktionen aktiviert wurden, und geben den Endbenutzer mit dem Link zur Webseite von Microsoft Datenschutzbestimmungen [hier](http://go.microsoft.com/fwlink/?LinkId=521839). 
* Sichern Sie Ihre Zustimmung, aus dem entsprechenden Benutzer Funktionen zu aktivieren, wird standardmäßig (falls erforderlich, durch das anwendbare Recht).
* Geben Sie Endbenutzern die Möglichkeit, der die diagnoseeinstellung an der Einstellung "Grundlegend" zu ändern.
* Wenn Sie die Microsoft-Accounts aktivieren, und Zugriff auf die Endbenutzerdaten, haben Wenn der Endbenutzer die Microsoft Account löscht, müssen Sie die gleichzeitigen löschen alle des Endbenutzers, Microsoft Account Daten auf dem Gerät aktivieren. 

## <a name="out-of-box-experience-oobe"></a>Out-of-Box-Experience (OOBE)

Die Out-of-Box-Experience für die IoT Core-Standard-App ist als lean, wie es abruft. Die ersten Seiten werden für eine Sprache und WLAN-Einstellungen der Standardrichtlinie gefragt. Von dort in der Reihenfolge für Ihre app auf DSGVO-Kompatibilität, benötigen Sie einen Bildschirm für diagnostische Daten und, wenn Sie planen, Speicherort nachzuverfolgen, müssen Sie einen Speicherort-berechtigungenbildschirm zu verfügen. Beispiele für beide sind unten dargestellt. 

![Einstellungen für den Speicherort für OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![diagnoseeinstellungen für OOBE](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>Befehlsleiste
Die Befehlsleiste ist der permanente Horizonatal-Leiste am unteren Rand des Bildschirms. Dies bietet einfachen Zugriff auf die folgende Funktionalität:
- Vorwärts und rückwärts navigieren
- Grundlegende Geräteinformationen, ohne die aktuelle Seite
- Aktivieren oder Deaktivieren von Vollbildmodus
- Erweiterten Verknüpfungen
- Bestimmte Seite-Schaltflächen

Es gibt viele Schaltflächen auf der Befehlsleiste, und manchmal dieser Schaltflächen verwirrend oder ausgeblendet werden können. Auf der Befehlsleiste zu erweitern, Zugriff auf diese Schaltflächen, und drücken Sie die Menüschaltfläche, in der unteren rechten Ecke:

![Wie Sie die Befehlsleiste zu erweitern](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>Startmenü - Play

Im Menü Start werden die meisten Features von Plug & Play gespeichert.

### <a name="weather"></a>Wetter
Verwenden die Daten von der National Weather Service, rendert die Seite "Weather" Wetterdaten in Ihrem aktuellen Standort.

### <a name="web-browser"></a>Webbrowser
Der Webbrowser können Sie sich die meisten Websites aus dem Web abrufen.

### <a name="music"></a>Musik
Auf dieser Seite spielen MP3 und WAV-Dateien aus der **Musikbibliothek**, können auf das über die [Windows Device Portal](../manage-your-device/DevicePortal.md).  Zum Hochladen von Dateien für den Musikplayer müssen Sie navigieren zu den Windows Device Portal, klicken auf die Dropdownliste "Apps", navigieren zu "Datei-Explorer", "Music" auswählen und Hochladen von Dateien von dort aus.


![Gewusst wie: Hochladen von Musikdateien](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>Slideshow
Auf dieser Seite zeigt alle PNG- oder JPEG-Bild-Dateien aus der **Bildbibliothek**, können auf das über die [Windows Device Portal](../manage-your-device/DevicePortal.md). Zum Hochladen von Bildern in der Diaschau, müssen Sie navigieren zu den Windows Device Portal, klicken auf die Dropdownliste "Apps", navigieren zu "Datei-Explorer", wählen Sie "Bilder" und Hochladen von Dateien von dort aus.


![Gewusst wie: Hochladen von Musikdateien](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>Draw
Auf dieser Seite können Sie Windows 10 IoT Core Freihandfunktionen zu testen.

## <a name="start-menu---explore"></a>Startmenü - erkunden 

### <a name="apps"></a>Apps 
Auf dieser Seite können Sie zum Starten von anderen Foreground-Anwendungen, die auf dem Gerät installiert. Starten einer Anwendung wird angehalten, IoT Core Standard-App, die erneut gestartet werden kann, mit dem App-Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).

Keine besonderen ist erforderlich, um die vordergrundanwendung, die auf der Seite aufgeführt sind, einfach verfügen [installieren](AppInstaller.md) oder [bereitstellen](AppDeployment.md) der Anwendung. Navigieren Sie nach der erfolgreichen Installation oder Bereitstellung erneut auf die Seite "Apps", um die Liste der Anwendungen zu aktualisieren.

Beachten Sie, dass es eine Reihe von automatisch generierten OS beziehen Anwendungen, die Sie filtern, finden Sie die Liste der app-Namen [hier](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).

### <a name="notifications"></a>Benachrichtigungen
Auf dieser Seite listet die letzten 20 Benachrichtigungen, da IoT Core-Standard-App gestartet wurde. Wenn IoT Core-Standard-App im Debugmodus ausgeführt wird, werden erstellt, die von testbenachrichtigungen Schaltflächen hinzugefügt.

### <a name="logs"></a>Protokolldateien
Auf dieser Seite listet alle automatisch generierten Abstürze oder Fehler Protokolle, die dann aus dem Gerät genommen und analysiert werden können.

### <a name="github"></a>GitHub
Diese Seite gelangen Sie auf den Open Source-GitHub-Speicherort des Codes IoT Core-Standard-App.

## <a name="start-menu---windows-device-portal"></a>Starten Sie Windows Device Portal-Menü –

Die Seiten in diesem Abschnitt nutzen Sie die Windows Device Portal REST-APIs, sich mit Ihren Windows Device Portal-Anmeldeinformationen anmelden müssen.

## <a name="device-information"></a>Geräteinformationen

Auf dieser Seite können Sie die verschiedenen Features für Ihr Gerät wie z.B. Ethernet-OS-Version, verbundenen Geräten und mehr finden Sie unter.

## <a name="command-line"></a>Befehlszeile

Auf dieser Seite können Sie Befehle direkt auf Ihrem Gerät ausführen.

Zum Aktivieren dieses Features müssen Sie einen Registrierungsschlüssel festlegen, damit die app die Befehle ausführen kann. Beim ersten Versuch zum Ausführen eines Befehls sehen Sie eine Verknüpfung, die Sie den Registrierungsschlüssel, die über einen Aufruf an die Windows Device Portal festlegen können. Klicken Sie auf den Link, um Ihr Gerät zum Ausführen von Befehlen zu aktivieren.

Einige Befehle erfordern Administratorzugriff. Aus Sicherheitsgründen verwendet die app wird standardmäßig ein nicht-Administratorkonto zum Ausführen von Befehlen an. Wenn Sie einen Befehl als Administrator ausführen möchten. Sie können eingeben "RunAsAdmin <your command>" in der Eingabeaufforderung.

## <a name="settings"></a>Einstellungen
Sie werden eine Reihe von einschließlich Wi-Fi, Bluetooth, Power-Optionen und weitere Einstellungen konfigurieren können.

### <a name="app-settings"></a>App-Einstellungen
Die **Anwendungseinstellungen** Abschnitt können Sie verschiedene Einstellungen für Seiten in der app zu konfigurieren.  

Sind einige der Einstellungen, die Sie anpassen können:

##### <a name="general-settings"></a>Allgemeine Einstellungen
* Legen Sie die Standardseite, die angezeigt wird, wenn die app gestartet wird
* Aktivieren/Deaktivieren des Bildschirmschoners

##### <a name="weather-settings"></a>Wetter-Einstellungen
* Ändern Sie den Speicherort
  > Dieses Feature ist nur aktiviert, wenn Sie einen gültigen angegeben haben [Bing Map-Diensts Token](https://msdn.microsoft.com/library/ff428642.aspx).  Um das Token an die app zu übergeben, erstellen eine **MapToken.config** Datei im Ordner "LocalState" der app (z. B. C:\Data\USERS\\[Benutzerkonto] \AppData\Packages\\[Vollständiger Paketname] \LocalState\ MapToken.config) und die app neu starten.
* Erweitern Sie die Karte
* Aktivieren/deaktivieren, damit die Zuordnung und der Wetter-Schalter wird in regelmäßigen Abständen zum Bildschirm Burn-in zu verhindern, dass zuordnen kippen

##### <a name="web-browser-settings"></a>Webbrowser-Einstellungen
* Legen Sie auf der Startseite für den Webbrowser

##### <a name="slideshow-settings"></a>Diaschau-Einstellungen
* Legen Sie das Intervall Bildschirmpräsentation

##### <a name="appearance"></a>Darstellung
* Verwenden von MDL2 Objekte anstelle von Emojis für die Kachel "-Symbole
* Legen Sie die Kachel Breite und Höhe
* Skalierung von UI - Festlegen der automatischen Skalierung wird standardmäßig festgelegt
* Legen Sie die kachelfarbe

#### <a name="system"></a>System
Ändern Sie die Sprache, Tastaturlayout und Zeitzone.

#### <a name="network--wi-fi"></a>Netzwerk und WLAN
Zeigen Sie der Eigenschaften des Netzwerkadapters an, oder eine Verbindung mit einem verfügbaren Wi-Fi-Netzwerk herstellen.

#### <a name="bluetooth"></a>Bluetooth
Mit einem Bluetooth-Gerät koppeln.

#### <a name="app-updates"></a>App-Updates
Überprüfen Sie nach app-Updates oder Ändern von Einstellungen für automatische Updates.

#### <a name="power-options"></a>Energieoptionen
Neustarten oder Herunterfahren des Geräts.

#### <a name="diagnostics"></a>Diagnose
Wählen Sie den Zeitraum von Diagnosedaten, die Sie Microsoft zur Verfügung stellen möchten.  Wir empfehlen, dass Benutzer abonnieren **vollständige** Diagnosedaten können Probleme schnell diagnostizieren und nehmen Sie Verbesserungen für das Produkt.

##### <a name="basic"></a>Einfach 
Senden Sie nur Informationen zu Ihrem Gerät, dessen Einstellungen und Funktionen, und gibt an, ob er ordnungsgemäß arbeitet.

##### <a name="full"></a>Vollständig
Senden Sie alle grundlegende Diagnosedaten und Informationen zu Websites, die Sie durchsuchen und die Verwendung von apps und Features sowie zusätzliche Informationen über die Integrität für Geräte,, Geräteaktivität und verbesserte Fehlerberichterstattung.

#### <a name="location"></a>Pfad
Zulassen oder Ablehnen des app Zugriffs auf Ihren Standort.
