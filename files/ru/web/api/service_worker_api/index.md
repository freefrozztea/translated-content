---
title: Service Worker API
slug: Web/API/Service_Worker_API
tags:
  - API
  - Landing
  - NeedsTranslation
  - Offline
  - Overview
  - Reference
  - Service Workers
  - TopicStub
  - Workers
translation_of: Web/API/Service_Worker_API
---
{{ServiceWorkerSidebar}}

Service worker фактически выполняет роль прокси-сервера, находящегося между веб-приложением и браузером, а также сетью (если доступна). Он позволяет (кроме прочего) описывать корректное поведение веб-приложения в режиме офлайн, перехватывать запросы сети и принимать соответствующие меры, основываясь на доступности сети, и обновлять данные, находящиеся на сервере при доступе к нему. Также они имеют доступ к push-уведомлениям и API для фоновой синхронизации.

## Концепция и использование Service Worker

Service worker — это событийно-управляемый [worker](/ru/docs/Web/API/Worker), регистрируемый на уровне источника и пути. Он представляет собой JavaScript-файл, который может контролировать веб-страницу/сайт, с которым он ассоциируется, перехватывать и модифицировать запросы навигации и ресурсов, очень гибко кешировать ресурсы, для того чтобы предоставить вам полный контроль над тем, как приложение ведёт себя в определённых ситуациях (например, когда сеть не доступна).

Service worker запускается в контексте воркеров, поэтому он не имеет доступа к DOM и работает в потоке отдельном от основного потока JavaScript, управляющего вашим приложением, а следовательно — не блокирует его. Он призван быть полностью асинхронным; как следствие, синхронные API, такие как [XHR](/ru/docs/Web/API/XMLHttpRequest) и [localStorage](/ru/docs/Web/Guide/API/DOM/Storage), в Service Worker'е использовать нельзя.

Из соображений безопасности service worker'ы работают только по HTTPS (либо, в целях разработки, на `localhost`). Давать сторонним людям возможность изменять сетевые запросы крайне опасно. Кроме того, Service Worker API недоступен в [режиме приватного просмотра](https://support.mozilla.org/ru/kb/privatnyj-prosmotr-prosmotr-veb-stranic-bez-sohran) браузера Firefox.

> **Примечание:** Service Worker'ы выигрывают у предыдущих решений, таких как [AppCache,](http://alistapart.com/article/application-cache-is-a-douchebag) потому что не делают предположений о том, что вы пытаетесь сделать, и не ломаются, в случаях если их предположения не оказываются верными; вы имеете полный контроль над всем.

> **Примечание:** Service worker'ы широко используют промисы ([Promises](/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise)). В общем случае они будут ждать ответа, после которого вернутся с успешным или неудачным завершением. Архитектура на промисах для этого подходит идеально.

### Регистрация

Service worker сначала регистрируется с помощью метода {{domxref("ServiceWorkerContainer.register()")}}. В случае успешной регистрации, service worker будет загружен клиентом и попытается установиться/активироваться (см. ниже) для всех URL, доступных пользователю, или только для указанного вами подмножества.

### Загрузка, установка и активация

Service Worker будет следовать следующему жизненному циклу:

1.  Загрузка
2.  Установка
3.  Активация

Когда пользователь впервые запросит доступ к сайту/странице, контролируемой Service Worker'ом, тот моментально будет загружен .

После этого он будет загружаться каждые 24 часа или около того. Он _может_ загружаться и чаще, но он **должен** загружаться как минимум каждые 24 часа, чтобы предотвратить использование старой версии кода клиентом.

Установка производится в случае если загружаемый файл признается новым — либо отличным от уже установленного service worker (определяется через побайтовое сравнение), либо первым устанавливаемым service воркером для этой страницы/сайта.

Если это первый раз, когда service worker оказался доступен, будет проведена установка, а после успешного её завершения — активация.

Если service worker уже существует, новая версия устанавливается в фоновом режиме, но не активируется — worker переходит в состояние _в ожидании_. Новая версия активируется только тогда, когда больше не останется загруженных страниц, использующих старый service worker. Как только это случится, новый service worker активируется (станет _активным воркером_). Активация может произойти раньше при использовании {{domxref ("ServiceWorkerGlobalScope.skipWaiting()")}}, а существующие страницы могут быть переведены под контроль активного воркера с помощью {{domxref ("Clients.claim()")}}.

Вы можете подписаться на {{domxref("InstallEvent")}}; для того чтобы подготовить ваш service worker к использованию, к примеру, чтобы создать кеш при помощи встроенного API хранилища и разместить внутри него данные, которые вам необходимы в вашем приложении для работы офлайн.

Есть также событие `activate`. Момент, когда это событие наступает, является удачным для очистки старого кеша и всего, что ассоциировалось с предыдущей версией вашего service worker'а.

Service worker может отвечать на запросы, используя событие {{domxref("FetchEvent")}}. Вы можете изменять ответ на эти запросы на своё усмотрение используя метод {{domxref("FetchEvent.respondWith") }}.

> **Примечание:** Так как выполнение `oninstall`/`onactivate` может занять время, спецификация service worker предоставляет метод `waitUntil`, который возвращает промис, когда вызывается `oninstall` или `onactivate`. Функциональные события не отправляются service worker, пока промис не завершится успешно.

Для полного руководства по созданию рабочего примера читайте [Использование Service Worker](/ru/docs/Web/API/ServiceWorker_API/Using_Service_Workers).

## Другие варианты использования

Service worker'ы также предназначены для таких вещей, как:

- Фоновая синхронизация данных
- Ответ на запросы от других источников
- Получение централизованного обновления для данных использующих тяжёлые вычисления, таких как геолокация или гироскоп, для того чтобы несколько страниц могли использовать одни и те же данные
- Компиляция и управление зависимостями на клиентской стороне для CoffeeScript, less, CJS/AMD модулей и т.д. для целей разработки
- Подписка на фоновые сервисы
- Кастомная шаблонизация, основанная на определённых паттернах URL
- Улучшение производительности, с помощью предварительной загрузки ресурсов, которые понадобятся пользователю в ближайшем будущем, например несколько последующих картинок в фотоальбоме.

В будущем service worker'ы будут способны на многие другие полезные вещи для веб-платформ, приближая их к нативным приложениям. Примечательно, что другие спецификации могут и будут использовать контекст service worker, к примеру для:

- [Фоновой синхронизации](https://github.com/slightlyoff/BackgroundSync): запускать service worker даже когда ни одного пользователя нет на сайте, чтобы обновить кеш.
- [Реакции на пуш-сообщения](/ru/docs/Web/API/Push_API): запускать service worker для отправки сообщений пользователям, чтобы оповестить их о новом доступном контенте.
- Реакции на определённое время и дату
- Введение гео-ограничений

## Интерфейс

- {{domxref("Cache") }}
  - : Представляет хранилище для объектов {{domxref("Request")}} / {{domxref("Response")}}, которые кешируются, как часть жизненного цикла {{domxref("ServiceWorker")}}.
- {{domxref("CacheStorage") }}
  - : Представляет хранилище для объектов {{domxref("Cache")}}. Он создаёт главную директорию для всех именованных кешей, к которым {{domxref("ServiceWorker")}} имеет доступ, и поддерживает отображение строковых имён соответствующего объекта {{domxref("Cache")}}.
- {{domxref("Client") }}
  - : Представляет область видимости клиента service worker. Это либо документ в контексте браузера, либо {{domxref("SharedWorker")}}, который контролируется активным воркером.
- {{domxref("Clients") }}
  - : Представляет контейнер для списка объектов {{domxref("Client")}}; основной способ получить доступ к клиентам активного service worker'а текущего источника.
- {{domxref("ExtendableEvent") }}
  - : Расширяет жизненный цикл событий `install` и `activate`, отправляемых {{domxref("ServiceWorkerGlobalScope")}} как часть жизненного цикла service worker'а. Это гарантирует, что любое функциональное событие (как {{domxref("FetchEvent")}}) не отправится в {{domxref("ServiceWorker")}}, пока он не обновит шаблон данных, удалив устаревшие данные кеша.
- {{domxref("ExtendableMessageEvent") }}
  - : Объект событий {{event("message_(ServiceWorker)","message")}} запускается в service worker (когда канал сообщений в {{domxref("ServiceWorkerGlobalScope")}} получил новое сообщение из другого контекста) — расширяет жизненный цикл таких событий.
- {{domxref("FetchEvent") }}
  - : Параметр, передающийся в обработчик {{domxref("ServiceWorkerGlobalScope.onfetch")}}, `FetchEvent` представляет собой событие получения, которое отправляется в {{domxref("ServiceWorkerGlobalScope")}} {{domxref("ServiceWorker")}}. Он содержит информацию о запросе и результирующем ответе и обеспечивает {{domxref("FetchEvent.respondWith", "FetchEvent.respondWith()")}} метод, который позволяет отправить произвольный ответ обратно контролируемой странице.
- {{domxref("InstallEvent") }}
  - : Параметр, передающийся в {{domxref("ServiceWorkerGlobalScope.oninstall", "oninstall")}} обработчик, `InstallEvent` представляет собой событие установки, которое отправляется {{domxref("ServiceWorkerGlobalScope")}} {{domxref("ServiceWorker")}}. Как наследник {{domxref("ExtendableEvent")}}, он гарантирует, что функциональные события, такие как {{domxref("FetchEvent")}}, не будут отправлены во время установки.
- {{domxref("Navigator.serviceWorker") }}
  - : Возвращает объект {{domxref("ServiceWorkerContainer")}}, который обеспечивает доступ к регистрации, удалению, обновлению и коммуникации с объектами {{domxref("ServiceWorker")}}[ассоциируемого документа](https://html.spec.whatwg.org/multipage/browsers.html#concept-document-window).
- {{domxref("NotificationEvent") }}
  - : Параметр, передаваемый в обработчик {{domxref("ServiceWorkerGlobalScope.onnotificationclick", "onnotificationclick")}}, интерфейс `NotificationEvent` представляет событие уведомления на клик, которое отправляется в {{domxref("ServiceWorkerGlobalScope")}} service worker'а.
- {{domxref("ServiceWorker") }}
  - : Представляет service worker. Несколько контекстов браузера (страницы, worker'ы, и т.д.) могут быть ассоциированы с одним объектом `ServiceWorker`.
- {{domxref("ServiceWorkerContainer") }}
  - : Предоставляет объект, описывающий service worker как общий блок в экосистеме сети, включая возможность регистрировать, отключать и обновлять service worker'ы, и предоставляет доступ к состоянию текущего и других зарегистрированных service воркеров.
- {{domxref("ServiceWorkerGlobalScope") }}
  - : Представляет глобальный контекст исполнения service worker'а.
- {{domxref("ServiceWorkerMessageEvent")}}
  - : Содержит информацию о событии, отправленном целевому {{domxref("ServiceWorkerContainer")}}.
- {{domxref("ServiceWorkerRegistration") }}
  - : Представляет регистрацию service worker'а.
- {{domxref("SyncEvent")}} {{non-standard_inline}}
  - : SyncEvent представляет синхронное действие, которое отправляется {{domxref("ServiceWorkerGlobalScope")}} ServiceWorker.
- {{domxref("SyncManager")}} {{non-standard_inline}}
  - : Обеспечивает интерфейс регистрации и перечисления синхронных регистрации.
- {{domxref("WindowClient") }}
  - : Представляет область видимости клиентского service worker'а, представленного в виде документа в контакте браузера, контролируемого активным воркером. Это особый тип объекта {{domxref("Client")}} с некоторыми дополнительными методами и свойствами.

## Спецификации (характеристики)

| Спецификации                             | Статус                               | Комментарий              |
| ---------------------------------------- | ------------------------------------ | ------------------------ |
| {{SpecName('Service Workers')}} | {{Spec2('Service Workers')}} | Изначальное определение. |

## Совместимость

{{Compat}}

## Смотрите также:

- Кулинарная книга [ServiceWorker](https://serviceworke.rs)
- Использование[ Service Workers](/ru/docs/Web/API/ServiceWorker_API/Using_Service_Workers)
- Основные примеры кода [Service workers](https://github.com/mdn/sw-test)
- Готов ли [ServiceWorker?](https://jakearchibald.github.io/isserviceworkerready/)
- Перспектива
- [Using web workers](/ru/docs/Web/Guide/Performance/Using_web_workers)
