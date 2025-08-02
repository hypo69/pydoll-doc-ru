## Содержание

- [Модуль `pydoll.commands.fetch_commands`](#модуль-pydollcommandsfetch_commands)
  - [Класс `FetchCommands`](#класс-fetchcommands)
    - [Методы](#методы)
      - [`continue_request`](#continue_requestrequest_id-str-url-optionalstr--none-method-optionalrequestmethod--none-post_data-optionalstr--none-headers-optionallistheaderentry--none-intercept_response-optionalbool--none---commandresponse)
      - [`continue_request_with_auth`](#continue_request_with_authrequest_id-str-auth_challenge_response-authchallengeresponsevalues-proxy_username-optionalstr--none-proxy_password-optionalstr--none---commandresponse)
      - [`disable`](#disable---commandresponse)
      - [`enable`](#enablehandle_auth_requests-bool-url_pattern-str----resource_type-optionalresourcetype--none-request_stage-optionalrequeststage--none---commandresponse)
      - [`fail_request`](#fail_requestrequest_id-str-error_reason-networkerrorreason---commandresponse)
      - [`fulfill_request`](#fulfill_requestrequest_id-str-response_code-int-response_headers-optionallistheaderentry--none-body-optionalstr--none-response_phrase-optionalstr--none---commandresponse)
      - [`get_response_body`](#get_response_bodyrequest_id-str---commandgetresponsebodyresponse)
      - [`continue_response`](#continue_responserequest_id-str-response_code-optionalint--none-response_headers-optionallistheaderentry--none-response_phrase-optionalstr--none---commandresponse)
      - [`take_response_body_as_stream`](#take_response_body_as_streamrequest_id-str---commandtakeresponsebodyasstreamresponse)

# Модуль `pydoll.commands.fetch_commands`

Этот модуль инкапсулирует команды `fetch` протокола Chrome DevTools Protocol (CDP). Домен `Fetch` CDP позволяет перехватывать и изменять сетевые запросы на уровне приложения. Это позволяет разработчикам проверять, изменять и контролировать сетевой трафик, что особенно полезно для тестирования, отладки и расширенных сценариев автоматизации.

## Класс `FetchCommands`

Предоставляет команды для взаимодействия с сетевыми запросами.

### Методы

#### `continue_request(request_id: str, url: Optional[str] = None, method: Optional[RequestMethod] = None, post_data: Optional[str] = None, headers: Optional[list[HeaderEntry]] = None, intercept_response: Optional[bool] = None) -> Command[Response]`

Создает команду для продолжения приостановленного запроса `fetch`. Эта команда позволяет браузеру возобновить операцию `fetch`, которая была перехвачена. Вы можете изменить URL-адрес запроса `fetch`, метод, заголовки и тело перед продолжением.

- `request_id`: Идентификатор запроса `fetch` для продолжения.
- `url`: Новый URL-адрес для запроса `fetch`. По умолчанию `None`.
- `method`: HTTP-метод для использования (например, 'GET', 'POST'). По умолчанию `None`.
- `post_data`: Данные тела для отправки с запросом `fetch`. По умолчанию `None`.
- `headers`: Список HTTP-заголовков для включения в запрос `fetch`. По умолчанию `None`.
- `intercept_response`: Указывает, следует ли перехватывать ответ. По умолчанию `None`.
- **Возвращает**: Команду для продолжения запроса `fetch`.

#### `continue_request_with_auth(request_id: str, auth_challenge_response: AuthChallengeResponseValues, proxy_username: Optional[str] = None, proxy_password: Optional[str] = None) -> Command[Response]`

Создает команду для продолжения приостановленного запроса `fetch` с аутентификацией. Эта команда используется, когда операция `fetch` требует аутентификации. Она предоставляет необходимые учетные данные для продолжения запроса.

- `request_id`: Идентификатор запроса `fetch` для продолжения.
- `auth_challenge_response`: Тип ответа на запрос аутентификации.
- `proxy_username`: Имя пользователя для аутентификации прокси. По умолчанию `None`.
- `proxy_password`: Пароль для аутентификации прокси. По умолчанию `None`.
- **Возвращает**: Команду для продолжения запроса `fetch` с аутентификацией.

#### `disable() -> Command[Response]`

Создает команду для отключения перехвата `fetch`. Эта команда останавливает браузер от перехвата запросов `fetch`.

- **Возвращает**: Команду для отключения перехвата `fetch`.

#### `enable(handle_auth_requests: bool, url_pattern: str = '*', resource_type: Optional[ResourceType] = None, request_stage: Optional[RequestStage] = None) -> Command[Response]`

Создает команду для включения перехвата `fetch`. Эта команда позволяет браузеру начать перехват запросов `fetch`. Вы можете указать, следует ли обрабатывать запросы аутентификации и типы ресурсов для перехвата.

- `handle_auth_requests`: Указывает, следует ли обрабатывать запросы аутентификации.
- `url_pattern`: Шаблон для сопоставления URL-адресов для перехвата. По умолчанию `'*'`.
- `resource_type`: Тип ресурса для перехвата. По умолчанию `None`.
- `request_stage`: Стадия запроса для перехвата. По умолчанию `None`.
- **Возвращает**: Команду для включения перехвата `fetch`.

#### `fail_request(request_id: str, error_reason: NetworkErrorReason) -> Command[Response]`

Создает команду для имитации сбоя в запросе `fetch`. Эта команда позволяет имитировать сбой для конкретной операции `fetch`, указывая причину сбоя.

- `request_id`: Идентификатор запроса `fetch` для сбоя.
- `error_reason`: Причина сбоя.
- **Возвращает**: Команду для сбоя запроса `fetch`.

#### `fulfill_request(request_id: str, response_code: int, response_headers: Optional[list[HeaderEntry]] = None, body: Optional[str] = None, response_phrase: Optional[str] = None) -> Command[Response]`

Создает команду для выполнения запроса `fetch` с пользовательским ответом. Эта команда позволяет предоставить пользовательский ответ для операции `fetch`, включая HTTP-статус-код, заголовки и содержимое тела.

- `request_id`: Идентификатор запроса `fetch` для выполнения.
- `response_code`: HTTP-статус-код для возврата.
- `response_headers`: Список заголовков ответа. По умолчанию `None`.
- `body`: Содержимое тела ответа. По умолчанию `None`.
- `response_phrase`: Фраза ответа (например, 'OK', 'Not Found'). По умолчанию `None`.
- **Возвращает**: Команду для выполнения запроса `fetch`.

#### `get_response_body(request_id: str) -> Command[GetResponseBodyResponse]`

Создает команду для получения тела ответа запроса `fetch`. Эта команда позволяет получить доступ к телу завершенной операции `fetch`, что может быть полезно для анализа данных ответа.

- `request_id`: Идентификатор запроса `fetch` для получения тела.

- **Возвращает**: Команду для получения тела ответа.

#### `continue_response(request_id: str, response_code: Optional[int] = None, response_headers: Optional[list[HeaderEntry]] = None, response_phrase: Optional[str] = None) -> Command[Response]`

Создает команду для продолжения ответа `fetch` для перехваченного запроса. Эта команда позволяет браузеру продолжить поток ответа для конкретного запроса `fetch`, включая настройку HTTP-статус-кода, заголовков и фразы ответа.

- `request_id`: Идентификатор запроса `fetch` для продолжения ответа.
- `response_code`: HTTP-статус-код для отправки. По умолчанию `None`.
- `response_headers`: Список заголовков ответа. По умолчанию `None`.
- `response_phrase`: Фраза ответа (например, 'OK'). По умолчанию `None`.
- **Возвращает**: Команду для продолжения ответа `fetch`.

#### `take_response_body_as_stream(request_id: str) -> Command[TakeResponseBodyAsStreamResponse]`

Создает команду для получения тела ответа в виде потока. Эта команда позволяет получать тело ответа в виде потока, что может быть полезно для обработки больших ответов.

- `request_id`: Идентификатор запроса `fetch` для получения потока тела ответа.
- **Возвращает**: Команду для получения тела ответа в виде потока.