---
title: Einrichten Ihres Geräts
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: Weitere Informationen zum Einrichten Ihres Geräts mit Windows 10 IoT Core eine SD-Karte.
keywords: Windows 10 IoT Core, SD-Karte Windows 10 IoT Core Dashboard
ms.custom: RS5
ms.openlocfilehash: ece83dcc7f6961a4614db2ee0c6a1331b009bb47
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512402"
---
# <a name="setting-up-your-device"></a>Einrichten Ihres Geräts

Im folgenden finden Sie vier Möglichkeiten, um Ihr Gerät mit Windows 10 IoT Core zu aktualisieren. Basierend auf dem Diagramm in die [Liste der vorgeschlagenen Boards zum Erstellen von Prototypen](PrototypeBoards.md), befolgen Sie die entsprechenden Anweisungen. Verwenden Sie die rechte Spalte zum Navigieren zwischen diesen unterschiedlichen Methoden der blinken.

> [!IMPORTANT]
> Verwenden Sie Maker Images nicht für gewerbliche Nutzung aus. Wenn Sie ein Gerät commercializing sind, müssen Sie eine benutzerdefinierte FFU für optimale Sicherheit verwenden. Weitere Informationen finden Sie [hier](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

> [!IMPORTANT]
> Wenn die "formatieren Sie diesen Datenträger" Popupfenster bis angezeigt werden, führen Sie _nicht_ formatieren Sie den Datenträger. Wir arbeiten an der Behebung dieses Problems.

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a>Mithilfe des IoT-Dashboards (Raspberry Pi, MinnowBoard NXP)

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> Die aktuelle 64-Bit-Firmware für MinnowBoard Turbot finden Sie auf die [MinnowBoard Website](https://minnowboard.org/tutorials/updating-the-firmware) (überspringen Sie Schritt 4 des Standorts MinnowBoard-Anweisungen).

> [!IMPORTANT]
> NXP unterstützt nur benutzerdefinierte Images. Wenn Sie ein benutzerdefiniertes Image flash, wählen Sie "Benutzerdefiniert" aus der Dropdownliste "Betriebssystembuild" suchen, folgen Sie den Anweisungen [hier](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) zum Erstellen einer Basis-Image und führen die restlichen die nachstehenden Anweisungen, um den Vorgang abzuschließen.

> [!NOTE]
> Dashboard kann nicht verwendet, um den Raspberry Pi 3 b + setup verwendet werden. Wenn Sie eine 3 b +-Gerät verfügen, müssen Sie verwenden die [technical Preview 3 b +](https://www.microsoft.com/en-us/software-download/windowsiot). Lesen Sie die [bekannte Einschränkungen](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) der technical Preview zu bestimmen, ob dies für die Entwicklung geeignet ist.

> [!TIP]
> Es wird empfohlen, verwenden eine Hochleistungs-SD-Karte, wie z. B. eine SanDisk SD-Karte für höhere Stabilität als auch das Anschließen des Geräts in einen externen Monitor, der Standard-Anwendung starten, finden Sie unter.


1. Laden Sie das Windows 10 IoT Core Dashboard [hier](https://docs.microsoft.com/windows/iot-core/downloads).
2. Nachdem Sie heruntergeladen haben, öffnen Sie das Dashboard, und klicken Sie auf _richten Sie ein neues Gerät_ , und fügen Sie eine SD-Karte in Ihren Computer.
3. Füllen Sie alle Felder ein, wie angegeben.
4. Die Software-Lizenzbedingungen akzeptieren, und klicken Sie auf _herunterladen und installieren_. Sie sehen, dass Windows 10 IoT Core nun Ihre SD-Karte blinkt.


![Screenshot des Dashboards](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a>Mithilfe des IoT-Dashboards (DragonBoard 410c)

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> Es wird empfohlen, Ihr Gerät anschließen, in einen externen Monitor, der Standard-Anwendung starten, finden Sie unter.

> [!IMPORTANT]
> Wenn Sie ein benutzerdefiniertes Image flash, wählen Sie "Benutzerdefiniert" aus der Dropdownliste "Betriebssystembuild" suchen, folgen Sie den Anweisungen [hier](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) zum Erstellen einer Basis-Image und führen die restlichen die nachstehenden Anweisungen, um den Vorgang abzuschließen.

> [!IMPORTANT]
> Wenn Sie mit einem neuen Dragonboard arbeiten, erfolgt mit Android installiert. Sie müssen zum Zurücksetzen und laden das Gerät mithilfe der blinkende eMMC-Methode.

> [!NOTE]
> Wenn Sie Audio-bezogene Probleme mit Ihrem DragonBoard ausführen, es wird empfohlen, dass Sie Qualcomms manuelle lesen [hier](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf). 

1. Laden Sie das Windows 10 IoT Core Dashboard [hier](https://docs.microsoft.com/windows/iot-core/downloads).
2. Nachdem Sie heruntergeladen haben, öffnen Sie das Dashboard aus, und wählen Sie "Qualcomm DragonBoard 410c". Klicken Sie dann _melden Sie sich als ein Windows-Insider_. Sie müssen als Insider angemeldet sein, um flash DragonBoard 410 c. 
3. Verbinden Sie das Board Qualcomm, mit dem Entwicklercomputer über ein Kabel MicroUSB.
4. Schalten Sie Ihr mit einer 12 v bei Dragonboard (> 1A) Netzteil (+) zum Erhöhen der Lautstärke gedrückter Schaltfläche. Das Gerät - beim Verbinden mit einer Anzeige - sollte das Image von einem Hammer, Blitz und ein Zahnradsymbol angezeigt werden. 
5. Das Gerät sollte jetzt auf dem Dashboard wie unten dargestellt angezeigt werden. Wählen Sie das entsprechende Gerät.
6. Die Software-Lizenzbedingungen akzeptieren, und klicken Sie auf _herunterladen und installieren_. Sie sehen, dass Windows 10 IoT Core jetzt auf Ihrem Gerät blinkt.


![DragonBoard im flash-Modus](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a>Blinken mit eMMC (für andere Geräte Qualcomm DragonBoard 410c)

1. Herunterladen und installieren Sie das DragonBoard Update-Tool für Ihre [X86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) oder [X64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) Computer.
2. Herunterladen der [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).
3. Doppelklicken Sie auf das heruntergeladene ISO-Datei, und suchen Sie das bereitgestellte Virtual CD-Laufwerk. Dieses Laufwerk ist eine Installer-Datei (.msi); enthalten. Doppelklicken Sie darauf. Dies erstellt ein neues Verzeichnis auf Ihrem PC unter `C:\Program Files (x86)\Microsoft IoT\FFU\` in die im Normalfall eine Bilddatei, "flash.ffu".
4. Stellen Sie sicher, dass Ihre DragonBoard befindet sich im Downloadmodus von der erste Start auf dem Board wechseln Sie zum Starten von USB-Einstellung, wie unten dargestellt. Klicken Sie dann eine Verbindung DragonBoard Host-PCs über ein Kabel MicroUSB, dann geben Sie die DragonBoard auf eine 12 v bei (> 1A) Netzteil.
5. Starten Sie das DragonBoard-Update-Tool, das erkennt, dass die DragonBoard verbunden, auf Ihren PC mit einem grünen Kreis. "Durchsuchen", um die DragonBoard des FFU, die Sie heruntergeladen haben, klicken Sie dann auf die _Programm_ Schaltfläche.
6. Klicken Sie erneut auf "Durchsuchen", und wählen Sie "rawprogram0.xml", die in Schritt 5 generiert wurde. Klicken Sie dann auf die Schaltfläche "Program".
7. Sobald der Download abgeschlossen ist, trennen Sie das Stromkabel für Bereitstellung und MicroUSB aus dem Board und ein-/ausschalten, das USB-Start wechseln zurück zu _OFF_. Verbinden Sie eine HDMI-Anzeige, Maus und Tastatur, mit den DragonBoard und Rec-Verbinden der Stromversorgung. Nach einigen Minuten sollte die standardmäßige Windows 10 IoT Core-Anwendung angezeigt werden. 

![DragonBoard im Downloadmodus](../../media/DeviceSetup/db1.png)

> [!NOTE]
> Stellen Sie sicher, dass das Gerät jetzt aus dem Arbeitsspeicher eMMC gestartet wird, von BIOS-Setup erneut einzugeben, und der Startlaufwerk Reihenfolge von der Festplatte statt über das USB-Laufwerk geladen.


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a>Blinken mit eMMC (für die sich im Quadrat, andere Geräte Intel)

1. Herunterladen und Installieren der [Windows-Assessment and Deployment Kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) mit der korrelierenden Version von Windows 10 ausgeführt wird.
2. Fügen Sie ein USB-Laufwerk auf Ihrem Computer.
3. Erstellen Sie einen startfähigen USB-WinPE-Abbild:
4. Starten Sie die Bereitstellung und Abbilderstellung Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` als Administrator.
5. Erstellen Sie eine Arbeitskopie der Windows PE-Dateien. Geben Sie x X86, amd64 oder ARM: `Copype amd64 C:\WINPE_amd64`
6. Installieren Sie Windows PE auf dem USB-Flashlaufwerk, den folgenden Windows PE-Laufwerkbuchstaben angeben. Weitere Informationen finden Sie [hier](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive). `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. Herunterladen der [Windows 10 IoT Core-Image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) durch Doppelklicken auf das heruntergeladene ISO-Datei, und suchen das bereitgestellte Virtual CD-Laufwerk.
8. Dieses Laufwerk enthält eine Installationsdatei (MSI); Doppelklicken. Dadurch wird ein neues Verzeichnis erstellt, auf Ihrem PC unter C:\Program Files (x86) \Microsoft IoT\FFU\ in dem Sie Shoul d finden Sie in eine Bilddatei, "flash.ffu".
9. Laden Sie herunter, entpacken Sie aus, und kopieren Sie die [eMMC Installationsskript](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) zum Stammverzeichnis des USB-Geräts, zusammen mit des Geräts FFU.
10. Verbinden Sie das USB-Laufwerk, Maus und Tastatur mit der USB-Hub an. Fügen Sie der HDMI-Anzeige auf Ihrem Gerät, das Gerät an den USB-Hub, und das Netzkabel an das Gerät an.
11. Fahren Sie mit der BIOS-Setup des Geräts. Wählen Sie *Windows* als Betriebssystem und legen Sie das Gerät, von dem USB-Laufwerk zu starten. Wenn das System neu gestartet wird, sehen Sie die Windows PE-Eingabeaufforderung. Wechseln Sie die Windows PE-Eingabeaufforderung auf das USB-Laufwerk ein. Dies ist normalerweise C: oder D:, aber Sie müssen möglicherweise andere Laufwerkbuchstaben versuchen Sie es.
12. Führen Sie das Installationsprogramm das Skript, das das Windows 10 IoT Core-Image, um den Speicher des Geräts eMMC installiert wird eMMC. Wenn der Vorgang abgeschlossen ist, drücken Sie eine beliebige Taste, und führen Sie `wpeutil reboot`. Das System sollte starten Sie Windows 10 IoT Core, starten Sie den Konfigurationsprozess und laden die standardanwendung.

> [!NOTE]
> Stellen Sie sicher, dass das Gerät jetzt aus dem Arbeitsspeicher eMMC gestartet wird, von BIOS-Setup erneut einzugeben, und der Startlaufwerk Reihenfolge von der Festplatte statt über das USB-Laufwerk geladen.


## <a name="connecting-to-a-network"></a>Herstellen einer Verbindung mit einem Netzwerk

#### <a name="wired-connection"></a>Kabelverbindung
Wenn Ihr Gerät mit einem Ethernet-Port oder die Unterstützung für USB-Ethernet-Adapter zu einer Kabelverbindung stammt, fügen Sie ein Ethernet-Kabel für die Verbindung mit Ihrem Netzwerk.

#### <a name="wireless-connection"></a>Drahtlose Verbindung
Wenn Ihr Gerät, Wi-Fi-Verbindungen unterstützt, und Sie haben es eine Anzeige verbunden, müssen Sie:

1. Wechseln Sie in die standardanwendung, und klicken Sie auf die Schaltfläche "Einstellungen" neben der Uhr.
2. Wählen Sie auf der Seite "Einstellungen" _Netzwerk- und Wi-Fi_.
3. Ihr Gerät beginnt die Überprüfung auf drahtlose Netzwerke.
4. Wenn Ihr Netzwerk in der Liste angezeigt wird, wählen Sie ihn, und klicken Sie auf _Connect_.

Wenn Sie noch nicht mit eine Anzeige verbunden und über Wi-Fi eine Verbindung herstellen möchten, müssen Sie:

1. Wechseln Sie zu der IoT-Dashboard, und klicken Sie auf _meine Geräte_.
2. Finden Sie das Board nicht konfigurierte, aus der Liste. Der Name beginnt mit "AJ_"... (z. B. AJ_58EA6C68). Wenn Sie nicht, dass das Board nach einigen Minuten angezeigt werden sehen, versuchen Sie es Ihrem Board Neustart.
3. Klicken Sie auf _Gerätekonfiguration_ , und geben Sie Ihre Anmeldeinformationen für das Netzwerk. Dadurch wird das Board mit dem Netzwerk verbinden.

> [!NOTE]
> WLAN auf Ihrem Computer muss eingeschaltet sein, um anderen Netzwerken zu finden.

## <a name="connecting-to-windows-device-portal"></a>Herstellen einer Verbindung mit Windows Device Portal

Verwenden der [Windows Device Portal](../../manage-your-device/DevicePortal.md) Verbinden Ihres Geräts über einen Webbrowser. Das Device Portal stellt nützliche Konfigurations- und Verwaltungsfunktionen für Geräte zur Verfügung. 

