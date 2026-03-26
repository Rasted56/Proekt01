<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mozilla Firefox — приватный и гибкий браузер</title>
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
            max-width: 1200px;
        }

        /* ========= КАРТОЧКИ ========= */
        .card {
            background: white;
            border-radius: 1rem;
            padding: 1.5rem;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
            border: 1px solid #e4eaf1;
            margin-bottom: 1.5rem;
        }

        .card h2 {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid #ff9500;
            display: inline-block;
        }

        .card h3 {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 0.75rem;
            color: #1e2a3a;
        }

        /* ========= СЕТКИ ========= */
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }

        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }

        /* ========= СПИСКИ ========= */
        .feature-list {
            list-style: none;
            margin-top: 1rem;
        }

        .feature-list li {
            padding: 0.6rem 0;
            border-bottom: 1px solid #eff3f8;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }

        .feature-list li strong {
            min-width: 100px;
            color: #ff6b35;
            font-weight: 600;
        }

        /* ========= БЭЙДЖИ ========= */
        .badge {
            background: #eef2f8;
            padding: 0.25rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
            color: #ff6b35;
            display: inline-block;
        }

        .badge-row {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin: 1rem 0;
        }

        .feature-tag {
            background: #fff0e6;
            padding: 0.3rem 1rem;
            border-radius: 30px;
            font-size: 0.8rem;
            font-weight: 500;
            color: #ff6b35;
            display: inline-block;
        }

        .feature-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem;
            margin-top: 1rem;
        }

        /* ========= СТАТИСТИКА ========= */
        .stat-block {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 1rem;
        }

        .stat-item {
            flex: 1;
            min-width: 100px;
            background: #f8fafc;
            padding: 0.8rem;
            text-align: center;
            border-radius: 0.8rem;
            border: 1px solid #eef2f8;
        }

        .stat-number {
            font-size: 1.8rem;
            font-weight: 700;
            color: #ff6b35;
        }

        .stat-label {
            font-size: 0.75rem;
            color: #6b7c93;
            margin-top: 0.25rem;
        }

        /* ========= ЦИТАТЫ ========= */
        .quote-block {
            background: #fef5e9;
            padding: 1.2rem;
            border-radius: 0.8rem;
            border-left: 4px solid #ff9500;
            margin: 1rem 0;
            font-style: italic;
            color: #4a5568;
        }

        /* ========= ССЫЛКИ ========= */
        .wiki-link {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: #ff6b35;
            color: white;
            padding: 0.5rem 1.2rem;
            border-radius: 30px;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            transition: background 0.2s;
        }

        .wiki-link:hover {
            background: #e55a2a;
        }

        /* ========= ЗАГОЛОВОК ========= */
        .page-header {
            margin-bottom: 2rem;
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
            
            .grid-2, .grid-3 {
                grid-template-columns: 1fr;
            }
            
            .feature-list li {
                flex-direction: column;
                gap: 4px;
            }
            
            .feature-list li strong {
                min-width: auto;
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
            <div class="nav-item">
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
            <div class="nav-item active">
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
        <h1>🦊 Mozilla Firefox</h1>
        <div class="subtitle">Свободный браузер с фокусом на приватность, открытый код и полную настраиваемость</div>
    </div>

    <div class="badge-row">
        <span class="badge">🔒 ETP (Enhanced Tracking Protection)</span>
        <span class="badge">📦 Контейнеры</span>
        <span class="badge">🛠️ Открытый код</span>
        <span class="badge">🌍 Gecko движок</span>
        <span class="badge">🎨 Глубокая кастомизация</span>
    </div>

    <a href="https://ru.wikipedia.org/wiki/Firefox" target="_blank" class="wiki-link">📖 Подробнее на Википедии →</a>

    <!-- Основные характеристики -->
    <div class="grid-2">
        <div class="card">
            <h2>⚙️ Технические данные</h2>
            <ul class="feature-list">
                <li><strong>Движок:</strong> Gecko (собственная разработка)</li>
                <li><strong>Разработчик:</strong> Mozilla Foundation / Mozilla Corporation</li>
                <li><strong>Первая версия:</strong> 9 ноября 2004 года</li>
                <li><strong>Платформы:</strong> Windows, macOS, Linux, Android, iOS</li>
                <li><strong>Лицензия:</strong> MPL 2.0 (свободное ПО)</li>
                <li><strong>Особенность:</strong> Единственный не-Chromium браузер в списке</li>
            </ul>
        </div>

        <div class="card">
            <h2>🔒 Приватность и безопасность</h2>
            <ul class="feature-list">
                <li><strong>ETP:</strong> Усиленная защита от отслеживания (Enhanced Tracking Protection)</li>
                <li><strong>Контейнеры:</strong> Изоляция данных разных сайтов (Facebook Container и др.)</li>
                <li><strong>Блокировка трекеров:</strong> По умолчанию блокирует социальные трекеры, кросс-сайтные cookie</li>
                <li><strong>Firefox Monitor:</strong> Проверка утечек паролей</li>
                <li><strong>Приватность:</strong> Очень высокая, минимальный сбор телеметрии, открытый код</li>
            </ul>
        </div>
    </div>

    <!-- Уникальные функции -->
    <div class="card">
        <h2>✨ Уникальные возможности</h2>
        <div class="grid-3">
            <div>
                <h3>📦 Контейнеры</h3>
                <p>Multi-Account Containers позволяют разделять личный и рабочий профили, изолируя данные разных сайтов друг от друга.</p>
            </div>
            <div>
                <h3>📄 Firefox View</h3>
                <p>Удобный обзор недавно закрытых вкладок, синхронизация между устройствами, быстрый доступ к сохранённому.</p>
            </div>
            <div>
                <h3>🔧 about:config</h3>
                <p>Расширенные настройки: доступ к сотням скрытых параметров для тонкой настройки браузера под себя.</p>
            </div>
        </div>
        <div class="feature-tags">
            <span class="feature-tag">📑 Встроенный PDF-редактор</span>
            <span class="feature-tag">🎨 Полная кастомизация интерфейса</span>
            <span class="feature-tag">🔍 Умная строка с подсказками</span>
            <span class="feature-tag">🌙 Тёмная тема</span>
            <span class="feature-tag">🔄 Синхронизация через Firefox Account</span>
        </div>
    </div>

    <!-- Производительность и разработчики -->
    <div class="grid-2">
        <div class="card">
            <h2>⚡ Производительность</h2>
            <div class="stat-block">
                <div class="stat-item">
                    <div class="stat-number">🚀</div>
                    <div class="stat-label">Быстрый JavaScript (SpiderMonkey)</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">🎯</div>
                    <div class="stat-label">Оптимизация памяти</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">🖥️</div>
                    <div class="stat-label">WebRender — ускоренный рендеринг</div>
                </div>
            </div>
            <div class="quote-block">
                💡 Firefox использует современный движок рендеринга WebRender, обеспечивающий плавную графику и быструю загрузку страниц. В тестах JavaScript показывает отличные результаты, но может немного уступать Chromium-браузерам в сложной графике.
            </div>
        </div>

        <div class="card">
            <h2>🛠️ Для разработчиков</h2>
            <ul class="feature-list">
                <li><strong>DevTools:</strong> Мощные инструменты разработчика с отладкой CSS Grid, Flexbox</li>
                <li><strong>Firefox Developer Edition:</strong> Отдельная версия для веб-разработчиков</li>
                <li><strong>Отладка мобильных устройств:</strong> Поддержка USB-отладки для Android</li>
                <li><strong>WebExtensions API:</strong> Совместимость с расширениями Chromium</li>
                <li><strong>about:performance:</strong> Встроенный менеджер задач браузера</li>
            </ul>
        </div>
    </div>

    <!-- Дизайн и настройка -->
    <div class="card">
        <h2>🎨 Дизайн и кастомизация</h2>
        <div class="grid-3">
            <div>
                <h3>🎭 Гибкий интерфейс</h3>
                <p>Можно перемещать, скрывать и настраивать практически любой элемент интерфейса: панели инструментов, кнопки, адресную строку.</p>
            </div>
            <div>
                <h3>🎨 Темы и оформление</h3>
                <p>Огромная библиотека тем (включая полноценные цветовые схемы), поддержка светлой и тёмной темы, возможность создавать свои темы.</p>
            </div>
            <div>
                <h3>🔧 about:config</h3>
                <p>Сотни скрытых настроек позволяют изменить поведение браузера до неузнаваемости — от сглаживания шрифтов до экспериментальных функций.</p>
            </div>
        </div>
        <div class="feature-tags">
            <span class="feature-tag">📌 Закреплённые вкладки</span>
            <span class="feature-tag">📱 Адаптивный дизайн</span>
            <span class="feature-tag">🎯 Пиктограммы в адресной строке</span>
        </div>
    </div>

    <!-- Популярность и факты -->
    <div class="grid-2">
        <div class="card">
            <h2>📊 Популярность и география</h2>
            <ul class="feature-list">
                <li><strong>Германия:</strong> Один из самых популярных браузеров (доля ~25-30%)</li>
                <li><strong>Европа:</strong> Стабильно входит в топ-3 в странах ЕС</li>
                <li><strong>Мир:</strong> Около 3-4% глобальной доли (на 2026 год)</li>
                <li><strong>Аудитория:</strong> Технически подкованные пользователи, разработчики, сторонники открытого ПО</li>
                <li><strong>Корпоративный сектор:</strong> Firefox ESR (Extended Support Release) для бизнеса</li>
            </ul>
        </div>

        <div class="card">
            <h2>📌 Интересные факты</h2>
            <ul class="feature-list">
                <li><strong>Имя:</strong> Изначально назывался Phoenix, затем Firebird, а с 2004 — Firefox</li>
                <li><strong>Маскот:</strong> Лиса (Firefox — красная панда, но в логотипе лиса, обнимающая земной шар)</li>
                <li><strong>Первый браузер:</strong> Один из первых массовых браузеров с блокировкой всплывающих окон и вкладками</li>
                <li><strong>Quantum:</strong> В 2017 году вышел Firefox Quantum — полное переосмысление движка</li>
                <li><strong>Некоммерческая основа:</strong> Mozilla Foundation управляет развитием, приоритет — открытый интернет</li>
            </ul>
        </div>
    </div>

    <!-- Официальные ссылки -->
    <div style="background: #eef2f8; border-radius: 0.8rem; padding: 1rem 1.5rem; margin-top: 0.5rem;">
        <p style="font-weight: 500; margin-bottom: 0.5rem;">🔗 Официальные ресурсы:</p>
        <p>
            <a href="https://www.mozilla.org/firefox/" target="_blank" style="margin-right: 1.5rem; color: #ff6b35; text-decoration: none;">Официальный сайт</a>
            <a href="https://support.mozilla.org/ru/products/firefox" target="_blank" style="margin-right: 1.5rem; color: #ff6b35; text-decoration: none;">Центр поддержки</a>
            <a href="https://www.mozilla.org/ru/firefox/developer/" target="_blank" style="margin-right: 1.5rem; color: #ff6b35; text-decoration: none;">Firefox Developer Edition</a>
            <a href="https://ru.wikipedia.org/wiki/Firefox" target="_blank" style="color: #ff6b35; text-decoration: none;">Википедия</a>
        </p>
    </div>

    <div class="footer">
        © 2026 Обзор актуален на март 2026. Данные основаны на официальных источниках Mozilla, тестах производительности и открытой статистике. Firefox — зарегистрированный товарный знак Mozilla Foundation.
    </div>
</div>

<script>
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
</html>
