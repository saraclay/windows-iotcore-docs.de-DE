---
title: USB-Peripheriegeräte Treiber installieren
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie ein Treiberpaket erstellen, und Installieren von Drittanbieter-Treiber auf Ihren Geräten.
keywords: Windows Iot, USB-Treiber, Peripheriegeräten, USB
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513585"
---
# <a name="install-usb-peripheral-drivers"></a>USB-Peripheriegeräte Treiber installieren
Führen Sie die folgenden Schritte zum Hinzufügen von Drittanbieter-Treiber (Usb) für Peripheriegeräte, z. B. USB-Mobile breitbandverbindungen Modems, Drucker, Scanner usw. aus. 

## <a name="step-1-get-drivers-from-pc"></a>Schritt 1: Abrufen von Treibern auf PC
___
Der Schritt zum Abrufen der X86 ist Version der Treiber von PC. Wenden Sie für ARM sich an den Lieferanten des Peripheriegerät rufen Sie die Sys/INF-Dateien.


1. Verbinden des Geräts mit der Windows-PCs

2. Installieren Sie den Treiber für das Gerät, auf dem PC

3. Wechseln Sie zum Geräte-Manager, wählen Sie dieses Gerät aus (siehe unter USB-Controller) und klicken Sie mit der rechten Maustaste auf ein, und wählen Sie Eigenschaften.

4. Wechseln Sie zur Registerkarte "Treiber" im Eigenschaftenfenster angezeigt, und klicken Sie auf Details zu den Treibern. Beachten Sie die Sys-Dateien aufgeführt.

5. Kopieren Sie die Sys-Dateien aus `C:\Windows\system32` und auch die zugehörigen inf-Datei aus `C:\Windows\Inf`. Sie finden die inf-Datei von führen für das Sys Dateiverweis in der `.inf` Dateien. Müssen Sie möglicherweise zusätzliche Dateien, die in der INF-Datei aufgelisteten kopieren und diese werden in der inf_filelist.txt-Datei erstellt, wenn aufgelistet `inf2pkg.cmd` im nächsten Schritt.


## <a name="step-2-create-a-driver-package"></a>Schritt 2: Erstellen eines Treiberpakets
___

Das Treiberpaket enthält die Verweise (InfSource) auf die Inf-Datei für den Treiber und auch eine Liste aller Dateien in der Inf-Datei verwiesen wird. Sie können den Treiber erstellen. mithilfe von wm.xml [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).

[Neue IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) die Paket-XML-Datei erstellt und auch direkt baut die Cab-Datei.

> [!NOTE]
> Windows IoT Core unterstützt nur [Universal INF "und" Universal Treiber](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).


Siehe auch: [Beispiel-Treiberpaket](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>Schritt 3: Installieren Sie auf dem Gerät
___

* Verbinden mit dem Gerät ([mithilfe von SSH](../connect-your-device/ssh.md) oder [mithilfe von Powershell](../connect-your-device/powershell.md))
* Kopieren der <filename>CAB-Datei an das Gerät in einem Verzeichnis sagen C:\OemInstall
* Initiieren Sie das Paket mit Staging `applyupdate -stage C:\OemInstall\<filename>.cab`. Beachten Sie, dass dieser Schritt wiederholt werden für jedes Paket, wenn Sie mehrere Pakete installiert haben.
* Die Pakete mithilfe von Commit `applyupdate -commit`.

Das Gerät wird neu gestartet, in dem Aktualisieren der Betriebssystemversion (mit Gears) zum Installieren der Pakete und wird neu zu Hauptbetriebssystems erneut gestartet. Dieser Vorgang kann einige Minuten dauern.

## <a name="step-4-check-status-of-driver"></a>Schritt 4: Überprüfen des Status des Treibers
___

* Starten Sie den [Powershell](../connect-your-device/PowerShell.md)
* Sie können den Status der installierten Treiber über die folgenden Powershell-Cmdlets abrufen.

    * [Get-PnpDevice](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [Get-PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
