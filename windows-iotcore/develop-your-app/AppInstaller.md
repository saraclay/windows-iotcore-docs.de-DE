---
title: Installieren der app auf ein Gerät IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie Ihre app mithilfe der Windows Device Portal oder im Rahmen der IoT-core-Image.
keywords: Windows Iot, app-Installation, Windows Device Portal-,-Geräte
ms.openlocfilehash: 6e188eaef6551548c6c71ac50859516d4cbe7e9c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513033"
---
# <a name="install-your-app-on-an-iot-core-device"></a>Installieren der app auf ein Gerät IoT Core
Sie können Ihre app mit einer der beiden Methoden, die unten aufgeführten installieren.

> [!NOTE]
> Die Methode mithilfe der Windows Device Portal ist nur für entwicklerszenarien. Die anderen beiden Methoden sind für Produktionsszenarien.

## <a name="using-windows-device-portal"></a>Mithilfe von Windows Device Portal

Für diese Methode müssen Sie sicherstellen, dass Sie mit dem Internet verbunden sind. Wenn Sie keinen Zugriff auf das Internet haben, haben Sie auch, eine Peer-zu-Peer-Ethernet-Verbindung zwischen dem Gerät und einem Clientcomputer, die einen Pfad für den Zugriff auf das offene Internet nicht enthält. Laufende über die zweite Möglichkeit wird die app installieren, jedoch kann nicht gestartet werden, wenn die app Store angemeldet ist.

Zum Installieren die Anwendung auf dem Gerät führen Sie die folgenden:

1. Öffnen der [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) für Ihr IoT-Gerät.

2. In der *Apps* im Menü Ihrer app zu installieren, indem Sie das app-Paket wird hochgeladen.
 ![Installieren der App](../media/AppInstaller/install-app.gif)

3. Bereitstellen der app an.

4. Die Anwendung wird jetzt in der Liste der Anwendungen auf Ihrem Gerät angezeigt werden.
 ![App-Liste](../media/AppInstaller/AppList.png)


## <a name="using-provisioning-package-from-wcd"></a>Verwenden die Bereitstellung eines Pakets aus WCD
Sie können ein Bereitstellungspaket erstellen, mit der app und das Paket auf dem Gerät installieren. Diese Methode funktioniert auch auf Geräten, die nicht über eine Internetverbindung verfügen, und ist die bevorzugte Methode für die Installation der Lizenzdatei Store. Beispielsweise kann diese Factory-Szenarien, in dem das Gerät nicht mit dem Internet verbunden ist, aber die primäre app ist eine UWP-app Store angemeldet.

> [!NOTE]
> Die Package Family Name (PFN) finden Sie im Windows Dev Center unter **App-Verwaltung > App-Identität**

1. Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. Wählen Sie **Erweiterte Bereitstellung**, geben Sie den Namen des Projekts und einer Beschreibung

3. Wählen Sie Windows 10 IoT Core, für die projekteinstellungen, und überspringen Sie die Bereitstellung paketimports

4. Erweitern Sie auf der linken Seite **Laufzeiteinstellungen** und klicken Sie auf **Universal-App installieren > Benutzer Kontext-App**

5. Geben Sie den Paketfamiliennamen Ihrer app und klicken Sie auf **hinzufügen**

6. Unter den neu hinzugefügten PFN
    - Fügen Sie die AppX-Datei und die zugehörigen Abhängigkeiten hinzu.
    - Legen Sie die DeploymentOptions "-Force-Ziel Anwendung schließen"

7. Für Store apps signiert wird, müssen Sie die Lizenz an. Unter UserContextAppLicense,
    - Hinzufügen von LicenseProductID (als LicenseID in der XML-Lizenzdatei verfügbar)
    - Ändern Sie die Lizenz XML-Erweiterung zum *.ms-Windows-Store-License*.
    - Wählen Sie die Lizenz-Produkt-ID auf der linken Seite, und navigieren Sie Ihrer Lizenzdatei, um LicenseInstall Feld zuweisen

8. Für signierte nicht über den Store-apps müssen Sie zum Hinzufügen der Datei app.cer unter **Zertifikate > RootCertificates** 

9. Das Paket exportieren

10. Kopieren Sie die exportierte ppkg-Datei _C:\Windows\Provisioning\Packages_ auf dem IoT-Gerät mit [SSH](../connect-your-device/SSH.md) oder [Powershell](../connect-your-device/powershell.md)) und neu starten. Wenn das Gerät neu gestartet, wird das Paket verarbeitet, und die app installiert ist.


## <a name="add-to-the-iot-core-imageffu"></a>Das IoT Core image(.ffu) hinzufügen   
Sie können die app als Teil des IoT Core-Images sich selbst hinzufügen. Dies ist die weit verbreitete Mechanismus für OEMs. 

Finden Sie unter Vorgehensweise [Hinzufügen einer app zu Ihrem Image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) und [Beispiel-app-Paket](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).
