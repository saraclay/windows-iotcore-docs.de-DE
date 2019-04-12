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
# <a name="uefi-requirements"></a><span data-ttu-id="6ebea-104">UEFI-Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6ebea-104">UEFI Requirements</span></span>

<span data-ttu-id="6ebea-105">Die UEFI-Anforderungen für IoT Core sind ähnlich wie andere Windows-Editionen, z. B. Desktop.</span><span class="sxs-lookup"><span data-stu-id="6ebea-105">The UEFI requirements for IoT Core are similar to other windows editions like desktop.</span></span> <span data-ttu-id="6ebea-106">Finden Sie unter [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) Details und insbesondere [UEFI-Anforderungen für die Windows-Editionen auf SoC-Plattformen](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span><span class="sxs-lookup"><span data-stu-id="6ebea-106">See [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) for details and specifically see [UEFI requirements for Windows editions on SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span></span> 

## <a name="acpi-design"></a><span data-ttu-id="6ebea-107">ACPI-Entwurf</span><span class="sxs-lookup"><span data-stu-id="6ebea-107">ACPI Design</span></span>

<span data-ttu-id="6ebea-108">Finden Sie unter [Windows ACPI-Entwurfshandbuch für SoC-Plattformen](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) ausführliche Informationen, die ACPI-Anforderungen für IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6ebea-108">See [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) for the details on the ACPI requirements for IoT Core.</span></span>

## <a name="replacing-windows-boot-logo"></a><span data-ttu-id="6ebea-109">Ersetzen Sie dabei Windows-Start-Logo</span><span class="sxs-lookup"><span data-stu-id="6ebea-109">Replacing Windows Boot Logo</span></span>

<span data-ttu-id="6ebea-110">Es gibt mehrere Möglichkeiten, den Start-Logo zu ersetzen, das vom BIOS oder UEFI angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="6ebea-110">There are multiple ways to replace the boot logo that is displayed by the BIOS or UEFI:</span></span>

* <span data-ttu-id="6ebea-111">Eine Möglichkeit besteht darin Lizenz die UEFI oder einen Board Hersteller-Anbieter dafür bezahlen, und nehmen Sie Änderungen direkt an den UEFI-Quellcode.</span><span class="sxs-lookup"><span data-stu-id="6ebea-111">One way is to license the UEFI, or pay a board manufacturer vendor to do so, and make changes directly to the UEFI source code.</span></span>
* <span data-ttu-id="6ebea-112">Sie können auch auf Geräten, deren Implementierung von UEFI signierte ladbare UEFI-Treiber unterstützt, es ist ein Beispiel [hier](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) , die zeigt, wie erstellen einen Treiber, der das Start-Logo ersetzt, und geben Sie eine Tabelle BGRT Bootmgr damit starten Sie die Windows Prozess bleibt Ihr Logo vorhanden, während des Starts, anstatt ihn zu ersetzen mit dem Windows-Logo.</span><span class="sxs-lookup"><span data-stu-id="6ebea-112">Alternatively, on devices whose UEFI implementation supports signed loadable UEFI drivers there is a sample [here](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) that shows how to build a driver that replaces the boot logo and supply a BGRT table to bootmgr so that the Windows boot process leaves your logo in place during boot instead of replacing it with the Windows logo.</span></span>

## <a name="smbios-settings"></a><span data-ttu-id="6ebea-113">SMBIOS-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="6ebea-113">SMBIOS settings</span></span>

<span data-ttu-id="6ebea-114">Mindestens erforderliche SMBIOS-Einstellungen werden in beschrieben [OEM Lizenzanforderungen](OEMLicenseRequirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ebea-114">Minimum required SMBIOS settings are described in [OEM License Requirements](OEMLicenseRequirements.md).</span></span>

## <a name="io-bus-access"></a><span data-ttu-id="6ebea-115">E/a-Bus Zugriff</span><span class="sxs-lookup"><span data-stu-id="6ebea-115">I/O Bus Access</span></span>

<span data-ttu-id="6ebea-116">Windows IoT Core und IoT Enterprise können Anwendungen mit System-e/a-Pins für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="6ebea-116">Windows IoT Core and IoT Enterprise allow for user applications to interface with system I/O pins.</span></span> <span data-ttu-id="6ebea-117">Um dies zu ermöglichen, sind bestimmte Konfigurationsschritte in der Tabelle Element (ASSL) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6ebea-117">To enable this, specific configuration is required in the ASL table.</span></span> <span data-ttu-id="6ebea-118">Lesen [aktivieren Benutzermoduszugriff auf Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="6ebea-118">Read [Enable user mode access on Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) for more information.</span></span>

## <a name="recovery-trigger"></a><span data-ttu-id="6ebea-119">Recovery-Trigger</span><span class="sxs-lookup"><span data-stu-id="6ebea-119">Recovery Trigger</span></span>

<span data-ttu-id="6ebea-120">Überprüfen Sie [Wiederherstellungsoptionen für Windows 10 IoT Core](Recovery.md) und wenn Sie die Hardware-Trigger, um in den Wiederherstellungsmodus zu erhalten benötigen, müssen Sie ggf. dies in der UEFI-apps zu implementieren, und rufen Sie die Wiederherstellung durch Festlegen der erforderlichen Bootsequence vor dem Starten von Windows .</span><span class="sxs-lookup"><span data-stu-id="6ebea-120">Review [Windows 10 IoT Core Recovery Options](Recovery.md) and if you require hardware trigger to get into recovery mode, you may require to implement this in the UEFI apps and invoke recovery by setting the required bootsequence before windows boots.</span></span>

<span data-ttu-id="6ebea-121">Die Bootsequence erforderlich, um die Wiederherstellung Betriebssystem starten, wird unten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6ebea-121">The bootsequence required to boot into the recovery OS is given below</span></span>

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
