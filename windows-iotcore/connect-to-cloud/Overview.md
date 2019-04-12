---
title: Übersicht über IoT in der Cloud
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über messaging, Sicherheit und geräteverwaltung, mit der Cloud mithilfe von Azure IoT.
keywords: Windows Iot, Cloud, Azure, Azure IoT Hub, messaging, UWP, universelle Windows-Plattform
ms.openlocfilehash: 4f38a45836e7c474655819988e447137249c2a7f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513562"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="96356-104">Übersicht über IoT in der Cloud</span><span class="sxs-lookup"><span data-stu-id="96356-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="96356-105">Das Internet der Dinge baut auf Cloud computing.</span><span class="sxs-lookup"><span data-stu-id="96356-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="96356-106">Die Möglichkeit, mit der Cloud kommunizieren, und leiten Erkenntnisse aus den Daten ist ein wesentlicher Bestandteil jeder IoT-Projekt.</span><span class="sxs-lookup"><span data-stu-id="96356-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="96356-107">Messaging</span><span class="sxs-lookup"><span data-stu-id="96356-107">Messaging</span></span>

<span data-ttu-id="96356-108">Kommunizieren in der Regel IoT-Geräte mit der Cloud oder in anderen, durch Senden und Empfangen von Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="96356-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="96356-109">Die Nutzlast einer Nachricht, die vom Gerät gesendet werden, in der cloud sind so klein wie ein Wert von einem Sensor und so groß wie eine Videodatei.</span><span class="sxs-lookup"><span data-stu-id="96356-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="96356-110">Eine Cloud, Gerät-Nachricht ist in der Regel einen Befehl, der das Gerät anweisen, eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="96356-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="96356-111">Message-Passing-Kommunikationsmuster Komplexität, die von einfachen unidirektionales messaging, komplexer Protokolle wie Anforderung-Antwort oder transaktional Protokolle wie z. B. das Zweiphasen-Commit bis hin variieren.</span><span class="sxs-lookup"><span data-stu-id="96356-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="96356-112">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="96356-112">Security</span></span>

<span data-ttu-id="96356-113">Sicherheit ist ein wesentlicher Bestandteil des IoT.</span><span class="sxs-lookup"><span data-stu-id="96356-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="96356-114">Für jede Nachricht müssen wir sicherstellen, dass es stammt (oder von empfangen wird) ein vertrauenswürdiges Gerät und nicht manipuliert wird.</span><span class="sxs-lookup"><span data-stu-id="96356-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="96356-115">Die Daten können Informationen enthalten, die verschlüsselt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="96356-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="96356-116">Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="96356-116">Azure IoT Hub</span></span>

<span data-ttu-id="96356-117">[Azure IoT-Hub](https://azure.microsoft.com/services/iot-hub/) ist Azure-Clouddienst, bietet zuverlässige und sichere Gerät-zu-Cloud und Cloud-zu-Gerät-messaging, die für Millionen von Geräten skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="96356-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="96356-118">Es bietet eine optimierte-Programmiermodell, mit der Sie erste Schritte mit minimalem Aufwand und skalieren Sie Ihre Lösung die Anforderungen zunehmen.</span><span class="sxs-lookup"><span data-stu-id="96356-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>

