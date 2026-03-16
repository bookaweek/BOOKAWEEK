<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="BOOKAWEEK">
<meta name="theme-color" content="#0A2A66">
<title>BOOKAWEEK</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
:root {
  --navy:#0A2A66; --navy2:#1B3D80; --blue:#1547B0;
  --gold:#F2B705; --gold-l:#FFF3CC; --gold-m:#FAD95C;
  --teal:#0D7A6E; --teal-l:#D4F0EB;
  --purple:#6B3FA0; --purple-l:#EDE0FF;
  --orange:#E07B39; --orange-l:#FCE8D8;
  --red:#C0392B; --green:#1A7A3C;
  --white:#FFFFFF; --off-w:#F8F9FF;
  --lgray:#EEF0F8; --mgray:#E0E0E8; --dgray:#2C2C3A; --cgray:#8899AA;
  --input-h:56px; --radius:14px;
  --shadow:0 8px 32px rgba(10,42,102,0.14);
}
html { -webkit-text-size-adjust:100%; }
body { font-family:'DM Sans',sans-serif; background:var(--navy); min-height:100vh; overflow-x:hidden; }
body::before {
  content:''; position:fixed; inset:0; pointer-events:none; z-index:0;
  background:
    radial-gradient(ellipse 80% 60% at 20% 10%,rgba(242,183,5,0.07) 0%,transparent 60%),
    radial-gradient(ellipse 60% 80% at 80% 90%,rgba(13,122,110,0.07) 0%,transparent 60%),
    repeating-linear-gradient(45deg,transparent,transparent 40px,rgba(255,255,255,0.012) 40px,rgba(255,255,255,0.012) 41px);
}

/* ── LAYOUT ── */
.app { position:relative; z-index:1; max-width:480px; margin:0 auto; padding-bottom:100px; }

/* ── HEADER ── */
.header { padding:44px 22px 22px; position:relative; }
.header::after { content:''; position:absolute; bottom:0; left:22px; right:22px; height:1px; background:linear-gradient(90deg,transparent,var(--gold),transparent); }
.logo-row { display:flex; align-items:center; gap:11px; margin-bottom:16px; }
.logo-mark { width:42px; height:42px; background:var(--gold); border-radius:10px; display:flex; align-items:center; justify-content:center; font-size:20px; flex-shrink:0; box-shadow:0 4px 16px rgba(242,183,5,0.4); }
.brand-name { font-family:'Playfair Display',serif; font-size:19px; font-weight:900; color:var(--white); letter-spacing:.04em; }
.brand-tag  { font-size:10px; color:var(--gold); letter-spacing:.12em; font-weight:600; text-transform:uppercase; margin-top:1px; }
.date-badge { display:inline-flex; align-items:center; gap:6px; background:rgba(255,255,255,0.06); border:1px solid rgba(242,183,5,0.2); border-radius:20px; padding:5px 12px; font-size:12px; color:rgba(255,255,255,0.7); margin-bottom:14px; }
.date-badge span { color:var(--gold); font-weight:600; }
.member-greeting { font-family:'Playfair Display',serif; font-size:26px; font-weight:900; color:var(--white); line-height:1.1; margin-bottom:4px; }
.member-greeting em { color:var(--gold); font-style:normal; }
.member-sub { font-size:13px; color:rgba(255,255,255,0.5); }

/* ── MODE SWITCHER ── */
.mode-bar { display:grid; grid-template-columns:1fr 1fr 1fr; gap:8px; margin:20px 16px 0; }
.mode-btn {
  height:54px; border:2px solid rgba(255,255,255,0.1); background:rgba(255,255,255,0.05);
  border-radius:14px; cursor:pointer; display:flex; flex-direction:column;
  align-items:center; justify-content:center; gap:3px; transition:all .2s;
  -webkit-tap-highlight-color:transparent;
}
.mode-btn .m-icon { font-size:18px; }
.mode-btn .m-label { font-size:10px; font-weight:700; color:rgba(255,255,255,0.5); letter-spacing:.06em; text-transform:uppercase; }
.mode-btn.active { border-color:var(--gold); background:rgba(242,183,5,0.12); }
.mode-btn.active .m-label { color:var(--gold); }
.mode-btn.sunday-locked { opacity:0.4; cursor:not-allowed; }

/* ── CARD ── */
.card { margin:16px 16px 0; background:var(--white); border-radius:20px; padding:22px 18px; box-shadow:var(--shadow); }
.card + .card { margin-top:12px; }
.card-title { font-size:11px; font-weight:700; letter-spacing:.14em; text-transform:uppercase; color:var(--cgray); margin-bottom:14px; display:flex; align-items:center; gap:8px; }
.card-title::before { content:''; width:4px; height:13px; background:var(--gold); border-radius:2px; flex-shrink:0; }

/* ── FIELDS ── */
.field { margin-bottom:13px; }
.field:last-child { margin-bottom:0; }
.field label { display:block; font-size:12px; font-weight:600; color:var(--navy); margin-bottom:6px; letter-spacing:.03em; }
.req { color:var(--gold); margin-left:2px; }
.field input,.field select,.field textarea {
  width:100%; height:var(--input-h); padding:0 16px;
  background:var(--off-w); border:2px solid var(--lgray); border-radius:12px;
  font-family:'DM Sans',sans-serif; font-size:16px; color:var(--dgray);
  outline:none; -webkit-appearance:none; appearance:none;
  transition:border-color .2s, background .2s, box-shadow .2s;
}
.field textarea { height:auto; min-height:88px; padding:14px 16px; resize:none; line-height:1.55; }
.field input:focus,.field select:focus,.field textarea:focus {
  border-color:var(--navy); background:var(--white); box-shadow:0 0 0 4px rgba(10,42,102,0.08);
}
.field select {
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='7' viewBox='0 0 12 7'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%230A2A66' stroke-width='2' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
  background-repeat:no-repeat; background-position:right 16px center; padding-right:40px; cursor:pointer;
}
.two-col { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-bottom:13px; }
.two-col .field { margin-bottom:0; }

/* ── STARS ── */
.stars { display:flex; gap:7px; margin-top:3px; }
.star-btn { flex:1; height:50px; border:2px solid var(--lgray); background:var(--off-w); border-radius:10px; font-size:20px; cursor:pointer; display:flex; align-items:center; justify-content:center; transition:all .15s; -webkit-tap-highlight-color:transparent; }
.star-btn.on { border-color:var(--gold); background:var(--gold-l); transform:scale(1.05); }

/* ── REST TOGGLE ── */
.rest-row { display:flex; align-items:center; gap:11px; padding:14px 16px; background:var(--off-w); border:2px solid var(--lgray); border-radius:12px; cursor:pointer; -webkit-tap-highlight-color:transparent; transition:all .2s; }
.rest-row.on { border-color:var(--orange); background:#FFF5EE; }
.tog-track { width:42px; height:24px; background:var(--lgray); border-radius:12px; position:relative; transition:background .2s; flex-shrink:0; }
.rest-row.on .tog-track { background:var(--orange); }
.tog-thumb { position:absolute; top:3px; left:3px; width:18px; height:18px; background:var(--white); border-radius:50%; transition:transform .2s; box-shadow:0 2px 5px rgba(0,0,0,.15); }
.rest-row.on .tog-thumb { transform:translateX(18px); }
.tog-lbl { font-size:14px; font-weight:500; color:var(--dgray); }

/* ── STAT CARDS (weekly auto-fill) ── */
.stat-strip { display:grid; grid-template-columns:1fr 1fr 1fr; gap:8px; margin-bottom:14px; }
.stat-mini { background:var(--off-w); border-radius:10px; padding:10px 8px; text-align:center; border:1px solid var(--lgray); }
.stat-mini .sv { font-family:'Playfair Display',serif; font-size:22px; font-weight:900; color:var(--navy); }
.stat-mini .sl { font-size:9px; font-weight:700; letter-spacing:.08em; color:var(--cgray); text-transform:uppercase; margin-top:2px; }

/* ── BOOK LIST (library mode) ── */
.book-list { display:flex; flex-direction:column; gap:8px; margin-bottom:14px; }
.book-item { display:flex; align-items:center; gap:10px; padding:12px 14px; background:var(--off-w); border-radius:12px; border:1px solid var(--lgray); }
.book-item .bi-num { width:26px; height:26px; background:var(--navy); border-radius:6px; display:flex; align-items:center; justify-content:center; font-size:11px; font-weight:700; color:var(--gold); flex-shrink:0; }
.book-item .bi-info { flex:1; min-width:0; }
.book-item .bi-title { font-size:13px; font-weight:600; color:var(--navy); white-space:nowrap; overflow:hidden; text-overflow:ellipsis; }
.book-item .bi-author { font-size:11px; color:var(--cgray); margin-top:1px; }
.book-item .bi-del { width:28px; height:28px; border:none; background:none; font-size:16px; cursor:pointer; color:var(--cgray); flex-shrink:0; -webkit-tap-highlight-color:transparent; display:flex; align-items:center; justify-content:center; }
.book-item .bi-del:hover { color:var(--red); }
.empty-lib { text-align:center; padding:24px; color:var(--cgray); font-size:13px; line-height:1.6; }
.empty-lib .el-icon { font-size:32px; margin-bottom:8px; display:block; }

/* ── PROGRESS ── */
.prog-bar { margin:14px 16px 0; height:3px; background:rgba(255,255,255,0.1); border-radius:2px; overflow:hidden; }
.prog-fill { height:100%; background:linear-gradient(90deg,var(--gold),var(--orange)); border-radius:2px; width:0%; transition:width .4s cubic-bezier(.34,1.56,.64,1); }

/* ── SUBMIT ── */
.submit-wrap { margin:20px 16px 0; }
.submit-btn { width:100%; height:60px; background:linear-gradient(135deg,var(--navy),var(--blue)); border:none; border-radius:18px; color:var(--gold); font-family:'Playfair Display',serif; font-size:17px; font-weight:700; letter-spacing:.04em; cursor:pointer; position:relative; overflow:hidden; box-shadow:0 8px 24px rgba(10,42,102,.35); -webkit-tap-highlight-color:transparent; transition:transform .15s; }
.submit-btn::before { content:''; position:absolute; inset:0; background:linear-gradient(135deg,rgba(242,183,5,0.14),transparent 60%); pointer-events:none; }
.submit-btn:active { transform:scale(.98); }
.submit-btn:disabled { opacity:.55; cursor:not-allowed; transform:none; }
.btn-inner { display:flex; align-items:center; justify-content:center; gap:9px; }
.spinner { width:20px; height:20px; border:3px solid rgba(242,183,5,.3); border-top-color:var(--gold); border-radius:50%; animation:spin .7s linear infinite; display:none; }
@keyframes spin { to { transform:rotate(360deg); } }

/* ── ERROR ── */
.err-box { display:none; background:rgba(192,57,43,.1); border:1px solid rgba(192,57,43,.28); border-radius:10px; padding:11px 14px; font-size:13px; color:#E07070; margin:10px 16px 0; text-align:center; }
.err-box.show { display:block; }

/* ── SUCCESS ── */
.success { display:none; position:fixed; inset:0; background:var(--navy); z-index:200; flex-direction:column; align-items:center; justify-content:center; padding:40px 28px; text-align:center; }
.success.show { display:flex; animation:fadeIn .35s ease; }
@keyframes fadeIn { from{opacity:0} to{opacity:1} }
.s-icon { width:90px; height:90px; background:linear-gradient(135deg,var(--gold),#F5C842); border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:44px; margin-bottom:28px; box-shadow:0 0 0 14px rgba(242,183,5,.1),0 0 0 28px rgba(242,183,5,.05); animation:popIn .55s cubic-bezier(.34,1.56,.64,1) .15s both; }
@keyframes popIn { from{transform:scale(0);opacity:0} to{transform:scale(1);opacity:1} }
.s-title { font-family:'Playfair Display',serif; font-size:32px; font-weight:900; color:var(--white); margin-bottom:10px; }
.s-title span { color:var(--gold); }
.s-msg { font-size:15px; color:rgba(255,255,255,.6); line-height:1.6; max-width:280px; margin-bottom:28px; }
.s-stats { background:rgba(255,255,255,.06); border-radius:14px; border:1px solid rgba(242,183,5,.18); padding:18px 24px; width:100%; max-width:300px; margin-bottom:28px; }
.s-row { display:flex; justify-content:space-between; align-items:center; padding:7px 0; border-bottom:1px solid rgba(255,255,255,.06); }
.s-row:last-child { border-bottom:none; }
.s-lbl { font-size:12px; color:rgba(255,255,255,.45); }
.s-val { font-size:14px; color:var(--gold); font-weight:700; }
.again-btn { width:100%; max-width:300px; height:52px; border:2px solid rgba(242,183,5,.35); background:transparent; border-radius:14px; color:var(--gold); font-family:'DM Sans',sans-serif; font-size:14px; font-weight:600; cursor:pointer; letter-spacing:.05em; -webkit-tap-highlight-color:transparent; }

/* ── QUOTE ── */
.quote { margin:16px 16px 0; padding:14px 18px; border-left:3px solid var(--gold); background:rgba(255,255,255,.04); border-radius:0 12px 12px 0; }
.q-text { font-family:'Playfair Display',serif; font-size:13px; font-style:italic; color:rgba(255,255,255,.65); line-height:1.6; }
.q-auth { font-size:10px; color:var(--gold); font-weight:600; letter-spacing:.08em; margin-top:5px; }
.footer { text-align:center; padding:24px; font-size:11px; color:rgba(255,255,255,.2); letter-spacing:.06em; }

/* ── MEMBER SELECT SCREEN ── */
.member-screen { position:fixed; inset:0; background:var(--navy); z-index:150; display:flex; flex-direction:column; align-items:center; justify-content:center; padding:32px 24px; }
.member-screen.hidden { display:none; }
.ms-logo { width:60px; height:60px; background:var(--gold); border-radius:14px; display:flex; align-items:center; justify-content:center; font-size:28px; margin-bottom:24px; box-shadow:0 6px 24px rgba(242,183,5,.45); }
.ms-title { font-family:'Playfair Display',serif; font-size:28px; font-weight:900; color:var(--white); margin-bottom:8px; text-align:center; }
.ms-sub { font-size:14px; color:rgba(255,255,255,.5); text-align:center; margin-bottom:32px; line-height:1.5; }
.ms-grid { display:grid; grid-template-columns:1fr 1fr; gap:10px; width:100%; max-width:340px; }
.ms-btn { height:64px; border:2px solid rgba(255,255,255,.1); background:rgba(255,255,255,.05); border-radius:16px; color:var(--white); font-family:'DM Sans',sans-serif; font-size:15px; font-weight:600; cursor:pointer; transition:all .2s; -webkit-tap-highlight-color:transparent; display:flex; align-items:center; justify-content:center; gap:8px; }
.ms-btn:hover,.ms-btn:active { border-color:var(--gold); background:rgba(242,183,5,.1); color:var(--gold); }
.ms-btn .ms-initial { width:32px; height:32px; background:var(--navy2); border-radius:8px; display:flex; align-items:center; justify-content:center; font-size:14px; font-weight:900; color:var(--gold); flex-shrink:0; }

/* ── BOOK MODE SPECIFIC ── */
.month-badge { display:inline-flex; align-items:center; gap:6px; background:rgba(13,122,110,.15); border:1px solid rgba(13,122,110,.3); border-radius:20px; padding:4px 12px; font-size:11px; font-weight:600; color:var(--teal); letter-spacing:.06em; text-transform:uppercase; margin-bottom:14px; }

/* ── WEEKLY UNLOCK MSG ── */
.unlock-msg { margin:16px 16px 0; background:rgba(255,255,255,.05); border:1px solid rgba(242,183,5,.15); border-radius:16px; padding:20px; text-align:center; }
.unlock-msg .um-icon { font-size:32px; margin-bottom:10px; display:block; }
.unlock-msg .um-title { font-family:'Playfair Display',serif; font-size:18px; font-weight:700; color:var(--white); margin-bottom:6px; }
.unlock-msg .um-sub { font-size:13px; color:rgba(255,255,255,.5); line-height:1.5; }
.um-days { display:flex; gap:6px; justify-content:center; margin-top:14px; }
.um-day { width:32px; height:32px; border-radius:8px; background:rgba(255,255,255,.05); border:1px solid rgba(255,255,255,.1); display:flex; align-items:center; justify-content:center; font-size:10px; font-weight:700; color:rgba(255,255,255,.3); letter-spacing:.02em; }
.um-day.done { background:rgba(13,122,110,.2); border-color:var(--teal); color:var(--teal); }
.um-day.today { background:rgba(242,183,5,.15); border-color:var(--gold); color:var(--gold); }

  /* ── HEADER LOGO ── */
  .logo-img-wrap {
    width: 48px; height: 48px; flex-shrink: 0;
    position: relative;
    animation: logoEntrance 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) both;
  }
  @keyframes logoEntrance {
    from { transform: scale(0) rotate(-15deg); opacity: 0; }
    to   { transform: scale(1) rotate(0deg);   opacity: 1; }
  }
  .logo-img {
    width: 48px; height: 48px;
    border-radius: 12px;
    object-fit: contain;
    filter: drop-shadow(0 4px 12px rgba(242,183,5,0.45));
    transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), filter 0.3s;
    cursor: pointer;
  }
  .logo-img:hover {
    transform: scale(1.12) rotate(3deg);
    filter: drop-shadow(0 6px 18px rgba(242,183,5,0.65));
  }
  .logo-img:active { transform: scale(0.95); }

  /* ── SPLASH SCREEN LOGO ── */
  .ms-logo-wrap {
    position: relative;
    width: 100px; height: 100px;
    margin-bottom: 28px;
    display: flex; align-items: center; justify-content: center;
  }
  .ms-logo-img {
    width: 80px; height: 80px;
    border-radius: 18px;
    object-fit: contain;
    position: relative; z-index: 2;
    filter: drop-shadow(0 6px 20px rgba(242,183,5,0.5));
    animation: splashLogo 0.9s cubic-bezier(0.34, 1.56, 0.64, 1) both;
  }
  @keyframes splashLogo {
    0%   { transform: scale(0) rotate(-20deg); opacity: 0; }
    60%  { transform: scale(1.1) rotate(3deg);  opacity: 1; }
    100% { transform: scale(1) rotate(0deg);    opacity: 1; }
  }
  .ms-logo-ring {
    position: absolute; border-radius: 50%;
    border: 2px solid rgba(242,183,5,0.25);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    animation: ringPulse 2.4s ease-out infinite;
  }
  .ms-ring1 { width: 90px;  height: 90px;  animation-delay: 0s;    animation-duration: 2.4s; }
  .ms-ring2 { width: 112px; height: 112px; animation-delay: 0.4s;  animation-duration: 2.4s; }
  .ms-ring3 { width: 134px; height: 134px; animation-delay: 0.8s;  animation-duration: 2.4s; }
  @keyframes ringPulse {
    0%   { opacity: 0.7; transform: translate(-50%, -50%) scale(0.85); }
    70%  { opacity: 0.1; transform: translate(-50%, -50%) scale(1);    }
    100% { opacity: 0;   transform: translate(-50%, -50%) scale(1.05); }
  }

  /* ── PAGE LOAD ANIMATION FOR MAIN APP ── */
  .header       { animation: fadeSlideDown 0.6s cubic-bezier(0.16, 1, 0.3, 1) 0.1s both; }
  .mode-bar     { animation: fadeSlideUp   0.6s cubic-bezier(0.16, 1, 0.3, 1) 0.2s both; }
  #mode-daily   { animation: fadeSlideUp   0.6s cubic-bezier(0.16, 1, 0.3, 1) 0.3s both; }
  @keyframes fadeSlideDown {
    from { opacity: 0; transform: translateY(-16px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── GOLD SHIMMER ON SUCCESS ICON ── */
  .s-icon {
    animation: popIn .55s cubic-bezier(0.34,1.56,0.64,1) .15s both, shimmer 3s ease 1s infinite;
  }
  @keyframes shimmer {
    0%, 100% { box-shadow: 0 0 0 14px rgba(242,183,5,0.1), 0 0 0 28px rgba(242,183,5,0.05); }
    50%       { box-shadow: 0 0 0 18px rgba(242,183,5,0.18), 0 0 0 36px rgba(242,183,5,0.08); }
  }

</style>
</head>
<body>

<!-- MEMBER SELECT SCREEN -->
<div class="member-screen" id="memberScreen">
  <div class="ms-logo-wrap" id="splashLogo">
    <img src="data:image/png;base64,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" class="ms-logo-img" alt="BOOKAWEEK" />
    <div class="ms-logo-ring ms-ring1"></div>
    <div class="ms-logo-ring ms-ring2"></div>
    <div class="ms-logo-ring ms-ring3"></div>
  </div>
  <div class="ms-title">Who's reading today?</div>
  <div class="ms-sub">Select your name to open your personal tracker</div>
  <div class="ms-grid">
    <button class="ms-btn" onclick="selectMember('Dorcas')"><div class="ms-initial">D</div> Dorcas</button>
    <button class="ms-btn" onclick="selectMember('Haliyah')"><div class="ms-initial">H</div> Haliyah</button>
    <button class="ms-btn" onclick="selectMember('Jesulayomi')"><div class="ms-initial">J</div> Jesulayomi</button>
    <button class="ms-btn" onclick="selectMember('Juliet')"><div class="ms-initial">J</div> Juliet</button>
    <button class="ms-btn" onclick="selectMember('Motolani')" style="grid-column:1/-1"><div class="ms-initial">M</div> Motolani</button>
  </div>
</div>

<!-- MAIN APP -->
<div class="app" id="mainApp" style="display:none">

  <!-- HEADER -->
  <div class="header">
    <div class="logo-row">
      <div class="logo-img-wrap" id="headerLogo">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAHgAAAB4CAYAAAA5ZDbSAAAViElEQVR4nO2ceXxU1dnHf8+5y2zJBAIEgiIWEWsWFIOUImWgtdZ+tLbWDm51f0kIFgVt6/J5dZi2b91aNwQSqm1d0aRaqXWrFUm1iksskEVUXJAlkJCQZCYzmZl7zvP+MRMIGCpUJcn7nu8ffMKdc8+99/zOc87znPPcC2g0Go1Go9FoNBqNRqPRaDQajUaj0Wg0Go1Go9FoNBqNRnMIYWbq73vQfEkwgwCAtMT/9+CqoAEAzz909YyKe0IzACAUCon+vSvNF8JLLwVMAHjh/guGvfzkT/75m8W/mQDo4XrQEwqFRI+4Kx+5buS6lWe+/UrV6fcBALO23kFLKATxUigtLAD8s/r8b619fObGNx6dmnqrqvQIABQKQQs82GAG9cy1APDSynnj36j6ztK1j5VwXfWx/OIDp1wIELS4g5CqXsLWrCgf82rVd25+/ZGSyOanCvj1+4/tePGPp1wCEKqCMP5dPQOZQewwBA0ECghYDdTMVECYAfABnkwcAlEY6pmq+SOGq/euJqf1ytzcmLupJZFIOf5Hm2TxbeeVPtgQDP7Irq6GBKrll/gwXxqDWOC+CBoIAqiuVtiP2MwgEEAAv/LYGXNsbrkr1xvz7Gh33utWQx5tlRMem33ZHxuBdAB8oD1moDLYBCYAPH7K+f7tXVm/ZBKdBtQGYaI+y+19b8uaO+K7SwaDxr5Cp8VN//PyIzMf8Ln5glhX5FGinGXTzl/1GhGlAOCu+eNdt7014+iuuFXsSBwLxvDRfv817756W6TnHg7xc//HmJ9dZKAQEkAhAbOV4R+SxdHUHBgujyRAKoW2SFfUV1i2yhTioSG5eU9tqg53p88LGpnhlRYtCtEiJn7p0VNXguSIXWrMkVuL79uZu+XmkUSFNHbqxed1xF1nXL+KAxD2KAgLIAY7sVRnQt4IIAowAYsICKv+bI0DZbBZMABg2LRLs+PtZiMYXtMU8xXzeFY8CYSpEPYolqldJMSSYYTbP6lbtgsIiaqqQpo9e7Zc/cSCUDzpZH33nKU/e63q1IuzPLHbEsr9+LTyaXe4h2/f4EgnSkyvgvAv26KNiaT6FRhWbo7v6C1r7mjr72c/WAaLBdPoEy8/Gm4Vn/PNvK33Pd/oxDDEJUgkInUVj/SMl6FQSNz9RFNhStCZivn8VtBlWUXlv4jWhytmzwaeefBU/7qP5dteMf6NN/804xk3bf2u7XQj2u2LJbeN2TRizJapY8i3fk1mqI8yKKtwzo1MlG24lGJmGjt54ai4SvpazhjxIcID34oHugUTAC4pOd27oXv0OkDkM2iH38OLIjH5P4rJGuLFUU1Z+UnUrAZQ4/Q+Mauo/DQF3ECQ71wyyzV38eLFiTf+umCcK1W/yuZPxrbHuruzPS5XWzx3yYwfvz5/z+QaMBGYifHxNm9TNFGvmLM8LlGaSOJmJgwncHRk/tDCD/9+SwcG+Jw8KIL3DiPHBLNg4fIZpFZ52a5RTLYgyNElJSnUhB2gRgIgICQQCJgMIFK/7Omu+mVTDcK637+UuuGaay44gmJrn7Xk5rHtkXiK2DKJDCJhCACYU1pipeuokagJO3mjuhgERSCf122sFQIvQbhzwBAy1T3QjQPAIBHYjiYVgxwiYhZizYe1d38CsA0imZW/rbf1MBBWqMlYcjBoAEyRuuV3dkXMh/L85pU+a9eE9q5uKQyvBQa4Zz8QwMkn1+7ldbfuBAAQCMbW15dtBLiGCAyAWXq0wF8UpunqaXRiVn4GKO3eMs3EzP2fWF0tAeIbQkEbm+7ZMLNg66uOo9gUBggqHQyDQaLv3V6XL9kjOM+ZU2GxghcDf1rbi0EhcCKrU4A4fa8KShzknLeoEBJg6ozFJJMkJgYTA5zuKor7Fs1yebnnQvn5EzjdKwYXg0Jgo93F4LSoImNthPS+bFPTewdoUcQGbDAb6VBWEQgEwQzBqs8OY3l8PZu/3FjY0qsMkXISPT/9Zw91iBgUAvcaooGMsCAi/CfDJRPAmYkUDGKCQaJPlVzNbcwMBgjBXsf3NuOBPWIPCoGdoYk9rdiTUcHMDIhXdm07iBaWIGaQyoy2xFDg/Q7RHo+fCWCARUNDQ3rex76Npi34cyNTCUKPCESZFqWD2T3aTboihgGCxQJEBCn6Fjg+spNAPVPB6N1lGKwMl1I9NQ5kBoXAhuVKq7IXLIhIBgtmHrDjI1gxCwUYlI6QKDPS76ebJGK5lBFwrxIECB0mfYGYu3rPwcTp2ZcIzHTgThZAyiJAgKEUIEmyVAzA4H87EjDQkzqbccYY2sn6Iom52SDaE6tyeqlBMYDag6nIkGCHmZksyX5HCLcN5Sg+gGbofR0mSD1Ef4EYZiQTtAK7vehMLnrJQdSTIlZej6CkGvIRsqdNdcSoB7OzPIIpkeqrfKy9RaAPBQkQMiEybact+HMjnexPh0Rpg0570YGACQQ/81lYkr+te9h2HjLl9KlnLqvtzg9d2tSeV6PgP2zvkkGBQMi0XN5MmAScnj9hLyXF7tBNW/DnxmOzgZ5xlDntPjMSDFh+dBrptedqmU4KCH46QS5YrQCgpc3zdn378d+b8YPKxsrKEmvWrFlOzPWNH2zuKl6BQMisrg4iXUe1RE3YGZHjMgmwACSbmt4jZjGw1eyDQbEfHE+S7IlBAUEcgvBVww/D5VnfEHs9u6jsKcu0H25bG25Ml+lJUE/v12Y2CDD7yucagecQCkGUldWmGCA6M9wO4HEgaFRnEuvyJpePiyf4rJfXJmezsA4nlnj33W1Gehkszd5O1sDVfVBYMADsDpOYicJQQmAJKacWhGJlZl+fcFSDr7Bs5ZDjywNpYcNqX2tmBoVCIREOpxejCOBAIGCmx/9qmVtS+rWsorIV0Tg+UEbWrQwxmZRcB8LSmppwN7B7SZMHyxA9KCxYySSBfemAlZBTUBCyG+vDPyMAxd++2rdpR/RUh/kSkHVGiq0zfEXlj/vc+HnzW8s+TFtzOqU2bcnh3TtTQIhqasLOuJNKj2jupF8lUu4LQArEyecM1fVHf7b7ha2ZNJ2S00u9H3wiRiV3a9zRH01x0Azs7pfJlhhXEszZER/yNpM5FiyjAJoJaAZRAwm85bKtl785btiHr23uHLErGpvLLP4bRLBIlnbUVf4Oe56zl7hpCx56fOlF3Y6oBEyXgHNHnsu+8+Zrpm+9/KbVX+l2nJOUEl8HqyIQRjMjDxBuItWS47WKtr25pDXt1dOAdaUHhcAlJ5fmbGjCRgjPcMAByAQgAJEZgVUKLLvbCLTSNPCQ10MdkRhdoci+0FCJezvrlpYSLaI91hsiorDKLpp7m0PunxoqsdLvo5uScVhxJc9h5rMg3KNg2JndYAmwArMDIgOQidhQv3dMOglPC/y5CYVC4vYndnyHQVlg5QhmmwlehhjJrMYx0zFgLiLLmwthgFNdWyzLuIukSiXZWCTIeb6rruIczszJhGqZVTR3uYR5vm06txIjlkihjCzvUWAGO12dBG4gEhsAfADCTkEUUeAkKzKFQV2nHjPrmerq2QP+bYdBIfCBMH7KfH9rIlmccjCTgbNguCex071DCH5TsThNgO+JNlReAQD+otIbHDZ+QXCeA4wCCNcRrOKNglBlCfNFn9fVuHXNHW0D1iwPgsEjcDBooLmZkJfHaG4m9KTq1DQysPcbDATAP3HuJEfhclZ8Hkh4SFiwRffpliFao0njNbACWHULIZ5wmbizbe2yN/cRlNILHgWZNlqN3dfOy+N0OtDAZ/AI/NlkBGkm1NRIZAQfUVJ6VCwhrmI25gBOhMBxJvswAecBl8u8qbX2ng27awgETNTkMVClBvK8ejAMBoH/Xd7x/n4jIEQIrBY9GZa5E0u/1i3F7wD2mRbmdq6tfCFdNGACeTxY3x4cDPSsCFE6zTVDINArRg+JPatTwF7lPv3/Pjpt+vexgYvcBYF5Wb2O7bPGvZ+lzv0bAvXx92AwmkMBU49o+SWl3r5K5JeUer0nzhvV6xD12k3C8JIF+Xt+CgmUlFoAgEDIRM/XcEpKrd7X2lMP9nSMQOjTCz6ZY4dPXejpfT97Lpeub+TEH/t2X7cgaO+ud6+6++/bHv3U20KioADmJ7T9dsU0RQg8zUwnmAIPddQtqwaArKKyGwHkQRhbWPHXDchfdtYvfwsAfIXlZxPk98mw3lLKmWUwPdzZUPGov7jsXEmuq4i7/9RVt/wWb0Hp/YJo28gx9qKNzy1OAmBfQemfLGH8or1+WV1WcenPmXw/EhxbEqmrvD+ruPQbpGhSpKHy7pzjymemJJfZJi1LJtVNgngzBNWy4oDX7boilkiWMWimATwGMo5lJWsNkzY47LqFVPfT0fqKsK+obCmBktkudX1TbWW8r+yQL5v+6VkBiMbGcJLBrWSYJ0brK8KAbHJgVAGAr7D010rxtbbXvj66funNrORHEtY/cqfM9/smzv0mhPEoCXF3ZP2S24n5D9Jwr8guLJ9GAq9B2JNJGS97CsuOg6Ck7aR+vTG+XgJgf1HpZLJzznIgLwDAhqDHADVZSRwFgJVEuQJuBsBSOkow1revXVYD5skMikbrKm8VQlRKJ9nNzJ0EcWKkvuK3bskLDOLtlik3EBknEqu3s48vO5oY2eQYv2yqXd4v4gL9vNlAoCSUlP6ism8DmCRk8lYCwEw/JaL7295Y3AmEhElYDGF5UjHnDHbUfJbJjyJ1FWuAoNHVsPwJlvGIhLpcmC7FTlxCqFMIfEXXsFHlre/+PpL2jEGKcSJS0SrF4pLcKfP9HesqP4YTe56JL8wvCXkJGAqy3P7COSeC6BgBegFpd7qVwa6c4nnfAhG3ravcSoANJZ3sifO+Fjf4vI76yj8nu+FVTsxRRFNUiq/Pdo8qi2xY0pp53H7xyvt3N4lZADAA5IFoFwvjiJGT5o0FkQniaNrhWcSmcCWgHIfBh4NoOIE70/NqAQMAMXcQkGsqx4ZyDKX4YoY4b2j71mPSF6pW2cVzJzBRMRn8IJneYcl48myAiQzzPkAcEUnsCAtT3MMy8Y7D4hYAeZ2ctw5AJsueciVhunLkhPS9QzCRYIXjwSqQPiYJLImZz2GIC7viW4oAAMHPTkb4suhXgRVxAqyczvrKh7MEXQgr55yYVF8nlmvBmJEOXYgd1Z0Pw2UKk14Ecy1IFBOIgbCaEQiZEObhxFwjpOokYTu2ZZcT+J2kdD0ZDFYZAFhBnUwQ21mRCSe2VkleCBBn2/JpsGxWUs696syRzwii+8n2zwLQjMZwEpn8eDA3RNcvDWfbrgeGl5TmM3EnlCOj9Usro/WV5+ccV3YkyGCQyZZhXQtW/5DCs/LwqQs96UWR/vlCXv84WYGQiRooX0FTJUzvf9kUn56U4vtMxoVeOzkpkRRjFeMFAbqCGWuY1b1M+DDWUHnBsEmXj+5OqX8A6m9CmHcqmboKZEwZPixvWntb83Rp+l+gZPtFpptXJ1OeTZCJlbYwbkgq53deNk5uaVwa9ReVzldW7t1w2udE6yru9RaUrSBif1fD8tN8E+cWQdLrpqkKO9ZVfuyfujBXRmKtzFxjgn4uCfMMwjOScQIM9zUWJ2Y4RCMg1VnCxF2K/K9zqnNBlkErosraAjivkUueFa3NbzvILwF9IfRbzDb+1Pmups2JHzAZXpBigpHwcWJVc/19OwAg57iyIx1FpxEZklhuitRVPNvzvY0RBfOy4iTPFsJ0s3IiucO7qzbV3N+dNbF0umL3UQaSzZG6imf9BZdNUcI+ASyblTD9HpP+1jq+eUf2u0MnS3iOIRlPTB6e//jbHdu/woAVXVvZiEDI9Ldun9WpRtWgEY6/oGWcY9BJxI4DBUWCc+ws31OpzniJJJFDLB0Slh+cqjcMiqXYPVGoWCTasPwJX/HFxUQ5023RXdO2trJxoO88HSKY+oxLv7BY8pDFpANiwaN/biIUEgiHla+g7FwyXZMgEzttn12R9pp7+HRv9xeV/YQM/LVjXeUmBAKGv6NgkpLibLDqNETqwY71936EgqCNxupkTnF5iWT1YwFqk6Se7KpbXtfXrWQdV3ZStsn/aqrN7+7ZL/YVly0g2DZxojlSv/wP+5zymZ9syCoqD0SP3fkKqqtl5nNO/bYM2j8CZx7aW1C6wjbspSmV+jYDUSJ8LMiaCU4+KECjpLC/ZyF1u5Q4TArzh1CpyaZh/ahj/T0fAYCvYM5CIUwSROskOxeaJO6Vwj6XZGK1VHwaEdwkRLNU6ikBcRRIFLKBZXC4iIRxiiDnBSk5TEL8Nlq3bDkQEgg2krdh6N8t2/WwcBINDvBVIpFQij2moPccmEGo1DoBXi1JXEek3hckNjHUR0qShwSNV0zXClLXEijJwj6ZVPLvkbqKv2TShw7pO8b940U3N2deBUHEIboEzAUGqAmKFxLRdiY6S4GGgslIOmqegrrIkPHriPC+Eqndw7cQRgeDAg7LciKxKqnUDQDvVEzTQfiYgScU1AYCZoJVkEi1CikXEOT3XcnYApP4ZQK/6SN+Ml1jWKGggAnokhAWw+gShufPUuFhwxQfpqRaKIi6QZgkiW4l4qcsGxVSqRKCGMKMo5mVV7B62rJdbyilFglW28A4PVP//5OFjry8dPxKiAmhVhDRJmHyZiLxlhJiiMs0nlXM00HMJGgzkVijDM91zOwWir6RXTT3UgBgsAWip8B4GcRMRH9hFocLA08TxGZhGDFAwICxjgnvMVnZbo97CRN9lHBn35gEjmTG1hhwjr947vXDJl06GuFFLAgOpJMrSZ0AlZxNxHcqxccZglYpVvlkiDUE8SAzfc9J4DKC8U8p+VwS4ocG6B0Flqlk6lQQnmGYh5EwHk8/eOiQj5j96ggMm/az7NZXb4sgEDJz423etjfujmRPvProyDGbPxjRMMKTNOy8EXG5dePGxYnsiVdNEBxvMbMTjtOVbXSsu6s9v6TU2zRuVwLV1TKv6LKRzfX37fCX/PQosyPRkjseiVS8k2ItPrOlcWl0/Pj5rh1ea2xk/e3vA0DWpCu/GvUPeR8tEDnW9tEesru2G4l21C5PZZWUDod05QmSSVvYXTtr72zKKikdHq1dvjNn4k++IgVFo2sXtwyZNG9swknKeN29W4YWlo8hU6m2dZXbRk682puUsdxdDcs2Z0+8aoLb6d7W0rg02p9t3Z8cSCf7rDJf8lZdX55372P79cwHhCfdn/QWZs++8O5jvO9x2rtsX/uxvO9v+9aHPsrt++4T7XO9fevv4+9Pld33fjQajUaj0Wg0Go1Go9FoNBqNRqPRaDQajUaj0Wg0Go1Go9FoNBqNRqPRaDQajUaj0Wg0Go1Go9FoNBqNRqPRaDQajUaj0Wg0mn7lfwFaUPp9krfMvgAAAABJRU5ErkJggg==" class="logo-img" alt="BOOKAWEEK" />
      </div>
      <div>
        <div class="brand-name">BOOKAWEEK</div>
        <div class="brand-tag">Read · Reflect · Execute</div>
      </div>
    </div>
    <div class="date-badge"><span id="dayName">Monday</span> · <span id="fullDate">—</span></div>
    <div class="member-greeting">Hey, <em id="greetName">—</em> 👋</div>
    <div class="member-sub" id="greetSub">What are you reading today?</div>
  </div>

  <!-- MODE BAR -->
  <div class="mode-bar">
    <button class="mode-btn active" id="btn-daily" onclick="setMode('daily')">
      <span class="m-icon">📅</span>
      <span class="m-label">Daily Log</span>
    </button>
    <button class="mode-btn" id="btn-books" onclick="setMode('books')">
      <span class="m-icon">📚</span>
      <span class="m-label">My Books</span>
    </button>
    <button class="mode-btn" id="btn-weekly" onclick="setMode('weekly')">
      <span class="m-icon">📆</span>
      <span class="m-label">Weekly</span>
    </button>
  </div>
  <div class="prog-bar"><div class="prog-fill" id="progFill"></div></div>

  <!-- ═══ DAILY MODE ═══ -->
  <div id="mode-daily">
    <form id="dailyForm" novalidate>
      <div class="card">
        <div class="card-title">Session Type</div>
        <div class="rest-row" id="restRow" onclick="toggleRest()">
          <div class="tog-track"><div class="tog-thumb"></div></div>
          <span class="tog-lbl" id="restLbl">Mark as Rest Day</span>
        </div>
      </div>

      <div id="dailyReadFields">
        <div class="card">
          <div class="card-title">What are you reading?</div>
          <div class="field">
            <label for="d-book">Book <span class="req">*</span></label>
            <select id="d-book" name="book">
              <option value="" disabled selected>Select from your library...</option>
            </select>
          </div>
          <div class="field">
            <label for="d-mod">BOOKAWEEK Module</label>
            <select id="d-mod" name="module">
              <option value="—">— Not a module session</option>
              <option value="M1">M1: Brain &amp; Discipline</option>
              <option value="M2">M2: Identity Shift</option>
              <option value="M3">M3: Environment Architecture</option>
              <option value="M4">M4: Book Selection</option>
              <option value="M5">M5: Reading Speed</option>
              <option value="M6">M6: Anti-Distraction</option>
              <option value="M7">M7: Memory Architecture</option>
              <option value="M8">M8: Notes System</option>
              <option value="M9">M9: Reading to Execute</option>
              <option value="M10">M10: 52-Book Blueprint</option>
              <option value="M11">M11: Competitive Advantage</option>
              <option value="M12">M12: Lifelong Reader</option>
            </select>
          </div>
          <div class="two-col">
            <div class="field"><label for="d-mins">Minutes <span class="req">*</span></label><input type="number" id="d-mins" placeholder="25" min="1" max="480" inputmode="numeric"></div>
            <div class="field"><label for="d-pages">Pages</label><input type="number" id="d-pages" placeholder="20" min="0" max="999" inputmode="numeric"></div>
          </div>
        </div>

        <div class="card">
          <div class="card-title">Read. Reflect. Execute.</div>
          <div class="field"><label for="d-insight">Key Insight <span class="req">*</span></label><textarea id="d-insight" placeholder="The most important thing you learned today..."></textarea></div>
          <div class="field"><label for="d-action">Action Committed</label><textarea id="d-action" placeholder="One specific thing you will do because of this..." style="min-height:72px;"></textarea></div>
        </div>

        <div class="card">
          <div class="card-title">Rate This Session</div>
          <div class="stars" id="starsRow">
            <button type="button" class="star-btn" onclick="setStar(1)">⭐</button>
            <button type="button" class="star-btn" onclick="setStar(2)">⭐</button>
            <button type="button" class="star-btn" onclick="setStar(3)">⭐</button>
            <button type="button" class="star-btn" onclick="setStar(4)">⭐</button>
            <button type="button" class="star-btn" onclick="setStar(5)">⭐</button>
          </div>
        </div>
      </div>

      <div class="err-box" id="dailyErr"></div>
      <div class="submit-wrap">
        <button type="submit" class="submit-btn" id="dailySubmit">
          <div class="btn-inner"><span id="dIcon">📖</span><span id="dTxt">Log My Session</span><div class="spinner" id="dSpin"></div></div>
        </button>
      </div>
    </form>
  </div>

  <!-- ═══ BOOKS MODE ═══ -->
  <div id="mode-books" style="display:none">
    <div style="margin:16px 16px 0;">
      <div class="month-badge">📅 <span id="currentMonth">March 2026</span> — Your Reading Library</div>
    </div>

    <div class="card">
      <div class="card-title">Your Books This Month</div>
      <div class="book-list" id="bookList">
        <div class="empty-lib"><span class="el-icon">📖</span>No books added yet.<br>Add the books you're reading this month below.</div>
      </div>
    </div>

    <div class="card">
      <div class="card-title">Add a New Book</div>
      <div class="field"><label for="b-title">Book Title <span class="req">*</span></label><input type="text" id="b-title" placeholder="e.g. Atomic Habits" autocomplete="off"></div>
      <div class="field"><label for="b-author">Author</label><input type="text" id="b-author" placeholder="e.g. James Clear" autocomplete="off"></div>
      <div class="two-col">
        <div class="field">
          <label for="b-status">Status</label>
          <select id="b-status">
            <option value="Reading">📖 Reading</option>
            <option value="Completed">✅ Completed</option>
            <option value="Next Up">📌 Next Up</option>
          </select>
        </div>
        <div class="field">
          <label for="b-cat">Category</label>
          <select id="b-cat">
            <option value="Business">Business</option>
            <option value="Leadership">Leadership</option>
            <option value="Psychology">Psychology</option>
            <option value="Finance">Finance</option>
            <option value="Biography">Biography</option>
            <option value="Philosophy">Philosophy</option>
            <option value="Science">Science</option>
            <option value="Self-Help">Self-Help</option>
            <option value="Strategy">Strategy</option>
            <option value="Other">Other</option>
          </select>
        </div>
      </div>

      <!-- Completed book extra fields -->
      <div id="completedFields" style="display:none">
        <div class="two-col">
          <div class="field"><label for="b-pages">Total Pages</label><input type="number" id="b-pages" placeholder="280" inputmode="numeric"></div>
          <div class="field"><label for="b-rating">Rating (1-5)</label><input type="number" id="b-rating" placeholder="5" min="1" max="5" inputmode="numeric"></div>
        </div>
        <div class="field"><label for="b-insight">Top Insight</label><textarea id="b-insight" placeholder="The single most valuable thing you took from this book..." style="min-height:72px;"></textarea></div>
        <div class="field"><label for="b-action">Action Committed</label><textarea id="b-action" placeholder="What will you do differently because of this book?" style="min-height:72px;"></textarea></div>
        <div class="field">
          <label for="b-rec">Recommend?</label>
          <select id="b-rec">
            <option value="⭐⭐⭐⭐⭐ Must Read">⭐⭐⭐⭐⭐ Must Read</option>
            <option value="⭐⭐⭐⭐ Recommended">⭐⭐⭐⭐ Recommended</option>
            <option value="⭐⭐⭐ Good">⭐⭐⭐ Good</option>
            <option value="⭐⭐ OK">⭐⭐ OK</option>
            <option value="⭐ Skip">⭐ Skip</option>
          </select>
        </div>
      </div>

      <div class="err-box" id="bookErr"></div>
      <div style="margin-top:14px">
        <button type="button" class="submit-btn" id="bookSubmit" onclick="submitBook()">
          <div class="btn-inner"><span id="bIcon">➕</span><span id="bTxt">Add to My Library</span><div class="spinner" id="bSpin"></div></div>
        </button>
      </div>
    </div>
  </div>

  <!-- ═══ WEEKLY MODE ═══ -->
  <div id="mode-weekly" style="display:none">

    <!-- Locked state (not Sunday) -->
    <div class="unlock-msg" id="weeklyLocked" style="display:none">
      <span class="um-icon">🔒</span>
      <div class="um-title">Weekly Reflection</div>
      <div class="um-sub">Your weekly reflection unlocks every <strong style="color:var(--gold)">Sunday</strong>.<br>Keep logging your daily sessions — see you then!</div>
      <div class="um-days" id="weekDays"></div>
    </div>

    <!-- Unlocked (Sunday or debug) -->
    <div id="weeklyUnlocked">
      <div class="card">
        <div class="card-title">This Week's Numbers</div>
        <div class="stat-strip">
          <div class="stat-mini"><div class="sv" id="w-days">—</div><div class="sl">Days Read</div></div>
          <div class="stat-mini"><div class="sv" id="w-mins">—</div><div class="sl">Minutes</div></div>
          <div class="stat-mini"><div class="sv" id="w-pages">—</div><div class="sl">Pages</div></div>
        </div>
        <div style="font-size:11px;color:var(--cgray);text-align:center;">Auto-calculated from your daily logs this week</div>
      </div>

      <form id="weeklyForm" novalidate>
        <div class="card">
          <div class="card-title">Weekly Reflection</div>
          <div class="field"><label for="w-book">Best Book This Week</label>
            <select id="w-book"><option value="" disabled selected>Select...</option></select>
          </div>
          <div class="field"><label for="w-insight">Top Insight of the Week <span class="req">*</span></label><textarea id="w-insight" placeholder="What's the single most powerful thing you learned this week?"></textarea></div>
          <div class="field"><label for="w-commit">Execution Commitment <span class="req">*</span></label><textarea id="w-commit" placeholder="What will you do differently next week because of what you read?" style="min-height:76px;"></textarea></div>
          <div class="field"><label for="w-reflect">Reflection</label><textarea id="w-reflect" placeholder="How did this week go? What's working? What needs to change?" style="min-height:76px;"></textarea></div>
          <div class="field">
            <label for="w-feeling">How are you feeling?</label>
            <select id="w-feeling">
              <option value="" disabled selected>Select...</option>
              <option value="🔥 On Fire">🔥 On Fire</option>
              <option value="💪 Strong">💪 Strong</option>
              <option value="😊 Good">😊 Good</option>
              <option value="😐 Neutral">😐 Neutral</option>
              <option value="😓 Struggling">😓 Struggling</option>
            </select>
          </div>
        </div>
        <div class="err-box" id="weeklyErr"></div>
        <div class="submit-wrap">
          <button type="submit" class="submit-btn" id="weeklySubmit">
            <div class="btn-inner"><span id="wIcon">📆</span><span id="wTxt">Submit Weekly Reflection</span><div class="spinner" id="wSpin"></div></div>
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote" id="quoteBlock">
    <div class="q-text" id="qText"></div>
    <div class="q-auth" id="qAuth"></div>
  </div>
  <div class="footer">BOOKAWEEK · Mar – Sep 2026</div>
</div>

<!-- SUCCESS OVERLAY -->
<div class="success" id="successOverlay">
  <div class="s-icon" id="sIcon">✓</div>
  <div class="s-title" id="sTitle">Session <span>Logged!</span></div>
  <div class="s-msg"  id="sMsg">Your reading session has been recorded.</div>
  <div class="s-stats" id="sStats"></div>
  <button class="again-btn" onclick="closeSuccess()">Continue</button>
</div>

<script>
// ═══════════════════════════════════════════════════════════════════════════
// CONFIG
// ═══════════════════════════════════════════════════════════════════════════
const SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbzBbVPZrVX5jRDb_dRsgQObJazGNpJS10_WBLGpGxa4YNFvBtrrfNNaarRyui9X_Oa3Tg/exec';
const STORAGE_PREFIX = 'baw_';

// ═══════════════════════════════════════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════════════════════════════════════
let currentMember = null;
let currentMode   = 'daily';
let starRating    = 0;
let isRestDay     = false;
let memberLibrary = []; // books registered this month

// ═══════════════════════════════════════════════════════════════════════════
// INIT
// ═══════════════════════════════════════════════════════════════════════════
document.addEventListener('DOMContentLoaded', () => {
  const saved = localStorage.getItem(STORAGE_PREFIX + 'member');
  if (saved) {
    selectMember(saved, true);
  }
  setQuote();
  setDateDisplay();
});

function setDateDisplay() {
  const now = new Date();
  const days = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
  document.getElementById('dayName').textContent  = days[now.getDay()];
  document.getElementById('fullDate').textContent = now.toLocaleDateString('en-GB',{day:'numeric',month:'long',year:'numeric'});
  document.getElementById('currentMonth').textContent = now.toLocaleDateString('en-GB',{month:'long',year:'numeric'});
}

function setQuote() {
  const quotes = [
    {t:"The man who does not read has no advantage over the man who cannot read.",a:"Mark Twain"},
    {t:"Not all readers are leaders, but all leaders are readers.",a:"Harry S. Truman"},
    {t:"Reading is to the mind what exercise is to the body.",a:"Joseph Addison"},
    {t:"Today a reader, tomorrow a leader.",a:"Margaret Fuller"},
    {t:"A reader lives a thousand lives. The man who never reads lives only one.",a:"George R.R. Martin"},
    {t:"Reading is the gateway skill that makes all other learning possible.",a:"Barack Obama"},
    {t:"The more that you read, the more things you will know.",a:"Dr. Seuss"},
    {t:"Show me a family of readers, and I will show you the people who move the world.",a:"Napoleon Bonaparte"},
  ];
  const q = quotes[Math.floor(Math.random() * quotes.length)];
  document.getElementById('qText').textContent = `"${q.t}"`;
  document.getElementById('qAuth').textContent = `— ${q.a}`;
}

// ═══════════════════════════════════════════════════════════════════════════
// MEMBER SELECTION
// ═══════════════════════════════════════════════════════════════════════════
function selectMember(name, skipSave) {
  currentMember = name;
  if (!skipSave) localStorage.setItem(STORAGE_PREFIX + 'member', name);

  document.getElementById('memberScreen').classList.add('hidden');
  document.getElementById('mainApp').style.display = 'block';

  // Set greeting
  const greetings = ['Hey','Welcome back','Good to see you','Let\'s go'];
  const g = greetings[Math.floor(Math.random() * greetings.length)];
  document.getElementById('greetName').textContent = name;
  document.getElementById('greetSub').textContent  = 'Ready to log your session?';

  // Load member's book library from localStorage
  loadLibrary();

  // Set up weekly mode
  setupWeekly();

  setMode('daily');
}

// ═══════════════════════════════════════════════════════════════════════════
// MODE SWITCHING
// ═══════════════════════════════════════════════════════════════════════════
function setMode(mode) {
  currentMode = mode;
  ['daily','books','weekly'].forEach(m => {
    document.getElementById('mode-' + m).style.display = m === mode ? 'block' : 'none';
    document.getElementById('btn-' + m).classList.toggle('active', m === mode);
  });

  if (mode === 'daily') {
    refreshBookDropdown();
    updateProgress();
  }
  if (mode === 'books') {
    renderLibrary();
  }
  if (mode === 'weekly') {
    setupWeekly();
    refreshWeeklyBookDropdown();
  }
}

// ═══════════════════════════════════════════════════════════════════════════
// LIBRARY (Books Mode)
// ═══════════════════════════════════════════════════════════════════════════
function libKey() { return STORAGE_PREFIX + currentMember + '_library'; }

function loadLibrary() {
  try { memberLibrary = JSON.parse(localStorage.getItem(libKey())) || []; }
  catch(e) { memberLibrary = []; }
}

function saveLibrary() {
  localStorage.setItem(libKey(), JSON.stringify(memberLibrary));
}

function renderLibrary() {
  const list = document.getElementById('bookList');
  if (memberLibrary.length === 0) {
    list.innerHTML = '<div class="empty-lib"><span class="el-icon">📖</span>No books added yet.<br>Add the books you\'re reading this month below.</div>';
    return;
  }
  list.innerHTML = memberLibrary.map((b, i) => `
    <div class="book-item">
      <div class="bi-num">${i+1}</div>
      <div class="bi-info">
        <div class="bi-title">${escHtml(b.title)}</div>
        <div class="bi-author">${escHtml(b.author || '—')} · ${b.status}</div>
      </div>
      <button class="bi-del" onclick="removeBook(${i})" title="Remove">✕</button>
    </div>
  `).join('');
}

function refreshBookDropdown() {
  const sel = document.getElementById('d-book');
  const cur = sel.value;
  sel.innerHTML = '<option value="" disabled>Select from your library...</option>';
  if (memberLibrary.length === 0) {
    sel.innerHTML += '<option value="" disabled>— Add books in the My Books tab —</option>';
  } else {
    memberLibrary.forEach(b => {
      const opt = document.createElement('option');
      opt.value = b.title + (b.author ? ' — ' + b.author : '');
      opt.textContent = b.title + (b.author ? ' · ' + b.author : '');
      if (opt.value === cur) opt.selected = true;
      sel.appendChild(opt);
    });
  }
  // Also allow manual entry option
  const manual = document.createElement('option');
  manual.value = '__manual__'; manual.textContent = '✏️ Type a book title...';
  sel.appendChild(manual);
}

function refreshWeeklyBookDropdown() {
  const sel = document.getElementById('w-book');
  sel.innerHTML = '<option value="" disabled selected>Select...</option><option value="—">— None this week —</option>';
  memberLibrary.forEach(b => {
    const opt = document.createElement('option');
    opt.value = b.title; opt.textContent = b.title;
    sel.appendChild(opt);
  });
}

// Handle manual book title entry
document.getElementById('d-book').addEventListener('change', function() {
  if (this.value === '__manual__') {
    const title = prompt('Enter book title:');
    if (title && title.trim()) {
      // Add to library temporarily
      memberLibrary.push({ title: title.trim(), author: '', status: 'Reading', category: 'Other', addedAt: new Date().toISOString() });
      saveLibrary();
      refreshBookDropdown();
      document.getElementById('d-book').value = title.trim();
    } else {
      this.value = '';
    }
  }
  updateProgress();
});

function removeBook(idx) {
  if (confirm('Remove "' + memberLibrary[idx].title + '" from your library?')) {
    memberLibrary.splice(idx, 1);
    saveLibrary();
    renderLibrary();
    refreshBookDropdown();
  }
}

// Show/hide completed fields based on status
document.getElementById('b-status').addEventListener('change', function() {
  document.getElementById('completedFields').style.display = this.value === 'Completed' ? 'block' : 'none';
});

async function submitBook() {
  const title = document.getElementById('b-title').value.trim();
  const errEl = document.getElementById('bookErr');
  errEl.classList.remove('show');

  if (!title) { errEl.textContent = 'Please enter the book title.'; errEl.classList.add('show'); return; }

  const status   = document.getElementById('b-status').value;
  const author   = document.getElementById('b-author').value.trim();
  const category = document.getElementById('b-cat').value;
  const now      = new Date();
  const monthStr = now.toLocaleDateString('en-GB', { month:'long', year:'numeric' });

  // Add to local library
  const bookEntry = { title, author, status, category, addedAt: now.toISOString() };
  memberLibrary.push(bookEntry);
  saveLibrary();

  // Build payload for sheet
  const payload = {
    action:    'addBook',
    member:    currentMember,
    date:      toDateStr(now),
    month:     monthStr,
    title, author, category, status,
    pages:     status === 'Completed' ? (parseInt(document.getElementById('b-pages').value) || 0) : 0,
    rating:    status === 'Completed' ? (parseInt(document.getElementById('b-rating').value) || 0) : 0,
    insight:   status === 'Completed' ? document.getElementById('b-insight').value.trim() : '',
    actionTaken: status === 'Completed' ? document.getElementById('b-action').value.trim() : '',
    recommend: status === 'Completed' ? document.getElementById('b-rec').value : '',
  };

  setBookLoading(true);
  try {
    await fetch(SCRIPT_URL, { method:'POST', mode:'no-cors', headers:{'Content-Type':'application/json'}, body:JSON.stringify(payload) });
    showSuccessOverlay(
      status === 'Completed' ? '📖 Book Logged!' : '📚 Added to Library!',
      `<em>${escHtml(title)}</em> has been ${status === 'Completed' ? 'logged as completed' : 'added to your reading library'} and will appear in the Daily Log dropdown.`,
      [['Book', title], ['Author', author || '—'], ['Status', status], ['Category', category]]
    );
    // Reset book form
    document.getElementById('b-title').value  = '';
    document.getElementById('b-author').value = '';
    document.getElementById('completedFields').style.display = 'none';
    document.getElementById('b-status').value = 'Reading';
    renderLibrary();
    refreshBookDropdown();
  } catch(e) {
    errEl.textContent = 'Connection failed. Book saved locally — will sync when reconnected.';
    errEl.classList.add('show');
  } finally {
    setBookLoading(false);
  }
}

// ═══════════════════════════════════════════════════════════════════════════
// DAILY LOG
// ═══════════════════════════════════════════════════════════════════════════
function toggleRest() {
  isRestDay = !isRestDay;
  document.getElementById('restRow').classList.toggle('on', isRestDay);
  document.getElementById('restLbl').textContent = isRestDay ? '✓ Rest Day Marked' : 'Mark as Rest Day';
  document.getElementById('dailyReadFields').style.opacity  = isRestDay ? '0.3' : '1';
  document.getElementById('dailyReadFields').style.pointerEvents = isRestDay ? 'none' : '';
  updateProgress();
}

function setStar(n) {
  starRating = n;
  document.querySelectorAll('.star-btn').forEach((b,i) => b.classList.toggle('on', i < n));
}

function updateProgress() {
  const vals = [
    currentMember,
    isRestDay || document.getElementById('d-book').value,
    isRestDay || document.getElementById('d-mins').value,
    isRestDay || document.getElementById('d-insight').value,
  ];
  document.getElementById('progFill').style.width = (vals.filter(Boolean).length / vals.length * 100) + '%';
}

['d-book','d-mins','d-insight'].forEach(id => {
  const el = document.getElementById(id);
  if (el) { el.addEventListener('input', updateProgress); el.addEventListener('change', updateProgress); }
});

document.getElementById('dailyForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  const errEl = document.getElementById('dailyErr');
  errEl.classList.remove('show');

  const book    = document.getElementById('d-book').value;
  const mins    = document.getElementById('d-mins').value;
  const insight = document.getElementById('d-insight').value.trim();

  if (!isRestDay) {
    if (!book || book === '__manual__') { errEl.textContent='Please select a book.'; errEl.classList.add('show'); return; }
    if (!mins) { errEl.textContent='Please enter minutes read.'; errEl.classList.add('show'); return; }
    if (!insight) { errEl.textContent='Please share your key insight.'; errEl.classList.add('show'); return; }
  }

  const now = new Date();
  const payload = {
    action:    'logDaily',
    member:    currentMember,
    date:      toDateStr(now),
    dateDisplay: now.toLocaleDateString('en-GB',{day:'numeric',month:'short',year:'numeric'}),
    book:    isRestDay ? 'Rest Day' : book,
    module:  isRestDay ? '—' : document.getElementById('d-mod').value,
    minutes: isRestDay ? 0 : (parseInt(mins) || 0),
    pages:   isRestDay ? 0 : (parseInt(document.getElementById('d-pages').value) || 0),
    insight: isRestDay ? '— Rest Day —' : insight,
    action:  isRestDay ? '' : document.getElementById('d-action').value.trim(),
    rating:  isRestDay ? 0 : starRating,
    isRestDay,
  };

  setDailyLoading(true);
  try {
    await fetch(SCRIPT_URL, { method:'POST', mode:'no-cors', headers:{'Content-Type':'application/json'}, body:JSON.stringify(payload) });
    showSuccessOverlay(
      isRestDay ? '🛌 Rest Day Logged!' : '📅 Session Logged!',
      isRestDay
        ? `Rest day recorded, ${currentMember}. Recovery is part of the system. 🌙`
        : `${payload.minutes} minutes logged. Every session builds the edge. 🔥`,
      isRestDay
        ? [['Member', currentMember], ['Date', payload.dateDisplay], ['Type', 'Rest Day']]
        : [['Member', currentMember], ['Date', payload.dateDisplay], ['Minutes', payload.minutes + ' min'], ['Book', book.split(' — ')[0].slice(0,22)]]
    );
    resetDailyForm();
  } catch(err) {
    errEl.textContent = 'Connection failed. Check internet and try again.';
    errEl.classList.add('show');
  } finally {
    setDailyLoading(false);
  }
});

// ═══════════════════════════════════════════════════════════════════════════
// WEEKLY REFLECTION
// ═══════════════════════════════════════════════════════════════════════════
function setupWeekly() {
  const now    = new Date();
  const isSun  = now.getDay() === 0;
  // For testing, also unlock if URL has ?weekly=open
  const force  = window.location.search.includes('weekly=open');

  document.getElementById('weeklyLocked').style.display   = (!isSun && !force) ? 'block' : 'none';
  document.getElementById('weeklyUnlocked').style.display = (isSun || force)   ? 'block' : 'none';

  if (!isSun && !force) {
    // Build day pills
    const days = ['M','T','W','T','F','S','Su'];
    const today = now.getDay() === 0 ? 7 : now.getDay();
    document.getElementById('weekDays').innerHTML = days.map((d,i) => {
      const dayNum = i + 1;
      const cls    = dayNum < today ? 'done' : dayNum === today ? 'today' : '';
      return `<div class="um-day ${cls}">${d}</div>`;
    }).join('');
  }

  if (isSun || force) {
    // Auto-calculate this week's stats from daily log storage or fetch
    calcWeekStats();
  }
}

function calcWeekStats() {
  // Gets data from the Apps Script (GET request to fetch weekly stats)
  // Falls back to 0 if not available
  document.getElementById('w-days').textContent  = '—';
  document.getElementById('w-mins').textContent  = '—';
  document.getElementById('w-pages').textContent = '—';

  // Fetch stats from script
  const params = new URLSearchParams({ action:'getWeekStats', member: currentMember });
  fetch(SCRIPT_URL + '?' + params.toString())
    .then(r => r.json())
    .then(data => {
      if (data && data.success) {
        document.getElementById('w-days').textContent  = data.daysRead  || 0;
        document.getElementById('w-mins').textContent  = data.totalMins || 0;
        document.getElementById('w-pages').textContent = data.totalPages|| 0;
      }
    })
    .catch(() => {
      document.getElementById('w-days').textContent  = '?';
      document.getElementById('w-mins').textContent  = '?';
      document.getElementById('w-pages').textContent = '?';
    });
}

document.getElementById('weeklyForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  const errEl  = document.getElementById('weeklyErr');
  const insight = document.getElementById('w-insight').value.trim();
  const commit  = document.getElementById('w-commit').value.trim();
  errEl.classList.remove('show');

  if (!insight) { errEl.textContent='Please share your top insight of the week.'; errEl.classList.add('show'); return; }
  if (!commit)  { errEl.textContent='Please enter your execution commitment.'; errEl.classList.add('show'); return; }

  const now = new Date();
  // Week number from Mar 16 2026
  const startDate = new Date(2026, 2, 16);
  const dayOff    = Math.round((now - startDate) / 86400000);
  const weekNum   = Math.ceil((dayOff + 1) / 7);

  const payload = {
    action:      'logWeekly',
    member:      currentMember,
    date:        toDateStr(now),
    weekNum,
    weekRange:   getWeekRange(now),
    topBook:     document.getElementById('w-book').value || '—',
    insight,
    commitment:  commit,
    reflection:  document.getElementById('w-reflect').value.trim(),
    feeling:     document.getElementById('w-feeling').value || '—',
    daysRead:    document.getElementById('w-days').textContent,
    totalMins:   document.getElementById('w-mins').textContent,
    totalPages:  document.getElementById('w-pages').textContent,
  };

  setWeeklyLoading(true);
  try {
    await fetch(SCRIPT_URL, { method:'POST', mode:'no-cors', headers:{'Content-Type':'application/json'}, body:JSON.stringify(payload) });
    showSuccessOverlay(
      '📆 Week Reflected!',
      `Week ${weekNum} reflection submitted, ${currentMember}. See you next Sunday! 🎯`,
      [['Week', weekNum], ['Top Book', payload.topBook.slice(0,22)], ['Feeling', payload.feeling]]
    );
    document.getElementById('weeklyForm').reset();
  } catch(err) {
    errEl.textContent = 'Connection failed. Try again.';
    errEl.classList.add('show');
  } finally {
    setWeeklyLoading(false);
  }
});

// ═══════════════════════════════════════════════════════════════════════════
// SUCCESS OVERLAY
// ═══════════════════════════════════════════════════════════════════════════
function showSuccessOverlay(title, msg, stats) {
  const overlay = document.getElementById('successOverlay');
  document.getElementById('sTitle').innerHTML = title;
  document.getElementById('sMsg').innerHTML   = msg;
  document.getElementById('sStats').innerHTML = stats.map(([l,v]) =>
    `<div class="s-row"><span class="s-lbl">${l}</span><span class="s-val">${escHtml(String(v))}</span></div>`
  ).join('');
  overlay.classList.add('show');
}

function closeSuccess() {
  document.getElementById('successOverlay').classList.remove('show');
}

// ═══════════════════════════════════════════════════════════════════════════
// LOADING STATES
// ═══════════════════════════════════════════════════════════════════════════
function setDailyLoading(on) {
  document.getElementById('dailySubmit').disabled = on;
  document.getElementById('dSpin').style.display  = on ? 'block':'none';
  document.getElementById('dIcon').style.display  = on ? 'none':'block';
  document.getElementById('dTxt').textContent     = on ? 'Sending...':'Log My Session';
}
function setBookLoading(on) {
  document.getElementById('bookSubmit').disabled = on;
  document.getElementById('bSpin').style.display = on ? 'block':'none';
  document.getElementById('bIcon').style.display = on ? 'none':'block';
  document.getElementById('bTxt').textContent    = on ? 'Saving...':'Add to My Library';
}
function setWeeklyLoading(on) {
  document.getElementById('weeklySubmit').disabled = on;
  document.getElementById('wSpin').style.display   = on ? 'block':'none';
  document.getElementById('wIcon').style.display   = on ? 'none':'block';
  document.getElementById('wTxt').textContent      = on ? 'Submitting...':'Submit Weekly Reflection';
}

// ═══════════════════════════════════════════════════════════════════════════
// HELPERS
// ═══════════════════════════════════════════════════════════════════════════
function toDateStr(d) {
  return d.getFullYear() + '-' + String(d.getMonth()+1).padStart(2,'0') + '-' + String(d.getDate()).padStart(2,'0');
}
function getWeekRange(d) {
  const start = new Date(d); start.setDate(d.getDate() - d.getDay() + 1);
  const end   = new Date(start); end.setDate(start.getDate() + 6);
  const fmt   = dt => dt.toLocaleDateString('en-GB',{day:'numeric',month:'short'});
  return fmt(start) + ' – ' + fmt(end);
}
function escHtml(s) {
  return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}
function resetDailyForm() {
  document.getElementById('dailyForm').reset();
  starRating = 0; isRestDay = false;
  document.getElementById('restRow').classList.remove('on');
  document.getElementById('restLbl').textContent = 'Mark as Rest Day';
  document.getElementById('dailyReadFields').style.opacity = '1';
  document.getElementById('dailyReadFields').style.pointerEvents = '';
  document.querySelectorAll('.star-btn').forEach(b => b.classList.remove('on'));
  document.getElementById('progFill').style.width = '0%';
  document.getElementById('dailyErr').classList.remove('show');
  refreshBookDropdown();
}
</script>
</body>
</html>
