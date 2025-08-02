## Содержание

- [Модуль `pydoll.commands.dom_commands`](#модуль-pydollcommandsdom_commands)
  - [Класс `DomCommands`](#класс-domcommands)
    - [Методы](#методы)
      - [`describe_node`](#describe_nodenode_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none-depth-optionalint--none-pierce-optionalbool--none---commanddescribenoderesponse)
      - [`disable`](#disable---commandresponse)
      - [`enable`](#enableinclude_whitespace-optionalincludewhitespace--none---commandresponse)
      - [`focus`](#focusnode_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none---commandresponse)
      - [`get_attributes`](#get_attributesnode_id-int---commandgetattributesresponse)
      - [`get_box_model`](#get_box_modelnode_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none---commandgetboxmodelresponse)
      - [`get_document`](#get_documentdepth-optionalint--none-pierce-optionalbool--none---commandgetdocumentresponse)
      - [`get_node_for_location`](#get_node_for_locationx-int-y-int-include_user_agent_shadow_dom-optionalbool--none-ignore_pointer_events_none-optionalbool--none---commandgetnodeforlocationresponse)
      - [`get_outer_html`](#get_outer_htmlnode_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none---commandgetouterhtmlresponse)
      - [`hide_highlight`](#hide_highlight---commandresponse)
      - [`highlight_node`](#highlight_node---commandresponse)
      - [`highlight_rect`](#highlight_rect---commandresponse)
      - [`move_to`](#move_tonode_id-int-target_node_id-int-insert_before_node_id-optionalint--none---commandmovetoresponse)
      - [`query_selector`](#query_selectornode_id-int-selector-str---commandqueryselectorresponse)
      - [`query_selector_all`](#query_selector_allnode_id-int-selector-str---commandqueryselectorallresponse)
      - [`remove_attribute`](#remove_attributenode_id-int-name-str---commandresponse)
      - [`remove_node`](#remove_nodenode_id-int---commandresponse)
      - [`request_child_nodes`](#request_child_nodesnode_id-int-depth-optionalint--none-pierce-optionalbool--none---commandresponse)
      - [`request_node`](#request_nodeobject_id-str---commandrequestnoderesponse)
      - [`resolve_node`](#resolve_nodenode_id-optionalint--none-backend_node_id-optionalint--none-object_group-optionalstr--none-execution_context_id-optionalint--none---commandresolvenoderesponse)
      - [`scroll_into_view_if_needed`](#scroll_into_view_if_needednode_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none-rect-optionalrect--none---commandresponse)
      - [`set_attributes_as_text`](#set_attributes_as_textnode_id-int-text-str-name-optionalstr--none---commandresponse)
      - [`set_attribute_value`](#set_attribute_valuenode_id-int-name-str-value-str---commandresponse)
      - [`set_file_input_files`](#set_file_input_filesfiles-liststr-node_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none---commandresponse)
      - [`set_node_name`](#set_node_namenode_id-int-name-str---commandsetnodenameresponse)
      - [`set_node_value`](#set_node_valuenode_id-int-value-str---commandresponse)
      - [`set_outer_html`](#set_outer_htmlnode_id-int-outer_html-str---commandresponse)
      - [`collect_class_names_from_subtree`](#collect_class_names_from_subtreenode_id-int---commandcollectclassnamesfromsubtreeresponse)
      - [`copy_to`](#copy_tonode_id-int-target_node_id-int-insert_before_node_id-optionalint--none---commandcopytoresponse)
      - [`discard_search_results`](#discard_search_resultssearch_id-str---commandresponse)
      - [`get_anchor_element`](#get_anchor_elementnode_id-int-anchor_specifier-optionalstr--none---commandgetanchorelementresponse)
      - [`get_container_for_node`](#get_container_for_nodenode_id-int-container_name-optionalstr--none-physical_axes-optionalphysicalaxes--none-logical_axes-optionallogicalaxes--none-queries_scroll_state-optionalbool--none---commandgetcontainerfornoderesponse)
      - [`get_content_quads`](#get_content_quadsnode_id-optionalint--none-backend_node_id-optionalint--none-object_id-optionalstr--none---commandgetcontentquadsresponse)
      - [`get_detached_dom_nodes`](#get_detached_dom_nodes---commandgetdetacheddomnodesresponse)
      - [`get_element_by_relation`](#get_element_by_relationnode_id-int-relation-elementrelation---commandgetelementbyrelationresponse)
      - [`get_file_info`](#get_file_infoobject_id-str---commandgetfileinforesponse)
      - [`get_frame_owner`](#get_frame_ownerframe_id-str---commandgetframeownerresponse)
      - [`get_nodes_for_subtree_by_style`](#get_nodes_for_subtree_by_stylenode_id-int-computed_styles-listcsscomputedstyleproperty-pierce-optionalbool--none---commandgetnodesforsubtreebystyleresponse)
      - [`get_node_stack_traces`](#get_node_stack_tracesnode_id-int---commandgetnodestacktracesresponse)
      - [`get_querying_descendants_for_container`](#get_querying_descendants_for_containernode_id-int---commandgetqueryingdescendantforcontainerresponse)
      - [`get_relayout_boundary`](#get_relayout_boundarynode_id-int---commandgetrelayoutboundaryresponse)
      - [`get_search_results`](#get_search_resultssearch_id-str-from_index-int-to_index-int---commandgetsearchresultsresponse)
      - [`get_top_layer_elements`](#get_top_layer_elements---commandgettoplayerelementsresponse)
      - [`mark_undoable_state`](#mark_undoable_state---commandresponse)
      - [`perform_search`](#perform_searchquery-str-include_user_agent_shadow_dom-optionalbool--none---commandperformsearchresponse)
      - [`push_node_by_path_to_frontend`](#push_node_by_path_to_frontendpath-str---commandpushnodebypathtofrontendresponse)
      - [`push_nodes_by_backend_ids_to_frontend`](#push_nodes_by_backend_ids_to_frontendbackend_node_ids-listint---commandpushnodesbybackendidstofrontendresponse)
      - [`redo`](#redo---commandresponse)
      - [`set_inspected_node`](#set_inspected_nodenode_id-int---commandresponse)
      - [`set_node_stack_traces_enabled`](#set_node_stack_traces_enabledenable-bool---commandresponse)
      - [`undo`](#undo---commandresponse)

# Модуль `pydoll.commands.dom_commands`

Этот модуль содержит класс `DomCommands`, который предоставляет набор команд для взаимодействия с объектной моделью документа (DOM) в браузере на основе Chrome DevTools Protocol (CDP).

## Класс `DomCommands`

Предоставляет команды для взаимодействия с DOM.

### Методы

#### `describe_node(node_id=None, backend_node_id=None, object_id=None, depth=None, pierce=None) -> Command[DescribeNodeResponse]`

Описывает узел DOM, идентифицированный по его ID без необходимости включения домена.

- `node_id`: Идентификатор узла, известный клиенту.
- `backend_node_id`: Идентификатор внутреннего узла, используемый браузером.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- `depth`: Максимальная глубина, на которой должны быть получены дочерние элементы (по умолчанию 1). Используйте -1 для всего поддерева.
- `pierce`: Следует ли обходить iframe и теневые корни при возврате поддерева (по умолчанию false).
- **Возвращает**: Команду CDP, которая возвращает подробную информацию о запрошенном узле.

#### `disable() -> Command[Response]`

Отключает агент DOM для текущей страницы.

- **Возвращает**: Команду CDP для отключения домена DOM.

#### `enable(include_whitespace=None) -> Command[Response]`

Включает агент DOM для текущей страницы.

- `include_whitespace`: Следует ли включать текстовые узлы, содержащие только пробелы, в массив дочерних элементов возвращаемых узлов. Допустимые значения: "none", "all".
- **Возвращает**: Команду CDP для включения домена DOM.

#### `focus(node_id=None, backend_node_id=None, object_id=None) -> Command[Response]`

Устанавливает фокус на заданный элемент.

- `node_id`: Идентификатор узла для фокусировки.
- `backend_node_id`: Идентификатор внутреннего узла для фокусировки.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- **Возвращает**: Команду CDP для фокусировки на указанном элементе.

#### `get_attributes(node_id: int) -> Command[GetAttributesResponse]`

Возвращает атрибуты для указанного узла.

- `node_id`: Идентификатор узла, для которого нужно получить атрибуты.
- **Возвращает**: Команду CDP, которая возвращает чередующийся массив имен и значений атрибутов узла.

#### `get_box_model(node_id=None, backend_node_id=None, object_id=None) -> Command[GetBoxModelResponse]`

Возвращает информацию о блочной модели для указанного узла.

- `node_id`: Идентификатор узла.
- `backend_node_id`: Идентификатор внутреннего узла.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- **Возвращает**: Команду CDP, которая возвращает блочную модель для узла, включая координаты для полей содержимого, отступов, границ и внешних отступов.

#### `get_document(depth=None, pierce=None) -> Command[GetDocumentResponse]`

Возвращает корневой узел DOM (и, при необходимости, поддерево) вызывающему объекту.

- `depth`: Максимальная глубина, на которой должны быть получены дочерние элементы (по умолчанию 1). Используйте -1 для всего поддерева.
- `pierce`: Следует ли обходить iframe и теневые корни при возврате поддерева (по умолчанию false).
- **Возвращает**: Команду CDP, которая возвращает корневой узел DOM.

#### `get_node_for_location(x: int, y: int, include_user_agent_shadow_dom=None, ignore_pointer_events_none=None) -> Command[GetNodeForLocationResponse]`

Возвращает идентификатор узла по заданному местоположению на странице.

- `x`: X-координата относительно области просмотра основного фрейма в CSS-пикселях.
- `y`: Y-координата относительно области просмотра основного фрейма в CSS-пикселях.
- `include_user_agent_shadow_dom`: Следует ли включать узлы в теневые корни пользовательского агента.
- `ignore_pointer_events_none`: Следует ли игнорировать `pointer-events:none` и проверять элементы под ними.
- **Возвращает**: Команду CDP, которая возвращает узел по заданному местоположению.

#### `get_outer_html(node_id=None, backend_node_id=None, object_id=None) -> Command[GetOuterHTMLResponse]`

Возвращает HTML-разметку узла, включая сам узел и всех его дочерних элементов.

- `node_id`: Идентификатор узла.
- `backend_node_id`: Идентификатор внутреннего узла.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- **Возвращает**: Команду CDP, которая возвращает внешнюю HTML-разметку узла.

#### `hide_highlight() -> Command[Response]`

Скрывает любое выделение элемента DOM.

- **Возвращает**: Команду CDP для скрытия выделения элементов DOM.

#### `highlight_node() -> Command[Response]`

Выделяет узел DOM.

- **Возвращает**: Команду CDP для выделения узла DOM.

#### `highlight_rect() -> Command[Response]`

Выделяет заданный прямоугольник.

- **Возвращает**: Команду CDP для выделения прямоугольной области.

#### `move_to(node_id: int, target_node_id: int, insert_before_node_id=None) -> Command[MoveToResponse]`

Перемещает узел в новый контейнер, помещая его перед заданным якорем.

- `node_id`: Идентификатор узла для перемещения.
- `target_node_id`: Идентификатор элемента, в который нужно поместить перемещенный узел.
- `insert_before_node_id`: Поместить узел перед этим узлом (если отсутствует, перемещенный узел становится последним дочерним элементом `target_node_id`).
- **Возвращает**: Команду CDP для перемещения узла, возвращающую новый идентификатор перемещенного узла.

#### `query_selector(node_id: int, selector: str) -> Command[QuerySelectorResponse]`

Выполняет `querySelector` на заданном узле.

- `node_id`: Идентификатор узла для запроса.
- `selector`: Строка CSS-селектора.
- **Возвращает**: Команду CDP, которая возвращает первый элемент, соответствующий селектору.

#### `query_selector_all(node_id: int, selector: str) -> Command[QuerySelectorAllResponse]`

Выполняет `querySelectorAll` на заданном узле.

- `node_id`: Идентификатор узла для запроса.
- `selector`: Строка CSS-селектора.
- **Возвращает**: Команду CDP, которая возвращает все элементы, соответствующие селектору.

#### `remove_attribute(node_id: int, name: str) -> Command[Response]`

Удаляет атрибут с заданным именем из элемента с заданным идентификатором.

- `node_id`: Идентификатор элемента, из которого нужно удалить атрибут.
- `name`: Имя атрибута для удаления.
- **Возвращает**: Команду CDP для удаления указанного атрибута.

#### `remove_node(node_id: int) -> Command[Response]`

Удаляет узел с заданным идентификатором.

- `node_id`: Идентификатор узла для удаления.
- **Возвращает**: Команду CDP для удаления указанного узла.

#### `request_child_nodes(node_id: int, depth=None, pierce=None) -> Command[Response]`

Запрашивает возврат дочерних элементов узла с заданным идентификатором вызывающему объекту.

- `node_id`: Идентификатор узла, для которого нужно получить дочерние элементы.
- `depth`: Максимальная глубина, на которой должны быть получены дочерние элементы (по умолчанию 1). Используйте -1 для всего поддерева.
- `pierce`: Следует ли обходить iframe и теневые корни.
- **Возвращает**: Команду CDP для запроса дочерних узлов.

#### `request_node(object_id: str) -> Command[RequestNodeResponse]`

Запрашивает отправку узла вызывающему объекту, учитывая ссылку на объект узла JavaScript.

- `object_id`: Идентификатор JavaScript-объекта для преобразования в узел.
- **Возвращает**: Команду CDP, которая возвращает идентификатор узла для заданного объекта.

#### `resolve_node(node_id=None, backend_node_id=None, object_group=None, execution_context_id=None) -> Command[ResolveNodeResponse]`

Разрешает объект узла JavaScript для заданного `NodeId` или `BackendNodeId`.

- `node_id`: Идентификатор узла для разрешения.
- `backend_node_id`: Идентификатор внутреннего узла для разрешения.
- `object_group`: Символическое имя группы, которое может быть использовано для освобождения нескольких объектов.
- `execution_context_id`: Идентификатор контекста выполнения, в котором нужно разрешить узел.
- **Возвращает**: Команду CDP, которая возвращает обертку JavaScript-объекта для узла.

#### `scroll_into_view_if_needed(node_id=None, backend_node_id=None, object_id=None, rect=None) -> Command[Response]`

Прокручивает указанный узел в область просмотра, если он еще не виден.

- `node_id`: Идентификатор узла.
- `backend_node_id`: Идентификатор внутреннего узла.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- `rect`: Необязательный прямоугольник для прокрутки в область просмотра, относительно границ узла.
- **Возвращает**: Команду CDP для прокрутки элемента в область просмотра.

#### `set_attributes_as_text(node_id: int, text: str, name=None) -> Command[Response]`

Устанавливает атрибут для элемента с заданным идентификатором, используя текстовое представление.

- `node_id`: Идентификатор элемента, для которого нужно установить атрибут.
- `text`: Текст с новым значением атрибута.
- `name`: Имя атрибута для замены новым текстовым значением.
- **Возвращает**: Команду CDP для установки атрибута в виде текста.

#### `set_attribute_value(node_id: int, name: str, value: str) -> Command[Response]`

Устанавливает атрибут для элемента с заданным идентификатором.

- `node_id`: Идентификатор элемента, для которого нужно установить атрибут.
- `name`: Имя атрибута.
- `value`: Значение атрибута.
- **Возвращает**: Команду CDP для установки значения атрибута.

#### `set_file_input_files(files: list[str], node_id=None, backend_node_id=None, object_id=None) -> Command[Response]`

Устанавливает файлы для заданного элемента ввода файла.

- `files`: Список путей к файлам для установки.
- `node_id`: Идентификатор узла.
- `backend_node_id`: Идентификатор внутреннего узла.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- **Возвращает**: Команду CDP для установки файлов для элемента ввода файла.

#### `set_node_name(node_id: int, name: str) -> Command[SetNodeNameResponse]`

Устанавливает имя узла для узла с заданным идентификатором.

- `node_id`: Идентификатор узла, для которого нужно установить имя.
- `name`: Новое имя узла.
- **Возвращает**: Команду CDP, которая возвращает новый идентификатор узла после изменения имени.

#### `set_node_value(node_id: int, value: str) -> Command[Response]`

Устанавливает значение узла для узла с заданным идентификатором.

- `node_id`: Идентификатор узла, для которого нужно установить значение.
- `value`: Новое значение узла.
- **Возвращает**: Команду CDP для установки значения узла.

#### `set_outer_html(node_id: int, outer_html: str) -> Command[Response]`

Устанавливает HTML-разметку узла, заменяя существующую.

- `node_id`: Идентификатор узла, для которого нужно установить внешнюю HTML-разметку.
- `outer_html`: HTML-разметка для установки.
- **Возвращает**: Команду CDP для установки внешней HTML-разметки узла.

#### `collect_class_names_from_subtree(node_id: int) -> Command[CollectClassNamesFromSubtreeResponse]`

Собирает имена классов для узла с заданным идентификатором и всех его дочерних элементов.

- `node_id`: Идентификатор узла, для которого нужно собрать имена классов.
- **Возвращает**: Команду CDP, которая возвращает список всех уникальных имен классов в поддереве.

#### `copy_to(node_id: int, target_node_id: int, insert_before_node_id=None) -> Command[CopyToResponse]`

Создает глубокую копию указанного узла и помещает ее в целевой контейнер.

- `node_id`: Идентификатор узла для копирования.
- `target_node_id`: Идентификатор элемента, в который нужно поместить копию.
- `insert_before_node_id`: Поместить копию перед этим узлом (если отсутствует, копия становится последним дочерним элементом `target_node_id`).
- **Возвращает**: Команду CDP, которая возвращает идентификатор новой копии.

#### `discard_search_results(search_id: str) -> Command[Response]`

Отбрасывает результаты поиска из сессии с заданным идентификатором.

- `search_id`: Уникальный идентификатор сессии поиска.
- **Возвращает**: Команду CDP для отбрасывания результатов поиска.

#### `get_anchor_element(node_id: int, anchor_specifier=None) -> Command[GetAnchorElementResponse]`

Находит ближайший родительский узел, который является элементом-якорем для заданного узла.

- `node_id`: Идентификатор узла для поиска якоря.
- `anchor_specifier`: Необязательный спецификатор для свойств тега якоря.
- **Возвращает**: Команду CDP, которая возвращает информацию об узле элемента-якоря.

#### `get_container_for_node(node_id: int, container_name=None, physical_axes=None, logical_axes=None, queries_scroll_state=None) -> Command[GetContainerForNodeResponse]`

Находит содержащий элемент для заданного узла на основе указанных параметров.

- `node_id`: Идентификатор узла, для которого нужно найти контейнер.
- `container_name`: Имя контейнера для поиска (например, 'scrollable', 'flex').
- `physical_axes`: Физические оси для рассмотрения (Horizontal, Vertical, Both).
- `logical_axes`: Логические оси для рассмотрения (Inline, Block, Both).
- `queries_scroll_state`: Следует ли запрашивать состояние прокрутки.
- **Возвращает**: Команду CDP, которая возвращает информацию о содержащем элементе.

#### `get_content_quads(node_id=None, backend_node_id=None, object_id=None) -> Command[GetContentQuadsResponse]`

Возвращает квады, описывающие положение узла на странице.

- `node_id`: Идентификатор узла.
- `backend_node_id`: Идентификатор внутреннего узла.
- `object_id`: Идентификатор JavaScript-объекта-обертки узла.
- **Возвращает**: Команду CDP, которая возвращает квады, описывающие положение узла.

#### `get_detached_dom_nodes() -> Command[GetDetachedDomNodesResponse]`

Возвращает информацию об отсоединенных элементах дерева DOM.

- **Возвращает**: Команду CDP, которая возвращает информацию об отсоединенных узлах DOM.

#### `get_element_by_relation(node_id: int, relation: ElementRelation) -> Command[GetElementByRelationResponse]`

Извлекает элемент, связанный с заданным, указанным способом.

- `node_id`: Идентификатор ссылочного узла.
- `relation`: Тип отношения (например, `nextSibling`, `previousSibling`, `firstChild`).
- **Возвращает**: Команду CDP, которая возвращает связанный узел элемента.

#### `get_file_info(object_id: str) -> Command[GetFileInfoResponse]`

Возвращает информацию о файле для заданного объекта `File`.

- `object_id`: Идентификатор JavaScript-объекта `File`, для которого нужно получить информацию.
- **Возвращает**: Команду CDP, которая возвращает информацию о файле.

#### `get_frame_owner(frame_id: str) -> Command[GetFrameOwnerResponse]`

Возвращает элемент iframe, которому принадлежит заданный фрейм.

- `frame_id`: Идентификатор фрейма, для которого нужно получить элемент-владелец.
- **Возвращает**: Команду CDP, которая возвращает элемент-владелец фрейма.

#### `get_nodes_for_subtree_by_style(node_id: int, computed_styles: list[CSSComputedStyleProperty], pierce=None) -> Command[GetNodesForSubtreeByStyleResponse]`

Находит узлы с заданным вычисленным стилем в поддереве.

- `node_id`: Узел, с которого начинается поиск.
- `computed_styles`: Список вычисленных свойств стиля для сопоставления.
- `pierce`: Следует ли обходить iframe и теневые корни.
- **Возвращает**: Команду CDP, которая возвращает узлы, соответствующие указанным стилям.

#### `get_node_stack_traces(node_id: int) -> Command[GetNodeStackTracesResponse]`

Получает трассировки стека, связанные с определенным узлом.

- `node_id`: Идентификатор узла, для которого нужно получить трассировки стека.
- **Возвращает**: Команду CDP, которая возвращает трассировки стека, связанные с узлом.

#### `get_querying_descendants_for_container(node_id: int) -> Command[GetQueryingDescendantForContainerResponse]`

Возвращает запрашиваемые потомки для контейнера.

- `node_id`: Идентификатор узла контейнера, для которого нужно найти запрашиваемых потомков.
- **Возвращает**: Команду CDP, которая возвращает информацию о запрашиваемых потомках.

#### `get_relayout_boundary(node_id: int) -> Command[GetRelayoutBoundaryResponse]`

Возвращает корень границы перекомпоновки для заданного узла.

- `node_id`: Идентификатор узла, для которого нужно найти границу перекомпоновки.
- **Возвращает**: Команду CDP, которая возвращает узел границы перекомпоновки.

#### `get_search_results(search_id: str, from_index: int, to_index: int) -> Command[GetSearchResultsResponse]`

Возвращает результаты поиска из заданного `fromIndex` до заданного `toIndex` из поиска.

- `search_id`: Уникальный идентификатор сессии поиска из `performSearch`.
- `from_index`: Начальный индекс для получения результатов.
- `to_index`: Конечный индекс для получения результатов (исключительно).
- **Возвращает**: Команду CDP, которая возвращает запрошенные результаты поиска.

#### `get_top_layer_elements() -> Command[GetTopLayerElementsResponse]`

Возвращает все элементы верхнего уровня в документе.

- **Возвращает**: Команду CDP, которая возвращает информацию об элементах верхнего уровня.

#### `mark_undoable_state() -> Command[Response]`

Помечает последнее отменяемое состояние.

- **Возвращает**: Команду CDP для пометки текущего состояния как отменяемого.

#### `perform_search(query: str, include_user_agent_shadow_dom=None) -> Command[PerformSearchResponse]`

Ищет заданную строку в дереве DOM.

- `query`: Обычный текст, селектор CSS или запрос XPath.
- `include_user_agent_shadow_dom`: `True` для включения теневого DOM пользовательского агента в поиск.
- **Возвращает**: Команду CDP, которая возвращает идентификатор и количество результатов поиска.

#### `push_node_by_path_to_frontend(path: str) -> Command[PushNodeByPathToFrontendResponse]`

Запрашивает отправку узла вызывающему объекту по его пути.

- `path`: Путь к узлу в проприетарном формате.
- **Возвращает**: Команду CDP, которая возвращает идентификатор узла для узла.

#### `push_nodes_by_backend_ids_to_frontend(backend_node_ids: list[int]) -> Command[PushNodesByBackendIdsToFrontendResponse]`

Запрашивает отправку партии узлов вызывающему объекту по их идентификаторам внутренних узлов.

- `backend_node_ids`: Массив идентификаторов внутренних узлов.
- **Возвращает**: Команду CDP, которая возвращает массив идентификаторов узлов.

#### `redo() -> Command[Response]`

Повторяет последнее отмененное действие.

- **Возвращает**: Команду CDP для повтора последнего отмененного действия.

#### `set_inspected_node(node_id: int) -> Command[Response]`

Позволяет консоли ссылаться на узел с заданным идентификатором с помощью API командной строки `$x`.

- `node_id`: Идентификатор узла DOM, который будет доступен с помощью API командной строки `$x`.
- **Возвращает**: Команду CDP для установки проверяемого узла.

#### `set_node_stack_traces_enabled(enable: bool) -> Command[Response]`

Устанавливает, следует ли захватывать трассировки стека для узлов.

- `enable`: Включить или отключить сбор трассировок стека.
- **Возвращает**: Команду CDP для включения или отключения трассировок стека узлов.

#### `undo() -> Command[Response]`

Отменяет последнее выполненное действие.

- **Возвращает**: Команду CDP для отмены последнего выполненного действия.
