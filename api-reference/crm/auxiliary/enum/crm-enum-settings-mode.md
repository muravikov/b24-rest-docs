# Возвращение описания режимов работы CRM

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

> Название метода: **crm.enum.settings.mode**
>
> Scope: [`crm`](../../../scopes/permissions.md)
>
> Кто может выполнять метод: `любой пользователь`

Возвращает описание режимов работы CRM.

## Параметры метода

Метод вызывается без параметров.

## Примеры кода

{% include [Сноска о примерах](../../../../_includes/examples.md) %}

{% list tabs %}

- cURL (Webhook)

    сюда мы сами вставим нужный код, перегенерированный из вашего примера на JS

- cURL (OAuth)

    сюда мы сами вставим нужный код, перегенерированный из вашего примера на JS

- JS

    ```js
    BX24.callMethod("crm.enum.settings.mode", result => {
        if (result.error())
            console.error(result.error());
        else
            console.dir(result.data());
    });
    ```

- PHP

    сюда мы сами вставим нужный код, перегенерированный из вашего примера на JS

{% endlist %}

{% note tip "Частые кейсы и сценарии" %}

Контент этого блока мы сами заполним потом. Или уберем блок за ненадобностью

{% endnote %}

## Обработка ответа

HTTP-статус: **200**

```json
{
     "result": [
        {
            "ID": 1,
            "NAME": "Классическая CRM",
        },
        {
            "ID": 2,
            "NAME": "Простая CRM",
        }
    ],
    "time": {
        "start": 1715091541.642592,
        "finish": 1715091541.730599,
        "duration": 0.08800697326660156,
        "date_start": "2024-05-03T17:19:01+03:00",
        "date_finish": "2024-05-03T17:19:01+03:00",
        "operating": 0
    }
}
```

### Возвращаемые данные

#|
|| **Название**
`тип` | **Описание** ||
|| **result**
[`object`](../../../data-types.md) | Возвращает массив доступных режимов для работы CRM: **1: классическая CRM** и **2: простая CRM**   ||
|| **time**
[`time`](../../data-types.md) | Информация о времени выполнения запроса ||
|#

## Обработка ошибок

{% include notitle [обработка ошибок](../../../../_includes/error-info.md) %}

### Возможные коды ошибок

{% include [системные ошибки](../../../../_includes/system-errors.md) %}

## Продолжите изучение

Этот блок мы сами потом заполним, но если есть рекомендации, какие методы или страницы документации тут стоит упомянять - будем благодарны