
# Introdução 


> ⚠️ Está vault é um template -   Não está Padrão do [Obisidian.md](https://obsidian.md/) -  Leia A apresentação Abaixo para o uso 




---




Estrutura base para um vault do Obsidian contendo templates, snippets, bases de notas e scripts auxiliares.

> 🔗 [Github Template Repo](https://github.com/NonakaVal/Obsidian-PKM-Intro-Template-Vault) -  ⬇️ `.zip` [Download Link](https://github.com/NonakaVal/Obsidian-PKM-Intro-Template-Vault/raw/refs/heads/main/Obsidian-PKM-Intro-Template-Vault.zip)

# Alterações e estrutura de uso proposta



# Conceitos Importantes

- ![[As 3 Areas ACE]]
- [[Estrutura base]]

<br>

# Funcionalidades


#### ➕ Criação de notas 

- `Ctrl + N` para criar uma nova nota – plugin [QuickAdd](https://github.com/chhoumann/quickadd)

![](https://imgur.com/f6ezubJ.png)


#### 💭 Daily Captures

> Registros rápidos nas notas diárias

![[daily-capture.png]]

#### ⚡ Templates


````tabs
tab: Formatação

```dataview
TABLE without id file.link as "Template"
FROM "X/Templates/Format"
SORT file.name asc
LIMIT 7
```
tab: Snippets
```dataview
TABLE without id file.link as "Template"
FROM "X/Templates/Snippet"
SORT file.name asc
LIMIT 10
```
````


####  🗄️ Bases  


> Visualizações
> - Templates
> - Assets
> - Snippets de CSS de: https://github.com/r-u-s-h-i-k-e-s-h/Obsidian-CSS-Snippets

<center>
  <img src="https://imgur.com/DVkq04P.jpg" width="100%">
</center>


#### ⌨️ Atalhos de teclado

![[_atalhos]]


<br>

# Próximos Passos 

```meta-bind-button
label: Começe Aqui (Tópicos em Ordem)
hidden: false
icon: space
class: ""
id: workspaces
style: destructive
actions:
  - type: command
    command: workspaces:load
```




---

<br>
<br>
<br>

# 🔌 Lista de Plugins da Comunidade
- **[Calendar](https://obsidian.md/plugins?id=calendar)** – Visualização em calendário integrada às notas diárias 
- **[Callout Manager](https://obsidian.md/plugins?id=callout-manager)** – Crie e gerencie callouts sem escrever CSS
- **[Dataview](https://obsidian.md/plugins?id=dataview)** – Consulte e organize notas como um banco de dados
- **[Force note view mode](https://obsidian.md/plugins?id=obsidian-view-mode-by-frontmatter)** – Força um modos de visualização
- **[Hotkeys for specific files](https://obsidian.md/plugins?id=obsidian-hotkeys-for-specific-files)** – Atalhos personalizados para abrir arquivos específicos 
- **[Iconize](https://obsidian.md/plugins?id=obsidian-icon-folder)** – Adicione ícones personalizados a arquivos, pastas e links
- **[Meta Bind](https://obsidian.md/plugins?id=obsidian-meta-bind-plugin)** – Campos interativos ligados diretamente ao frontmatter
- **[Outliner](https://obsidian.md/plugins?id=obsidian-outliner)** – Edição em estilo de lista com atalhos aprimorados
- **[Paste URL into selection](https://obsidian.md/plugins?id=url-into-selection)** – Converte automaticamente o texto selecionado em link
- **[Periodic Notes](https://obsidian.md/plugins?id=periodic-notes)** – Crie e gerencie notas semanais, mensais e anuais
- **[QuickAdd](https://obsidian.md/plugins?id=quickadd)** – Captura rápida de conteúdo usando comandos, templates e automações
- **[Recent Files](https://obsidian.md/plugins?id=recent-files-obsidian)** – Acesso rápido a notas abertas recentemente
- **[Tabs](https://obsidian.md/plugins?id=tabs)** – Navegação por abas dentro do Obsidian
- **[Simple Banner](https://obsidian.md/plugins?id=simple-banner)** – Adicione banners visuais às notas
- **[Tag Wrangler](https://obsidian.md/plugins?id=tag-wrangler)** – Renomeie, una e gerencie tags em todo o vault
- **[Paste Image Rename](https://obsidian.md/plugins?id=obsidian-paste-image-rename)** – Renomeia automaticamente imagens coladas
- **[Settings Search](https://obsidian.md/plugins?id=settings-search)** – Busca e navegação rápidas nas configurações do Obsidian



# 🆘 Correções de problemas comuns

- Bugs de sistema e de blocos de plugins.

![[rebuild vault cache.png|600]]

- Snippets de CSS não aplicam: Configurações → Aparência → Snippets de CSS → ative o snippet desejado.

![[snippetss.png|500]]

- Templater não executa: confirme o caminho da pasta de Templates nas configurações do plugin.




<br><br><br><br>


---




![[Créditos-Atribuições]]