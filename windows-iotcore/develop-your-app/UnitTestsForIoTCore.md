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
# <a name="developing-unit-tests"></a><span data-ttu-id="6c432-104">Entwicklung von Komponententests</span><span class="sxs-lookup"><span data-stu-id="6c432-104">Developing unit tests</span></span>
<span data-ttu-id="6c432-105">Informationen Sie zu UWP-Komponententests wird unter Windows 10 IoT Core unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6c432-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="6c432-106">UWP-Komponententests</span><span class="sxs-lookup"><span data-stu-id="6c432-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="6c432-107">Komponententests bieten wichtige Schutz und zusätzliche Validierung für app-Entwickler.</span><span class="sxs-lookup"><span data-stu-id="6c432-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="6c432-108">Visual Studio 15.6 zusätzliche Unterstützung für Windows 10 IoT Core in der neue Testplattform.</span><span class="sxs-lookup"><span data-stu-id="6c432-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="6c432-109">Durch diese neue Unterstützung ist es möglich, Komponententests für UWP-Funktionalität zu erstellen, die als Teil eines Continuous Integration-Builds oder direkt aus Visual Studio ausführen können.</span><span class="sxs-lookup"><span data-stu-id="6c432-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="6c432-110">Neue Komponententestprojekt erstellen</span><span class="sxs-lookup"><span data-stu-id="6c432-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="6c432-111">Öffnen Sie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c432-111">Open Visual Studio</span></span>

2. <span data-ttu-id="6c432-112">Erstellen Sie ein neues Komponententestprojekt ![installieren](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="6c432-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="6c432-113">Aktualisieren von UnitTest.cs zum Einbeziehen von Testcode</span><span class="sxs-lookup"><span data-stu-id="6c432-113">Update UnitTest.cs to include your test code</span></span>
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="6c432-114">Remote Ausführen von Komponententests für Windows 10 IoT Core-Geräts</span><span class="sxs-lookup"><span data-stu-id="6c432-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="6c432-115">Öffnen Sie Visual Studio Test-Explorer (Test > Windows > Test-Explorer).</span><span class="sxs-lookup"><span data-stu-id="6c432-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 ![Test-Explorer](../media/UnitTests/show-test-explorer.png)

1. <span data-ttu-id="6c432-117">Für Test-Bereitstellung funktioniert muss Ihr Projekt auf die gleiche Weise konfiguriert werden, die UWP-apps (insbesondere mit universelle Authentifizierung und Remote-Computer) konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="6c432-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="6c432-118">Finden Sie unter [Bereitstellen einer App mit Visual Studio](../develop-your-app/appdeployment.md) Einzelheiten.</span><span class="sxs-lookup"><span data-stu-id="6c432-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="6c432-119">Um einen Komponententest Remote ausführen möchten, können Sie die Test-Explorer und rechten Maustaste auf die gewünschte TestMethod und Ausführen/Debuggen ausgewählte Tests auswählen ![Test-Explorer](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="6c432-119">To remotely run a unit test, you can use the Test Explorer and right clicking the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="6c432-120">Um Remote auszuführen oder alle Komponententests Debuggen, können Sie Test > ausführen oder testen > Debuggen ![Test-Explorer](../media/UnitTests/run-tests.png)
 ![Test-Explorer](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="6c432-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="6c432-121">Konfigurieren von Komponententests als Teil eines Continuous Integration-Builds</span><span class="sxs-lookup"><span data-stu-id="6c432-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="6c432-122">Visual Studio-Team hat einen hervorragenden Blogbeitrag zeigt, wie Sie Komponententests für Windows 10 IoT Core in einem VSTS-Build integrieren: [DevOps für IoT mit Win10 IoT Core, UWP und VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="6c432-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

