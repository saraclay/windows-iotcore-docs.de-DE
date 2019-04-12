---
title: Azure IoT Device Management
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Weitere Informationen zum Verwalten Ihrer Geräte mithilfe von Azure IoT-Geräteverwaltung und Windows IoT.
keywords: Windows Iot, Azure IoT Azure Device Management, geräteverwaltung
ms.openlocfilehash: eb8f99c91ec5d4b6bdb27d7aa0b1cd7e7f20cc2b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513249"
---
# <a name="azure-iot-device-management"></a>Azure IoT Device Management

Wenn es an angeschlossene Geräte geht, ist die remote geräteverwaltung eine der wichtigsten Features von Systemoperatoren verwendet. Sie können Operatoren neu konfigurieren und Aktualisieren von Software und Parameter des Geräts Remote ohne lokale, physische Zugriff auf das Gerät haben. Mit Windows 10 IoT Core können OEMs Geräte erstellen, die außerhalb der Kontrollkästchen für diese Funktionen zu bieten. Windows 10 IoT Core als auch von anderen Windows 10-Versionen bereits bietet Mobile Device Management (MDM) basierend auf [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management). Dies wird hauptsächlich in unternehmenslösungen mit Verwaltungstools wie SCCM oder Intune verwendet. Während dieser Lösungen gut geeignet für Geräte, die in einer unternehmensumgebung platziert sind, verfügt es über Herausforderungen in unterschiedlichen Einstellungen, die wir in IoT-Lösungen finden Sie unter. Diese Herausforderungen sind auch im IoT-Geräte, die Verwaltung der Lightweight-Geräte erfordern angezeigt. Für diese Geräte bietet Microsoft [über Azure IoT Hub-geräteverwaltung](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview).

## <a name="scalable-device-management-with-windows-iot"></a>Skalierbare-geräteverwaltung mit Windows IoT

Mit Windows IoT Core ausgeführt wird, auf Geräte wie heimanwendungen, HVAC-Systeme und andere besteht eine Notwendigkeit einer anpassbaren, light Weight geräteverwaltungslösung zur Verfügung. In der Windows-Ersteller-Edition, Microsoft ermöglicht [Azure IoT Hub-geräteverwaltung](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview). OEMs können den [Windows IoT Azure Clientbibliothek](https://aka.ms/iot-core-azure-dm-client) hinzuzufügende Verwaltungsfunktionen für Geräte mit ihren Azure IoT-Hub verbundene Geräte. Diese Bibliothek wird die standardmäßige Windows-Gerät-Management-Komponenten zugreifen ([Configuration Service Providers](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP).  OEMs können nun Geräte erstellen, die Unterstützung von SCCM, Intune und Azure IoT Hub für die geräteverwaltung und lassen sie ihre Kunden können den Typ DM-Lösung auswählen, die sie passt best. 

![Azure IoT Hub Device Management](../media/AzureIoTDM/azureDM.png)

## <a name="how-does-it-work"></a>Wie funktioniert das?

Die [Windows IoT Azure Clientbibliothek](https://aka.ms/iot-core-azure-dm-client) in der hostanwendung verknüpft ist. Es gibt die Azure IoT Hub-Verbindung für die Host-app frei. Wodurch zusätzliche Registrierung unnötige geräteverwaltung zu aktivieren. Die folgende Abbildung zeigt die Architektur für eine Azure IoT Hub-Geräteverwaltung-Lösung, die mit der Azure-Geräteverwaltung für Windows IoT-Clientbibliothek. 

![Azure-DM-Flussdiagramm](../media/AzureIoTDM/AzureDM-Architecture.png)

Microsoft bietet zwei Systemkomponenten, CommProxy.exe und SystemConfigurator.exe, der OEM muss in das Image des Geräts eingeschlossen werden sollen. Diese Komponenten erhalten Zugriff auf den CSPs. Die IoTDMClientLib ordnet die CSP-Schnittstelle auf Funktionen, die von Azure IoT Hub-geräteverwaltung genutzt werden können. Darüber hinaus DM-Funktionen, die einen CSP, z. B. Zeitzone nicht verwenden. Die IoTDMClientLib wird als eine open-Source-Komponente bereitgestellt. OEMs können es erweitern, um DM-Funktionen hinzuzufügen, die für ihr Gerät wie z. B. Konfigurationen für Sensoren oder Aktuatoren spezifisch sind. 

## <a name="device-health-attestation"></a>Integritätsnachweis für Geräte
Für einen sicheren Betrieb von IoT-Geräten ist es wichtig, um festzustellen, ob ein Gerät in einem vertrauenswürdigen und kompatiblen Zustand gestartet wird. Mit [Windows IoT Device Health Attestation (DHA)](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) Operatoren den Sicherheitsstatus eines Geräts zu überprüfen, und nehmen Sie geeignete Wartungsaktionen aus, bei Bedarf über [Azure IoT Hub-Geräteverwaltung](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md). DHA ist Teil der Windows IoT Core Azure Device Management-Client. Um den DHA-Funktion in Ihrer Lösung zu verwenden ist Zugriff auf den Microsoft-DHA-Dienst erforderlich. Ein Abonnement für den Dienst steht über den [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview).

### <a name="reference"></a>Referenz
[Integritätsnachweis für Geräte für Azure-IoT-DM](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)

[Bereitstellen von Azure-Ressourcen für den Integritätsnachweis für Geräte](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)


## <a name="how-to-get-started"></a>Informationen zum Einstieg?

Azure-Geräteverwaltung für Windows IoT-Clientbibliothek ist auf GitHub verfügbar. Neben dem Projekt IoTDMClientLib enthält es Beispiele zum schnellen Einstieg. Weitere Informationen finden Sie unter folgenden Links.

### <a name="project-github-page"></a>GitHub-Projektseite

[Windows IoT Azure Clientbibliothek](https://aka.ms/iot-core-azure-dm-client) ist auf GitHub verfügbar.

### <a name="dm-dashboard"></a>DM-Dashboard

[DM-Dashboard](https://aka.ms/iot-core-azure-dm-client-dashboard) ist eine Anwendung zum Testen der DM-Funktion auf einem Gerät. Die app eine Verbindung mit dem Gerät über Azure IoT Hub. Die app kann verwendet werden, um der DM-Funktionen des Geräts zu überprüfen. Es kann erweitert werden, um alle Drittanbieter-DM-Funktionen zu testen, die die IoTDMClientLib hinzugefügt wurden.

### <a name="dm-background-application"></a>DM-hintergrundanwendung

Die [DM-hintergrundanwendung](https://aka.ms/iot-core-azure-dm-client-backgroundapp) zeigt, wie die IoTDMClientLib in einer Anwendung verwendet werden kann, die eine Verbindung mit Azure IoT Hub herstellt und das als Hintergrund-app unter Windows IoT Core ausgeführt werden muss. 

### <a name="toaster-application"></a>Toaster-Anwendung

Die [Toaster Anwendung](https://aka.ms/iot-core-azure-dm-client-toasterapp), wie die geräteverwaltungs-Hintergrund-app oben ermöglicht Azure DM-Funktionen für ein Gerät. Diese app wird im Vordergrund ausgeführt und Zulassen des Zugriffs auf DM-Parameter und Funktionen über die UI-Geräte. 

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>Registrieren Ihres Geräts mit Azure Device bereitstellen Service (DPS) 

Azure Device Provisioning-Dienst können Kunden automatisch zuordnen, und konfigurieren Sie ein Gerät mit einem IoT Hub-Postproduktion. Für diesen Prozess benötigen Device Provisioning-Dienst eine eindeutige und challengeable-Geräte-ID, um das Gerät sicher zu konfigurieren, wenn das Gerät in den Vorgang eingefügt wird. Device Provisioning-Dienst verwendet der TPMS öffentlichen Endorsement Key (EKeyPub) für diesen Zweck. Um das Gerät bei DPS registrieren zu können, muss die EKeyPub vom Gerät abgegriffen werden. Die bevorzugte für diesen Schritt wird während der Produktion (während der End-of-Line-Test des Geräts). Allerdings kann der Prozess auch nach der Produktion erfolgen bei Bedarf.  

Microsoft bietet das Limpet-Tool, um den Registrierungsprozess für den Device Provisioning-Dienst zu optimieren. Je nach Ihrer Einrichtung Fertigung Wenn eine online-Verbindung verfügbar ist, das Gerät mit Limpet direkt mit dem Device Provisioning-Dienst registriert werden kann oder Limpet kann die EKeyPub für einen späteren, offline-Registrierung des Geräts mit Gerät sammeln Provisioning-Dienst.

Weitere Informationen zum Registrierungsprozess mit Limpet Device Provisioning-Dienst finden Sie unter den [Registrieren des Geräts im Device Provisioning-Dienst](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) im Abschnitt der [Limpet Dokumentation](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md). 

Projekt-Repository: [Limpet-Projekt-repository](https://github.com/ms-iot/azure-dm-client/) 


Lizenz: Limpet wird unter der MIT open-Source-Lizenz lizenziert. 

  
  

