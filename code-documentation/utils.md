## Содержание

- [Модуль `pydoll.utils`](#модуль-pydollutils)
  - [Основные возможности](#основные-возможности)
  - [Класс `TextExtractor`](#класс-textextractor)
    - [Методы](#методы)
  - [Функции](#функции)
    - [`extract_text_from_html`](#extract_text_from_htmlhtml-separator-stripfalse)
    - [`decode_base64_to_bytes`](#decode_base64_to_bytesimage)
    - [`async def get_browser_ws_address`](#async-def-get_browser_ws_addressport)
    - [`validate_browser_paths`](#validate_browser_pathspaths)
    - [`clean_script_for_analysis`](#clean_script_for_analysisscript)
    - [`is_script_already_function`](#is_script_already_functionscript)
    - [`has_return_outside_function`](#has_return_outside_functionscript)

# Модуль `pydoll.utils`

Этот модуль предоставляет набор утилит, используемых в различных частях `pydoll` для выполнения общих задач, таких как извлечение текста из HTML, работа с base64, получение адреса WebSocket браузера и анализ JavaScript-кода.

## Основные возможности

- **Извлечение текста из HTML**: предоставляет класс `TextExtractor` и функцию `extract_text_from_html` для извлечения видимого текста из HTML-документов.
- **Декодирование Base64**: функция `decode_base64_to_bytes` для декодирования строк base64 в байты.
- **Получение адреса WebSocket**: асинхронная функция `get_browser_ws_address` для получения адреса WebSocket отладки браузера.
- **Валидация путей к браузеру**: функция `validate_browser_paths` для проверки существования и доступности исполняемого файла браузера.
- **Анализ JavaScript**: функции `clean_script_for_analysis`, `is_script_already_function` и `has_return_outside_function` для анализа и очистки JavaScript-кода.

## Класс `TextExtractor`

`TextExtractor` — это парсер HTML, который извлекает видимый текстовый контент из HTML-строки, игнорируя содержимое содержимого тегов, таких как `<script>`, `<style>` и `<template>`.

### Методы

- `handle_starttag(tag, attrs)`: определяет начало тегов, которые следует пропустить.
- `handle_endtag(tag)`: определяет конец тегов, которые следует пропустить.
- `handle_data(data)`: обрабатывает текстовые узлы и добавляет их в результат, если они не находятся внутри пропущенного тега.
- `get_strings(strip)`: возвращает все собранные фрагменты видимого текста.
- `get_text(separator, strip)`: возвращает весь видимый текст в виде одной строки с указанным разделителем.

## Функции

### `extract_text_from_html(html, separator='', strip=False)`

Извлекает видимый текстовый контент из HTML-строки.

- `html`: HTML-строка для извлечения текста.
- `separator`: строка, вставляемая между извлеченными фрагментами текста.
- `strip`: если `True`, удаляет начальные и конечные пробелы из каждого фрагмента.
- **Возвращает**: извлеченный видимый текст.

### `decode_base64_to_bytes(image)`

Декодирует строку изображения в формате base64 в байты.

- `image`: строка изображения в формате base64.
- **Возвращает**: декодированное изображение в виде байтов.

### `async def get_browser_ws_address(port)`

Асинхронно получает адрес WebSocket для экземпляра браузера.

- `port`: порт, на котором запущен браузер.
- **Возвращает**: адрес WebSocket для отладки браузера.
- **Вызывает**: `NetworkError`, если не удается получить адрес, или `InvalidResponse`, если ответ не является допустимым JSON.

### `validate_browser_paths(paths)`

Проверяет список потенциальных путей к исполняемому файлу браузера и возвращает первый допустимый.

- `paths`: список потенциальных путей к файлам.
- **Возвращает**: первый допустимый путь к исполняемому файлу браузера.
- **Вызывает**: `InvalidBrowserPath`, если исполняемый файл браузера не найден ни по одному из путей.

### `clean_script_for_analysis(script)`

Очищает JavaScript-код, удаляя комментарии и строковые литералы.

- `script`: JavaScript-код для очистки.
- **Возвращает**: очищенный скрипт.

### `is_script_already_function(script)`

Проверяет, является ли JavaScript-скрипт уже обернутым в функцию.

- `script`: JavaScript-код для анализа.
- **Возвращает**: `True`, если скрипт уже является функцией, иначе `False`.

### `has_return_outside_function(script)`

Проверяет, есть ли в JavaScript-скрипте операторы `return` вне функций.

- `script`: JavaScript-код для анализа.
- **Возвращает**: `True`, если в скрипте есть `return` вне функции, иначе `False`.