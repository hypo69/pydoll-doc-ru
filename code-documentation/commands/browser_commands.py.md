## Содержание

- [Модуль `pydoll.commands.browser_commands`](#модуль-pydollcommandsbrowser_commands)
  - [Класс `BrowserCommands`](#класс-browsercommands)
    - [Методы](#методы)
      - [`get_version`](#get_version---commandgetversionresponse)
      - [`reset_permissions`](#reset_permissionsbrowser_context_id-optionalstr--none---commandresponse)
      - [`cancel_download`](#cancel_downloadguid-str-browser_context_id-optionalstr--none---commandresponse)
      - [`crash`](#crash---commandresponse)
      - [`crash_gpu_process`](#crash_gpu_process---commandresponse)
      - [`set_download_behavior`](#set_download_behaviorbehavior-downloadbehavior-download_path-optionalstr--none-browser_context_id-optionalstr--none-events_enabled-bool--true---commandresponse)
      - [`close`](#close---commandresponse)
      - [`get_window_for_target`](#get_window_for_targettarget_id-str---commandgetwindowfortargetresponse)
      - [`set_window_bounds`](#set_window_boundswindow_id-int-bounds-windowboundsdict---commandresponse)
      - [`set_window_maximized`](#set_window_maximizedwindow_id-int---commandresponse)
      - [`set_window_minimized`](#set_window_minimizedwindow_id-int---commandresponse)
      - [`grant_permissions`](#grant_permissionspermissions-listpermissiontype-origin-optionalstr--none-browser_context_id-optionalstr--none---commandresponse)

# Модуль `pydoll.commands.browser_commands`

Этот модуль содержит класс `BrowserCommands`, который предоставляет набор команд для взаимодействия с основной функциональностью браузера на основе CDP. Эти команды позволяют управлять окнами браузера, такими как закрытие окон, получение идентификаторов окон и настройка границ окон (размера и состояния).

## Класс `BrowserCommands`

Предоставляет набор команд для взаимодействия с основной функциональностью браузера на основе CDP.

### Методы

#### `get_version() -> Command[GetVersionResponse]`

Генерирует команду для получения информации о версии браузера.

- **Возвращает**: Команду CDP, которая возвращает сведения о версии браузера, включая версию протокола, название продукта, ревизию и пользовательский агент.

#### `reset_permissions(browser_context_id: Optional[str] = None) -> Command[Response]`

Генерирует команду для сброса всех разрешений.

- `browser_context_id`: Идентификатор контекста браузера, для которого нужно сбросить разрешения. Если не указан, сбрасывает разрешения для контекста по умолчанию.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ.

#### `cancel_download(guid: str, browser_context_id: Optional[str] = None) -> Command[Response]`

Генерирует команду для отмены загрузки.

- `guid`: Глобальный уникальный идентификатор загрузки.
- `browser_context_id`: Идентификатор контекста браузера, к которому относится загрузка. Если не указан, используется контекст по умолчанию.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ.

#### `crash() -> Command[Response]`

Генерирует команду для аварийного завершения основного процесса браузера.

- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ перед аварийным завершением браузера.

#### `crash_gpu_process() -> Command[Response]`

Генерирует команду для аварийного завершения процесса GPU браузера.

- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ перед аварийным завершением процесса GPU.

#### `set_download_behavior(behavior: DownloadBehavior, download_path: Optional[str] = None, browser_context_id: Optional[str] = None, events_enabled: bool = True) -> Command[Response]`

Генерирует команду для установки поведения загрузки для браузера.

- `behavior`: Поведение, которое нужно установить для загрузок.
- `download_path`: Путь для загрузок.
- `browser_context_id`: Идентификатор контекста браузера, для которого нужно установить поведение загрузки.
- `events_enabled`: Включить события загрузки.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ.

#### `close() -> Command[Response]`

Генерирует команду для закрытия браузера.

- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ перед закрытием браузера.

#### `get_window_for_target(target_id: str) -> Command[GetWindowForTargetResponse]`

Генерирует команду для получения окна для данного идентификатора цели.

- `target_id`: Идентификатор цели, для которой нужно получить окно.
- **Возвращает**: Команду CDP, которая возвращает информацию об окне, включая `windowId` и `bounds`.

#### `set_window_bounds(window_id: int, bounds: WindowBoundsDict) -> Command[Response]`

Генерирует команду для установки границ окна.

- `window_id`: Идентификатор окна, для которого нужно установить границы.
- `bounds`: Границы, которые нужно установить для окна, которые должны включать `windowState` и, при необходимости, `width`, `height`, `x` и `y` координаты.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ после установки границ окна.

#### `set_window_maximized(window_id: int) -> Command[Response]`

Генерирует команду для максимизации окна.

- `window_id`: Идентификатор окна для максимизации.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ после максимизации окна.

#### `set_window_minimized(window_id: int) -> Command[Response]`

Генерирует команду для минимизации окна.

- `window_id`: Идентификатор окна для минимизации.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ после минимизации окна.

#### `grant_permissions(permissions: list[PermissionType], origin: Optional[str] = None, browser_context_id: Optional[str] = None) -> Command[Response]`

Генерирует команду для предоставления определенных разрешений данному источнику.

- `permissions`: Список разрешений для предоставления.
- `origin`: Источник, которому нужно предоставить разрешения. Если не указан, предоставляет для всех источников.
- `browser_context_id`: Контекст браузера, в котором нужно предоставить разрешения. Если не указан, используется контекст по умолчанию.
- **Возвращает**: Команду CDP, которая возвращает базовый успешный ответ после предоставления указанных разрешений.
