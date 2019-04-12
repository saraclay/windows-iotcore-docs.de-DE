---
author: saraclay
Description: Problembehandlung bei anderen Entwicklung bezogene.
title: Problembehandlung
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 00c748e4ce06e960dbc2a4250fb3cb279f4d092a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513290"
---
# <a name="troubleshooting"></a><span data-ttu-id="3ad12-103">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="3ad12-103">Troubleshooting</span></span>
<span data-ttu-id="3ad12-104">Dies ist ein Artikel, der allgemeine Fragen zur Problembehandlung enthält, die Leute kennen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="3ad12-105">Um etwas bestimmtem zu suchen, verwenden Sie STRG + F, um ein Wort oder Ausdruck zu suchen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="3ad12-106">Haben Sie erfahren, die Sie hinzufügen möchten?</span><span class="sxs-lookup"><span data-stu-id="3ad12-106">Have any insight you want to add?</span></span> <span data-ttu-id="3ad12-107">Erstellen Sie einen PR für diese Dokumentation oder der provident inhaltsfeedback unten ein.</span><span class="sxs-lookup"><span data-stu-id="3ad12-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="3ad12-108">Zur Behandlung von Problemen, die im Zusammenhang mit der Produktion aus, und Lesen Sie die [Problembehandlung Doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in unserem Handbuch für die Produktion.</span><span class="sxs-lookup"><span data-stu-id="3ad12-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="3ad12-109">Unterstützung für ASUS Tinkerboard und Rockchip</span><span class="sxs-lookup"><span data-stu-id="3ad12-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="3ad12-110">Die ASUS Tinkerboard und Rockchip nicht offiziell von uns unterstützt werden, gibt es Fälle, in denen Rockchip mit Drittanbietern abzurufenden SoC funktioniert auf Windows 10 IoT Core gearbeitet hat.</span><span class="sxs-lookup"><span data-stu-id="3ad12-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="3ad12-111">Problem beim Verbinden von einem MBM-Gerät beim roaming</span><span class="sxs-lookup"><span data-stu-id="3ad12-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="3ad12-112">Es gibt zwei Punkte zu berücksichtigen, wenn Sie roaming aktivieren:</span><span class="sxs-lookup"><span data-stu-id="3ad12-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="3ad12-113">Die profile.xml wird roaming konfiguriert und das Verhalten, das automatische Herstellung einer Verbindung mit dem Mobilfunknetz.</span><span class="sxs-lookup"><span data-stu-id="3ad12-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="3ad12-114">Legen Sie ein Profil für das roaming finden Sie unter [in diesem Artikel](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span><span class="sxs-lookup"><span data-stu-id="3ad12-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

```
  <!-- applicability to any combination of home carrier, partner MOs and non-partner MOs, except for HomeAndNonPartner -->
  <xs:simpleType name="roamApplicabilityType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="NonPartnerOnly"/>
       <xs:enumeration value="PartnerOnly"/>
       <xs:enumeration value="HomeOnly"/>
       <xs:enumeration value="HomeAndPartner"/>
       <xs:enumeration value="PartnerAndNonpartner"/>
       <xs:enumeration value="AllRoaming"/>
    </xs:restriction>
  </xs:simpleType>
  
  <xs:simpleType name="roamControlType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="AllRoamAllowed"/>
       <xs:enumeration value="PartnerRoamAllowed"/>
       <xs:enumeration value="NoRoamAllowed"/>
    </xs:restriction>
  </xs:simpleType>
``` 

<span data-ttu-id="3ad12-115">Um ein Profil für die automatische Verbindung festzulegen, wählen Sie "auto" ein:</span><span class="sxs-lookup"><span data-stu-id="3ad12-115">To set a profile for automatic connection, select "auto":</span></span>

```  
<!-- Connection Mode, default is "manual" -->
    <xs:element name="ConnectionMode" minOccurs="0">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <!-- manual connect always -->
          <xs:enumeration value="manual" />
          <!-- auto connect always -->
          <xs:enumeration value="auto" />
          <!-- auto connect when not roaming -->
          <xs:enumeration value="auto-home"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

2. <span data-ttu-id="3ad12-116">Ein weiterer Faktor ist, dass die Schnittstellenbasierte roaming Richtlinie erfüllt sein muss.</span><span class="sxs-lookup"><span data-stu-id="3ad12-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="3ad12-117">Diese Richtlinie ist standardmäßig auf "false" ("home Spediteur nur") festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3ad12-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="3ad12-118">Diese können abgefragt und in der Befehlszeile aus über geändert werden</span><span class="sxs-lookup"><span data-stu-id="3ad12-118">This can be queried and changed in command line via</span></span> `netsh mbn get/set dataroamcontrol.`

<span data-ttu-id="3ad12-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3ad12-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="3ad12-120">Sie erhalten möglicherweise die Fehlermeldung **0x139f (ERROR_INVALID_STATE)** die Groß-/Kleinschreibung bei der das Gerät roaming, aber die roaming Richtlinie lässt keine datenroaming - Fehler bei einer verbindungsanforderung gesendet, um Wwansvc.</span><span class="sxs-lookup"><span data-stu-id="3ad12-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="3ad12-121">Raspberry Pi 3 b + startende Probleme</span><span class="sxs-lookup"><span data-stu-id="3ad12-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="3ad12-122">Diese Version für die Raspberry Pi 3 b + ist eine nicht unterstützte technical Preview-Version.</span><span class="sxs-lookup"><span data-stu-id="3ad12-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="3ad12-123">Begrenzt überprüft und die Aktivierung abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="3ad12-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="3ad12-124">Treten Sie für eine bessere Evaluierung auf, und für alle kommerziellen Produkten, verwenden Sie den Raspberry Pi 3-b oder andere Geräte mit unterstützten Intel, Qualcomm oder NXP SoCs.</span><span class="sxs-lookup"><span data-stu-id="3ad12-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="3ad12-125">Zur Behandlung von Problemen mit dem Raspberry Pi 3 b aus, informieren Sie sich unsere Handbuch zur Problembehandlung [hier](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="3ad12-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="3ad12-126">Der Raspberry Pi 3 Modell B + das neueste Produkt im Bereich von Raspberry Pi 3, ist einen Quad-Core 64-Bit-Prozessor mit 1,4 GHz, 2,4-GHz-Dual-Band- und 5 GHz w-LAN, Bluetooth-4.2/BLE, schnellere Ethernet, desktopumstellungsprojekt und PoE-Funktion über einen separaten PoE HA.</span><span class="sxs-lookup"><span data-stu-id="3ad12-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="3ad12-127">Viele Kunden, die Windows 10 IoT Core interessiert sind, gefunden vor kurzem ein Problem, wenn das Gerät konnte nicht normal starten, nach dem leeren Windows 10 IoT Core, aber die Raspbian funktioniert gut auf.</span><span class="sxs-lookup"><span data-stu-id="3ad12-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flushing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="3ad12-128">Im folgenden sind einige Vorschläge dazu, wie Sie das Startproblem beheben.</span><span class="sxs-lookup"><span data-stu-id="3ad12-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="3ad12-129">Es gibt einige bekannte Probleme in dieser Abbildung Insider Preview.</span><span class="sxs-lookup"><span data-stu-id="3ad12-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="3ad12-130">Bitte beachten Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="3ad12-130">Please note that:</span></span>
* <span data-ttu-id="3ad12-131">Dieses Image ist nur für den Raspberry Pi 3 b + vorgesehen und werden nicht auf die Raspbierry Pi 2 gestartet.</span><span class="sxs-lookup"><span data-stu-id="3ad12-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="3ad12-132">F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="3ad12-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="3ad12-133">Integrieren von WLAN- und Bluetooth funktionieren auf dem Raspberry Pi 3 b + nicht.</span><span class="sxs-lookup"><span data-stu-id="3ad12-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="3ad12-134">Ft5406 Touch Bildschirm Treiber ist auf dem Raspberry Pi 3 b + deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="3ad12-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="3ad12-135">SD-Karte Aktivität LED ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="3ad12-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="3ad12-136">Es gibt nur zwei Anforderungen bei der Auswahl der SD-Karten mit Windows 10 IoT Core verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ad12-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="3ad12-137">Sie müssen eine Klasse 10 SD-Karte und stellen Sie sicher, dass die Karte ausreichend Speicherplatz - mindestens 8 GB Speicherplatz verfügt.</span><span class="sxs-lookup"><span data-stu-id="3ad12-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="3ad12-138">Es gibt eine Reihe von SD-Karten, die von Microsoft mit Windows 10 IoT Core kompatibel bestätigt wurden:</span><span class="sxs-lookup"><span data-stu-id="3ad12-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="3ad12-139">Samsung EVO 32 GB class 10 Micros SDHC card</span><span class="sxs-lookup"><span data-stu-id="3ad12-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="3ad12-140">SanDisk Ultra Micro SDHC, 16 GB-Karte</span><span class="sxs-lookup"><span data-stu-id="3ad12-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="3ad12-141">Im Allgemeinen müssen Sie überprüfen, wenn die SD-Karte gefälschte ist oder wenn er beschädigt ist.</span><span class="sxs-lookup"><span data-stu-id="3ad12-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="3ad12-142">Die SD-Karte ist gleichermaßen anfällig gegenüber Beschädigungen aufgrund verschiedener Faktoren wie z. B. Stromausfalls oder falsche entfernen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="3ad12-143">Es ist wichtig, um Ihre Karte Klammern vor Beschädigung zu schützen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="3ad12-144">Um Ihr Image auf einer SD-Karte flash, können Sie die [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span><span class="sxs-lookup"><span data-stu-id="3ad12-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="3ad12-145">Sie benötigen, wählen "Benutzerdefiniert" im Feld Betriebssystembuild, und wählen Sie die Datei FFU Flash.</span><span class="sxs-lookup"><span data-stu-id="3ad12-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="3ad12-146">Überprüfen Sie, wenn alle Hardwarefehler vorhanden, auf dem Gerät sind.</span><span class="sxs-lookup"><span data-stu-id="3ad12-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="3ad12-147">Es gibt zwei LEDs auf dem Raspberry Pi 3 b + Board identisch mit der 3-b.</span><span class="sxs-lookup"><span data-stu-id="3ad12-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="3ad12-148">Eine ist für PWR, während eine andere für ACT.</span><span class="sxs-lookup"><span data-stu-id="3ad12-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="3ad12-149">Die Anzahl der blinkt, die helle wird bestimmt, und zwar unabhängig davon, ob das Board gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="3ad12-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="3ad12-150">Die SD-Karte Aktivitäts-LED leuchtet nicht während der einige Teile der auf dem Raspberry Pi 3 b + starten.</span><span class="sxs-lookup"><span data-stu-id="3ad12-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="3ad12-151">Wenn das Gerät wird gestartet, und das Gerät die Seite "Warten zeigt", bitte Geduld.</span><span class="sxs-lookup"><span data-stu-id="3ad12-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="3ad12-152">In der Regel wird dies die letzten bis zu eine Minute.</span><span class="sxs-lookup"><span data-stu-id="3ad12-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="3ad12-153">Aber in einigen Fällen aufgrund der Geschwindigkeit für die Lese-/ Schreibzugriff der SD-Karte, kann länger dauern.</span><span class="sxs-lookup"><span data-stu-id="3ad12-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="3ad12-154">Wenn das Gerät mit Windows 10 IoT Core normal starten nicht möglich, können Sie versuchen, ein Linux-Betriebssystem (z.B. Raspbian) flash auf die SD-Karte Sie genauer ermitteln, ob das Problem durch die Hardware verursacht wird.</span><span class="sxs-lookup"><span data-stu-id="3ad12-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="3ad12-155">Wenn Sie feststellen, dass Sie einen Bildschirm"Rainbow" erhalten, prüfen Sie, um sicherzustellen, dass Sie die verfügbaren 3 b + Releaseversion, per flashvorgang [hier](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="3ad12-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="3ad12-156">Sie können überprüfen, den Prozess mit einer Community bereitgestellten 3 b + blinken Tutorial [hier](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span><span class="sxs-lookup"><span data-stu-id="3ad12-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="3ad12-157">Serieller Anschluss-Kommunikation auf Windows 10 IoT Core für Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="3ad12-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="3ad12-158">Auf dem Raspberry Pi sind Hardware UART und USB UART Adapter sowohl für die Anwendung mit seriellen Communicaiton verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3ad12-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="3ad12-159">Standardmäßig werden die UART übertragen und Empfangen von Pins sind Pins, 8 und 10 für den GPIO-Header.</span><span class="sxs-lookup"><span data-stu-id="3ad12-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![UART und USB UART-Adapter](media/Troubleshooting/adapters.png)

<span data-ttu-id="3ad12-161">Sie können lesen [in diesem Artikel](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) finden Sie weitere Informationen zum Initialisieren von UART0, und führen Sie einen Schreibvorgang, gefolgt von einem Lesevorgang.</span><span class="sxs-lookup"><span data-stu-id="3ad12-161">You can read [this article](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="3ad12-162">Darüber hinaus ist Radio Frequency Communication (RFCOMM) der zugrunde liegenden serielle Kommunikation von klassischen Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="3ad12-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="3ad12-163">Finden Sie unter [dieses GitHub-Beispiel](https://github.com/djaus2/iotbluetoothserial) , Informationen zum Ausführen von UWP-apps in Windows 10 IoT Core an verbundenen über ein IoT-Gerät mit der Bluetooth-Seriennummer.</span><span class="sxs-lookup"><span data-stu-id="3ad12-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="3ad12-164">Wenn, dass das Gerät Daten über den seriellen Anschluss Schreib-/kann nicht auftreten, führen Sie die folgenden Schritte zur Problembehandlung:</span><span class="sxs-lookup"><span data-stu-id="3ad12-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="3ad12-165">RX mit Jumper - unten - Verbindung mit dem TX, und führen Sie den Beispielcode, um festzustellen, ob die app lesen und Schreiben von Daten kann.</span><span class="sxs-lookup"><span data-stu-id="3ad12-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="3ad12-166">Wenn dies nicht funktioniert, kann die Erstkonfiguration auf dem Board unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="3ad12-166">If this does not work, the IC on the board may be broken.</span></span>

![TX mit RX auf Raspberry Pi](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="3ad12-168">Stellen Sie sicher, dass die BaudRate, Handshake und Stoppbits ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="3ad12-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="3ad12-169">Weist der serielle Anschluss getestet werden, eine vollständige RS232-Schnittstelle (z. B. DB9), verwenden Sie Schleichwerbung DB mit der Verbindung mit dem typischen Handshake Übergänge RxTx Crossover-Drähten an.</span><span class="sxs-lookup"><span data-stu-id="3ad12-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="3ad12-170">Einige RS232-Ports (oder ein USB-Adapter) erfordern beispielsweise Netzbetreiber erkennen DCD () "und" DCE bereit (DSR) ", um bestätigt zu werden, bevor sie ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="3ad12-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="3ad12-171">Wenn Sie USB UART-Adapter für Windows 10 IoT Core verwenden möchten, werden die folgenden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="3ad12-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="3ad12-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="3ad12-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="3ad12-173">Gültigkeitsdauer (TTL) Modul Seriell-Konverter</span><span class="sxs-lookup"><span data-stu-id="3ad12-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="3ad12-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="3ad12-174">FTDI</span></span>
* <span data-ttu-id="3ad12-175">Generische "Usbser.sys"</span><span class="sxs-lookup"><span data-stu-id="3ad12-175">Generic usbser.sys</span></span>

<span data-ttu-id="3ad12-176">Sie können auch den Stapel devcon.exe \* und devcon.exe Status \* Cmdlet, um die erwartete Treiber Stack und der Treiberstatus auf Windows 10 IoT Core überprüfen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="3ad12-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) ist ein weiteres nützliches Tool zur Problembehandlung des seriellen Anschlusses.</span><span class="sxs-lookup"><span data-stu-id="3ad12-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="3ad12-178">Mit diesem Tool kann Ports auflisten, erhalten Sie ihren Anzeigenamen und eine Geräte-ID, Öffnen von Ports, konfigurieren Sie Einstellungen (d. h. Baudrate, Stoppbits usw.) und senden und Empfangen von Daten.</span><span class="sxs-lookup"><span data-stu-id="3ad12-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="3ad12-179">Sirep-Test-Dienst</span><span class="sxs-lookup"><span data-stu-id="3ad12-179">Sirep Test service</span></span>
<span data-ttu-id="3ad12-180">Obwohl Sirep-Testdienst nicht in Retail-Images, standardmäßig aktiviert ist, für den Fall, dass Sie weiterhin den Sirep-Dienst beim Start zu deaktivieren möchten, können Sie anmelden und Sirep aus automatischen Start zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="3ad12-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="3ad12-181">Sie können die folgenden PowerShell-Befehle verwenden, zu diesem Zweck, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="3ad12-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

```
administrator@MINWINPC C:\Data\Users\administrator>sc stop TestSirepSvc

SERVICE_NAME: TestSirepSvc
       TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 3  STOP_PENDING
                                (STOPPABLE, NOT_PAUSABLE, ACCEPTS_PRESHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x4
        WAIT_HINT          : 0x1770

administrator@MINWINPC C:\Data\Users\administrator>sc query TestSirepSvc

SERVICE_NAME: TestSirepSvc
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 1  STOPPED
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0

administrator@MINWINPC C:\Data\Users\administrator>sc config TestSirepSvc start=disabled
[SC] ChangeServiceConfig SUCCESS
```

## <a name="tablet-mode"></a><span data-ttu-id="3ad12-182">Tabletmodus</span><span class="sxs-lookup"><span data-stu-id="3ad12-182">Tablet mode</span></span>

<span data-ttu-id="3ad12-183">"Tablet-Modus" gilt nicht ist ein Konzept, das nur auf Desktop-Shell eingesetzt werden und für IoT Core.</span><span class="sxs-lookup"><span data-stu-id="3ad12-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="3ad12-184">Wenn das Gerät Hardware (entweder über I2C oder USB HID Touch) unterstützt haben, sollte die automatisch mit den Treibern Posteingang Touch ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3ad12-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="3ad12-185">Erfahren Sie mehr zu diesem [hier](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span><span class="sxs-lookup"><span data-stu-id="3ad12-185">You can read more about this [here](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="3ad12-186">Yubikey-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="3ad12-186">Yubikey support</span></span>

<span data-ttu-id="3ad12-187">Windows 10 IoT Core keine Unterstützung von Smartcards.</span><span class="sxs-lookup"><span data-stu-id="3ad12-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="3ad12-188">Smartcards sind jedoch in der Regel Geräte, die für die Identität des Benutzers und nicht für die geräteidentität verwendet werden, da sie PINs und, bei der Yubikey, eine Schaltfläche drücken, gesichert sind.</span><span class="sxs-lookup"><span data-stu-id="3ad12-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="3ad12-189">Dies ist nicht mit einem IoT-Gerät vereinheitlichen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="3ad12-190">Wenn Sie eine alternative Möglichkeit suchen, ein TPM 2.0 auf dem Gerät möglicherweise besser als eine Yubikey oder einer Smartcard dienen.</span><span class="sxs-lookup"><span data-stu-id="3ad12-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="3ad12-191">Es ist vollständiges Zertifikat-Unterstützung für die TPMs und zum Speichern von Geräten als auch für Benutzerzertifikate sollen, und Azure IoT-Zugriffsanmeldeinformationen (Limpets).</span><span class="sxs-lookup"><span data-stu-id="3ad12-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
