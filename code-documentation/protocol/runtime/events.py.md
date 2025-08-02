## Содержание

- [Модуль `pydoll.protocol.runtime.events`](#модуль-pydollprotocolruntimeevents)
  - [Класс `RuntimeEvent`](#класс-runtimeevent)
    - [События](#события)
      - [`CONSOLE_API_CALLED`](#console_api_called--runtimeconsoleapicalled)
      - [`EXCEPTION_REVOKED`](#exception_revoked--runtimeexceptionrevoked)
      - [`EXCEPTION_THROWN`](#exception_thrown--runtimeexceptionthrown)
      - [`EXECUTION_CONTEXT_CREATED`](#execution_context_created--runtimeexecutioncontextcreated)
      - [`EXECUTION_CONTEXT_DESTROYED`](#execution_context_destroyed--runtimeexecutioncontextdestroyed)
      - [`EXECUTION_CONTEXTS_CLEARED`](#execution_contexts_cleared--runtimeexecutioncontextscleared)
      - [`INSPECT_REQUESTED`](#inspect_requested--runtimeinspectrequested)
      - [`BINDING_CALLED`](#binding_called--runtimebindingcalled)

# Модуль `pydoll.protocol.runtime.events`

Этот модуль определяет события из домена `Runtime` протокола Chrome DevTools Protocol (CDP). Эти события предоставляют информацию о выполнении JavaScript, вызовах Console API, исключениях и контекстах выполнения.

## Класс `RuntimeEvent`

Перечисление, содержащее имена событий, связанных с `Runtime`, которые могут быть получены из Chrome DevTools Protocol.

### События

#### `CONSOLE_API_CALLED = 'Runtime.consoleAPICalled'`

Выдается, когда был вызван Console API.

- `type` (str): Тип вызова. Допустимые значения: `log`, `debug`, `info`, `error`, `warning`, `dir`, `dirxml`, `table`, `trace`, `clear`, `startGroup`, `startGroupCollapsed`, `endGroup`, `assert`, `profile`, `profileEnd`, `count`, `timeEnd`.
- `args` (array[RemoteObject]): Аргументы вызова.
- `executionContextId` (ExecutionContextId): Идентификатор контекста, в котором был сделан вызов.
- `timestamp` (Timestamp): Метка времени вызова.
- `stackTrace` (StackTrace): Трассировка стека, захваченная при вызове.
- `context` (str): Дескриптор контекста консоли для вызовов в неконтексте консоли по умолчанию.

#### `EXCEPTION_REVOKED = 'Runtime.exceptionRevoked'`

Выдается, когда необработанное исключение было отозвано.

- `reason` (str): Причина, описывающая, почему исключение было отозвано.
- `exceptionId` (int): Идентификатор отозванного исключения, как сообщается в `exceptionThrown`.

#### `EXCEPTION_THROWN = 'Runtime.exceptionThrown'`

Выдается, когда было выброшено и не обработано исключение.

- `timestamp` (Timestamp): Метка времени исключения.
- `exceptionDetails` (ExceptionDetails): Подробности об исключении.

#### `EXECUTION_CONTEXT_CREATED = 'Runtime.executionContextCreated'`

Выдается, когда создается новый контекст выполнения.

- `context` (ExecutionContextDescription): Вновь созданный контекст выполнения.

#### `EXECUTION_CONTEXT_DESTROYED = 'Runtime.executionContextDestroyed'`

Выдается, когда контекст выполнения уничтожается.

- `executionContextId` (ExecutionContextId): Идентификатор уничтоженного контекста.
- `executionContextUniqueId` (str): Уникальный идентификатор уничтоженного контекста.

#### `EXECUTION_CONTEXTS_CLEARED = 'Runtime.executionContextsCleared'`

Выдается, когда все контексты выполнения были очищены в браузере.

#### `INSPECT_REQUESTED = 'Runtime.inspectRequested'`

Выдается, когда объект должен быть проверен (например, в результате вызова `inspect()` из API командной строки).

- `object` (RemoteObject): Объект для проверки.
- `hints` (object): Подсказки.
- `executionContextId` (ExecutionContextId): Идентификатор контекста, в котором был сделан вызов.

#### `BINDING_CALLED = 'Runtime.bindingCalled'`

Уведомление выдается каждый раз, когда вызывается привязка.

- `name` (str): Имя привязки.
- `payload` (str): Полезная нагрузка привязки.
- `executionContextId` (ExecutionContextId): Идентификатор контекста, в котором был сделан вызов.
