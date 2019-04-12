---
title: Verbinden Sie Ihres Geräts mit der cloud
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Informationen Sie zum Verbinden Ihres Geräts mit der Cloud.
keywords: Windows Azure, Iot-Sicherheit, Trusted Platform Module, SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513842"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="d4f46-104">Verbinden Sie Ihres Geräts mit der cloud</span><span class="sxs-lookup"><span data-stu-id="d4f46-104">Connect your device to the cloud</span></span>

<span data-ttu-id="d4f46-105">Sichere Informationen wie z. B. ein Kennwort oder ein Zertifikat auf einem Gerät speichern, kann ein Gerät für Offenlegung anfällig machen.</span><span class="sxs-lookup"><span data-stu-id="d4f46-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="d4f46-106">Einem kompromittierten Kennwort ist ein scherzhafter Kommentar Möglichkeit, die die Sicherheit eines Geräts oder ein ganzes System zu gefährden.</span><span class="sxs-lookup"><span data-stu-id="d4f46-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="d4f46-107">In der Windows-Familie ist die Technologie, die die Sicherheit des Betriebssystems unterstützt das Trusted Platform Module.</span><span class="sxs-lookup"><span data-stu-id="d4f46-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="d4f46-108">Ein [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM)-Gerät ist ein Microcontroller, die Daten speichern und Berechnungen ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="d4f46-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="d4f46-109">Es kann entweder eine diskrete Chip aufgelötet auf der Hauptplatine des Computers oder eines Moduls, das System auf einem Chip (SoC) vom Hersteller integriert sein.</span><span class="sxs-lookup"><span data-stu-id="d4f46-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="d4f46-110">Innerhalb des TPM</span><span class="sxs-lookup"><span data-stu-id="d4f46-110">Inside the TPM</span></span> 

<span data-ttu-id="d4f46-111">Ein entscheidendes Merkmal des TPM ist der lesegeschützte Speicher.</span><span class="sxs-lookup"><span data-stu-id="d4f46-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="d4f46-112">Auf Grundlage der Daten in ihr ist TPM kann auch berechnen einen kryptografischen Hash (z. B. die [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), basierend auf diesen Daten.</span><span class="sxs-lookup"><span data-stu-id="d4f46-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="d4f46-113">Es ist unmöglich, entdecken Sie den geheimen Schlüssel, der den Hash angegeben, aber wenn beide Seiten der Kommunikation der geheime Schlüssel bekannt ist, ist es möglich, zu bestimmen, ob der Hash von einer anderen Partei empfangen diesen geheimen Schlüssel erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="d4f46-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="d4f46-114">Die grundlegende Idee hinter der Verwendung von kryptografischer Schlüsseln: der geheime Schlüssel (auch als "den SAS-Schlüssel" bezeichnet) hergestellt und das IoT-Geräte und der Cloud während der Device provisioning-Prozess gemeinsam ist.</span><span class="sxs-lookup"><span data-stu-id="d4f46-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="d4f46-115">Ab diesem Punkt wird ein HMAC, abgeleitet aus dem geheimen Schlüssel zum Authentifizieren des IoT-Geräts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d4f46-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="d4f46-116">Gerätebereitstellung</span><span class="sxs-lookup"><span data-stu-id="d4f46-116">Device Provisioning</span></span> 

<span data-ttu-id="d4f46-117">Das Tool, mit dem Windows 10 IoT Core-Geräte bereitgestellt IoT Core Dashboard aufgerufen wird, und kann heruntergeladen werden [die Seite Downloads Aufrufen](http://go.microsoft.com/fwlink/?LinkID=708576).</span><span class="sxs-lookup"><span data-stu-id="d4f46-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="d4f46-118">Das Dashboard ein Image des Betriebssystems und Ihr Gerät sicher mit Azure verbunden.</span><span class="sxs-lookup"><span data-stu-id="d4f46-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="d4f46-119">Dies erfolgt durch das physische Gerät mit Geräte-ID im Azure IoT Hub und die dazugehörigen Geschäftsparameter imprinting des gemeinsame Zugriffsschlüssels und gerätespezifische auf dem Gerät des TPM.</span><span class="sxs-lookup"><span data-stu-id="d4f46-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="d4f46-120">Für Geräte, die nicht über ein TPM-Chip verfügen, kann das Tool Software emulierte TPM installieren.</span><span class="sxs-lookup"><span data-stu-id="d4f46-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="d4f46-121">Keine Sicherheit geboten, aber dies ermöglicht Ihnen das Entwickeln von Apps, die mit einem Gerät Maker (z. B. Raspberry Pi 2- oder 3) und Sicherheit "light einrichten" auf einem Gerät mit der TPM-Hardware verfügen, ohne die app ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="d4f46-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="d4f46-122">Um Ihr Gerät mit Azure verbinden möchten, klicken Sie auf der Registerkarte "Connect to Azure":</span><span class="sxs-lookup"><span data-stu-id="d4f46-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![Öffnen Sie eine Verbindung herstellen, auf der Registerkarte "Azure"](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="d4f46-124">Sie werden aufgefordert, die bei Ihrem Azure-Konto anmelden.</span><span class="sxs-lookup"><span data-stu-id="d4f46-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="d4f46-125">Wählen Sie die gewünschte Instanz von Azure IoT Hub, und ordnen Sie Ihr physische Gerät zu.</span><span class="sxs-lookup"><span data-stu-id="d4f46-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="d4f46-126">Wenn Sie nicht über die jeder IoT Hub-Instanzen im Azure-Abonnement verfügen, erlauben das Tool Ihnen, eine kostenlose Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4f46-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="d4f46-127">Nachdem Sie den IoT Hub und die Geräte-ID Ihres Geräts mit zuordnen ausgewählt haben, können Sie auf das TPM versehen den SAS-Schlüssel des Geräts dadurch:</span><span class="sxs-lookup"><span data-stu-id="d4f46-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![Bereitstellen eines Geräts](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="d4f46-129">Ihr Gerät ist jetzt auf sichere Weise eine Verbindung mit Azure bereit.</span><span class="sxs-lookup"><span data-stu-id="d4f46-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="d4f46-130">Die Windows Device Portal können auch um eine IoT Hub-Verbindungszeichenfolge dynamisch zu erlangen, obwohl es zuerst mit dem Internet verbindet, nach der bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d4f46-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="d4f46-131">Dies kann auf der Registerkarte "Azure-Clients" in das Device Portal erfolgen.</span><span class="sxs-lookup"><span data-stu-id="d4f46-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Registerkarte "Azure-Clients"](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="d4f46-133">Hilfreiche Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="d4f46-133">Helpful resources:</span></span>
* [<span data-ttu-id="d4f46-134">Verbinden Ihrer app in Azure</span><span class="sxs-lookup"><span data-stu-id="d4f46-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="d4f46-135">Erstellen sichere apps IoT Core</span><span class="sxs-lookup"><span data-stu-id="d4f46-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
