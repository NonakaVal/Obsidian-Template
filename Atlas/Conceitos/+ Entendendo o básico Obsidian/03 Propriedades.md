---
collection: "[[+ Gestão de Conhecimento]]"
---
No **Obsidian** (e em sistemas de PKM em geral), **metadados** são informações adicionais registradas no início de cada nota, geralmente no formato **YAML frontmatter**:

```yaml
---
created: [[2025-08-19]]
up: [[Projeto X]]
collection: [[Estudos]]
related: [[Ideia A]], [[Pessoa B]]
---
````

Esses metadados funcionam como **camadas de contexto**, ajudando a:
- Organizar e estruturar suas notas
- Navegar entre hierarquias e conexões
- Automatizar consultas com **Dataview** ou **DataviewJS**
---

### 🔑 Principais Metadados

- **`created` → Data de criação**  
    Acompanha a linha do tempo das anotações e permite gerar históricos, revisões mensais ou anuais.
    > Ex.: `created: [[2025-08-19]]`
- **`up` → Hierarquia**  
    Define a **nota superior** ou o contexto maior em que a nota se insere.
    > Ex.: um capítulo teria `up: [[Livro X]]`.
- **`collection` → Coleções**  
    Agrupa notas em **temas ou áreas específicas**.
    > Ex.: `collection: [[AULAS]], [[CURSOS]]`
- **`related` → Conexões manuais**  
    Lista notas relacionadas, ampliando o **Graph View** com links explícitos.
    > Ex.: `related: [[Conceito Y]], [[Questão Z]]`

---

### 🛠️ Dicas de Uso

- Combine `collection` + `related` para criar **mapas de estudo personalizados**.
- Use `up` em conjunto com MOCs para estruturar **hierarquias claras**.
- Explore consultas com Dataview (ex.: `TABLE created, up, collection FROM "Estudos"`).

<br>

 Seguir para ➡️ [[04 Entendendo Coleções]]
