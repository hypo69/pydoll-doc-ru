## Содержание

- [Модуль `pydoll.constants`](#модуль-pydollconstants)
  - [Перечисления](#перечисления)
    - [`By(str, Enum)`](#bystr-enum)
    - [`Scripts`](#scripts)
    - [`Key(tuple[str, int], Enum)`](#keytuplestr-int-enum)
    - [`BrowserType(Enum)`](#browsertypeenum)
    - [`WindowState(str, Enum)`](#windowstatestr-enum)
    - [`DownloadBehavior(str, Enum)`](#downloadbehaviorstr-enum)
    - [`PermissionType(str, Enum)`](#permissiontypestr-enum)
    - [`RequestMethod(str, Enum)`](#requestmethodstr-enum)
    - [`AuthChallengeResponseValues(str, Enum)`](#authchallengeresponsevaluesstr-enum)
    - [`ResourceType(str, Enum)`](#resourcetypestr-enum)
    - [`RequestStage(str, Enum)`](#requeststagestr-enum)
    - [`NetworkErrorReason(str, Enum)`](#networkerrorreasonstr-enum)
    - [`CookiePriority(str, Enum)`](#cookieprioritystr-enum)
    - [`CookieSourceScheme(str, Enum)`](#cookiesourceschemestr-enum)
    - [`CookieSameSite(str, Enum)`](#cookiesamesitestr-enum)
    - [`ConnectionType(str, Enum)`](#connectiontypestr-enum)
    - [`ContentEncoding(str, Enum)`](#contentencodingstr-enum)
    - [`ScreenshotFormat(str, Enum)`](#screenshotformatstr-enum)
    - [`TransitionType(str, Enum)`](#transitiontypestr-enum)
    - [`ReferrerPolicy(str, Enum)`](#referrerpolicystr-enum)
    - [`TransferMode(str, Enum)`](#transfermodestr-enum)
    - [`AutoResponseMode(str, Enum)`](#autoresponsemodestr-enum)
    - [`WebLifecycleState(str, Enum)`](#weblifecyclestatestr-enum)
    - [`ScreencastFormat(str, Enum)`](#screencastformatstr-enum)
    - [`OriginTrialStatus(str, Enum)`](#origintrialstatusstr-enum)
    - [`OriginTrialUsageRestriction(str, Enum)`](#origintrialusagerestrictionstr-enum)
    - [`OriginTrialTokenStatus(str, Enum)`](#origintrialtokenstatusstr-enum)
    - [`PermissionsPolicyBlockReason(str, Enum)`](#permissionspolicyblockreasonstr-enum)
    - [`PermissionsPolicyFeature(str, Enum)`](#permissionspolicyfeaturestr-enum)
    - [`CrossOriginOpenerPolicyStatus(str, Enum)`](#crossoriginopenerpolicystatusstr-enum)
    - [`CrossOriginEmbedderPolicyStatus(str, Enum)`](#crossoriginembedderpolicystatusstr-enum)
    - [`ContentSecurityPolicySource(str, Enum)`](#contentsecuritypolicysourcestr-enum)
    - [`UnserializableEnum(str, Enum)`](#unserializableenumstr-enum)
    - [`SerializationValue(str, Enum)`](#serializationvaluestr-enum)
    - [`RemoteObjectType(str, Enum)`](#remoteobjecttypestr-enum)
    - [`RemoteObjectSubtype(str, Enum)`](#remoteobjectsubtypestr-enum)
    - [`DeepSerializedValueType(str, Enum)`](#deepserializedvaluetypestr-enum)
    - [`ObjectPreviewType(str, Enum)`](#objectpreviewtypestr-enum)
    - [`ObjectPreviewSubtype(str, Enum)`](#objectpreviewsubtypestr-enum)
    - [`PropertyPreviewType(str, Enum)`](#propertypreviewtypestr-enum)
    - [`PropertyPreviewSubtype(str, Enum)`](#propertypreviewsubtypestr-enum)
    - [`StorageBucketDurability(str, Enum)`](#storagebucketdurabilitystr-enum)
    - [`StorageType(str, Enum)`](#storagetypestr-enum)
    - [`KeyEventType(str, Enum)`](#keyeventtypestr-enum)
    - [`KeyModifier(int, Enum)`](#keymodifierint-enum)
    - [`KeyLocation(int, Enum)`](#keylocationint-enum)
    - [`MouseEventType(str, Enum)`](#mouseeventtypestr-enum)
    - [`MouseButton(str, Enum)`](#mousebuttonstr-enum)
    - [`PointerType(str, Enum)`](#pointertypestr-enum)
    - [`TouchEventType(str, Enum)`](#toucheventtypestr-enum)
    - [`DragEventType(str, Enum)`](#drageventtypestr-enum)
    - [`GestureSourceType(str, Enum)`](#gesturesourcetypestr-enum)
    - [`IncludeWhitespace(str, Enum)`](#includewhitespacestr-enum)
    - [`PhysicalAxes(str, Enum)`](#physicalaxesstr-enum)
    - [`LogicalAxes(str, Enum)`](#logicalaxesstr-enum)
    - [`PseudoType(str, Enum)`](#pseudotypestr-enum)
    - [`ShadowRootType(str, Enum)`](#shadowroottypestr-enum)
    - [`CompatibilityMode(str, Enum)`](#compatibilitymodestr-enum)
    - [`ElementRelation(str, Enum)`](#elementrelationstr-enum)
    - [`MixedContentType(str, Enum)`](#mixedcontenttypestr-enum)
    - [`ResourcePriority(str, Enum)`](#resourceprioritystr-enum)
    - [`TrustTokenOperationType(str, Enum)`](#trusttokenoperationtypestr-enum)
    - [`RefreshPolicy(str, Enum)`](#refreshpolicystr-enum)
    - [`DialogType(str, Enum)`](#dialogtypestr-enum)
    - [`InitiatorType(str, Enum)`](#initiatortypestr-enum)
    - [`NetworkServiceWorkerRouterSourceType(str, Enum)`](#networkserviceworkerroutersourcetypestr-enum)
    - [`NetworkServiceWorkerResponseSource(str, Enum)`](#networkserviceworkerresponsesourcestr-enum)
    - [`AlternateProtocolUsage(str, Enum)`](#alternateprotocolusagestr-enum)
    - [`SecurityState(str, Enum)`](#securitystatestr-enum)
    - [`CertificateTransparencyCompliance(str, Enum)`](#certificatetransparencycompliancestr-enum)

# Модуль `pydoll.constants`

Этот модуль содержит различные константы и перечисления, используемые в проекте `pydoll` для определения типов, состояний, поведений и других фиксированных значений.

## Перечисления

### `By(str, Enum)`

Определяет стратегии поиска элементов на веб-странице.

- `CSS_SELECTOR = 'css'`
- `XPATH = 'xpath'`
- `CLASS_NAME = 'class_name'`
- `ID = 'id'`
- `TAG_NAME = 'tag_name'`
- `NAME = 'name'`

### `Scripts`

Содержит предопределенные JavaScript-скрипты для выполнения различных действий в контексте браузера.

- `ELEMENT_VISIBLE`: Проверяет видимость элемента.
- `ELEMENT_ON_TOP`: Проверяет, находится ли элемент поверх других элементов.
- `CLICK`: Выполняет клик по элементу.
- `CLICK_OPTION_TAG`: Выбирает опцию в элементе `<select>`.
- `BOUNDS`: Возвращает границы элемента.
- `FIND_RELATIVE_XPATH_ELEMENT`: Находит элемент по относительному XPath.
- `FIND_XPATH_ELEMENT`: Находит элемент по абсолютному XPath.
- `FIND_RELATIVE_XPATH_ELEMENTS`: Находит все элементы по относительному XPath.
- `FIND_XPATH_ELEMENTS`: Находит все элементы по абсолютному XPath.
- `QUERY_SELECTOR`: Выполняет `document.querySelector`.
- `RELATIVE_QUERY_SELECTOR`: Выполняет `this.querySelector`.
- `QUERY_SELECTOR_ALL`: Выполняет `document.querySelectorAll`.
- `RELATIVE_QUERY_SELECTOR_ALL`: Выполняет `this.querySelectorAll`.

### `Key(tuple[str, int], Enum)`

Определяет коды клавиш для имитации ввода с клавиатуры.

Примеры: `BACKSPACE`, `TAB`, `ENTER`, `SHIFT`, `CONTROL`, `ALT`, `F1`, `SEMICOLON` и т.д.

### `BrowserType(Enum)`

Определяет поддерживаемые типы браузеров.

- `CHROME`
- `EDGE`

### `WindowState(str, Enum)`

Возможные состояния окна браузера.

- `MAXIMIZED = 'maximized'`
- `MINIMIZED = 'minimized'`
- `NORMAL = 'normal'`

### `DownloadBehavior(str, Enum)`

Возможные поведения для обработки загрузок.

- `ALLOW = 'allow'`
- `DENY = 'deny'`
- `ALLOW_AND_NAME = 'allowAndName'`
- `DEFAULT = 'default'`

### `PermissionType(str, Enum)`

Типы разрешений браузера, как определено в Chrome DevTools Protocol.

Примеры: `GEOLOCATION`, `NOTIFICATIONS`, `CAMERA_CAPTURE`, `AUDIO_CAPTURE` и т.д.

### `RequestMethod(str, Enum)`

Методы HTTP-запросов.

- `GET = 'GET'`
- `POST = 'POST'`
- `OPTIONS = 'OPTIONS'`
- `PUT = 'PUT'`
- `DELETE = 'DELETE'`

### `AuthChallengeResponseValues(str, Enum)`

Возможные значения для ответа на запрос аутентификации.

- `DEFAULT = 'Default'`
- `CANCEL_AUTH = 'CancelAuth'`
- `PROVIDE_CREDENTIALS = 'ProvideCredentials'`

### `ResourceType(str, Enum)`

Типы ресурсов, загружаемых браузером.

Примеры: `DOCUMENT`, `STYLESHEET`, `IMAGE`, `SCRIPT`, `XHR`, `WEBSOCKET` и т.д.

### `RequestStage(str, Enum)`

Стадии сетевого запроса.

- `REQUEST = 'Request'`
- `RESPONSE = 'Response'`

### `NetworkErrorReason(str, Enum)`

Причины сбоев на сетевом уровне.

Примеры: `FAILED`, `ABORTED`, `TIMED_OUT`, `ACCESS_DENIED` и т.д.

### `CookiePriority(str, Enum)`

Уровни приоритета файлов cookie.

- `LOW = 'Low'`
- `MEDIUM = 'Medium'`
- `HIGH = 'High'`

### `CookieSourceScheme(str, Enum)`

Схемы источника файлов cookie.

- `UNSET = 'Unset'`
- `NON_SECURE = 'NonSecure'`
- `SECURE = 'Secure'`

### `CookieSameSite(str, Enum)`

Значения `SameSite` для файлов cookie.

- `STRICT = 'Strict'`
- `LAX = 'Lax'`
- `NONE = 'None'`

### `ConnectionType(str, Enum)`

Типы сетевых подключений.

Примеры: `WIFI`, `ETHERNET`, `CELLULAR4G` и т.д.

### `ContentEncoding(str, Enum)`

Типы кодирования контента.

- `GZIP = 'gzip'`
- `DEFLATE = 'deflate'`
- `BR = 'br'`
- `ZSTD = 'zstd'`

### `ScreenshotFormat(str, Enum)`

Форматы скриншотов.

- `JPEG = 'jpeg'`
- `PNG = 'png'`
- `WEBP = 'webp'`

### `TransitionType(str, Enum)`

Типы переходов между страницами.

Примеры: `LINK`, `TYPED`, `RELOAD` и т.д.

### `ReferrerPolicy(str, Enum)`

Политики реферера.

Примеры: `NO_REFERRER`, `ORIGIN`, `SAME_ORIGIN` и т.д.

### `TransferMode(str, Enum)`

Режимы передачи данных.

- `RETURN_AS_STREAM = 'returnAsStream'`
- `RETURN_AS_BASE64 = 'returnAsBase64'`

### `AutoResponseMode(str, Enum)`

Режимы автоматического ответа.

- `NONE = 'none'`
- `AUTO_ACCEPT = 'autoAccept'`
- `AUTO_REJECT = 'autoReject'`
- `AUTO_OPTOUT = 'autoOptout'`

### `WebLifecycleState(str, Enum)`

Состояния жизненного цикла веб-страницы.

- `FROZEN = 'frozen'`
- `ACTIVE = 'active'`

### `ScreencastFormat(str, Enum)`

Форматы скринкастов.

- `JPEG = 'jpeg'`
- `PNG = 'png'`

### `OriginTrialStatus(str, Enum)`

Статус пробной версии Origin Trial.

- `ENABLED = 'Enabled'`
- `VALID_TOKEN_NOT_PROVIDED = 'ValidTokenNotProvided'`
- `OS_NOT_SUPPORTED = 'OsNotSupported'`
- `TRIAL_NOT_ALLOWED = 'TrialNotAllowed'`

### `OriginTrialUsageRestriction(str, Enum)`

Ограничения использования пробной версии Origin Trial.

- `NONE = 'None'`
- `SUBSET = 'Subset'`

### `OriginTrialTokenStatus(str, Enum)`

Статус токена пробной версии Origin Trial.

Примеры: `SUCCESS`, `NOT_SUPPORTED`, `EXPIRED` и т.д.

### `PermissionsPolicyBlockReason(str, Enum)`

Причины блокировки политики разрешений.

- `HEADER = 'Header'`
- `IFRAME_ATTRIBUTE = 'IframeAttribute'`
- `IN_FANCED_FRAME_TREE = 'InFancedFrameTree'`
- `IN_ISOLATED_APP = 'InIsolatedApp'`

### `PermissionsPolicyFeature(str, Enum)`

Функции политики разрешений.

Примеры: `ACCELEROMETER`, `CAMERA`, `GEOLOCATION`, `MICROPHONE` и т.д.

### `CrossOriginOpenerPolicyStatus(str, Enum)`

Статус политики `Cross-Origin-Opener-Policy`.

Примеры: `SAME_ORIGIN`, `SAME_ORIGIN_ALLOW_POPUPS` и т.д.

### `CrossOriginEmbedderPolicyStatus(str, Enum)`

Статус политики `Cross-Origin-Embedder-Policy`.

- `NONE = 'None'`
- `CREDENTIALLESS = 'Credentialless'`
- `REQUIRE_CORP = 'RequireCorp'`

### `ContentSecurityPolicySource(str, Enum)`

Источники политики безопасности контента.

- `HTTP = 'HTTP'`
- `META = 'Meta'`

### `UnserializableEnum(str, Enum)`

Несериализуемые значения.

- `NEGATIVE_ZERO = '-0'`
- `NAN = 'NaN'`
- `INFINITY = 'Infinity'`
- `NEGATIVE_INFINITY = '-Infinity'`

### `SerializationValue(str, Enum)`

Значения сериализации.

- `DEEP = 'deep'`
- `JSON = 'json'`
- `ID_ONLY = 'idOnly'`

### `RemoteObjectType(str, Enum)`

Типы удаленных объектов.

Примеры: `OBJECT`, `FUNCTION`, `STRING`, `NUMBER` и т.д.

### `RemoteObjectSubtype(str, Enum)`

Подтипы удаленных объектов.

Примеры: `ARRAY`, `NULL`, `NODE`, `REGEXP` и т.д.

### `DeepSerializedValueType(str, Enum)`

Типы глубоко сериализованных значений.

Примеры: `UNDEFINED`, `NULL`, `STRING`, `NUMBER` и т.д.

### `ObjectPreviewType(str, Enum)`

Типы предварительного просмотра объектов.

Примеры: `OBJECT`, `FUNCTION`, `STRING`, `NUMBER` и т.д.

### `ObjectPreviewSubtype(str, Enum)`

Подтипы предварительного просмотра объектов.

Примеры: `ARRAY`, `NULL`, `NODE`, `REGEXP` и т.д.

### `PropertyPreviewType(str, Enum)`

Типы предварительного просмотра свойств.

Примеры: `OBJECT`, `FUNCTION`, `STRING`, `NUMBER` и т.д.

### `PropertyPreviewSubtype(str, Enum)`

Подтипы предварительного просмотра свойств.

Примеры: `ARRAY`, `NULL`, `NODE`, `REGEXP` и т.д.

### `StorageBucketDurability(str, Enum)`

Надежность корзины хранения.

- `RELAXED = 'relaxed'`
- `STRICT = 'strict'`

### `StorageType(str, Enum)`

Типы хранилищ.

Примеры: `COOKIES`, `LOCAL_STORAGE`, `INDEXEDDB` и т.д.

### `KeyEventType(str, Enum)`

Типы событий клавиатуры.

- `KEY_DOWN = 'keyDown'`
- `KEY_UP = 'keyUp'`
- `CHAR = 'char'`
- `RAW_KEY_DOWN = 'rawKeyDown'`

### `KeyModifier(int, Enum)`

Модификаторы клавиш.

- `ALT = 1`
- `CTRL = 2`
- `META = 4`
- `SHIFT = 8`

### `KeyLocation(int, Enum)`

Расположение клавиши.

- `LEFT = 1`
- `RIGHT = 2`

### `MouseEventType(str, Enum)`

Типы событий мыши.

- `MOUSE_PRESSED = 'mousePressed'`
- `MOUSE_RELEASED = 'mouseReleased'`
- `MOUSE_MOVED = 'mouseMoved'`
- `MOUSE_WHEEL = 'mouseWheel'`

### `MouseButton(str, Enum)`

Кнопки мыши.

- `NONE = 'none'`
- `LEFT = 'left'`
- `MIDDLE = 'middle'`
- `RIGHT = 'right'`
- `BACK = 'back'`
- `FORWARD = 'forward'`

### `PointerType(str, Enum)`

Типы указателей.

- `MOUSE = 'mouse'`
- `PEN = 'pen'`

### `TouchEventType(str, Enum)`

Типы сенсорных событий.

- `TOUCH_START = 'touchStart'`
- `TOUCH_MOVE = 'touchMove'`
- `TOUCH_END = 'touchEnd'`
- `TOUCH_CANCEL = 'touchCancel'`

### `DragEventType(str, Enum)`

Типы событий перетаскивания.

- `DRAG_ENTER = 'dragEnter'`
- `DRAG_OVER = 'dragOver'`
- `DROP = 'drop'`
- `DRAG_CANCEL = 'dragCancel'`

### `GestureSourceType(str, Enum)`

Типы источников жестов.

- `TOUCH = 'touch'`
- `MOUSE = 'mouse'`
- `DEFAULT = 'default'`

### `IncludeWhitespace(str, Enum)`

Включение пробелов.

- `NONE = 'none'`
- `ALL = 'all'`

### `PhysicalAxes(str, Enum)`

Физические оси.

- `HORIZONTAL = 'Horizontal'`
- `VERTICAL = 'Vertical'`
- `BOTH = 'Both'`

### `LogicalAxes(str, Enum)`

Логические оси.

- `INLINE = 'Inline'`
- `BLOCK = 'Block'`
- `BOTH = 'Both'`

### `PseudoType(str, Enum)`

Псевдотипы элементов.

Примеры: `FIRST_LINE`, `BEFORE`, `AFTER`, `SELECTION` и т.д.

### `ShadowRootType(str, Enum)`

Типы теневого DOM.

- `OPEN = 'open'`
- `CLOSED = 'closed'`
- `USER_AGENT = 'user-agent'`

### `CompatibilityMode(str, Enum)`

Режимы совместимости.

- `QUIRKS_MODE = 'QuirksMode'`
- `LIMITED_QUIRKS_MODE = 'LimitedQuirksMode'`
- `NO_QUIRKS_MODE = 'NoQuirksMode'`

### `ElementRelation(str, Enum)`

Отношения элементов.

- `POPOVER_TARGET = 'PopoverTarget'`
- `INTEREST_TARGET = 'InterestTarget'`

### `MixedContentType(str, Enum)`

Типы смешанного контента.

- `BLOCKABLE = 'blockable'`
- `OPTIONALLY_BLOCKABLE = 'optionally-blockable'`
- `NONE = 'none'`

### `ResourcePriority(str, Enum)`

Приоритеты ресурсов.

- `VERY_LOW = 'VeryLow'`
- `LOW = 'Low'`
- `MEDIUM = 'Medium'`
- `HIGH = 'High'`
- `VERY_HIGH = 'VeryHigh'`

### `TrustTokenOperationType(str, Enum)`

Типы операций с Trust Token.

- `ISSUANCE = 'Issuance'`
- `REDEMPTION = 'Redemption'`
- `SIGNING = 'Signing'`

### `RefreshPolicy(str, Enum)`

Политики обновления.

- `USE_CACHED = 'UseCached'`
- `REFRESH = 'Refresh'`

### `DialogType(str, Enum)`

Типы диалоговых окон.

- `ALERT = 'alert'`
- `CONFIRM = 'confirm'`
- `PROMPT = 'prompt'`
- `BEFORE_UNLOAD = 'beforeunload'`

### `InitiatorType(str, Enum)`

Типы инициаторов.

- `PARSER = 'parser'`
- `SCRIPT = 'script'`
- `PRELOAD = 'preload'`
- `SIGNED_EXCHANGE = 'SignedExchange'`
- `PREFLIGHT = 'preflight'`
- `OTHER = 'other'`

### `NetworkServiceWorkerRouterSourceType(str, Enum)`

Типы источников маршрутизатора Service Worker.

- `NETWORK = 'network'`
- `CACHE = 'cache'`
- `FETCH_EVENT = 'fetch-event'`
- `RACE_NETWORK = 'race-network'`
- `RACE_NETWORK_AND_FETCH_HANDLER = 'race-network-and-fetch-handler'`
- `RACE_NETWORK_AND_CACHE = 'race-network-and-cache'`

### `NetworkServiceWorkerResponseSource(str, Enum)`

Типы источников ответа Service Worker.

- `CACHE_STORAGE = 'cache-storage'`
- `HTTP_CACHE = 'http-cache'`
- `FALLBACK_CODE = 'fallback-code'`
- `NETWORK = 'network'`

### `AlternateProtocolUsage(str, Enum)`

Типы использования альтернативного протокола.

Примеры: `ALTERNATIVE_JOB_WON_WITHOUT_RACE`, `MAIN_JOB_WON_RACE` и т.д.

### `SecurityState(str, Enum)`

Типы состояния безопасности.

- `UNKNOWN = 'unknown'`
- `NEUTRAL = 'neutral'`
- `INSECURE = 'insecure'`
- `INFO = 'info'`
- `INSECURE_BROKEN = 'insecure-broken'`

### `CertificateTransparencyCompliance(str, Enum)`

Типы соответствия прозрачности сертификатов.

- `UNKNOWN = 'unknown'`
- `NOT_COMPLIANT = 'not-compliant'`
- `COMPLIANT = 'compliant'`