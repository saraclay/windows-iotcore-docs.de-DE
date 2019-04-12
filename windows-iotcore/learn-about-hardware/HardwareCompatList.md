---
title: Hardware-Kompatibilitätsliste
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, bis die peripheren Schnittstellen und Protokolle, die Windows 10 IoT Core, die beste unterstützt.
keywords: Windows Iot, Peripheriegeräten, Protokolle, Kompatibilität, Bussen, hardware
ms.openlocfilehash: 819414db94d01e826fbcf721c911fff9d02f6c94
ms.sourcegitcommit: b79c2b74968e552bee664ecc886725754d183657
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514149"
---
# <a name="hardware-compatibility-list"></a>Hardware-Kompatibilitätsliste

Windows 10 IoT Core unterstützt eine Vielzahl von peripheren Schnittstellen und Protokolle, einschließlich der Unterstützung für allgemeine Bussen wie z. B. I2C, UART, USB und vieles mehr. Diese Seite listet bekannte unterstützte Peripheriegeräte und zum Zeitpunkt der letzten RTM-Version aktuell ist. Bestimmte Einträge, funktionieren möglicherweise nur auf Insider-Versionen und als solche gekennzeichnet. Es wird empfohlen, diese Liste auf GitHub mitwirken!

> [!IMPORTANT]
> Diese Liste ist nicht vollständig. Es gibt viele andere Peripheriegeräte auf dieser Seite nicht angezeigt, die mit Windows 10 IoT Core kompatibel sind. Wenn ein Gerät, die nicht aufgeführt, wird der konform-Klasse mit, was bereits in Windows 10 IoT Core unterstützt wird jedoch angezeigt, funktioniert es. 


Suchen Sie nach Informationen zu den unterstützten Hardwareplattformen? Klicken Sie auf [hier](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) eine Liste der entwicklungsboards mit Windows kompatibel.

## <a name="usb-devices"></a>USB-Geräte

### <a name="wifi-adapters"></a>WiFi-Adapter
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | Offizielle Raspberry Pi-WLAN-dongle | ARM32, x64, x86 | Die offizielle Raspberry Pi-WLAN-Dongle bietet die bestmögliche WiFi Leistung für die All-Größe. | | &#10004;  |
> | Airlink Wireless N 150 Mini-USB-Adapter | x64, x86 | Airlink 101 AWL5077 Golden 150 Mbit/s drahtlosen Mini-USB-Adapter mit WEP, WPA und WPA2 verstärkte Sicherheit bei drahtlosen Verbindungen | | &#10004;  
> | Panda PAU06 | x64, x86 |  Panda 300 Mbit/s drahtlosen N-USB-Adapter mit großer nutzen Antenne | |  &#10004;  
> | TP-LINK TL_WN725N |  ARM32, x64, x86 | TP-LINK-TL-WN725N Wireless N Nano USB-Adapter 150 Mbit/s `(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | NET-DYN-USB-WLAN-Adapter | MBM | WiFi-USB-Adapter-NET-DYN | |  &#10004;  
> | Realtek 8191 USB-Wireless-WiFi | ARM32, x64, x86 | Realtek 8191 300 Mbit/s 802.11n/g/b/ USB-Wireless-WiFi-LAN-Karte Netzwerkadapter | | &#10004;  
> | Realtek 8192 USB-Wireless-WiFi | ARM32, x64, x86 | Realtek Single-Chip IEEE 802.11b/g/n 2T2R WLAN-Controller mit USB 2.0-Schnittstelle | | &#10004; |
> | Realtek 8188EU USB-Wireless-WiFi | ARM32, Mx64, x86BM | Realtek RTL8188EU Drahtlos-LAN-802.11n/g/b USB 2.0-Netzwerkadapter | | &#10004; |
> | Realtek 8192EU USB-Wireless-WiFi | ARM32, x64, x86 | Realtek RTL8192EU Drahtlos-LAN-802.11n/g/b USB 2.0-Netzwerkadapter | | &#10004; |
> | Drahtlose WiFi CanaKit USB | x64, x86 | Chipset Ralink 5370 | | &#10004;
> | D-Link DWA-172 | ARM32 | Drahtlose AC600 Dual-Band-leistungsstarken USB-Adapter | [Datenblatt](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>Ethernet-Adapter
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | ASIX AX88772 USB-2.0 Fast Ethernet-Adapter | ARM32, x64, x86 | Hierbei handelt es sich um eine hohe Leistung und hoher RSWINDOWSBASIC in eingebetteten 28 KB SRAM integriert, für die Pufferung des Pakets.  | | &#10004;  |


### <a name="bluetooth-dongles"></a>Bluetooth-Dongles
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | CSR Mini-USB-Bluetooth-Version 4.0-Adapter | ARM32, x64, x86 | Klasse 2 Bluetooth 4.0 intelligente bereit-Adapter, mit niedrigem Energieverbrauch, dual power |  | &#10004; 
> | ORICO BTA-403 Mini Bluetooth 4.0 USB Dongle | ARM32, x64, x86 | Energiesparendes Bluetooth-4.0-Adapter USB-Micro-Adapter-Dongle |  | &#10004; 
> | CSR Mini-USB-Bluetooth-Version 4.0-Adapter | x64, x86 | Klasse 2 Bluetooth 4.0 intelligente bereit-Adapter, mit niedrigem Energieverbrauch, dual power |  | &#10004;|

### <a name="cameras"></a>Kameras
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Microsoft Lifecam 3000 USB Camera | ARM32, x64, x86 | USB Webcam | [Home Security Camera Project](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32, x64, x86 | Microsoft LifeCam HD-5000 720p HD Webcam | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® LifeCam Studio™ (Modell: 1425) 1080p HD Webcam | | |
> | Logitech Webcam C210 | ARM32, x64, x86 | USB-Webcam, 1,3-MP Foto |  |&#10004; |

### <a name="audio"></a>Audio
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Modell AU-EMAC1 Sabrent USB-externen Stereo Sound-Adapter | ARM32, x64, x86 | Konvertiert USB 3,5 mm Audio- und Mikrofon Signale | | &#10004; 

### <a name="miscellaneous"></a>Sonstiges
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-Wave Z-Stick Serie 2 USB-Dongle DSA02203-ZWUS | ARM32 | Serie 2 Z-Wave-USB-Stick-Z Controller |  | &#10004; |
> | [Wandtafel Electronics 7" LCD-Anzeige kapazitiven Touchscreen anzeigen](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [Aktualisieren der Firmware](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32, x64, x86 | Vodafone (Huawei) K5150 150 Mbit/s 4G LTE FDD USB-mobilen Breitband Modem |  | &#10004;  |
> | Vodafone (Huawei) K5160 | ARM32, x64, x86 | Vodafone (Huawei) K5160 150 Mbit/s GSM/EDGE / 3G/HSPA / LTE-CAT4 USB-mobilen Breitband-Modem |  | |
> | Drahtlose Sierra-Funktionen (AirCard 340U) | x64, x86 |    Sierra drahtlosen Balken (AirCard 340U) 4G LTE USB-mobilen Breitband Modem |  |&#10004; |
> | Microsoft, Xbox 360-Controller | ARM32 | Eine HID-kompatiblen USB-Gamepad für die Microsoft Xbox 360 | [Robot Kit](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM, x32 | Eine HID-kompatiblen USB-kabellose Maus, Tastatur und gamepad |  | &#10004; |

## <a name="other-hardware-peripherals"></a>Andere Hardwareperipheriegeräte

### <a name="storage-media"></a>Speichermedien
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO Class 10 Micro SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32, x64, x86 | Eine empfohlene SD-Karte für Geräte, die Windows 10 IoT Core per flashvorgang haben kann. | | &#10004;|
> | [SanDisk Ultra Micro SDHC 16GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32, x64, x86 | Eine empfohlene SD-Karte für Geräte, die Windows 10 IoT Core per flashvorgang haben kann. | | &#10004; |

### <a name="pi-hats"></a>Pi-Hüten
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16-Kanal PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | Fügt die Möglichkeit, bis zu 16 Servomotoren entsteht kein zusätzlicher Mehraufwand des Raspberry Pi-Verarbeitung zu steuern. Können PWM bis zu 1,6 KHz mit 12-Bit-Präzision. | [Adafruit Tutorial C# IoT-Beispiel](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter Branchen GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | Sie können Hunderte von verschiedenen Sensoren ohne Lötarbeiten, damit Sie sie zum Überwachen, Programmieren können-Steuerelement, zu verbinden und automatisieren Geräte in Ihrem Leben. | [GrovePi-Beispiele](https://github.com/DexterInd/GrovePi/) | |
> | Dexter Industries GoPiGo | ARM, x32 | Die GoPiGo ist ein positives und vollständige Roboter für den Raspberry Pi, die den Pi in einer voll funktionsfähigen Roboter verwandelt. GoPiGo ist eine mobile robotic-Plattform für den Raspberry Pi von Dexter Branchen entwickelt wurde. | [GoPiGo-Beispiele](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |

### <a name="sensors"></a>Sensoren
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Basic-Temperatur-Feuchtigkeitssensor DHT11 | ARM32, x64, x86 | Ein grundlegendes, ultra kostengünstige digitale Temperatur- und luftfeuchtigkeitsdaten Sensor. Es verwendet Feuchtigkeitssensor Kapazitäten und eine: Thermistor, um die umgebende Luft zu messen und aufgreifen digital Signal in die Data-Pin (keine analogen Eingabepins erforderlich).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | DHT22-Temperatur-Feuchtigkeitssensor | ARM32, x64, x86 | Ein grundlegendes, ultra kostengünstige digitale Temperatur- und luftfeuchtigkeitsdaten Sensor. Es verwendet Feuchtigkeitssensor Kapazitäten und eine: Thermistor, um die umgebende Luft zu messen und aufgreifen digital Signal in die Data-Pin (keine analogen Eingabepins erforderlich).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | SparkFun Triple Achse Beschleunigungsmesser Breakout - ADXL345 | ARM32, x64, x86 | Kleine, schlanke, niedrige Leistung, 3-Achsen MEMS Beschleunigungsmesser mit hoher Auflösung (13-Bit) Messung bei bis zu ±16 g. Digitale Ausgabe von Daten ist als 16-Bit-Verpackungskiste ergänzen formatiert und können über eine SPI (3 oder 4 – über das Netzwerk) oder digitale I2C-Schnittstelle zugegriffen werden. |[Beschleunigungsmesserbeispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | Adafruit BMP280 Temperatur- und Barometric Sensor | ARM32 | Bosch environmental Sensor in Verbindung mit der Temperatur, Luftdruck | |   &#10004; |
> | [Adafruit TCS34725 Farbe Sensor](http://www.adafruit.com/products/1334) | ARM, x32 | RGB-Farbe Sensor mit IR-Filter und weiß LED - TCS34725 | | &#10004; |
> | Rohm BH1750FVI ambient lichtsensor | ARM32 | Kleine I2C-Sensor für die ambient-hell-Messung | [I2C-Beispiele](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Bosch BMP180 Temperatur- und barometric sensor | ARM, x32 | Environmental Bosch-Sensor mit Tempreature, Luftdruck | [I2C-Beispiele](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Dorji DSTH01 Relative Luftfeuchtigkeit sensor | ARM32 | Relative Luftfeuchtigkeit I2C-sensor | [I2C-Beispiele](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L digitale 3-Achsen Compass/magnetometer | ARM32 | Eine kleine 3-Achsen Magnetometer für digitale Compass verwenden und Magnetfelds Messungen | [I2C-Beispiele](https://github.com/mickut/Win10-IoT-Sensors) | |


### <a name="port-expanders"></a>Port-Erweiterungen
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Expander für MCP23008-8-Bit-e/a-Port | ARM32, x64, x86 | I2C-Schnittstelle-Chip GPIO-Anschluss Expander-Steuerelement. 8-Ports, 18-PDIP-Paket | [SPI-Port Explander-Beispiel](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | MCP23S17 16-Bit-e/a-Port-Expander | ARM32, x64, x86 | I2C-Schnittstelle-Chip GPIO-Anschluss Expander-Steuerelement. 16-Ports, 28 SPDIP Paket | [Interaktive Piano-Beispiel](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="nfcrfidproximity"></a>NFC/RFID/NEAR
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft |
> |----------------|-------------------|-------------|--------|------------------------------|
> | NXP OM5577-Demo-board | ARM32 | Demo-Board für den NXP PN7120 NFC-Chip. | [ProximityDevice-Dokumentation](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32, x64, x86 | NXP NFC-Chips wird unterstützt. | | &#10004; |

### <a name="miscellaneous"></a>Sonstiges
> | Teil von Namen / Nein. | Kompatible Architektur | Beschreibung | Relevante Links | Microsoft überprüft | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Offizielle Pi anzeigen | ARM32 | 800 x 480 7" touch anzeigen. | [Raspberry Pi 7" Touchscreen](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | Monochrome 1.3" 128 x 64 OLED grafische Darstellung |ARM, x32, x64, x86 | 1.3" diagonal, hoher Kontrast s/w OLED anzeigen. 128 x 64 einzelne weißen OLED Pixel, jeweils ist aktiviert, aktiviert oder deaktiviert wird, durch den Controller-Chip. | [SPI-Anzeige-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | SN74HC595N Schieberegister IC- | ARM32, x64, x86 | IC-8-BIT-SCHIEBEREGISTER 16-DIP-ADRESSE | [UMSCHALT-Register-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | Microchip Technology ADC MCP3002-I/P | AARM32, x64, x86 | MCP3002 10 Bit Analog zu Digital Konverter. |  [Potentiometer Sensor-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | Microchip Technology ADC MCP3208-CI/P | ARM32, x64, x86 | MCP3208 12 Bit Analog zu Digital Konverter. | [Potentiometer Sensor-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM, x32, x64, x86 | Extrem klein, energiesparenden, 16-Bit-ADC | [ADC-Bus-Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | CP2102 USB 2.0 Gültigkeitsdauer (TTL) Modul Seriell-Konverter | ARM32, x64, x86 | CP2102 USB 2.0 Gültigkeitsdauer (TTL) Modul Seriell-Konverter | [Serieller Anschluss-Beispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32, x64, x86 | 16-Kanal, der 12-Bit-PWM Fm + I2C-Bus-LED-Controller. | [PWM Bus Anbieter](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


