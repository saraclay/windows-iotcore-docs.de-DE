---
title: Übersicht über Windows 10 IoT
author: saraclay
ms.author: saclayt
ms.date: 01/30/2018
ms.topic: article
description: Erfahren Sie, was Windows 10 IoT und was Sie damit tun können.
keywords: Windows 10 IoT Enterprise, Windows 10 IoT Core, monitorlose, Spracherkennung, Features, binäre Edition, Editionen
ms.openlocfilehash: ecfb80049b4fe1dd5437faf6bce410f9fcb3c528
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512314"
---
# <a name="an-overview-of-windows-10-iot"></a>Eine Übersicht über Windows 10 IoT 

## <a name="what-is-windows-10-iot"></a>Was ist Windows 10 IoT?
Windows 10 IoT ist ein Mitglied der Windows 10-Familie, die Power von Enterprise-Klasse, Sicherheit und verwaltbarkeit für das Internet der Dinge bereitstellt.  Es nutzt Windows embedded Erfahrung "," Umgebung "und" Cloud-Konnektivität, dadurch können Unternehmen ihre Internet der Dinge mit sicheren Geräten zu erstellen, die schnell bereitgestellt, auf einfache Weise verwaltet und mit einer umfassenden cloudstrategie nahtlos verbunden werden können.  

## <a name="windows-10-iot-editions"></a>Windows 10 IoT Editions
Windows 10 IoT ist in zwei Editionen.  Windows 10 IoT Core ist das kleinste Element der Windows 10-Betriebssystem-Familie.  Obwohl nur eine einzelne app ausführen, wird es noch immer die Verwaltbarkeit und Sicherheit von Windows 10 erwartet.  Windows 10 IoT Enterprise ist hingegen eine Vollversion von Windows 10 mit speziellen Funktionen zum Erstellen von dedizierte Geräte, die auf einen bestimmten Satz von Anwendungen und Peripheriegeräte gesperrt. 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Unterschiede zwischen Windows 10 IoT Core und Windows 10 IoT Enterprise

Während Windows 10 IoT Core und Windows 10 IoT Enterprise in Namen ähnlich sind, unterscheiden sich was diese bieten, und was sie unterstützen. Im folgenden finden eine Liste der Funktionen, die Edition Unterschiede hervorhebt.

> |             | Windows 10 IoT Core  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | Benutzererfahrung | Eine UWP-app in den Vordergrund zu einem Zeitpunkt (finden Sie unter [IoT-Shell-Dokumentation](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoreshell) für die app BackStack-Behandlung) mit Unterstützung von Hintergrund-apps und Dienste. | Herkömmliche Windows-Shell mit erweiterten Lockdown-Funktionen |
> | Monitorlose unterstützt | Ja | Ja |
> | Unterstützte App-Architektur | Nur UWP UI | Vollständige Windows-Benutzeroberflächenautomatisierungs-Unterstützung (z. B. UWP, Windows Forms usw.) |
> | Cortana | [*Cortana-SDK*](https://developer.microsoft.com/en-us/cortana/devices) | Ja |
> | Domänenbeitritt | Nur AAD | AAD und herkömmliche |
> | Management | MDM | MDM |
> | Gerät-Sicherheitstechnologien | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [sicherer Start, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker), und der Geräteintegrität | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [sicherer Start, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) und Integritätsnachweis für Geräte |
> | Unterstützung für CPU-Architektur | X86 X64 und ARM | x86 und x64 |
> | Lizenzierung | Online-Lizenzierung Vereinbarung und eingebettete OEM-Verträge, lizenzgebührenfreie | Direkte und indirekte eingebettete OEM-Vereinbarungen |
> | Verwendungsszenarien | [Digitalen Beschilderung](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), Smart Building, IoT-Gateway, HMI, intelligente Home, tragbare Geräte | Industry-Tablets, POS, Kiosk-, [digitalen Beschilderung](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), Geldautomaten, medizinische Geräte, Herstellungsgeräte, Thin Clients |

Mindestanforderung Details, finden Sie auf [der Windows-Hardware-Website](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Unterschiede zwischen Windows 10 Desktop und Windows 10 IoT Core

### <a name="different-features-available-on-desktop-and-iot-core"></a>Verschiedene Funktionen, die auf dem Desktop und IoT Core verfügbar

* Inbox Cortana ist seit Version 1809 (17763) nicht mehr auf Windows 10 IoT Core verfügbar. Wenn Sie einer VCD-Gerät auf den Markt schnell bringen möchten, können Sie Cortana-Unterstützung integrieren, in dem Gerät mit der [Vorschau des Cortana Devices SDK](https://developer.microsoft.com/en-us/cortana/devices).
* Die [FileOpenPicker-API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) wird in Windows 10 IoT Core nicht unterstützt. Um den Zugriff auf lokale Laufwerke oder Wechselmedien können Sie dies in Ihrer eigenen Anwendung implementieren.
* Das Windows 10 IoT Core-Gerät wird gestartet, um die [Standard-app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) anstelle eines Desktops-PCs. Der Zweck dieser Anwendung ist nicht nur für die Sie mit einer benutzerfreundlichen Shell beim ersten Start zu interagieren, sondern auch verwendet werden Geben Sie die [Open Source-Code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) für diese Anwendung, damit Sie diese Funktionen verwenden können, um die Plug & play- Ihre eigenen benutzerdefinierten Anwendungen.

### <a name="differences-in-driver-supported-areas"></a>Unterschiede in Bereichen Driver-Unterstützung

* Windows 10 Desktop-Treiber verfügt über mehr als Windows 10 IoT Core unterstützt werden. Um den gleichen funktionieren Gerät(e) auf Windows 10 IoT Core wie auf Desktop, müssen Sie möglicherweise einen Treiber aus der Quelle für ein Windows 10 IoT Core-Gerät erstellen oder finden eine weitere Möglichkeit, vor allem für ARM-Architektur.
* Es ist kein Out-of-the-Box-Treiber für Libusb für Windows 10 IoT Core (ARM) – Sie müssen von der Quelle zum Ziel der ARM-Architektur zu erstellen.

### <a name="differences-in-available-registry-set"></a>Unterschiede in der Gruppe der verfügbare Registrierungsspeicher

* Auf Desktop besteht die Option auf "Automatisch ausblenden Bildlaufleisten in Windows", die auf off festgelegt sein können. Es wird durch den folgenden Registrierungseintrag gesteuert: 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* Es ist keine solche Registrierung auf Geräten mit Windows 10 IoT Core standardmäßig ein. Sie müssen ein Register "Dynamische Bildlaufleisten" nach Bedarf hinzufügen.
* Zum Ausblenden von Bildlaufleisten automatisch in eine UWP-Anwendung zu aktivieren, können Sie hinzufügen, die "DynamicScrollbars" registrieren, und legen Sie den Wert auf "1" wie folgt:

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* Der Registrierungsschlüssel muss aus dem Standard-Konto festgelegt werden. Wenn das ScrollViewer-Elements XAML-Einstellung auf "Visible" ist, erzwingt die nDer registrierungseinstellung 0 die Bildlaufleiste Regardlss, der angibt, ob angezeigt werden Inhalt vorhanden ist ausreichend, haben den Bildlauf in der Benutzeroberfläche angezeigt werden. Eine registrierungseinstellung 1 bleibt die Bildlaufleiste ausgeblendet, bis genügend Inhalt vorhanden ist.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* Schließlich ist die ScrollViewer XAMLs Einstellung "Auto" zeigt klicken Sie dann die registrierungseinstellung 0 die vollständige Bildlaufleiste nur wenn genügend Inhalte die Bildlaufleiste angezeigt. Wenn die Einstellung der Registrierung 1 ist, wird die Bildlaufleiste angezeigt, und klicken Sie dann bei genügend Inhalte oder ausgeblendet, wenn kein Inhalt vorhanden ist.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>Andere unterstützte Befehle

* Der Remove-AppxPackage des PowerShell-Befehl funktioniert auf tritt jedoch nicht auf Windows 10 IoT Core.
* Nicht alle Ordner auf Ihrem Gerät sind universelle Windows-Apps zugreifen können. Auf Windows 10 IoT Core können Sie die FolderPermissions-Tool verwenden, um einen Ordner in einer UWP-app zugänglich zu machen. Führen Sie z. B. FolderPermissions c:\test -e, um UWP-apps den Zugriff auf Ordner "c:\test" ein. Dies ist jedoch nicht auf den Desktop verfügbar.

Alle Unterschiede, die in diesem Beitrag wurde eventuell im Laufe der Zeit, da Windows 10 IoT Core ist nicht mehr aktualisiert.


## <a name="helpful-resources"></a>Hilfreiche Ressourcen
* [Windows 10 IoT Enterprise](windows-iot-enterprise.md)
* [Windows 10 IoT Core](windows-iot-core.md)
