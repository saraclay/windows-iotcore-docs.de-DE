---
title: Windows-Dateifreigabe
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über das Windows-Dateifreigabe, die zum Übertragen von Dateien zu und von Ihrem Gerät verwenden.
keywords: Windows Iot, Dateiübertragung, Dateifreigabe, Windows-Dateifreigabe
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513873"
---
# <a name="windows-file-sharing"></a>Windows-Dateifreigabe

Sie können die Windows-Dateifreigabe verwenden, zum Übertragen von Dateien in und aus Ihr Gerät.

## <a name="accessing-your-files-using-windows-file-sharing"></a>Zugriff auf Ihre Dateien mithilfe von Windows-Dateifreigabe
* Dem Dateifreigabeserver auf Ihrem Gerät Windows IoT Core wird beim Systemstart automatisch gestartet.  Um eine Verbindung herstellen möchten, benötigen Sie die IP-Adresse Ihres Geräts.  Sie finden die IP-Adresse auf die Standard-app, die gestartet wird, wenn Ihr Gerät gestartet wird.

    ![DefaultApp unter Windows IoT Core](../media/WindowsFileSharing/DefaultApp.png)
    
* Nachdem Sie die IP-Adresse haben, öffnen Sie **Datei-Explorer** auf Ihrem Computer und dem Typ `\\<TARGET_DEVICE>\c$`, wobei `<TARGET_DEVICE>` ist der Name oder die IP-Adresse Ihres Geräts für die Windows IoT Core, und drücken Sie die EINGABETASTE.  

Geben Sie Ihre Benutzernamen und das Kennwort ein, wenn Sie aufgefordert werden. Der Benutzername sollte die IP-Adresse Ihres Windows IoT Core-Geräts als Präfix eingegeben werden. Beispiel: **Benutzername:** `192.168.1.118\Administrator`  **Kennwort:** `{your_password}`.

![Datei-Explorer](../media/WindowsFileSharing/smb_file_explorer.png)

* Jetzt können Sie die Dateien auf Ihrem Gerät über Windows-Dateifreigabe zugreifen.

## <a name="starting-and-stopping-the-file-sharing-server"></a>Starten und beenden die Dateifreigabe-server
* Herstellen einer Verbindung Ihres Geräts über mit [PowerShell](../connect-your-device/powershell.md) oder [SSH](../connect-your-device/ssh.md).
* Standardmäßig wird dem Dateifreigabeserver gestartet, wenn das Gerät gestartet wird.
* Geben Sie zum Beenden der Dateifreigabeserver `net stop Server /y`
* Geben Sie zum Starten der Dateifreigabeserver `net start Server`

    ![Server starten und beenden](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>Deaktivieren und aktivieren die Dateifreigabe-Server beim Start
* Herstellen einer Verbindung Ihres Geräts über mit [PowerShell](../connect-your-device/powershell.md) oder [SSH](../connect-your-device/ssh.md).
* Standardmäßig wird dem Dateifreigabeserver gestartet, wenn das Gerät gestartet wird.
* Geben Sie zum Deaktivieren der Datei mit dem Server gemeinsam, sodass er nicht gestartet wird, wenn das Gerät gestartet wird `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* Geben Sie zum Aktivieren der Dateifreigabeserver, sodass, die gestartet wird, wenn das Gerät gestartet wird `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![Server aktivieren deaktivieren](../media/WindowsFileSharing/smb_enable_disable.png)
