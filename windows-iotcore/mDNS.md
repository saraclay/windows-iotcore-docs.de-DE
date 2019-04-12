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
# <a name="getting-started-with-mdns-responder-sample-source"></a>Erste Schritte mit mDNS-Responder-Beispielquelle

## <a name="getting-started"></a>Erste Schritte

1.  Kompilieren Sie das Projekt *mDNSResponder* zu Get-mDNSResponder.exe, einem Dienst. Der .exe auf den Zielcomputer kopieren und dann den Dienst zu registrieren und ausführen.
2. Führen Sie "mDNSResponder.exe /?" So drucken Sie die Verwendung
3.  Kompilieren Sie das Projekt *Dnssd*, dnssd.dll generiert
4.  Kompilieren Sie das Projekt *mDNSUWP*. Es ist keine UWP-Broker-Instanz, die im Gespräch mit dnssd.dll und generiert eine eigene Dll und winmd
5.  Kompilieren Sie das Projekt *mDNSTest*, das ist ein Beispiel für UWP-app mDNSUWP nutzen und schließlich in mDNSResponder-Dienst kommuniziert.
6.  Diese UWP-app abhängig ist, auf der UWP-Broker und dnssd.dll (es gibt Skript so konfiguriert, dass um alles, was in der UWP-Appx-Ordner zu kopieren.)
7.  MDNSTest bereitstellen/starten, legen Sie eine ID und klicken Sie auf registrieren, der Code reagieren muss 0 (Erfolg)
8.  Wenn Sie einen beliebigen Bonjour Browser zur gleichen Zeit ausführen, sollte das neue Gerät für die (scheinbar) aufgeführt werden.

![Registrierung für mDNS](media/mDNS/mDNS1.png)

## <a name="resources"></a>Ressourcen

* Herunterladen der Bonjour-kompatiblen mDNS Beantworter für Windows IoT (Beispielcode) [hier](https://go.microsoft.com/fwlink/?linkid=2077676).

