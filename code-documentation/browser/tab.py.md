## Содержание

- [Модуль `pydoll.browser.tab`](#модуль-pydollbrowsertab)
  - [Класс `Tab`](#класс-tab)
    - [Свойства](#свойства)
    - [Методы](#методы)
      - [`__new__`](#__new__cls-browser-connection_port-target_id-browser_context_idnone)
      - [`__init__`](#__init__self-browser-connection_port-target_id-browser_context_idnone)
      - [`_remove_instance`](#_remove_instancecls-target_id)
      - [`get_instance`](#get_instancecls-target_id)
      - [`get_all_instances`](#get_all_instancescls)
      - [`enable_page_events`](#enable_page_eventsself)
      - [`enable_network_events`](#enable_network_eventsself)
      - [`enable_fetch_events`](#enable_fetch_eventsself-handle_authfalse-resource_typenone-request_stagenone)
      - [`enable_dom_events`](#enable_dom_eventsself)
      - [`enable_runtime_events`](#enable_runtime_eventsself)
      - [`enable_intercept_file_chooser_dialog`](#enable_intercept_file_chooser_dialogself)
      - [`enable_auto_solve_cloudflare_captcha`](#enable_auto_solve_cloudflare_captchaself-custom_selectornone-time_before_click2-time_to_wait_captcha5)
      - [`disable_fetch_events`](#disable_fetch_eventsself)
      - [`disable_page_events`](#disable_page_eventsself)
      - [`disable_network_events`](#disable_network_eventsself)
      - [`disable_dom_events`](#disable_dom_eventsself)
      - [`disable_runtime_events`](#disable_runtime_eventsself)
      - [`disable_intercept_file_chooser_dialog`](#disable_intercept_file_chooser_dialogself)
      - [`disable_auto_solve_cloudflare_captcha`](#disable_auto_solve_cloudflare_captchaself)
      - [`close`](#closeself)
      - [`get_frame`](#get_frameself-frame)
      - [`get_cookies`](#get_cookiesself)
      - [`get_network_response_body`](#get_network_response_bodyself-request_id)
      - [`get_network_logs`](#get_network_logsself-filternone)
      - [`set_cookies`](#set_cookiesself-cookies)
      - [`delete_all_cookies`](#delete_all_cookiesself)
      - [`go_to`](#go_toself-url-timeout300)
      - [`refresh`](#refreshself-ignore_cachefalse-script_to_evaluate_on_loadnone)
      - [`take_screenshot`](#take_screenshotself-pathnone-quality100-as_base64false)
      - [`print_to_pdf`](#print_to_pdfself-path-landscapefalse-display_header_footerfalse-print_backgroundtrue-scale10-as_base64false)
      - [`has_dialog`](#has_dialogself)
      - [`get_dialog_message`](#get_dialog_messageself)
      - [`handle_dialog`](#handle_dialogself-accept-prompt_textnone)
      - [`execute_script`](#execute_scriptself-script-elementnone)
      - [`continue_request`](#continue_requestself-request_id-urlnone-methodnone-post_datanone-headersnone-intercept_responsenone)
      - [`fail_request`](#fail_requestself-request_id-error_reason)
      - [`fulfill_request`](#fulfill_requestself-request_id-response_code-response_headersnone-bodynone-response_phrasenone)
      - [`on`](#onself-event_name-callback-temporaryfalse)
    - [Контекстные менеджеры](#контекстные-менеджеры)
      - [`expect_file_chooser`](#expect_file_chooserself-files)
      - [`expect_and_bypass_cloudflare_captcha`](#expect_and_bypass_cloudflare_captchaself-custom_selectornone-time_before_click2-time_to_wait_captcha5)

# Модуль `pydoll.browser.tab`

Этот модуль содержит класс `Tab`, который предоставляет основной интерфейс для автоматизации веб-страниц через Chrome DevTools Protocol (CDP). Он позволяет управлять навигацией, манипулировать DOM, выполнять JavaScript, обрабатывать события, отслеживать сеть и выполнять специализированные задачи, такие как обход Cloudflare.

Класс `Tab` реализует шаблон Singleton на основе `target_id`, чтобы гарантировать существование только одного экземпляра `Tab` для каждой вкладки браузера.

## Класс `Tab`

Управляет вкладкой браузера через Chrome DevTools Protocol.

### Свойства

- `page_events_enabled` (bool): Указывает, включены ли события домена CDP Page.
- `network_events_enabled` (bool): Указывает, включены ли события домена CDP Network.
- `fetch_events_enabled` (bool): Указывает, включены ли события домена CDP Fetch (перехват запросов).
- `dom_events_enabled` (bool): Указывает, включены ли события домена CDP DOM.
- `runtime_events_enabled` (bool): Указывает, включены ли события домена CDP Runtime.
- `intercept_file_chooser_dialog_enabled` (bool): Указывает, активен ли перехват диалога выбора файла.
- `current_url` (str): Текущий URL страницы (отражает перенаправления и навигацию на стороне клиента).
- `page_source` (str): Полный HTML-источник текущей страницы (состояние живого DOM).

### Методы

#### `__new__(cls, browser, connection_port, target_id, browser_context_id=None)`

Создает или возвращает существующий экземпляр `Tab` для данного `target_id`.

- `browser`: Экземпляр `Browser`, который создал эту вкладку.
- `connection_port`: Порт WebSocket CDP.
- `target_id`: Идентификатор цели CDP для этой вкладки.
- `browser_context_id`: Необязательный идентификатор контекста браузера.
- **Возвращает**: Экземпляр `Tab` (новый или существующий) для `target_id`.

#### `__init__(self, browser, connection_port, target_id, browser_context_id=None)`

Инициализирует контроллер вкладки для существующей вкладки браузера.

#### `_remove_instance(cls, target_id)`

Удаляет экземпляр из реестра при закрытии вкладки.

#### `get_instance(cls, target_id)`

Получает существующий экземпляр `Tab` для `target_id`, если он существует.

#### `get_all_instances(cls)`

Получает все активные экземпляры `Tab`.

#### `enable_page_events(self)`

Включает события домена CDP Page (загрузка, навигация, диалоги и т.д.).

#### `enable_network_events(self)`

Включает события домена CDP Network (запросы, ответы и т.д.).

#### `enable_fetch_events(self, handle_auth=False, resource_type=None, request_stage=None)`

Включает домен CDP Fetch для перехвата запросов.

#### `enable_dom_events(self)`

Включает события домена CDP DOM (изменения структуры документа).

#### `enable_runtime_events(self)`

Включает события домена CDP Runtime.

#### `enable_intercept_file_chooser_dialog(self)`

Включает перехват диалога выбора файла для автоматической загрузки.

#### `enable_auto_solve_cloudflare_captcha(self, custom_selector=None, time_before_click=2, time_to_wait_captcha=5)`

Включает автоматический обход капчи Cloudflare Turnstile.

#### `disable_fetch_events(self)`

Отключает домен CDP Fetch и освобождает приостановленные запросы.

#### `disable_page_events(self)`

Отключает события домена CDP Page.

#### `disable_network_events(self)`

Отключает события домена CDP Network.

#### `disable_dom_events(self)`

Отключает события домена CDP DOM.

#### `disable_runtime_events(self)`

Отключает события домена CDP Runtime.

#### `disable_intercept_file_chooser_dialog(self)`

Отключает перехват диалога выбора файла.

#### `disable_auto_solve_cloudflare_captcha(self)`

Отключает автоматический обход капчи Cloudflare Turnstile.

#### `close(self)`

Закрывает эту вкладку браузера.

#### `get_frame(self, frame)`

Получает объект `Tab` для взаимодействия с содержимым iframe.

#### `get_cookies(self)`

Получает все файлы cookie, доступные с текущей страницы.

#### `get_network_response_body(self, request_id)`

Получает тело ответа для данного идентификатора запроса.

#### `get_network_logs(self, filter=None)`

Получает сетевые журналы.

#### `set_cookies(self, cookies)`

Устанавливает несколько файлов cookie для текущей страницы.

#### `delete_all_cookies(self)`

Удаляет все файлы cookie из текущего контекста браузера.

#### `go_to(self, url, timeout=300)`

Переходит по URL и ожидает завершения загрузки.

#### `refresh(self, ignore_cache=False, script_to_evaluate_on_load=None)`

Перезагружает текущую страницу и ожидает завершения.

#### `take_screenshot(self, path=None, quality=100, as_base64=False)`

Делает скриншот текущей страницы.

#### `print_to_pdf(self, path, landscape=False, display_header_footer=False, print_background=True, scale=1.0, as_base64=False)`

Генерирует PDF текущей страницы.

#### `has_dialog(self)`

Проверяет, отображается ли в данный момент диалог JavaScript.

#### `get_dialog_message(self)`

Получает текст сообщения из текущего диалога JavaScript.

#### `handle_dialog(self, accept, prompt_text=None)`

Отвечает на диалог JavaScript.

#### `execute_script(self, script, element=None)`

Выполняет JavaScript в контексте страницы.

#### `continue_request(self, request_id, url=None, method=None, post_data=None, headers=None, intercept_response=None)`

Продолжает приостановленный запрос без изменений.

#### `fail_request(self, request_id, error_reason)`

Завершает запрос с кодом ошибки.

#### `fulfill_request(self, request_id, response_code, response_headers=None, body=None, response_phrase=None)`

Выполняет запрос с данными ответа.

#### `on(self, event_name, callback, temporary=False)`

Регистрирует прослушиватель событий CDP.

### Контекстные менеджеры

#### `expect_file_chooser(self, files)`

Контекстный менеджер для автоматической обработки загрузки файлов.

#### `expect_and_bypass_cloudflare_captcha(self, custom_selector=None, time_before_click=2, time_to_wait_captcha=5)`

Контекстный менеджер для автоматического обхода капчи Cloudflare.