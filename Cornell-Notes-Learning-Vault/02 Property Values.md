---
cssclasses:
  - cornell-left
  - cornell-border
  - banner-image
---
>[!banner-image] ![[banner-data.jpg]]
# Properties
As explained in the [[Cornell Notes in Obsidian#Properties to Mark Your Note as a Cornell Note|Properties to Mark Your Note as a Cornell Note]] section of this vault, you need to include specific instructions in the properties section of a note ton enable  Cornell Notes formatting. This is done by adding one of the following values to the *cssclasses* property in a note.

>[!cue] Values to be used with the cssclasses property

|Value| Purpose|
|-|-|
|cornell-left|Add a cue column to the left of the document (Do not use this with cornell-right)|
|cornell-right|Add a cue column to the right of the document (Do not use this with cornell-left)|
|cornell-border|Add a borderline that separates the cue column and the summary footer. Note: the border line only extends for the length of the content, not the screen. |
|cornell-livepreview|(Experimental) enable the Cornell Notes formatting while editing in Live Preview. This doesn't work so well.|

---

## Examples
The following are examples of *cssclasses* property values that can be added to a file and their various effects.

##### Example 1: Left Cue Column with Borders
```
---
cssclasses:
  - cornell-left
  - cornell-border
---
```

##### Example 2: Left Cue Column with no Borders
- Notice in this example; we don't include the cornell-border value. 

```
---
cssclasses:
  - cornell-left
---
```

##### Example 3: Right Cue Column with Borders
```
---
cssclasses:
  - cornell-right
  - cornell-border
---
```

##### Example 4: Right Cue Column with no Borders
```
---
cssclasses:
  - cornell-right
---
```


#### Notes about the cornell-right Setting
The `cornell-right` value may create a large margin on the left side of a document in wide panes. Unfortunately, this is one limitation of the Cornell Notes Learning Vault. However, in narrower panes, this setting looks good. Also, the page output will look normal when using Export to PDF. This also affects the [[01 Introduction to Tufte Sidenotes|Tufte sidenotes]].

