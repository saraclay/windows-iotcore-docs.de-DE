---
title: Verbinden Sie Ihres Geräts mit der cloud
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Verbinden Ihres Geräts mit der Cloud.
keywords: Windows Azure, Iot-Sicherheit, Trusted Platform Module, SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513842"
---
# <a name="connect-your-device-to-the-cloud"></a>Verbinden Sie Ihres Geräts mit der cloud

Sichere Informationen wie z. B. ein Kennwort oder ein Zertifikat auf einem Gerät speichern, kann ein Gerät für Offenlegung anfällig machen. Einem kompromittierten Kennwort ist ein scherzhafter Kommentar Möglichkeit, die die Sicherheit eines Geräts oder ein ganzes System zu gefährden. In der Windows-Familie ist die Technologie, die die Sicherheit des Betriebssystems unterstützt das Trusted Platform Module.

Ein [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM)-Gerät ist ein Microcontroller, die Daten speichern und Berechnungen ausführen kann. Es kann entweder eine diskrete Chip aufgelötet auf der Hauptplatine des Computers oder eines Moduls, das System auf einem Chip (SoC) vom Hersteller integriert sein. 

## <a name="inside-the-tpm"></a>Innerhalb des TPM 

Ein entscheidendes Merkmal des TPM ist der lesegeschützte Speicher. Auf Grundlage der Daten in ihr ist TPM kann auch berechnen einen kryptografischen Hash (z. B. die [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), basierend auf diesen Daten.
Es ist unmöglich, entdecken Sie den geheimen Schlüssel, der den Hash angegeben, aber wenn beide Seiten der Kommunikation der geheime Schlüssel bekannt ist, ist es möglich, zu bestimmen, ob der Hash von einer anderen Partei empfangen diesen geheimen Schlüssel erstellt wurde.

Die grundlegende Idee hinter der Verwendung von kryptografischer Schlüsseln: der geheime Schlüssel (auch als "den SAS-Schlüssel" bezeichnet) hergestellt und das IoT-Geräte und der Cloud während der Device provisioning-Prozess gemeinsam ist. Ab diesem Punkt wird ein HMAC, abgeleitet aus dem geheimen Schlüssel zum Authentifizieren des IoT-Geräts verwendet werden.

## <a name="device-provisioning"></a>Gerätebereitstellung 

Das Tool, mit dem Windows 10 IoT Core-Geräte bereitgestellt IoT Core Dashboard aufgerufen wird, und kann heruntergeladen werden [die Seite Downloads Aufrufen](http://go.microsoft.com/fwlink/?LinkID=708576).

Das Dashboard ein Image des Betriebssystems und Ihr Gerät sicher mit Azure verbunden. Dies erfolgt durch das physische Gerät mit Geräte-ID im Azure IoT Hub und die dazugehörigen Geschäftsparameter imprinting des gemeinsame Zugriffsschlüssels und gerätespezifische auf dem Gerät des TPM. 

Für Geräte, die nicht über ein TPM-Chip verfügen, kann das Tool Software emulierte TPM installieren. Keine Sicherheit geboten, aber dies ermöglicht Ihnen das Entwickeln von Apps, die mit einem Gerät Maker (z. B. Raspberry Pi 2- oder 3) und Sicherheit "light einrichten" auf einem Gerät mit der TPM-Hardware verfügen, ohne die app ändern zu müssen. 

Um Ihr Gerät mit Azure verbinden möchten, klicken Sie auf der Registerkarte "Connect to Azure":

![Öffnen Sie eine Verbindung herstellen, auf der Registerkarte "Azure"](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

Sie werden aufgefordert, die bei Ihrem Azure-Konto anmelden. Wählen Sie die gewünschte Instanz von Azure IoT Hub, und ordnen Sie Ihr physische Gerät zu. Wenn Sie nicht über die jeder IoT Hub-Instanzen im Azure-Abonnement verfügen, erlauben das Tool Ihnen, eine kostenlose Instanz zu erstellen. 

Nachdem Sie den IoT Hub und die Geräte-ID Ihres Geräts mit zuordnen ausgewählt haben, können Sie auf das TPM versehen den SAS-Schlüssel des Geräts dadurch:

![Bereitstellen eines Geräts](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

Ihr Gerät ist jetzt auf sichere Weise eine Verbindung mit Azure bereit. 

Die Windows Device Portal können auch um eine IoT Hub-Verbindungszeichenfolge dynamisch zu erlangen, obwohl es zuerst mit dem Internet verbindet, nach der bereitgestellt wird. Dies kann auf der Registerkarte "Azure-Clients" in das Device Portal erfolgen.

![Registerkarte "Azure-Clients"](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a>Hilfreiche Ressourcen:
* [Verbinden Ihrer app in Azure](../connect-to-cloud/ConnectAppToCloud.md)
* [Erstellen sichere apps IoT Core](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
