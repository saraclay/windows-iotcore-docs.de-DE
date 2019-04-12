# <a name="contributing-to-the-windows-10-iot-documentation"></a>Mitwirkung an der Windows 10 IoT-Dokumentation

Vielen Dank für Ihr Interesse an unserer Dokumentation. Wir schätzen Ihr Feedback, Änderungen, Ergänzungen und Unterstützung bei der Verbesserung der Dokumentation. Diese Seite behandelt die grundlegenden Schritte und die Richtlinien für Ihren Beitrag.

## <a name="sign-a-cla"></a>Unterzeichnen einer CLA

Wenn Sie mehr als ein paar Zeilen beitragen möchten, und Sie nicht bei Microsoft angestellt sind sind, müssen Sie [signieren Sie eine Microsoft Contribution Licensing Agreement (CLA)](https://cla.microsoft.com/). 

## <a name="proposing-a-change"></a>Änderungsvorschlägen

Um eine Änderung an der Dokumentation wird empfohlen, gehen Sie folgendermaßen vor:

1. Wenn Sie die Seite "Docs.microsoft.com" anzeigen, klicken Sie auf die **bearbeiten** Schaltfläche oben rechts auf der Seite.  Sie gelangen auf die entsprechende Markdown-Quelldatei in die [GitHub-Repository](https://github.com/MicrosoftDocs/windows-iotcore-docs).  Wenn Sie bereits im GitHub-Repository enthalten sind, können Sie einfach zur Quelldatei navigieren, die Sie ändern möchten.
2. Wenn Sie bereits über ein GitHub-Konto haben, klicken Sie auf **registrieren** in der oberen rechten, und ein neues Konto erstellen.
3. Der GitHub-Seite, die Sie ändern möchten, klicken Sie auf das Stiftsymbol. 
4. Ändern Sie die Datei, und verwenden Sie die Registerkarte "Vorschau", um sicherzustellen, dass die Änderungen gut aussehen.
5. Wenn Sie fertig sind, committen Sie Ihre Änderungen, und öffnen Sie eine Pull-Anforderung.

Nachdem Sie den Pull Request erstellt haben, überprüft ein Mitglied der Windows 10 IoT-Team. Wenn Ihre Anforderung akzeptiert wird, werden Updates in veröffentlicht [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).

## <a name="making-more-substantial-changes"></a>Vornehmen größerer Änderungen

Um wesentliche Änderungen an einem vorhandenen Artikel vornehmen, hinzufügen oder ändern Sie die Bilder oder einen neuen Artikel beitragen, es wird empfohlen forken des Repositorys in Ihrem GitHub-Konto (klicken Sie auf die Schaltfläche "Verzweigung" in der oberen rechten Ecke des der [GitHub-Repository](https://github.com/MicrosoftDocs/windows-iotcore-docs), und klicken Sie dann Erstellen eines lokalen Klons (klicken Sie auf die grüne Schaltfläche der "Clone or Download", geben Sie die Kopie in die Zwischenablage, und Sie dann in der Befehlszeile Sie `git clone <paste your repo clone link>`).

Wir bitten Sie auch, die vor dem einen neuen Artikel, um sich die folgenden Fragen stellen beitragen...
* Eingeschlossen ich eine und nur eine # auf Titel (Äquivalent zu H1 im HTML-Format) haben? 
* Befindet sich im Titel meiner neuen Artikels im Präsens und konsistent mit den anderen Dokumentationen die Zeitform Verb (falls zutreffend)?
* Ist alle meine Grammatik richtig?
* Ich – Wenn einen neuen Artikel beitragen - hinzugefügt meinen Artikel, um die entsprechende Kategorie als auch aktualisiert TOC.md?
* Ich ordnungsgemäß formatiert wurden URLs [aussehen](https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md) nicht: https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md
* Haben Sie über mindestens zwei Personen, die Ihr neuen Artikel überprüfen?
* Haben Sie kontaktiert Sara (Saclayt) oder Namrata (Namkedia) Wenn Sie nicht sicher sind, alles sind?

Wenn Ihre neue Artikel angenommen werden, empfehlen wir Folgendes:
* Den Artikel für Ihr Team frei! Blenden Sie nicht Ihre Entdeckung - Kollegen wissen zu lassen.
* Befolgen Sie die Kommentare für Ihre Artikel durch Klicken auf die Schaltfläche "Folgen" unter dem Kommentarfeld ein. Auf diese Weise werden Sie auf die Kommentare aktualisiert sein, die Ihren Artikel angezeigt werden kann.

Weitere Informationen finden Sie unter [Verzweigen eines Repositorys](https://help.github.com/articles/fork-a-repo/). Beachten Sie, dass wir keine PRs zusammengeführt wird, die auf der live-Verzweigung. Stellen Sie sicher, dass Sie einen Pull Request zum master-Branch übermittelt werden.

Wenn Sie mit der Verwendung von Git nicht vertraut sind, versuchen Sie es der [Lynda.com Git Essentials Training](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html).

## <a name="authoring-your-contribution"></a>Erstellen Ihren Beitrag

Sobald Sie verzweigt haben und das Repository auf Ihrem lokalen Computer geklont haben, können Sie beginnen, mit dem Texteditor Ihrer Wahl erstellen.  Natürlich sollten [Visual Studio Code](https://code.visualstudio.com/), ein kostenloses lightweight-open-Source-Editor von Microsoft. Um Hilfe zur Markdown-dokumenterstellung, finden Sie in diesem [Markdown ist für alle Benutzer! Poster](windows-iotcore/media/DocsMarkdownPoster.pdf) mit alles über die Grundlagen, die Sie wissen müssen. Sie auch ausdrucken und hängen Sie es an der Wand als Erinnerung an beitragen. 

## <a name="submitting-your-contribution-and-filing-a-pull-request-pr"></a>Übermitteln Ihren Beitrag und einen Pull Request (PR) einreichen

Sobald Sie bereit sind für die Änderungen der remote-Repository hinzufügen, damit sie für die Veröffentlichung bereitgestellt werden, geben Sie die folgenden Schritte aus, in der Befehlszeile aus:
- `git status`: Mit diesem Befehl zeigt Dateien Sie geändert haben, sodass Sie bestätigen können, dass Sie diese Änderungen zu übernehmen. 
- `git add -A`: Dieser Befehl teilt Git, um alle Ihre Änderungen hinzuzufügen. Wenn Sie lieber nur hinzufügen, die Änderungen an einer bestimmten Datei vorgenommen wurden, und geben Sie stattdessen den Befehl: `git add <file.md>`, wobei "file.md" den Namen der Datei, die mit Ihrer Änderungen darstellt.
- `git commit -m “Fixed a few typos”`: Dieser Befehl teilt Git, um die Änderungen zu übernehmen, die Sie hinzugefügt haben, im vorherigen Schritt, und eine kurze Meldung zur Beschreibung der Änderungen, die Sie vorgenommen.
- `git push origin <yourbranchname>`: Dieser Befehl sendet die Änderungen an das remote-Repository, das Sie auf GitHub ("Ursprung") in den Branch verzweigt, die Sie angegeben haben. Da Sie das Repository in Ihr eigenes GitHub-Konto verzweigt haben, können Sie gerne, Ihre Arbeit zu erledigen, der **entwickeln** Branch. 

Wenn Sie mit Ihren Änderungen zufrieden und bereit, um einen Pull Request zu übermitteln sind:
- Wechseln Sie zu Ihrem Fork des Repositorys IoT: https://github.com/your-github-alias/windows-iotcore-docs.
- Klicken Sie auf die Schaltfläche "New pull Request". (Die "Basis-Verzweigung:", wird er als "MicrosoftDocs/Windows-Iotcore-Docs", die "Head Fork:" sollte angezeigt werden Ihrem Fork des Repositorys und den Branch, in dem Sie Ihre Änderungen vorgenommen haben.) Sie können auch hier die Änderungen überprüfen. 
- Klicken Sie auf die grüne Schaltfläche "Create Pull Request". Klicken Sie dann aufgefordert, Ihr Pull Request einen Titel und eine Beschreibung zu erhalten, und klicken Sie dann die Schaltfläche "Create Pull Request" noch einmal.

Nach Ihren Beitrag an das Remoterepository übertragen, Sie erhält eine e-Mail von *Open Publishing Builddienst* darüber informiert, ob Ihr Beitrag wurde erfolgreich erstellt, und Verknüpfen mit Fehler Warnungen wie z. B. auf fehlerhafte Links, klicken Sie auf der enthält Links zu finden in Ihre Inhalte auf der Website bereitgestellt.

Nachdem Sie Ihren Beitrag überprüft haben, auf die [Stagingsite für Windows 10 IoT-Dokumentation](https://review.docs.microsoft.com/en-us/windows/iot-core/) und sind davon überzeugt, dass Ihre Änderungen live veröffentlicht werden sollen, müssen Sie einen Pull Request (PR) einreichen.

Sobald Ihr Pull Request übermittelt wurde, überprüft ein Mitglied der Windows 10 IoT-Dokumentationsteam. Wenn es akzeptiert wird, Sie werden die Änderungen anzuzeigen, auf die [Stagingwebsite](https://review.docs.microsoft.com/en-us/windows/iot-core). Diese Updates werden schließlich veröffentlicht werden live [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).

## <a name="working-with-branches"></a>Arbeiten mit Verzweigungen

Die [Windows 10 IoT-Docs-GitHub-Repository](https://github.com/MicrosoftDocs/windows-iotcore-docs) nutzt zwei Hauptknoten der übergeordneten Branches: [Entwickeln](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/develop), diese Inhalte kann überprüft werden, auf die [Stagingwebsite](https://review.docs.microsoft.com/en-us/windows/iot-core), und [Live](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/live), für Inhalt angezeigt wird, auf die [Livewebsite](https://docs.microsoft.com/windows/iot-core). 

Wenn Sie Beiträge zu vornehmen, bitte senden Sie Ihre Pull Request (PR) die **entwickeln** Branch. Dieser Branch kann auf der Stagingsite angezeigt werden und sollte nur Beiträge, die Livemigration veröffentlicht werden, sind enthalten.

## <a name="using-issues-to-provide-feedback-on-iot-documentation"></a>Mithilfe der Probleme zum Bereitstellen von Feedback in IoT-Dokumentation

Bereitstellen von Feedback und nicht direkt ändern, tatsächliche Dokumentationsseiten [erstellen Sie ein Problem](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).

Vergessen Sie nicht, den Titel des Themas und die URL für die Seite anzugeben.

## <a name="additional-resources"></a>Zusätzliche Ressourcen
- [Erste Schritte mit dem Schreiben und zu formatieren auf GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Zusätzliche Ressourcen für Microsoft-Mitarbeiter
- [Verbinden Sie Ihr GitHub-Konto und MS-alias](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Ressourcen für das Schreiben von Markdown](https://review.docs.microsoft.com/en-us/windows-authoring-guide/writing-guidance/writing-markdown)
