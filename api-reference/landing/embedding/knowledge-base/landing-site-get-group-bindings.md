# Получение привязок к группам

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- отсутствуют примеры
- отсутствует ответ в случае успеха
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "landing.site.getGroupBindings" %}

**Scope**: [`landing`](../../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `landing.site.getGroupBindings` позволяет узнать, существует ли привязка к группе, или какие вообще есть привязки к группам. Вернутся только привязки, к Базам знаний которых текущий пользователь имеет доступ на чтение.

## Параметры

#|
|| **Параметр** | **Описание** | **С версии** ||
|| **groupId**
[`unknown`](../../../data-types.md) | Идентификатор группы, для которой надо вернуть привязку. Не обязательный, по умолчанию возвращаются все привязки к любым группам. | ||
|#

## Примеры

```js
BX24.callMethod(
    'landing.site.getGroupBindings',
    {
        groupId: 174
    },
    function(result)
    {
        if(result.error())
        {
            console.error(result.error());
        }
        else
        {
            console.info(result.data());
        }
    }
);
```

{% include [Сноска о примерах](../../../../_includes/examples.md) %}