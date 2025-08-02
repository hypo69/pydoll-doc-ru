## Содержание

- [Класс `TargetCommands`](#класс-targetcommands)
  - [Методы](#методы)
    - [`activate_target`](#activate_targettarget_id-str---commandresponse)
    - [`attach_to_target`](#attach_to_targettarget_id-str-flatten-optionalbool--none---commandattachtotargetresponse)
    - [`close_target`](#close_targettarget_id-str---commandresponse)
    - [`create_browser_context`](#create_browser_contextdispose_on_detach-optionalbool--none-proxy_server-optionalstr--none-proxy_bypass_list-optionalstr--none-origins_with_universal_network_access-optionalliststr--none---commandcreatebrowsercontextresponse)
    - [`create_target`](#create_targeturl-str-left-optionalint--none-top-optionalint--none-width-optionalint--none-height-optionalint--none-window_state-optionalwindowstate--none-browser_context_id-optionalstr--none-enable_begin_frame_control-optionalbool--none-new_window-optionalbool--none-background-optionalbool--none-for_tab-optionalbool--none-hidden-optionalbool--none---commandcreatetargetresponse)
    - [`detach_from_target`](#detach_from_targetsession_id-optionalstr--none---commandresponse)
    - [`dispose_browser_context`](#dispose_browser_contextbrowser_context_id-str---commandresponse)
    - [`get_browser_contexts`](#get_browser_contexts---commandgetbrowsercontextsresponse)
    - [`get_targets`](#get_targetsfilter-optionallist--none---commandgettargetsresponse)
    - [`set_auto_attach`](#set_auto_attachauto_attach-bool-wait_for_debugger_on_start-optionalbool--none-flatten-optionalbool--none-filter-optionallist--none---commandresponse)
    - [`set_discover_targets`](#set_discover_targetscover-bool-filter-optionallist--none---commandresponse)
    - [`attach_to_browser_target`](#attach_to_browser_targetsession_id-str---commandattachtobrowsertargetresponse)
    - [`get_target_info`](#get_target_infotarget_id-str---commandgettargetinforesponse)
    - [`set_remote_locations`](#set_remote_locationslocations-listremotelocation---commandresponse)

# Модуль `pydoll.commands.target_commands`

Этот модуль содержит класс `TargetCommands`, который предоставляет набор команд для управления целями браузера с использованием Chrome DevTools Protocol (CDP).

## Класс `TargetCommands`

Предоставляет методы для создания команд для взаимодействия с целями браузера, включая создание, активацию, подключение и закрытие целей через команды CDP.

### Методы

#### `activate_target(target_id: str) -> Command[Response]`

Генерирует команду для активации (фокусировки) цели.

- `target_id`: Идентификатор цели для активации.
- **Возвращает**: Команду CDP для активации цели.

#### `attach_to_target(target_id: str, flatten: Optional[bool] = None) -> Command[AttachToTargetResponse]`

Генерирует команду для подключения к цели с заданным ID.

- `target_id`: Идентификатор цели для подключения.
- `flatten`: Если `True`, включает "плоский" доступ к сессии через указание атрибута `sessionId` в командах.
- **Возвращает**: Команду CDP для подключения к цели, которая вернет `sessionId`.

#### `close_target(target_id: str) -> Command[Response]`

Генерирует команду для закрытия цели.

- `target_id`: Идентификатор цели для закрытия.
- **Возвращает**: Команду CDP для закрытия цели, которая вернет флаг успеха.

#### `create_browser_context(dispose_on_detach: Optional[bool] = None, proxy_server: Optional[str] = None, proxy_bypass_list: Optional[str] = None, origins_with_universal_network_access: Optional[list[str]] = None) -> Command[CreateBrowserContextResponse]`

Генерирует команду для создания нового пустого контекста браузера.

- `dispose_on_detach`: Если указано, контекст будет удален при отключении сессии отладки.
- `proxy_server`: Строка прокси-сервера.
- `proxy_bypass_list`: Список обхода прокси.
- `origins_with_universal_network_access`: Необязательный список источников для предоставления неограниченного кросс-доменного доступа.
- **Возвращает**: Команду CDP для создания контекста браузера, которая вернет ID созданного контекста.

#### `create_target(url: str, left: Optional[int] = None, top: Optional[int] = None, width: Optional[int] = None, height: Optional[int] = None, window_state: Optional[WindowState] = None, browser_context_id: Optional[str] = None, enable_begin_frame_control: Optional[bool] = None, new_window: Optional[bool] = None, background: Optional[bool] = None, for_tab: Optional[bool] = None, hidden: Optional[bool] = None) -> Command[CreateTargetResponse]`

Генерирует команду для создания новой страницы (цели).

- `url`: Начальный URL, на который будет переходить страница.
- `left`: Позиция левого края фрейма в DIP.
- `top`: Позиция верхнего края фрейма в DIP.
- `width`: Ширина фрейма в DIP.
- `height`: Высота фрейма в DIP.
- `window_state`: Состояние окна фрейма: `normal`, `minimized`, `maximized` или `fullscreen`.
- `browser_context_id`: Контекст браузера, в котором нужно создать страницу.
- `enable_begin_frame_control`: Включить ли контроль `BeginFrames` для этой цели.
- `new_window`: Создавать ли новое окно или вкладку.
- `background`: Создавать ли цель в фоновом или переднем плане.
- `for_tab`: Создавать ли цель типа "tab".
- `hidden`: Создавать ли скрытую цель.
- **Возвращает**: Команду CDP для создания цели, которая вернет ID созданной цели.

#### `detach_from_target(session_id: Optional[str] = None) -> Command[Response]`

Генерирует команду для отсоединения сессии от ее цели.

- `session_id`: ID сессии для отсоединения. Если не указан, отсоединяет все сессии.
- **Возвращает**: Команду CDP для отсоединения от цели.

#### `dispose_browser_context(browser_context_id: str) -> Command[Response]`

Генерирует команду для удаления контекста браузера.

- `browser_context_id`: ID контекста браузера для удаления.
- **Возвращает**: Команду CDP для удаления контекста браузера.

#### `get_browser_contexts() -> Command[GetBrowserContextsResponse]`

Генерирует команду для получения всех контекстов браузера, созданных с помощью `createBrowserContext`.

- **Возвращает**: Команду CDP для получения всех контекстов браузера, которая вернет массив ID контекстов браузера.

#### `get_targets(filter: Optional[list] = None) -> Command[GetTargetsResponse]`

Генерирует команду для получения списка доступных целей.

- `filter`: Будут сообщены только цели, соответствующие фильтру.
- **Возвращает**: Команду CDP для получения целей, которая вернет список объектов `TargetInfo` с подробностями о каждой цели.

#### `set_auto_attach(auto_attach: bool, wait_for_debugger_on_start: Optional[bool] = None, flatten: Optional[bool] = None, filter: Optional[list] = None) -> Command[Response]`

Генерирует команду для управления автоматическим подключением к новым целям.

- `auto_attach`: Автоматически подключаться ли к связанным целям.
- `wait_for_debugger_on_start`: Приостанавливать ли новые цели при подключении к ним.
- `flatten`: Включает "плоский" доступ к сессии через указание атрибута `sessionId` в командах.
- `filter`: Будут подключены только цели, соответствующие фильтру.
- **Возвращает**: Команду CDP для установки поведения автоматического подключения.

#### `set_discover_targets(discover: bool, filter: Optional[list] = None) -> Command[Response]`

Генерирует команду для управления обнаружением целей.

- `discover`: Обнаруживать ли доступные цели.
- `filter`: Будут обнаружены только цели, соответствующие фильтру.
- **Возвращает**: Команду CDP для установки обнаружения целей.

#### `attach_to_browser_target(session_id: str) -> Command[AttachToBrowserTargetResponse]`

Генерирует команду для подключения к цели браузера.

- `session_id`: ID сессии для подключения к цели браузера.
- **Возвращает**: Команду CDP для подключения к цели браузера, которая вернет новый ID сессии.

#### `get_target_info(target_id: str) -> Command[GetTargetInfoResponse]`

Генерирует команду для получения информации о конкретной цели.

- `target_id`: ID цели, о которой нужно получить информацию.
- **Возвращает**: Команду CDP для получения информации о цели, которая вернет объект `TargetInfo` с подробностями о цели.

#### `set_remote_locations(locations: list[RemoteLocation]) -> Command[Response]`

Генерирует команду для включения обнаружения целей для указанных удаленных местоположений.

- `locations`: Список удаленных местоположений, каждое из которых содержит хост и порт.
- **Возвращает**: Команду CDP для установки удаленных местоположений для обнаружения целей.
