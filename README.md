<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ThinG GameshoP | แหล่งรวมไอดีเกมระดับพรีเมียม</title>
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600&family=Orbitron:wght@500;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-neon: #00d4ff;
            --secondary-neon: #fb2576;
            --dark-blue: #0f3460;
            --deep-dark: #1a1a2e;
            --glass: rgba(255, 255, 255, 0.05);
        }

        * { box-sizing: border-box; }
        
        body { 
            margin: 0; padding: 0; font-family: 'Kanit', sans-serif;
            background: radial-gradient(circle at center, #16213e 0%, #1a1a2e 100%);
            min-height: 100vh;
            color: white;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
        }

        /* --- Header Section --- */
        .main-header {
            width: 100%;
            background: rgba(10, 10, 25, 0.9);
            backdrop-filter: blur(15px);
            border-bottom: 2px solid var(--primary-neon);
            position: fixed;
            top: 0; left: 0; z-index: 1000;
            padding: 10px 0;
            animation: slideDown 0.6s ease-out;
        }

        .header-container {
            max-width: 1200px; margin: 0 auto; padding: 0 20px;
            display: flex; justify-content: space-between; align-items: center;
        }

        .brand-name {
            font-family: 'Orbitron', sans-serif; font-size: 24px; font-weight: 900;
            text-transform: uppercase; letter-spacing: 2px;
            color: white; text-shadow: 0 0 10px var(--primary-neon);
            cursor: pointer; transition: 0.3s;
        }

        .brand-name span { color: var(--primary-neon); }
        .brand-name:hover { transform: scale(1.05); }

        .nav-menu ul {
            display: flex; list-style: none; gap: 25px; margin: 0; padding: 0;
        }

        .nav-menu a {
            text-decoration: none; color: #ccc; font-size: 14px; font-weight: 600;
            transition: 0.3s; letter-spacing: 1px;
        }

        .nav-menu a:hover { color: var(--primary-neon); text-shadow: 0 0 8px var(--primary-neon); }

        .header-actions .btn-login-nav {
            background: transparent; border: 2px solid var(--secondary-neon);
            color: var(--secondary-neon); padding: 8px 18px; border-radius: 8px;
            font-family: 'Orbitron', sans-serif; font-size: 12px; font-weight: bold;
            cursor: pointer; transition: 0.4s;
        }

        .header-actions .btn-login-nav:hover {
            background: var(--secondary-neon); color: white;
            box-shadow: 0 0 15px var(--secondary-neon);
        }

        /* --- Main Content Section --- */
        .content-wrapper {
            flex: 1; display: flex; justify-content: center; align-items: center;
            padding-top: 100px; 
            padding-bottom: 40px;
        }

        .auth-container {
            background: var(--glass);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 40px; border-radius: 24px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            width: 90%; max-width: 420px; text-align: center;
            animation: zoomIn 0.5s ease-out;
        }

        h2 { 
            font-family: 'Orbitron', sans-serif; font-size: 28px; 
            margin-bottom: 30px; color: white;
            text-shadow: 0 0 10px rgba(255,255,255,0.3);
        }

        .input-group { margin-bottom: 15px; text-align: left; }
        label { display: block; font-size: 12px; color: var(--primary-neon); margin-bottom: 5px; margin-left: 5px; }

        input {
            width: 100%; padding: 15px;
            background: rgba(0, 0, 0, 0.4); border: 2px solid #222;
            border-radius: 12px; color: #fff; font-size: 16px; outline: none;
            transition: 0.3s;
        }

        input:focus { 
            border-color: var(--primary-neon); 
            box-shadow: 0 0 15px rgba(0, 212, 255, 0.2); 
        }

        .btn-main {
            width: 100%; padding: 16px; 
            background: linear-gradient(45deg, #e94560, #fb2576);
            color: white; border: none; border-radius: 12px;
            font-size: 16px; font-weight: 700; font-family: 'Orbitron', sans-serif;
            cursor: pointer; transition: 0.3s; margin-top: 10px;
            text-transform: uppercase; letter-spacing: 1px;
        }

        .btn-main:hover { 
            transform: translateY(-3px); 
            box-shadow: 0 10px 20px rgba(251, 37, 118, 0.4); 
        }

        .btn-register { background: linear-gradient(45deg, #00d4ff, #0072ff); }
        .btn-register:hover { box-shadow: 0 10px 20px rgba(0, 212, 255, 0.4); }

        .switch-link { color: #888; margin-top: 25px; font-size: 14px; cursor: pointer; transition: 0.3s; }
        .switch-link:hover { color: var(--primary-neon); }

        #message { margin-top: 20px; font-size: 14px; min-height: 24px; font-weight: 600; }
        .hidden { display: none; }

        /* --- Animations --- */
        @keyframes slideDown { from { transform: translateY(-100%); } to { transform: translateY(0); } }
        @keyframes zoomIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        .loader {
            border: 3px solid rgba(255,255,255,0.1); border-top: 3px solid var(--primary-neon);
            border-radius: 50%; width: 20px; height: 20px; animation: spin 0.8s linear infinite;
            display: inline-block; vertical-align: middle; margin-right: 10px;
        }

        @media (max-width: 768px) {
            .nav-menu { display: none; }
            .auth-container { padding: 30px 20px; }
        }
    </style>
</head>
<body>

    <header class="main-header">
        <div class="header-container">
            <div class="brand-name" onclick="location.reload()">ThinG <span>GameshoP</span></div>
            <nav class="nav-menu">
                <ul>
                    <li><a href="#">หน้าแรก</a></li>
                    <li><a href="#">สินค้าทั้งหมด</a></li>
                    <li><a href="#">วิธีเติมเงิน</a></li>
                    <li><a href="#">ติดต่อเรา</a></li>
                </ul>
            </nav>
            <div class="header-actions">
                <button class="btn-login-nav" onclick="focusAuth()">MEMBER</button>
            </div>
        </div>
    </header>

    <div class="content-wrapper">
        <div class="auth-container" id="authBox">
            
            <div id="loginForm">
                <h2>LOGIN</h2>
                <div class="input-group">
                    <label>ชื่อผู้ใช้งาน</label>
                    <input type="text" id="userLogin" placeholder="ENTER USERNAME" autocomplete="off">
                </div>
                <div class="input-group">
                    <label>รหัสผ่าน</label>
                    <input type="password" id="passLogin" placeholder="ENTER PASSWORD">
                </div>
                <button class="btn-main" id="btnLogin" onclick="auth('login')">Access System</button>
                <div class="switch-link" onclick="toggleForm()">ยังไม่มีบัญชีสมาชิก? สมัครได้ที่นี่</div>
            </div>

            <div id="registerForm" class="hidden">
                <h2>REGISTER</h2>
                <div class="input-group">
                    <label>ตั้งชื่อผู้ใช้งาน</label>
                    <input type="text" id="userReg" placeholder="NEW USERNAME" autocomplete="off">
                </div>
                <div class="input-group">
                    <label>ตั้งรหัสผ่าน</label>
                    <input type="password" id="passReg" placeholder="NEW PASSWORD">
                </div>
                <button class="btn-main btn-register" id="btnReg" onclick="auth('register')">Confirm Register</button>
                <div class="switch-link" onclick="toggleForm()">มีบัญชีอยู่แล้ว? กลับหน้าล็อกอิน</div>
            </div>

            <div id="message"></div>
        </div>
    </div>

    <script>
        // *** อัปเดต URL ล่าสุดตามที่คุณขอเรียบร้อยแล้ว ***
        const scriptURL = 'https://script.google.com/macros/s/AKfycbwmBrzWnrCtMgBc9OmyC_Vl8iSyzz3xmHsGWGapmj-eOV2LLSI5IvkrnHjQ1E6B4InfAA/exec';

        function toggleForm() {
            const loginFm = document.getElementById('loginForm');
            const regFm = document.getElementById('registerForm');
            const msg = document.getElementById('message');
            
            loginFm.classList.toggle('hidden');
            regFm.classList.toggle('hidden');
            msg.innerText = "";
            
            document.getElementById('authBox').style.animation = 'none';
            document.getElementById('authBox').offsetHeight; 
            document.getElementById('authBox').style.animation = 'zoomIn 0.4s ease-out';
        }

        function focusAuth() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
            const box = document.getElementById('authBox');
            box.style.boxShadow = "0 0 30px var(--primary-neon)";
            setTimeout(() => { box.style.boxShadow = "0 20px 50px rgba(0, 0, 0, 0.5)"; }, 1000);
        }

        async function auth(action) {
            const isLogin = (action === 'login');
            const user = document.getElementById(isLogin ? 'userLogin' : 'userReg').value.trim();
            const pass = document.getElementById(isLogin ? 'passLogin' : 'passReg').value.trim();
            const btn = document.getElementById(isLogin ? 'btnLogin' : 'btnReg');
            const msg = document.getElementById('message');

            if (!user || !pass) {
                msg.style.color = "#ff4d4d";
                msg.innerText = "✖ กรุณากรอกข้อมูลให้ครบถ้วน";
                return;
            }

            btn.disabled = true;
            msg.style.color = "var(--primary-neon)";
            msg.innerHTML = '<div class="loader"></div> กำลังสื่อสารกับเซิร์ฟเวอร์...';

            try {
                const response = await fetch(scriptURL, {
                    method: 'POST',
                    body: JSON.stringify({ action: action, username: user, password: pass })
                });
                
                const result = await response.text();

                if (result === "success") {
                    msg.style.color = "#39ff14";
                    msg.innerText = "✔ ยืนยันตัวตนสำเร็จ! กำลังเข้าสู่ระบบ...";
                    setTimeout(() => {
                        window.location.href = "https://www.google.com"; 
                    }, 1500);
                } else if (result === "registered") {
                    msg.style.color = "#39ff14";
                    msg.innerText = "✔ สมัครสมาชิกสำเร็จ! ระบบกำลังพากลับไปล็อกอิน";
                    setTimeout(() => toggleForm(), 2000);
                } else if (result === "exists") {
                    msg.style.color = "#ffcc00";
                    msg.innerText = "✖ ขออภัย! ชื่อผู้ใช้นี้ถูกใช้งานแล้ว";
                    btn.disabled = false;
                } else {
                    msg.style.color = "#ff4d4d";
                    msg.innerText = "✖ ชื่อผู้ใช้หรือรหัสผ่านไม่ถูกต้อง";
                    btn.disabled = false;
                }
            } catch (error) {
                msg.style.color = "#ff4d4d";
                msg.innerText = "⚠ เชื่อมต่อล้มเหลว (Check Network/Deployment)";
                btn.disabled = false;
            }
        }
    </script>
</body>
</html>
