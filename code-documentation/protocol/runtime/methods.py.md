## Содержание

- [Модуль `pydoll.protocol.runtime.methods`](#модуль-pydollprotocolruntimemethods)
  - [Класс `RuntimeMethod`](#класс-runtimemethod)
    - [Методы](#методы)

# Модуль `pydoll.protocol.runtime.methods`

Этот модуль определяет методы, доступные в домене `Runtime` протокола Chrome DevTools Protocol (CDP). Эти методы используются для взаимодействия с JavaScript-средой выполнения браузера.

## Класс `RuntimeMethod`

Перечисление, содержащее имена методов, связанных с `Runtime`.

### Методы

- `ADD_BINDING = 'Runtime.addBinding'`: Добавляет привязку JavaScript.
- `AWAIT_PROMISE = 'Runtime.awaitPromise'`: Ожидает промис JavaScript и возвращает его результат.
- `CALL_FUNCTION_ON = 'Runtime.callFunctionOn'`: Вызывает функцию с заданным объявлением на определенном объекте.
- `COMPILE_SCRIPT = 'Runtime.compileScript'`: Компилирует JavaScript-выражение.
- `DISABLE = 'Runtime.disable'`: Отключает домен выполнения.
- `DISCARD_CONSOLE_ENTRIES = 'Runtime.discardConsoleEntries'`: Отбрасывает записи консоли.
- `ENABLE = 'Runtime.enable'`: Включает домен выполнения.
- `EVALUATE = 'Runtime.evaluate'`: Оценивает JavaScript-выражение в глобальном контексте.
- `GET_PROPERTIES = 'Runtime.getProperties'`: Получает свойства JavaScript-объекта.
- `GLOBAL_LEXICAL_SCOPE_NAMES = 'Runtime.globalLexicalScopeNames'`: Получает имена переменных из глобальной лексической области видимости.
- `QUERY_OBJECTS = 'Runtime.queryObjects'`: Запрашивает объекты с заданным прототипом.
- `RELEASE_OBJECT = 'Runtime.releaseObject'`: Освобождает JavaScript-объект.
- `RELEASE_OBJECT_GROUP = 'Runtime.releaseObjectGroup'`: Освобождает все объекты в группе.
- `REMOVE_BINDING = 'Runtime.removeBinding'`: Удаляет привязку JavaScript.
- `RUN_IF_WAITING_FOR_DEBUGGER = 'Runtime.runIfWaitingForDebugger'`: Запускает выполнение, если ожидается отладчик.
- `RUN_SCRIPT = 'Runtime.runScript'`: Выполняет скомпилированный скрипт.
- `SET_ASYNC_CALL_STACK_DEPTH = 'Runtime.setAsyncCallStackDepth'`: Устанавливает глубину асинхронного стека вызовов.
- `GET_EXCEPTION_DETAILS = 'Runtime.getExceptionDetails'`: Получает детали исключения.
- `GET_HEAP_USAGE = 'Runtime.getHeapUsage'`: Получает использование кучи.
- `GET_ISOLATE_ID = 'Runtime.getIsolateId'`: Получает идентификатор изолята.
- `SET_CUSTOM_OBJECT_FORMATTER_ENABLED = 'Runtime.setCustomObjectFormatterEnabled'`: Включает или отключает пользовательские форматеры объектов.
- `SET_MAX_CALL_STACK_SIZE_TO_CAPTURE = 'Runtime.setMaxCallStackSizeToCapture'`: Устанавливает максимальный размер стека вызовов для захвата.
- `TERMINATE_EXECUTION = 'Runtime.terminateExecution'`: Завершает выполнение.
