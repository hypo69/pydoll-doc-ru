## Содержание

- [Модуль `pydoll.commands.storage_commands`](#модуль-pydollcommandsstorage_commands)
  - [Класс `StorageCommands`](#класс-storagecommands)
    - [Методы](#методы)
      - [`clear_cookies`](#clear_cookiesbrowser_context_id-optionalstr--none---commandresponse)
      - [`clear_data_for_origin`](#clear_data_for_originorigin-str-storage_types-str---commandresponse)
      - [`clear_data_for_storage_key`](#clear_data_for_storage_keystorage_key-str-storage_types-str---commandresponse)
      - [`get_cookies`](#get_cookiesbrowser_context_id-optionalstr--none---commandgetcookiesresponse)
      - [`get_storage_key_for_frame`](#get_storage_key_for_frameframe_id-str---commandgetstoragekeyforframeresponse)
      - [`get_usage_and_quota`](#get_usage_and_quotaorigin-str---commandgetusageandquotaresponse)
      - [`set_cookies`](#set_cookiescookies-listcookieparam-browser_context_id-optionalstr--none---commandresponse)
      - [`set_protected_audience_k_anonymity`](#set_protected_audience_k_anonymityowner-str-name-str-hashes-liststr---commandresponse)
      - [`track_cache_storage_for_origin`](#track_cache_storage_for_originorigin-str---commandresponse)
      - [`track_cache_storage_for_storage_key`](#track_cache_storage_for_storage_keystorage_key-str---commandresponse)
      - [`track_indexed_db_for_origin`](#track_indexed_db_for_originorigin-str---commandresponse)
      - [`track_indexed_db_for_storage_key`](#track_indexed_db_for_storage_keystorage_key-str---commandresponse)
      - [`untrack_cache_storage_for_origin`](#untrack_cache_storage_for_originorigin-str---commandresponse)
      - [`untrack_cache_storage_for_storage_key`](#untrack_cache_storage_for_storage_keystorage_key-str---commandresponse)
      - [`untrack_indexed_db_for_origin`](#untrack_indexed_db_for_originorigin-str---commandresponse)
      - [`untrack_indexed_db_for_storage_key`](#untrack_indexed_db_for_storage_keystorage_key-str---commandresponse)
      - [`clear_shared_storage_entries`](#clear_shared_storage_entriesowner_origin-str---commandresponse)
      - [`clear_trust_tokens`](#clear_trust_tokensissuer_origin-str---commandcleartrusttokensresponse)
      - [`delete_shared_storage_entry`](#delete_shared_storage_entryowner_origin-str-key-str---commandresponse)
      - [`delete_storage_bucket`](#delete_storage_bucketbucket-storagebucket---commandresponse)
      - [`get_affected_urls_for_third_party_cookie_metadata`](#get_affected_urls_for_third_party_cookie_metadatafirst_party_url-str-third_party_urls-liststr---commandgetaffectedurlsforthirdpartycookiemetadataresponse)
      - [`get_interest_group_details`](#get_interest_group_detailsowner_origin-str-name-str---commandgetinterestgroupdetailsresponse)
      - [`get_related_website_sets`](#get_related_website_setssets-listrelatedwebsiteset---commandgetrelatedwebsitesetsresponse)
      - [`get_shared_storage_entries`](#get_shared_storage_entriesowner_origin-str---commandgetsharedstorageentriesresponse)
      - [`get_shared_storage_metadata`](#get_shared_storage_metadataowner_origin-str---commandgetsharedstoragemetadataresponse)
      - [`get_trust_tokens`](#get_trust_tokens---commandgettrusttokensresponse)
      - [`override_quota_for_origin`](#override_quota_for_originorigin-str-quota_size-optionalfloat--none---commandresponse)
      - [`reset_shared_storage_budget`](#reset_shared_storage_budgetowner_origin-str---commandresponse)
      - [`run_bounce_tracking_mitigations`](#run_bounce_tracking_mitigations---commandrunbouncetrackingmitigationsresponse)
      - [`send_pending_attribution_reports`](#send_pending_attribution_reports---commandsendpendingattributionreportsresponse)
      - [`set_attribution_reporting_local_testing_mode`](#set_attribution_reporting_local_testing_modeenable-bool---commandresponse)
      - [`set_attribution_reporting_tracking`](#set_attribution_reporting_trackingenable-bool---commandresponse)
      - [`set_interest_group_auction_tracking`](#set_interest_group_auction_trackingenable-bool---commandresponse)
      - [`set_interest_group_tracking`](#set_interest_group_trackingenable-bool---commandresponse)
      - [`set_shared_storage_entry`](#set_shared_storage_entryowner_origin-str-key-str-value-str-ignore_if_present-optionalbool--none---commandresponse)
      - [`set_shared_storage_tracking`](#set_shared_storage_trackingenable-bool---commandresponse)
      - [`set_storage_bucket_tracking`](#set_storage_bucket_trackingstorage_key-str-enable-bool---commandresponse)

# Модуль `pydoll.commands.storage_commands`

Этот модуль содержит класс `StorageCommands`, который предоставляет набор команд для взаимодействия с различными типами хранилищ браузера с использованием Chrome DevTools Protocol (CDP).

## Класс `StorageCommands`

Предоставляет команды для взаимодействия с различными типами хранилищ браузера, включая:
- Cookies
- Cache Storage
- IndexedDB
- Web Storage (localStorage/sessionStorage)
- Shared Storage
- Trust Tokens
- Interest Groups
- Attribution Reporting

### Методы

#### `clear_cookies(browser_context_id: Optional[str] = None) -> Command[Response]`

Генерирует команду для очистки всех файлов cookie браузера.

- `browser_context_id`: Идентификатор контекста браузера (необязательно). Полезно при работе с несколькими контекстами (например, несколькими окнами или вкладками).
- **Возвращает**: Команду CDP для очистки всех файлов cookie.

#### `clear_data_for_origin(origin: str, storage_types: str) -> Command[Response]`

Генерирует команду для очистки данных хранилища для определенного источника.

- `origin`: Источник безопасности (например, "https://example.com").
- `storage_types`: Разделенный запятыми список типов хранилища для очистки. Возможные значения включают: "cookies", "local_storage", "indexeddb", "cache_storage" и т.д. Используйте "all" для очистки всех типов.
- **Возвращает**: Команду CDP для очистки данных для указанного источника.

#### `clear_data_for_storage_key(storage_key: str, storage_types: str) -> Command[Response]`

Генерирует команду для очистки данных для определенного ключа хранилища.

- `storage_key`: Ключ хранилища, для которого нужно очистить данные. В отличие от источника, ключ хранилища является более конкретным идентификатором, который может включать изоляцию разделов.
- `storage_types`: Разделенный запятыми список типов хранилища для очистки. Возможные значения включают: "cookies", "local_storage", "indexeddb", "cache_storage" и т.д. Используйте "all" для очистки всех типов.
- **Возвращает**: Команду CDP для очистки данных для указанного ключа хранилища.

#### `get_cookies(browser_context_id: Optional[str] = None) -> Command[GetCookiesResponse]`

Генерирует команду для получения всех файлов cookie браузера.

- `browser_context_id`: Идентификатор контекста браузера (необязательно). Полезно при работе с несколькими контекстами (например, несколькими окнами или вкладками).
- **Возвращает**: Команду CDP для получения всех файлов cookie, которая вернет массив объектов Cookie.

#### `get_storage_key_for_frame(frame_id: str) -> Command[GetStorageKeyForFrameResponse]`

Генерирует команду для получения ключа хранилища для определенного фрейма.

- `frame_id`: Идентификатор фрейма, для которого нужно получить ключ хранилища.
- **Возвращает**: Команду CDP для получения ключа хранилища для указанного фрейма.

#### `get_usage_and_quota(origin: str) -> Command[GetUsageAndQuotaResponse]`

Генерирует команду для получения информации об использовании хранилища и квоте для источника.

- `origin`: Источник безопасности (например, "https://example.com"), для которого нужно получить информацию.
- **Возвращает**: Команду CDP, которая вернет:
    - `usage`: Использование хранилища в байтах
    - `quota`: Квота хранилища в байтах
    - `usageBreakdown`: Разбивка использования по типу хранилища
    - `overrideActive`: Активно ли переопределение квоты

#### `set_cookies(cookies: list[CookieParam], browser_context_id: Optional[str] = None) -> Command[Response]`

Генерирует команду для установки файлов cookie браузера.

- `cookies`: Список объектов Cookie для установки.
- `browser_context_id`: Идентификатор контекста браузера (необязательно). Полезно при работе с несколькими контекстами (например, несколькими окнами или вкладками).
- **Возвращает**: Команду CDP для установки указанных файлов cookie.

#### `set_protected_audience_k_anonymity(owner: str, name: str, hashes: list[str]) -> Command[Response]`

Генерирует команду для установки K-анонимности для защищенной аудитории.

- `owner`: Владелец конфигурации K-анонимности.
- `name`: Имя конфигурации K-анонимности.
- `hashes`: Список хешей для конфигурации.
- **Возвращает**: Команду CDP для установки K-анонимности защищенной аудитории.

#### `track_cache_storage_for_origin(origin: str) -> Command[Response]`

Генерирует команду для регистрации источника для получения уведомлений об изменениях в его Cache Storage.

- `origin`: Источник безопасности (например, "https://example.com") для мониторинга.
- **Возвращает**: Команду CDP для регистрации мониторинга Cache Storage источника.

#### `track_cache_storage_for_storage_key(storage_key: str) -> Command[Response]`

Генерирует команду для регистрации ключа хранилища для получения уведомлений об изменениях в его Cache Storage.

- `storage_key`: Ключ хранилища для мониторинга.
- **Возвращает**: Команду CDP для регистрации мониторинга Cache Storage ключа.

#### `track_indexed_db_for_origin(origin: str) -> Command[Response]`

Генерирует команду для регистрации источника для получения уведомлений об изменениях в его IndexedDB.

- `origin`: Источник безопасности (например, "https://example.com") для мониторинга.
- **Возвращает**: Команду CDP для регистрации мониторинга IndexedDB источника.

#### `track_indexed_db_for_storage_key(storage_key: str) -> Command[Response]`

Генерирует команду для регистрации ключа хранилища для получения уведомлений об изменениях в его IndexedDB.

- `storage_key`: Ключ хранилища для мониторинга.
- **Возвращает**: Команду CDP для регистрации мониторинга IndexedDB ключа.

#### `untrack_cache_storage_for_origin(origin: str) -> Command[Response]`

Генерирует команду для отмены регистрации источника для получения уведомлений об изменениях в его Cache Storage.

- `origin`: Источник безопасности (например, "https://example.com") для прекращения мониторинга.
- **Возвращает**: Команду CDP для отмены мониторинга Cache Storage источника.

#### `untrack_cache_storage_for_storage_key(storage_key: str) -> Command[Response]`

Генерирует команду для отмены регистрации ключа хранилища для получения уведомлений об изменениях в его Cache Storage.

- `storage_key`: Ключ хранилища для прекращения мониторинга.
- **Возвращает**: Команду CDP для отмены мониторинга Cache Storage ключа.

#### `untrack_indexed_db_for_origin(origin: str) -> Command[Response]`

Генерирует команду для отмены регистрации источника для получения уведомлений об изменениях в его IndexedDB.

- `origin`: Источник безопасности (например, "https://example.com") для прекращения мониторинга.
- **Возвращает**: Команду CDP для отмены мониторинга IndexedDB источника.

#### `untrack_indexed_db_for_storage_key(storage_key: str) -> Command[Response]`

Генерирует команду для отмены регистрации ключа хранилища для получения уведомлений об изменениях в его IndexedDB.

- `storage_key`: Ключ хранилища для прекращения мониторинга.
- **Возвращает**: Команду CDP для отмены мониторинга IndexedDB ключа.

#### `clear_shared_storage_entries(owner_origin: str) -> Command[Response]`

Генерирует команду для очистки всех записей Shared Storage для определенного источника.

- `owner_origin`: Источник-владелец Shared Storage для очистки.
- **Возвращает**: Команду CDP для очистки записей Shared Storage.

#### `clear_trust_tokens(issuer_origin: str) -> Command[ClearTrustTokensResponse]`

Генерирует команду для удаления всех Trust Tokens, выпущенных указанным источником.

- `issuer_origin`: Источник-эмитент токенов для удаления.
- **Возвращает**: Команду CDP для очистки Trust Tokens, которая вернет:
    - `didDeleteTokens`: `True`, если какие-либо токены были удалены, иначе `False`.

#### `delete_shared_storage_entry(owner_origin: str, key: str) -> Command[Response]`

Генерирует команду для удаления определенной записи Shared Storage.

- `owner_origin`: Источник-владелец Shared Storage.
- `key`: Ключ записи для удаления.
- **Возвращает**: Команду CDP для удаления записи Shared Storage.

#### `delete_storage_bucket(bucket: StorageBucket) -> Command[Response]`

Генерирует команду для удаления Storage Bucket с указанным ключом и именем.

- `bucket`: Объект `StorageBucket`, содержащий `storageKey` и имя корзины для удаления.
- **Возвращает**: Команду CDP для удаления Storage Bucket.

#### `get_affected_urls_for_third_party_cookie_metadata(first_party_url: str, third_party_urls: list[str]) -> Command[GetAffectedUrlsForThirdPartyCookieMetadataResponse]`

Генерирует команду для получения списка URL-адресов со страницы и ее встроенных ресурсов, которые соответствуют существующим правилам URL-шаблонов льготного периода.

- `first_party_url`: URL-адрес посещаемой страницы (первая сторона).
- `third_party_urls`: Необязательный список URL-адресов встроенных сторонних ресурсов.
- **Возвращает**: Команду CDP для получения URL-адресов, затронутых метаданными сторонних файлов cookie.

#### `get_interest_group_details(owner_origin: str, name: str) -> Command[GetInterestGroupDetailsResponse]`

Генерирует команду для получения сведений о конкретной группе интересов.

- `owner_origin`: Источник-владелец группы интересов.
- `name`: Имя группы интересов.
- **Возвращает**: Команду CDP для получения сведений о группе интересов.

#### `get_related_website_sets(sets: list[RelatedWebsiteSet]) -> Command[GetRelatedWebsiteSetsResponse]`

Генерирует команду для получения связанных наборов веб-сайтов.

- `sets`: Список объектов `RelatedWebsiteSet`.
- **Возвращает**: Команду CDP для получения связанных наборов веб-сайтов.

#### `get_shared_storage_entries(owner_origin: str) -> Command[GetSharedStorageEntriesResponse]`

Генерирует команду для получения всех записей Shared Storage для источника.

- `owner_origin`: Источник-владелец Shared Storage.
- **Возвращает**: Команду CDP для получения записей Shared Storage.

#### `get_shared_storage_metadata(owner_origin: str) -> Command[GetSharedStorageMetadataResponse]`

Генерирует команду для получения метаданных Shared Storage для источника.

- `owner_origin`: Источник-владелец Shared Storage.
- **Возвращает**: Команду CDP для получения метаданных Shared Storage.

#### `get_trust_tokens() -> Command[GetTrustTokensResponse]`

Генерирует команду для получения всех доступных Trust Tokens.

- **Возвращает**: Команду CDP для получения Trust Tokens, которая вернет пары источника-эмитента и количества доступных токенов.

#### `override_quota_for_origin(origin: str, quota_size: Optional[float] = None) -> Command[Response]`

Генерирует команду для переопределения квоты хранилища для определенного источника.

- `origin`: Источник, для которого нужно переопределить квоту.
- `quota_size`: Размер новой квоты в байтах (необязательно). Если не указан, любое существующее переопределение будет удалено.
- **Возвращает**: Команду CDP для переопределения квоты источника.

#### `reset_shared_storage_budget(owner_origin: str) -> Command[Response]`

Генерирует команду для сброса бюджета Shared Storage для источника.

- `owner_origin`: Источник-владелец Shared Storage.
- **Возвращает**: Команду CDP для сброса бюджета Shared Storage.

#### `run_bounce_tracking_mitigations() -> Command[RunBounceTrackingMitigationsResponse]`

Генерирует команду для запуска мер по смягчению последствий отслеживания переходов.

- **Возвращает**: Команду CDP для запуска мер по смягчению последствий отслеживания переходов.

#### `send_pending_attribution_reports() -> Command[SendPendingAttributionReportsResponse]`

Генерирует команду для отправки ожидающих отчетов об атрибуции.

- **Возвращает**: Команду CDP для отправки ожидающих отчетов об атрибуции.

#### `set_attribution_reporting_local_testing_mode(enable: bool) -> Command[Response]`

Генерирует команду для включения или отключения режима локального тестирования для Attribution Reporting.

- `enable`: `True` для включения режима локального тестирования, `False` для отключения.
- **Возвращает**: Команду CDP для установки режима локального тестирования Attribution Reporting.

#### `set_attribution_reporting_tracking(enable: bool) -> Command[Response]`

Генерирует команду для включения или отключения отслеживания Attribution Reporting.

- `enable`: `True` для включения отслеживания, `False` для отключения.
- **Возвращает**: Команду CDP для установки отслеживания Attribution Reporting.

#### `set_interest_group_auction_tracking(enable: bool) -> Command[Response]`

Генерирует команду для включения или отключения отслеживания аукционов групп интересов.

- `enable`: `True` для включения отслеживания, `False` для отключения.
- **Возвращает**: Команду CDP для установки отслеживания аукционов групп интересов.

#### `set_interest_group_tracking(enable: bool) -> Command[Response]`

Генерирует команду для включения или отключения отслеживания групп интересов.

- `enable`: `True` для включения отслеживания, `False` для отключения.
- **Возвращает**: Команду CDP для установки отслеживания групп интересов.

#### `set_shared_storage_entry(owner_origin: str, key: str, value: str, ignore_if_present: Optional[bool] = None) -> Command[Response]`

Генерирует команду для установки записи в Shared Storage.

- `owner_origin`: Источник-владелец Shared Storage.
- `key`: Ключ записи для установки.
- `value`: Значение записи для установки.
- `ignore_if_present`: Если `True`, не будет заменять существующую запись с тем же ключом.
- **Возвращает**: Команду CDP для установки записи Shared Storage.

#### `set_shared_storage_tracking(enable: bool) -> Command[Response]`

Генерирует команду для включения или отключения отслеживания Shared Storage.

- `enable`: `True` для включения отслеживания, `False` для отключения.
- **Возвращает**: Команду CDP для установки отслеживания Shared Storage.

#### `set_storage_bucket_tracking(storage_key: str, enable: bool) -> Command[Response]`

Генерирует команду для включения или отключения отслеживания Storage Bucket.

- `storage_key`: Ключ хранилища, для которого нужно установить отслеживание.
- `enable`: `True` для включения отслеживания, `False` для отключения.
- **Возвращает**: Команду CDP для установки отслеживания Storage Bucket.
