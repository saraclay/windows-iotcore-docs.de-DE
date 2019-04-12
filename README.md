## <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="5364c-101">Microsoft Open Source Verhaltenskodex</span><span class="sxs-lookup"><span data-stu-id="5364c-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="5364c-102">Dieses Projekt folgt dem [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="5364c-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="5364c-103">Weitere Informationen finden Sie unter den [Code von durchführen – häufig gestellte Fragen](https://opensource.microsoft.com/codeofconduct/faq/) oder wenden Sie sich an [ opencode@microsoft.com ](mailto:opencode@microsoft.com) weitere Fragen und Kommentare.</span><span class="sxs-lookup"><span data-stu-id="5364c-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a><span data-ttu-id="5364c-104">Mitwirken an der Windows 10-IoTCore-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="5364c-104">How to contribute to Windows 10 IoTCore documentation</span></span>

## <a name="legal-notices"></a><span data-ttu-id="5364c-105">Rechtliche Hinweise</span><span class="sxs-lookup"><span data-stu-id="5364c-105">Legal Notices</span></span>
<span data-ttu-id="5364c-106">Microsoft und alle Mitwirkenden gewähren Ihnen eine Lizenz für die Microsoft-Dokumentation und andere Inhalte in diesem Repository im Rahmen der [Creative Commons Namensgebung 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), siehe Datei [LIZENZ](LICENSE), sowie eine Lizenz für den gesamten Code in dem Repository im Rahmen der [MIT-Lizenz](https://opensource.org/licenses/MIT), siehe Datei [LIZENZCODE](LICENSE-CODE).</span><span class="sxs-lookup"><span data-stu-id="5364c-106">Microsoft and any contributors grant you a license to the Microsoft documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the [LICENSE-CODE](LICENSE-CODE) file.</span></span>

<span data-ttu-id="5364c-107">Microsoft, Windows, Microsoft Azure und/oder andere Microsoft-Produkte und -Dienste, auf die in der Dokumentation verwiesen wird, sind möglicherweise Marken oder eingetragene Marken von Microsoft in den USA und/oder anderen Ländern.</span><span class="sxs-lookup"><span data-stu-id="5364c-107">Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.</span></span>
<span data-ttu-id="5364c-108">Die Lizenzen für dieses Projekt berechtigen Sie nicht dazu, Microsoft-Namen, -Logos oder -Marken zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5364c-108">The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.</span></span>
<span data-ttu-id="5364c-109">Microsofts allgemeine Markenrichtlinien finden Sie unter http://go.microsoft.com/fwlink/?LinkID=254653.</span><span class="sxs-lookup"><span data-stu-id="5364c-109">Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.</span></span>

<span data-ttu-id="5364c-110">Informationen zum Datenschutz finden Sie unter https://privacy.microsoft.com/en-us/</span><span class="sxs-lookup"><span data-stu-id="5364c-110">Privacy information can be found at https://privacy.microsoft.com/en-us/</span></span>

<span data-ttu-id="5364c-111">Microsoft und die Beitragenden behalten sich alle weiteren Rechte vor, ob gemäß den jeweiligen Urheber-, Patent- oder Markenrechten oder ob implizit, durch rechtshemmenden Einwand oder anderweitig.</span><span class="sxs-lookup"><span data-stu-id="5364c-111">Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel or otherwise.</span></span>

## <a name="contributing"></a><span data-ttu-id="5364c-112">Beitragen</span><span class="sxs-lookup"><span data-stu-id="5364c-112">Contributing</span></span>

<span data-ttu-id="5364c-113">Dies ist das Repository für Windows 10 IoT **Dokumentation** an gehostete [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).</span><span class="sxs-lookup"><span data-stu-id="5364c-113">This is the repository for Windows 10 IoT **documentation** hosted at [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).</span></span>

<span data-ttu-id="5364c-114">Wenn Sie möchten, finden Sie unter Neues Coverage oder Feedback haben, erwägen Sie [ **beitragen**](/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="5364c-114">If you would like to see new coverage or have feedback, please consider [**contributing**](/CONTRIBUTING.md).</span></span>  <span data-ttu-id="5364c-115">Sie können den vorhandenen Inhalt bearbeiten, neue Inhalte hinzufügen oder einfach neu erstellen [Probleme](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).</span><span class="sxs-lookup"><span data-stu-id="5364c-115">You can edit the existing content, add new content, or simply create new [issues](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).</span></span> <span data-ttu-id="5364c-116">Wir werden sehen Sie sich Ihre Vorschläge und wird arbeiten zusammen, um sie in der Dokumentation zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="5364c-116">We’ll take a look at your suggestions and will work together to incorporate them into the docs.</span></span>

<span data-ttu-id="5364c-117">Um Inhalt zu bearbeiten, klicken Sie auf Bearbeiten, für den Artikel, dem Sie ändern möchten:</span><span class="sxs-lookup"><span data-stu-id="5364c-117">To edit content, just click edit on the article you want to make changes to:</span></span>

![GIF-Datei zum Bearbeiten von docs](windows-iotcore/media/edit-doc.gif)


<span data-ttu-id="5364c-119">Sie können auch Klonen oder laden das Repository, um Änderungen vorzunehmen:</span><span class="sxs-lookup"><span data-stu-id="5364c-119">You can also clone or download the repo to make changes:</span></span>

![GIF zum Klonen oder Herunterladen-Repository](windows-iotcore/media/download-repo.gif)

<span data-ttu-id="5364c-121">Sie müssen auch einen Bearbeiter oder Prüfungen auf genehmigt werden Pull Requests hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="5364c-121">You will also need to add a reviewer or reviews to your pull requests to get them approved:</span></span>

![Ihr Pull Request Reviewer hinzugefügt](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a><span data-ttu-id="5364c-123">Konventionen</span><span class="sxs-lookup"><span data-stu-id="5364c-123">Conventions</span></span>
  - <span data-ttu-id="5364c-124">Beim Hinzufügen einer Seite müssen Sie einen Eintrag hinzufügen, damit es in [toc.md](windows-iotcore/TOC.md) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5364c-124">When adding a page, you must add an entry for it in [toc.md](windows-iotcore/TOC.md) for it to appear.</span></span>
  - <span data-ttu-id="5364c-125">Ein Ordner kann weitere Ordner enthalten oder `readme.md`s</span><span class="sxs-lookup"><span data-stu-id="5364c-125">A folder can contain more folders or `readme.md`s</span></span>
  - <span data-ttu-id="5364c-126">Ordner/Verzeichnisnamen werden durch Bindestriche getrennt (z. B. `f12-tools`) und Kleinbuchstaben.</span><span class="sxs-lookup"><span data-stu-id="5364c-126">Folder/directory names are dash-separated (e.g., `f12-tools`) and lowercase.</span></span> <span data-ttu-id="5364c-127">Sie werden auf der docs.microsoft.com-Website-URLs verwendet.</span><span class="sxs-lookup"><span data-stu-id="5364c-127">They are used in URLs on the docs.microsoft.com site.</span></span> <span data-ttu-id="5364c-128">Verwenden Sie keine Unterstriche oder PascalCase/CamelCase.</span><span class="sxs-lookup"><span data-stu-id="5364c-128">Don't use underscores or PascalCase/camelCase.</span></span>


## <a name="other-text-elements"></a><span data-ttu-id="5364c-129">Andere Textelemente</span><span class="sxs-lookup"><span data-stu-id="5364c-129">Other text elements</span></span>

<span data-ttu-id="5364c-130">Diese anderen Textelemente haben Stile zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="5364c-130">These other text elements have styling available:</span></span>

* <span data-ttu-id="5364c-131">Unsortierte Listen</span><span class="sxs-lookup"><span data-stu-id="5364c-131">Unordered lists</span></span>
* <span data-ttu-id="5364c-132">Haben Sie die normale Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="5364c-132">Have regular bullets</span></span>
   * <span data-ttu-id="5364c-133">Sie können auch Aufzählungszeichen schachteln.</span><span class="sxs-lookup"><span data-stu-id="5364c-133">You can also nest bullets</span></span>
   * <span data-ttu-id="5364c-134">Listen mit Aufzählungszeichen sollte mehr als ein Eintrag vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5364c-134">Bullets lists should have more than one entry.</span></span>
* <span data-ttu-id="5364c-135">Ziemlich standard</span><span class="sxs-lookup"><span data-stu-id="5364c-135">Pretty standard</span></span>

1. <span data-ttu-id="5364c-136">Sortierte Listen</span><span class="sxs-lookup"><span data-stu-id="5364c-136">Ordered lists</span></span>
2. <span data-ttu-id="5364c-137">Reguläre alten westliche Nummerierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="5364c-137">Use regular ol' western-style numbering.</span></span>
3. <span data-ttu-id="5364c-138">Sollte verwendet werden, nur, wenn Sie eine Liste wirklich Reihenfolge enthält.</span><span class="sxs-lookup"><span data-stu-id="5364c-138">Should be used only when a list truly has order.</span></span>

_________________________

<span data-ttu-id="5364c-139">Horizontale Linien sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5364c-139">Horizontal rules are available.</span></span> <span data-ttu-id="5364c-140">Es wird empfohlen, mit ihnen nur selten übersichtlicher gestalten möchten.</span><span class="sxs-lookup"><span data-stu-id="5364c-140">We suggest using them sparingly to reduce clutter.</span></span>
<span data-ttu-id="5364c-141">Kombinieren Sie horizontale Linien mit Überschriften-Tags nicht; Einige verwendet bereits Linienarten für visuelle Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="5364c-141">Do not combine horizontal rules with heading tags; some already used line styles for visual hierarchy.</span></span>
<span data-ttu-id="5364c-142">Darüber hinaus Anmerkungen zu dieser Version (siehe unten) in der Mitte nummerierte Listen nicht kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="5364c-142">Also, do not combine notes (see below) in the middle of numbered lists.</span></span> <span data-ttu-id="5364c-143">Dies verwirrt, mit der Nummerierung Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="5364c-143">This messes with the numbering order.</span></span>

## <a name="displaying-code"></a><span data-ttu-id="5364c-144">Anzeigen von code</span><span class="sxs-lookup"><span data-stu-id="5364c-144">Displaying code</span></span>

<span data-ttu-id="5364c-145">Sie können die Inline `code` Markdown-Syntax (mit dem Graviszeichen).</span><span class="sxs-lookup"><span data-stu-id="5364c-145">You can use inline `code` Markdown syntax (with the backticks).</span></span>

<span data-ttu-id="5364c-146">Sie können Codeblöcke anzeigen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5364c-146">Or you can display blocks of code like so:</span></span>

```css
body {
    background: #fff;
}
```

## <a name="tables"></a><span data-ttu-id="5364c-147">Tabellen</span><span class="sxs-lookup"><span data-stu-id="5364c-147">Tables</span></span>

| <span data-ttu-id="5364c-148">Sie können</span><span class="sxs-lookup"><span data-stu-id="5364c-148">You can</span></span>     | <span data-ttu-id="5364c-149">Verwenden von Headern</span><span class="sxs-lookup"><span data-stu-id="5364c-149">use headers</span></span> | <span data-ttu-id="5364c-150">für Tabellen</span><span class="sxs-lookup"><span data-stu-id="5364c-150">on tables</span></span>    |
|-------------|-------------|-------------:|
| <span data-ttu-id="5364c-151">Linksbündig</span><span class="sxs-lookup"><span data-stu-id="5364c-151">Left-aligned</span></span>| <span data-ttu-id="5364c-152">Es sei denn, ein #</span><span class="sxs-lookup"><span data-stu-id="5364c-152">Unless a #</span></span>  | <span data-ttu-id="5364c-153">456</span><span class="sxs-lookup"><span data-stu-id="5364c-153">456</span></span>          |
| <span data-ttu-id="5364c-154">Textwert</span><span class="sxs-lookup"><span data-stu-id="5364c-154">Text value</span></span>  | <span data-ttu-id="5364c-155">Weitere text</span><span class="sxs-lookup"><span data-stu-id="5364c-155">More text</span></span>   | <span data-ttu-id="5364c-156">$0.00</span><span class="sxs-lookup"><span data-stu-id="5364c-156">$0.00</span></span>        |

## <a name="notes"></a><span data-ttu-id="5364c-157">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5364c-157">Notes</span></span>

<span data-ttu-id="5364c-158">Verwenden Sie die Anmerkungen zu dieser Version nur selten.</span><span class="sxs-lookup"><span data-stu-id="5364c-158">Use notes sparingly.</span></span> <span data-ttu-id="5364c-159">Sie sind die Blöcke, die entworfen, um "nicht-Fehleranzahl-It" Informationen hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="5364c-159">They are blocks designed to highlight "don't-miss-it" information.</span></span>

<span data-ttu-id="5364c-160">Es gibt vier verschiedene Versionen von Notizen, die derzeit im Stil:</span><span class="sxs-lookup"><span data-stu-id="5364c-160">We have four different versions of notes currently styled:</span></span>
- <span data-ttu-id="5364c-161">HINWEIS</span><span class="sxs-lookup"><span data-stu-id="5364c-161">NOTE</span></span>
- <span data-ttu-id="5364c-162">WARNUNG</span><span class="sxs-lookup"><span data-stu-id="5364c-162">WARNING</span></span>
- <span data-ttu-id="5364c-163">TIPP</span><span class="sxs-lookup"><span data-stu-id="5364c-163">TIP</span></span>
- <span data-ttu-id="5364c-164">WICHTIG</span><span class="sxs-lookup"><span data-stu-id="5364c-164">IMPORTANT</span></span>


<span data-ttu-id="5364c-165">Verwenden Sie mehrzeilige Blockquote Anmerkungen zu dieser eine > vor jeder Zeile der Notizen wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="5364c-165">For multi-line blockquote notes, use a > in front of each line of the notes as seen in the example below.</span></span>

## <a name="images"></a><span data-ttu-id="5364c-166">Abbilder</span><span class="sxs-lookup"><span data-stu-id="5364c-166">Images</span></span>

<span data-ttu-id="5364c-167">Bilder gespeichert werden sollen, einem `media` Ordner und mit einem relativen Pfad verwiesen wird:</span><span class="sxs-lookup"><span data-stu-id="5364c-167">Images should be stored in a `media` folder and referenced with a relative path:</span></span>

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a><span data-ttu-id="5364c-168">Verhaltenskodex</span><span class="sxs-lookup"><span data-stu-id="5364c-168">Code of Conduct</span></span>
<span data-ttu-id="5364c-169">Dieses Projekt folgt dem [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="5364c-169">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="5364c-170">Weitere Informationen finden Sie unter den [Code von durchführen – häufig gestellte Fragen](https://opensource.microsoft.com/codeofconduct/faq/) oder wenden Sie sich an [ opencode@microsoft.com ](mailto:opencode@microsoft.com) weitere Fragen und Kommentare.</span><span class="sxs-lookup"><span data-stu-id="5364c-170">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>
