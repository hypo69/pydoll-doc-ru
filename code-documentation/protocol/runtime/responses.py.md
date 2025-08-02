## Содержание

- [Модуль `pydoll.protocol.runtime.responses`](#модуль-pydollprotocolruntimeresponses)
  - [Типы данных](#типы-данных)
    - [`AwaitPromiseResultDict`](#awaitpromiseresultdict)
    - [`CallFunctionOnResultDict`](#callfunctiononresultdict)
    - [`CompileScriptResultDict`](#compilescriptresultdict)
    - [`EvaluateResultDict`](#evaluateresultdict)
    - [`GetPropertiesResultDict`](#getpropertiesresultdict)
    - [`GlobalLexicalScopeNamesResultDict`](#globallexicalscopenamesresultdict)
    - [`QueryObjectsResultDict`](#queryobjectsresultdict)
    - [`RunScriptResultDict`](#runscriptresultdict)
    - [`GetExceptionDetailsResultDict`](#getexceptiondetailsresultdict)
    - [`GetHeapUsageResultDict`](#getheapusageresultdict)
    - [`GetIsolateIdResultDict`](#getisolateidresultdict)
  - [Ответы](#ответы)
    - [`AwaitPromiseResponse`](#awaitpromiseresponse)
    - [`CallFunctionOnResponse`](#callfunctiononresponse)
    - [`CompileScriptResponse`](#compilescriptresponse)
    - [`EvaluateResponse`](#evaluateresponse)
    - [`GetPropertiesResponse`](#getpropertiesresponse)
    - [`GlobalLexicalScopeNamesResponse`](#globallexicalscopenamesresponse)
    - [`QueryObjectsResponse`](#queryobjectsresponse)
    - [`RunScriptResponse`](#runscriptresponse)
    - [`GetHeapUsageResponse`](#getheapusageresponse)
    - [`GetIsolateIdResponse`](#getisolateidresponse)

# Модуль `pydoll.protocol.runtime.responses`

Этот модуль определяет типы данных для ответов, возвращаемых методами домена `Runtime` протокола Chrome DevTools Protocol (CDP). Эти типы данных представляют собой структуры, которые содержат результаты выполнения команд, связанных с JavaScript-средой выполнения.

## Типы данных

### `AwaitPromiseResultDict`

Результат выполнения команды `awaitPromise`.

- `result` (RemoteObject): Результат промиса.
- `exceptionDetails` (NotRequired[ExceptionDetails]): Детали исключения, если оно произошло.

### `CallFunctionOnResultDict`

Результат выполнения команды `callFunctionOn`.

- `result` (RemoteObject): Результат вызова функции.
- `exceptionDetails` (NotRequired[ExceptionDetails]): Детали исключения, если оно произошло.

### `CompileScriptResultDict`

Результат выполнения команды `compileScript`.

- `scriptId` (NotRequired[str]): Идентификатор скомпилированного скрипта.
- `exceptionDetails` (NotRequired[ExceptionDetails]): Детали исключения, если оно произошло.

### `EvaluateResultDict`

Результат выполнения команды `evaluate`.

- `result` (RemoteObject): Результат оценки выражения.
- `exceptionDetails` (NotRequired[ExceptionDetails]): Детали исключения, если оно произошло.

### `GetPropertiesResultDict`

Результат выполнения команды `getProperties`.

- `result` (list[PropertyDescriptor]): Список свойств.
- `internalProperties` (NotRequired[list[InternalPropertyDescriptor]]): Список внутренних свойств.
- `privateProperties` (NotRequired[list[PrivatePropertyDescriptor]]): Список приватных свойств.
- `exceptionDetails` (NotRequired[ExceptionDetails]): Детали исключения, если оно произошло.

### `GlobalLexicalScopeNamesResultDict`

Результат выполнения команды `globalLexicalScopeNames`.

- `names` (list[str]): Список имен.

### `QueryObjectsResultDict`

Результат выполнения команды `queryObjects`.

- `objects` (list[RemoteObject]): Список объектов.

### `RunScriptResultDict`

Результат выполнения команды `runScript`.

- `result` (RemoteObject): Результат выполнения скрипта.
- `exceptionDetails` (NotRequired[ExceptionDetails]): Детали исключения, если оно произошло.

### `GetExceptionDetailsResultDict`

Результат выполнения команды `getExceptionDetails`.

- `exceptionDetails` (ExceptionDetails): Детали исключения.

### `GetHeapUsageResultDict`

Результат выполнения команды `getHeapUsage`.

- `usedSize` (float): Использованный размер кучи.
- `totalSize` (float): Общий размер кучи.
- `embedderHeapUsedSize` (float): Использованный размер кучи встраиваемого объекта.
- `backingStorageSize` (float): Размер резервного хранилища.

### `GetIsolateIdResultDict`

Результат выполнения команды `getIsolateId`.

- `id` (str): Идентификатор изолята.

## Ответы

### `AwaitPromiseResponse`

Ответ на команду `awaitPromise`.

- `result` (AwaitPromiseResultDict): Результат выполнения команды.

### `CallFunctionOnResponse`

Ответ на команду `callFunctionOn`.

- `result` (CallFunctionOnResultDict): Результат выполнения команды.

### `CompileScriptResponse`

Ответ на команду `compileScript`.

- `result` (CompileScriptResultDict): Результат выполнения команды.

### `EvaluateResponse`

Ответ на команду `evaluate`.

- `result` (EvaluateResultDict): Результат выполнения команды.

### `GetPropertiesResponse`

Ответ на команду `getProperties`.

- `result` (GetPropertiesResultDict): Результат выполнения команды.

### `GlobalLexicalScopeNamesResponse`

Ответ на команду `globalLexicalScopeNames`.

- `result` (GlobalLexicalScopeNamesResultDict): Результат выполнения команды.

### `QueryObjectsResponse`

Ответ на команду `queryObjects`.

- `result` (QueryObjectsResultDict): Результат выполнения команды.

### `RunScriptResponse`

Ответ на команду `runScript`.

- `result` (RunScriptResultDict): Результат выполнения команды.

### `GetHeapUsageResponse`

Ответ на команду `getHeapUsage`.

- `result` (GetHeapUsageResultDict): Результат выполнения команды.

### `GetIsolateIdResponse`

Ответ на команду `getIsolateId`.

- `result` (GetIsolateIdResultDict): Результат выполнения команды.
