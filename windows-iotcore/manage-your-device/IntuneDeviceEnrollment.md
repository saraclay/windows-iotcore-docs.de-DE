---
title: Windows IoT Core-Geräte in Intune registrieren
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Weitere Informationen zum Verwalten Ihrer Geräte mit Microsoft Intune-Geräteverwaltung und Windows IoT.
keywords: Windows Iot, Azure IoT Device Management in Intune, geräteverwaltung
ms.openlocfilehash: 5d75c64813a3e61f60630abd87185949b63e178b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512361"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>Registrieren von Windows IoT Core-Geräten in Microsoft Intune

Ihr Unternehmen kann es sich um Geräte IoT Core, zusammen mit alle anderen verwalteten Geräte verwalten. Dies bietet Ihnen eine einheitliche Methode zum IoT Core, IoT-Unternehmen und andere Windows-Geräten mit Intune zu verwalten.

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>Wie registriere ich ein IoT Core-Geräts bei Intune?

Intune-Registrierung eines IoT Core-Geräts erfolgt mithilfe von Windows IoT Core Dashboard zum Vorbereiten des Geräts, und klicken Sie dann mithilfe von Windows Configuration Designer zum Erstellen eines Bereitstellungspakets.

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>Ändern Sie den Intune-MDM-Benutzerbereich in Azure AD

1. Melden Sie sich bei der [Azure-Portal](https://portal.azure.com), und wählen Sie dann **Azure Active Directory**.
2. Wählen Sie **Mobilität (MDM und MAM)**.


~~~
 ![Selecting Mobility and Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)
~~~
1. Wählen Sie **Microsoft Intune**. Auf der **Konfigurieren von Microsoft Intune** Seite neben **MDM-Benutzerbereich**Option **alle**. Dadurch kann Ihre IoT Core Benutzer des Geräts bei Intune registriert werden, nach dem Beitritt zu Azure AD.

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>Erstellen Sie eine Setup-SD-Karte für das Gerät IoT Core
1. Fügen Sie eine MicroSD-Karte in den Smartcardleser auf Ihrem PC. 
     > [!NOTE]
     > Die MicroSD-Karte wird während dieses Vorgangs formatiert sein, damit alle Daten auf der Karte werden gelöscht.
2. Wechseln Sie zu [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) herunterladen und installieren das Dashboard.
3. Nach der Installation des Dashboards öffnen, und wählen **richten Sie ein neues Gerät**.

     ![Windows IoT Core Dashboard](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. Geben Sie einen **Gerätename**.
5. Geben Sie ein neues Administratorkennwort ein. 
6. Wenn Sie Wi-Fi für das Gerät aktivieren möchten, wählen Sie die **Wi-Fi-Verbindung** Kontrollkästchen. Überspringen Sie dies aus, wenn das Gerät nur eine Ethernet-Netzwerkverbindung verwenden.

     ![Wi-Fi-Kontrollkästchen auf dem IoT-dashboard](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. Wählen Sie die **ich akzeptiere die Lizenzbedingungen der Software** Kontrollkästchen, und wählen Sie dann **herunterladen und installieren**.
8. Wenn die bestätigungsmeldung angezeigt wird, wählen Sie die Option **Format** SD-Karte. 
     > [!NOTE]
     > Sehen Sie sich für die **Format** bestätigungsmeldung während des Setups. Die Nachricht von einer anderen open-Anwendung ausgeblendet werden kann, aber es ist wichtig, die Format-Option ausgewählt haben. Wenn das Laufwerk ordnungsgemäß formatiert ist nicht, schlägt der Start fehl.
9. Die Nachricht **der SD-Karte kann** angezeigt wird.

     ![SD-Karte bereit Nachricht](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. Minimieren Sie diese Seite.  Sie werden darauf später zurückkehren.

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>Erstellen eines Bereitstellungspakets für Intune-Registrierung
1. Installieren die Windows-Konfigurationsentwurf app anhand der Schritte in [Installieren von Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).

2. Öffnen der **Windows Imaging- und Konfigurations-Designer**.
3. Wählen Sie **Desktopgeräte bereitstellen** zum Erstellen eines Projekts 

     ![Auswählen von Desktops Bereitstellen von Diensten](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. Geben Sie die **Projektdetails** je nach Bedarf. Wählen Sie dann **Fertig stellen**.
5. Wechseln Sie zu der **Kontoverwaltung** Seite und wählen Sie **bei Azure AD registrieren**.
      > [!NOTE]
     > Installieren der app aus dem Microsoft Store oder das Windows Assessment und Deployment Kit (ADK) ist in Ordnung.

     ![In Azure AD registrieren auswählen](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. Neben **Massentokens**, geben Sie ein Massenladen Ablauf des Tokens.
7. Wählen Sie **Tokenabruf Bulk**. Für die Verbindung mit Azure AD wird eine Meldung-Anmeldung angezeigt.

     ![Azure AD-Anmeldeseite](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. Geben Sie den Benutzernamen des Mandanten (z. B. john@mycompany.onmicrosoft.com) und das Kennwort ein.   
9. Stimmen Sie die Konfigurationsentwurf für Windows-app auf Ihrem Azure AD die Informationen zugreifen kann. 
10. Eine Nachricht auf der Seite zeigt, dass das Bulk-AAD-Token wurde erfolgreich abgerufen wurde.

     ![BULK-token-erfolgreich-Meldung](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. Wählen Sie **wechseln Sie zur erweiterten Editor**, und wählen Sie dann *Ja*.

     ![Wechseln Sie zur erweiterten Editor-Seite "Bestätigung"](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. Unter **ausgewählt Anpassungen**, lassen Sie die **Konto** Einstellungen, aber alle anderen Einstellungen entfernen:
13. Wählen Sie **OOBE**, und wählen Sie dann **entfernen**.
14. Wenn **SharedPC** ist aufgeführt, wählen Sie ihn, und wählen Sie dann **entfernen**.

     ![Entfernen von Anpassungen](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. Wählen Sie **exportieren**, und wählen Sie dann **Bereitstellung Paket**.

     ![Bereitstellung Paket auswählen](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. Klicken Sie auf der nächsten Seite die Standardeinstellungen übernehmen, und wählen **Weiter**.
17. In diesem Fall auf der nächsten Seite übernehmen Sie die Standardeinstellungen, und klicken Sie auf Weiter.
18. Ändern der **Bereitstellung Paket** Ziel oder lassen Sie den Standardpfad, und drücken Sie **Weiter**.
19. Wählen Sie **erstellen**.
20. Wählen Sie die **Ausgabespeicherort** verknüpfen, sodass Sie die ppkg-Datei zugreifen können, wenn er bereit ist.

     ![Speicherort der ausgabeverknüpfungen](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. Wählen Sie **Fertig stellen**.
22. Wechseln Sie zur Datei-Explorer aus, und kopieren Sie das Paket auf Ihrem Gerät IoT Core. Speichern Sie es auf der MicroSD-Karte unter dem **MainOS** Laufwerk in der **c:\windows\provisioning\packages** Ordner.  Sie müssen zum Gewähren von Berechtigungen zum Speichern der Datei in diesem Ordner.

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>Bereitstellen Sie und registrieren Sie des IoT Core-Geräts bei Intune
1. Legen Sie die MicroSD-Karte in Ihrer IoT Core-Geräts ein.
2. Aktivieren Sie auf Ihrem Gerät IoT Core, und warten sie beim Starten und den standardmäßigen Bildschirm anzuzeigen. 
3. Geben Sie auf der Microsoft Intune-Konsole im Azure-Portal zurück. Ihr Gerät sollte in der Liste der Geräte angezeigt werden.
     > [!NOTE]
     > Registrierung kann es sich um 15 Minuten oder mehr dauern.

     ![Liste der Intune-Geräte](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>Nächste Schritte
- [Anzeigen von Gerätedetails in Intune](https://docs.microsoft.com/intune/device-inventory).
- [Das Gerät, rufen Sie die neuesten Richtlinien und Aktionen mit Intune synchronisieren,](https://docs.microsoft.com/intune/device-sync).
- [Starten Sie das Gerät bei Intune Remote neu](https://docs.microsoft.com/intune/device-restart).
