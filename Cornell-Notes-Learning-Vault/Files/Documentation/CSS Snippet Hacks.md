---
cssclasses:
  - border-around-images
---
# CSS Snippet Hacks
This document includes several exciting solutions to the needs of Cornell Notes Learning Learning Vault users. These "hacks" are not supported but are provided as insights into how Cornell Notes can be adapted in various environments.

This file consolidates those hacks and is intended for users who are comfortable working with CSS Snippets and modifying CSS.

>**Note:** There is no support for these hacks; they are provided as learning tools for the community to build on. They are not thoroughly tested, so they may not work in every usage scenario. But since they are so interesting, they are provided for your experimentation. 

---

# Adding a Borderline across the top of a Cue till the End of the Document
This hack will draw a line across the top of the cue, and that line will extend from the far left-hand margin of the document to the right-hand margin, as shown in this image:
![[Hack-cue-top-borderline.png|500]]
*Inspired by: `Mastodon:@autonomygaps@pkm.social`*
###### CSS Snippet
```css
.markdown-preview-view.cornell-cue-top-border:is(.cornell-left, .cornell-right) .markdown-preview-section [data-callout="cue"] {
    width: 100% !important;
    border-top: 1px solid var(--background-modifier-border) !important;
    .callout-title,
    .callout-content {
        width: var(--cornell-cue-callout-width) !important;  
        padding-bottom: 0px;
    }
    .callout-content {
        padding-top: 0px !important;
        margin-top: 0px !important;
    }
}

.markdown-preview-view.cornell-right.cornell-cue-top-border .markdown-preview-section [data-callout="cue"] {
    .callout-title,
    .callout-content {
        position: fixed !important;
        right: 0px !important;
    }
    .callout-content {
        margin-top: 25px !important;
    }
}
```

###### Using This Snippet
Add the following value to the cssclass in the *cssclasses* property: `cornell-cue-top-border`.

This snippet will likely need to be fine-tuned for your theme. A few things to look for are the width of the cue. This can be changed by replacing the value for width. For example, change:

`width: var(--cornell-cue-callout-width) !important;`

to some other value, like 140px:

`width: 140px;`

---
# Make the Title Area of a Callout that is a Cue Default to Standard Text Formatting
This hack makes the title area of a callout cue use standard text formatting, not a title format.
![[Hack-Normal-Title-Cues.png|500]]

*Inspired by: `jkenton on Discord`*
###### CSS Snippet
```css
.markdown-source-view.cornell-cue-normal-title:is(.cornell-left,  .cornell-right),
.markdown-preview-view.cornell-cue-normal-title:is(.cornell-left, .cornell-right){
    .callout-title-inner {
        color: var(--text-normal);
        font-weight: var(--anp-font-preview-wt, normal) !important; 
    }
} 
```

###### Using This Snippet
Add the following value to the cssclass in the *cssclasses* property: `cornell-cue-normal-title`.


---
# # Customizing the Font Areas of the Cues and Summaries

With CSS, how can the font attributes used within cues and summaries be changed? The following CSS snippet shows how to change the content body and titles of cues and summaries.

*Inspired by: `anderbill on Discord`*
###### CSS Snippet
```css
div:not(.markdown-embed-content) >  :is(.cornell-left, .cornell-right) [data-callout="cue"] {
    .callout-content {
        font-size: 16pt;
        color: blue;
    }

    .callout-title-inner {
        font-size: 18pt;
        color: green;
    }
}

div:not(.markdown-embed-content) >  :is(.cornell-left, .cornell-right) [data-callout="summary"] {
    .callout-content {
        font-size: 16pt;
        color: chocolate;
    }

    .callout-title-inner {
        font-size: 18pt;
        color: sienna;
    }
}
```

The .callout-title-inner is where you can change the font attributes for the title part of the callouts, and the .callout-content is where you change font attributes for the content inside a cue or summary.

This is a simple example, just changing font size and color, but a lot more can be done, including the style of font used, its weight, and so on. If you know a little CSS, you might want to hack around with giving your cues and summaries more personal style.
