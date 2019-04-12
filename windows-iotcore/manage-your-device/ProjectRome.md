---
title: Verwenden von Projekt "ROME" mit Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: Erfahren Sie, und verstehen Sie die Schritte in Ihrem Windows-IoT-Gerät auf den Markt zu.
keywords: Windows 10 IoT Core, Projekt "ROME", remote-Geräte
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513897"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>Verwenden von Projekt "ROME" mit Windows 10 IoT Core 
 
[Projekt "ROME"](https://developer.microsoft.com/en-us/windows/project-rome) können Sie Remote mit Geräten mit Windows 10 IoT Core unter Verwendung des RemoteSystems und AppServiceProvider-APIs arbeiten. 
 
In diesem Artikel Gehe wir durch die Schritte zum Ermitteln,-Steuerelement, und eine Verbindung mit Geräten mit Windows 10 IoT Core mit Projekt "ROME".  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>Ermittlung von IoT-Core-Geräte mit dem RemoteSystem-APIs 
 
_Setup:_
* Führen Sie das RemoteSystems-Beispiel auf einem Desktop, während Sie bei Ihrem Microsoft-Konto angemeldet.  
* Keine App auf IoT Core ausgeführt wird melden Sie sich bei Ihrem Microsoft-Konto dazu auf Cortana-Anmeldung. 
 
_Schritte:_
1. Ausführen des RemoteSystems-Beispiels auf Ihrem desktop 
2. Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen" 

![Zur Suche nach Systemen](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>IoT Core-Geräte mit RemoteSystems.LaunchUri steuern 
 
_Setup:_
* Führen Sie die [RemoteSystems Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) auf etwas Desktop [bei Ihrem Microsoft-Konto angemeldet](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).
* Keine App auf IoT Core ausgeführt wird melden Sie sich bei Ihrem Microsoft-Konto dazu auf Cortana-Anmeldung. 
 
_Schritte:_
1. Aktivieren Sie die IoT Core-VM mit Cortana und Anmeldung bei Ihrem Microsoft-Konto von cortana erhalten. 
2. Führen Sie das Beispiel RemoteSystems, auf dem Desktop. 
3. Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen". 
4. Klicken Sie unter "(2) Start-URI" Wählen Sie das IoT Core-Gerät, das Cortana ausgeführt wird. 
5. Geben Sie diesen URI, und starten. 

![Starten des URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>Herstellen einer Verbindung mit dem App-Remotedienst auf IoT Core ausgeführt wird 
_Setup:_
* Führen Sie die [RemoteSystems Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) auf etwas Desktop [bei Ihrem Microsoft-Konto angemeldet](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement). 
* Stellen Sie sicher, damit die [AppServiceProvider-app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) bereitgestellt und auf mindestens ein Gerät von IoT Core ausgeführt wird. 
 
_Schritte:_
1. Aktivieren Sie auf der IoT Core-VM mit Cortana, und melden Sie sich bei Ihrem Microsoft-Konto von cortana erhalten. Die AppServiceProvider-app bereitstellen, einmal ausgeführt, und beenden sie Sie. 
2. Führen Sie das Beispiel RemoteSystems, auf dem Desktop. 
3. Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen". 
4. Unter"(3) starten App-Dienste" auswählen, die der IoT core-Gerät, das die AppServiceProvider-app bereitgestellt wurde und der zuvor ausgeführt wurde. 
5. Eine Zufallszahl zu generieren.  

![Starten der App-Dienste](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>Steuern von anderen Geräten und app-Dienste über ein Gerät IoT Core 

_Setup:_
* Führen Sie die [RemoteSystems Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) auf ein Gerät IoT Core bereitgestellten [bei Ihrem Microsoft-Konto angemeldet](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) aus der Cortana-app. 
* Haben Sie einem Desktopcomputer mit der [AppServiceProvider-app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) bereitgestellt, und dass sich mindestens einmal ausgeführt wurde. 
 
_Schritte:_
1. Ausführen des RemoteSystems-Beispiels. 
2. Klicken Sie unter "(1) Ermittlung" klicken Sie auf "Suche nach Systemen". 
3. Klicken Sie unter "(2) Start-URI" Wählen Sie die Desktop-Computer und starten. 
4. Klicken Sie unter "(3) starten App Services" Wählen Sie den desktop-Computer.  
 
> [!NOTE] 
> Beim ersten Versuch kann dies sehr lange dauern. Versuchen Sie es erneut für eine viel schnellere Antwort. 
 
### <a name="helpful-links"></a>Hilfreiche Links: 
* [Projekt "ROME" Dokumentation auf MSDN](https://developer.microsoft.com/en-us/windows/project-rome )
* [Verwenden von Projekt "ROME" für UWP](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
