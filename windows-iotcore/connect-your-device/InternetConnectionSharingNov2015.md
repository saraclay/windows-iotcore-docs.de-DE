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
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a>Gemeinsame Nutzung der Tutorial (Release vom November 2015)

Dieses Dokument beschreibt die Schritte zum Aktivieren (Internet Connection Sharing, ICS) auf einem Gerät mit Windows 10 IoT Core Release von November 2015. Das Ziel ist eine Internetverbindung zwischen einer Software Wi-Fi-Zugriffspunkt (SoftAP) und ein Ethernet-Adapter freigeben. Bei Verwendung der Anniversary Version von Windows 10 IoT Core finden Sie in der [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).

## <a name="prerequisites"></a>Vorraussetzungen

* Gerät mit Windows 10 IoT Core Release von November 2015.
* Wi-Fi-USB-Geräte, die eine SoftAP ab. Finden Sie in der [Hardware-Kompatibilitätsliste](../learn-about-hardware/HardwareCompatList.md) Wi-Fi-USB-Geräte unterstützt.
* Ethernet-Verbindung mit Internetzugriff.


## <a name="setup"></a>Setup

### <a name="step-1-gathering-network-information"></a>Schritt 1: Netzwerkinformationen werden ermittelt.

1. Starten-Gerät mit WLAN-Dongle angeschlossen, Ethernet-Kabel angeschlossen.
2. Starten Sie SoftAP, über das IoT Core-Gerät.

   Standardmäßig bereitgestellten Microsoft Images starten eine IoT-Onboarding-Anwendung, die eine SoftAP setup wird, wenn die Wi-Fi-Radio ist in der Lage, und kein WLAN-Profil hinzugefügt wurde. SoftAP UWP-Anwendungen können verwenden Sie zum Starten der [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx). Der Quellcode für die IoT-Onboarding-Anwendung kann auf GitHub werden [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).

   Notieren Sie die SSID des Netzwerks SoftAP. Sie benötigen diese später, um die Verbindung mit Ihrem IoT Core-Gerät über WLAN. Für IoT-Onboarding-Anwendung die SSID beginnt mit "AJ\_SoftAPSsid\_" und kann geändert werden, in der Anwendungskonfiguration [Datei](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).

3. Herstellen einer Remoteverbindung mit dem Gerät IoT Core [über ssh](ssh.md).
4. Sammeln Sie Informationen zu-Gerät-Netzwerke durch Suchen der Netzwerk-Gerät-Indizes und eine Beschreibung ein. Dies ist erforderlich, um das Netzwerk so Bridge zu deklarieren.

   Führen Sie auf dem Gerät **weiterleiten Drucken** und Sammeln Sie die folgenden Daten:

   * Datensatz öffentlichen Netzwerk Schnittstellenindex für die Ethernet.
   * Datensatz PRIVATE Schnittstelle für den network Index für die SoftAP (z.B.) "Microsoft Wi-Fi Direct virtuelle Adapter #2").

   Beispielsweise ist die SoftAP über Schnittstellenindex 5 adapterbeschreibung "Microsoft Wi-Fi Direct virtuellen Adapter #2" verfügbar gemacht.

   ![Route – print](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   Führen Sie auf dem Gerät **Ipconfig/all** und Sammeln Sie die folgenden Daten:
    
   * Die Namen der Datensatz PRIVATE Schnittstelle des Netzwerkadapters für die SoftAP

   Z. B., "Ipconfig/all" sucht nach den bestimmten Adapter, die mit dem Namen "lokale Area Connection * 3", die eine Beschreibung des "Microsoft Wi-Fi Direct virtuellen Adapter #2" aufweist. Verwenden Sie diese Methode, um manuell zu finden, dass der Name des Adapters aus der Beschreibung im "Route print" zurückgegeben.

   ![Alle ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a>Schritt 2: Skripterstellung Internet Connection Sharing-trigger

Starten die gemeinsame Nutzung der Internetverbindung zwischen zwei Netzwerken, erfordert die folgenden Schritte aus:

* Legen Sie die Registrierungsschlüssel Bridge Private (SoftAP) und Netzwerkschnittstellen, öffentliche (Ethernet) festlegen.
* Legen Sie geeignete Firewallregeln.
* DHCP in der privaten Schnittstelle wird deaktiviert.
* Legt die statische IP-Adresse für die private Schnittstelle fest.
* SharedAccess-Dienst gestartet.
* Sendet Befehlscode "129" SharedAccess-Dienst.


#### <a name="create-a-script-to-automate-the-ics-settings"></a>Erstellen eines Skripts zum Automatisieren der ICS-Einstellungen

Unten ist ein Beispiel des Skripts und Code zum Automatisieren der, die obigen Schritte in der Startsequenz Gerät integriert werden. Erstellen einer Skriptdatei (z. B. **ConfigureICS.cmd**) mit dem folgenden Inhalt:

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

Dieses Skript tun alles, was aber SharedAccess-Dienst starten/beenden, und sendet keine Dienstbefehl. Für diese Aufgaben, die sie zum SharedAccessUtility.exe aufruft, die erstellt werden muss.

#### <a name="build-the-sharedaccessutility-application"></a>Erstellen Sie die Anwendung SharedAccessUtility
In Visual Studio mit [Windows IoT Core-Projektvorlagen Erweiterungen](https://go.microsoft.com/fwlink/?linkid=847472) installiert haben, erstellen Sie ein neues "Leere Windows IoT Core-Konsolenanwendung" Visual C++ Projekt, mit dem Namen **SharedAccessUtility**.

![Neue Visual Studio-Projekts](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

Ersetzen Sie Inhalt von ConsoleApplication.cpp, durch den folgenden Code:

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

Erstellen Sie für die Zielarchitektur, z. B. Version X86 und suchen Sie nach Ausgabe **SharedAccessUtility.exe**

### <a name="step-3-starting-internet-connection-sharing"></a>Schritt 3: Starten Internet Connection Sharing

1. Kopie **ConfigICS.cmd** Skript in Schritt2 erstellte auf dem Gerät an einem Ort, z. B. um `C:\test\`
2. Kopie **SharedAccessUtility.exe** in Schritt2 erstellte auf dem Gerät am gleichen Speicherort, z. B. `C:\test`\
3. Führen Sie auf dem Gerät **C:\test\ConfigureICS.cmd Start [öffentliche Index] [private Index] [Adaptername des private-]** In diesem Beispiel wäre dies <strong>C:\test\ConfigureICS.cmd starten 4 5 "Lokale Area Connection * 3"</strong>

An diesem Punkt hat gemeinsame Nutzung der Internetverbindung von das Gerät sogar für alle Clients, die Verbindung des Geräts angekündigte SSID aktiviert.
