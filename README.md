<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>پنل نماینده ایرانیستا</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, 'Roboto', sans-serif;
        }

        body {
            background: #000000;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 16px;
        }

        .card {
            width: 100%;
            max-width: 460px;
            height: auto;
            min-height: 620px;
            background: #0c0c0c;
            border-radius: 48px;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            box-shadow: 0 25px 40px rgba(0, 0, 0, 0.8);
            border: 1px solid rgba(255, 255, 255, 0.06);
        }

        .header {
            padding: 24px 24px 16px 24px;
            display: flex;
            align-items: center;
            gap: 14px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.06);
        }

        .avatar {
            width: 52px;
            height: 52px;
            border-radius: 50%;
            object-fit: cover;
            border: 1.5px solid #ffb347;
            background: #111;
        }

        .brand h1 {
            color: #ffb347;
            font-size: 1.4rem;
            font-weight: 700;
        }

        .brand p {
            color: #6b6b6b;
            font-size: 0.7rem;
            margin-top: 2px;
        }

        .main-content {
            flex: 1;
            padding: 24px 24px 20px 24px;
        }

        .step {
            display: none;
            animation: fadeIn 0.3s ease;
        }

        .step.active {
            display: block;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(8px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .step-title {
            font-size: 1.55rem;
            font-weight: 700;
            color: #fff;
            margin-bottom: 28px;
            border-right: 3px solid #ffb347;
            padding-right: 14px;
        }

        .info-card {
            background: #0f0f0f;
            border-radius: 28px;
            padding: 18px;
            margin: 20px 0;
            border: 1px solid #1a1a1a;
        }

        .info-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            color: #ccc;
            font-size: 0.95rem;
            border-bottom: 1px solid #1a1a1a;
        }

        .info-item:last-child {
            border-bottom: none;
        }

        .info-item span:first-child {
            color: #ffb347;
            font-weight: 500;
        }

        .username-box {
            background: #151515;
            border-radius: 32px;
            padding: 14px 20px;
            margin-bottom: 24px;
            border: 1px solid #252525;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .username-label {
            color: #aaa;
            font-size: 0.85rem;
        }

        .username-value {
            color: #ffb347;
            font-size: 1.1rem;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .volume-ctrl {
            background: #0f0f0f;
            border-radius: 60px;
            padding: 8px 18px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 24px 0;
            border: 1px solid #1a1a1a;
        }

        .vol-btn {
            background: #1c1c1c;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 40px;
            font-size: 2rem;
            font-weight: bold;
            color: #ffb347;
            cursor: pointer;
        }

        .vol-btn:active {
            transform: scale(0.94);
        }

        .vol-value {
            font-size: 2rem;
            font-weight: 700;
            color: #ffb347;
        }

        .next-btn {
            background: #ffb347;
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 44px;
            font-size: 1rem;
            font-weight: 700;
            color: #000;
            margin-top: 20px;
            cursor: pointer;
        }

        .next-btn:active {
            transform: scale(0.98);
        }

        .final-area {
            display: none;
            margin-top: 20px;
            background: #0f0f0f;
            border-radius: 32px;
            padding: 18px;
            border: 1px solid #1a1a1a;
        }

        .preview-card {
            background: #0a0a0a;
            border-radius: 24px;
            padding: 14px;
            margin-bottom: 16px;
        }

        .preview-row {
            display: flex;
            justify-content: space-between;
            padding: 10px 6px;
            border-bottom: 1px solid #151515;
            color: #ddd;
            font-size: 0.9rem;
        }

        .preview-row .label {
            color: #ffb347;
            font-weight: 500;
        }

        .submit-btn {
            background: #ffb347;
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 44px;
            font-size: 1rem;
            font-weight: 800;
            color: #000;
            cursor: pointer;
            margin-top: 8px;
        }

        .submit-btn:active {
            transform: scale(0.98);
        }

        .footer {
            padding: 14px;
            text-align: center;
            font-size: 0.7rem;
            color: #ffb347;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            background: #080808;
            cursor: pointer;
            transition: all 0.2s;
        }

        .footer:active {
            background: #111;
        }

        .note {
            font-size: 10px;
            color: #555;
            text-align: center;
            margin-top: 12px;
        }

        .toast-msg {
            position: fixed;
            bottom: 80px;
            left: 50%;
            transform: translateX(-50%);
            background: #1a1a1a;
            color: #ffb347;
            padding: 10px 20px;
            border-radius: 40px;
            font-size: 0.85rem;
            font-weight: 500;
            z-index: 1000;
            border: 1px solid #ffb347;
            white-space: nowrap;
            display: none;
        }

        .toast-msg.show {
            display: block;
            animation: fadeOut 2s ease forwards;
        }

        @keyframes fadeOut {
            0% {
                opacity: 1;
            }
            70% {
                opacity: 1;
            }
            100% {
                opacity: 0;
                display: none;
            }
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="header">
            <img class="avatar" src="https://cdn.imgurl.ir/uploads/y633955_IMG_20260423_002704_888.jpg" alt="logo" onerror="this.src='https://placehold.co/52x52/ffb347/white?text=P'">
            <div class="brand">
                <h1>🇮🇷 ایرانیستا</h1>
                <p>سرویس اختصاصی ۳۰ روزه</p>
            </div>
        </div>

        <div class="main-content">
            <div class="step active" id="step1">
                <div class="step-title">❶ نام کاربری</div>
                <div class="username-box">
                    <span class="username-label">👤 نام کاربری شما:</span>
                    <span class="username-value" id="generatedUsername">XRO_0000000</span>
                </div>
                <button class="next-btn" onclick="nextStep(2)">➡ مرحله بعد</button>
            </div>

            <div class="step" id="step2">
                <div class="step-title">❷ اطلاعات سفارش</div>
                <div class="info-card">
                    <div class="info-item">
                        <span>📅 مدت دوره</span>
                        <span>۳۰ روز ثابت</span>
                    </div>
                    <div class="info-item">
                        <span>👥 نوع کاربر</span>
                        <span>تک نفره</span>
                    </div>
                </div>
                <button class="next-btn" onclick="nextStep(3)">➡ مرحله بعد</button>
            </div>

            <div class="step" id="step3">
                <div class="step-title">❸ حجم درخواستی</div>
                <div class="volume-ctrl">
                    <button class="vol-btn" id="volDown">−</button>
                    <span class="vol-value" id="volumeVal">1.7G</span>
                    <button class="vol-btn" id="volUp">+</button>
                </div>
                <button class="next-btn" id="confirmVolumeNext">✅ تأیید حجم</button>
                <div class="note">پس از تأیید، ثبت نهایی نمایش داده می‌شود</div>
            </div>

            <div id="finalContainer" class="final-area">
                <div class="preview-card" id="previewInfo"></div>
                <button class="submit-btn" id="finalSubmit">📨 ثبت درخواست سفارش</button>
            </div>
        </div>

        <div class="footer" id="footerBtn">
            🇮🇷 پنل نماینده ایرانیستا
        </div>
    </div>

    <div id="toastMsg" class="toast-msg"></div>

    <script>
        // تولید نام کاربری رندوم با فرمت XRO_XXXXXXX
        function generateRandomUsername() {
            let randomNum = Math.floor(1000000 + Math.random() * 9000000);
            return "XRO_" + randomNum;
        }

        let currentUsername = generateRandomUsername();
        document.getElementById("generatedUsername").innerText = currentUsername;

        // تنظیمات حجم
        let volumeIdx = 0;
        const volumes = ["1.7G", "3G", "5G"];
        const volDisplay = document.getElementById("volumeVal");

        document.getElementById("volUp")?.addEventListener("click", () => {
            if (volumeIdx < volumes.length - 1) volumeIdx++;
            volDisplay.innerText = volumes[volumeIdx];
        });

        document.getElementById("volDown")?.addEventListener("click", () => {
            if (volumeIdx > 0) volumeIdx--;
            volDisplay.innerText = volumes[volumeIdx];
        });

        // جابجایی بین مراحل
        function nextStep(step) {
            document.querySelectorAll(".step").forEach(s => s.classList.remove("active"));
            document.getElementById(`step${step}`).classList.add("active");
        }

        // تولید کد کاربری یکتا
        function generateUniqueCode() {
            return Date.now().toString(36).slice(-5).toUpperCase() + Math.floor(Math.random() * 1000).toString().padStart(3, '0');
        }

        // نمایش پیام موقت (toast)
        function showToast(message) {
            const toast = document.getElementById("toastMsg");
            toast.innerText = message;
            toast.classList.add("show");
            setTimeout(() => {
                toast.classList.remove("show");
            }, 2000);
        }

        // دکمه تأیید حجم
        document.getElementById("confirmVolumeNext")?.addEventListener("click", () => {
            let selectedVolume = document.getElementById("volumeVal").innerText;
            let previewHTML = `
                <div class="preview-row">
                    <span class="label">👤 نام کاربری</span>
                    <span>${escapeHtml(currentUsername)}</span>
                </div>
                <div class="preview-row">
                    <span class="label">📅 مدت دوره</span>
                    <span>۳۰ روز ثابت</span>
                </div>
                <div class="preview-row">
                    <span class="label">👥 نوع کاربر</span>
                    <span>تک نفره</span>
                </div>
                <div class="preview-row">
                    <span class="label">💾 حجم کاربر</span>
                    <span>${escapeHtml(selectedVolume)}</span>
                </div>
            `;
            document.getElementById("previewInfo").innerHTML = previewHTML;
            document.getElementById("step3").classList.remove("active");
            document.getElementById("finalContainer").style.display = "block";
            window.orderData = {
                username: currentUsername,
                volume: selectedVolume
            };
        });

        // دکمه ثبت نهایی (ارسال پیامک)
        document.getElementById("finalSubmit")?.addEventListener("click", () => {
            let data = window.orderData || {};
            let username = data.username || currentUsername;
            let volume = data.volume || document.getElementById("volumeVal")?.innerText || "1.7G";
            let uniqueCode = generateUniqueCode();
            
            let message = `نام کاربری: ${username}%0Aکد کاربری: ${uniqueCode}%0Aنوع کاربر: تک نفره%0Aحجم کاربر: ${volume}%0A%0A✅ بعد از ارسال منتظر باش تا شماره کارت واست ارسال بشه ...`;
            let phoneNumber = "9231121847";
            let smsUrl = `sms:${phoneNumber}?body=${message}`;
            window.location.href = smsUrl;
        });

        // دکمه فوتر (پنل نماینده ایرانیستا)
        document.getElementById("footerBtn")?.addEventListener("click", () => {
            showToast("کیر تو کون اشکان");
        });

        // تابع escape برای امنیت
        function escapeHtml(str) {
            return str.replace(/[&<>]/g, function(m) {
                if (m === '&') return '&amp;';
                if (m === '<') return '&lt;';
                if (m === '>') return '&gt;';
                return m;
            });
        }
    </script>
</body>
</html>
