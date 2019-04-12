---
title: File Transfer Protocol
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie (FTP, File Transfer Protocol) verwenden, um Dateien zu und von Ihren Geräten zu übertragen.
keywords: Transfer-Protokoll für Windows Iot, FTP, Datei, die Übertragung von Dateien, die Geräte
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512665"
---
# <a name="file-transfer-protocol"></a><span data-ttu-id="3a548-104">File Transfer Protocol</span><span class="sxs-lookup"><span data-stu-id="3a548-104">File Transfer Protocol</span></span>
<span data-ttu-id="3a548-105">Die Datei Transfer Protocol (FTP) können Sie zum Übertragen von Dateien in und aus Ihr Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="3a548-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a548-106">FTP wird für Entwickler, die anfängliche Entwicklung vereinfachen, in der Regel empfohlen.</span><span class="sxs-lookup"><span data-stu-id="3a548-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="3a548-107">Wir empfehlen nicht mithilfe von FTP in Retail-Geräten.</span><span class="sxs-lookup"><span data-stu-id="3a548-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="3a548-108">Starten Sie den FTP-Server auf Ihrem Gerät</span><span class="sxs-lookup"><span data-stu-id="3a548-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="3a548-109">Standardmäßig ist der FTP-Server auf Ihrem IoT Core-Gerät deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="3a548-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="3a548-110">Um den FTP-Server auf Ihrem Gerät zu starten, müssen Sie zunächst auf Ihrem Gerät über eine Verbindung herstellen [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="3a548-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="3a548-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3a548-111">Type</span></span> `start C:\Windows\System32\ftpd.exe`
* <span data-ttu-id="3a548-112">Sehen Sie sich, dass der Server, indem Sie eingeben ausgeführt wird `tlist`, die werden alle ausgeführten Prozesse aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="3a548-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="3a548-113">Wenn der FTP-Server ausgeführt wird, sollten Sie sehen `ftpd.exe` in der Liste.</span><span class="sxs-lookup"><span data-stu-id="3a548-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![FTP-Start](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="3a548-115">Beenden den FTP-Server auf Ihrem Gerät<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="3a548-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="3a548-116">Um den FTP-Server auf Ihrem Gerät IoT Core zu beenden, müssen Sie zunächst auf Ihrem Gerät über eine Verbindung herstellen [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="3a548-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="3a548-117">Wenn Sie eine Verbindung mithilfe von PowerShell hergestellt, geben Sie `kill -processname ftpd*` auf den FTP-Vorgang zu beenden.</span><span class="sxs-lookup"><span data-stu-id="3a548-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![Beenden der FTP-PowerShell](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="3a548-119">Wenn Sie eine Verbindung über SSH hergestellt, geben Sie `kill ftpd*` auf den FTP-Vorgang zu beenden.</span><span class="sxs-lookup"><span data-stu-id="3a548-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![FTP-SSH beenden](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="3a548-121">Zugriff auf Ihre Dateien über FTP</span><span class="sxs-lookup"><span data-stu-id="3a548-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="3a548-122">Der FTP-Server auf Ihrem Gerät IoT Core wird beim Systemstart automatisch gestartet.</span><span class="sxs-lookup"><span data-stu-id="3a548-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="3a548-123">Um eine Verbindung herstellen möchten, benötigen Sie die IP-Adresse Ihres Geräts.</span><span class="sxs-lookup"><span data-stu-id="3a548-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="3a548-124">Sie finden die IP-Adresse auf die Standard-app, die gestartet wird, wenn Ihr Gerät gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="3a548-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![DefaultApp unter Windows IoT Core](../media/ftp/DefaultApp.png)

* <span data-ttu-id="3a548-126">Nachdem Sie die IP-Adresse haben, öffnen Sie **Datei-Explorer** auf Ihrem PC, und geben `ftp://<TARGET_DEVICE>`, wobei `<TARGET_DEVICE>` ist entweder der Name oder die IP-Adresse von Ihrem Gerät, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="3a548-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="3a548-127">Geben Sie Ihre Benutzernamen und das Kennwort ein, wenn Sie aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="3a548-127">Enter your administrator username and password if prompted.</span></span>

![FTP-explorer](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="3a548-129">Jetzt können Sie die Dateien auf Ihrem Gerät über FTP zugreifen.</span><span class="sxs-lookup"><span data-stu-id="3a548-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="3a548-130">Ändern die FTP-Stammverzeichnis</span><span class="sxs-lookup"><span data-stu-id="3a548-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="3a548-131">Wird standardmäßig der FTP-Server, alle Ordner im Stammverzeichnis des Geräts in dessen C: zeigt\\.</span><span class="sxs-lookup"><span data-stu-id="3a548-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="3a548-132">Führen Sie die gleichen Schritte aus, um den FTP-Server zu starten, außer dass Sie in das Stammverzeichnis als Parameter übergeben, um das Root-Verzeichnis zu ändern.</span><span class="sxs-lookup"><span data-stu-id="3a548-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="3a548-133">Um dies zu ändern, zunächst eine Verbindung mit Ihrem Gerät über [PowerShell](../connect-your-device/PowerShell.md) oder [SSH](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="3a548-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="3a548-134">[Beenden Sie](#stopftp) der FTP-Prozesses, wenn er bereits ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a548-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="3a548-135">Typ `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, wobei `<PATH_TO_DIRECTORY>` ist der absolute Pfad zu dem Verzeichnis, das als Stammverzeichnis festlegen, wie z. B. möchten `C:\Users\DefaultAccount`.</span><span class="sxs-lookup"><span data-stu-id="3a548-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![FTP, beginnen Sie mit dem Parameter](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="3a548-137">Nun, wenn Sie über FTP an Ihr Gerät verbinden, sehen den Inhalt des Stammverzeichnisses Sie, die Sie festlegen.</span><span class="sxs-lookup"><span data-stu-id="3a548-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![FTP-Explorer mit der neuen Stammverzeichnis](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="3a548-139">Um diese Änderungen permanent zu machen, müssen Sie einen Aufruf hinzufügen `start ftpd.exe <PATH_TO_DIRECTORY>` , in denen `<PATH_TO_DIRECTORY>` ist der absolute Pfad zu dem Verzeichnis, das als Stammverzeichnis festlegen, wie z. B. möchten `C:\Data\Users\DefaultAccount` zu OEMCustomization.cmd und platzieren</span><span class="sxs-lookup"><span data-stu-id="3a548-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in</span></span> `C:\Windows\System32`
