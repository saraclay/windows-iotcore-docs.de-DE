---
title: Universelle Gerätetreiber erstellen
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Erstellen von Universal Treiber, um die paketerstellung für die einzelnen Treiber für Geräte zu ermöglichen.
keywords: Windows Iot, universal-Treiber, Treiber, Windows 10 UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512329"
---
# <a name="universal-driver-creation"></a><span data-ttu-id="c5a99-104">Universelle Gerätetreiber erstellen</span><span class="sxs-lookup"><span data-stu-id="c5a99-104">Universal Driver Creation</span></span>

<span data-ttu-id="c5a99-105">Dieses Dokument führt Sie durch die Erstellung der Universal-Treiber für Ihr IoT Core-Gerät.</span><span class="sxs-lookup"><span data-stu-id="c5a99-105">This document will walk you through the creation of Universal Drivers for your IoT Core device.</span></span>

<span data-ttu-id="c5a99-106">Universelle Treiber können Sie einem Treiberpaket zu erstellen, die über mehrere Gerätetypen, die mit UWP-basierten Editionen von Windows 10, einschließlich IoT Core ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c5a99-106">Universal Drivers enable you to create a single driver package that runs across several device types running UWP-based editions of Windows 10, including IoT Core.</span></span>

<span data-ttu-id="c5a99-107">Dieses Paket enthält, eine Universal INF-Datei und mehrere Binärdateien.</span><span class="sxs-lookup"><span data-stu-id="c5a99-107">This driver package contains a Universal INF file and several binaries.</span></span> <span data-ttu-id="c5a99-108">Die Anforderungen für die einzelnen sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c5a99-108">The requirements for each are as follows:</span></span>
- <span data-ttu-id="c5a99-109">Universal INF-Dateien können nur [die Teilmenge der INF-Syntax, die auf UWP-basierten Editionen von Windows unterstützt](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span><span class="sxs-lookup"><span data-stu-id="c5a99-109">Universal INF files can only use [the subset of INF syntax supported on UWP-based editions of Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span></span> <span data-ttu-id="c5a99-110">Verwenden Sie beim Schreiben der INF-Datei, die [InfVerif Tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) , stellen Sie sicher, dass die Datei diese Syntax entspricht.</span><span class="sxs-lookup"><span data-stu-id="c5a99-110">While writing your INF file, use the [InfVerif tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) to verify that the file adheres to that syntax.</span></span>

- <span data-ttu-id="c5a99-111">Binärdateien können nur Gerätetreiberschnittstellen für UWP-basierten Editionen von Windows 10 (markiert als auf den Referenzseiten Dokumentation universell) unterstützt: [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), oder das Windows-Treibermodell (WDM).</span><span class="sxs-lookup"><span data-stu-id="c5a99-111">binaries can only use device driver interfaces supported on UWP-based editions of Windows 10 (marked as Universal on the documentation reference pages): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), or the Windows Driver Model (WDM).</span></span> <span data-ttu-id="c5a99-112">Sie können auch nur in der OneCore-Teilmenge enthalten APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c5a99-112">They can also only call APIs included in the OneCore Subset.</span></span> <span data-ttu-id="c5a99-113">Verwenden der [ApiValidator Tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) um sicherzustellen, dass die Binärdateien-APIs aufrufen gültig sind.</span><span class="sxs-lookup"><span data-stu-id="c5a99-113">Use the [ApiValidator tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) to verify that the APIs your binaries call are valid.</span></span>

<span data-ttu-id="c5a99-114">Um zu erfahren wie **ein Treiberpaket erstellen, in Visual Studio**, besuchen Sie [ein Treiberpaket erstellen](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span><span class="sxs-lookup"><span data-stu-id="c5a99-114">To learn how to **create a driver package in Visual Studio**, please visit [Creating a Driver Package](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span></span>

<span data-ttu-id="c5a99-115">Wenn Sie möchten **ein Beispiel, um eine universelle Gerätetreiber unter IoT Core erstellen**, finden Sie auf unserer [universelle Gerätetreiber-Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span><span class="sxs-lookup"><span data-stu-id="c5a99-115">If you would like **a sample to help you create a Universal Driver on IoT Core**, please visit our [Universal Driver sample](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span></span>

## <a name="additional-universal-driver-resources"></a><span data-ttu-id="c5a99-116">Zusätzliche universelle Treiberressourcen</span><span class="sxs-lookup"><span data-stu-id="c5a99-116">Additional Universal Driver Resources</span></span>

1. <span data-ttu-id="c5a99-117">Weitere Informationen zu **Entwurfsprinzipien** und **bewährte Methoden** Wenn Sie ein Paket für universelle Gerätetreiber entwickeln zu können, finden Sie auf [erste Schritte mit der Universal-Treiber](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span><span class="sxs-lookup"><span data-stu-id="c5a99-117">For additional details on **design principles** and **best practices** when developing a Universal Driver package, please visit [Getting Started with Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span></span>

2. <span data-ttu-id="c5a99-118">Hilfe **Debuggen Ihre universelle Gerätetreiber**, besuchen Sie [Debuggen einen universelle Windows-Treiber](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span><span class="sxs-lookup"><span data-stu-id="c5a99-118">For help **debugging your Universal Driver**, please visit [Debugging a Universal Windows driver](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span></span>

