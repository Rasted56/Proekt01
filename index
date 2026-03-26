<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Титульный лист — Сравнение браузеров</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
            background: #f5f7fc;
            color: #1a2c3e;
            line-height: 1.5;
        }

        /* Боковая панель */
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

        /* Основной контент */
        .main-content {
            margin-left: 260px;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 2rem;
        }

        /* Титульная карточка */
        .title-card {
            max-width: 700px;
            width: 100%;
            background: white;
            border-radius: 1rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            padding: 2.5rem;
            text-align: center;
            border: 1px solid #e4eaf1;
        }

        .title-card h1 {
            font-size: 2rem;
            font-weight: 700;
            margin: 1rem 0 0.5rem;
            color: #1e2a3a;
        }

        .title-card h2 {
            font-size: 1.2rem;
            font-weight: 500;
            color: #4a627a;
            margin-bottom: 2rem;
        }

        .info-block {
            margin: 2rem 0;
            text-align: left;
            border-top: 1px solid #eef2f8;
            border-bottom: 1px solid #eef2f8;
            padding: 1.5rem 0;
        }

        .info-row {
            margin: 0.8rem 0;
            font-size: 1rem;
        }

        .info-row strong {
            display: inline-block;
            width: 140px;
            font-weight: 600;
            color: #1e4663;
        }

        .date {
            margin-top: 2rem;
            color: #6b7c93;
            font-size: 0.9rem;
        }

        hr {
            margin: 1rem 0;
            border: none;
            height: 1px;
            background: #eef2f8;
        }

        /* Адаптив */
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
            .title-card {
                padding: 1.5rem;
            }
            .info-row strong {
                width: 120px;
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

<!-- БОКОВАЯ ПАНЕЛЬ -->
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

<div class="mobile-menu-btn" onclick="document.getElementById('sidebar').classList.toggle('open')">
    ☰ Меню
</div>

<div class="main-content">
    <div class="title-card">
        
        <h1>Сравнительный анализ<br>веб-браузеров</h1>
        <h2>Яндекс Браузер, Firefox, Edge, Opera</h2>
        
        <div class="info-block">
            <div class="info-row">
                <strong>Учебное учреждение:</strong> 
                <!-- Название учереждения -->
            Слободской колледж педагогики и социальных отношений.
            </div>
            <div class="info-row">
                <strong>Студент:</strong> 
                <!-- Моя фамилия -->
                Шумилов К.A.
            </div>
            <div class="info-row">
                <strong>Преподаватель:</strong> 
                <!--  Фамилия препода -->
                Желваков
            </div>
        </div>
        
        <div class="date">
            <!-- Город -->
            Слободской, 2026
        </div>
        
    </div>
</div>

<script>
    // Подсветка активного пункта меню
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

    // Закрытие панели на мобильных
    document.addEventListener('click', function(event) {
        if (window.innerWidth <= 768) {
            const sidebar = document.getElementById('sidebar');
            const menuBtn = document.querySelector('.mobile-menu-btn');
            if (sidebar && !sidebar.contains(event.target) && menuBtn && !menuBtn.contains(event.target)) {
                sidebar.classList.remove('open');
            }
        }
    });
</script>

</body>
</html>
