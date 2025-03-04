---
title: style
slug: Web/SVG/Attribute/style
tags:
  - Atributo SVG
  - SVG
translation_of: Web/SVG/Attribute/style
---
« [Página inicial de referência do atributo SVG](/en/SVG/Attribute)

Este atributo especifica informação de estilo para o elemento atual. O atributo "style" especifica informação de estilo para um único elemento. As linguagem da folha de estilos para as regras de estilos em linhas é dada pelo valor do atributo {{ SVGAttr("contentStyleType") }} no elemento the {{ SVGElement("SVG") }}.

## Contexto de uso

| Categorias          | Atributo de apresentação                                                    |
| ------------------- | --------------------------------------------------------------------------- |
| Valor               | \<style>                                                                    |
| Animável?           | Não                                                                         |
| Documento Normativo | [SVG 1.1 (2ª Edição)](http://www.w3.org/TR/SVG/styling.html#StyleAttribute) |

- \<style>
  - : A sintaxe do estilo depende de uma linguagem de folha de estilos. Por padrão, se {{ SVGAttr("contentStyleType") }} não for definido, a linguagem da folha de estilo utilizada será a CSS.

## Exemplo

O exemplo a seguir mostra a estilização de um retângulo com um atributo de estilo utilizando a linguagem de folha de estilos do CSS.

```html
<svg version="1.1" viewbox="0 0 1000 500" xmlns="http://www.w3.org/2000/svg">
  <rect height="300" width="600" x="200" y="100"
     style="fill: red; stroke: blue; stroke-width: 3"/>
</svg>
```

## Elementos

Os seguintes elementos podem utilizar o atributo `style`

- [Elementos "container"](/en/SVG/Element#Container) »
- [Elementos de filtro primitivo](/en/SVG/Element#FilterPrimitive) »
- [Elementos de gradiente](/en/SVG/Element#Gradient) »
- [Elementos gráficos](/en/SVG/Element#Graphics) »
- [Elementos estruturais](/en/SVG/Element#Structural) »
- [Elementos de texto](/en/SVG/Element#TextContent) »
- {{ SVGElement("clipPath") }}
- {{ SVGElement("filter") }}
- {{ SVGElement("font") }}
- {{ SVGElement("foreignObject") }}
- {{ SVGElement("glyphRef") }}
- {{ SVGElement("stop") }}
- {{ SVGElement("glyph") }}

## Veja também

- {{ SVGElement("style") }}
