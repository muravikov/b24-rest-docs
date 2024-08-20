# Получение информации о подключении к real-time серверам и организация мгновенных коммуникаций в рамках приложений

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- не указана обязательность параметров
- отсутствуют примеры

{% endnote %}

{% endif %}

{% note info "pull.application.config.get" %}

**Scope**: [`pull`](../../scopes/permissions.md) | **Кто может выполнять метод**: `администратор`

{% endnote %}

Метод `pull.application.config.get` служит для получения информации о подключении к real-time серверам и организации мгновенных коммуникаций в рамках приложений.

Благодаря подключению к RT-серверам вы сможете:
- создать действительно интерактивное приложение,
- менять состояния,
- мгновенно обновлять интерфейс без необходимости обновления страницы в режиме реального времени.

{% note warning %}

Метод вернет данные о подключении к каналам, созданных специально для вашего rest-приложения. В рамках этих каналов вы будете получать только ваши события.

{% endnote %}

#|
|| **Параметр** | **Описание** ||
|| **CACHE** | `Y / N` Возвращать кешированные данные или нет, по умолчанию Y. ||
|#

## Примеры

{% list tabs %}

- JavaScript

    ```js
    BX24.callMethod('pull.application.config.get', {
        'CACHE': 'Y',
    }, function(result){
        if(result.error())
        {
            console.error(result.error().ex);
        }
        else
        {
            console.log(result.data());
        }
    });
    ```

- PHP
  
    ```php
    $result = restCommand('pull.application.config.get', [
        'CACHE' => 'Y',
    ], $_REQUEST["auth"]);
    ```

{% endlist %}

{% include [Сноска о примерах](../../../_includes/examples.md) %}

## Ответ в случае успеха

> 200 OK

```json
{
    "result": {
        "server": {
            "version": 4,
            "server_enabled": true,
            "long_polling": "http://rt.bitrix24.com/sub/",
            "long_polling_secure": "https://rt.bitrix24.com/sub/",
            "websocket_enabled": true,
            "websocket": "ws://rt.bitrix24.com/sub/",
            "websocket_secure": "wss://rt.bitrix24.com/sub/",
            "publish_enabled": true,
            "publish": "http://rt.bitrix24.com/pubweb/",
            "publish_secure": "https://rt.bitrix24.com/pubweb/"
        },
        "channels": {
            "shared": {
                "id": "46a437d2336d4a88e4e9b3cd956ecf45.7910bb25e660bf211fdec15e33c5e25e4c3b644a",
                "start": "2017-06-28T12:04:00+02:00",
                "end": "2017-06-29T00:04:00+02:00",
                "type": "shared"
            },
            "private": {
                "id": "925153cd80b6b5a4dbf8659d5be21d1:abe9e6964532000ab8b7acf092ba627b.605ea91793ad24be3f9745d662713b23a5803a94",
                "public_id": "abe9e6964532000ab8b7acf092ba627b.057ac8625ae4ac0da4ed093a19950f9dab7e29d0",
                "start": "2017-06-28T09:57:48+02:00",
                "end": "2017-06-28T21:57:48+02:00",
                "type": "private"
            }
        }
    }
}
```

Объект **server** описывает конфигурацию сервера и пути для подключения к real-time каналу. Ключи объекта:

- **version** - версия установленного сервера,
- **server_enabled** - активирована или нет работа с сервером,
- **websocket_enabled** - доступна или нет работа с веб сокетами,
- **long_pooling** и **websocket** - пути подключения,
- **long_pooling_secure** и **websocket_secure** - пути подключения при использовании протокола https,
- **publish_enabled** - доступна или нет [возможность публикации сообщения](*ключ_возможность) со стороны клиента. 
- **publish** и **publish_secure** - пути для публикации сообщений со стороны клиента,
- **clientId** - уникальный идентификатор портала на облачном push-сервере. Возвращается в случае, если на портале используется облачный push-сервер.

Объект **channels** описывает данные для подключения пользователя к каналам. Ключи:

- **shared** - общий канал портала. На этом канале публикуются команды для всех пользователей портала (в том числе пользователей экстранет).
- **private** - приватный канал пользователя. На этом канале публикуются команды только для текущего пользователя.

Массив канала, содержит:

- **id** - идентификатор канала;
- **public_id** - публичный [идентификатор канала](*ключ_идентификатор);
- **start** - время создания канала (в формате ATOM);
- **end** - время окончания работы канала (в формате ATOM);
- **type** - тип канала.
  
## Ответ в случае ошибки

> 200 Error, 50x Error

```json
{
    "error": "SERVER_ERROR",
    "error_description": "Push & Pull server is not configured"
}
```

Ключи:

- **error** - код возникшей ошибки
- **error_description** - краткое описание возникшей ошибки
  
### Возможные коды ошибок

#|
|| **Код** | **Описание** ||
|| SERVER_ERROR | На портале не настроен модуль **Push & Pull** на работу с сервером очередей. ||
|| WRONG_AUTH_TYPE | Метод можно использовать только в рамках [OAuth 2.0](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=99&LESSON_ID=2486&LESSON_PATH=8771.5380.5379.2486) или через [веб-хуки](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=99&LESSON_ID=8581&LESSON_PATH=8771.8583.8581). ||
|#

## Смотрите также

- [Интерактивность в приложениях](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=99&CHAPTER_ID=012565)

[*ключ_возможность]: Доступно начиная с 4-й версии сервера очередей.

[*ключ_идентификатор]: Доступен только для 4-й версии сервера очередей и только для приватных каналов.