---
created: <% tp.date.now("YYYY-MM-DD @ HH:mm") %>
tags:
  - calendar/daily
week: '[[<% tp.date.now("gggg-[W]ww") %>]]'
---

<% tp.date.now("YYYY-MM-DD") %>’s Note

[[<% tp.date.yesterday("YYYY-MM-DD") %>|↶ Ontem]] | [[<% tp.date.tomorrow("YYYY-MM-DD") %>|Amanhã ↷]]

# Daily Mood 

 `INPUT[inlineSelect(option('🙂 – Neutral'), option('😄 – Happy'), option('😐 – Meh'), option('😞 – Sad'), option('😠 – Frustrated'), showcase):daily-mood]`


---

# Gratidão

 _Comece o dia escrevendo pelo que você é grato(a) para cultivar um senso de contentamento e apreciação_








---

# Registro de Trabalho #inlog

<%tp.file.cursor()%>

---

# Algo bom

_Recorde e anote acontecimentos positivos do seu dia, por menores que sejam._
   

---



<%*
const folderPath = "Calendar & Review/Daily Notes";
if (!tp.app.vault.getAbstractFileByPathInsensitive(folderPath)) {
  await tp.app.vault.createFolder(folderPath);
}
await tp.file.move(`${folderPath}/${tp.file.title}`);
-%>

