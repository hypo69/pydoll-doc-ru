## Содержание

- [Модуль `pydoll.exceptions`](#модуль-pydollexceptions)
  - [Базовые классы исключений](#базовые-классы-исключений)
    - [`PydollException(Exception)`](#pydollexceptionexception)
    - [`ConnectionException(PydollException)`](#connectionexceptionpydollexception)
    - [`BrowserException(PydollException)`](#browserexceptionpydollexception)
    - [`ProtocolException(PydollException)`](#protocolexceptionpydollexception)
    - [`ElementException(PydollException)`](#elementexceptionpydollexception)
    - [`TimeoutException(PydollException)`](#timeoutexceptionpydollexception)
    - [`ConfigurationException(PydollException)`](#configurationexceptionpydollexception)
    - [`DialogException(PydollException)`](#dialogexceptionpydollexception)
    - [`ScriptException(PydollException)`](#scriptexceptionpydollexception)
  - [Конкретные классы исключений](#конкретные-классы-исключений)
    - [Исключения подключения](#исключения-подключения)
    - [Исключения браузера](#исключения-браузера)
    - [Исключения протокола](#исключения-протокола)
    - [Исключения элементов](#исключения-элементов)
    - [Исключения таймаутов](#исключения-таймаутов)
    - [Исключения конфигурации](#исключения-конфигурации)
    - [Исключения диалоговых окон](#исключения-диалоговых-окон)
    - [Прочие исключения](#прочие-исключения)

# Модуль `pydoll.exceptions`

Этот модуль содержит все классы исключений, используемые в библиотеке `pydoll`. Исключения организованы по категориям на основе их функциональности и сценариев использования. Каждая категория имеет базовый класс, который предоставляет общую функциональность для связанных исключений.

## Базовые классы исключений

### `PydollException(Exception)`

Базовый класс для всех исключений `pydoll`.

- `message`: Сообщение об ошибке по умолчанию.

### `ConnectionException(PydollException)`

Базовый класс для исключений, связанных с подключением к браузеру.

- `message`: Сообщение об ошибке по умолчанию: 'A connection error occurred'.

### `BrowserException(PydollException)`

Базовый класс для исключений, связанных с управлением процессом браузера.

- `message`: Сообщение об ошибке по умолчанию: 'A browser error occurred'.

### `ProtocolException(PydollException)`

Базовый класс для исключений, связанных с обменом данными по протоколу CDP.

- `message`: Сообщение об ошибке по умолчанию: 'A protocol error occurred'.

### `ElementException(PydollException)`

Базовый класс для исключений, связанных с взаимодействием с элементами.

- `message`: Сообщение об ошибке по умолчанию: 'An element interaction error occurred'.

### `TimeoutException(PydollException)`

Базовый класс для исключений, связанных с таймаутами.

- `message`: Сообщение об ошибке по умолчанию: 'A timeout occurred'.

### `ConfigurationException(PydollException)`

Базовый класс для исключений, связанных с конфигурацией и опциями.

- `message`: Сообщение об ошибке по умолчанию: 'A configuration error occurred'.

### `DialogException(PydollException)`

Базовый класс для исключений, связанных с диалоговыми окнами браузера.

- `message`: Сообщение об ошибке по умолчанию: 'A dialog error occurred'.

### `ScriptException(PydollException)`

Базовый класс для исключений, связанных с выполнением JavaScript.

- `message`: Сообщение об ошибке по умолчанию: 'A script execution error occurred'.

## Конкретные классы исключений

### Исключения подключения

- `ConnectionFailed(ConnectionException)`: Возникает, когда не удается установить соединение с браузером.
- `ReconnectionFailed(ConnectionException)`: Возникает, когда попытка повторного подключения к браузеру завершается неудачей.
- `WebSocketConnectionClosed(ConnectionException)`: Возникает, когда WebSocket-соединение с браузером неожиданно закрывается.
- `NetworkError(ConnectionException)`: Возникает при общей сетевой ошибке во время связи с браузером.

### Исключения браузера

- `BrowserNotRunning(BrowserException)`: Возникает при попытке взаимодействия с неработающим браузером.
- `FailedToStartBrowser(BrowserException)`: Возникает, когда процесс браузера не может быть запущен.
- `UnsupportedOS(BrowserException)`: Возникает при попытке запуска на неподдерживаемой операционной системе.
- `NoValidTabFound(BrowserException)`: Возникает, когда не удается найти или создать действительную вкладку браузера.

### Исключения протокола

- `InvalidCommand(ProtocolException)`: Возникает, когда в браузер отправляется недопустимая команда.
- `InvalidResponse(ProtocolException)`: Возникает, когда от браузера получен недопустимый ответ.
- `ResendCommandFailed(ProtocolException)`: Возникает, когда попытка повторной отправки неудачной команды завершается неудачей.
- `CommandExecutionTimeout(ProtocolException)`: Возникает, когда истекает время выполнения команды.
- `InvalidCallback(ProtocolException)`: Возникает, когда для события предоставляется недопустимый обратный вызов.
- `EventNotSupported(ProtocolException)`: Возникает при попытке подписаться на неподдерживаемое событие.

### Исключения элементов

- `ElementNotFound(ElementException)`: Возникает, когда элемент не может быть найден в DOM.
- `ElementNotVisible(ElementException)`: Возникает при попытке взаимодействия с невидимым элементом.
- `ElementNotInteractable(ElementException)`: Возникает при попытке взаимодействия с элементом, который не может принимать взаимодействие.
- `ClickIntercepted(ElementException)`: Возникает, когда операция клика перехватывается другим элементом.
- `ElementNotAFileInput(ElementException)`: Возникает при попытке использования методов ввода файла для элемента, не являющегося полем ввода файла.

### Исключения таймаутов

- `PageLoadTimeout(TimeoutException)`: Возникает, когда истекает время загрузки страницы.
- `WaitElementTimeout(TimeoutException)`: Возникает, когда истекает время ожидания элемента.

### Исключения конфигурации

- `InvalidOptionsObject(ConfigurationException)`: Возникает, когда предоставляется недопустимый объект опций.
- `InvalidBrowserPath(ConfigurationException)`: Возникает, когда предоставляется недопустимый путь к исполняемому файлу браузера.
- `ArgumentAlreadyExistsInOptions(ConfigurationException)`: Возникает при попытке добавить повторяющийся аргумент в опции браузера.
- `InvalidFileExtension(ConfigurationException)`: Возникает, когда предоставляется неподдерживаемое расширение файла.

### Исключения диалоговых окон

- `NoDialogPresent(DialogException)`: Возникает при попытке взаимодействия с несуществующим диалоговым окном.

### Прочие исключения

- `NotAnIFrame(PydollException)`: Возникает, когда элемент не является iframe.
- `InvalidIFrame(PydollException)`: Возникает, когда iframe недействителен.
- `IFrameNotFound(PydollException)`: Возникает, когда iframe не найден.
- `NetworkEventsNotEnabled(PydollException)`: Возникает, когда сетевые события не включены.
- `InvalidScriptWithElement(ScriptException)`: Возникает, когда скрипт содержит 'argument', но элемент не предоставлен.