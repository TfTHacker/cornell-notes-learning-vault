<%*
/*
Author: TfTHacker - more info https://tfthacker.com/
Date: 2023-12-06
  Description: Adds a Cornell Note to the vault with proper frontmatter.
  Part of the Cornell Notes Learning Vault https://tfthacker.com/cornell-notes.
*/

const setFrontMatter = async (file) => {
  await app.fileManager.processFrontMatter(file, (frontmatter) => {
    let newCssClasses = [];
    if (frontmatter && frontmatter.cssclasses) // Remove any existing element starting with cornell-  
      newCssClasses = frontmatter.cssclasses.filter((item) => !item.startsWith("cornell-"));
    newCssClasses.push(columnSide);
    if (columnBorder) newCssClasses.push("cornell-border");
    frontmatter["cssclasses"] = newCssClasses;
  });
}

const isNewFileFromTemplate = tp.config.run_mode === 0 ? true : false;

const columnSide = await tp.system.suggester(["left", "right"], ["cornell-left", "cornell-right"], false, "Select a side for the Cornell Note");
if (columnSide === null) return;

const columnBorder = await tp.system.suggester(["Yes", "No"], [true, false], false, "Should a border be displayed between the cues, summaries and notes?");
if (columnBorder === null) return;

const file = tp.file.find_tfile(tp.file.path(true));

if (isNewFileFromTemplate)
  setTimeout(async () => await setFrontMatter(file), 500); // Wait for the file to be created
else
  await setFrontMatter(file);

%>
