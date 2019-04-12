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
# <a name="configure-your-device-to-wake-on-touch"></a>Konfigurieren Sie das Gerät, auf die Toucheingabe zu aktivieren.

In einigen Szenarien möchten Sie Ihre Gerätebildschirm nicht in Gebrauch deaktivieren und aktivieren Sie schnell, wenn ein Benutzer den Touchscreen berührt. Dieses Dokument beschreibt, wie Sie Ihr Gerät für dieses Szenario zu konfigurieren.

## <a name="setting-a-video-idle-timeout"></a>Ein video Leerlauftimeout festlegen

Sie können den Bildschirm, um nach einem bestimmten Zeitraum der Inaktivität deaktivieren, indem Sie ein video Leerlauftimeout Einstellung konfigurieren. Wenn der Benutzer nicht mit dem Gerät für eine angegebene Zeitdauer interagiert hat, wird der Bildschirm ausgeschaltet. Dadurch wird das Gerät ein niedrigen Energiestatus durch Ausschalten von Komponenten, die im Zusammenhang mit der Anzeige eingeben.

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

Weitere Informationen finden Sie unter [Anzeige Leerlauftimeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) und [Anzeige Energiesparmodus und Ruhezustand leerlauftimer](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).

## <a name="disabling-modern-standby"></a>Deaktivieren moderne standby

Auf AoAC-Systemen (enthält alle ARM-Systeme), das System wechselt automatisch in [moderne Standby](/windows-hardware/design/device-experiences/modern-standby) bei der Anzeige wird deaktiviert. Wenn ein System moderne Standbymodus aktiviert ist, können sie nur von bestimmten Eingaben reaktiviert werden. Dies ist nicht erschöpfende Liste, aber diese Eingaben enthalten Drücken des Netzschalters, öffnen die Reaktivierung des Ruhezustands auf einem Laptop oder durch Klicken mit der Maus. Auf dem Bildschirm wird das Gerät aus dem modernen Standbymodus nicht aktivieren. Wenn Ihr Gerät von Touch reaktiviert werden sollen, müssen Sie das Gerät so, dass nicht moderne in den Standbymodus zu konfigurieren. Um moderne Standby zu deaktivieren, legen Sie die folgenden Registrierungsschlüssel und ein Neustart aus.

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
Deaktivieren der modernen Standby kann Stromverbrauch auswirken, wenn das System im Leerlauf befindet. Sie sollten den Stromverbrauch des Systems mit modernen Standby aktiviert und deaktiviert, bevor Sie bei der Entscheidung, deaktivieren Sie moderne Standby messen.

Moderne Standbymodus ist ein Software-Mechanismus, der versucht, ein Stiller Systemaktivität so weit wie möglich, wodurch die Hardware ein niedrigen Energiestatus eingeben. Theoretisch kann ein ausreichend quiet-Gerät mit modernen standby deaktiviert die gleichen niedrigen Energieverbrauch als ein Gerät in modernen Standby erreichen. Es ist wichtig, die Minimierung von Hintergrundaktivitäten, die Software von Timern und periodischen Aufgaben einschließlich, ob modernen Standby deaktiviert ist.
