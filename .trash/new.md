---
created: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
collection: [[<% selectedItem %>]]
---

<%*
const folder = "X/Collections";
const items = tp.app.vault.getMarkdownFiles().filter(x => x.path.startsWith(folder));
const selectedItem = (await tp.system.suggester((item) => item.basename, items)).basename;
-%>


