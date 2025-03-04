---
title: Element.animate()
slug: Web/API/Element/animate
tags:
  - API
  - Animation
  - Element
  - Experimental
  - Method
  - Reference
  - web animation
translation_of: Web/API/Element/animate
---
{{APIRef('Web Animations')}} {{SeeCompatTable}}

Метод **`animate()` **интерфейса\*\* \*\*{{domxref("Element")}} это быстрый способ создания {{domxref("Animation")}}, которая сразу применяется к элементу, а затем проигрывает эту анимацию. Метод возвращает созданный экземпляр класса {{domxref("Animation")}}.

> **Примечание:** Элементы могут иметь несколько, прикреплённых к ним, анимаций. Вы можете получить список анимаций, которые влияют на элемент, вызвав {{domxref("Element.getAnimations()")}}.

## Синтаксис

```
var animation = element.animate(keyframes, options);
```

### Параметры

- `keyframes`
  - : Массив объектов ключевых кадров, **либо** объект ключевого кадра, свойства которого являются массивами значений для итерации. Смотрите [Keyframe Formats](/ru/docs/Web/API/Web_Animations_API/Keyframe_Formats) для получения подробной информации.
- `options`

  - : Целое число**, представляющее продолжительность анимации** (в миллисекундах), **или** объект, содержащий одно или более временных свойств.

    - `id {{optional_inline}}`
      - : Свойство уникальное для `animate()`: [`DOMString`](https://developer.mozilla.org/en-US/docs/Web/API/DOMString "DOMString is a UTF-16 String. As JavaScript already uses such strings, DOMString is mapped directly to a String."), с помощью которого можно ссылаться на анимацию.

    {{Page("ru/docs/Web/API/EffectTiming", "Свойства")}}

#### Будущие возможности

Следующие возможности в настоящее **нигде не поддерживаются**, но будут добавлены в **ближайшем будущем** .

- `composite {{optional_inline}}`

  - : Определяет, как значения объединяются между этой анимацией и другими отдельными анимациями, которые не задают свою собственную конкретную составную операцию. По умолчанию `replace`.

    - `add` диктует аддитивный эффект, где каждая последующая итерация строится на последней. Пример с `transform`, `translateX(-200px)` не будут переопределять ранний вариант со значением `rotate(20deg)`, поэтому результат будет `translateX(-200px) rotate(20deg)`.
    - `accumulate` схоже, но немного умнее: `blur(2)` и `blur(5)` станет `blur(7)`, а не `blur(2) blur(5)`.
    - `replace` переписывает предыдущие значения на новые.

- `iterationComposite {{optional_inline}}`
  - : Определяет как значения строятся от итерации к итерации в этой анимации. Может быть установлено как `accumulate` или `replace` (смотрите выше). По умолчанию `replace`.
- `spacing {{optional_inline}}`

  - : Определяет как ключевые кадры, без временных смещений, должны распределяться по всей длительности анимации. По умолчанию `distribute`.

    - `distribute` позиционирует ключевые кадры так, чтобы разница между последующими смещениями ключевых кадров была равна, то есть без каких-либо смещений, ключевые кадры будут равномерно распределены по всему времени проигрыша анимации.
    - `paced` позиционирует ключевые кадры так, чтобы расстояние между последующими значениями заданного темпового свойства было равным, то есть, чем больше разница в значениях свойств ключевых кадров, тем на большем расстоянии они расположены друг от друга.

    ![](https://w3c.github.io/web-animations/img/spacing-distribute.svg) ![ ](https://w3c.github.io/web-animations/img/spacing-paced.svg)

### Возвращаемое значение

Возвращает {{domxref("Animation")}}.

## Пример

В демо [Down the Rabbit Hole (with the Web Animation API)](https://codepen.io/rachelnabors/pen/rxpmJL/?editors=0010), мы используем удобный метод `animate()`, чтобы сразу создать и проиграть анимацию на элементе `#tunnel`, чтобы заставить его крутиться в падении, бесконечно. Обратите внимание на массив объектов, в котором переданы ключевые кадры, а также блок временных параметров.

```js
document.getElementById("tunnel").animate([
  // keyframes
  { transform: 'translate3D(0, 0, 0)' },
  { transform: 'translate3D(0, -300px, 0)' }
], {
  // timing options
  duration: 1000,
  iterations: Infinity
})
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- [Web Animations API](/ru/docs/Web/API/Web_Animations_API)
- {{domxref("Element.getAnimations()")}}
- {{domxref("Animation")}}
