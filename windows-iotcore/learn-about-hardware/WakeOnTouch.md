---
title: Wake-on-Touch
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: Konfigurieren Sie das Gerät, auf die Toucheingabe zu aktivieren.
keywords: Windows Iot, Bildschirm, Ruhezustand, Aktivierung, Touch, Standby, power
ms.custom: RS5
ms.openlocfilehash: 7c0fc9613f1b1ed45fb8d69a18d82b034eb366fb
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513025"
---
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="44787-104">Konfigurieren Sie das Gerät, auf die Toucheingabe zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="44787-104">Configure your device to wake on touch</span></span>

<span data-ttu-id="44787-105">In einigen Szenarien möchten Sie Ihre Gerätebildschirm nicht in Gebrauch deaktivieren und aktivieren Sie schnell, wenn ein Benutzer den Touchscreen berührt.</span><span class="sxs-lookup"><span data-stu-id="44787-105">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="44787-106">Dieses Dokument beschreibt, wie Sie Ihr Gerät für dieses Szenario zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="44787-106">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="44787-107">Ein video Leerlauftimeout festlegen</span><span class="sxs-lookup"><span data-stu-id="44787-107">Setting a video idle timeout</span></span>

<span data-ttu-id="44787-108">Sie können den Bildschirm, um nach einem bestimmten Zeitraum der Inaktivität deaktivieren, indem Sie ein video Leerlauftimeout Einstellung konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="44787-108">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="44787-109">Wenn der Benutzer nicht mit dem Gerät für eine angegebene Zeitdauer interagiert hat, wird der Bildschirm ausgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="44787-109">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="44787-110">Dadurch wird das Gerät ein niedrigen Energiestatus durch Ausschalten von Komponenten, die im Zusammenhang mit der Anzeige eingeben.</span><span class="sxs-lookup"><span data-stu-id="44787-110">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="44787-111">Weitere Informationen finden Sie unter [Anzeige Leerlauftimeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) und [Anzeige Energiesparmodus und Ruhezustand leerlauftimer](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span><span class="sxs-lookup"><span data-stu-id="44787-111">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="44787-112">Deaktivieren moderne standby</span><span class="sxs-lookup"><span data-stu-id="44787-112">Disabling modern standby</span></span>

<span data-ttu-id="44787-113">Auf AoAC-Systemen (enthält alle ARM-Systeme), das System wechselt automatisch in [moderne Standby](/windows-hardware/design/device-experiences/modern-standby) bei der Anzeige wird deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="44787-113">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="44787-114">Wenn ein System moderne Standbymodus aktiviert ist, können sie nur von bestimmten Eingaben reaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="44787-114">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="44787-115">Dies ist nicht erschöpfende Liste, aber diese Eingaben enthalten Drücken des Netzschalters, öffnen die Reaktivierung des Ruhezustands auf einem Laptop oder durch Klicken mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="44787-115">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="44787-116">Auf dem Bildschirm wird das Gerät aus dem modernen Standbymodus nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="44787-116">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="44787-117">Wenn Ihr Gerät von Touch reaktiviert werden sollen, müssen Sie das Gerät so, dass nicht moderne in den Standbymodus zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="44787-117">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="44787-118">Um moderne Standby zu deaktivieren, legen Sie die folgenden Registrierungsschlüssel und ein Neustart aus.</span><span class="sxs-lookup"><span data-stu-id="44787-118">To disable modern standby, set the following registry key and reboot.</span></span>

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="44787-119">Deaktivieren der modernen Standby kann Stromverbrauch auswirken, wenn das System im Leerlauf befindet.</span><span class="sxs-lookup"><span data-stu-id="44787-119">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="44787-120">Sie sollten den Stromverbrauch des Systems mit modernen Standby aktiviert und deaktiviert, bevor Sie bei der Entscheidung, deaktivieren Sie moderne Standby messen.</span><span class="sxs-lookup"><span data-stu-id="44787-120">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="44787-121">Moderne Standbymodus ist ein Software-Mechanismus, der versucht, ein Stiller Systemaktivität so weit wie möglich, wodurch die Hardware ein niedrigen Energiestatus eingeben.</span><span class="sxs-lookup"><span data-stu-id="44787-121">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="44787-122">Theoretisch kann ein ausreichend quiet-Gerät mit modernen standby deaktiviert die gleichen niedrigen Energieverbrauch als ein Gerät in modernen Standby erreichen.</span><span class="sxs-lookup"><span data-stu-id="44787-122">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="44787-123">Es ist wichtig, die Minimierung von Hintergrundaktivitäten, die Software von Timern und periodischen Aufgaben einschließlich, ob modernen Standby deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="44787-123">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
