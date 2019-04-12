---
title: Update für Oktober 2018 - Build 17763
author: saraclay
ms.author: saclayt
ms.date: 10/02/2018
ms.topic: article
description: Erfahren Sie, was in der Oktober 2018 Update für Windows neu ist.
keywords: Windows IoT, Oktober 2018 aktualisieren, die Anmerkungen zu dieser Version
ms.openlocfilehash: 886f86a733f53632dee73d0af7b2c172693bc3a5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514133"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Versionsanmerkungen zu Update vom Oktober 2018 für Windows 10 IoT
Buildnummer 17763. Oktober 2018

> [!IMPORTANT]
> Bei Verwendung der [Oktober 2018 aktualisieren](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/october2018update), verwenden Sie die [Oktober-Update (mit Januar Pack Build 17763.253 Wartung)](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/17763) stattdessen release. Wir haben festgestellt, es gibt bekannte Probleme, die Benutzer von der Oktober 2018 betreffen aktualisieren. 

Windows 10 IoT ermöglicht die Entwicklung von eingebetteten oder dedizierte Zwecke Geräte und ist die Wahl für OEMs und Entwicklung von Windows-Lösungen für intelligente Geräte.

Dieses Dokument enthält Informationen, die anderen Inhalt und die Dokumentation für diese Version von Windows 10 IoT zu ergänzen.

## <a name="privacy-statement"></a>Datenschutzbestimmungen

Die Datenschutzbestimmungen für diese Version des Windows-Betriebssystems angezeigt werden kann, am [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-october-2018-update"></a>Neuerungen im Oktober 2018 Update

_Windows 10 IoT Enterprise und Windows 10 IoT Core_
* Der Windows 10 IoT Oktober 2018 Update 10 Jahre lang mit Unterstützung für IoT Core und IoT-Unternehmen müssen.
* [Mit Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) ist ein vollständig verwalteter Dienst, der bereitstellt Intelligence lokal durch Bereitstellen und Ausführen von arbeitsauslastungen von künstlichen (AI), Azure-Dienste und benutzerdefinierte Logik direkt auf Windows 10 IoT-Geräten.
* [Windows Machine Learning](https://docs.microsoft.com/windows/ai/) ermöglicht Entwicklern, vorab trainierten Machine learning-Modelle in ihren Anwendungen verwenden. Diese Modelle werden in der Regel in der Cloud trainiert, am Rand ausgewertet werden soll. Lokale Auswertung auf Geräten mit Windows 10 IoT hilft dabei, Probleme der Konnektivität, Bandbreite und den Datenschutz zu verringern.  

_Windows 10 IoT Core_
* [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) Abonnement ist jetzt allgemein verfügbar. Dieses Abonnement wird mit drei entscheidende Vorteile, einschließlich Betriebssystem 10 Jahre unterstützt, aktualisieren Sie Steuerelement mit dem [Device Update Center](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center), und (Device Health Attestation, DHA).
* Um der wachsenden Bedarf und der Partner für Silicon Vielfalt, Microsoft, die eng mit NXP, haben die Unterstützung für NXP i.MX 6, 7 und 8-Prozessoren für M-Serie zu Windows 10 IoT Core hinzugefügt. 
* Qualcomm und Microsoft haben eine Lösung entwickelt, die Windows 10 IoT Enterprise mit Snapdragon-Prozessoren, um Geräte zu erstellen, die weniger Energie verbrauchen, immer verbunden sind und sofort aktiviert kombiniert. Lange Akkulaufzeit kann dedizierte Geräte wie mobile POS und -Tablets für Line-of-Business-to-last einen ganzen Tag an die häufige Verwendung. 
* [Die Windows 10 IoT Core standardmäßig App](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) verfügt über mehr Funktionen, die Benutzer für ihre eigenen Anwendungen nutzen können, insbesondere, wenn ihre Geräte auf den Markt zu bringen. Zu diesen Funktionen gehören Wetter, Freihandfunktionen, Audiofunktionen. 
* Wenn Sie ein open Retail-Gerät für die kommerzielle Bereitstellung in einer "Installation von bestimmten/eingeschränkt" erstellen (d. h. Vorinstallations- oder Retail Store), in dem der Endbenutzer ist die endgültige Konfiguration und Dokumentieren Sie Ihre Kunden, die sie müssen [erhalten eine Zertifikat für WDP, und installieren Sie es WDP und eine Verbindung herstellen Browser sowohl Kennwörter WDP geändert werden](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), und klicken Sie dann mithilfe von WDP in dieser Instanz mit schmalen kommerziellen zulässig ist. Retail-Images in diesem Szenario IOT_TOOLKIT darf noch nicht enthalten, aber Sie sollten IOT_WEBBEXTN Paket verwenden, um WDP zu erhalten. 
* Limpet.exe steht jetzt als eine [open Source-Projekt](https://github.com/ms-iot/azure-dm-client). Um Tests einfacher zu machen, wir verfügen über eine nicht signierte, vorab erstellte Version Limpet.exe verfügbar und kann direkt von WDP heruntergeladen werden. Erfahren Sie mehr über dieses Feature über die [Windows Device Portal Dokumentation](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal).  
* Mit RS5 können Entwickler jetzt um benutzerdefinierte FFUs auf ihre Geräte über das Dashboard zu aktualisieren. Dies kann mit dem DragonBoard 410 C oder NXP erfolgen. Weitere Informationen und erste Schritte [hier](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup).
* Windows 10 IoT Core verwendet jetzt die gleichen Komponenten des Touch-Tastatur, als die desktop Edition von Windows die Features wie Diktatmodus, den gesamten Satz von Windows-Sprache Tastaturlayouts und mehr ermöglicht. Dieses neue Update enthält auch Support für Emoticons, die Eingabe "Bereiche" und eine bessere mehrsprachige Unterstützung. Erfahren Sie, wie Sie diese Features nutzen [hier](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard).
* Erfahren Sie, wie Sie [Konfigurieren Ihres Geräts, um die es ermöglichen, die deaktiviert werden](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch) zwar nicht verwendet und eingeschaltet werden, wenn ein Benutzer einen Bildschirm berührt.
* Bluetooth A2DP-SENKE wird jetzt optional unterstützt (z. B. ermöglicht das Ausgeben von Remotequelle wie iPhone IoT-Geräte) und Bluetooth A2DP-SRC ist jetzt ein optionales Paket (wurde im April 2018 standardmäßig verfügbare Version). Sie können Bluetooth A2DP-SRC "und" A2DP-SENKE profileinstellungen steuern, wenn beide Profile vorhanden sind und mit einem anderen Gerät koppeln, die auch beides unterstützt. 
* Windows 10 IoT Core wird einen Anwendung-Rahmen um das Fenster einer Anwendung – nicht in Worten: angezeigt, eine Anwendung als Vollbild angezeigt wird, werden standardmäßig. Aber in dieser Version haben Entwickler die Möglichkeit [konfigurieren Titelleisten](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars).
* Bus-Tools, mit denen Sie für die Interaktion mit Gpio, I2c, Spi und UART stehen nun in [unser beispielrepository](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools). Diese Tools werden auf eine beliebige Edition von Windows einschließlich Windows 10 IoT Core und Windows Enterprise ausgeführt. 
* [Der Namespace-API für Windows.System.Update](https://docs.microsoft.com/uwp/api/windows.system.update) ermöglicht Aufrufe für die interaktive Steuerung von Systemupdates. Dieser Namespace ist nur für Windows 10 IoT Core verfügbar.
* Wenn Sie IoT Central als Teil einer Windows 10 IoT-Lösung verwenden möchten, können Sie jetzt vorbereiten und [ein Windows 10 IoT Core-Gerät mit Ihrem Azure IoT Central-Anwendung verbinden](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore). 
* Die Version für die Raspberry Pi 3 b + (finden Sie herunterladbare ISO [hier](http://go.microsoft.com/fwlink/?LinkID=708576)) wird von eine technical Preview, und es gibt derzeit keine Zeitachse für eine veröffentlichte Version. Für eine bessere Evaluierung und "fr" verwenden alle kommerziellen Produkten, Sie den Raspberry Pi 3-b oder andere Geräte mit unterstützten Intel, Qualcomm oder NXP SoCs. 

## <a name="iot-enterprise-manufacturing-guide"></a>IoT Unternehmensleitfaden Produktionskalender

* Ist eine neue Fertigung-Anleitung für Windows 10 IoT Enterprise [sofort](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview). 

## <a name="improvements-in-assigned-access"></a>Verbesserungen bei der zugewiesenen Zugriff 

_Windows 10 IoT Enterprise_

* Kioske und digital signiert sind häufig platzieren, an öffentlichen Orten, in dem Probleme häufig von Personen angezeigt werden. Mit integrierten Statusberichte Device Management-Systemen sind automatisch Probleme aufmerksam gemacht und können ausgeben, korrekturmaßnahmen wie z. B. Neustarten des Geräts oder verteilen einen Servicetechniker. 
* Kostensparender Einsatz von Bereitstellung und Verwaltung sind die wichtigsten Einflussfaktoren für die Rendite. Windows 10 IoT Enterprise verbesserten Funktionen für eine Kiosk-benutzererfahrung über einen neuen Assistenten Einstellungen konfigurieren, Verwalten von Kiosks für mehrere Apps und Anpassen der [Microsoft Edge-Browser-Erfahrung für Kiosk-Geräte](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy).
* Zwar Gerät Generatoren Flexibilität zugewiesener Zugriff mithilfe von Bereitstellungspaketen, die app "Einstellungen" und Verwaltungssystemen für mobile Geräte zu konfigurieren, benötigen einige Kunden noch mehr. [Verwenden einen neuen Satz von APIs für zugewiesenen Zugriff](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings), Entwickler können jetzt zugewiesener Zugriff programmgesteuert über innerhalb ihrer Anwendungen konfigurieren.
* Mit der Version vom Oktober 2018 können Kunden eine Benutzeroberfläche automatisch gestartet als Teil der Konfiguration mit mehreren Apps zugewiesen Zugriff angeben, damit Benutzer stets über eine Standardbenutzeroberfläche für den primären app verfügen.
* Sie können steuern, was ab dem Zeitpunkt der Benutzer sieht, die das Gerät eingeschaltet wird, bis er ausgeschaltet ist. Gestartet wird, indem Sie Ihr Logo anstelle der Windows-Logo auf Start oder automatischer Neustart von apps ohne Fehlermeldungen angezeigt, nach einem Absturz der app, eines Systemfehlers oder einer Unterbrechung der Stromversorgung. 
* Sie können das Feature Unified Write Filter (, UWF) verwenden, ein Gerät "schreibgeschützt" zu erstellen, die in einen bekannten Zustand zurückgegeben werden soll, nachdem eine Potenz durchlaufen werden, da der datenträgeränderungen im Arbeitsspeicher abgelegt und auf den Datenträger zu schreiben. Sie können auch UWF mit der Hibernate Once, fortsetzen viele (HORM)-Funktion mit einer vordefinierten Sitzung fortsetzen kombinieren. 


## <a name="more-management-support"></a>Support für Weitere

_Windows 10 IoT Enterprise_
* Azure IoT Hub bietet einfache geräteverwaltungsfeatures und ein Erweiterbarkeitsmodell, mit dem Gerät und Cloud-Entwickler stabile geräteverwaltungslösungen entwickeln können. Integration mit [Azure IoT-Geräteverwaltung](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) ist jetzt für Windows 10 IoT Core und Enterprise verfügbar. 

_Windows 10 IoT Core_
* Unternehmen, mit denen [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) für ihr Gerät kann Management jetzt Windows 10 IoT Core-Geräte zusammen mit ihrer Windows 10 IoT Enterprise-Geräte und andere verwaltete Geräte verwalten. Dadurch werden Operatoren eine einheitliche Methode zum Verwalten von Windows 10 IoT-Geräten, die über die gleichen Management-Benutzeroberfläche und Steuerelemente. 


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


## <a name="known-issues"></a>Bekannte Probleme
* F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter Windows 10 IoT Core. Treiber müssen manuell kopiert und auf dem Gerät registriert werden.
* Geräte, die über NOOBS installiert wurden, können nicht das Bcdedit-Tool zum Aktivieren des Kernel-Debuggers ausgeführt.
* Der Windows-IoT-Remote-Client funktioniert nicht für Raspberry Pi. Verwenden Sie ein Board mit beschleunigter Grafikfunktionen z. B. Minnowboard Max oder Dragonboard, oder fügen Sie einen Monitor für die lokale Anzeige.
