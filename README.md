<div align="center">

<img src=".github/readme/banner.svg" alt="Wildbeast — site sobre animais selvagens em HTML e CSS Grid" width="100%">

**Página sobre animais selvagens montada com CSS Grid: três colunas no desktop, duas no tablet e uma no celular.**

[![Demo](https://img.shields.io/badge/demo-ao%20vivo-8844ee?style=for-the-badge&logo=githubpages&logoColor=white)](https://kessleru.github.io/Wildbeast-Web/)
[![GitHub Pages](https://img.shields.io/github/deployments/kessleru/Wildbeast-Web/github-pages?style=for-the-badge&label=pages)](https://github.com/kessleru/Wildbeast-Web/actions/workflows/pages/pages-build-deployment)
[![Último commit](https://img.shields.io/github/last-commit/kessleru/Wildbeast-Web?style=for-the-badge&color=b07dfb)](https://github.com/kessleru/Wildbeast-Web/commits/main)

<img src=".github/readme/desktop.jpg" alt="Página do Lobo Cinza no desktop: menu lateral de ícones, conteúdo com fotos e coluna de anúncios" width="100%">

</div>

## Sobre

A Wildbeast é uma página de ficha de animal — aqui, o **Lobo Cinza** — com menu lateral de ícones,
estatísticas, galeria de fotos, citação em destaque, ficha técnica e uma coluna de anúncios. É um
projeto da [Origamid](https://www.origamid.com), feito só com HTML e CSS.

O ponto do projeto é o layout: a página inteira é um único grid descrito por
`grid-template-areas`, e cada breakpoint redesenha o mapa de áreas em vez de mexer em larguras e
floats.

## Telas

### Tablet — abaixo de 1200px

A coluna de anúncios desce para baixo do conteúdo e o menu de ícones ocupa a lateral inteira.

<img src=".github/readme/tablet.jpg" alt="Página em 1000px: duas colunas, menu de ícones à esquerda e conteúdo à direita" width="100%">

### Celular — abaixo de 760px

<table>
<tr>
<td width="50%"><img src=".github/readme/mobile.jpg" alt="Página no celular em coluna única" width="100%"></td>
<td width="50%">

Tudo vira uma coluna só, na ordem `header → sidenav → content → anuncios → footer`, e o menu de
ícones passa a ser uma faixa com rolagem horizontal.

</td>
</tr>
</table>

## O grid

```css
.estrutura {
  grid-template-columns: minmax(160px, 1fr) 3fr 300px;
  grid-template-areas:
    'header  header  header'
    'sidenav content anuncios'
    'footer  footer  footer';
}

@media (max-width: 1200px) {
  .estrutura {
    grid-template-columns: minmax(160px, 1fr) 3fr;
    grid-template-areas:
      'header  header'
      'sidenav content'
      'sidenav anuncios'
      'footer  footer';
  }
}
```

## Funcionalidades

| | |
|---|---|
| 🧩 **Layout por áreas** | `grid-template-areas` redesenhado em 1200px, 760px e 600px |
| 🐾 **Menu de ícones** | Seis animais em SVG na lateral, que viram uma faixa com rolagem horizontal no celular |
| 🖼️ **Galeria** | Fotos em grid de duas colunas e uma imagem em largura total |
| 📋 **Ficha técnica** | Lista estilizada com fonte monoespaçada |
| 📰 **Anúncios** | Coluna própria no desktop, com texto sobreposto às imagens |

## Stack

| Camada | Ferramenta |
|---|---|
| Marcação | HTML5 |
| Estilo | CSS3 — Grid, `grid-template-areas`, Flexbox, media queries |
| Fonte | [Vollkorn](https://fonts.google.com/specimen/Vollkorn) (Google Fonts) |
| Deploy | [GitHub Pages](https://pages.github.com) |

## Rodando localmente

```bash
git clone https://github.com/kessleru/Wildbeast-Web.git
cd Wildbeast-Web
python -m http.server 8000
```

Abra `http://localhost:8000`. Não há dependências nem build — abrir o `index.html` direto no
navegador também funciona.

## Estrutura

```
├── index.html
├── css/
│   └── style.css     # grid geral, componentes e os três breakpoints
└── img/
    ├── icones/       # cervo, leão, gato, vaca, ovelha e abelha (SVG)
    ├── wolf1-3.jpg   # galeria
    └── anuncio-1-2.jpg
```

<details>
<summary><b>Regerando as imagens deste README</b></summary>

```bash
node .github/readme/gerar.mjs                 # banner.svg

python -m http.server 8000                    # em outro terminal
npm i --no-save puppeteer-core sharp
node .github/readme/capturar.mjs              # desktop, tablet e celular, em 2x
```

</details>

---

<div align="center">
<sub>Feito por <a href="https://github.com/kessleru">Otávio Kessler Ustra</a> · projeto da <a href="https://www.origamid.com">Origamid</a></sub>
</div>
