```dataview
TABLE WITHOUT ID
	file.link AS "📂 Coleção",
	file.inlinks AS "📝 Notas",
	length(file.inlinks) AS "🔢 Total"
FROM "X/Collections"
SORT file.ctime DESC
LIMIT 33

```
