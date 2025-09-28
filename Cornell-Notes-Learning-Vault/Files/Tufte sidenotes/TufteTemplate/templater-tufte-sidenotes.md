<%*
  /*
  Author: TfTHacker - more info  https://tfthacker.com/
  Date:   2023-11-27
  */


  /*
  Notes:
  - TABLES: Work in tables, but links are buggy
  - LISTS: footnotes are only supported in the first level of list, no in child nodes
  - Sidenotes will overlap with footnotes from other document sections
  - create a template to add Tufte footnote to cssclasses
  - no support for embedded content
  - sidenotes can disappear while editing. they usually appear after reopening file or continuing to edit document outside of current section. This is due to waiting for Obsidian to update the footer section.
  */


  console.log("Loading Tufte Sidenotes Processor");

const templaterPlugin = app.plugins.getPlugin('templater-obsidian').templater;

//if script is reloaded, unregister the Markdown procesor
try {
  templaterPlugin.current_functions_object.obsidian.MarkdownPreviewRenderer.unregisterPostProcessor(window.TufteSidenote.MarkdownPostProcessor);
} catch (error) { }

window.TufteSidenote = {};
window.TufteSidenote.footnotes = {};
window.TufteSidenote.sidenotes = {};

// The Obsidian base class 
class Component {
  load() { }
  onload() { }
  unload() { }
}

class SidenoteRenderer extends Component {
  constructor(el, ctx) {
    super(el);
    this.ctx = ctx;
  }

  // Adds each footnote by section into a container with the class name tufte-sidenotes-collection
  // this class will align the footnotes to the right and stack them using a flex grid
  processFootnotes(el, docId, exportToPDF = false) {
    for (const fRef of Array.from(el.querySelectorAll("sup.footnote-ref"))) {
      const footnoteId = fRef.id.replace("fnref", "fn");

      // Deetermine what should be the parent node for the sidenotes container
      let collectionParentNode;
      if (fRef.parentNode.nodeName === "LI") { //if in a list, only support the first level
        if (fRef.parentNode.parentNode.parentNode.nodeName === "DIV")
          collectionParentNode = fRef.parentNode.parentNode;
      } else if (fRef.parentNode.nodeName === "TD") //if a table
        collectionParentNode = fRef.parentNode;
      else if (fRef.parentNode.nodeName === "P") //if in a paragraph
        collectionParentNode = fRef.parentNode;
      else // default paragraph text flow
        collectionParentNode = exportToPDF ? fRef.parentNode : fRef.parentNode.parentNode;

      // Collection of footnotes
      let sidenotesCollectionEl;
      if (collectionParentNode?.querySelector(".tufte-sidenotes-collection")) {
        sidenotesCollectionEl = collectionParentNode.querySelector(".tufte-sidenotes-collection")
      } else {
        sidenotesCollectionEl = document.createElement("div");
        sidenotesCollectionEl.classList.add("tufte-sidenotes-collection");
        collectionParentNode?.insertBefore(sidenotesCollectionEl, collectionParentNode.firstChild);
      }

      const sidenoteEl = document.createElement("div");
      sidenoteEl.classList.add("tufte-sidenote");
      sidenoteEl.setAttribute("tufte-fn-Id", footnoteId);
      sidenotesCollectionEl.appendChild(sidenoteEl);

      try {
        if (exportToPDF === false) {
          (window.TufteSidenote.sidenotes[docId] ??= []).push(sidenoteEl);
        }
        formatFootnote(sidenoteEl, footnoteId, window.TufteSidenote.footnotes[docId][footnoteId].html);
      } catch (error) { }
    }
  }


  load() {
    super.load();
    // contains("markdown-rendered") true when doing an export to PDF
    this.processFootnotes(this.ctx.el, this.ctx.docId, this.ctx.el.classList.contains("markdown-rendered"));
  }

  onunload() { super.onunload() }

  unload() {
    super.unload();
    const docId = this.ctx.docId;
    const rs = window.TufteSidenote.sidenotes[docId] ??= [];
    rs.remove(this)
    if (rs.length <= 0) {
      delete window.TufteSidenote.sidenotes[docId];
      delete window.TufteSidenote.footnotes[docId];
    }
  }

} //END: SidenoteRenderer

const formatFootnote = (el, footnoteId, innerHTML) => {
  const footnoteNumber = footnoteId.match(/(?<=fn-)\d+(?=-)/)[0];
  el.innerHTML = `<span class="tufte-footnote-number">${footnoteNumber}</span>` + innerHTML;
  el.querySelector("a.footnote-backref.footnote-link").remove();
}

window.TufteSidenote.MarkdownPostProcessor = async (el, ctx) => {

  // Test if the document has the proper css classed defined. It needs:
  // - tufte-sidenotes
  // - either cornell-left or cornell-right
  if (ctx.frontmatter === undefined) return;
  let cssclasses = ctx.frontmatter["cssclass"];
  if (cssclasses === undefined) cssclasses = ctx.frontmatter["cssclasses"]; // make compatible with Obsidian 1.4.1+

  if (!cssclasses?.includes("tufte-sidenotes")) return;
  if (!cssclasses?.includes("cornell-left") && !cssclasses?.includes("cornell-right")) return;

  // Detect if there are footnotes. 
  // If using Export To PDF, the el element has a class called markdown-rendered
  // - This means el is the entire document, not section by section as normally handled by MarkdownPostProcessor
  // if this class doesn't exist, the footnotes are not process until all other sections are process
  // - for this reason we add an empty div for the footnote, then after footnotes section is processed, the
  //   empty food note divs are updated with the html of the footnote
  // Long story short, we have to process "screen" and "Export to PDF" differently in rendering 
  const footnotes = el.querySelectorAll(".footnotes li");
  if (footnotes.length > 0) {
    window.TufteSidenote.footnotes[ctx.docId] = {}
    for (const footnote of footnotes) {
      // Save footnotes for later processing
      window.TufteSidenote.footnotes[ctx.docId][footnote.id] = {
        html: footnote.innerHTML
      }
      // if NOT exporting to PDF, update the footnotes
      if (!el.classList.contains("markdown-rendered"))
        for (sidenoteEl of window.TufteSidenote.sidenotes[ctx.docId])
          if (sidenoteEl.getAttribute("tufte-fn-Id") === footnote.id)
            formatFootnote(sidenoteEl, footnote.id, footnote.innerHTML);
    } // END: for
  } // END: if

  ctx.addChild(new SidenoteRenderer(el, ctx));

}

templaterPlugin.plugin.registerMarkdownPostProcessor(window.TufteSidenote.MarkdownPostProcessor);

%>