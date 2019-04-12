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
# <a name="using-powershell-for-windows-iot"></a>Mithilfe von PowerShell für Windows IoT

Remote konfigurieren und Verwalten von einem beliebigen Gerät für Windows 10 IoT Core mithilfe von Windows PowerShell.
PowerShell ist eine aufgabenbasierte Befehlszeilenshell und Skriptsprache, die speziell für die systemverwaltung konzipiert.

Stellen Sie sicher, dass diese Schritte ausführen, um Ihr Gerät mit Windows 10 IoT Core funktioniert auch mit Visual Studio 2017 ordnungsgemäß zu konfigurieren.

## <a name="initiating-a-powershell-session"></a>Initiieren eine PowerShell-Sitzung
1. Um eine PowerShell-Sitzung mit Ihrem Windows 10 IoT Core-Gerät zu starten, müssen Sie zuerst eine Vertrauensstellung zwischen Ihrem Host-PC und Ihr Gerät zu erstellen. Nach dem Starten Ihres Geräts für die Windows IoT Core, wird eine IP-Adresse auf dem Bildschirm des Geräts angezeigt.

    ![DefaultApp auf Windows 10 IoT Core](../media/PowerShell/DefaultApp.png)

   Sie finden die gleiche Informationen auf dem Windows 10 IoT Core Dashboard.

2. Öffnen Sie eine Administrator-PowerShell-Konsole auf dem lokalen Computer. Typ **Powershell** in die **suchen im Web und auf Windows** Feld in der Nähe der Windows-Startmenü. Windows finden PowerShell auf Ihrem PC.

    ![Finden von PowerShell](../media/PowerShell/start-ps.png)

3. Zum Starten von PowerShell als Administrator Maustaste **Windows PowerShell**, und wählen Sie dann **als Administrator ausführen**.

    ![Führen Sie PowerShell als administrator](../media/PowerShell/start-ps2.png)

   Jetzt sollte die PowerShell-Konsole angezeigt werden.

    ![PowerShell-Konsole](../media/PowerShell/ps.PNG)

4. Sie müssen möglicherweise starten den WinRM-Dienst auf dem Desktop, um Remoteverbindungen zu aktivieren. Geben Sie an der PowerShell-Konsole dazu, den folgenden Befehl ein:

        net start WinRM

5. Über die PowerShell-Konsole, geben Sie Folgendes ein, und Ersetzen Sie dabei `<machine-name or IP address>` mit den entsprechenden Wert (mit Ihrer **Computername** ist das einfachste, aber wenn Ihr Gerät eindeutig in Ihrem Netzwerk, nicht heißt wiederholen Sie die IP-Adresse):

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. Geben Sie `Y` um die Änderung zu bestätigen.

> [!NOTE]
> Wenn Sie mehrere Geräte eine Verbindung herstellen möchten, können Sie Kommas und Anführungszeichen ein, um jedes Gerät zu trennen können.
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. Nun können Sie eine Sitzung mit Ihrem Gerät Windows IoT Core beginnen. Geben Sie PowerShell-Administratorkonsole:

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. Geben Sie in das Dialogfeld "Anmeldeinformationen" das Standardkennwort für die folgenden aus: `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span> HINWEIS </h5>
      <p>Der Verbindungsprozess erfolgt nicht sofort, und es kann bis zu 30 Sekunden dauern.</p>
    </div>    
    
    Wenn Sie erfolgreich auf dem Gerät verbunden, sehen Sie die IP-Adresse Ihres Geräts, bevor Sie die Eingabeaufforderung.

    ![PowerShell-Konsole](../media/PowerShell/ps_device.png)

9. Kennwort für Ihr Konto zu aktualisieren. Wir *wird dringend empfohlen,* , das Standardkennwort für das Administratorkonto zu aktualisieren. Zu diesem Zweck geben Sie die folgenden Befehle in Ihrer PowerShell-Verbindung:

    a. Ersetzen Sie dies `[new password]` durch ein sicheres Kennwort:
    
            net user Administrator [new password]
            
    b. Als Nächstes Einrichten einer neuen PowerShell-Sitzung, mit `Exit-PSSession` und `Enter-PSSession` mit den neuen Anmeldeinformationen.
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a>Häufig verwendete PowerShell-Befehle

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>Problembehandlung mit Visual Studio Remote Debugger

Um zum Bereitstellen von Anwendungen aus Visual Studio 2017 können, müssen Sie sicherstellen, dass die Visual Studio Remote Debugger auf Ihrem Gerät Windows IoT Core ausgeführt wird. Der Remotedebugger sollte automatisch geöffnet, wenn Sie Ihre Computer starten. Verwenden Sie zum Überprüfen, die `tlist` Befehl zum Auflisten alle ausgeführten Prozesse über PowerShell. Es sollten zwei Instanzen von msvsmon.exe auf dem Gerät vorhanden sein.

Es ist möglich, dass Visual Studio Remote Debugger zu einem Timeout nach langer Inaktivität. Wenn Visual Studio kann nicht auf Ihrem Windows IoT Core-Gerät verbunden sind, starten Sie das Gerät.

### <a name="configure-your-windows-iot-core-device"></a>Konfigurieren Sie das Gerät Windows IoT Core

Wenn Sie möchten, können Sie Ihr Gerät umbenennen. 

1. Um den Namen des Computers zu ändern, verwenden die `setcomputername` Hilfsprogramm:

        setcomputername <new-name>

2. Das Gerät für die Änderung wirksam wird neu gestartet. Sie können die `shutdown` -Befehls wie folgt:

        shutdown /r /t 0

3. Da der Computername geändert wurde, nachdem Sie Sie neu gestartet wird, müssen diesen Befehl, um die Verbindung mit Ihrem Gerät mithilfe des neuen Namens erneut ausführen:

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
Ihr Windows IoT Core-Gerät sollte jetzt ordnungsgemäß konfiguriert und einsatzbereit sein!

### <a name="commonly-used-utilities"></a>Häufig verwendete Hilfsprogramme

Eine Liste der Befehle und Dienstprogramme, die Sie mit PowerShell verwenden können, finden Sie unter den [über die Befehlszeile "utils"](../manage-your-device/CommandLineUtils.md) Seite.

## <a name="known-issues-and-workarounds"></a>Bekannte Probleme und Umgehungen

**PROBLEM**: Ein bekanntes Problem in den PowerShell-Sicherheitsrichtlinien bewirkt, dass die folgenden Probleme, die in der Remotesitzung manifest:
* Get-Help Gibt unerwartete Übereinstimmungen zurück.
* Get-Command, auf ein angegebenes Modul gibt eine leere Liste zurück.
* Ausführen eines Cmdlets aus diesen Modulen löst CommandNotFoundException aus: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.
* Import-Module auf die obigen Module Ausnahme PSSecurityException mit darin. Auto-Laden von Modulen scheint nicht zu funktionieren.

**Problemumgehung**: Ändern Sie die Ausführungsrichtlinie in der PowerShell-Remotesitzung zu **"RemoteSigned"**. Weitere Informationen zu den verschiedenen Ausführungsrichtlinien, finden Sie unter [mithilfe des Cmdlets Set-ExecutionPolicy](https://technet.microsoft.com/library/ee176961.aspx).

**PROBLEM**: Manchmal sind die Cmdlets aus einigen Modulen wie z. B. NetAdapter nicht sichtbar. Get-Module NetAdapter gibt beispielsweise eine leere Liste zurück. 

**Problemumgehung**: Verwendet den - Force-Parameter mit Import-Module. Beispiel: `Import-Module NetAdapter -Force`Hyper-V-Hosts oder Hyper-V-Hostcluster in einem separaten Namespace als verwaltete Hyper-V-Hosts hinzuzufügen.

**PROBLEM**: Festlegen der Ausführungsrichtlinie "AllSigned" unterbricht die PowerShell-Remoting. Nachfolgende Versuche zum Erstellen einer Remotesitzung fehl mit SecurityException Typesv3.ps1xml werden geladen. 

**Problemumgehung**: Verwenden Sie winrs.exe, um die Ausführungsrichtlinie von PowerShell wiederherstellen:
* Console-Codepage ändern `Chcp 65001`
* Melden Sie sich an einen Remoteserver cmd.exe-shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* Ändern Sie den entsprechenden Registrierungsschlüssel in remote cmd.exe `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* Beenden Sie remote cmd.exe-Sitzung `exit`

### <a name="other-known-issues"></a>Andere bekannte Probleme

- In PowerShell-Skripts funktionieren Attribute, die PowerShell-Klasse oder eines Enumerationswerts nicht. Hinzufügen von attributierten führt die folgende Ausnahme ausgelöst: *Typ muss ein Typ-Laufzeitobjekt*.

- Ausgehende CIM und PowerShell-Remoting wird nicht unterstützt. Relevante Funktionen in der vertrauenden Seite-Cmdlets sind nicht verfügbar. Dazu gehören die Receive-Job, Import-Module, Enter-PSSession, Get-Job, Invoke-Command und Copy-Item.

- SecureString Befehle ConvertFrom-SecureString "und" ConvertTo-SecureString funktionieren nicht, es sei denn, die Sitzung die CredSSP-Authentifizierung erstellt wird. Andernfalls den - Schlüssel muss Parameter angegeben werden. Weitere Informationen zum Konfigurieren von CredSSP-Authentifizierung finden Sie unter [das Problem "Doppelhop"](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).


