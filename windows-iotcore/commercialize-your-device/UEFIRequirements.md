---
title: UEFI-Anforderungen
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, die UEFI-Anforderungen für Windows 10 IoT Core OS.
keywords: Windows Iot "," Images "," Anpassungen "," OEM-Anpassungen, UEFI
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512289"
---
# <a name="uefi-requirements"></a>UEFI-Anforderungen

Die UEFI-Anforderungen für IoT Core sind ähnlich wie andere Windows-Editionen, z. B. Desktop. Finden Sie unter [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) Details und insbesondere [UEFI-Anforderungen für die Windows-Editionen auf SoC-Plattformen](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms). 

## <a name="acpi-design"></a>ACPI-Entwurf

Finden Sie unter [Windows ACPI-Entwurfshandbuch für SoC-Plattformen](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) ausführliche Informationen, die ACPI-Anforderungen für IoT Core.

## <a name="replacing-windows-boot-logo"></a>Ersetzen Sie dabei Windows-Start-Logo

Es gibt mehrere Möglichkeiten, den Start-Logo zu ersetzen, das vom BIOS oder UEFI angezeigt wird:

* Eine Möglichkeit besteht darin Lizenz die UEFI oder einen Board Hersteller-Anbieter dafür bezahlen, und nehmen Sie Änderungen direkt an den UEFI-Quellcode.
* Sie können auch auf Geräten, deren Implementierung von UEFI signierte ladbare UEFI-Treiber unterstützt, es ist ein Beispiel [hier](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) , die zeigt, wie erstellen einen Treiber, der das Start-Logo ersetzt, und geben Sie eine Tabelle BGRT Bootmgr damit starten Sie die Windows Prozess bleibt Ihr Logo vorhanden, während des Starts, anstatt ihn zu ersetzen mit dem Windows-Logo.

## <a name="smbios-settings"></a>SMBIOS-Einstellungen

Mindestens erforderliche SMBIOS-Einstellungen werden in beschrieben [OEM Lizenzanforderungen](OEMLicenseRequirements.md).

## <a name="io-bus-access"></a>E/a-Bus Zugriff

Windows IoT Core und IoT Enterprise können Anwendungen mit System-e/a-Pins für den Benutzer. Um dies zu ermöglichen, sind bestimmte Konfigurationsschritte in der Tabelle Element (ASSL) erforderlich. Lesen [aktivieren Benutzermoduszugriff auf Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) für Weitere Informationen.

## <a name="recovery-trigger"></a>Recovery-Trigger

Überprüfen Sie [Wiederherstellungsoptionen für Windows 10 IoT Core](Recovery.md) und wenn Sie die Hardware-Trigger, um in den Wiederherstellungsmodus zu erhalten benötigen, müssen Sie ggf. dies in der UEFI-apps zu implementieren, und rufen Sie die Wiederherstellung durch Festlegen der erforderlichen Bootsequence vor dem Starten von Windows .

Die Bootsequence erforderlich, um die Wiederherstellung Betriebssystem starten, wird unten angezeigt.

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
