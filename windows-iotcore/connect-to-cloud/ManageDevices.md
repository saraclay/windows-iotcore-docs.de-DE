---
title: Verwalten Sie die Windows-Geräte mit Azure IoT Hub
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Erfahren Sie, wie Sie Ihre Windows-Geräte mit Azure IoT Hub verwalten.
keywords: Windows Iot, Azure, DM, geräteverwaltung, Azure IoT Hub, Iothub, Integrität für Geräte
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513154"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="89b13-104">Verwalten Sie die Windows-Geräte mit Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="89b13-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="89b13-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="89b13-105">Overview</span></span>
<span data-ttu-id="89b13-106">Geräteverwaltung (DM) ermöglicht den Operatoren, Remote zu konfigurieren und gleichzeitig sehr großen Mengen von IoT-Geräten zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="89b13-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="89b13-107">Konfiguration für die Geräte kann auf Geräten per Push übertragen werden, ob die Zielgeräte online oder offline sind.</span><span class="sxs-lookup"><span data-stu-id="89b13-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="89b13-108">Wenn das Gerät offline ist übernehmen es die neue Konfiguration die beim erneuten Herstellen der Verbindung.</span><span class="sxs-lookup"><span data-stu-id="89b13-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="89b13-109">Gerät-Operatoren können auch abrufen, den Status eines jeden Geräts, z. B., ob Updates für die Konfiguration von Geräten erfolgreich oder nicht angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="89b13-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="89b13-110">Aktivieren diese Funktionen für IoT-Geräte erfordert eine Central, robust, und zuverlässigen Mechanismus zum Speichern die Konfigurationsdaten bereitstellen, die Zielgeräte und Gerätestatus überwachen – nach Maß.</span><span class="sxs-lookup"><span data-stu-id="89b13-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="89b13-111">Eine vollständige Lösung benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="89b13-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="89b13-112">Zuverlässig/skalierbare Cloud-Dienst in die gewünschten und gemeldeten Status der verschiedenen Geräte zu speichern.</span><span class="sxs-lookup"><span data-stu-id="89b13-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="89b13-113">Azure IoT Hub und Azure-Geräteverwaltung bieten einen hochgradig skalierbaren und effizienten Cloud-Dienst für die Verwaltung von Millionen von Geräten.</span><span class="sxs-lookup"><span data-stu-id="89b13-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="89b13-114">Ein Client, der auf dem Gerät ausgeführt wird und anwenden die gewünschte Konfiguration und kann den Status des Geräts zu melden.</span><span class="sxs-lookup"><span data-stu-id="89b13-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="89b13-115">Die Windows IoT Azure DM-Client (eine Open-source-SDK und Runtime) in Verbindung mit Azure IoT Hub-Instanz, anwenden und melden kann einen großen Satz allgemeiner, manchmal kritisch, Windows-Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="89b13-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="89b13-116">Ein Portal oder eine Anwendung, die durch den Operator zum Konfigurieren und Abfragen der Geräte per Remotezugriff verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="89b13-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="89b13-117">Dies muss für Geräte, die vom Gerät OEM oder Operator angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="89b13-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="89b13-118">Als Teil dieser Lösung wir außerdem Geben Sie ein open-Source-Datenmodell und Beispiel-Implementierung für die einfachere Interaktion mit der IoT Hub-Speicher und der Windows-IoT-Client.</span><span class="sxs-lookup"><span data-stu-id="89b13-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="89b13-119">Weitere Informationen zur geräteverwaltung für Windows-Geräte finden Sie auf der Hauptseite [Geräteverwaltungsclient Repository](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span><span class="sxs-lookup"><span data-stu-id="89b13-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
