# Контекстное меню

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- нужны правки под стандарт написания
- не прописаны ссылки на несозданные ещё страницы

{% endnote %}

{% endif %}

Контекстное меню позволит пользователю взаимодействовать с чат-ботом или приложением для чата из контекстного меню сообщения.

![Контекстное меню](./_images/custom_menu.png)

## Как добавить свои пункты в контекстное меню

Контекстное меню – это часть сообщения, при создании сообщения нужно добавить ключ `MENU` и передать параметры.

Методы, которые поддерживают контекстное меню:
- [imbot.message.add](../../chat-bots/messages/imbot-message-add.md) - отправка сообщения от чат-бота.
- [imbot.message.update](../../chat-bots/messages/imbot-message-update.md) - отправка изменения сообщения чат-бота.
- [imbot.command.answer](../../chat-bots/commands/imbot-command-answer.md) - публикация ответа на команду.
- [im.message.add](./im-message-add.md) - отправка сообщения в чат.
- [im.message.update](./im-message-update.md) - отправка изменения сообщения чат-бота.

Рассмотрим на примере это сообщение:

{% include [Пояснение о restCommand](../_includes/rest-command.md) %}

```php
restCommand(
    'im.message.add',
    Array(
        "DIALOG_ID" => 12,
        "MESSAGE" => "Hello! Message with context menu!",
        "MENU" => Array(
            Array(
                "TEXT" => "Bitrix24",
                "LINK" => "http://bitrix24.com",
            ),
            Array(
                "TEXT" => "Echo",
                "COMMAND" => "echo",
                "COMMAND_PARAMS" => "test from keyboard"
            ),
            Array(
                "TEXT" => "Open app",
                "APP_ID" => "12",
                "APP_PARAMS" => "TEST"
            ),
        )
    ),
    $_REQUEST["auth"]
);
```

Контекстное меню - это набор кнопок, каждая кнопка может состоять из следующих ключей:

- **TEXT** - текст кнопки;
- **LINK** - ссылка;
- **COMMAND** - команда, которая будет отправлена боту;
- **COMMAND_PARAMS** - параметры для команды;
- **APP_ID** - идентификатор установленного приложения для чата.
- **APP_PARAMS** - параметры для запуска приложения для чата.
- **DISABLED** - если указать `Y`, то данная кнопка не будет кликабельной.
- **ACTION** - действие, может быть одно из следующих типов ([REST ревизии 28](../../chat-bots/im-revision-get.md)):
  - **PUT** - вставить в поле ввода.
  - **SEND** - отправить текст.
  - **COPY** - копировать текст в буфер обмена.
  - **CALL** - позвонить.
  - **DIALOG** - открыть указанный диалог.
- **ACTION_VALUE** - значение, для каждого типа означает свое ([REST ревизии 28](../../chat-bots/im-revision-get.md)):
  - **PUT** - текст, который будет вставлен в поле ввода.
  - **SEND** - текст, который будет отправлен.
  - **COPY** - текст, который будет скопирован в буфер обмена.
  - **CALL** - номер телефона в международном формате.
  - **DIALOG** - идентификатор диалога, это может быть `ID` пользователя, либо `ID` чата в формате `chatXXX`.

Обязательными полями является **TEXT** и либо поле **LINK**, либо поле **COMMAND**.

Если указан ключ **LINK**, то кнопка становится внешней ссылкой. Если указаны поля **COMMAND** и **COMMAND_PARAMS**, то кнопка является действием и отправляет команду чат-боту, не публикуя ее в чат. Доступно с 26 версии [ревизии API (версии платформы)](../../chat-bots/im-revision-get.md).

Если указаны поля **APP_ID** и **APP_PARAMS**, то кнопка откроет окно с приложением для чата.

Если необходимо сделать две строки с кнопками в ряд, то для их разделения нужно добавить кнопку со следующим содержимым: `"TYPE" => "NEWLINE"`.

## Обработка команд чат-ботом

Для обработки нажатия кнопок клавиатуры и пунктов меню, используются **команды**.

1. Для того, чтобы команда отрабатывала в клавиатуре (и не только), необходимо ее предварительно зарегистрировать через метод [imbot.command.register](../../chat-bots/commands/imbot-command-register.md) (чтобы команда была доступна только для клавиатуры, необходимо создать ее с ключом `"HIDDEN" => "Y"`).

    В кнопке указывается следующие ключи:

    ```php
    "COMMAND" => "page", // команда, которая будет отправлена чат-боту
    "COMMAND_PARAMS" => "1", // параметры для команды
    ```

2. Нажатие на кнопку создаст событие [ONIMCOMMANDADD](../../chat-bots/commands/events/index.md).

3. Внутри этого события нужно либо создать новое сообщение, либо отредактировать старое (тем самым формируя эффект постраничной навигации).

4. Внутри события, в массиве **[data][COMMAND]** будут переданы данные о вызванном событии. В нем есть значение **COMMAND_CONTEXT** - это специальный ключ, описывающий в каком контексте была вызвана команда:
   - если команду написал пользователь самостоятельно, там будет **TEXTAREA**;
   - если команда пришла из клавиатуры, то будет **KEYBOARD**;
   - если команда пришла из контекстного меню, то будет **MENU**.

## Обработка открытия приложения для чата

Приложение для чата, запускаемые из контекстного меню, работают по принципам [Контекстного приложения](/learning/course/?COURSE_ID=93&LESSON_ID=9303).