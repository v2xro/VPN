<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>رویداد ایکسرو | رندم باکس | پنجره‌های تمام صفحه</title>
    <!-- Font Awesome 6 (Free) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* ----- RESET & BASE ----- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
            -webkit-user-select: none;
        }

        html, body {
            width: 100%;
            height: 100%;
            overflow: hidden;
            position: fixed;
            top: 0;
            left: 0;
            background: #000; /* این پس زمینه هرگز نمایش داده نمی‌شه چون دو پنجره تمام صفحه روی اون قرار می‌گیرن */
        }

        body {
            font-family: 'Segoe UI', 'Vazir', system-ui, -apple-system, 'Inter', sans-serif;
            background: radial-gradient(circle at 30% 10%, #0c0c12, #020205);
            /* بدنه اصلی (صفحه خالی) هرگز دیده نمی‌شه چون پنجره دوم تمام صفحه روی اونه و پنجره اول هم قبلاً بسته شده */
        }

        /* ----- لایه اول: اسپلش اسکرین (پنجره اول) که بعد 3 ثانیه بسته می‌شه ----- */
        .window-splash {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, #0f0a03, #000000);
            z-index: 10000; /* بالاترین لایه */
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            backdrop-filter: blur(3px);
            transition: opacity 0.6s ease, visibility 0.6s ease;
            opacity: 1;
            visibility: visible;
        }

        .splash-content {
            text-align: center;
            transform: scale(0.95);
            animation: pulseGlow 1.4s infinite alternate;
        }

        .splash-content i {
            font-size: 5.5rem;
            background: linear-gradient(135deg, #ffd700, #ff8c00, #ff4500);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            filter: drop-shadow(0 0 15px #ff6600);
            margin-bottom: 0.5rem;
        }

        .splash-content h2 {
            font-size: 2.5rem;
            font-weight: 900;
            letter-spacing: 4px;
            background: linear-gradient(135deg, #ffd700, #ffb347);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 8px rgba(255,69,0,0.5);
        }

        .splash-content p {
            margin-top: 12px;
            font-size: 0.8rem;
            color: #ffaa66;
            opacity: 0.8;
        }

        @keyframes pulseGlow {
            0% { transform: scale(0.95); text-shadow: 0 0 0px #ff8c00; }
            100% { transform: scale(1.05); text-shadow: 0 0 20px #ff4500; }
        }

        /* ----- لایه دوم: پنجره اصلی (تمام صفحه، هرگز بسته نمی‌شه) ----- */
        .window-main {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 30% 10%, #0c0c12, #020205);
            z-index: 1000; /* پایین‌تر از اسپلش ولی بالای بدنه اصلی */
            overflow-y: auto;
            overflow-x: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0.8rem;
            opacity: 0; /* ابتدا مخفی، بعد از بسته شدن اسپلش با انیمیشن نمایش داده میشه */
            transition: opacity 0.7s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            visibility: visible;
            backdrop-filter: blur(0px);
        }

        /* محتوای داخل پنجره اصلی (همان طراحی قبلی با بهبود) */
        .main-content {
            width: 100%;
            max-width: 780px;
            margin: 0 auto;
            backdrop-filter: blur(4px);
            height: auto;
            max-height: 98vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            z-index: 10;
        }

        /* نوار درصد خط خطی */
        .percentage-bg {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 6px;
            background: rgba(30, 30, 40, 0.7);
            z-index: 20;
            backdrop-filter: blur(4px);
            border-top: 1px solid rgba(255, 140, 0, 0.3);
        }
        
        .percentage-fill {
            width: 0%;
            height: 100%;
            background: linear-gradient(90deg, #ffd700, #ff8c00, #ff4500);
            transition: width 0.08s linear;
            box-shadow: 0 0 12px #ff8c00;
            position: relative;
            overflow: hidden;
        }
        
        .percentage-fill::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: repeating-linear-gradient(
                45deg,
                rgba(255, 255, 255, 0.2) 0px,
                rgba(255, 255, 255, 0.2) 2px,
                transparent 2px,
                transparent 8px
            );
            pointer-events: none;
        }
        
        .percentage-number {
            position: fixed;
            bottom: 12px;
            left: 12px;
            background: rgba(0,0,0,0.6);
            backdrop-filter: blur(8px);
            padding: 3px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-family: monospace;
            font-weight: bold;
            color: #ffd966;
            z-index: 21;
            border: 1px solid #ff8c00;
            letter-spacing: 1px;
        }

        /* خطوط مورب زیبا روی پنجره اصلی */
        .window-main::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: repeating-linear-gradient(
                35deg,
                rgba(255, 215, 0, 0.02) 0px,
                rgba(255, 215, 0, 0.02) 1px,
                transparent 1px,
                transparent 10px
            );
            pointer-events: none;
            z-index: 0;
        }
        
        .window-main::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: repeating-linear-gradient(
                125deg,
                rgba(255, 100, 0, 0.03) 0px,
                rgba(255, 100, 0, 0.03) 2px,
                transparent 2px,
                transparent 14px
            );
            pointer-events: none;
            z-index: 0;
        }

        .hero {
            text-align: center;
            margin-bottom: 1rem;
            flex-shrink: 0;
            animation: fadeInDown 0.7s cubic-bezier(0.2, 0.9, 0.4, 1.1);
        }
        .hero h1 {
            font-size: 2rem;
            font-weight: 900;
            background: linear-gradient(135deg, #ffd700, #ffb347, #ff4500, #ffd700);
            background-size: 250% auto;
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: shine 4s linear infinite;
            letter-spacing: -1px;
            text-shadow: 0 0 15px rgba(255, 69, 0, 0.4);
        }
        @keyframes shine {
            0% { background-position: 0% 50%; }
            100% { background-position: 200% 50%; }
        }
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .badge-event {
            background: linear-gradient(95deg, #2c1a0a, #1a0e05);
            display: inline-block;
            padding: 0.3rem 1rem;
            border-radius: 40px;
            font-size: 0.7rem;
            margin-top: 0.5rem;
            backdrop-filter: blur(8px);
            border: 1px solid #ffd700;
            color: #ffd700;
            font-weight: bold;
            box-shadow: 0 0 8px rgba(255, 215, 0, 0.3);
        }

        .how-it-works {
            background: rgba(0, 0, 0, 0.65);
            backdrop-filter: blur(12px);
            border-radius: 1.5rem;
            padding: 0.9rem;
            margin-bottom: 1rem;
            border: 1px solid rgba(255, 180, 70, 0.6);
            box-shadow: 0 12px 30px -12px rgba(0, 0, 0, 0.6), 0 0 12px rgba(255, 69, 0, 0.2);
        }
        
        .how-it-works h3 {
            font-size: 0.9rem;
            text-align: center;
            margin-bottom: 0.4rem;
            color: #ffd700;
        }
        
        .steps {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.7rem;
            margin-top: 0.6rem;
        }
        
        .step {
            background: rgba(10, 10, 10, 0.75);
            backdrop-filter: blur(6px);
            padding: 0.5rem 0.2rem;
            border-radius: 1rem;
            border: 1px solid #ff8c00;
            text-align: center;
            transition: all 0.25s ease;
        }
        .step:hover {
            transform: translateY(-3px);
            border-color: #ffd700;
            background: rgba(31, 20, 8, 0.9);
            box-shadow: 0 0 12px rgba(255, 215, 0, 0.4);
        }
        .step i {
            font-size: 1rem;
            color: #ffd700;
            margin-bottom: 0.2rem;
        }
        .step h4 {
            font-size: 0.7rem;
            margin: 0.2rem 0;
            font-weight: bold;
            color: #ffb347;
        }
        .step p {
            font-size: 0.55rem;
            color: #e0bc8c;
            line-height: 1.25;
        }

        .single-order-btn {
            display: flex;
            justify-content: center;
            margin: 0.2rem 0 0.5rem;
        }
        .big-order-btn {
            background: linear-gradient(105deg, #ff8c00, #ff4500, #cc3300);
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 3rem;
            font-weight: bold;
            font-size: 1.15rem;
            color: #fff3e0;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            gap: 12px;
            box-shadow: 0 0 20px rgba(255, 69, 0, 0.7);
            width: 90%;
            max-width: 340px;
            justify-content: center;
            border: 1px solid rgba(255, 215, 0, 0.9);
            position: relative;
            overflow: hidden;
        }
        .big-order-btn:before {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        .big-order-btn:hover:before {
            left: 100%;
        }
        .big-order-btn:hover {
            background: linear-gradient(105deg, #ffa500, #ff6347, #ff2400);
            transform: scale(1.02);
            box-shadow: 0 0 32px #ff6600;
        }

        .price-message {
            background: rgba(0, 0, 0, 0.6);
            border-radius: 1rem;
            margin-top: 0.2rem;
            padding: 0.4rem;
            text-align: center;
            border: 1px solid #ff8c00;
            backdrop-filter: blur(5px);
        }
        .price-text {
            font-size: 0.7rem;
            font-weight: bold;
            color: #ffd700;
            background: rgba(255, 69, 0, 0.2);
            display: inline-block;
            padding: 0.2rem 0.8rem;
            border-radius: 1.5rem;
            letter-spacing: 0.3px;
        }
        
        footer {
            text-align: center;
            margin-top: 0.5rem;
            font-size: 0.6rem;
            color: #ccaa77;
            border-top: 1px solid rgba(255, 140, 0, 0.4);
            padding-top: 0.5rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.4rem;
            flex-shrink: 0;
        }
        .footer-warning {
            background: rgba(255, 69, 0, 0.15);
            padding: 0.25rem 0.8rem;
            border-radius: 1.2rem;
            font-size: 0.6rem;
            color: #ffc89c;
            display: inline-flex;
            align-items: center;
            gap: 5px;
            direction: rtl;
            backdrop-filter: blur(4px);
        }
        .footer-warning i {
            font-size: 0.55rem;
            color: #ff7b4a;
        }
        .footer-mahsa-link {
            color: #ffaa88;
            text-decoration: none;
            font-weight: bold;
            border-bottom: 1px dashed #ffaa88;
            font-size: 0.6rem;
        }
        .instagram-link {
            display: inline-flex;
            align-items: center;
            gap: 5px;
            background: linear-gradient(45deg, #f09433, #d62976, #962fbf);
            padding: 0.2rem 0.8rem;
            border-radius: 1.5rem;
            color: white;
            text-decoration: none;
            font-weight: bold;
            font-size: 0.65rem;
            box-shadow: 0 2px 6px rgba(0,0,0,0.3);
        }
        
        .toast-message {
            position: fixed;
            bottom: 60px;
            left: 50%;
            transform: translateX(-50%) scale(0.9);
            background: #1f1a0cdd;
            backdrop-filter: blur(16px);
            border-radius: 50px;
            padding: 8px 16px;
            color: #ffd700;
            font-size: 0.7rem;
            border: 1px solid #ffb347;
            z-index: 11000;
            text-align: center;
            white-space: nowrap;
            font-weight: bold;
            pointer-events: none;
            opacity: 0;
            transition: 0.2s;
        }
        
        @media (max-height: 700px) {
            .step p { font-size: 0.5rem; }
            .step h4 { font-size: 0.65rem; }
            .hero h1 { font-size: 1.6rem; }
            .big-order-btn { padding: 0.6rem 1.3rem; font-size: 1rem; }
            .how-it-works { padding: 0.6rem; }
        }
        
        /* اسکرول در پنجره اصلی مجاز است ولی بدنه اصلی قفل */
        .window-main::-webkit-scrollbar {
            width: 5px;
        }
        .window-main::-webkit-scrollbar-track {
            background: #1f1a10;
            border-radius: 10px;
        }
        .window-main::-webkit-scrollbar-thumb {
            background: #ff8c00;
            border-radius: 10px;
        }
    </style>
</head>
<body>

<!-- 
    ساختار سه لایه‌ای:
    1. بدنه body (پس زمینه خالی) -> هرگز دیده نمی‌شه چون دو پنجره تمام صفحه داریم.
    2. پنجره اول: window-splash (اسپلش) -> بعد 3 ثانیه بسته می‌شه و از DOM حذف می‌گردد.
    3. پنجره دوم: window-main (محتوای اصلی) -> تمام صفحه، همیشه باز و هرگز بسته نمی‌شه، محتوای اصلی داخل آن قرار دارد.
-->

<!-- پنجره شماره 1: اسپلش اسکرین (اولین نمایش، بعد ۳ ثانیه بسته می‌شه) -->
<div id="windowSplash" class="window-splash">
    <div class="splash-content">
        <i class="fas fa-crown"></i>
        <h2>XRO</h2>
        <p>در حال آماده‌سازی رویداد...</p>
    </div>
</div>

<!-- پنجره شماره 2: پنجره اصلی (تمام صفحه، هرگز بسته نمی‌شود و محتوای صفحه اصلی در آن قرار دارد) -->
<div id="windowMain" class="window-main">
    <!-- نوار درصد خط خطی در پایین پنجره -->
    <div class="percentage-bg">
        <div class="percentage-fill" id="percentFill"></div>
    </div>
    <div class="percentage-number" id="percentValue">0%</div>

    <div class="main-content">
        <div class="hero">
            <h1><i class="fas fa-crown"></i> رویداد ایکسرو</h1>
            <div class="badge-event"><i class="fas fa-calendar-alt"></i> رویداد رندوم باکس تا 17 تیر به اتمام می‌رسد</div>
        </div>

        <div class="how-it-works">
            <h3><i class="fas fa-lightbulb"></i> راهنمایی های لازم</h3>
            <div class="steps">
                <div class="step">
                    <i class="fas fa-database"></i>
                    <h4>حجم ثابت</h4>
                    <p>هر خرید دارای 40 گیگ کانفیگ است و متغیر نیست</p>
                </div>
                <div class="step">
                    <i class="fas fa-users-slash"></i>
                    <h4>کاربر محدود</h4>
                    <p>هر کانفیگ برای 3 کاربر قابل استفاده است توجه داشته باشید اگه بیشتر 3 کاربر بشه کانفیگ مسدود میشه</p>
                </div>
                <div class="step">
                    <i class="fas fa-random"></i>
                    <h4>زمان رندوم</h4>
                    <p>شما اطلاع ندارید کی و کجا زمان کانفیگ تموم می‌کنه شاید 3 روز شاید 1 سال با این حال 3 روز اول را خودمان گارانتی می‌کنیم</p>
                </div>
                <div class="step">
                    <i class="fas fa-tachometer-alt"></i>
                    <h4>سرعت ثابت</h4>
                    <p>درصورتی که سرعت اینترنت نسبتا خوبی داشته باشید در 95 درصد مواقع سرعت کانفیگ بین 100 تا 160 می باشد</p>
                </div>
            </div>
            
            <div class="price-message">
                <div class="price-text">
                    <i class="fas fa-ticket-alt"></i> مبلغ ثبت سفارش ۶۳ هزارتومان می‌باشد
                </div>
            </div>
        </div>

        <div class="single-order-btn">
            <button class="big-order-btn" id="directOrderBtn"><i class="fas fa-shopping-cart fa-lg"></i> ثبت سفارش</button>
        </div>

        <footer>
            <div class="footer-warning">
                <i class="fas fa-exclamation-triangle"></i>
                <span>بعد از دریافت کانفیگ حتما باید در برنامه</span>
                <a href="#" id="footerMahsaLink" class="footer-mahsa-link">mahsa NG</a>
                <span>استفاده کنید</span>
            </div>
            <a href="https://instagram.com/amin.xro" target="_blank" class="instagram-link" id="instagramLink">
                <i class="fab fa-instagram"></i> @amin.xro
            </a>
        </footer>
    </div>
</div>

<script>
    // ======================= سه لایه ای و مدیریت پنجره ها =======================
    // پنجره اول (اسپلش): بعد ۳ ثانیه با افکت بسته می‌شه و از DOM حذف میگرده
    const splashWindow = document.getElementById('windowSplash');
    const mainWindow = document.getElementById('windowMain');
    
    // اطمینان از اینکه پنجره اصلی در ابتدا مخفی است (opacity:0) ولی نمایش داده نمیشه تا اسپلش بسته بشه
    mainWindow.style.opacity = '0';
    mainWindow.style.visibility = 'visible';
    
    // بعد از ۳ ثانیه اسپلش رو ببند و پنجره اصلی رو با انیمیشن نمایش بده
    setTimeout(() => {
        if(splashWindow) {
            splashWindow.style.opacity = '0';
            splashWindow.style.visibility = 'hidden';
            // بعد از اتمام انیمیشن، اسپلش رو از DOM حذف می‌کنیم (پنجره اول کاملاً بسته میشه)
            setTimeout(() => {
                if(splashWindow && splashWindow.parentNode) {
                    splashWindow.parentNode.removeChild(splashWindow);
                }
            }, 600);
        }
        // نمایش پنجره اصلی با افکت محو و اسلاید ملایم
        mainWindow.style.transition = 'opacity 0.7s cubic-bezier(0.2, 0.9, 0.4, 1.1)';
        mainWindow.style.opacity = '1';
        
        // همچنین یک تریگر برای اطمینان از اسکرول صحیح (پنجره اصلی قابل اسکرول هست)
        document.body.style.overflow = 'hidden'; // بدنه اصلی قفل هست اما پنجره اصلی اسکرول میخوره
    }, 3000);
    
    // ======================= انیمیشن درصد (نوار خط خطی پایین پنجره اصلی) =======================
    let percent = 0;
    const percentFill = document.getElementById('percentFill');
    const percentValueSpan = document.getElementById('percentValue');
    
    function animatePercentage() {
        if(percent <= 100) {
            percentFill.style.width = percent + '%';
            percentValueSpan.innerText = percent + '%';
            percent++;
            setTimeout(animatePercentage, 45); // پر شدن حدود 4.5 ثانیه
        } else {
            // پس از پر شدن کامل، نوار پر نگه داشته میشود
            if(percentValueSpan) percentValueSpan.style.color = "#ffaa44";
        }
    }
    
    // انیمیشن درصد همزمان با بارگذاری صفحه شروع میشه
    animatePercentage();
    
    // ======================= توابع ارتباط با تلگرام و دکمه‌ها =======================
    function sendOrderToTelegram() {
        const message = "سلام درخواست خرید کانفیگ رویدادی را دارم :)";
        const telegramUsername = "u0v0n";
        const encodedMsg = encodeURIComponent(message);
        const tgUrl = `https://t.me/${telegramUsername}?text=${encodedMsg}`;
        
        showToastMessage("🔄 در حال انتقال به تلگرام...");
        
        setTimeout(() => {
            window.open(tgUrl, '_blank');
            setTimeout(() => {
                showToastMessage("✅ پیام شما به @u0v0n ارسال شد");
            }, 600);
        }, 150);
    }
    
    function showToastMessage(message) {
        let existingToast = document.querySelector('.toast-message');
        if(existingToast) existingToast.remove();
        
        const toast = document.createElement('div');
        toast.className = 'toast-message';
        toast.innerText = message;
        document.body.appendChild(toast);
        
        setTimeout(() => {
            toast.style.opacity = '1';
            toast.style.transform = 'translateX(-50%) scale(1)';
        }, 10);
        
        setTimeout(() => {
            toast.style.opacity = '0';
            toast.style.transform = 'translateX(-50%) scale(0.8)';
            setTimeout(() => {
                if(toast && toast.remove) toast.remove();
            }, 300);
        }, 2500);
    }
    
    const orderBtn = document.getElementById('directOrderBtn');
    if(orderBtn) {
        orderBtn.addEventListener('click', (e) => {
            e.preventDefault();
            sendOrderToTelegram();
        });
    }
    
    const instaLink = document.getElementById('instagramLink');
    if(instaLink) {
        instaLink.setAttribute('href', 'https://instagram.com/amin.xro');
        instaLink.setAttribute('target', '_blank');
        instaLink.setAttribute('rel', 'noopener noreferrer');
    }
    
    function openMahsaStore() {
        window.open('https://play.google.com/store/apps/details?id=com.MahsaNet.MahsaNG', '_blank');
    }
    
    const footerMahsaLink = document.getElementById('footerMahsaLink');
    if(footerMahsaLink) {
        footerMahsaLink.addEventListener('click', function(e) {
            e.preventDefault();
            openMahsaStore();
        });
    }
    
    // جلوگیری از اسکرول در بدنه اصلی (بدنه body قفل میمونه)، اما درون پنجره اصلی اسکرول آزاد است
    // این کار باعث میشه حس پنجره دوم تمام صفحه حفظ بشه و صفحه اصلی (body خالی) هرگز دیده نشه
    window.addEventListener('touchmove', function(e) {
        // اگر المان هدف داخل پنجره اصلی باشه و نیاز به اسکرول داشته باشه، اجازه بده
        const targetEl = e.target;
        const isInsideMainWindow = mainWindow.contains(targetEl);
        if(isInsideMainWindow) {
            // اجازه اسکرول طبیعی در پنجره اصلی داده میشه (چون پنجره اصلی overflow-y:auto داره)
            return;
        }
        // در غیر اینصورت (لمس روی body یا فضای خالی) جلوگیری کن
        e.preventDefault();
    }, { passive: false });
    
    // برای رویداد wheel نیز به همین صورت: اگر داخل پنجره اصلی باشد، اجازه اسکرول بده
    window.addEventListener('wheel', function(e) {
        const isInsideMainWindow = mainWindow.contains(e.target);
        if(isInsideMainWindow) {
            return; // اسکرول در پنجره اصلی مجاز است
        }
        e.preventDefault();
    }, { passive: false });
    
    // افکت فشردن دکمه ثبت سفارش
    const btn = document.querySelector('.big-order-btn');
    if(btn) {
        btn.addEventListener('mousedown', () => {
            btn.style.transform = 'scale(0.98)';
        });
        btn.addEventListener('mouseup', () => {
            btn.style.transform = 'scale(1.02)';
        });
        btn.addEventListener('mouseleave', () => {
            btn.style.transform = 'scale(1)';
        });
    }
    
    // همچنین به صورت پیشگیرانه مطمئن میشیم که بدنه body هیچ محتوایی نداره و پنجره اصلی کامل نمایش داده بشه
    // به مرور اگر اسپلش حذف شد، پنجره اصلی تنها لایه قابل مشاهده است و هیچ وقت بسته نمیشه.
    console.log("ساختار سه لایه‌ای: پنجره اول (اسپلش) بعد 3 ثانیه بسته میشود، پنجره دوم (اصلی) تمام صفحه باقی میماند و صفحه اصلی(body) هرگز نمایش نمیابد.");
    
    // اطمینان از اینکه صفحه اصلی خالی هیچ گاه دیده نمی شود: body پس زمینه سیاه و پنجره اصلی تمام ابعاد را پوشانده
    // در صورت تغییر سایز ویوپورت، پنجره اصلی همچنان full-screen باقی میماند (از قبل fixed هست)
</script>
</body>
</html>
