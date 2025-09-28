---
cssclasses:
  - banner-image
  - cornell-left
  - cornell-border
---
>[!banner-image] ![[banner-printer.jpg|300]]
# Printing and PDF
>[!cue] Export to PDF Command

Obsidian has no **Print** feature. However, we can export a Markdown document to PDF using the **Export to PDF** command. This command will generate a PDF document that can then be printed. 

The Export to PDF command, though, has its limitations. The formatting and layout of your Markdown document will likely look slightly different in PDF. 

This can be frustrating, but it is essential to remember that the way a Markdown document renders on a screen differs from paper since both mediums have advantages and disadvantages. Obsidian makes some choices about how Markdown is rendered into PDF, which does the job very well in most cases but, in some cases, may not be what you expected.

---
>[!cue] Limitations

The cornell.css includes some additional parameters to help export Markdown documents to PDF. However, there are some limitations. Keep the following in mind:
- Only cues are displayed in the margin.
- Summaries are not rendered at the top or bottom of a page but as a standard Obsidian callout. 
- If you enabled border lines in your document, these are not exported to PDF. (This is due to the difference in how Obsidian handles PDF documents)
- When [embedding a file](https://help.obsidian.md/Linking+notes+and+files/Embedding+files) with cues into another document, the embedded file will not be printed.

While there are limitations, the overall effect of Cornell Notes is maintained when exporting a Markdown document to PDF.

