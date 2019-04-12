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
# <a name="secure-shell-ssh"></a><span data-ttu-id="c384c-104">Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="c384c-104">Secure Shell (SSH)</span></span>
<span data-ttu-id="c384c-105">Secure Shell (SSH) können Sie remote verwalten und konfigurieren Sie das Gerät Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="c384c-105">Secure Shell (SSH) allows you to remotely administer and configure your Windows IoT Core device</span></span>

## <a name="using-the-windows-10-openssh-client"></a><span data-ttu-id="c384c-106">Mithilfe des OpenSSH von Windows 10-Clients</span><span class="sxs-lookup"><span data-stu-id="c384c-106">Using the Windows 10 OpenSSH client</span></span>
> [!IMPORTANT]
> <span data-ttu-id="c384c-107">Die Windows-OpenSSH-Client erfordert, dass es sich bei Ihrem SSH-Client Hostbetriebssystem 1803(17134) für Windows 10-Version ist.</span><span class="sxs-lookup"><span data-stu-id="c384c-107">The Windows OpenSSH client requires that your SSH client host OS is Windows 10 version 1803(17134).</span></span> <span data-ttu-id="c384c-108">Darüber hinaus muss das Gerät Windows 10 IoT Core RS5 Windows Insider Preview-Version 17723 oder höher ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c384c-108">Also, the Windows 10 IoT Core device must be running RS5 Windows Insider Preview release 17723 or greater.</span></span>

<span data-ttu-id="c384c-109">Die **OpenSSH-Client** wurde auf Windows 10 in 1803 (Build 17134) als optionales Feature hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c384c-109">The **OpenSSH Client** was added to Windows 10 in 1803 (build 17134) as an optional feature.</span></span> <span data-ttu-id="c384c-110">Zum Installieren des Clients, Sie können nach **optionale Funktionen verwalten** in Windows 10-Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="c384c-110">To install the client you can search for **Manage Optional Features** in Windows 10 settings.</span></span> <span data-ttu-id="c384c-111">Wenn die **OpenSSH-Client** ist nicht aufgeführt, in der Liste der installierten Features und wählen Sie dann **Hinzufügen einer Funktion**.</span><span class="sxs-lookup"><span data-stu-id="c384c-111">If the **OpenSSH Client** is not listed in the list of installed features then choose **Add a feature**.</span></span>

![Hinzufügen einer Funktion](../media/SSH/add_a_feature.png)

<span data-ttu-id="c384c-113">Wählen Sie als Nächstes **OpenSSH-Client** in der Liste und klicken Sie auf **installieren**.</span><span class="sxs-lookup"><span data-stu-id="c384c-113">Next select **OpenSSH Client** in the list and click **Install**.</span></span>

![OpenSSH-Client installieren](../media/SSH/optional_features.png)

<span data-ttu-id="c384c-115">Anmeldung mit einem Benutzernamen und das Kennwort den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c384c-115">To login with a username and password use the following command:</span></span>

```cmd
ssh administrator@host
```

<span data-ttu-id="c384c-116">In dem Host entweder die IP-Adresse des Geräts Windows IoT Core oder der Gerätename ist.</span><span class="sxs-lookup"><span data-stu-id="c384c-116">Where host is either the IP address of the Windows IoT Core device or the device name.</span></span>

<span data-ttu-id="c384c-117">Beim ersten herstellen sinngemäß die folgende Meldung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c384c-117">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="c384c-118">Typ **Ja** , und drücken Sie **geben**.</span><span class="sxs-lookup"><span data-stu-id="c384c-118">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="c384c-119">Wenn Sie als anmelden müssen **DefaultAccount** und nicht als Administrator Sie müssen einen Schlüssel generieren und verwenden Sie den Schlüssel für die Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="c384c-119">If you need to log in as **DefaultAccount** rather than as administrator you will need to generate a key and use the key to log in.</span></span>  <span data-ttu-id="c384c-120">Über den Desktop, die Sie an Ihre IoT-Gerät aus eine Verbindung herstellen möchten, öffnen Sie ein Powershell-Fenster, und ändern Sie in Ihrem Ordner für persönliche Daten (z. B. cd ~)</span><span class="sxs-lookup"><span data-stu-id="c384c-120">From the desktop that you intend to connect to your IoT Device from, open a powershell window and change to your personal data folder (e.g cd ~)</span></span>

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

<span data-ttu-id="c384c-121">Registrieren Sie den Schlüssel mit ssh-Agent (optional, für die Umgebung für einmaliges Anmelden).</span><span class="sxs-lookup"><span data-stu-id="c384c-121">Register the key with ssh-agent (optional, for single sign-on experience).</span></span>  <span data-ttu-id="c384c-122">Beachten Sie, die ssh-add-muss ausgeführt werden, aus einem Ordner, die Zugriffssteuerungsliste aktualisieren möchten, als die angemeldeten Benutzer ("BUILTIN\Administrators" und dem NT_AUTHORITY\System-Benutzer sind auch ok).</span><span class="sxs-lookup"><span data-stu-id="c384c-122">Note that ssh-add must be performed from a folder that is  ACL'd to you as the signed-in user (Builtin\Administrators and the NT_AUTHORITY\System user are also ok).</span></span>  <span data-ttu-id="c384c-123">Durch die Standard-cd ~ über Powershell sollte ausreichend sein, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c384c-123">By default cd ~ from powershell should be sufficient as shown below.</span></span>

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> <span data-ttu-id="c384c-124">Wenn Sie eine Meldung, dass der ssh-Agent-Dienst deaktiviert ist können sie mit **sc.exe Config ssh-Agent-Start = Auto**</span><span class="sxs-lookup"><span data-stu-id="c384c-124">If you receive a message that the ssh-agent service is disabled you can enable it with **sc.exe config ssh-agent start=auto**</span></span>

<span data-ttu-id="c384c-125">So aktivieren Sie einmalige Anmelden, fügen Sie den öffentlichen Schlüssel an das Gerät Windows IoT Core **Authorized_keys** Datei.</span><span class="sxs-lookup"><span data-stu-id="c384c-125">To enable single sign append the public key to the Windows IoT Core device **authorized_keys** file.</span></span>  <span data-ttu-id="c384c-126">Oder wenn Sie nur noch Schlüssel Sie kopieren eine Datei mit die öffentliche Schlüssel mit dem **Authorized_keys** Datei.</span><span class="sxs-lookup"><span data-stu-id="c384c-126">Or if you only have one key you copy the public key file to the remote **authorized_keys** file.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

<span data-ttu-id="c384c-127">Wenn der Schlüssel mit ssh-Agent nicht registriert ist, müssen sie in der Befehlszeile, Login angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="c384c-127">If the key is not registered with ssh-agent it must be specified on the command line to login:</span></span> 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

<span data-ttu-id="c384c-128">Wenn der private Schlüssel mit ssh-Agent registriert ist, müssen Sie nur an <strong>DefaultAccount@host</strong>:</span><span class="sxs-lookup"><span data-stu-id="c384c-128">If the private key is registered with ssh-agent then you only need to specify <strong>DefaultAccount@host</strong>:</span></span>

```cmd
ssh DefaultAccount@host
```

<span data-ttu-id="c384c-129">Beim ersten herstellen sinngemäß die folgende Meldung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c384c-129">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="c384c-130">Typ **Ja** , und drücken Sie **geben**.</span><span class="sxs-lookup"><span data-stu-id="c384c-130">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="c384c-131">Sie sollten nun über eine Verbindung als **DefaultAccount**</span><span class="sxs-lookup"><span data-stu-id="c384c-131">You should now be connected as **DefaultAccount**</span></span>

<span data-ttu-id="c384c-132">Verwenden Sie einmaliges Anmelden mit der **Administrator** account, fügen Sie Ihren öffentlichen Schlüssel an c:\data\ProgramData\ssh\administrators_authorized_keys auf dem Gerät Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c384c-132">To use single sign-on with the **administrator** account, append your public key to c:\data\ProgramData\ssh\administrators_authorized_keys on the Windows IoT Core device.</span></span> 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="c384c-133">Sie müssen auch die ACL für Administrators_authorized_keys entsprechend die ACL des Ssh_host_dsa_key im gleichen Verzeichnis festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c384c-133">You will also need to set the ACL for administrators_authorized_keys to match the ACL of ssh_host_dsa_key in the same directory.</span></span>

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="c384c-134">Die ACL, die mithilfe von Powershell festlegen.</span><span class="sxs-lookup"><span data-stu-id="c384c-134">To set the ACL using powershell</span></span>

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> <span data-ttu-id="c384c-135">Wenn angezeigt wird eine **Identifikation des REMOTE-HOST geändert** Nachrichten nach dem vornehmen von Änderungen auf dem Windows 10 IoT Core-Gerät, und dann bearbeiten C:\Users\<Benutzername >\.Ssh\known_hosts und entfernen Sie den Host, die geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="c384c-135">If you see a **REMOTE HOST IDENTIFICATION CHANGED** message after making changes to the Windows 10 IoT Core device, then edit C:\Users\<username>\.ssh\known_hosts and remove the host that has changed.</span></span>

<span data-ttu-id="c384c-136">Siehe auch: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span><span class="sxs-lookup"><span data-stu-id="c384c-136">See also: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span></span>

## <a name="using-putty"></a><span data-ttu-id="c384c-137">Verwenden von PuTTY</span><span class="sxs-lookup"><span data-stu-id="c384c-137">Using PuTTY</span></span>

### <a name="download-a-ssh-client"></a><span data-ttu-id="c384c-138">Einen SSH-Client herunterladen</span><span class="sxs-lookup"><span data-stu-id="c384c-138">Download a SSH client</span></span>
<span data-ttu-id="c384c-139">Um mit Ihrem Gerät über SSH eine Verbindung herzustellen, Sie müssen zunächst einen SSH-Client herunterladen, z.B. [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span><span class="sxs-lookup"><span data-stu-id="c384c-139">In order to connect to your device using SSH, you'll first need to download a SSH client, such as [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span></span>

### <a name="connect-to-your-device"></a><span data-ttu-id="c384c-140">Herstellen einer Verbindung Ihres Geräts mit</span><span class="sxs-lookup"><span data-stu-id="c384c-140">Connect to your device</span></span>
* <span data-ttu-id="c384c-141">Um auf Ihr Gerät zu verbinden, müssen Sie zuerst die IP-Adresse des Geräts abrufen.</span><span class="sxs-lookup"><span data-stu-id="c384c-141">In order to connect to your device, you need to first get the IP address of the device.</span></span>  <span data-ttu-id="c384c-142">Nach dem Start Ihres Geräts für die Windows IoT Core, wird eine IP-Adresse auf dem Bildschirm des Geräts angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="c384c-142">After booting your Windows IoT Core device, an IP address will be shown on the screen attached to the device:</span></span>

    ![DefaultApp unter Windows IoT Core](../media/SSH/DefaultApp.png)

* <span data-ttu-id="c384c-144">Jetzt starten Sie PuTTY, und geben Sie die IP-Adresse der `Host Name` Textfeld ein und stellen Sie sicher, dass die `SSH` Optionsfeld ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="c384c-144">Now launch PuTTY and enter the IP address in the `Host Name` text box and make sure the `SSH` radio button is selected.</span></span>  <span data-ttu-id="c384c-145">Klicken Sie dann auf `Open`.</span><span class="sxs-lookup"><span data-stu-id="c384c-145">Then click `Open`.</span></span>

    ![PuTTY-Konfiguration](../media/SSH/putty_config.png)

* <span data-ttu-id="c384c-147">Wenn Sie auf Ihrem Gerät zum ersten Mal auf Ihrem Computer verbinden, wird möglicherweise die folgenden sicherheitswarnung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c384c-147">If you're connecting to your device for the first time from your computer, you may see the following security alert.</span></span>  <span data-ttu-id="c384c-148">Klicken Sie einfach auf `Yes` um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="c384c-148">Just click `Yes` to continue.</span></span>

    ![PuTTY-Sicherheitswarnung](../media/SSH/putty_security_prompt.png)

* <span data-ttu-id="c384c-150">Wenn die Verbindung erfolgreich hergestellt wurde, sollten Sie sehen `login as:` auf dem Bildschirm Sie zum Anmelden aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="c384c-150">If the connection was successful, you should see `login as:` on the screen, prompting you to login.</span></span>  
    <span data-ttu-id="c384c-151">Geben Sie `Administrator` , und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="c384c-151">Enter `Administrator` and press enter.</span></span>  <span data-ttu-id="c384c-152">Geben Sie dann das Standardkennwort `p@ssw0rd` wie das Kennwort ein und drücken Sie EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="c384c-152">Then enter the default password `p@ssw0rd` as the password and press enter.</span></span>

    ![PuTTY-Anmeldung](../media/SSH/putty_login.png)

    <span data-ttu-id="c384c-154">Würden Sie sich erfolgreich anmelden können, sollten Sie etwa Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c384c-154">If you were able to login successfully, you should see something like this:</span></span>

    ![PuTTY-Konsole](../media/ssh/putty_console.png)

### <a name="update-account-password"></a><span data-ttu-id="c384c-156">Kontokennwort aktualisieren</span><span class="sxs-lookup"><span data-stu-id="c384c-156">Update account password</span></span>

<span data-ttu-id="c384c-157">Es ist **dringend empfohlen,** , das Standardkennwort für das Administratorkonto zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c384c-157">It is **highly recommended** that you update the default password for the Administrator account.</span></span>

<span data-ttu-id="c384c-158">Zu diesem Zweck geben Sie den folgenden Befehl in der PuTTY-Konsole, und Ersetzen Sie dabei `[new password]` durch ein sicheres Kennwort:</span><span class="sxs-lookup"><span data-stu-id="c384c-158">To do this, enter the following command in the PuTTY console, replacing `[new password]` with a strong password:</span></span>
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="c384c-159">Konfigurieren Sie das Gerät Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="c384c-159">Configure your Windows IoT Core device</span></span>
* <span data-ttu-id="c384c-160">Um zum Bereitstellen von Anwendungen aus Visual Studio 2017 können, müssen Sie sicherstellen, dass die Visual Studio Remote Debugger auf Ihrem Gerät Windows IoT Core ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c384c-160">To be able to deploy applications from Visual Studio 2017, you will need to make sure the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="c384c-161">Der Remotedebugger sollte zur Startzeit des Computers automatisch gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="c384c-161">The remote debugger should launch automatically at machine boot time.</span></span> <span data-ttu-id="c384c-162">Um zu überprüfen, verwenden Sie den "Tlist"-Befehl zum Auflisten aller aktiven Prozesse in Powershell aus.</span><span class="sxs-lookup"><span data-stu-id="c384c-162">To double check, use the tlist command to list all the running processes from powershell.</span></span> <span data-ttu-id="c384c-163">Es sollten zwei Instanzen von msvsmon.exe auf dem Gerät vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="c384c-163">There should be two instances of msvsmon.exe running on the device.</span></span>

* <span data-ttu-id="c384c-164">Es ist möglich, dass Visual Studio Remote Debugger zu einem Timeout nach langer Inaktivität.</span><span class="sxs-lookup"><span data-stu-id="c384c-164">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="c384c-165">Wenn Visual Studio kann nicht auf Ihrem Windows IoT Core-Gerät verbunden sind, versuchen Sie, einen Neustart des Geräts.</span><span class="sxs-lookup"><span data-stu-id="c384c-165">If Visual Studio cannot connect to your Windows IoT Core device, try rebooting the device.</span></span>

* <span data-ttu-id="c384c-166">Wenn Sie möchten, können Sie auch Ihr Gerät umbenennen.</span><span class="sxs-lookup"><span data-stu-id="c384c-166">If you want, you can also rename your device.</span></span> <span data-ttu-id="c384c-167">Verwenden Sie zum Ändern der "Computername" der `setcomputername` Hilfsprogramm:</span><span class="sxs-lookup"><span data-stu-id="c384c-167">To change the 'computer name', use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

    <span data-ttu-id="c384c-168">Sie müssen zum Neustarten des Geräts, damit die Änderung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="c384c-168">You will need to reboot the device for the change to take effect.</span></span> <span data-ttu-id="c384c-169">Sie können die `shutdown` -Befehls wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c384c-169">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a><span data-ttu-id="c384c-170">Häufig verwendete Hilfsprogramme</span><span class="sxs-lookup"><span data-stu-id="c384c-170">Commonly used utilities</span></span>

<span data-ttu-id="c384c-171">Finden Sie unter den [über die Befehlszeile "utils"](../manage-your-device/CommandLineUtils.md) Seite eine Liste der Befehle und Dienstprogramme, die Sie mit SSH verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c384c-171">See the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page for a list of commands and utilities you can use with SSH.</span></span>
