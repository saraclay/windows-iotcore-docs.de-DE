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
# <a name="troubleshooting"></a>Problembehandlung
Dies ist ein Artikel, der allgemeine Fragen zur Problembehandlung enthält, die Leute kennen. Um etwas bestimmtem zu suchen, verwenden Sie STRG + F, um ein Wort oder Ausdruck zu suchen. Haben Sie erfahren, die Sie hinzufügen möchten? Erstellen Sie einen PR für diese Dokumentation oder der provident inhaltsfeedback unten ein.

> [!TIP]
> Zur Behandlung von Problemen, die im Zusammenhang mit der Produktion aus, und Lesen Sie die [Problembehandlung Doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in unserem Handbuch für die Produktion.

## <a name="asus-tinkerboard-and-rockchip-support"></a>Unterstützung für ASUS Tinkerboard und Rockchip

Die ASUS Tinkerboard und Rockchip nicht offiziell von uns unterstützt werden, gibt es Fälle, in denen Rockchip mit Drittanbietern abzurufenden SoC funktioniert auf Windows 10 IoT Core gearbeitet hat.

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a>Problem beim Verbinden von einem MBM-Gerät beim roaming

Es gibt zwei Punkte zu berücksichtigen, wenn Sie roaming aktivieren:

1. Die profile.xml wird roaming konfiguriert und das Verhalten, das automatische Herstellung einer Verbindung mit dem Mobilfunknetz.
Legen Sie ein Profil für das roaming finden Sie unter [in diesem Artikel](https://docs.microsoft.com/windows/desktop/mbn/schema-root).

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

Um ein Profil für die automatische Verbindung festzulegen, wählen Sie "auto" ein:

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

2. Ein weiterer Faktor ist, dass die Schnittstellenbasierte roaming Richtlinie erfüllt sein muss. Diese Richtlinie ist standardmäßig auf "false" ("home Spediteur nur") festgelegt. Diese können abgefragt und in der Befehlszeile aus über geändert werden `netsh mbn get/set dataroamcontrol.`

Beispiel:

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

Sie erhalten möglicherweise die Fehlermeldung **0x139f (ERROR_INVALID_STATE)** die Groß-/Kleinschreibung bei der das Gerät roaming, aber die roaming Richtlinie lässt keine datenroaming - Fehler bei einer verbindungsanforderung gesendet, um Wwansvc.

## <a name="raspberry-pi-3b-booting-issues"></a>Raspberry Pi 3 b + startende Probleme

> [!NOTE]
> Diese Version für die Raspberry Pi 3 b + ist eine nicht unterstützte technical Preview-Version. Begrenzt überprüft und die Aktivierung abgeschlossen wurde. Treten Sie für eine bessere Evaluierung auf, und für alle kommerziellen Produkten, verwenden Sie den Raspberry Pi 3-b oder andere Geräte mit unterstützten Intel, Qualcomm oder NXP SoCs. Zur Behandlung von Problemen mit dem Raspberry Pi 3 b aus, informieren Sie sich unsere Handbuch zur Problembehandlung [hier](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues). 

Der Raspberry Pi 3 Modell B + das neueste Produkt im Bereich von Raspberry Pi 3, ist einen Quad-Core 64-Bit-Prozessor mit 1,4 GHz, 2,4-GHz-Dual-Band- und 5 GHz w-LAN, Bluetooth-4.2/BLE, schnellere Ethernet, desktopumstellungsprojekt und PoE-Funktion über einen separaten PoE HA.

Viele Kunden, die Windows 10 IoT Core interessiert sind, gefunden vor kurzem ein Problem, wenn das Gerät konnte nicht normal starten, nach dem leeren Windows 10 IoT Core, aber die Raspbian funktioniert gut auf. Im folgenden sind einige Vorschläge dazu, wie Sie das Startproblem beheben.

Es gibt einige bekannte Probleme in dieser Abbildung Insider Preview. Bitte beachten Sie Folgendes:
* Dieses Image ist nur für den Raspberry Pi 3 b + vorgesehen und werden nicht auf die Raspbierry Pi 2 gestartet.
* F5-Treiber-Bereitstellung aus Visual Studio funktioniert nicht unter Windows 10 IoT Core.
* Integrieren von WLAN- und Bluetooth funktionieren auf dem Raspberry Pi 3 b + nicht.
* Ft5406 Touch Bildschirm Treiber ist auf dem Raspberry Pi 3 b + deaktiviert.
* SD-Karte Aktivität LED ist deaktiviert.

Es gibt nur zwei Anforderungen bei der Auswahl der SD-Karten mit Windows 10 IoT Core verwenden. Sie müssen eine Klasse 10 SD-Karte und stellen Sie sicher, dass die Karte ausreichend Speicherplatz - mindestens 8 GB Speicherplatz verfügt. Es gibt eine Reihe von SD-Karten, die von Microsoft mit Windows 10 IoT Core kompatibel bestätigt wurden:
* Samsung EVO 32 GB class 10 Micros SDHC card
* SanDisk Ultra Micro SDHC, 16 GB-Karte

Im Allgemeinen müssen Sie überprüfen, wenn die SD-Karte gefälschte ist oder wenn er beschädigt ist. Die SD-Karte ist gleichermaßen anfällig gegenüber Beschädigungen aufgrund verschiedener Faktoren wie z. B. Stromausfalls oder falsche entfernen. Es ist wichtig, um Ihre Karte Klammern vor Beschädigung zu schützen.

Um Ihr Image auf einer SD-Karte flash, können Sie die [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard). Sie benötigen, wählen "Benutzerdefiniert" im Feld Betriebssystembuild, und wählen Sie die Datei FFU Flash. 

Überprüfen Sie, wenn alle Hardwarefehler vorhanden, auf dem Gerät sind. Es gibt zwei LEDs auf dem Raspberry Pi 3 b + Board identisch mit der 3-b. Eine ist für PWR, während eine andere für ACT. Die Anzahl der blinkt, die helle wird bestimmt, und zwar unabhängig davon, ob das Board gestartet wird. Die SD-Karte Aktivitäts-LED leuchtet nicht während der einige Teile der auf dem Raspberry Pi 3 b + starten.

Wenn das Gerät wird gestartet, und das Gerät die Seite "Warten zeigt", bitte Geduld. In der Regel wird dies die letzten bis zu eine Minute. Aber in einigen Fällen aufgrund der Geschwindigkeit für die Lese-/ Schreibzugriff der SD-Karte, kann länger dauern.

Wenn das Gerät mit Windows 10 IoT Core normal starten nicht möglich, können Sie versuchen, ein Linux-Betriebssystem (z.B. Raspbian) flash auf die SD-Karte Sie genauer ermitteln, ob das Problem durch die Hardware verursacht wird. 

Wenn Sie feststellen, dass Sie einen Bildschirm"Rainbow" erhalten, prüfen Sie, um sicherzustellen, dass Sie die verfügbaren 3 b + Releaseversion, per flashvorgang [hier](https://www.microsoft.com/en-us/software-download/windowsiot). Sie können überprüfen, den Prozess mit einer Community bereitgestellten 3 b + blinken Tutorial [hier](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a>Serieller Anschluss-Kommunikation auf Windows 10 IoT Core für Raspberry Pi 

Auf dem Raspberry Pi sind Hardware UART und USB UART Adapter sowohl für die Anwendung mit seriellen Communicaiton verwendet werden. Standardmäßig werden die UART übertragen und Empfangen von Pins sind Pins, 8 und 10 für den GPIO-Header.

![UART und USB UART-Adapter](media/Troubleshooting/adapters.png)

Sie können lesen [in diesem Artikel](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) finden Sie weitere Informationen zum Initialisieren von UART0, und führen Sie einen Schreibvorgang, gefolgt von einem Lesevorgang.

Darüber hinaus ist Radio Frequency Communication (RFCOMM) der zugrunde liegenden serielle Kommunikation von klassischen Bluetooth. Finden Sie unter [dieses GitHub-Beispiel](https://github.com/djaus2/iotbluetoothserial) , Informationen zum Ausführen von UWP-apps in Windows 10 IoT Core an verbundenen über ein IoT-Gerät mit der Bluetooth-Seriennummer.

Wenn, dass das Gerät Daten über den seriellen Anschluss Schreib-/kann nicht auftreten, führen Sie die folgenden Schritte zur Problembehandlung:

1. RX mit Jumper - unten - Verbindung mit dem TX, und führen Sie den Beispielcode, um festzustellen, ob die app lesen und Schreiben von Daten kann. Wenn dies nicht funktioniert, kann die Erstkonfiguration auf dem Board unterbrochen werden.

![TX mit RX auf Raspberry Pi](media/Troubleshooting/txrx.png)

2. Stellen Sie sicher, dass die BaudRate, Handshake und Stoppbits ordnungsgemäß konfiguriert sind. Weist der serielle Anschluss getestet werden, eine vollständige RS232-Schnittstelle (z. B. DB9), verwenden Sie Schleichwerbung DB mit der Verbindung mit dem typischen Handshake Übergänge RxTx Crossover-Drähten an. Einige RS232-Ports (oder ein USB-Adapter) erfordern beispielsweise Netzbetreiber erkennen DCD () "und" DCE bereit (DSR) ", um bestätigt zu werden, bevor sie ordnungsgemäß funktionieren.

3. Wenn Sie USB UART-Adapter für Windows 10 IoT Core verwenden möchten, werden die folgenden unterstützt:

* CP2102 USB 2.0
* Gültigkeitsdauer (TTL) Modul Seriell-Konverter
* FTDI
* Generische "Usbser.sys"

Sie können auch den Stapel devcon.exe * und devcon.exe Status * Cmdlet, um die erwartete Treiber Stack und der Treiberstatus auf Windows 10 IoT Core überprüfen.

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) ist ein weiteres nützliches Tool zur Problembehandlung des seriellen Anschlusses. Mit diesem Tool kann Ports auflisten, erhalten Sie ihren Anzeigenamen und eine Geräte-ID, Öffnen von Ports, konfigurieren Sie Einstellungen (d. h. Baudrate, Stoppbits usw.) und senden und Empfangen von Daten. 

## <a name="sirep-test-service"></a>Sirep-Test-Dienst
Obwohl Sirep-Testdienst nicht in Retail-Images, standardmäßig aktiviert ist, für den Fall, dass Sie weiterhin den Sirep-Dienst beim Start zu deaktivieren möchten, können Sie anmelden und Sirep aus automatischen Start zu deaktivieren. 

Sie können die folgenden PowerShell-Befehle verwenden, zu diesem Zweck, wie unten dargestellt:

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

## <a name="tablet-mode"></a>Tabletmodus

"Tablet-Modus" gilt nicht ist ein Konzept, das nur auf Desktop-Shell eingesetzt werden und für IoT Core. 

Wenn das Gerät Hardware (entweder über I2C oder USB HID Touch) unterstützt haben, sollte die automatisch mit den Treibern Posteingang Touch ausgeführt werden. Erfahren Sie mehr zu diesem [hier](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).


## <a name="yubikey-support"></a>Yubikey-Unterstützung

Windows 10 IoT Core keine Unterstützung von Smartcards. Smartcards sind jedoch in der Regel Geräte, die für die Identität des Benutzers und nicht für die geräteidentität verwendet werden, da sie PINs und, bei der Yubikey, eine Schaltfläche drücken, gesichert sind. Dies ist nicht mit einem IoT-Gerät vereinheitlichen. Wenn Sie eine alternative Möglichkeit suchen, ein TPM 2.0 auf dem Gerät möglicherweise besser als eine Yubikey oder einer Smartcard dienen. Es ist vollständiges Zertifikat-Unterstützung für die TPMs und zum Speichern von Geräten als auch für Benutzerzertifikate sollen, und Azure IoT-Zugriffsanmeldeinformationen (Limpets).
