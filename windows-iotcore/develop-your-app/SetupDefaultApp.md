---
title: Eine Standard-App einrichten
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: Informationen Sie zum Einrichten einer Standard-app, die über die Windows Device Portal oder die Shell.
keywords: Windows Iot, Standard-app, PowerShell, iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513322"
---
# <a name="setup-a-default-app"></a>Eine Standard-app einrichten
Hier erfahren Sie, wie Ihre Anwendung als standardanwendung festlegen. Die standardanwendung ist diejenige, die beim Systemstart gestartet wird.  

> [!NOTE]
> Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.

## <a name="runtime-options"></a>Laufzeitoptionen

Während der Entwicklung / experimentelle Phasen, Sie können die Standard-app folgende Art und Weise ändern.

### <a name="using-windows-device-portal"></a>Mithilfe von Windows Device Portal

Klicken Sie auf **Start** Spalte, die für die app.
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>Mithilfe der shell

Schritte zum Festlegen der Standard-app, die über die shell 

1. Verbinden mit dem Gerät über [Powershell](../connect-your-device/PowerShell.md)

2. Auflisten der Anwendungen, die mithilfe von installiert `iotstartup list`

3. Beachten Sie die App-ID für die Anwendung, die Sie verwenden möchten, erstellen, die als Standard, und legen Sie es mit `iotstartup add headed <appid>`. Verwenden Sie für die monitorlose app `iotstartup add headless <appid>`.


## <a name="build-time-option"></a>Erstellen der Time (Option)

Bei umfangreichen Bereitstellungen können Sie hierzu Bereitstellungspaket

Sie können die StartupApp/Standardeinstellung in den WCD während der Bereitstellung paketerstellung angeben.
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

Finden Sie unter [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) als Beispiel. Erhalten Sie die Anwendung Benutzer Modell ID (AUMID) der ein Appx mit [GetAppxInfo Tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).

## <a name="how-to-configure-home-key"></a>Vorgehensweise: Konfigurieren von "Home" Schlüssel

Windows 10 IoT Anniversary Update (1607) bietet die shellunterstützung für das standardanwendungsfenster in den Vordergrund bringen, wenn eine andere Anwendung derzeit ausgeführt wird.

Informationen zum Aktivieren des Schlüssels "Home", besuchen Sie unsere [IoT-Shell-Seite](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)
