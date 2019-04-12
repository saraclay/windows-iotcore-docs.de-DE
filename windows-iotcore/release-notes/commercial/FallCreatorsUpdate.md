---
title: Fall Creators Update - Build 16299
author: saraclay
ms.author: saclayt
ms.date: 10/12/2017
ms.topic: article
description: Erfahren Sie mehr über in dem Fall Creators Update für Windows 10 IoT neuerungen.
keywords: Anmerkungen zur Version von Windows IoT, Fall Creators Update
ms.openlocfilehash: 00daad18d5519eee9be695105332aced81a1133f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512337"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Fall Creators Update-Anmerkungen zu dieser Version für Windows 10 IoT
Buildnummer 16299. Oktober 2017

Windows 10 IoT ermöglicht die Entwicklung von eingebetteten oder dedizierte Zwecke Geräte und ist die Wahl für OEMs und Entwicklung von Windows-Lösungen für intelligente Geräte.

Dieses Dokument enthält Informationen, die anderen Inhalt und die Dokumentation für diese Version von Windows 10 IoT zu ergänzen.

Um diese neueste Build sowie die Pakete herunterzuladen, besuchen Sie die [Seite Windows Insider Preview-Downloads](https://www.microsoft.com/en-us/software-download/windowsiot).

## <a name="privacy-statement"></a>Datenschutzbestimmungen

Die Datenschutzbestimmungen für diese Version des Windows-Betriebssystems angezeigt werden kann, am [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-fall-creators-update"></a>Neuerungen in Update Fall Creators
* [.NET für UWP-apps](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396), den Satz von verwalteten Typen, die verwendet werden kann, um die universelle Windows-Plattform-apps erstellen C# oder Visual Basic getragenen [Tausende von neuen APIs](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/) dialogfeldbasiert kompatibel mit .NET Standard 2.0.
* Aktualisiert die sprachunterstützung für Windows 10 IoT Core, einschließlich Englisch (En-US und En-GB-), Französisch (fr-FR und fr-CA), Spanisch (es-ES und es-MX) und Chinesisch (vereinfacht) (Zh-CN). Sie können erstellen FFUs Unterstützung mehrerer Sprachen – Siehe [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) und [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample) für Weitere Informationen.
* Unterstützung für [Notverwaltungsdienste](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx) auf Windows 10 IoT Core.
* Verbesserte [Unterstützung für Freihandeingaben](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) auf Windows 10 IoT Core. Über ein Digitalisierungsgerät kompatibel Stift können Sie jetzt DirectInk-APIs für Textmarker Stift und Freihandeingaben vektorbasierte nutzen. Wir haben außerdem XAML Freihandeingaben Steuerelemente hinzugefügt, für die UWP, einschließlich InkCanvas-Steuerelement und InkToolbar, die Schablonen wie Lineale und Protractors und einer multimodalen Interaktionen wie Gleichzeitiges Stift aktivieren, und tippen Sie auf kompatible Hardware. Intelligente Freihand-Features wie z. B. handschriftenerkennung und handschrifterkennung werden nicht unterstützt.
* Zusätzliche Unterstützung für die Steuerung der Zeile angezeigt, einschließlich Anpassung des Cursor-Stil, Helligkeit, BlinkRate und Zeichensätze. Wir haben außerdem Unterstützung für benutzerdefinierte Symbole, Transaktion Deskriptoren und Marquee-Modus für den Lauftext hinzugefügt.
* Unter Windows 10 IoT Enterprise, haben wir Zugriff auf Industry standard Bussen wie GPIO, I2C, SPI und UART aktiviert, vom Benutzermodus über die [Windows.Devices APIs](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).
* [Zugriff zugewiesen](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) ist ein Feature in Windows 10 IoT Enterprise Hier können Sie ein bestimmtes Benutzerkonto mit nur einer universellen Windows-app zu beschränken. Wir haben zugewiesener Zugriff Unterstützung für mehrere UWP ausführen erweitert, und Win32-apps in eine Sperrung auftreten und diese Einstellungen über die Cloud verwalten.
* Sie können die Systemsprache, die mithilfe von IoTSettings.exe oder neue APIs ändern. Weitere Informationen finden Sie im Abschnitt Configuration Language der [über die Befehlszeile "utils"](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) und [sprachunterstützung](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) Dokumentation.
* Updates für Raspberry Pi-UEFI-Start-Volume-Monitor zu aktivieren.
* SMSC Netzwerktreiber für alle Architekturen von Windows 10 IoT Core hinzugefügt.
* Aktiviert [Audiostreams im exklusiven Modus](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx) für audio Clientendpunkt-Geräten auf Windows 10 IoT Core.
* Neue APIs in WinRT für das Festlegen von das Systemdatum und die Uhrzeit für Windows 10 IoT Core hinzugefügt.
* Unterstützung für [universelle BSP (wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages). Verwenden Sie die Iot-Adk-Addonkit v4. 0 mit der aktuellen Version von ADK aus.
* Hinzugefügte Sprachauswahl und lokalisierte Layouts zur Bildschirmtastatur. Weitere Informationen finden Sie unter [Onscreen-Tastaturlayouts](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts).

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Funktionen in der Vorschau für Entwicklungs- und Testszenarien
* Update-Komponentendienst [Vorschau] können OEMs Global verwalten ihre apps und Übertragen von Updates für das Betriebssystem, apps, Einstellungen und Dateien aus der Cloud an Geräte, damit sie auf dem neuesten Stand und geschützt werden können.
* Unterstützung für das Hosten [Nano Server-Container](https://docs.microsoft.com/virtualization/windowscontainers/about/index) auf 64-Bit-Editionen von Windows 10 IoT Core and Enterprise, Aktivieren von Anwendungen und ihre Daten kann von jeder anderen isoliert und verschoben werden sollen schnell von der Entwicklung in produktionsumgebung oder Cloud-zu-die Rand.
* Windows Device Health Attestation [Vorschau]-Dienst verwendet, Hardwarefunktionen und Clouddienste für die korrekturhilfen vor Manipulationen und remote-Nachweis der geräteintegrität bieten basierend auf Metriken auf Hostebene Hardware und Daten bestätigt.
* [Mit Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) auf Windows IoT [Vorschau] können Sie IoT-Lösungen zum orchestrieren von Intelligence zwischen der Cloud und Edge-Geräten, um sicherzustellen, dass Anwendungen und Dienste auf IoT-Daten fungieren können, wo es am sinnvollsten ist.
* Azure IoT-Hub [Device Provisioning-Dienst [Vorschau]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) ermöglicht Windows 10 IoT-Geräten mit ein common-Image erstellt wird, während der Herstellung und so konfiguriert, dass beim ersten Start mit Azure IoT Hub zum Abrufen automatisch eine Verbindung hergestellt werden gerätespezifische Bereitstellungsinformationen.
* [Azure IoT-Geräteverwaltung [Vorschau]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM) IoT-Betreiber zum Verwalten der Konfiguration installiert z. B. Anwendungen für Geräte, die Windows-Updates, die Zertifikate und Einstellungen von einem Remotestandort aus der Cloud ermöglicht.

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT Core-Referenzimages
___ 
* Minnowboard Max
  * Prozessor: Intel Atom E3825
  * Architektur: x86
  * BSP-Version: 10.0.4.0
* Raspberry Pi 3
  * Prozessor: Broadcom BCM2837
  * Architektur: ARM
  * BSP-Version: 10.0.16248.1001
* DragonBoard 410c
  * Prozessor: Qualcomm Snapdragon 410
  * Architektur: ARM
  * BSP-Version: 2112.0.0.0

## <a name="additional-information"></a>Weitere Informationen
* Basierend auf die jüngste Ankündigung von Intel, die nicht mehr von der Intel Joule-Plattform, FFUs für Intel Joule in dieser Version nicht mehr. Identifizierung von Kunden, die Auswertung von Intel Joule sollten eine Alternative mit einer anderen Plattform SoCs unterstützt?: Siehe [vorgeschlagene Boards und SoCs](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards) eine Liste.
* Das Feature IOT_WEBB_EXTN wurde umgestaltet, um die Onboarding-Funktion zu entfernen, die jetzt als IOT_ONBOARDING_APP verfügbar ist. Mit diesem Update die Onboarding-Funktion entfernt werden, und Geräte, die mit diesem Feature reflashed werden sollte, um dieses Feature erneut aus.

## <a name="known-issues"></a>Bekannte Probleme
* F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter Windows 10 IoT Core. Treiber müssen manuell kopiert und auf dem Gerät registriert werden.
* Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi. Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.
