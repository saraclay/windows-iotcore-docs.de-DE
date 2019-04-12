---
title: Trusted Platform Module (TPM)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie ein Trusted Platform Module verwenden, um kryptografische Funktionen, um besser zu schützen, Geräte zu aktivieren.
keywords: Windows Iot, Sicherheit, Trusted Platform Module "," TPM "," Kryptografie "," Schlüssel
ms.openlocfilehash: cf22811cbf45b5c715a19b8e12d7b00c2afaa9b8
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512826"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>Trusted Platform Module (TPM) auf Windows 10 IoT Core

## <a name="what-is-tpm"></a>Was ist TPM?
Ein Trusted Platform Module (TPM), ist eine kryptografische Coprozessor, einschließlich der Funktionen für die zufallszahlengenerierung, sicheren Generierung von kryptografischen Schlüsseln und Einschränkung ihrer Verwendung. Darüber hinaus Funktionen wie remote Attestation und sealed-Speicher.
Technische Spezifikationen des TPM ist öffentlich verfügbar ist, von der Trusted Computing Group (TCG) gesteuert. Die neueste Version von TPM 2.0 (veröffentlicht im Oktober 2014), handelt es sich um eine wichtige Neugestaltung der Spezifikation, die neue Funktionalität und Fehlerbehebungen Nachteilen der frühere TPM 1.2.

## <a name="why-tpm"></a>Warum TPM?  
Computer mit einem TPM können Kryptografieschlüssel generieren und so verschlüsseln, dass sie nur durch das TPM wieder entschlüsselt werden können. Dieser Prozess wird häufig aufgerufen, **"wrapping"** oder **"binding"** ein Schlüssel, das den Schlüssel vor Offenlegung zu schützen können. Jedes TPM verfügt über einen master "wrapping" Schlüssel namens Storage Root Key, die im TPM gespeichert wird. Der private Teil eines in einem TPM erstellten Schlüssels wird nie eine beliebige andere Komponente, Software, Prozess oder Person verfügbar gemacht.  

Computer, auf denen ein TPM verfügen, können auch einen Schlüssel erstellen, der nur nicht umschlossen wurden, aber auch an bestimmte Eigenschaften der Plattform gebunden ist. Diese Art von Schlüssel kann nur entschlüsselt werden, wenn die entsprechenden Plattformeigenschaften dieselben Werte aufweisen, die wie beim Erstellen der Schlüssel erstellt wurde. Dieser Prozess heißt **"Versiegeln"** den Schlüssel auf dem TPM. Das Entschlüsseln des Schlüssels wird aufgerufen, **"Entsiegeln"**. Das TPM kann auch versiegeln und Versiegelung von Daten, die außerhalb des TPM. Mit diesem versiegelten Schlüssel und Software wie BitLocker-Laufwerkverschlüsselung können Sie Daten sperren, bis bestimmte Hardware- oder softwarebedingungen erfüllt sind.  

Mit einem TPM werden die privaten Teile von Schlüsselpaaren von dem vom Betriebssystem kontrollierten Speicher getrennt gespeichert. Schlüssel können versiegelt werden, auf dem TPM, und bestimmte zusicherungen über den Zustand eines Systems (zusicherungen, die definieren, die "Vertrauenswürdigkeit" eines Systems) können vorgenommen werden, bevor die Schlüssel entsiegelt und für die Verwendung freigegeben. Da das TPM zum Verarbeiten von Anweisungen eigene interne Firmware und logikschaltungen verwendet wird, basiert nicht auf das Betriebssystem und Sicherheitsrisiken, die in die Betriebssysteme oder Anwendungen vorhanden sind, möglicherweise nicht verfügbar gemacht.

## <a name="tpm-architecture"></a>TPM-Architektur
_Der Unterschied zwischen 1.2 und TPM 2.0._  
TPM-Spezifikation wurde zweimal entwickelt. Erstmals ausführen, entwickelte sich von 1.1B-kompatiblen, 1.2, Einbinden von neuen Funktionen, die von der Spezifikation Committee angefordert/identifiziert. Diese Funktion – mit langsamerem Fortschritt-Form der Entwicklung, die die endgültige TPM 1.2-Spezifikation sehr vorgenommen kompliziert. Schließlich wurden kryptografische Schwächen von SHA-1 (die die stärksten kommerziellen Algorithmus in TPM 1.2 war) angezeigt, die die Notwendigkeit einer Änderung verursacht hat. Die TPM-Architektur wurde von Grund auf neu, was im TPM 2.0 viel besser integrierte, einheitliche Entwurf umgestaltet.  

Die Änderungen und Verbesserungen im Vergleich zu den vorherigen TPM 1.2 gehören:

* Unterstützung weiterer Kryptografiealgorithmen
* Verbesserungen für die Verfügbarkeit des TPM für Anwendungen
* Verbesserte Autorisierungsmechanismen
* Vereinfachte TPM-Verwaltung
* Zusätzliche Funktionen zur Verbesserung der Sicherheit von Plattform-Diensten

Beachten Sie, dass Windows IoT Core nur TPM 2.0 unterstützt und die veralteten TPM 1.2 nicht unterstützt.

## <a name="what-is-tbs"></a>Was ist TB? 
Die TPM-Basis-Dienste (TB)-Funktion ist ein Systemdienst, der ermöglicht die transparente Freigabe von der TPM-Ressourcen. Er teilt der TPM-Ressourcen innerhalb mehrerer Anwendungen auf demselben physischen Computer über Remoteprozeduraufrufe (RPC). Durch die zentrale TPM-Zugriff für Anwendungen mit Prioritäten, die von der aufrufenden Anwendungen angegeben werden.  

TPM stellt kryptografische Funktionen, die entwickelt, um Vertrauen in die Plattform bereitstellen. Da das TPM in der Hardware implementiert wird, hat es begrenzte Ressourcen. Die TCG definiert eine TPM-Software-Stack (TSS), diese Ressourcen verwendet wird, um vertrauenswürdige Vorgänge für Anwendungssoftware bereitzustellen. Allerdings besteht keine Möglichkeit für die Ausführung einer TSS Implementierung Seite-an-Seite mit Betriebssystem-Software, die auch die TPM-Ressourcen verwendet werden kann. Das Feature TB löst dieses Problem durch Aktivieren der einzelnen Software-Stack, mit denen kommuniziert mit TB-Bereich mit TPM-Ressourcen, die Überprüfung für jede andere Software zur Verfügung, die auf dem Computer ausgeführt werden kann.

## <a name="tpm-solutions-available-on-windows-iot-core"></a>TPM-Lösungen unter Windows IoT Core  
_Einige Worte über Software-TPM (sTPM), Firmware-TPM (fTPM), diskretes TPM (dTPM)..._

### <a name="firmware-tpm-ftpm"></a>Firmware-TPM (fTPM)  
Firmware-TPM (fTPM) erfordert spezielle Prozessor/SoC-Unterstützung, die derzeit nicht auf dem Raspberry Pi 2- oder 3 implementiert wird. MinnowBoard Max benötigt Firmwareversion 0,80 oder höher. DragonBoard410c bietet fTPM standardmäßig standardmäßig aktiviert.  

### <a name="discrete-tpm-dtpm"></a>Diskretes TPM (dTPM)  
Diskretes TPM (dTPM) wird unter allen Umständen die enorm vertrauenswürdige Lösung betrachtet werden.  
Es gibt mehrere Hersteller von dTPM Chips und Leiterplatte-Modulen, die unter Windows IoT Core unterstützt werden:

> | Hersteller | Webseite | Modul-Typ | TPM-Chip |
> |-------------|----------|----------|----------| 
> | Infineon | [Infineon TPM](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [Infineon SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| Große Produkt & Evalboard | [Infineon SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>Software-TPM (sTPM)  
Software-TPM (sTPM) wird auch als TPM-Simulator bezeichnet. Es ist plattformunabhängig, unter Windows IoT Core unterstützt wird.  

> [!NOTE]
> sTPM dient nur zu Entwicklungszwecken und stellt keinen wirklichen Vorteile.  


## <a name="samples"></a>Proben  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Bibliotheksbeispiel Urchin](https://github.com/ms-iot/security/tree/master/Urchin/Lib) in diesem Tutorial wird veranschaulicht, wie zum Erstellen C++ -Anwendung, die die TPM-Funktionalität mit führt die [Urchin Bibliothek](https://github.com/ms-iot/security). Urchin ist eine abgeleitet von der referenzimplementierung für TPM 2.0-Spezifikation kompatibel-Bibliothek. Es bietet auf der Client die Funktionalität zum Marshallen/Marshallens alle Datenstrukturen, ordnungsgemäß autorisierungen zu berechnen, führen Sie die parameterverschlüsselung und führen die Überwachung.

## <a name="additional-resources"></a>Zusätzliche Ressourcen  
* [Trusted Platform Module (TPM)-Spezifikationen](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [Die Spezifikation der TCG-TPM 2.0-Typbibliothek](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [TPM-Basisdienste](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [Sicherer Start "und" BitLocker aktiviert](SecureBootAndBitLocker.md)

