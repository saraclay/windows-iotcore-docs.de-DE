---
title: Media Transfer-Protokoll
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
description: Erfahren Sie, wie Sie die optionale Funktion von Medien-Transfer-Protokolls (MTP) zum Übertragen von Dateien in und aus Ihrer Geräte über USB zu aktivieren.
keywords: Windows Iot, MTP, Media transfer-Protokoll, die Übertragung von Dateien, die Geräte
ms.openlocfilehash: 72856617c8d49a1b06eadd13ab5fb085340d2ed4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512322"
---
# <a name="media-transfer-protocol"></a>Media Transfer-Protokoll
Des Media Transfer-Protokolls (MTP) ermöglicht Ihnen, zum Übertragen von Dateien in und aus Ihr Windows 10 IoT Core-Gerät per USB. Sie können den Zugriff auf internen Speicher des Geräts und der SD-Karte, falls vorhanden.

Das Feature ist Teil der IoT-Core-Kits, die heruntergeladen und installiert werden kann die [Windows 10 IoT Core Pakete](https://www.microsoft.com/en-us/download/details.aspx?id=55031).

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>Gewusst wie: Installieren des MTP-Features auf einem Gerät mit Windows 10 IoT Core

### <a name="provisioning-the-device-with-required-packages"></a>Bereitstellen des Geräts mit der erforderlichen Pakete

1. Starten Sie [Powershell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md) und greifen Sie auf Ihrem Gerät Windows 10 IoT Core ausgeführt.
2. Führen Sie über Powershell oder SSH folgende Schritte aus:
    1. Erstellen Sie einen temporären Ordner auf dem Zielcomputer (z. B. `C:\MTPTemp`).
    2. Kopieren Sie die folgenden Pakete basierend auf Ihrem Gerät die Architektur von Ihrem PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) zu `C:\MTPTemp`:
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. Führen Sie folgende Befehle aus `C:\MTPTemp` zum Installieren der Pakete auf Ihrem IoT-Gerät-Systemabbild:
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. Das Gerät wird gestartet wird, um die Betriebssystemversion aktualisieren, die MTP-Funktion installieren und neu starten, um die MainOS.

### <a name="enabling-the-mtp-usb-interface"></a>Aktivieren die MTP USB-Schnittstelle

Sobald das Gerät wieder auf die MainOS verfügbar ist, muss die USBFN Konfiguration immer noch aktualisiert werden, um das Einschließen von MTP. Zu diesem Zweck müssen Sie die Schnittstellen aufgelistet USBFN MTP hinzu.
Die [USB-registrierungseinstellungen](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) Artikel wird erläutert, die Details des USB-Konfiguration.

Während Sie die USBFN-Standardkonfiguration, die unter ändern, können die `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` Schlüssel, es wird empfohlen, Ihre eigenen definieren, wie sie von Systemupdates nicht überschrieben werden.

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>Erstellen eine neue USBFN-Konfiguration mit der MTP-Schnittstelle

Um eine neue Konfiguration für MTP hinzuzufügen, gehen Sie wie folgt vor:
1. Hinzufügen eines neuen Schlüssels unter `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`. Beispiel: `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`.
2. Erstellen Sie unter den neuen Schlüssel ein `REG_MULTI_SZ` Wert `InterfaceList` gleich `MTP`.
3. Erstellen Sie unter dem gleichen Schlüssel eine `REG_BINARY` Wert `MSOSCompatIdDescriptor` gleich `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`.
4. Klicken Sie unter `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` fügen Sie einen neuen `REG_SZ` Wert `CurrentConfiguration` gleich dem Namen des neu erstellten Schlüssels. In diesem Fall wäre es `MyConfiguration`.
5. [**Optional**] unter `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` fügen Sie einen neuen `REG_DWORD` Wert `IncludeDefaultCfg` gleich 1. Dies veranlasst, dass den USB-Treiber die Standard-Schnittstellen zusammen mit MTP aufgelistet werden.

> [!NOTE]
> Wenn Sie bereits eine benutzerdefinierte Konfiguration verwenden, müssen Sie es ändern, anstatt einen neuen zu erstellen.

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>Hinzufügen der MTP-Schnittstelle zu einer vorhandenen Konfiguration

Um eine vorhandene Konfiguration einer USBFN MTP hinzuzufügen, gehen Sie wie folgt vor:
1. Suchen Sie die aktuelle Konfiguration anhand der `CurrentConfiguration` Wert `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`. Wenn der Wert vorhanden ist, wird die aktuelle Konfiguration Sie unter finden `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`. Andernfalls ist es unter `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`.
2. Fügen Sie unterhalb der aktuellen Konfigurationsschlüssel `\0MTP` auf den Wert der `InterfaceList`. Die ***\0*** Teil wird verwendet, mit dem Typ der `InterfaceList` ist `REG_MULTI_SZ` müssen Sie das Trennzeichen zwischen Werten.
3. Ändern der `MSOSCompatIdDescriptor` Wert einschließen des MTP Deskriptor. Damit erstellen Sie einen gültigen-Deskriptor mit derzeit alle Schnittstellen, unter dem `InterfaceList` Wert, führen Sie die Anweisungen Dokumentation zur Verfügung, am unteren Rand [auf dieser Seite](https://msdn.microsoft.com/windows/hardware/gg463179.aspx). *OS_Desc_CompatID.doc* bietet eine Erklärung des Deskriptors des Formats und der ein Beispiel für mehrere Schnittstellen im Deskriptor einschließlich. MTP kompatiblen und nicht kompatible IDs sind auch auf derselben Seite verfügbar und werden in eines der Beispiele verwendet.

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>Zum Einschließen von MTP in Ihre benutzerdefinierte FFU

1. Hinzufügen **IOT_MTP** Funktions-ID an den OEM-Eingabedatei. Dies entspricht der folgenden Schritte von der "[**Bereitstellen des Geräts mit der erforderlichen Pakete**](#provisioning-the-device-with-required-packages)" im Abschnitt.
2. Stellen Sie sicher, dass Änderungen an der gleichen Registrierung anwenden, wie in der "[**erstellen eine neue USBFN-Konfiguration mit der MTP-Schnittstelle**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" im Abschnitt. Führen Sie [diese Anweisungen](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) erfahren, wie ein FFU registrierungsänderungen zuweisen.
3. Erstellen Sie die Image\FFU. Lesen [in diesem Artikel](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) Anweisungen.

> [!WARNING]
> Ändern der Standardkonfiguration werden nicht durch die Anpassung der FFU unternommen. Systemdefinierte Einträge können von einem Systemupdate aktualisiert oder geändert werden, und ggf. vorhandene benutzerdefinierten Einstellungen gehen verloren.

## <a name="how-to-setup-the-mtp-sd-card-filter"></a>Zum Einrichten der Filter der MTP SD-Karte

Standardmäßig werden MTP den Inhalt einer SD-Karte Auflisten aller Wenn es auf dem Gerät vorhanden ist. Es ist jedoch möglich, diese Enumeration auf einen bestimmten Unterordner zu beschränken. Zu diesem Zweck müssen Sie einen Registrierungswert hinzufügen `MTPSDFolderFilter` unter dem Registrierungsschlüssel `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`.
Der Wert ist vom Typ `REG_SZ` als kontrollsammlung und enthält einen relativen Pfad zu dem Ordner MTP aufgelistet werden sollen. Der Ordner wird automatisch erstellt zu erhalten, wenn es nicht bereits vorhanden ist.

Beispiel-Pfade:
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory.

> [!WARNING]
> Verwenden Sie keinen absoluten Pfad, der mit dem Laufwerksbuchstaben wie `C:\Some\Folder\Path` – Dies kann verhindern, dass die SD-Karte aufgezählt werden.

Finden Sie unter [diesen Link](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) ausführliche Informationen zum Anpassen des Abbilds mit spezifischen Registrierungseinträgen.
