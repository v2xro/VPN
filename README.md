<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>رویداد ایکسرو | رندم باکس | سرویس کلود</title>
    <!-- Font Awesome 6 (Free) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* ----- RESET & BASE - لایه سوم: صفحه اصلی خالی ----- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
            -webkit-user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        
        /* لایه سوم (body) - کاملاً خالی، فقط پس‌زمینه سیاه، هیچ محتوایی نمایش داده نمی‌شه */
        html, body {
            width: 100%;
            height: 100%;
            overflow: hidden;
            position: fixed;
            top: 0;
            left: 0;
            background: #000000;
        }
        
        body {
            background: #000000;
            font-family: 'Segoe UI', 'Vazir', 'Impact', system-ui, sans-serif;
        }
        
        /* جلوگیری از کپی و منوی راست کلیک */
        body {
            -webkit-touch-callout: none;
            -webkit-user-select: none;
            -khtml-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }
        
        /* ===== لایه اول: پنجره اسپلش (Splash Window) که بعد از 100% بسته می‌شه ===== */
        .window-splash {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, #3e1a1a, #0b0303);
            z-index: 10000;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            backdrop-filter: blur(6px);
            transition: opacity 0.6s ease, visibility 0s linear 0.6s;
            opacity: 1;
            visibility: visible;
            border: none;
            box-shadow: 0 0 80px rgba(255,0,0,0.2);
        }
        
        /* نوار درصد ساده و ممتد */
        .splash-percentage-container {
            position: absolute;
            bottom: 60px;
            left: 40px;
            right: 40px;
            background: rgba(0, 0, 0, 0.7);
            border-radius: 40px;
            padding: 4px;
            backdrop-filter: blur(10px);
            border: 1px solid #cc5533;
            direction: ltr;
        }
        .splash-percentage-bg {
            width: 100%;
            height: 8px;
            background: #2a1515;
            border-radius: 30px;
            overflow: hidden;
        }
        .splash-percentage-fill {
            width: 0%;
            height: 100%;
            background: linear-gradient(90deg, #ffcc66, #ff5533, #cc2200);
            border-radius: 30px;
            transition: width 0.04s linear;
            box-shadow: 0 0 12px #ff4422;
        }
        
        .splash-content {
            text-align: center;
            transform: scale(0.98);
            animation: splashPulse 1.5s infinite alternate;
            background: rgba(0,0,0,0.55);
            padding: 28px 48px;
            border-radius: 80px;
            backdrop-filter: blur(24px);
            border: 2px solid #ffcc44;
            box-shadow: 0 0 55px rgba(255,50,0,0.5);
        }
        .splash-content i {
            font-size: 6rem;
            background: linear-gradient(135deg, #ffdd88, #ff5533, #cc3311);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            filter: drop-shadow(0 0 25px #ff4400);
            margin-bottom: 0.8rem;
        }
        .splash-content h2 {
            font-size: 3rem;
            font-weight: 900;
            letter-spacing: 8px;
            background: linear-gradient(135deg, #ffd700, #ff5533);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 15px rgba(255,40,0,0.7);
        }
        .splash-content p {
            margin-top: 12px;
            font-size: 0.95rem;
            color: #ffcc99;
            font-weight: bold;
            letter-spacing: 1px;
        }
        
        @keyframes splashPulse {
            0% { transform: scale(0.96); filter: brightness(1); box-shadow: 0 0 20px rgba(255,50,0,0.3);}
            100% { transform: scale(1.04); filter: brightness(1.12); box-shadow: 0 0 50px rgba(255,50,0,0.7);}
        }
        
        /* ===== لایه دوم: پنجره اصلی (همیشه باز، هرگز بسته نمی‌شه) ===== */
        .window-main {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 30% 20%, #1c0a0a, #030101);
            z-index: 9999;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 1rem;
            opacity: 0;
            transition: opacity 0.8s cubic-bezier(0.3, 1, 0.5, 1);
            visibility: visible;
            box-shadow: inset 0 0 100px rgba(0,0,0,0.5);
        }
        
        /* کانتینر محتوای اصلی - قابل اسکرول داخلی */
        .main-content {
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
            height: auto;
            max-height: 95vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            z-index: 12;
            backdrop-filter: blur(2px);
            overflow-y: auto;
            overflow-x: hidden;
            padding: 0.5rem;
            scrollbar-width: thin;
        }
        
        .main-content::-webkit-scrollbar {
            width: 4px;
        }
        .main-content::-webkit-scrollbar-track {
            background: #2a1515;
            border-radius: 10px;
        }
        .main-content::-webkit-scrollbar-thumb {
            background: #ff6633;
            border-radius: 10px;
        }
        
        /* هدر بدون خطوط اضافی */
        .hero {
            text-align: center;
            margin-bottom: 1.2rem;
            animation: fadeInUp 0.8s ease;
            background: linear-gradient(145deg, #2c0e0e, #110303);
            padding: 1rem;
            border-radius: 60px;
            border: 2px solid #e2b13b;
            box-shadow: 0 12px 28px rgba(0,0,0,0.6), inset 0 1px 0 rgba(255,215,0,0.25);
        }
        .hero h1 {
            font-size: 2rem;
            font-weight: 900;
            background: linear-gradient(135deg, #ffdd77, #ff7722, #ff3311);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 2px;
            text-shadow: 0 0 8px rgba(255,68,0,0.4);
        }
        .hero h1 i {
            margin-left: 8px;
            color: #ffaa44;
        }
        
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(25px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .badge-event {
            background: #2a0c0c;
            display: inline-block;
            padding: 0.4rem 1.3rem;
            border-radius: 40px;
            font-size: 0.75rem;
            margin-top: 0.7rem;
            border: 1px solid #ffbb33;
            color: #ffbb77;
            font-weight: bold;
            font-family: monospace;
            backdrop-filter: blur(4px);
        }
        
        /* کارت اطلاعاتی */
        .how-it-works {
            background: rgba(10, 5, 5, 0.85);
            backdrop-filter: blur(14px);
            border-radius: 1.8rem;
            padding: 1.2rem;
            margin-bottom: 1.2rem;
            border: 1px solid #d4af37;
            box-shadow: 0 20px 35px -12px black, 0 0 18px rgba(220, 60, 50, 0.4);
        }
        
        .how-it-works h3 {
            font-size: 1.1rem;
            text-align: center;
            margin-bottom: 0.8rem;
            color: #ffcc66;
            letter-spacing: 1px;
            font-weight: bold;
        }
        
        .steps {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
            margin-top: 0.6rem;
        }
        
        .step {
            background: #1c0f0fe0;
            backdrop-filter: blur(8px);
            padding: 0.8rem 0.3rem;
            border-radius: 1.5rem;
            border: 1px solid #bd7a2e;
            text-align: center;
            transition: all 0.3s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            box-shadow: 0 5px 12px black;
        }
        .step:hover {
            transform: translateY(-5px);
            border-color: #ffcc44;
            background: #3a1818cc;
            box-shadow: 0 8px 22px rgba(255,80,0,0.4);
        }
        .step i {
            font-size: 1.4rem;
            color: #ffbb55;
            text-shadow: 0 0 6px red;
        }
        .step h4 {
            font-size: 0.8rem;
            margin: 0.4rem 0;
            font-weight: bold;
            color: #ffb347;
        }
        .step p {
            font-size: 0.6rem;
            color: #f0cf9c;
            line-height: 1.35;
            padding: 0 0.2rem;
        }
        
        .price-message {
            background: #1c0606aa;
            border-radius: 2rem;
            margin-top: 0.7rem;
            padding: 0.6rem;
            text-align: center;
            border: 1px solid #ffaa33;
            backdrop-filter: blur(8px);
        }
        .price-text {
            font-size: 0.8rem;
            font-weight: bold;
            color: #ffd966;
            background: #2a0c0c99;
            display: inline-block;
            padding: 0.3rem 1.4rem;
            border-radius: 3rem;
        }
        
        .single-order-btn {
            display: flex;
            justify-content: center;
            margin: 0.4rem 0 1rem;
        }
        .big-order-btn {
            background: linear-gradient(115deg, #9b2f1f, #c43a1a, #631005);
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 3rem;
            font-weight: bold;
            font-size: 1.1rem;
            color: #fff0c0;
            cursor: pointer;
            transition: 0.25s;
            display: flex;
            align-items: center;
            gap: 12px;
            box-shadow: 0 0 28px #ff3300;
            width: 90%;
            max-width: 340px;
            justify-content: center;
            border: 2px solid #ffcf4a;
            position: relative;
            overflow: hidden;
        }
        .big-order-btn:before {
            content: "☭";
            font-size: 1.3rem;
            position: absolute;
            left: -30px;
            transition: 0.4s;
            opacity: 0;
        }
        .big-order-btn:hover:before {
            left: 15px;
            opacity: 1;
        }
        .big-order-btn:hover {
            background: linear-gradient(115deg, #b33a22, #e34d28, #7a1a0a);
            transform: scale(1.02);
            box-shadow: 0 0 38px #ff4411;
        }
        
        footer {
            text-align: center;
            margin-top: 0.6rem;
            font-size: 0.65rem;
            color: #ccaa77;
            border-top: 1px solid #ab5f2f;
            padding-top: 0.8rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
        }
        .footer-warning {
            background: #2d1313b3;
            padding: 0.3rem 1rem;
            border-radius: 2rem;
            font-size: 0.65rem;
            color: #ffcd94;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            backdrop-filter: blur(12px);
            border: 1px solid #e09d32;
        }
        .instagram-link {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            background: #2c1a1a;
            padding: 0.3rem 1rem;
            border-radius: 2rem;
            color: #ffdd99;
            text-decoration: none;
            font-weight: bold;
            font-size: 0.7rem;
            border: 1px solid #ff9933;
            transition: 0.2s;
        }
        .instagram-link:hover {
            background: #4a2525;
            transform: scale(1.02);
        }
        
        .toast-message {
            position: fixed;
            bottom: 70px;
            left: 50%;
            transform: translateX(-50%) scale(0.9);
            background: #2a0c0c;
            backdrop-filter: blur(20px);
            border-radius: 50px;
            padding: 8px 20px;
            color: #ffcc77;
            font-size: 0.75rem;
            border: 1px solid #ff9933;
            z-index: 11000;
            white-space: nowrap;
            font-weight: bold;
            opacity: 0;
            transition: 0.2s;
            font-family: monospace;
        }
    </style>
</head>
<body>

<!-- لایه اول: پنجره اسپلش (Splash) که بعد از 100% بسته میشه -->
<div id="windowSplash" class="window-splash">
    <div class="splash-content">
        <i class="fas fa-cloud-upload-alt"></i>
        <h2>XRO ☭</h2>
        <p style="font-size:1rem; font-weight:900;">نشر سرویس کلود</p>
        <p style="margin-top: 8px;">با تشکر از اپ مهسا</p>
    </div>
    <div class="splash-percentage-container">
        <div class="splash-percentage-bg">
            <div class="splash-percentage-fill" id="splashPercentFill"></div>
        </div>
    </div>
</div>

<!-- لایه دوم: پنجره اصلی (همیشه باز، هرگز بسته نمیشه) -->
<div id="windowMain" class="window-main">
    <div class="main-content">
        <div class="hero">
            <h1><i class="fas fa-crown"></i> رویداد ایکسرو</h1>
            <div class="badge-event"><i class="fas fa-calendar-alt"></i> رویداد رندوم باکس تا ۲۵ تیر پا برجا است</div>
        </div>

        <div class="how-it-works">
            <h3><i class="fas fa-question-circle"></i> چرا کانفیگ ما؟</h3>
            <div class="steps">
                <div class="step">
                    <i class="fas fa-infinity"></i>
                    <h4>حجم نامحدود</h4>
                    <p>هر خرید دارای یک کانفیگ با حجم نامحدود است</p>
                </div>
                <div class="step">
                    <i class="fas fa-users"></i>
                    <h4>کاربر نامحدود</h4>
                    <p>هر کانفیگ برای نامحدود کاربر قابل استفاده است (هرچه تعداد اتصال بیشتر باشد، سرعت کندتر می‌شود)</p>
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
                    <i class="fas fa-ticket-alt"></i> مبلغ ثبت سفارش ۷۴ هزارتومان می‌باشد
                </div>
            </div>
        </div>

        <div class="single-order-btn">
            <button class="big-order-btn" id="directOrderBtn"><i class="fas fa-pen-alt"></i> ثبت درخواست</button>
        </div>

        <footer>
            <div class="footer-warning">
                <i class="fas fa-exclamation-triangle"></i>
                <span>بعد از دریافت کانفیگ حتما باید در برنامه</span>
                <a href="#" id="footerMahsaLink" style="color:#ffaa88; text-decoration:none; font-weight:bold;">mahsa NG</a>
                <span>استفاده کنید</span>
            </div>
            <a href="https://instagram.com/amin.xro" target="_blank" class="instagram-link" id="instagramLink">
                <i class="fab fa-instagram"></i> @amin.xro
            </a>
        </footer>
    </div>
</div>

<script>
    // ========== مدیریت سه لایه ==========
    const splashWindow = document.getElementById('windowSplash');
    const mainWindow = document.getElementById('windowMain');
    const splashFill = document.getElementById('splashPercentFill');
    
    let percent = 0;
    const interval = setInterval(() => {
        if(percent <= 100) {
            if(splashFill) splashFill.style.width = percent + '%';
            percent++;
        } 
        if(percent > 100) {
            clearInterval(interval);
            // بستن لایه اول (پنجره اسپلش)
            if(splashWindow) {
                splashWindow.style.transition = 'opacity 0.6s ease';
                splashWindow.style.opacity = '0';
                setTimeout(() => {
                    if(splashWindow && splashWindow.parentNode) {
                        splashWindow.parentNode.removeChild(splashWindow);
                    }
                    // نمایش لایه دوم (پنجره اصلی)
                    mainWindow.style.opacity = '1';
                }, 600);
            } else {
                mainWindow.style.opacity = '1';
            }
        }
    }, 43); // حدود 4.3 ثانیه تا 100%
    
    // Fallback ایمنی (در صورتی که اینتروال به هر دلیل کامل نشد)
    setTimeout(() => {
        if(splashWindow && splashWindow.parentNode && splashWindow.style.opacity !== '0') {
            clearInterval(interval);
            splashWindow.style.opacity = '0';
            setTimeout(() => {
                if(splashWindow && splashWindow.parentNode) splashWindow.parentNode.removeChild(splashWindow);
                mainWindow.style.opacity = '1';
            }, 500);
        }
    }, 5200);
    
    // ========== توابع کاربردی ==========
    function sendOrderToTelegram() {
        const message = "سلام درخواست خرید کانفیگ (حجم نامحدود) رویداد ایکسرو";
        const telegramUsername = "u0v0n";
        const tgUrl = `https://t.me/${telegramUsername}?text=${encodeURIComponent(message)}`;
        showToastMessage("🔄 ارسال درخواست به تلگرام ...");
        setTimeout(() => {
            window.open(tgUrl, '_blank');
            setTimeout(() => showToastMessage("✅ پیام شما به @u0v0n ارسال شد"), 600);
        }, 150);
    }
    
    function showToastMessage(msg) {
        let existing = document.querySelector('.toast-message');
        if(existing) existing.remove();
        const toast = document.createElement('div');
        toast.className = 'toast-message';
        toast.innerText = msg;
        document.body.appendChild(toast);
        setTimeout(() => { toast.style.opacity = '1'; toast.style.transform = 'translateX(-50%) scale(1)'; }, 10);
        setTimeout(() => {
            toast.style.opacity = '0';
            setTimeout(() => toast.remove(), 300);
        }, 2300);
    }
    
    document.getElementById('directOrderBtn')?.addEventListener('click', (e) => { e.preventDefault(); sendOrderToTelegram(); });
    document.getElementById('instagramLink')?.setAttribute('target', '_blank');
    document.getElementById('footerMahsaLink')?.addEventListener('click', (e) => {
        e.preventDefault();
        window.open('https://play.google.com/store/apps/details?id=com.MahsaNet.MahsaNG', '_blank');
    });
    
    // جلوگیری کامل از کپی، منوی راست کلیک و زوم
    document.addEventListener('contextmenu', (e) => e.preventDefault());
    document.addEventListener('copy', (e) => e.preventDefault());
    document.addEventListener('cut', (e) => e.preventDefault());
    document.addEventListener('paste', (e) => e.preventDefault());
    document.addEventListener('dragstart', (e) => e.preventDefault());
    document.addEventListener('selectstart', (e) => e.preventDefault());
    
    // جلوگیری از اسکرول در صفحه اصلی، اجازه اسکرول فقط داخل main-content
    window.addEventListener('touchmove', (e) => { if(!e.target.closest('.main-content')) e.preventDefault(); }, { passive: false });
    window.addEventListener('wheel', (e) => { if(!e.target.closest('.main-content')) e.preventDefault(); }, { passive: false });
    
    // افکت دکمه ثبت درخواست
    const btn = document.querySelector('.big-order-btn');
    if(btn) {
        btn.addEventListener('mousedown', () => btn.style.transform = 'scale(0.97)');
        btn.addEventListener('mouseup', () => btn.style.transform = 'scale(1.02)');
        btn.addEventListener('mouseleave', () => btn.style.transform = 'scale(1)');
    }
    
    console.log("ساختار سه لایه: لایه اول (اسپلش) بسته شد، لایه دوم (محتوای اصلی) نمایش داده شد، لایه سوم (body) خالی می‌ماند.");
</script>
</body>
</html>
