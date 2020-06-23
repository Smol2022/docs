# sendMessage

Метод предназначен для отправки текстового сообщения;
Сообщение будет добавлено в очередь на отправку;

## Запрос {#request}

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный параметр | Описание
----- | ----- | ----- | -----
`chatId` | **string** | Нет | идентификатор чата (string) в формате Whatsapp (17633123456@c.us - для личных сообщений). ``Обязателен``, если не указан phoneNumber;
`phoneNumber` | **integer** | Нет | номер телефона получателя в международном формате (без +) 11 или 12 цифр. ``Обязателен``, если не указан chatId;
`message ` | **string** | Да | текст сообщения (string);

## Ответ {#response}

### Поля успешного ответа {#response-parameters}

* idMessage - идентификатор сообщения (string:20);

* reason - причина почему сообщение не было добавлено в очередь на отправку (string). Присутствует, если нет idMessage; Возможные значения reason:

    * instance in starting process try later - инстанс аккаунта находится в процессе запуска/перезапуска, попробовать спустя несколько секунд;

    * instance account not authorized - инстанс аккаунта не авторизован;

    * bad request data - данные запроса не валидны;


### Ошибки ChangeMessageVisibility {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [{#T}](../common-errors.md).

Код HTTP | Идентификатор ошибки | Описание
----- | ----- | -----
400 | `bad request data` | данные запроса не валидны.

## Пример запроса {#request-example}

```json
{
    "chatId": "",
    "phoneNumber": 79001234567,
    "message": "Hello man"
}
```

Подробнее о формировании запросов см. в разделе [Общий вид запросов к API](../index.md#api-request).

## Пример ответа {#response-example}
RESPONSE: 200 － OK
```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```