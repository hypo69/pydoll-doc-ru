## Содержание

- [Модуль `pydoll.protocol.page.responses`](#модуль-pydollprotocolpageresponses)
  - [Типы данных](#типы-данных)
    - [`AddScriptToEvaluateOnNewDocumentResultDict`](#addscripttoevaluateonnewdocumentresultdict)
    - [`CaptureScreenshotResultDict`](#capturescreenshotresultdict)
    - [`CreateIsolatedWorldResultDict`](#createisolatedworldresultdict)
    - [`GetAppManifestResultDict`](#getappmanifestresultdict)
    - [`GetFrameTreeResultDict`](#getframetreeresultdict)
    - [`GetLayoutMetricsResultDict`](#getlayoutmetricsresultdict)
    - [`GetNavigationHistoryResultDict`](#getnavigationhistoryresultdict)
    - [`NavigateResultDict`](#navigateresultdict)
    - [`PrintToPDFResultDict`](#printtopdfresultdict)
    - [`CaptureSnapshotResultDict`](#capturesnapshotresultdict)
    - [`GetAdScriptAncestryIdsResultDict`](#getadscriptancestryidsresultdict)
    - [`GetAppIdResultDict`](#getappidresultdict)
    - [`GetInstallabilityErrorsResultDict`](#getinstallabilityerrorsresultdict)
    - [`GetOriginTrialsResultDict`](#getorigintrialsresultdict)
    - [`GetPermissionsPolicyStateResultDict`](#getpermissionspolicystateresultdict)
    - [`GetResourceContentResultDict`](#getresourcecontentresultdict)
    - [`GetResourceTreeResultDict`](#getresourcetreeresultdict)
    - [`SearchInResourceResultDict`](#searchinresourceresultdict)
  - [Ответы](#ответы)
    - [`AddScriptToEvaluateOnNewDocumentResponse`](#addscripttoevaluateonnewdocumentresponse)
    - [`CaptureScreenshotResponse`](#capturescreenshotresponse)
    - [`CreateIsolatedWorldResponse`](#createisolatedworldresponse)
    - [`GetAppManifestResponse`](#getappmanifestresponse)
    - [`GetFrameTreeResponse`](#getframetreeresponse)
    - [`GetLayoutMetricsResponse`](#getlayoutmetricsresponse)
    - [`GetNavigationHistoryResponse`](#getnavigationhistoryresponse)
    - [`NavigateResponse`](#navigateresponse)
    - [`PrintToPDFResponse`](#printtopdfresponse)
    - [`CaptureSnapshotResponse`](#capturesnapshotresponse)
    - [`GetAdScriptAncestryIdsResponse`](#getadscriptancestryidsresponse)
    - [`GetAppIdResponse`](#getappidresponse)
    - [`GetInstallabilityErrorsResponse`](#getinstallabilityerrorsresponse)
    - [`GetOriginTrialsResponse`](#getorigintrialsresponse)
    - [`GetPermissionsPolicyStateResponse`](#getpermissionspolicystateresponse)
    - [`GetResourceContentResponse`](#getresourcecontentresponse)
    - [`GetResourceTreeResponse`](#getresourcetreeresponse)
    - [`SearchInResourceResponse`](#searchinresourceresponse)

# Модуль `pydoll.protocol.page.responses`

Этот модуль определяет типы данных для ответов, возвращаемых методами домена `Page` протокола Chrome DevTools Protocol (CDP). Эти типы данных представляют собой структуры, которые содержат результаты выполнения команд, связанных со страницей.

## Типы данных

### `AddScriptToEvaluateOnNewDocumentResultDict`

Результат выполнения команды `addScriptToEvaluateOnNewDocument`.

- `identifier` (str): Идентификатор.

### `CaptureScreenshotResultDict`

Результат выполнения команды `captureScreenshot`.

- `data` (str): Данные изображения в кодировке Base64.

### `CreateIsolatedWorldResultDict`

Результат выполнения команды `createIsolatedWorld`.

- `executionContextId` (int): Идентификатор контекста выполнения.

### `GetAppManifestResultDict`

Результат выполнения команды `getAppManifest`.

- `url` (str): URL.
- `errors` (list[AppManifestError]): Ошибки.
- `data` (str): Содержимое манифеста в виде строки.
- `manifest` (NotRequired[WebAppManifest]): Манифест.

### `GetFrameTreeResultDict`

Результат выполнения команды `getFrameTree`.

- `frameTree` (FrameTree): Дерево фреймов.

### `GetLayoutMetricsResultDict`

Результат выполнения команды `getLayoutMetrics`.

- `cssLayoutViewport` (LayoutViewport): Область просмотра макета CSS.
- `cssVisualViewport` (VisualViewport): Визуальная область просмотра CSS.
- `cssContentSize` (Rect): Размер содержимого CSS.

### `GetNavigationHistoryResultDict`

Результат выполнения команды `getNavigationHistory`.

- `currentIndex` (int): Текущий индекс.
- `entries` (list[NavigationEntry]): Записи.

### `NavigateResultDict`

Результат выполнения команды `navigate`.

- `frameId` (str): Идентификатор фрейма.
- `loaderId` (NotRequired[str]): Идентификатор загрузчика.
- `errorText` (NotRequired[str]): Текст ошибки.

### `PrintToPDFResultDict`

Результат выполнения команды `printToPDF`.

- `data` (str): Данные PDF в кодировке Base64.
- `stream` (NotRequired[str]): Дескриптор потока, который содержит данные PDF.

### `CaptureSnapshotResultDict`

Результат выполнения команды `captureSnapshot`.

- `data` (str): Данные изображения в кодировке Base64.

### `GetAdScriptAncestryIdsResultDict`

Результат выполнения команды `getAdScriptAncestryIds`.

- `adScriptAncestryIds` (list[AdScriptId]): Идентификаторы предков рекламного скрипта.

### `GetAppIdResultDict`

Результат выполнения команды `getAppId`.

- `appId` (NotRequired[str]): Идентификатор приложения.
- `recommendedId` (NotRequired[str]): Рекомендуемый идентификатор.

### `GetInstallabilityErrorsResultDict`

Результат выполнения команды `getInstallabilityErrors`.

- `installabilityErrors` (list[InstallabilityError]): Ошибки установки.

### `GetOriginTrialsResultDict`

Результат выполнения команды `getOriginTrials`.

- `originTrials` (list[OriginTrial]): Пробные версии Origin Trial.

### `GetPermissionsPolicyStateResultDict`

Результат выполнения команды `getPermissionsPolicyState`.

- `states` (list[PermissionsPolicyFeatureState]): Состояния.

### `GetResourceContentResultDict`

Результат выполнения команды `getResourceContent`.

- `content` (str): Содержимое.
- `base64Encoded` (bool): Закодировано в Base64.

### `GetResourceTreeResultDict`

Результат выполнения команды `getResourceTree`.

- `frameTree` (FrameResourceTree): Дерево ресурсов фрейма.

### `SearchInResourceResultDict`

Результат выполнения команды `searchInResource`.

- `result` (list[SearchMatch]): Результат.

## Ответы

### `AddScriptToEvaluateOnNewDocumentResponse`

Ответ на команду `addScriptToEvaluateOnNewDocument`.

- `result` (AddScriptToEvaluateOnNewDocumentResultDict): Результат выполнения команды.

### `CaptureScreenshotResponse`

Ответ на команду `captureScreenshot`.

- `result` (CaptureScreenshotResultDict): Результат выполнения команды.

### `CreateIsolatedWorldResponse`

Ответ на команду `createIsolatedWorld`.

- `result` (CreateIsolatedWorldResultDict): Результат выполнения команды.

### `GetAppManifestResponse`

Ответ на команду `getAppManifest`.

- `result` (GetAppManifestResultDict): Результат выполнения команды.

### `GetFrameTreeResponse`

Ответ на команду `getFrameTree`.

- `result` (GetFrameTreeResultDict): Результат выполнения команды.

### `GetLayoutMetricsResponse`

Ответ на команду `getLayoutMetrics`.

- `result` (GetLayoutMetricsResultDict): Результат выполнения команды.

### `GetNavigationHistoryResponse`

Ответ на команду `getNavigationHistory`.

- `result` (GetNavigationHistoryResultDict): Результат выполнения команды.

### `NavigateResponse`

Ответ на команду `navigate`.

- `result` (NavigateResultDict): Результат выполнения команды.

### `PrintToPDFResponse`

Ответ на команду `printToPDF`.

- `result` (PrintToPDFResultDict): Результат выполнения команды.

### `CaptureSnapshotResponse`

Ответ на команду `captureSnapshot`.

- `result` (CaptureSnapshotResultDict): Результат выполнения команды.

### `GetAdScriptAncestryIdsResponse`

Ответ на команду `getAdScriptAncestryIds`.

- `result` (GetAdScriptAncestryIdsResultDict): Результат выполнения команды.

### `GetAppIdResponse`

Ответ на команду `getAppId`.

- `result` (GetAppIdResultDict): Результат выполнения команды.

### `GetInstallabilityErrorsResponse`

Ответ на команду `getInstallabilityErrors`.

- `result` (GetInstallabilityErrorsResultDict): Результат выполнения команды.

### `GetOriginTrialsResponse`

Ответ на команду `getOriginTrials`.

- `result` (GetOriginTrialsResultDict): Результат выполнения команды.

### `GetPermissionsPolicyStateResponse`

Ответ на команду `getPermissionsPolicyState`.

- `result` (GetPermissionsPolicyStateResultDict): Результат выполнения команды.

### `GetResourceContentResponse`

Ответ на команду `getResourceContent`.

- `result` (GetResourceContentResultDict): Результат выполнения команды.

### `GetResourceTreeResponse`

Ответ на команду `getResourceTree`.

- `result` (GetResourceTreeResultDict): Результат выполнения команды.

### `SearchInResourceResponse`

Ответ на команду `searchInResource`.

- `result` (SearchInResourceResultDict): Результат выполнения команды.
