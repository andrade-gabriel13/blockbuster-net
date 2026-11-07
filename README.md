# Blockbuster.NET

Lista de filmes e séries para assistir, com visual dark/hi-tech (neon ciano e magenta sobre fundo escuro).

## Contexto

Projeto do exercício **"Minha lista de filmes e séries"** (Vue), originalmente pensado para o [Vue Playground](https://play.vuejs.org). Aqui ele foi montado como uma página estática, para rodar localmente e publicar no GitHub Pages, indo além dos requisitos do exercício.

## O que o site entrega

**Requisitos do exercício**
- Título da lista e nome do autor exibidos a partir de variáveis (`ref` + `{{ }}`).
- Campo de texto com `v-model`; adiciona com o botão ou com Enter, limpa o campo e não aceita título vazio.
- Lista iniciada com 3 títulos (`id`, `nome`, `assistido`) renderizada com `v-for` e `:key`.
- Checkbox de assistido que risca o nome (`:class`) e botão para remover.
- `v-if` / `v-else` com a mensagem "Nada para assistir por enquanto!" quando a lista está vazia.
- Desafio extra: escolha entre **Filme** e **Série** (`<select>`), exibida como tag ao lado do nome.

**Extras**
- **Filtros:** busca por nome, filtro por tipo e abas Todos / Pendentes / Assistidos / Favoritos.
- **Ordenação:** por ordem de adição, A–Z ou nota.
- **Progresso:** contador de assistidos e barra de progresso.
- **Nota** de 0 a 5 estrelas e **favoritos** (♥).
- **Editar nome** com duplo clique (Enter salva, Esc cancela).
- **Sortear** um título pendente para assistir.
- **Limpar assistidos** de uma vez.
- **Persistência** automática no `localStorage` do navegador.
- **Exportar / Importar JSON** para backup ou edição manual, com popup explicando o formato.

### Formato do JSON

```json
[
  {
    "nome": "Matrix",
    "tipo": "Filme",
    "assistido": false,
    "favorito": true,
    "nota": 5
  }
]
```

Só `nome` é obrigatório. `tipo` aceita `"Filme"` (padrão) ou `"Série"`; `nota` vai de 0 a 5. A importação **substitui** a lista atual. A exportação também inclui o `id`, que é ignorado ao importar.

## Stack

- [Vue 3](https://vuejs.org/) (Composition API: `ref`, `computed`, `watch`), carregado por CDN (cdnjs), sem build e sem npm.
- HTML + CSS puros em um único arquivo, `index.html`.
- `localStorage` para persistência.
- GitHub Pages para hospedagem, com deploy via GitHub Actions.

## Rodar local

Abra `index.html` no navegador (precisa de internet para carregar o Vue pelo CDN), ou sirva a pasta:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Publicar no GitHub Pages

O deploy é feito pelo GitHub Actions (`.github/workflows/pages.yml`).

1. Suba o repositório para o GitHub.
2. Em **Settings → Pages → Build and deployment → Source**, escolha **GitHub Actions** (só na primeira vez).
3. A cada push na `main` o workflow publica o site. Também dá para rodar manualmente em **Actions → Deploy to GitHub Pages → Run workflow**.

O endereço final aparece no resumo do job e em Settings → Pages (`https://<usuario>.github.io/<repositorio>/`).

## Estrutura

```
index.html                      # app completo (template, estilos e lógica)
README.md
.github/workflows/pages.yml     # deploy no GitHub Pages
```
