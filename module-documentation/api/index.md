# Справочник по API

Добро пожаловать в справочник по API Pydoll! В этом разделе представлена исчерпывающая документация по всем классам, методам и функциям, доступным в библиотеке Pydoll.

## Обзор

Pydoll организован в несколько ключевых модулей, каждый из которых служит определенной цели в автоматизации браузера:

### Модуль браузера
Модуль браузера содержит классы для управления экземплярами браузера и их жизненным циклом.

- **[Chrome](browser/chrome.md)** - автоматизация браузера Chrome
- **[Edge](browser/edge.md)** - автоматизация браузера Microsoft Edge
- **[Options](browser/options.md)** - параметры конфигурации браузера
- **[Tab](browser/tab.md)** - управление вкладками и взаимодействие с ними
- **[Managers](browser/managers.md)** - менеджеры жизненного цикла браузера

### Модуль элементов
Модуль элементов предоставляет классы для взаимодействия с элементами веб-страницы.

- **[WebElement](elements/web_element.md)** - взаимодействие с отдельными элементами
- **[Mixins](elements/mixins.md)** - многократно используемая функциональность элементов

### Модуль подключения
Модуль подключения обрабатывает связь с браузером через протокол Chrome DevTools.

- **[Обработчик подключений](connection/connection.md)** - управление подключением WebSocket
- **[Менеджеры](connection/managers.md)** - менеджеры жизненного цикла подключения

### Модуль команд
Модуль команд предоставляет низкоуровневые реализации команд протокола Chrome DevTools.

- **[Обзор команд](commands/index.md)** - реализации команд CDP по доменам

### Модуль протокола
Модуль протокола реализует команды и события протокола Chrome DevTools.

- **[Команды](protocol/commands.md)** - реализации команд CDP
- **[События](protocol/events.md)** - обработка событий CDP

### Основной модуль
Основной модуль содержит фундаментальные утилиты, константы и исключения.

- **[Константы](core/constants.md)** - константы и перечисления библиотеки
- **[Исключения](core/exceptions.md)** - пользовательские классы исключений
- **[Утилиты](core/utils.md)** - служебные функции

## Быстрая навигация

### Наиболее распространенные классы

| Класс | Назначение | Модуль |
|-------|---------|--------|
| `Chrome` | Автоматизация браузера Chrome | `pydoll.browser.chromium` |
| `Edge` | Автоматизация браузера Edge | `pydoll.browser.chromium` |
| `Tab` | Взаимодействие с вкладками и управление ими | `pydoll.browser.tab` |
| `WebElement` | Взаимодействие с элементами | `pydoll.elements.web_element` |
| `ChromiumOptions` | Конфигурация браузера | `pydoll.browser.options` |

### Ключевые перечисления и константы

| Имя | Назначение | Модуль |
|------|---------|--------|
| `By` | Стратегии выбора элементов | `pydoll.constants` |
| `Key` | Константы клавиш клавиатуры | `pydoll.constants` |
| `PermissionType` | Типы разрешений браузера | `pydoll.constants` |

### Общие исключения

| Исключение | Когда возникает | Модуль |
|-----------|-------------|--------|
| `ElementNotFound` | Элемент не найден в DOM | `pydoll.exceptions` |
| `WaitElementTimeout` | Тайм-аут ожидания элемента | `pydoll.exceptions` |
| `BrowserNotStarted` | Браузер не запущен | `pydoll.exceptions` |

## Шаблоны использования

### Базовая автоматизация браузера

```python
from pydoll.browser.chromium import Chrome

async with Chrome() as browser:
    tab = await browser.start()
    await tab.go_to("https://example.com")
    element = await tab.find(id="my-element")
    await element.click()
```

### Поиск элементов

```python
# Использование современного метода find()
element = await tab.find(id="username")
element = await tab.find(tag_name="button", class_name="submit")

# Использование селекторов CSS или XPath
element = await tab.query("#username")
element = await tab.query("//button[@class='submit']")
```

### Обработка событий

```python
await tab.enable_page_events()
await tab.on('Page.loadEventFired', handle_page_load)
```

## Подсказки типов

Pydoll полностью типизирован и предоставляет исчерпывающие подсказки типов для лучшей поддержки IDE и безопасности кода. Все общедоступные API включают правильные аннотации типов.

```python
from typing import Optional, List
from pydoll.elements.web_element import WebElement

# Методы возвращают правильно типизированные объекты
element: Optional[WebElement] = await tab.find(id="test", raise_exc=False)
elements: List[WebElement] = await tab.find(class_name="item", find_all=True)
```

## Поддержка Async/Await

Все операции Pydoll являются асинхронными и должны использоваться с `async`/`await`:

```python
import asyncio

async def main():
    # Все операции Pydoll являются асинхронными
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to("https://example.com")
        
asyncio.run(main())
```

Просмотрите разделы ниже, чтобы изучить полную документацию по API для каждого модуля.