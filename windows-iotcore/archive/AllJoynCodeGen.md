---
title: Übersicht über die AllJoynCodeGen
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Informationen Sie zu AllJoynCodeGen, ein Tool zur codegenerierung, die eine vollständige Windows-Runtime-Komponente, die über AllJoyn-Schnittstellen generiert.
keywords: Windows Iot, dass AllJoyn
ms.openlocfilehash: c8e9f08c5565c7e4252e1b15858c08402eedb712
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513730"
---
> [!NOTE]
> Sie zeigen die archivierte Dokumentation. AllJoyn wird nicht mehr von Windows 10 IoT unterstützt. Öffnen Sie ein Problem auf GitHub, oder lassen Sie uns Feedback in den Kommentaren, Fragen.

# <a name="alljoyncodegen-overview"></a>Übersicht über die AllJoynCodeGen

Wir haben ein Tool zur codegenerierung, AllJoynCodeGen, erstellt, die eine vollständige Windows-Runtime-Komponente, die über eine oder mehrere AllJoyn-Schnittstellen abgeleitet, eine Spezifikation oder ein Gerät eine XML-Beschreibung generiert.

Die Windows-Runtime-Komponente, die von diesem Tool generierte in einer beliebigen unterstützten Sprache genutzt werden kann (JS, C#, C++/CX usw.) mithilfe von APIs, die in die universelle Windows-SDK verfügbar sind. Dies bedeutet, dass die gleiche Komponente auf allen Plattformen verwendet werden kann, die das AllJoyn OneCore-Paket (Router-Dienst und C-API-Dll). Entwickler können dann die Komponente, um ein Producer und/oder ein Consumer dieser Schnittstelle zu erstellen. 

**Beachten Sie** für Weitere Informationen zu den C-AllJoyn-APIs, Sie können den AllJoyn Core SDK und die Dokumentation unter [der AllSeen Alliance](http://go.microsoft.com/fwlink/?LinkId=524584).

## <a name="how-does-alljoyncodegen-work"></a>Wie funktioniert die AllJoynCodeGen?

Der grundlegende Ablauf sieht wie folgt aus:

1. Eine XML-Datei erstellt, in der AllJoyn-XML (derzeit DBus Introspection-Format), die den Dienst beschreibt ist das Codegen-Tool erfasst werden.
2. Die AllJoynCodeGen-Tool generiert Code, der zu einer Windows-Runtime-Komponente führt. Dieser generierte Code basiert auf **MSAJAPI.lib** und [Windows.Devices.AllJoyn](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx) aus dem Windows 10-SDK.
3. Der Entwickler erstellt eine Anwendung, die diese Komponente verwendet.
4. Zur Laufzeit wird die Anwendung des Entwicklers die Windows-Runtime-Komponente, die vom Tool generierten geladen (z. B.: foo.dll,) als auch die mitgelieferten DLLs **MSAJAPI.dll** und **Windows.Devices.AllJoyn.dll**.

Im folgenden Workflowdiagramm veranschaulicht diesen Prozess:

![Dass AllJoyn-CodeGen-Diagramm](../media/AllJoyn/alljoyncodegen.png)

## <a name="running-from-the-command-line"></a>Ausführen über die Befehlszeile

Das Tool AllJoynCodeGen ist derzeit als ein Befehlszeilentool, das im Lieferumfang von Windows 10 SDK vorhanden. Führen Sie das Tool übergeben Sie eine gültige XML-Datei mithilfe der folgenden Zeichenfolge:

    AllJoynCodeGen –i Foo.xml –o c:\users\developer1\documents\Foo\

## <a name="reviewing-the-output"></a>Überprüfen die Ausgabe

Die generierten Klassen zu umschließen Funktionalität, die von der Kern-C-API verfügbar gemacht werden. Da es sich bei der generierte Code eine Abstraktion ist, ist dies keine 1: 1 Zuordnung. Die folgende Tabelle zeigt, welcher Kern C++ APIs werden von jeder Klasse generierten Code eingeschlossen. Für die generierten Namen in der Tabelle werden die folgenden Platzhalter verwendet:

* `<Foo>` Der Name der Schnittstelle definiert die XML-Datei
* `<Signal>` Der Name eines Signals zu stammt aus der XML-Datei
* `<Method>` Der Name einer Methode, die XML-Datei entnommen
* `<Property>` Der Name einer Eigenschaft, die XML-Datei entnommen


> | Windows-Runtime-Klasse |  | Beschreibung | Core C++ API |
> | ------------------------ | --- | --------- | ---------- |
> | `<Foo>`Watcher |  | Sucht nach Hersteller, die den Zieldienst angekündigt werden soll. | *BusListener* Klasse. *BusAttachment* Klasse |
> | `<Foo>`JoinSessionResult |  | Meldet den Erfolg oder Misserfolg der beitreten zu einer Sitzung, und stellt eine `<Foo>Consumer` -Instanz für die Sitzung, wenn die Verknüpfung erfolgreich war. | *JoinSessionAsyncCB* class; *QStatus* |
> | `<Foo>`Producer |  | Kündigt einen Dienst, und macht Sie Handler für AllJoyn-Ereignisse verfügbar. | *BusObject* Klasse. *BusAttachment* Klasse. *InterfaceDescription* Klasse. *SessionPortListener* Klasse. *Nachricht* Klasse |
> | `<Foo>`Signale |  | Macht Methoden und -Handler zum Senden und Empfangen von Signalen. Wird von sowohl Producer und Consumer verwendet. | *BusObject* Klasse. *InterfaceDescription* Klasse. *Nachricht* Klasse |
> | `<Foo>`Consumer |  | Interagiert mit einem Dienst, nachdem diese ermittelt wurde. | *ProxyBusObject* Klasse. *InterfaceDescription* Klasse. *SessionListener* Klasse. *Nachricht* Klasse |
> | `<Foo>``<Method>`CalledEventArgs |  | Argumente übergeben an Methoden in `EventAdapters.<Foo>ServiceEventAdapter`. | *Nachricht* Klasse |
> | `<Foo>``<Method>`Ergebnis |  | Ein, die Implementierungen der Dienstmethode in der ich<Foo>Dienst, um den Erfolg oder Fehler des Aufrufs, sowie alle Rückgabewerte melden. | *Nachricht* Klasse. *QStatus* |
> | `<Foo>``<Signal>`ReceivedEventArgs |  | Argumente zu übergeben, auf ein Signal in <Foo>signalisiert. | *Nachricht* Klasse |


## <a name="build-guide"></a>Handbuch zu erstellen

#### <a name="creating-the-component"></a>Erstellen der Komponente

Der generierte Code muss in einer Komponente enthalten sein, die den gleichen Schnittstellennamen als der XML-Code gemeinsam. Wenn der XML-Code für einen Toaster als com.microsoft.sample.toaster definiert ist, würden wir z. B. com.microsoft.sample eine Common Language Runtime-Komponente erstellen. 

Alternativ können Sie die Komponente den Namen (z. B. FooCodeGenComponent) angezeigt werden sollen, jedoch müssen Sie manuell aktualisieren, den Stamm-Namespace in den Projekteigenschaften auf den Namen der Schnittstelle identisch sein.

> [!TIP]
> Sie finden den Stamm-Namespace in der Datei "PCH.h", die aus dem AllJoynCodeGen-Tool generiert wird.
