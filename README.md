# dz-courses
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>منصة الدورات الرقمية</title>
  <style>
    body {
      margin: 0;
      font-family: 'Tahoma', sans-serif;
      background: linear-gradient(to bottom right, #0b0b0b, #1c003c);
      color: white;
      text-align: center;
      overflow: hidden;
    }

    header {
      padding: 60px 20px 30px;
    }

    header h1 {
      font-size: 42px;
      margin-bottom: 15px;
      color: #fff;
      text-shadow: 1px 1px 8px #6f42c1;
    }

    header p {
      font-size: 18px;
      color: #ccc;
    }

    .avatar {
      position: absolute;
      top: 20px;
      left: 20px;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      object-fit: cover;
      border: 2px solid #fff;
      cursor: pointer;
    }

    .dropdown {
      display: none;
      position: absolute;
      top: 90px;
      left: 20px;
      background-color: #222;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.5);
      padding: 10px;
      z-index: 1000;
    }

    .dropdown button {
      background: none;
      border: none;
      color: white;
      padding: 10px;
      font-size: 16px;
      text-align: right;
      width: 100%;
      cursor: pointer;
    }

    .dropdown button:hover {
      background-color: #6f42c1;
    }

    .why-us {
      padding: 50px 20px;
    }

    .why-us h2 {
      color: white;
      font-size: 28px;
      margin-bottom: 20px;
    }

    .why-us p {
      color: #bbb;
      font-size: 16px;
      max-width: 600px;
      margin: 0 auto 30px;
      line-height: 1.8;
    }

    .logo-box img {
      width: 120px;
      margin-bottom: 15px;
    }

    .logo-box button {
      padding: 10px 24px;
      background-color: #6f42c1;
      border: none;
      border-radius: 6px;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    #lockScreen {
      position: fixed;
      top: 0; right: 0; bottom: 0; left: 0;
      background-color: rgba(0, 0, 0, 0.3);
      backdrop-filter: blur(3px);
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      z-index: 9999;
    }

    #lockScreen input, .form-popup input {
      padding: 12px;
      font-size: 16px;
      margin-bottom: 10px;
      width: 260px;
      border-radius: 5px;
      border: 1px solid #6f42c1;
      background-color: rgba(255, 255, 255, 0.08);
      color: white;
      text-align: center;
    }

    #lockScreen button, .form-popup button {
      margin-top: 10px;
      padding: 10px 20px;
      background-color: #6f42c1;
      border: none;
      border-radius: 5px;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    /* نافذة النماذج */
    .form-popup {
      display: none;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: #1a1a1a;
      padding: 25px;
      border-radius: 10px;
      z-index: 10000;
      box-shadow: 0 0 20px rgba(0,0,0,0.6);
    }

    .form-popup h3 {
      color: white;
      margin-bottom: 15px;
    }

    .form-popup .close {
      position: absolute;
      top: 8px;
      right: 15px;
      font-size: 20px;
      color: #aaa;
      cursor: pointer;
    }

    .form-popup .close:hover {
      color: white;
    }
  </style>
</head>
<body>

  <!-- شاشة رمز الدخول -->
  <div id="lockScreen">
    <h2>يرجى إدخال رمز الدورة للدخول</h2>
    <input type="text" id="codeInput" placeholder="مثال: R590">
    <button onclick="unlock()">تسجيل دخول</button>
  </div>

  <!-- صورة المستخدم -->
  <img src="https://img.icons8.com/3d-fluency/94/user-male-circle.png" class="avatar" onclick="toggleMenu()">

  <!-- قائمة -->
  <div class="dropdown" id="userMenu">
    <button onclick="showLoginForm()">تسجيل دخول</button>
    <button onclick="alert('الدورات التدريبية')">دورات تدريبية</button>
    <button onclick="alert('المدرب الخاص')">مدرب خاص</button>
    <button onclick="alert('قسم التوظيف')">قسم توظيف</button>
  </div>

  <!-- محتوى -->
  <header>
    <h1>أفضل منصة للدورات الرقمية</h1>
    <p>أفضل المدرسين المخصصين في المنصة، الوسيط العربي الرائد لتلبية احتياجاتك في تعلم التقنيات الرقمية الحديثة.</p>
  </header>

  <section class="why-us">
    <h2>ليش منصتنا التعليمية؟</h2>
    <p>
      لأننا الأفضل في الأمان، ودقة المجال، والتقنية الفاخرة، والاحترام الكامل للمتعلم.
      نظامنا التعليمي يدمج بين الجودة والتطور التقني.
    </p>
    <div class="logo-box">
      <img src="https://img.icons8.com/fluency/96/online.png" alt="شعار المنصة">
      <br>
      <button onclick="showLoginChoice()">تسجيل دخول</button>
    </div>
  </section>

  <!-- نافذة اختيار تسجيل الدخول أو إنشاء حساب -->
  <div class="form-popup" id="loginChoice">
    <span class="close" onclick="closeForms()">×</span>
    <h3>اختر نوع العملية</h3>
    <button onclick="showForm('signupForm')">إنشاء حساب</button>
    <button onclick="showForm('loginForm')">تسجيل دخول</button>
  </div>

  <!-- نموذج إنشاء حساب -->
  <div class="form-popup" id="signupForm">
    <span class="close" onclick="closeForms()">×</span>
    <h3>إنشاء حساب جديد</h3>
    <input type="text" placeholder="الاسم الكامل">
    <input type="number" placeholder="العمر">
    <input type="text" placeholder="رقم الهوية">
    <input type="email" placeholder="البريد الإلكتروني">
    <input type="password" placeholder="كلمة السر">
    <button onclick="alert('تم إنشاء الحساب بنجاح')">تسجيل</button>
  </div>

  <!-- نموذج تسجيل دخول -->
  <div class="form-popup" id="loginForm">
    <span class="close" onclick="closeForms()">×</span>
    <h3>تسجيل دخول</h3>
    <input type="text" placeholder="رقم الجوال">
    <input type="text" placeholder="رقم الهوية">
    <button onclick="alert('تم تسجيل الدخول بنجاح')">دخول</button>
  </div>

  <script>
    function unlock() {
      const code = document.getElementById("codeInput").value.trim();
      if (code === "R590") {
        document.getElementById("lockScreen").style.display = "none";
        document.body.style.overflow = "auto";
      } else {
        alert("رمز الدورة غير صحيح.");
      }
    }

    function toggleMenu() {
      const menu = document.getElementById("userMenu");
      menu.style.display = (menu.style.display === "block") ? "none" : "block";
    }

    window.onclick = function(event) {
      const menu = document.getElementById("userMenu");
      const avatar = document.querySelector(".avatar");
      if (!avatar.contains(event.target) && !menu.contains(event.target)) {
        menu.style.display = "none";
      }
    }

    function showLoginChoice() {
      document.getElementById("loginChoice").style.display = "block";
    }

    function showLoginForm() {
      document.getElementById("loginChoice").style.display = "block";
    }

    function showForm(formId) {
      closeForms();
      document.getElementById(formId).style.display = "block";
    }

    function closeForms() {
      document.getElementById("loginChoice").style.display = "none";
      document.getElementById("signupForm").style.display = "none";
      document.getElementById("loginForm").style.display = "none";
    }
  </script>
</body>
</html>
