---
title: Bereitstellen einer App mit Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie eine app mithilfe der Visual Studio Remotedebuggen-Funktion bereitstellen.
keywords: Windows Iot, visual Studio, app-Bereitstellung, Remotedebuggen
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513241"
---
# <a name="deploying-an-app-with-visual-studio"></a>Bereitstellen einer App mit Visual Studio

Bereitstellen und Debuggen Ihrer Anwendung ist ganz einfach mit Visual Studio. Wir verwenden die **Remotedebuggen** Feature zum Bereitstellen der app auf dem lokal verbundenen Windows 10 IoT Core-Gerät. 

> [!NOTE]
> Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.

> [!NOTE]
> Um Remotedebuggen zu verwenden, muss Ihre IoT Core-Geräts zunächst mit gleichen lokalen Netzwerk als Ihrem Entwicklungs-PC angeschlossen werden.  
>Finden Sie unter den [Herstellen einer Verbindung mit einem Gerät](../connect-your-device/SetupWiFi.md) Anweisungen.

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>Bereitstellen einer C# app auf Ihrem Windows 10 IoT Core-Gerät 
___

1. Legen Sie mit der Anwendung in Visual Studio geöffnet ist die Architektur in der Dropdownliste der Symbolleiste aus. Wenn Sie für den Minnowboard maximalen erstellen, wählen Sie `x86`. Wenn Sie Raspberry Pi 2-oder Raspberry Pi 3 mit der Dragonboard erstellen, wählen Sie `ARM`.

2. Klicken Sie anschließend in der Visual Studio-Symbolleiste auf die `Local Machine` Dropdownliste, und wählen Sie `Remote Machine`.

![Der Remotecomputer in Visual Studio](../media/AppDeployment/cs-remote-machine-debugging.png)

3. Visual Studio bietet nun die **Remoteverbindungen** Dialogfeld. Wenn Sie zuvor [PowerShell](../connect-your-device/PowerShell.md) um einen eindeutigen Namen für Ihr Gerät festzulegen, können Sie ihn hier eingeben (in diesem Beispiel verwenden wir **mein Gerät**). Verwenden Sie andernfalls die IP-Adresse Ihres Windows IoT Core-Geräts.

4. Wählen Sie nach dem Eingeben der Servername/IP-Geräts `Universal (Unencrypted Protocol)` Authentifizierungsmodus, klicken Sie dann auf **wählen**. 

![Universelle Authentifizierung](../media/AppDeployment/cs-remote-connections.png)

Sie überprüfen können, oder ändern Sie diese Werte durch Navigieren zu den Projekteigenschaften (Wählen Sie **Eigenschaften** im Projektmappen-Explorer) auswählen und die `Debug` links auf die Registerkarte:

![Registerkarte „Debuggen“](../media/AppDeployment/cs-debug-project-properties.png)

5. Jetzt sind wir bereit für die Bereitstellung. Drücken Sie einfach F5 (oder die Option Debuggen \| Debuggen starten) zum Starten des Debuggings unsere app. Daraufhin sollte die app auf dem Bildschirm des Geräts kommen.

6. Nach der Bereitstellung können Sie festlegen, Haltepunkte, finden Sie unter Variablenwerte usw. Drücken Sie die app auf die Schaltfläche "Debugging beenden" beendet (oder die Option Debuggen \| Debuggen beenden).

7. Ändern die Konfigurationen-Dropdownliste in Visual Studio-Symbolleiste aus, nach dem erfolgreichen Bereitstellen und Debuggen Ihrer UWP-Anwendung, erstellen eine Releaseversion - `Debug` zu `Release`.  Sie können jetzt erstellen und Bereitstellen Ihrer app auf Ihrem Gerät durch Auswählen von Build \| Projektmappe neu erstellen "und" Build \| Projektmappe bereitstellen.

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>Bereitstellen einer C++ app auf Ihrem Windows 10 IoT Core-Gerät

1. Legen Sie mit der Anwendung in Visual Studio geöffnet ist die Architektur in der Dropdownliste der Symbolleiste aus. Wenn Sie für den Minnowboard maximalen erstellen, wählen Sie `86`. Wenn Sie für die Raspberry Pi 2- oder 3 erstellen, wählen Sie `ARM`.

2. Klicken Sie anschließend in der Visual Studio-Symbolleiste auf die `Local Machine` Dropdownliste, und wählen Sie `Remote Machine`

![Lokalen Computer mit Visual Studio](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. Als Nächstes der rechten Maustaste auf das Projekt in der **Projektmappen-Explorer** Bereich. Wählen Sie **Eigenschaften** aus. 

![Eigenschaften in Visual Studio](../media/AppDeployment/cpp-project-properties.png)

4. Klicken Sie unter **Konfigurationseigenschaften -> Debugging**, ändern Sie die folgenden Felder:

    * **Computername**: Wenn Sie zuvor [PowerShell](../connect-your-device/PowerShell.md) um einen eindeutigen Namen für Ihr Gerät festzulegen, können Sie ihn hier eingeben (in diesem Beispiel verwenden wir **mein Gerät**). Verwenden Sie andernfalls die IP-Adresse Ihres Windows IoT Core-Geräts.
    * **Authentifizierungsmodus**: Legen Sie auf **universell (unverschlüsseltes Protokoll)**
    
![Universelle Authentifizierung](../media/AppDeployment/cpp-debug-project-properties.png)

5. Jetzt sind wir bereit für die Bereitstellung. Drücken Sie einfach F5 (oder die Option Debuggen \| Debuggen starten) zum Starten des Debuggings unsere app. Daraufhin sollte die app im Windows IoT Core Gerätebildschirm kommen.

6. Nach der Bereitstellung können Sie festlegen, Haltepunkte, finden Sie unter Variablenwerte usw. Drücken Sie auf die Schaltfläche "Debugging beenden", um die app zu beenden (oder die Option Debuggen \| Debuggen beenden).

7. Erfolgreich bereitgestellt und Debuggen Ihrer UWP-Anwendung, erstellen Sie eine Releaseversion: ändern die Konfigurationen-Dropdownliste in Visual Studio-Symbolleiste von `Debug` zu `Release`.  Sie können jetzt erstellen und Bereitstellen Ihrer app auf Ihrem Gerät durch Auswählen von Build \| Projektmappe neu erstellen "und" Build \| Projektmappe bereitstellen.

