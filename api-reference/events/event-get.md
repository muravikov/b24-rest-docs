# Получить список зарегистрированных обработчиков событий

> Название метода: **event.get**
>
> Кто может выполнять метод: любой пользователь

Метод `event.get` позволяет получить список зарегистрированных обработчиков событий.

Без параметров.

## Примеры кода

{% include [Сноска о примерах](../../_includes/examples.md) %}

{% list tabs %}

- cURL (Webhook)

    ```curl
    curl -X POST \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{}' \
    https://**put_your_bitrix24_address**/rest/**put_your_user_id_here**/**put_your_webbhook_here**/event.get
    ```

- cURL (OAuth)

    ```curl
    curl -X POST \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{}' \
    https://**put_your_bitrix24_address**/rest/event.get
    ```

- JS

    ```js
    BX24.callMethod(
        "event.get",
        {},
        function(result)
        {
            if(result.error())
                console.error(result.error());
            else
                console.log(result.data());
        }
    );
    ```

- PHP

    ```php
    require_once('crest.php');

    $result = CRest::call(
        'event.get',
        []
    );

    echo '<PRE>';
    print_r($result);
    echo '</PRE>';
    ```

{% endlist %}


## Обработка ответа

HTTP-статус: **200**

```json
{
    "result": [
        {
            "event": "ONCRMLEADADD",
            "handler": "https:\/\/www.my-domain.ru\/handler\/",
            "auth_type": "0",
            "offline": 0
        },
        {
            "event": "ONCRMLEADADD",
            "handler": "https:\/\/www.my-domain.ru\/handler\/",
            "auth_type": "15",
            "offline": 0
        }
    ],
    "time": {
        "start": 1721297941.536696,
        "finish": 1721297941.661148,
        "duration": 0.12445211410522461,
        "processing": 0.0029609203338623047,
        "date_start": "2024-07-18T12:19:01+02:00",
        "date_finish": "2024-07-18T12:19:01+02:00",
        "operating": 0
    }
}
```

### Возвращаемые данные

#|
|| **Название**
`тип` | **Описание** ||
|| **result**
[`object`](../data-types.md) | Корневой элемент ответа ||
|| **time**
[`time`](../data-types.md) | Информация о времени выполнения запроса ||
|#

## Обработка ошибок

{% include [системные ошибки](../../_includes/system-errors.md) %}

## Продолжите изучение

- [{#T}](./events.md)
- [{#T}](./event-bind.md)
- [{#T}](./event-unbind.md)
- [{#T}](./safe-event-handlers.md)
- [{#T}](./offline-events.md)
- [{#T}](./event-offline-list.md)
- [{#T}](./event-offline-get.md)
- [{#T}](./event-offline-clear.md)
- [{#T}](./event-offline-error.md)
- [{#T}](./on-offline-event.md)