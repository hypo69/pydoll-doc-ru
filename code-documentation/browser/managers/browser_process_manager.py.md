## Содержание

- [Модуль `pydoll.browser.managers.browser_process_manager`](#модуль-pydollbrowsermanagersbrowser_process_manager)
  - [Класс `BrowserProcessManager`](#класс-browserprocessmanager)
    - [Методы](#методы)
      - [`__init__`](#__init__self-process_creatornone)
      - [`start_browser_process`](#start_browser_processself-binary_location-port-arguments)
      - [`_default_process_creator`](#_default_process_creatorcommand)
      - [`stop_process`](#stop_processself)

# Модуль `pydoll.browser.managers.browser_process_manager`

Этот модуль содержит класс `BrowserProcessManager`, который управляет жизненным циклом процесса браузера для автоматизации CDP. Он отвечает за создание, мониторинг и завершение процессов браузера с надлежащей очисткой ресурсов и корректным завершением работы.

## Класс `BrowserProcessManager`

Управляет жизненным циклом процесса браузера для автоматизации CDP.

### Методы

#### `__init__(self, process_creator=None)`

Инициализирует менеджер процессов браузера.

- `process_creator`: Пользовательская функция для создания процессов браузера. Должна принимать список команд и возвращать объект `subprocess.Popen`. Если `None`, используется реализация `subprocess` по умолчанию.

#### `start_browser_process(self, binary_location, port, arguments)`

Запускает процесс браузера с включенной отладкой CDP.

- `binary_location`: Путь к исполняемому файлу браузера.
- `port`: TCP-порт для WebSocket-соединений CDP.
- `arguments`: Дополнительные аргументы командной строки.
- **Возвращает**: Запущенный экземпляр процесса браузера.

#### `_default_process_creator(command)`

Статический метод, который создает процесс браузера с захватом вывода для предотвращения засорения консоли.

#### `stop_process(self)`

Завершает процесс браузера с корректным завершением работы. Сначала пытается отправить `SIGTERM`, затем `SIGKILL` после 15-секундного таймаута. Безопасно вызывать, даже если процесс не запущен.