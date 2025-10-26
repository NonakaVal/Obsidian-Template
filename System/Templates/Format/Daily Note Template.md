---
created: <% tp.date.now("YYYY-MM-DD @ HH:mm") %>
tags:
  - calendar/daily
daily-mood:
week: '[[<% tp.date.now("YYYY [Week] WW") %>]]'
---
# <% tp.date.now("YYYY-MM-DD") %>’s Note

[[<% tp.date.yesterday("YYYY-MM-DD") %>|↶ Previous Day]] | [[<% tp.date.tomorrow("YYYY-MM-DD") %>|Following Day ↷]]

---

 🔹 `INPUT[inlineSelect(option('🙂 – Neutral'), option('😄 – Happy'), option('😐 – Meh'), option('😞 – Sad'), option('😠 – Frustrated'), showcase):daily-mood]`

# Work Log



<%tp.file.cursor()%>


# Logs 
