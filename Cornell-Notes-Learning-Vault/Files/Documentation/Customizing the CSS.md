---
cssclasses:
  - banner-image
---
>[!banner-image] ![[banner-code.jpg]]
# Customizing the cornell.css File
The cornell.css file included with this vault can be customized for your needs. You may need to make adjustments so that the Cornell Note formatting works well in your vault. Specifically, the colors used along with the column widths may need adjustment.

However, changing the CSS file can easily break the styling. So, it is always good to have a backup of the cornell.css file.

This document will highlight some key settings you may want to adjust. The good news is that most of the values you want to adjust are at the top of the cornell.css file.

If you don't mind using a plugin, these customizations can be made with the Style Settings plugin. See the document [[Customizing Cornell Notes with the Style Settings Plugin]].

#### Colors
The cornell.css contains the following variables that affect the coloring of borders and summaries:
```css
.theme-light {
  --cornell-summary-callout-background-color: aliceblue;
  --cornell-border-color: grey;
}

.theme-dark {
  --cornell-summary-callout-background-color: rgb(46, 42, 42);
  --cornell-border-color: rgb(55, 53, 53);
}
```
There are variables for dark mode and light mode. The summary color can be changed, along with the border color. You'll want to modify the color values here to match your theme.

The default colors in this script work well with the default theme in Obsidian.

Consult with this online resource for more color options: https://www.w3schools.com/cssref/css_colors.php

#### Cues
The width of the cue and the column where the cue is displayed (either in the left or right margin) are controlled by these variables:
```css
--cornell-cue-column-width: 150px;
--cornell-cue-column-width-readable-line: 150px;

--cornell-cue-callout-width: 160px;
--cornell-cue-callout-width-readable-line: 160px;
```
`--cornell-cue-column-width` controls the margin on the document's left or right. This margin width is used when the user uses cornell-left or cornell-right in the notes [[02 Property Values|properties]].

`--cornell-cue-callout-width: 160px` controls the width of the callout itself. The default theme is a little wider than the margin. This has to do with the way the default theme formats callouts. 

You'll also notice separate settings for when the user is using **readable line length**. If you use readable line length, you'll want to adjust the variables with `-readable-line` at the end.

#### Summary
The height of the summary callout that appears at the bottom of the screen is controlled with this variable and can be adjusted:
```css
--cornell-summary-callout-max-height: 150px !important;
```

The height of the summary that appears at the top of a screen can also be customized by changing this variable:
```css
--cornell-summary-callout-top-height: 150px !important;
```

#### Screen Width for Mobile Devices

The following line determines the minimal width of a screen for the Cornell Notes styling to take effect. 
```css
@media (min-width: 400px) {
```
If the screen is less than 400px, a column for the cues is not created. You can adjust this minimum width to better match your personal mobile devices.


## More Information
Please see [[Theme specific customizations]] for more information about fine-tuning cornell.css for other themes.