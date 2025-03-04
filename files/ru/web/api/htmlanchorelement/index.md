---
title: HTMLAnchorElement
slug: Web/API/HTMLAnchorElement
translation_of: Web/API/HTMLAnchorElement
---
{{APIRef("HTML DOM")}}

Интерфейс **`HTMLAnchorElement`** представляет элементы гиперссылки и предоставляет специальные свойства и методы (помимо обычного объектного интерфейса {{domxref("HTMLElement")}}, который они наследуют) для управления макетом и представлением таких элементов.
Этот интерфейс соответствует элементу \<a>; не путать с < link>, который представлен HTMLLinkElement.

{{InheritanceDiagram(600, 120)}}

## Свойства

_Наследует свойства от его родителя,\_\_{{domxref("HTMLElement")}}, и реализует те из {{domxref("URLUtils")}}._

- {{domxref("HTMLAnchorElement.accessKey")}}
  - : Это {{domxref("DOMString")}} отображает собой единичный символ, который переключает фокус ввода на гиперссылку.
- {{domxref("HTMLAnchorElement.charset")}} {{obsolete_inline}}
  - : Это {{domxref("DOMString")}} отображает кодировку символов связанного ресурса.
- {{domxref("HTMLAnchorElement.coords")}} {{obsolete_inline}}
  - : Это {{domxref("DOMString")}} отображает список координат разделённый запятыми.
- {{domxref("HTMLAnchorElement.download")}} {{experimental_inline}}
  - : Это {{domxref("DOMString")}} показывать что связанный ресурс предназначен для загрузки, а не для отображения в браузере. Значение представляет предполагаемое имя файла. Если имя не является допустимым именем файла нижележащей ОС, браузер будет адаптировать его. Значение это URL по схеме `http:`, `file:`, `data:` или даже `blob:` (созданный с помощью {{domxref("URL.createObjectURL")}}).
- {{domxref("URLUtils.hash")}}
  - : Это {{domxref("DOMString")}} отображает фрагмент идентификатора, включая ведущий hash mark ('`#`'), если, указан в URL.
- {{domxref("URLUtils.host")}}
  - : Это {{domxref("DOMString")}} отображает имя хоста порт (если это не порт по умолчанию) в указанном URL.
- {{domxref("URLUtils.hostname")}}
  - : Это {{domxref("DOMString")}} отображает имя хоста в указанном URL.
- {{domxref("URLUtils.href")}}
  - : Это {{domxref("DOMString")}} что отображает {{htmlattrxref("href", "a")}} HTML атрибут, содержащий действительный URL связанного ресурса.
- {{domxref("HTMLAnchorElement.hreflang")}}
  - : Это {{domxref("DOMString")}} что отображает HTML атрибут {{htmlattrxref("hreflang", "a")}}, показывающий язык связанного ресурса.
- {{domxref("HTMLAnchorElement.media")}}
  - : Это {{domxref("DOMString")}} что отображает {{htmlattrxref("media", "a")}} HTML атрибут, с указанием предполагаемого media для связанного ресурса.
- {{domxref("HTMLAnchorElement.name")}} {{obsolete_inline}}
  - : Это {{domxref("DOMString")}} отображает имя якоря.
- {{domxref("URLUtils.password")}}
  - : Это {{domxref("DOMString")}} содержащий пароль, указанный перед именем домена.
- {{domxref("URLUtils.origin")}} {{readonlyInline}}
  - : Возвращает {{domxref("DOMString")}} содержащий источник, то есть его схему, его домен и его порт.
- {{domxref("URLUtils.pathname")}}
  - : Это {{domxref("DOMString")}} отображающий составную часть пути имени, любого, ссылающегося URL.
- {{domxref("URLUtils.port")}}
  - : Это {{domxref("DOMString")}} отображающий составную часть порта, любого, ссылающегося URL.
- {{domxref("URLUtils.protocol")}}
  - : Is a {{domxref("DOMString")}} отображающий составную часть протокола, включая двоеточия ('`:`'), ссылающегося URL.
- {{domxref("HTMLAnchorElement.referrer")}} {{experimental_inline}}
  - : Это {{domxref("DOMString")}} что отображает {{htmlattrxref("referrer", "a")}} HTML атрибут, показывающий какой referrer используется, когда выбрано изображение.
- {{domxref("HTMLAnchorElement.rel")}}
  - : Это {{domxref("DOMString")}} что отображает {{htmlattrxref("rel", "a")}} HTML атрибут, уточняя взаимоотношения целевого объекта к связанному объекту.
- {{domxref("HTMLAnchorElement.relList")}} {{readonlyInline}}
  - : Возвращает {{domxref("DOMTokenList")}} который отображает {{htmlattrxref("rel", "a")}} HTML атрибут, как список токенов.
- {{domxref("HTMLAnchorElement.rev")}} {{obsolete_inline}}
  - : Это {{domxref("DOMString")}} отображающий как {{htmlattrxref("rev", "a")}} HTML атрибут, уточняя взаимоотношения связанного объекта к целевому объекту
- {{domxref("URLUtils.search")}}
  - : Это {{domxref("DOMString")}} отображающий искомый элемент, включая ведущий знак вопроса ('`?`'), если таковой имеется, в ссылающемся URL.
- {{domxref("HTMLAnchorElement.shape")}} {{obsolete_inline}}
  - : Это {{domxref("DOMString")}} отображающий вид активной области.
- {{domxref("HTMLAnchorElement.tabindex")}}
  - : Это `long` содержащий положение элемента в порядке навигационного переключения для текущего документа.
- {{domxref("HTMLAnchorElement.target")}}
  - : Это {{domxref("DOMString")}} который отображает {{htmlattrxref("target", "a")}} HTML атрибут, указывая где отображается связанный ресурс.
- {{domxref("HTMLAnchorElement.text")}}
  - : Это {{domxref("DOMString")}} является синонимом {{domxref("Node.textContent")}} свойства.
- {{domxref("HTMLAnchorElement.type")}}
  - : Это {{domxref("DOMString")}} которое отображает {{htmlattrxref("type", "a")}} HTML атрибут, показывающий MIME тип связанного ресурса.
- {{domxref("URLUtils.username")}}
  - : Это {{domxref("DOMString")}} содержащий имя пользователя определённое перед именем домена.

## Методы

_Наследует методы от его родителя, {{domxref("HTMLElement")}},_ _и реализует те из {{domxref("URLUtils")}}\_\_._

- {{domxref("HTMLElement.blur()")}}
  - : Удаляет фокус клавиатуры из текущего элемента.
- {{domxref("HTMLElement.focus()")}}
  - : Даёт фокус клавиатуры на текущий элемент.
- {{domxref("URLUtils.toString()")}}
  - : Возвращает {{domxref("DOMString")}} содержащий весь URl. Это синоним {{domxref("URLUtils.href")}}, хотя он не может быть использован для изменения значения.

`blur()` и `focus()` методы наследуемые от {{domxref("HTMLElement")}} для HTML5, но они были определены в `HTMLAnchorElement` в DOM Level 2 HTML и более ранней спецификации.

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- HTML-элемент реализующий это интерфейс: {{HTMLElement("a")}}
