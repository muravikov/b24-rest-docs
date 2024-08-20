# Добавление нового ресурса

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- отсутствуют примеры
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "calendar.resource.add" %}

**Scope**: [`calendar`](../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `calendar.resource.add` добавляет новый ресурс, принимает на вход массив с параметрами.

#|
|| **Параметр** / **Тип** | **Описание** ||
|| **name**^*^ 
[`string`](../data-types.md) | Наименование ресурса. ||
|#

{% include [Сноска о параметрах](../../_includes/required.md) %}

## Пример

```js
BX24.callMethod("calendar.resource.add",
    {
        name: 'My resource title'
    }
);
```

{% include [Сноска о примерах](../../_includes/examples.md) %}

## Ответ в случае успеха

Возвращает ID добавленного ресурса.