<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>HealthQ — Your Smart Health Companion</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/js/all.min.js"></script>
<style>
:root{
  --green:#16A085; --green-dark:#087F6C; --blue:#4F7CFF; --purple:#7657FF;
  --white:#FFFFFF; --bg:#F5F9F8; --text:#17252F; --muted:#6B8079;
  --card:#FFFFFF; --border:#E4EEEB; --danger:#E5534B; --warn:#E8A33D;
  --radius:18px; --shadow:0 8px 24px rgba(23,37,47,.08);
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --bg:#0E1614; --card:#16201D; --text:#EAF3F0; --muted:#8FA39C; --border:#233029; --white:#16201D;
  }
}
:root[data-theme="dark"]{
  --bg:#0E1614; --card:#16201D; --text:#EAF3F0; --muted:#8FA39C; --border:#233029; --white:#16201D;
}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{margin:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
body{font-family:Inter,system-ui,sans-serif;background:var(--bg);color:var(--text);height:100%;overflow-x:hidden;transition:background .2s,color .2s}
html,body{height:100%}
button,input,select{font-family:inherit}
.app{max-width:480px;margin:0 auto;min-height:100%;position:relative;padding-bottom:calc(78px + env(safe-area-inset-bottom,0px))}
@media(min-width:900px){.app{max-width:1100px}}

/* topbar */
.topbar{position:sticky;top:0;z-index:20;display:flex;align-items:center;justify-content:space-between;padding:14px 18px;padding-top:calc(14px + env(safe-area-inset-top,0px));background:linear-gradient(180deg,var(--bg) 70%,transparent);backdrop-filter:blur(6px)}
.brand{display:flex;align-items:center;gap:8px;font-weight:800;font-size:19px}
.brand .mark{width:34px;height:34px;border-radius:10px;background:linear-gradient(135deg,var(--green),var(--blue));display:flex;align-items:center;justify-content:center;color:#fff;font-size:16px;box-shadow:var(--shadow)}
.icon-btn{width:38px;height:38px;border-radius:12px;border:none;background:var(--card);box-shadow:var(--shadow);display:flex;align-items:center;justify-content:center;color:var(--text);cursor:pointer;position:relative}
.icon-btn .dot{position:absolute;top:6px;right:6px;width:7px;height:7px;background:var(--danger);border-radius:50%}
.topbar-actions{display:flex;gap:8px}

/* views */
.view{display:none;padding:4px 18px 24px;animation:fade .25s ease}
.view.active{display:block}
@keyframes fade{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}

/* desktop nav */
.desktop-nav{display:none}
@media(min-width:900px){
  .desktop-nav{display:flex;gap:6px;padding:0 18px 14px}
  .desktop-nav button{border:none;background:transparent;color:var(--muted);font-weight:600;padding:10px 16px;border-radius:12px;cursor:pointer;font-size:14px}
  .desktop-nav button.active{background:var(--card);color:var(--green-dark);box-shadow:var(--shadow)}
  .bottom-nav{display:none !important}
  .app{padding-bottom:24px}
}

/* card */
.card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:18px;box-shadow:var(--shadow)}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.section-title{font-size:15px;font-weight:700;margin:22px 0 12px;display:flex;align-items:center;justify-content:space-between}
.section-title span.link{font-size:12.5px;color:var(--blue);font-weight:600;cursor:pointer}
.muted{color:var(--muted);font-size:13px}
.pill{display:inline-flex;align-items:center;gap:6px;font-size:11px;font-weight:700;padding:4px 9px;border-radius:99px;background:rgba(22,160,133,.12);color:var(--green-dark)}
.pill.sample{background:rgba(232,163,61,.15);color:#B4791F}

/* buttons */
.btn{border:none;border-radius:14px;padding:14px 18px;font-weight:700;font-size:14.5px;cursor:pointer;display:inline-flex;align-items:center;justify-content:center;gap:8px;width:100%;transition:transform .12s, opacity .12s}
.btn:active{transform:scale(.97)}
.btn:disabled{opacity:.5;cursor:not-allowed}
.btn-primary{background:linear-gradient(135deg,var(--green),var(--green-dark));color:#fff;box-shadow:0 6px 18px rgba(22,160,133,.35)}
.btn-outline{background:transparent;border:1.5px solid var(--border);color:var(--text)}
.btn-ghost{background:rgba(79,124,255,.1);color:var(--blue)}
.btn-danger{background:rgba(229,83,75,.1);color:var(--danger)}
.btn-sm{padding:9px 14px;font-size:13px;width:auto}
.btn .spin{width:15px;height:15px;border:2px solid #fff;border-top-color:transparent;border-radius:50%;animation:spin .7s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}

/* forms */
.field{margin-bottom:14px}
.field label{display:block;font-size:12.5px;font-weight:600;margin-bottom:6px;color:var(--muted)}
.input-wrap{position:relative}
.field input,.field select{width:100%;padding:13px 14px;border-radius:12px;border:1.5px solid var(--border);background:var(--bg);color:var(--text);font-size:14.5px;outline:none}
.field input:focus,.field select:focus{border-color:var(--green)}
.field .toggle-pass{position:absolute;right:12px;top:50%;transform:translateY(-50%);cursor:pointer;color:var(--muted)}
.field.error input{border-color:var(--danger)}
.field .err-msg{color:var(--danger);font-size:11.5px;margin-top:5px;display:none}
.field.error .err-msg{display:block}
.row{display:flex;align-items:center;gap:8px;font-size:13px;color:var(--muted)}

/* auth */
.auth-wrap{padding-top:28px}
.auth-logo{width:64px;height:64px;border-radius:18px;background:linear-gradient(135deg,var(--green),var(--purple));display:flex;align-items:center;justify-content:center;color:#fff;font-size:28px;margin:0 auto 14px;box-shadow:var(--shadow)}
.auth-tabs{display:flex;background:var(--card);border-radius:14px;padding:4px;margin-bottom:22px;border:1px solid var(--border)}
.auth-tabs button{flex:1;border:none;background:transparent;padding:11px;border-radius:11px;font-weight:700;color:var(--muted);cursor:pointer;font-size:13.5px}
.auth-tabs button.active{background:var(--green);color:#fff}
.divider{display:flex;align-items:center;gap:10px;color:var(--muted);font-size:12px;margin:16px 0}
.divider::before,.divider::after{content:"";flex:1;height:1px;background:var(--border)}

/* health score ring */
.score-card{background:linear-gradient(135deg,var(--green),var(--blue));color:#fff;border-radius:var(--radius);padding:20px;display:flex;align-items:center;justify-content:space-between;box-shadow:0 10px 26px rgba(22,160,133,.3)}
.ring{width:64px;height:64px;border-radius:50%;background:conic-gradient(#fff var(--pct,78%),rgba(255,255,255,.3) 0);display:flex;align-items:center;justify-content:center}
.ring-inner{width:50px;height:50px;border-radius:50%;background:rgba(0,0,0,.12);display:flex;align-items:center;justify-content:center;font-weight:800;font-size:15px}

/* health metric cards */
.metric{display:flex;flex-direction:column;gap:6px}
.metric .top{display:flex;align-items:center;justify-content:space-between}
.metric .icon{width:34px;height:34px;border-radius:10px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:14px}
.bar{height:6px;border-radius:99px;background:var(--border);overflow:hidden;margin-top:4px}
.bar>div{height:100%;border-radius:99px}
.metric-val{font-size:19px;font-weight:800}
.metric-label{font-size:11.5px;color:var(--muted)}

/* quick actions */
.qa-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}
.qa{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:12px 6px;text-align:center;cursor:pointer;box-shadow:var(--shadow)}
.qa .ic{width:40px;height:40px;border-radius:12px;margin:0 auto 8px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:16px}
.qa span{font-size:10.5px;font-weight:600;color:var(--muted);line-height:1.2;display:block}

/* chat */
.chat-box{display:flex;flex-direction:column;gap:10px;padding:6px 0 14px;min-height:300px}
.msg{max-width:80%;padding:11px 14px;border-radius:16px;font-size:14px;line-height:1.4}
.msg.ai{background:var(--card);border:1px solid var(--border);border-bottom-left-radius:4px;align-self:flex-start}
.msg.user{background:linear-gradient(135deg,var(--green),var(--green-dark));color:#fff;border-bottom-right-radius:4px;align-self:flex-end}
.typing{display:flex;gap:4px;padding:12px 14px}
.typing span{width:6px;height:6px;background:var(--muted);border-radius:50%;animation:blink 1.2s infinite}
.typing span:nth-child(2){animation-delay:.2s}.typing span:nth-child(3){animation-delay:.4s}
@keyframes blink{0%,60%,100%{opacity:.3}30%{opacity:1}}
.chat-input-bar{position:sticky;bottom:calc(78px + env(safe-area-inset-bottom,0px));display:flex;gap:8px;background:var(--bg);padding-top:8px}
.chip{display:inline-block;font-size:12.5px;padding:9px 13px;border-radius:99px;background:var(--card);border:1px solid var(--border);margin:4px 6px 0 0;cursor:pointer}
.disclaimer{font-size:11.5px;color:var(--muted);background:rgba(232,163,61,.1);border:1px solid rgba(232,163,61,.3);padding:10px 12px;border-radius:12px;margin-bottom:14px}
.emergency-banner{background:rgba(229,83,75,.1);border:1px solid rgba(229,83,75,.3);color:var(--danger);padding:10px 12px;border-radius:12px;font-size:12px;margin-top:10px}

/* symptom chips */
.symptom-grid{display:flex;flex-wrap:wrap;gap:8px;margin:10px 0}
.sym-chip{padding:9px 14px;border-radius:99px;background:var(--card);border:1.5px solid var(--border);font-size:13px;cursor:pointer;font-weight:600}
.sym-chip.sel{background:var(--green);border-color:var(--green);color:#fff}

/* doctor card */
.doc-card{display:flex;gap:12px;align-items:center}
.avatar{width:52px;height:52px;border-radius:14px;background:linear-gradient(135deg,var(--blue),var(--purple));display:flex;align-items:center;justify-content:center;color:#fff;font-weight:800;font-size:17px;flex-shrink:0}
.stars{color:#F0A83A;font-size:12px}

/* medicine row */
.med-row{display:flex;align-items:center;gap:12px}
.med-icon{width:44px;height:44px;border-radius:12px;background:rgba(79,124,255,.12);color:var(--blue);display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0}
.med-actions{display:flex;gap:6px}
.circle-btn{width:34px;height:34px;border-radius:50%;border:1.5px solid var(--border);background:transparent;color:var(--muted);cursor:pointer;display:flex;align-items:center;justify-content:center}
.circle-btn.taken{background:var(--green);border-color:var(--green);color:#fff}

/* modal */
.overlay{position:fixed;inset:0;background:rgba(10,20,17,.5);z-index:50;display:none;align-items:flex-end;justify-content:center}
.overlay.active{display:flex}
@media(min-width:640px){.overlay{align-items:center}}
.modal{background:var(--card);width:100%;max-width:480px;border-radius:22px 22px 0 0;padding:20px;max-height:88vh;overflow-y:auto;animation:up .25s ease}
@media(min-width:640px){.modal{border-radius:22px}}
@keyframes up{from{transform:translateY(30px);opacity:0}to{transform:translateY(0);opacity:1}}
.modal-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px}
.modal-head h3{font-size:17px}
.close-x{width:32px;height:32px;border-radius:50%;border:none;background:var(--bg);color:var(--text);cursor:pointer}

/* toast */
.toast{position:fixed;bottom:calc(90px + env(safe-area-inset-bottom,0px));left:50%;transform:translateX(-50%) translateY(20px);background:var(--text);color:var(--bg);padding:12px 20px;border-radius:99px;font-size:13px;font-weight:600;z-index:60;opacity:0;transition:.25s;pointer-events:none;box-shadow:var(--shadow)}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* bottom nav */
.bottom-nav{position:fixed;bottom:0;left:0;right:0;background:var(--card);border-top:1px solid var(--border);display:flex;max-width:480px;margin:0 auto;z-index:30;padding-bottom:env(safe-area-inset-bottom,0px)}
@media(min-width:900px){.bottom-nav{max-width:1100px}}
.nav-btn{flex:1;border:none;background:transparent;padding:11px 4px 9px;display:flex;flex-direction:column;align-items:center;gap:4px;color:var(--muted);cursor:pointer;font-size:10px;font-weight:600}
.nav-btn i{font-size:17px}
.nav-btn.active{color:var(--green)}
.nav-btn.center{position:relative;top:-16px}
.nav-btn.center .fab{width:52px;height:52px;border-radius:50%;background:linear-gradient(135deg,var(--green),var(--blue));display:flex;align-items:center;justify-content:center;color:#fff;font-size:19px;box-shadow:0 8px 20px rgba(22,160,133,.4)}

/* empty state */
.empty{text-align:center;padding:36px 10px;color:var(--muted)}
.empty i{font-size:30px;margin-bottom:10px;opacity:.5}

h1{font-size:22px;font-weight:800}
h2{font-size:17px;font-weight:700}
::-webkit-scrollbar{display:none}
</style>
</head>
<body>
<div class="app" id="app">

  <!-- AUTH VIEW -->
  <div class="view active" id="view-auth">
    <div class="auth-wrap">
      <div class="auth-logo"><i class="fa-solid fa-heart-pulse"></i></div>
      <h1 style="text-align:center">HealthQ</h1>
      <p class="muted" style="text-align:center;margin-top:4px">Your Smart Health Companion</p>
      <div class="auth-tabs" style="margin-top:24px">
        <button class="active" id="tab-login" onclick="switchAuthTab('login')">Log In</button>
        <button id="tab-signup" onclick="switchAuthTab('signup')">Sign Up</button>
      </div>

      <form id="form-login" onsubmit="return handleLogin(event)">
        <div class="field"><label>Email</label><input type="email" id="li-email" placeholder="you@example.com" required></div>
        <div class="field">
          <label>Password</label>
          <div class="input-wrap">
            <input type="password" id="li-pass" placeholder="••••••••" required minlength="4">
            <i class="fa-regular fa-eye toggle-pass" onclick="togglePass('li-pass',this)"></i>
          </div>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:18px">
          <label class="row"><input type="checkbox" checked> Remember me</label>
          <span class="muted" style="color:var(--blue);cursor:pointer" onclick="toast('Password reset link sent (demo)')">Forgot password?</span>
        </div>
        <button class="btn btn-primary" type="submit" id="login-btn">Log In</button>
      </form>

      <form id="form-signup" style="display:none" onsubmit="return handleSignup(event)">
        <div class="field"><label>Full Name</label><input type="text" id="su-name" required></div>
        <div class="field"><label>Email</label><input type="email" id="su-email" required></div>
        <div class="field"><label>Mobile Number</label><input type="tel" id="su-mobile" required></div>
        <div class="grid2">
          <div class="field"><label>Date of Birth</label><input type="date" id="su-dob" required></div>
          <div class="field"><label>Gender</label><select id="su-gender"><option>Female</option><option>Male</option><option>Other</option></select></div>
        </div>
        <div class="field">
          <label>Password</label>
          <div class="input-wrap"><input type="password" id="su-pass" required minlength="4"><i class="fa-regular fa-eye toggle-pass" onclick="togglePass('su-pass',this)"></i></div>
        </div>
        <div class="field" id="su-confirm-field">
          <label>Confirm Password</label>
          <div class="input-wrap"><input type="password" id="su-confirm" required minlength="4"><i class="fa-regular fa-eye toggle-pass" onclick="togglePass('su-confirm',this)"></i></div>
          <div class="err-msg">Passwords don't match</div>
        </div>
        <label class="row" style="margin-bottom:18px"><input type="checkbox" required> I agree to the Terms &amp; Privacy Policy</label>
        <button class="btn btn-primary" type="submit">Create Account</button>
      </form>

      <div class="divider">or continue with</div>
      <div class="grid2">
        <button class="btn btn-outline" onclick="toast('Google login — placeholder')"><i class="fa-brands fa-google"></i> Google</button>
        <button class="btn btn-outline" onclick="toast('OTP login — placeholder')"><i class="fa-solid fa-key"></i> OTP</button>
      </div>
    </div>
  </div>

  <!-- MAIN APP (post-login) -->
  <div id="main-wrap" style="display:none">
    <div class="topbar">
      <div class="brand"><div class="mark"><i class="fa-solid fa-heart-pulse"></i></div>HealthQ</div>
      <div class="topbar-actions">
        <button class="icon-btn" onclick="openModal('modal-notif')"><i class="fa-regular fa-bell"></i><span class="dot" id="notif-dot"></span></button>
        <button class="icon-btn" onclick="toggleTheme()"><i class="fa-solid fa-circle-half-stroke" id="theme-icon"></i></button>
        <button class="icon-btn" onclick="go('profile')"><i class="fa-regular fa-user"></i></button>
      </div>
    </div>

    <div class="desktop-nav" id="desktop-nav"></div>

    <!-- HOME -->
    <div class="view" id="view-home">
      <h1 id="welcome-name">Welcome Back 👋</h1>
      <p class="muted">Take care of your health.</p>

      <div class="score-card" style="margin-top:16px">
        <div>
          <div style="font-size:12px;opacity:.85;font-weight:600">Today's Health Score</div>
          <div style="font-size:26px;font-weight:800;margin-top:2px">78 / 100</div>
          <div style="font-size:12px;opacity:.9;margin-top:2px">Looking good — stay consistent</div>
        </div>
        <div class="ring" style="--pct:78%"><div class="ring-inner">78%</div></div>
      </div>

      <div class="section-title">Quick Actions</div>
      <div class="qa-grid">
        <div class="qa" onclick="go('ai')"><div class="ic" style="background:linear-gradient(135deg,var(--purple),var(--blue))"><i class="fa-solid fa-robot"></i></div><span>AI Assistant</span></div>
        <div class="qa" onclick="openModal('modal-symptom')"><div class="ic" style="background:linear-gradient(135deg,var(--green),var(--green-dark))"><i class="fa-solid fa-stethoscope"></i></div><span>Symptom Checker</span></div>
        <div class="qa" onclick="go('doctors')"><div class="ic" style="background:linear-gradient(135deg,var(--blue),#2a5bd7)"><i class="fa-solid fa-user-doctor"></i></div><span>Find Doctor</span></div>
        <div class="qa" onclick="go('medicine')"><div class="ic" style="background:linear-gradient(135deg,#E8A33D,#c97f1f)"><i class="fa-solid fa-pills"></i></div><span>Medicine</span></div>
      </div>

      <div class="section-title">Health Overview <span class="pill sample">Sample data</span></div>
      <div class="grid2">
        <div class="card metric">
          <div class="top"><div class="icon" style="background:var(--danger)"><i class="fa-solid fa-heart-pulse"></i></div><span class="muted" style="font-size:11px">Normal</span></div>
          <div class="metric-val">72 <span style="font-size:11px;font-weight:600">BPM</span></div>
          <div class="metric-label">Heart Rate</div>
        </div>
        <div class="card metric">
          <div class="top"><div class="icon" style="background:var(--blue)"><i class="fa-solid fa-droplet"></i></div></div>
          <div class="metric-val">1.5<span style="font-size:11px;font-weight:600">/2.5 L</span></div>
          <div class="metric-label">Water Intake</div>
          <div class="bar"><div style="width:60%;background:var(--blue)"></div></div>
        </div>
        <div class="card metric">
          <div class="top"><div class="icon" style="background:var(--green)"><i class="fa-solid fa-shoe-prints"></i></div></div>
          <div class="metric-val">6,820</div>
          <div class="metric-label">Steps / 10,000</div>
          <div class="bar"><div style="width:68%;background:var(--green)"></div></div>
        </div>
        <div class="card metric">
          <div class="top"><div class="icon" style="background:var(--purple)"><i class="fa-solid fa-moon"></i></div></div>
          <div class="metric-val">7.2<span style="font-size:11px;font-weight:600">hrs</span></div>
          <div class="metric-label">Sleep</div>
          <div class="bar"><div style="width:80%;background:var(--purple)"></div></div>
        </div>
      </div>

      <div class="section-title">Today's Medicine <span class="link" onclick="go('medicine')">View all</span></div>
      <div id="home-med-list" class="card" style="display:flex;flex-direction:column;gap:14px"></div>

      <div class="section-title">Health Tips</div>
      <div class="card" style="margin-bottom:10px">
        <span class="pill">Hydration</span>
        <h2 style="margin-top:8px">Why water matters more than you think</h2>
        <p class="muted" style="margin-top:4px">Staying hydrated supports energy, focus and digestion throughout your day.</p>
      </div>
    </div>

    <!-- HEALTH -->
    <div class="view" id="view-health">
      <h1>Health Tracking</h1>
      <p class="muted">Diet, fitness &amp; vitals — <span class="pill sample" style="margin-left:4px">Sample data</span></p>
      <div class="section-title">Vitals</div>
      <div class="grid2" id="vitals-grid"></div>
      <div class="section-title">Nutrition Today</div>
      <div class="card">
        <div style="display:flex;justify-content:space-between;margin-bottom:10px"><span class="muted">Calories</span><b>1,450 / 2,000 kcal</b></div>
        <div class="bar"><div style="width:72%;background:var(--green)"></div></div>
        <div class="grid2" style="margin-top:16px">
          <div><div class="muted" style="font-size:11.5px">Protein</div><b>62g</b></div>
          <div><div class="muted" style="font-size:11.5px">Carbs</div><b>180g</b></div>
          <div><div class="muted" style="font-size:11.5px">Fat</div><b>40g</b></div>
          <div><div class="muted" style="font-size:11.5px">Water</div><b>1.5L</b></div>
        </div>
      </div>
      <div class="section-title">Fitness</div>
      <div class="grid2">
        <div class="card"><div class="muted" style="font-size:11.5px">Workout</div><b>32 min</b></div>
        <div class="card"><div class="muted" style="font-size:11.5px">Calories Burned</div><b>310 kcal</b></div>
      </div>
    </div>

    <!-- AI ASSISTANT -->
    <div class="view" id="view-ai">
      <h1>HealthQ AI</h1>
      <div class="disclaimer"><i class="fa-solid fa-circle-info"></i> HealthQ AI provides general health information only and cannot diagnose conditions. For emergencies, contact your local emergency service immediately.</div>
      <div id="chat-box" class="chat-box"></div>
      <div id="suggested-wrap">
        <div class="muted" style="font-size:12px;margin-bottom:4px">Try asking:</div>
        <span class="chip" onclick="sendSuggested('I have a headache. What should I do?')">I have a headache. What should I do?</span>
        <span class="chip" onclick="sendSuggested('How much water should I drink?')">How much water should I drink?</span>
        <span class="chip" onclick="sendSuggested('Help me create a healthy routine.')">Help me create a healthy routine.</span>
        <span class="chip" onclick="sendSuggested('Explain my health report.')">Explain my health report.</span>
      </div>
      <div class="chat-input-bar">
        <button class="icon-btn" onclick="toast('Voice input — placeholder')"><i class="fa-solid fa-microphone"></i></button>
        <input type="text" id="chat-input" placeholder="Ask HealthQ AI..." style="flex:1;padding:13px 14px;border-radius:14px;border:1.5px solid var(--border);background:var(--card);color:var(--text)" onkeydown="if(event.key==='Enter')sendChat()">
        <button class="icon-btn" style="background:var(--green);color:#fff" onclick="sendChat()"><i class="fa-solid fa-paper-plane"></i></button>
      </div>
      <div style="display:flex;justify-content:space-between;margin-top:10px">
        <span class="muted" style="font-size:12px;cursor:pointer" onclick="clearChat()"><i class="fa-solid fa-trash"></i> Clear chat</span>
        <select style="border:none;background:transparent;color:var(--muted);font-size:12px" onchange="toast('Language set to '+this.value)">
          <option>English</option><option>Hindi</option>
        </select>
      </div>
    </div>

    <!-- DOCTORS -->
    <div class="view" id="view-doctors">
      <h1>Find a Doctor</h1>
      <div class="input-wrap" style="margin:14px 0">
        <input type="text" id="doc-search" placeholder="Search doctors, specialties..." oninput="renderDoctors()" style="padding-left:38px">
        <i class="fa-solid fa-magnifying-glass" style="position:absolute;left:13px;top:50%;transform:translateY(-50%);color:var(--muted)"></i>
      </div>
      <div style="display:flex;gap:8px;overflow-x:auto;padding-bottom:4px" id="spec-filters"></div>
      <div id="doctor-list" style="display:flex;flex-direction:column;gap:12px;margin-top:16px"></div>
    </div>

    <!-- MEDICINE -->
    <div class="view" id="view-medicine">
      <h1>Medicine Reminder</h1>
      <button class="btn btn-primary" style="margin:14px 0" onclick="openModal('modal-add-med')"><i class="fa-solid fa-plus"></i> Add Medicine</button>
      <div class="section-title" style="margin-top:8px">Today</div>
      <div id="med-list" style="display:flex;flex-direction:column;gap:12px"></div>
    </div>

    <!-- APPOINTMENTS -->
    <div class="view" id="view-appointments">
      <h1>Appointments</h1>
      <div id="appt-list" style="display:flex;flex-direction:column;gap:12px;margin-top:14px"></div>
    </div>

    <!-- PROFILE -->
    <div class="view" id="view-profile">
      <h1>Profile</h1>
      <div class="card" style="display:flex;align-items:center;gap:14px;margin:16px 0">
        <div class="avatar" style="width:60px;height:60px;font-size:20px" id="profile-avatar">U</div>
        <div>
          <h2 id="profile-name">—</h2>
          <p class="muted" id="profile-email" style="font-size:12.5px">—</p>
        </div>
      </div>
      <div class="card" style="display:flex;flex-direction:column">
        <div class="prof-row" onclick="openModal('modal-edit-profile')">Edit Profile <i class="fa-solid fa-chevron-right"></i></div>
        <div class="prof-row" onclick="go('records')">Health Records <i class="fa-solid fa-chevron-right"></i></div>
        <div class="prof-row" onclick="go('reports')">Health Reports <i class="fa-solid fa-chevron-right"></i></div>
        <div class="prof-row" onclick="toast('Language: English')">Language <i class="fa-solid fa-chevron-right"></i></div>
        <div class="prof-row" onclick="openModal('modal-notif')">Notifications <i class="fa-solid fa-chevron-right"></i></div>
        <div class="prof-row" onclick="toast('Privacy settings — placeholder')">Privacy &amp; Security <i class="fa-solid fa-chevron-right"></i></div>
        <div class="prof-row" onclick="go('emergency')">Emergency Contacts <i class="fa-solid fa-chevron-right"></i></div>
      </div>
      <button class="btn btn-danger" style="margin-top:16px" onclick="logout()"><i class="fa-solid fa-right-from-bracket"></i> Logout</button>
      <style>.prof-row{display:flex;justify-content:space-between;align-items:center;padding:14px 4px;border-bottom:1px solid var(--border);font-size:14px;cursor:pointer;color:var(--text)}.prof-row:last-child{border:none}.prof-row i{color:var(--muted);font-size:12px}</style>
    </div>

    <!-- RECORDS -->
    <div class="view" id="view-records">
      <h1>Health Records</h1>
      <div class="card" style="margin-top:14px;display:flex;flex-direction:column;gap:12px">
        <div><div class="muted" style="font-size:11.5px">Blood Group</div><b id="rec-blood">O+</b></div>
        <div><div class="muted" style="font-size:11.5px">Allergies</div><b>None reported</b></div>
        <div><div class="muted" style="font-size:11.5px">Existing Conditions</div><b>None reported</b></div>
        <div><div class="muted" style="font-size:11.5px">Emergency Contact</div><b id="rec-emergency">Not set</b></div>
      </div>
      <button class="btn btn-outline" style="margin-top:14px" onclick="toast('Edit records — placeholder')"><i class="fa-solid fa-pen"></i> Edit Records</button>
    </div>

    <!-- REPORTS -->
    <div class="view" id="view-reports">
      <h1>Health Reports</h1>
      <button class="btn btn-primary" style="margin:14px 0" onclick="toast('Upload — placeholder, connect backend to enable')"><i class="fa-solid fa-upload"></i> Upload Report</button>
      <div class="empty"><i class="fa-solid fa-file-medical"></i><p>No reports uploaded yet.</p></div>
      <div class="disclaimer">AI report analysis is not yet connected. Reports are not medically interpreted until a validated backend is integrated.</div>
    </div>

    <!-- EMERGENCY -->
    <div class="view" id="view-emergency">
      <h1>Emergency Support</h1>
      <div class="card" style="margin-top:14px;text-align:center">
        <i class="fa-solid fa-truck-medical" style="font-size:30px;color:var(--danger)"></i>
        <h2 style="margin-top:10px">Need immediate help?</h2>
        <p class="muted" style="margin:8px 0 16px">Set your local emergency number and contacts below so they're ready when needed.</p>
        <button class="btn btn-danger" onclick="callEmergency()"><i class="fa-solid fa-phone"></i> Emergency</button>
      </div>
      <div class="section-title">Your Emergency Contacts</div>
      <div class="card">
        <div class="field"><label>Country / Region Emergency Number</label><input type="text" id="emg-number" placeholder="e.g. 112" value="Not set"></div>
        <div class="field"><label>Primary Contact Name</label><input type="text" id="emg-name" placeholder="Contact name"></div>
        <div class="field" style="margin-bottom:0"><label>Contact Phone</label><input type="tel" id="emg-phone" placeholder="Phone number"></div>
        <button class="btn btn-primary" style="margin-top:14px" onclick="saveEmergency()">Save</button>
      </div>
    </div>

  </div>

  <div class="bottom-nav" id="bottom-nav" style="display:none">
    <button class="nav-btn active" data-view="home" onclick="go('home')"><i class="fa-solid fa-house"></i>HOME</button>
    <button class="nav-btn" data-view="health" onclick="go('health')"><i class="fa-solid fa-chart-simple"></i>HEALTH</button>
    <button class="nav-btn center" data-view="ai" onclick="go('ai')"><div class="fab"><i class="fa-solid fa-robot"></i></div></button>
    <button class="nav-btn" data-view="doctors" onclick="go('doctors')"><i class="fa-solid fa-user-doctor"></i>DOCTORS</button>
    <button class="nav-btn" data-view="profile" onclick="go('profile')"><i class="fa-regular fa-user"></i>PROFILE</button>
  </div>
</div>

<!-- MODALS -->
<div class="overlay" id="modal-notif" onclick="if(event.target===this)closeModal('modal-notif')">
  <div class="modal">
    <div class="modal-head"><h3>Notifications</h3><button class="close-x" onclick="closeModal('modal-notif')"><i class="fa-solid fa-xmark"></i></button></div>
    <div id="notif-list" style="display:flex;flex-direction:column;gap:10px"></div>
    <button class="btn btn-outline" style="margin-top:14px" onclick="clearNotifs()">Clear All</button>
  </div>
</div>

<div class="overlay" id="modal-symptom" onclick="if(event.target===this)closeModal('modal-symptom')">
  <div class="modal">
    <div class="modal-head"><h3>Symptom Checker</h3><button class="close-x" onclick="closeModal('modal-symptom')"><i class="fa-solid fa-xmark"></i></button></div>
    <div id="symptom-step-select">
      <p class="muted" style="font-size:13px">Select all symptoms you're experiencing</p>
      <div class="symptom-grid" id="symptom-grid"></div>
      <div class="field" style="margin-top:14px"><label>Duration</label><select id="sym-duration"><option>Less than a day</option><option>1-3 days</option><option>More than 3 days</option><option>More than a week</option></select></div>
      <div class="field"><label>Severity</label><select id="sym-severity"><option>Mild</option><option>Moderate</option><option>Severe</option></select></div>
      <div class="field"><label>Age</label><input type="number" id="sym-age" placeholder="Your age" min="0" max="120"></div>
      <button class="btn btn-primary" onclick="checkSymptoms()">Check Symptoms</button>
    </div>
    <div id="symptom-step-result" style="display:none"></div>
  </div>
</div>

<div class="overlay" id="modal-add-med" onclick="if(event.target===this)closeModal('modal-add-med')">
  <div class="modal">
    <div class="modal-head"><h3>Add Medicine</h3><button class="close-x" onclick="closeModal('modal-add-med')"><i class="fa-solid fa-xmark"></i></button></div>
    <div class="field"><label>Medicine Name</label><input type="text" id="med-name" placeholder="e.g. Paracetamol"></div>
    <div class="grid2">
      <div class="field"><label>Dosage</label><input type="text" id="med-dosage" placeholder="e.g. 500mg"></div>
      <div class="field"><label>Frequency</label><select id="med-freq"><option>Once daily</option><option>Twice daily</option><option>3x daily</option></select></div>
    </div>
    <div class="grid2">
      <div class="field"><label>Start Date</label><input type="date" id="med-start"></div>
      <div class="field"><label>End Date</label><input type="date" id="med-end"></div>
    </div>
    <div class="grid2">
      <div class="field"><label>Time</label><input type="time" id="med-time" value="09:00"></div>
      <div class="field"><label>Food</label><select id="med-food"><option>After food</option><option>Before food</option></select></div>
    </div>
    <button class="btn btn-primary" onclick="addMedicine()">Save Medicine</button>
  </div>
</div>

<div class="overlay" id="modal-book" onclick="if(event.target===this)closeModal('modal-book')">
  <div class="modal">
    <div class="modal-head"><h3>Book Appointment</h3><button class="close-x" onclick="closeModal('modal-book')"><i class="fa-solid fa-xmark"></i></button></div>
    <div class="card doc-card" id="book-doc-preview" style="margin-bottom:16px"></div>
    <div class="field"><label>Date</label><input type="date" id="book-date"></div>
    <div class="field"><label>Time</label><select id="book-time"><option>09:00 AM</option><option>11:30 AM</option><option>02:00 PM</option><option>04:30 PM</option></select></div>
    <div class="field" style="margin-bottom:16px"><label>Consultation Type</label>
      <div style="display:flex;gap:8px">
        <button type="button" class="btn btn-outline btn-sm ctype active" data-t="Video" onclick="selectCtype(this)"><i class="fa-solid fa-video"></i> Video</button>
        <button type="button" class="btn btn-outline btn-sm ctype" data-t="Audio" onclick="selectCtype(this)"><i class="fa-solid fa-phone"></i> Audio</button>
        <button type="button" class="btn btn-outline btn-sm ctype" data-t="In-person" onclick="selectCtype(this)"><i class="fa-solid fa-hospital"></i> Visit</button>
      </div>
    </div>
    <button class="btn btn-primary" onclick="confirmBooking()">Confirm Booking</button>
  </div>
</div>

<div class="overlay" id="modal-edit-profile" onclick="if(event.target===this)closeModal('modal-edit-profile')">
  <div class="modal">
    <div class="modal-head"><h3>Edit Profile</h3><button class="close-x" onclick="closeModal('modal-edit-profile')"><i class="fa-solid fa-xmark"></i></button></div>
    <div class="field"><label>Full Name</label><input type="text" id="ep-name"></div>
    <div class="grid2">
      <div class="field"><label>Height (cm)</label><input type="number" id="ep-height" placeholder="170"></div>
      <div class="field"><label>Weight (kg)</label><input type="number" id="ep-weight" placeholder="65"></div>
    </div>
    <div class="field"><label>Blood Group</label>
      <select id="ep-blood"><option>O+</option><option>O-</option><option>A+</option><option>A-</option><option>B+</option><option>B-</option><option>AB+</option><option>AB-</option></select>
    </div>
    <button class="btn btn-primary" onclick="saveProfile()">Save Changes</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
/* ---------- Data / Storage ---------- */
const K = {
  user:'hq_user', theme:'hq_theme', meds:'hq_meds', appts:'hq_appts', notifs:'hq_notifs', logged:'hq_logged_in'
};
function ls_get(k, fallback){ try{ const v = localStorage.getItem(k); return v ? JSON.parse(v) : fallback; }catch(e){ return fallback; } }
function ls_set(k, v){ try{ localStorage.setItem(k, JSON.stringify(v)); }catch(e){} }

const SPECIALTIES = ['General Physician','Cardiologist','Dermatologist','Pediatrician','Dentist','Orthopedic','Gynecologist','Neurologist'];
const SYMPTOMS = ['Fever','Headache','Cough','Cold','Sore throat','Stomach pain','Vomiting','Diarrhea','Dizziness','Fatigue','Chest discomfort','Other'];
const DOCTORS = [
  {id:1,name:'Dr. Anita Rao',spec:'General Physician',exp:'12 yrs',rating:4.8,fee:'$25',time:'Today 4:30 PM'},
  {id:2,name:'Dr. Marcus Lee',spec:'Cardiologist',exp:'15 yrs',rating:4.9,fee:'$60',time:'Tomorrow 10:00 AM'},
  {id:3,name:'Dr. Sara Kim',spec:'Dermatologist',exp:'8 yrs',rating:4.7,fee:'$40',time:'Today 6:00 PM'},
  {id:4,name:'Dr. Priya Nair',spec:'Pediatrician',exp:'10 yrs',rating:4.9,fee:'$30',time:'Tomorrow 9:00 AM'},
  {id:5,name:'Dr. James Cole',spec:'Dentist',exp:'6 yrs',rating:4.6,fee:'$35',time:'Today 2:00 PM'},
  {id:6,name:'Dr. Fatima Al-Sayed',spec:'Gynecologist',exp:'14 yrs',rating:4.8,fee:'$45',time:'Tomorrow 11:30 AM'},
  {id:7,name:'Dr. Rohan Mehta',spec:'Orthopedic',exp:'11 yrs',rating:4.7,fee:'$50',time:'Today 5:00 PM'},
  {id:8,name:'Dr. Elena Petrova',spec:'Neurologist',exp:'17 yrs',rating:4.9,fee:'$70',time:'Tomorrow 1:00 PM'}
];

let selectedSymptoms = new Set();
let selectedSpec = 'All';
let bookingDoctor = null;
let selectedCtype = 'Video';

/* ---------- Theme ---------- */
function applyTheme(){
  const t = ls_get(K.theme, 'auto');
  if(t === 'auto') document.documentElement.removeAttribute('data-theme');
  else document.documentElement.setAttribute('data-theme', t);
}
function toggleTheme(){
  const cur = ls_get(K.theme,'auto');
  const next = cur === 'dark' ? 'light' : (cur === 'light' ? 'auto' : 'dark');
  ls_set(K.theme, next);
  applyTheme();
  toast('Theme: ' + next);
}
applyTheme();

/* ---------- Toast ---------- */
let toastTimer;
function toast(msg){
  const t = document.getElementById('toast');
  t.textContent = msg; t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(()=>t.classList.remove('show'), 2200);
}

/* ---------- Auth ---------- */
function switchAuthTab(tab){
  document.getElementById('tab-login').classList.toggle('active', tab==='login');
  document.getElementById('tab-signup').classList.toggle('active', tab==='signup');
  document.getElementById('form-login').style.display = tab==='login' ? 'block':'none';
  document.getElementById('form-signup').style.display = tab==='signup' ? 'block':'none';
}
function togglePass(id, icon){
  const el = document.getElementById(id);
  const show = el.type === 'password';
  el.type = show ? 'text' : 'password';
  icon.classList.toggle('fa-eye', !show);
  icon.classList.toggle('fa-eye-slash', show);
}
function handleLogin(e){
  e.preventDefault();
  const btn = document.getElementById('login-btn');
  btn.innerHTML = '<span class="spin"></span>'; btn.disabled = true;
  const email = document.getElementById('li-email').value;
  setTimeout(()=>{
    let user = ls_get(K.user, null);
    if(!user){ user = {name: email.split('@')[0], email, mobile:'', gender:'', dob:'', height:'', weight:'', blood:'O+'}; ls_set(K.user, user); }
    else { user.email = email; ls_set(K.user, user); }
    ls_set(K.logged, true);
    btn.innerHTML = 'Log In'; btn.disabled = false;
    enterApp();
  }, 700);
  return false;
}
function handleSignup(e){
  e.preventDefault();
  const pass = document.getElementById('su-pass').value;
  const confirm = document.getElementById('su-confirm').value;
  const field = document.getElementById('su-confirm-field');
  if(pass !== confirm){ field.classList.add('error'); return false; }
  field.classList.remove('error');
  const user = {
    name: document.getElementById('su-name').value,
    email: document.getElementById('su-email').value,
    mobile: document.getElementById('su-mobile').value,
    dob: document.getElementById('su-dob').value,
    gender: document.getElementById('su-gender').value,
    height:'', weight:'', blood:'O+'
  };
  ls_set(K.user, user); ls_set(K.logged, true);
  toast('Account created!');
  enterApp();
  return false;
}
function logout(){
  ls_set(K.logged, false);
  document.getElementById('main-wrap').style.display = 'none';
  document.getElementById('bottom-nav').style.display = 'none';
  document.getElementById('view-auth').classList.add('active');
  toast('Logged out');
}

/* ---------- Navigation ---------- */
const VIEWS = ['home','health','ai','doctors','medicine','appointments','profile','records','reports','emergency'];
const NAV_LABELS = {home:'Home',health:'Health',ai:'AI Assistant',doctors:'Doctors',medicine:'Medicine',profile:'Profile'};
function go(view){
  VIEWS.forEach(v=>{
    const el = document.getElementById('view-'+v);
    if(el) el.classList.toggle('active', v===view);
  });
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.toggle('active', b.dataset.view===view));
  document.querySelectorAll('#desktop-nav button').forEach(b=>b.classList.toggle('active', b.dataset.view===view));
  window.scrollTo(0,0);
}
function buildDesktopNav(){
  const el = document.getElementById('desktop-nav');
  el.innerHTML = Object.keys(NAV_LABELS).map(v=>`<button data-view="${v}" onclick="go('${v}')">${NAV_LABELS[v]}</button>`).join('');
}

/* ---------- App init ---------- */
function enterApp(){
  document.getElementById('view-auth').classList.remove('active');
  document.getElementById('main-wrap').style.display = 'block';
  document.getElementById('bottom-nav').style.display = 'flex';
  const user = ls_get(K.user, {name:'User'});
  document.getElementById('welcome-name').textContent = `Welcome Back, ${user.name.split(' ')[0]} 👋`;
  document.getElementById('profile-name').textContent = user.name;
  document.getElementById('profile-email').textContent = user.email || '';
  document.getElementById('profile-avatar').textContent = (user.name||'U').charAt(0).toUpperCase();
  document.getElementById('rec-blood').textContent = user.blood || 'O+';
  buildDesktopNav();
  renderVitals();
  renderMedicine();
  renderDoctorFilters();
  renderDoctors();
  renderNotifs();
  renderAppts();
  go('home');
}

/* ---------- Vitals ---------- */
function renderVitals(){
  const items = [
    {label:'Blood Pressure', val:'118/76', unit:'mmHg', icon:'fa-heart', color:'var(--danger)'},
    {label:'Blood Sugar', val:'92', unit:'mg/dL', icon:'fa-droplet', color:'var(--blue)'},
    {label:'Oxygen Level', val:'98', unit:'%', icon:'fa-lungs', color:'var(--green)'},
    {label:'BMI', val:'22.4', unit:'normal', icon:'fa-weight-scale', color:'var(--purple)'},
    {label:'Temperature', val:'98.4', unit:'°F', icon:'fa-thermometer-half', color:'#E8A33D'},
    {label:'Calories', val:'1,450', unit:'kcal', icon:'fa-fire', color:'var(--danger)'}
  ];
  document.getElementById('vitals-grid').innerHTML = items.map(i=>`
    <div class="card metric">
      <div class="top"><div class="icon" style="background:${i.color}"><i class="fa-solid ${i.icon}"></i></div></div>
      <div class="metric-val">${i.val} <span style="font-size:11px;font-weight:600">${i.unit}</span></div>
      <div class="metric-label">${i.label}</div>
    </div>`).join('');
}

/* ---------- Medicine ---------- */
function seedMeds(){
  return [
    {id:1,name:'Vitamin D3',dosage:'1000 IU',time:'09:00',food:'After food',status:'pending'},
    {id:2,name:'Metformin',dosage:'500mg',time:'13:00',food:'After food',status:'pending'},
    {id:3,name:'Omega-3',dosage:'1 capsule',time:'20:00',food:'After food',status:'pending'}
  ];
}
function renderMedicine(){
  let meds = ls_get(K.meds, null);
  if(!meds){ meds = seedMeds(); ls_set(K.meds, meds); }
  const rowHTML = m => `
    <div class="med-row">
      <div class="med-icon"><i class="fa-solid fa-pills"></i></div>
      <div style="flex:1">
        <b style="font-size:14px">${m.name}</b>
        <div class="muted" style="font-size:11.5px">${m.dosage} • ${m.time} • ${m.food}</div>
      </div>
      <div class="med-actions">
        <button class="circle-btn ${m.status==='taken'?'taken':''}" onclick="setMedStatus(${m.id},'taken')" title="Taken"><i class="fa-solid fa-check"></i></button>
        <button class="circle-btn" onclick="setMedStatus(${m.id},'skipped')" title="Skip"><i class="fa-solid fa-xmark"></i></button>
        <button class="circle-btn" onclick="deleteMed(${m.id})" title="Delete"><i class="fa-solid fa-trash"></i></button>
      </div>
    </div>`;
  document.getElementById('med-list').innerHTML = meds.length ? meds.map(rowHTML).join('') : `<div class="empty"><i class="fa-solid fa-pills"></i><p>No medicines added yet.</p></div>`;
  document.getElementById('home-med-list').innerHTML = meds.length ? meds.slice(0,2).map(rowHTML).join('') : `<div class="empty"><i class="fa-solid fa-pills"></i><p>No medicines scheduled.</p></div>`;
}
function setMedStatus(id, status){
  let meds = ls_get(K.meds, []);
  meds = meds.map(m => m.id===id ? {...m, status} : m);
  ls_set(K.meds, meds); renderMedicine();
  toast(status==='taken' ? 'Marked as taken' : 'Marked as skipped');
}
function deleteMed(id){
  let meds = ls_get(K.meds, []).filter(m=>m.id!==id);
  ls_set(K.meds, meds); renderMedicine();
}
function addMedicine(){
  const name = document.getElementById('med-name').value.trim();
  if(!name){ toast('Enter a medicine name'); return; }
  let meds = ls_get(K.meds, []);
  meds.push({
    id: Date.now(),
    name, dosage: document.getElementById('med-dosage').value || '—',
    time: document.getElementById('med-time').value || '09:00',
    food: document.getElementById('med-food').value, status:'pending'
  });
  ls_set(K.meds, meds); renderMedicine(); closeModal('modal-add-med');
  toast('Medicine added');
  ['med-name','med-dosage'].forEach(id=>document.getElementById(id).value='');
  if(Notification && Notification.permission === 'default') Notification.requestPermission();
}

/* ---------- Doctors ---------- */
function renderDoctorFilters(){
  const el = document.getElementById('spec-filters');
  const all = ['All', ...SPECIALTIES];
  el.innerHTML = all.map(s=>`<button class="btn btn-sm ${s===selectedSpec?'btn-primary':'btn-outline'}" style="white-space:nowrap" onclick="filterSpec('${s}')">${s}</button>`).join('');
}
function filterSpec(s){ selectedSpec = s; renderDoctorFilters(); renderDoctors(); }
function renderDoctors(){
  const q = (document.getElementById('doc-search').value || '').toLowerCase();
  const list = DOCTORS.filter(d =>
    (selectedSpec==='All' || d.spec===selectedSpec) &&
    (d.name.toLowerCase().includes(q) || d.spec.toLowerCase().includes(q))
  );
  const el = document.getElementById('doctor-list');
  if(!list.length){ el.innerHTML = `<div class="empty"><i class="fa-solid fa-magnifying-glass"></i><p>No doctors found.</p></div>`; return; }
  el.innerHTML = list.map(d=>`
    <div class="card doc-card">
      <div class="avatar">${d.name.split(' ').map(n=>n[0]).slice(0,2).join('')}</div>
      <div style="flex:1">
        <b style="font-size:14.5px">${d.name}</b>
        <div class="muted" style="font-size:12px">${d.spec} • ${d.exp}</div>
        <div style="display:flex;align-items:center;gap:6px;margin-top:3px">
          <span class="stars"><i class="fa-solid fa-star"></i> ${d.rating}</span>
          <span class="muted" style="font-size:11.5px">• ${d.fee} • ${d.time}</span>
        </div>
      </div>
      <button class="btn btn-primary btn-sm" onclick='openBooking(${JSON.stringify(d)})'>Book</button>
    </div>`).join('');
}
function openBooking(doc){
  bookingDoctor = doc;
  document.getElementById('book-doc-preview').innerHTML = `
    <div class="avatar">${doc.name.split(' ').map(n=>n[0]).slice(0,2).join('')}</div>
    <div><b>${doc.name}</b><div class="muted" style="font-size:12px">${doc.spec} • ${doc.fee}</div></div>`;
  document.querySelectorAll('.ctype').forEach(b=>b.classList.toggle('active', b.dataset.t==='Video'));
  selectedCtype = 'Video';
  const d = new Date(); d.setDate(d.getDate()+1);
  document.getElementById('book-date').value = d.toISOString().slice(0,10);
  openModal('modal-book');
}
function selectCtype(btn){
  document.querySelectorAll('.ctype').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active'); selectedCtype = btn.dataset.t;
}
function confirmBooking(){
  if(!bookingDoctor) return;
  let appts = ls_get(K.appts, []);
  appts.push({
    id: Date.now(), doctor: bookingDoctor.name, spec: bookingDoctor.spec,
    date: document.getElementById('book-date').value,
    time: document.getElementById('book-time').value,
    type: selectedCtype, status:'Confirmed'
  });
  ls_set(K.appts, appts);
  closeModal('modal-book'); renderAppts();
  toast('Appointment booked!');
  go('appointments');
}
function renderAppts(){
  const appts = ls_get(K.appts, []);
  const el = document.getElementById('appt-list');
  if(!appts.length){ el.innerHTML = `<div class="empty"><i class="fa-regular fa-calendar"></i><p>No appointments yet. Book one from Find Doctor.</p></div>`; return; }
  el.innerHTML = appts.map(a=>`
    <div class="card">
      <div style="display:flex;justify-content:space-between;align-items:flex-start">
        <div><b>${a.doctor}</b><div class="muted" style="font-size:12px">${a.spec}</div></div>
        <span class="pill">${a.status}</span>
      </div>
      <div style="display:flex;gap:14px;margin:10px 0;font-size:12.5px" class="muted">
        <span><i class="fa-regular fa-calendar"></i> ${a.date}</span>
        <span><i class="fa-regular fa-clock"></i> ${a.time}</span>
        <span><i class="fa-solid fa-${a.type==='Video'?'video':a.type==='Audio'?'phone':'hospital'}"></i> ${a.type}</span>
      </div>
      <div style="display:flex;gap:8px">
        <button class="btn btn-outline btn-sm" onclick="toast('Reschedule — placeholder')">Reschedule</button>
        <button class="btn btn-danger btn-sm" onclick="cancelAppt(${a.id})">Cancel</button>
      </div>
    </div>`).join('');
}
function cancelAppt(id){
  let appts = ls_get(K.appts, []).filter(a=>a.id!==id);
  ls_set(K.appts, appts); renderAppts(); toast('Appointment cancelled');
}

/* ---------- AI Chat ---------- */
let sampleClient = null;
let chatHistory = [];
const AI_SYSTEM_PROMPT = "You are the HealthQ in-app assistant. Give brief, friendly, general health information and self-care tips. You are not a doctor: never diagnose, and for anything that sounds urgent or emergency-related, clearly tell the user to contact local emergency services or a healthcare professional right away. Keep replies to a few sentences.";
async function initSample(){
  if (typeof claude === 'undefined' || !claude.use) return;
  try { sampleClient = await claude.use('sample'); } catch(e) { sampleClient = null; }
}
function renderChatMsg(text, who){
  const box = document.getElementById('chat-box');
  const div = document.createElement('div');
  div.className = 'msg ' + who;
  div.textContent = text;
  box.appendChild(div);
  box.scrollIntoView({block:'end'});
  return div;
}
function sendSuggested(q){ document.getElementById('chat-input').value = q; sendChat(); }
function clearChat(){ document.getElementById('chat-box').innerHTML=''; toast('Chat cleared'); }
function fakeAIResponse(q){
  q = q.toLowerCase();
  if(q.includes('emergency') || q.includes('chest pain') || q.includes('can\'t breathe')){
    return "If this could be a medical emergency, please contact your local emergency service or seek immediate medical care right away.";
  }
  if(q.includes('headache')){
    return "Headaches are often linked to dehydration, stress, or lack of sleep. Try resting in a quiet, dark room, drinking water, and gentle neck stretches. If it's severe, sudden, or comes with vision changes or fever, please see a doctor.";
  }
  if(q.includes('water')){
    return "A common general guideline is around 2-2.5 liters (8-10 cups) a day for adults, though needs vary with activity, climate, and body size. Your Health Overview shows today's intake.";
  }
  if(q.includes('routine')){
    return "A simple healthy routine: consistent sleep/wake times, 7-9 hours of sleep, 30 min of movement, balanced meals with vegetables and protein, and regular hydration. I can help tailor this further — tell me your current schedule.";
  }
  if(q.includes('report')){
    return "I can help explain general terms once you upload a report in Health Reports. Note: I provide general information only, not a medical interpretation — always confirm findings with your doctor.";
  }
  return "Thanks for sharing that. I can offer general health information, but I'm not able to diagnose conditions. Could you tell me a bit more about your symptoms or question? For anything urgent, please contact a healthcare professional.";
}
async function sendChat(){
  const input = document.getElementById('chat-input');
  const text = input.value.trim();
  if(!text) return;
  document.getElementById('suggested-wrap').style.display = 'none';
  renderChatMsg(text, 'user');
  chatHistory.push({role:'user', content:text});
  input.value = '';
  const box = document.getElementById('chat-box');
  const typing = document.createElement('div');
  typing.className = 'msg ai typing';
  typing.innerHTML = '<span></span><span></span><span></span>';
  box.appendChild(typing);
  box.scrollIntoView({block:'end'});

  if(sampleClient){
    try{
      const transcript = chatHistory.map(m=>(m.role==='user'?'User: ':'Assistant: ')+m.content).join('\n');
      const res = await sampleClient(AI_SYSTEM_PROMPT + '\n\nConversation so far:\n' + transcript + '\nAssistant:', {modelTier:'quick'});
      typing.remove();
      const answer = (res && res.text) ? res.text.trim() : fakeAIResponse(text);
      renderChatMsg(answer, 'ai');
      chatHistory.push({role:'assistant', content:answer});
    }catch(err){
      typing.remove();
      const fallback = fakeAIResponse(text);
      renderChatMsg(fallback, 'ai');
      chatHistory.push({role:'assistant', content:fallback});
    }
  } else {
    setTimeout(()=>{
      typing.remove();
      const answer = fakeAIResponse(text);
      renderChatMsg(answer, 'ai');
      chatHistory.push({role:'assistant', content:answer});
    }, 900);
  }
}

/* ---------- Symptom Checker ---------- */
function renderSymptomGrid(){
  document.getElementById('symptom-grid').innerHTML = SYMPTOMS.map(s=>
    `<div class="sym-chip" onclick="toggleSymptom(this,'${s}')">${s}</div>`).join('');
}
function toggleSymptom(el, s){
  el.classList.toggle('sel');
  if(selectedSymptoms.has(s)) selectedSymptoms.delete(s); else selectedSymptoms.add(s);
}
function checkSymptoms(){
  if(selectedSymptoms.size===0){ toast('Select at least one symptom'); return; }
  const severity = document.getElementById('sym-severity').value;
  const emergency = selectedSymptoms.has('Chest discomfort') || severity==='Severe';
  document.getElementById('symptom-step-select').style.display = 'none';
  const resEl = document.getElementById('symptom-step-result');
  resEl.style.display = 'block';
  resEl.innerHTML = `
    <div class="disclaimer">This is general information, not a diagnosis.</div>
    <h2>Possible General Explanation</h2>
    <p class="muted" style="margin:8px 0">Based on ${Array.from(selectedSymptoms).join(', ').toLowerCase()}, this combination is commonly associated with common colds, viral infections, or stress-related causes. It could also reflect something else entirely — only a clinician can confirm.</p>
    <h2 style="margin-top:14px">Self-care</h2>
    <p class="muted" style="margin:8px 0">Rest, stay hydrated, and monitor your symptoms. Over-the-counter relief may help mild discomfort — check with a pharmacist for suitability.</p>
    <h2 style="margin-top:14px">Warning Signs — Seek Care If</h2>
    <p class="muted" style="margin:8px 0">Symptoms worsen rapidly, last more than a few days, or are accompanied by high fever, difficulty breathing, or severe pain.</p>
    <h2 style="margin-top:14px">Recommended Specialist</h2>
    <p class="muted" style="margin:8px 0">${selectedSymptoms.has('Chest discomfort') ? 'Cardiologist / Emergency Care' : 'General Physician'}</p>
    ${emergency ? `<div class="emergency-banner"><i class="fa-solid fa-triangle-exclamation"></i> If you think this is a medical emergency, contact your local emergency service or seek immediate medical care.</div>` : ''}
    <div style="display:flex;gap:8px;margin-top:16px">
      <button class="btn btn-outline" onclick="resetSymptomChecker()">Check Again</button>
      <button class="btn btn-primary" onclick="closeModal('modal-symptom');go('doctors')">Find Doctor</button>
    </div>`;
}
function resetSymptomChecker(){
  selectedSymptoms.clear();
  document.getElementById('symptom-step-select').style.display = 'block';
  document.getElementById('symptom-step-result').style.display = 'none';
  renderSymptomGrid();
}

/* ---------- Notifications ---------- */
function seedNotifs(){
  return [
    {id:1,icon:'fa-pills',text:'Time to take Vitamin D3 (09:00)',read:false},
    {id:2,icon:'fa-calendar-check',text:'Appointment reminder: tomorrow 10:00 AM',read:false},
    {id:3,icon:'fa-droplet',text:"You're behind on today's water goal",read:false},
    {id:4,icon:'fa-lightbulb',text:'New health tip: 5 ways to sleep better',read:true}
  ];
}
function renderNotifs(){
  let notifs = ls_get(K.notifs, null);
  if(!notifs){ notifs = seedNotifs(); ls_set(K.notifs, notifs); }
  const el = document.getElementById('notif-list');
  el.innerHTML = notifs.length ? notifs.map(n=>`
    <div class="card" style="display:flex;gap:12px;align-items:center;padding:12px;${n.read?'opacity:.55':''}" onclick="markRead(${n.id})">
      <div class="med-icon"><i class="fa-solid ${n.icon}"></i></div>
      <div style="flex:1;font-size:13px">${n.text}</div>
      ${!n.read?'<span class="dot" style="position:static;width:7px;height:7px;background:var(--danger);border-radius:50%"></span>':''}
    </div>`).join('') : `<div class="empty"><i class="fa-regular fa-bell"></i><p>No notifications</p></div>`;
  document.getElementById('notif-dot').style.display = notifs.some(n=>!n.read) ? 'block':'none';
}
function markRead(id){
  let notifs = ls_get(K.notifs, []).map(n=> n.id===id?{...n,read:true}:n);
  ls_set(K.notifs, notifs); renderNotifs();
}
function clearNotifs(){ ls_set(K.notifs, []); renderNotifs(); toast('Notifications cleared'); }

/* ---------- Profile edit ---------- */
function saveProfile(){
  const user = ls_get(K.user, {});
  user.name = document.getElementById('ep-name').value || user.name;
  user.height = document.getElementById('ep-height').value;
  user.weight = document.getElementById('ep-weight').value;
  user.blood = document.getElementById('ep-blood').value;
  ls_set(K.user, user);
  document.getElementById('profile-name').textContent = user.name;
  document.getElementById('profile-avatar').textContent = (user.name||'U').charAt(0).toUpperCase();
  document.getElementById('rec-blood').textContent = user.blood;
  closeModal('modal-edit-profile');
  toast('Profile updated');
}

/* ---------- Emergency ---------- */
function saveEmergency(){
  const num = document.getElementById('emg-number').value;
  const name = document.getElementById('emg-name').value;
  const phone = document.getElementById('emg-phone').value;
  ls_set('hq_emergency', {num,name,phone});
  document.getElementById('rec-emergency').textContent = name && phone ? `${name} — ${phone}` : 'Not set';
  toast('Emergency contact saved');
}
function callEmergency(){
  const e = ls_get('hq_emergency', null);
  if(!e || !e.num || e.num==='Not set'){ toast('Please set your local emergency number first'); return; }
  toast('Calling ' + e.num + ' (demo)');
}

/* ---------- Modals ---------- */
function openModal(id){ document.getElementById(id).classList.add('active'); if(id==='modal-symptom') resetSymptomChecker(); }
function closeModal(id){ document.getElementById(id).classList.remove('active'); }

/* ---------- Boot ---------- */
window.addEventListener('DOMContentLoaded', ()=>{
  initSample();
  renderSymptomGrid();
  if(ls_get(K.logged, false)){ enterApp(); }
  const ee = ls_get('hq_emergency', null);
  if(ee) document.getElementById('emg-number').value = ee.num;
});
</script>
</body>
</html>
