# Удаление события

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- отсутствуют примеры
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "calendar.event.delete" %}

**Scope**: [`calendar`](../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `calendar.event.delete` удаляет событие.

#|
|| **Параметр** | **Описание** ||
|| **type**^*^ | Тип календаря: 
- user; 
- group. ||
|| **ownerId**^*^ | Идентификатор владельца календаря. ||
|| **id**^*^ | Идентификатор события. ||
|#

{% include [Сноска о параметрах](../../_includes/required.md) %}

## Пример

```js
BX24.callMethod("calendar.event.delete",
    {
        id: 698,
        type: 'user',
        ownerId: '2'
    }
);
```

{% include [Сноска о примерах](../../_includes/examples.md) %}

## Ответ в случае успеха

Возвращает **true** в случае успешного удаления.