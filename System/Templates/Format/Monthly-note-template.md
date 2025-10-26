---
created: <% tp.date.now("YYYY-MM-DD @ HH:mm") %>
cssclasses:
  - wide-page
tags:
  - calendar/monthly
---

# <% tp.date.now("YYYY-MM, MMM") %>

<< [[<% moment(tp.file.title,'YYYY-MM').add(-1,'month').format("YYYY-MM") %>|⏪ Last month(<% moment(tp.file.title,'YYYY-MM').add(-1,'month').format("YYYY-MM") %>)]] | [[<% moment(tp.file.title,'YYYY-MM').add(1,'month').format("YYYY-MM") %>|Next month(<% moment(tp.file.title,'YYYY-MM').add(1,'month').format("YYYY-MM") %>) ⏩]] >>


- ? Use `Alt + E` e os Snippets com `&` para montar sua revisão  