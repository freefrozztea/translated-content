---
title: Идемпотентный метод
slug: Glossary/Idempotent
tags:
  - Glossary
  - HTTP
translation_of: Glossary/Idempotent
original_slug: Глоссарий/Idempotent
---
Метод HTTP является идемпотентным, если повторный идентичный запрос, сделанный один или несколько раз подряд, имеет один и тот же эффект, не изменяющий состояние сервера. Другими словами, идемпотентный метод не должен иметь никаких побочных эффектов (side-effects), кроме сбора статистики или подобных операций. Корректно реализованные методы {{HTTPMethod("GET")}}, {{HTTPMethod("HEAD")}}, {{HTTPMethod("PUT")}} и {{HTTPMethod("DELETE")}} **идемпотентны**, но не метод {{HTTPMethod("POST")}}. Также все {{glossary("safe", "безопасные")}} методы являются идемпотентными.

Для идемпотентности нужно рассматривать только изменение фактического внутреннего состояния сервера, а возвращаемые запросами коды статуса могут отличаться: первый вызов {{HTTPMethod("DELETE")}} вернёт код {{HTTPStatus("200")}}, в то время как последующие вызовы вернут код {{HTTPStatus("404")}}. Из идемпотентности {{HTTPMethod("DELETE")}} неявно следует, что разработчики не должны использовать метод {{HTTPMethod("DELETE")}} при реализации RESTful API с функциональностью _**удалить последнюю запись**_.

Обратите внимание, что идемпотентность метода не гарантируется сервером, и некоторые приложения могут нарушать ограничение идемпотентности.

`GET /pageX HTTP/1.1` идемпотентен. Вызвавший несколько раз подряд этот запрос, клиент получит тот же результат:

```
GET /pageX HTTP/1.1
GET /pageX HTTP/1.1
GET /pageX HTTP/1.1
GET /pageX HTTP/1.1
```

`POST /add_row HTTP/1.1` не идемпотентен; если его вызвать несколько раз, то он добавит несколько строк:

```
POST /add_row HTTP/1.1
POST /add_row HTTP/1.1   -> Adds a 2nd row
POST /add_row HTTP/1.1   -> Adds a 3rd row
```

`DELETE /idX/delete HTTP/1.1` идемпотентен, даже если возвращаемый код отличается:

```
DELETE /idX/delete HTTP/1.1   -> Returns 200 if idX exists
DELETE /idX/delete HTTP/1.1   -> Returns 404 as it just got deleted
DELETE /idX/delete HTTP/1.1   -> Returns 404
```

## Материалы для изучения

### Общие

- Определение [идемпотентности](https://tools.ietf.org/html/rfc7231#section-4.2.2) в спецификации HTTP.

### Технические

- Описание общих идемпотентных методов: {{HTTPMethod("GET")}}, {{HTTPMethod("HEAD")}}, {{HTTPMethod("PUT")}}, {{HTTPMethod("DELETE")}}, {{HTTPMethod("OPTIONS")}}
- Описание общих неидемпотентных методов: {{HTTPMethod("POST")}}
