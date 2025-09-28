<%*
/* 
Author: TfTHacker - more info  https://tfthacker.com/
Date: 2023-12-06
Description: Adds a Tufte sidenotes to cssclasss to the current file. Part of the Cornell Notes Learning Vault https://tfthacker.com/cornell-notes.
*/

const setFrontMatter = async (file) => {
    await app.fileManager.processFrontMatter(file, (frontmatter) => {
        if (!frontmatter.cssclasses || !frontmatter.cssclasses.includes("tufte-sidenotes")) {
            if (!frontmatter.cssclasses) frontmatter.cssclasses = [];
            frontmatter.cssclasses.push("tufte-sidenotes");
        }
    });
}

const file = tp.file.find_tfile(tp.file.path(true));
setTimeout(async () => await setFrontMatter(file), 500); // Wait for the file to be created

%>
