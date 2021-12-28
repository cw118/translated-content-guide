# Guide to localization particularities: mdn/translated-content

A guide/checklist for myself (and any interested [mdn/translated-content](https://github.com/mdn/translated-content) contributors) for localization differences in MDN Web Docs' translated content. Primarily created based on/for the [l10n-fr (French) locale](https://github.com/mdn/translated-content/tree/main/files/fr).

When it comes to differences in content between the English page and its translated counterparts, **always** consider the **English version** to be "correct"/up-to-date.

*Note: This guide was **not** created by any member of MDN. It contains observations and tips gathered by myself from various PRs and read-throughs of mdn/translated-content's French documentation. If reviewers suggest, request or push changes, it's a good idea to keep those in mind for future contributions to avoid repeating the same mistakes.*

## Links: Good places to start

Links to important GitHub repos and shortcuts to key documents/webpages:

- GitHub repo containing all translated MDN content: [mdn/translated-content](https://github.com/mdn/translated-content)
  - README, Contributing to translated-content: [README.md in mdn/translated-content](https://github.com/mdn/translated-content/blob/main/README.md)
  - [translated-content issues](https://github.com/mdn/translated-content/issues)
- Localizing MDN: [Active locales](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Localize)
- GitHub repo containing the content behind MDN Web Docs (en-US original version): [mdn/content](https://github.com/mdn/content)
- The content repo README, which has information on fundamental concepts, PR etiquette and common actions: [README.md in mdn/content](https://github.com/mdn/content/blob/main/README.md)
- MDN's how-to guides: [Contributing to MDN, how-tos](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Howto)
- What's Deployed for translated-content (see if your merged PR has been deployed to the site): [translated-content — What's Deployed](https://whatsdeployed.io/s/16d/mdn/translated-content)

## Types of contributions

Maintaining translated versions of MDN Web Docs can be quite difficult. Here are some types of contributions to consider if you're not sure where to start or what to do:

- Typo and formatting fixes
- Fixing links (dead, unneeded external, https, etc.)
- Fixing issues with images (not displaying, wrong source, etc.)
- Fixing issues with macros *(more detail on this in [Using macros](#using_macros))*
  - Fixing issues with live code examples
- Updating/synchronizing translated docs with the en-US versions
- General "clean-up" *(typically includes most/all of the above)*
- Fixing actionable issues through pull requests
- Creating issues to notify teams and contributors of problems found on translated pages ***(please be as clear and as detailed as possible in your issue titles and descriptions)***
- Translating a document from English into another language ***(refer to the list of [active locales](https://github.com/mdn/translated-content#locales))***

## Similarities: en-US and translations

Here is a quick list of what's kept the same or what's similar between `content` and `translated-content`, including small additions for files in the latter repo:

- **title:** the `title:` declaration is always at the very top of each file in both en-US and localized versions. Page titles can and should be translated *(with the exception of official coding terms and syntax such as HTML elements/tags, CSS properties, JavaScript functions, etc.)*.
- **slug:** also found at the top of every file, the slug essentially specifies part of a page's link. **Note that slugs are *not* to be translated!**
- **translation_of:** provide the slug of the en-US counterpart here. Unique to the `translated-content` repo, though `translation_of` often has the same slug as `slug`.
- **Formal definition:** the {{CSSinfo}} macro is used universally; however, the placement of the `Formal definition` section/block tends to vary with each locale. Refer to other pages in the locale to which you're contributing to see where to place this.
- **Specifications:** specs in `translated-content` are and should be translated from en-US counterparts.
- **Compatibility tables:** translated pages use the same compatibility tables (or macro, depending on the page) as their en-US counterparts, though the content of these tables are translated to the corresponding language.
  - **browser-compat:** only necessary for pages with compatibility tables — the same `browser-compat` value is used in en-US and localized versions. This declaration is placed below `translation_of` in `translated-content` files.
- **Sidebars:** translated pages use the same sidebar macros as their en-US counterparts.

## Key localization differences

Below is a non-extensive list of important differences between `translated-content` and `content` document structures, based on tips from review teams and my observations. Certain "concepts", such as macros, require more in-depth explanations and are given a subsection to address their particularities.

- **Tags:** the translated docs do **not** use tags (teams and contributors are still in the process of removing them) — found at the top of en-US files and possibly translated files where they haven't yet been deleted.
- **No-breaking spaces (mostly French-specific):** when using punctuation that requires spaces before and/or after alphabetic characters like guillemets (`«»`), colons (`:`), semi-colons (`;`), question and exclamation marks (`?` and `!`), use no-breaking spaces (HTML entity `&nbsp`).
  - A seemingly good rule of thumb for this is that when you're in doubt of whether a non-breaking space is "required", use one.
  - For example, note the presence of a non-breaking space in the following sentence: `Travailler avec des formulaires peut s'avérer compliqué&nbsp;!` (*renders as:* Travailler avec des formulaires peut s'avérer compliqué&nbsp;!).
  - An example with guillemets: `des «&nbsp;gouttières&nbsp;»` (*renders as:* des «&nbsp;gouttières&nbsp;»).
- **Translation differences:** keep in mind that it's often not possible to find direct translations — in those cases, translate in a way that "makes sense" in the language concerned, while preserving the key meaning/conveying the main message.
- **Cards in l10n:** see the [Cards](#cards) section for details on using cards (in English, these are `Note:`, `Callout:` and `Warning:`).
- **Images:** see the [Images](#images) section.
- **Links:** see the [Links](#links) section.
- **Macros:** see the [Using macros](#using_macros) section for details on vocabulary macros (`htmlelement`, `cssxref`, etc.) and embed macros (`EmbedLiveSample`, `EmbedInteractiveSample`, etc.).

### Cards

Coming soon!

<!-- To see the card keywords used by each locale, see their corresponding localization JSON file at [mdn/yari/markdown/localizations](https://github.com/mdn/yari/tree/main/markdown/localizations). -->

### Images

Coming soon!

### Links

Coming soon!

### Macros

Coming soon!

#### Vocabulary macros

Coming soon!

#### Live and interactive code samples

Coming soon!

<!-- This section covers best practices for including these embed macros, and not how they work. If you'd like more details on the latter, see [Live samples — The MDN project](https://developer.mozilla.org/en-US/docs/MDN/Structures/Live_samples). -->