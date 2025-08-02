## Содержание

- [Модуль `pydoll.protocol.page.params`](#модуль-pydollprotocolpageparams)
  - [Параметры команд](#параметры-команд)
    - [`AddScriptToEvaluateOnNewDocumentParams`](#addscripttoevaluateonnewdocumentparams)
    - [`CaptureScreenshotParams`](#capturescreenshotparams)
    - [`CreateIsolatedWorldParams`](#createisolatedworldparams)
    - [`PageEnableParams`](#pageenableparams)
    - [`GetAppManifestParams`](#getappmanifestparams)
    - [`HandleJavaScriptDialogParams`](#handlejavascriptdialogparams)
    - [`NavigateParams`](#navigateparams)
    - [`NavigateToHistoryEntryParams`](#navigatetoHistoryentryparams)
    - [`PrintToPDFParams`](#printtopdfparams)
    - [`RemoveScriptToEvaluateOnNewDocumentParams`](#removescripttoevaluateonnewdocumentparams)
    - [`ReloadParams`](#reloadparams)
    - [`SetBypassCSPParams`](#setbypasscspparams)
    - [`SetDocumentContentParams`](#setdocumentcontentparams)
    - [`SetInterceptFileChooserDialogParams`](#setinterceptfilechooserdialogparams)
    - [`SetLifecycleEventsEnabledParams`](#setlifecycleeventsenabledparams)
    - [`AddCompilationCacheParams`](#addcompilationcacheparams)
    - [`CaptureSnapshotParams`](#capturesnapshotparams)
    - [`GenerateTestReportParams`](#generatetestreportparams)
    - [`GetAdScriptAncestryIdsParams`](#getadscriptancestryidsparams)
    - [`GetAppIdParams`](#getappidparams)
    - [`GetInstallabilityErrorsParams`](#getinstallabilityerrorsparams)
    - [`GetOriginTrialsParams`](#getorigintrialsparams)
    - [`GetPermissionsPolicyStateParams`](#getpermissionspolicystateresponse)
    - [`GetResourceContentParams`](#getresourcecontentparams)
    - [`ScreencastFrameAckParams`](#screencastframeackparams)
    - [`SearchInResourceParams`](#searchinresourceparams)
    - [`SetAdBlockingEnabledParams`](#setadblockingenabledparams)
    - [`SetFontFamiliesParams`](#setfontfamiliesparams)
    - [`SetFontSizesParams`](#setfontsizesparams)
    - [`SetPrerenderingAllowedParams`](#setprerenderingallowedparams)
    - [`SetRPHRegistrationModeParams`](#setrphregistrationmodeparams)
    - [`SetSPCTransactionModeParams`](#setspctransactionmodeparams)
    - [`SetWebLifecycleStateParams`](#setweblifecyclestateparams)
    - [`StartScreencastParams`](#startscreencastparams)
    - [`CompilationCacheParams`](#compilationcacheparams)
    - [`ProduceCompilationCacheParams`](#producecompilationcacheparams)

# Модуль `pydoll.protocol.page.params`

Этот модуль определяет параметры для команд, используемых в домене `Page` протокола Chrome DevTools Protocol (CDP). Эти параметры представляют собой структуры, которые передаются при вызове команд для взаимодействия со страницами браузера.

## Параметры команд

### `AddScriptToEvaluateOnNewDocumentParams`

Параметры для добавления скрипта для выполнения в новом документе.

- `source` (str): Исходный код скрипта для выполнения.
- `worldName` (NotRequired[str]): Имя мира.
- `includeCommandLineAPI` (NotRequired[bool]): Включать ли API командной строки.
- `runImmediately` (NotRequired[bool]): Выполнять ли немедленно.

### `CaptureScreenshotParams`

Параметры для захвата скриншота страницы.

- `format` (NotRequired[ScreenshotFormat]): Формат изображения.
- `quality` (NotRequired[int]): Качество сжатия.
- `clip` (NotRequired[Viewport]): Область для захвата.
- `fromSurface` (NotRequired[bool]): Захват с поверхности.
- `captureBeyondViewport` (NotRequired[bool]): Захват за пределами области просмотра.
- `optimizeForSpeed` (NotRequired[bool]): Оптимизировать для скорости.

### `CreateIsolatedWorldParams`

Параметры для создания изолированного мира.

- `frameId` (str): Идентификатор фрейма.
- `worldName` (NotRequired[str]): Имя мира.
- `grantUniveralAccess` (NotRequired[bool]): Предоставлять ли универсальный доступ.

### `PageEnableParams`

Параметры для включения домена страницы.

- `enableFileChooserOpenedEvent` (NotRequired[bool]): Включить ли событие открытия диалога выбора файла.

### `GetAppManifestParams`

Параметры для получения манифеста приложения.

- `manifestId` (NotRequired[str]): Идентификатор манифеста.

### `HandleJavaScriptDialogParams`

Параметры для обработки диалогового окна JavaScript.

- `accept` (bool): Принять или отклонить диалог.
- `promptText` (NotRequired[str]): Текст для подсказки.

### `NavigateParams`

Параметры для навигации по URL.

- `url` (str): URL для навигации.
- `referrer` (NotRequired[str]): URL реферера.
- `transitionType` (NotRequired[TransitionType]): Тип перехода.
- `frameId` (NotRequired[str]): Идентификатор фрейма.
- `referrerPolicy` (NotRequired[ReferrerPolicy]): Политика реферера.

### `NavigateToHistoryEntryParams`

Параметры для навигации к записи истории.

- `entryId` (int): Идентификатор записи истории.

### `PrintToPDFParams`

Параметры для печати в PDF.

- `landscape` (NotRequired[bool]): Ориентация страницы.
- `displayHeaderFooter` (NotRequired[bool]): Отображать верхний и нижний колонтитулы.
- `printBackground` (NotRequired[bool]): Печатать фон.
- `scale` (NotRequired[float]): Масштаб.
- `paperWidth` (NotRequired[float]): Ширина бумаги.
- `paperHeight` (NotRequired[float]): Высота бумаги.
- `marginTop` (NotRequired[float]): Верхнее поле.
- `marginBottom` (NotRequired[float]): Нижнее поле.
- `marginLeft` (NotRequired[float]): Левое поле.
- `marginRight` (NotRequired[float]): Правое поле.
- `pageRanges` (NotRequired[str]): Диапазоны страниц.
- `headerTemplate` (NotRequired[str]): Шаблон верхнего колонтитула.
- `footerTemplate` (NotRequired[str]): Шаблон нижнего колонтитула.
- `preferCSSPageSize` (NotRequired[bool]): Предпочитать ли размер страницы CSS.
- `transferMode` (NotRequired[TransferMode]): Режим передачи.
- `generateTaggedPDF` (NotRequired[bool]): Генерировать ли тегированный PDF.
- `generateDocumentOutline` (NotRequired[bool]): Генерировать ли структуру документа.

### `RemoveScriptToEvaluateOnNewDocumentParams`

Параметры для удаления скрипта для выполнения в новом документе.

- `identifier` (str): Идентификатор скрипта.

### `ReloadParams`

Параметры для перезагрузки страницы.

- `ignoreCache` (NotRequired[bool]): Игнорировать ли кэш.
- `scriptToEvaluateOnLoad` (NotRequired[str]): Скрипт для выполнения при загрузке.
- `loaderId` (NotRequired[str]): Идентификатор загрузчика.

### `SetBypassCSPParams`

Параметры для установки обхода CSP.

- `enabled` (bool): Включить/отключить.

### `SetDocumentContentParams`

Параметры для установки содержимого документа.

- `frameId` (str): Идентификатор фрейма.
- `html` (str): HTML-содержимое.

### `SetInterceptFileChooserDialogParams`

Параметры для установки перехвата диалога выбора файла.

- `enabled` (bool): Включить/отключить.
- `cancel` (NotRequired[bool]): Отменить.

### `SetLifecycleEventsEnabledParams`

Параметры для включения/отключения событий жизненного цикла.

- `enabled` (bool): Включить/отключить.

### `AddCompilationCacheParams`

Параметры для добавления записи в кэш компиляции.

- `url` (str): URL.
- `data` (str): Данные.

### `CaptureSnapshotParams`

Параметры для захвата снимка.

- `format` (Literal['mhtml']): Формат.

### `GenerateTestReportParams`

Параметры для генерации тестового отчета.

- `message` (str): Сообщение.
- `group` (NotRequired[str]): Группа.

### `GetAdScriptAncestryIdsParams`

Параметры для получения идентификаторов предков рекламного скрипта.

- `frameId` (str): Идентификатор фрейма.

### `GetAppIdParams`

Параметры для получения идентификатора приложения.

- `appId` (NotRequired[str]): Идентификатор приложения.
- `recommendedId` (NotRequired[str]): Рекомендуемый идентификатор.

### `GetInstallabilityErrorsParams`

Параметры для получения ошибок установки.

- `installabilityErrors` (NotRequired[list[InstallabilityError]]): Ошибки установки.

### `GetOriginTrialsParams`

Параметры для получения пробных версий Origin Trial.

- `frameId` (str): Идентификатор фрейма.

### `GetPermissionsPolicyStateParams`

Параметры для получения состояния политики разрешений.

- `frameId` (str): Идентификатор фрейма.

### `GetResourceContentParams`

Параметры для получения содержимого ресурса.

- `frameId` (str): Идентификатор фрейма.
- `url` (str): URL.

### `ScreencastFrameAckParams`

Параметры для подтверждения кадра скринкаста.

- `sessionId` (str): Идентификатор сессии.

### `SearchInResourceParams`

Параметры для поиска в ресурсе.

- `frameId` (str): Идентификатор фрейма.
- `url` (str): URL.
- `query` (str): Запрос.
- `caseSensitive` (NotRequired[bool]): Учитывать регистр.
- `isRegex` (NotRequired[bool]): Является ли регулярным выражением.

### `SetAdBlockingEnabledParams`

Параметры для включения блокировки рекламы.

- `enabled` (bool): Включить/отключить.

### `SetFontFamiliesParams`

Параметры для установки семейств шрифтов.

- `fontFamilies` (FontFamilies): Семейства шрифтов.
- `forScripts` (list[ScriptFontFamilies]): Для скриптов.

### `SetFontSizesParams`

Параметры для установки размеров шрифтов.

- `fontSizes` (FontSizes): Размеры шрифтов.

### `SetPrerenderingAllowedParams`

Параметры для разрешения предварительного рендеринга.

- `allowed` (bool): Разрешено.

### `SetRPHRegistrationModeParams`

Параметры для установки режима регистрации RPH.

- `mode` (AutoResponseMode): Режим.

### `SetSPCTransactionModeParams`

Параметры для установки режима транзакций SPC.

- `mode` (AutoResponseMode): Режим.

### `SetWebLifecycleStateParams`

Параметры для установки состояния жизненного цикла веб-страницы.

- `state` (WebLifecycleState): Состояние.

### `StartScreencastParams`

Параметры для запуска скринкаста.

- `format` (ScreencastFormat): Формат.
- `quality` (NotRequired[int]): Качество.
- `maxWidth` (NotRequired[int]): Максимальная ширина.
- `maxHeight` (NotRequired[int]): Максимальная высота.
- `everyNthFrame` (NotRequired[int]): Каждый N-й кадр.

### `CompilationCacheParams`

Параметры кэша компиляции.

- `url` (str): URL.
- `eager` (NotRequired[bool]): Жадный.

### `ProduceCompilationCacheParams`

Параметры для создания записи в кэше компиляции.

- `scripts` (list[CompilationCacheParams]): Скрипты.
