# Удаление цены из коллекции цен товаров

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указана обязательность параметров
- отсутствует ответ в случае ошибки
- нет примеров на др. языках
  
{% endnote %}

{% endif %}

{% note info "catalog.price.delete" %}

**Scope**: [`catalog`](../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

## Описание

```http
catalog.price.delete(id)
```

Метод удаляет цену товара из коллекции цен товаров.
Если операция успешна, возвращается `true` в теле ответа.

## Параметры

#|
|| **Параметр** | **Описание** ||
|| **id** 
[`integer`](../../data-types.md)| Идентификатор цены товара. ||
|#

{% include [Сноска о параметрах](../../../_includes/required.md) %}

## Примеры

```javascript
BX24.callMethod(
    'catalog.price.delete',
    {
        id: 56
    },
    function(result)
    {
        if(result.error())
            console.error(result.error().ex);
        else
            console.log(result.data());
    }
);
```
{% include [Сноска о примерах](../../../_includes/examples.md) %}