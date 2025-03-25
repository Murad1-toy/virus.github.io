<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Кибербезопасность: вирусы и защита</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #00ff88;
            --secondary: #00b3ff;
            --dark: #121212;
            --darker: #0d0d0d;
            --light: #f5f5f5;
            --gray: #333;
            --light-gray: #444;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--dark);
            color: var(--light);
            line-height: 1.6;
        }
        
        header {
            background-color: var(--darker);
            padding: 1rem 5%;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary);
        }
        
        .logo i {
            font-size: 1.8rem;
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
        }
        
        .nav-links a {
            color: var(--light);
            text-decoration: none;
            transition: color 0.3s;
            position: relative;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--primary);
            transition: width 0.3s;
        }
        
        .nav-links a:hover::after {
            width: 100%;
        }
        
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--light);
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        .hero {
            background: linear-gradient(135deg, var(--darker), var(--gray));
            padding: 5rem 5%;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none"><path fill="rgba(0,255,136,0.05)" d="M0,0 L100,0 L100,100 L0,100 Z" /><path fill="none" stroke="rgba(0,255,136,0.2)" stroke-width="0.5" d="M0,50 Q25,25 50,50 T100,50" /></svg>');
            background-size: 50px 50px;
            opacity: 0.5;
        }
        
        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            position: relative;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .hero p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto 2rem;
            position: relative;
        }
        
        .btn {
            display: inline-block;
            padding: 0.8rem 1.8rem;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            color: var(--dark);
            border: none;
            border-radius: 50px;
            font-weight: bold;
            text-decoration: none;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
            overflow: hidden;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 255, 136, 0.2);
        }
        
        .btn::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, rgba(255,255,255,0.3), rgba(255,255,255,0));
            transform: translateX(-100%);
            transition: transform 0.3s;
        }
        
        .btn:hover::after {
            transform: translateX(100%);
        }
        
        section {
            padding: 4rem 5%;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }
        
        .section-title h2 {
            font-size: 2.5rem;
            display: inline-block;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .section-title::after {
            content: '';
            display: block;
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            margin: 1rem auto 0;
            border-radius: 2px;
        }
        
        .viruses-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .virus-card {
            background-color: var(--gray);
            border-radius: 10px;
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            border-left: 4px solid var(--primary);
        }
        
        .virus-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        
        .virus-card-header {
            padding: 1.5rem;
            background-color: var(--light-gray);
            border-bottom: 1px solid rgba(0, 255, 136, 0.2);
        }
        
        .virus-card-header h3 {
            color: var(--primary);
            margin-bottom: 0.5rem;
        }
        
        .virus-card-body {
            padding: 1.5rem;
        }
        
        .virus-card-body ul {
            list-style-type: none;
        }
        
        .virus-card-body ul li {
            margin-bottom: 0.5rem;
            position: relative;
            padding-left: 1.5rem;
        }
        
        .virus-card-body ul li::before {
            content: '→';
            position: absolute;
            left: 0;
            color: var(--primary);
        }
        
        .protection-methods {
            background-color: var(--darker);
        }
        
        .methods-container {
            max-width: 1000px;
            margin: 0 auto;
        }
        
        .method {
            display: flex;
            gap: 2rem;
            margin-bottom: 3rem;
            align-items: center;
        }
        
        .method:nth-child(even) {
            flex-direction: row-reverse;
        }
        
        .method-icon {
            flex: 0 0 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2rem;
            color: var(--dark);
        }
        
        .method-content {
            flex: 1;
        }
        
        .method-content h3 {
            color: var(--primary);
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }
        
        .survey {
            background: linear-gradient(135deg, var(--darker), var(--gray));
        }
        
        .survey-container {
            max-width: 800px;
            margin: 0 auto;
            background-color: var(--gray);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }
        
        .form-group input[type="text"],
        .form-group input[type="email"],
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            background-color: var(--light-gray);
            border: 1px solid rgba(0, 255, 136, 0.2);
            border-radius: 5px;
            color: var(--light);
            font-size: 1rem;
        }
        
        .form-group textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        .radio-group, .checkbox-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }
        
        .radio-option, .checkbox-option {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .radio-option input, .checkbox-option input {
            accent-color: var(--primary);
        }
        
        .results {
            margin-top: 3rem;
            padding: 2rem;
            background-color: var(--light-gray);
            border-radius: 10px;
            display: none;
        }
        
        .results h3 {
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        .chart-container {
            height: 300px;
            margin-top: 2rem;
            position: relative;
        }
        
        footer {
            background-color: var(--darker);
            padding: 3rem 5%;
            text-align: center;
        }
        
        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;
        }
        
        .social-links {
            display: flex;
            gap: 1.5rem;
        }
        
        .social-links a {
            color: var(--light);
            font-size: 1.5rem;
            transition: color 0.3s;
        }
        
        .social-links a:hover {
            color: var(--primary);
        }
        
        .copyright {
            color: var(--light-gray);
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                position: absolute;
                top: 70px;
                left: 0;
                width: 100%;
                background-color: var(--darker);
                flex-direction: column;
                gap: 1rem;
                padding: 1rem 5%;
                box-shadow: 0 5px 10px rgba(0, 0, 0, 0.3);
            }
            
            .nav-links.active {
                display: flex;
            }
            
            .mobile-menu-btn {
                display: block;
            }
            
            .hero h1 {
                font-size: 2.2rem;
            }
            
            .method {
                flex-direction: column;
            }
            
            .method:nth-child(even) {
                flex-direction: column;
            }
            
            .method-icon {
                margin-bottom: 1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">
                <i class="fas fa-shield-alt"></i>
                <span>CyberShield</span>
            </div>
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
            <div class="nav-links" id="navLinks">
                <a href="#viruses">Вирусы</a>
                <a href="#protection">Защита</a>
                <a href="#survey">Анкета</a>
                <a href="#results">Результаты</a>
            </div>
        </nav>
    </header>

    <section class="hero">
        <h1>Кибербезопасность в современном мире</h1>
        <p>Узнайте о самых опасных компьютерных угрозах и эффективных методах защиты ваших данных и устройств</p>
        <a href="#survey" class="btn">Пройти анкету</a>
    </section>

    <section id="viruses">
        <div class="section-title">
            <h2>Типы компьютерных вирусов</h2>
        </div>
        <div class="viruses-grid">
            <div class="virus-card">
                <div class="virus-card-header">
                    <h3>Трояны</h3>
                    <p>Маскируются под полезные программы</p>
                </div>
                <div class="virus-card-body">
                    <ul>
                        <li>Крадут пароли и банковские данные</li>
                        <li>Создают бэкдоры для хакеров</li>
                        <li>Распространяются через пиратский софт</li>
                    </ul>
                </div>
            </div>
            <div class="virus-card">
                <div class="virus-card-header">
                    <h3>Черви</h3>
                    <p>Самостоятельно распространяются по сети</p>
                </div>
                <div class="virus-card-body">
                    <ul>
                        <li>Используют уязвимости ОС</li>
                        <li>Загружают систему и замедляют работу</li>
                        <li>Пример: WannaCry, NotPetya</li>
                    </ul>
                </div>
            </div>
            <div class="virus-card">
                <div class="virus-card-header">
                    <h3>Шифровальщики</h3>
                    <p>Ransomware-атаки</p>
                </div>
                <div class="virus-card-body">
                    <ul>
                        <li>Шифруют файлы и требуют выкуп</li>
                        <li>Часто атакуют компании и госучреждения</li>
                        <li>Ущерб исчисляется миллионами долларов</li>
                    </ul>
                </div>
            </div>
            <div class="virus-card">
                <div class="virus-card-header">
                    <h3>Шпионские программы</h3>
                    <p>Spyware и кейлоггеры</p>
                </div>
                <div class="virus-card-body">
                    <ul>
                        <li>Записывают нажатия клавиш</li>
                        <li>Делают скриншоты экрана</li>
                        <li>Перехватывают пароли и сообщения</li>
                    </ul>
                </div>
            </div>
            <div class="virus-card">
                <div class="virus-card-header">
                    <h3>Рекламные вирусы</h3>
                    <p>Adware и браузерные угонщики</p>
                </div>
                <div class="virus-card-body">
                    <ul>
                        <li>Показывают навязчивую рекламу</li>
                        <li>Меняют стартовую страницу браузера</li>
                        <li>Замедляют скорость интернета</li>
                    </ul>
                </div>
            </div>
            <div class="virus-card">
                <div class="virus-card-header">
                    <h3>Ботнеты</h3>
                    <p>Сети зараженных компьютеров</p>
                </div>
                <div class="virus-card-body">
                    <ul>
                        <li>Используются для DDoS-атак</li>
                        <li>Рассылают спам и вирусы</li>
                        <li>Действуют скрытно от пользователя</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section class="protection-methods" id="protection">
        <div class="section-title">
            <h2>Методы защиты</h2>
        </div>
        <div class="methods-container">
            <div class="method">
                <div class="method-icon">
                    <i class="fas fa-shield-virus"></i>
                </div>
                <div class="method-content">
                    <h3>Антивирусное ПО</h3>
                    <p>Используйте надежные антивирусные программы с регулярными обновлениями. Лучшие решения включают Kaspersky, Bitdefender и Norton. Обязательно активируйте режим реального времени для постоянной защиты.</p>
                </div>
            </div>
            <div class="method">
                <div class="method-icon">
                    <i class="fas fa-lock"></i>
                </div>
                <div class="method-content">
                    <h3>Обновления системы</h3>
                    <p>Регулярно обновляйте операционную систему и все установленные программы. Большинство вирусов используют известные уязвимости, которые уже исправлены в последних версиях ПО.</p>
                </div>
            </div>
            <div class="method">
                <div class="method-icon">
                    <i class="fas fa-user-secret"></i>
                </div>
                <div class="method-content">
                    <h3>Осторожность в сети</h3>
                    <p>Не открывайте подозрительные письма и вложения, не переходите по сомнительным ссылкам. Фишинг остается одним из самых распространенных способов заражения.</p>
                </div>
            </div>
            <div class="method">
                <div class="method-icon">
                    <i class="fas fa-cloud-upload-alt"></i>
                </div>
                <div class="method-content">
                    <h3>Резервное копирование</h3>
                    <p>Регулярно создавайте резервные копии важных данных на внешних носителях или в облачных хранилищах. Это защитит вас от потери информации при атаке шифровальщиков.</p>
                </div>
            </div>
            <div class="method">
                <div class="method-icon">
                    <i class="fas fa-key"></i>
                </div>
                <div class="method-content">
                    <h3>Надежные пароли</h3>
                    <p>Используйте сложные уникальные пароли для разных сервисов. Менеджер паролей и двухфакторная аутентификация значительно повысят вашу безопасность в интернете.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="survey" id="survey">
        <div class="section-title">
            <h2>Анкета о кибербезопасности</h2>
        </div>
        <div class="survey-container">
            <form id="cyberSurvey">
                <div class="form-group">
                    <label for="age">1. Ваш возраст:</label>
                    <select id="age" name="age" required>
                        <option value="" disabled selected>Выберите вариант</option>
                        <option value="under18">До 18 лет</option>
                        <option value="18-25">18-25 лет</option>
                        <option value="26-35">26-35 лет</option>
                        <option value="36-50">36-50 лет</option>
                        <option value="over50">Старше 50 лет</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>2. Ваш род деятельности:</label>
                    <div class="radio-group">
                        <div class="radio-option">
                            <input type="radio" id="student" name="occupation" value="student" required>
                            <label for="student">Ученик/студент</label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="it" name="occupation" value="it">
                            <label for="it">IT-специалист</label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="office" name="occupation" value="office">
                            <label for="office">Офисный работник</label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="business" name="occupation" value="business">
                            <label for="business">Предприниматель</label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="other" name="occupation" value="other">
                            <label for="other">Другое</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>3. Сталкивались ли вы с компьютерными вирусами?</label>
                    <div class="radio-group">
                        <div class="radio-option">
                            <input type="radio" id="virusYes" name="virusExperience" value="yes" required>
                            <label for="virusYes">Да</label>
                        </div>
                        <div class="radio-option">
                            <input type="radio" id="virusNo" name="virusExperience" value="no">
                            <label for="virusNo">Нет</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group" id="virusConsequencesGroup" style="display: none;">
                    <label>4. Если да, то какие последствия это вызвало? (можно выбрать несколько)</label>
                    <div class="checkbox-group">
                        <div class="checkbox-option">
                            <input type="checkbox" id="dataLoss" name="consequences" value="dataLoss">
                            <label for="dataLoss">Потеря данных</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="slowPc" name="consequences" value="slowPc">
                            <label for="slowPc">Замедление работы компьютера</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="ransomware" name="consequences" value="ransomware">
                            <label for="ransomware">Вымогательство (ransomware)</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="identityTheft" name="consequences" value="identityTheft">
                            <label for="identityTheft">Кража личных данных</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="otherConsequences" name="consequences" value="other">
                            <label for="otherConsequences">Другое</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>5. Какие антивирусные программы вы используете? (можно выбрать несколько)</label>
                    <div class="checkbox-group">
                        <div class="checkbox-option">
                            <input type="checkbox" id="avast" name="antivirus" value="avast">
                            <label for="avast">Avast / AVG</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="kaspersky" name="antivirus" value="kaspersky">
                            <label for="kaspersky">Kaspersky</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="norton" name="antivirus" value="norton">
                            <label for="norton">Norton</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="defender" name="antivirus" value="defender">
                            <label for="defender">Windows Defender</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="malwarebytes" name="antivirus" value="malwarebytes">
                            <label for="malwarebytes">Malwarebytes</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="none" name="antivirus" value="none">
                            <label for="none">Не использую</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>6. Какие меры предосторожности вы применяете? (можно выбрать несколько)</label>
                    <div class="checkbox-group">
                        <div class="checkbox-option">
                            <input type="checkbox" id="caution" name="precautions" value="caution">
                            <label for="caution">Не открываю подозрительные письма/ссылки</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="updates" name="precautions" value="updates">
                            <label for="updates">Регулярно обновляю ОС и программы</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="passwords" name="precautions" value="passwords">
                            <label for="passwords">Использую сложные пароли</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="backup" name="precautions" value="backup">
                            <label for="backup">Делаю резервные копии данных</label>
                        </div>
                        <div class="checkbox-option">
                            <input type="checkbox" id="nothing" name="precautions" value="nothing">
                            <label for="nothing">Ничего из перечисленного</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="suggestions">7. Какие способы защиты от вирусов вы считаете самыми эффективными?</label>
                    <textarea id="suggestions" name="suggestions" placeholder="Ваши предложения..."></textarea>
                </div>
                
                <button type="submit" class="btn">Отправить ответы</button>
            </form>
            
            <div class="results" id="results">
                <h3>Результаты анкетирования</h3>
                <p>На основе ответов 154 участников:</p>
                
                <div class="chart-container">
                    <!-- Здесь будет график с результатами -->
                    <canvas id="resultsChart"></canvas>
                </div>
                
                <p>Основные выводы:</p>
                <ul>
                    <li>68% респондентов сталкивались с вирусами</li>
                    <li>Наиболее распространенные антивирусы: Windows Defender (45%), Kaspersky (32%)</li>
                    <li>Только 28% регулярно делают резервные копии</li>
                    <li>Главная проблема - недостаток знаний о кибербезопасности</li>
                </ul>
            </div>
        </div>
    </section>

    <footer>
        <div class="footer-content">
            <div class="logo">
                <i class="fas fa-shield-alt"></i>
                <span>CyberShield</span>
            </div>
            <div class="social-links">
                <a href="#"><i class="fab fa-vk"></i></a>
                <a href="#"><i class="fab fa-telegram"></i></a>
                <a href="#"><i class="fab fa-youtube"></i></a>
                <a href="#"><i class="fab fa-github"></i></a>
            </div>
            <p class="copyright">© 2023 CyberShield. Все права защищены.</p>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // Мобильное меню
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const navLinks = document.getElementById('navLinks');
        
        mobileMenuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });
        
        // Показ/скрытие вопросов о последствиях
        const virusYes = document.getElementById('virusYes');
        const virusNo = document.getElementById('virusNo');
        const virusConsequencesGroup = document.getElementById('virusConsequencesGroup');
        
        virusYes.addEventListener('change', () => {
            virusConsequencesGroup.style.display = 'block';
        });
        
        virusNo.addEventListener('change', () => {
            virusConsequencesGroup.style.display = 'none';
        });
        
        // Обработка формы
        const surveyForm = document.getElementById('cyberSurvey');
        const resultsSection = document.getElementById('results');
        
        surveyForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            // Здесь должна быть отправка данных на сервер
            // Для демонстрации просто покажем результаты
            
            resultsSection.style.display = 'block';
            window.location.href = '#results';
            
            // Создаем демонстрационный график
            const ctx = document.getElementById('resultsChart').getContext('2d');
            
            if (window.resultsChart) {
                window.resultsChart.destroy();
            }
            
            window.resultsChart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['До 18', '18-25', '26-35', '36-50', '50+'],
                    datasets: [{
                        label: 'Сталкивались с вирусами',
                        data: [65, 72, 68, 63, 55],
                        backgroundColor: '#00ff88',
                        borderColor: '#00b3ff',
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    scales: {
                        y: {
                            beginAtZero: true,
                            max: 100,
                            title: {
                                display: true,
                                text: 'Процент респондентов'
                            }
                        },
                        x: {
                            title: {
                                display: true,
                                text: 'Возрастные группы'
                            }
                        }
                    }
                }
            });
        });
        
        // Плавная прокрутка
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // Закрываем мобильное меню после клика
                    navLinks.classList.remove('active');
                }
            });
        });
    </script>
</body>
</html>
