# Привязка данных к приложению.

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- нужны правки под стандарт написания
- не указана обязательность параметров
- отсутствуют примеры
- отсутствует ответ в случае успеха
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "app.option.set" %}

**Scope**: [`базовый`](../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `app.option.set` привязывает данные к приложению.

## Параметры

#|
|| **Метод** | **Описание** | **С версии** ||
|| **options**
[`array`](../../data-types.md) | Массив, где ключ - название сохраняемого свойства, а значение - значение свойства.
Если подать значение с новым ключом, то метод его запишет, если существующее, то обновит. | ||
|#

## Примеры

```js
CRest::call(
    'app.option.set',
    [
        "options"=>[
            'data' => 'value',
            'data2' => 'value2',
        ]
    ]
);
```

```js
CRest::call(
    'app.option.set',
    [
        "options"=>[
            'data' => 'NewValue',
        ]
    ]
),
```

{% include [Сноска о примерах](../../../_includes/examples.md) %}