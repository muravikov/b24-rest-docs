# Показать информацию о приложении app.info

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- отсутствуют параметры или поля
- отсутствуют примеры
- отсутствует ответ в случае успеха

{% endnote %}

{% endif %}

> Scope: [`базовый`](../../scopes/permissions.md)
>
> Кто может выполнять метод: любой пользователь

Метод `app.info` показывает информацию о приложении. Поддерживает безопасный вызов.

## Примеры

Запрос
```http
http://my.bitrix24.ru/rest/app.info?auth=d161f25928c3184678924ec127edd29a
```

{% include [Сноска о примерах](../../../_includes/examples.md) %}

## Ответ в случае успеха

> 200 OK
```json
{
    "result": {
        "ID":"7",
        "CODE":"local.56017020f07e17.98523769",
        "VERSION":1,
        "STATUS":"L",
        "INSTALLED":true,
        "PAYMENT_EXPIRED":"N",
        "DAYS":null,
        "LICENSE":"ru_project"
    }
}
```

### Возвращаемые данные
#|
|| **Поле** | **Описание** ||
|| **ID** | локальный идентификатор приложения на портале ||
|| **CODE** | код приложения ||
|| **VERSION** | установленная версия приложения ||
|| **STATUS** | статус приложения. Возможные значения:
- **F** (Free) - бесплатное;
- **D** (Demo) - демо-версия;
- **T** (Trial) - триальная версия (ограниченная по времени);
- **P** (Paid) - оплаченное приложение;
- **L** (Local) - локальное приложение;
- **S** (Subscription) - подписное приложение. ||
|| **INSTALLED** | [true\|false] Статус установленности приложения. Если приложение не установлено, оно доступно только администраторам портала и должно сигнализировать об окончании установки при помощи вызова [BX24.installFinish()](700086) ||
|| **PAYMENT_EXPIRED** | [Y\|N] флаг, показывающий, истек ли оплаченный период или период триального использования. ||
|| **DAYS** | Количество дней, оставшееся до конца оплаченного периода или периода триального использования. ||
|| **LICENSE** | Обозначение тарифа с указанием региона в виде префикса.Состоит из базового языка портала и идентификатора тарифного плана. В случае с тарифами, состав которых менялся при сохранении публичного наименования (как CRM+, Команда и Компания), понять, какой именно тариф действует по этому полю нельзя. Примеры вариантов значений:
- **ru_project** - тариф Проект
- **ru_basic** - тариф Базовый
- **ru_std** - тариф Стандартный
- **ru_pro100** - тариф Профессиональный
- **ru_ent250** - Энтерпрайз 250
- **ru_ent500** - Энтерпрайз 500
- **ru_ent1000** - Энтерпрайз 1000
- **ru_ent2000** - Энтерпрайз 2000
- **ru_ent10000** - Энтерпрайз 10000 ||
|#

По истечении оплаченного периода приложение продолжит работать в течение периода, отводимого на возможные задержки поступления оплаты (grace period), по окончании которого будет автоматически переключено на демо-режим или заблокировано. При этом значение флага PAYMENT_EXPIRED будет равен Y, а поле DAYS будет содержать отрицательное число.