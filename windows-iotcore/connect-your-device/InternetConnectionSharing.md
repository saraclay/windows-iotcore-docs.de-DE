---
title: Gemeinsame Nutzung der Internetverbindung
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Aktivieren und konfigurieren die gemeinsame Nutzung unter Windows IoT Core.
keywords: Windows Iot, Internet Connection Sharing, ICS, Device Portal
ms.openlocfilehash: dcf51d98bc618c1a843c43b2d33fc8f832ef73d4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512970"
---
# <a name="internet-connection-sharing"></a>Gemeinsame Nutzung der Internetverbindung

In diesem Dokument wird beschrieben, wie der Internetverbindungsfreigabe (gemeinsam genutzter Internetverbindung) unter Windows IoT Core aktiviert werden kann. Die NetworkTetheringManager-API können Entwickler um gemeinsam genutzter Internetverbindung programmgesteuert zu konfigurieren. Die API finden Sie auf die [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) Klasse.
Bei Verwendung einer der der [Release-Image von Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS kann auch mithilfe des Device Portal konfiguriert werden.

> [!IMPORTANT]
> Ein WLAN-Profil muss zuerst erstellt und die folgenden müssen dem Manifest hinzugefügt werden:
`<DeviceCapability Name="wiFiControl" />`

Lesen Sie Sie für das Tutorial Freigabe der [Windows IoT Core Release von November 2015](InternetConnectionSharingNov2015.md) Dokument.

## <a name="configuring-ics-using-the-device-portal"></a>Konfigurieren von Clients mithilfe des Device portal
Finden Sie Dokumentation zum [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).

## <a name="ics-code-sample"></a>ICS-Codebeispiel
Im folgenden Codebeispiel wird veranschaulicht, wie die [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) -API wird verwendet, um eine Ethernet-Verbindung über Wi-Fi-Freigabe zu starten. Die CreateFromConnectionProfile-Methode akzeptiert die Argumente, die die öffentliche und private-Schnittstelle angegeben. In jedem Fällen einer Fehlkonfiguration z. B. die Wi-Fi-Radio ist deaktiviert, oder -Ethernet-über Konnektivität eingeschränkte verfügt, schützt dann der Versuch, die Nutzung der Internetverbindung starten einen geeigneten Fehlercode bezieht sich auf dieses Szenario.

```
using Windows.Networking.NetworkOperators;
using Windows.Networking.Connectivity; 
 
// Find the Ethernet profile (IANA Type 6)
var connectionProfiles = NetworkInformation.GetConnectionProfiles(); 
var ethernetConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 6); 

// Find an 802.11 wireless network interface (IANA Type 71)
var wirelessConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 71);
var targetNetworkAdapter = wirelessConnectionProfile.NetworkAdapter;

if (ethernetConnectionProfile != null && targetNetworkAdapter != null)
{
    var tetheringManager = NetworkOperatorTetheringManager.CreateFromConnectionProfile(ethernetConnectionProfile, targetNetworkAdapter); 

    var result = await tetheringManager.StartTetheringAsync(); 
    if (result.Status == TetheringOperationStatus.Success)
    {
        UpdateUI();
    }
    else
    {
        ProcessTetheringError(result);
    }
}
```
