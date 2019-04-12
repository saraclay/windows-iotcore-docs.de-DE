---
title: Secure Shell (SSH)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie mit secure Shell Remote zu verwalten und Konfigurieren Ihres IoT Core-Geräts.
keywords: Windows Iot, secure Shell, Remote, SSH-Client, PuTTY, SSH
ms.openlocfilehash: 2c83184507a840c6017b1dfe36ac915004057d9a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513233"
---
# <a name="secure-shell-ssh"></a>Secure Shell (SSH)
Secure Shell (SSH) können Sie remote verwalten und konfigurieren Sie das Gerät Windows IoT Core

## <a name="using-the-windows-10-openssh-client"></a>Mithilfe des OpenSSH von Windows 10-Clients
> [!IMPORTANT]
> Die Windows-OpenSSH-Client erfordert, dass es sich bei Ihrem SSH-Client Hostbetriebssystem 1803(17134) für Windows 10-Version ist. Darüber hinaus muss das Gerät Windows 10 IoT Core RS5 Windows Insider Preview-Version 17723 oder höher ausgeführt werden.

Die **OpenSSH-Client** wurde auf Windows 10 in 1803 (Build 17134) als optionales Feature hinzugefügt. Zum Installieren des Clients, Sie können nach **optionale Funktionen verwalten** in Windows 10-Einstellungen. Wenn die **OpenSSH-Client** ist nicht aufgeführt, in der Liste der installierten Features und wählen Sie dann **Hinzufügen einer Funktion**.

![Hinzufügen einer Funktion](../media/SSH/add_a_feature.png)

Wählen Sie als Nächstes **OpenSSH-Client** in der Liste und klicken Sie auf **installieren**.

![OpenSSH-Client installieren](../media/SSH/optional_features.png)

Anmeldung mit einem Benutzernamen und das Kennwort den folgenden Befehl aus:

```cmd
ssh administrator@host
```

In dem Host entweder die IP-Adresse des Geräts Windows IoT Core oder der Gerätename ist.

Beim ersten herstellen sinngemäß die folgende Meldung angezeigt:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

Typ **Ja** , und drücken Sie **geben**.

Wenn Sie als anmelden müssen **DefaultAccount** und nicht als Administrator Sie müssen einen Schlüssel generieren und verwenden Sie den Schlüssel für die Anmeldung.  Über den Desktop, die Sie an Ihre IoT-Gerät aus eine Verbindung herstellen möchten, öffnen Sie ein Powershell-Fenster, und ändern Sie in Ihrem Ordner für persönliche Daten (z. B. cd ~)

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

Registrieren Sie den Schlüssel mit ssh-Agent (optional, für die Umgebung für einmaliges Anmelden).  Beachten Sie, die ssh-add-muss ausgeführt werden, aus einem Ordner, die Zugriffssteuerungsliste aktualisieren möchten, als die angemeldeten Benutzer ("BUILTIN\Administrators" und dem NT_AUTHORITY\System-Benutzer sind auch ok).  Durch die Standard-cd ~ über Powershell sollte ausreichend sein, wie unten dargestellt.

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> Wenn Sie eine Meldung, dass der ssh-Agent-Dienst deaktiviert ist können sie mit **sc.exe Config ssh-Agent-Start = Auto**

So aktivieren Sie einmalige Anmelden, fügen Sie den öffentlichen Schlüssel an das Gerät Windows IoT Core **Authorized_keys** Datei.  Oder wenn Sie nur noch Schlüssel Sie kopieren eine Datei mit die öffentliche Schlüssel mit dem **Authorized_keys** Datei.

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

Wenn der Schlüssel mit ssh-Agent nicht registriert ist, müssen sie in der Befehlszeile, Login angegeben werden: 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

Wenn der private Schlüssel mit ssh-Agent registriert ist, müssen Sie nur an <strong>DefaultAccount@host</strong>:

```cmd
ssh DefaultAccount@host
```

Beim ersten herstellen sinngemäß die folgende Meldung angezeigt:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

Typ **Ja** , und drücken Sie **geben**.

Sie sollten nun über eine Verbindung als **DefaultAccount**

Verwenden Sie einmaliges Anmelden mit der **Administrator** account, fügen Sie Ihren öffentlichen Schlüssel an c:\data\ProgramData\ssh\administrators_authorized_keys auf dem Gerät Windows IoT Core. 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

Sie müssen auch die ACL für Administrators_authorized_keys entsprechend die ACL des Ssh_host_dsa_key im gleichen Verzeichnis festgelegt.

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

Die ACL, die mithilfe von Powershell festlegen.

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> Wenn angezeigt wird eine **Identifikation des REMOTE-HOST geändert** Nachrichten nach dem vornehmen von Änderungen auf dem Windows 10 IoT Core-Gerät, und dann bearbeiten C:\Users\<Benutzername >\.Ssh\known_hosts und entfernen Sie den Host, die geändert wurde.

Siehe auch: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>Verwenden von PuTTY

### <a name="download-a-ssh-client"></a>Einen SSH-Client herunterladen
Um mit Ihrem Gerät über SSH eine Verbindung herzustellen, Sie müssen zunächst einen SSH-Client herunterladen, z.B. [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).

### <a name="connect-to-your-device"></a>Herstellen einer Verbindung Ihres Geräts mit
* Um auf Ihr Gerät zu verbinden, müssen Sie zuerst die IP-Adresse des Geräts abrufen.  Nach dem Start Ihres Geräts für die Windows IoT Core, wird eine IP-Adresse auf dem Bildschirm des Geräts angezeigt werden:

    ![DefaultApp unter Windows IoT Core](../media/SSH/DefaultApp.png)

* Jetzt starten Sie PuTTY, und geben Sie die IP-Adresse der `Host Name` Textfeld ein und stellen Sie sicher, dass die `SSH` Optionsfeld ausgewählt ist.  Klicken Sie dann auf `Open`.

    ![PuTTY-Konfiguration](../media/SSH/putty_config.png)

* Wenn Sie auf Ihrem Gerät zum ersten Mal auf Ihrem Computer verbinden, wird möglicherweise die folgenden sicherheitswarnung angezeigt.  Klicken Sie einfach auf `Yes` um den Vorgang fortzusetzen.

    ![PuTTY-Sicherheitswarnung](../media/SSH/putty_security_prompt.png)

* Wenn die Verbindung erfolgreich hergestellt wurde, sollten Sie sehen `login as:` auf dem Bildschirm Sie zum Anmelden aufgefordert werden.  
    Geben Sie `Administrator` , und drücken Sie die EINGABETASTE.  Geben Sie dann das Standardkennwort `p@ssw0rd` wie das Kennwort ein und drücken Sie EINGABETASTE.

    ![PuTTY-Anmeldung](../media/SSH/putty_login.png)

    Würden Sie sich erfolgreich anmelden können, sollten Sie etwa Folgendes angezeigt:

    ![PuTTY-Konsole](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>Kontokennwort aktualisieren

Es ist **dringend empfohlen,** , das Standardkennwort für das Administratorkonto zu aktualisieren.

Zu diesem Zweck geben Sie den folgenden Befehl in der PuTTY-Konsole, und Ersetzen Sie dabei `[new password]` durch ein sicheres Kennwort:
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a>Konfigurieren Sie das Gerät Windows IoT Core
* Um zum Bereitstellen von Anwendungen aus Visual Studio 2017 können, müssen Sie sicherstellen, dass die Visual Studio Remote Debugger auf Ihrem Gerät Windows IoT Core ausgeführt wird. Der Remotedebugger sollte zur Startzeit des Computers automatisch gestartet werden. Um zu überprüfen, verwenden Sie den "Tlist"-Befehl zum Auflisten aller aktiven Prozesse in Powershell aus. Es sollten zwei Instanzen von msvsmon.exe auf dem Gerät vorhanden sein.

* Es ist möglich, dass Visual Studio Remote Debugger zu einem Timeout nach langer Inaktivität. Wenn Visual Studio kann nicht auf Ihrem Windows IoT Core-Gerät verbunden sind, versuchen Sie, einen Neustart des Geräts.

* Wenn Sie möchten, können Sie auch Ihr Gerät umbenennen. Verwenden Sie zum Ändern der "Computername" der `setcomputername` Hilfsprogramm:

        setcomputername <new-name>

    Sie müssen zum Neustarten des Geräts, damit die Änderung wirksam wird. Sie können die `shutdown` -Befehls wie folgt:

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a>Häufig verwendete Hilfsprogramme

Finden Sie unter den [über die Befehlszeile "utils"](../manage-your-device/CommandLineUtils.md) Seite eine Liste der Befehle und Dienstprogramme, die Sie mit SSH verwenden können.
