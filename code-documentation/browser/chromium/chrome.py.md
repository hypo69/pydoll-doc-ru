## Содержание

- [Модуль `pydoll.browser.chromium.chrome`](#модуль-pydollbrowserchromiumchrome)
  - [Класс `Chrome`](#класс-chrome)
    - [Методы](#методы)
      - [`__init__`](#__init__self-optionsnone-connection_portnone)
      - [`_get_default_binary_location`](#_get_default_binary_location)

# Модуль `pydoll.browser.chromium.chrome`

Этот модуль содержит реализацию класса `Chrome`, который наследуется от абстрактного базового класса `Browser` и предоставляет специфичную для Chrome функциональность для автоматизации браузера с использованием Chrome DevTools Protocol (CDP).

## Класс `Chrome`

Реализация браузера Chrome для автоматизации CDP.

### Методы

#### `__init__(self, options=None, connection_port=None)`

Инициализирует экземпляр браузера Chrome.

- `options`: Объекты `ChromiumOptions` для настройки Chrome (по умолчанию, если `None`).
- `connection_port`: Порт WebSocket CDP (случайный, если `None`).

#### `_get_default_binary_location()`

Статический метод, который возвращает путь к исполняемому файлу Chrome по умолчанию в зависимости от операционной системы.

- **Возвращает**: Путь к исполняемому файлу Chrome.
- **Вызывает**:
    - `UnsupportedOS`: Если операционная система не поддерживается.
    - `ValueError`: Если исполняемый файл не найден по пути по умолчанию.