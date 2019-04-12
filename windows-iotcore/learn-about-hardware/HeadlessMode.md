---
title: Spitzen und monitorlose-Geräte
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Windows IoT Core Spitzen oder monitorlosen Modus für die Geräte zu konfigurieren.
keywords: Windows Iot, Bildschirme, Spitzen, monitorlose UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513298"
---
# <a name="headed-and-headless-devices"></a>Spitzen und monitorlose-Geräte

Windows 10 IoT Core kann konfiguriert werden, entweder *Spitzen* oder *monitorlose* Modus. 

## <a name="headed-mode"></a>Modus
Modus wird durch das Vorhandensein der Benutzeroberfläche definiert. In *Spitzen* Modus eine einzelne app für die Benutzeroberfläche beim Systemstart gestartet, und es kann außerdem werden 0 oder mehr "Hintergrund-Apps" (StartupTasks). 

## <a name="headless-mode"></a>Monitorlosen Modus
Monitorlosen Modus besitzt keine Benutzeroberfläche.  Geräte, die Funktionen der Benutzeroberfläche nicht benötigen, können so festgelegt werden *monitorlose* Modus. Der UI-Stapel ist deaktiviert, und UI-apps nicht gestartet. Dies reduziert die Menge an Systemressourcen verwendet. Wenn Sie einen Monitor an Ihr Gerät anfügen, wird der Bildschirm schwarze sein.

> [!NOTE]
> Wenn Sie Ihr Gerät in monitorlosen Modus zu versetzen, können Sie die Windows 10 IoT Core Dashboard-Anwendung, unten, um die IP-Adresse finden verwenden.

## <a name="changing-the-mode"></a>Modus ändern
Sie können den Spitzen monitorlose/Status Ihres Geräts aus einer Windows PowerShell-Sitzung oder einer SSH-Sitzung ändern. Weitere Informationen zu PowerShell finden Sie unter den [PowerShell IoT Core](../connect-your-device/PowerShell.md) Seite. Weitere Informationen zu SSH finden Sie unter den [SSH für IoT Core](../connect-your-device/SSH.md) Seite.

* Um den aktuellen Status des Geräts anzuzeigen, verwenden Sie die `setbootoption` Hilfsprogramm:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* Um den Status Ihres Geräts monitorlosen Modus zu ändern, verwenden die `setbootoption` -Hilfsprogramm mit der `headless` Arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* Verwenden Sie zum Ändern der Status des Geräts zu, die Spitzen im Aktivierungsmodus der `setbootoption` -Hilfsprogramm mit der `headed` Arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>Suchen Ihr Gerät monitorlose

Ein IoT Core-Geräts, das im monitorlosen Modus kann ermittelt werden, mithilfe der **Windows 10 IoT Core Dashboard** Anwendung.  Informationen zum Herunterladen der IoT-Dashboard finden Sie unter den [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) Seite.
Bei der Ausführung wird die Anwendung wartet auf Ping-Nachrichten von jedem IoT Core-Geräten im lokalen Netzwerk und zeigt die Geräteinformationen, z. B. den Namen, IP-Adresse und mehr.

![Windows 10 IoT Core Dashboard](../media/HeadlessMode/selectDevice.png)
