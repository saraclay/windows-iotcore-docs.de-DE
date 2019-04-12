---
title: Verbinden Sie Ihre app in die cloud
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Ihre app in die Cloud zu verbinden.
keywords: Windows Iot, Cloud, Azure, Azure IoT Hub
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513353"
---
# <a name="connect-your-app-to-the-cloud"></a>Verbinden Sie Ihre app in die cloud

Diese schrittweise Anleitung können Sie machen Sie sich mit Windows 10 IoT Core, richten Sie Ihr Gerät aus, und Erstellen Ihrer ersten Anwendung, die mit Azure IoT Hub verbindet.

## <a name="step-1-prepare-your-device"></a>Schritt 1: Bereiten Sie Ihr Gerät vor.

Anweisungen finden Sie Anleitungen zum Vorbereiten Ihres Geräts auf die [Seite für erste Schritte](https://developer.microsoft.com/en-us/windows/iot/getstarted) stellen Sie sicher, dass Sie [die Trusted Platform Module auf Ihrem Gerät bereitstellen](../connect-to-cloud/ConnectDeviceToCloud.md)

## <a name="step-2-install-visual-studio-2017-and-tools"></a>Schritt 2: Installieren von Visual Studio 2017 und tools

Installieren Sie [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271). Sie können eine beliebige Edition von Visual Studio, einschließlich der kostenlosen communityedition installieren.

Achten Sie darauf, wählen Sie die **Entwicklungstools für universelle Windows-App**, die Komponente, die für das Schreiben von Windows 10-apps erforderlich sind:

![Entwicklungstools für universelle Windows-Apps](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>Schritt 3: Installieren Sie die verbundenen Dienste für Azure IoT Hub

Die verbundene Dienste für Azure IoT Hub Visual Studio-Erweiterung können Sie eine Verbindung herstellen und Interaktion mit Azure IoT Hub in weniger als einer Minute.

Sie können die Erweiterung von installieren die [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>Schritt 4: Erstellen Sie eine Visual Studio-UWP-Projektmappe

Zum Erstellen einer UWP-Lösung in Visual Studio auf die **Datei** Menü klicken Sie auf **neu** dann **Projekt**:

![Erstellung eines neuen Projekts](../media/ConnectAppToCloud/new_project_menu.png)

Wählen Sie im Dialogfeld für neue Projekte, die angezeigt wird, **leere App (Universelles Windows) Visual C#** . Geben Sie Ihrem Projekt einen Namen (e-Mail-Domäne(n) **MyFirstIoTCoreApp**):

![Dialogfeld "neue Projektmappe"](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>Verwenden Sie das verbundene Dienste für Azure IoT Hub für die Verbindung mit Azure IoT Hub

Befolgen Sie die Anweisungen aus den [Tool für verbundene Dienste](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) um Ihr Projekt mit Azure IoT Hub zu verbinden. Das Tool generiert zwei Funktionen, `SendDeviceToCloudMessageAsync` und `ReceiveCloudToDeviceMessageAsync` , die Sie an einer beliebigen Stelle in Ihrer app aufrufen können. Sie können diese Funktionen ändern, nach Bedarf.  

