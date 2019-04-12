---
title: Verwalten von Geräten für Windows IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie mehr über die verschiedenen Methoden zum Verwalten von Geräten mit Windows 10 IoT Core.
keywords: Windows Iot, geräteverwaltung, Iot mit Windows, Azure-Geräteverwaltung, Azure-Hub, Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513713"
---
# <a name="managing-windows-iot-core-devices"></a>Verwalten von Geräten für Windows IoT Core

Windows 10 IoT Core-Geräte können verwaltet werden, mithilfe eines herkömmlichen OMA-DM-MDM-Servers, das zertifikatbasierte Anmeldung unterstützt, oder verwenden Azure IoT Hub-Geräteverwaltung.  

 _Weitere Informationen zu Verwaltung mobiler Geräte und Windows 10 [hier](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)._  

Richten Sie die MDM-Richtlinien für Windows 10 IoT Core mit den Richtlinien, die in anderen Editionen von Windows 10 unterstützt, für Geräte, die mit einem OMA DM-Server verwaltet werden. Um weitere Informationen zu Richtlinien und als ein Element auf IoT-Core-Geräte verwaltet werden können, finden Sie unter Konfigurationsdienstanbieter-Referenz für Windows 10 [hier](https://aka.ms/csplist). Die MDM-Unterstützung in Windows 10 basiert auf Open Mobile Alliance (OMA) Device Management (DM) 1.2.1-Protokollspezifikation.

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>Wie registriere ich ein Gerät IoT Core in einer MDM?
___
MDM-Registrierung eines IoT Core-Geräts erfolgt mithilfe eines Pakets für die Bereitstellung. Bereitstellung der Pakete kann mithilfe von Windows-Image-Konfiguration und -Designer (WICD) erstellt werden. Probieren Sie die Registrierung eines Geräts in einer Verwaltung mobiler Geräte.

### <a name="creating-a-provisioning-package"></a>Erstellen eines Pakets für die Bereitstellung

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (eigenständig oder SCCM + Intune-Hybridlösung)

1. Öffnen Sie die Configuration Manager-Verwaltungskonsole (Configuration Manager-Konsole)

2. Navigieren Sie zu _Bestand und Kompatibilität > Kompatibilitätseinstellungen > Zugriff auf Unternehmensressourcen > Zertifikatprofile_
   ![Zertifikatprofile](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. Klicken Sie auf **Zertifikatprofil erstellen**

4. Geben Sie einen Namen und Beschreibung für das Profil
   - Name: ConfigMgr-Beispiel vertrauenswürdiges Stammzertifikat
     - Der Typ des Zertifikatprofils an: Vertrauenswürdiges Zertifikat der Zertifizierungsstelle  
     ![Vertrauenswürdiger Zertifizierungsstellen](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. Klicken Sie auf **Weiter**.

6. Importieren Sie die Zertifikatdatei ein.

7. Wählen Sie **Computerzertifikatspeicher – Stamm** für die **Ziel Store**.

8. Klicken Sie auf **Weiter**.

9. Wählen Sie **wählen Sie alle** für unterstützte Plattformen ![unterstützte Plattformen](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. Klicken Sie auf **Zusammenfassung "," Weiter, und schließen** um den Assistenten zu beenden.

11. Mit der rechten Maustaste auf das soeben erstellte Profil, und klicken Sie auf **exportieren**.

12. Klicken Sie auf **Durchsuchen**, suchen Sie einen Standort, in dem die ppkg-Datei exportiert werden sollen, und klicken Sie dann auf **speichern**.

13. Klicken Sie auf **exportieren** , und klicken Sie auf **OK** um den Assistenten zu beenden.

#### <a name="other-mdm-servers"></a>Andere MDM-Server

1. Herunterladen und Installieren der [Windows-Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).

2. Öffnen Sie Windows-Abbilderstellung und Konfigurations-Designer (WICD).
   ![Windows Bildverarbeitungs- und Konfigurations-Designer](../media/ManagingDevices/WICD-Start-Page.png)

3. Wählen Sie **Erweiterte Bereitstellung**

4. Legen Sie einen Namen für Ihr Paket.

5. Wählen Sie die gemeinsame Einstellungen für Windows 10 IoT Core.

6. Überspringen Sie den Schritt Paket importieren.
   ![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. Navigieren Sie zu dem Arbeitsplatz -> Registrierungen.

8. Geben Sie in das Feld "UPN" das Konto, das zum Registrieren Ihres Geräts unter werden sollen (d. h. trmck@contoso.co), und klicken Sie auf **hinzufügen**.

   ![Workplace Registrierungen gefüllt](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. AuthPolicy zur Wahl zwischen Benutzername-Kennwort-basierte Authentifizierung (lokalem System) oder zertifikatbasierte Authentifizierung.

10. Geben Sie die Discovery-Dienst-URL für Ihre MDM-Server ein.

> [!NOTE]
> Dienst-URL für Registrierung und Gruppenrichtlinie-Dienst-URL sind optional.

11. Für den geheimen EINGABETASTE  
    - Lokalem System: Das Kennwort für das Konto, dem Sie sich registrieren können  
    - Zertifikat: Den Fingerabdruck des Zertifikats
    
    ![Ausgefüllte OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. Klicken Sie am oberen Fensterrand WICD auf **Exportieren > Bereitstellung Paket**.

13. Geben Sie einen Namen und die Version für Ihr Paket, und klicken Sie auf **Weiter**. 

> [!NOTE]
> Achten Sie darauf, dass Sie erhöht die Versionsnummer, um sicherzustellen, dass ein aktualisiertes Paket ausgeführt wird.

14. Klicken Sie auf **Weiter** auf die **Details-Seite "Sicherheit"**.

15. Wählen Sie den Speicherort, an dem das Paket exportiert werden, auf dem lokalen Computer und auf **Weiter**.

16. Klicken Sie auf **erstellen** und dann **Fertig stellen** um den Assistenten zu beenden.

### <a name="installing-the-provisioning-package"></a>Installieren des Pakets für die Bereitstellung

Es gibt einige Möglichkeiten, die in denen ein Paket für die Bereitstellung auf einem IoT-Gerät bereitgestellt werden kann. Es ist möglich, das Bereitstellen eines Pakets durch Kopieren des Pakets auf dem Gerät oder das Paket während des imageerstellungsprozesses auf das Bild hinzugefügt.

#### <a name="copying-package-to-device"></a>Kopieren des Pakets auf Gerät

Nehmen Sie die Bereitstellung-Paket, das aus SCCM oder WICD exportiert wurde, und kopieren Sie die ppkg-Datei `C:\Windows\Provisioning\Packages` Verzeichnis auf dem IoT-Gerät. Bei einem Neustart des Geräts wird das Paket ausgeführt werden, und das Gerät wird die Registrierung zu starten.

#### <a name="adding-package-to-image"></a>Hinzufügen des Pakets zu Bild

Finden Sie unter [fügen Sie ein Bereitstellungspaket zu einem Bild](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image). Beim ersten Start wird das Gerät das Paket ausführen und den Registrierungsprozess starten.
