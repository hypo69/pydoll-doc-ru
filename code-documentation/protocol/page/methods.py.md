## Содержание

- [Модуль `pydoll.protocol.page.methods`](#модуль-pydollprotocolpagemethods)
  - [Класс `PageMethod`](#класс-pagemethod)
    - [Методы](#методы)
      - [`ADD_SCRIPT_TO_EVALUATE_ON_NEW_DOCUMENT`](#add_script_to_evaluate_on_new_documentsource-str-world_name-optionalstr--none-include_command_line_api-optionalbool--none-run_immediately-optionalbool--none---commandaddscripttoevaluateonnewdocumentresponse)
      - [`BRING_TO_FRONT`](#bring_to_front---commandresponse)
      - [`CAPTURE_SCREENSHOT`](#capture_screenshotformat-optionalscreenshotformat--none-quality-optionalint--none-clip-optionalviewport--none-from_surface-optionalbool--none-capture_beyond_viewport-optionalbool--none-optimize_for_speed-optionalbool--none---commandcapturescreenshotresponse)
      - [`CLOSE`](#close---commandresponse)
      - [`CREATE_ISOLATED_WORLD`](#create_isolated_worldframe_id-str-world_name-optionalstr--none-grant_universal_access-optionalbool--none---commandcreateisolatedworldresponse)
      - [`DISABLE`](#disable---commandresponse)
      - [`ENABLE`](#enableenable_file_chooser_opened_event-optionalbool--none---commandresponse)
      - [`GET_APP_MANIFEST`](#get_app_manifestmanifest_id-optionalstr--none---commandgetappmanifestresponse)
      - [`GET_FRAME_TREE`](#get_frame_tree---commandgetframetreeresponse)
      - [`GET_LAYOUT_METRICS`](#get_layout_metrics---commandgetlayoutmetricsresponse)
      - [`GET_NAVIGATION_HISTORY`](#get_navigation_history---commandgetnavigationhistoryresponse)
      - [`HANDLE_JAVASCRIPT_DIALOG`](#handle_javascript_dialogaccept-bool-prompt_text-optionalstr--none---commandresponse)
      - [`NAVIGATE`](#navigateurl-str-referrer-optionalstr--none-transition_type-optionaltransitiontype--none-frame_id-optionalstr--none-referrer_policy-optionalreferrerpolicy--none---commandnavigateresponse)
      - [`NAVIGATE_TO_HISTORY_ENTRY`](#navigate_to_history_entryentry_id-int---commandresponse)
      - [`PRINT_TO_PDF`](#print_to_pdflandscape-optionalbool--none-display_header_footer-optionalbool--none-print_background-optionalbool--none-scale-optionalfloat--none-paper_width-optionalfloat--none-paper_height-optionalfloat--none-margin_top-optionalfloat--none-margin_bottom-optionalfloat--none-margin_left-optionalfloat--none-margin_right-optionalfloat--none-page_ranges-optionalstr--none-header_template-optionalstr--none-footer_template-optionalstr--none-prefer_css_page_size-optionalbool--none-transfer_mode-optionaltransfermode--none-generate_tagged_pdf-optionalbool--none-generate_document_outline-optionalbool--none---commandprinttopdfresponse)
      - [`RELOAD`](#reloadignore_cache-optionalbool--none-script_to_evaluate_on_load-optionalstr--none-loader_id-optionalstr--none---commandresponse)
      - [`REMOVE_SCRIPT_TO_EVALUATE_ON_NEW_DOCUMENT`](#remove_script_to_evaluate_on_new_documentidentifier-str---commandresponse)
      - [`RESET_NAVIGATION_HISTORY`](#reset_navigation_history---commandresponse)
      - [`SET_BYPASS_CSP`](#set_bypass_cspenabled-bool---commandresponse)
      - [`SET_DOCUMENT_CONTENT`](#set_document_contentframe_id-str-html-str---commandresponse)
      - [`SET_INTERCEPT_FILE_CHOOSER_DIALOG`](#set_intercept_file_chooser_dialogenabled-bool---commandresponse)
      - [`SET_LIFECYCLE_EVENTS_ENABLED`](#set_lifecycle_events_enabledenabled-bool---commandresponse)
      - [`STOP_LOADING`](#stop_loading---commandresponse)
      - [`ADD_COMPILATION_CACHE`](#add_compilation_cacheurl-str-data-str---commandresponse)
      - [`CAPTURE_SNAPSHOT`](#capture_snapshotformat-literalmhtml--mhtml---commandcapturesnapshotresponse)
      - [`CLEAR_COMPILATION_CACHE`](#clear_compilation_cache---commandresponse)
      - [`CRASH`](#crash---commandresponse)
      - [`GENERATE_TEST_REPORT`](#generate_test_reportmessage-str-group-optionalstr--none---commandresponse)
      - [`GET_AD_SCRIPT_ANCESTRY_IDS`](#get_ad_script_ancestry_idsframe_id-str---commandgetadscriptancestryidsresponse)
      - [`GET_APP_ID`](#get_app_idapp_id-optionalstr--none-recommended_id-optionalstr--none---commandgetappidresponse)
      - [`GET_INSTALLABILITY_ERRORS`](#get_installability_errors---commandgetinstallabilityerrorsresponse)
      - [`GET_ORIGIN_TRIALS`](#get_origin_trialsframe_id-str---commandgetorigintrialsresponse)
      - [`GET_PERMISSIONS_POLICY_STATE`](#get_permissions_policy_stateframe_id-str---commandgetpermissionspolicystateresponse)
      - [`GET_RESOURCE_CONTENT`](#get_resource_contentframe_id-str-url-str---commandgetresourcecontentresponse)
      - [`GET_RESOURCE_TREE`](#get_resource_tree---commandgetresourcetreeresponse)
      - [`PRODUCE_COMPILATION_CACHE`](#produce_compilation_cachescripts-listcompilationcacheparams---commandresponse)
      - [`SCREENCAST_FRAME_ACK`](#screencast_frame_acksession_id-str---commandresponse)
      - [`SEARCH_IN_RESOURCE`](#search_in_resourceframe_id-str-url-str-query-str-case_sensitive-optionalbool--none-is_regex-optionalbool--none---commandsearchinresourceresponse)
      - [`SET_AD_BLOCKING_ENABLED`](#set_ad_blocking_enabledenabled-bool---commandresponse)
      - [`SET_FONT_FAMILIES`](#set_font_familiesfont_families-fontfamilies-for_scripts-listscriptfontfamilies---commandresponse)
      - [`SET_FONT_SIZES`](#set_font_sizesfont_sizes-fontsizes---commandresponse)
      - [`SET_PRERENDERING_ALLOWED`](#set_prerendering_allowedallowed-bool---commandresponse)
      - [`SET_RPH_REGISTRATION_MODE`](#set_rph_registration_modemode-autoresponsemode---commandresponse)
      - [`SET_SPC_TRANSACTION_MODE`](#set_spc_transaction_modemode-autoresponsemode---commandresponse)
      - [`SET_WEB_LIFECYCLE_STATE`](#set_web_lifecycle_statestate-weblifecyclestate---commandresponse)
      - [`START_SCREENCAST`](#start_screencastformat-screencastformat-quality-optionalint--none-max_width-optionalint--none-max_height-optionalint--none-every_nth_frame-optionalint--none---commandresponse)
      - [`STOP_SCREENCAST`](#stop_screencast---commandresponse)
      - [`WAIT_FOR_DEBUGGER`](#wait_for_debugger---commandresponse)

# Модуль `pydoll.protocol.page.methods`

Этот модуль определяет методы, доступные в домене `Page` протокола Chrome DevTools Protocol (CDP). Эти методы используются для взаимодействия со страницами браузера.

## Класс `PageMethod`

Перечисление, содержащее имена методов, связанных со страницей.

### Методы

- `ADD_SCRIPT_TO_EVALUATE_ON_NEW_DOCUMENT = 'Page.addScriptToEvaluateOnNewDocument'`: Добавляет скрипт, который будет выполняться при создании нового документа.
- `BRING_TO_FRONT = 'Page.bringToFront'`: Переводит страницу на передний план.
- `CAPTURE_SCREENSHOT = 'Page.captureScreenshot'`: Захватывает скриншот текущей страницы.
- `CLOSE = 'Page.close'`: Закрывает текущую страницу.
- `CREATE_ISOLATED_WORLD = 'Page.createIsolatedWorld'`: Создает изолированный мир для данного фрейма.
- `DISABLE = 'Page.disable'`: Отключает уведомления домена страницы.
- `ENABLE = 'Page.enable'`: Включает уведомления домена страницы.
- `GET_APP_MANIFEST = 'Page.getAppManifest'`: Получает манифест текущего документа.
- `GET_FRAME_TREE = 'Page.getFrameTree'`: Получает дерево фреймов для текущей страницы.
- `GET_LAYOUT_METRICS = 'Page.getLayoutMetrics'`: Получает метрики макета страницы.
- `GET_NAVIGATION_HISTORY = 'Page.getNavigationHistory'`: Получает историю навигации для текущей страницы.
- `HANDLE_JAVASCRIPT_DIALOG = 'Page.handleJavaScriptDialog'`: Обрабатывает диалоговое окно JavaScript.
- `NAVIGATE = 'Page.navigate'`: Переходит по указанному URL-адресу.
- `NAVIGATE_TO_HISTORY_ENTRY = 'Page.navigateToHistoryEntry'`: Переходит к определенной записи истории.
- `PRINT_TO_PDF = 'Page.printToPDF'`: Печатает текущую страницу в PDF.
- `RELOAD = 'Page.reload'`: Перезагружает текущую страницу.
- `REMOVE_SCRIPT_TO_EVALUATE_ON_NEW_DOCUMENT = 'Page.removeScriptToEvaluateOnNewDocument'`: Удаляет скрипт, который был добавлен для выполнения в новых документах.
- `RESET_NAVIGATION_HISTORY = 'Page.resetNavigationHistory'`: Сбрасывает историю навигации.
- `SET_BYPASS_CSP = 'Page.setBypassCSP'`: Переключает обход CSP страницы.
- `SET_DOCUMENT_CONTENT = 'Page.setDocumentContent'`: Устанавливает содержимое документа фрейма.
- `SET_INTERCEPT_FILE_CHOOSER_DIALOG = 'Page.setInterceptFileChooserDialog'`: Устанавливает, следует ли перехватывать диалоговые окна выбора файла.
- `SET_LIFECYCLE_EVENTS_ENABLED = 'Page.setLifecycleEventsEnabled'`: Включает/отключает события жизненного цикла.
- `STOP_LOADING = 'Page.stopLoading'`: Останавливает загрузку страницы.
- `ADD_COMPILATION_CACHE = 'Page.addCompilationCache'`: Добавляет запись в кэш компиляции.
- `CAPTURE_SNAPSHOT = 'Page.captureSnapshot'`: Захватывает снимок страницы.
- `CLEAR_COMPILATION_CACHE = 'Page.clearCompilationCache'`: Очищает кэш компиляции.
- `CRASH = 'Page.crash'`: Аварийно завершает страницу.
- `GENERATE_TEST_REPORT = 'Page.generateTestReport'`: Генерирует тестовый отчет.
- `GET_AD_SCRIPT_ANCESTRY_IDS = 'Page.getAdScriptAncestryIds'`: Получает идентификаторы предков рекламного скрипта для данного фрейма.
- `GET_APP_ID = 'Page.getAppId'`: Получает идентификатор приложения.
- `GET_INSTALLABILITY_ERRORS = 'Page.getInstallabilityErrors'`: Получает ошибки установки.
- `GET_ORIGIN_TRIALS = 'Page.getOriginTrials'`: Получает пробные версии Origin Trial для данного источника.
- `GET_PERMISSIONS_POLICY_STATE = 'Page.getPermissionsPolicyState'`: Получает состояние политики разрешений.
- `GET_RESOURCE_CONTENT = 'Page.getResourceContent'`: Получает содержимое ресурса.
- `GET_RESOURCE_TREE = 'Page.getResourceTree'`: Получает дерево ресурсов.
- `PRODUCE_COMPILATION_CACHE = 'Page.produceCompilationCache'`: Создает запись в кэше компиляции.
- `SCREENCAST_FRAME_ACK = 'Page.screencastFrameAck'`: Подтверждает кадр скринкаста.
- `SEARCH_IN_RESOURCE = 'Page.searchInResource'`: Ищет строку в ресурсе.
- `SET_AD_BLOCKING_ENABLED = 'Page.setAdBlockingEnabled'`: Включает блокировку рекламы.
- `SET_FONT_FAMILIES = 'Page.setFontFamilies'`: Устанавливает семейства шрифтов.
- `SET_FONT_SIZES = 'Page.setFontSizes'`: Устанавливает размеры шрифтов.
- `SET_PRERENDERING_ALLOWED = 'Page.setPrerenderingAllowed'`: Разрешает предварительный рендеринг.
- `SET_RPH_REGISTRATION_MODE = 'Page.setRPHRegistrationMode'`: Устанавливает режим регистрации RPH.
- `SET_SPC_TRANSACTION_MODE = 'Page.setSPCTransactionMode'`: Устанавливает режим транзакций SPC.
- `SET_WEB_LIFECYCLE_STATE = 'Page.setWebLifecycleState'`: Устанавливает состояние жизненного цикла веб-страницы.
- `START_SCREENCAST = 'Page.startScreencast'`: Запускает скринкаст.
- `STOP_SCREENCAST = 'Page.stopScreencast'`: Останавливает скринкаст.
- `WAIT_FOR_DEBUGGER = 'Page.waitForDebugger'`: Ожидает отладчика.
