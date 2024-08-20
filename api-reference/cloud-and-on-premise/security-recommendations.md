# Рекомендации по безопасности в приложениях на REST API

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- надо проверять на сервере авторизации полученные токены
- надо проверять application_token в событиях
- не надо использовать вебхуки для авторизации внутри фронтэнд
- не надо хранить лишнюю перс. информацию на своем сервере
- надо разделять права на доступ к файловым разделам, если на сервере несколько приложений. разделять базы данных приложений и пользователей с доступом к каждому приложению

{% endnote %}

{% endif %}
