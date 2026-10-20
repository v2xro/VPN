<html lang="en-US" dir="rtl"><head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">

<title>xroVPN | آقای ایکسرو</title>
<meta name="generator" content="Jekyll v3.10.0">
<meta name="description" content="آقای ایکسرو">
<link rel="canonical" href="https://xrovpn.github.io/xroVPN/">

    <style>
        :root {
            --primary-color: #000000;
            --primary-dark: #1a1a1a;
            --primary-light: #333333;
            --success-color: #000000;
            --danger-color: #ff0000;
            --text-color: #000000;
            --text-light: #666666;
            --text-white: #ffffff;
            --bg-color: #ffffff;
            --card-bg: #f5f5f5;
            --card-hover: #e0e0e0;
            --border-color: rgba(0,0,0,0.3);
            --shadow-color: rgba(0,0,0,0.1);
            --transition: all .3s cubic-bezier(.4,0,.2,1);
            --glow-effect: 0 0 15px rgba(0,0,0,0.4), 0 0 30px rgba(0,0,0,0.2);
            --bg-line1: #e0e0e0;
            --z-index-modal: 1000;
            --z-index-overlay: 999;
            --z-index-notification: 10000;
            --z-index-loading: 100000;
            --notebook-lines: repeating-linear-gradient(0deg, transparent, transparent 49px, var(--bg-line1) 49px, var(--bg-line1) 50px);
        }

        .loading-overlay {
            position: fixed;
            inset: 0;
            z-index: var(--z-index-loading);
            background: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            margin: 0;
            padding: 0;
            overflow: hidden;
            font-family: Tahoma, Arial, sans-serif;
            opacity: 0;
            visibility: hidden;
            transition: all 0.5s ease;
        }

        .loading-overlay.show { opacity: 1; visibility: visible; }
        .loading-overlay.fade-out { opacity: 0; visibility: hidden; }

        .notebook {
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(to bottom, transparent, transparent 8.2vw, #e0e0e0 8.4vw);
            background-size: 100% 8.4vw;
            position: absolute;
            top: 0;
            left: 0;
        }

        .loading-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-family: 'Permanent Marker', 'Comic Sans MS', 'Arial', sans-serif;
            font-size: 20vw;
            font-weight: bold;
            display: flex;
            justify-content: center;
            align-items: center;
            user-select: none;
            text-shadow: 1vw 1vw 2vw rgba(0,0,0,0.3), -0.5vw -0.5vw 1.5vw rgba(255,255,255,0.5);
        }

        .x { color: red; animation: flicker 4s 1; margin-right: 6vw; }
        .ro {
            position: relative;
            color: transparent;
            background: linear-gradient(to bottom, black 40%, rgba(0,0,0,0.7) 60%, transparent 100%);
            -webkit-background-clip: text;
            background-clip: text;
            animation: melt 3s infinite ease-in-out;
        }
        .ro:not(:last-child) { margin-right: 6vw; }

        @keyframes flicker {
            0% { opacity: 1; } 10% { opacity: 0.4; } 25% { opacity: 1; }
            30% { opacity: 0.4; } 35% { opacity: 1; } 50% { opacity: 0.4; } 100% { opacity: 1; }
        }
        @keyframes melt {
            0% { background-position: 0 0; } 50% { background-position: 0 5vw; } 100% { background-position: 0 0; }
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }

        body {
            font-family: 'Vazirmatn', 'Segoe UI', sans-serif;
            background: var(--bg-color) var(--notebook-lines);
            color: var(--text-color);
            height: 100vh;
            overflow: hidden;
            user-select: none;
            position: relative;
            background-size: 100% 51px;
            background-position: top right;
            background-repeat: repeat-y;
        }

        .permanent-window {
            position: fixed;
            inset: 0;
            z-index: 10;
            background: transparent;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            animation: fadeIn 1s ease-out;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 6px 20px;
            background: var(--card-bg);
            border-bottom: 1px solid var(--border-color);
            box-shadow: 0 4px 20px var(--shadow-color);
            z-index: 100;
        }

        .logo {
            font-size: 1.3rem;
            font-weight: 700;
            padding: 12px 18px;
            border-radius: 12px;
            cursor: pointer;
            background: var(--card-bg);
            display: flex;
            align-items: center;
            gap: 12px;
            transition: var(--transition);
            border: 3px solid #000000;
            box-shadow: var(--glow-effect);
            color: var(--text-color);
        }

        .logo:hover {
            background: var(--card-hover);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 8px 25px var(--shadow-color);
        }

        .content {
            height: calc(100vh - 50px);
            display: flex;
            flex-direction: column;
            padding: 10px;
            overflow-y: auto;
        }

        .welcome-container {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px 10px;
        }

        /* متن قراردادی */
        .contract-container {
            width: 100%;
            max-width: 560px;
            background: var(--card-bg);
            border: 2px solid var(--primary-color);
            border-radius: 18px;
            padding: 24px 22px;
            box-shadow: var(--glow-effect);
            display: flex;
            flex-direction: column;
            gap: 18px;
            animation: slideUp 0.7s ease-out;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .contract-title {
            font-size: 1.15rem;
            font-weight: 700;
            text-align: center;
            padding-bottom: 14px;
            border-bottom: 2px dashed var(--border-color);
            color: var(--text-color);
        }

        .contract-title i { color: var(--primary-color); margin-left: 6px; }

        .contract-body {
            font-size: 1rem;
            line-height: 2.1;
            color: var(--text-color);
            text-align: right;
        }

        .contract-line {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 6px;
            margin-bottom: 4px;
        }

        .contract-line.final {
            margin-top: 8px;
            padding-top: 12px;
            border-top: 1px dashed var(--border-color);
            line-height: 1.9;
        }

        .contract-input {
            flex: 1;
            min-width: 110px;
            border: none;
            border-bottom: 2px dotted var(--primary-color);
            background: transparent;
            font-family: 'Vazirmatn', sans-serif;
            font-size: 0.95rem;
            font-weight: 600;
            color: var(--primary-color);
            padding: 4px 6px;
            outline: none;
            text-align: center;
            transition: var(--transition);
        }

        .contract-input:focus {
            border-bottom-color: #ff0000;
            background: rgba(0,0,0,0.03);
        }

        .contract-input::placeholder {
            color: #999;
            font-weight: 400;
            font-size: 0.85rem;
        }

        /* دراپ‌داون انتخاب نوع اعتبار */
        .credit-selector {
            position: relative;
            display: inline-flex;
            flex: 1;
            min-width: 130px;
        }

        .credit-select-btn {
            width: 100%;
            padding: 6px 12px;
            border: none;
            border-bottom: 2px dotted var(--primary-color);
            background: transparent;
            font-family: 'Vazirmatn', sans-serif;
            font-size: 0.95rem;
            font-weight: 700;
            color: var(--primary-color);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 8px;
            transition: var(--transition);
        }

        .credit-select-btn:hover { background: rgba(0,0,0,0.04); }

        .credit-select-btn .placeholder {
            color: #999;
            font-weight: 400;
            font-size: 0.85rem;
        }

        .credit-select-btn i { font-size: 0.8rem; transition: var(--transition); }
        .credit-select-btn.open i { transform: rotate(180deg); }

        .credit-dropdown {
            position: absolute;
            top: calc(100% + 8px);
            right: 0;
            left: 0;
            background: #ffffff;
            border: 2px solid var(--primary-color);
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.25);
            z-index: 50;
            overflow: hidden;
            max-height: 0;
            opacity: 0;
            transition: all 0.25s ease;
            pointer-events: none;
        }

        .credit-dropdown.open {
            max-height: 300px;
            opacity: 1;
            pointer-events: auto;
        }

        .credit-option {
            padding: 12px 16px;
            font-size: 0.95rem;
            font-weight: 600;
            color: var(--text-color);
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: var(--transition);
            border-bottom: 1px solid rgba(0,0,0,0.06);
        }

        .credit-option:last-child { border-bottom: none; }
        .credit-option:hover { background: #000000; color: #ffffff; }
        .credit-option i { font-size: 0.9rem; width: 18px; }

        /* چک‌باکس تعهد */
        .commitment-row {
            display: flex;
            align-items: flex-start;
            gap: 10px;
            margin-top: 10px;
            padding-top: 12px;
            border-top: 1px dashed var(--border-color);
        }

        .commitment-checkbox {
            appearance: none;
            -webkit-appearance: none;
            width: 22px;
            height: 22px;
            min-width: 22px;
            border: 2px solid var(--primary-color);
            border-radius: 6px;
            cursor: pointer;
            position: relative;
            transition: var(--transition);
            margin-top: 2px;
            background: #ffffff;
        }

        .commitment-checkbox:checked { background: #000000; border-color: #000000; }

        .commitment-checkbox:checked::after {
            content: '\f00c';
            font-family: 'Font Awesome 6 Free';
            font-weight: 900;
            color: #ffffff;
            font-size: 0.75rem;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        .commitment-checkbox:hover {
            transform: scale(1.1);
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }

        .commitment-label {
            font-size: 0.95rem;
            line-height: 1.8;
            color: var(--text-color);
            cursor: pointer;
            flex: 1;
        }

        /* دکمه ارسال */
        .submit-contract-btn {
            margin-top: 8px;
            padding: 16px;
            border-radius: 14px;
            background: linear-gradient(135deg, #000000, #1a1a1a);
            color: var(--text-white);
            font-family: 'Vazirmatn', sans-serif;
            font-size: 1.05rem;
            font-weight: 700;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            transition: var(--transition);
            box-shadow: 0 6px 20px var(--shadow-color);
        }

        .submit-contract-btn i { font-size: 1.15rem; }

        .submit-contract-btn:hover {
            background: linear-gradient(135deg, #1a1a1a, #000000);
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 12px 30px var(--shadow-color), 0 0 20px rgba(0,0,0,0.3);
        }

        .submit-contract-btn:hover i { transform: rotate(15deg) scale(1.1); }
        .submit-contract-btn:active { transform: translateY(0) scale(0.99); }
        .submit-contract-btn:disabled { opacity: 0.6; cursor: not-allowed; transform: none; }

        /* دکمه راهنما */
        .floating-btn {
            position: fixed;
            bottom: 28px;
            left: 15px;
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            border-radius: 18px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 26px;
            color: var(--text-white);
            box-shadow: 0 10px 30px var(--shadow-color);
            cursor: pointer;
            border: none;
            transition: var(--transition);
            z-index: 100;
            animation: gentleFloat 6s ease-in-out infinite;
        }

        .floating-btn::after {
            content: '';
            position: absolute;
            bottom: -13px;
            left: 50%;
            transform: translateX(-50%);
            width: 35px;
            height: 4px;
            background: linear-gradient(90deg, #666, #333);
            border-radius: 2px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.4);
            transition: all 0.3s ease;
        }

        .floating-btn i { font-size: 1.6rem; transition: var(--transition); }

        .floating-btn:hover {
            box-shadow: 0 15px 40px var(--shadow-color);
            background: linear-gradient(135deg, var(--primary-dark), var(--primary-color));
            animation-play-state: paused;
        }

        .floating-btn:hover i { transform: rotate(360deg); }

        @keyframes gentleFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }

        @media (max-width: 480px) {
            .floating-btn { width: 65px; height: 65px; bottom: 25px; }
            .floating-btn i { font-size: 1.4rem; }
        }

        /* Overlay و مودال‌ها */
        .modal-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.7);
            z-index: var(--z-index-overlay);
            display: none;
            transition: opacity .3s ease;
        }

        .modal-overlay.show { display: block; opacity: 1; }
        .modal-overlay.hidden { opacity: 0; }

        .modal-window {
            position: fixed;
            background: var(--card-bg);
            z-index: var(--z-index-modal);
            transition: var(--transition);
            box-shadow: 0 12px 40px var(--shadow-color);
            border: 1px solid var(--border-color);
            border-radius: 18px;
            display: flex;
            flex-direction: column;
            max-height: 80vh;
            overflow: hidden;
        }

        .guide-panel {
            bottom: -100%;
            left: 0;
            width: 100%;
            max-height: 70%;
            border-radius: 18px 18px 0 0;
            transition: bottom .3s ease;
        }
        .guide-panel.open { bottom: 0; }

        .report-problem-menu {
            top: -100%;
            right: 0;
            width: 100%;
            max-height: 65%;
            border-radius: 0 0 18px 18px;
            transition: top .3s ease;
        }
        .report-problem-menu.open { top: 0; }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 20px;
            border-bottom: 1px solid var(--border-color);
            background: var(--card-bg);
            box-shadow: 0 4px 15px var(--shadow-color);
        }

        .modal-title { font-weight: 700; font-size: 1.3rem; color: var(--text-color); }

        .home-btn {
            cursor: pointer;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            transition: var(--transition);
            background: var(--card-bg);
            border: 1px solid var(--border-color);
        }

        .home-btn:hover {
            background: var(--card-hover);
            transform: scale(1.1);
            box-shadow: 0 6px 20px var(--shadow-color);
        }

        .home-btn i { font-size: 1.4rem; transition: var(--transition); }
        .home-btn:hover i { transform: scale(1.2); }

        .modal-content {
            display: flex;
            flex-direction: column;
            padding: 12px;
            background: var(--card-bg);
            height: 100%;
        }

        /* ===== محتوای راهنما ===== */
        .guide-content {
            position: relative;
            padding: 20px;
            overflow-y: auto;
            min-height: 300px;
        }

        .guide-view {
            display: flex;
            flex-direction: column;
            gap: 16px;
            transition: opacity .35s ease, transform .35s ease;
        }

        .guide-view.slide-out {
            opacity: 0;
            transform: translateY(-30px);
            pointer-events: none;
            position: absolute;
            inset: 20px;
        }

        .guide-view.slide-in {
            opacity: 0;
            transform: translateY(-30px);
        }

        .guide-view.active {
            opacity: 1;
            transform: translateY(0);
        }

        .guide-item {
            background: var(--bg-color);
            border: 1px solid var(--border-color);
            border-radius: 14px;
            padding: 18px 20px;
            box-shadow: 0 4px 15px var(--shadow-color);
            display: flex;
            align-items: center;
            gap: 16px;
            transition: var(--transition);
            cursor: pointer;
        }

        .guide-item:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px var(--shadow-color);
            background: var(--card-hover);
        }

        .guide-item-number {
            width: 44px;
            height: 44px;
            min-width: 44px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            color: var(--text-white);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            font-weight: 700;
            box-shadow: 0 4px 12px var(--shadow-color);
        }

        .guide-item-text { font-size: 1.05rem; font-weight: 600; color: var(--text-color); flex: 1; }
        .guide-item-icon { font-size: 1.3rem; color: var(--text-light); transition: var(--transition); }
        .guide-item:hover .guide-item-icon { color: var(--text-color); transform: translateX(-5px); }

        /* ===== محتوای جزئیات خرید (۰ تا ۱۰۰) ===== */
        .detail-header {
            display: flex;
            align-items: center;
            gap: 12px;
            padding-bottom: 14px;
            border-bottom: 2px dashed var(--border-color);
            margin-bottom: 6px;
        }

        .detail-back-btn {
            width: 40px;
            height: 40px;
            min-width: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            color: var(--text-white);
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
            box-shadow: 0 4px 12px var(--shadow-color);
        }

        .detail-back-btn i { font-size: 1rem; }
        .detail-back-btn:hover { transform: translateX(4px) scale(1.05); box-shadow: 0 6px 18px var(--shadow-color); }

        .detail-header-title { font-size: 1.05rem; font-weight: 700; color: var(--text-color); flex: 1; }

        .detail-icons-row {
            display: flex;
            justify-content: space-around;
            align-items: flex-start;
            gap: 10px;
            padding: 20px 0 10px;
        }

        .detail-icon-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            flex: 1;
        }

        .detail-icon-circle {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: linear-gradient(135deg, #000000, #1a1a1a);
            color: #ffffff;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.6rem;
            box-shadow: 0 8px 20px rgba(0,0,0,0.25), inset 0 0 10px rgba(255,255,255,0.1);
            transition: var(--transition);
        }

        .detail-icon-item:hover .detail-icon-circle {
            transform: translateY(-5px) scale(1.08);
            box-shadow: 0 12px 28px rgba(0,0,0,0.35), inset 0 0 14px rgba(255,255,255,0.15);
        }

        .detail-icon-label {
            font-size: 0.85rem;
            font-weight: 700;
            color: var(--text-color);
        }

        .detail-description {
            background: rgba(0,0,0,0.05);
            border-radius: 14px;
            padding: 16px 18px;
            font-size: 0.95rem;
            line-height: 1.9;
            color: var(--text-color);
            border-right: 4px solid var(--primary-color);
            margin-top: 8px;
        }

        /* ===== محتوای طریقه پرداخت ===== */
        .payment-card {
            background: linear-gradient(135deg, #000000, #1a1a1a);
            border-radius: 18px;
            padding: 24px 20px;
            color: #ffffff;
            text-align: center;
            box-shadow: 0 12px 30px rgba(0,0,0,0.3);
            margin-bottom: 16px;
            position: relative;
            overflow: hidden;
        }

        .payment-card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -30%;
            width: 200px;
            height: 200px;
            background: rgba(255,255,255,0.05);
            border-radius: 50%;
        }

        .payment-card::after {
            content: '';
            position: absolute;
            bottom: -40%;
            left: -20%;
            width: 150px;
            height: 150px;
            background: rgba(255,255,255,0.04);
            border-radius: 50%;
        }

        .payment-card-icon {
            font-size: 2rem;
            margin-bottom: 12px;
            position: relative;
            z-index: 1;
        }

        .payment-card-label {
            font-size: 0.85rem;
            opacity: 0.8;
            margin-bottom: 8px;
            position: relative;
            z-index: 1;
        }

        .payment-card-number {
            font-size: 1.4rem;
            font-weight: 700;
            letter-spacing: 2px;
            direction: ltr;
            font-family: 'Vazirmatn', monospace;
            position: relative;
            z-index: 1;
            user-select: text;
            cursor: text;
        }

        .payment-info {
            font-size: 0.95rem;
            line-height: 2;
            color: var(--text-color);
            background: rgba(255,0,0,0.06);
            border-right: 4px solid #ff0000;
            border-radius: 12px;
            padding: 14px 16px;
        }

        .payment-info strong { color: #ff0000; }

        /* ===== محتوای احراز هویت ===== */
        .verification-content {
            text-align: center;
            padding: 30px 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 18px;
        }

        .verification-icon {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            background: linear-gradient(135deg, #000000, #1a1a1a);
            color: #ffffff;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.4rem;
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
            animation: gentleFloat 4s ease-in-out infinite;
        }

        .verification-title {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--text-color);
        }

        .verification-text {
            font-size: 0.95rem;
            line-height: 2;
            color: var(--text-light);
            max-width: 340px;
        }

        /* گزارش مشکل */
        .report-problem-content {
            display: flex;
            flex-direction: column;
            gap: 18px;
            padding: 20px;
            height: 100%;
        }

        .report-problem-content textarea {
            width: 100%;
            min-height: 100px;
            padding: 12px;
            border-radius: 10px;
            border: 1px solid var(--border-color);
            background: var(--card-bg);
            color: var(--text-color);
            font-family: 'Vazirmatn', sans-serif;
            font-size: 0.9rem;
            resize: vertical;
            box-shadow: 0 0 10px var(--shadow-color);
            transition: var(--transition);
        }

        .report-problem-content textarea:focus {
            outline: none;
            border-color: var(--primary-light);
            box-shadow: 0 0 12px var(--shadow-color);
        }

        .report-problem-content button {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            color: var(--text-white);
            padding: 14px;
            border-radius: 12px;
            font-weight: 700;
            cursor: pointer;
            border: none;
            transition: var(--transition);
            box-shadow: 0 6px 20px var(--shadow-color);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .report-problem-content button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 10px 25px var(--shadow-color);
        }

        .notification {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: var(--z-index-notification);
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 16px 20px;
            border-radius: 12px;
            background: var(--card-bg);
            color: var(--text-color);
            box-shadow: 0 8px 25px var(--shadow-color);
            transform: translateX(100%);
            opacity: 0;
            transition: var(--transition);
            border: 1px solid var(--border-color);
            min-width: 280px;
            max-width: 90vw;
            word-wrap: break-word;
        }

        .notification.show { transform: translateX(0); opacity: 1; }
        .notification-success { border-left: 4px solid #00aa00; }
        .notification-error { border-left: 4px solid var(--danger-color); }
        .notification-info { border-left: 4px solid var(--primary-color); }

        .notification-icon { font-size: 1.2rem; min-width: 20px; }
        .notification-message { font-weight: 600; flex: 1; }
    </style>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@400;500;700&display=swap">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap" rel="stylesheet">
</head>
<body>

    <!-- صفحه لودینگ -->
    <div class="loading-overlay show" id="loadingOverlay">
        <div class="notebook"></div>
        <div class="loading-text">
            <span class="x">X</span><span class="ro">R</span><span class="ro">O</span>
        </div>
    </div>

    <!-- آهنگ جدید -->
    <audio id="bgMusic" loop preload="auto">
        <source src="https://dl.musicdel.ir/tag/music/1402/08/21/Rauf%20Faik%20-%20kolybelnaya%20Instrumental%20(128).mp3" type="audio/mpeg">
    </audio>
    <audio id="buttonClickSound" preload="auto">
        <source src="https://sedatoseda.com/wp-content/uploads/interface-124464.mp3" type="audio/mpeg">
    </audio>
    <audio id="generalClickSound" preload="auto">
        <source src="https://sedatoseda.com/wp-content/uploads/button-31.mp3" type="audio/mpeg">
    </audio>
    <audio id="errorSound" preload="auto">
        <source src="https://sedatoseda.com/wp-content/uploads/error-warning-login-denied-132113.mp3" type="audio/mpeg">
    </audio>
    <audio id="successSound" preload="auto">
        <source src="https://dl4.fara-download.ir/audio/sound_effect/alarms/check/Twitch%20Follower%20Alert%20Sound%20Effect%20SFX.mp3" type="audio/mpeg">
    </audio>

    <!-- پنجره اصلی -->
    <div class="permanent-window" id="permanentWindow" style="display: none;">
        <div class="top-bar">
            <div class="logo" id="reportProblemBtn" role="button" tabindex="0" aria-label="گزارش مشکل">
                <i class="fas fa-bug" aria-hidden="true"></i>
                <span>گزارش مشکل</span>
            </div>
        </div>
        <div class="content">
            <div class="welcome-container">
                <div class="contract-container">
                    <div class="contract-title">
                        <i class="fas fa-file-contract"></i>
                        قرارداد فروش اعتبار
                    </div>
                    <div class="contract-body">
                        <div class="contract-line">
                            اینجانب جناب آقای/خانوم:
                            <input type="text" class="contract-input" id="contractName" placeholder="نام و نام خانوادگی" aria-label="نام و نام خانوادگی">
                        </div>
                        <div class="contract-line">
                            با شماره:
                            <input type="tel" class="contract-input" id="contractPhone" placeholder="شماره تماس" aria-label="شماره تماس" inputmode="numeric">
                        </div>
                        <div class="contract-line">
                            قصد فروش اعتبار
                            <div class="credit-selector">
                                <button type="button" class="credit-select-btn" id="creditSelectBtn" aria-haspopup="listbox" aria-expanded="false">
                                    <span class="placeholder" id="creditSelectedText">انتخاب کنید</span>
                                    <i class="fas fa-chevron-down" aria-hidden="true"></i>
                                </button>
                                <div class="credit-dropdown" id="creditDropdown" role="listbox" aria-label="نوع اعتبار">
                                    <div class="credit-option" data-value="اوزون" role="option"><i class="fas fa-shopping-bag"></i> اوزون</div>
                                    <div class="credit-option" data-value="اوکالا" role="option"><i class="fas fa-store"></i> اوکالا</div>
                                    <div class="credit-option" data-value="باسلام" role="option"><i class="fas fa-handshake"></i> باسلام</div>
                                    <div class="credit-option" data-value="ترب پی" role="option"><i class="fas fa-motorcycle"></i> ترب پی</div>
                                    <div class="credit-option" data-value="اسنپ پی" role="option"><i class="fas fa-bolt"></i> اسنپ پی</div>
                                </div>
                            </div>
                            خود به مبلغ:
                            <input type="text" class="contract-input" id="contractAmount" placeholder="مبلغ" aria-label="مبلغ اعتبار" inputmode="numeric">
                            را دارم.
                        </div>

                        <div class="commitment-row">
                            <input type="checkbox" class="commitment-checkbox" id="commitmentCheck" aria-label="تعهد پرداخت اقساط">
                            <label class="commitment-label" for="commitmentCheck">
                                همچنین اینجانب متعهد می‌شوم اقساط را در موعد مقرر و بدون مشکل پرداخت نمایم.
                            </label>
                        </div>
                    </div>
                    <button class="submit-contract-btn" id="submitContractBtn" role="button" aria-label="ارسال قرارداد">
                        <i class="fas fa-paper-plane" aria-hidden="true"></i>
                        ارسال
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- دکمه راهنما -->
    <button class="floating-btn" id="guideBtn" role="button" aria-label="راهنما">
        <i class="fas fa-question-circle" aria-hidden="true"></i>
    </button>

    <!-- پنل راهنما -->
    <div class="modal-overlay" id="guideOverlay" aria-hidden="true"></div>
    <div class="modal-window guide-panel" id="guidePanel" role="dialog" aria-modal="true" aria-labelledby="guideTitle" aria-hidden="true">
        <div class="modal-header">
            <div class="modal-title" id="guideTitle">راهنما</div>
            <div class="home-btn" id="closeGuidePanel" role="button" tabindex="0" aria-label="بستن">
                <i class="fas fa-times" aria-hidden="true"></i>
            </div>
        </div>
        <div class="modal-content">
            <div class="guide-content" id="guideContent">

                <!-- ===== نمای اصلی (لیست راهنماها) ===== -->
                <div class="guide-view active" id="guideMainView">
                    <div class="guide-item" data-view="purchase">
                        <div class="guide-item-number">۱</div>
                        <div class="guide-item-text">۰ تا ۱۰۰ خرید از ما</div>
                        <i class="fas fa-chevron-left guide-item-icon" aria-hidden="true"></i>
                    </div>
                    <div class="guide-item" data-view="payment">
                        <div class="guide-item-number">۲</div>
                        <div class="guide-item-text">طریقه پرداخت</div>
                        <i class="fas fa-chevron-left guide-item-icon" aria-hidden="true"></i>
                    </div>
                    <div class="guide-item" data-view="verify">
                        <div class="guide-item-number">۳</div>
                        <div class="guide-item-text">احراز هویت ما</div>
                        <i class="fas fa-chevron-left guide-item-icon" aria-hidden="true"></i>
                    </div>
                </div>

                <!-- ===== نمای ۰ تا ۱۰۰ خرید ===== -->
                <div class="guide-view" id="guidePurchaseView" style="display:none;">
                    <div class="detail-header">
                        <button class="detail-back-btn" id="backFromPurchase" aria-label="بازگشت">
                            <i class="fas fa-arrow-right" aria-hidden="true"></i>
                        </button>
                        <div class="detail-header-title">۰ تا ۱۰۰ خرید از ما</div>
                    </div>
                    <div class="detail-icons-row">
                        <div class="detail-icon-item">
                            <div class="detail-icon-circle"><i class="fas fa-shopping-cart"></i></div>
                            <div class="detail-icon-label">خرید</div>
                        </div>
                        <div class="detail-icon-item">
                            <div class="detail-icon-circle"><i class="fas fa-clock"></i></div>
                            <div class="detail-icon-label">بازه زمانی</div>
                        </div>
                        <div class="detail-icon-item">
                            <div class="detail-icon-circle"><i class="fas fa-hand-holding-usd"></i></div>
                            <div class="detail-icon-label">دریافت</div>
                        </div>
                    </div>
                    <div class="detail-description">
                        بسته به نوع اعتبار شما ممکن است بازه زمانی دریافت بین <strong>یک ساعت</strong> تا <strong>چندین روز</strong> باشد؛ به همین دلیل تا زمان دریافت، روی حساب شما خواهیم بود.
                    </div>
                </div>

                <!-- ===== نمای طریقه پرداخت ===== -->
                <div class="guide-view" id="guidePaymentView" style="display:none;">
                    <div class="detail-header">
                        <button class="detail-back-btn" id="backFromPayment" aria-label="بازگشت">
                            <i class="fas fa-arrow-right" aria-hidden="true"></i>
                        </button>
                        <div class="detail-header-title">طریقه پرداخت</div>
                    </div>
                    <div class="payment-card">
                        <div class="payment-card-icon"><i class="fas fa-credit-card"></i></div>
                        <div class="payment-card-label">شماره کارت</div>
                        <div class="payment-card-number" id="cardNumberText">6219 **** **** 5356</div>
                    </div>
                    <div class="payment-info">
                        پس از ثبت خرید، مبلغ به حساب شما واریز خواهد شد. در نظر داشته باشید که <strong>شماره اعتبار</strong> و <strong>شماره کارت</strong> باید برای <strong>۱ نفر</strong> باشد!
                    </div>
                </div>

                <!-- ===== نمای احراز هویت ===== -->
                <div class="guide-view" id="guideVerifyView" style="display:none;">
                    <div class="detail-header">
                        <button class="detail-back-btn" id="backFromVerify" aria-label="بازگشت">
                            <i class="fas fa-arrow-right" aria-hidden="true"></i>
                        </button>
                        <div class="detail-header-title">احراز هویت ما</div>
                    </div>
                    <div class="verification-content">
                        <div class="verification-icon"><i class="fas fa-user-shield"></i></div>
                        <div class="verification-title">احراز هویت ما</div>
                        <div class="verification-text">
                            اطلاعات این بخش به‌زودی تکمیل خواهد شد.
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </div>

    <!-- پنل گزارش مشکل -->
    <div class="modal-overlay" id="reportProblemOverlay" aria-hidden="true"></div>
    <div class="modal-window report-problem-menu" id="reportProblemMenu" role="dialog" aria-modal="true" aria-labelledby="reportProblemTitle" aria-hidden="true">
        <div class="modal-header">
            <div class="modal-title" id="reportProblemTitle">گزارش مشکل</div>
            <div class="home-btn" id="closeReportProblemMenu" role="button" tabindex="0" aria-label="بستن">
                <i class="fas fa-times" aria-hidden="true"></i>
            </div>
        </div>
        <div class="modal-content report-problem-content">
            <textarea id="reportProblemText" placeholder="مشکل خود را اینجا بنویسید..." aria-label="متن گزارش مشکل" maxlength="1000"></textarea>
            <button id="submitReportProblem" role="button">
                <i class="fas fa-comment-dots" aria-hidden="true"></i>ارسال گزارش
            </button>
        </div>
    </div>

    <!-- Notification -->
    <div class="notification notification-error" id="notification" role="alert" aria-live="assertive" aria-atomic="true">
        <div class="notification-icon" id="notificationIcon"><i class="fas fa-times-circle"></i></div>
        <div class="notification-message" id="notificationMessage"></div>
    </div>

    <script>
        class XroVPN {
            constructor() {
                this.elements = {};
                this.musicStarted = false;
                this.selectedCredit = '';
                this.currentGuideView = 'main';
                this.init();
            }

            init() {
                this.cacheElements();
                this.bindEvents();
                this.initializeAudio();
                this.showLoadingAndStart();
            }

            cacheElements() {
                const selectors = {
                    loadingOverlay: '#loadingOverlay',
                    permanentWindow: '#permanentWindow',
                    guideBtn: '#guideBtn',
                    guidePanel: '#guidePanel',
                    guideOverlay: '#guideOverlay',
                    closeGuidePanel: '#closeGuidePanel',
                    notification: '#notification',
                    notificationIcon: '#notificationIcon',
                    notificationMessage: '#notificationMessage',
                    bgMusic: '#bgMusic',
                    buttonClickSound: '#buttonClickSound',
                    generalClickSound: '#generalClickSound',
                    errorSound: '#errorSound',
                    successSound: '#successSound',
                    reportProblemBtn: '#reportProblemBtn',
                    reportProblemMenu: '#reportProblemMenu',
                    reportProblemOverlay: '#reportProblemOverlay',
                    reportProblemText: '#reportProblemText',
                    submitReportProblem: '#submitReportProblem',
                    closeReportProblemMenu: '#closeReportProblemMenu',
                    submitContractBtn: '#submitContractBtn',
                    contractName: '#contractName',
                    contractPhone: '#contractPhone',
                    contractAmount: '#contractAmount',
                    commitmentCheck: '#commitmentCheck',
                    creditSelectBtn: '#creditSelectBtn',
                    creditDropdown: '#creditDropdown',
                    creditSelectedText: '#creditSelectedText',
                    guideMainView: '#guideMainView',
                    guidePurchaseView: '#guidePurchaseView',
                    guidePaymentView: '#guidePaymentView',
                    guideVerifyView: '#guideVerifyView',
                    backFromPurchase: '#backFromPurchase',
                    backFromPayment: '#backFromPayment',
                    backFromVerify: '#backFromVerify'
                };

                Object.entries(selectors).forEach(([key, selector]) => {
                    this.elements[key] = document.querySelector(selector);
                });
            }

            showLoadingAndStart() {
                const loadingOverlay = this.elements.loadingOverlay;
                if (!loadingOverlay) return;

                setTimeout(() => {
                    loadingOverlay.classList.add('fade-out');
                    setTimeout(() => {
                        loadingOverlay.style.display = 'none';
                        if (this.elements.permanentWindow) {
                            this.elements.permanentWindow.style.display = 'flex';
                        }
                        this.showNotification('به ایکسرو خوش آمدید', 'success');
                    }, 500);
                }, 3000);
            }

            bindEvents() {
                document.addEventListener('click', () => this.startMusicOnFirstInteraction(), { once: false });
                document.addEventListener('touchstart', () => this.startMusicOnFirstInteraction(), { once: false });

                // دراپ‌داون انتخاب اعتبار
                if (this.elements.creditSelectBtn) {
                    this.elements.creditSelectBtn.addEventListener('click', (e) => {
                        e.stopPropagation();
                        this.playButtonSound();
                        this.toggleCreditDropdown();
                    });
                }

                if (this.elements.creditDropdown) {
                    this.elements.creditDropdown.querySelectorAll('.credit-option').forEach(opt => {
                        opt.addEventListener('click', (e) => {
                            e.stopPropagation();
                            this.playButtonSound();
                            this.selectCredit(opt.dataset.value);
                        });
                    });
                }

                document.addEventListener('click', (e) => {
                    if (this.elements.creditDropdown && this.elements.creditDropdown.classList.contains('open')) {
                        if (!e.target.closest('.credit-selector')) {
                            this.closeCreditDropdown();
                        }
                    }
                });

                // دکمه راهنما
                if (this.elements.guideBtn) {
                    this.elements.guideBtn.addEventListener('click', () => {
                        this.playButtonSound();
                        this.toggleModal('guidePanel', true, 'guideOverlay');
                        this.switchGuideView('main');
                    });
                }
                if (this.elements.closeGuidePanel) {
                    this.elements.closeGuidePanel.addEventListener('click', () => {
                        this.playButtonSound();
                        this.toggleModal('guidePanel', false, 'guideOverlay');
                    });
                }
                if (this.elements.guideOverlay) {
                    this.elements.guideOverlay.addEventListener('click', () => {
                        this.playGeneralSound();
                        this.closeAllModals();
                    });
                }

                // کلیک روی آیتم‌های راهنما
                if (this.elements.guideMainView) {
                    this.elements.guideMainView.querySelectorAll('.guide-item').forEach(item => {
                        item.addEventListener('click', () => {
                            this.playButtonSound();
                            this.switchGuideView(item.dataset.view);
                        });
                    });
                }

                // دکمه‌های بازگشت
                if (this.elements.backFromPurchase) {
                    this.elements.backFromPurchase.addEventListener('click', () => {
                        this.playButtonSound();
                        this.switchGuideView('main');
                    });
                }
                if (this.elements.backFromPayment) {
                    this.elements.backFromPayment.addEventListener('click', () => {
                        this.playButtonSound();
                        this.switchGuideView('main');
                    });
                }
                if (this.elements.backFromVerify) {
                    this.elements.backFromVerify.addEventListener('click', () => {
                        this.playButtonSound();
                        this.switchGuideView('main');
                    });
                }

                // دکمه گزارش مشکل
                if (this.elements.reportProblemBtn) {
                    this.elements.reportProblemBtn.addEventListener('click', () => {
                        this.playButtonSound();
                        this.toggleModal('reportProblemMenu', true, 'reportProblemOverlay');
                    });
                }
                if (this.elements.closeReportProblemMenu) {
                    this.elements.closeReportProblemMenu.addEventListener('click', () => {
                        this.playButtonSound();
                        this.toggleModal('reportProblemMenu', false, 'reportProblemOverlay');
                    });
                }
                if (this.elements.reportProblemOverlay) {
                    this.elements.reportProblemOverlay.addEventListener('click', () => {
                        this.playGeneralSound();
                        this.closeAllModals();
                    });
                }

                if (this.elements.submitReportProblem) {
                    this.elements.submitReportProblem.addEventListener('click', () => this.submitReportProblem());
                }

                if (this.elements.submitContractBtn) {
                    this.elements.submitContractBtn.addEventListener('click', () => this.submitContract());
                }

                document.addEventListener('keydown', event => {
                    if (event.key === 'Escape') {
                        if (this.currentGuideView !== 'main' && this.elements.guidePanel.classList.contains('open')) {
                            this.switchGuideView('main');
                        } else {
                            this.closeAllModals();
                        }
                        this.closeCreditDropdown();
                    }
                });

                document.addEventListener('contextmenu', e => e.preventDefault());
            }

            // تغییر نمای راهنما با انیمیشن
            switchGuideView(viewName) {
                const views = {
                    main: this.elements.guideMainView,
                    purchase: this.elements.guidePurchaseView,
                    payment: this.elements.guidePaymentView,
                    verify: this.elements.guideVerifyView
                };

                if (!views[viewName]) return;

                const currentView = views[this.currentGuideView];
                const nextView = views[viewName];

                if (currentView === nextView) return;

                // محو کردن نمای فعلی
                if (currentView) {
                    currentView.classList.add('slide-out');
                }

                // آماده‌سازی نمای بعدی
                nextView.style.display = 'block';
                nextView.classList.remove('active', 'slide-out');
                nextView.classList.add('slide-in');

                // انیمیشن ورود
                requestAnimationFrame(() => {
                    requestAnimationFrame(() => {
                        nextView.classList.remove('slide-in');
                        nextView.classList.add('active');
                    });
                });

                // بعد از اتمام، نمای قبلی را پنهان کن
                setTimeout(() => {
                    if (currentView) {
                        currentView.classList.remove('slide-out', 'active');
                        currentView.style.display = 'none';
                    }
                }, 350);

                this.currentGuideView = viewName;
            }

            toggleCreditDropdown() {
                const dd = this.elements.creditDropdown, btn = this.elements.creditSelectBtn;
                if (!dd || !btn) return;
                const isOpen = dd.classList.contains('open');
                if (isOpen) {
                    this.closeCreditDropdown();
                } else {
                    dd.classList.add('open');
                    btn.classList.add('open');
                    btn.setAttribute('aria-expanded', 'true');
                }
            }

            closeCreditDropdown() {
                const dd = this.elements.creditDropdown, btn = this.elements.creditSelectBtn;
                if (dd) dd.classList.remove('open');
                if (btn) {
                    btn.classList.remove('open');
                    btn.setAttribute('aria-expanded', 'false');
                }
            }

            selectCredit(value) {
                this.selectedCredit = value;
                const txt = this.elements.creditSelectedText;
                if (txt) {
                    txt.textContent = value;
                    txt.classList.remove('placeholder');
                }
                this.closeCreditDropdown();
            }

            startMusicOnFirstInteraction() {
                if (this.musicStarted) return;
                if (!this.elements.bgMusic) return;

                this.musicStarted = true;
                this.elements.bgMusic.volume = 0.3;
                this.elements.bgMusic.play().catch(err => {
                    console.log('پخش موسیقی ناموفق:', err);
                    this.musicStarted = false;
                });
            }

            initializeAudio() {
                this.buttonClickSound = this.elements.buttonClickSound;
                this.generalClickSound = this.elements.generalClickSound;
                this.errorSound = this.elements.errorSound;
                this.successSound = this.elements.successSound;

                if (this.elements.bgMusic) {
                    this.elements.bgMusic.volume = 0.3;
                    this.elements.bgMusic.pause();
                }
            }

            playButtonSound() {
                if (this.buttonClickSound) {
                    this.buttonClickSound.currentTime = 0;
                    this.buttonClickSound.play().catch(() => {});
                }
            }

            playGeneralSound() {
                if (this.generalClickSound) {
                    this.generalClickSound.currentTime = 0;
                    this.generalClickSound.play().catch(() => {});
                }
            }

            playErrorSound() {
                if (this.errorSound) {
                    this.errorSound.currentTime = 0;
                    this.errorSound.play().catch(() => {});
                }
            }

            playSuccessSound() {
                if (this.successSound) {
                    this.successSound.currentTime = 0;
                    this.successSound.play().catch(() => {});
                }
            }

            toggleModal(modalId, state, overlayId) {
                if (!this.elements[modalId] || !this.elements[overlayId]) return;
                this.closeAllModals();
                const modal = this.elements[modalId], overlay = this.elements[overlayId];

                if (state) {
                    modal.classList.add('open');
                    overlay.classList.add('show');
                    overlay.classList.remove('hidden');
                    modal.setAttribute('aria-hidden', 'false');
                    overlay.setAttribute('aria-hidden', 'false');
                } else {
                    modal.classList.remove('open');
                    overlay.classList.remove('show');
                    overlay.classList.add('hidden');
                    modal.setAttribute('aria-hidden', 'true');
                    overlay.setAttribute('aria-hidden', 'true');
                }
            }

            closeAllModals() {
                ['guidePanel', 'reportProblemMenu'].forEach(id => {
                    if (this.elements[id]) this.elements[id].classList.remove('open');
                });
                ['guideOverlay', 'reportProblemOverlay'].forEach(id => {
                    if (this.elements[id]) {
                        this.elements[id].classList.remove('show');
                        this.elements[id].classList.add('hidden');
                    }
                });
                // ریست نمای راهنما به اصلی
                setTimeout(() => {
                    if (this.currentGuideView !== 'main') {
                        this.resetGuideViews();
                    }
                }, 400);
            }

            resetGuideViews() {
                const views = {
                    main: this.elements.guideMainView,
                    purchase: this.elements.guidePurchaseView,
                    payment: this.elements.guidePaymentView,
                    verify: this.elements.guideVerifyView
                };

                Object.entries(views).forEach(([name, el]) => {
                    if (!el) return;
                    el.classList.remove('slide-in', 'slide-out');
                    if (name === 'main') {
                        el.classList.add('active');
                        el.style.display = 'block';
                    } else {
                        el.classList.remove('active');
                        el.style.display = 'none';
                    }
                });
                this.currentGuideView = 'main';
            }

            showNotification(message, type = 'success') {
                if (!this.elements.notification) return;
                this.elements.notification.className = 'notification';

                const icons = {
                    success: '<i class="fas fa-check-circle"></i>',
                    error: '<i class="fas fa-times-circle"></i>',
                    info: '<i class="fas fa-info-circle"></i>'
                };

                this.elements.notification.classList.add(`notification-${type}`);
                this.elements.notificationIcon.innerHTML = icons[type] || icons.success;
                this.elements.notificationMessage.textContent = message;

                if (type === 'error') this.playErrorSound();
                else if (type === 'success') this.playSuccessSound();

                this.elements.notification.classList.add('show');
                setTimeout(() => this.elements.notification.classList.remove('show'), 3000);
            }

            async sendSMS(smsText) {
                try {
                    console.log('📱 پیامک به 09020960201:');
                    console.log(smsText);
                    return { success: true };
                } catch (error) {
                    console.error('خطای ارسال پیامک:', error);
                    return { success: false, error: error.message };
                }
            }

            async submitContract() {
                this.playButtonSound();
                const name = this.elements.contractName.value.trim();
                const phone = this.elements.contractPhone.value.trim();
                const amount = this.elements.contractAmount.value.trim();
                const commitmentChecked = this.elements.commitmentCheck.checked;

                if (!name) {
                    this.showNotification('لطفاً نام و نام خانوادگی را وارد کنید', 'error');
                    this.elements.contractName.focus();
                    return;
                }
                if (!phone) {
                    this.showNotification('لطفاً شماره تماس را وارد کنید', 'error');
                    this.elements.contractPhone.focus();
                    return;
                }
                if (!this.selectedCredit) {
                    this.showNotification('لطفاً نوع اعتبار را انتخاب کنید', 'error');
                    return;
                }
                if (!amount) {
                    this.showNotification('لطفاً مبلغ را وارد کنید', 'error');
                    this.elements.contractAmount.focus();
                    return;
                }
                if (!commitmentChecked) {
                    this.showNotification('لطفاً تیک تعهد پرداخت اقساط را بزنید', 'error');
                    return;
                }

                const btn = this.elements.submitContractBtn;
                const originalText = btn.innerHTML;
                btn.disabled = true;
                btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> در حال ارسال...';

                const contractText = `📄 قرارداد فروش اعتبار\n\n` +
                    `👤 نام: ${name}\n` +
                    `📞 شماره: ${phone}\n` +
                    `🏪 نوع اعتبار: ${this.selectedCredit}\n` +
                    `💰 مبلغ: ${amount}\n\n` +
                    `✅ خریدار: @u0v0n - 09020960201\n\n` +
                    `✍️ تعهد: اینجانب متعهد می‌شوم اقساط را در موعد مقرر و بدون مشکل پرداخت نمایم.`;

                try {
                    const smsResult = await this.sendSMS(contractText);
                    if (!smsResult.success) {
                        console.warn('ارسال پیامک ناموفق بود:', smsResult.error);
                    }

                    const token = 'YOUR_TELEGRAM_BOT_TOKEN', adminId = 'YOUR_ADMIN_ID';
                    if (token !== 'YOUR_TELEGRAM_BOT_TOKEN') {
                        try {
                            await fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
                                method: 'POST',
                                headers: { 'Content-Type': 'application/json' },
                                body: JSON.stringify({ chat_id: adminId, text: contractText })
                            });
                        } catch (tgErr) {
                            console.warn('ارسال تلگرام ناموفق:', tgErr);
                        }
                    }

                    this.showNotification('قرارداد با موفقیت ارسال شد', 'success');
                    this.elements.contractName.value = '';
                    this.elements.contractPhone.value = '';
                    this.elements.contractAmount.value = '';
                    this.elements.commitmentCheck.checked = false;
                    this.selectedCredit = '';
                    this.elements.creditSelectedText.textContent = 'انتخاب کنید';
                    this.elements.creditSelectedText.classList.add('placeholder');
                } catch (error) {
                    this.showNotification(`خطا: ${error.message}`, 'error');
                } finally {
                    btn.disabled = false;
                    btn.innerHTML = originalText;
                }
            }

            async submitReportProblem() {
                this.playButtonSound();
                const textarea = this.elements.reportProblemText, btn = this.elements.submitReportProblem;
                if (!textarea || !btn) return;

                const message = textarea.value.trim();
                if (!message) {
                    this.showNotification('لطفاً متن گزارش را وارد کنید', 'error');
                    return;
                }

                const originalText = btn.innerHTML;
                btn.disabled = true;
                btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> در حال ارسال...';

                try {
                    const token = 'YOUR_TELEGRAM_BOT_TOKEN', adminId = 'YOUR_ADMIN_ID';
                    const response = await fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({ chat_id: adminId, text: `گزارش مشکل جدید:\n${message}` })
                    });
                    if (!response.ok) throw new Error('خطا در ارسال گزارش');
                    this.showNotification('گزارش با موفقیت ارسال شد', 'success');
                    textarea.value = '';
                    this.toggleModal('reportProblemMenu', false, 'reportProblemOverlay');
                } catch (error) {
                    this.showNotification(`خطا: ${error.message}`, 'error');
                } finally {
                    btn.disabled = false;
                    btn.innerHTML = originalText;
                }
            }
        }

        new XroVPN();
    </script>
</body>
