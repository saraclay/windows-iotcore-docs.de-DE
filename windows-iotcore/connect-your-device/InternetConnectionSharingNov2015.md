---
title: Gemeinsame Nutzung der Tutorial (Release vom November 2015)
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
description: Informationen Sie zum Aktivieren und konfigurieren die gemeinsame Nutzung für die November 2015-Version von Windows.
keywords: Windows Iot, Internet Connection Sharing, ICS, Device Portal
ms.openlocfilehash: c8f27b48197a0ec881a66da5d3e81272b3076100
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513034"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a><span data-ttu-id="0bc0b-104">Gemeinsame Nutzung der Tutorial (Release vom November 2015)</span><span class="sxs-lookup"><span data-stu-id="0bc0b-104">Internet Connection Sharing Tutorial (November 2015 Release)</span></span>

<span data-ttu-id="0bc0b-105">Dieses Dokument beschreibt die Schritte zum Aktivieren (Internet Connection Sharing, ICS) auf einem Gerät mit Windows 10 IoT Core Release von November 2015.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-105">This document describes the steps to enable Internet Connection Sharing (ICS) on a device running Windows 10 IoT Core November 2015 Release.</span></span> <span data-ttu-id="0bc0b-106">Das Ziel ist eine Internetverbindung zwischen einer Software Wi-Fi-Zugriffspunkt (SoftAP) und ein Ethernet-Adapter freigeben.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-106">The objective is to share an Internet connection between a software Wi-Fi access point (SoftAP) and an Ethernet adapter.</span></span> <span data-ttu-id="0bc0b-107">Bei Verwendung der Anniversary Version von Windows 10 IoT Core finden Sie in der [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span><span class="sxs-lookup"><span data-stu-id="0bc0b-107">If you are using the Windows 10 IoT Core Anniversary Release please refer to the [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0bc0b-108">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0bc0b-108">Prerequisites</span></span>

* <span data-ttu-id="0bc0b-109">Gerät mit Windows 10 IoT Core Release von November 2015.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-109">Device running Windows 10 IoT Core November 2015 Release.</span></span>
* <span data-ttu-id="0bc0b-110">Wi-Fi-USB-Geräte, die eine SoftAP ab.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-110">Wi-Fi USB device capable of starting a SoftAP.</span></span> <span data-ttu-id="0bc0b-111">Finden Sie in der [Hardware-Kompatibilitätsliste](../learn-about-hardware/HardwareCompatList.md) Wi-Fi-USB-Geräte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-111">Please refer to the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) for supported Wi-Fi USB devices.</span></span>
* <span data-ttu-id="0bc0b-112">Ethernet-Verbindung mit Internetzugriff.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-112">Ethernet connection with Internet Access.</span></span>


## <a name="setup"></a><span data-ttu-id="0bc0b-113">Setup</span><span class="sxs-lookup"><span data-stu-id="0bc0b-113">Setup</span></span>

### <a name="step-1-gathering-network-information"></a><span data-ttu-id="0bc0b-114">Schritt 1: Netzwerkinformationen werden ermittelt.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-114">Step 1: Gathering Network Information</span></span>

1. <span data-ttu-id="0bc0b-115">Starten-Gerät mit WLAN-Dongle angeschlossen, Ethernet-Kabel angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-115">Boot up device with Wi-Fi dongle plugged in, Ethernet cable plugged in.</span></span>
2. <span data-ttu-id="0bc0b-116">Starten Sie SoftAP, über das IoT Core-Gerät.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-116">Start SoftAP from the IoT Core device.</span></span>

   <span data-ttu-id="0bc0b-117">Standardmäßig bereitgestellten Microsoft Images starten eine IoT-Onboarding-Anwendung, die eine SoftAP setup wird, wenn die Wi-Fi-Radio ist in der Lage, und kein WLAN-Profil hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-117">By default, the Microsoft provided images start an IoT Onboarding application that will setup a SoftAP if Wi-Fi radio is capable and no WLAN profile has been added.</span></span> <span data-ttu-id="0bc0b-118">SoftAP UWP-Anwendungen können verwenden Sie zum Starten der [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span><span class="sxs-lookup"><span data-stu-id="0bc0b-118">To start SoftAP, UWP applications can use the [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span></span> <span data-ttu-id="0bc0b-119">Der Quellcode für die IoT-Onboarding-Anwendung kann auf GitHub werden [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span><span class="sxs-lookup"><span data-stu-id="0bc0b-119">The source code for the IoT Onboarding application can be on GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span></span>

   <span data-ttu-id="0bc0b-120">Notieren Sie die SSID des Netzwerks SoftAP.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-120">Record the SSID of the SoftAP network.</span></span> <span data-ttu-id="0bc0b-121">Sie benötigen diese später, um die Verbindung mit Ihrem IoT Core-Gerät über WLAN.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-121">You will need it later to connect to your IoT Core device via Wi-Fi.</span></span> <span data-ttu-id="0bc0b-122">Für IoT-Onboarding-Anwendung die SSID beginnt mit "AJ\_SoftAPSsid\_" und kann geändert werden, in der Anwendungskonfiguration [Datei](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span><span class="sxs-lookup"><span data-stu-id="0bc0b-122">For IoT Onboarding application the SSID will start with "AJ\_SoftAPSsid\_" and can be changed in application's configuration [file](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span></span>

3. <span data-ttu-id="0bc0b-123">Herstellen einer Remoteverbindung mit dem Gerät IoT Core [über ssh](ssh.md).</span><span class="sxs-lookup"><span data-stu-id="0bc0b-123">Remotely connect to the IoT Core device [using ssh](ssh.md).</span></span>
4. <span data-ttu-id="0bc0b-124">Sammeln Sie Informationen zu-Gerät-Netzwerke durch Suchen der Netzwerk-Gerät-Indizes und eine Beschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-124">Collect information about device networks by finding network device indexes and descriptions.</span></span> <span data-ttu-id="0bc0b-125">Dies ist erforderlich, um das Netzwerk so Bridge zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-125">This is needed to declare which networks to bridge.</span></span>

   <span data-ttu-id="0bc0b-126">Führen Sie auf dem Gerät **weiterleiten Drucken** und Sammeln Sie die folgenden Daten:</span><span class="sxs-lookup"><span data-stu-id="0bc0b-126">On device, run **route print** and collect the following data:</span></span>

   * <span data-ttu-id="0bc0b-127">Datensatz öffentlichen Netzwerk Schnittstellenindex für die Ethernet.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-127">Record PUBLIC Interface network index for the Ethernet.</span></span>
   * <span data-ttu-id="0bc0b-128">Datensatz PRIVATE Schnittstelle für den network Index für die SoftAP (z.B.) "Microsoft Wi-Fi Direct virtuelle Adapter #2").</span><span class="sxs-lookup"><span data-stu-id="0bc0b-128">Record PRIVATE Interface network index for the SoftAP (e.g. “Microsoft Wi-Fi Direct Virtual Adapter #2”).</span></span>

   <span data-ttu-id="0bc0b-129">Beispielsweise ist die SoftAP über Schnittstellenindex 5 adapterbeschreibung "Microsoft Wi-Fi Direct virtuellen Adapter #2" verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-129">For example, the SoftAP is exposed through interface index 5, adapter description “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span>

   ![Route – print](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   <span data-ttu-id="0bc0b-131">Führen Sie auf dem Gerät **Ipconfig/all** und Sammeln Sie die folgenden Daten:</span><span class="sxs-lookup"><span data-stu-id="0bc0b-131">On device, run **ipconfig /all** and collect the following data:</span></span>
    
   * <span data-ttu-id="0bc0b-132">Die Namen der Datensatz PRIVATE Schnittstelle des Netzwerkadapters für die SoftAP</span><span class="sxs-lookup"><span data-stu-id="0bc0b-132">Record PRIVATE Interface network adapter name for the SoftAP</span></span>

   <span data-ttu-id="0bc0b-133">Z. B., "Ipconfig/all" sucht nach den bestimmten Adapter, die mit dem Namen "lokale Area Connection \* 3", die eine Beschreibung des "Microsoft Wi-Fi Direct virtuellen Adapter #2" aufweist.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-133">For example, running "ipconfig /all" finds the specific adapter named “Local Area Connection\* 3” that has a description of “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span> <span data-ttu-id="0bc0b-134">Verwenden Sie diese Methode, um manuell zu finden, dass der Name des Adapters aus der Beschreibung im "Route print" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-134">Use this method to manually find Adapter Name from the Description returned in “route print”.</span></span>

   ![Alle ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a><span data-ttu-id="0bc0b-136">Schritt 2: Skripterstellung Internet Connection Sharing-trigger</span><span class="sxs-lookup"><span data-stu-id="0bc0b-136">Step 2: Scripting Internet Connection Sharing trigger</span></span>

<span data-ttu-id="0bc0b-137">Starten die gemeinsame Nutzung der Internetverbindung zwischen zwei Netzwerken, erfordert die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="0bc0b-137">Starting Internet Connection Sharing between two networks requires the following steps:</span></span>

* <span data-ttu-id="0bc0b-138">Legen Sie die Registrierungsschlüssel Bridge Private (SoftAP) und Netzwerkschnittstellen, öffentliche (Ethernet) festlegen.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-138">Set registry keys to set private (SoftAP) and public (Ethernet) network interfaces to bridge.</span></span>
* <span data-ttu-id="0bc0b-139">Legen Sie geeignete Firewallregeln.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-139">Set appropriate firewall rules.</span></span>
* <span data-ttu-id="0bc0b-140">DHCP in der privaten Schnittstelle wird deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-140">Turns off DHCP on private interface.</span></span>
* <span data-ttu-id="0bc0b-141">Legt die statische IP-Adresse für die private Schnittstelle fest.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-141">Sets static IP address on private interface.</span></span>
* <span data-ttu-id="0bc0b-142">SharedAccess-Dienst gestartet.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-142">Starts SharedAccess service.</span></span>
* <span data-ttu-id="0bc0b-143">Sendet Befehlscode "129" SharedAccess-Dienst.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-143">Sends command code “129” to SharedAccess service.</span></span>


#### <a name="create-a-script-to-automate-the-ics-settings"></a><span data-ttu-id="0bc0b-144">Erstellen eines Skripts zum Automatisieren der ICS-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0bc0b-144">Create a script to automate the ICS settings</span></span>

<span data-ttu-id="0bc0b-145">Unten ist ein Beispiel des Skripts und Code zum Automatisieren der, die obigen Schritte in der Startsequenz Gerät integriert werden.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-145">Below is an example of a scripts and code to automate the steps listed above that can be integrated into the device startup sequence.</span></span> <span data-ttu-id="0bc0b-146">Erstellen einer Skriptdatei (z. B. **ConfigureICS.cmd**) mit dem folgenden Inhalt:</span><span class="sxs-lookup"><span data-stu-id="0bc0b-146">Create a script file (e.g. **ConfigureICS.cmd**) with the following content:</span></span>

```
echo off

set START_OR_STOP=%1
set PUBLIC_INDEX=%2
set PRIVATE_INDEX=%3
set PRIVATE_INTERFACE_NAME=%4

if not defined PRIVATE_INTERFACE_NAME (
  goto usage
)

if "%START_OR_STOP%"=="start" (

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d %PRIVATE_INDEX%
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d %PUBLIC_INDEX%

  REM Set the firewall rules to allow DHCP to work
  netsh advfirewall firewall add rule name=\"AllowPort67In\" protocol=UDP dir=in localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68In\" protocol=UDP dir=in localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort67Out\" protocol=UDP dir=out localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68Out\" protocol=UDP dir=out localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53Out\" protocol=UDP dir=out localport=53 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53In\" protocol=UDP dir=in localport=53 action=allow

  REM Turn off DHCP and set static IP for private interface
  netsh interface ip set address %4 static 192.168.137.1

  REM Start sharing
  call SharedAccessUtility.exe start

) else if "%START_OR_STOP%"=="stop" (

  REM Stop sharing
  call SharedAccessUtility.exe stop

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d 0
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d 0

  REM Clear the firewall rules
  netsh advfirewall firewall delete rule name="AllowPort67In"
  netsh advfirewall firewall delete rule name="AllowPort68In"
  netsh advfirewall firewall delete rule name="AllowPort67Out"
  netsh advfirewall firewall delete rule name="AllowPort68Out"
  netsh advfirewall firewall delete rule name="AllowPort53Out"
  netsh advfirewall firewall delete rule name="AllowPort53In"

  REM Reenable DHCP for private interface
  netsh interface ip set address %4 dhcp

) else (
  goto usage
)

goto eof

:usage
ECHO USAGE: %0 [start ^| stop] [public interface index] [private interface index] [private interface name]
ECHO e.g. %0 start 1 2 "Ethernet"

:eof
```

<span data-ttu-id="0bc0b-147">Dieses Skript tun alles, was aber SharedAccess-Dienst starten/beenden, und sendet keine Dienstbefehl.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-147">This script will do everything but start/stop SharedAccess service, and does not send service command.</span></span> <span data-ttu-id="0bc0b-148">Für diese Aufgaben, die sie zum SharedAccessUtility.exe aufruft, die erstellt werden muss.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-148">For those tasks it calls to SharedAccessUtility.exe, which needs to be created.</span></span>

#### <a name="build-the-sharedaccessutility-application"></a><span data-ttu-id="0bc0b-149">Erstellen Sie die Anwendung SharedAccessUtility</span><span class="sxs-lookup"><span data-stu-id="0bc0b-149">Build the SharedAccessUtility application</span></span>
<span data-ttu-id="0bc0b-150">In Visual Studio mit [Windows IoT Core-Projektvorlagen Erweiterungen](https://go.microsoft.com/fwlink/?linkid=847472) installiert haben, erstellen Sie ein neues "Leere Windows IoT Core-Konsolenanwendung" Visual C++ Projekt, mit dem Namen **SharedAccessUtility**.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-150">In Visual Studio with [Windows IoT Core Project Templates extensions](https://go.microsoft.com/fwlink/?linkid=847472) installed, create a new “Blank Windows IoT Core Console Application” Visual C++ project, named **SharedAccessUtility**.</span></span>

![Neue Visual Studio-Projekts](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

<span data-ttu-id="0bc0b-152">Ersetzen Sie Inhalt von ConsoleApplication.cpp, durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="0bc0b-152">Replace contents of ConsoleApplication.cpp with the following code:</span></span>

```C++
#include "pch.h"
#include <ws2tcpip.h>
#include <iphlpapi.h>
#include <mstcpip.h>
#include <stdio.h>

#define SHARED_ACCESS_NAME L"SharedAccess"
#define START_SHARING_CONTROL 129

DWORD StartSharedAccessService(SC_HANDLE *phScm, SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    // open a handle to SCM
    *phScm = OpenSCManager(NULL, NULL, SC_MANAGER_CONNECT);
    if (*phScm == NULL)
    {
        dwError = GetLastError();
        printf("\nOpenSCManager failed; error = %d", dwError);
    }
    else
    {
        // open a handle to the service
        *phSvc = OpenService(*phScm, SHARED_ACCESS_NAME, SERVICE_START | SERVICE_QUERY_STATUS | SERVICE_QUERY_CONFIG | SERVICE_STOP | SERVICE_USER_DEFINED_CONTROL);
        if (*phSvc == NULL)
        {
            dwError = GetLastError();
            printf("\nOpenService failed; error = %d", dwError);
        }
        else
        {
            if (!StartService(*phSvc, 0, NULL))
            {
                dwError = GetLastError();
                if (dwError != ERROR_SERVICE_ALREADY_RUNNING)
                {
                    printf("\nStartService failed; error = %d", dwError);
                }
                else
                {
                    dwError = ERROR_SUCCESS;
                    printf("\nService already running.");
                }
            }

            if (dwError == ERROR_SUCCESS)
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_RUNNING)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to start.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_RUNNING)
                            {
                                printf("\nService is running.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                                {
                                    printf("\nService could not run.");
                                    // it is, so break out
                                    dwError = ERROR_SERVICE_NOT_ACTIVE;
                                    break;
                                }
                            }
                        }
                        else
                        {
                            printf("\nWaiting more time.");
                        }
                    }
                }
            }
        }
    }

    if (dwError == ERROR_SUCCESS) //service is running
    {
        if (!ControlService(*phSvc, START_SHARING_CONTROL, &svcStatus))
        {
            dwError = GetLastError();
            printf("\nControl service for start sharing failure, %d", dwError);
        }
        else
        {
            printf("\nSharing started");
        }
    }

    // Service cleanup done at the main.
    return dwError;
}


DWORD StopSharedAccessService(SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    if (!QueryServiceStatus(*phSvc, &svcStatus))
    {
        dwError = GetLastError();
        printf("\nFailed to query sharedaccess, %d", dwError);
    }
    else
    {
        if (svcStatus.dwCurrentState != SERVICE_STOPPED)
        {
            if (ControlService(*phSvc, SERVICE_CONTROL_STOP, &svcStatus))
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_STOPPED)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to stop.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                            {
                                printf("\nService stopped.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                printf("\nWaiting more time.");
                            }
                        }
                    }
                }
            }
        }
    }
    return dwError;
}

void ShowUsage()
{
    printf("Usage: SharedAccessUtility.exe start | stop\n"
        "Setup: Make sure the public and private interfaces are up and running and that the SharedAccess registry keys are set.");
}

int __cdecl
main(
    __in int argc,
    __in_ecount(argc) LPSTR argv[]
    )
{
    SC_HANDLE hScm = NULL;
    SC_HANDLE hSvc = NULL;
    DWORD dwError = NO_ERROR;
    bool startSharing = true;

    if (argc < 2)
    {
        ShowUsage();
        return -1;
    }
    else
    {
        if (strcmp(argv[1], "start") == 0 || strcmp(argv[1], "/start") == 0)
        {
            startSharing = true;
        }
        else if (strcmp(argv[1], "stop") == 0 || strcmp(argv[1], "/stop") == 0)
        {
            startSharing = false;
        }
        else
        {
            ShowUsage();
            return -1;
        }
    }

    dwError = startSharing ? StartSharedAccessService(&hScm, &hSvc) : StopSharedAccessService(&hSvc);

    // Cleanup
    if (hSvc != NULL)
    {
        CloseServiceHandle(hSvc);
        hSvc = NULL;
    }
    if (hScm != NULL)
    {
        CloseServiceHandle(hScm);
        hScm = NULL;
    }
    return 0;
}
```

<span data-ttu-id="0bc0b-153">Erstellen Sie für die Zielarchitektur, z. B. Version X86 und suchen Sie nach Ausgabe **SharedAccessUtility.exe**</span><span class="sxs-lookup"><span data-stu-id="0bc0b-153">Build for target architecture, e.g. Release x86, and locate output **SharedAccessUtility.exe**</span></span>

### <a name="step-3-starting-internet-connection-sharing"></a><span data-ttu-id="0bc0b-154">Schritt 3: Starten Internet Connection Sharing</span><span class="sxs-lookup"><span data-stu-id="0bc0b-154">Step 3: Starting Internet Connection Sharing</span></span>

1. <span data-ttu-id="0bc0b-155">Kopie **ConfigICS.cmd** Skript in Schritt2 erstellte auf dem Gerät an einem Ort, z. B. um</span><span class="sxs-lookup"><span data-stu-id="0bc0b-155">Copy **ConfigICS.cmd** script created in Step 2 to the device in some location, e.g. to</span></span> `C:\test\`
2. <span data-ttu-id="0bc0b-156">Kopie **SharedAccessUtility.exe** in Schritt2 erstellte auf dem Gerät am gleichen Speicherort, z. B. `C:\test`\\</span><span class="sxs-lookup"><span data-stu-id="0bc0b-156">Copy **SharedAccessUtility.exe** created in Step 2 to the device in the same location, e.g. `C:\test`\\</span></span>
3. <span data-ttu-id="0bc0b-157">Führen Sie auf dem Gerät **C:\test\ConfigureICS.cmd Start [öffentliche Index] [private Index] [Adaptername des private-]** In diesem Beispiel wäre dies <strong>C:\test\ConfigureICS.cmd starten 4 5 "Lokale Area Connection \* 3"</strong></span><span class="sxs-lookup"><span data-stu-id="0bc0b-157">On the device, run **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** In this example, this would mean <strong>C:\test\ConfigureICS.cmd start 4 5 "Local Area Connection\* 3"</strong></span></span>

<span data-ttu-id="0bc0b-158">An diesem Punkt hat gemeinsame Nutzung der Internetverbindung von das Gerät sogar für alle Clients, die Verbindung des Geräts angekündigte SSID aktiviert.</span><span class="sxs-lookup"><span data-stu-id="0bc0b-158">At this point the device has enabled Internet Connection Sharing for any client connected to the device’s advertised SSID.</span></span>
