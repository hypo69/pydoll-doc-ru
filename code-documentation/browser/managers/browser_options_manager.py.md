## Содержание

- [Модуль `pydoll.browser.managers.browser_options_manager`](#модуль-pydollbrowsermanagersbrowser_options_manager)
  - [Класс `ChromiumOptionsManager`](#класс-chromiumoptionsmanager)
    - [Методы](#методы)
      - [`__init__`](#__init__self-optionsnone)
      - [`initialize_options`](#initialize_optionsself---chromiumoptions)
      - [`add_default_arguments`](#add_default_argumentsself)

# Модуль `pydoll.browser.managers.browser_options_manager`

Этот модуль содержит класс `ChromiumOptionsManager`, который отвечает за управление конфигурацией опций для браузеров на основе Chromium. Он обрабатывает создание, проверку и применение аргументов CDP по умолчанию.

## Класс `ChromiumOptionsManager`

Управляет конфигурацией опций браузера для браузеров на основе Chromium.

### Методы

#### `__init__(self, options=None)`

Инициализирует менеджер опций.

- `options`: Необязательный объект `Options` для начальной настройки.

#### `initialize_options(self) -> ChromiumOptions`

Инициализирует и проверяет опции браузера. Если опции не предоставлены, создается экземпляр `ChromiumOptions`. Проверяет, является ли предоставленный объект опций экземпляром `ChromiumOptions`, и применяет аргументы CDP по умолчанию.

- **Возвращает**: Правильно сконфигурированный экземпляр `ChromiumOptions`.
- **Вызывает**: `InvalidOptionsObject`, если предоставленные опции не являются `ChromiumOptions`.

#### `add_default_arguments(self)`

Добавляет аргументы по умолчанию, необходимые для интеграции CDP, такие как `--no-first-run` и `--no-default-browser-check`.