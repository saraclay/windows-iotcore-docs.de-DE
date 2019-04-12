---
title: Konfigurieren Sie das Kopfzeilen Gerät mit dem Windows 10 IoT Core auf dem Bildschirm Tastatur
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Erfahren Sie mehr über die neue auf dem Bildschirm Tastatur- und wie Sie es in Windows 10 IoT Core, Version 1809 konfigurieren.
keywords: Windows 10 IoT Core, Touch, Tastatur, Bildschirmtastatur, auf dem Bildschirm, auf dem Bildschirm, Eingabe, Sip-Ime, Spitzen, Diktat, Stimme und Sprache
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512346"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>Bildschirmtastatur für Multi-Geräte

In Windows 10 IoT Core, Version 1809, der Tastaturkomponente wurde auf dem Bildschirm geändert, erheblich, und zwar zum besseren! IoT Core verwendet jetzt die gleichen Komponenten des Touch-Tastatur, als die desktop Edition von Windows.

## <a name="new-features"></a>Neue Funktionen
Die neue Implementierung der Tastatur bietet die folgenden Vorteile für Ihre Multi-Device-Entwicklung:

* [Der gesamte Satz von Windows-Sprache Tastaturlayouts](#windows-keyboard-language-layouts)
* [Unterstützung für die Eingabe von Bereichen (z. B. e-Mail-Adresse, numerische PIN, suchen (Feld), usw.)](#support-for-input-scopes)
* [Eingabemethoden-Editor (IME)](#input-method-editor-ime)
* [Nicht-verdeckt-Felder](#non-obscured-text-input-fields)
* [Diktatmodus](#dictation-mode)
* [Eine Auswahl von Voreinstellungen für die Benutzeroberfläche](#user-interface-configuration)

## <a name="feature-packages"></a>Feature-Pakete

Für Images zum Erstellen von Prototypen (Entwicklung) der Tastatur-Feature ist auf dem Bildschirm bereits enthalten, aber Sie müssen zum Aktivieren von Einstellungen für Geräte in der [Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features).

Für gewerbliche Nutzung, die folgende optionale Funktion Pakete hinzufügen, werden die Bildschirmtastatur zu Ihrem Image:
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> Weitere Informationen zu IoT Core-Features, finden Sie unter [IoT Core-Featureliste](/windows-hardware/manufacture/iot/iot-core-feature-list) und [IoT Core Produktionskalender Handbuch](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

## <a name="windows-keyboard-language-layouts"></a>Windows-Sprache Tastaturlayouts

In dieser Version unterstützte Sprache Layouts wurde erweitert den vollständigen Satz von in der Windows-desktop-Edition verfügbar sind. Um Ihre Benutzer für die Auswahl zwischen den Layouts für verschiedene Sprachen zu ermöglichen, müssten Sie in der Regel die Benutzeroberfläche zur Auswahl im Bereich "Einstellungen" Ihrer Anwendung einfügen. Die folgende API wird bereitgestellt, um die Anwendung Festlegen der Sprache, die auf dem Bildschirm für die Tastatur verwendet werden:

[Windows.Globalization.Language.TrySetInputMethodLanguageTag](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

Ein Beispiel für diese API finden Sie in der [IoTCoreDefaultApp beispielanwendung](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)in die [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) Datei.

## <a name="support-for-input-scopes"></a>Unterstützung für die Eingabe-Bereiche

In früheren Versionen war nur der Eingabebereich EmailSmtpAddress verfügbar. In dieser Version sind der vollständige Satz von Eingabedaten Bereiche verfügbar. Im folgende Thema wird erläutert, Eingabe Bereiche und diese in Ihren Anwendungen verwenden:

[Verwenden des Eingabeumfangs zum Ändern der Bildschirmtastatur](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>Eingabemethoden-Editor (IME)

Dieses Release bietet einen Eingabemethoden-Editor, der für jede Sprache erforderlich, die weitere Graphemes ist als Schlüssel vorhanden, auf der Tastatur, z. B. Chinesisch, Japanisch und Koreanisch sind.

## <a name="non-obscured-text-input-fields"></a>Nicht-verdeckt-Felder

In früheren Versionen kann die Bildschirmtastatur fokussierte Textfeld verdecken, damit, dass der Benutzer nicht sehen wurde, was sie eingeben. Diese Version behebt dieses Problem durch das Textfeld automatisch in der Ansicht zu scrollen, damit, dass es nicht mehr von der Bildschirmtastatur verdeckt wird.

## <a name="dictation-mode"></a>Diktatmodus

Nastavena die Eingabesprache für die Sprache des Betriebssystems, die der Standardwert ist, ist die Eingabe Voice-Erkennung-Funktion verfügbar.
Um die Schaltfläche mit den Diktatmodus der Tastatur anzuzeigen, finden Sie im folgenden Abschnitt auf [Benutzeroberfläche Konfiguration](#user-interface-configuration).

## <a name="user-interface-configuration"></a>Benutzeroberflächenkonfiguration

Die auf dem Bildschirm Tastatur bietet mehrere konfigurierbare Optionen für die Benutzeroberfläche. Diese werden über die Registrierung konfiguriert.
Während der Entwicklung können Sie [PowerShell](/windows/iot-core/connect-your-device/powershell) oder [Secure Shell (SSH)](/windows/iot-core/connect-your-device/ssh). Für ein OEM-Image erstellen, ist der bevorzugte Mechanismus für die Registrierungswerte dem `OEMInput.xml` Datei hier erläutert:

[Anpassungen für Common Language Runtime](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> Die meisten der hier dokumentierten registrierungseinstellungen werden wirksam, während die Tastatur auf dem Bildschirm wird angezeigt.
> Dadurch können Sie während der Entwicklung leicht unterschiedliche Combinatations Einstellungen Werte sofort sehen die Änderungen in Echtzeit zu testen. Wenn eine Einstellung nicht sofort wirksam wird, müssen Sie das Gerät neu starten, damit die Änderungen an der Tastatur-Benutzeroberfläche finden Sie unter.

### <a name="keyboard-height"></a>Höhe der Tastatur

Standardmäßig wird die Bildschirmtastatur die niedrigere 45 % des Bildschirms Höhe verwendet. Dies möglicherweise zu groß oder klein ist, auf Ihrem Gerät abhängig von seiner Größe und Auflösung angezeigt. Sie können die Höhe auf maximal zwei Drittel Anpassen der Höhe des Bildschirms. Jeder Wert nicht im Bereich wird in den Bereich geklammert. Da diese als Gleitkommazahl angegeben ist-Wert für die Genauigkeit von Pixel auf Serverebene ermöglicht. Wenden Sie einfach die folgende Formel zur Berechnung des Prozentsatzes an:

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

Beispielsweise würden Sie zum Ändern der Höhe und 56.783 %, den folgenden Registrierungswert festlegen:
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
oder über PowerShell:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> Der Typ muss eine Zeichenfolge sein (`REG_SZ`), sodass der Bruchzahlen mit dargestellt werden können.
> ein Dezimaltrennzeichen. Verwenden die DWord (`REG_DWORD`) wird _nicht_ funktionieren, auch für die Prozentsätze der ganze Zahl.

### <a name="additional-preferences"></a>Zusätzliche Einstellungen

Die verbleibenden Einstellungen sind Zeichenfolgenwerte in den Voreinstellungen Unterschlüssel:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| Registrierungswert               | Standardwert      | Beschreibung                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | "0"                | "0" ermöglicht das audio klicken Sie auf Feedback; "1" wird deaktiviert.                                          |
| Dictation_Disabled           | "1"                | "0" wird die Schaltfläche mit den Diktatmodus (Spracherkennung) angezeigt. "1" blendet ihn aus.<br/> (siehe Hinweis unten)             |
| KeyboardModeEnabled_full     | "0"                | "0" deaktiviert die Tastatur voller Größe Modus; "1" wird aktiviert.                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0" deaktiviert den Tastaturmodus für die schmale; "1" wird aktiviert.                                              |
| KeyboardModeEnabled_wide     | "1"                | "0" deaktiviert den Tastaturmodus für große; "1" wird aktiviert.                                                |
| ModeOrder                    | "wide; eingrenzen; vollständiger" | Die Reihenfolge (von links nach rechts) in der die Modi im Dropdown-Menü Modus aufgeführt sind, wenn aktiviert |
| SettingsMenuKey_Collapsed    | "0"                | Blendet die Modus Dropdown-Menü aus. Legen Sie diese Einstellung auf "1", wenn nur ein Modus aktiviert ist.                         |
| Paste_Disabled               | "0"                | "0" zeigt die Schaltfläche "Einfügen"; "1" blendet ihn aus.<br/> Änderung wird nach Neustart wirksam.                    |
| CloseButton_Disabled         | "0"                | "0" wird die Schaltfläche "Schließen" angezeigt. "1" Blendet die Schaltfläche "Schließen"<br/> Änderung wird nach Neustart wirksam.       |
| EmojiKeyEnabled              | "0"                | "0" Blendet den Emoji Schlüssel aus. "1" wird angezeigt, damit der Benutzer Emoji Zeichen eingeben.                 |

> [!NOTE]
> Diktatmodus erfordert ein Sprachpaket für die ausgewählte Eingabesprache sowie eines Audioeingabegeräts installiert werden. Wenn eine entsprechende Pakete für die Sprache nicht installiert ist, wird die Schaltfläche mit den Diktatmodus nicht angezeigt.
> 
> Alle Images enthalten die En-US-Speech-Sprache. Andere Sprache-Pakete werden als optionalen Funktionen installiert.
> Weitere Informationen zu IoT-Features, finden Sie unter [IoT Core-Featureliste](/windows-hardware/manufacture/iot/iot-core-feature-list) und [IoT Core Produktionskalender Handbuch](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

Als Beispiel, die nur `wide` Tastaturmodus in PowerShell können Sie die folgenden Schritte:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
mkdir Preferences
cd Preferences
Set-ItemProperty . -Name KeyboardModeEnabled_full -Value "0"      # Optional, since the default is "0"
Set-ItemProperty . -Name KeyboardModeEnabled_narrow -Value "0"
Set-ItemProperty . -Name KeyboardModeEnabled_wide -Value "1"      # Optional, since the default is "1"
Set-ItemProperty . -Name SettingsMenuKey_Collapsed -Value "1"
```
