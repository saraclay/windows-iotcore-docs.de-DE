---
title: Mithilfe von DISM in Windows 10 IoT Core flash
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Erfahren Sie, wie Sie DISM verwenden, um Windows 10 IoT Core auf eine Micro SD-Karte zu aktualisieren.
keywords: Windows Iot – DISM, Wartung Imageverwaltung, SD-Karte, Flash, Betriebssystem
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514109"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a>Mithilfe von DISM in Windows 10 IoT Core flash

> [!NOTE]
> Offlinewartung DISM wird nicht unterstützt. Sie erhalten die folgende Fehlermeldung angezeigt, wenn Sie versuchen, eine FFU IoT Core bereitstellen: Die Anforderung wird nicht unterstützt.
> Das Image verfügt nicht über einen Namen, und es ist wahrscheinlich eine Mobile/Onecore-FFU, dies wird derzeit nicht unterstützt.
> Fehler 0 x 80070032 FfuMountImage #160.

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a>Eine alternative Methode zum IoT-Dashboard zum Blinken eine FFU

Sie können Deployment Image Servicing and Management(Dism.exe) verwenden, um Windows 10 IoT Core auf die SD-Karte zu aktualisieren. Sie benötigen eine FFU-Bilddatei, die den Typ Ihres Geräts entspricht. 

* Öffnen Sie eine administratoreingabeaufforderung, und navigieren Sie zu dem Ordner, die mit Ihrer lokalen flash.ffu-Datei.

* -Plug-in Ihrer SD-Karte auf Ihrem Computer. 

* Suchen Sie die Anzahl der Datenträger, die die SD-Karte auf Ihrem Computer ist.  Dies wird verwendet, wenn das Abbild, im nächsten Schritt angewendet wurde.  Zu diesem Zweck können Sie den Diskpart-Hilfsprogramm verwenden.  Führen Sie die folgenden Befehle aus:

        c:\FFUFolder>diskpart

        DISKPART>list disk

    Es sollten alle Speichergeräte, die an den Computer angeschlossen aufgelistet. 

    ![Datenträger der DISM-Liste](../media/Dism/DiskpartListDisk.png)

    Beachten Sie die Anzahl der Datenträger, und geben Sie beenden, Beenden von Diskpart. 

        DISKPART>exit

* Die Eingabeaufforderung mit Administratorberechtigungen aus, wenden Sie das Abbild auf die SD-Karte, indem Sie den folgenden Befehl ausführen (PhysicalDriveN mit dem Wert ersetzen Sie Sie finden Sie im vorherigen Schritt, zum Beispiel, in diesem Fall ist die SD-Karte Datenträgernummer 4, daher verwenden wir `/ApplyDrive:\\.\PhysicalDrive4` Siehe unten)

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* Klicken Sie auf das Symbol "Hardware sicher entfernen" in Ihrer Taskleiste, und wählen Sie den USB-SD-Kartenleser sicher aus dem System entfernen.  Dies unterlassen, kann eine Beschädigung des Images führen.
