## Содержание

- [Модуль `pydoll.protocol.runtime.params`](#модуль-pydollprotocolruntimeparams)
  - [Параметры команд](#параметры-команд)
    - [`AddBindingParams`](#addbindingparams)
    - [`AwaitPromiseParams`](#awaitpromiseparams)
    - [`CallFunctionOnParams`](#callfunctiononparams)
    - [`CompileScriptParams`](#compilescriptparams)
    - [`EvaluateParams`](#evaluateparams)
    - [`GetPropertiesParams`](#getpropertiesparams)
    - [`GlobalLexicalScopeNamesParams`](#globallexicalscopenamesparams)
    - [`QueryObjectsParams`](#queryobjectsparams)
    - [`ReleaseObjectParams`](#releaseobjectparams)
    - [`ReleaseObjectGroupParams`](#releaseobjectgroupparams)
    - [`RemoveBindingParams`](#removebindingparams)
    - [`RunScriptParams`](#runscriptparams)
    - [`SetAsyncCallStackDepthParams`](#setasynccallstackdepthparams)
    - [`GetExceptionDetailsParams`](#getexceptiondetailsparams)
    - [`SetCustomObjectFormatterEnabledParams`](#setcustomobjectformatterenabledparams)
    - [`SetMaxCallStackSizeToCaptureParams`](#setmaxcallstacksizetocaptureparams)

# Модуль `pydoll.protocol.runtime.params`

Этот модуль определяет параметры для команд, используемых в домене `Runtime` протокола Chrome DevTools Protocol (CDP). Эти параметры представляют собой структуры, которые передаются при вызове команд для взаимодействия с JavaScript-средой выполнения.

## Параметры команд

### `AddBindingParams`

Параметры для команды `addBinding`.

- `name` (str): Имя привязки для добавления.
- `executionContextName` (NotRequired[str]): Имя контекста выполнения для привязки.

### `AwaitPromiseParams`

Параметры для команды `awaitPromise`.

- `promiseObjectId` (str): Идентификатор промиса для ожидания.
- `returnByValue` (NotRequired[bool]): Возвращать ли результат по значению вместо ссылки.
- `generatePreview` (NotRequired[bool]): Генерировать ли предварительный просмотр для результата.

### `CallFunctionOnParams`

Параметры для команды `callFunctionOn`.

- `functionDeclaration` (str): Объявление функции для вызова.
- `objectId` (NotRequired[str]): Идентификатор объекта, на котором нужно вызвать функцию.
- `arguments` (NotRequired[list[CallArgument]]): Аргументы для передачи функции.
- `silent` (NotRequired[bool]): Подавлять ли исключения.
- `returnByValue` (NotRequired[bool]): Возвращать ли результат по значению вместо ссылки.
- `generatePreview` (NotRequired[bool]): Генерировать ли предварительный просмотр для результата.
- `userGesture` (NotRequired[bool]): Обрабатывать ли вызов как инициированный жестом пользователя.
- `awaitPromise` (NotRequired[bool]): Ожидать ли результат промиса.
- `executionContextId` (NotRequired[str]): Идентификатор контекста выполнения, в котором нужно вызвать функцию.
- `objectGroup` (NotRequired[str]): Символическое имя группы для результата.
- `throwOnSideEffect` (NotRequired[bool]): Вызывать ли исключение, если побочный эффект не может быть исключен.
- `uniqueContextId` (NotRequired[str]): Уникальный идентификатор контекста для вызова функции.
- `serializationOptions` (NotRequired[SerializationOptions]): Опции сериализации для результата.

### `CompileScriptParams`

Параметры для команды `compileScript`.

- `expression` (str): JavaScript-выражение для компиляции.
- `sourceURL` (NotRequired[str]): URL исходного файла для скрипта.
- `persistScript` (NotRequired[bool]): Сохранять ли скомпилированный скрипт.
- `executionContextId` (NotRequired[str]): Идентификатор контекста выполнения, в котором нужно скомпилировать скрипт.

### `EvaluateParams`

Параметры для команды `evaluate`.

- `expression` (str): JavaScript-выражение для оценки.
- `objectGroup` (NotRequired[str]): Символическое имя группы для результата.
- `includeCommandLineAPI` (NotRequired[bool]): Включать ли API командной строки.
- `silent` (NotRequired[bool]): Подавлять ли исключения.
- `contextId` (NotRequired[str]): Идентификатор контекста выполнения для оценки.
- `returnByValue` (NotRequired[bool]): Возвращать ли результат по значению вместо ссылки.
- `generatePreview` (NotRequired[bool]): Генерировать ли предварительный просмотр для результата.
- `userGesture` (NotRequired[bool]): Обрабатывать ли оценку как инициированную жестом пользователя.
- `awaitPromise` (NotRequired[bool]): Ожидать ли результат промиса.
- `throwOnSideEffect` (NotRequired[bool]): Вызывать ли исключение, если побочный эффект не может быть исключен.
- `timeout` (NotRequired[float]): Таймаут в миллисекундах.
- `disableBreaks` (NotRequired[bool]): Отключать ли точки останова во время оценки.
- `replMode` (NotRequired[bool]): Выполнять ли в режиме REPL.
- `allowUnsafeEvalBlockedByCSP` (NotRequired[bool]): Разрешать ли небезопасную оценку, заблокированную CSP.
- `uniqueContextId` (NotRequired[str]): Уникальный идентификатор контекста для оценки.
- `serializationOptions` (NotRequired[SerializationOptions]): Опции сериализации для результата.

### `GetPropertiesParams`

Параметры для команды `getProperties`.

- `objectId` (str): Идентификатор объекта, для которого нужно получить свойства.
- `ownProperties` (NotRequired[bool]): Возвращать ли только собственные свойства.
- `accessorPropertiesOnly` (NotRequired[bool]): Возвращать ли только свойства-аксессоры.
- `generatePreview` (NotRequired[bool]): Генерировать ли предварительный просмотр для значений свойств.
- `nonIndexedPropertiesOnly` (NotRequired[bool]): Возвращать ли только неиндексированные свойства.

### `GlobalLexicalScopeNamesParams`

Параметры для команды `globalLexicalScopeNames`.

- `executionContextId` (NotRequired[str]): Идентификатор контекста выполнения, из которого нужно получить имена области видимости.

### `QueryObjectsParams`

Параметры для команды `queryObjects`.

- `prototypeObjectId` (str): Идентификатор объекта-прототипа.
- `objectGroup` (NotRequired[str]): Символическое имя группы для результатов.

### `ReleaseObjectParams`

Параметры для команды `releaseObject`.

- `objectId` (str): Идентификатор объекта для освобождения.

### `ReleaseObjectGroupParams`

Параметры для команды `releaseObjectGroup`.

- `objectGroup` (str): Имя группы объектов для освобождения.

### `RemoveBindingParams`

Параметры для команды `removeBinding`.

- `name` (str): Имя привязки для удаления.

### `RunScriptParams`

Параметры для команды `runScript`.

- `scriptId` (str): Идентификатор скомпилированного скрипта для выполнения.
- `executionContextId` (NotRequired[str]): Идентификатор контекста выполнения, в котором нужно выполнить скрипт.
- `objectGroup` (NotRequired[str]): Символическое имя группы для результата.
- `silent` (NotRequired[bool]): Подавлять ли исключения.
- `includeCommandLineAPI` (NotRequired[bool]): Включать ли API командной строки.
- `returnByValue` (NotRequired[bool]): Возвращать ли результат по значению вместо ссылки.
- `generatePreview` (NotRequired[bool]): Генерировать ли предварительный просмотр для результата.
- `awaitPromise` (NotRequired[bool]): Ожидать ли результат промиса.

### `SetAsyncCallStackDepthParams`

Параметры для команды `setAsyncCallStackDepth`.

- `maxDepth` (int): Максимальная глубина асинхронных стеков вызовов.

### `GetExceptionDetailsParams`

Параметры для команды `getExceptionDetails`.

- `errorObjectId` (str): Идентификатор объекта ошибки.

### `SetCustomObjectFormatterEnabledParams`

Параметры для команды `setCustomObjectFormatterEnabled`.

- `enabled` (bool): Включить или отключить пользовательские форматеры объектов.

### `SetMaxCallStackSizeToCaptureParams`

Параметры для команды `setMaxCallStackSizeToCapture`.

- `size` (int): Максимальный размер стека вызовов для захвата.
