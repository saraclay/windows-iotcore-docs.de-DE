---
title: Programme im Hintergrund
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum hintergrundanwendungen für Ihre IoT-Geräte zu entwickeln.
keywords: Windows Iot, Programme im Hintergrund
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512914"
---
# <a name="developing-background-applications"></a><span data-ttu-id="2fa64-104">Entwickeln von Hintergrundanwendungen</span><span class="sxs-lookup"><span data-stu-id="2fa64-104">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="2fa64-105">Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="2fa64-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="2fa64-106">Hintergrundanwendungen sind Anwendungen, die keine direkte Benutzeroberfläche haben.</span><span class="sxs-lookup"><span data-stu-id="2fa64-106">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="2fa64-107">Nach der Bereitstellung und Konfiguration werden diese Anwendungen beim Start des Computers zu starten und ausführen, ohne alle Prozesslebensdauer-Ressource verwenden Sie Einschränkungen kontinuierlich.</span><span class="sxs-lookup"><span data-stu-id="2fa64-107">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="2fa64-108">Falls sie abstürzt oder beendet wird das System automatisch diese neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="2fa64-108">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="2fa64-109">Diese Programme im Hintergrund haben eine sehr einfache Ausführung-Modell.</span><span class="sxs-lookup"><span data-stu-id="2fa64-109">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="2fa64-110">Die Vorlagen erstellen eine Klasse, die "IBackgroundTask"-Schnittstelle implementiert und generiert die Methode leer "ausführen".</span><span class="sxs-lookup"><span data-stu-id="2fa64-110">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="2fa64-111">Diese Methode "Run" ist der Einstiegspunkt der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="2fa64-111">This "Run" method is the entry point to your application.</span></span>

![Hintergrundaufgabe](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="2fa64-113">Es gibt einen wichtigen Punkt beachten: standardmäßig die Anwendung wird heruntergefahren, wenn die run-Methode abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="2fa64-113">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="2fa64-114">Dies bedeutet, dass apps, die die allgemeine IoT-Muster der Ausführung von eines Servers, die darauf warten, für die Eingabe oder auf einem Zeitgeber und führen Sie die app beenden vorzeitig finden.</span><span class="sxs-lookup"><span data-stu-id="2fa64-114">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="2fa64-115">Um dies zu verhindern, müssen Sie die "GetDeferral"-Methode, um zu verhindern, dass die Anwendung beendet wird aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2fa64-115">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="2fa64-116">Sie finden weitere Informationen zum Muster für die Verzögerung [hier](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span><span class="sxs-lookup"><span data-stu-id="2fa64-116">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="2fa64-117">Wo kann Hintergrundanwendungen aus werden installiert?</span><span class="sxs-lookup"><span data-stu-id="2fa64-117">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="2fa64-118">Sie können auch herunterladen und installieren Sie IoT-Vorlagen, um das Hintergrund-Anwendungen aus der Visual Studio Gallery können [hier](https://go.microsoft.com/fwlink/?linkid=847472).</span><span class="sxs-lookup"><span data-stu-id="2fa64-118">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="2fa64-119">Alternativ können die Vorlagen gefunden werden, durch Suchen nach `Windows IoT Core Project Templates` in die [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) oder direkt aus Visual Studio im Dialogfeld "Erweiterungen und Updates" (Extras > Erweiterungen und Updates > Online).</span><span class="sxs-lookup"><span data-stu-id="2fa64-119">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="2fa64-120">Welche Sprachen verfügbar sind?</span><span class="sxs-lookup"><span data-stu-id="2fa64-120">What languages are available?</span></span>

<span data-ttu-id="2fa64-121">**Anwendung (IoT) im Hintergrund** Vorlagen für befinden:</span><span class="sxs-lookup"><span data-stu-id="2fa64-121">**Background Application (IoT)** templates can be found for:</span></span>

* **<span data-ttu-id="2fa64-122">C++</span><span class="sxs-lookup"><span data-stu-id="2fa64-122">C++</span></span>** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **<span data-ttu-id="2fa64-123">C#</span><span class="sxs-lookup"><span data-stu-id="2fa64-123">C#</span></span>** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **<span data-ttu-id="2fa64-124">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fa64-124">Visual Basic</span></span>** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **<span data-ttu-id="2fa64-125">JavaScript</span><span class="sxs-lookup"><span data-stu-id="2fa64-125">JavaScript</span></span>** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a><span data-ttu-id="2fa64-126">Wie werden Programme im Hintergrund verwendet?</span><span class="sxs-lookup"><span data-stu-id="2fa64-126">How are background applications used?</span></span> 

<span data-ttu-id="2fa64-127">Erstellen einer hintergrundanwendung ist sehr ähnlich ist, erstellen Sie eine Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="2fa64-127">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="2fa64-128">Wenn die Hintergrundanwendung gestartet wird, wird die Run-Methode aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="2fa64-128">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="2fa64-129">Wenn die Run-Methode beendet, es sei denn, ein Deferral-Objekt erstellt wird, wird der hintergrundanwendung beendet.</span><span class="sxs-lookup"><span data-stu-id="2fa64-129">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="2fa64-130">Die allgemeinen Brauch werden, für die asynchrone Programmierung ist zu einer Verzögerung wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2fa64-130">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

<span data-ttu-id="2fa64-131">Nachdem eine Verzögerung ausgeführt wird, wird die hintergrundanwendung fortgesetzt, bis vollständige Methode für das Deferral-Objekt aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="2fa64-131">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="2fa64-132">Wie beginne hintergrundanwendungen?</span><span class="sxs-lookup"><span data-stu-id="2fa64-132">How do background applications start?</span></span>

<span data-ttu-id="2fa64-133">Diese Frage kann in der Bereitstellung und Aufrufs unterteilt werden.</span><span class="sxs-lookup"><span data-stu-id="2fa64-133">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="2fa64-134">Um einen hintergrundanwendung bereitzustellen, ist Folgendes möglich:</span><span class="sxs-lookup"><span data-stu-id="2fa64-134">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="2fa64-135">Verwenden Sie Visual Studio F5 (das Erstellen, bereitstellen und aufrufen wird).</span><span class="sxs-lookup"><span data-stu-id="2fa64-135">Use Visual Studio's F5 (which will build, deploy and invoke).</span></span>  <span data-ttu-id="2fa64-136">Weitere Informationen finden Sie unserem [Hello World-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) , in dem wir beschreiben, wie zum Bereitstellen und starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2fa64-136">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="2fa64-137">Dadurch wird nicht konfiguriert, dass die hintergrundanwendung beim start des Geräts gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2fa64-137">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="2fa64-138">Erstellen Sie eine AppX-Datei durch Auswählen des Projekts in Visual Studio > Store > App-Pakete erstellen.</span><span class="sxs-lookup"><span data-stu-id="2fa64-138">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="2fa64-139">Nachdem Sie eine AppX-Datei erstellt haben, können Sie [Windows Device Portal](../manage-your-device/DevicePortal.md) für Ihr Windows 10 IoT Core-Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2fa64-139">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="2fa64-140">Um hintergrundanwendung aufzurufen, ist Folgendes möglich:</span><span class="sxs-lookup"><span data-stu-id="2fa64-140">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="2fa64-141">Wie oben erwähnt, wird Visual Studio die F5-Funktion bereitstellen und die Hintergrund-Anwendung sofort starten.</span><span class="sxs-lookup"><span data-stu-id="2fa64-141">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="2fa64-142">Dadurch wird nicht konfiguriert, dass die hintergrundanwendung beim start des Geräts gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2fa64-142">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="2fa64-143">Für einen hintergrundanwendung, die auf einem IoT-Gerät bereitgestellt wurde, können Sie das Hilfsprogramm iotstartup.exe so konfigurieren Sie Ihre hintergrundanwendung gestartet, wenn das Gerät gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2fa64-143">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="2fa64-144">Gehen Sie zum Angeben der hintergrundanwendung als ein Start-App (**ersetzen Sie den Namen Ihrer app** für `BackgroundApplication1` unten):</span><span class="sxs-lookup"><span data-stu-id="2fa64-144">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="2fa64-145">Starten Sie eine PowerShell (PS)-Sitzung mit Ihrem Gerät Windows IoT Core, wie beschrieben [hier](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="2fa64-145">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="2fa64-146">Geben Sie die PS-Sitzung ein:</span><span class="sxs-lookup"><span data-stu-id="2fa64-146">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="2fa64-147">Der vollständige Name der hintergrundanwendung sollte etwa wie z. B. angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="2fa64-147">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="2fa64-148">Das Hilfsprogramm bestätigt, dass die hintergrundanwendung eine "monitorlose"-Anwendung ist und ordnungsgemäß installiert ist.</span><span class="sxs-lookup"><span data-stu-id="2fa64-148">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="2fa64-149">Sie sehen wahrscheinlich auch einen Headed-Eintrag für Ihre Anwendungen Hintergrund, aber dies ignoriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="2fa64-149">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="2fa64-150">Jetzt ist es einfach, diese app als "Start-App" festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2fa64-150">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="2fa64-151">Geben Sie einfach den Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="2fa64-151">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="2fa64-152">Das Hilfsprogramm wird bestätigen Sie, dass die Liste der monitorlose "Start-Apps" die hintergrundanwendung hinzugefügt wurde:</span><span class="sxs-lookup"><span data-stu-id="2fa64-152">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="2fa64-153">Fahren Sie fort, und starten Sie Ihr Windows IoT Core-Gerät neu.</span><span class="sxs-lookup"><span data-stu-id="2fa64-153">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="2fa64-154">In der PS-Sitzung können Sie den Befehl "Herunterfahren" ausgeben:</span><span class="sxs-lookup"><span data-stu-id="2fa64-154">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="2fa64-155">Nach dem Neustart des Geräts die hintergrundanwendung wird automatisch gestartet, und Windows 10 IoT Core sicherzustellen, dass sie jedes Mal, wenn es beendet, neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2fa64-155">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="2fa64-156">Sobald eine Hintergrund-app registriert wird, führen Sie automatisch, wenn die app beendet wird oder stürzt ab, wird es automatisch neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="2fa64-156">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="2fa64-157">Die app ist nicht über den Grund informiert, gestartet wird oder in der so neu gestartet werden, wenn ein Neustart besondere Aktionen Sie den Status der app in Ihrer app überwachen müssen möchten.</span><span class="sxs-lookup"><span data-stu-id="2fa64-157">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="2fa64-158">Sie können Ihre hintergrundanwendung aus der Liste der monitorlose Startup-Apps entfernen, durch Eingabe des Befehls:</span><span class="sxs-lookup"><span data-stu-id="2fa64-158">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="2fa64-159">Das Hilfsprogramm wird bestätigt, dass die hintergrundanwendung aus der Liste der monitorlose "Start-Apps" entfernt wurde:</span><span class="sxs-lookup"><span data-stu-id="2fa64-159">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a><span data-ttu-id="2fa64-160">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2fa64-160">See Also</span></span>
<span data-ttu-id="2fa64-161">So fügen Sie einen Hintergrund-app hinzu, beim Erstellen eines benutzerdefinierten Images finden Sie unter [erstellen Sie ein Appx-Paket](../build-your-image/createinstallpackage.md)</span><span class="sxs-lookup"><span data-stu-id="2fa64-161">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
