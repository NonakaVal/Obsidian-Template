
---
created: <% tp.date.now("YYYY-MM-DD @ HH:mm") %>
cssclasses:
  - wide-page
tags:
  - calendar/week
---

:LiCalendarCheck2: [[<% tp.date.now("YYYY [Week] WW", -7) %>|↶ Previous Week]] | [[<% tp.date.now("YYYY [Week] WW", 7) %>|Following Week ↷]] 
~<% tp.date.now("YYYY-MM [Week] WW") %>  

<%tp.file.cursor()%>


<%*
const folderPath = "Calendar & Review/Weekly Notes";
if (!tp.app.vault.getAbstractFileByPathInsensitive(folderPath)) {
  await tp.app.vault.createFolder(folderPath);
}
await tp.file.move(`${folderPath}/${tp.file.title}`);
-%>

