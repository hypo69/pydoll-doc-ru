## Содержание

- [Модуль `pydoll.browser.managers.proxy_manager`](#модуль-pydollbrowsermanagersproxy_manager)
  - [Класс `ProxyManager`](#класс-proxymanager)
    - [Методы](#методы)
      - [`__init__`](#__init__self-options)
      - [`get_proxy_credentials`](#get_proxy_credentialsself---tuplebool-tupleoptionalstr-optionalstr)
      - [`_find_proxy_argument`](#_find_proxy_argumentself---optionaltupleint-str)
      - [`_parse_proxy`](#_parse_proxyproxy_value---tuplebool-optionalstr-optionalstr-str)
      - [`_update_proxy_argument`](#_update_proxy_argumentself-index-clean_proxy)

# Модуль `pydoll.browser.managers.proxy_manager`

Этот модуль содержит класс `ProxyManager`, который управляет конфигурацией прокси и учетными данными для автоматизации CDP. Он извлекает встроенные учетные данные из URL-адресов прокси, защищает информацию аутентификации и очищает аргументы командной строки.

## Класс `ProxyManager`

Управляет конфигурацией прокси и учетными данными для автоматизации CDP.

### Методы

#### `__init__(self, options)`

Инициализирует менеджер прокси с опциями браузера.

- `options`: Опции браузера, потенциально содержащие конфигурацию прокси. Будут изменены, если найдены учетные данные.

#### `get_proxy_credentials(self) -> tuple[bool, tuple[Optional[str], Optional[str]]]`

Извлекает и защищает учетные данные аутентификации прокси. Ищет настройки прокси, извлекает встроенные учетные данные и очищает опции для предотвращения раскрытия учетных данных.

- **Возвращает**: Кортеж из (`has_private_proxy`, (`username`, `password`)).

#### `_find_proxy_argument(self) -> Optional[tuple[int, str]]`

Находит конфигурацию прокси-сервера в опциях браузера.

- **Возвращает**: Кортеж из (`index`, `proxy_url`), если найден, иначе `None`.

#### `_parse_proxy(proxy_value) -> tuple[bool, Optional[str], Optional[str], str]`

Статический метод, который разбирает URL-адрес прокси для извлечения учетных данных аутентификации.

- `proxy_value`: URL-адрес прокси, потенциально содержащий `username:password@server:port`.
- **Возвращает**: Кортеж из (`has_credentials`, `username`, `password`, `clean_proxy_url`).

#### `_update_proxy_argument(self, index, clean_proxy)`

Заменяет аргумент прокси версией без учетных данных.