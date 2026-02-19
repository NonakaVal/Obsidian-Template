---
project: "[[<% tp.file.folder() %>]]"
tags:
type: project
created: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
---

```meta-bind-button
label: Criar Nota de Projeto
icon: plus
hidden: false
class: ""
id: TEMPLATE-CRIAR-NOVA-AREA
style: primary
actions:
  - type: command
    command: quickadd:choice:47106046-31c4-44c7-9d17-6044352d6654
```




---
## 🧾 Descrição do Projeto

<%tp.file.cursor()%>



<%* tp.hooks.on_all_templates_executed(async () => { 
    const file = tp.file.find_tfile(tp.file.path(true)); 
    const task_tag_value = tp.file.folder().toLowerCase().split(" ").join("_");
    await app.fileManager.processFrontMatter(file, (frontmatter) => { 
        frontmatter["tags"] = `project/${task_tag_value}`; 
    }); 
}); -%>

