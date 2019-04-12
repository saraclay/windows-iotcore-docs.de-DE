---
title: Eingebetteten Modus
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Informationen Sie zum Konfigurieren von Windows um eingebetteten Modus aktivieren hintergrundanwendungen und andere Funktionen zu ermöglichen.
keywords: Windows Iot, eingebetteten Modus, Programme im Hintergrund
ms.openlocfilehash: 1944cec09400cff4d895bb9e55b89b3b19a3f5f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512321"
---
# <a name="embedded-mode"></a>Eingebetteten Modus

Eingebetteter Modus wird unter Windows IoT Core und Windows IoT Enterprise unterstützt. Eingebetteter Modus ermöglicht:

* [Programme im Hintergrund (Weitere Informationen)](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* Verwenden der LowLevelDevice-Funktion
* Verwenden der Management-Funktion

Eingebetteter Modus ist immer auf Fenster IoT Core aktiviert werden.
Eingebetteter Modus muss aktiviert werden, indem Sie die folgenden Schritte auf Windows IoT Enterprise.

## <a name="background-applications"></a>Programme im Hintergrund

Hintergrundanwendungen werden mit die Hintergrundanwendung (IoT)-Vorlage in Visual Studio erstellt.
Weitere Informationen zum Erstellen [Hintergrundanwendungen](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).

Programme im Hintergrund ausführen, ohne Unterbrechung und ohne Einschränkungen. Auch wenn die hintergrundanwendung aus irgendeinem Grund beendet wird, und eingebettete aktiviert ist die hintergrundanwendung wird durch das System neu gestartet werden.

Während das System automatisch hintergrundanwendungen neu gestartet wird, müssen zum Sperren von Systemfunktionen zu verhindern, dass Benutzer beenden oder beeinträchtigt den Betrieb von Hintergrundanwendungen aktiviert sein.

## <a name="lowleveldevice-capability"></a>LowLevelDevice-Funktion

Die Funktion LowLevelDevice ermöglicht den Zugriff auf Low-Level Hardwareschnittstellen wie GPIO, I2C und SPI.

* [Hauptverkaufsargument Sample(GPIO)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [Beschleunigungsmesserbeispiel](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

## <a name="systemmanagment-capability"></a>SystemManagment-Funktion

Wenn Sie die SystemManagment-Funktionen für Ihre Anwendung aktivieren, ist dies den Satz von APIs, die nicht gesperrte abruft:  

* [Windows.System.ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System.ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows.Globalization.Language.TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>Debuggen von Hintergrundanwendungen

Wenn Debuggen auf einem Gerät, auf denen nicht Windows IoT Core ausgeführt wird, und Sie eine der folgenden Fehlermeldungen sehen müssen Sie sicherstellen, dass AllowEmbeddedMode auf dem Gerät aktiviert ist und der eingebetteten Modus-Dienst ausgeführt wird:

* Es sind keine weiteren Endpunkte von der endpunktzuordnung verfügbar.
* Dieses Programm ist durch Gruppenrichtlinien blockiert. Weitere Informationen wenden Sie sich an Ihren Systemadministrator.

## <a name="changing-the-mode"></a>Modus ändern
Um eingebetteten Modus zu aktivieren, Sie müssen ein Bereitstellungspaket erstellen, in der Abbilderstellung und der Configuration Designer (Windows ICD), die AllowEmbeddedMode festlegt = 1.  ICD installieren, müssen Sie zum Herunterladen und installieren das Windows ADK für Windows 10.

* [Das Windows ADK für Windows 10 herunterladen](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [Erfahren Sie mehr über die Neuigkeiten in das Windows ADK für Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. Wenn das ADK installieren auswählen **Abbilderstellung und der Configuration Designer (Windows ICD)**
2. Führen Sie nach der Installation Windows Imaging und Konfigurations-Designer (WICD).

    ![Symbol "WICD"](../media/EmbeddedMode/WICD_Icon.png)

3. Klicken Sie auf **Erweiterte Bereitstellung**.  Nennen Sie das Projekt **AllowEmbeddedMode** , und klicken Sie auf **Weiter**.
    ![Schritt 3](../media/EmbeddedMode/Step3.png)

4. Wählen Sie **üblich, alle Editionen von Windows** dann **Weiter**.
    ![Schritt 4](../media/EmbeddedMode/Step4.png)

5. Klicken Sie auf **Fertig stellen**.

    ![Schritt 5](../media/EmbeddedMode/Step5.png)

6. Klicken Sie in das Suchfeld **EmbeddedMode** , und klicken Sie dann auf **AllowEmbeddedMode**.

    ![Schritt 6](../media/EmbeddedMode/Step6.png)

7. Legen Sie den Wert des in der Mitte Bereich **AllowEmbeddedMode** zu **Ja** ![Step7](../media/EmbeddedMode/Step7.png)

8. Klicken Sie auf Exportieren > Bereitstellungspaket

    ![Step8](../media/EmbeddedMode/Step8.png)

9. Klicken Sie auf Weiter.

    ![Step9](../media/EmbeddedMode/Step9.png)

10. Klicken Sie auf Weiter.

    ![Step10](../media/EmbeddedMode/Step10.png)

11. Klicken Sie auf Weiter.

    ![Step11](../media/EmbeddedMode/Step11.png)

12. Klicken Sie auf erstellen.

    ![Schritt12 fort](../media/EmbeddedMode/Step12.png)

13. Um die eingebetteten Modus zu installieren. PPKG unter Windows IoT Enterprise Doppelklicken Sie auf der. PPKG.

14. Klicken Sie auf **Ja, hinzufügen**.
    Klicken Sie auf Ja, auf das Dialogfeld "LUA", wenn es angezeigt wird, und klicken Sie auf **Ja, hinzufügen** auf die unten gezeigte Dialogfeld.
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>Hintergrundanwendung für die Ausführung konfigurieren automatisch
1. Hintergrundanwendung automatisch bei der Ausführung zu konfigurieren, müssen Sie die Anweisungen zum [MinnowBoardMax SD-Karten erstellen](https://developer.microsoft.com/en-us/windows/iot/getstarted) , und kopieren Sie `D:\windows\system32\iotstartup.exe` (wobei "d:" der SD-Karte ist).

2. So erhalten Sie eine Liste der installierten Programme im Hintergrund-Typ:

        C:\> iotstartup list BackgroundApplication1

3. Die Ausgabe sollte den vollständigen Namen der einzelnen installierten Anwendungen Hintergrund enthalten, das wie folgt aussieht:

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. So konfigurieren Sie diese app auf Starttyp ausgeführt:

        C:\> iotstartup add headless BackgroundApplication1

6. Wenn der Hintergrund-Anwendung wurde erfolgreich zur Startliste hinzugefügt wurde sollte Folgendes angezeigt:

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. Neustarten des eingebetteten Modus-Geräts:

8. Sobald das Gerät neu gestartet wurde, wird der Hintergrund-Anwendung automatisch gestartet.  Der eingebetteten Modus-Dienst, der Hintergrundanwendungen verwaltet dauert einige Minuten, um zu starten.  Der Dienst eingebetteten Modus Hintergrundanwendungen auf Startliste zu überwachen, und stellen Sie sicher, dass sie neu gestartet zu erhalten, wenn sie beendet wird.  Wenn Hintergrundanwendung mehrere Male in kurzer Zeit beendet wird, wird sie nicht mehr gestartet.

9. So entfernen Sie die Hintergrund-Anwendung aus der Liste Starttyp:

        C:\> iotstartup remove headless BackgroundApplication1

10. Wenn der Hintergrund-Anwendung aus der Startliste entfernt wird, wird die Ausgabe wie folgt aussehen:

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
