<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jacoding | معرض أعمال مهندس برمجيات</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* --- المتغيرات العامة والألوان --- */
        :root {
            --bg-primary: #0f172a;
            --bg-secondary: #1e293b;
            --accent-blue: #3b82f6;
            --accent-purple: #8b5cf6;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --gradient: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            --glass: rgba(30, 41, 59, 0.7);
            --border-glass: rgba(255, 255, 255, 0.05);
        }

        /* --- التنسيقات الأساسية --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-primary);
            color: var(--text-main);
            overflow-x: hidden;
        }

        a {
            text-decoration: none;
            color: inherit;
        }

        li {
            list-style: none;
        }

        /* --- الهيدر وشريط التنقل --- */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border-glass);
            z-index: 1000;
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 900;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            font-weight: 600;
            transition: color 0.3s;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            right: 0;
            background: var(--gradient);
            transition: width 0.3s;
        }

        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }

        .nav-links a:hover {
            color: var(--accent-blue);
        }

        .menu-btn {
            display: none;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* --- القسم الترحيبي (Hero) --- */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 0 1rem;
            background: radial-gradient(circle at 50% 50%, rgba(59, 130, 246, 0.1), transparent 50%);
            margin-top: 4rem;
        }

        .hero-content h1 {
            font-size: 3.5rem;
            font-weight: 900;
            margin-bottom: 1rem;
            line-height: 1.2;
        }

        .hero-content h1 span {
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-content p {
            font-size: 1.2rem;
            color: var(--text-muted);
            max-width: 600px;
            margin: 0 auto 2rem auto;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 0.8rem 2rem;
            border-radius: 50px;
            font-weight: 700;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        .btn-primary {
            background: var(--gradient);
            color: #fff;
            border: none;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(139, 92, 246, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-main);
            border: 2px solid var(--accent-blue);
        }

        .btn-secondary:hover {
            background: rgba(59, 130, 246, 0.1);
            transform: translateY(-3px);
        }

        /* --- الأقسام العامة --- */
        section {
            padding: 6rem 5%;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 60px;
            height: 4px;
            background: var(--gradient);
            margin: 10px auto 0 auto;
            border-radius: 2px;
        }

        /* --- قسم الخدمات --- */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .service-card {
            background: var(--glass);
            border: 1px solid var(--border-glass);
            padding: 2.5rem 2rem;
            border-radius: 16px;
            text-align: center;
            transition: transform 0.3s, border-color 0.3s;
        }

        .service-card:hover {
            transform: translateY(-10px);
            border-color: var(--accent-blue);
        }

        .service-icon {
            font-size: 3rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1.5rem;
        }

        .service-card h3 {
            margin-bottom: 1rem;
            font-size: 1.4rem;
        }

        .service-card p {
            color: var(--text-muted);
            font-size: 0.95rem;
            line-height: 1.6;
        }

        /* --- قسم معرض الأعمال (Portfolio) --- */
        .portfolio-filters {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            background: var(--bg-secondary);
            color: var(--text-muted);
            border: 1px solid var(--border-glass);
            padding: 0.5rem 1.5rem;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .filter-btn.active, .filter-btn:hover {
            background: var(--gradient);
            color: #fff;
            border-color: transparent;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
        }

        .portfolio-item {
            background: var(--bg-secondary);
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid var(--border-glass);
            transition: transform 0.3s;
        }

        .portfolio-item:hover {
            transform: scale(1.02);
        }

        .project-img-placeholder {
            height: 200px;
            background: linear-gradient(45deg, #1e1b4b, #311042);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: rgba(255, 255, 255, 0.1);
        }

        .project-img-placeholder::before {
            content: '</>';
            font-family: monospace;
            font-weight: bold;
        }

        .project-info {
            padding: 1.5rem;
        }

        .project-tag {
            font-size: 0.8rem;
            background: rgba(59, 130, 246, 0.15);
            color: var(--accent-blue);
            padding: 0.2rem 0.8rem;
            border-radius: 20px;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 0.8rem;
        }

        .project-info h3 {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }

        .project-info p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 1.5rem;
            line-height: 1.5;
        }

        .project-links {
            display: flex;
            justify-content: space-between;
        }

        .project-link {
            font-size: 0.9rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--accent-blue);
        }

        .project-link:hover {
            color: var(--accent-purple);
        }

        /* --- قسم الاتصال --- */
        .contact-container {
            max-width: 700px;
            margin: 0 auto;
            background: var(--glass);
            border: 1px solid var(--border-glass);
            padding: 3rem;
            border-radius: 24px;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 1rem;
            background: var(--bg-primary);
            border: 1px solid var(--border-glass);
            border-radius: 8px;
            color: var(--text-main);
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .form-group input:focus, .form-group textarea:focus {
            outline: none;
            border-color: var(--accent-blue);
        }

        /* --- الفوتر --- */
        footer {
            background: #090d16;
            text-align: center;
            padding: 2rem;
            border-top: 1px solid var(--border-glass);
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* --- شاشات التجاوب (Responsive) --- */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                flex-direction: column;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: var(--bg-primary);
                padding: 2rem;
                border-bottom: 1px solid var(--border-glass);
                gap: 1.5rem;
                text-align: center;
            }

            .nav-links.active {
                display: flex;
            }

            .menu-btn {
                display: block;
            }

            .hero-content h1 {
                font-size: 2.3rem;
            }

            .contact-container {
                padding: 1.5rem;
            }
        }
    </style>
</head>
<body>

    <!-- الهيدر -->
    <header>
        <div class="logo">jacoding</div>
        <div class="menu-btn" id="menuBtn">
            <i class="fas fa-bars"></i>
        </div>
        <ul class="nav-links" id="navLinks">
            <li><a href="#home" class="active">الرئيسية</a></li>
            <li><a href="#services">الخدمات</a></li>
            <li><a href="#portfolio">المشاريع</a></li>
            <li><a href="#contact">اتصل بي</a></li>
        </ul>
    </header>

    <!-- القسم الترحيبي -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>أهلاً بك، أنا مهندس برمجيات ومصمم <span>منصات رقمية</span></h1>
            <p>أقوم بتحويل الأفكار المعقدة إلى مواقع ويب وتطبيقات ذكية، احترافية، ومخصصة بالكامل لتلبية احتياجاتك واحتياجات طلاب التخرج.</p>
            <div class="cta-buttons">
                <a href="#portfolio" class="btn btn-primary">رؤية أعمالي</a>
                <a href="#contact" class="btn btn-secondary">تواصل معي</a>
            </div>
        </div>
    </section>

    <!-- قسم الخدمات -->
    <section id="services">
        <h2 class="section-title">ماذا أقدم؟</h2>
        <div class="services-grid">
            <div class="service-card">
                <div class="service-icon"><i class="fas fa-code"></i></div>
                <h3>تطوير المواقع الإلكترونية</h3>
                <p>بناء مواقع تعريفية، ومتاجر إلكترونية متكاملة سريعة ومتوافقة مع محركات البحث وسهلة الاستخدام.</p>
            </div>
            <div class="service-card">
                <div class="service-icon"><i class="fas fa-mobile-alt"></i></div>
                <h3>تصميم وتطوير التطبيقات</h3>
                <p>برمجة تطبيقات هواتف ذكية (iOS & Android) بأحدث التقنيات مع واجهات مستخدم سلسة وعصرية.</p>
            </div>
            <div class="service-card">
                <div class="service-icon"><i class="fas fa-graduation-cap"></i></div>
                <h3>مشاريع تخرج للطلاب</h3>
                <p>مساعدة طلاب كليات هندسة وحاسبات في بناء مشاريع تخرجهم برمجياً مع شرح كامل للكود والتوثيق.</p>
            </div>
        </div>
    </section>

    <!-- قسم معرض الأعمال -->
    <section id="portfolio">
        <h2 class="section-title">معرض المشاريع والأعمال</h2>
        
        <div class="portfolio-filters">
            <button class="filter-btn active" data-filter="all">الكل</button>
            <button class="filter-btn" data-filter="web">مواقع ويب</button>
            <button class="filter-btn" data-filter="app">تطبيقات</button>
            <button class="filter-btn" data-filter="grad">مشاريع تخرج</button>
        </div>

        <div class="portfolio-grid">
            <!-- مشروع 1 -->
            <div class="portfolio-item" data-category="web">
                <div class="project-img-placeholder"></div>
                <div class="project-info">
                    <span class="project-tag">موقع ويب</span>
                    <h3>منصة تجارة إلكترونية متكاملة</h3>
                    <p>موقع بيع وشراء متكامل مع لوحة تحكم كاملة لإدارة المنتجات والمبيعات والمخزون.</p>
                    <div class="project-links">
                        <a href="#" class="project-link"><i class="fas fa-external-link-alt"></i> معاينة حية</a>
                        <a href="#" class="project-link"><i class="fab fa-github"></i> كود المصدر</a>
                    </div>
                </div>
            </div>

            <!-- مشروع 2 -->
            <div class="portfolio-item" data-category="app">
                <div class="project-img-placeholder" style="background: linear-gradient(45deg, #0f172a, #0369a1);"></div>
                <div class="project-info">
                    <span class="project-tag">تطبيق موبايل</span>
                    <h3>تطبيق توصيل وخدمات لوجستية</h3>
                    <p>تطبيق يعتمد على الخرائط الحية لتتبع الشحنات والمناديب وتسهيل عمليات التوصيل للشركات.</p>
                    <div class="project-links">
                        <a href="#" class="project-link"><i class="fas fa-external-link-alt"></i> معاينة حية</a>
                        <a href="#" class="project-link"><i class="fab fa-github"></i> كود المصدر</a>
                    </div>
                </div>
            </div>

            <!-- مشروع 3 -->
            <div class="portfolio-item" data-category="grad">
                <div class="project-img-placeholder" style="background: linear-gradient(45deg, #311042, #581c87);"></div>
                <div class="project-info">
                    <span class="project-tag">مشروع تخرج</span>
                    <h3>نظام ذكي لإدارة البلاغات والتقارير</h3>
                    <p>مشروع تخرج متكامل يعتمد على الذكاء الاصطناعي لتصنيف البلاغات الأمنية والمجتمعية وإدارتها.</p>
                    <div class="project-links">
                        <a href="#" class="project-link"><i class="fas fa-external-link-alt"></i> معاينة حية</a>
                        <a href="#" class="project-link"><i class="fab fa-github"></i> كود المصدر</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- قسم الاتصال -->
    <section id="contact">
        <h2 class="section-title">ابدأ مشروعك الآن</h2>
        <div class="contact-container">
            <form id="contactForm" onsubmit="event.preventDefault(); alert('تم إرسال رسالتك بنجاح! شكراً لتواصلك.');">
                <div class="form-group">
                    <label for="name">الاسم الكريم</label>
                    <input type="text" id="name" required placeholder="أدخل اسمك هنا">
                </div>
                <div class="form-group">
                    <label for="email">البريد الإلكتروني</label>
                    <input type="email" id="email" required placeholder="name@example.com">
                </div>
                <div class="form-group">
                    <label for="message">تفاصيل المشروع أو الطلب</label>
                    <textarea id="message" rows="5" required placeholder="اشرح لي باختصار ما هي فكرتك أو مشروعك..."></textarea>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">إرسال الرسالة</button>
            </form>
        </div>
    </section>

    <!-- الفوتر -->
    <footer>
        <p>&copy; 2026 jacoding. جميع الحقوق محفوظة.</p>
    </footer>

    <!-- السكريبت الخاص بالتفاعلية والفلترة والدعم لشاشات الموبايل -->
    <script>
        const menuBtn = document.getElementById('menuBtn');
        const navLinks = document.getElementById('navLinks');

        menuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });

        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                navLinks.classList.remove('active');
                document.querySelectorAll('.nav-links a').forEach(el => el.classList.remove('active'));
                link.classList.add('active');
            });
        });

        const filterButtons = document.querySelectorAll('.filter-btn');
        const portfolioItems = document.querySelectorAll('.portfolio-item');

        filterButtons.forEach(button => {
            button.addEventListener('click', () => {
                filterButtons.forEach(btn => btn.classList.remove('active'));
                button.classList.add('active');

                const filterValue = button.getAttribute('data-filter');

                portfolioItems.forEach(item => {
                    if (filterValue === 'all' || item.getAttribute('data-category') === filterValue) {
                        item.style.display = 'block';
                    } else {
                        item.style.display = 'none';
                    }
                });
            });
        });
    </script>
</body>
</html>
