---
title: Erfassen von Fiddler-Ablaufverfolgungen
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Fiddler verwenden, um das Erfassen von Fiddler-ablaufverfolgungen unter Windows IoT Core.
keywords: Windows Iot, Fiddler, ablaufverfolgungen, PuTTY, Fiddler-ablaufverfolgungen
ms.openlocfilehash: b8bf4fa6390aad9640ad9139a8a164a9c83fcff5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513289"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>Erfassen von Fiddler-Ablaufverfolgungen unter Windows IoT Core

Fiddler ist ein Tool zum Debuggen von Webdatenverkehr an. Es ist besonders hilfreich, da Sie es für bestimmte Anforderungen, die mithilfe von Erweiterungen und Add-ons anpassen und das Tool viele nützliche Informationen, die spezifisch für Webdatenverkehr können bietet.

## <a name="assumptions"></a>Annahmen 

* Sie haben [PuTTY](http://www.putty.org/) auf der entwicklerbox oder eine Alternative für SSH
* Die folgenden Anweisungen führen zu der Annahme einer IoT Core VM, aber funktioniert auf *alle* IoT Core-Geräts

## <a name="initial-setup"></a>Anfangssetup

1. Herunterladen und installieren Sie die neueste Version des [Fiddler](http://www.telerik.com/fiddler/) auf der entwicklerbox, sofern Sie noch nicht geschehen.
2. Starten Sie Fiddler, und stellen Sie die folgende Einstellung Updates unter _Extras -> Telerik Fiddler-Optionen -> HTTPS_ Registerkarte
    * Überprüfen Sie _HTTPS CONNECTs erfassen_
    * Überprüfen Sie _HTTPS-Datenverkehr entschlüsseln, die von allen Prozessen ->_
    * Klicken Sie auf den Link "Von generierten Zertifikate", und wählen Sie _"MakeCert"-Engine_ (Empfehlung: Fiddler für diese Änderung wirksam wird neu gestartet)
    * Exportieren Sie als Nächstes die Datei FiddlerRoot.cer über _Aktionen -> Root-Zertifikat auf Desktop exportieren_
3. Nehmen Sie folgende Einstellung Änderungen unter _Telerik Fiddler-Optionen für Extras -> Verbindungen ->_ Registerkarte:
    * Einrichten von Fiddler, fungiert als systemproxy anhand _Remotecomputern zum Herstellen einer Verbindung zulassen_
    * _Fiddler Lauscht auf Port_ sollte festgelegt werden, um _8888_
  
Hinweis: Sie starten Sie Fiddler anschließend neu, und akzeptieren alle UAC-Eingabeaufforderung.

## <a name="transfer-and-import-fiddler-root-certificate"></a>Übertragen Sie und importieren Sie Fiddler-Stammzertifikat
Sie müssen das Stammzertifikat Fiddler auf Ihren IoT-Image oder zu importieren, um Https routing von Datenverkehr über den PC zu debuggen.  Gehen Sie dazu wie folgt vor:

1. Einbinden die VHD-Datei (klicken Sie mit der rechten Maustaste auf die virtuelle Festplatte, und wählen Sie _einbinden_) oder eine Verbindung mit Ihrem IoT-Gerät per PuTTY herstellen (oder anderen SSH-Client)
2. Navigieren Sie zu der Partition MainOS und erstellen Sie eine _testen_ Ordner Stamm (über SSH verwenden _Md c:\test_)
3. Kopieren Sie zuvor generierten FiddlerRoot.cer (sollte auf Ihrem Desktop standardmäßig sein) in den Test-Ordner
4. Wenn Sie eine virtuelle Festplatte verwenden zu können, indem jedem bereitgestelltes Laufwerk auswerfen heben Sie auf und dann starten Sie die IoT-Core-VM über Hyper-v
5. Starten einer [SSH-Sitzung](../connect-your-device/ssh.md) und melden Sie sich als Administrator 
6. Navigieren Sie zu c:\test-Verzeichnis, in der SSH-Sitzung
7. Importieren Sie Fiddler-Stammzertifikats per Befehl:
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. SSH-Sitzung schließen


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>Einrichten der Proxy auf dem virtuellen Computer oder IoT Core-Geräts
Die folgenden Schritte werden Ihre IoT-VM oder ein Gerät zum Weiterleiten von Datenverkehr über den PC zulassen, damit, Fiddler Netzwerkdatenverkehr für die Analyse erfassen kann:

1. Bestimmen Sie die IP-Adresse Ihres Entwicklungscomputers, die über eine CMD-Konsole über _Ipconfig_
2. Starten Sie eine neue SSH-Sitzung, und dieses Mal ist, melden Sie sich als DefaultUser (Benutzername: _DefaultAccount_ Pwd: _[leere]_ )
3. Legen Sie den Proxy über die folgenden Befehle ein:
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

Wenn nicht bereits ausgeführt wird, starten Sie Fiddler auf Ihrem PC, Neustarten des virtuellen Computers oder IoT Core-Geräts ein, und Datenverkehr an Fiddler jetzt weitergeleitet werden soll. 

Hinweis: Wenn Sie Https-Verbindung in Fiddler, aber keine Daten angezeigt wird, wurde das Zertifikat wahrscheinlich nicht ordnungsgemäß installiert. Stellen Sie sicher, dass Sie nicht verpassen der _übertragen und Import Fiddler-Stammzertifikat_ oben beschriebenen Schritte.

Veröffentlichungsanzahl, wenn Sie den Proxy wieder aus Anmerkung aktivieren, dass die oben genannten Registrierungsschlüssel in ein binäres Blob in einen anderen Schlüssel zwischengespeichert abrufen möchten. Daher müssen zusätzlich zum Entfernen von oben Sie in Schritt 3 hinzugefügten Schlüssel auch Schritte ausführen:

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
