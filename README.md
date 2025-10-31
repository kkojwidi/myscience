<!doctype html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>منصة مستر محمد محمود — علوم</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#f6fbff;            /* خلفية فاتحة */
    --card:#ffffff;
    --accent1:#2b9ed9;       /* أزرق */
    --accent2:#3ddc97;       /* أخضر */
    --accent3:#ffd166;       /* أصفر فاتح */
    --muted:#5b6b74;
    --text:#05323a;
    --glass: rgba(3,19,26,0.04);
    --radius:14px;
  }
  *{box-sizing:border-box;font-family:'Cairo',sans-serif}
  html,body{height:100%;margin:0;background:linear-gradient(180deg,#f6fbff,#eaf7ff);color:var(--text);-webkit-font-smoothing:antialiased}
  .wrap{max-width:1100px;margin:18px auto;padding:18px;}

  /* ====== عام ====== */
  header.appbar{
    display:flex;gap:12px;align-items:center;justify-content:space-between;padding:12px 18px;border-radius:12px;
    background:linear-gradient(90deg, rgba(43,158,217,0.06), rgba(61,220,151,0.04));
    box-shadow: 0 8px 30px rgba(17,33,50,0.06);
  }
  .brand {display:flex;gap:12px;align-items:center}
  .logo{
    width:64px;height:64px;border-radius:12px;display:flex;align-items:center;justify-content:center;
    background:linear-gradient(135deg,var(--accent1),var(--accent2));color:white;font-weight:700;font-size:18px;
    box-shadow:0 8px 24px rgba(43,158,217,0.18);
  }
  .brand h1{margin:0;font-size:18px}
  .brand p{margin:0;font-size:12px;color:var(--muted)}

  /* صفحات (sections) */
  section.page{display:none;animation:fadeIn .28s ease; padding:18px 0}
  section.page.active{display:block}

  @keyframes fadeIn {from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}

  /* ====== صفحة التسجيل (ثنائية الواجهات) ====== */
  .auth-card{
    background:var(--card);border-radius:14px;padding:18px;box-shadow:0 10px 30px rgba(16,33,45,0.06);
    display:flex;gap:20px;align-items:center;
  }
  .auth-left{flex:1;padding:8px}
  .auth-right{width:420px;max-width:42%;min-width:260px}

  .toggle-auth{display:flex;gap:8px;margin-bottom:12px}
  .toggle-auth button{flex:1;padding:10px;border-radius:12px;border:0;cursor:pointer;font-weight:700;background:transparent;color:var(--muted)}
  .toggle-auth button.active{background:linear-gradient(90deg,var(--accent1),var(--accent2));color:white;box-shadow:0 8px 24px rgba(43,158,217,0.18)}

  label{display:block;font-size:13px;color:var(--muted);margin:8px 0 6px}
  input[type="text"], input[type="password"], input[type="email"]{
    width:100%;padding:12px;border-radius:10px;border:1px solid rgba(5,50,58,0.06);background:#fbfeff;font-size:15px;
  }

  .auth-actions{display:flex;gap:10px;align-items:center;margin-top:12px}
  .btn{padding:10px 16px;border-radius:10px;border:0;background:linear-gradient(90deg,var(--accent1),var(--accent2));color:white;cursor:pointer;font-weight:700}
  .btn.ghost{background:transparent;border:1px solid rgba(5,50,58,0.06);color:var(--text)}

  /* رسومات متحركة صغيرة في اليسار */
  .hero-visual{position:relative;padding:6px;border-radius:12px;background:linear-gradient(180deg,#ffffff,#f0fbff);box-shadow:inset 0 1px 0 rgba(255,255,255,0.6)}
  .atom-svg{width:100%;height:260px}

  /* ====== الصفحة الرئيسية ====== */
  .welcome-card{
    background:linear-gradient(180deg,#fff,#f7feff);border-radius:14px;padding:18px;display:flex;gap:18px;align-items:center;
    box-shadow: 0 10px 30px rgba(10,30,40,0.04);
  }
  .welcome-text{flex:1;text-align:right}
  .welcome-text h2{margin:0;font-size:20px}
  .welcome-text p{margin:6px 0 0;color:var(--muted)}

  .actions-row{display:flex;gap:12px;margin-top:12px;flex-wrap:wrap}
  .phase-btn{padding:12px 16px;border-radius:12px;background:linear-gradient(90deg,#ffffff,rgba(255,255,255,0.8));border:1px solid rgba(5,50,58,0.04);cursor:pointer;font-weight:700;min-width:150px}
  .phase-btn:hover{transform:translateY(-6px);box-shadow:0 12px 30px rgba(43,158,217,0.06)}

  /* ====== اختيار السنة (قائمة) ====== */
  .years-grid{display:flex;gap:12px;flex-wrap:wrap;margin-top:14px}
  .year-card{padding:14px 18px;border-radius:12px;background:linear-gradient(180deg,#ffffff,#f6fbff);cursor:pointer;border:1px solid rgba(5,50,58,0.04);min-width:130px;text-align:center}
  .year-card.active{background:linear-gradient(90deg,var(--accent2),var(--accent1));color:white;box-shadow:0 8px 24px rgba(61,220,151,0.12)}

  /* ====== صفحة الصف (الأسبوعيات) ====== */
  .weeks-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:12px;margin-top:18px}
  .week-card{background:#fff;padding:12px;border-radius:12px;cursor:pointer;border:1px solid rgba(5,50,58,0.04);text-align:center;box-shadow:0 6px 20px rgba(3,19,26,0.02)}
  .week-card:hover{transform:translateY(-6px)}
  .week-card.active{background:linear-gradient(90deg,var(--accent1),var(--accent2));color:white}

  .content-panel{margin-top:16px;background:linear-gradient(180deg,#ffffff,#f8ffff);padding:16px;border-radius:12px;border:1px solid rgba(5,50,58,0.04)}
  iframe.video{width:100%;height:320px;border-radius:10px;border:0;background:#000}

  .quiz-link{display:inline-block;margin-top:12px;padding:10px 12px;border-radius:10px;background:linear-gradient(90deg,var(--accent3),var(--accent2));color:#052;font-weight:700;text-decoration:none}

  /* footer */
  footer.appfooter{margin-top:20px;text-align:center;color:var(--muted);font-size:13px}

  /* responsive */
  @media(max-width:880px){
    .auth-card{flex-direction:column}
    .auth-right{width:100%;max-width:100%}
    .hero-visual{height:220px}
    iframe.video{height:220px}
  }
  @media(max-width:520px){
    header.appbar{flex-direction:column;align-items:flex-start;gap:8px}
    .brand p{display:none}
    .logo{width:56px;height:56px}
  }
</style>
</head>
<body>
  <div class="wrap">

    <!-- App bar -->
    <header class="appbar" role="banner">
      <div class="brand">
        <div class="logo">م م</div>
        <div>
          <h1>مستر محمد محمود</h1>
          <p>منصة تفاعلية لتعليم العلوم</p>
        </div>
      </div>
      <div id="top-right-area">
        <!-- يظهر بعد تسجيل الدخول -->
        <div id="user-info" style="display:none;text-align:right">
          <div style="font-weight:700" id="top-student-name"></div>
          <div style="font-size:12px;color:var(--muted)">طالب علوم</div>
        </div>
      </div>
    </header>

    <!-- ========= صفحة التسجيل (واجهتين: تسجيل جديد / تسجيل موجود) ========= -->
    <section id="auth-page" class="page active" aria-labelledby="auth-title">
      <h2 id="auth-title" style="text-align:right;margin:12px 0">أهلًا بك في منصة مستر محمد — سجّل أو ادخل</h2>

      <div class="auth-card" role="region" aria-label="منطقة التسجيل">
        <!-- اليسار: رسوم متحركة وتعريف -->
        <div class="auth-left">
          <div class="hero-visual" aria-hidden="true">
            <!-- ذرة متحركة (SVG) -->
            <svg class="atom-svg" viewBox="0 0 600 360" preserveAspectRatio="xMidYMid meet">
              <defs>
                <linearGradient id="gA" x1="0" x2="1"><stop offset="0" stop-color="#2b9ed9"/><stop offset="1" stop-color="#3ddc97"/></linearGradient>
              </defs>
              <rect x="24" y="12" width="552" height="336" rx="14" fill="url(#gA)" opacity="0.06"/>
              <g transform="translate(80,40)">
                <g transform="translate(200,120)">
                  <circle r="12" fill="#fff"/>
                  <g stroke="url(#gA)" stroke-width="3" stroke-opacity="0.25" fill="none">
                    <ellipse rx="160" ry="36" transform="rotate(20)"></ellipse>
                    <ellipse rx="100" ry="60" transform="rotate(-25)"></ellipse>
                    <ellipse rx="60" ry="140" transform="rotate(50)"></ellipse>
                  </g>

                  <!-- إلكترونات تتحرك -->
                  <circle cx="-10" cy="-160" r="8" fill="#fff">
                    <animateTransform attributeName="transform" dur="8s" type="rotate" from="0 0 0" to="360 0 0" repeatCount="indefinite"/>
                    <animate attributeName="cx" values="-10;-10;-10" dur="8s" repeatCount="indefinite"/>
                  </circle>
                  <circle cx="150" cy="0" r="7" fill="#fff">
                    <animateTransform attributeName="transform" dur="6s" type="rotate" from="360 0 0" to="0 0 0" repeatCount="indefinite"/>
                  </circle>
                  <circle cx="0" cy="170" r="6" fill="#fff">
                    <animateTransform attributeName="transform" dur="10s" type="rotate" from="0 0 0" to="360 0 0" repeatCount="indefinite"/>
                  </circle>
                </g>
              </g>

              <!-- فقاعات متحركة -->
              <g>
                <circle cx="80" cy="40" r="10" fill="#3ddc97" opacity="0.12">
                  <animate attributeName="cy" dur="4s" values="40;10;40" repeatCount="indefinite"/>
                </circle>
                <circle cx="520" cy="320" r="14" fill="#ffd166" opacity="0.12">
                  <animate attributeName="cy" dur="6s" values="320;260;320" repeatCount="indefinite"/>
                </circle>
              </g>
            </svg>
          </div>

          <div style="margin-top:12px;text-align:right">
            <h3 style="margin:0">منصة تعليمية بسيطة وممتعة</h3>
            <p style="margin:6px 0;color:var(--muted)">دروس فيديو منظمة في 12 أسبوع لكل صف + اختبارات قصيرة. مناسب للابتدائي والإعدادي والثانوي.</p>
            <ul style="margin:8px 0 0 18px;color:var(--muted);text-align:right">
              <li>واجهة خفيفة وسهلة</li>
              <li>عرض فيديو و رابط الاختبار لكل أسبوع</li>
              <li>تعمل على الموبايل والكمبيوتر</li>
            </ul>
          </div>
        </div>

        <!-- اليمين: واجهة التسجيل / الدخول -->
        <div class="auth-right" style="text-align:right">
          <div class="toggle-auth" role="tablist" aria-label="تبديل تسجيل">
            <button id="tab-new" class="active" onclick="showAuth('new')">تسجيل جديد</button>
            <button id="tab-loginExisting" onclick="showAuth('exist')">دخول لمستخدم مسجل</button>
          </div>

          <!-- تسجيل جديد -->
          <div id="auth-new">
            <label>اسم الطالب</label>
            <input id="reg-name" type="text" placeholder="مثال: أحمد محمد">

            <label>البريد/الهاتف (اختياري)</label>
            <input id="reg-contact" type="text" placeholder="مثال: example@mail.com or 0112...">

            <label>كلمة مرور</label>
            <input id="reg-pass" type="password" placeholder="اختر كلمة قوية">

            <div style="margin-top:10px;display:flex;gap:8px;flex-wrap:wrap">
              <button class="btn" onclick="registerNew()">سجل وابدأ</button>
              <button class="btn ghost" onclick="document.getElementById('reg-name').value='';document.getElementById('reg-contact').value='';document.getElementById('reg-pass').value=''">إعادة</button>
            </div>
            <p style="color:var(--muted);font-size:13px;margin-top:10px">لو مسجل بالفعل؟ استخدم تبويب "دخول لمستخدم مسجل".</p>
          </div>

          <!-- دخول موجود -->
          <div id="auth-exist" style="display:none">
            <label>اسم المستخدم</label>
            <input id="login-name" type="text" placeholder="اكتب اسمك">

            <label>كلمة المرور</label>
            <input id="login-pass" type="password" placeholder="كلمة المرور">

            <div style="margin-top:10px;display:flex;gap:8px;flex-wrap:wrap">
              <button class="btn" onclick="loginExisting()">دخول</button>
              <button class="btn ghost" onclick="fillDemo()">تجربة سريعة</button>
            </div>
            <p style="color:var(--muted);font-size:13px;margin-top:10px">إذا نسيت بياناتك، سجل جديدًا أو اتصل بالمدرس.</p>
          </div>

        </div>
      </div> <!-- auth-card -->
    </section>

    <!-- ========= الصفحة الرئيسية بعد الدخول ========= -->
    <section id="home-page" class="page" aria-labelledby="home-title">
      <div class="welcome-card">
        <div style="flex:1;text-align:right" class="welcome-text">
          <h2 id="welcome-title">أهلًا بك يا <span id="student-name-display"></span> 👋</h2>
          <p>أنا <strong>مستر محمد محمود</strong> — مدرس علوم. هنا هتلاقي دروس مبسطة، تجارب، وفيديوهات لكل مرحلة.</p>
          <div style="margin-top:8px;color:var(--muted)">اختر مرحلتك لعرض السنوات المتاحة</div>
          <div class="actions-row" style="margin-top:12px">
            <div class="phase-btn" onclick="choosePhase('ابتدائي')">المرحلة الابتدائية</div>
            <div class="phase-btn" onclick="choosePhase('إعدادي')">المرحلة الإعدادية</div>
            <div class="phase-btn" onclick="choosePhase('ثانوي')">المرحلة الثانوية</div>
          </div>
        </div>

        <div style="width:260px;min-width:200px">
          <!-- صورة مصغرة تعريفية و بطاقة مدرس -->
          <div style="background:linear-gradient(180deg,#fff,#f7fffb);padding:12px;border-radius:12px;box-shadow:0 8px 30px rgba(3,19,26,0.03);text-align:center">
            <div style="width:84px;height:84px;margin:0 auto;border-radius:12px;background:linear-gradient(135deg,var(--accent1),var(--accent2));display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:20px">م م</div>
            <h3 style="margin:10px 0 4px">مستر محمد محمود</h3>
            <p style="margin:0;color:var(--muted);font-size:13px">مدرس علوم — خبرة في تبسيط المناهج</p>
          </div>
          <div style="margin-top:12px;background:linear-gradient(180deg,#fff,#f6fbff);padding:10px;border-radius:12px;text-align:right;color:var(--muted)">
            <div style="font-weight:700;margin-bottom:6px">مزايا المنصة</div>
            <ul style="margin:0 0 0 14px">
              <li>دروس فيديو قصيرة</li>
              <li>اختبارات تقييمية</li>
              <li>محتوى مناسب لكل مرحلة</li>
            </ul>
          </div>
        </div>
      </div>

      <div style="margin-top:18px;display:flex;gap:12px;flex-wrap:wrap;align-items:center">
        <div style="flex:1">
          <h3 style="margin:0 0 6px">اختر المرحلة لعرض السنوات</h3>
          <div id="years-area" class="years-grid"></div>
        </div>
      </div>

      <div style="margin-top:14px">
        <button class="btn ghost" onclick="logout()">تسجيل خروج</button>
      </div>
    </section>

    <!-- ========= صفحة الصف (12 أسبوع) ========= -->
    <section id="class-page" class="page" aria-labelledby="class-title">
      <div style="display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap">
        <div style="text-align:right">
          <h2 id="class-title">صف — <span id="class-info"></span></h2>
          <p style="color:var(--muted);margin:6px 0 0">اختر أسبوع لتشاهد الفيديو وتدخل الاختبار.</p>
        </div>
        <div>
          <button class="btn ghost" onclick="backToHome()">⬅ العودة للرئيسية</button>
        </div>
      </div>

      <div class="weeks-grid" id="weeks-grid"></div>

      <div id="content-area" class="content-panel hidden" aria-live="polite">
        <div id="chosen-week-title" style="font-weight:700;margin-bottom:8px"></div>
        <div id="video-area">
          <h4 style="margin:6px 0">الفيديو التعليمي</h4>
          <iframe id="video-iframe" class="video" src="" allowfullscreen></iframe>
        </div>

        <div id="quiz-area" style="margin-top:12px">
          <h4 style="margin:6px 0">رابط الاختبار</h4>
          <a id="quiz-link" class="quiz-link" href="#" target="_blank">اذهب للاختبار</a>
        </div>
      </div>
    </section>

    <footer class="appfooter">© 2025 مستر محمد محمود — منصة تعليمية للعلوم</footer>
  </div>

<script>
/* ================= بيانات التكوين - عدّل الروابط هنا بسهولة =================
  - الصيغة: content[level][year][weekIndex] = { video: 'embed link', quiz: 'quiz link' }
  - مثال لينك يوتيوب embed: "https://www.youtube.com/embed/VIDEO_ID"
  - مثال اختبار: "https://forms.gle/XXXXX"
  - يمكنك ترك الخانات فارغة "" ثم إضافة لاحقًا.
*/
const content = {
  'ابتدائي': {
    'الرابعة': Array(12).fill({video:'',quiz:'#'}),
    'الخامسة': Array(12).fill({video:'',quiz:'#'}),
    'السادسة': Array(12).fill({video:'',quiz:'#'})
  },
  'إعدادي': {
    'الأولى': Array(12).fill({video:'',quiz:'#'}),
    'الثانية': Array(12).fill({video:'',quiz:'#'}),
    'الثالثة': Array(12).fill({video:'',quiz:'#'})
  },
  'ثانوي': {
    'الأولى': Array(12).fill({video:'',quiz:'#'}),
    'الثانية': Array(12).fill({video:'',quiz:'#'}),
    'الثالثة': Array(12).fill({video:'',quiz:'#'})
  }
};

/* --- ملاحظة مهمة: لو عايز تضع روابط لكل أسبوع تفتح الكونسول وتنفذ أمثلة:
   content['ابتدائي']['الرابعة'][0] = {video:'https://www.youtube.com/embed/VIDEOID', quiz:'https://forms.gle/XYZ'}
   ثم احفظ الملف محليًا - أو تضيفها مباشرة داخل الكود أعلاه.
*/

/* ========= إدارة الصفحات والتنقّل ========= */
function showPage(id){
  document.querySelectorAll('section.page').forEach(s=>s.classList.remove('active'));
  const el = document.getElementById(id);
  if(el) el.classList.add('active');
  window.scrollTo({top:0,behavior:'smooth'});
}

/* ---- واجهة تسجيل (تبديل) ---- */
function showAuth(mode){
  document.getElementById('tab-new').classList.remove('active');
  document.getElementById('tab-loginExisting').classList.remove('active');
  if(mode==='new'){
    document.getElementById('tab-new').classList.add('active');
    document.getElementById('auth-new').style.display='block';
    document.getElementById('auth-exist').style.display='none';
  } else {
    document.getElementById('tab-loginExisting').classList.add('active');
    document.getElementById('auth-new').style.display='none';
    document.getElementById('auth-exist').style.display='block';
  }
}

/* ---- تسجيل جديد (حفظ محليًا) ---- */
function registerNew(){
  const name = document.getElementById('reg-name').value.trim();
  const contact = document.getElementById('reg-contact').value.trim();
  const pass = document.getElementById('reg-pass').value;
  if(!name || !pass){ alert('من فضلك املأ الاسم وكلمة المرور'); return; }

  // نحفظ في localStorage بسيط (تطبيق تعليمي فقط)
  const users = JSON.parse(localStorage.getItem('mm_users')||'{}');
  if(users[name]){
    if(!confirm('الاسم موجود بالفعل. هل تريد استبدال بياناته؟')) return;
  }
  users[name] = {contact,pass};
  localStorage.setItem('mm_users', JSON.stringify(users));
  alert('تم التسجيل بنجاح! مرحبًا '+name);
  loginUser(name);
}

/* ---- دخول مستخدم مسجل ---- */
function loginExisting(){
  const name = document.getElementById('login-name').value.trim();
  const pass = document.getElementById('login-pass').value;
  if(!name || !pass){ alert('من فضلك املأ الحقول'); return; }
  const users = JSON.parse(localStorage.getItem('mm_users')||'{}');
  if(users[name] && users[name].pass===pass){
    loginUser(name);
  } else {
    alert('خطأ في بيانات الدخول. إذا لم تسجل بعد، استخدم "تسجيل جديد".');
  }
}

/* ---- وظيفة تجربة سريعة ---- */
function fillDemo(){
  // نسجل مستخدم تجريبي (غير دائم)
  const demo = 'طالب تجريبي';
  const users = JSON.parse(localStorage.getItem('mm_users')||'{}');
  users[demo] = {contact:'',pass:'1234'};
  localStorage.setItem('mm_users', JSON.stringify(users));
  document.getElementById('login-name').value = demo;
  document.getElementById('login-pass').value = '1234';
  loginExisting();
}

/* ---- بعد تسجيل الدخول ---- */
function loginUser(name){
  localStorage.setItem('mm_current', name);
  document.getElementById('top-student-name').textContent = name;
  document.getElementById('student-name-display').textContent = name;
  document.getElementById('user-info').style.display = 'block';
  showPage('home-page');
}

/* ---- خروج ---- */
function logout(){
  localStorage.removeItem('mm_current');
  document.getElementById('user-info').style.display = 'none';
  showPage('auth-page');
}

/* ---- اختيار المرحلة ثم السنوات ---- */
const phaseMap = {
  'ابتدائي': ['الرابعة','الخامسة','السادسة'],
  'إعدادي': ['الأولى','الثانية','الثالثة'],
  'ثانوي': ['الأولى','الثانية','الثالثة']
};

function choosePhase(phase){
  // عرض السنوات المتاحة
  const area = document.getElementById('years-area');
  area.innerHTML = '';
  phaseMap[phase].forEach(year=>{
    const d = document.createElement('div');
    d.className = 'year-card';
    d.textContent = year;
    d.onclick = ()=>openClass(phase, year);
    area.appendChild(d);
  });
  // Scroll to years
  area.scrollIntoView({behavior:'smooth'});
}

/* ---- فتح صفحة الصف (مع 12 أسبوع) ---- */
let currentPhase='', currentYear='';
function openClass(phase, year){
  currentPhase = phase; currentYear = year;
  document.getElementById('class-info').textContent = phase + ' — ' + year;
  // تظبيط العنوان
  document.getElementById('chosen-week-title').textContent = '';
  // إنشاء 12 بطاقة أسبوع
  const grid = document.getElementById('weeks-grid');
  grid.innerHTML = '';
  for(let i=1;i<=12;i++){
    const w = document.createElement('div');
    w.className = 'week-card';
    w.textContent = 'الأسبوع ' + i;
    w.dataset.week = i;
    w.onclick = ()=>selectWeek(i, w);
    grid.appendChild(w);
  }
  // إخفاء المحتوى حتى يضغط على أسبوع
  document.getElementById('content-area').classList.add('hidden');
  showPage('class-page');
}

/* ---- اختيار أسبوع ---- */
function selectWeek(weekNum, el){
  // تمييز
  document.querySelectorAll('.week-card').forEach(c=>c.classList.remove('active'));
  el.classList.add('active');

  // جلب الروابط من object content
  const level = currentPhase;
  const year = currentYear;
  let info = {video:'',quiz:'#'};
  try{
    info = (content[level] && content[level][year] && content[level][year][weekNum-1]) || {video:'',quiz:'#'};
  }catch(e){ info = {video:'',quiz:'#'}; }

  // عرض العنوان
  document.getElementById('chosen-week-title').textContent = `المحتوى — ${level} / ${year} — الأسبوع ${weekNum}`;
  // الفيديو
  const vf = document.getElementById('video-iframe');
  vf.src = info.video || '';
  // الاختبار
  const ql = document.getElementById('quiz-link');
  ql.href = info.quiz || '#';
  ql.textContent = (info.quiz && info.quiz!=='#') ? 'اذهب للاختبار' : 'لم يُضاف رابط للاختبار بعد';

  // إظهار اللوحة
  document.getElementById('content-area').classList.remove('hidden');
  // تمرير لعرض المحتوى
  document.getElementById('content-area').scrollIntoView({behavior:'smooth',block:'center'});
}

/* ---- العودة للرئيسية ---- */
function backToHome(){
  showPage('home-page');
}

/* ---- تشغيل الصفحة حسب إذا كان فيه مستخدم محفوظ ---- */
(function init(){
  const cur = localStorage.getItem('mm_current');
  if(cur){
    document.getElementById('top-student-name').textContent = cur;
    document.getElementById('student-name-display').textContent = cur;
    document.getElementById('user-info').style.display = 'block';
    showPage('home-page');
  } else {
    showPage('auth-page');
  }
})();

/* ============== تعليمات سريعة لإضافة الروابط ==============
- لتعبئة روابط الفيديو والاختبارات لكل أسبوع يمكنك تعديل الـ object 'content' أعلى في بداية السكربت.
- مثال: لتعيين فيديو للأسبوع الأول رابعة ابتدائي:
  content['ابتدائي']['الرابعة'][0] = { video: 'https://www.youtube.com/embed/VIDEO_ID', quiz: 'https://forms.gle/XXXX' }
- تأكد أن رابط الفيديو بصيغة embed (https://www.youtube.com/embed/ID) حتى يظهر داخل الإطار.
========================================================== */
</script>
</body>
</html>
