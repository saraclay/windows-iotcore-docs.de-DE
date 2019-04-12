---
title: Mobile Breitbandverbindung
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Erfahren Sie, wie Sie mit der mobilen Breitband-Verbindung für Windows 10 IoT Core.
keywords: Windows Iot, MBB, mobile Breitbandverbindung
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513577"
---
## <a name="mobile-broadband-connection"></a>Mobile Breitbandverbindung

Mobile Breitbandverbindung wird unterstützt, auf [Windows 10 IoT Core](http://windowsondevices.com). Wenn Ihre IoT-Gateway über das Modem für mobiles Breitband-Modul unterstützt, können Sie mithilfe der `MBBConnect` Tool, das setupkonfigurationen für mobile Breitbandverbindung im IoT Core hilft.

`MBBConnect` Ruft die Daten zu verbinden, z. B. Abonnenten-ID, SIM Chipkarte-ID, Schnittstellenname, und home Anbietername usw. ab. Anschließend erstellen sie das Verbindungsprofil. Alles, was Sie tun müssen APN bereitstellen ist und es wird die Verbindung automatisch einrichten.

`MBBConnect` entwickelt und getestet mit MinnowBoard Max-basiertes führt IoT Core Version 16299 und dem mobilen Breitband-Modem-Modul mit der SIM-Karte von wichtigen Telekommunikationsanbieters in Taiwan IoT-Gateway.

### <a name="usage"></a>Verwendung

1. Kopie `MBBConnect.exe` IoT-Gateway.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Verbinden Sie über Powershell oder die SSH-Gateways.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. Wechseln Sie zu dem Ordner, in denen `MBBConnect.exe` befindet. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>Beispiel
Im folgenden Beispiel wird die MBBConnect.exe in PowerShell. Verwenden Sie z. B. ist der APN der SIM-Karte "Internet", `MBBConnect.exe Internet` eine Verbindung herstellen.
 
Die ausgehende Nachricht wird den Flow angezeigt:

* Der Status ist nicht verbunden, verbunden geändert. 

* WWAN Netzwerk wurde erfolgreich konfiguriert.

Testen Sie das Beispiel für Mobile Breitbandverbindung [hier](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).
