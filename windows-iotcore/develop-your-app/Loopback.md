---
title: Kommunikation mit "localhost"
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie eine TCP/IP-Verbindung mit zwei Prozessen erstellen, indem Sie "localhost" Loopback aktivieren.
keywords: Windows Iot "," Localhost "," Loopback, UWP, visual Studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512290"
---
# <a name="communicating-with-localhost-loopback"></a><span data-ttu-id="428a2-104">Kommunikation mit "localhost" (Loopback)</span><span class="sxs-lookup"><span data-stu-id="428a2-104">Communicating with localhost (loopback)</span></span>

<span data-ttu-id="428a2-105">Unter Windows IoT Core müssen Sie eine TCP/IP-Verbindung zwischen 2 auf demselben Gerät ausgeführten Prozesse erstellen möchten, und eine davon ist eine UWP-app Sie "localhost" Loopback aktivieren.</span><span class="sxs-lookup"><span data-stu-id="428a2-105">On Windows IoT Core, if you want to create a TCP/IP connection between 2 processes running on the same device and one of them is a UWP app you must enable localhost loopback.</span></span>

## <a name="loopback-and-the-debugger"></a><span data-ttu-id="428a2-106">Loopback und der debugger</span><span class="sxs-lookup"><span data-stu-id="428a2-106">Loopback and the debugger</span></span> 
<span data-ttu-id="428a2-107">In der Standardeinstellung aktiviert ausgeführt wird, unter dem Visual Studio-Debugger ausgehende Loopback automatisch für diese Debugsitzung nur.</span><span class="sxs-lookup"><span data-stu-id="428a2-107">By default, running under the Visual Studio debugger enables outbound loopback automatically for that debug session only.</span></span><span data-ttu-id="428a2-108">  Es sollte keine nichts weiter tun, solange die Loopback-Kontrollkästchen in den Debuggereinstellungen für Ihr Startprojekt aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="428a2-108">  You shouldn’t have to do anything as long as the loopback checkbox is checked in the debugger settings for your startup project.</span></span> <span data-ttu-id="428a2-109"> Wenn Sie ein socketlisteners implementieren möchten, müssen Sie "localhost" Loopback für eingehende Verbindungen (siehe unten) aktivieren.</span><span class="sxs-lookup"><span data-stu-id="428a2-109"> If you want to implement a socket listener the you must enable localhost loopback for inbound connections (see below).</span></span>
 
## <a name="enabling-the-inbound-loopback-policy"></a><span data-ttu-id="428a2-110">Aktivieren der eingehenden Loopbackrichtlinie</span><span class="sxs-lookup"><span data-stu-id="428a2-110">Enabling the inbound loopback policy</span></span>
<span data-ttu-id="428a2-111">Die "localhost" eingehende Loopbackrichtlinie für **Windows IoT Core** muss aktiviert sein, für die UWP-apps, die Server zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="428a2-111">The localhost inbound loopback policy for **Windows IoT Core** must be enabled for UWP apps that implement servers.</span></span>  <span data-ttu-id="428a2-112">Diese Richtlinie wird durch den folgenden Registrierungsschlüssel gesteuert:</span><span class="sxs-lookup"><span data-stu-id="428a2-112">This policy is controlled by the following registry key:</span></span>

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

<span data-ttu-id="428a2-113">Diesen Registrierungsschlüsselwert IoTInboundLoopbackPolicy muss auf DWORD: 00000001 festgelegt werden, aktivieren zu können.</span><span class="sxs-lookup"><span data-stu-id="428a2-113">This IoTInboundLoopbackPolicy registry key value must be set to dword:00000001 to enable.</span></span> <span data-ttu-id="428a2-114">Wenn Sie den Registrierungswert IoTInboundLoopbackPolicy ändern, müssen Sie für die Änderung wirksam wird neu starten.</span><span class="sxs-lookup"><span data-stu-id="428a2-114">If you change the IoTInboundLoopbackPolicy registry value you must reboot for the change to take effect.</span></span><span data-ttu-id="428a2-115">  Die Loopback-Richtlinie von "localhost" standardmäßig aktiviert werden sollte, auf \*\*Windows IoT Core** </span><span class="sxs-lookup"><span data-stu-id="428a2-115">  The localhost loopback policy should be enabled by default on \*\*Windows IoT Core**</span></span>

<span data-ttu-id="428a2-116">So überprüfen, dass der Wert festlegen, führen Sie den folgenden Befehl auf dem **Windows IoT Core** Gerät:</span><span class="sxs-lookup"><span data-stu-id="428a2-116">To verify that the value is set execute the following command on the **Windows IoT Core** device:</span></span>

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

<span data-ttu-id="428a2-117">So aktivieren Sie die Richtlinie, führen Sie den folgenden Befehl auf dem **Windows IoT Core** Gerät:</span><span class="sxs-lookup"><span data-stu-id="428a2-117">To enable the policy execute the following command on the **Windows IoT Core** device:</span></span>

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a><span data-ttu-id="428a2-118">Aktivieren die Loopbacks für eine UWP-Anwendung</span><span class="sxs-lookup"><span data-stu-id="428a2-118">Enabling loopback for a UWP application</span></span>
<span data-ttu-id="428a2-119">Bevor Sie die Loopbacks für eine Anwendung aktivieren können, benötigen Sie den paketfamiliennamen.</span><span class="sxs-lookup"><span data-stu-id="428a2-119">Before you can enable loopback for an application you will need the package family name.</span></span>  <span data-ttu-id="428a2-120">Sie finden den paketfamiliennamen für eine installierte Anwendung mit **Iotstartup Liste**.</span><span class="sxs-lookup"><span data-stu-id="428a2-120">You can find the package family name for an installed application by running **iotstartup list**.</span></span>  <span data-ttu-id="428a2-121">Wenn die **Iotstartup Liste** Eintrag für die Anwendung ist IoTCoreDefaultApp\_1w720vyc4ccym! Klicken Sie dann den paketfamiliennamen-App ist IoTCoreDefaultApp\_1w720vyc4ccym</span><span class="sxs-lookup"><span data-stu-id="428a2-121">If the **iotstartup list** entry for the application is IoTCoreDefaultApp\_1w720vyc4ccym!App then the package family name is IoTCoreDefaultApp\_1w720vyc4ccym</span></span>

<span data-ttu-id="428a2-122">Loopback-Verbindungen von Clients zu `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span><span class="sxs-lookup"><span data-stu-id="428a2-122">To enable loopback for client connections use `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span></span>  <span data-ttu-id="428a2-123">CheckNetIsolation.exe konfiguriert die Loopbacks für die Anwendung, und beenden.</span><span class="sxs-lookup"><span data-stu-id="428a2-123">CheckNetIsolation.exe will configure loopback for the application and exit.</span></span> <span data-ttu-id="428a2-124">Dadurch wird die Anwendung zum Herstellen ausgehende Verbindungen zu einem Server aktiviert.</span><span class="sxs-lookup"><span data-stu-id="428a2-124">This will enable the application to make outbound connections to a server.</span></span>

<span data-ttu-id="428a2-125">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="428a2-125">Example:</span></span> `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

<span data-ttu-id="428a2-126">So aktivieren Sie eine Server-Anwendung zum Empfangen von eingehenden Verbindungen verwenden `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span><span class="sxs-lookup"><span data-stu-id="428a2-126">To enable a server application to receive inbound connections use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span></span> <span data-ttu-id="428a2-127">Im Gegensatz zur Konfiguration der ausgehenden Verbindung müssen eingehende Verbindungen CheckNetIsolation.exe auszuführende fortlaufend auf, während die Serveranwendung Verbindungen empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="428a2-127">Unlike outbound connection configuration, inbound connections require CheckNetIsolation.exe to run continuously while the server application is receiving connections.</span></span><span data-ttu-id="428a2-128">  Dies ist ein neuer ist als 10.0.14393 Betriebssystembuild erforderlich.</span><span class="sxs-lookup"><span data-stu-id="428a2-128">  This requires an OS build newer than 10.0.14393.</span></span>

<span data-ttu-id="428a2-129">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="428a2-129">Example:</span></span> `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

<span data-ttu-id="428a2-130">Die beste Möglichkeit, CheckNetIsolation.exe beim Start automatisch ausgeführt wird schtasks.exe verwendet:</span><span class="sxs-lookup"><span data-stu-id="428a2-130">The best way to run CheckNetIsolation.exe automatically on startup is to use schtasks.exe:</span></span> `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

<span data-ttu-id="428a2-131">Beim Neustarten werden Sie überprüfen, checknetisolation.exe mit tlist.exe ausgeführt wird oder [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span><span class="sxs-lookup"><span data-stu-id="428a2-131">Upon rebooting you should be able to verify that checknetisolation.exe is running by using tlist.exe or [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span></span>
