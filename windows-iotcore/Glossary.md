---
title: Glossar für Windows IoT
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Erfahren Sie, die verschiedene Begriffe im Zusammenhang mit Windows IoT Core mithilfe unserer Dokumentation.
keywords: Windows Iot, Glossar, Begriffe, Terminologie, Definitionen
ms.openlocfilehash: 155de380459cbb74642352ff2a2ff718ebfe1ed7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513706"
---
# <a name="glossary-for-windows-iot"></a>Glossar für Windows IoT

**Erweiterte Konfiguration & Power Interface (ACPI)** ACPI (Advanced Configuration and Power Interface) ist eine offene Spezifikation, die gemeinsam von Hewlett-Packard, Intel, Microsoft, Phoenix und Toshiba entwickelt.  ACPI richtet ein Industriestandard-Schnittstellen, die OS-gesteuerte Konfiguration, die energieverwaltung sowie zur Verwaltung von mobilen, Desktop- und Server-Plattformen ermöglichen.

**(Basic Input/Output System-BIOS)** den Satz von wichtiger Routinen, die beim Start die Hardware zu testen, Starten des Betriebssystems und die Übertragung von Daten zwischen Hardwaregeräte zu unterstützen.

**Kommerziell** entwickeln und ein Gerät mit dem Ziel platzieren ihn für die Öffentlichkeit kommerziell manufacturing.

**Allgemeine e/a (GPIO)** GPIO ist eine generische Pin für eine integrierte Verbindung, deren Verhalten, z. B., ob es sich um einen Eingabe- oder Ausgabepin ist zur Laufzeit vom Benutzer gesteuert werden kann.  Sie können die Windows.Devices.Gpio Namespace in Ihrer app zum Bearbeiten der GPIO-Schnittstelle auf dem Board angeheftet.

**Spitzen** Windows IoT Core kann entweder im Modus Spitzen oder "monitorlose" sein. Der Unterschied zwischen diesen beiden Modi ist das Vorhandensein oder fehlen von keinerlei Benutzeroberfläche. Standardmäßig wird Windows 10 IoT Core befindet sich im Modus, und zeigt Systeminformationen, wie Sie den Computernamen und IP-Adresse.

**Monitorlose** im monitorlosen Modus steht kein UI-Stapel zur Verfügung und apps sind nicht interaktiv. Monitorlosen Modus apps können als Dienste betrachtet werden.

**Kommunikation zwischen integrierten Verbindungen (I2C)** einfache bidirektionale serielle zwei über das Netzwerk-Daten (SDA) und serielle Uhr (SCL) Busse für integriert zwischen Verbindung-Steuerelement.  Sie können den Windows.Devices.I2c-Namespace in Ihrer app verwenden, für die Kommunikation mit einem Gerät über I2C.

**Leuchtdiode (LED)** eine LED ist eine zwei-Lead Semiconductor Lichtquelle. Es ist ein Pn-Junction Positionen anzeigen, der Licht, die bei Aktivierung gibt.

**Microsoft Windows Kernel Mode Driver Framework (KMDF)** Microsoft Entwicklungsframework dadurch Treiberentwickler Funktionalität des Treibers im Kernelmodus verfügbar machen, der Treiber den Zugriff auf den Systemspeicher und Hardware zu erhalten.

**Prototyp** eine endgültige Version eines Geräts, das Sie, zum Erstellen erhoffen eine mehr Rohdaten Version entwickeln. Erstellen von Prototypen wird, wenn kein Auswahlparameter Schritt im Fertigungsprozess empfohlen. Diese Phase sollte verwendet werden, zu Testzwecken alle Features, die Sie erhoffen, der für die endgültige Version von Ihrem Gerät verwendet wird.

**Serial Peripheral Interface Bus Sicherheitsparameterindex (SPI)** SPI-Bus ist eine synchrone serielle Kommunikation Schnittstelle-Spezifikation, die für die kurze Entfernung Kommunikation in erster Linie in eingebetteten Systemen verwendet.  Sie können den Windows.Devices.Spi-Namespace in Ihrer app verwenden, für die Kommunikation mit einem Gerät über SPI.

**Universal Asynchronous Receiver/Transmitter (UART)** UART ist ein Stück Computerhardware, die Bytes der Daten und überträgt nacheinander die einzelnen Bits.

**Universelle Windows-Plattform (UWP)** die universelle Windows-Plattform bietet eine garantierte Haupt-API-Ebene auf Geräten.  Sie können eine einzelne app-Paket erstellen, die auf einer Vielzahl von Geräten installiert werden können.

**Virtuelle Computer (VM)**<br/>
Software, die fungiert als Schnittstelle zwischen Compiler Binärcode und den Mikroprozessor, der tatsächlich des Programms Anweisungen ausführt.  In Windows können Sie Hyper-V-Manager zum Verwalten von virtuellen Computern.

**Konsole der Windows-Geräts (Devcon.exe)** DevCon (Devcon.exe), die Konsole des Geräts ist ein Befehlszeilentool, das ausführliche Informationen zu Geräten auf Computern unter Windows anzeigt. Sie können die DevCon zu aktivieren, deaktivieren, installieren, konfigurieren und Entfernen von Geräten verwenden.  Dieses Tool wird hauptsächlich verwendet, für das manuelle Installieren und Entfernen von Treibern.
