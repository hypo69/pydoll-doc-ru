<p align="center">
    <img src="https://github.com/user-attachments/assets/219f2dbc-37ed-4aea-a289-ba39cdbb335d" alt="Логотип Pydoll" /> <br>
</p>
<h1 align="center">Pydoll: Автоматизируйте веб, естественно</h1>

<p align="center">
    <a href="https://codecov.io/gh/autoscrape-labs/pydoll" >
        <img src="https://codecov.io/gh/autoscrape-labs/pydoll/graph/badge.svg?token=40I938OGM9"/>
    </a>
    <img src="https://github.com/thalissonvs/pydoll/actions/workflows/tests.yml/badge.svg" alt="Тесты">
    <img src="https://github.com/thalissonvs/pydoll/actions/workflows/ruff-ci.yml/badge.svg" alt="Ruff CI">
    <img src="https://github.com/thalissonvs/pydoll/actions/workflows/mypy.yml/badge.svg" alt="MyPy CI">
    <img src="https://img.shields.io/badge/python-%3E%3D3.10-blue" alt="Python >= 3.10">
    <a href="https://deepwiki.com/autoscrape-labs/pydoll"><img src="https://deepwiki.com/badge.svg" alt="Спросить DeepWiki"></a>
</p>


<p align="center">
  📖 <a href="https://autoscrape-labs.github.io/pydoll/">Документация</a> •
  🚀 <a href="#getting-started">Начало работы</a> •
  ⚡ <a href="#advanced-features">Расширенные возможности</a> •
  🤝 <a href="#contributing">Участие в проекте</a> •
  💖 <a href="#support-my-work">Поддержать мою работу</a>
</p>

# Puppeteer больше не поддерживается, а Pydoll - это его замена

Представьте себе следующий сценарий: вам нужно автоматизировать задачи в браузере. Возможно, это тестирование веб-приложения, сбор данных с сайта или даже автоматизация повторяющихся процессов. Обычно это требует использования внешних драйверов, сложных конфигураций и сопряжено с множеством проблем совместимости.

**Pydoll был создан для решения этих проблем.**

Разработанный с нуля и с другой философией, Pydoll напрямую подключается к протоколу Chrome DevTools (CDP), устраняя необходимость во внешних драйверах. Эта чистая реализация в сочетании с реалистичными способами кликов, навигации и взаимодействия с элементами делает его практически неотличимым от реального пользователя.

Мы считаем, что мощная автоматизация не должна требовать от вас становиться экспертом в настройке или постоянно бороться с системами защиты от ботов. С Pydoll вы можете сосредоточиться на том, что действительно важно: на логике вашей автоматизации, а не на базовой сложности или системах защиты.

## 🌟 Что делает Pydoll особенным?

- **Без веб-драйверов**: Попрощайтесь с проблемами совместимости веб-драйверов
- **Движок взаимодействия, имитирующий человека**: Способен проходить поведенческие CAPTCHA, такие как reCAPTCHA v3 или Turnstile, в зависимости от репутации IP и шаблонов взаимодействия
- **Асинхронная производительность**: Для высокоскоростной автоматизации и выполнения нескольких задач одновременно
- **Очеловеченные взаимодействия**: Имитирует поведение реального пользователя
- **Простота**: С Pydoll вы просто устанавливаете и готовы к автоматизации.

### ⚖️ Заявление об этичном использовании
Pydoll предназначен для имитации реалистичных взаимодействий в браузере, чтобы избежать обнаружения в качестве бота при выполнении легитимных задач автоматизации. Он не взламывает и не обходит CAPTCHA в традиционном смысле (например, решая головоломки с изображениями или взламывая систему).

Вместо этого он повышает вероятность того, что его примут за реального пользователя, имитируя человеческое поведение, что может привести к прохождению защит на основе поведения, таких как reCAPTCHA v3 или Cloudflare Turnstile.

Мы не поддерживаем и не одобряем использование этого инструмента для доступа к веб-сайтам в нарушение их условий обслуживания, для сбора персональных данных или для обхода явных ограничений доступа.

Используйте его ответственно. 🚨

## Что нового в версии 2.4.0

### Расширенная поддержка настроек браузера (спасибо [@LucasAlvws](https://github.com/LucasAlvws))
Теперь вы можете настраивать параметры браузера Chromium через словарь `browser_preferences` в `ChromiumOptions`.<br><br>
Устанавливайте такие вещи, как каталог для загрузок, язык, блокировку уведомлений, обработку PDF и многое другое.
Для удобства были добавлены вспомогательные свойства, такие как `set_default_download_directory`, `set_accept_languages` и `prompt_for_download`.
Настройки объединяются автоматически, не нужно переопределять все.<br><br>
Вот пример:

```python
options = ChromiumOptions()
options.browser_preferences = {  # вы можете установить весь словарь
    'download': {
        'default_directory': '/tmp/downloads',
        'prompt_for_download': False
    },
    'intl': {
        'accept_languages': 'en-US,en,pt-BR'
    },
    'profile': {
        'default_content_setting_values': {
            'notifications': 2  # Блокировать уведомления
        }
    }
}

options.set_default_download_directory('/tmp/downloads')   # или только отдельные свойства
options.set_accept_languages('en-US,en,pt-BR')
options.prompt_for_download = False
```
Подробнее см. в [docs/features.md](docs/features.md#custom-browser-preferences).

### Новый метод `get_parent_element()`
Получите родительский элемент любого WebElement, что упрощает навигацию по структуре DOM:
```python
element = await tab.find(id='button')
parent = await element.get_parent_parent()
```
### Новая опция start_timeout (спасибо [@j0j1j2](https://github.com/j0j1j2))
Добавлено в ChromiumOptions для контроля времени, которое может занять запуск браузера. Полезно на медленных машинах или в средах CI.

```python
options = ChromiumOptions()
options.start_timeout = 20  # ждать 20 секунд
```

## 📦 Установка

```bash
pip install pydoll-python
```

И это все! Просто установите и начинайте автоматизировать.

## 🚀 Начало работы

### Ваша первая автоматизация

Начнем с реального примера: автоматизация, которая выполняет поиск в Google и кликает по первому результату. На этом примере мы увидим, как работает библиотека и как вы можете начать автоматизировать свои задачи.

```python
import asyncio

from pydoll.browser import Chrome
from pydoll.constants import Key

async def google_search(query: str):
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://www.google.com')
        search_box = await tab.find(tag_name='textarea', name='q')
        await search_box.insert_text(query)
        await search_box.press_keyboard_key(Key.ENTER)
        await (await tab.find(
            tag_name='h3',
            text='autoscrape-labs/pydoll',
            timeout=10,
        )).click()
        await tab.find(id='repository-container-header', timeout=10)

asyncio.run(google_search('pydoll python'))
```

Без конфигураций, просто с помощью простого скрипта, мы можем выполнить полноценный поиск в Google!
Хорошо, теперь давайте посмотрим, как мы можем извлекать данные со страницы, используя тот же предыдущий пример.
Будем считать в коде ниже, что мы уже находимся на странице Pydoll. Мы хотим извлечь следующую информацию:

- Описание проекта
- Количество звезд
- Количество форков
- Количество проблем (issues)
- Количество пулл-реквестов

Приступим! Чтобы получить описание проекта, мы будем использовать запросы xpath. Вы можете проверить документацию, чтобы узнать, как создавать свои собственные запросы.

```python
description = await (await tab.query(
    '//h2[contains(text(), "About")]/following-sibling::p',
    timeout=10,
)).text
```

И это все! Давайте разберемся, что делает этот запрос:

1. `//h2[contains(text(), "About")]` - Выбирает первый `<h2>`, который содержит "About"
2. `/following-sibling::p` - Выбирает первый `<p>`, который идет после `<h2>`

Теперь давайте получим остальные данные:

```python
number_of_stars = await (await tab.find(
    id='repo-stars-counter-star'
)).text

number_of_forks = await (await tab.find(
    id='repo-network-counter'
)).text
number_of_issues = await (await tab.find(
    id='issues-repo-tab-count',
)).text
number_of_pull_requests = await (await tab.find(
    id='pull-requests-repo-tab-count',
)).text

data = {
    'description': description,
    'number_of_stars': number_of_stars,
    'number_of_forks': number_of_forks,
    'number_of_issues': number_of_issues,
    'number_of_pull_requests': number_of_pull_requests,
}
print(data)

```

На изображении ниже мы видим скорость выполнения и результат автоматизации.
В целях демонстрации браузер не отображается.

![пример поиска в google](./docs/images/google-search-example.gif)


Всего за 5 секунд нам удалось извлечь все необходимые данные! Это та 
скорость, которую вы можете ожидать от автоматизации с Pydoll.


### Более сложный пример

Теперь перейдем к случаю, с которым вы, вероятно, сталкивались много раз: капча,
подобная той, что у Cloudflare. У Pydoll есть метод, чтобы попытаться справиться с этим, хотя, как уже упоминалось ранее, эффективность зависит от различных факторов. В коде ниже приведен полный пример того, как обойти капчу Cloudflare.

```python
import asyncio

from pydoll.browser import Chrome
from pydoll.constants import By

async def cloudflare_example():
    async with Chrome() as browser:
        tab = await browser.start()
        async with tab.expect_and_bypass_cloudflare_captcha():
            await tab.go_to('https://2captcha.com/demo/cloudflare-turnstile')
        print('Капча пройдена, продолжаем...')
        await asyncio.sleep(5)  # просто чтобы увидеть результат :)

asyncio.run(cloudflare_example())

```

Ниже представлен результат выполнения:

![пример с cloudflare](./docs/images/cloudflare-example.gif)


Всего за несколько строк кода нам удалось справиться с одной из самых
сложных капч. Это лишь одна из многих функциональностей, которые предлагает Pydoll.
Но это еще не все!


### Пользовательские конфигурации

Иногда нам нужен больший контроль над браузером. Pydoll предлагает гибкий способ для этого. Давайте посмотрим на пример ниже:


```python
from pydoll.browser import Chrome
from pydoll.browser.options import ChromiumOptions as Options

async def custom_automation():
    # Настраиваем параметры браузера
    options = Options()
    options.add_argument('--proxy-server=username:password@ip:port')
    options.add_argument('--window-size=1920,1080')
    options.binary_location = '/path/to/your/browser'
    options.start_timeout = 20

    async with Chrome(options=options) as browser:
        tab = await browser.start()
        # Ваш код автоматизации здесь
        await tab.go_to('https://example.com')
        # Теперь браузер использует ваши пользовательские настройки

asyncio.run(custom_automation())
```

В этом примере мы настраиваем браузер на использование прокси и окна размером 1920x1080, а также указываем пользовательский путь к бинарному файлу Chrome, на случай если ваше место установки отличается от стандартных.


## ⚡ Расширенные возможности

Pydoll предлагает ряд расширенных функций, которые удовлетворят даже самых
требовательных пользователей.


### Расширенный поиск элементов

У нас есть несколько способов находить элементы на странице. Независимо от ваших предпочтений, у нас есть способ, который будет для вас удобен:

```python
import asyncio
from pydoll.browser import Chrome

async def element_finding_examples():
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://example.com')

        # Поиск по атрибутам (наиболее интуитивный)
        submit_btn = await tab.find(
            tag_name='button',
            class_name='btn-primary',
            text='Submit'
        )
        # Поиск по ID
        username_field = await tab.find(id='username')
        # Поиск нескольких элементов
        all_links = await tab.find(tag_name='a', find_all=True)
        # CSS-селекторы и XPath
        nav_menu = await tab.query('nav.main-menu')
        specific_item = await tab.query('//div[@data-testid="item-123"]')
        # С таймаутом и обработкой ошибок
        delayed_element = await tab.find(
            class_name='dynamic-content',
            timeout=10,
            raise_exc=False  # Возвращает None, если не найден
        )
        # Продвинутый: Пользовательские атрибуты
        custom_element = await tab.find(
            data_testid='submit-button',
            aria_label='Submit form'
        )

asyncio.run(element_finding_examples())
```

Метод `find` более удобен для пользователя. Мы можем искать по общим атрибутам, таким как id, tag_name, class_name и т.д., вплоть до пользовательских атрибутов (например, `data-testid`).

Если этого недостаточно, мы можем использовать метод `query` для поиска элементов с помощью CSS-селекторов, XPath-запросов и т.д. Pydoll автоматически определяет, какой тип запроса мы используем.


### Параллельная автоматизация

Одним из больших преимуществ Pydoll является возможность обрабатывать несколько задач одновременно благодаря его асинхронной реализации. Мы можем автоматизировать несколько вкладок
одновременно! Давайте посмотрим на пример:

```python
import asyncio
from pydoll.browser import Chrome

async def scrape_page(url, tab):
    await tab.go_to(url)
    title = await tab.execute_script('return document.title')
    links = await tab.find(tag_name='a', find_all=True)
    return {
        'url': url,
        'title': title,
        'link_count': len(links)
    }

async def concurrent_scraping():
    browser = Chrome()
    tab_google = await browser.start()
    tab_duckduckgo = await browser.new_tab()
    tasks = [
        scrape_page('https://google.com/', tab_google),
        scrape_page('https://duckduckgo.com/', tab_duckduckgo)
    ]
    results = await asyncio.gather(*tasks)
    print(results)
    await browser.stop()

asyncio.run(concurrent_scraping())
```

Ниже мы видим невероятную скорость выполнения:

![пример параллельного выполнения](./docs/images/concurrent-example.gif)


Нам удалось извлечь данные с двух страниц одновременно! Скажите, разве это не невероятно?


И это еще далеко не все! Система событий для реактивной автоматизации, перехват и изменение запросов и многое другое. Загляните в документацию, вы не
пожалеете!


## 🔧 Быстрое устранение неполадок

**Браузер не найден?**
```python
from pydoll.browser import Chrome
from pydoll.browser.options import ChromiumOptions

options = ChromiumOptions()
options.binary_location = '/path/to/your/chrome'
browser = Chrome(options=options)
```

**Браузер запускается после ошибки FailedToStartBrowser?**
```python
from pydoll.browser import Chrome
from pydoll.browser.options import ChromiumOptions

options = ChromiumOptions()
options.start_timeout = 20  # по умолчанию 10 секунд

browser = Chrome(options=options)
```

**Нужен прокси?**
```python
options.add_argument('--proxy-server=your-proxy:port')
```

**Запускаете в Docker?**
```python
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')
```

## 📚 Документация

Для получения полной документации, подробных примеров и глубокого изучения всех функциональных возможностей Pydoll посетите нашу [официальную документацию](https://autoscrape-labs.github.io/pydoll/).

Документация включает:
- **Руководство по началу работы** - Пошаговые инструкции
- **Справочник API** - Полная документация по методам
- **Продвинутые техники** - Перехват сетевых запросов, обработка событий, оптимизация производительности

>Китайская версия этого README находится [здесь](README_zh.md).

## 🤝 Участие в проекте

Мы будем рады вашей помощи, чтобы сделать Pydoll еще лучше! Ознакомьтесь с нашими [руководством по участию в проекте](CONTRIBUTING.md), чтобы начать. Будь то исправление ошибок, добавление новых функций или улучшение документации - любой вклад приветствуется!

Пожалуйста, убедитесь, что вы:
- Пишете тесты для новых функций или исправлений ошибок
- Следуете стилю кода и соглашениям
- Используете конвенциональные коммиты для пулл-реквестов
- Запускаете проверки линтером и тесты перед отправкой

## 💖 Поддержать мою работу

Если вы находите Pydoll полезным, рассмотрите возможность [поддержать меня на GitHub](https://github.com/sponsors/thalissonvs).  
Вы получите доступ к эксклюзивным преимуществам, таким как приоритетная поддержка, пользовательские функции и многое другое!

Не можете поддержать сейчас? Не проблема — вы все равно можете очень помочь:
- Поставив звезду репозиторию
- Поделившись в социальных сетях
- Написав посты или руководства
- Оставляя отзывы или сообщая о проблемах

Каждая частичка поддержки имеет значение — спасибо!

## 📄 Лицензия

Pydoll распространяется под [лицензией MIT](LICENSE).

<p align="center">
  <b>Pydoll</b> — Делаем автоматизацию браузера волшебной!
</p>