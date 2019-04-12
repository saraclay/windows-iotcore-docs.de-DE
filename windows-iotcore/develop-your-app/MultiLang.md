---
title: Windows 10 IoT Core-sprachunterstützung
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/17
ms.topic: article
description: Informationen Sie zu Unterstützung mehrerer Sprachen in UWP-Anwendungen und Betriebssystem unter IoT Core.
keywords: Windows Iot, Sprachen, app-Typen, UWP, Betriebssystem
ms.openlocfilehash: 211ed2ee8350d8c92d6f959f8d9e7b5d6f567af7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512386"
---
# <a name="language-support"></a>Sprachunterstützung

Sprachunterstützung kann auf zwei Ebenen, Anwendungs- und BS-Ebene, abhängig von der Sprachressourcen zur Verfügung gestellt, auf das Bild, aktiviert werden.

## <a name="languages-in-uwp-applications"></a>Sprachen in UWP-Anwendungen
UWP-Anwendung-Sprachen sind nicht begrenzt, für die Sprachen, die im Betriebssystem enthalten.  Ein IoT-Geräte, die keine Benutzeroberfläche der Shell ausgelöst oder Nutzung von Sprachressourcen kann in der Tat eine geräteerfahrung in verschiedenen Sprachen über die UWP-Anwendungen bereitstellen, obwohl das zugrunde liegende Windows 10 IoT Core-Betriebssystem einfach im standardmäßigen Modus für En-US erstellt wird. 

UWP-Anwendungen müssen die Ressourcen für die Sprachen angeben, die die unterstützt werden. [Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs kann verwendet werden, um das Language-bezogene Einstellungen angeben.

Finden Sie unter den nachfolgend aufgeführten Beispielanwendungen:

* [IoTDefaultApp-Beispiel](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [ApplicationResources-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>Sprachen im Betriebssystem

Windows 10-IoTCore Kits enthalten jetzt die Sprachressourcen für die folgenden Sprachen:

> | Sprache  | Code | Region |
> |-------------|-----|-----|
> | Englisch (USA) | en-US | Nordamerika | 
> | Englisch (Großbritannien) | en-GB | Europa |
> | Französisch (Frankreich) | fr-FR | Europa |
> | Französisch (Kanada) | fr-CA | Nordamerika |
> | Spanisch (Spanien) | es-ES | Europa |
> | Spanisch (Mexiko) | es-MX | Nordamerika |
> | Chinesisch | zh-CN | Asien | 
> | Arabisch | ar-SA | Asien |
> | Deutsch | de-DE | Europa |
> | Italienisch | it-IT | Europa | 
> | Japanisch | ja-JP | Asien |
> | Koreanisch | ko-KR | Asien |
> | Niederländisch | nl-NL | Europa |
> | Polnisch | pl-PL | Europa | 
> | Rumänisch | ro-RO | Europa |
> | Russisch | ro-RU | Europa |
> | Griechisch | el-GR | Europa |
> | Portugiesisch (Brasilien) | pt-BR | Südamerika/Europa |
> | Portuese (Portugal) | pt-PR | Südamerika/Europa |

Diese Sprachressourcen enthält UI-Zeichenfolgen, Sprache und stimmen (Sprachsynthese). Windows IoT-Images mit einem oder mehreren dieser Ressourcen erstellt werden können und muss angegeben werden, während der Image-Zeit und kann nicht später geändert werden. Beachten Sie, dass die Sprache der Benutzeroberfläche verknüpft Ressourcen sind unabhängig als Sprache und voice-Ressourcen.

### <a name="specifying-ui-and-speech-resources"></a>Angeben von BENUTZEROBERFLÄCHEN-und Spracherkennung 
Die OEM-Abhängige Eingabe-XML-Datei werden die erforderliche Benutzeroberfläche und die Sprachen für Sprachausgabe angegeben, wie unten dargestellt

``` xml
  <SupportedLanguages>
    <UserInterface>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </UserInterface>
    <Keyboard>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Keyboard>
    <Speech>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Speech>
  </SupportedLanguages>
  <BootUILanguage>en-us</BootUILanguage>
  <BootLocale>en-us</BootLocale>
```


### <a name="specifying-speech-data-resources"></a>Angeben der Sprache Data-Ressourcen
Die OEM-Abhängige Eingabe-XML-Datei werden die Datenressourcen erforderliche Sprache angegeben, wie unten dargestellt,

``` xml
    <Microsoft>
       ...
      <Feature>IOT_SPEECHDATA_EN_CA</Feature>
      <Feature>IOT_SPEECHDATA_ES_MX</Feature> 
      <Feature>IOT_SPEECHDATA_FR_CA</Feature> 
      <Feature>IOT_SPEECHDATA_EN_GB</Feature>
      <Feature>IOT_SPEECHDATA_ES_ES</Feature>  
      <Feature>IOT_SPEECHDATA_FR_FR</Feature> 
    </Microsoft>
```

> [!NOTE]
> Standardmäßig ist die En-US-Sprachdaten in der Abbildung enthalten.

### <a name="samples"></a>Proben
* Finden Sie unter [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) für mehrere Sprachen zu unterstützen
* Finden Sie unter [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) für "fr-FR" En-US als Fallbacksprache-Sprache.
    * Beachten Sie, dass, wenn der Start-Sprache der Benutzeroberfläche geändert wird, die `administrator` Kontoname wird auch in der Start-UI-Sprache übersetzt. In "fr-FR" ist es daher `administrateur`. Finden Sie unter [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>Ändern von benutzereinstellungen (Sprache, Region, Spracherkennung und Sprache)

UWP-Anwendung kann WinRT-APIs verwenden, um festzulegen, die Region, Liste der bevorzugten UI-Sprache, Sprache und Stimme an, die standardmäßig verwendet werden soll. Einmal bevorzugte UI Sprache Liste festgelegt, wird UWP-Anwendung versucht, die entsprechenden Ressourcen geladen werden (es sei denn, die Anwendung programmgesteuert, verhindert).
 
Wenn die Anwendung nicht über die entsprechenden Ressourcen verfügt, werden dann Fallbackressourcen geladen werden. Auf ähnliche Weise Wenn die Betriebssystemressourcen für die bevorzugten Sprachen Teil des Windows-IoT-Images nicht sind, wird Windows IoT die fallback-tastenzuordnungen wahrscheinlich Englisch (En-US) verwendet.

* Legen Sie die Region mit `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* Mithilfe von Set UI Sprache `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* Mithilfe von Set Spracherkennung Sprache `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* Legen Sie mithilfe von Voice `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> Für das ordnungsgemäße funktionieren, Cortana ist erforderlich, die Region, die Sprache der Benutzeroberfläche und die Sprache-Sprache, z. B. konsistent sind, werden: Region FR, Benutzeroberfläche und Spracherkennung Sprachen "fr-FR" oder die Region ES, Benutzeroberflächen und Spracherkennung Sprachen es-ES. Cortana verwendet eine eigene Stimme, UWP-Anwendung nicht ändern.

## <a name="iotsettingsexe"></a>IoTSettings.exe

Weitere Informationen zum Ändern der Einstellungen für die Region und Benutzer- oder Sprache, zum Erstellen von Produkten der Cortana aktiviert, und Lesen Sie unsere [über die Befehlszeile "utils"](../manage-your-device/CommandLineUtils.md) Dokumentation.
