---
title: Introdução
permalink: /docs/home/
redirect_from: /docs/index.html
---


A falta de tratamento de efluentes e o seu descarte inadequado acarretam em problemas ambientais. Quando o tratamento não é realizado, o descarte destes efluentes nos corpos receptores e no solo torna-se altamente nocivo à composição química da água e ao lençol freático que aos poucos vão sendo contaminados. Segundo {% cite amaral2017diretrizes %}, em áreas urbanas, com considerável concentração de pessoas, o lançamento sem tratamento dos esgotos aumenta ainda mais o risco, principalmente quanto à redução da qualidade da saúde da população. Por esta razão há a necessidade de se tratar os efluentes domésticos em ETE.


As Estações de Tratamento de Efluentes (ETE) têm por objetivo  reduzir a sua carga poluidora e atender aos padrões de exigências de lançamento no corpo  receptor sem degradar o meio ambiente {% cite neumann2017 %}. O tratamento de efluente doméstico, em especial, remove os constituintes presentes no esgoto que alteram as características físico, químicas e biológicas da água. Segundo {% cite menezes2017 %}, a escolha do tipo de tratamento para cada situação é feita considerando-se várias condições, desde a eficiência desejada até o custo final de operação. Existem vários processos disponíveis, por esta razão cada ETE possui um arranjo de unidades que varia em função das características desejadas para o efluente, respeitando os limites estabelecidos pela legislação vigente.

As ETEs, assim como qualquer processo, deve ser monitorada para que a eficiência do sistema implantado alcance o que foi previsto em projeto. O controle da estação é realizado através de vários parâmetros que podem ser determinados _in situ_ a exemplo da vazão, do \ac{OD}, \ac{SS}, \ac{pH}, \ac{SDT}, condutividade e salinidade, e outros em laboratório através de coleta de amostras, como \ac{DBO}, \ac{DQO}, \ac{SST}, nitrogênio amoniacal, fósforo, dentre outros. As determinações _in situ_ e as amostras seguem procedimentos específicos para cada parâmetro, o que torna o controle manual suscetível a erros e esquecimentos.

Sabe-se, ainda, que cada um dos parâmetros possui uma metodologia específica e caso não haja um bom planejamento experimental podem ocorrer erros no processo de amostragem e de determinação dos parâmetros em laboratório {% cite nascimento2017thais %}. Por esta razão há a necessidade de se utilizar ferramentas no auxílio do gerenciamento das atividades dos operadores das ETEs.

A tecnologia vem para agregar mais agilidade nos processos e seu uso já se faz presente em algumas ETEs do Brasil e é recorrente nos países desenvolvidos. Automatizar toda uma estação sai muito caro, mas há a possibilidade de desenvolver uma ferramenta computacional multiplataforma para controlar o processo no que se refere à coleta de dados do processo e metodologia de determinação de parâmetros, que hoje é realizada de manualmente nas ETEs do estado de Sergipe.







## Getting started asdasd sadsad sss

[GitHub Pages](https://pages.github.com) can automatically generate and serve the website for you.
Let's say you have a username/organisation `my-org` and project `my-proj`; if you locate Jekyll source under `docs` folder of master branch in your repo `github.com/my-org/my-proj`, the website will be served on `my-org.github.io/my-proj`.
The good thing about coupling your documentation with the source repo is, whenever you merge features with regarding content to master branch, it will also be published on the webpage instantly.

1. Just [download the source](https://github.com/aksakalli/jekyll-doc-theme/archive/gh-pages.zip) into your repo under `docs` folder.
2. Edit site settings in  `_config.yml` file according to your project. !!! `baseurl` should be your website's relative URI like `/my-proj` !!!
3. Replace `favicon.ico` and `img/logonav.png` with your own logo.

## Writing content

### Docs

Docs are [collections](https://jekyllrb.com/docs/collections/) of pages stored under `_docs` folder. To create a new page:

**1.** Create a new Markdown as `_docs/my-page.md` and write [front matter](https://jekyllrb.com/docs/frontmatter/) & content such as:

```
---
title: My Page
permalink: /docs/my-page/
---

Hello World!
```

**2.** Add the pagename to `_data/docs.yml` file in order to list in docs navigation panel:

```
- title: My Group Title
  docs:
  - my-page
```

### Blog posts

Add a new Markdown file such as `2017-05-09-my-post.md` and write the content similar to other post examples.

### Pages

The homepage is located under `index.html` file. You can change the content or design completely different welcome page for your taste. (You can use [bootstrap components](http://getbootstrap.com/components/))

In order to add a new page, create a new `.html` or `.md` (markdown) file under root directory and link it in `_includes/topnav.html`.
