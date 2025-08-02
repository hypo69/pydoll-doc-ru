## Содержание

- [Модуль `pydoll.commands.network_commands`](#модуль-pydollcommandsnetwork_commands)
  - [Класс `NetworkCommands`](#класс-networkcommands)
    - [Методы](#методы)
      - [`clear_browser_cache`](#clear_browser_cache---commandresponse)
      - [`clear_browser_cookies`](#clear_browser_cookies---commandresponse)
      - [`delete_cookies`](#delete_cookiesname-str-url-optionalstr--none-domain-optionalstr--none-path-optionalstr--none-partition_key-optionalcookiepartitionkey--none---commandresponse)
      - [`disable`](#disable---commandresponse)
      - [`enable`](#enablemax_total_buffer_size-optionalint--none-max_resource_buffer_size-optionalint--none-max_post_data_size-optionalint--none---commandresponse)
      - [`get_cookies`](#get_cookiesurls-optionalliststr--none---commandgetcookiesresponse)
      - [`get_request_post_data`](#get_request_post_datarequest_id-str---commandgetrequestpostdataresponse)
      - [`get_response_body`](#get_response_bodyrequest_id-str---commandgetresponsebodyresponse)
      - [`set_cache_disabled`](#set_cache_disabledcache_disabled-bool---commandresponse)
      - [`set_cookie`](#set_cookiename-str-value-str-url-optionalstr--none-domain-optionalstr--none-path-optionalstr--none-secure-optionalbool--none-http_only-optionalbool--none-same_site-optionalcookiesamesite--none-expires-optionalfloat--none-priority-optionalcookiepriority--none-same_party-optionalbool--none-source_scheme-optionalcookiesourcescheme--none-source_port-optionalint--none-partition_key-optionalcookiepartitionkey--none---commandsetcookieresponse)
      - [`set_cookies`](#set_cookiescookies-listsetcookieparams---commandresponse)
      - [`set_extra_http_headers`](#set_extra_http_headersheaders-listheaderentry---commandresponse)
      - [`set_useragent_override`](#set_useragent_overrideuser_agent-str-accept_language-optionalstr--none-platform-optionalstr--none-user_agent_metadata-optionaluseragentmetadata--none---commandresponse)
      - [`clear_accepted_encodings_override`](#clear_accepted_encodings_override---commandresponse)
      - [`enable_reporting_api`](#enable_reporting_apienabled-bool---commandresponse)
      - [`search_in_response_body`](#search_in_response_bodyrequest_id-str-query-str-case_sensitive-bool--false-is_regex-bool--false---commandsearchinresponsebodyresponse)
      - [`set_blocked_urls`](#set_blocked_urlsurls-liststr---commandresponse)
      - [`set_bypass_service_worker`](#set_bypass_service_workerbypass-bool---commandresponse)
      - [`get_certificate`](#get_certificateorigin-str---commandgetcertificateresponse)
      - [`get_response_body_for_interception`](#get_response_body_for_interceptioninterception_id-str---commandgetresponsebodyforinterceptionresponse)
      - [`set_accepted_encodings`](#set_accepted_encodingsencodings-listcontentencoding---commandresponse)
      - [`set_attach_debug_stack`](#set_attach_debug_stackenabled-bool---commandresponse)
      - [`set_cookie_controls`](#set_cookie_controlsenable_third_party_cookie_restriction-bool-disable_third_party_cookie_metadata-optionalbool--none-disable_third_party_cookie_heuristics-optionalbool--none---commandresponse)
      - [`stream_resource_content`](#stream_resource_contentrequest_id-str---commandstreamresourcecontentresponse)
      - [`take_response_body_for_interception_as_stream`](#take_response_body_for_interception_as_streaminterception_id-str---commandtakeresponsebodyforinterceptionasstreamresponse)
      - [`emulate_network_conditions`](#emulate_network_conditionsoffline-bool-latency-float-download_throughput-float-upload_throughput-float-connection_type-optionalconnectiontype--none-packet_loss-optionalfloat--none-packet_queue_length-optionalint--none-packet_reordering-optionalbool--none---commandresponse)
      - [`get_security_isolation_status`](#get_security_isolation_statusframe_id-optionalstr--none---commandgetsecurityisolationstatusresponse)
      - [`load_network_resource`](#load_network_resourceurl-str-options-loadnetworkresourceoptions-frame_id-optionalstr--none---commandloadnetworkresourceresponse)
      - [`replay_xhr`](#replay_xhrrequest_id-str---commandresponse)

# Модуль `pydoll.commands.network_commands`

Этот модуль реализует команды Chrome DevTools Protocol (CDP) для домена `Network`. Он предоставляет команды для мониторинга и манипулирования сетевой активностью, обеспечивая детальный контроль над HTTP-запросами и ответами.

## Класс `NetworkCommands`

Предоставляет команды для мониторинга и манипулирования сетевой активностью.

### Методы

#### `clear_browser_cache() -> Command[Response]`

Очищает кэш браузера.

- **Возвращает**: Команду CDP для очистки всего кэша браузера.

#### `clear_browser_cookies() -> Command[Response]`

Очищает все файлы cookie, хранящиеся в браузере.

- **Возвращает**: Команду для очистки всех файлов cookie в браузере.

#### `delete_cookies(name: str, url: Optional[str] = None, domain: Optional[str] = None, path: Optional[str] = None, partition_key: Optional[CookiePartitionKey] = None) -> Command[Response]`

Удаляет файлы cookie браузера, соответствующие заданным критериям.

- `name`: Имя файлов cookie для удаления (обязательно).
- `url`: Удалить файлы cookie для определенного URL (домен/путь должны совпадать).
- `domain`: Точный домен для удаления файлов cookie.
- `path`: Точный путь для удаления файлов cookie.
- `partition_key`: Атрибуты ключа раздела для изоляции файлов cookie.
- **Возвращает**: Команду CDP для выполнения выборочного удаления файлов cookie.

#### `disable() -> Command[Response]`

Останавливает мониторинг сети и отчетность о событиях.

- **Возвращает**: Команду CDP для отключения мониторинга сети.

#### `enable(max_total_buffer_size: Optional[int] = None, max_resource_buffer_size: Optional[int] = None, max_post_data_size: Optional[int] = None) -> Command[Response]`

Включает мониторинг сети с настраиваемыми буферами.

- `max_total_buffer_size`: Общий буфер памяти для сетевых данных (байты).
- `max_resource_buffer_size`: Ограничение буфера на ресурс (байты).
- `max_post_data_size`: Максимальный размер POST-данных для захвата (байты).
- **Возвращает**: Команду CDP для включения мониторинга сети.

#### `get_cookies(urls: Optional[list[str]] = None) -> Command[GetCookiesResponse]`

Извлекает файлы cookie, соответствующие указанным URL-ададресам.

- `urls`: Список URL-адресов для определения области получения файлов cookie.
- **Возвращает**: Команду CDP, возвращающую сведения о файлах cookie.

#### `get_request_post_data(request_id: str) -> Command[GetRequestPostDataResponse]`

Извлекает POST-данные из конкретного сетевого запроса.

- `request_id`: Уникальный идентификатор сетевого запроса.
- **Возвращает**: Команду CDP, которая возвращает необработанные POST-данные.

#### `get_response_body(request_id: str) -> Command[GetResponseBodyResponse]`

Извлекает полное содержимое сетевого ответа.

- `request_id`: Уникальный идентификатор сетевого запроса.
- **Возвращает**: Команду CDP, возвращающую тело ответа и сведения о кодировке.

#### `set_cache_disabled(cache_disabled: bool) -> Command[Response]`

Управляет механизмом кэширования браузера.

- `cache_disabled`: `True` для отключения кэширования, `False` для включения.
- **Возвращает**: Команду CDP для изменения поведения кэша.

#### `set_cookie(name: str, value: str, url: Optional[str] = None, domain: Optional[str] = None, path: Optional[str] = None, secure: Optional[bool] = None, http_only: Optional[bool] = None, same_site: Optional[CookieSameSite] = None, expires: Optional[float] = None, priority: Optional[CookiePriority] = None, same_party: Optional[bool] = None, source_scheme: Optional[CookieSourceScheme] = None, source_port: Optional[int] = None, partition_key: Optional[CookiePartitionKey] = None) -> Command[SetCookieResponse]`

Создает или обновляет файл cookie с указанными атрибутами.

- `name`: Имя файла cookie.
- `value`: Значение файла cookie.
- `url`: Целевой URL для файла cookie.
- `domain`: Область действия домена файла cookie.
- `path`: Область действия пути файла cookie.
- `secure`: Требовать HTTPS.
- `http_only`: Запретить доступ JavaScript.
- `same_site`: Политика доступа между сайтами.
- `expires`: Метка времени истечения срока действия.
- `priority`: Уровень приоритета файла cookie.
- `same_party`: Флаг First-Party Sets.
- `source_scheme`: Контекст источника файла cookie.
- `source_port`: Ограничение порта источника.
- `partition_key`: Ключ раздела хранилища.
- **Возвращает**: Команду CDP, которая возвращает статус успеха.

#### `set_cookies(cookies: list[SetCookieParams]) -> Command[Response]`

Устанавливает несколько файлов cookie за одну операцию.

- `cookies`: Список параметров файлов cookie, включая имя, значение и атрибуты.
- **Возвращает**: Команду CDP для массовой установки файлов cookie.

#### `set_extra_http_headers(headers: list[HeaderEntry]) -> Command[Response]`

Применяет пользовательские HTTP-заголовки ко всем последующим запросам.

- `headers`: Список пар ключ-значение заголовков.
- **Возвращает**: Команду CDP для установки глобальных HTTP-заголовков.

#### `set_useragent_override(user_agent: str, accept_language: Optional[str] = None, platform: Optional[str] = None, user_agent_metadata: Optional[UserAgentMetadata] = None) -> Command[Response]`

Переопределяет строку User-Agent браузера.

- `user_agent`: Полная строка User-Agent.
- `accept_language`: Заголовок предпочтения языка.
- `platform`: Идентификатор платформы.
- `user_agent_metadata`: Подробные метаданные User-Agent.
- **Возвращает**: Команду CDP для переопределения User-Agent.

#### `clear_accepted_encodings_override() -> Command[Response]`

Восстанавливает принятые по умолчанию кодировки контента.

- **Возвращает**: Команду CDP для очистки переопределений кодировок.

#### `enable_reporting_api(enabled: bool) -> Command[Response]`

Управляет функциональностью Reporting API.

- `enabled`: `True` для включения, `False` для отключения.
- **Возвращает**: Команду CDP для настройки Reporting API.

#### `search_in_response_body(request_id: str, query: str, case_sensitive: bool = False, is_regex: bool = False) -> Command[SearchInResponseBodyResponse]`

Ищет содержимое в телах ответов.

- `request_id`: Идентификатор целевого ответа.
- `query`: Строка поиска или шаблон.
- `case_sensitive`: Учитывать регистр.
- `is_regex`: Использовать регулярные выражения.
- **Возвращает**: Команду CDP, возвращающую результаты совпадений.

#### `set_blocked_urls(urls: list[str]) -> Command[Response]`

Блокирует загрузку указанных URL-адресов.

- `urls`: Список шаблонов URL-адресов для блокировки.
- **Возвращает**: Команду CDP для установки правил блокировки URL-адресов.

#### `set_bypass_service_worker(bypass: bool) -> Command[Response]`

Управляет перехватом сетевых запросов Service Worker.

- `bypass`: `True` для пропуска Service Worker, `False` для разрешения.
- **Возвращает**: Команду CDP для настройки поведения Service Worker.

#### `get_certificate(origin: str) -> Command[GetCertificateResponse]`

Извлекает информацию о SSL/TLS-сертификате для домена.

- `origin`: Целевой домен для проверки сертификата.
- **Возвращает**: Команду CDP, возвращающую данные сертификата.

#### `get_response_body_for_interception(interception_id: str) -> Command[GetResponseBodyForInterceptionResponse]`

Извлекает тело ответа из перехваченного запроса.

- `interception_id`: Идентификатор перехваченного запроса.
- **Возвращает**: Команду CDP, предоставляющую содержимое перехваченного ответа.

#### `set_accepted_encodings(encodings: list[ContentEncoding]) -> Command[Response]`

Указывает принятые кодировки контента для запросов.

- `encodings`: Список принятых методов кодирования (gzip, deflate, br и т.д.).
- **Возвращает**: Команду CDP для установки предпочтений кодирования.

#### `set_attach_debug_stack(enabled: bool) -> Command[Response]`

Включает/отключает прикрепление отладочного стека к запросам.

- `enabled`: `True` для прикрепления отладочной информации, `False` для отключения.
- **Возвращает**: Команду CDP для настройки прикрепления отладочного стека.

#### `set_cookie_controls(enable_third_party_cookie_restriction: bool, disable_third_party_cookie_metadata: Optional[bool] = None, disable_third_party_cookie_heuristics: Optional[bool] = None) -> Command[Response]`

Настраивает политики обработки сторонних файлов cookie.

- `enable_third_party_cookie_restriction`: Включить ограничения.
- `disable_third_party_cookie_metadata`: Пропускать проверки метаданных.
- `disable_third_party_cookie_heuristics`: Отключить логику обнаружения.
- **Возвращает**: Команду CDP для установки политик управления файлами cookie.

#### `stream_resource_content(request_id: str) -> Command[StreamResourceContentResponse]`

Включает потоковую передачу содержимого ответа.

- `request_id`: Идентификатор целевого запроса.
- **Возвращает**: Команду CDP для инициации потоковой передачи содержимого.

#### `take_response_body_for_interception_as_stream(interception_id: str) -> Command[TakeResponseBodyForInterceptionAsStreamResponse]`

Создает поток для перехваченного тела ответа.

- `interception_id`: Идентификатор перехваченного ответа.
- **Возвращает**: Команду CDP, возвращающую дескриптор потока.

#### `emulate_network_conditions(offline: bool, latency: float, download_throughput: float, upload_throughput: float, connection_type: Optional[ConnectionType] = None, packet_loss: Optional[float] = None, packet_queue_length: Optional[int] = None, packet_reordering: Optional[bool] = None) -> Command[Response]`

Эмулирует пользовательские сетевые условия для реалистичных сценариев тестирования.

- `offline`: Имитировать полное отключение сети.
- `latency`: Минимальная задержка в миллисекундах (время кругового пути).
- `download_throughput`: Максимальная скорость загрузки (байты/сек, -1 для отключения).
- `upload_throughput`: Максимальная скорость загрузки (байты/сек, -1 для отключения).
- `connection_type`: Тип сетевого соединения (сотовая связь, Wi-Fi и т.д.).
- `packet_loss`: Имитируемый процент потери пакетов (0-100).
- `packet_queue_length`: Имитация размера сетевого буфера.
- `packet_reordering`: Включить рандомизацию порядка пакетов.
- **Возвращает**: Команду CDP для активации эмуляции сети.

#### `get_security_isolation_status(frame_id: Optional[str] = None) -> Command[GetSecurityIsolationStatusResponse]`

Извлекает информацию об изоляции безопасности.

- `frame_id`: Необязательный фрейм для проверки.
- **Возвращает**: Команду CDP, возвращающую статус изоляции.

#### `load_network_resource(url: str, options: LoadNetworkResourceOptions, frame_id: Optional[str] = None) -> Command[LoadNetworkResourceResponse]`

Загружает сетевой ресурс с определенными опциями.

- `url`: URL ресурса для загрузки.
- `options`: Конфигурация загрузки.
- `frame_id`: Контекст целевого фрейма.
- **Возвращает**: Команду CDP для загрузки ресурса.

#### `replay_xhr(request_id: str) -> Command[Response]`

Повторяет XHR-запрос.

- `request_id`: XHR-запрос для повтора.
- **Возвращает**: Команду CDP для повтора XHR.
