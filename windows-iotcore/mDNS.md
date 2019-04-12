---
title: Erste Schritte mit der mDNS-Responder-Beispielquelle
author: saraclay
ms.author: saclayt
ms.date: 02/26/2019
ms.topic: article
description: Informationen Sie zum Einstieg in die mDNS-Responder-Beispielquelle.
keywords: Windows 10 IoT Core, mDNS-Responder-Beispielquelle
ms.openlocfilehash: eacd22bf4d8a93948706e214fd48262c61c59a08
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512281"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="c849d-104">Erste Schritte mit mDNS-Responder-Beispielquelle</span><span class="sxs-lookup"><span data-stu-id="c849d-104">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="c849d-105">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="c849d-105">Getting started</span></span>

1.  <span data-ttu-id="c849d-106">Kompilieren Sie das Projekt *mDNSResponder* zu Get-mDNSResponder.exe, einem Dienst.</span><span class="sxs-lookup"><span data-stu-id="c849d-106">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="c849d-107">Der .exe auf den Zielcomputer kopieren und dann den Dienst zu registrieren und ausführen.</span><span class="sxs-lookup"><span data-stu-id="c849d-107">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="c849d-108">Führen Sie "mDNSResponder.exe /?"</span><span class="sxs-lookup"><span data-stu-id="c849d-108">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="c849d-109">So drucken Sie die Verwendung</span><span class="sxs-lookup"><span data-stu-id="c849d-109">to print the usage</span></span>
3.  <span data-ttu-id="c849d-110">Kompilieren Sie das Projekt *Dnssd*, dnssd.dll generiert</span><span class="sxs-lookup"><span data-stu-id="c849d-110">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="c849d-111">Kompilieren Sie das Projekt *mDNSUWP*.</span><span class="sxs-lookup"><span data-stu-id="c849d-111">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="c849d-112">Es ist keine UWP-Broker-Instanz, die im Gespräch mit dnssd.dll und generiert eine eigene Dll und winmd</span><span class="sxs-lookup"><span data-stu-id="c849d-112">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="c849d-113">Kompilieren Sie das Projekt *mDNSTest*, das ist ein Beispiel für UWP-app mDNSUWP nutzen und schließlich in mDNSResponder-Dienst kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="c849d-113">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="c849d-114">Diese UWP-app abhängig ist, auf der UWP-Broker und dnssd.dll (es gibt Skript so konfiguriert, dass um alles, was in der UWP-Appx-Ordner zu kopieren.)</span><span class="sxs-lookup"><span data-stu-id="c849d-114">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="c849d-115">MDNSTest bereitstellen/starten, legen Sie eine ID und klicken Sie auf registrieren, der Code reagieren muss 0 (Erfolg)</span><span class="sxs-lookup"><span data-stu-id="c849d-115">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="c849d-116">Wenn Sie einen beliebigen Bonjour Browser zur gleichen Zeit ausführen, sollte das neue Gerät für die (scheinbar) aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c849d-116">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![Registrierung für mDNS](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="c849d-118">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c849d-118">Resources</span></span>

* <span data-ttu-id="c849d-119">Herunterladen der Bonjour-kompatiblen mDNS Beantworter für Windows IoT (Beispielcode) [hier](https://go.microsoft.com/fwlink/?linkid=2077676).</span><span class="sxs-lookup"><span data-stu-id="c849d-119">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

