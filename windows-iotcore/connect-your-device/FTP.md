---
title: File Transfer Protocol
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie (FTP, File Transfer Protocol) verwenden, um Dateien zu und von Ihren Geräten zu übertragen.
keywords: Transfer-Protokoll für Windows Iot, FTP, Datei, die Übertragung von Dateien, die Geräte
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512665"
---
# <a name="file-transfer-protocol"></a>File Transfer Protocol
Die Datei Transfer Protocol (FTP) können Sie zum Übertragen von Dateien in und aus Ihr Windows 10 IoT Core-Gerät

> [!IMPORTANT]
> FTP wird für Entwickler, die anfängliche Entwicklung vereinfachen, in der Regel empfohlen. Wir empfehlen nicht mithilfe von FTP in Retail-Geräten.

## <a name="starting-the-ftp-server-on-your-device"></a>Starten Sie den FTP-Server auf Ihrem Gerät
* Standardmäßig ist der FTP-Server auf Ihrem IoT Core-Gerät deaktiviert.  Um den FTP-Server auf Ihrem Gerät zu starten, müssen Sie zunächst auf Ihrem Gerät über eine Verbindung herstellen [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md).
* Typ `start C:\Windows\System32\ftpd.exe`
* Sehen Sie sich, dass der Server, indem Sie eingeben ausgeführt wird `tlist`, die werden alle ausgeführten Prozesse aufgeführt.  Wenn der FTP-Server ausgeführt wird, sollten Sie sehen `ftpd.exe` in der Liste.

![FTP-Start](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a>Beenden den FTP-Server auf Ihrem Gerät<a name="stopftp"/>
* Um den FTP-Server auf Ihrem Gerät IoT Core zu beenden, müssen Sie zunächst auf Ihrem Gerät über eine Verbindung herstellen [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md).
* Wenn Sie eine Verbindung mithilfe von PowerShell hergestellt, geben Sie `kill -processname ftpd*` auf den FTP-Vorgang zu beenden.

![Beenden der FTP-PowerShell](../media/ftp/ftp_kill_powershell.png)

* Wenn Sie eine Verbindung über SSH hergestellt, geben Sie `kill ftpd*` auf den FTP-Vorgang zu beenden.

![FTP-SSH beenden](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>Zugriff auf Ihre Dateien über FTP
* Der FTP-Server auf Ihrem Gerät IoT Core wird beim Systemstart automatisch gestartet.  Um eine Verbindung herstellen möchten, benötigen Sie die IP-Adresse Ihres Geräts.  Sie finden die IP-Adresse auf die Standard-app, die gestartet wird, wenn Ihr Gerät gestartet wird.

![DefaultApp unter Windows IoT Core](../media/ftp/DefaultApp.png)

* Nachdem Sie die IP-Adresse haben, öffnen Sie **Datei-Explorer** auf Ihrem PC, und geben `ftp://<TARGET_DEVICE>`, wobei `<TARGET_DEVICE>` ist entweder der Name oder die IP-Adresse von Ihrem Gerät, und drücken Sie die EINGABETASTE.  Geben Sie Ihre Benutzernamen und das Kennwort ein, wenn Sie aufgefordert werden.

![FTP-explorer](../media/ftp/ftp_explorer.png)

* Jetzt können Sie die Dateien auf Ihrem Gerät über FTP zugreifen.

## <a name="changing-the-root-ftp-directory"></a>Ändern die FTP-Stammverzeichnis
* Wird standardmäßig der FTP-Server, alle Ordner im Stammverzeichnis des Geräts in dessen C: zeigt\\.  Führen Sie die gleichen Schritte aus, um den FTP-Server zu starten, außer dass Sie in das Stammverzeichnis als Parameter übergeben, um das Root-Verzeichnis zu ändern.
* Um dies zu ändern, zunächst eine Verbindung mit Ihrem Gerät über [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md).
* [Beenden Sie](#stopftp) der FTP-Prozesses, wenn er bereits ausgeführt wird.
* Typ `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, wobei `<PATH_TO_DIRECTORY>` ist der absolute Pfad zu dem Verzeichnis, das als Stammverzeichnis festlegen, wie z. B. möchten `C:\Users\DefaultAccount`.

![FTP, beginnen Sie mit dem Parameter](../media/ftp/ftp_start_parameter.png)

Nun, wenn Sie über FTP an Ihr Gerät verbinden, sehen den Inhalt des Stammverzeichnisses Sie, die Sie festlegen.

![FTP-Explorer mit der neuen Stammverzeichnis](../media/ftp/ftp_explorer_parameter.png)

Um diese Änderungen permanent zu machen, müssen Sie einen Aufruf hinzufügen `start ftpd.exe <PATH_TO_DIRECTORY>` , in denen `<PATH_TO_DIRECTORY>` ist der absolute Pfad zu dem Verzeichnis, das als Stammverzeichnis festlegen, wie z. B. möchten `C:\Data\Users\DefaultAccount` zu OEMCustomization.cmd und platzieren `C:\Windows\System32`
