<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Uma coleção de dicas para aumentar as tuas habilidades no CSS.

> Dá  uma olhada em outras [listas fantásticas](https://github.com/sindresorhus/awesome/) mantidas por [@sindresorhus](https://github.com/sindresorhus/).


## Índice

* [Protips](#protips)
* [Suporte](#suporte)
* [Contribuições](../../CONTRIBUTING.md)


## Protips

1. [Usa um Reset CSS](#usa-um-reset-css)
1. [Herda o `box-sizing`](#herda-o-box-sizing)
1. [Usa `unset` Em vez de of Reconfigurar Todas as Propriedades](#usa-unset-Em-Vez-De-reconfigurar-todas-as-propriedades)
1. [Usa `:not()` para Aplicar/Remover Bordas](#usa-not-para-aplicarremover-bordas)
1. [Define o `line-height` no `body`](#define-o-line-height-no-body)
1. [Alinha Elementos Verticalmente](#alinha-elementos-verticalmente)
1. [Listas Separadas por Vírgula](#listas-separadas-por-vírgula)
1. [Seleciona Itens Usando `nth-child` Negativo](#seleciona-itens-usando-nth-child-negativo)
1. [Ícones SVG](#Ícones-svg)
1. [Usa o Seletor "Lobotomized Owl"](#usa-o-seletor-lobotomized-owl)
1. [Sliders em CSS com `max-height`](#sliders-em-css-com-max-height)
1. [Tabelas com Células de Tamanho Igual](#tabelas-com-células-de-tamanho-igual)
1. [Esquece as "Margin Hacks", use Flexbox](#esquece-as-margin-hacks-use-flexbox)
1. [Usa Seletores de Atributo em Links Vazios](#usa-seletores-de-atributo-em-links-vazios)
1. [Estiliza Links "Default"](#estiliza-links-default)
1. [Espaçamento Vertical Consistente](#espaçamento-vertical-consistente)
1. [Div com Proporção de Tela Fixa](#div-com-proporção-de-tela-fixa)
1. [Estiliza Imagens Quebradas](#estiliza-imagens-quebradas)
1. [Usa `rem` para Definir Tamanhos Globais; Usa `em` para Definir Tamanhos Locais](#usa-rem-para-definir-tamanhos-globais-usa-em-para-definir-tamanhos-locais)
1. [Esconde Vídeos em Autoplay Que Não Estejam no modo Mudo](#esconde-vídeos-em-autoplay-que-não-estejam-no-modo-mudo)
1. [Usa `:root` para uma Tipografia Flexível](#usa-root-para-uma-tipografia-flexível)
vel1. [Define `font-size` em Elementos de Formulário para uma Melhor Experiência Móvel](#Define-font-size-em-elementos-de-formulário-para-uma-melhor-experiência-móvel)


### Faz um Reset CSS

Reiniciar o CSS vai ajudar te a manter a consistência de estilo em diferentes navegadores com um ponto de partida limpo para elementos de estilo. Tu podes usar a biblioteca de reset CSS como [Normalize](http://necolas.github.io/normalize.css/), ou se preferires,adota uma abordagem mais simplificada.:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Agora os elementos estão sem margens, preenchimento e `box-sizing`.Permitindo-te gerir o layout com o teu CSS.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Nota:** Se tu seguires o guia [Herda o box-sizing](#herde-o-box-sizing) abaixo, podes optar por não incluir a propriedade `box-sizing` na tua redefinição de CSS.

<sup>[Regressar ao índice](#índice)</sup>


### Herda o `box-sizing`

Faz com que o `box-sizing` seja herdado do `html`:

```css
html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}
```

Assim fica mais fácil de alterar o `box-sizing` em plugins ou outros componentes que tenham um comportamento diferente.

<sup>[Regressar ao índice](#índice)</sup>


### Usa `unset` Em vez de Reconfigurar Todas as Propriedades

Quando estiveres a reconfigurar as propriedades de um elemento, não vai necessario  reconfigurar cada propriedade individualmente:

```css
button {
  background: none;
  border: none;
  color: inherit;
  font: inherit;
  outline: none;
  padding: 0;
}
```

Tu podes especificar todas as propriedades de um elemento usando o atalho `all`. Configurar o valor para `unset` muda a propriedade de um elemento para o seu valor inicial:

```css
button {
  all: unset;
}
```

**Nota:** o atalho `all` não tem supporte no IE11 e de  está a ser considerado para supporte no Edge. 

<sup>[Regressar ao índice](#table-of-contents)</sup>



### Usa `:not()` para Aplicar/Retirar Bordas

Ao invés de colocar a borda…

```css
/* adiciona a borda */
.nav li {
  border-right: 1px solid #666;
}
```

…para então retirar o último elemento…

```css
/* retira a borda */
.nav li:last-child {
  border-right: none;
}
```

…utiliza a _pseudo-class_ `:not()` para aplicar a borda apenas nos elementos corretos:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Claro,podes usar `.nav li + li` ou até `.nav li:first-child ~ li`, mas usando `:not()` a intenção fica mais clara e o seletor CSS passa a definir a borda de uma maneira que nós seres humanos entendemos mais fácilmente.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[Regressar ao índice](#índice)</sup>


### Define o `line-height` no `body`

Não precisas de adicionar o `line-height` para cada `<p>`, `<h*>`, _et al_. separadamente. Apenas adiciona ao `body`:

```css
body {
  line-height: 1.5;
}
```

Desta forma elementos de texto vão herdar o `line-height` do `body`.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[Regressar ao índice](#índice)</sup>


### Alinha Elementos Verticalmente

Que bruxaria é essa? Não é bruxaria!Tu realmente podes centralizar elementos verticalmente:

```css
html, body {
  height: 100%;
  margin: 0;
}

body {
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  display: -webkit-flex;
  display: flex;
}
```

Isto não resolveu o teu problema? O site CSS-Tricks tem [um guia completo](https://css-tricks.com/centering-css-complete-guide/) em como centralizar elementos com CSS.

 **Aviso:** Fica atento aos [bugs](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) quando estás a utilizar a flexbox no IE11.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[Regressar ao índice](#índice)</sup>


### Listas Separadas por Vírgula

Transforma listas normais em listas separadas por vírgula:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilize a _pseudo-class_ `:not()` para evitar que a vírgula seja adicionada depois do último item.

**Aviso:** Tendo em conta acessibilidade esta dica pode não ser ideal, especialmente para utilizadores de leitores de tela. Além disso, copiar e/ou colar não funciona em conteúdo criado com CSS. Procede com cautela.

<sup>[Regressar ao índice](#índice)</sup>


### Seleciona Itens Usando `nth-child` Negativo

Utilize `nth-child` negativo no CSS para selecionar itens de 1 a n.

```css
li {
  display: none;
}

/* mostrar itens de 1 a 3 */
li:nth-child(-n+3) {
  display: block;
}
```

Já que aprendeste um bocadinho sobre como usar a _pseudo-class_ [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), agora podes tentar:

```css
/* seleciona todos os itens, exceto o primeiro 3 e exibe-os */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Mais fácil que isto não há.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[Regressar ao índice](#índice)</sup>


### Ícones SVG

Não há motivo nenhum para não usares ícones em SVG:

```css
.logo {
  background: url("logo.svg");
}
```

A vantagem da SVG é que o ícone fica bom em qualquer resolução, além de ter suporte amplo em todos os browsers [desde o IE9](http://caniuse.com/#search=svg). Agora podes  desfazer-te dos teus arquivos .png, .jpg, ou ainda .gif-jif-qissomano.

**Aviso:** Se tens botões feitos apenas com ícones SVG, a dica a seguir ajudará-te a manter a acessibilidade:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[Regressar ao índice](#índice)</sup>


### Usa o Seletor "Lobotomized Owl"

O nome é super estranho (traduzido literalmente para:"coruja lobotomizada"), mas o seu uso do seletor universal (`*`) com o seletor adjacente (`+`) pode ser muito útil:

```css
* + * {
  margin-top: 1.5em;
}
```

Neste exemplo, todos os elementos acompanhados de outros elementos recebem `margin-top: 1.5em`.

Para mais exemplos utilizando o seletor "lobotomized owl", lê [o artigo escrito por Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) no site *A List Apart*.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Regressar ao índice](#índice)</sup>


### Sliders em CSS com `max-height`

Cria _sliders_ usando apenas CSS com `max-height` e `overflow-y: hidden`:

```css
.slider {
  max-height: 200px;
  overflow-y: hidden;
  width: 300px;
}

.slider:hover {
  max-height: 600px;
  overflow-y: scroll;
}
```

O elemento expandirá-se ao valor definido no `max-height` no _hover_ e terás um _slider_ devido ao uso do overflow.

<sup>[Regressar ao índice](#índice)</sup>


### Tabelas com Células de Tamanho Igual

Não há nada mais chato do que trabalhar com tabelas, mas agora podes usar `table-layout: fixed` para manter as células do mesmo tamanho:

```css
.calendar {
  table-layout: fixed;
}
```

Tabelas sem dores de cabeça.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Regressar ao índice](#índice)</sup>


### Esquece as "Margin Hacks", usa a Flexbox

Quando definires o espaçamento entre as colunas,deixa os seletores `nth-`, `first-`, e `last-child` de lado e usa a propriedade `space-between` do flexbox:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Assim as colunas ficam espaçadas uniformemente.

<sup>[Regressar ao índice](#índice)</sup>


### Usa Seletores de Atributo em Links Vazios

Mostra links para `<a>` tags vazias que possuem o atributo `href`:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Mão na roda.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[Regressar ao índice](#índice)</sup>


### Estiliza Links "Default"

Define estilos para links "default":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Desta forma, links que foram inseridos por CMS – que normalmente não possuem o atributo `class` – vão ser estilizados sem comprometer outros links.

<sup>[Regressar ao índice](#índice)</sup>


### Espaçamento Vertical Consistente

Usa o seletor universal dentro de um elemento para criar um espaçamento vertical consistente:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Com um espaçamento vertical consistente o seu conteúdo fica visualmente mais agradável de ler.

<sup>[Regressar ao índice](#índice)</sup>


### Div com Proporção de Tela Fixa

Para criar uma div com proporção de tela fixa, tudo que você precisa fazer é adicionar `padding` (`top` ou `bottom`) a div pai:

```css
.container {
  height: 0;
  padding-bottom: 20%;
  position: relative;
}

.container div {
  border: 2px dashed #ddd;
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
```

Se usares 20% no `padding` a altura da div vai ser igual a 20% de sua largura. Independente da largura do _viewport_, a div filho vai sempre manter a proporção de tela (100% / 20% = 5:1).

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[Regressar ao índice](#índice)</sup>


### Estiliza Imagens Quebradas

Faz com que imagens quebradas fiquem esteticamente mais agradáveis com um pouquinho de CSS:

```css
img {
  display: block;
  font-family: Helvetica, Arial, sans-serif;
  font-weight: 300;
  height: auto;
  line-height: 2;
  position: relative;
  text-align: center;
  width: 100%;
}
```

Agora adiciona regras com _pseudo-elements_ para mostrar uma mensagem e a URL da imagem quebrada:

```css
img::before {
  content: "Desculpe, a imagem abaixo não pode ser carregada :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Lê mais um pouco sobre como estilizar imagens quebradas no [artigo original](http://bitsofco.de/styling-broken-images/) por [Ire Aderinokun](https://github.com/ireade/).

<sup>[Regressar ao índice](#índice)</sup>


### Usa `rem` para Definir Tamanhos Globais; Usa `em` para Definir Tamanhos Locais

Depois de definires o tamanho de fonte base na raíz (`html { font-size: 100%; }`), define o tamanho de fonte para elementos de texto utilizando `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Então define o tamanho da fonte de módulos utilizando `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Assim fica mais fácil de estilizar e manter cada módulo, além de ser flexível.

<sup>[Regressar ao índice](#índice)</sup>


### Esconde Vídeos em Autoplay Que Não Estejam no Mudo

Ótima dica para uma _stylesheet_ personalizada. Evita sobrecarregar o utilizador com sons de vídeos em autoplay. Se o som não estiver no mudo, esconde o vídeo:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

E aqui está mais uma entre as muitas vantagens de usar a _pseudo-class_ [`:not()`](#use-not-to-applyunapply-borders-on-navigation).
 
<sup>[Regressar ao índice](#índice)</sup>


### Usa `:root` para uma Typografia Flexível

O tamanho de fonte de um site _responsive_ deverá ser ajustável de acordo com cada _viewport_.Podes calcular o tamanho da fonte baseando-te na largura e na altura do _viewport_ usando `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Desta forma,podes utilizar a unidade de medida `root em` baseada no valor calculado por `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[Regressar ao índice](#índice)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>
### Define `font-size` em Elementos de Formulário para uma Melhor Experiência Móvel

Para evitar zoom indesejado em elementos de formulários de navegadores móveis (iOS Safari, _et al_) quando um `<select>` é selecionado, adiciona `font-size` no seletor:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[Regressar ao índice](#índice)</sup>


## Suporte

Versões atuais do Chrome, Firefox, Safari, Opera, Edge, e IE11.