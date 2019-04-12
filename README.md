## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft Open Source Verhaltenskodex

Dieses Projekt folgt dem [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/).
Weitere Informationen finden Sie unter den [Code von durchführen – häufig gestellte Fragen](https://opensource.microsoft.com/codeofconduct/faq/) oder wenden Sie sich an [ opencode@microsoft.com ](mailto:opencode@microsoft.com) weitere Fragen und Kommentare.

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>Mitwirken an der Windows 10-IoTCore-Dokumentation

## <a name="legal-notices"></a>Rechtliche Hinweise
Microsoft und alle Mitwirkenden gewähren Ihnen eine Lizenz für die Microsoft-Dokumentation und andere Inhalte in diesem Repository im Rahmen der [Creative Commons Namensgebung 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), siehe Datei [LIZENZ](LICENSE), sowie eine Lizenz für den gesamten Code in dem Repository im Rahmen der [MIT-Lizenz](https://opensource.org/licenses/MIT), siehe Datei [LIZENZCODE](LICENSE-CODE).

Microsoft, Windows, Microsoft Azure und/oder andere Microsoft-Produkte und -Dienste, auf die in der Dokumentation verwiesen wird, sind möglicherweise Marken oder eingetragene Marken von Microsoft in den USA und/oder anderen Ländern.
Die Lizenzen für dieses Projekt berechtigen Sie nicht dazu, Microsoft-Namen, -Logos oder -Marken zu verwenden.
Microsofts allgemeine Markenrichtlinien finden Sie unter http://go.microsoft.com/fwlink/?LinkID=254653.

Informationen zum Datenschutz finden Sie unter https://privacy.microsoft.com/en-us/

Microsoft und die Beitragenden behalten sich alle weiteren Rechte vor, ob gemäß den jeweiligen Urheber-, Patent- oder Markenrechten oder ob implizit, durch rechtshemmenden Einwand oder anderweitig.

## <a name="contributing"></a>Beitragen

Dies ist das Repository für Windows 10 IoT **Dokumentation** an gehostete [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).

Wenn Sie möchten, finden Sie unter Neues Coverage oder Feedback haben, erwägen Sie [ **beitragen**](/CONTRIBUTING.md).  Sie können den vorhandenen Inhalt bearbeiten, neue Inhalte hinzufügen oder einfach neu erstellen [Probleme](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues). Wir werden sehen Sie sich Ihre Vorschläge und wird arbeiten zusammen, um sie in der Dokumentation zu integrieren.

Um Inhalt zu bearbeiten, klicken Sie auf Bearbeiten, für den Artikel, dem Sie ändern möchten:

![GIF-Datei zum Bearbeiten von docs](windows-iotcore/media/edit-doc.gif)


Sie können auch Klonen oder laden das Repository, um Änderungen vorzunehmen:

![GIF zum Klonen oder Herunterladen-Repository](windows-iotcore/media/download-repo.gif)

Sie müssen auch einen Bearbeiter oder Prüfungen auf genehmigt werden Pull Requests hinzufügen:

![Ihr Pull Request Reviewer hinzugefügt](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>Konventionen
  - Beim Hinzufügen einer Seite müssen Sie einen Eintrag hinzufügen, damit es in [toc.md](windows-iotcore/TOC.md) angezeigt.
  - Ein Ordner kann weitere Ordner enthalten oder `readme.md`s
  - Ordner/Verzeichnisnamen werden durch Bindestriche getrennt (z. B. `f12-tools`) und Kleinbuchstaben. Sie werden auf der docs.microsoft.com-Website-URLs verwendet. Verwenden Sie keine Unterstriche oder PascalCase/CamelCase.


## <a name="other-text-elements"></a>Andere Textelemente

Diese anderen Textelemente haben Stile zur Verfügung:

* Unsortierte Listen
* Haben Sie die normale Aufzählungszeichen
   * Sie können auch Aufzählungszeichen schachteln.
   * Listen mit Aufzählungszeichen sollte mehr als ein Eintrag vorhanden ist.
* Ziemlich standard

1. Sortierte Listen
2. Reguläre alten westliche Nummerierung verwendet.
3. Sollte verwendet werden, nur, wenn Sie eine Liste wirklich Reihenfolge enthält.

_________________________

Horizontale Linien sind verfügbar. Es wird empfohlen, mit ihnen nur selten übersichtlicher gestalten möchten.
Kombinieren Sie horizontale Linien mit Überschriften-Tags nicht; Einige verwendet bereits Linienarten für visuelle Hierarchie.
Darüber hinaus Anmerkungen zu dieser Version (siehe unten) in der Mitte nummerierte Listen nicht kombiniert werden. Dies verwirrt, mit der Nummerierung Reihenfolge.

## <a name="displaying-code"></a>Anzeigen von code

Sie können die Inline `code` Markdown-Syntax (mit dem Graviszeichen).

Sie können Codeblöcke anzeigen wie folgt:

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>Tabellen

| Sie können     | Verwenden von Headern | für Tabellen    |
|-------------|-------------|-------------:|
| Linksbündig| Es sei denn, ein #  | 456          |
| Textwert  | Weitere text   | $0.00        |

## <a name="notes"></a>Hinweise

Verwenden Sie die Anmerkungen zu dieser Version nur selten. Sie sind die Blöcke, die entworfen, um "nicht-Fehleranzahl-It" Informationen hervorzuheben.

Es gibt vier verschiedene Versionen von Notizen, die derzeit im Stil:
- HINWEIS
- WARNUNG
- TIPP
- WICHTIG


Verwenden Sie mehrzeilige Blockquote Anmerkungen zu dieser eine > vor jeder Zeile der Notizen wie im folgenden Beispiel gezeigt.

## <a name="images"></a>Abbilder

Bilder gespeichert werden sollen, einem `media` Ordner und mit einem relativen Pfad verwiesen wird:

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>Verhaltenskodex
Dieses Projekt folgt dem [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/). Weitere Informationen finden Sie unter den [Code von durchführen – häufig gestellte Fragen](https://opensource.microsoft.com/codeofconduct/faq/) oder wenden Sie sich an [ opencode@microsoft.com ](mailto:opencode@microsoft.com) weitere Fragen und Kommentare.
