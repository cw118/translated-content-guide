# Guide to localization particularities: mdn/translated-content

A guide/checklist for myself (and any interested [mdn/translated-content](https://github.com/mdn/translated-content) reviewers and contributors) for localization differences in MDN Web Docs' translated content. **Primarily created based on/for the [l10n-fr (French) locale](https://github.com/mdn/translated-content/tree/main/files/fr).**

When it comes to differences in content between the English page and its translated counterparts, **always** consider the **English version** to be "correct"/up-to-date. As such, when updating a localized page *("update vs. en-US")*, you should **refer to the English counterpart and its corresponding file on GitHub** to ensure the translated version matches en-US (page slugs and file paths are the same except for the locale abbreviation, e.g. **`files/en-us/learn/forms/`** in `mdn/content` has a French counterpart **`files/fr/learn/forms/`** in `mdn/translated-content`).

***Note**: Guidelines may be slightly different for each locale. If reviewers suggest, request or push changes, it's a good idea to keep those in mind for future contributions to avoid repeating the same mistakes :)*

## Table of contents

- [Links: Good places to start](#links-good-places-to-start)
- [Types of contributions](#types-of-contributions)
- [Similarities: en-US and locales](#similarities-en-us-and-locales)
  - [Style and formatting](#style-and-formatting)
  - [Front matter and macros](#front-matter-and-macros)
- [Key localization differences](#key-localization-differences)
  - [Cards](#cards)
  - [Images](#images)
  - [Links](#links)
    - [Relative links](#relative-links)
    - [External links](#external-links)
  - [Using macros](#using-macros)
    - [Vocabulary macros](#vocabulary-macros)
    - [Live and interactive code samples](#live-and-interactive-code-samples)
    - [The EmbedLiveSample macro](#the-embedlivesample-macro)
- [HTML-Markdown conversion](#html-markdown-conversion)
  - [The conversion process](#the-conversion-process)
  - [Conversion preparation: what to look out for in HTML](#conversion-preparation-what-to-look-out-for-in-html)
  - [Common conversion-provoked Markdown errors](#common-conversion-provoked-markdown-errors)

---

## Links: Good places to start

Links to important GitHub repos and shortcuts to key documents/webpages:

- GitHub repo containing all translated MDN content: [mdn/translated-content](https://github.com/mdn/translated-content)
  - README, Contributing to translated-content: [README.md in mdn/translated-content](https://github.com/mdn/translated-content/blob/main/README.md)
  - [translated-content issues](https://github.com/mdn/translated-content/issues)
- Localizing MDN (+ contact the locale teams): [Active locales](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Localize)
- GitHub repo containing the content behind MDN Web Docs (en-US original version): [mdn/content](https://github.com/mdn/content)
- The content repo README, which has information on fundamental concepts, PR etiquette and common actions: [README.md in mdn/content](https://github.com/mdn/content/blob/main/README.md)
- MDN's how-to guides: [Contributing to MDN, how-tos](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Howto)
- Guidelines for MDN's locales: [General guidelines for MDN translated content](https://github.com/mdn/translated-content/tree/main/docs)
- MDN's style guides: [Code example guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines)
- What's Deployed for translated-content (see if your merged PR has been deployed to the site): [translated-content — What's Deployed](https://whatsdeployed.io/s/16d/mdn/translated-content)

---
---

## Types of contributions

Maintaining translated versions of MDN Web Docs can be quite difficult — the English docs are almost constantly changing and evolving, which can make it difficult to keep the translated versions up-to-date. Here are some types of contributions to consider if you're not sure where to start or what to do:

- Typo and formatting fixes
- Fixing links (dead, unneeded external, https, etc.)
- Fixing issues with images (not displaying, wrong source, etc.)
- Fixing issues with macros *(more detail on this in [Using macros](#using-macros))*
  - Fixing issues with live code examples
- Translating sections mistakenly left in English (fixing/correcting missed translations)
- Updating/synchronizing translated docs with the en-US versions
- General "clean-up" *(typically includes most/all of the above)*
- Fixing actionable issues through pull requests
- Creating issues to notify teams and contributors of problems found on translated pages ***(please be as clear and as detailed as possible in your issue titles and descriptions)***
- Translating a document from English into another language ***(refer to the list of [active locales](https://github.com/mdn/translated-content#locales))***

---
---

## Similarities: en-US and locales

Here is a quick list of what's kept the same or what's similar between `content` and `translated-content`, including small additions for files in the latter repo.

---

### Style and formatting

- **Newline at end of file:** at the end of every file in MDN Web Docs, whether it's en-US or any locale, should have a newline. This is considered an **MDN standard** (please also read the note directly below).
  - **Note: it's important to realize that when viewing a file on the regular GitHub UI (without expressly clicking to edit the file), this final newline is *not* shown. This often occurs even when viewing files in a commit or PR, so it's quite likely that a newline was left at the end as "required", but that it's simply not displayed/visible.**
- **Code styles and conventions:** MDN has outlined [code example guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines), which **we abide by both in mdn/content and mdn/translated-content**! For instance, when including code examples in JavaScript, all statements must end with semicolons (`;`), and single quotes (`'`) must be used. *See below for some quick links — you can refer to these for MDN Web Docs' code style standards and explanations of certain stylistic choices.*
  - [General code guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines)
  - [HTML guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines/HTML)
  - [CSS guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines/CSS)
  - [JavaScript guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines/JavaScript)
  - [Shell prompt guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines/Shell)
- **Formatting and layout:** the translated docs should, in general, be formatted and laid out in the same way as the en-US versions — however, if you find mistakes (e.g. incorrect Markdown syntax), please correct them in the translated file(s), and feel free to submit a PR at the mdn/content repo to fix those errors at the source as well!

#### Unicode characters

Code editors like VS Code have implemented features to highlight characters that are "often confused with another" and/or "invisible" (in VS Code, this is done with a yellow rectangle surrounding a character) — you can hover over each highlighted character to see its unicode hex and a potential replacement. The [Gremlins tracker for Visual Studio Code] extension ([find/install it here](https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins)) is an excellent to search for these characters as well — see after the table below for images of the VS Code and Gremlins tracker features in action. Here are some examples of "gremlins":

> **Note:** These "invisible" chars, or "gremlins", aren't detected or highlighted on the GitHub UI, so you'll have to check for some by reviewing locally. Don't worry too much about gremlins, though it won't hurt to nitpick a little with typography.

| Character name | Unicode hex | Can potentially be replaced by... |
| -------------- | ------- | --------------------- |
| Non-breaking space | `U+00a0` | Regular space — if you see any that are "randomly placed" in a file, feel free to replace them as they're probably not meant to be there. (**Note:** Non-breaking spaces are [sometimes intentional](#key-localization-differences)) |
| EN dash (slightly longer than a dash, meant for use with number ranges, e.g. "2–3") | `U+2013` | Regular dash (e.g. "2-3") |
| Typographer's apostrophe/quotation marks (also called "smart apostrophe"/"smart quotes"): ‘’ and “” | `U+2018`, `U+2019`, `U+201c`, `U+201d` | Regular apostrophes/quotation marks ('' and "") |
| Chinese punctuation (，, ；, （ and ）, etc.) | `U+ff0c`, `U+ff1b`, `U+ff08` and `U+ff09`... | None — these are intentional, but are identified as gremlins because their spacing is different from common keyboard layouts (QWERTY, AZERTY, etc.). |
| Various cyrillic letters (с, а, е, б, о, р, г, etc.) | `U+0441`, `U+0430`, `U+0435`, `U+0431`, `U+043e`, `U+0440`, `U+0433`... | None — these are intentional (while they closely resemble Latin characters like English letters, cyrillic characters are not the same and are used in other languages such as Russian) |

<details>
<summary>VS Code's character highlighting feature in a `translated-content` Russian file:</summary>

![VS Code gremlin highlighting cyrillic letters](assets/unicode-highlight/ru-gremlin-highlighting.png)
</details>

<details>
<summary>Gremlins highlighted by the <a href="https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins">Gremlins tracker extension</a>):</summary>

![Gremlins tracker extension highlighting gremlin punctuation](assets/unicode-highlight/gremlins-tracker.png)
</details>

---

### Front matter and macros

Note that in HTML files (those not yet converted to Markdown, or those in the Tools folder, for which there was a consensus to leave in HTML), macros are typically wrapped in `<div>` or `<p>` tags.

- **title:** the `title:` declaration is always at the very top of each file in both en-US and localized versions. Page titles can and should be translated *(with the exception of official coding terms and syntax such as HTML elements/tags, CSS properties, JavaScript functions and objects, etc.)*.
- **slug:** also found at the top of every file, the slug essentially specifies part of a page's link. **Note that slugs are *not* to be translated!**
- **Formal definition:** the `{{CSSinfo}}` macro *(also seen as `{{cssinfo}}`, though case doesn't necessarily matter)* is used universally; however, the placement of the `Formal definition` section/block tends to vary with each locale. Usually, it's recommended to place the `Formal definition` directly above the `Formal syntax` (see below) like the en-US pages, but not all locales follow this structure — refer to other pages in the locale to which you're contributing to see where to place this, or politely ask the reviewing team.
  - CSS formal definitions can be found for all locales (including en-US) at the [l10n folder of the mdn/data repo](https://github.com/mdn/data/tree/main/l10n). If you see that a formal definition hasn't been translated to your locale language, the `css.json` file in that folder is where you can add translated strings for missing translations.
- **Formal syntax:** the various syntax macros, such as `{{csssyntax}}`, are used universally; however, the placement of the `Formal syntax` section/block tends to vary with each locale. It's generally recommended to place `Formal syntax` below `Formal definition`, but some locales don't follow this structure — refer to other pages in the locale to which you're contributing to see where to place this, or politely ask the reviewing team.
  - Formal syntax and other data for CSS can be found in [this folder of the mdn/data repo](https://github.com/mdn/data/tree/main/css)
  - Inheritance data for APIs can be found in the [api folder at mdn/data](https://github.com/mdn/data/tree/main/api)
- **Specifications:** translated pages use the same `{{Specifications}}` macro as the en-US pages. For the few that are still formatted as specs tables, those in `translated-content` are/should be translated from en-US counterparts.
- **Compatibility tables:** translated pages use the same compatibility tables (or macro, depending on the page) as their en-US counterparts, though the content of these tables are translated to the corresponding language. For HTML files, compatibility table macros are typically wrapped in `<div>` (sometimes `<p>`) tags.
  - **browser-compat:** only necessary for pages with compatibility tables where the `{{Compat}}` macro takes no arguments — the same `browser-compat` value is used in en-US and localized versions. This declaration is usually placed below (sometimes above) `translation_of` in `translated-content` files.
- **Sidebars:** translated pages use the same sidebar macros as their en-US counterparts.
- **Menus/navigation:** menu macros such as `{{NextMenu}}` and `{{PreviousMenuNext}}` should take the same arguments as their en-US counterparts.
- **Various compatibility and deprecation warnings:** macros like `{{SeeCompatTable}}` (notifies users that a technology is experimental), `{{optional_inline}}` (inline symbol that lets users know that something, often a function argument or CSS rule parameter, is optional), and `{{Deprecated_Inline}}` (inline icon that lets user know something has been deprecated), etc. should match their usage in en-US files. In other words, there shouldn't be a `{{SeeCompatTable}}` warning in a Chinese file if it's not in its English counterpart, and if the English version has a `{{Deprecated_Header}}` (similar to its inline version, but it's displayed as a card-style warning), the Chinese (or any locale/translated) counterpart should have it as well.

---
---

## Key localization differences

Below is a non-extensive list of important differences between `translated-content` and `content` document structures, based on tips from review teams and my observations. Certain "concepts", such as macros, require more in-depth explanations and are given a subsection to address their particularities.

- **Tags:** the translated docs do **not** use tags (teams and contributors are still in the process of removing them) — found at the top of en-US files and possibly translated files where they haven't yet been deleted.
  - Removing tags doesn't seem to be a priority, so no need to make a PR removing tags from all files — if you're editing a page in the translated-content repo that happens to have tags, please do remove them.
- **translation_of:** provide the slug of the en-US counterpart here. Unique to the `translated-content` repo, though `translation_of` should usually be the same as `slug` *(see [Similarities — Front matter and macros](#front-matter-and-macros))*.
- **original_slug:** the original slug, with English words translated to the locale language (e.g. the `original_slug` for `Learn/Server-side/Django/Generic_views` in French is `Learn/Server-side/Django/Vues_generiques`). Unique to the`translated-content` repo. *Note that this declaration is not required if it (the "original `slug`") is identical to the actual slug. Often not included/needed.*
- **No-breaking spaces (mostly French-specific):** when using punctuation that requires spaces before and/or after alphabetic characters like guillemets (`«»`), colons (`:`), semi-colons (`;`), question and exclamation marks (`?` and `!`), use no-breaking spaces (HTML entity `&nbsp;`).
  - ***Important:*** do **not** use no-breaking spaces in cards, otherwise they won't be rendered correctly! *(For example, write `**Attention :**` and **not** `**Attention&nbsp;:**`!)*
  - A seemingly good rule of thumb for this is that when you're in doubt of whether a non-breaking space is "required", use one.
  - For example, note the presence of a non-breaking space in the following sentence: `Travailler avec des formulaires peut s'avérer compliqué&nbsp;!` (*renders as:* Travailler avec des formulaires peut s'avérer compliqué&nbsp;!).
  - An example with guillemets: `des «&nbsp;gouttières&nbsp;»` (*renders as:* des «&nbsp;gouttières&nbsp;»).
- **Code blocks:** for the most part, code such as class/ID names and the inner HTML of tags can be translated. Comments can be translated as well; however, declarations of variables and functions are usually kept in English.
- **Translation differences:** keep in mind that it's often not possible to find direct translations — in those cases, translate in a way that "makes sense" in the language concerned, while preserving the key meaning/conveying the main message.
- **Cards in l10n:** see the [Cards](#cards) section for details on using cards (in English, these are `Note:`, `Callout:` and `Warning:`).
- **Images:** see the [Images](#images) section.
- **Links:** see the [Links](#links) section.
- **Macros:** see the [Using macros](#using-macros) section for details on vocabulary/xref macros (`htmlelement`, `cssxref`, etc.) and embed macros (`EmbedLiveSample`, `EmbedInteractiveSample`, etc.).

---
---

### Cards

In English, the three main types of cards can be added using the bolded keywords **Note:**, **Callout:**, and **Warning:**. The translated content also uses these cards *(they should be placed in the same file/page locations with the matching card style)*, but with translated keywords — to see the card keywords used by each locale, see their corresponding localization JSON file at [mdn/yari/markdown/localizations](https://github.com/mdn/yari/tree/main/markdown/localizations) (or add keywords for your locale to that folder if they don't exist). ***All contents of such cards can and should be translated!***

For example, a **Note:** card is styled as follows, by writing the keyword and a colon `:` in bold:

![MDN blue note card](assets/cards/note.png)

Depending on whether the file you're working on has an `.html` or `.md` extension, you'd type:

- `.html` (the file is still in **HTML**): Create a `<div>` and apply the `note` class to it, then wrap `<strong>` tags around the keyword. The colon after the keyword tends to be placed outside of the `<strong>` tags. See below for an example.

```html
<div class="note">
  <p><strong>Примечание</strong>: Here's a note card in HTML.</p>
  <p>
    <pre class="brush: html">&lt;p&gt;You can also add blocks of code in these cards!&lt;/p&gt;</pre>
  </p>
</div>
```

- `.md` (the file has been converted to **Markdown**): Type `> **Note :**` to use the card *(notice the Markdown bold and blockquote formatting, as well as the space preceding the colon as per French grammar rules — do **not** use a non-breaking space `&nbsp;` in card keywords!)*. The "syntax" for a French note card would essentially match that of a blockquote in Markdown:

> **Note :** Paragraphe de référence (placeholder text), paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence.
>
> ```html
> <p>You can also add blocks of code in these cards!</p>
> ```

Similarly, a callout card (**Callout:**) looks like the following:

![MDN blue callout card](assets/cards/callout.png)

Aside from the change in keyword *(Note > Callout)*, the "syntax" for this type of card is the same as a that of a **Note:**. Directly below is an example for a Markdown file in the French locale *(Note > Remarque)*:

> **Remarque :** Paragraphe de référence (placeholder text), paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence, paragraphe de référence.
>
> ```html
> <p>You can also add blocks of code in these cards!</p>
> ```

The warning card (**Warning:**) follows the same rules as **Note:** and **Callout:**. *Also see [MDN's guidelines and writing style guide](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Writing_style_guide#text_formatting_and_styles) for more on styles and formatting.*

---
---

### Images

Like in the `content` repo, avoid using external links for images: instead, use relative sources by providing the file name of the image to be displayed. Ensure that the source you provide matches that of the image file in the en-US repo. **The `alt` attribute can and should be translated to the locale language.**

If you're using the **same image as the en-US counterpart** of a page, using the same relative source for the image (which is really just the image's file name) will suffice. ***Please also note the exception specified below.***

- For example, to link to the "flexbox-example1.png" image, you can simply write `![alt text here](flexbox-example1.png)` for Markdown, or for HTML, give the `<img>` tag a `src` attribute of "flexbox-example1.png" (and ideally, an `alt` attribute as well) like this: `<img src="flexbox-example1.png" alt="alt text here">`.
  - If you see external links/sources such as `https://mdn.mozillademos.org/files/13406/flexbox-example1.png`, or even relative file paths like `/files/3739/flex_terms.png`, be sure to test out the relative source on your local copy to ensure you've found the correct image source! Often, the simplest way to do so is to use the same image source as the en-US file. *See [PR #3331](https://github.com/mdn/translated-content/pull/3331) for an example of fixing image sources.*
- ***Exception:*** for embed macros like `{{EmbedLiveSample}}` to function properly, a copy of all images used in those live samples must be present in the same folder as the translated repo's `index.html` or `index.md` file. ***(Note: [a PR waiting on triage and merging at mdn/yari](https://github.com/mdn/yari/pull/5215) could remove this exception, but at the moment, no "solution" for this has been implemented.)***
  - *For example, the [French page on CSS `<blend-mode>`](https://developer.mozilla.org/fr/docs/Web/CSS/blend-mode) has multiple `{{EmbedLiveSample}}`s that rely on two image files, `br.png` and `tr.png`. Without these two image files in the `blend-mode` folder, the samples won't display properly — this was fixed in [PR #3383](https://github.com/mdn/translated-content/pull/3383).*

However, note that **if a locale is using an image that's different from the one included in en-US files, the image file will need to be uploaded to the same folder as the `index.md` or `index.html` file**.

---
---

### Links

The guidelines for relative and external links are very similar — concerns surrounding links in MDN's translated documentation primarily stem from the quality or existence of a page/resource in a certain language.

---

#### Relative links

For links within MDN Web Docs itself, simply provide the **slug in English** with `/<your-locale>/docs/` as a "prefix" *(if the full HTTP header is provided for a relative link, or if a non-canonical/non-English slug is used, Yari's flaw checker will detect this)*. If the linked page has been translated for your locale, link to the corresponding translated version. If not, you can link to the en-US page or do the same as before — in the latter case, Yari will detect a "broken link" and have it fallback on the en-US version, adding a "(en-US)" note after the link. For example:

- To link to the French *"Démarrer avec CSS"* page *("Getting started with CSS" in en-US)*, the following slug should be provided as the link source: `/fr/docs/Learn/CSS/First_steps/Getting_started`

If you're linking to a section header, chances are you won't be able to keep the English header ID/name — simply provide the ID or name that matches whichever section you're linking to. *This may vary with certain locales, particularly with zh-TW, which keeps their header IDs in English.*

- For example, to link to the *"Ajouter une classe" ("Adding a class" in en-US)* section/header of the French *"Démarrer avec CSS"* page, one would use the following slug: `/fr/docs/Learn/CSS/First_steps/Getting_started#ajouter_une_classe`
  - **Note:** to link to a section/header on the same page, just use the section ID. To be more precise — using the same example as above, if you're editing the *"Démarrer avec CSS"* page and want to link to the *"Ajouter une classe"* section at some point, just use this as the link source: `#ajouter_une_classe`.

---

#### External links

Links should match those in the en-US counterpart, even if it leads to a page that is only available in English. Ensure that `https:` is used in external links *(the flaw-checker will warn of `http:` usage otherwise)*.

On a similar note, if the linked resource has a translation available for the language of your locale, you may include a link to the resource in that language provided that:

- It is of good quality, and its content matches/is up-to-date with the original (usually English) version;
- It is "well-maintained" and often updated (if applicable).

---
---

### Using macros

Macros were "migrated" to Yari from MDN's previous Kuma system, and some have been or are on track to being deprecated (deleted). Certain macros are here to stay, namely `{{EmbedLiveSample}}` and other various live sample macros, but vocabulary macros are possibly expected to be removed in the future. One macro that is in the process of being "purged" from translated-content pages, since it was deleted, is the `{{page}}` transclusion macro (see [mdn/translated-content issues](https://github.com/mdn/translated-content/issues)).

Also note that it's best to avoid adding spaces between the double curly braces (`{{` and `}}`), parentheses (`(` and `)`), and the actual macro with its arguments (e.g. `{{Glossary( "Truthy")}}`, `{{ EmbedLiveSample("", '100%') }}`, etc.). Some older files may have macros "formatted" this way — this is something that can and should be corrected on the translated-content side (continuing with the previous examples, they should become `{{Glossary("Truthy")}}` and `{{EmbedLiveSample("", '100%')}}`).

See the [macros folder at mdn/yari](https://github.com/mdn/yari/tree/main/kumascript/macros) for a full list of macros used in MDN Web Docs.

---

#### Vocabulary macros

Depending on the locale, the reviewing team may continue using macros as the en-US files do, or they may prefer to replace these macros with their corresponding links. For instance, the French (fr) locale replaces all vocabulary macros and some others with links — this is because it's said that many Kumascript macros will be deleted in the future, with the exception of some such as `{{EmbedLiveSample}}` as explained above; thus, beginning to remove macros that will likely/potentially be deleted is done in preparation for their eventual deletion.

Some examples of these, as in vocabulary and wiki macros, are *(to ensure you replace macros with the correct links, you can also preview pages locally, click on the links resulting from macros, and copy the URL)*:

| Macro | Corresponding link | Example (in the *`fr`* locale) |
| ----- | ------------------ | ------- |
| `{{HTMLElement}}` | `/<locale>/docs/Web/HTML/Element/<element-name>` | `{{HTMLElement("select")}}` -> `/fr/docs/Web/HTML/Element/select` |
| `{{CSSxRef}}` | `/<locale>/docs/Web/CSS/<css-rule-property-etc>` | `{{cssxref("@keyframes")}}` -> `/fr/docs/Web/CSS/@keyframes` |
| `{{JSxRef}}` | `/<locale>/docs/Web/JavaScript/Reference/Global_Objects/<js-term>` | `{{jsxref("Promise")}}` -> `/fr/docs/Web/JavaScript/Reference/Global_Objects/Promise` |
| `{{bug}}` | `https://bugzilla.mozilla.org/show_bug.cgi?id=<bug-id>` | `{{bug("11011"}}` -> `https://bugzilla.mozilla.org/show_bug.cgi?id=11011`|
| `{{Interwiki("wikipedia", ...)}}` | `https://<wikipedia-locale-abbr>.wikipedia.org/wiki/<term-expression-etc>` | `{{interwiki("wikipedia", "Raccourci_clavier")}}` -> `https://fr.wikipedia.org/wiki/Raccourci_clavier` |
| `{{Glossary}}` | `/<locale>/docs/Glossary/<term>` | `{{Glossary("IPv4")}}` -> `/fr/docs/Glossary/IPv4` |
| `{{HTTPStatus}}` | `/<locale>/docs/Web/HTTP/Status/<http-status-code>` | `{{HTTPStatus("404")}}` -> `/fr/docs/Web/HTTP/Status/404` |
| `{{DOMxRef}}` | `/<locale>/docs/Web/API/<DOM-term>` | `{{domxref("DOMString")}}` -> `/fr/docs/Web/API/DOMString` |

---

#### Live and interactive code samples

The most commonly used live sample macro is `{{EmbedLiveSample}}` *(also see this macro's own [subsection below](#the-embedlivesample-macro))*, though there are also some others such as `{{EmbedGHLiveSample}}` and `{{EmbedInteractiveExample}}`.

The `{{EmbedLiveSample}}` macro has lots of particularities (peculiarities) pertaining to it, which is why it has [its own subsection](#the-embedlivesample-macro). The `GHLiveSample` and `InteractiveExample` macros should be exact "copies" of what's written/used in the en-US counterparts.

*This section covers best practices for including these embed macros, and not how they work. If you'd like more details on the latter, see [Live samples — The MDN project](https://developer.mozilla.org/en-US/docs/MDN/Structures/Live_samples).*

---
---

#### The EmbedLiveSample macro

`{{EmbedLiveSample}}` must always take at least one argument — the first or only argument in the English files is the section anchor/heading, but **this sometimes causes rendering errors for translated-content, so on the translated-content side, we tend to leave an empty string as the argument instead** (e.g. `{{EmbedLiveSample("")}}` or `{{EmbedLiveSample('')}}`). The remaining arguments, typically width and height, should be kept the same as en-US.

Something to keep in mind is that Yari's flaw checker may complain about "translation differences in important macros" due to different first arguments for `{{EmbedLiveSample}}`s — know that **these can be safely/fully ignored**!

However, there are some exceptions/special cases to watch out for when using this macro. The "empty string first argument" strategy only works if the `{{EmbedLiveSample}}` macro is placed under its own heading (usually a "Result" heading), or if all code blocks are placed under a single heading (usually "Example" or a subheading better describing the example) with the macro right under them. See the demonstrations below:

---

**Example/case 1:** *One (type of) code block under one heading*

With only one code block (meaning code in only one language), the EmbedLiveSample macro will work perfectly with an empty string as the first argument (otherwise it can be problematic when rendering). Taking the Spanish locale as an example, both of the code snippets below have only one HTML code block — one with a large heading (`h2`), and the second with both a heading and subheading (`h2` followed by an `h3`) — will output the same live sample result.

<details>
<summary>Collapse/show the case 1 example:</summary>

<img width="500" alt="An h2 heading with an HTML code block and EmbedLiveSample" src="assets/embedlivesample/onecodeblock/onecb-sample.png">

<img width="500" alt="An h2 heading, followed by an h3 heading and an HTML code block, then the EmbedLiveSample" src="assets/embedlivesample/onecodeblock/onecb-subheading.png">

Both will produce this (which is correct/what's expected):

<img width="650" alt="One code block EmbedLiveSample example result" src="assets/embedlivesample/onecodeblock/onecb-live.png">
</details>

---

**Example/case 2:** *Multiple (types of) code blocks under one heading*

Sometimes, pages will have multiple code blocks, since a sample involves multiple programming or markup languages. The most common combinations involve HTML, CSS and JavaScript. However, one must note that these example code blocks can be organized in various ways — sometimes, they're each under their own subheading (see example 3), while they can **all be placed under one heading/subheading**. This example demonstrates the second of these cases, where the EmbedLiveSample macro will handle an empty string first argument well.

<details>
<summary>Here's a test of grouping several code blocks under one heading, with the <code>{{EmbedLiveSample}}</code> immediately following them, done in the `es` (Spanish) locale:</summary>

<img width="600" alt="Three code blocks grouped under one h2 heading" src="assets/embedlivesample/multiplecodeblocks/mcb-oneheading.png">

<img width="700" alt="Multiple code blocks under an h2 example result" src="assets/embedlivesample/multiplecodeblocks/mcb-oneheading-live.png">
</details>

---

**Example/case 3:** *Multiple (types of) code blocks under separate headings*

Similar to case 2, pages may have **multiple code blocks that are each under their own subheadings**. This tends to be more common in MDN Web Docs, especially in newer and (somewhat/recently) updated pages. In this case, more care needs to be taken, as the EmbedLiveSample macro **cannot** immediately come after the final code block as it did in example 2 — **instead, the `{{EmbedLiveSample}}` *must* be placed under its own (sub)heading!** The subheading often used when multiple code blocks are organized this way (as in they're each under their own heading/subheading) is "Result" *(also "Résultat" in French, "Resultado" in Spanish, "Резултат" in Russian and so on)*.

<details>
<summary>First off, here's is a <strong>bad</strong> example (do <strong>not</strong> try to include an <code>{{EmbedLiveSample}}</code> like this!):</summary>

<img width="600" alt="Bad usage of EmbedLiveSample, which isn't under its own heading, with multiple code blocks each under a separate heading" src="assets/embedlivesample/multiplecodeblocks/mcb-headings-bad.png">

The above code would result in a blank ("incorrect") live sample:

<img width="700" alt="Result of bad EmbedLiveSample usage with multiple headings" src="assets/embedlivesample/multiplecodeblocks/mcb-headings-bad-live.png">
</details>

<details>
<summary>Instead, do the following by <strong>placing the EmbedLiveSample macro under its own heading</strong>:</summary>

<img width="600" alt="Good usage of EmbedLiveSample, which is under its own Result heading, with multiple code blocks each under a separate heading" src="assets/embedlivesample/multiplecodeblocks/mcb-headings-good.png">

With the `{{EmbedLiveSample}}` under its own "Resultado" (Spanish for "Result") heading, the live sample will render properly/as expected:

<img width="700" alt="Result of good EmbedLiveSample usage with multiple headings" src="assets/embedlivesample/multiplecodeblocks/mcb-headings-good-live.png">
</details>

---
---

## HTML-Markdown conversion

On the en-US (mdn/content) side, all files have been converted to Markdown with the exception of the Tools section, as there was a consensus to keep the latter in HTML (that is, to **not** convert it). As for locales (mdn/translated-content), HTML to Markdown conversion (`h2m`) is either in-progress or completed (thus far, only the French locale has been fully converted to Markdown).

---

### The conversion process

Long-time contributor, reviewer, and French locale maintainer **SphinxKnight** has created an [extensive guide to converting translated-content to Markdown](https://github.com/mdn/translated-content/discussions/2474). Definitely give it a read, especially if you plan on converting entire sections at once.

There are two approaches for HTML-Markdown conversion. One is to convert entire sections at once; the other is to convert one/a few documents at a time while updating them vs. their en-US counterparts (this would fix outdated content and convert the file or files).

Here's an extremely basic and brief overview of the HTML to Markdown conversion process.

What you'll need (see the individual repos for setup instructions):

- A local copy/fork of the [mdn/yari repo](https://github.com/mdn/yari), where the `h2m` conversion tool can be found
- A local copy/fork of the [mdn/translated-content repo (and any prerequisites needed to work on it)](https://github.com/mdn/translated-content)

A **basic** overview of the conversion process (please see [the guide](https://github.com/mdn/translated-content/discussions/2474) for complete and detailed instructions):

- Prepare the HTML content for conversion: ensure it results in a "clean" build and a "clean" report from the conversion tool
- Review the preparation PRs (it's recommended to sample at least 10-20 files for especially large PRs, such as those modifying over 100 files) and merging, **provided all CI checks pass**
- Convert from HTML to Markdown in two commits (do **not** squash these commits!):
  - The first commit should rename the file(s) from `*.html` to `*.md` (change the file extension from HTML to Markdown)
  - The second commit should convert HTML code to Markdown
  - ***IMPORTANT: do NOT squash the renaming and conversion commits!***
  - **Watch out for conflicts with other commits/PRs/issues — these should be "frozen"** ([see SphinxKnight's guide for more information](https://github.com/mdn/translated-content/discussions/2474))

---

### Conversion preparation: what to look out for in HTML

A number of code style or formatting choices that display/render without a problem in HTML will become erroneous after conversion to Markdown. Many of these errors can be avoided by using a Markdown linter (I currently use the [`vscode-markdownlint` extension](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)).

Here are some things to look out for when modifying/reviewing HTML files *(the slashes `/` are just separators and delimiters, please ignore them)*. **Note that while some Markdown errors occasionally display properly, examples in the "To AVOID" column are *bad practices* and should *not* be used in order to prevent unexpected rendering/formatting:**

| Description | TODO (HTML) | Markdown equivalent | To AVOID (HTML) | Erroneous Markdown equivalent |
| ----------- | ----------- | ------------------- | --------------- | ----------------------------- |
| ***No*** whitespace between HTML emphasis tags and the text nested within them | / `<strong>Some text</strong>` / `<em>Some text</em>` / | / **Some text** / *Some text* / | / `<strong> Some text</strong>` / `<em>Some text </em>` / | / ** Some text** / *Some text * / |
| ***No*** whitespace between `<code>` tags and the text nested within them | `<code>HTTP 404</code> is` | `HTTP 404` is | `<code>HTTP 404 </code>is` | `HTTP 404 `is |
| ***No*** whitespace between `<a>` tags and the text nested within them *(this one is less problematic, but should still be avoided)* | `See <a href="#">here</a>` | See [here](#conversion-preparation-what-to-look-out-for-in-html) | `See<a href="#"> here</a>` | See[ here](#conversion-preparation-what-to-look-out-for-in-html) |

---

### Common conversion-provoked Markdown errors

The `h2m` conversion tool isn't perfect, so some HTML may be incorrectly converted, resulting in slightly strange-looking pages. For the most part, there's no shortcut to just "find all and replace all" — you'll have to check some manually to correct the formatting to what was intended, rather than just removing the problematic Markdown; also note that some perceived errors may have been intentional and should not be "accidentally" modified (e.g. sometimes characters are purposely escaped, and not the result of a mistaken conversion). Sometimes, errors are caused by missed typos in the HTML file — `h2m` conversion may not only carry over the typo, but also result in incorrect formatting due to missing whitespace and more.

Here are some common ones to look out/search for and correct *(slashes `/` are just delimiters)*:

| Description | Notes | Example(s) of erroneous Markdown | Incorrectly rendered Markdown | Regex/text search rule |
| ----------- | ----- | -------------------------------- | ----------------------------- | ---------------------- |
| Missing (white)space | This may occur with various [card keywords](#cards) and in different locales | `**Note :**Pour plus...` | **Note :**Pour plus... | `Note :\*\*[^ ]` |
| Single escaped asterisks | Watch out for **intentionally escaped asterisks** (e.g. 8 \* 8 for multiplication, \*see exception, etc.)! Often occurs due to nested emphasis tags. | / `**\*u**nordered **l**ist\*` / `**OK\***.\*` / | / **\*u**nordered **l**ist\* / **OK\***.\* / | `\*` |
| Double escaped asterisks | The intended formatting can be tricky to determine with these. Often occurs due to nested emphasis tags. | / `**\*Note**:\*` / `\*(Couleur)**\* **` / | / **\*Note**:\* / \*(Couleur)**\* ** / | `\*\*` |
| Missing `code` formatting | Typically occurs with HTML tags, which are simply escaped rather than formatted as `code` | `\<a>` | \<a> | `\\<(\S*?)[^>]*>` |
