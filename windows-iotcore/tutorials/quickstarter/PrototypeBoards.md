---
title: Vorgeschlagene Prototypboards
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: Informationen Sie zu den vorgeschlagenen prototypboards für Windows 10 IoT.
keywords: Windows Iot, Entwicklung Geräten und Boards, Raspberry Pi 2, Raspberry Pi 3, Minnowboard Max, Dragonboard
ms.openlocfilehash: fc13f44a183e79a4c3f7381c3a12d8b5dcba8895
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512298"
---
# <a name="suggested-prototype-boards"></a>Vorgeschlagene Prototypboards

## <a name="windows-10-iot-core-development-devices"></a>Geräte für Windows 10 IoT Core-Entwicklung
Im folgenden finden Sie Boards, die wir empfehlen, um Ihnen den Einstieg in Windows 10 IoT Core erleichtern. Diese Boards bieten ein Bild enthält vollständige Flash-Update (FFU), und Erstellen von Prototypen schneller mit einer vorgefertigten Images und dadurch sorget er für Windows 10 IoT Core blinkende ein Kinderspiel.

> [!IMPORTANT]
> Sie müssen eigene Images erstellen und verwenden nicht die bereitgestellten Bilder unten auf, wenn Sie planen, Ihr Gerät kommerziell.

> [!NOTE]
> Der Raspberry Pi 3 b + eingeschränkter Kompatibilität mit Windows 10 IoT Core. Lesen Sie die [Anmerkungen zu dieser Version](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/insider/17744) für Weitere Informationen. Verwenden Sie für eine vollständige Windows 10 IoT Core-Oberfläche ein Raspberry Pi 3-b, DragonBoard, Up2-Board oder NXP-Gerät. 


| Boards | Weitere Informationen | FFU Link | Einrichten | Beginnen |
|-----------|----------|---------|---------|---------|---------|-------|
| [Quadrat AAEON einrichten](https://up-board.org/upsquared/specifications/) | [Board-Website](https://up-shop.org/28-up-squared) | [FFU herunterladen](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) | [eMMC (für die sich im Quadrat, Intel)](DeviceSetup.md#flashing-with-emmc-for-up-squared-other-intel-devices) | [Kommerzialisierung](https://up-shop.org/home/270-up-squared.html) | 
| [DragonBoard 410c](https://developer.qualcomm.com/hardware/dragonboard-410c) | [Pfeil nach Standort](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | [FFU herunterladen](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [IoT-Dashboard](DeviceSetup.md#using-the-iot-dashboard-dragonboard-410c),<br>[eMMC (für DragonBoard Qualcomm 410c)](DeviceSetup.md#flashing-with-emmc-for-up-squared-other-intel-devices) | [Kommerzialisierung](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | 
| [MinnowBoard Turbot](https://minnowboard.org) | [Minnowboard-Website](https://minnowboard.org/get-a-board) | [FFU herunterladen](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [IoT-Dashboard](DeviceSetup.md#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | Nicht zutreffend |
| [NXP i.MX 6](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [NXP-Website](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [FFU herunterladen](https://github.com/ms-iot/imx-iotcore) | [IoT-Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Kommerzialisierung](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | 
| [NXP i.MX 7](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [NXP-Website](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [FFU herunterladen](https://github.com/ms-iot/imx-iotcore) | [IoT-Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Kommerzialisierung](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | 
| [NXP i.MX 8 Min./8 Min. Mini](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [NXP-Website](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [FFU herunterladen](https://github.com/ms-iot/imx-iotcore) | [IoT-Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Dev-Kit 8 Min.](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) oder [kleine Entwickler-Kit 8 Min.](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-mini-applications-processor:8MMINILPD4-EVK) |
| [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/)<br> (1.2 nicht unterstützt) | [Raspberry Pi-Website](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/) | [FFU herunterladen](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [IoT-Dashboard (Raspberry Pi, MinnowBoard)](DeviceSetup.md#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Adafruit Kit](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/adafruitkit) | 
| [Raspberry Pi 3B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)<br> (3 b + ist eine nicht unterstützte Technische Vorschau) | [Raspberry Pi-Website](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) | [FFU herunterladen](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [IoT-Dashboard](DeviceSetup.md#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Adafruit Kit](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/adafruitkit) |
