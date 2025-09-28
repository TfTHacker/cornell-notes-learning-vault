---
cssclasses:
  - cornell-left
  - cornell-border
  - banner-image
---
>[!banner-image] ![[banner-learn.jpg]]

# How to Take Cornell Notes in Obsidian

>[!summary] How to use?
>- Make a document a Cornell Note - add the following to the property `cssclasses: cornell-left, cornell-border`
>- For cues - use a cue callout `>[!cue]`
>- For a summary - use a summary callout `>[!summary]`


The Cornell Note-Taking System is a methodology for note-taking where you have **three** types of elements in your notes:

1. Notes
2. Cues
3. Summary

This vault contains all you need to do this.

## Install the cornell.css Snippet
The solution presented in this learning vault does not require installing any plugins. However, it does require the installation of a CSS snippet. The instructions for doing this in your vault are in this document: [[Installing the snippet]]. This step must be completed before proceeding.

>[!cue] Properties

## Properties to Mark Your Note as a Cornell Note
Your notes will only display the unique Cornell Note format if you add the necessary property to the beginning of the note. This allows you to control which notes will be Cornell Notes.

>[!Question] What is a property? 
>If you are unfamiliar with the term property, you should learn about this feature of Obsidian before going further. You can read about this feature in Obsidian's online help at this [link](https://help.obsidian.md/Editing+and+formatting/Properties).

To use the Cornell Notes formatting, add a *cssclasses* property to the properties section of a note. It would look like the following:

```
---
cssclasses:
  - cornell-left
  - cornell-border
---
```
This property tells Obsidian to make a Cornell Notes cue column on the page's left side and add the border. To learn about all the cssclasses options, reference the [[02 Property Values]] document.

>[!cue] Cues
## Add Cues to Your Notes
You add a cue to your notes using Obsidian's callout feature and identify the callout as a `cue`.

>[!question] What is a callout?
> If you have not used Obsidian's callout feature, you can learn more about it at this [link](https://help.obsidian.md/Editing+and+formatting/Callouts)

Here is a simple example of a cue callout:
>[!cue] This is a cue
```
>[!cue] This is a cue
```
Looking at the left column, you see how this cue callout renders in Obsidian.
>[!cue] This is another cue
```
>[!cue] This is another cue
```

This is another cue. You can have as many cues as you want; keep adding cue callouts to your document. To learn more about how to use cues, check out [[03 CUE Callouts]].


>[!cue] Summary 
# Adding a Summary to Your Notes

Just as with cues, the Summary section is built on Obsidian callouts. Here is a simple summary of this page:
```
>[!summary] How to use?
>- Make a document a Cornell Note - add the following to the properties `cssclasses: cornell-left, cornell-border`
>- For cues - use a cue callout `>[!cue]`
>- For a summary - use a summary callout `>[!summary]`
```

Learn more about summaries in [[04 SUMMARY Callouts]].