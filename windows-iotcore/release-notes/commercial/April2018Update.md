---
title: Update von April 2018 - Build 17134
author: saraclay
ms.author: saclayt
ms.date: 05/01/2018
ms.topic: article
description: Erfahren Sie, was ist neu im April 2018 Update für Windows 10 IoT.
keywords: Windows IoT, Update von April 2018, Anmerkungen zu dieser Version
ms.openlocfilehash: b61ee94651c2bea0ec0582669b62867d47c85a0c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512338"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>April 2018 Update – Versionshinweise für Windows 10 IoT
Buildnummer 17134. Mai 2018

Windows 10 IoT ermöglicht die Entwicklung von eingebetteten oder dedizierte Zwecke Geräte und ist die Wahl für OEMs und Entwicklung von Windows-Lösungen für intelligente Geräte.

Dieses Dokument enthält Informationen, die anderen Inhalt und die Dokumentation für diese Version von Windows 10 IoT zu ergänzen.

## <a name="privacy-statement"></a>Datenschutzbestimmungen

Die Datenschutzbestimmungen für diese Version des Windows-Betriebssystems angezeigt werden kann, am [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-april-2018-update"></a>Neuerungen im April 2018 Update
* Die [Visual Studio-Testplattform](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/) , im Lieferumfang [Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) unterstützt nun Tests auf Windows 10 IoT Core. Wenn [Schreiben von Komponententests](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/) für ein Projekt in Visual Studio 2017, das auf Windows 10 IoT Core-Entwickler können jetzt Ausführen dieser Komponententests Remote auf dem Gerät direkt aus Visual Studio anstatt Tests auf dem Gerät bereitstellen und sie manuell ausführen.
* Entwickler können die Funktionen in der [Windows-Plattform für künstliche Intelligenz](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/) auf Windows 10 IoT Sie intelligenter Geräte erstellen und zu beschleunigen ML modellauswertung mit CPU oder GPU.
* OEMs, die Suche nach einer VCD-Gerät auf den Markt schnell bringen integriert werden können Cortana-Support ihr Gerät mit der [Vorschau des Cortana Devices SDK](http://www.aka.ms/cortanadevices).
* OEMs können den umfangreichen Satz von CSPs, die auf Windows zum Ausführen von remote-Konfiguration verfügbar sind und die Verwaltung von Geräten in großem Umfang mithilfe nutzen [Azure IoT-Geräteverwaltung](https://github.com/ms-iot/iot-core-azure-dm-client). Diese neue beispielimplementierung kombiniert einen lokalen Client, Cloud-Dienst und -Verwaltungsportal, aktivieren die IoT-Bediener geräteverwaltung in der Cloud ausführen.
* Sie können mit dieser Version schreiben [UWP-Konsolen-apps](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp) , die in einem Host mit der Konsole, z. B. eine Befehlskonsole oder PowerShell ausgeführt. UWP-Konsolen-apps können können sich auch auf die Win32-APIs in UWP-apps verfügbar und veröffentlicht und über den Microsoft Store aktualisiert werden.
* Wir haben ein neues hinzugefügt [Miracast-Feature-Paket](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast) IoT Core zusammen mit einer [Satz der Umwandlung von APIs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) um ein Gerät genau dann agieren als Miracast-Sender oder Empfänger zu aktivieren.
* Wir haben Unterstützung für die [Bluetooth A2DP-SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) Profil für die ein Gerät genau dann agieren als Quelle für das streaming Bluetooth-audio ermöglicht, einschließlich der Remotesteuerung Funktionen per Bluetooth mithilfe des Profils AVRCP.
* Eines unserer am häufigsten verwendeten Qualcomm-Boards, das DragonBoard 410c, ist viel leichter zu dieser Version flash geworden. Verwenden die neueste Version von der [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), einfach Verbinden des Boards, flash-Modus abgelegt und [das Gerät flash](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice) direkt über das Dashboard.
* Zum Suchen und eine Verbindung mit WLAN-Netzwerke, wir haben aktualisiert die [WiFi-Connector-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS) werden mit dem Befehl Netcmd zuvor als veraltet markiert wurde. Dieses Beispiel verwendet die [WiFiAdapter APIs](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) zum Verwalten von Verbindungen mit Drahtlosnetzwerken und Adapter.
* Wir haben das neue zeitbezogene APIs automatisch durch Festlegen der Systemzeit auf den [Ortszeit](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) und [Zeitzone](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_) basierend auf dem Gerätestandort, Aktivieren von OEMs, um eine optimierte aus Box-Experience zu erstellen.
* Wir haben neue Sprach-APIs für das Festlegen des bevorzugten Benutzers [Sprache](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__), [Region](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), standardmäßige [Spracherkennung](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) Standardsprache, und [Voice](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync).
* Mit einem neuen [MTP-Featurepaket](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md), Sie können die Dateien zu und von einem Windows 10 IoT Core-Gerät über USB, die mithilfe des Media Transfer-Protokolls (MTP) übertragen. Dies schließt die Dateien, die auf den internen Speicher und SD-Karte des Geräts gespeichert werden, falls vorhanden.
* Wir haben ein neues veröffentlicht [auf GitHub](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) und [Channel 9-Video](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central) zeigt, wie einfach es ist, erhalten eine Windows 10 IoT Geräte, die in Azure IoT Central integriert. Außerdem haben wir unsere Dokumentation beschreiben aktualisiert [wie zum Verbinden von Geräten](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) unter Windows 10 IoT Core, Azure IoT Central.

## <a name="improvements-in-assigned-access"></a>Verbesserungen bei der zugewiesenen Zugriff
* Wir haben Unterstützung für mehrere Bildschirme für Anwendungsfälle digitalen Beschilderung hinzugefügt.
* Die Registrierungsstatus für die Seite enthält jetzt die Möglichkeit, um sicherzustellen, dass alle MDM-Konfigurationen auf dem Gerät vor dem Eingeben von zugewiesenen Zugriff erzwungen werden.
* Wir haben die Möglichkeit zum Konfigurieren und Ausführen des Shell-Startprogramm zusätzlich zu vorhandenen UWP-Store-apps hinzugefügt.
* Geräte, die mit zugewiesenem Zugriff können konfiguriert werden, um automatisch einen gewünschten Status nach einem Neustart mit einem vereinfachten Prozess für das Erstellen und Konfigurieren eines Kontos für die automatische Anmeldung einzugeben.
* Für Mehrbenutzer-Geräte, anstatt jeden Benutzer ist es jetzt möglich, verschiedene Konfigurationen für zugewiesene Azure AD-Gruppen oder Active Directory-Gruppen zuzuweisen.
* Um bei der Problembehandlung zu helfen, können Sie jetzt Fehlerberichte anzeigen, die generiert werden, wenn bei einer für zugewiesen Zugriff konfigurierten App Probleme auftreten.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Funktionen in der Vorschau für Entwicklungs- und Testszenarien
* Gerät-Update Center [Vorschau] können OEMs Global verwalten ihre apps und Übertragen von Updates für das Betriebssystem, apps, Einstellungen und Dateien aus der Cloud an Geräte, damit sie auf dem neuesten Stand und geschützt werden können.
* Unterstützung für das Hosten [Nano Server-Container](https://docs.microsoft.com/virtualization/windowscontainers/about/index) auf 64-Bit-Editionen von Windows 10 IoT Core and Enterprise, Aktivieren von Anwendungen und ihre Daten kann von jeder anderen isoliert und verschoben werden sollen schnell von der Entwicklung in produktionsumgebung oder Cloud-zu-die Rand.
* Windows Device Health Attestation [Vorschau]-Dienst verwendet, Hardwarefunktionen und Clouddienste für die korrekturhilfen vor Manipulationen und remote-Nachweis der geräteintegrität bieten basierend auf Metriken auf Hostebene Hardware und Daten bestätigt.
* [Mit Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) auf Windows IoT [Vorschau] können Sie IoT-Lösungen zum orchestrieren von Intelligence zwischen der Cloud und Edge-Geräten, um sicherzustellen, dass Anwendungen und Dienste auf IoT-Daten fungieren können, wo es am sinnvollsten ist.
* Azure IoT-Hub [Device Provisioning-Dienst [Vorschau]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) ermöglicht Windows 10 IoT-Geräten mit ein common-Image erstellt wird, während der Herstellung und so konfiguriert, dass beim ersten Start mit Azure IoT Hub zum Abrufen automatisch eine Verbindung hergestellt werden gerätespezifische Bereitstellungsinformationen.

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT Core-Referenzimages
___ 
* Minnowboard Max
  * Prozessor: Intel Atom E3825
  * Architektur: x86

* Raspberry Pi 3, Modell B
  * Prozessor: Broadcom BCM2837
  * Architektur: ARM

* DragonBoard 410c
  * Prozessor: Qualcomm Snapdragon 410
  * Architektur: ARM
  * BSP-Version: 2120.0.0.0

## <a name="additional-information"></a>Weitere Informationen
* Basierend auf die jüngste Ankündigung von Intel, die nicht mehr von der Intel Joule-Plattform, wurden FFUs für Intel Joule in der vorherigen Version nicht mehr unterstützt. Identifizierung von Kunden, die Auswertung von Intel Joule sollten eine Alternative mit einer anderen Plattform SoCs unterstützt?: Siehe [vorgeschlagene Boards und SoCs](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) eine Liste.

## <a name="known-issues"></a>Bekannte Probleme
* F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter Windows 10 IoT Core. Treiber müssen manuell kopiert und auf dem Gerät registriert werden.
* Geräte, die über NOOBS installiert wurden, können nicht das Bcdedit-Tool zum Aktivieren des Kernel-Debuggers ausgeführt.
* Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi. Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.
