---
title: Lightning-Installationshandbuch
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie den Standard-Controller-Treiber an den Treiber Lightning DMAP auf einem Gerät zu ändern.
keywords: Windows Iot "," Lightning "," Setup "," Lightning-Setup, Windows Device Portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513201"
---
# <a name="lightning-setup-guide"></a>Lightning-Installationshandbuch

Dieses Handbuch führt Sie durch die erforderlichen Schritte zum Ändern des Standard-Controller-Treibers an den Treiber Lightning direct Memory Access-zugeordnet (DMAP), auf einem Windows IoT Core-Gerät. Dies ermöglicht die Verwendung von Lightning-fähigen Anwendungen auf diesem Gerät.

## <a name="change-the-default-controller-driver"></a>Ändern Sie den Standard-Controller-Treiber

Wir möchten die Windows Device Portal zu öffnen.

1. Suchen Sie die IP-Adresse Ihres Geräts, indem Sie entweder mithilfe der Windows 10 IoT Core Dashboard-Anwendung oder das Board zu einem Monitor einbinden.

2. Öffnen Sie auf dem lokalen Computer der Webseite für Windows-Geräte-Portal durch Eingabe von dieser Adresse http://{BoardIPAddress}:8080/ in Ihrem Webbrowser.
   ![Windows-Geräte-Portal](../media/LightningSetup/dmap1.png)

3. Die Windows-Geräte-Portalseite Fragen Sie Ihre Anmeldeinformationen. Der Standardbenutzername lautet `Administrator` und das Kennwort `p@ssw0rd` Beachten Sie, dass nach der Eingabe von Benutzername und Kennwort, das Portal fragt Sie, ob Sie das Kennwort ändern möchten. Es ist immer empfiehlt sich, ihn zu ändern.
   ![Portal Anmeldeinformationen für die Windows-Geräte](../media/LightningSetup/dmap2.png)

4. Klicken Sie im Navigationsmenü öffnen Sie die Seite "Geräte" auf Geräten ![Seite "Geräte"](../media/LightningSetup/dmap3.png)

5. Die Seite "Geräte" listet die verfügbaren Controller-Treiber. Standardmäßig wird der Treiber für Posteingang in das aktuelle festgelegt.

6. Wechseln Sie zu der Lightning-Treiber, durch den direkten Speicher zugeordnet Treiber aus dem Dropdownmenü auswählen, und klicken Sie auf die Schaltfläche "Treiber aktualisieren"<br/>
   ![Wählen Sie zugeordneter Direct-Memory-Treiber](../media/LightningSetup/dmap4.png)

7. Warten Sie, bis die Seite können Sie wissen, wann die Installation des Treibers abgeschlossen ist.
   ![Treiberinstallation abgeschlossen](../media/LightningSetup/dmap5.png)

8. Wenn ein Neustart erforderlich ist, wird die Seite Sie auch zu informieren. Sie können neu starten, mit der Schaltfläche "Neustart" am oberen Rand der Seite.

9. Nun können Sie zum Erstellen und verwenden verwenden Anwendungen sorgen dafür, des Treibers Lightning direkte Arbeitsspeicher zugeordnet.
