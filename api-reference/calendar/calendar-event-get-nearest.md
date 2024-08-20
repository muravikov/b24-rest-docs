# Просмотр списка будущих событий для текущего пользователя

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- не указана обязательность параметров
- отсутствуют примеры
- отсутствует ответ в случае успеха
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}


{% note info "calendar.event.get.nearest" %}

**Scope**: [`calendar`](../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `calendar.event.get.nearest` возвращает список будущих событий для текущего пользователя.

#|
|| **Параметр** | **Описание** ||
|| **type** | Тип календаря: 
- user; 
- group. ||
|| **ownerId** | Идентификатор владельца календаря. ||
|| **days** | Число дней для выборки (по умолчанию - 60). ||
|| **forCurrentUser** | Вывод списка событий для текущего пользователя. ||
|| **maxEventsCount** | Максимальное число выводимых событий. ||
|| **detailUrl** | URL для календаря. ||
|#

## Пример

```js
BX24.callMethod("calendar.event.get.nearest",
    {
        type: 'user',
        ownerId: '2',
        days: 10,
        forCurrentUser: true,
        detailUrl: '/company/personal/user/#user_id#/calendar/'
    }
);
```

{% include [Сноска о примерах](../../_includes/examples.md) %}