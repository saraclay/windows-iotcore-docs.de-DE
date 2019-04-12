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
# <a name="language-support"></a><span data-ttu-id="a51a2-104">Sprachunterstützung</span><span class="sxs-lookup"><span data-stu-id="a51a2-104">Language Support</span></span>

<span data-ttu-id="a51a2-105">Sprachunterstützung kann auf zwei Ebenen, Anwendungs- und BS-Ebene, abhängig von der Sprachressourcen zur Verfügung gestellt, auf das Bild, aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="a51a2-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="a51a2-106">Sprachen in UWP-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="a51a2-106">Languages in UWP Applications</span></span>
<span data-ttu-id="a51a2-107">UWP-Anwendung-Sprachen sind nicht begrenzt, für die Sprachen, die im Betriebssystem enthalten.</span><span class="sxs-lookup"><span data-stu-id="a51a2-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="a51a2-108">Ein IoT-Geräte, die keine Benutzeroberfläche der Shell ausgelöst oder Nutzung von Sprachressourcen kann in der Tat eine geräteerfahrung in verschiedenen Sprachen über die UWP-Anwendungen bereitstellen, obwohl das zugrunde liegende Windows 10 IoT Core-Betriebssystem einfach im standardmäßigen Modus für En-US erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="a51a2-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="a51a2-109">UWP-Anwendungen müssen die Ressourcen für die Sprachen angeben, die die unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="a51a2-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="a51a2-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs kann verwendet werden, um das Language-bezogene Einstellungen angeben.</span><span class="sxs-lookup"><span data-stu-id="a51a2-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="a51a2-111">Finden Sie unter den nachfolgend aufgeführten Beispielanwendungen:</span><span class="sxs-lookup"><span data-stu-id="a51a2-111">See the below sample applications:</span></span>

* [<span data-ttu-id="a51a2-112">IoTDefaultApp-Beispiel</span><span class="sxs-lookup"><span data-stu-id="a51a2-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="a51a2-113">ApplicationResources-Beispiel</span><span class="sxs-lookup"><span data-stu-id="a51a2-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="a51a2-114">Sprachen im Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="a51a2-114">Languages in OS</span></span>

<span data-ttu-id="a51a2-115">Windows 10-IoTCore Kits enthalten jetzt die Sprachressourcen für die folgenden Sprachen:</span><span class="sxs-lookup"><span data-stu-id="a51a2-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="a51a2-116">Sprache</span><span class="sxs-lookup"><span data-stu-id="a51a2-116">Language</span></span>  | <span data-ttu-id="a51a2-117">Code</span><span class="sxs-lookup"><span data-stu-id="a51a2-117">Code</span></span> | <span data-ttu-id="a51a2-118">Region</span><span class="sxs-lookup"><span data-stu-id="a51a2-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="a51a2-119">Englisch (USA)</span><span class="sxs-lookup"><span data-stu-id="a51a2-119">English (United States)</span></span> | <span data-ttu-id="a51a2-120">en-US</span><span class="sxs-lookup"><span data-stu-id="a51a2-120">en-US</span></span> | <span data-ttu-id="a51a2-121">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="a51a2-121">North America</span></span> | 
> | <span data-ttu-id="a51a2-122">Englisch (Großbritannien)</span><span class="sxs-lookup"><span data-stu-id="a51a2-122">English (UK)</span></span> | <span data-ttu-id="a51a2-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="a51a2-123">en-GB</span></span> | <span data-ttu-id="a51a2-124">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-124">Europe</span></span> |
> | <span data-ttu-id="a51a2-125">Französisch (Frankreich)</span><span class="sxs-lookup"><span data-stu-id="a51a2-125">French (France)</span></span> | <span data-ttu-id="a51a2-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="a51a2-126">fr-FR</span></span> | <span data-ttu-id="a51a2-127">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-127">Europe</span></span> |
> | <span data-ttu-id="a51a2-128">Französisch (Kanada)</span><span class="sxs-lookup"><span data-stu-id="a51a2-128">French (Canada)</span></span> | <span data-ttu-id="a51a2-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="a51a2-129">fr-CA</span></span> | <span data-ttu-id="a51a2-130">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="a51a2-130">North America</span></span> |
> | <span data-ttu-id="a51a2-131">Spanisch (Spanien)</span><span class="sxs-lookup"><span data-stu-id="a51a2-131">Spanish (Spain)</span></span> | <span data-ttu-id="a51a2-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="a51a2-132">es-ES</span></span> | <span data-ttu-id="a51a2-133">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-133">Europe</span></span> |
> | <span data-ttu-id="a51a2-134">Spanisch (Mexiko)</span><span class="sxs-lookup"><span data-stu-id="a51a2-134">Spanish (Mexico)</span></span> | <span data-ttu-id="a51a2-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="a51a2-135">es-MX</span></span> | <span data-ttu-id="a51a2-136">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="a51a2-136">North America</span></span> |
> | <span data-ttu-id="a51a2-137">Chinesisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-137">Chinese</span></span> | <span data-ttu-id="a51a2-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="a51a2-138">zh-CN</span></span> | <span data-ttu-id="a51a2-139">Asien</span><span class="sxs-lookup"><span data-stu-id="a51a2-139">Asia</span></span> | 
> | <span data-ttu-id="a51a2-140">Arabisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-140">Arabic</span></span> | <span data-ttu-id="a51a2-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="a51a2-141">ar-SA</span></span> | <span data-ttu-id="a51a2-142">Asien</span><span class="sxs-lookup"><span data-stu-id="a51a2-142">Asia</span></span> |
> | <span data-ttu-id="a51a2-143">Deutsch</span><span class="sxs-lookup"><span data-stu-id="a51a2-143">German</span></span> | <span data-ttu-id="a51a2-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="a51a2-144">de-DE</span></span> | <span data-ttu-id="a51a2-145">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-145">Europe</span></span> |
> | <span data-ttu-id="a51a2-146">Italienisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-146">Italian</span></span> | <span data-ttu-id="a51a2-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="a51a2-147">it-IT</span></span> | <span data-ttu-id="a51a2-148">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-148">Europe</span></span> | 
> | <span data-ttu-id="a51a2-149">Japanisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-149">Japanese</span></span> | <span data-ttu-id="a51a2-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="a51a2-150">ja-JP</span></span> | <span data-ttu-id="a51a2-151">Asien</span><span class="sxs-lookup"><span data-stu-id="a51a2-151">Asia</span></span> |
> | <span data-ttu-id="a51a2-152">Koreanisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-152">Korean</span></span> | <span data-ttu-id="a51a2-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="a51a2-153">ko-KR</span></span> | <span data-ttu-id="a51a2-154">Asien</span><span class="sxs-lookup"><span data-stu-id="a51a2-154">Asia</span></span> |
> | <span data-ttu-id="a51a2-155">Niederländisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-155">Dutch</span></span> | <span data-ttu-id="a51a2-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="a51a2-156">nl-NL</span></span> | <span data-ttu-id="a51a2-157">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-157">Europe</span></span> |
> | <span data-ttu-id="a51a2-158">Polnisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-158">Polish</span></span> | <span data-ttu-id="a51a2-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="a51a2-159">pl-PL</span></span> | <span data-ttu-id="a51a2-160">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-160">Europe</span></span> | 
> | <span data-ttu-id="a51a2-161">Rumänisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-161">Romanian</span></span> | <span data-ttu-id="a51a2-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="a51a2-162">ro-RO</span></span> | <span data-ttu-id="a51a2-163">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-163">Europe</span></span> |
> | <span data-ttu-id="a51a2-164">Russisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-164">Russian</span></span> | <span data-ttu-id="a51a2-165">ro-RU</span><span class="sxs-lookup"><span data-stu-id="a51a2-165">ro-RU</span></span> | <span data-ttu-id="a51a2-166">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-166">Europe</span></span> |
> | <span data-ttu-id="a51a2-167">Griechisch</span><span class="sxs-lookup"><span data-stu-id="a51a2-167">Greek</span></span> | <span data-ttu-id="a51a2-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="a51a2-168">el-GR</span></span> | <span data-ttu-id="a51a2-169">Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-169">Europe</span></span> |
> | <span data-ttu-id="a51a2-170">Portugiesisch (Brasilien)</span><span class="sxs-lookup"><span data-stu-id="a51a2-170">Portugese (Brazil)</span></span> | <span data-ttu-id="a51a2-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="a51a2-171">pt-BR</span></span> | <span data-ttu-id="a51a2-172">Südamerika/Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-172">South America/Europe</span></span> |
> | <span data-ttu-id="a51a2-173">Portuese (Portugal)</span><span class="sxs-lookup"><span data-stu-id="a51a2-173">Portuese (Portugal)</span></span> | <span data-ttu-id="a51a2-174">pt-PR</span><span class="sxs-lookup"><span data-stu-id="a51a2-174">pt-PR</span></span> | <span data-ttu-id="a51a2-175">Südamerika/Europa</span><span class="sxs-lookup"><span data-stu-id="a51a2-175">South America/Europe</span></span> |

<span data-ttu-id="a51a2-176">Diese Sprachressourcen enthält UI-Zeichenfolgen, Sprache und stimmen (Sprachsynthese).</span><span class="sxs-lookup"><span data-stu-id="a51a2-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="a51a2-177">Windows IoT-Images mit einem oder mehreren dieser Ressourcen erstellt werden können und muss angegeben werden, während der Image-Zeit und kann nicht später geändert werden.</span><span class="sxs-lookup"><span data-stu-id="a51a2-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="a51a2-178">Beachten Sie, dass die Sprache der Benutzeroberfläche verknüpft Ressourcen sind unabhängig als Sprache und voice-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="a51a2-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="a51a2-179">Angeben von BENUTZEROBERFLÄCHEN-und Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="a51a2-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="a51a2-180">Die OEM-Abhängige Eingabe-XML-Datei werden die erforderliche Benutzeroberfläche und die Sprachen für Sprachausgabe angegeben, wie unten dargestellt</span><span class="sxs-lookup"><span data-stu-id="a51a2-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

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


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="a51a2-181">Angeben der Sprache Data-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a51a2-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="a51a2-182">Die OEM-Abhängige Eingabe-XML-Datei werden die Datenressourcen erforderliche Sprache angegeben, wie unten dargestellt,</span><span class="sxs-lookup"><span data-stu-id="a51a2-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

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
> <span data-ttu-id="a51a2-183">Standardmäßig ist die En-US-Sprachdaten in der Abbildung enthalten.</span><span class="sxs-lookup"><span data-stu-id="a51a2-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="a51a2-184">Proben</span><span class="sxs-lookup"><span data-stu-id="a51a2-184">Samples</span></span>
* <span data-ttu-id="a51a2-185">Finden Sie unter [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) für mehrere Sprachen zu unterstützen</span><span class="sxs-lookup"><span data-stu-id="a51a2-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="a51a2-186">Finden Sie unter [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) für "fr-FR" En-US als Fallbacksprache-Sprache.</span><span class="sxs-lookup"><span data-stu-id="a51a2-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="a51a2-187">Beachten Sie, dass, wenn der Start-Sprache der Benutzeroberfläche geändert wird, die `administrator` Kontoname wird auch in der Start-UI-Sprache übersetzt.</span><span class="sxs-lookup"><span data-stu-id="a51a2-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="a51a2-188">In "fr-FR" ist es daher `administrateur`.</span><span class="sxs-lookup"><span data-stu-id="a51a2-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="a51a2-189">Finden Sie unter [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="a51a2-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="a51a2-190">Ändern von benutzereinstellungen (Sprache, Region, Spracherkennung und Sprache)</span><span class="sxs-lookup"><span data-stu-id="a51a2-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="a51a2-191">UWP-Anwendung kann WinRT-APIs verwenden, um festzulegen, die Region, Liste der bevorzugten UI-Sprache, Sprache und Stimme an, die standardmäßig verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a51a2-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="a51a2-192">Einmal bevorzugte UI Sprache Liste festgelegt, wird UWP-Anwendung versucht, die entsprechenden Ressourcen geladen werden (es sei denn, die Anwendung programmgesteuert, verhindert).</span><span class="sxs-lookup"><span data-stu-id="a51a2-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="a51a2-193">Wenn die Anwendung nicht über die entsprechenden Ressourcen verfügt, werden dann Fallbackressourcen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="a51a2-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="a51a2-194">Auf ähnliche Weise Wenn die Betriebssystemressourcen für die bevorzugten Sprachen Teil des Windows-IoT-Images nicht sind, wird Windows IoT die fallback-tastenzuordnungen wahrscheinlich Englisch (En-US) verwendet.</span><span class="sxs-lookup"><span data-stu-id="a51a2-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="a51a2-195">Legen Sie die Region mit `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a51a2-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a51a2-196">Mithilfe von Set UI Sprache `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a51a2-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a51a2-197">Mithilfe von Set Spracherkennung Sprache `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="a51a2-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="a51a2-198">Legen Sie mithilfe von Voice `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="a51a2-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="a51a2-199">Für das ordnungsgemäße funktionieren, Cortana ist erforderlich, die Region, die Sprache der Benutzeroberfläche und die Sprache-Sprache, z. B. konsistent sind, werden: Region FR, Benutzeroberfläche und Spracherkennung Sprachen "fr-FR" oder die Region ES, Benutzeroberflächen und Spracherkennung Sprachen es-ES.</span><span class="sxs-lookup"><span data-stu-id="a51a2-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="a51a2-200">Cortana verwendet eine eigene Stimme, UWP-Anwendung nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="a51a2-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="a51a2-201">IoTSettings.exe</span><span class="sxs-lookup"><span data-stu-id="a51a2-201">IoTSettings.exe</span></span>

<span data-ttu-id="a51a2-202">Weitere Informationen zum Ändern der Einstellungen für die Region und Benutzer- oder Sprache, zum Erstellen von Produkten der Cortana aktiviert, und Lesen Sie unsere [über die Befehlszeile "utils"](../manage-your-device/CommandLineUtils.md) Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="a51a2-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
