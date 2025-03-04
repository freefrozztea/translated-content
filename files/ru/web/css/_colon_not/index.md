---
title: ':not()'
slug: Web/CSS/:not
translation_of: Web/CSS/:not
---
{{ CSSRef() }}

## Описание

**Отрицательный** [CSS псевдокласс](/ru/docs/CSS/Pseudo-classes), `:not(X)` - функция, принимающая простой селектор _X_ в качестве аргумента. Он находит элементы, не соответствующие селектору. _X_ не должен содержать других отрицательных селекторов.

> **Примечание:** **Замечания:**
>
> - С этого псевдокласса можно написать бесполезные селекторы. Например, `:not(*)` найдёт любой элемент, являющийся не любым, то есть правило не применится ни к одному элементу.
> - Возможно переписать другие правила. Например `foo:not(bar)` найдёт тот же элемент, что и простой `foo`. Тем не менее [специфичность](/ru/docs/CSS/Specificity) первого выше.
> - `:not(foo){}`найдёт что угодно, что не `foo`, **включая {{HTMLElement("html")}} и {{HTMLElement("body")}}.**
> - Это селектор применяется только к одному элементу. Вы не можете использовать его, чтобы исключить всех родителей. Например, `body :not(table) a` применится к ссылкам внутри таблицы, тогда как {{HTMLElement("tr")}} будет соответствовать `:not()` части селектора.

## Синтаксис

```
:not(selector) { style properties }
```

## Пример

```css
p:not(.classy) { color: red; }
body :not(p) { color: green; }
```

CSS выше и HTML ниже...

```html
<p>Некоторый текст.</p>
<p class="classy">Какой-то другой текст.</p>
<span>Ещё текст<span>
```

Выведет это:

{{ EmbedLiveSample('Examples', '', '', '', 'Web/CSS/:not') }}

## Спецификации

{{Specifications}}

## Поддержка браузерами

{{Compat}}
