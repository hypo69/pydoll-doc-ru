## Содержание

- [Модуль `pydoll.browser.chromium.edge`](#модуль-pydollbrowserchromiumedge)
  - [Класс `Edge`](#класс-edge)
    - [Методы](#методы)
      - [`__init__`](#__init__self-optionsnone-connection_portnone)
      - [`_get_default_binary_location`](#_get_default_binary_location)

# Модуль `pydoll.browser.chromium.edge`

Этот модуль содержит реализацию класса `Edge`, который наследуется от абстрактного базового класса `Browser` и предоставляет специфичную для Edge функциональность для автоматизации браузера с использованием Chrome DevTools Protocol (CDP).

## Класс `Edge`

Реализация браузера Edge для автоматизации CDP.

### Методы

#### `__init__(self, options=None, connection_port=None)`

Инициализирует экземпляр браузера Edge.

- `options`: Объекты `Options` для настройки Edge (по умолчанию, если `None`).
- `connection_port`: Порт WebSocket CDP (случайный, если `None`).

#### `_get_default_binary_location()`

Статический метод, который возвращает путь к исполняемому файлу Edge по умолчанию в зависимости от операционной системы.

- **Возвращает**: Путь к исполняемому файлу Edge.
- **Вызывает**:
    - `UnsupportedOS`: Если операционная система не поддерживается.
    - `ValueError`: Если исполняемый файл не найден по пути по умолчанию.