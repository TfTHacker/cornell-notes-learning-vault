---
cssclasses:
  - cornell-right
---

> [!info]
> ![[Sidenotes Beta]]

# Sidenotes
Once you have completed the configuration as explained in [[Installing the Tufte Sidenotes Solution]], adding Tufte sidenotes to your documents is a breeze.

## Add Tufte-style Sidenotes to the Cssclass

First, in the cssclass of the document, you have to define if the margins are on the left or right, using the cornell-left or cornell-right values. These values are documented in [[02 Property Values]].

Second, add `tufte-sidenotes` value to the cssclass. 


As an example, the *cssclasses* property for right-margin sidenotes would look like this:


>[!cue] Right margin sidenotes
```
---
cssclasses: cornell-right tufte-sidenotes
---
```


If you want the sidenotes to appear in the left-hand margin, then use cornell-left, as shown in the following:

>[!cue] Left margin sidenotes

```
---
cssclasses: cornell-left tufte-sidenotes
---
```
The Cornell Notes margins and cues are designed to work side-by-side with the Tufte sidenotes.


## Footnotes

Sidenotes are created from Obsidian footnotes. So as you add footnotes to your document, they will appear as sidenotes when you switch from editing mode to Preview mode in Obsidian.

>[!cue] Standard & Inline footnotes 

You can learn more about Obsidian footnotes in [Obsidian's online help](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax#Footnotes). Also, note that this solution supports standard numbered footnotes and inline footnotes.

##### Tufte-hide-footnotes

By default, when using the Tufte-style sidenotes solution provided by this vault, the footer section is still displayed at the bottom of the document in preview mode or when exported to PDF. If you would like the footnotes section of a document in Preview mode not to be visible, add the `tufte-hide-footnotes` to the *cssclasses* property.

## Preview Mode
This solution makes sidenotes appear when viewing a document in Preview mode in Obsidian. Sidenotes are not visible while editing a document in Live Preview mode or Source mode.

## Support for Export to PDF
>[!cue] Printing

To support sidenotes in PDF, nothing else needs to be done other than defining the cssclass values as defined in the previous section of this document.

However, please keep in mind that PDF documents rendered by Obsidian do not always 100% look the same as they do in Obsidian. There can be subtle differences between text and margin alignments.

## Nothing is Ever Perfect
This solution is forcing Obsidian to do some internal monkey business and as a result, the solution in this vault is not perfect. There are a number of cases where the Tufte sidenotes won't work as we expect them. However, with trial and error, you will see they work in most documents.

>[!cue] Close/Reopen
>Sometimes you need to close/reopen a document to get the sidenotes to appear.

**A few known issues:**
- **Tables**: sidenotes work with tables, but the footnote indicator links don't work as expected.
- **Lists**: sidenotes are only supported in the first level, not in secondary levels.
- **Images** and **Embeds** are not supported in sidenotes, but regular text and text formatting are supported. If you need to use an image or embed, use a [[03 CUE Callouts|cue]].
- Sidenotes will **overlap** other sidenotes if the footnotes from one paragraph and another paragraph are too close. When sidenotes overlap, you will have to experiment with the footnote locations to create space between the sidenotes.
- Sidenotes **can disappear** while editing. They usually reappear after reopening a file or continuing to edit a document outside of the current section. This is due to waiting for Obsidian to update the footer section. Closing and reopening a document will usually force all sidenotes to render correctly.


![[02 Property Values#Notes about the cornell-right setting]]