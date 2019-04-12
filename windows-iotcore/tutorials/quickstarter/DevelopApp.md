---
title: Entwickeln einer app für Ihr Gerät
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: Erfahren Sie mehr über das Hinzufügen und Entwickeln von apps für Ihr Gerät
keywords: Windows 10 IoT Core, erste Schritte, Entwickeln von apps, apps
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513945"
---
# <a name="develop-an-app-for-your-device"></a>Entwickeln einer app für Ihr Gerät

> [!NOTE]
> Visual Studio generiert einen kryptischen Fehler bei der Bereitstellung in einer RS5 (oder Version RS4 mit OpenSSH aktiviert) IoT image, es sei denn, eine SDK, Version RS4 oder höher installiert ist, dass Visual Studio zugreifen können.

Nun, da Sie ein Gerät für die Arbeit mit ausgeführte Standard-app verfügen, sollten Sie Ihr Gerät auf die nächste Stufe zu nutzen, indem entwickeln und Bereitstellen einer app auf Ihrem Gerät. Bevor näher auf Beispiele, müssen Sie zum Herunterladen [Visual Studio 2017](https://www.visualstudio.com/downloads/) für die Anwendungsentwicklung.

Wenn Sie planen, verwenden Sie C++ für Ihre Projekte, beim Herunterladen von Visual Studio 2017, überprüfen Sie die Felder die gleiche Weise wie im folgenden Beispiel:

![Grundlegende Informationen für die C++ und Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

Wenn Sie im Hintergrund, Arduino verknüpfen oder konsolenanwendungen in Zukunft entwickeln möchten, sollten Sie auch Projektvorlagen aus Herunterladen der [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).


Es wird empfohlen, um mit einer app betriebsbereit zu machen, eine vorgeschlagene Starter-Beispiel unten ab. Aber wenn Sie zum Bereitstellen Ihrer eigenen app bereit sind, haben wir auch nützliche Links im Abschnitt nach bereitgestellt.

## <a name="suggested-starter-samples"></a>Vorgeschlagene Starter-Beispielen

* [Hello Blinky](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [IoT-Start-App-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [RPi Cognitive Service-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



Nach dem Bereitstellen Ihrer app - Herzlichen Glückwunsch, haben Sie diese Quickstarter wurde abgeschlossen. Weiter experimentieren oder, wenn man ein paar Ideen rund um die im Kopf, springenden sehen Sie sich unsere Dokumentation zu commercializing mit Windows 10 IoT. 

## <a name="app-development-resources"></a>Entwicklungsressourcen für Apps

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">Entwickeln von vordergrundanwendungen</a></p></td>
<td align="left"><p>Informationen Sie zu den verschiedenen Sprachen, die auf Windows 10 IoT Core als auch für die UWP unterstützt werden und nicht-UWP-app-Typen, die unterstützt werden.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Entwickeln von hintergrundanwendungen</a></p></td>
<td align="left"><p>Informationen Sie zu den verschiedenen Sprachen, die auf Windows 10 IoT Core als auch für die UWP unterstützt werden und nicht-UWP-app-Typen, die unterstützt werden.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Bereitstellen einer App mit Visual Studio</a></p></td>
<td align="left"><p>Erfahren Sie, wie Ihre anderen apps mit Visual Studio auf Ihrem Windows 10 IoT Core-Gerät bereitstellen.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Debuggen einer app mithilfe von Remote Console App Debuggen</a></p></td>
<td align="left"><p>Erfahren Sie, wie Sie Ihre apps mit Remote Console App Debuggen in Visual Studio zu debuggen.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Installieren der app auf Ihrem Windows 10 IoT Core-Gerät</a></p></td>
<td align="left"><p>Erfahren Sie, wie Sie Ihre app auf Ihrem Windows 10 IoT Core-Gerät zu installieren.</p></td>
</tr>

</tbody>
</table>
