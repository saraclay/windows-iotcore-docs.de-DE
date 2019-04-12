---
title: Eine Standard-App einrichten
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: Informationen Sie zum Einrichten einer Standard-app, die über die Windows Device Portal oder die Shell.
keywords: Windows Iot, Standard-app, PowerShell, iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513322"
---
# <a name="setup-a-default-app"></a><span data-ttu-id="f884d-104">Eine Standard-app einrichten</span><span class="sxs-lookup"><span data-stu-id="f884d-104">Setup a default app</span></span>
<span data-ttu-id="f884d-105">Hier erfahren Sie, wie Ihre Anwendung als standardanwendung festlegen.</span><span class="sxs-lookup"><span data-stu-id="f884d-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="f884d-106">Die standardanwendung ist diejenige, die beim Systemstart gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="f884d-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="f884d-107">Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="f884d-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="f884d-108">Laufzeitoptionen</span><span class="sxs-lookup"><span data-stu-id="f884d-108">Runtime options</span></span>

<span data-ttu-id="f884d-109">Während der Entwicklung / experimentelle Phasen, Sie können die Standard-app folgende Art und Weise ändern.</span><span class="sxs-lookup"><span data-stu-id="f884d-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="f884d-110">Mithilfe von Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="f884d-110">Using Windows Device Portal</span></span>

<span data-ttu-id="f884d-111">Klicken Sie auf **Start** Spalte, die für die app.</span><span class="sxs-lookup"><span data-stu-id="f884d-111">You can click on **Startup** column corresponding to the app.</span></span>
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a><span data-ttu-id="f884d-113">Mithilfe der shell</span><span class="sxs-lookup"><span data-stu-id="f884d-113">Using the shell</span></span>

<span data-ttu-id="f884d-114">Schritte zum Festlegen der Standard-app, die über die shell</span><span class="sxs-lookup"><span data-stu-id="f884d-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="f884d-115">Verbinden mit dem Gerät über [Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="f884d-115">Connect to the device via [Powershell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="f884d-116">Auflisten der Anwendungen, die mithilfe von installiert</span><span class="sxs-lookup"><span data-stu-id="f884d-116">List the applications installed using</span></span> `iotstartup list`

3. <span data-ttu-id="f884d-117">Beachten Sie die App-ID für die Anwendung, die Sie verwenden möchten, erstellen, die als Standard, und legen Sie es mit `iotstartup add headed <appid>`.</span><span class="sxs-lookup"><span data-stu-id="f884d-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="f884d-118">Verwenden Sie für die monitorlose app `iotstartup add headless <appid>`.</span><span class="sxs-lookup"><span data-stu-id="f884d-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="f884d-119">Erstellen der Time (Option)</span><span class="sxs-lookup"><span data-stu-id="f884d-119">Build time option</span></span>

<span data-ttu-id="f884d-120">Bei umfangreichen Bereitstellungen können Sie hierzu Bereitstellungspaket</span><span class="sxs-lookup"><span data-stu-id="f884d-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="f884d-121">Sie können die StartupApp/Standardeinstellung in den WCD während der Bereitstellung paketerstellung angeben.</span><span class="sxs-lookup"><span data-stu-id="f884d-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

<span data-ttu-id="f884d-123">Finden Sie unter [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) als Beispiel.</span><span class="sxs-lookup"><span data-stu-id="f884d-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="f884d-124">Erhalten Sie die Anwendung Benutzer Modell ID (AUMID) der ein Appx mit [GetAppxInfo Tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span><span class="sxs-lookup"><span data-stu-id="f884d-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="f884d-125">Vorgehensweise: Konfigurieren von "Home" Schlüssel</span><span class="sxs-lookup"><span data-stu-id="f884d-125">How to configure "Home" key</span></span>

<span data-ttu-id="f884d-126">Windows 10 IoT Anniversary Update (1607) bietet die shellunterstützung für das standardanwendungsfenster in den Vordergrund bringen, wenn eine andere Anwendung derzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f884d-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="f884d-127">Informationen zum Aktivieren des Schlüssels "Home", besuchen Sie unsere [IoT-Shell-Seite](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span><span class="sxs-lookup"><span data-stu-id="f884d-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
