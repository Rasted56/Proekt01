<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сравнение браузеров — Яндекс, Firefox, Edge, Opera</title>
    <style>
        /* ========= ОБЩИЕ СТИЛИ ========= */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
            background: #f9fbfd;
            color: #1a2c3e;
            line-height: 1.5;
        }

        /* ========= БОКОВАЯ ПАНЕЛЬ ========= */
        .sidebar {
            position: fixed;
            left: 0;
            top: 0;
            width: 260px;
            height: 100vh;
            background: #1e2a3a;
            color: #e2e8f0;
            overflow-y: auto;
            z-index: 1000;
            box-shadow: 2px 0 8px rgba(0, 0, 0, 0.1);
        }

        .sidebar-header {
            padding: 1.5rem 1.2rem;
            border-bottom: 1px solid #2d3e4e;
            margin-bottom: 1rem;
        }

        .sidebar-header h3 {
            font-size: 1.3rem;
            font-weight: 600;
            color: #fff;
            margin-bottom: 0.25rem;
        }

        .sidebar-header p {
            font-size: 0.7rem;
            color: #8aaec4;
        }

        .sidebar-nav {
            padding: 0 0.8rem;
        }

        .nav-group {
            margin-bottom: 1.5rem;
        }

        .nav-group-title {
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
            color: #7f9eb5;
            padding: 0.5rem 1rem;
            margin-top: 0.5rem;
        }

        .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 0.6rem 1rem;
            margin: 2px 0;
            border-radius: 10px;
            transition: all 0.2s ease;
            font-size: 0.9rem;
            font-weight: 500;
            color: #cbdde9;
        }

        .nav-item:hover {
            background: #2d4053;
            color: white;
            cursor: pointer;
        }

        .nav-item.active {
            background: #3a5a74;
            color: white;
        }

        .nav-icon {
            width: 28px;
            font-size: 1.1rem;
            text-align: center;
        }

        .sidebar-nav a {
            text-decoration: none;
            color: inherit;
            display: flex;
            align-items: center;
            gap: 12px;
            width: 100%;
        }

        /* ========= ОСНОВНОЙ КОНТЕНТ ========= */
        .main-content {
            margin-left: 260px;
            padding: 2rem;
            max-width: 1400px;
        }

        /* ========= ПАНЕЛЬ ВЫБОРА БРАУЗЕРОВ ========= */
        .selector-panel {
            background: white;
            border-radius: 1rem;
            padding: 1rem 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #e4eaf1;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 1.5rem;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
        }

        .selector-title {
            font-weight: 600;
            color: #1e2a3a;
            font-size: 0.9rem;
        }

        .checkbox-group {
            display: flex;
            flex-wrap: wrap;
            gap: 1.2rem;
        }

        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            padding: 0.3rem 0.6rem;
            border-radius: 30px;
            transition: background 0.2s;
        }

        .checkbox-item:hover {
            background: #f0f4fa;
        }

        .checkbox-item input {
            width: 18px;
            height: 18px;
            cursor: pointer;
            accent-color: #4a627a;
        }

        .checkbox-item label {
            cursor: pointer;
            font-weight: 500;
            font-size: 0.9rem;
        }

        .checkbox-item.yandex label { color: #fc3f1d; }
        .checkbox-item.firefox label { color: #ff9500; }
        .checkbox-item.edge label { color: #0078d4; }
        .checkbox-item.opera label { color: #ff1a2e; }

        /* ========= ТАБЛИЦА ========= */
        .table-wrapper {
            overflow-x: auto;
            border-radius: 1rem;
            border: 1px solid #e4eaf1;
            background: white;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
        }

        .comparison-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.85rem;
            min-width: 700px;
        }

        .comparison-table th,
        .comparison-table td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid #eef2f8;
            vertical-align: top;
        }

        .comparison-table th {
            background: #f8fafd;
            font-weight: 700;
            color: #1e4a6b;
            border-bottom: 2px solid #e4eaf1;
        }

        .comparison-table tr:last-child td {
            border-bottom: none;
        }

        /* Стили для скрытых колонок */
        .comparison-table th.hidden-col,
        .comparison-table td.hidden-col {
            display: none;
        }

        /* Первая колонка всегда видима */
        .comparison-table th:first-child,
        .comparison-table td:first-child {
            background: #fefefe;
            font-weight: 600;
            color: #1e4663;
            position: sticky;
            left: 0;
            background: white;
            box-shadow: 2px 0 5px -2px rgba(0,0,0,0.05);
        }

        .highlight {
            font-weight: 700;
            color: #1f6392;
            background: #ecf7ff;
            border-radius: 12px;
            padding: 0.1rem 0.3rem;
            display: inline-block;
        }

        .badge-leader {
            background: #ffe6c7;
            color: #b45309;
            font-size: 0.7rem;
            font-weight: 600;
            padding: 0.2rem 0.6rem;
            border-radius: 20px;
            display: inline-block;
            margin-left: 0.3rem;
        }

        .feature-list {
            margin: 0;
            padding-left: 1.2rem;
        }

        .feature-list li {
            margin-bottom: 0.2rem;
        }

        /* ========= ЗАГОЛОВОК ========= */
        .page-header {
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid #e4eaf1;
        }

        .page-header h1 {
            font-size: 2rem;
            font-weight: 700;
            color: #1e2a3a;
            margin-bottom: 0.5rem;
        }

        .page-header .subtitle {
            font-size: 1rem;
            color: #4a627a;
        }

        /* ========= ПОДВАЛ ========= */
        .footer {
            text-align: center;
            padding: 2rem 0 1rem;
            color: #6b7c93;
            font-size: 0.75rem;
            border-top: 1px solid #e2eaf1;
            margin-top: 2rem;
        }

        /* ========= АДАПТИВНОСТЬ ========= */
        @media (max-width: 768px) {
            .sidebar {
                transform: translateX(-100%);
                transition: transform 0.3s ease;
            }
            
            .sidebar.open {
                transform: translateX(0);
            }
            
            .main-content {
                margin-left: 0;
                padding: 1rem;
            }
            
            .mobile-menu-btn {
                display: block;
                position: fixed;
                top: 1rem;
                left: 1rem;
                z-index: 1001;
                background: #1e2a3a;
                color: white;
                padding: 0.5rem 0.8rem;
                border-radius: 8px;
                cursor: pointer;
                font-size: 0.9rem;
            }
            
            .selector-panel {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .checkbox-group {
                gap: 0.8rem;
            }
        }

        @media (min-width: 769px) {
            .mobile-menu-btn {
                display: none;
            }
        }
    </style>
</head>
<body>

<!-- ========= БОКОВАЯ ПАНЕЛЬ ========= -->
<div class="sidebar" id="sidebar">
    <div class="sidebar-header">
        <h3>🧭 BrowserHub</h3>
        <p>Сравнение браузеров</p>
    </div>
    <div class="sidebar-nav">
        
        <div class="nav-group">
            <div class="nav-group-title">Основное</div>
			<div class="nav-item active">
                <a href="index.html">
                    <span class="nav-icon">🏠</span>
                    <span>Главная</span>
                </a>
            </div>
            <div class="nav-item active">
                <a href="comparison.html">
                    <span class="nav-icon">📊</span>
                    <span>Сравнительная таблица</span>
                </a>
            </div>
            <div class="nav-item">
                <a href="hotkeys.html">
                    <span class="nav-icon">⌨️</span>
                    <span>Горячие клавиши</span>
                </a>
            </div>
        </div>

        <div class="nav-group">
            <div class="nav-group-title">Браузеры</div>
            <div class="nav-item">
                <a href="yandex.html">
                    <span class="nav-icon">🔷</span>
                    <span>Яндекс Браузер</span>
                </a>
            </div>
            <div class="nav-item">
                <a href="firefox.html">
                    <span class="nav-icon">🦊</span>
                    <span>Mozilla Firefox</span>
                </a>
            </div>
            <div class="nav-item">
                <a href="edge.html">
                    <span class="nav-icon">🌊</span>
                    <span>Microsoft Edge</span>
                </a>
            </div>
            <div class="nav-item">
                <a href="opera.html">
                    <span class="nav-icon">🎭</span>
                    <span>Opera / Opera GX</span>
                </a>
            </div>
        </div>
    </div>
</div>

<!-- Кнопка для мобильных устройств -->
<div class="mobile-menu-btn" onclick="document.getElementById('sidebar').classList.toggle('open')">
    ☰ Меню
</div>

<!-- ОСНОВНОЙ КОНТЕНТ -->
<div class="main-content">
    <div class="page-header">
        <h1>📊 Сравнение браузеров</h1>
        <div class="subtitle">Детальное сравнение Яндекс Браузера, Firefox, Microsoft Edge и Opera</div>
    </div>

    <!-- Панель выбора браузеров -->
    <div class="selector-panel">
        <div class="selector-title">📌 Выберите браузеры для сравнения:</div>
        <div class="checkbox-group">
            <div class="checkbox-item yandex">
                <input type="checkbox" id="chk-yandex" value="yandex" checked>
                <label for="chk-yandex">🔷 Яндекс Браузер</label>
            </div>
            <div class="checkbox-item firefox">
                <input type="checkbox" id="chk-firefox" value="firefox" checked>
                <label for="chk-firefox">🦊 Mozilla Firefox</label>
            </div>
            <div class="checkbox-item edge">
                <input type="checkbox" id="chk-edge" value="edge" checked>
                <label for="chk-edge">🌊 Microsoft Edge</label>
            </div>
            <div class="checkbox-item opera">
                <input type="checkbox" id="chk-opera" value="opera" checked>
                <label for="chk-opera">🎭 Opera / Opera GX</label>
            </div>
        </div>
    </div>

    <!-- Таблица сравнения -->
    <div class="table-wrapper">
        <table class="comparison-table" id="comparison-table">
            <thead>
                <tr id="table-header">
                    <th>Критерий сравнения</th>
                    <th data-browser="yandex">🔷 Яндекс Браузер</th>
                    <th data-browser="firefox">🦊 Mozilla Firefox</th>
                    <th data-browser="edge">🌊 Microsoft Edge</th>
                    <th data-browser="opera">🎭 Opera / Opera GX</th>
                </tr>
            </thead>
            <tbody id="table-body">
                <!-- Движок -->
                <tr>
                    <td><strong>Браузерный движок</strong></td>
                    <td data-browser="yandex">Chromium (Blink)</td>
                    <td data-browser="firefox">Gecko (собственный)</td>
                    <td data-browser="edge">Chromium (Blink)</td>
                    <td data-browser="opera">Chromium (Blink)</td>
                </tr>
                <!-- Скорость и производительность -->
                <tr>
                    <td><strong>Скорость и производительность</strong></td>
                    <td data-browser="yandex"><span class="highlight">Высокая</span> (оптимизация, Турбо 2.0)<span class="badge-leader">⚡ лидер сжатия</span></td>
                    <td data-browser="firefox">Отличная JS-производительность, графически может уступать</td>
                    <td data-browser="edge"><span class="highlight">Лидер графики</span> (Motionmark 1.3), быстрый UI</td>
                    <td data-browser="opera"><span class="highlight">Лидер JavaScript</span> (Jetstream2), отличная графика</td>
                </tr>
                <!-- Безопасность -->
                <tr>
                    <td><strong>Безопасность (защита от фишинга)</strong></td>
                    <td data-browser="yandex"><span class="highlight">Абсолютный лидер</span> — нейросети Protect распознают до 85/100 фишинговых сайтов</td>
                    <td data-browser="firefox">Базовая защита (Google Safe Browsing), строгая политика приватности</td>
                    <td data-browser="edge">Базовая защита (Microsoft Defender SmartScreen)</td>
                    <td data-browser="opera">Слабая встроенная защита (обнаружила 6/100 в тестах)</td>
                </tr>
                <!-- Уникальные функции -->
                <tr>
                    <td><strong>Встроенные уникальные функции</strong></td>
                    <td data-browser="yandex">«Алиса», «Видеосеть», Турбо 2.0, перевод видео, проверка паролей</td>
                    <td data-browser="firefox">Контейнеры (Multi-Account), Firefox View, мощный PDF-редактор, ETP защита от слежки</td>
                    <td data-browser="edge">Купонный кешбэк, Split Screen, вертикальные вкладки, Drops (облачное хранилище)</td>
                    <td data-browser="opera">Встроенный бесплатный VPN*, мессенджеры в боковой панели, Opera GX для геймеров</td>
                </tr>
                <!-- Конфиденциальность -->
                <tr>
                    <td><strong>Конфиденциальность</strong></td>
                    <td data-browser="yandex">Средняя (глубокая интеграция с сервисами Яндекса, сбор телеметрии)</td>
                    <td data-browser="firefox"><span class="highlight">Очень высокая</span>, открытый код, ETP, приоритет защиты данных</td>
                    <td data-browser="edge">Средняя (связан с экосистемой Microsoft, телеметрия Windows)</td>
                    <td data-browser="opera">Средняя, с 2025 года в ряде версий привязка к поиску Яндекса</td>
                </tr>
                <!-- Дизайн -->
                <tr>
                    <td><strong>Дизайн и интерфейс</strong></td>
                    <td data-browser="yandex">Минималистичный, умная строка, дизайн «Табло», прозрачные панели</td>
                    <td data-browser="firefox">Классический, функциональный, глубокая кастомизация, темная тема</td>
                    <td data-browser="edge">Современный (Windows 11), Mica, плавные анимации, вертикальные вкладки</td>
                    <td data-browser="opera">Яркий, геймерский (Opera GX), настраиваемая боковая панель, множество тем</td>
                </tr>
                <!-- Удобство -->
                <tr>
                    <td><strong>Удобство использования</strong></td>
                    <td data-browser="yandex">Для русскоязычных пользователей, низкий порог входа, Алиса, группировка вкладок</td>
                    <td data-browser="firefox">Для ценителей приватности, гибкая настройка, контейнеры, новичкам сложнее</td>
                    <td data-browser="edge">Для продуктивных пользователей Windows, синхронизация с Microsoft 365, коллекции</td>
                    <td data-browser="opera">Для любителей соцсетей и музыки, боковая панель с Telegram/WhatsApp, YouTube</td>
                </tr>
                <!-- ВКонтакте -->
                <tr>
                    <td><strong>Работа с ВКонтакте</strong></td>
                    <td data-browser="yandex">Отлично: поиск музыки из умной строки, Алиса включает записи, встроенный перевод</td>
                    <td data-browser="firefox">Отлично, но иногда отключать защиту для виджетов</td>
                    <td data-browser="edge">Отлично, интеграция с буфером обмена, стабильно</td>
                    <td data-browser="opera">Отлично, закрепление VK в боковой панели — всегда на связи</td>
                </tr>
                <!-- Rutube -->
                <tr>
                    <td><strong>Работа с Rutube</strong></td>
                    <td data-browser="yandex">Уникальные фишки: перевод и озвучка видео нейросетями, краткий пересказ, отдельное окно</td>
                    <td data-browser="firefox">Отлично, работает без нареканий (часто даже стабильнее)</td>
                    <td data-browser="edge">Хорошо/отлично, но из-за санкций может потребоваться VPN</td>
                    <td data-browser="opera">Стабильно на Chromium, без особых уникальных функций</td>
                </tr>
                <!-- Популярность -->
                <tr>
                    <td><strong>Популярность (регионы)</strong></td>
                    <td data-browser="yandex">Россия, страны СНГ (доля в Рунете ~36,65%)</td>
                    <td data-browser="firefox">Германия, Европа (лидер приватности)</td>
                    <td data-browser="edge">США, Великобритания, Канада, Австралия (браузер по умолчанию в Windows)</td>
                    <td data-browser="opera">Россия, Украина, Восточная Европа</td>
                </tr>
                <!-- Кроссплатформенность -->
                <tr>
                    <td><strong>Кроссплатформенность</strong></td>
                    <td data-browser="yandex">Windows, macOS, Linux, Android, iOS</td>
                    <td data-browser="firefox">Windows, macOS, Linux, Android, iOS</td>
                    <td data-browser="edge">Windows, macOS, Linux, Android, iOS</td>
                    <td data-browser="opera">Windows, macOS, Linux, Android, iOS</td>
                </tr>
            </tbody>
        </table>
    </div>

    <!-- Примечание -->
    <div style="background: #f0f4fa; border-radius: 0.8rem; padding: 0.8rem 1.2rem; margin-top: 1rem; font-size: 0.8rem; color: #4a627a;">
        <p>※ Opera VPN может требовать дополнительной активации в зависимости от региона. Турбо режим в Яндекс.Браузере прекращён с 2025 года в связи с ростом скоростей интернета, но сохранены другие технологии оптимизации.</p>
        <p style="margin-top: 0.3rem;">※ Данные актуальны на март 2026. Производительность основана на тестах Motionmark 1.3, Jetstream2 и других бенчмарках.</p>
    </div>

    <div class="footer">
        © 2026 Сравнение браузеров. Данные основаны на официальных источниках, тестах производительности и открытой статистике.
    </div>
</div>

<script>
    // Функция для обновления видимости колонок в зависимости от выбранных галочек
    function updateTableVisibility() {
        // Получаем состояние галочек
        const showYandex = document.getElementById('chk-yandex').checked;
        const showFirefox = document.getElementById('chk-firefox').checked;
        const showEdge = document.getElementById('chk-edge').checked;
        const showOpera = document.getElementById('chk-opera').checked;

        // Получаем все заголовки и ячейки таблицы
        const headers = document.querySelectorAll('#table-header th');
        const rows = document.querySelectorAll('#table-body tr');

        // Определяем порядок колонок: индекс 0 - критерий, 1 - Яндекс, 2 - Firefox, 3 - Edge, 4 - Opera
        const browserIndex = {
            yandex: 1,
            firefox: 2,
            edge: 3,
            opera: 4
        };

        // Скрываем/показываем заголовки
        if (headers[1]) {
            headers[1].style.display = showYandex ? '' : 'none';
        }
        if (headers[2]) {
            headers[2].style.display = showFirefox ? '' : 'none';
        }
        if (headers[3]) {
            headers[3].style.display = showEdge ? '' : 'none';
        }
        if (headers[4]) {
            headers[4].style.display = showOpera ? '' : 'none';
        }

        // Скрываем/показываем ячейки в каждой строке
        rows.forEach(row => {
            const cells = row.querySelectorAll('td');
            if (cells[1]) cells[1].style.display = showYandex ? '' : 'none';
            if (cells[2]) cells[2].style.display = showFirefox ? '' : 'none';
            if (cells[3]) cells[3].style.display = showEdge ? '' : 'none';
            if (cells[4]) cells[4].style.display = showOpera ? '' : 'none';
        });
    }

    // Добавляем обработчики событий на все галочки
    document.getElementById('chk-yandex').addEventListener('change', updateTableVisibility);
    document.getElementById('chk-firefox').addEventListener('change', updateTableVisibility);
    document.getElementById('chk-edge').addEventListener('change', updateTableVisibility);
    document.getElementById('chk-opera').addEventListener('change', updateTableVisibility);

    // Вызываем функцию при загрузке страницы (все галочки по умолчанию включены)
    updateTableVisibility();

    // Скрипт для закрытия панели при клике вне её на мобильных
    document.addEventListener('click', function(event) {
        if (window.innerWidth <= 768) {
            const sidebar = document.getElementById('sidebar');
            const menuBtn = document.querySelector('.mobile-menu-btn');
            if (sidebar && !sidebar.contains(event.target) && menuBtn && !menuBtn.contains(event.target)) {
                sidebar.classList.remove('open');
            }
        }
    });
		// Автоматическая подсветка активного пункта меню
	    function setActiveNavItem() {
        const currentPath = window.location.pathname;
        const currentFile = currentPath.split('/').pop() || 'index.html';
        
        const navLinks = document.querySelectorAll('.sidebar-nav a');
        navLinks.forEach(link => {
            const href = link.getAttribute('href');
            if (href === currentFile) {
                link.parentElement.classList.add('active');
            } else {
                link.parentElement.classList.remove('active');
            }
        });
    }
    
    setActiveNavItem();
</script>

</body>
