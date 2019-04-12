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
# <a name="internet-connection-sharing"></a><span data-ttu-id="f2dad-104">Gemeinsame Nutzung der Internetverbindung</span><span class="sxs-lookup"><span data-stu-id="f2dad-104">Internet connection sharing</span></span>

<span data-ttu-id="f2dad-105">In diesem Dokument wird beschrieben, wie der Internetverbindungsfreigabe (gemeinsam genutzter Internetverbindung) unter Windows IoT Core aktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="f2dad-105">This document describes how internet connection sharing (ICS) can be enabled on Windows IoT Core.</span></span> <span data-ttu-id="f2dad-106">Die NetworkTetheringManager-API können Entwickler um gemeinsam genutzter Internetverbindung programmgesteuert zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f2dad-106">Developers can use the NetworkTetheringManager API to configure ICS programmatically.</span></span> <span data-ttu-id="f2dad-107">Die API finden Sie auf die [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) Klasse.</span><span class="sxs-lookup"><span data-stu-id="f2dad-107">The API is described in the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) class.</span></span>
<span data-ttu-id="f2dad-108">Bei Verwendung einer der der [Release-Image von Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS kann auch mithilfe des Device Portal konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="f2dad-108">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS can also be configured using the device portal.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2dad-109">Ein WLAN-Profil muss zuerst erstellt und die folgenden müssen dem Manifest hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="f2dad-109">A WiFi profile must be created first and the following will need to be added to the manifest:</span></span>
`<DeviceCapability Name="wiFiControl" />`

<span data-ttu-id="f2dad-110">Lesen Sie Sie für das Tutorial Freigabe der [Windows IoT Core Release von November 2015](InternetConnectionSharingNov2015.md) Dokument.</span><span class="sxs-lookup"><span data-stu-id="f2dad-110">For the Sharing Tutorial, please view the [Windows IoT Core November 2015 Release](InternetConnectionSharingNov2015.md) document.</span></span>

## <a name="configuring-ics-using-the-device-portal"></a><span data-ttu-id="f2dad-111">Konfigurieren von Clients mithilfe des Device portal</span><span class="sxs-lookup"><span data-stu-id="f2dad-111">Configuring ICS using the device portal</span></span>
<span data-ttu-id="f2dad-112">Finden Sie Dokumentation zum [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span><span class="sxs-lookup"><span data-stu-id="f2dad-112">See documentation on [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span></span>

## <a name="ics-code-sample"></a><span data-ttu-id="f2dad-113">ICS-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f2dad-113">ICS code sample</span></span>
<span data-ttu-id="f2dad-114">Im folgenden Codebeispiel wird veranschaulicht, wie die [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) -API wird verwendet, um eine Ethernet-Verbindung über Wi-Fi-Freigabe zu starten.</span><span class="sxs-lookup"><span data-stu-id="f2dad-114">The code sample below demonstrates how the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API is used to start sharing an Ethernet connection over Wi-Fi.</span></span> <span data-ttu-id="f2dad-115">Die CreateFromConnectionProfile-Methode akzeptiert die Argumente, die die öffentliche und private-Schnittstelle angegeben.</span><span class="sxs-lookup"><span data-stu-id="f2dad-115">The CreateFromConnectionProfile method accepts arguments that specifies the public and private interface.</span></span> <span data-ttu-id="f2dad-116">In jedem Fällen einer Fehlkonfiguration z. B. die Wi-Fi-Radio ist deaktiviert, oder -Ethernet-über Konnektivität eingeschränkte verfügt, schützt dann der Versuch, die Nutzung der Internetverbindung starten einen geeigneten Fehlercode bezieht sich auf dieses Szenario.</span><span class="sxs-lookup"><span data-stu-id="f2dad-116">In any cases of misconfiguration, such as the Wi-Fi radio is turned off, or Ethernet has limited connectivity, then the attempt to start internet sharing conveys an appropriate error code pertaining to this scenario.</span></span>

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
