## Содержание

- [Модуль `pydoll.browser.managers.temp_dir_manager`](#модуль-pydollbrowsermanagerstemp_dir_manager)
  - [Класс `TempDirectoryManager`](#класс-tempdirectorymanager)
    - [Методы](#методы)
      - [`__init__`](#__init__self-temp_dir_factorytemporarydirectory)
      - [`create_temp_dir`](#create_temp_dirself---temporarydirectory)
      - [`retry_process_file`](#retry_process_filefunc-path-retry_times10)
      - [`handle_cleanup_error`](#handle_cleanup_errorself-func-path-exc_info)
      - [`cleanup`](#cleanupself)

# Модуль `pydoll.browser.managers.temp_dir_manager`

Этот модуль содержит класс `TempDirectoryManager`, который управляет жизненным циклом временных каталогов для автоматизации браузера с использованием CDP. Он создает изолированные временные каталоги для профилей браузера и обеспечивает безопасную очистку с механизмами повторных попыток для заблокированных файлов.

## Класс `TempDirectoryManager`

Управляет жизненным циклом временных каталогов для автоматизации браузера с использованием CDP.

### Методы

#### `__init__(self, temp_dir_factory=TemporaryDirectory)`

Инициализирует менеджер временных каталогов.

- `temp_dir_factory`: Функция для создания временных каталогов. Должна возвращать объект, совместимый с `TemporaryDirectory`.

#### `create_temp_dir(self) -> TemporaryDirectory`

Создает и отслеживает новый временный каталог для использования браузером.

- **Возвращает**: Объект `TemporaryDirectory` для аргумента `--user-data-dir` браузера.

#### `retry_process_file(func, path, retry_times=10)`

Статический метод, который выполняет файловую операцию с логикой повторных попыток для заблокированных файлов.

- `func`: Функция для выполнения над путем.
- `path`: Путь к файлу или каталогу для операции.
- `retry_times`: Максимальное количество попыток повтора (отрицательное = неограниченное).
- **Вызывает**: `PermissionError`, если операция завершается неудачей после всех повторных попыток.

#### `handle_cleanup_error(self, func, path, exc_info)`

Обрабатывает ошибки во время очистки каталога с использованием обходных путей, специфичных для браузера.

- `func`: Исходная функция, которая завершилась неудачей.
- `path`: Путь, который не удалось обработать.
- `exc_info`: Кортеж информации об исключении.

#### `cleanup(self)`

Удаляет все отслеживаемые временные каталоги с обработкой ошибок. Использует пользовательский обработчик ошибок для проблем с блокировкой файлов, специфичных для браузера. Продолжает очистку, даже если некоторые файлы не удаляются.