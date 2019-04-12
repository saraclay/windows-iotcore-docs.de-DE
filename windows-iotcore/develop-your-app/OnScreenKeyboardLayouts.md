---
title: Geben Sie auf dem Bildschirm verfügbar Tastaturlayouts Sprache
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: Informationen zum Angeben der Sprache Bildschirmtastatur Layouts für die Benutzer Ihre Windows-IoT-Geräte verfügbar sind.
keywords: Windows 10 IoT Core, kommerziell, Bildschirmtastatur Tastaturlayouts für Sprache auf dem Bildschirm
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513026"
---
# <a name="on-screen-keyboard-language-layouts"></a>Sprache auf dem Bildschirm Tastaturlayouts

> [!IMPORTANT]
> Ab Windows 10 IoT Core, Version 1809, ist in diesem Artikel nicht mehr gültig. Informieren Sie sich die [Bildschirmtastatur für Multi-Geräte](./OnScreenKeyboard.md) Seite für die aktuelle Dokumentation.

Die auf dem Bildschirm Tastatur (Bildschirmtastatur) in Windows 10 IoT Core, Version 1703 und 1709 1803, Layouts für die folgenden Sprachen unterstützt:

| Sprach-Tag  | Beschreibung             | Layout-Codes |
| :------------ | :---------------------- | -----------:|
| en-US         | Englisch (USA) |    00000409 |
| en-AU         | Englisch (Australien)     |    00000C09 |
| en-CA         | Englisch (Kanada)        |    00001009 |
| en-GB         | Englisch (Großbritannien) |    00000809 |
| es-ES         | Spanisch (Spanien)         |    0000040A |
| es-MX         | Spanisch (Mexiko)        |    0000080A |
| de-DE         | Deutsch                  |    00000407 |
| fr-CA         | Französisch (Kanada)         |    00000C0C |
| fr-FR         | Französisch (Frankreich)         |    0000040C |
| it-IT         | Italienisch                 |    00000410 |
| pt-BR         | Portugiesisch (Brasilien)     |    00000416 |

Durch Gedrückthalten der Bildschirmtastatur auf die Schaltfläche "& 123", der Benutzer kann auswählen, welches Layout verwendet werden soll:

![Alle Sprachen](../media/OnScreenKeyboard/AllLanguages.png)
 
Als ein OEM können Sie jedoch Einschränken der Layoutoptionen, die dem Benutzer angezeigt werden. Um die Layouts, um dem Benutzer anzuzeigen, zu beschränken, verweisen Sie zuerst die Anleitung aus dem [Tastaturlayout Doucmentation auf TechNet](https://technet.microsoft.com/library/cc978687.aspx).
 
Für ein konkretes Beispiel, wenn Sie zulassen, nur Layouts für Nordamerika-Sprache möchten (En-US "," En-CA "," es-MX, fr-CA), können Sie Ihr Skript OEMCustomization.cmd Folgendes hinzufügen:

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

SetKeyboardLanguages.cmd ist, in dem ein Skript im selben Verzeichnis enthält:
 
```console
@echo off

set getDefaultAccountSID="wmic.exe useraccount where name='DefaultAccount' get sid"

for /F "tokens=2 usebackq delims== " %%s in (`%getDefaultAccountSID%`) do (
    set registryKey="HKEY_USERS\%%~s\Keyboard Layout\Preload"
    goto :setRegistry
  )
)
echo Unable to determine SID for DefaultAccount
goto :eof

:setRegistry
  echo on
  REG ADD %registryKey% /v "1" /d "00000409" /f
  REG ADD %registryKey% /v "2" /d "00001009" /f
  REG ADD %registryKey% /v "3" /d "0000080A" /f
  REG ADD %registryKey% /v "4" /d "00000C0C" /f
  @echo off
goto :eof
```

Die resultierende Auswirkungen des obigen Befehls Skripts werden:

![Nordamerika Sprachen](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>Einige Punkte zu beachten:
*  Die Namen der Werte geben Sie eine decimal-Sequenz an.
*  Die Werte sind Werte vom Typ String (REG_SZ).
*  Der oben genannten Skripttext kann natürlich direkt in das Skript OEMCustomization.cmd hinzugefügt werden.
*  **Nicht** den Registrierungsschlüssel "Vorab laden" gelöscht werden, da es über Berechtigungen, die speziell auf Zulassen festgelegt verfügt die Anwendung, um die Werte der Bildschirmtastatur.
*  Eine Voraussetzung für diese Anweisungen, um die gilt, ist, dass Ihr Image die folgenden Features * enthalten muss:
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

Weitere Informationen zu IoT-Features, finden Sie unter [IoT Core-Featureliste](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list).
