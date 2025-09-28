---
cssclasses:
  - cornell-left
  - cornell-border
  - banner-image
---
>[!banner-image] ![[banner-bullhorn.jpg]]
# Cue Callouts
The Cornell Notes formatting for cues is trigged with an [Obsidian callout](https://help.obsidian.md/Editing+and+formatting/Callouts#Customize%20callouts) using a callout type identifier of `cue`.

As defined in [[02 Property Values]], the cue can appear to the left (as it does in this document) or to the right.

>[!cue] Simple Example Cue

Here is an example cue:
```
>[!cue] Simple Example Cue
```
Let us break this down. 
- The first character on the line is `>`, this character tells Obsidian to treat this line as a [block quote](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax#Quotes), which is formatted in a special way by Obsidian.
- The following characters `[!cue]` tell Obsidian to treat this block quote as a callout and that it is of the type **cue**. Obsidian supports several predefined [types](https://help.obsidian.md/Editing+and+formatting/Callouts#Supported%20types). This sample vault adds a [custom callout type identifier](https://help.obsidian.md/Editing+and+formatting/Callouts#Customize%20callouts) named **cue** to your vault. 
- The **cornell.css** you installed earlier has custom formatting for putting a cue callout into the left or right margin.

>Also note that the cue tends to be visible in the line below where it is inserted. For this reason, add your cue callouts just above the line where you want the cue to appear. 

---
# Tips
Cue callouts give our documents a snappy visual representation of crucial ideas. However, remember that we are forcing markdown into a narrow column. This narrow column has limitations. Keep the following in mind:
- Keep the length of the text as short as possible. Long text may not flow into the column as expected, or it is hard to connect the cue with the notes in the note area if it is too long.
- If one cue is long, that is, has a lot of text, and another is started near the first one, the cues may overlap in the margins. When there is overlap, you need to shorten the text of the first cue.
- The cues are formatted based on the settings in the theme used by the Obsidian. Not all themes will work well with the **cornell.css** CSS snippet. Some experimentation is required.

>[!info] Bonus Tip
> Having two panes open to the same document can be helpful. On the left side, have the document open in Live Preview mode and have the second pane open in Preview mode. That way, you can see how your document will appear when the Cornell Notes formatting is applied to it. Check out this article about the [Link with Tab](https://medium.com/obsidian-observer/obsidian-quick-tip-enhance-markdown-editing-with-link-with-tab-55a8b5c99177) feature to make side-by-side editing of documents easier.

---
# Examples

>[!cue] Simple Example Cue
##### Example 1: Simple Cue
```
>[!cue] Simple Example Cue
```
>[!cue] Title for cue
>- text under the title 
##### Example 2: Title with Text under it
```
>[!cue] Title for cue
>- text under the title 
```
>[!cue] Links in a cue
>[[00 START HERE]]
>[[01 INDEX]]
##### Example 3: Title with Links under it
```
>[!cue] Links in a cue
>[[00 START HERE]]
>[[01 INDEX]]
```
>[!cue] ![[nuclear-power.jpg|130]]
##### Example 4: Image in a Cue
```
>[!cue] ![[nicolas-hippert-C82jAEQkfE0-unsplash.jpg|130]]
```
- You can control the size of an image by adding a | sign followed by the pixel length of the image. See this [link](https://help.obsidian.md/Linking+notes+and+files/Embedding+files#Embed%20an%20image%20in%20a%20note) for more details.

>[!cue] The Basics
>
>|Concepts to learn|
>|-|
>|Water types|
>|Colors|
>|Composition|


##### Example 5: Table in a Cue

```
>[!cue] The Basics
>
>|Concepts to learn|
>|-|
>|Water types|
>|Colors|
>|Composition|
```
