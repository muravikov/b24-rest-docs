# Пользователи, прочитавшие Важное сообщение

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- не указана обязательность параметров
- отсутствует ответ в случае ошибки
- нет примеров на др. языках
- в описании нужна ссылка на пользовательскую документацию на статью про важные сообщения

{% endnote %}

{% endif %}

{% note info "log.blogpost.getusers.important" %}

{% include notitle [Скоуп log все](./_includes/scope-log-all.md) %}

{% endnote %}

Отдает массив идентификаторов пользователей, прочитавших указанное важное сообщение.

#|
|| **Параметр** | **Описание** ||
|| **POST_ID** | ID сообщения ленты новостей, являющегося важным сообщением. ||
|#

{% include [Сноска о параметрах](../../_includes/required.md) %}

## Пример

```js
BX24.callMethod(
    'log.blogpost.getusers.important',
    {
        POST_ID: 345
    },
    function(result)
    {
        console.log(result.data());
    }
);
```
{% include [Сноска о примерах](../../_includes/examples.md) %}

## Запрос:

```http
https://my.bitrix24.ru/rest/log.blogpost.getusers.important.json?POST_ID=345&auth=xxxxxxx
```

## Ответ:

> 200 OK

```json
{"result":["1","2","3"]}
```