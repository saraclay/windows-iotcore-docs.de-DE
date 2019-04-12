---
title: Windows-Dateifreigabe
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über das Windows-Dateifreigabe, die zum Übertragen von Dateien zu und von Ihrem Gerät verwenden.
keywords: Windows Iot, Dateiübertragung, Dateifreigabe, Windows-Dateifreigabe
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513873"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="7612d-104">Windows-Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="7612d-104">Windows file sharing</span></span>

<span data-ttu-id="7612d-105">Sie können die Windows-Dateifreigabe verwenden, zum Übertragen von Dateien in und aus Ihr Gerät.</span><span class="sxs-lookup"><span data-stu-id="7612d-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="7612d-106">Zugriff auf Ihre Dateien mithilfe von Windows-Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="7612d-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="7612d-107">Dem Dateifreigabeserver auf Ihrem Gerät Windows IoT Core wird beim Systemstart automatisch gestartet.</span><span class="sxs-lookup"><span data-stu-id="7612d-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="7612d-108">Um eine Verbindung herstellen möchten, benötigen Sie die IP-Adresse Ihres Geräts.</span><span class="sxs-lookup"><span data-stu-id="7612d-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="7612d-109">Sie finden die IP-Adresse auf die Standard-app, die gestartet wird, wenn Ihr Gerät gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="7612d-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![DefaultApp unter Windows IoT Core](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="7612d-111">Nachdem Sie die IP-Adresse haben, öffnen Sie **Datei-Explorer** auf Ihrem Computer und dem Typ `\\<TARGET_DEVICE>\c$`, wobei `<TARGET_DEVICE>` ist der Name oder die IP-Adresse Ihres Geräts für die Windows IoT Core, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="7612d-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="7612d-112">Geben Sie Ihre Benutzernamen und das Kennwort ein, wenn Sie aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="7612d-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="7612d-113">Der Benutzername sollte die IP-Adresse Ihres Windows IoT Core-Geräts als Präfix eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7612d-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="7612d-114">Beispiel: **Benutzername:** `192.168.1.118\Administrator`  **Kennwort:** `{your_password}`.</span><span class="sxs-lookup"><span data-stu-id="7612d-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![Datei-Explorer](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="7612d-116">Jetzt können Sie die Dateien auf Ihrem Gerät über Windows-Dateifreigabe zugreifen.</span><span class="sxs-lookup"><span data-stu-id="7612d-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="7612d-117">Starten und beenden die Dateifreigabe-server</span><span class="sxs-lookup"><span data-stu-id="7612d-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="7612d-118">Herstellen einer Verbindung Ihres Geräts über mit [PowerShell](../connect-your-device/powershell.md) oder [SSH](../connect-your-device/ssh.md).</span><span class="sxs-lookup"><span data-stu-id="7612d-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="7612d-119">Standardmäßig wird dem Dateifreigabeserver gestartet, wenn das Gerät gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="7612d-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="7612d-120">Geben Sie zum Beenden der Dateifreigabeserver</span><span class="sxs-lookup"><span data-stu-id="7612d-120">To stop the file sharing  server, type</span></span> `net stop Server /y`
* <span data-ttu-id="7612d-121">Geben Sie zum Starten der Dateifreigabeserver</span><span class="sxs-lookup"><span data-stu-id="7612d-121">To start the file sharing  server, type</span></span> `net start Server`

    ![Server starten und beenden](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="7612d-123">Deaktivieren und aktivieren die Dateifreigabe-Server beim Start</span><span class="sxs-lookup"><span data-stu-id="7612d-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="7612d-124">Herstellen einer Verbindung Ihres Geräts über mit [PowerShell](../connect-your-device/powershell.md) oder [SSH](../connect-your-device/ssh.md).</span><span class="sxs-lookup"><span data-stu-id="7612d-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="7612d-125">Standardmäßig wird dem Dateifreigabeserver gestartet, wenn das Gerät gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="7612d-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="7612d-126">Geben Sie zum Deaktivieren der Datei mit dem Server gemeinsam, sodass er nicht gestartet wird, wenn das Gerät gestartet wird</span><span class="sxs-lookup"><span data-stu-id="7612d-126">To disable the file sharing  server so that it does not start when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* <span data-ttu-id="7612d-127">Geben Sie zum Aktivieren der Dateifreigabeserver, sodass, die gestartet wird, wenn das Gerät gestartet wird</span><span class="sxs-lookup"><span data-stu-id="7612d-127">To enable the file sharing  server so that starts when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![Server aktivieren deaktivieren](../media/WindowsFileSharing/smb_enable_disable.png)
