## Содержание

- [Модуль `pydoll.protocol.page.types`](#модуль-pydollprotocolpagetypes)
  - [Типы данных](#типы-данных)
    - [`Viewport`](#viewport)
    - [`InstallabilityErrorArgument`](#installabilityerrorargument)
    - [`InstallabilityError`](#installabilityerror)
    - [`FontFamilies`](#fontfamilies)
    - [`ScriptFontFamilies`](#scriptfontfamilies)
    - [`FontSizes`](#fontsizes)
    - [`AppManifestError`](#appmanifesterror)
    - [`ImageResource`](#imageresource)
    - [`FileFilter`](#filefilter)
    - [`FileHandler`](#filehandler)
    - [`LaunchHandler`](#launchhandler)
    - [`ProtocolHandler`](#protocolhandler)
    - [`RelatedApplication`](#relatedapplication)
    - [`ScopeExtension`](#scopeextension)
    - [`Screenshot`](#screenshot)
    - [`ShareTarget`](#sharetarget)
    - [`Shortcut`](#shortcut)
    - [`WebAppManifest`](#webappmanifest)
    - [`Frame`](#frame)
    - [`FrameResource`](#frameresource)
    - [`FrameResourceTree`](#frameresourcetree)
    - [`FrameTree`](#frametree)
    - [`LayoutViewport`](#layoutviewport)
    - [`VisualViewport`](#visualviewport)
    - [`NavigationEntry`](#navigationentry)
    - [`AdScriptId`](#adscriptid)
    - [`OriginTrialToken`](#origintrialtoken)
    - [`OriginTrialTokenWithStatus`](#origintrialtokenwithstatus)
    - [`OriginTrial`](#origintrial)
    - [`PermissionsPolicyBlockLocator`](#permissionspolicyblocklocator)
    - [`PermissionsPolicyFeatureState`](#permissionspolicyfeaturestate)
    - [`JavascriptDialogOpeningEventParams`](#javascriptdialogopeningeventparams)
    - [`JavascriptDialogOpeningEvent`](#javascriptdialogopeningevent)

# Модуль `pydoll.protocol.page.types`

Этот модуль определяет типы данных, используемые в домене `Page` протокола Chrome DevTools Protocol (CDP). Эти типы данных представляют собой структуры, которые описывают различные сущности, связанные со страницей браузера.

## Типы данных

### `Viewport`

Область просмотра для захвата скриншота или обрезки прямоугольника.

- `x` (float): X-координата.
- `y` (float): Y-координата.
- `width` (float): Ширина.
- `height` (float): Высота.
- `scale` (NotRequired[float]): Масштаб.

### `InstallabilityErrorArgument`

Аргумент ошибки установки.

- `name` (str): Имя.
- `value` (str): Значение.

### `InstallabilityError`

Ошибка установки.

- `errorId` (str): Идентификатор ошибки.
- `errorArguments` (list[InstallabilityErrorArgument]): Аргументы ошибки.

### `FontFamilies`

Семейства шрифтов.

- `standard` (NotRequired[str]): Стандартный.
- `fixed` (NotRequired[str]): Фиксированный.
- `serif` (NotRequired[str]): С засечками.
- `sansSerif` (NotRequired[str]): Без засечек.
- `cursive` (NotRequired[str]): Курсив.
- `fantasy` (NotRequired[str]): Фантазийный.
- `math` (NotRequired[str]): Математический.

### `ScriptFontFamilies`

Семейства шрифтов скрипта.

- `script` (str): Скрипт.
- `fontFamilies` (FontFamilies): Семейства шрифтов.

### `FontSizes`

Размеры шрифтов.

- `standard` (NotRequired[int]): Стандартный.
- `fixed` (NotRequired[int]): Фиксированный.

### `AppManifestError`

Структура ошибки манифеста приложения.

- `message` (str): Сообщение.
- `critical` (NotRequired[int]): Критический.
- `line` (NotRequired[int]): Строка.
- `column` (NotRequired[int]): Столбец.

### `ImageResource`

Ресурс изображения.

- `url` (str): URL.
- `sizes` (NotRequired[str]): Размеры.
- `type` (NotRequired[str]): Тип.

### `FileFilter`

Фильтр файлов.

- `name` (NotRequired[str]): Имя.
- `accepts` (NotRequired[list[str]]): Принимает.

### `FileHandler`

Обработчик файлов.

- `action` (str): Действие.
- `name` (str): Имя.
- `icons` (NotRequired[list[ImageResource]]): Иконки.
- `accepts` (NotRequired[list[FileFilter]]): Принимает.
- `launchType` (NotRequired[str]): Тип запуска.

### `LaunchHandler`

Обработчик запуска.

- `clientMode` (str): Режим клиента.

### `ProtocolHandler`

Обработчик протокола.

- `protocol` (str): Протокол.
- `url` (str): URL.

### `RelatedApplication`

Связанное приложение.

- `id` (str): Идентификатор.
- `url` (str): URL.

### `ScopeExtension`

Расширение области видимости.

- `origin` (str): Источник.
- `hasOriginWildcard` (bool): Имеет ли подстановочный знак источника.

### `Screenshot`

Скриншот.

- `image` (ImageResource): Изображение.
- `formFactor` (str): Форм-фактор.
- `label` (NotRequired[str]): Метка.

### `ShareTarget`

Цель обмена.

- `action` (str): Действие.
- `method` (str): Метод.
- `enctype` (str): Тип кодирования.
- `title` (NotRequired[str]): Заголовок.
- `text` (NotRequired[str]): Текст.
- `url` (NotRequired[str]): URL.
- `files` (NotRequired[list[FileFilter]]): Файлы.

### `Shortcut`

Ярлык.

- `name` (str): Имя.
- `url` (str): URL.

### `WebAppManifest`

Манифест веб-приложения.

- `backgroundColor` (NotRequired[str]): Цвет фона.
- `description` (NotRequired[str]): Описание.
- `dir` (NotRequired[str]): Направление.
- `display` (NotRequired[str]): Отображение.
- `displayOverrides` (NotRequired[list[str]]): Переопределения отображения.
- `fileHandlers` (NotRequired[list[FileHandler]]): Обработчики файлов.
- `icons` (NotRequired[list[ImageResource]]): Иконки.
- `id` (NotRequired[str]): Идентификатор.
- `lang` (NotRequired[str]): Язык.
- `launchHandler` (NotRequired[LaunchHandler]): Обработчик запуска.
- `name` (NotRequired[str]): Имя.
- `orientation` (NotRequired[str]): Ориентация.
- `preferRelatedApplications` (NotRequired[bool]): Предпочитать связанные приложения.
- `protocolHandlers` (NotRequired[list[ProtocolHandler]]): Обработчики протоколов.
- `relatedApplications` (NotRequired[list[RelatedApplication]]): Связанные приложения.
- `scope` (NotRequired[str]): Область видимости.
- `scopeExtensions` (NotRequired[list[ScopeExtension]]): Расширения области видимости.
- `screenshots` (NotRequired[list[Screenshot]]): Скриншоты.
- `shareTarget` (NotRequired[ShareTarget]): Цель обмена.
- `shortName` (NotRequired[str]): Короткое имя.
- `shortcuts` (NotRequired[list[Shortcut]]): Ярлыки.
- `startUrl` (NotRequired[str]): Начальный URL.
- `themeColor` (NotRequired[str]): Цвет темы.

### `Frame`

Информация о фрейме.

- `id` (str): Идентификатор.
- `loaderId` (NotRequired[str]): Идентификатор загрузчика.
- `url` (str): URL.
- `securityOrigin` (NotRequired[str]): Источник безопасности.
- `mimeType` (NotRequired[str]): Тип MIME.
- `unreachableUrl` (NotRequired[str]): Недоступный URL.

### `FrameResource`

Ресурс фрейма.

- `url` (str): URL.
- `type` (ResourceType): Тип.
- `mimeType` (str): Тип MIME.
- `lastModified` (NotRequired[str]): Последнее изменение.
- `contentSize` (NotRequired[float]): Размер содержимого.
- `failed` (NotRequired[bool]): Неудачно.
- `canceled` (NotRequired[bool]): Отменено.

### `FrameResourceTree`

Информация о иерархии фреймов.

- `frame` (Frame): Фрейм.
- `childFrames` (NotRequired[list['FrameResourceTree']]): Дочерние фреймы.
- `resources` (NotRequired[list[FrameResource]]): Ресурсы.

### `FrameTree`

Дерево фреймов.

- `frame` (Frame): Фрейм.
- `childFrames` (NotRequired[list['FrameTree']]): Дочерние фреймы.

### `LayoutViewport`

Позиция и размеры области просмотра макета.

- `pageX` (int): X-координата страницы.
- `pageY` (int): Y-координата страницы.
- `clientWidth` (int): Ширина клиента.
- `clientHeight` (int): Высота клиента.

### `VisualViewport`

Позиция, размеры и масштаб визуальной области просмотра.

- `offsetX` (float): Смещение по X.
- `offsetY` (float): Смещение по Y.
- `pageX` (float): X-координата страницы.
- `pageY` (float): Y-координата страницы.
- `clientWidth` (float): Ширина клиента.
- `clientHeight` (float): Высота клиента.
- `scale` (float): Масштаб.
- `zoom` (NotRequired[float]): Масштабирование.

### `NavigationEntry`

Запись истории навигации.

- `id` (int): Идентификатор.
- `url` (str): URL.
- `userTypedURL` (str): URL, введенный пользователем.
- `title` (str): Заголовок.
- `transitionType` (TransitionType): Тип перехода.

### `AdScriptId`

Идентификатор рекламного скрипта.

- `scriptId` (str): Идентификатор скрипта.
- `debuggerId` (str): Идентификатор отладчика.

### `OriginTrialToken`

Токен пробной версии Origin Trial.

- `origin` (str): Источник.
- `matchSubDomains` (bool): Совпадают ли поддомены.
- `trialName` (str): Имя пробной версии.
- `expiryTime` (str): Время истечения срока действия.
- `isThirdParty` (bool): Является ли сторонним.
- `usageRestriction` (NotRequired[OriginTrialUsageRestriction]): Ограничение использования.

### `OriginTrialTokenWithStatus`

Токен пробной версии Origin Trial со статусом.

- `rawTokenText` (str): Необработанный текст токена.
- `parsedTokenText` (NotRequired[OriginTrialToken]): Разобранный текст токена.
- `status` (OriginTrialTokenStatus): Статус.

### `OriginTrial`

Пробная версия Origin Trial.

- `trialName` (str): Имя пробной версии.
- `status` (OriginTrialStatus): Статус.
- `tokenWithStatus` (list[OriginTrialTokenWithStatus]): Токен со статусом.

### `PermissionsPolicyBlockLocator`

Локатор блокировки политики разрешений.

- `frameId` (str): Идентификатор фрейма.
- `blockReason` (PermissionsPolicyBlockReason): Причина блокировки.

### `PermissionsPolicyFeatureState`

Состояние функции политики разрешений.

- `feature` (PermissionsPolicyFeature): Функция.
- `allowed` (bool): Разрешено.
- `locator` (NotRequired[PermissionsPolicyBlockLocator]): Локатор.

### `JavascriptDialogOpeningEventParams`

Параметры события открытия диалогового окна JavaScript.

- `url` (str): URL.
- `frameId` (str): Идентификатор фрейма.
- `message` (str): Сообщение.
- `type` (DialogType): Тип.
- `hasBrowserHandler` (bool): Имеет ли обработчик браузера.
- `defaultPrompt` (NotRequired[str]): Подсказка по умолчанию.

### `JavascriptDialogOpeningEvent`

Событие открытия диалогового окна JavaScript.

- `method` (str): Метод.
- `params` (NotRequired[JavascriptDialogOpeningEventParams]): Параметры.
