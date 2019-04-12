---
title: Erstellen von Komponententests
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: Informationen Sie zu den Komponententests, die von IoT Core unterstützt werden.
keywords: Windows Iot, Komponententests, UWP
ms.openlocfilehash: 0a54ad7ffa3065353045f0e2f81306a1a1e0ac13
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513346"
---
# <a name="developing-unit-tests"></a>Entwicklung von Komponententests
Informationen Sie zu UWP-Komponententests wird unter Windows 10 IoT Core unterstützt.

## <a name="uwp-unit-tests"></a>UWP-Komponententests
___

Komponententests bieten wichtige Schutz und zusätzliche Validierung für app-Entwickler.  Visual Studio 15.6 zusätzliche Unterstützung für Windows 10 IoT Core in der neue Testplattform.  Durch diese neue Unterstützung ist es möglich, Komponententests für UWP-Funktionalität zu erstellen, die als Teil eines Continuous Integration-Builds oder direkt aus Visual Studio ausführen können.


### <a name="create-new-unit-test-project"></a>Neue Komponententestprojekt erstellen
___

1. Öffnen Sie Visual Studio

2. Erstellen Sie ein neues Komponententestprojekt ![installieren](../media/UnitTests/newproject.png)

3. Aktualisieren von UnitTest.cs zum Einbeziehen von Testcode
   ```C#
   namespace UnitTestProject1
   {
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            // test code here
        }
    }
   }
   ```


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a>Remote Ausführen von Komponententests für Windows 10 IoT Core-Geräts
___

1. Öffnen Sie Visual Studio Test-Explorer (Test > Windows > Test-Explorer).
 ![Test-Explorer](../media/UnitTests/show-test-explorer.png)

1. Für Test-Bereitstellung funktioniert muss Ihr Projekt auf die gleiche Weise konfiguriert werden, die UWP-apps (insbesondere mit universelle Authentifizierung und Remote-Computer) konfiguriert sind.  Finden Sie unter [Bereitstellen einer App mit Visual Studio](../develop-your-app/appdeployment.md) Einzelheiten.

1. Um einen Komponententest Remote ausführen möchten, können Sie die Test-Explorer und rechten Maustaste auf die gewünschte TestMethod und Ausführen/Debuggen ausgewählte Tests auswählen ![Test-Explorer](../media/UnitTests/test-explorer.png)

1. Um Remote auszuführen oder alle Komponententests Debuggen, können Sie Test > ausführen oder testen > Debuggen ![Test-Explorer](../media/UnitTests/run-tests.png)
 ![Test-Explorer](../media/UnitTests/debug-tests.png)
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a>Konfigurieren von Komponententests als Teil eines Continuous Integration-Builds
___

Visual Studio-Team hat einen hervorragenden Blogbeitrag zeigt, wie Sie Komponententests für Windows 10 IoT Core in einem VSTS-Build integrieren: [DevOps für IoT mit Win10 IoT Core, UWP und VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)

