---
title: Document.close()
slug: Web/API/Document/close
tags:
  - API
  - Document
  - HTML DOM
  - Справка
  - метод
translation_of: Web/API/Document/close
---
{{APIRef("DOM")}}

Метод `document.close()` завершает запись в документ, открытый с помощью [document.open()](/en/DOM/document.open "en/DOM/document.open").

## Синтаксис

```
document.close();
```

## Пример

```
// открытие документа для записи в него.
// запись содержимого документа.
// закрытие документа.
document.open();
document.write("<p>The one and only content.</p>");
document.close();
```

## Спецификации

{{Specifications}}

## Браузерная поддержка

{{Compat}}
