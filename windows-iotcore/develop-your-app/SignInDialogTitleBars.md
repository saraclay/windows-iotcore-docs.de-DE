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
# <a name="title-bars-for-sign-in-dialogs"></a><span data-ttu-id="7cac7-104">Titelleisten für die Anmeldung von Dialogfeldern</span><span class="sxs-lookup"><span data-stu-id="7cac7-104">Title bars for sign in dialogs</span></span>

<span data-ttu-id="7cac7-105">Beabsichtigt, Windows 10 IoT Core zeigt nicht an eine Anwendung-Rahmen um das Anwendungsfenster \- erhalten Sie im Vollbildmodus.</span><span class="sxs-lookup"><span data-stu-id="7cac7-105">By design, Windows 10 IoT Core does not display an application frame around your application's window \- you get the full screen.</span></span> <span data-ttu-id="7cac7-106">Allerdings haben in Version 1809 mehrere Systemdialogfelder erhalten eine Titelleiste mit Schaltfläche "Schließen", damit Benutzer aus, abgebrochen werden soll, selbst wenn der Inhalt des Dialogfelds keine Schaltfläche "Abbrechen" enthält.</span><span class="sxs-lookup"><span data-stu-id="7cac7-106">However, in version 1809, several system dialog boxes have been given a title bar containing close button to allow the user to cancel out of them, even when the content of the dialog box provides no cancel button.</span></span>

## <a name="sign-in-dialog-boxes"></a><span data-ttu-id="7cac7-107">Melden Sie sich die Dialogfelder</span><span class="sxs-lookup"><span data-stu-id="7cac7-107">Sign in dialog boxes</span></span>

<span data-ttu-id="7cac7-108">Dialoge, die diese Funktion hinzugefügt haben, sind die Identity-Dialogfelder - für die Anmeldung bei Microsoft-Konten (MSA) und Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="7cac7-108">The dialogs that have this feature added are the identity dialogs - for signing in to Microsoft Accounts (MSA) and Azure Active Directory (AAD).</span></span> <span data-ttu-id="7cac7-109">Diese können in Ihrer Anwendung verwendet werden, siehe die [Web-Kontoverwaltung Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in die [Microsoft UWP-app-Beispiele Repository](https://github.com/Microsoft/Windows-universal-samples).</span><span class="sxs-lookup"><span data-stu-id="7cac7-109">These can be used in your application as shown in the [Web Account Management sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in the [Microsoft UWP app samples repo](https://github.com/Microsoft/Windows-universal-samples).</span></span>

## <a name="configuring-the-title-bar-height"></a><span data-ttu-id="7cac7-110">Konfigurieren die Höhe der Titelleiste</span><span class="sxs-lookup"><span data-stu-id="7cac7-110">Configuring the title bar height</span></span>

<span data-ttu-id="7cac7-111">Die Titelleiste verfügt über eine Standardhöhe von 25 Pixel, und kann auf einen beliebigen Wert größer, bis zu 50 Pixel festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="7cac7-111">The title bar has a default height of 25 pixels, and can be set to any greater value up to 50 pixels.</span></span> <span data-ttu-id="7cac7-112">Alle Werte größer als 50 wird auf 50 geklammert.</span><span class="sxs-lookup"><span data-stu-id="7cac7-112">Any value greater than 50 will be clamped to 50.</span></span> <span data-ttu-id="7cac7-113">Die Höhe kann kleiner als 25 werden, aber beachten Sie die möglicherweise negative Auswirkungen auf die benutzerfreundlichkeit bei der die Höhe der Schaltfläche "Schließen".</span><span class="sxs-lookup"><span data-stu-id="7cac7-113">The height can be less than 25, but consider the possibly negative effect on the user's experience when deciding the height of the close button.</span></span>

<span data-ttu-id="7cac7-114">Als Beispiel für die Höhe der Titelleiste festzulegen, x 32 Pixel besitzen, können in PowerShell Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="7cac7-114">As an example, to set the title bar height to 32 pixels, in PowerShell you could do the following:</span></span>
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> <span data-ttu-id="7cac7-115">Für ein OEM-Image erstellen, ist der bevorzugte Mechanismus für die Einstellungswerte für die Registrierung mit dem `OEMInput.xml` Datei ausführlicher [laufzeitanpassungen](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span><span class="sxs-lookup"><span data-stu-id="7cac7-115">For creating an OEM image, the preferred mechanism for setting registry values is with the `OEMInput.xml` file discussed in [Runtime customizations](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span></span>
