Este é o seu novo *vault*.



---

# Introdução

Estrutura base para um vault do Obsidian contendo templates, snippets, bases de notas e scripts auxiliares. Projetado como um esqueleto reutilizável para organização pessoal, Zettelkasten, gerenciamento de projetos e automações (scripts em Python).

Esta pasta já inclui uma configuração `.obsidian` pronta para uso (plugins, snippets, temas), além de coleções de templates / CSS / scripts para acelerar a criação de novos vaults.
# Alterações e estrutura de uso proposta



![img|400](https://imgur.com/TTkN4ay.png)


## :LiInfo: :LiArrowBigRight:  [[As 3 Areas ACE]]
## :LiFolder: :LiArrowBigRight: [[Estrutura base]]

---

<br>


# Funcionalidades

## Criação de notas 

- `Ctrl + N` para criar uma nova nota – plugin [QuickAdd](https://github.com/chhoumann/quickadd) ![](https://imgur.com/f6ezubJ.png)

## Templates

````tabs
tab: 📜 Formato
```dataview
TABLE without id file.link as "Template"
FROM "X/Templates/Format"
SORT file.name asc
LIMIT 7
`````

tab: & Snippets

```dataview
TABLE without id file.link as "Template"
FROM "X/Templates/Snippet"
SORT file.name asc
LIMIT 10
```

````
## Plugins
- **Calendar** – Visualização em calendário integrada às notas diárias
- **Callout Manager** – Crie e gerencie callouts sem escrever CSS
- **Dataview** – Consulte e organize notas como um banco de dados
- **Force note view mode** – Força um modo de visualização padrão (leitura ou edição) por nota
- **Hotkeys for specific files** – Atalhos personalizados para abrir arquivos específicos rapidamente
- **Iconize** – Adicione ícones personalizados a arquivos, pastas e links
- **Meta Bind** – Campos interativos ligados diretamente ao frontmatter
- **Outliner** – Edição em estilo de lista com atalhos aprimorados
- **Paste URL into selection** – Converte automaticamente o texto selecionado em link
- **Periodic Notes** – Crie e gerencie notas semanais, mensais e anuais
- **QuickAdd** – Captura rápida de conteúdo usando comandos, templates e automações
- **Recent Files** – Acesso rápido a notas abertas recentemente
- **Style Settings** – Interface gráfica para personalizar temas e estilos de plugins
- **Tabs** – Navegação por abas dentro do Obsidian
- **Simple Banner** – Adicione banners visuais às notas
- **Tag Wrangler** – Renomeie, una e gerencie tags em todo o vault
- **Paste Image Rename** – Renomeia automaticamente imagens coladas
- **Settings Search** – Busca e navegação rápidas nas configurações do Obsidian

## Bases :LiArrowBigRight: [[X.base]]


- Visualizações
	- Templates
	- Assets
	- Snippets de CSS de: https://github.com/r-u-s-h-i-k-e-s-h/Obsidian-CSS-Snippets

<center>
  <img src="https://imgur.com/DVkq04P.jpg" width="100%">
</center>


## Atalhos de teclado

![[Hotkeys]]

# Correções de problemas comuns

- Plugins não aparecem: mova a pasta `.obsidian` para dentro do diretório do vault e reinicie o Obsidian.
- Snippets de CSS não aplicam: Configurações → Aparência → Snippets de CSS → ative o snippet desejado.
- Templater não executa: confirme o caminho da pasta de Templates nas configurações do plugin.
    

## Arquivos / Recursos principais

- `.obsidian/` — configurações e plugins instalados.
- `Templates/Format/_ base template.md` — template base para novas notas.
- `Scripts/organizacao_obsidian/ChanGe-Templates-Folder.py` — script para reorganizar templates (leia antes de executar).
- `Assets/Dataview/` — consultas e dashboards prontos para uso com Dataview.
    



![[Créditos & Atribuição]]
```
````