---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, wie Sie mit der Windows Device Portal zum Konfigurieren und verwalten Ihr Gerät Remote.
keywords: Windows Iot, Windows Device Portal, remote-Device-portal
ms.openlocfilehash: 715e9c138e86efcd82b485d832c5fbdd536398dd
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512410"
---
# <a name="windows-device-portal"></a>Windows Device Portal
   Die Windows Device Portal (WDP) können Sie konfigurieren und verwalten Sie Ihr Gerät remote über das lokale Netzwerk.
Die wichtigsten Funktionen sind unter dokumentiert die [Windows Device Portal-Seite "Übersicht"](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)

![Device Portal-Startseite](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> Verwenden Sie Maker Images nicht für gewerbliche Nutzung aus. Wenn Sie ein Gerät commercializing sind, müssen Sie eine benutzerdefinierte FFU für optimale Sicherheit verwenden. Weitere Informationen finden Sie [hier](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

> [!WARNING]
> Live-Kernel-Debugging ist derzeit für ARM-Geräte fehlgeschlagen. Wir arbeiten daran, dies behoben werden.

> [!IMPORTANT]
> Wenn Sie ein open Retail-Gerät für die kommerzielle Bereitstellung in einer "Installation von bestimmten/eingeschränkt" erstellen (d. h. Vorinstallations- oder Retail Store), in dem der Endbenutzer ist die endgültige Konfiguration und Dokumentieren Sie Ihre Kunden, die sie müssen [erhalten eine Zertifikat für WDP, und installieren Sie es WDP und eine Verbindung herstellen Browser sowohl Kennwörter WDP geändert werden](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), und klicken Sie dann mithilfe von WDP in dieser Instanz mit schmalen kommerziellen zulässig ist. Einzelhandel-Images in diesem Szenario sollte dennoch *nicht* IOT_TOOLKIT u. sollten IOT_WEBBEXTN Paket verwenden, um WDP zu erhalten. 

## <a name="shared-documentation"></a>Shared-Dokumentation
WDP ist ein Tool für Entwickler von Windows 10-Geräten gemeinsam verwendet. Jedes Produkt verfügt über eine eigene spezielle Features, aber die Kernfunktionalitäten sind identisch.
Dokumentation für die wichtigsten Funktionen befinden sich die [Windows Device Portal-Seite "Übersicht"](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal). Der Rest der folgenden Dokumentation werden bestimmte IoT.

## <a name="set-up"></a>Einrichtung

Es gibt zwei Möglichkeiten, wechseln die Windows Device Portal betriebsbereit zu machen.

### <a name="1-windows-10-iot-dashboard"></a>1. Windows 10 IoT Dashboard

Zunächst sollten Sie zum Herunterladen der [Windows 10 IoT-Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), ein Tool für Entwickler, die es einfach macht, neue Geräte einrichten. Nachdem Sie das Dashboard verwendet haben, um ein Windows 10 IoT Core-Image auf Ihrem Gerät zu aktualisieren, überprüfen Sie, dass Ihr Gerät unter "Meine Geräte" angezeigt wird, wird ein. 

Verwenden Sie dort die Auslassungspunkte klicken Sie unter "Aktionen" auf "Öffnen in Device Portal". Von dort aus gelangen Sie auf die Device Portal-Authentifizierungsseite, es sei denn, Sie zuerst die Anmeldeinformationen geändert, werden die standardmäßigen Anmeldeinformationen: 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2. Browser
Wenn Sie können nicht finden im Dashboard Ihres Geräts oder über das Dashboard zu überspringen möchten, können Sie auch im Device Portal öffnen, durch die IP-Adresse Ihres Geräts plus Eingabe `:8080` am Ende. Bei ordnungsgemäßer Durchführung, sollte es etwa wie folgt aussehen:


   ![Geräte IoTDashboard anzeigen](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>IoT-spezifischen features

### <a name="device-settings"></a>Einstellungen für Geräte

IoT Core Fügt ein Kontrollkästchen zum Aktivieren oder Deaktivieren der [Bildschirmtastatur](../develop-your-app/OnScreenKeyboard.md)
> [!NOTE]
> Dieses Kontrollkästchen hat es sich um ein bekanntes Problem, in dem sie "von leuchtet," überprüft, um nicht aktiviert. Bitte aktualisieren Sie die Seite (F5), nach dem Klicken auf, um sicherzustellen, dass das Kontrollkästchen mit den gewünschten Zustand angezeigt wird.

### <a name="apps"></a>Apps
Stellt Funktionen für Installation/Deinstallation für AppX-Paketen und Paketen auf Ihrem Gerät bereit.
![App-Liste](../media/DevicePortal/AppList.png)

IoT Core ist einzigartig, da es nur eine Vordergrund-app auf einmal ausführen kann. Die app-Liste geändert wird, um sicherzustellen, dass dies der Fall ist. Unter den **Start** Spalte, Sie können auswählen, so viele Programme im Hintergrund standardmäßig gestartet, aber kann nur eine Anwendung im Vordergrund festgelegt.  

### <a name="app-file-explorer"></a>App-Datei-Explorer

Die app-Datei-Explorer zeigt die Verzeichnisse, dass Ihre apps zugreifen können.

* CameraRoll wird von allen apps gemeinsam genutzt.
* Dokumente von allen apps gemeinsam genutzt wird
* LocalAppData enthält Ordner für jede app spezifisch. In diesem Ordner werden auf dem gleichen Namen wie Ihre app und anderen apps nicht verfügbar.

### <a name="debugging"></a>Debuggen

#### <a name="kernel-dumps"></a>Kernel-dumps
![Debuggen mit Kernel-dumps](../media/DevicePortal/Debug1.png)

Alle Systemabstürze werden automatisch protokolliert und sind verfügbar, um über das Web-Management-Tool anzuzeigen.  Dann können die Kernelabbild herunterladen und versucht zu ermitteln, was vor sich geht.

#### <a name="process-dumps"></a>Prozessdumps
![Debuggen mit prozessdumps](../media/DevicePortal/Debug2.png)

Dies entspricht in Dumps für Live-Kernel, aber die Prozesse im Benutzermodus. Klicken auf die **herunterladen** Schaltfläche führt dazu, dass einen "Minidump" und der gesamte Status dieses Prozesses wird heruntergeladen werden. Dies ist gut für das Debuggen von hängenden Prozessen.

#### <a name="kernel-crash-settings"></a>Absturz kerneleinstellungen
![Absturz kerneleinstellungen](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>Bluetooth
Auf dieser Seite erfahren Sie, alle gekoppelten Bluetooth-Geräte und alle Geräte, die die erkannt werden. Um eine andere Bluetooth-Gerät gekoppelt werden, setzen Sie das Gerät im Modus zum Verbinden, und warten Sie, bis er in der Liste der verfügbaren Geräte angezeigt werden.  
![Liste der Bluetooth-Geräte](../media/DevicePortal/Bluetooth.png)

Klicken Sie auf **Paar Link** um das Gerät zu koppeln. Wenn das Gerät eine PIN anfordert, für die Paarung, tritt ein Popup mit der ein Meldungsfeld mit der PIN. Sobald das Gerät verbunden ist, wird es in der Liste der gepaarten Geräte angezeigt. Sie können un-Paar des Geräts, indem Sie durch Klicken auf **entfernen**. 

Nachdem Sie auf der Seite "Bluetooth" navigieren, wird Ihr Gerät von anderen Geräten erkannt werden. Sie können auch auf Ihrem PC/Telefon zu finden und verbinden Sie es von dort aus.

Weitere Informationen zu Bluetooth finden Sie auf die [Bluetooth-Seite](https://go.microsoft.com/fwlink/?linkid=823223).

### <a name="iot-onboarding"></a>IoT-Onboarding

IoT-Onboarding stellt Unterstützung für die Konfiguration eines IoT-Geräts Wi-Fi-Konnektivitätsoptionen.

**(Internet Connection Sharing, ICS)** gemeinsame Nutzung der Internetverbindung können Sie den Zugriff auf das Internet Ihres Geräts mit anderen Geräten, die mit dem Gerät verbunden sind, über die Wi-Fi-SoftAP nutzen.
Um dieses Feature verwenden zu können, muss Ihr Windows 10 IoT-Gerät (z. B. über eine Kabelverbindung für die LAN) mit dem Internet zugreifen.  In "Onboarding-Konnektivität > -> SoftAP Einstellungen auf"aktivieren"und die SSID-Namen und das Kennwort fest.  Wählen Sie dann in "Verbindungen -> gemeinsame Nutzung der Internetverbindung" für "Zugriff auf Point-Adapter", wählen Sie "Microsoft Wi-FI Direct virtuellen Adapter #2" und "gemeinsam genutzten Netzwerkadapter" Ihren verkabelte Ethernet-Adapter ein.  Klicken Sie abschließend auf "start SAS".  Nach dem Start der SoftAP auf Ihrem Windows 10 IoT-Gerät Verbindung ein separates WLAN-fähiges Gerät.  Nach dem Herstellen einer Verbindung werden Ihre separaten WLAN-fähiges Geräts über Ihr Windows 10 IoT-Gerät eine Verbindung mit dem Internet herstellen können.

> [!NOTE]
> Gemeinsam genutzter Internetverbindung ist deaktiviert, wenn ein WLAN-Profil auf dem Gerät vorhanden ist. Beispielsweise werden gemeinsam genutzter Internetverbindung deaktiviert werden, wenn Sie eine Verbindung mit einem Wi-Fi-Zugriffspunkt herstellen und überprüfen Sie "Create-Profil (automatisch erneut verbinden)".

**Einstellungen für SoftAP** der SoftAP-Einstellungen können Sie steuern, ob Ihres Geräts SoftAP aktiviert ist.  Es bietet auch eine Möglichkeit für die Konfiguration Ihrer SoftAP die SSID und die WPA2-PSK Schlüssel dem von einem anderen Gerät die Verbindung der SoftAP erforderlich sind.

**Einstellungen für die Integration von AllJoyn** der AllJoyn-Onboarding-Einstellungen können Sie steuern, ob Ihres Geräts Wi-Fi-Verbindung kann über Ihres Geräts AllJoyn Onboarding Producer konfiguriert.  Wenn ein separates Gerät mit einer AllJoyn Onboarding Consumer-Anwendung mit Ihrem Windows 10 IoT-SoftAP verbunden ist, kann AllJoyn-Onboarding-Consumer-Anwendung so konfigurieren Sie Ihre IoT-Geräte, WLAN-Adapter verwendet werden.  Wenn aktiviert, verwendet die app AllJoyn Onboarding Producer (IoTOnboarding) die Authentifizierungsmethode ECDHE_NULL. 

> [!NOTE]
> AllJoyn mit Integration mit Windows 10 IoT 10.0.14393 erstellt werden soll, oder zuvor erfordert eine Aktualisierung der <strong>IotOnboarding</strong> Beispiel möglicherweise [hier zum Download](https://github.com/ms-iot/samples).

![Onboarding auf AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding auf gemeinsam genutzter Internetverbindung](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> Access Point-Adapter ist der WLAN-Adapter, die als ein WLAN-Zugriffspunkt (sie hat in der Regel eine IP-Adresse wie 192.168.137.1) fungieren.
> Gemeinsam genutzten Netzwerkadapter ist ein Adapter, die mit dem Internet verbindet (z. B.: Ethernet-Adapter).

![Integrieren in Soft AP](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> SoftAP SSID wird automatisch von "AJ_" verwendet werden, wenn es sich bei AllJoyn Onboarding aktiviert ist, und die MAC-Adresse des WLAN-Adapters angehängt sein. Die Passphrase SoftAP muss zwischen 8 und 63 ASCII-Zeichen sein.


### <a name="tpm-configuration"></a>TPM-Konfiguration
Das Trusted Platform Module (TPM) ist eine kryptografische Coprozessor, einschließlich der Funktionen für die zufallszahlengenerierung, sicheren Generierung von kryptografischen Schlüsseln und Einschränkung ihrer Verwendung. Darüber hinaus Funktionen wie remote Attestation und sealed-Speicher. Weitere Informationen zu den TPM und die Sicherheit unter IoT Core finden Sie auf die [die Entwicklung von sicheren Geräten](../secure-your-device/BuildingSecureDevices.md) Seite und die [TPM](../secure-your-device/TPM.md) Seite.

> [!IMPORTANT]
> Limpet.exe verwendet Windows IoT Core angehören. Ab Oktober 2018 können sie steht jetzt als ein open-Source-Projekt wird auf [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client).

Um Tests einfacher zu machen, wir verfügen über eine nicht signierte vorab erstellte Version Limpet.exe verfügbar und kann direkt von WDP heruntergeladen werden. Sie müssen nur die Registerkarte "TPM-Konfiguration" und "Neueste installieren" klicken. 

> [!NOTE]
> Diese Version von Limpet.exe sollte nicht mit endgültigen Produkt ausgeliefert werden. Stattdessen müssen Sie open Source-Projekt erstellen, Signieren und Packen sie mit Ihrem Image.

### <a name="azure-clients-configuration"></a>Konfiguration von Azure Clients

IoT-Geräte können per Remotezugriff über Cloud-Dienste verwaltet werden. Azure bietet einen sehr umfangreichen Satz von Diensten für derartige Szenarien bieten. Wir haben eine geräteverwaltungsclient erstellt, die mehrere Windows-Verwaltungsfunktionen zur Verfügung und ergänzt, die die von Azure Device Provisioning Service (DPS) und des Azure IoT Hub-Dienst auf der Windows-Plattform.

Die Clients werden als open Source-Projekte bereitgestellt werden. Um leichter testen, werden wir vorab erstellte Binärdateien bereitstellen. Sie können sich auf die Registerkarte "Azure-Clients" in WDP zu installieren. Führen Sie die Binärdateien zu testen.

> [!NOTE]
> Diese Version der Tools sollten nicht mit der endgültigen Produkt ausgeliefert werden. Stattdessen müssen Sie open Source-Projekt erstellen, Signieren und Packen sie mit Ihrem Image.

In dieser Dokumentation wird aktualisiert, sobald die open-Source-Projekte für die Nutzung verfügbar sind.

### <a name="remote"></a>Fernbedienung
Die Windows IoT-Remoteserver ermöglicht finden Sie unter was auf ihrem Gerät angezeigt wird, ohne eine Verbindung eines physischen Monitors mit der Tastatur.


## <a name="additional-information"></a>Weitere Informationen 

### <a name="changing-the-default-port"></a>Ändern des Standardports
 
1. Starten Sie Powershell und [eine Verbindung mit Ihrem Gerät herstellen.](../connect-your-device/PowerShell.md)
2. Herunterladen [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, erstellen und kopieren Sie ihn auf Ihrem Gerät. 
3. Übernehmen des Besitzes des Registrierungsschlüssels für den Dienst durch Ausführen

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. Legen Sie den gewünschten Port durch Ändern der registrierungseinstellungen 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. Starten Sie den Dienst WebManagement mit folgenden oder durch einen Neustart des Geräts

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>Mithilfe von HTTPS 

Wenn Sie HTTPS verwenden möchten, zuerst nutzen Sie den Besitz des Registrierungsschlüssels, wie im vorherigen Abschnitt beschrieben und legen Sie die Registrierungsschlüssel HttpsPort und EncryptionMode wie unten gezeigt, und klicken Sie dann starten den Webmanagement-Dienst neu

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a>Datenbankbereitstellung Device Portal mit einem benutzerdefinierten SSL-Zertifikat

In der Windows 10 Creators Update hinzugefügt die Windows Device Portal eine Möglichkeit für Geräteadministratoren ein benutzerdefiniertes Zertifikat für die Verwendung in HTTPS-Kommunikation zu installieren.

Weitere Informationen, [finden Sie in der Dokumentation unter Windows Device Portal Dokumentation](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl). 


## <a name="additional-resources"></a>Zusätzliche Ressourcen
___ 

1. [Windows Device Portal-Seite "Übersicht"](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
