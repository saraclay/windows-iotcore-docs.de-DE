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
# <a name="communicating-with-localhost-loopback"></a>Kommunikation mit "localhost" (Loopback)

Unter Windows IoT Core müssen Sie eine TCP/IP-Verbindung zwischen 2 auf demselben Gerät ausgeführten Prozesse erstellen möchten, und eine davon ist eine UWP-app Sie "localhost" Loopback aktivieren.

## <a name="loopback-and-the-debugger"></a>Loopback und der debugger 
In der Standardeinstellung aktiviert ausgeführt wird, unter dem Visual Studio-Debugger ausgehende Loopback automatisch für diese Debugsitzung nur.  Es sollte keine nichts weiter tun, solange die Loopback-Kontrollkästchen in den Debuggereinstellungen für Ihr Startprojekt aktiviert ist.  Wenn Sie ein socketlisteners implementieren möchten, müssen Sie "localhost" Loopback für eingehende Verbindungen (siehe unten) aktivieren.
 
## <a name="enabling-the-inbound-loopback-policy"></a>Aktivieren der eingehenden Loopbackrichtlinie
Die "localhost" eingehende Loopbackrichtlinie für **Windows IoT Core** muss aktiviert sein, für die UWP-apps, die Server zu implementieren.  Diese Richtlinie wird durch den folgenden Registrierungsschlüssel gesteuert:

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

Diesen Registrierungsschlüsselwert IoTInboundLoopbackPolicy muss auf DWORD: 00000001 festgelegt werden, aktivieren zu können. Wenn Sie den Registrierungswert IoTInboundLoopbackPolicy ändern, müssen Sie für die Änderung wirksam wird neu starten.  Die Loopback-Richtlinie von "localhost" standardmäßig aktiviert werden sollte, auf **Windows IoT Core** 

So überprüfen, dass der Wert festlegen, führen Sie den folgenden Befehl auf dem **Windows IoT Core** Gerät:

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

So aktivieren Sie die Richtlinie, führen Sie den folgenden Befehl auf dem **Windows IoT Core** Gerät:

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a>Aktivieren die Loopbacks für eine UWP-Anwendung
Bevor Sie die Loopbacks für eine Anwendung aktivieren können, benötigen Sie den paketfamiliennamen.  Sie finden den paketfamiliennamen für eine installierte Anwendung mit **Iotstartup Liste**.  Wenn die **Iotstartup Liste** Eintrag für die Anwendung ist IoTCoreDefaultApp\_1w720vyc4ccym! Klicken Sie dann den paketfamiliennamen-App ist IoTCoreDefaultApp\_1w720vyc4ccym

Loopback-Verbindungen von Clients zu `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.  CheckNetIsolation.exe konfiguriert die Loopbacks für die Anwendung, und beenden. Dadurch wird die Anwendung zum Herstellen ausgehende Verbindungen zu einem Server aktiviert.

Beispiel: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

So aktivieren Sie eine Server-Anwendung zum Empfangen von eingehenden Verbindungen verwenden `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`. Im Gegensatz zur Konfiguration der ausgehenden Verbindung müssen eingehende Verbindungen CheckNetIsolation.exe auszuführende fortlaufend auf, während die Serveranwendung Verbindungen empfangen wird.  Dies ist ein neuer ist als 10.0.14393 Betriebssystembuild erforderlich.

Beispiel: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

Die beste Möglichkeit, CheckNetIsolation.exe beim Start automatisch ausgeführt wird schtasks.exe verwendet: `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

Beim Neustarten werden Sie überprüfen, checknetisolation.exe mit tlist.exe ausgeführt wird oder [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)
