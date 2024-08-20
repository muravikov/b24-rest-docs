# Установка специальной страницы для сайта

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- отсутствуют параметры или поля
- не указаны типы параметров
- не указана обязательность параметров
- отсутствуют примеры
- отсутствует ответ в случае успеха
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "landing.syspage.set" %}

**Scope**: [`landing`](../../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `landing.syspage.set` устанавливает для сайта специальную страницу. Если параметр **lid** не передан, то соответствующий тип страницы, не сама страница, будет удален. Метод не возвращает результата.

## Примеры

```js
BX24.callMethod(
    'landing.syspage.set',
    {
        id: 1390,// ИД сайта
        type: 'personal',// тип страницы
        lid: 8593// ИД страницы, которая в рамках сайта будет считаться данного типа
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
)
```

{% include [Сноска о примерах](../../../../_includes/examples.md) %}