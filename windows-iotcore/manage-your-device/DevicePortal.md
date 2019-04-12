---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, wie Sie mit der Windows Device Portal zum Konfigurieren und verwalten Ihr Gerät Remote.
keywords: Windows Iot, Windows Device Portal, remote-Device-portal
ms.openlocfilehash: 715e9c138e86efcd82b485d832c5fbdd536398dd
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512410"
---
# <a name="windows-device-portal"></a><span data-ttu-id="6cdec-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="6cdec-104">Windows Device Portal</span></span>
   <span data-ttu-id="6cdec-105">Die Windows Device Portal (WDP) können Sie konfigurieren und verwalten Sie Ihr Gerät remote über das lokale Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="6cdec-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="6cdec-106">Die wichtigsten Funktionen sind unter dokumentiert die [Windows Device Portal-Seite "Übersicht"](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="6cdec-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![Device Portal-Startseite](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="6cdec-108">Verwenden Sie Maker Images nicht für gewerbliche Nutzung aus.</span><span class="sxs-lookup"><span data-stu-id="6cdec-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="6cdec-109">Wenn Sie ein Gerät commercializing sind, müssen Sie eine benutzerdefinierte FFU für optimale Sicherheit verwenden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="6cdec-110">Weitere Informationen finden Sie [hier](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="6cdec-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="6cdec-111">Live-Kernel-Debugging ist derzeit für ARM-Geräte fehlgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="6cdec-112">Wir arbeiten daran, dies behoben werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cdec-113">Wenn Sie ein open Retail-Gerät für die kommerzielle Bereitstellung in einer "Installation von bestimmten/eingeschränkt" erstellen (d. h. Vorinstallations- oder Retail Store), in dem der Endbenutzer ist die endgültige Konfiguration und Dokumentieren Sie Ihre Kunden, die sie müssen [erhalten eine Zertifikat für WDP, und installieren Sie es WDP und eine Verbindung herstellen Browser sowohl Kennwörter WDP geändert werden](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), und klicken Sie dann mithilfe von WDP in dieser Instanz mit schmalen kommerziellen zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="6cdec-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="6cdec-114">Einzelhandel-Images in diesem Szenario sollte dennoch *nicht* IOT_TOOLKIT u. sollten IOT_WEBBEXTN Paket verwenden, um WDP zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6cdec-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="6cdec-115">Shared-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="6cdec-115">Shared Documentation</span></span>
<span data-ttu-id="6cdec-116">WDP ist ein Tool für Entwickler von Windows 10-Geräten gemeinsam verwendet.</span><span class="sxs-lookup"><span data-stu-id="6cdec-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="6cdec-117">Jedes Produkt verfügt über eine eigene spezielle Features, aber die Kernfunktionalitäten sind identisch.</span><span class="sxs-lookup"><span data-stu-id="6cdec-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="6cdec-118">Dokumentation für die wichtigsten Funktionen befinden sich die [Windows Device Portal-Seite "Übersicht"](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span><span class="sxs-lookup"><span data-stu-id="6cdec-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="6cdec-119">Der Rest der folgenden Dokumentation werden bestimmte IoT.</span><span class="sxs-lookup"><span data-stu-id="6cdec-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="6cdec-120">Einrichtung</span><span class="sxs-lookup"><span data-stu-id="6cdec-120">Set up</span></span>

<span data-ttu-id="6cdec-121">Es gibt zwei Möglichkeiten, wechseln die Windows Device Portal betriebsbereit zu machen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="6cdec-122">1. Windows 10 IoT Dashboard</span><span class="sxs-lookup"><span data-stu-id="6cdec-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="6cdec-123">Zunächst sollten Sie zum Herunterladen der [Windows 10 IoT-Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), ein Tool für Entwickler, die es einfach macht, neue Geräte einrichten.</span><span class="sxs-lookup"><span data-stu-id="6cdec-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="6cdec-124">Nachdem Sie das Dashboard verwendet haben, um ein Windows 10 IoT Core-Image auf Ihrem Gerät zu aktualisieren, überprüfen Sie, dass Ihr Gerät unter "Meine Geräte" angezeigt wird, wird ein.</span><span class="sxs-lookup"><span data-stu-id="6cdec-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="6cdec-125">Verwenden Sie dort die Auslassungspunkte klicken Sie unter "Aktionen" auf "Öffnen in Device Portal".</span><span class="sxs-lookup"><span data-stu-id="6cdec-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="6cdec-126">Von dort aus gelangen Sie auf die Device Portal-Authentifizierungsseite, es sei denn, Sie zuerst die Anmeldeinformationen geändert, werden die standardmäßigen Anmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="6cdec-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="6cdec-127">2. Browser</span><span class="sxs-lookup"><span data-stu-id="6cdec-127">2. Browser</span></span>
<span data-ttu-id="6cdec-128">Wenn Sie können nicht finden im Dashboard Ihres Geräts oder über das Dashboard zu überspringen möchten, können Sie auch im Device Portal öffnen, durch die IP-Adresse Ihres Geräts plus Eingabe `:8080` am Ende.</span><span class="sxs-lookup"><span data-stu-id="6cdec-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="6cdec-129">Bei ordnungsgemäßer Durchführung, sollte es etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="6cdec-129">When done correctly, it should look something like this:</span></span>


   ![Geräte IoTDashboard anzeigen](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="6cdec-131">IoT-spezifischen features</span><span class="sxs-lookup"><span data-stu-id="6cdec-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="6cdec-132">Einstellungen für Geräte</span><span class="sxs-lookup"><span data-stu-id="6cdec-132">Device Settings</span></span>

<span data-ttu-id="6cdec-133">IoT Core Fügt ein Kontrollkästchen zum Aktivieren oder Deaktivieren der [Bildschirmtastatur](../develop-your-app/OnScreenKeyboard.md)</span><span class="sxs-lookup"><span data-stu-id="6cdec-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="6cdec-134">Dieses Kontrollkästchen hat es sich um ein bekanntes Problem, in dem sie "von leuchtet," überprüft, um nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6cdec-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="6cdec-135">Bitte aktualisieren Sie die Seite (F5), nach dem Klicken auf, um sicherzustellen, dass das Kontrollkästchen mit den gewünschten Zustand angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6cdec-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="6cdec-136">Apps</span><span class="sxs-lookup"><span data-stu-id="6cdec-136">Apps</span></span>
<span data-ttu-id="6cdec-137">Stellt Funktionen für Installation/Deinstallation für AppX-Paketen und Paketen auf Ihrem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="6cdec-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
![App-Liste](../media/DevicePortal/AppList.png)

<span data-ttu-id="6cdec-139">IoT Core ist einzigartig, da es nur eine Vordergrund-app auf einmal ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="6cdec-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="6cdec-140">Die app-Liste geändert wird, um sicherzustellen, dass dies der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="6cdec-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="6cdec-141">Unter den **Start** Spalte, Sie können auswählen, so viele Programme im Hintergrund standardmäßig gestartet, aber kann nur eine Anwendung im Vordergrund festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6cdec-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="6cdec-142">App-Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="6cdec-142">App File Explorer</span></span>

<span data-ttu-id="6cdec-143">Die app-Datei-Explorer zeigt die Verzeichnisse, dass Ihre apps zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="6cdec-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="6cdec-144">CameraRoll wird von allen apps gemeinsam genutzt.</span><span class="sxs-lookup"><span data-stu-id="6cdec-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="6cdec-145">Dokumente von allen apps gemeinsam genutzt wird</span><span class="sxs-lookup"><span data-stu-id="6cdec-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="6cdec-146">LocalAppData enthält Ordner für jede app spezifisch.</span><span class="sxs-lookup"><span data-stu-id="6cdec-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="6cdec-147">In diesem Ordner werden auf dem gleichen Namen wie Ihre app und anderen apps nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6cdec-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="6cdec-148">Debuggen</span><span class="sxs-lookup"><span data-stu-id="6cdec-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="6cdec-149">Kernel-dumps</span><span class="sxs-lookup"><span data-stu-id="6cdec-149">Kernel dumps</span></span>
![Debuggen mit Kernel-dumps](../media/DevicePortal/Debug1.png)

<span data-ttu-id="6cdec-151">Alle Systemabstürze werden automatisch protokolliert und sind verfügbar, um über das Web-Management-Tool anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="6cdec-152">Dann können die Kernelabbild herunterladen und versucht zu ermitteln, was vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="6cdec-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="6cdec-153">Prozessdumps</span><span class="sxs-lookup"><span data-stu-id="6cdec-153">Process dumps</span></span>
![Debuggen mit prozessdumps](../media/DevicePortal/Debug2.png)

<span data-ttu-id="6cdec-155">Dies entspricht in Dumps für Live-Kernel, aber die Prozesse im Benutzermodus.</span><span class="sxs-lookup"><span data-stu-id="6cdec-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="6cdec-156">Klicken auf die **herunterladen** Schaltfläche führt dazu, dass einen "Minidump" und der gesamte Status dieses Prozesses wird heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="6cdec-157">Dies ist gut für das Debuggen von hängenden Prozessen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="6cdec-158">Absturz kerneleinstellungen</span><span class="sxs-lookup"><span data-stu-id="6cdec-158">Kernel crash settings</span></span>
![Absturz kerneleinstellungen](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="6cdec-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="6cdec-160">Bluetooth</span></span>
<span data-ttu-id="6cdec-161">Auf dieser Seite erfahren Sie, alle gekoppelten Bluetooth-Geräte und alle Geräte, die die erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="6cdec-162">Um eine andere Bluetooth-Gerät gekoppelt werden, setzen Sie das Gerät im Modus zum Verbinden, und warten Sie, bis er in der Liste der verfügbaren Geräte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![Liste der Bluetooth-Geräte](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="6cdec-164">Klicken Sie auf **Paar Link** um das Gerät zu koppeln.</span><span class="sxs-lookup"><span data-stu-id="6cdec-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="6cdec-165">Wenn das Gerät eine PIN anfordert, für die Paarung, tritt ein Popup mit der ein Meldungsfeld mit der PIN.</span><span class="sxs-lookup"><span data-stu-id="6cdec-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="6cdec-166">Sobald das Gerät verbunden ist, wird es in der Liste der gepaarten Geräte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6cdec-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="6cdec-167">Sie können un-Paar des Geräts, indem Sie durch Klicken auf **entfernen**.</span><span class="sxs-lookup"><span data-stu-id="6cdec-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="6cdec-168">Nachdem Sie auf der Seite "Bluetooth" navigieren, wird Ihr Gerät von anderen Geräten erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="6cdec-169">Sie können auch auf Ihrem PC/Telefon zu finden und verbinden Sie es von dort aus.</span><span class="sxs-lookup"><span data-stu-id="6cdec-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="6cdec-170">Weitere Informationen zu Bluetooth finden Sie auf die [Bluetooth-Seite](https://go.microsoft.com/fwlink/?linkid=823223).</span><span class="sxs-lookup"><span data-stu-id="6cdec-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="6cdec-171">IoT-Onboarding</span><span class="sxs-lookup"><span data-stu-id="6cdec-171">IoT Onboarding</span></span>

<span data-ttu-id="6cdec-172">IoT-Onboarding stellt Unterstützung für die Konfiguration eines IoT-Geräts Wi-Fi-Konnektivitätsoptionen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="6cdec-173">**(Internet Connection Sharing, ICS)** gemeinsame Nutzung der Internetverbindung können Sie den Zugriff auf das Internet Ihres Geräts mit anderen Geräten, die mit dem Gerät verbunden sind, über die Wi-Fi-SoftAP nutzen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="6cdec-174">Um dieses Feature verwenden zu können, muss Ihr Windows 10 IoT-Gerät (z. B. über eine Kabelverbindung für die LAN) mit dem Internet zugreifen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="6cdec-175">In "Onboarding-Konnektivität > -> SoftAP Einstellungen auf"aktivieren"und die SSID-Namen und das Kennwort fest.</span><span class="sxs-lookup"><span data-stu-id="6cdec-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="6cdec-176">Wählen Sie dann in "Verbindungen -> gemeinsame Nutzung der Internetverbindung" für "Zugriff auf Point-Adapter", wählen Sie "Microsoft Wi-FI Direct virtuellen Adapter #2" und "gemeinsam genutzten Netzwerkadapter" Ihren verkabelte Ethernet-Adapter ein.</span><span class="sxs-lookup"><span data-stu-id="6cdec-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="6cdec-177">Klicken Sie abschließend auf "start SAS".</span><span class="sxs-lookup"><span data-stu-id="6cdec-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="6cdec-178">Nach dem Start der SoftAP auf Ihrem Windows 10 IoT-Gerät Verbindung ein separates WLAN-fähiges Gerät.</span><span class="sxs-lookup"><span data-stu-id="6cdec-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="6cdec-179">Nach dem Herstellen einer Verbindung werden Ihre separaten WLAN-fähiges Geräts über Ihr Windows 10 IoT-Gerät eine Verbindung mit dem Internet herstellen können.</span><span class="sxs-lookup"><span data-stu-id="6cdec-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="6cdec-180">Gemeinsam genutzter Internetverbindung ist deaktiviert, wenn ein WLAN-Profil auf dem Gerät vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="6cdec-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="6cdec-181">Beispielsweise werden gemeinsam genutzter Internetverbindung deaktiviert werden, wenn Sie eine Verbindung mit einem Wi-Fi-Zugriffspunkt herstellen und überprüfen Sie "Create-Profil (automatisch erneut verbinden)".</span><span class="sxs-lookup"><span data-stu-id="6cdec-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="6cdec-182">**Einstellungen für SoftAP** der SoftAP-Einstellungen können Sie steuern, ob Ihres Geräts SoftAP aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="6cdec-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="6cdec-183">Es bietet auch eine Möglichkeit für die Konfiguration Ihrer SoftAP die SSID und die WPA2-PSK Schlüssel dem von einem anderen Gerät die Verbindung der SoftAP erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="6cdec-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="6cdec-184">**Einstellungen für die Integration von AllJoyn** der AllJoyn-Onboarding-Einstellungen können Sie steuern, ob Ihres Geräts Wi-Fi-Verbindung kann über Ihres Geräts AllJoyn Onboarding Producer konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="6cdec-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="6cdec-185">Wenn ein separates Gerät mit einer AllJoyn Onboarding Consumer-Anwendung mit Ihrem Windows 10 IoT-SoftAP verbunden ist, kann AllJoyn-Onboarding-Consumer-Anwendung so konfigurieren Sie Ihre IoT-Geräte, WLAN-Adapter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="6cdec-186">Wenn aktiviert, verwendet die app AllJoyn Onboarding Producer (IoTOnboarding) die Authentifizierungsmethode ECDHE_NULL.</span><span class="sxs-lookup"><span data-stu-id="6cdec-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="6cdec-187">AllJoyn mit Integration mit Windows 10 IoT 10.0.14393 erstellt werden soll, oder zuvor erfordert eine Aktualisierung der <strong>IotOnboarding</strong> Beispiel möglicherweise [hier zum Download](https://github.com/ms-iot/samples).</span><span class="sxs-lookup"><span data-stu-id="6cdec-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

![<span data-ttu-id="6cdec-188">Onboarding auf AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding auf gemeinsam genutzter Internetverbindung</span><span class="sxs-lookup"><span data-stu-id="6cdec-188">Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS</span></span>](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> <span data-ttu-id="6cdec-189">Access Point-Adapter ist der WLAN-Adapter, die als ein WLAN-Zugriffspunkt (sie hat in der Regel eine IP-Adresse wie 192.168.137.1) fungieren.</span><span class="sxs-lookup"><span data-stu-id="6cdec-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="6cdec-190">Gemeinsam genutzten Netzwerkadapter ist ein Adapter, die mit dem Internet verbindet (z. B.: Ethernet-Adapter).</span><span class="sxs-lookup"><span data-stu-id="6cdec-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![Integrieren in Soft AP](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="6cdec-192">SoftAP SSID wird automatisch von "AJ_" verwendet werden, wenn es sich bei AllJoyn Onboarding aktiviert ist, und die MAC-Adresse des WLAN-Adapters angehängt sein.</span><span class="sxs-lookup"><span data-stu-id="6cdec-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="6cdec-193">Die Passphrase SoftAP muss zwischen 8 und 63 ASCII-Zeichen sein.</span><span class="sxs-lookup"><span data-stu-id="6cdec-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="6cdec-194">TPM-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6cdec-194">TPM configuration</span></span>
<span data-ttu-id="6cdec-195">Das Trusted Platform Module (TPM) ist eine kryptografische Coprozessor, einschließlich der Funktionen für die zufallszahlengenerierung, sicheren Generierung von kryptografischen Schlüsseln und Einschränkung ihrer Verwendung.</span><span class="sxs-lookup"><span data-stu-id="6cdec-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="6cdec-196">Darüber hinaus Funktionen wie remote Attestation und sealed-Speicher.</span><span class="sxs-lookup"><span data-stu-id="6cdec-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="6cdec-197">Weitere Informationen zu den TPM und die Sicherheit unter IoT Core finden Sie auf die [die Entwicklung von sicheren Geräten](../secure-your-device/BuildingSecureDevices.md) Seite und die [TPM](../secure-your-device/TPM.md) Seite.</span><span class="sxs-lookup"><span data-stu-id="6cdec-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cdec-198">Limpet.exe verwendet Windows IoT Core angehören.</span><span class="sxs-lookup"><span data-stu-id="6cdec-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="6cdec-199">Ab Oktober 2018 können sie steht jetzt als ein open-Source-Projekt wird auf [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client).</span><span class="sxs-lookup"><span data-stu-id="6cdec-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="6cdec-200">Um Tests einfacher zu machen, wir verfügen über eine nicht signierte vorab erstellte Version Limpet.exe verfügbar und kann direkt von WDP heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="6cdec-201">Sie müssen nur die Registerkarte "TPM-Konfiguration" und "Neueste installieren" klicken.</span><span class="sxs-lookup"><span data-stu-id="6cdec-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="6cdec-202">Diese Version von Limpet.exe sollte nicht mit endgültigen Produkt ausgeliefert werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="6cdec-203">Stattdessen müssen Sie open Source-Projekt erstellen, Signieren und Packen sie mit Ihrem Image.</span><span class="sxs-lookup"><span data-stu-id="6cdec-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="6cdec-204">Konfiguration von Azure Clients</span><span class="sxs-lookup"><span data-stu-id="6cdec-204">Azure Clients configuration</span></span>

<span data-ttu-id="6cdec-205">IoT-Geräte können per Remotezugriff über Cloud-Dienste verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="6cdec-206">Azure bietet einen sehr umfangreichen Satz von Diensten für derartige Szenarien bieten.</span><span class="sxs-lookup"><span data-stu-id="6cdec-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="6cdec-207">Wir haben eine geräteverwaltungsclient erstellt, die mehrere Windows-Verwaltungsfunktionen zur Verfügung und ergänzt, die die von Azure Device Provisioning Service (DPS) und des Azure IoT Hub-Dienst auf der Windows-Plattform.</span><span class="sxs-lookup"><span data-stu-id="6cdec-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="6cdec-208">Die Clients werden als open Source-Projekte bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="6cdec-209">Um leichter testen, werden wir vorab erstellte Binärdateien bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="6cdec-210">Sie können sich auf die Registerkarte "Azure-Clients" in WDP zu installieren. Führen Sie die Binärdateien zu testen.</span><span class="sxs-lookup"><span data-stu-id="6cdec-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="6cdec-211">Diese Version der Tools sollten nicht mit der endgültigen Produkt ausgeliefert werden.</span><span class="sxs-lookup"><span data-stu-id="6cdec-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="6cdec-212">Stattdessen müssen Sie open Source-Projekt erstellen, Signieren und Packen sie mit Ihrem Image.</span><span class="sxs-lookup"><span data-stu-id="6cdec-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="6cdec-213">In dieser Dokumentation wird aktualisiert, sobald die open-Source-Projekte für die Nutzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="6cdec-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="6cdec-214">Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="6cdec-214">Remote</span></span>
<span data-ttu-id="6cdec-215">Die Windows IoT-Remoteserver ermöglicht finden Sie unter was auf ihrem Gerät angezeigt wird, ohne eine Verbindung eines physischen Monitors mit der Tastatur.</span><span class="sxs-lookup"><span data-stu-id="6cdec-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="6cdec-216">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6cdec-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="6cdec-217">Ändern des Standardports</span><span class="sxs-lookup"><span data-stu-id="6cdec-217">Changing the default port</span></span>
 
1. <span data-ttu-id="6cdec-218">Starten Sie Powershell und [eine Verbindung mit Ihrem Gerät herstellen.](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="6cdec-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="6cdec-219">Herunterladen [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, erstellen und kopieren Sie ihn auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="6cdec-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="6cdec-220">Übernehmen des Besitzes des Registrierungsschlüssels für den Dienst durch Ausführen</span><span class="sxs-lookup"><span data-stu-id="6cdec-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="6cdec-221">Legen Sie den gewünschten Port durch Ändern der registrierungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="6cdec-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="6cdec-222">Starten Sie den Dienst WebManagement mit folgenden oder durch einen Neustart des Geräts</span><span class="sxs-lookup"><span data-stu-id="6cdec-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="6cdec-223">Mithilfe von HTTPS</span><span class="sxs-lookup"><span data-stu-id="6cdec-223">Using HTTPS</span></span> 

<span data-ttu-id="6cdec-224">Wenn Sie HTTPS verwenden möchten, zuerst nutzen Sie den Besitz des Registrierungsschlüssels, wie im vorherigen Abschnitt beschrieben und legen Sie die Registrierungsschlüssel HttpsPort und EncryptionMode wie unten gezeigt, und klicken Sie dann starten den Webmanagement-Dienst neu</span><span class="sxs-lookup"><span data-stu-id="6cdec-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="6cdec-225">Datenbankbereitstellung Device Portal mit einem benutzerdefinierten SSL-Zertifikat</span><span class="sxs-lookup"><span data-stu-id="6cdec-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="6cdec-226">In der Windows 10 Creators Update hinzugefügt die Windows Device Portal eine Möglichkeit für Geräteadministratoren ein benutzerdefiniertes Zertifikat für die Verwendung in HTTPS-Kommunikation zu installieren.</span><span class="sxs-lookup"><span data-stu-id="6cdec-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="6cdec-227">Weitere Informationen, [finden Sie in der Dokumentation unter Windows Device Portal Dokumentation](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span><span class="sxs-lookup"><span data-stu-id="6cdec-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 


## <a name="additional-resources"></a><span data-ttu-id="6cdec-228">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6cdec-228">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="6cdec-229">Windows Device Portal-Seite "Übersicht"</span><span class="sxs-lookup"><span data-stu-id="6cdec-229">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
