# Ключевые особенности

Pydoll предоставляет революционные возможности для автоматизации браузеров, делая его значительно мощнее традиционных инструментов и одновременно проще в использовании.

## Основные возможности

### Нулевые веб-драйверы

В отличие от традиционных инструментов автоматизации браузеров, таких как Selenium, Pydoll полностью устраняет необходимость в веб-драйверах. Подключаясь напрямую к браузерам через протокол Chrome DevTools, Pydoll:

- Устраняет проблемы совместимости версий между браузером и драйвером
- Снижает сложность настройки и накладные расходы на обслуживание
- Обеспечивает более надежные соединения без проблем, связанных с драйверами
- Позволяет автоматизировать все браузеры на базе Chromium с помощью единого API

Больше никаких ошибок «версия chromedriver не соответствует версии Chrome» или загадочных сбоев веб-драйвера.

### Архитектура Async-First

Созданный с нуля с использованием `asyncio` в Python, Pydoll обеспечивает:

- **Истинную многопоточность**: выполняйте несколько операций параллельно без блокировки
- **Эффективное использование ресурсов**: управляйте множеством экземпляров браузера с минимальными накладными расходами
- **Современные шаблоны Python**: менеджеры контекста, асинхронные итераторы и другие `asyncio`-дружественные интерфейсы
- **Оптимизация производительности**: снижение задержек и увеличение пропускной способности для задач автоматизации

### Взаимодействия, подобные человеческим

Избегайте обнаружения, имитируя поведение реального пользователя:

- **Естественный ввод**: вводите текст со случайной задержкой между нажатиями клавиш
- **Реалистичные щелчки**: щелкайте с реалистичным временем и движением, включая смещение

### Возможности, управляемые событиями

Реагируйте на события браузера в режиме реального времени:

- **Мониторинг сети**: отслеживайте запросы, ответы и неудачные загрузки
- **Наблюдение за DOM**: реагируйте на изменения в структуре страницы
- **События жизненного цикла страницы**: перехватывайте события навигации, загрузки и рендеринга
- **Пользовательские обработчики событий**: регистрируйте обратные вызовы для конкретных интересующих событий

### Поддержка нескольких браузеров

Pydoll без проблем работает с:

- **Google Chrome**: основная поддержка со всеми доступными функциями
- **Microsoft Edge**: полная поддержка специфичных для Edge функций
- **Chromium**: поддержка других браузеров на базе Chromium

### Скриншот и экспорт в PDF

Захватывайте визуальный контент с веб-страниц:

- **Скриншоты всей страницы**: захватывайте все содержимое страницы, даже за пределами видимой области
- **Скриншоты элементов**: нацеливайтесь на конкретные элементы для захвата
- **Высококачественный экспорт в PDF**: создавайте PDF-документы с веб-страниц
- **Пользовательское форматирование**: скоро!

## Интуитивно понятный поиск элементов

Pydoll v2.0+ представляет революционный подход к поиску элементов, который одновременно более интуитивен и мощен, чем традиционные методы на основе селекторов.

### Современный метод `find()`

Новый метод `find()` позволяет искать элементы, используя естественные атрибуты:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def element_finding_examples():
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://example.com')

        # Поиск по имени тега и классу
        submit_button = await tab.find(tag_name='button', class_name='btn-primary')

        # Поиск по ID (наиболее распространенный)
        username_field = await tab.find(id='username')

        # Поиск по текстовому содержимому
        login_link = await tab.find(tag_name='a', text='Login')

        # Поиск по нескольким атрибутам
        search_input = await tab.find(
            tag_name='input',
            type='text',
            placeholder='Search...'
        )

        # Поиск с пользовательскими атрибутами данных
        custom_element = await tab.find(
            data_testid='submit-button',
            aria_label='Submit form'
        )

        # Поиск нескольких элементов
        all_links = await tab.find(tag_name='a', find_all=True)

        # С тайм-аутом и обработкой ошибок
        delayed_element = await tab.find(
            class_name='dynamic-content',
            timeout=10,
            raise_exc=False  # Возвращает None, если не найден
        )

asyncio.run(element_finding_examples())
```

### CSS-селекторы и XPath с `query()`

Для разработчиков, предпочитающих традиционные селекторы, метод `query()` обеспечивает прямую поддержку CSS-селекторов и XPath:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def query_examples():
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://example.com')

        # CSS-селекторы
        nav_menu = await tab.query('nav.main-menu')
        first_article = await tab.query('article:first-child')
        submit_button = await tab.query('button[type="submit"]')

        # Выражения XPath
        specific_item = await tab.query('//div[@data-testid="item-123"]')
        text_content = await tab.query('//span[contains(text(), "Welcome")]')

        # Сложные селекторы
        nested_element = await tab.query('div.container > .content .item:nth-child(2)')

asyncio.run(query_examples())
```

## Встроенный обход капчи Cloudflare

!!! warning "Важная информация об обходе капчи"
    Эффективность обхода Cloudflare Turnstile зависит от нескольких факторов:

    - **Репутация IP**: Cloudflare присваивает «оценку доверия» каждому IP-адресу. Чистые домашние IP-адреса обычно получают более высокие оценки.
    - **Предыдущая история**: IP-адреса с историей подозрительной активности могут быть навсегда помечены.

    Pydoll может достигать оценок, сопоставимых с обычной сессией браузера, но не может преодолеть блокировки на основе IP или чрезвычайно строгие конфигурации. Для достижения наилучших результатов используйте домашние IP-адреса с хорошей репутацией.

    Помните, что методы обхода капчи действуют в «серой зоне» и должны использоваться ответственно.

Одной из самых мощных функций Pydoll является его способность автоматически обходить капчи Cloudflare Turnstile, которые блокируют большинство инструментов автоматизации:

### Подход с использованием менеджера контекста (синхронный)

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def bypass_cloudflare_example():
    async with Chrome() as browser:
        tab = await browser.start()

    # Менеджер контекста будет ждать обработки капчи
    # перед продолжением выполнения
        async with tab.expect_and_bypass_cloudflare_captcha():
            await tab.go_to('https://site-with-cloudflare.com')
        print("Ожидание обработки капчи...")

    # Этот код выполняется только после успешного обхода капчи
    print("Капча обойдена! Продолжение автоматизации...")
        protected_content = await tab.find(id='protected-content')
        content_text = await protected_content.text
        print(f"Защищенный контент: {content_text}")

asyncio.run(bypass_cloudflare_example())
```

### Подход с фоновой обработкой

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def background_bypass_example():
    async with Chrome() as browser:
        tab = await browser.start()

    # Включить автоматическое решение капчи перед навигацией
        await tab.enable_auto_solve_cloudflare_captcha()

    # Перейдите на защищенный сайт — капча обрабатывается автоматически в фоновом режиме
        await tab.go_to('https://site-with-cloudflare.com')
    print("Страница загружена, капча будет обработана в фоновом режиме...")

    # Добавьте небольшую задержку, чтобы дать время на решение капчи
    await asyncio.sleep(3)

    # Продолжить автоматизацию
        protected_content = await tab.find(id='protected-content')
        content_text = await protected_content.text
        print(f"Защищенный контент: {content_text}")

    # Отключите автоматическое решение, когда оно больше не нужно
        await tab.disable_auto_solve_cloudflare_captcha()

asyncio.run(background_bypass_example())
```

Получайте доступ к веб-сайтам, которые активно блокируют инструменты автоматизации, без использования сторонних сервисов для решения капчи. Эта встроенная обработка капчи делает Pydoll подходящим для автоматизации ранее недоступных веб-сайтов.

## Управление несколькими вкладками

Pydoll предоставляет сложные возможности управления вкладками с использованием шаблона «одиночка», который обеспечивает эффективное использование ресурсов и предотвращает создание дублирующихся экземпляров `Tab` для одной и той же вкладки браузера.

### Шаблон «одиночка» для вкладок

Pydoll реализует шаблон «одиночка» для экземпляров `Tab` на основе идентификатора цели браузера. Это означает:

- **Один экземпляр `Tab` на вкладку браузера**: несколько ссылок на одну и ту же вкладку браузера возвращают один и тот же объект `Tab`
- **Автоматическое управление ресурсами**: нет дублирующихся соединений или обработчиков для одной и той же вкладки
- **Согласованное состояние**: все ссылки на вкладку совместно используют одно и то же состояние и обработчики событий

```python
import asyncio
from pydoll.browser.chromium import Chrome
from pydoll.browser.tab import Tab

async def singleton_demonstration():
    async with Chrome() as browser:
        tab = await browser.start()

        # Получите одну и ту же вкладку разными методами — это идентичные объекты
        same_tab = Tab(browser, browser._connection_port, tab._target_id)
        opened_tabs = await browser.get_opened_tabs()

        # Все ссылки указывают на один и тот же экземпляр-одиночку
        print(f"Один и тот же объект? {tab is same_tab}")  # Может быть True, если target_id тот же
        print(f"Экземпляры Tab управляются как одиночки")

asyncio.run(singleton_demonstration())
```

### Программное создание новых вкладок

Используйте `new_tab()` для программного создания вкладок с полным контролем:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def programmatic_tab_creation():
    async with Chrome() as browser:
        # Начните с начальной вкладки
        main_tab = await browser.start()

        # Создайте дополнительные вкладки с конкретными URL-адресами
        search_tab = await browser.new_tab('https://google.com')
        news_tab = await browser.new_tab('https://news.ycombinator.com')
        docs_tab = await browser.new_tab('https://docs.python.org')

        # Работайте с несколькими вкладками одновременно
        await search_tab.find(name='q').type_text('Python automation')
        await news_tab.find(class_name='storylink', find_all=True)
        await docs_tab.find(id='search-field').type_text('asyncio')

        # Получить все открытые вкладки
        all_tabs = await browser.get_opened_tabs()
        print(f"Всего открыто вкладок: {len(all_tabs)}")

        # Закройте определенные вкладки, когда закончите
        await search_tab.close()
        await news_tab.close()

asyncio.run(programmatic_tab_creation())
```

### Обработка вкладок, открытых пользователем

Когда пользователи нажимают на ссылки, открывающие новые вкладки (`target="_blank"`), используйте `get_opened_tabs()` для их обнаружения и управления:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def handle_user_opened_tabs():
    async with Chrome() as browser:
        main_tab = await browser.start()
        await main_tab.go_to('https://example.com')

        # Получить начальное количество вкладок
        initial_tabs = await browser.get_opened_tabs()
        initial_count = len(initial_tabs)
        print(f"Начальное количество вкладок: {initial_count}")

        # Нажмите на ссылку, которая открывает новую вкладку (target="_blank")
        external_link = await main_tab.find(text='Open in New Tab')
        await external_link.click()

        # Подождите, пока откроется новая вкладка
        await asyncio.sleep(2)

        # Обнаружить новые вкладки
        current_tabs = await browser.get_opened_tabs()
        new_tab_count = len(current_tabs)

        if new_tab_count > initial_count:
            print(f"Обнаружена новая вкладка! Всего вкладок: {new_tab_count}")

            # Получить только что открытую вкладку (последнюю в списке)
            new_tab = current_tabs[-1]

            # Работа с новой вкладкой
            await new_tab.go_to('https://different-site.com')
            title = await new_tab.execute_script('return document.title')
            print(f"Заголовок новой вкладки: {title}")

            # Закройте новую вкладку, когда закончите
            await new_tab.close()

asyncio.run(handle_user_opened_tabs())
```

### Ключевые преимущества управления вкладками в Pydoll

1. **Шаблон «одиночка»**: предотвращает дублирование ресурсов и обеспечивает согласованное состояние
2. **Автоматическое обнаружение**: `get_opened_tabs()` находит все вкладки, включая открытые пользователем
3. **Параллельная обработка**: обрабатывайте несколько вкладок одновременно с помощью `asyncio`
4. **Управление ресурсами**: правильная очистка предотвращает утечки памяти
5. **Изоляция событий**: каждая вкладка поддерживает свои собственные обработчики событий и состояние

Это сложное управление вкладками делает Pydoll идеальным для:

- **Многостраничных рабочих процессов**, требующих координации между вкладками
- **Параллельного извлечения данных** из нескольких источников
- **Тестирования приложений**, использующих всплывающие окна или новые вкладки
- **Мониторинга поведения пользователей** на нескольких вкладках браузера


## Параллельный скрейпинг

Архитектура `async` в Pydoll позволяет одновременно извлекать данные с нескольких страниц или веб-сайтов для максимальной эффективности:

```python
import asyncio
from functools import partial
from pydoll.browser.chromium import Chrome

async def scrape_page(browser, url):
    """Обработать одну страницу и извлечь данные с помощью общего браузера"""
    # Создать новую вкладку для этого URL
    tab = await browser.new_tab()

    try:
        await tab.go_to(url)

        # Извлечь данные
        title = await tab.execute_script('return document.title')

        # Найти элементы и извлечь содержимое
        elements = await tab.find(class_name='article-content', find_all=True)
        content = []
        for element in elements:
            text = await element.text
            content.append(text)

        return {
            "url": url,
            "title": title,
            "content": content
        }
    finally:
        # Закройте вкладку, когда закончите, чтобы освободить ресурсы
        await tab.close()

async def main():
    # Список URL-адресов для параллельного скрейпинга
    urls = [
        'https://example.com/page1',
        'https://example.com/page2',
        'https://example.com/page3',
        'https://example.com/page4',
        'https://example.com/page5',
    ]

    async with Chrome() as browser:
        # Запустить браузер один раз
        await browser.start()

        # Создать частичную функцию с параметром браузера
        scrape_with_browser = partial(scrape_page, browser)

        # Обработать все URL-адреса одновременно, используя один и тот же браузер
        results = await asyncio.gather(*(scrape_with_browser(url) for url in urls))

    # Распечатать результаты
    for result in results:
        print(f"Scraped {result['url']}: {result['title']}")
        print(f"Найдено {len(result['content'])} блоков контента")

    return results

# Запустить параллельный скрейпинг
all_data = asyncio.run(main())
```

Этот подход обеспечивает значительное повышение производительности по сравнению с последовательным скрейпингом, особенно для задач, связанных с вводом-выводом, таких как веб-скрейпинг. Вместо того, чтобы ждать загрузки каждой страницы одна за другой, Pydoll обрабатывает их все одновременно, что значительно сокращает общее время выполнения. Например, скрейпинг 10 страниц, каждая из которых загружается 2 секунды, займет чуть более 2 секунд вместо 20+ секунд при последовательной обработке.

## Расширенное управление клавиатурой

Pydoll обеспечивает взаимодействие с клавиатурой, подобное человеческому, с точным контролем над поведением при наборе текста:

```python
import asyncio
from pydoll.browser.chromium import Chrome
from pydoll.common.keys import Keys

async def realistic_typing_example():
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://example.com/login')

        # Найти элементы формы входа
        username = await tab.find(id='username')
        password = await tab.find(id='password')

        # Ввод текста с реалистичной задержкой (интервал между нажатиями клавиш)
        await username.type_text("user@example.com", interval=0.15)

        # Использовать специальные комбинации клавиш
        await password.click()
        await password.key_down(Keys.SHIFT)
        await password.type_text("PASSWORD")
        await password.key_up(Keys.SHIFT)

        # Нажать Enter для отправки
        await password.press_keyboard_key(Keys.ENTER)

        # Подождать навигации
        await asyncio.sleep(2)
        print("Вход выполнен успешно!")

asyncio.run(realistic_typing_example())
```

Этот реалистичный ввод помогает избежать обнаружения веб-сайтами, которые ищут шаблоны автоматизации. Естественная синхронизация и возможность использовать специальные комбинации клавиш делают взаимодействия Pydoll практически неотличимыми от действий человека.

## Мощная система событий

Система событий Pydoll позволяет реагировать на события браузера в режиме реального времени:

```python
import asyncio
from pydoll.browser.chromium import Chrome
from pydoll.protocol.page.events import PageEvent

async def event_monitoring_example():
    async with Chrome() as browser:
        tab = await browser.start()

        # Мониторинг событий загрузки страницы
        async def on_page_loaded(event):
            print(f"🌐 Страница загружена: {event['params'].get('url')}")

        await tab.enable_page_events()
        await tab.on(PageEvent.LOAD_EVENT_FIRED, on_page_loaded)

        # Мониторинг сетевых запросов
        async def on_request(event):
            url = event['params']['request']['url']
            print(f"🔄 Запрос к: {url}")

        await tab.enable_network_events()
        await tab.on('Network.requestWillBeSent', on_request)

        # Перейдите и посмотрите на события в действии
        await tab.go_to('https://example.com')
        await asyncio.sleep(5)  # Дайте время, чтобы увидеть события

asyncio.run(event_monitoring_example())
```

Система событий делает Pydoll уникально мощным для мониторинга запросов и ответов API, создания реактивной автоматизации, отладки сложных веб-приложений и создания комплексных инструментов веб-мониторинга.

## Анализ сети и извлечение ответов

Pydoll предоставляет мощные методы для анализа сетевого трафика и извлечения данных ответов из веб-приложений. Эти возможности необходимы для мониторинга API, извлечения данных и отладки проблем, связанных с сетью.

### Анализ сетевых журналов

Метод `get_network_logs()` позволяет получать и анализировать все сетевые запросы, сделанные страницей:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def network_analysis_example():
    async with Chrome() as browser:
        tab = await browser.start()

        # Включить мониторинг сети
        await tab.enable_network_events()

        # Перейдите на страницу с вызовами API
        await tab.go_to('https://example.com/dashboard')

        # Подождите, пока страница загрузится и сделает запросы
        await asyncio.sleep(3)

        # Получить все сетевые журналы
        all_logs = await tab.get_network_logs()
        print(f"Всего сетевых запросов: {len(all_logs)}")

        # Отфильтровать журналы только для запросов API
        api_logs = await tab.get_network_logs(filter='api')
        print(f"Запросы API: {len(api_logs)}")

        # Отфильтровать журналы для определенного домена
        domain_logs = await tab.get_network_logs(filter='example.com')
        print(f"Запросы к example.com: {len(domain_logs)}")

        # Анализ шаблонов запросов
        for log in api_logs:
            request = log['params'].get('request', {})
            url = request.get('url', 'Unknown')
            method = request.get('method', 'Unknown')
            print(f"📡 {method} {url}")

asyncio.run(network_analysis_example())
```

### Извлечение тела ответа

Метод `get_network_response_body()` позволяет извлекать фактическое содержимое ответа из сетевых запросов:

```python
import asyncio
import json
from functools import partial
from pydoll.browser.chromium import Chrome
from pydoll.protocol.network.events import NetworkEvent

async def response_extraction_example():
    async with Chrome() as browser:
        tab = await browser.start()

        # Хранилище для ответов API
        api_responses = {}

        async def capture_api_responses(tab, event):
            """Захват тел ответов API"""
            request_id = event['params']['requestId']
            response = event['params']['response']
            url = response['url']

            # Захватывать только успешные ответы API
            if '/api/' in url and response['status'] == 200:
                try:
                    # Извлечь тело ответа
                    body = await tab.get_network_response_body(request_id)

                    # Попробовать разобрать как JSON
                    try:
                        data = json.loads(body)
                        api_responses[url] = data
                        print(f"✅ Захвачен ответ API от: {url}")
                        print(f"Ключи данных: {list(data.keys()) if isinstance(data, dict) else 'Ответ не в виде словаря'}")
                    except json.JSONDecodeError:
                        # Обработка ответов не в формате JSON
                        api_responses[url] = body
                        print(f"📄 Захвачен текстовый ответ от: {url} ({len(body)} символов)")

                except Exception as e:
                    print(f"❌ Не удалось получить тело ответа для {url}: {e}")

        # Включить мониторинг сети и зарегистрировать обратный вызов
        await tab.enable_network_events()
        await tab.on(NetworkEvent.RESPONSE_RECEIVED, partial(capture_api_responses, tab))

        # Перейдите на страницу с вызовами API
        await tab.go_to('https://jsonplaceholder.typicode.com')

        # Вызвать некоторые вызовы API, взаимодействуя со страницей
        await asyncio.sleep(5)

        # Отобразить захваченные ответы
        print(f"\n📊 Результаты анализа:")
        print(f"Захвачено {len(api_responses)} ответов API")

        for url, data in api_responses.items():
            if isinstance(data, dict):
                print(f"🔗 {url}: {len(data)} полей")
            else:
                print(f"🔗 {url}: {len(str(data))} символов")

        return api_responses

asyncio.run(response_extraction_example())
```

### Расширенный мониторинг сети

Объедините оба метода для всестороннего анализа сети:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def comprehensive_network_monitoring():
    async with Chrome() as browser:
        tab = await browser.start()

        # Включить мониторинг сети
        await tab.enable_network_events()

        # Перейдите в сложное веб-приложение
        await tab.go_to('https://example.com/app')

        # Подождите начальной загрузки страницы и вызовов API
        await asyncio.sleep(5)

        # Получить всесторонний анализ сети
        all_logs = await tab.get_network_logs()
        api_logs = await tab.get_network_logs(filter='api')
        static_logs = await tab.get_network_logs(filter='.js')

        print(f"📈 Сводка сетевого трафика:")
        print(f"   Всего запросов: {len(all_logs)}")
        print(f"   Вызовы API: {len(api_logs)}")
        print(f"   Файлы JavaScript: {len(static_logs)}")

        # Анализ типов запросов
        request_types = {}
        for log in all_logs:
            request = log['params'].get('request', {})
            url = request.get('url', '')

            if '/api/' in url:
                request_types['API'] = request_types.get('API', 0) + 1
            elif any(ext in url for ext in ['.js', '.css', '.png', '.jpg']):
                request_types['Static'] = request_types.get('Static', 0) + 1
            else:
                request_types['Other'] = request_types.get('Other', 0) + 1

        print(f"📊 Разбивка запросов: {request_types}")

        # Показать конечные точки API
        print(f"\n🔗 Вызванные конечные точки API:")
        for log in api_logs[:10]:  # Показать первые 10
            request = log['params'].get('request', {})
            method = request.get('method', 'GET')
            url = request.get('url', 'Unknown')
            print(f"   {method} {url}")

asyncio.run(comprehensive_network_monitoring())
```

Эти возможности анализа сети делают Pydoll идеальным для:

- **Тестирования API**: мониторинг и проверка ответов API
- **Анализа производительности**: отслеживание времени и размеров запросов
- **Извлечения данных**: извлечение динамического контента, загружаемого через AJAX
- **Отладки**: выявление неудачных запросов и проблем с сетью
- **Тестирования безопасности**: анализ шаблонов запросов/ответов

## Пользовательские настройки браузера

Pydoll теперь поддерживает расширенную настройку браузера через свойство `ChromiumOptions.browser_preferences`. Это позволяет вам устанавливать любые настройки браузера Chromium для вашей сессии автоматизации.

### Что вы можете настроить
- Каталог загрузки и поведение запроса
- Принятые языки
- Блокировка уведомлений
- Обработка PDF
- Любые другие поддерживаемые Chromium настройки

### Пример: установка настроек
```python
from pydoll.browser.chromium import Chrome
from pydoll.browser.options import ChromiumOptions

options = ChromiumOptions()
options.browser_preferences = {
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

# Вспомогательные методы для общих настроек
options.set_default_download_directory('/tmp/downloads')
options.set_accept_languages('en-US,en,pt-BR')
options.prompt_for_download = False

browser = Chrome(options=options)
```

Вы можете вызывать `browser_preferences` несколько раз — новые ключи будут объединены, а не заменены.

### Почему это полезно?
- Детальный контроль для скрейпинга, тестирования или автоматизации
- Избегайте всплывающих окон или нежелательных запросов
- Соответствие локали пользователя или автоматизация загрузок

---

## Поддержка загрузки файлов

Беспрепятственно обрабатывайте загрузку файлов в вашей автоматизации:

```python
import asyncio
import os
from pydoll.browser.chromium import Chrome

async def file_upload_example():
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://example.com/upload')

        # Метод 1: Прямой ввод файла
        file_input = await tab.find(tag_name='input', type='file')
        await file_input.set_input_files('path/to/document.pdf')

        # Метод 2: Использование выбора файла с кнопкой загрузки
        sample_file = os.path.join(os.getcwd(), 'sample.jpg')
        async with tab.expect_file_chooser(files=sample_file):
            upload_button = await tab.find(id='upload-button')
            await upload_button.click()

        # Отправить форму
        submit = await tab.find(id='submit-button')
        await submit.click()

        print("Файлы успешно загружены!")

asyncio.run(file_upload_example())
```

Загрузка файлов, как известно, сложна для автоматизации в других фреймворках, часто требуя обходных путей. Pydoll делает это простым благодаря поддержке как прямого ввода файлов, так и диалогового окна выбора файлов.

## Пример с несколькими браузерами

Pydoll работает с разными браузерами через согласованный API:

```python
import asyncio
from pydoll.browser.chromium import Chrome, Edge

async def multi_browser_example():
    # Запустить ту же автоматизацию в Chrome
    async with Chrome() as chrome:
        chrome_tab = await chrome.start()
        await chrome_tab.go_to('https://example.com')
        chrome_title = await chrome_tab.execute_script('return document.title')
        print(f"Заголовок Chrome: {chrome_title}")

    # Запустить ту же автоматизацию в Edge
    async with Edge() as edge:
        edge_tab = await edge.start()
        await edge_tab.go_to('https://example.com')
        edge_title = await edge_tab.execute_script('return document.title')
        print(f"Заголовок Edge: {edge_title}")

asyncio.run(multi_browser_example())
```

Кросс-браузерная совместимость без изменения вашего кода. Тестируйте свою автоматизацию в разных браузерах, чтобы убедиться, что она работает везде.

## Интеграция с прокси

В отличие от многих инструментов автоматизации, которые испытывают трудности с реализацией прокси, Pydoll предлагает встроенную поддержку прокси с полными возможностями аутентификации. Это делает его идеальным для:

- **Проектов веб-скрейпинга**, которым необходимо ротировать IP-адреса
- **Гео-таргетированного тестирования** приложений в разных регионах
- **Автоматизации, ориентированной на конфиденциальность**, которая требует анонимизации трафика
- **Тестирования веб-приложений** через корпоративные прокси

Настройка прокси в Pydoll проста:

```python
import asyncio
from pydoll.browser.chromium import Chrome
from pydoll.browser.options import ChromiumOptions

async def proxy_example():
    # Создать опции браузера
    options = ChromiumOptions()

    # Простой прокси без аутентификации
    options.add_argument('--proxy-server=192.168.1.100:8080')
    # Или прокси с аутентификацией
    # options.add_argument('--proxy-server=username:password@192.168.1.100:8080')

    # Обход прокси для определенных доменов
    options.add_argument('--proxy-bypass-list=*.internal.company.com,localhost')

    # Запустить браузер с конфигурацией прокси
    async with Chrome(options=options) as browser:
        tab = await browser.start()

        # Протестировать прокси, посетив сервис эха IP
        await tab.go_to('https://api.ipify.org')
        ip_address = await tab.execute_script('return document.body.textContent')
        print(f"Текущий IP-адрес: {ip_address}")

        # Продолжить автоматизацию
        await tab.go_to('https://example.com')
        title = await tab.execute_script('return document.title')
        print(f"Заголовок страницы: {title}")

asyncio.run(proxy_example())
```

## Работа с iFrame

Pydoll обеспечивает бесшовное взаимодействие с iframe через метод `get_frame()`:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def iframe_interaction():
    async with Chrome() as browser:
        tab = await browser.start()
        await tab.go_to('https://example.com/page-with-iframe')

        # Найти элемент iframe
        iframe_element = await tab.query('.hcaptcha-iframe', timeout=10)

        # Получить экземпляр Tab для содержимого iframe
        frame = await tab.get_frame(iframe_element)

        # Теперь взаимодействуйте с элементами внутри iframe
        submit_button = await frame.find(tag_name='button', class_name='submit')
        await submit_button.click()

        # Вы можете использовать все методы Tab для фрейма
        form_input = await frame.find(id='captcha-input')
        await form_input.type_text('verification-code')

        # Найти элементы различными методами
        links = await frame.find(tag_name='a', find_all=True)
        specific_element = await frame.query('#specific-id')

asyncio.run(iframe_interaction())
```

## Перехват запросов

Перехватывайте и изменяйте сетевые запросы перед их отправкой:

### Базовое изменение запроса

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def request_interception_example():
    async with Chrome() as browser:
        tab = await browser.start()

        # Определить перехватчик запросов
        async def intercept_request(event):
            request_id = event['params']['requestId']
            url = event['params']['request']['url']

            if '/api/' in url:
                # Получить исходные заголовки
                original_headers = event['params']['request'].get('headers', {})

                # Добавить пользовательские заголовки
                custom_headers = {
                    **original_headers,
                    'Authorization': 'Bearer my-token-123',
                    'X-Custom-Header': 'CustomValue'
                }

                print(f"🔄 Изменение запроса к: {url}")
                await tab.continue_request(
                        request_id=request_id,
                        headers=custom_headers
                )
            else:
                # Продолжить в обычном режиме для запросов не к API
                await tab.continue_request(request_id=request_id)

        # Включить перехват и зарегистрировать обработчик
        await tab.enable_request_interception()
        await tab.on('Fetch.requestPaused', intercept_request)

        # Перейдите, чтобы вызвать запросы
        await tab.go_to('https://example.com')
        await asyncio.sleep(5)  # Дайте время на обработку запросов

asyncio.run(request_interception_example())
```

### Блокировка нежелательных запросов

Используйте `fail_request` для блокировки определенных запросов, таких как реклама, трекеры или нежелательные ресурсы:

```python
import asyncio
from pydoll.browser.chromium import Chrome

async def block_requests_example():
    async with Chrome() as browser:
        tab = await browser.start()

        # Определить заблокированные домены и типы ресурсов
        blocked_domains = ['doubleclick.net', 'googletagmanager.com', 'facebook.com']
        blocked_resources = ['image', 'stylesheet', 'font']

        async def block_unwanted_requests(event):
            request_id = event['params']['requestId']
            url = event['params']['request']['url']
            resource_type = event['params'].get('resourceType', '').lower()

            # Блокировать запросы с определенных доменов
            if any(domain in url for domain in blocked_domains):
                print(f"🚫 Блокировка запроса к: {url}")
                await tab.fail_request(
                    request_id=request_id,
                    error_reason='BlockedByClient'
                )
                return

            # Блокировать определенные типы ресурсов (изображения, CSS, шрифты)
            if resource_type in blocked_resources:
                print(f"🚫 Блокировка {resource_type}: {url}")
                await tab.fail_request(
                    request_id=request_id,
                    error_reason='BlockedByClient'
                )
                return

            # Продолжить с разрешенными запросами
            await tab.continue_request(request_id=request_id)

        # Включить перехват и зарегистрировать обработчик
        await tab.enable_request_interception()
        await tab.on('Fetch.requestPaused', block_unwanted_requests)

        # Перейдите на страницу с множеством внешних ресурсов
        await tab.go_to('https://example.com')
        await asyncio.sleep(10)  # Дайте время, чтобы увидеть заблокированные запросы

asyncio.run(block_requests_example())
```

### Имитация ответов API

Используйте `fulfill_request` для возврата пользовательских ответов без выполнения фактических сетевых запросов:

```python
import asyncio
import json
from pydoll.browser.chromium import Chrome

async def mock_api_responses_example():
    async with Chrome() as browser:
        tab = await browser.start()

        async def mock_api_requests(event):
            request_id = event['params']['requestId']
            url = event['params']['request']['url']

            # Имитировать конечную точку API пользователя
            if '/api/user' in url:
                mock_user_data = {
                    "id": 123,
                    "name": "John Doe",
                    "email": "john@example.com",
                    "role": "admin"
                }

                print(f"🎭 Имитация ответа API для: {url}")
                await tab.fulfill_request(
                    request_id=request_id,
                    response_code=200,
                    response_headers={
                        'Content-Type': 'application/json',
                        'Access-Control-Allow-Origin': '*'
                    },
                    body=json.dumps(mock_user_data)
                )
                return

            # Имитировать конечную точку API продуктов
            elif '/api/products' in url:
                mock_products = [
                    {"id": 1, "name": "Product A", "price": 29.99},
                    {"id": 2, "name": "Product B", "price": 39.99},
                    {"id": 3, "name": "Product C", "price": 19.99}
                ]

                print(f"🎭 Имитация ответа API продуктов для: {url}")
                await tab.fulfill_request(
                    request_id=request_id,
                    response_code=200,
                    response_headers={'Content-Type': 'application/json'},
                    body=json.dumps(mock_products)
                )
                return

            # Имитировать ошибку API для определенных конечных точек
            elif '/api/error' in url:
                error_response = {"error": "Internal Server Error", "code": 500}

                print(f"🎭 Имитация ответа об ошибке для: {url}")
                await tab.fulfill_request(
                    request_id=request_id,
                    response_code=500,
                    response_headers={'Content-Type': 'application/json'},
                    body=json.dumps(error_response)
                )
                return

            # Продолжить с реальными запросами для всего остального
            await tab.continue_request(request_id=request_id)

        # Включить перехват и зарегистрировать обработчик
        await tab.enable_request_interception()
        await tab.on('Fetch.requestPaused', mock_api_requests)

        # Перейдите на страницу, которая делает вызовы API
        await tab.go_to('https://example.com/dashboard')
        await asyncio.sleep(5)  # Дайте время для вызовов API

asyncio.run(mock_api_responses_example())
```

### Расширенное управление запросами

Объедините все методы перехвата для всестороннего контроля над запросами:

```python
import asyncio
import json
from pydoll.browser.chromium import Chrome

async def advanced_request_control():
    async with Chrome() as browser:
        tab = await browser.start()

        async def advanced_interceptor(event):
            request_id = event['params']['requestId']
            url = event['params']['request']['url']
            method = event['params']['request']['method']
            headers = event['params']['request'].get('headers', {})

            print(f"📡 Перехвачен {method} запрос к: {url}")

            # Блокировать аналитику и отслеживание
            if any(tracker in url for tracker in ['analytics', 'tracking', 'ads']):
                print(f"🚫 Заблокирован запрос отслеживания: {url}")
                await tab.fail_request(request_id=request_id, error_reason='BlockedByClient')
                return

            # Имитировать конечную точку аутентификации
            if '/auth/login' in url and method == 'POST':
                mock_auth_response = {
                    "success": True,
                    "token": "mock-jwt-token-12345",
                    "user": {"id": 1, "username": "testuser"}
                }
                print(f"🎭 Имитация ответа на вход")
                await tab.fulfill_request(
                    request_id=request_id,
                    response_code=200,
                    response_headers={'Content-Type': 'application/json'},
                    body=json.dumps(mock_auth_response)
                )
                return

            # Добавить аутентификацию к запросам API
            if '/api/' in url and 'Authorization' not in headers:
                modified_headers = {
                    **headers,
                    'Authorization': 'Bearer mock-token-12345',
                    'X-Test-Mode': 'true'
                }
                print(f"🔧 Добавление заголовков аутентификации к: {url}")
                await tab.continue_request(
                    request_id=request_id,
                    headers=modified_headers
                )
                return

            # Продолжить с неизмененным запросом
            await tab.continue_request(request_id=request_id)

        # Включить перехват
        await tab.enable_request_interception()
        await tab.on('Fetch.requestPaused', advanced_interceptor)

        # Протестировать перехват
        await tab.go_to('https://example.com/app')
        await asyncio.sleep(10)

asyncio.run(advanced_request_control())
```

Эта мощная возможность позволяет вам:

- **Динамически добавлять заголовки аутентификации** к запросам API
- **Блокировать нежелательные ресурсы**, такие как реклама, трекеры и тяжелые изображения, для более быстрой загрузки
- **Имитировать ответы API** для тестирования без зависимостей от бэкенда
- **Имитировать сетевые ошибки** для тестирования обработки ошибок
- **Изменять полезную нагрузку запросов** перед их отправкой
- **Анализировать и отлаживать сетевой трафик** в режиме реального времени

Каждая из этих функций демонстрирует, что делает Pydoll инструментом автоматизации браузера следующего поколения, сочетая в себе мощь прямого управления браузером с интуитивно понятным, `async`-нативным API.