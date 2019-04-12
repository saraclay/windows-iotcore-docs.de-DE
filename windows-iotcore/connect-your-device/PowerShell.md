---
title: Mithilfe von PowerShell für Windows IoT
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Verwenden von PowerShell zum Herstellen einer Verbindung Ihres Geräts mit als auch Ihr Gerät verwalten.
keywords: Windows Iot, PowerShell, Windows PowerShell, Befehlszeile, eine Befehlszeilenshell
ms.openlocfilehash: 1519fb9dd61a8d6521757fdd97999f03b74afa7d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513914"
---
# <a name="using-powershell-for-windows-iot"></a><span data-ttu-id="7d5c2-104">Mithilfe von PowerShell für Windows IoT</span><span class="sxs-lookup"><span data-stu-id="7d5c2-104">Using PowerShell for Windows IoT</span></span>

<span data-ttu-id="7d5c2-105">Remote konfigurieren und Verwalten von einem beliebigen Gerät für Windows 10 IoT Core mithilfe von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-105">Remotely configure and manage any Windows 10 IoT Core device by using Windows PowerShell.</span></span>
<span data-ttu-id="7d5c2-106">PowerShell ist eine aufgabenbasierte Befehlszeilenshell und Skriptsprache, die speziell für die systemverwaltung konzipiert.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-106">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span>

<span data-ttu-id="7d5c2-107">Stellen Sie sicher, dass diese Schritte ausführen, um Ihr Gerät mit Windows 10 IoT Core funktioniert auch mit Visual Studio 2017 ordnungsgemäß zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-107">Make sure to follow these steps to correctly configure your device running Windows 10 IoT Core to work well with Visual Studio 2017.</span></span>

## <a name="initiating-a-powershell-session"></a><span data-ttu-id="7d5c2-108">Initiieren eine PowerShell-Sitzung</span><span class="sxs-lookup"><span data-stu-id="7d5c2-108">Initiating a PowerShell session</span></span>
1. <span data-ttu-id="7d5c2-109">Um eine PowerShell-Sitzung mit Ihrem Windows 10 IoT Core-Gerät zu starten, müssen Sie zuerst eine Vertrauensstellung zwischen Ihrem Host-PC und Ihr Gerät zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-109">To start a PowerShell session with your Windows 10 IoT Core device, you'll first need to create a trust relationship between your host PC and your device.</span></span> <span data-ttu-id="7d5c2-110">Nach dem Starten Ihres Geräts für die Windows IoT Core, wird eine IP-Adresse auf dem Bildschirm des Geräts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-110">After starting your Windows IoT Core device, an IP address will be shown on the screen attached to the device.</span></span>

    ![DefaultApp auf Windows 10 IoT Core](../media/PowerShell/DefaultApp.png)

   <span data-ttu-id="7d5c2-112">Sie finden die gleiche Informationen auf dem Windows 10 IoT Core Dashboard.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-112">You can find the same information on the Windows 10 IoT Core Dashboard.</span></span>

2. <span data-ttu-id="7d5c2-113">Öffnen Sie eine Administrator-PowerShell-Konsole auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-113">Open an administrator PowerShell console on your local PC.</span></span> <span data-ttu-id="7d5c2-114">Typ **Powershell** in die **suchen im Web und auf Windows** Feld in der Nähe der Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-114">Type **powershell** in the **Search the web and Windows** box near the Windows Start menu.</span></span> <span data-ttu-id="7d5c2-115">Windows finden PowerShell auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-115">Windows will find PowerShell on your PC.</span></span>

    ![Finden von PowerShell](../media/PowerShell/start-ps.png)

3. <span data-ttu-id="7d5c2-117">Zum Starten von PowerShell als Administrator Maustaste **Windows PowerShell**, und wählen Sie dann **als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-117">To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>

    ![Führen Sie PowerShell als administrator](../media/PowerShell/start-ps2.png)

   <span data-ttu-id="7d5c2-119">Jetzt sollte die PowerShell-Konsole angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-119">Now you should see the PowerShell console.</span></span>

    ![PowerShell-Konsole](../media/PowerShell/ps.PNG)

4. <span data-ttu-id="7d5c2-121">Sie müssen möglicherweise starten den WinRM-Dienst auf dem Desktop, um Remoteverbindungen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-121">You may need to start the WinRM service on your desktop to enable remote connections.</span></span> <span data-ttu-id="7d5c2-122">Geben Sie an der PowerShell-Konsole dazu, den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-122">To do so, from the PowerShell console, type the following command:</span></span>

        net start WinRM

5. <span data-ttu-id="7d5c2-123">Über die PowerShell-Konsole, geben Sie Folgendes ein, und Ersetzen Sie dabei `<machine-name or IP address>` mit den entsprechenden Wert (mit Ihrer **Computername** ist das einfachste, aber wenn Ihr Gerät eindeutig in Ihrem Netzwerk, nicht heißt wiederholen Sie die IP-Adresse):</span><span class="sxs-lookup"><span data-stu-id="7d5c2-123">From the PowerShell console, type the following, substituting `<machine-name or IP address>` with the appropriate value (using your **machine-name** is the easiest, but if your device is not uniquely named on your network, try the IP address):</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. <span data-ttu-id="7d5c2-124">Geben Sie `Y` um die Änderung zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-124">Enter `Y` to confirm the change.</span></span>

> [!NOTE]
> <span data-ttu-id="7d5c2-125">Wenn Sie mehrere Geräte eine Verbindung herstellen möchten, können Sie Kommas und Anführungszeichen ein, um jedes Gerät zu trennen können.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-125">If you want to connect multiple devices, you can use commas and quotation marks to separate each device.</span></span>
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. <span data-ttu-id="7d5c2-126">Nun können Sie eine Sitzung mit Ihrem Gerät Windows IoT Core beginnen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-126">Now you can start a session with your Windows IoT Core device.</span></span> <span data-ttu-id="7d5c2-127">Geben Sie PowerShell-Administratorkonsole:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-127">From you administrator PowerShell console, type:</span></span>

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. <span data-ttu-id="7d5c2-128">Geben Sie in das Dialogfeld "Anmeldeinformationen" das Standardkennwort für die folgenden aus:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-128">In the credential dialog, enter the following default password:</span></span> `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span data-ttu-id="7d5c2-129"><span class="win-icon win-icon-Page"></span> HINWEIS</span><span class="sxs-lookup"><span data-stu-id="7d5c2-129"><span class="win-icon win-icon-Page"></span> NOTE</span></span> </h5>
      <p><span data-ttu-id="7d5c2-130">Der Verbindungsprozess erfolgt nicht sofort, und es kann bis zu 30 Sekunden dauern.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-130">The connection process is not immediate and can take up to 30 seconds.</span></span></p>
    </div>    
    
    <span data-ttu-id="7d5c2-131">Wenn Sie erfolgreich auf dem Gerät verbunden, sehen Sie die IP-Adresse Ihres Geräts, bevor Sie die Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-131">If you successfully connected to the device, you should see the IP address of your device before the prompt.</span></span>

    ![PowerShell-Konsole](../media/PowerShell/ps_device.png)

9. <span data-ttu-id="7d5c2-133">Kennwort für Ihr Konto zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-133">Update your account password.</span></span> <span data-ttu-id="7d5c2-134">Wir *wird dringend empfohlen,* , das Standardkennwort für das Administratorkonto zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-134">We *highly recommend* that you update the default password for the Administrator account.</span></span> <span data-ttu-id="7d5c2-135">Zu diesem Zweck geben Sie die folgenden Befehle in Ihrer PowerShell-Verbindung:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-135">To do this, issue the following commands in your PowerShell connection:</span></span>

    <span data-ttu-id="7d5c2-136">a.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-136">a.</span></span> <span data-ttu-id="7d5c2-137">Ersetzen Sie dies `[new password]` durch ein sicheres Kennwort:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-137">Replace `[new password]` with a strong password:</span></span>
    
            net user Administrator [new password]
            
    <span data-ttu-id="7d5c2-138">b.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-138">b.</span></span> <span data-ttu-id="7d5c2-139">Als Nächstes Einrichten einer neuen PowerShell-Sitzung, mit `Exit-PSSession` und `Enter-PSSession` mit den neuen Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-139">Next, establish a new PowerShell session using `Exit-PSSession` and `Enter-PSSession` with the new credentials.</span></span>
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a><span data-ttu-id="7d5c2-140">Häufig verwendete PowerShell-Befehle</span><span class="sxs-lookup"><span data-stu-id="7d5c2-140">Commonly used PowerShell commands</span></span>

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a><span data-ttu-id="7d5c2-141">Problembehandlung mit Visual Studio Remote Debugger</span><span class="sxs-lookup"><span data-stu-id="7d5c2-141">Troubleshooting with Visual Studio Remote Debugger</span></span>

<span data-ttu-id="7d5c2-142">Um zum Bereitstellen von Anwendungen aus Visual Studio 2017 können, müssen Sie sicherstellen, dass die Visual Studio Remote Debugger auf Ihrem Gerät Windows IoT Core ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-142">To be able to deploy applications from Visual Studio 2017, you will need to make sure that the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="7d5c2-143">Der Remotedebugger sollte automatisch geöffnet, wenn Sie Ihre Computer starten.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-143">The remote debugger should open automatically when you start your computer.</span></span> <span data-ttu-id="7d5c2-144">Verwenden Sie zum Überprüfen, die `tlist` Befehl zum Auflisten alle ausgeführten Prozesse über PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-144">To double check, use the `tlist` command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="7d5c2-145">Es sollten zwei Instanzen von msvsmon.exe auf dem Gerät vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-145">There should be two instances of msvsmon.exe running on the device.</span></span>

<span data-ttu-id="7d5c2-146">Es ist möglich, dass Visual Studio Remote Debugger zu einem Timeout nach langer Inaktivität.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-146">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="7d5c2-147">Wenn Visual Studio kann nicht auf Ihrem Windows IoT Core-Gerät verbunden sind, starten Sie das Gerät.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-147">If Visual Studio cannot connect to your Windows IoT Core device, try restarting the device.</span></span>

### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="7d5c2-148">Konfigurieren Sie das Gerät Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="7d5c2-148">Configure your Windows IoT Core device</span></span>

<span data-ttu-id="7d5c2-149">Wenn Sie möchten, können Sie Ihr Gerät umbenennen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-149">If you want, you can rename your device.</span></span> 

1. <span data-ttu-id="7d5c2-150">Um den Namen des Computers zu ändern, verwenden die `setcomputername` Hilfsprogramm:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-150">To change the computer name, use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

2. <span data-ttu-id="7d5c2-151">Das Gerät für die Änderung wirksam wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-151">Restart the device for the change to take effect.</span></span> <span data-ttu-id="7d5c2-152">Sie können die `shutdown` -Befehls wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-152">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0

3. <span data-ttu-id="7d5c2-153">Da der Computername geändert wurde, nachdem Sie Sie neu gestartet wird, müssen diesen Befehl, um die Verbindung mit Ihrem Gerät mithilfe des neuen Namens erneut ausführen:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-153">Because the computer name was changed, after you restart you will need to rerun this command to connect to your device using the new name:</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
<span data-ttu-id="7d5c2-154">Ihr Windows IoT Core-Gerät sollte jetzt ordnungsgemäß konfiguriert und einsatzbereit sein!</span><span class="sxs-lookup"><span data-stu-id="7d5c2-154">Your Windows IoT Core device should now be properly configured and ready to use!</span></span>

### <a name="commonly-used-utilities"></a><span data-ttu-id="7d5c2-155">Häufig verwendete Hilfsprogramme</span><span class="sxs-lookup"><span data-stu-id="7d5c2-155">Commonly used utilities</span></span>

<span data-ttu-id="7d5c2-156">Eine Liste der Befehle und Dienstprogramme, die Sie mit PowerShell verwenden können, finden Sie unter den [über die Befehlszeile "utils"](../manage-your-device/CommandLineUtils.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-156">For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page.</span></span>

## <a name="known-issues-and-workarounds"></a><span data-ttu-id="7d5c2-157">Bekannte Probleme und Umgehungen</span><span class="sxs-lookup"><span data-stu-id="7d5c2-157">Known issues and workarounds</span></span>

<span data-ttu-id="7d5c2-158">**PROBLEM**: Ein bekanntes Problem in den PowerShell-Sicherheitsrichtlinien bewirkt, dass die folgenden Probleme, die in der Remotesitzung manifest:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-158">**ISSUE**: A known bug in PowerShell security policies causes the following issues to manifest within the remote session:</span></span>
* <span data-ttu-id="7d5c2-159">Get-Help Gibt unerwartete Übereinstimmungen zurück.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-159">Get-Help returns unexpected matches.</span></span>
* <span data-ttu-id="7d5c2-160">Get-Command, auf ein angegebenes Modul gibt eine leere Liste zurück.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-160">Get-Command on a specified module returns an empty command list.</span></span>
* <span data-ttu-id="7d5c2-161">Ausführen eines Cmdlets aus diesen Modulen löst CommandNotFoundException aus: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-161">Running a cmdlet from any of these modules throws CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span></span>
* <span data-ttu-id="7d5c2-162">Import-Module auf die obigen Module Ausnahme PSSecurityException mit darin.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-162">Import-Module on any of the above modules throws PSSecurityException exception with UnauthorizedAccess.</span></span> <span data-ttu-id="7d5c2-163">Auto-Laden von Modulen scheint nicht zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-163">Module auto loading does not seem to work either.</span></span>

<span data-ttu-id="7d5c2-164">**Problemumgehung**: Ändern Sie die Ausführungsrichtlinie in der PowerShell-Remotesitzung zu **"RemoteSigned"**.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-164">**Workaround**: Modify the execution policy within the remote PowerShell session to **RemoteSigned**.</span></span> <span data-ttu-id="7d5c2-165">Weitere Informationen zu den verschiedenen Ausführungsrichtlinien, finden Sie unter [mithilfe des Cmdlets Set-ExecutionPolicy](https://technet.microsoft.com/library/ee176961.aspx).</span><span class="sxs-lookup"><span data-stu-id="7d5c2-165">For more details on the different execution policies, see [Using the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx).</span></span>

<span data-ttu-id="7d5c2-166">**PROBLEM**: Manchmal sind die Cmdlets aus einigen Modulen wie z. B. NetAdapter nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-166">**ISSUE**: Cmdlets from some modules such as NetAdapter are sometimes not visible.</span></span> <span data-ttu-id="7d5c2-167">Get-Module NetAdapter gibt beispielsweise eine leere Liste zurück.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-167">For example, Get-Module NetAdapter returns an empty list.</span></span> 

<span data-ttu-id="7d5c2-168">**Problemumgehung**: Verwendet den - Force-Parameter mit Import-Module.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-168">**Workaround**: Use the -Force parameter with Import-Module.</span></span> <span data-ttu-id="7d5c2-169">Beispiel: `Import-Module NetAdapter -Force`Hyper-V-Hosts oder Hyper-V-Hostcluster in einem separaten Namespace als verwaltete Hyper-V-Hosts hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-169">For example, `Import-Module NetAdapter -Force`.</span></span>

<span data-ttu-id="7d5c2-170">**PROBLEM**: Festlegen der Ausführungsrichtlinie "AllSigned" unterbricht die PowerShell-Remoting.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-170">**ISSUE**: Setting execution policy to "AllSigned" breaks PowerShell remoting.</span></span> <span data-ttu-id="7d5c2-171">Nachfolgende Versuche zum Erstellen einer Remotesitzung fehl mit SecurityException Typesv3.ps1xml werden geladen.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-171">Subsequent attempts to create a remote session fail with a SecurityException loading Typesv3.ps1xml.</span></span> 

<span data-ttu-id="7d5c2-172">**Problemumgehung**: Verwenden Sie winrs.exe, um die Ausführungsrichtlinie von PowerShell wiederherstellen:</span><span class="sxs-lookup"><span data-stu-id="7d5c2-172">**Workaround**: Use winrs.exe to restore PowerShell's execution policy:</span></span>
* <span data-ttu-id="7d5c2-173">Console-Codepage ändern</span><span class="sxs-lookup"><span data-stu-id="7d5c2-173">Change console code page</span></span> `Chcp 65001`
* <span data-ttu-id="7d5c2-174">Melden Sie sich an einen Remoteserver cmd.exe-shell</span><span class="sxs-lookup"><span data-stu-id="7d5c2-174">Log on to a remote cmd.exe shell</span></span> `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* <span data-ttu-id="7d5c2-175">Ändern Sie den entsprechenden Registrierungsschlüssel in remote cmd.exe</span><span class="sxs-lookup"><span data-stu-id="7d5c2-175">Within remote cmd.exe, modify the appropriate registry key</span></span> `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* <span data-ttu-id="7d5c2-176">Beenden Sie remote cmd.exe-Sitzung</span><span class="sxs-lookup"><span data-stu-id="7d5c2-176">Exit remote cmd.exe session</span></span> `exit`

### <a name="other-known-issues"></a><span data-ttu-id="7d5c2-177">Andere bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="7d5c2-177">Other known issues</span></span>

- <span data-ttu-id="7d5c2-178">In PowerShell-Skripts funktionieren Attribute, die PowerShell-Klasse oder eines Enumerationswerts nicht.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-178">In PowerShell scripts, attributes to PowerShell class or enumeration do not work.</span></span> <span data-ttu-id="7d5c2-179">Hinzufügen von attributierten führt die folgende Ausnahme ausgelöst: *Typ muss ein Typ-Laufzeitobjekt*.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-179">Adding attributed results in the following exception thrown: *Type must be a runtime Type object*.</span></span>

- <span data-ttu-id="7d5c2-180">Ausgehende CIM und PowerShell-Remoting wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-180">Outbound CIM and PowerShell remoting is not supported.</span></span> <span data-ttu-id="7d5c2-181">Relevante Funktionen in der vertrauenden Seite-Cmdlets sind nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-181">Relevant functionality in relying cmdlets will not work.</span></span> <span data-ttu-id="7d5c2-182">Dazu gehören die Receive-Job, Import-Module, Enter-PSSession, Get-Job, Invoke-Command und Copy-Item.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-182">These include  Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command, and Copy-Item.</span></span>

- <span data-ttu-id="7d5c2-183">SecureString Befehle ConvertFrom-SecureString "und" ConvertTo-SecureString funktionieren nicht, es sei denn, die Sitzung die CredSSP-Authentifizierung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-183">SecureString commands ConvertFrom-SecureString and ConvertTo-SecureString do not work unless the session is created using CredSSP authentication.</span></span> <span data-ttu-id="7d5c2-184">Andernfalls den - Schlüssel muss Parameter angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7d5c2-184">Otherwise, the -Key parameter must be specified.</span></span> <span data-ttu-id="7d5c2-185">Weitere Informationen zum Konfigurieren von CredSSP-Authentifizierung finden Sie unter [das Problem "Doppelhop"](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span><span class="sxs-lookup"><span data-stu-id="7d5c2-185">For details on configuring CredSSP authentication, see [The “Double-Hop” Problem](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span></span>


