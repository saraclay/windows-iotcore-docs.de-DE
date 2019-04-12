---
title: Erstellen von sicheren Geräten mit Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie sichere Geräte durch Aktivieren der sicheren Start, Implementieren von TPMs und vieles mehr erstellen.
keywords: Windows Iot, Sicherheit, Firmware, sicherer Start TPM kann Bitlocker, Verschlüsselung
ms.openlocfilehash: e9d9bc476455bfbd653a7923c729880dbfad0891
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513956"
---
# <a name="building-secure-devices-with-windows-10-iot-core"></a>Erstellen von sicheren Geräten mit Windows 10 IoT Core

## <a name="introduction"></a>Einführung  
Mit der Einführung von Windows 10 IoT Core ist Microsoft starken Unternehmen bringen Sicherheitsfeatures auf Unternehmensniveau, die genutzt werden können, in kleinere, eingeschränkten Ressourcenklassen von IoT-Geräten.  Damit diese Sicherheitsfunktionen handfeste Vorteile bieten kann muss die Hardwareplattform auch eine Möglichkeit, diese Verankern bereitstellen. Dieses Dokument bietet Anleitung auf hoher Ebene, OEM-Geräte-Generatoren und Sicherheit bewusste "Entwickler", die entsprechenden Hardware auswählen und erstellen, konfigurieren und eine sichere IoT-Geräte für ihre Kunden senden möchten. 

## <a name="firmware"></a>Firmware  
Auf allgemeiner computing-Geräte, die "Offen", wie z. B. PCs sind, können Benutzer Firmware-Einstellungen während des Starts der Geräte über verschiedene Tastenkombinationen zugreifen (z. B. F2 gibt UEFI-Setup auf den meisten PCs heute). Dadurch können Benutzer Änderungen vornehmen, wie die Plattform startet als auch aktivieren und deaktivieren Sie verschiedene Geräteports, Funktionen und andere potenzielle Sicherheitsfunktionen, die auf dem Gerät verfügbar.  

Bei der vertrauliche Art solcher Änderungen IoT-Geräte nicht funktionieren sollte wie "Öffnen Geräte", und sollte funktionieren, eher vergleichbar mit "gesperrten" Geräte wie Mobiltelefone, in denen Zugriff auf die Firmware in der Regel nicht zulässig ist.  Dies kann normalerweise durch, um sicherzustellen, dass die Verwendung von gesperrten Firmware in der Ihr Gerät in der produktionsumgebung erfolgen. Gesperrte Firmware sollten über Ihren Firmware-Anbieter verfügbar sein.  Sollten Sie auf Geräten, in dem gesperrten Firmware nicht verfügbar oder möglicherweise ungeeignet, wie z. B. für die Verwendung durch Entwickler ist, ist, zumindest in der Firmware-Einstellungen für den Zugriff über ein sicheres Administratorkennwort schützen.

## <a name="enabling-secure-boot"></a>Der sichere Start aktiviert
Windows 10 IoT Core wird auf Geräten gestartet, die Unified Extensible Firmware Interface (UEFI) zu implementieren.  Die UEFI-standard implementiert eine Sicherheitsfunktion, die als sicherer Start bezeichnet. Dies kann ein Gerät nur vertrauenswürdige Software zu starten, indem Sie einschränken, das System, um die Ausführung von Binärdateien, die von einer angegebenen Stelle signiert nur zu ermöglichen.  Wenn ein Gerät eingeschaltet ist, überprüft der sicheren UEFI-Start die Signatur der einzelnen Bestandteile Boot-Software, einschließlich der Firmwaretreiber und das Betriebssystem.  Wenn die Signaturen nicht übereinstimmen (z. B. wenn ein Angreifer das ursprüngliche Bild mit einem kompromittierten Betriebssystem ersetzen) die Plattform wird nicht gestartet. Wenn die Signaturen überprüft und gute sind, wird das Gerät weiterhin starten, und gibt dann die Kontrolle an das Betriebssystem.  Beachten Sie, dass zwar die Einschränkung für einen definierten Satz von Behörden veröffentlichen alle unbekannten Code schließt, es nicht unbedingt bekannten von ungültigen Code verhindert ausgeführt werden (z. B. Rollback Angriffe).  Aktivieren der sicheren Start wird dringend empfohlen, wenn die Firmware unterstützt. 

Gerätehersteller müssen die Datenbanken "Sicherer Start" auf ihren Geräten zu speichern.  Dies schließt die Signaturdatenbank (Db), gesperrten Signaturen-Datenbank (Dbx) und Schlüssel für die Registrierung von Schlüssel-Datenbank (KEK).  Diese Datenbanken werden in der Regel auf die Firmware permanenten RAM (NV-RAM) zur Fertigungszeit gespeichert. Die Signaturdatenbank (Db) und die gesperrten Signaturen-Datenbank (Dbx) Liste Signaturgeber oder Hashes der UEFI-Anwendungen, Betriebssystem-Ladeprogrammen (z. B. der Microsoft-Betriebssystem-Lader oder Start-Manager), Bild und UEFI-Treiber, die auf dem Gerät geladen werden können sowie die gesperrten-Images für Elemente, die nicht mehr vertrauenswürdig sind und können nicht geladen werden. Die Schlüssel für die Registrierung von Schlüssel-Datenbank (KEK) ist eine separate Datenbank der Signaturschlüssel, die verwendet werden kann, um die Signaturdatenbank und gesperrten Signaturen zu aktualisieren. Microsoft erfordert einen angegebenen Schlüssel in der KEK-Datenbank eingeschlossen werden, damit in der Zukunft Microsoft neuen Betriebssysteme in der Signaturdatenbank hinzufügen oder der gesperrten Signaturen Datenbank bekannter ungültige Bilder hinzufügen kann.

Nachdem diese Datenbanken hinzugefügt wurden, und nach dem letzten Firmware Prüf- und Testergebnisse, Firmware Bearbeiten gesperrt ist, und ein Plattformschlüssel (PK) generiert und hinzugefügt werden kann. Der Primärschlüssel kann anschließend zum Signieren von Updates auf den KEK, oder stellen alle gewünschten Änderungen an der sicheren Variablen verwendet werden. 

Gerät-Generatoren sollten ihre Firmware Tools und Unterstützung beim Erstellen dieser Datenbanken Hersteller. Finden Sie auf dieser [TechNet-Artikel](https://technet.microsoft.com/library/dn747883.aspx) für Weitere Informationen zum sicheren Start Schlüssel erstellen und verwalten.

## <a name="implementing-tpms"></a>Implementieren von TPMs  
Ein Trusted Platform Module (TPM), ist eine kryptografische Coprozessor, einschließlich der Funktionen für die zufallszahlengenerierung, sicheren Generierung von kryptografischen Schlüsseln und Einschränkung ihrer Verwendung. Darüber hinaus Funktionen wie remote Attestation und sealed-Speicher. Technische Spezifikationen des TPM wird ist öffentlich verfügbar und durch eine Standardisierungsorganisation der Trusted Computing Group (TCG) aufgerufen.  TPM 2.0 steht als diskrete Komponente (von verschiedenen Herstellern) sowie innerhalb einiger SOCs, in der Firmware implementiert.

Geräte, die einem TPM können kryptografische Schlüssel erstellen und verschlüsseln, sodass sie nur vom TPM entschlüsselt werden können. Dieser Prozess, der oft als "wrapping" oder "binding" eines Schlüssels bezeichnet können den Schlüssel vor Offenlegung zu schützen. Jedes TPM verfügt über einen master "wrapping" Schlüssel namens Storage Root Key (SRK), die im TPM gespeichert wird. Der private Teil eines in einem TPM erstellten Schlüssels wird nie eine beliebige andere Komponente, Software, Prozess oder Person verfügbar gemacht. Geräte, die einem TPM können darüber hinaus auch einen Schlüssel erstellen, der nur nicht umschlossen wurden, aber auch an bestimmte Eigenschaften der Plattform gebunden ist. Diese Art von Schlüssel kann nur entschlüsselt werden, wenn die entsprechenden Plattformeigenschaften dieselben Werte aufweisen, die wie beim Erstellen der Schlüssel erstellt wurde. Dieser Prozess wird "Versiegeln" genannten die Taste, um das TPM beim "Entschlüsseln des Schlüssels Entsiegeln" genannt. ist Das TPM kann auch versiegeln und Versiegelung von Daten, die außerhalb des TPM. Mit diesem versiegelten Schlüssel und Software wie BitLocker-Laufwerkverschlüsselung können Sie Daten sperren, bis bestimmte Hardware- oder softwarebedingungen erfüllt sind. 

Mit einem TPM werden die privaten Teile von Schlüsselpaaren von dem vom Betriebssystem kontrollierten Speicher getrennt gespeichert. Schlüssel können versiegelt werden, auf dem TPM, und bestimmte zusicherungen über den Zustand eines Systems (zusicherungen, die definieren, die "Vertrauenswürdigkeit" eines Systems) können vorgenommen werden, bevor die Schlüssel entsiegelt und für die Verwendung freigegeben. Da das TPM zum Verarbeiten von Anweisungen eigene interne Firmware und logikschaltungen verwendet wird, basiert nicht auf das Betriebssystem und Sicherheitsrisiken, die in die Betriebssysteme oder Anwendungen vorhanden sind, möglicherweise nicht verfügbar gemacht.

> [!NOTE] 
> Obwohl einige Geräte zu einen älteren TPM 1.2-Chip integrieren können, unterstützt Windows 10 IoT Core nur TPM 2.0.

## <a name="enabling-bitlocker-encryption"></a>Aktivieren der BitLocker-Verschlüsselung  
Um ruhende Daten (z. B. Datum, die auf einem Gerät gespeichert) zu schützen, hochgefahren Microsoft seine professionelle Unternehmens-BitLocker Drive Encryption-Technologie, um den IoT-Geräten in Windows 10 IoT Core.  BitLocker stellt sicher, dass auf einem Gerät gespeicherte Daten verschlüsselt, bleiben, selbst wenn das Gerät manipuliert wird, während das Betriebssystem nicht ausgeführt wird.  Dies schützt vor "offline-Angriffen" Angriffe durch das Deaktivieren oder umgehen des installierten Betriebssystems, oder Ansprüche von physisch Speichermedium des Geräts zu trennen, um die Daten separat anzugreifen. 

BitLocker verwendet ein Trusted Platform Module (TPM) aus, um erweiterten Schutz für Ihre Daten bereitzustellen und um die Integrität der Frühstartkomponenten zu gewährleisten. Dadurch schützen Ihre Daten vor Diebstahl oder nicht autorisiertem, durch die Verschlüsselung des gesamten Windows-Volumes und alle Partitionen, die auf dem Gerät vorhanden sein können.

Für weitere Anweisungen zum Aktivieren von BitLocker auf Windows 10 IoT Core, befolgen Sie die Schritte [hier](../secure-your-device/SecureBootandBitLocker.md).

## <a name="onboard-storage-options"></a>Integrieren von Storage-Optionen
Entwicklungsboards, wie das beliebte Raspberry Pi 3, bieten Flexibilität und ermöglichen es Entwicklern, problemlos auf jeder Plattform über einen Wechseldatenträger SD-Karte gestartet.  Für die meisten Branche IoT-Geräte wird diese Flexibilität nicht erwünscht ist, und Sie können solche Geräte stellen ein leichtes Ziel für Angriffe. Beim Entwerfen Ihrer Hardware stattdessen Sie verwenden Sie einen eMMC Speicher für Ihre IoT-Geräte kleiner und kostengünstiger.  Eingebettete Speicher macht es erheblich schwieriger des Inhalts vom Gerät zu trennen und wiederum verringert das Potenzial der Einführung von Malware auf dem Gerät Diebstahl von Daten. 

## <a name="developer-tools"></a>Entwicklungstools  
Wenn Sie Ihr Windows 10 IoT Core-Image endgültige Protokollversand-Gerät mit ICD (Image-Konfigurations-Designer) zu erstellen, stellen Sie sicher, dass kein Entwickler, die in Ihrem Einzelhandel-Abbild enthalten sind.  Tools, mit dem Entwickler, Remotezugriff und Debuggen von Geräten für IoT Core darf nicht auf Produktionssystemen vorhanden sein, da diese möglicherweise Einrichtung Ihres Geräts für Angriffe geöffnet werden können.  Stellen Sie sicher, dass wenn Sie unsere Entwicklertools wie Windows Device Portal "," ftp-Server "," SSH "oder" PowerShell in Ihren Bildern während der Entwicklung verwenden, testen und überprüfen Sie Ihre Szenarien für die Verkaufsversion, die IoT-Core-images, die diese Tools nicht enthalten.

## <a name="user-accounts"></a>Benutzerkonten  
Die meisten Benutzer sind vertraut mit dem Konzept der Besitz "" Geräte wie PCs und Smartphones – das Konzept der Personalisieren des Geräts beim Unboxing und Anmeldeinformationen für das Gerät einrichten. Im Gegensatz zum Consumer-PCs und Smartphones IoT-Geräten sollen nicht als allgemeiner Computergeräten dienen. Stattdessen sind sie in der Regel einzelnen-app, festen Geräten. Obwohl Windows über das Konzept der Geräteadministratoren, die für Geräte während eines Entwicklungszyklus eine Remoteverbindung herstellen können unterstützt, kann diese Unterstützung auf IoT-Geräten Branche eine Bedrohung darstellen, insbesondere, wenn Sie unsichere Kennwörter verwendet werden.  Microsoft empfiehlt im Allgemeinen keine "Default" Konten oder Kennwörter auf Geräten mit Windows 10 IoT Core erstellt werden soll.


