---
title: Konfigurieren Sie die Höhe der Titelleiste für die Anmeldung in Dialogfeldern
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Erfahren Sie, wie Sie die Höhe der Titelleiste für die Anmeldung in Dialogfelder in Windows 10 IoT Core, Version 1809 konfigurieren.
keywords: Windows 10 IoT Core, Msa "," Aad "," Titlebar "," Schließen "," Abbrechen ", entwickelt, web, Konto WebAccountManagement, Anmeldung anmelden
ms.custom: RS5
ms.openlocfilehash: 69f59b4416c5db39d119994139eba4907035598e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513314"
---
# <a name="title-bars-for-sign-in-dialogs"></a>Titelleisten für die Anmeldung von Dialogfeldern

Beabsichtigt, Windows 10 IoT Core zeigt nicht an eine Anwendung-Rahmen um das Anwendungsfenster \- erhalten Sie im Vollbildmodus. Allerdings haben in Version 1809 mehrere Systemdialogfelder erhalten eine Titelleiste mit Schaltfläche "Schließen", damit Benutzer aus, abgebrochen werden soll, selbst wenn der Inhalt des Dialogfelds keine Schaltfläche "Abbrechen" enthält.

## <a name="sign-in-dialog-boxes"></a>Melden Sie sich die Dialogfelder

Dialoge, die diese Funktion hinzugefügt haben, sind die Identity-Dialogfelder - für die Anmeldung bei Microsoft-Konten (MSA) und Azure Active Directory (AAD). Diese können in Ihrer Anwendung verwendet werden, siehe die [Web-Kontoverwaltung Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in die [Microsoft UWP-app-Beispiele Repository](https://github.com/Microsoft/Windows-universal-samples).

## <a name="configuring-the-title-bar-height"></a>Konfigurieren die Höhe der Titelleiste

Die Titelleiste verfügt über eine Standardhöhe von 25 Pixel, und kann auf einen beliebigen Wert größer, bis zu 50 Pixel festgelegt werden. Alle Werte größer als 50 wird auf 50 geklammert. Die Höhe kann kleiner als 25 werden, aber beachten Sie die möglicherweise negative Auswirkungen auf die benutzerfreundlichkeit bei der die Höhe der Schaltfläche "Schließen".

Als Beispiel für die Höhe der Titelleiste festzulegen, x 32 Pixel besitzen, können in PowerShell Sie folgendermaßen vor:
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> Für ein OEM-Image erstellen, ist der bevorzugte Mechanismus für die Einstellungswerte für die Registrierung mit dem `OEMInput.xml` Datei ausführlicher [laufzeitanpassungen](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)
