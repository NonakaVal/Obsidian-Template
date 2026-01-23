<%*
const folder = "X/Collections";
const items = tp.app.vault
  .getMarkdownFiles()
  .filter(x => x.path.startsWith(folder));

const selectedItem = (await tp.system.suggester(
  item => item.basename,
  items
))?.basename;

const createdDate = tp.date.now("YYYY-MM-DD");

/* FRONTMATTER (fica acima) */
tR += `---
created: "[[${createdDate}]]"
collection: "[[${selectedItem}]]"
---\n\n`;
-%>

