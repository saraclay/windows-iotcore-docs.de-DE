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
# <a name="universal-driver-creation"></a>Universelle Gerätetreiber erstellen

Dieses Dokument führt Sie durch die Erstellung der Universal-Treiber für Ihr IoT Core-Gerät.

Universelle Treiber können Sie einem Treiberpaket zu erstellen, die über mehrere Gerätetypen, die mit UWP-basierten Editionen von Windows 10, einschließlich IoT Core ausgeführt wird.

Dieses Paket enthält, eine Universal INF-Datei und mehrere Binärdateien. Die Anforderungen für die einzelnen sind wie folgt:
- Universal INF-Dateien können nur [die Teilmenge der INF-Syntax, die auf UWP-basierten Editionen von Windows unterstützt](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file). Verwenden Sie beim Schreiben der INF-Datei, die [InfVerif Tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) , stellen Sie sicher, dass die Datei diese Syntax entspricht.

- Binärdateien können nur Gerätetreiberschnittstellen für UWP-basierten Editionen von Windows 10 (markiert als auf den Referenzseiten Dokumentation universell) unterstützt: [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), oder das Windows-Treibermodell (WDM). Sie können auch nur in der OneCore-Teilmenge enthalten APIs aufrufen. Verwenden der [ApiValidator Tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) um sicherzustellen, dass die Binärdateien-APIs aufrufen gültig sind.

Um zu erfahren wie **ein Treiberpaket erstellen, in Visual Studio**, besuchen Sie [ein Treiberpaket erstellen](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)

Wenn Sie möchten **ein Beispiel, um eine universelle Gerätetreiber unter IoT Core erstellen**, finden Sie auf unserer [universelle Gerätetreiber-Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)

## <a name="additional-universal-driver-resources"></a>Zusätzliche universelle Treiberressourcen

1. Weitere Informationen zu **Entwurfsprinzipien** und **bewährte Methoden** Wenn Sie ein Paket für universelle Gerätetreiber entwickeln zu können, finden Sie auf [erste Schritte mit der Universal-Treiber](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)

2. Hilfe **Debuggen Ihre universelle Gerätetreiber**, besuchen Sie [Debuggen einen universelle Windows-Treiber](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).

