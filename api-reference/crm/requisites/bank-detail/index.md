# О банковских реквизитах

> Scope: [`crm`](../../../scopes/permissions.md)
>
> Кто может выполнять методы: любой пользователь

Банковские реквизиты — это строгая последовательность цифр, необходимых для осуществления операций с расчетным счетом. По реквизитам можно отправить безналичный платеж или внести деньги на счет через кассу.

К обязательным банковским реквизитам относятся:
- номер расчетного счета
- номер корреспондентского счета
- банковский идентификационный код (БИК) и полное наименование банка

В CRM банковские реквизиты связываются с объектом универсальных реквизитов. Несколько банковских реквизитов могут быть привязаны к одному реквизиту.

# Поля банковских реквизитов

#|
|| **Название**
`тип` | **Описание** | **Чтение** | **Запись** | **Обязательное** | **Неизменяемое** ||
|| **ID**
[`integer`](../../../data-types.md) | Идентификатор банковского реквизита. Создается автоматически и уникален в рамках портала | Да | Нет | Нет | Нет ||
|| **ENTITY_TYPE_ID**
[`integer`](../../../data-types.md) | Идентификатор типа родительского объекта. Может быть только `Реквизит` (значение `8`).

Идентификаторы типов объектов возвращает метод [crm.enum.ownertype](../../auxiliary/enum/crm-enum-owner-type.md) | Да | Нет | Нет | Нет ||
|| **ENTITY_ID**
[`integer`](../../../data-types.md) | Идентификатор родительского объекта | Да | Да | Да | Да ||
|| **COUNTRY_ID**
[`integer`](../../../data-types.md) | Идентификатор страны, которой соответствует набор полей банковского реквизита (смотрите метод [crm.requisite.preset.countries](../presets/crm-requisite-preset-countries.md) для получения доступных значений).

Код страны банковского реквизита совпадает с кодом страны в привязанном шаблоне реквизитов, идентификатор которого указан в поле `ENTITY_ID` 
| Да | Да | Нет | Нет ||
|| **DATE_CREATE**
[`datetime`](../../../data-types.md) | Дата создания | Да | Нет | Нет | Нет ||
|| **DATE_MODIFY**
[`datetime`](../../../data-types.md) | Дата изменения | Да | Нет | Нет | Нет ||
|| **CREATED_BY_ID**
[`user`](../../../data-types.md) | Идентификатор пользователя, создавшего реквизит | Да | Нет | Нет | Нет ||
|| **MODIFY_BY_ID**
[`user`](../../../data-types.md) | Идентификатор пользователя, изменившего реквизит | Да | Нет | Нет | Нет ||
|| **NAME^*^**
[`string`](../../../data-types.md) | Название банковского реквизита | Да | Да | Нет | Нет ||
|| **CODE**
[`string`](../../../data-types.md) | Символьный код реквизита | Да | Да | Нет | Нет ||
|| **XML_ID**
[`string`](../../../data-types.md) | Внешний ключ. Используется для операций обмена. Идентификатор объекта внешней информационной базы. 

Назначение поля может меняться конечным разработчиком. Каждое приложение обеспечивает уникальность значений в этом поле. 

Рекомендуется использовать уникальный префикс для избежания коллизий с другими приложениями | Да | Да | Нет | Нет ||
|| **ACTIVE**
[`char`](../../../data-types.md) | Признак активности. Используются значения `Y` или `N`. 

Сейчас поле фактически ни на что не влияет | Да | Да | Нет | Нет ||
|| **SORT**
[`integer`](../../../data-types.md) | Сортировка | Да | Да | Нет | Нет ||
|| **RQ_BANK_NAME**
[`string`](../../../data-types.md) | Наименование банка | Да | Да | Нет | Нет ||
|| **RQ_BANK_ADDR**
[`string`](../../../data-types.md) | Адрес банка | Да | Да | Нет | Нет ||
|| **RQ_BANK_CODE**
[`string`](../../../data-types.md) | Código do banco (для страны BR) | Да | Да | Нет | Нет ||
|| **RQ_BANK_ROUTE_NUM**
[`string`](../../../data-types.md) | Bank Routing Number | Да | Да | Нет | Нет ||
|| **RQ_BIK**
[`string`](../../../data-types.md) | БИК | Да | Да | Нет | Нет ||
|| **RQ_CODEB**
[`string`](../../../data-types.md) | Code Banque (для страны FR) | Да | Да | Нет | Нет ||
|| **RQ_CODEG**
[`string`](../../../data-types.md) | Code Guichet (для страны FR) | Да | Да | Нет | Нет ||
|| **RQ_RIB**
[`string`](../../../data-types.md) | Clé RIB (для страны FR) | Да | Да | Нет | Нет ||
|| **RQ_MFO**
[`string`](../../../data-types.md) | МФО | Да | Да | Нет | Нет ||
|| **RQ_ACC_NAME**
[`string`](../../../data-types.md) | Bank Account Holder Name | Да | Да | Нет | Нет ||
|| **RQ_ACC_NUM**
[`string`](../../../data-types.md) | Bank Account Number | Да | Да | Нет | Нет ||
|| **RQ_ACC_TYPE**
[`string`](../../../data-types.md) | Tipo da conta (для страны BR) | Да | Да | Нет | Нет ||
|| **RQ_AGENCY_NAME**
[`string`](../../../data-types.md) | Agência (для страны BR) | Да | Да | Нет | Нет ||
|| **RQ_IIK**
[`string`](../../../data-types.md) | ИИК | Да | Да | Нет | Нет ||
|| **RQ_ACC_CURRENCY**
[`string`](../../../data-types.md) | Валюта счета | Да | Да | Нет | Нет ||
|| **RQ_COR_ACC_NUM**
[`string`](../../../data-types.md) | Корреспондентский счет | Да | Да | Нет | Нет ||
|| **RQ_IBAN**
[`string`](../../../data-types.md) | IBAN | Да | Да | Нет | Нет ||
|| **RQ_SWIFT**
[`string`](../../../data-types.md) | SWIFT | Да | Да | Нет | Нет ||
|| **RQ_BIC**
[`string`](../../../data-types.md) | BIC | Да | Да | Нет | Нет ||
|| **COMMENTS**
[`string`](../../../data-types.md) | Комментарий | Да | Да | Нет | Нет ||
|| **ORIGINATOR_ID**
[`string`](../../../data-types.md) | Идентификатор внешней информационной базы. Назначение поля может меняться конечным разработчиком | Да | Да | Нет | Нет ||
|#

## Обзор методов

#|
|| **Метод** | **Описание** ||
|| [crm.requisite.bankdetail.add](./crm-requisite-bank-detail-add.md) | Создает новый банковский реквизит ||
|| [crm.requisite.bankdetail.update](./crm-requisite-bank-detail-update.md) | Изменяет существующий банковский реквизит ||
|| [crm.requisite.bankdetail.get](./crm-requisite-bank-detail-get.md) | Возвращает банковский реквизит по идентификатору ||
|| [crm.requisite.bankdetail.list](./crm-requisite-bank-detail-list.md) | Возвращает список банковских реквизитов по фильтру ||
|| [crm.requisite.bankdetail.delete](./crm-requisite-bank-detail-delete.md) | Удаляет банковский реквизит ||
|| [crm.requisite.bankdetail.fields](./crm-requisite-bank-detail-fields.md) | Возвращает формальное описание полей банковских реквизитов ||
|#


