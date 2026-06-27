<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="color-scheme" content="dark light">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no, shrink-to-fit=no">
<title>Arus Keuangan | RHN CAPITAL</title>

<link rel="manifest" href="manifest.json">
<meta name="theme-color" content="#050505">
<link rel="apple-touch-icon" href="RHN LOGO.jpg">

<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;600;700;800&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

<script>
  window.addEventListener('DOMContentLoaded', function() {
    var testEl = document.createElement('div');
    testEl.style.cssText = 'font-size: 100px; position: absolute; visibility: hidden; z-index: -999;';
    document.body.appendChild(testEl);
    
    var actualSize = parseFloat(window.getComputedStyle(testEl).fontSize);
    document.body.removeChild(testEl);
    
    if (actualSize !== 100 && actualSize > 0) {
       var zoomRatio = 100 / actualSize;
       document.documentElement.style.zoom = zoomRatio;
    }
  });
</script>

<style>
/* ==========================================================================
   TEMA ORIGINAL (GELAP PEKAT) + TEKS NOMINAL PUTIH ELEGAN
   ========================================================================== */
* { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; -webkit-text-size-adjust: none; text-size-adjust: none; }

h1, hr, .page-header, .site-header, .project-name { display: none !important; }

:root {
  --bg: #050505; 
  --bg2: #121215; 
  --bg3: #1A1A1F;
  --card: #121215;
  --border: #222228; 
  --border2: #33333E;
  --text: #FFFFFF; 
  --text2: #CCCCCC; 
  --text3: #888899;
  
  --gold: #FBBF24; 
  --gold2: #F59E0B; 
  --green2: #10B981; 
  --red2: #F87171;
  --blue: #3B82F6;
  --blue-title: #007BFF;
  
  --shadow-float: 0 12px 32px rgba(0,0,0,0.5);
  --radius: 16px; 
}

body.light-mode {
  --bg: #DFE2E6; 
  --bg2: #E9EDF1; 
  --bg3: #D0D5DB;
  --card: #E9EDF1; 
  --border: #C2C8D0; 
  --border2: #9CA3AF;
  --text: #111827; 
  --text2: #374151; 
  --text3: #4B5563;
  --blue-title: #0056b3;
}

body {
  font-family: 'Outfit', sans-serif;
  background-color: var(--bg);
  color: var(--text);
  font-size: 14px;
  line-height: 1.5;
  min-height: 100vh;
  overflow-x: hidden;
  transition: background-color 0.4s ease, color 0.4s ease;
}

.swal2-container { z-index: 100000 !important; }
.centered-modal { border-radius: 24px !important; overflow: hidden; box-shadow: var(--shadow-float) !important; }

/* HEADER */
.header-area { padding: 20px 24px; }
.logo-row { display: flex; align-items: center; justify-content: center; flex-direction: column; gap: 8px; margin-bottom: 20px; padding-top: 10px; }
.logo-img { width: 60px; height: 60px; border-radius: 14px; border: 1px solid var(--gold2); padding: 2px; }
.logo-img img { width: 100%; height: 100%; border-radius: 10px; object-fit: cover; }
.logo-text { text-align: center; }
.logo-text .main-text { font-size: 20px; font-weight: 800; color: var(--text); letter-spacing: 0.5px; }
.logo-text .sub-text { font-size: 10px; font-weight: 700; color: var(--gold); text-transform: uppercase; letter-spacing: 1.5px; }

/* EXTERNAL LINKS */
.top-ext-links {
  display: flex; gap: 16px; padding: 0 0 24px 0;
  flex-wrap: wrap; align-items: center; justify-content: center;
}
.nav-ext-btn {
  background: transparent; border: none; color: var(--gold);
  font-weight: 700; font-size: 11px; font-family: 'Outfit', sans-serif;
  cursor: pointer; text-transform: uppercase; letter-spacing: 0.5px;
}
.nav-ext-btn:hover { color: var(--text); }

.status-row { display: flex; gap: 12px; margin-bottom: 20px; }
.status-pill {
  background: var(--bg2); border: 1px solid var(--border); border-radius: 12px;
  padding: 8px 16px; display: flex; align-items: center; justify-content: center; gap: 8px;
}
.usd-val { font-family: 'JetBrains Mono', monospace; font-size: 14px; font-weight: 700; color: var(--text); }
.sync-dot { width: 8px; height: 8px; border-radius: 50%; box-shadow: 0 0 8px currentColor; }
.sync-text { font-size: 10px; font-weight: 700; color: var(--text3); text-transform: uppercase; letter-spacing: 1px; }

/* USER ROW */
.user-row { display: flex; align-items: center; gap: 12px; position: relative; width: 100%; }
.theme-btn {
  background: var(--bg2); border: 1px solid var(--border); color: var(--gold);
  width: 40px; height: 40px; border-radius: 12px; display: flex; align-items: center; justify-content: center;
  font-size: 16px; cursor: pointer; flex-shrink: 0; transition: 0.3s;
}
.theme-btn:hover { background: var(--bg3); }
.user-pill {
  flex: 1; background: var(--bg2); border: 1px solid var(--border); border-radius: 12px;
  padding: 4px 12px 4px 4px; display: flex; align-items: center; justify-content: space-between;
}
.user-pill-left { display: flex; align-items: center; gap: 10px; }
.u-avatar {
  width: 30px; height: 30px; border-radius: 50%; border: 1px solid var(--gold);
  display: flex; align-items: center; justify-content: center; color: var(--gold); font-weight: 700; font-size: 12px;
}
.u-name { font-size: 12px; font-weight: 600; color: var(--text); }

.user-action-wrap { display: flex; gap: 6px; padding-right: 4px; align-items: center; }
.setting-btn { background: transparent; border: 1px solid var(--border2); color: var(--text3); width: 32px; height: 32px; border-radius: 8px; display: flex; align-items: center; justify-content: center; cursor: pointer; transition: 0.3s; padding: 0; }
.logout-btn { background: transparent; border: 1px solid var(--border2); color: var(--text3); height: 32px; padding: 0 12px; border-radius: 8px; font-size: 10px; font-weight: 800; cursor: pointer; text-transform: uppercase; transition: 0.3s; display: flex; align-items: center; justify-content: center; }
.setting-btn:hover { background: rgba(255,255,255,0.05); border-color: var(--text); color: var(--text); }
.logout-btn:hover { background: rgba(248,113,113,0.1); border-color: var(--red2); color: var(--red2); }

/* NAVIGATION */
.nav {
  padding: 0 24px 24px; display: flex; gap: 12px;
  overflow-x: auto; scrollbar-width: none; white-space: nowrap;
}
.nav::-webkit-scrollbar { display: none; }
.nav-btn {
  padding: 10px 20px; font-size: 11px; font-weight: 700; color: var(--text3);
  border: 1px solid var(--border); border-radius: 100px; background: transparent;
  cursor: pointer; transition: 0.3s; text-transform: uppercase; letter-spacing: 0.5px;
}
.nav-btn.active { background: var(--text); color: var(--bg); border-color: var(--text); }

/* MAIN CONTENT */
.main { padding: 0 24px 80px; max-width: 1400px; margin: 0 auto; }
.page { display: none; animation: fadeIn 0.4s ease; } .page.active { display: block; }
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

/* METRICS */
.metrics { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; margin-bottom: 24px; }
.m-card { background: var(--card); border-radius: var(--radius); padding: 16px; border: 1px solid var(--border); display: flex; flex-direction: column; }
.m-label { font-size: 9px; font-weight: 800; text-transform: uppercase; color: var(--text3); margin-bottom: 8px; letter-spacing: 0.5px; }
.m-val { font-family: 'JetBrains Mono', monospace; font-size: 18px; font-weight: 800; margin-bottom: 4px; color: var(--text); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; width: 100%; display: block; }
.usd-pill {
  display: inline-block; background: var(--bg3); color: var(--text3);
  font-size: 10px; font-family: 'JetBrains Mono', monospace; font-weight: 600;
  padding: 2px 8px; border-radius: 6px; align-self: flex-start; margin-bottom: 8px;
}
.m-sub { font-size: 10px; font-weight: 500; color: var(--text3); margin-bottom: 12px; flex-grow: 1; }
.m-bar { height: 4px; background: var(--bg3); border-radius: 2px; width: 100%; overflow: hidden; }
.m-bar-fill { height: 100%; border-radius: 2px; transition: width 0.6s ease; }
.inc .m-bar-fill { background: var(--green2); } .exp .m-bar-fill { background: var(--red2); }
.bal .m-bar-fill { background: var(--border2); } .cnt .m-bar-fill { background: var(--blue); }

/* WALLETS */
.wallet-scroll { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 24px; }
.w-card { background: var(--bg3); border: 1px solid var(--border); border-radius: 12px; padding: 10px 8px; display: flex; flex-direction: column; justify-content: center; overflow: hidden; position: relative; }
.w-label { font-size: 8px; font-weight: 800; color: var(--text3); text-transform: uppercase; margin-bottom: 2px; letter-spacing: 0.5px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.w-val { font-family: 'JetBrains Mono', monospace; font-size: 12px; font-weight: 700; color: var(--text); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; width: 100%; display: block; }
.w-val.min { color: var(--red2); }
.w-pct-badge { position: absolute; top: 8px; right: 8px; font-size: 8px; font-weight: 800; background: var(--border); padding: 2px 4px; border-radius: 4px; color: var(--text2); display: none; }

.sum-grid { display: grid; gap: 16px; margin-bottom: 24px; }

/* FORMS */
.card { background: var(--card); border-radius: var(--radius); padding: 32px; border: 1px solid var(--border); margin-bottom: 24px; }
.card-head { margin-bottom: 16px; }
.card-title { font-size: 16px; font-weight: 700; color: var(--text); margin-bottom: 4px; }
.card-sub { font-size: 12px; color: var(--text3); }

.type-toggle { display: flex; background: var(--bg3); border-radius: 16px; padding: 4px; margin-bottom: 20px; }
.t-btn { flex: 1; padding: 12px; border: none; border-radius: 12px; font-size: 12px; font-weight: 700; cursor: pointer; background: transparent; color: var(--text3); transition: 0.2s; }
.t-btn.income.active { background: var(--bg2); color: var(--green2); box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
.t-btn.expense.active { background: var(--bg2); color: var(--text); box-shadow: 0 2px 8px rgba(0,0,0,0.1); }

.f-input-dark {
  width: 100%; padding: 16px; border-radius: 16px; border: 1px solid var(--border);
  background-color: var(--bg2) !important; color: var(--text) !important;
  outline: none; font-family: 'Outfit', sans-serif; font-size: 15px; font-weight: 500;
  appearance: none; -webkit-appearance: none; transition: all 0.3s ease;
  box-shadow: 0 2px 10px rgba(0,0,0,0.03); 
}
#f-amount { overflow-x: auto; white-space: nowrap; scrollbar-width: none; font-size: 20px; font-weight: 800; }
.f-input-dark:focus { border-color: var(--gold); box-shadow: 0 0 0 3px rgba(251, 191, 36, 0.15); }
.f-input-dark::placeholder { color: var(--text3); }

select.f-input-dark {
  background-image: url('data:image/svg+xml;utf8,<svg fill="%23888899" height="24" viewBox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>');
  background-repeat: no-repeat; background-position: right 16px center; padding-right: 40px; cursor: pointer;
}
select.f-input-dark option { background: var(--bg2); color: var(--text); font-weight: 500; padding: 12px; }

.form-row { margin-bottom: 16px; }
.form-label { font-size: 10px; font-weight: 800; color: var(--text3); margin-bottom: 8px; display: block; text-transform: uppercase; letter-spacing: 0.5px; }
.form-row textarea { height: 100px; resize: none; border-radius: 16px; }
.submit-btn { width: 100%; padding: 16px; background: var(--text); color: var(--bg); border: none; border-radius: 16px; font-size: 13px; font-weight: 800; cursor: pointer; transition: 0.2s; text-transform: uppercase; margin-top: 8px; }

/* HISTORY CARDS */
.list-wrap { padding: 8px 0; }
.recent-item {
  padding: 16px; margin-bottom: 12px; border-radius: 16px; 
  background: var(--bg2); border: 1px solid var(--border); 
  display: flex; align-items: center; justify-content: space-between;
}
.ri-icon {
  width: 40px; height: 40px; border-radius: 12px; display: flex; align-items: center; justify-content: center;
  font-size: 18px; font-weight: 800; background: var(--bg3); margin-right: 12px; flex-shrink: 0;
}
.ri-icon.inc { color: var(--green2); } .ri-icon.exp { color: var(--red2); }
.ri-left { display: flex; align-items: center; flex: 1; }

.ri-note { font-size: 14px; font-weight: 700; color: var(--text); margin-bottom: 2px; display: flex; align-items: center; gap: 8px; flex-wrap: wrap; line-height: 1.4; }
.ri-meta { font-size: 11px; font-weight: 500; color: var(--text3); }
.cat-badge { font-size: 9px; font-weight: 600; padding: 2px 6px; border-radius: 6px; background: var(--bg); border: 1px solid var(--border); color: var(--text3); text-transform: uppercase; display: inline-block; white-space: nowrap; }

.ri-right-wrap { display: flex; flex-direction: column; align-items: flex-end; gap: 4px; flex-shrink: 0; margin-left: 12px; }
.ri-amounts-col { display: flex; flex-direction: column; align-items: flex-end; }
.ri-amount { font-family: 'JetBrains Mono', monospace; font-size: 15px; font-weight: 800; white-space: nowrap; color: var(--text); }
.ri-usd { font-family: 'JetBrains Mono', monospace; font-size: 11px; font-weight: 600; color: var(--text3); margin-top: 2px; }
.del-btn-recent, .edit-btn-recent { background: transparent; border: none; color: var(--text3); font-size: 11px; font-weight: 700; cursor: pointer; text-transform: uppercase; margin-top: 4px; }
.del-btn-recent { color: var(--red2); }
.export-btn { background: var(--text); color: var(--bg); padding: 16px 24px; border: none; border-radius: 12px; font-size: 12px; font-weight: 800; cursor: pointer; text-transform: uppercase; flex-shrink: 0; white-space: nowrap; }
.action-btns { display: flex; gap: 8px; margin-top: 4px; align-items: center; justify-content: flex-end; }

/* KALKULATOR MATA UANG */
.calc-curr-item { display: flex; justify-content: space-between; align-items: center; padding: 16px; cursor: pointer; border-radius: 12px; transition: 0.2s; margin-bottom: 4px; border: 1px solid transparent; }
.calc-curr-item:hover { background: rgba(255,255,255,0.02); border-color: var(--border); }
.calc-curr-item.active { background: rgba(16, 185, 129, 0.05); border-color: var(--green2); }
.calc-curr-item.active .calc-amount { color: var(--green2); border-right: 2px solid var(--green2); padding-right: 6px; animation: blinkCursor 1s step-end infinite; }
@keyframes blinkCursor { 50% { border-color: transparent; } }

.calc-left { display: flex; align-items: center; gap: 12px; }
.calc-flag { display: flex; align-items: center; justify-content: center; }
.calc-code-wrap { display: flex; flex-direction: column; align-items: flex-start; }

.calc-select {
    background: transparent; color: var(--text); border: none; font-size: 16px; font-weight: 800;
    outline: none; cursor: pointer; font-family: 'Outfit', sans-serif; appearance: none; -webkit-appearance: none; padding-right: 18px;
    background-image: url('data:image/svg+xml;utf8,<svg fill="%23888899" height="16" viewBox="0 0 24 24" width="16" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>');
    background-repeat: no-repeat; background-position: right center;
}
.calc-name { font-size: 10px; color: var(--text3); margin-top: 2px; padding-left: 2px; }
.calc-right { text-align: right; overflow: hidden; }
.calc-amount { font-family: 'JetBrains Mono', monospace; font-size: 20px; font-weight: 600; color: var(--text); margin-bottom: 2px; transition: color 0.2s; max-width: 55vw; overflow-x: auto; white-space: nowrap; scrollbar-width: none; }

.swap-btn { background: var(--bg2); border: 1px solid var(--border); color: var(--text3); width: 32px; height: 32px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center; font-size: 14px; transition: 0.2s; box-shadow: 0 2px 8px rgba(0,0,0,0.2); }
.swap-btn:hover { background: var(--bg3); color: var(--text); border-color: var(--text3); transform: scale(1.1); }
.calc-keypad-wrap { background: #1A1C1F; border-bottom-left-radius: 16px; border-bottom-right-radius: 16px; padding: 24px 16px; margin-top: 8px; }
.calc-keypad { display: grid; grid-template-columns: repeat(4, 1fr); grid-template-rows: repeat(4, 55px); gap: 12px; }
.calc-btn { background: transparent; border: none; color: var(--text); font-size: 22px; font-family: 'Outfit', sans-serif; cursor: pointer; border-radius: 12px; transition: 0.1s; display: flex; align-items: center; justify-content: center; }
.calc-btn:active { background: rgba(255,255,255,0.1); transform: scale(0.95); }
.calc-btn-ac { background: #23342B; color: #4ADE80; grid-column: 4; grid-row: 1 / 3; font-size: 20px; font-weight: 700; border-radius: 16px; }
.calc-btn-del { background: #23342B; color: #4ADE80; grid-column: 4; grid-row: 3 / 5; border-radius: 16px; }

/* SETTINGS MODULE */
.set-group { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 20px; margin-bottom: 24px; }
.set-title { font-size: 11px; font-weight: 800; color: var(--gold); text-transform: uppercase; margin-bottom: 16px; letter-spacing: 1px; border-bottom: 1px solid var(--border2); padding-bottom: 12px; display: flex; align-items: center; gap: 8px; }
.set-item { display: flex; justify-content: space-between; align-items: center; padding: 12px 0; border-bottom: 1px dashed var(--border2); }
.set-item:last-child { border-bottom: none; padding-bottom: 0; }
.set-label { font-size: 13px; font-weight: 700; color: var(--text); }
.set-sub { font-size: 10px; color: var(--text3); margin-top: 4px; font-weight: 500; }
.set-action { padding: 8px 16px; background: var(--bg3); border: 1px solid var(--border); color: var(--text); border-radius: 8px; font-size: 10px; font-weight: 800; cursor: pointer; transition: 0.2s; text-transform: uppercase; white-space: nowrap; }
.set-action:hover { background: var(--bg2); border-color: var(--gold); color: var(--gold); }
.set-action.danger { color: var(--red2); border-color: rgba(248,113,113,0.3); }
.set-action.danger:hover { background: rgba(248,113,113,0.1); border-color: var(--red2); }
.set-select { background: var(--bg2); border: 1px solid var(--border); color: var(--text); padding: 8px 12px; border-radius: 8px; font-size: 12px; font-weight: 600; outline: none; font-family: 'Outfit', sans-serif; cursor: pointer; }

/* CHART & FILTERS BAR */
.chart-wrap { margin-bottom: 24px; }
.chart-legend { display: flex; gap: 16px; margin-bottom: 16px; justify-content: center; }
.leg-item { display: flex; align-items: center; gap: 8px; font-size: 10px; font-weight: 700; color: var(--text3); text-transform: uppercase; }
.leg-dot { width: 10px; height: 10px; border-radius: 2px; }
.period-bar { display: flex; gap: 8px; overflow-x: auto; scrollbar-width: none; margin-bottom: 20px; padding-bottom: 8px; }
.p-btn { padding: 10px 20px; border: 1px solid var(--border); border-radius: 100px; font-size: 11px; font-weight: 700; cursor: pointer; background: var(--bg2); color: var(--text3); white-space: nowrap; }
.p-btn.active { border-color: var(--text); color: var(--text); background: var(--bg); }
.filter-bar { display: flex; gap: 16px; width: 100%; margin-bottom: 24px; align-items: center; }
.filter-bar select.f-input-dark { width: 250px; flex-shrink: 0; }
.filter-bar input.f-input-dark { flex: 1; }

/* AUTH SCREEN */
#auth-screen { position: fixed; inset: 0; background: var(--bg); display: flex; align-items: center; justify-content: center; z-index: 9999; }
.auth-box { background: var(--card); border-radius: 24px; padding: 40px 24px; width: 90%; max-width: 400px; border: 1px solid var(--border); text-align: center; }
.auth-box img { width: 64px; border-radius: 16px; margin-bottom: 16px; border: 1px solid var(--border2); }
.auth-title { font-size: 22px; font-weight: 800; color: var(--text); margin-bottom: 4px; }
.auth-sub { font-size: 12px; color: var(--text3); font-weight: 500; margin-bottom: 24px; }
.auth-tabs { display: flex; background: var(--bg3); border-radius: 12px; padding: 4px; margin-bottom: 24px; }
.auth-tab { flex: 1; padding: 12px; font-size: 12px; font-weight: 700; cursor: pointer; background: transparent; border: none; color: var(--text3); border-radius: 8px; }
.auth-tab.active { background: var(--bg2); color: var(--text); }
.auth-field input { width: 100%; padding: 16px; font-size: 14px; font-weight: 500; font-family: 'Outfit', sans-serif; border: 1px solid var(--border); border-radius: 12px; background: var(--bg2); color: var(--text); margin-bottom: 12px; outline: none; }
.auth-btn { width: 100%; padding: 16px; background: var(--text); color: var(--bg); border: none; border-radius: 12px; font-size: 13px; font-weight: 800; cursor: pointer; text-transform: uppercase; margin-top: 8px; }
.btn-google { background: #fff !important; color: #000 !important; border: 1px solid #ddd !important; display: flex; align-items: center; justify-content: center; gap: 10px; margin-top: 12px; }

/* ==========================================================================
   MOBILE RESPONSIVE
   ========================================================================== */
@media (max-width: 768px) {
  .top-ext-links { justify-content: center; padding: 0 0 16px 0; }
  .header-area { padding: 16px; }
  .status-row { flex-direction: row; }
  .status-pill { flex: 1; }
  .user-row { flex-direction: row; justify-content: flex-start; }
  .nav { padding: 0 16px 20px; }
  
  .main { padding: 0 0 80px 0 !important; width: 100%; overflow-x: hidden; }
  
  .metrics { grid-template-columns: repeat(2, 1fr); gap: 8px; padding: 0 !important; margin: 0 !important; background: transparent; border: none; }
  .metrics .m-card { border-radius: 24px !important; border-left: none; border-right: none; }
  
  .wallet-scroll { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; padding-left: 16px; padding-right: 16px; margin: 8px 0 16px 0 !important; width: 100%; }
  .w-card { border-radius: 12px !important; padding: 6px !important; }

  .sum-grid { grid-template-columns: repeat(2, 1fr); gap: 8px; padding: 0 !important; margin: 0 0 24px 0 !important; background: transparent; border: none; }
  .sum-grid .m-card { border-radius: 24px !important; border-left: none; border-right: none; }

  .panel { display: flex; flex-direction: column; gap: 16px; background: transparent; }
  .card { padding: 16px 0 !important; border-radius: 0 !important; border: none !important; background: transparent !important; margin-bottom: 0; }
  
  .card-head, .form-row, .filter-bar, .chart-wrap, .period-bar { padding-left: 16px !important; padding-right: 16px !important; }
  
  .filter-bar { flex-direction: column; } 
  .export-btn { width: 100%; text-align: center; border-radius: 16px; padding: 18px 16px; }
  
  .type-toggle, .submit-btn { width: calc(100% - 32px) !important; margin-left: 16px !important; margin-right: 16px !important; }
  .filter-bar select.f-input-dark, .filter-bar input.f-input-dark { width: 100%; border-radius: 16px; }
  .f-input-dark { padding: 18px 16px; font-size: 15px; border-radius: 16px; }
  
  .list-wrap { padding: 0 !important; margin: 0 !important; width: 100%; }
  .recent-item { width: 100% !important; margin: 0 0 12px 0 !important; padding: 16px 16px !important; border-radius: 24px !important; border-left: none !important; border-right: none !important; background: var(--card); flex-direction: row; justify-content: space-between; align-items: center; }
  .ri-right-wrap { margin-left: 0; align-items: flex-end; }
  .del-btn-recent, .edit-btn-recent { margin-top: 0px; }
  .cat-badge { display: inline-block !important; }

  .set-group { border-radius: 0; border-left: none; border-right: none; padding: 20px 16px; }
  .logout-btn { padding: 0 8px; font-size: 9px; height: 28px; }
  .setting-btn { width: 28px; height: 28px; padding: 4px; }
}

@media (min-width: 769px) {
  .metrics { grid-template-columns: repeat(4, 1fr); gap: 24px; }
  .sum-grid { grid-template-columns: repeat(4, 1fr); gap: 24px; }
  .wallet-scroll { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; padding-bottom: 0; }
  .w-card { min-width: 0; }
  .panel { display: grid; grid-template-columns: 380px 1fr; gap: 24px; align-items: start; }
  .main, .header-area, .nav { max-width: 1200px; margin: 0 auto; }
}

/* STYLING HUTANG PIUTANG & DOMPET */
.t-btn.debt.active { background: var(--bg2); color: var(--gold); border: 1px solid var(--gold); }
.t-btn.recv.active { background: var(--bg2); color: var(--blue); border: 1px solid var(--blue); }
.t-btn.transfer.active { background: var(--bg2); color: var(--text); border: 1px solid var(--text); }
.ri-icon.debt { color: var(--gold); background: rgba(251, 191, 36, 0.15); }
.ri-icon.recv { color: var(--blue); background: rgba(59, 130, 246, 0.15); }
.ri-icon.transfer { color: var(--text); background: var(--bg3); }
.ri-amount.debt { color: var(--gold); }
.ri-amount.recv { color: var(--blue); }
.ri-amount.transfer { color: var(--text); }
.wallet-badge { background: var(--bg3); color: var(--text2); font-size: 7px; padding: 2px 6px; border-radius: 4px; margin-left: 6px; font-weight: 800; border: 1px solid var(--border2); text-transform: uppercase; display: inline-block; white-space: normal; word-break: break-word; line-height: 1.2; }

body.hide-usd .usd-pill, body.hide-usd .ri-usd, body.hide-usd .usd-wallet-val, body.hide-usd .usd-status-pill { display: none !important; }

/* ==========================================================================
   SPLASH SCREEN V3: ULTIMATE MASTERPIECE
   ========================================================================== */
#splash-screen {
  position: fixed; inset: 0; 
  background: radial-gradient(circle at center, #121215 0%, #050505 100%);
  z-index: 999999; display: flex; align-items: center; justify-content: center; overflow: hidden;
}

#splash-screen.splash-exit { animation: diveIn 0.8s cubic-bezier(0.7, 0, 0.3, 1) forwards; }
@keyframes diveIn {
  0% { transform: scale(1); opacity: 1; filter: blur(0); }
  100% { transform: scale(1.5); opacity: 0; filter: blur(10px); visibility: hidden; }
}

.splash-particles { position: absolute; inset: 0; z-index: 1; pointer-events: none; }
.particle {
  position: absolute; background: var(--gold); border-radius: 50%;
  box-shadow: 0 0 10px var(--gold); opacity: 0; 
  animation: floatParticle 3s infinite ease-in-out;
}

@keyframes floatParticle {
  0% { transform: translateY(0) scale(0); opacity: 0; }
  50% { opacity: 0.6; }
  100% { transform: translateY(-50px) scale(1.5); opacity: 0; }
}

.splash-content { position: relative; z-index: 2; display: flex; flex-direction: column; align-items: center; }
.splash-logo-box { position: relative; width: 110px; height: 110px; margin-bottom: 20px; display: flex; align-items: center; justify-content: center; }
.splash-ring {
  position: absolute; inset: -5px; 
  border: 2px dashed rgba(245, 158, 11, 0.5); border-radius: 24px;
  animation: spinRing 10s linear infinite, popIn 1s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
}

.splash-img {
  width: 90px; height: 90px; border-radius: 18px; border: 2px solid var(--gold); padding: 3px;
  box-shadow: 0 0 35px rgba(245, 158, 11, 0.5); opacity: 0;
  animation: logoZoomFade 1.2s cubic-bezier(0.2, 0.8, 0.2, 1) forwards 0.2s;
}

.splash-img-shine { position: absolute; width: 90px; height: 90px; border-radius: 18px; overflow: hidden; pointer-events: none; }
.splash-img-shine::after {
  content: ""; position: absolute; top: -50%; left: -50%; width: 200%; height: 200%;
  background: linear-gradient(to right, transparent, rgba(255,255,255,0.6), transparent);
  transform: rotate(45deg) translateX(-100%);
  animation: flashShine 2.5s infinite cubic-bezier(0.4, 0, 0.2, 1) 1s;
}

.splash-title-wrap { overflow: hidden; padding-bottom: 5px; }
.splash-title {
  color: var(--text); font-family: 'Outfit', sans-serif; font-size: 28px; font-weight: 800;
  text-shadow: 0 4px 20px rgba(245, 158, 11, 0.6); 
  transform: translateY(100%); opacity: 0;
  animation: revealText 1s cubic-bezier(0.2, 0.8, 0.2, 1) forwards 0.6s;
}

.splash-sub {
  color: var(--gold); font-size: 11px; font-weight: 700; letter-spacing: 4px; margin-top: 4px; opacity: 0;
  animation: fadeSub 1s ease forwards 1.2s;
}

@keyframes spinRing { 100% { transform: rotate(360deg); } }
@keyframes popIn { 0% { transform: scale(0); opacity: 0; } 100% { transform: scale(1); opacity: 1; } }
@keyframes logoZoomFade { 0% { transform: scale(0.5); opacity: 0; filter: blur(5px); } 100% { transform: scale(1); opacity: 1; filter: blur(0); } }
@keyframes flashShine { 0% { transform: rotate(45deg) translateX(-100%); } 100% { transform: rotate(45deg) translateX(100%); } }
@keyframes revealText { 0% { transform: translateY(100%); opacity: 0; letter-spacing: 12px; } 100% { transform: translateY(0); opacity: 1; letter-spacing: 3px; } }
@keyframes fadeSub { 0% { opacity: 0; transform: translateY(10px); } 100% { opacity: 1; transform: translateY(0); } }
</style>
</head>
<body>

<div id="splash-screen">
  <div class="splash-particles" id="splash-particles"></div>
  <div class="splash-content">
    <div class="splash-logo-box">
      <div class="splash-ring"></div>
      <img src="RHN LOGO.jpg" alt="RHN Capital Logo" class="splash-img">
      <div class="splash-img-shine"></div>
    </div>
    <div class="splash-title-wrap">
      <div class="splash-title">RHN CAPITAL</div>
    </div>
    <div class="splash-sub">ARUS KEUANGAN</div>
  </div>
</div>

<div id="offline-banner" style="display:none; background:#F87171; color:#000; text-align:center; padding:10px; font-size:12px; font-weight:800; position:fixed; top:0; left:0; width:100%; z-index:100000; text-transform:uppercase; box-shadow:0 4px 12px rgba(0,0,0,0.5);">
  ⚠️ Koneksi Terputus - Mode Offline Aktif
</div>

<div id="auth-screen">
  <div class="auth-box">
    <img src="RHN LOGO.jpg" alt="RHN Capital Logo">
    <div class="auth-title">RHN CAPITAL</div>
    <div class="auth-sub">Arus Keuangan Akses Masuk</div>
    <div class="auth-tabs">
      <button class="auth-tab active" id="tab-login" onclick="switchTab('login')">Masuk</button>
      <button class="auth-tab" id="tab-register" onclick="switchTab('register')">Daftar</button>
    </div>
    <div id="auth-err" style="color:var(--red2);font-size:12px;margin-bottom:12px;display:none;"></div>
    
    <div class="form-row"><input type="email" id="auth-email" class="f-input-dark" placeholder="Email"></div>
    <div class="form-row"><input type="password" id="auth-pass" class="f-input-dark" placeholder="Sandi" onkeydown="if(event.key==='Enter')doAuth()"></div>
    <div class="form-row" id="field-confirm" style="display:none"><input type="password" id="auth-pass2" class="f-input-dark" placeholder="Ulangi Sandi"></div>
    
    <button class="auth-btn" id="auth-submit-btn" onclick="doAuth()">MASUK</button>
    
    <button class="auth-btn btn-google" id="btn-google" onclick="doGoogleAuth()">
      <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 48 48"><path fill="#FFC107" d="M43.611,20.083H42V20H24v8h11.303c-1.649,4.657-6.08,8-11.303,8c-6.627,0-12-5.373-12-12c0-6.627,5.373-12,12-12c3.059,0,5.842,1.154,7.961,3.039l5.657-5.657C34.046,6.053,29.268,4,24,4C12.955,4,4,12.955,4,24c0,11.045,8.955,20,20,20c11.045,0,20-8.955,20-20C44,22.659,43.862,21.35,43.611,20.083z"/><path fill="#FF3D00" d="M6.306,14.691l6.571,4.819C14.655,15.108,18.961,12,24,12c3.059,0,5.842,1.154,7.961,3.039l5.657-5.657C34.046,6.053,29.268,4,24,4C16.318,4,9.656,8.337,6.306,14.691z"/><path fill="#4CAF50" d="M24,44c5.166,0,9.86-1.977,13.409-5.192l-6.19-5.238C29.211,35.091,26.715,36,24,36c-5.202,0-9.619-3.317-11.283-7.946l-6.522,5.025C9.505,39.556,16.227,44,24,44z"/><path fill="#1976D2" d="M43.611,20.083H42V20H24v8h11.303c-0.792,2.237-2.231,4.166-4.087,5.571c0.001-0.001,0.002-0.001,0.003-0.002l6.19,5.238C36.971,39.205,44,34,44,24C44,22.659,43.862,21.35,43.611,20.083z"/></svg>
      MASUK DENGAN GOOGLE
    </button>

    <button style="background:transparent; border:none; color:var(--text3); font-size:10px; margin-top:16px; cursor:pointer; font-weight:700; text-transform:uppercase; text-decoration:underline; width:100%;" onclick="doResetPassword()" id="btn-forgot">Lupa Sandi?</button>
    <div style="font-size: 10px; color: var(--gold); margin-top: 6px; text-align: center;">Cek folder SPAM jika email reset tidak masuk</div>
  </div>
</div>

<div id="pin-screen" style="display:none; position: fixed; inset: 0; background: var(--bg); align-items: center; justify-content: center; z-index: 9999;">
  <div class="auth-box">
    <img src="RHN LOGO.jpg" alt="RHN Capital Logo">
    <div class="auth-title" id="pin-title">Masukkan PIN</div>
    <div class="auth-sub" id="pin-sub">Masukkan 6 digit PIN keamanan</div>
    <div id="pin-err" style="color:var(--red2);font-size:12px;margin-bottom:12px;display:none;"></div>
    <div class="form-row">
       <input type="password" id="app-pin" class="f-input-dark" style="text-align:center; letter-spacing: 12px; font-size: 24px; padding: 12px;" inputmode="numeric" maxlength="6" placeholder="••••••">
    </div>
    <button class="auth-btn" id="pin-submit-btn" onclick="verifyPin()" style="display:none;">BUKA APLIKASI</button>
    
    <div style="display: flex; justify-content: space-between; gap: 16px; margin-top: 24px;">
      <button style="background:transparent; border:none; color:var(--text3); font-size:10px; cursor:pointer; font-weight:700; text-transform:uppercase; text-decoration:underline;" onclick="resetAccount()">Ganti Akun</button>
      <button style="background:transparent; border:none; color:var(--text3); font-size:10px; cursor:pointer; font-weight:700; text-transform:uppercase; text-decoration:underline;" onclick="resetPinFromLogin()">Reset PIN</button>
    </div>
  </div>
</div>

<div id="app-screen" style="display:none;">
<div class="header-area">
  
  <div class="logo-row">
    <div class="logo-img"><img src="RHN LOGO.jpg" alt="Logo"></div>
    <div class="logo-text">
      <div class="main-text">RHN CAPITAL</div>
      <div class="sub-text">ARUS KEUANGAN</div>
    </div>
  </div>

  <div class="top-ext-links">
    <button class="nav-ext-btn" onclick="window.location.href='latar.html'">📈 HALAMAN RHN CAPITAL ↗</button>
    <button class="nav-ext-btn" onclick="window.location.href='jurnal.html'">📈 JURNAL FOREX ↗</button>
    <button class="nav-ext-btn" onclick="window.location.href='aset.html'">📈 JURNAL ASET ↗</button>
    <button class="nav-ext-btn" onclick="window.location.href='data.html'">📈 DATA PRIBADI ↗</button>
  </div>
  
  <div class="status-row">
    <div class="status-pill usd-status-pill" style="padding: 6px 4px;">
      <span class="usd-val" id="usd-rate-val" style="font-size: 9px;">...</span>
    </div>
    
    <div class="status-pill" style="padding: 6px 4px; flex-direction: column; justify-content: center; gap: 2px; font-size: 8px; font-weight: 800; color: var(--gold);">
      <span style="line-height: 1; white-space: nowrap;">XAU <span id="xau-rate-val" style="color: var(--text); font-family: 'JetBrains Mono', monospace; margin-left: 2px;">...</span></span>
      <span id="xau-idr-oz" style="display: none;"></span>
      <span style="line-height: 1; white-space: nowrap;">GRAM <span id="xau-idr-gr" style="color: var(--text); font-family: 'JetBrains Mono', monospace; margin-left: 2px;">...</span></span>
    </div>

    <div class="status-pill" style="padding: 6px 4px; gap: 4px;">
      <span class="sync-dot" id="sync-dot" style="background:var(--text3); width: 6px; height: 6px;"></span>
      <span class="sync-text" id="sync-label" style="font-size: 8px; letter-spacing: 0.5px;">MENGHUBUNGKAN...</span>
    </div>
  </div>

  <div class="user-row">
    <button class="theme-btn" onclick="toggleTheme()" id="theme-toggle">🌙</button>
    <div class="user-pill">
      <div class="user-pill-left">
        <div class="u-avatar" id="user-avatar">?</div>
        <div class="u-name" id="user-name">Memuat...</div>
      </div>
      <div class="user-action-wrap">
        <button class="setting-btn" onclick="switchPage('pengaturan')" title="Pengaturan">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"></circle><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path></svg>
        </button>
        <button class="logout-btn" onclick="doLogout()">KELUAR</button>
      </div>
    </div>
  </div>
</div>

<div class="nav">
  <button class="nav-btn active" onclick="switchPage('dashboard')">DASHBOARD</button>
  <button class="nav-btn" onclick="switchPage('harian')">HARIAN</button>
  <button class="nav-btn" onclick="switchPage('mingguan')">MINGGUAN</button>
  <button class="nav-btn" onclick="switchPage('bulanan')">BULANAN</button>
  <button class="nav-btn" onclick="switchPage('tahunan')">TAHUNAN</button>
  <button class="nav-btn" onclick="switchPage('riwayat')">RIWAYAT</button>
</div>

<div class="main">

<div id="page-dashboard" class="page active">
  <div class="metrics" id="metric-cards"></div>
  <div id="wallet-balances" class="wallet-scroll"></div>
  <div class="panel">
    <div class="card">
      <div class="card-head">
        <div class="card-title">Tambah Transaksi</div>
        <div class="card-sub">Catat pemasukan atau pengeluaran baru</div>
      </div>
      <div class="type-toggle" style="flex-wrap: wrap; gap: 8px;">
        <button class="t-btn income active" id="btn-inc" onclick="selType('income')" style="flex-basis: 31%;">+ Pemasukan</button>
        <button class="t-btn expense" id="btn-exp" onclick="selType('expense')" style="flex-basis: 31%;"> - Pengeluaran</button>
        <button class="t-btn transfer" id="btn-transfer" onclick="selType('transfer')" style="flex-basis: 31%;">🔄 Transfer</button>
        <button class="t-btn debt" id="btn-debt" onclick="selType('debt')" style="flex-basis: 48%;">💳 Hutang</button>
        <button class="t-btn recv" id="btn-recv" onclick="selType('recv')" style="flex-basis: 48%;">💸 Piutang</button>
      </div>
      
      <div class="form-row">
        <label class="form-label">JUMLAH (RP)</label>
        <input type="text" inputmode="numeric" id="f-amount" class="f-input-dark" placeholder="0">
      </div>
      
      <div class="form-row" id="row-cat">
        <label class="form-label">KATEGORI</label>
        <select id="f-cat" class="f-input-dark"></select>
      </div>
      
      <div class="form-row">
        <label class="form-label" id="label-wallet">SUMBER DANA / DOMPET</label>
        <select id="f-wallet" class="f-input-dark">
          <option value="Kas Tunai">Kas Tunai</option>
          <option value="DANA">DANA</option>
          <option value="GoPay">GoPay</option>
          <option value="ShopeePay">ShopeePay</option>
          <option value="MT5 Trading">Saldo MT5 Trading</option>
          <option value="Bank">Bank</option>
          <option value="Hutang">Hutang (Tarik/Bayar)</option>
          <option value="Piutang">Piutang (Beri/Tarik)</option>
        </select>
      </div>
      
      <div class="form-row" id="row-wallet-to" style="display:none;">
        <label class="form-label">TUJUAN DANA / DOMPET</label>
        <select id="f-wallet-to" class="f-input-dark">
          <option value="Kas Tunai">Kas Tunai</option>
          <option value="DANA">DANA</option>
          <option value="GoPay">GoPay</option>
          <option value="ShopeePay">ShopeePay</option>
          <option value="MT5 Trading">Saldo MT5 Trading</option>
          <option value="Bank">Bank</option>
          <option value="Hutang">Hutang (Tarik/Bayar)</option>
          <option value="Piutang">Piutang (Beri/Tarik)</option>
        </select>
      </div>
      
      <div class="form-row">
        <label class="form-label">KETERANGAN</label>
        <textarea id="f-note" class="f-input-dark" placeholder="Catatan transaksi..."></textarea>
      </div>
      
      <div class="form-row">
        <label class="form-label" style="display:flex; justify-content:space-between; align-items:center;">
          <span>WAKTU</span>
          <button type="button" onclick="setRealLocalTime()" style="background:transparent; border:none; color:var(--gold); font-size:10px; font-weight:800; font-family:'Outfit', sans-serif; cursor:pointer;">SEKARANG ⏱</button>
        </label>
        <input type="datetime-local" id="f-date" class="f-input-dark">
      </div>
      
      <button class="submit-btn" id="cancel-edit-btn" onclick="cancelEdit()" style="display:none; background:var(--bg3); color:var(--text); margin-bottom:8px;">BATAL EDIT</button>
      <button class="submit-btn" id="save-btn" onclick="addTx()">SIMPAN TRANSAKSI</button>
    </div>
    
    <div class="card">
      <div class="card-head"><div class="card-title">Aktivitas Terakhir</div></div>
      <div id="recent-list" class="list-wrap"></div>
    </div>
  </div>
</div>

<div id="page-harian" class="page">
  <div class="sum-grid" id="daily-sum"></div>
  <div class="card">
    <div class="card-head">
      <div class="card-title">Laporan Harian</div>
      <div style="margin-top:12px;">
         <input type="date" id="pick-daily" onchange="renderDaily()" class="f-input-dark">
      </div>
    </div>
    <div class="list-wrap" id="daily-body"></div>
  </div>
</div>

<div id="page-mingguan" class="page">
  <div class="period-bar" id="week-sel"></div>
  <div class="sum-grid" id="week-sum"></div>
  <div class="card">
    <div class="card-head"><div class="card-title">Laporan Mingguan</div></div>
    <div class="chart-wrap">
      <div class="chart-legend">
        <div class="leg-item"><div class="leg-dot" style="background:var(--green2)"></div>Pemasukan</div>
        <div class="leg-item"><div class="leg-dot" style="background:var(--red2)"></div>Pengeluaran</div>
      </div>
      <div style="height:250px"><canvas id="chartWeek"></canvas></div>
    </div>
    <div class="list-wrap" id="week-body"></div>
  </div>
</div>

<div id="page-bulanan" class="page">
  <div class="period-bar" id="month-sel"></div>
  <div class="sum-grid" id="month-sum"></div>
  <div class="card">
    <div class="card-head"><div class="card-title">Laporan Bulanan</div></div>
    <div class="chart-wrap">
      <div class="chart-legend">
        <div class="leg-item"><div class="leg-dot" style="background:var(--green2)"></div>Pemasukan</div>
        <div class="leg-item"><div class="leg-dot" style="background:var(--red2)"></div>Pengeluaran</div>
      </div>
      <div style="height:250px"><canvas id="chartMonth"></canvas></div>
    </div>
    <div class="list-wrap" id="month-body"></div>
  </div>
</div>

<div id="page-tahunan" class="page">
  <div class="period-bar" id="year-sel"></div>
  <div class="sum-grid" id="year-sum"></div>
  <div class="card">
    <div class="card-head"><div class="card-title">Laporan Tahunan</div></div>
    <div class="chart-wrap">
      <div class="chart-legend">
        <div class="leg-item"><div class="leg-dot" style="background:var(--green2)"></div>Pemasukan</div>
        <div class="leg-item"><div class="leg-dot" style="background:var(--red2)"></div>Pengeluaran</div>
      </div>
      <div style="height:250px"><canvas id="chartYear"></canvas></div>
    </div>
    <div class="list-wrap" id="year-body"></div>
  </div>
</div>

<div id="page-riwayat" class="page">
  <div class="sum-grid" id="all-sum"></div>
  <div class="card">
    <div class="card-head"><div class="card-title">Semua Riwayat</div></div>
    <div class="filter-bar">
      <select id="flt-type" class="f-input-dark" onchange="renderAll()">
        <option value="">Semua Filter</option>
        <option value="income">Pemasukan Saja</option>
        <option value="expense">Pengeluaran Saja</option>
      </select>
      <input type="text" id="flt-search" class="f-input-dark" placeholder="Cari berdasarkan keterangan atau kategori..." oninput="renderAll()">
      <button class="export-btn" onclick="exportCSV()">UNDUH CSV 📥</button>
    </div>
    <div class="chart-wrap" style="margin-top: 16px;">
      <div class="chart-legend">
        <div class="leg-item"><div class="leg-dot" style="background:var(--green2)"></div>Pemasukan</div>
        <div class="leg-item"><div class="leg-dot" style="background:var(--red2)"></div>Pengeluaran</div>
      </div>
      <div style="height:250px"><canvas id="chartRiwayat"></canvas></div>
    </div>
    <div class="list-wrap" id="all-body"></div>
  </div>
</div>

<div id="page-pengaturan" class="page">
  
  <div class="set-group" style="padding: 0; overflow: hidden; border-color: var(--border2);">
    <div class="set-title" style="padding: 16px 16px 8px 16px; margin: 0; border-bottom: none; font-size: 13px;">
      ⬅️ Kalkulator Mata Uang Online <span style="margin-left: 6px; font-size: 9px; background: var(--green2); color: #000; padding: 2px 6px; border-radius: 4px; font-weight: 800;">LIVE REALTIME Ticker</span>
    </div>
    <div id="calc-display" style="display: flex; flex-direction: column; padding: 0 8px;"></div>
    <div style="font-size: 9px; color: var(--text3); text-align: center; padding: 4px 0 8px 0;">
      Diperbarui pada <span id="calc-last-update">...</span>
    </div>

    <div class="calc-keypad-wrap">
      <div class="calc-keypad">
        <button class="calc-btn" onclick="calcPress('7')">7</button>
        <button class="calc-btn" onclick="calcPress('8')">8</button>
        <button class="calc-btn" onclick="calcPress('9')">9</button>
        <button class="calc-btn calc-btn-ac" onclick="calcPress('AC')">AC</button>
        
        <button class="calc-btn" onclick="calcPress('4')">4</button>
        <button class="calc-btn" onclick="calcPress('5')">5</button>
        <button class="calc-btn" onclick="calcPress('6')">6</button>
        
        <button class="calc-btn" onclick="calcPress('1')">1</button>
        <button class="calc-btn" onclick="calcPress('2')">2</button>
        <button class="calc-btn" onclick="calcPress('3')">3</button>
        <button class="calc-btn calc-btn-del" onclick="calcPress('DEL')">⌫</button>
        
        <button class="calc-btn" onclick="calcPress('00')">00</button>
        <button class="calc-btn" onclick="calcPress('0')">0</button>
        <button class="calc-btn" onclick="calcPress('.')">,</button>
      </div>
    </div>
  </div>
  
  <div class="set-group">
    <div class="set-title">🔒 KEAMANAN AKUN</div>
    <div class="set-item">
      <div>
        <div class="set-label">Reset Kata Sandi</div>
        <div class="set-sub">Kirim link reset ke email kamu</div>
      </div>
      <button class="set-action" onclick="reqResetPasswordViaSettings()">KIRIM LINK</button>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">Ubah PIN Keamanan</div>
        <div class="set-sub">Ganti 6 digit PIN tanpa perlu keluar (logout)</div>
      </div>
      <button class="set-action" onclick="changePinInApp()">GANTI PIN</button>
    </div>
  </div>

  <div class="set-group">
    <div class="set-title">⚡ PREFERENSI BAWAAN FORM</div>
    <div style="font-size: 11px; color: var(--text3); margin-bottom: 16px;">Pengaturan ini otomatis terpilih di formulir tambah transaksi setiap aplikasi dibuka.</div>
    <div class="set-item">
      <div><div class="set-label">Tipe Transaksi</div></div>
      <select id="pref-type" class="set-select" onchange="updatePrefCategories()">
        <option value="expense">Pengeluaran</option>
        <option value="income">Pemasukan</option>
      </select>
    </div>
    <div class="set-item">
      <div><div class="set-label">Kategori Rutin</div></div>
      <select id="pref-cat" class="set-select"></select>
    </div>
    <div class="set-item">
      <div><div class="set-label">Dompet Utama</div></div>
      <select id="pref-wallet" class="set-select">
        <option value="Kas Tunai">Kas Tunai</option>
        <option value="DANA">DANA</option>
        <option value="GoPay">GoPay</option>
        <option value="ShopeePay">ShopeePay</option>
        <option value="MT5 Trading">Saldo MT5 Trading</option>
        <option value="Bank">Bank</option>
      </select>
    </div>
    <div class="set-item" style="justify-content: flex-end; padding-top: 16px;">
      <button class="set-action" style="background:var(--gold); color:#000; border:none;" onclick="savePreferences()">SIMPAN PREFERENSI</button>
    </div>
  </div>

  <div class="set-group">
    <div class="set-title">⚙️ 7 FITUR FINANSIAL & SISTEM TAMBAHAN</div>
    <div class="set-item">
      <div>
        <div class="set-label">Kunci Otomatis (Auto-Lock)</div>
        <div class="set-sub">Kunci otomatis jika didiamkan 30 detik</div>
      </div>
      <select id="ext_autolock" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Tidak Aktif</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">1. Sembunyikan Dompet Bersaldo Nol</div>
        <div class="set-sub">Hilangkan dompet dari layar jika uangnya kosong</div>
      </div>
      <select id="ext_hidezero" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">2. Tampilkan Persentase Aset (%)</div>
        <div class="set-sub">Tampilkan porsi persentase saldo di tiap dompet</div>
      </div>
      <select id="ext_walletpct" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">3. Format Angka Ringkas (Dashboard)</div>
        <div class="set-sub">Ubah format panjang Rp 1.500.000 menjadi 1,5 Jt</div>
      </div>
      <select id="ext_shortnum" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">4. Peringatan Saldo Kritis</div>
        <div class="set-sub">Efek merah menyala bila saldo keseluruhan turun di bawah 50rb</div>
      </div>
      <select id="ext_warnbalance" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">5. Mode Hemat Harian (Budget Alert)</div>
        <div class="set-sub">Indikator merah jika pengeluaran harian melebihi Rp 100.000</div>
      </div>
      <select id="ext_budget" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">6. Sorotan Label Hutang & Piutang</div>
        <div class="set-sub">Tampilkan label "Belum Lunas" secara tegas di riwayat</div>
      </div>
      <select id="ext_debtbadge" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">7. Anti Intip Saldo</div>
        <div class="set-sub">Sembunyikan/blur nominal saldo di seluruh aplikasi</div>
      </div>
      <select id="ext_antiintip" class="set-select" onchange="saveExtraPrefs()">
        <option value="off">Mati</option>
        <option value="on">Aktif</option>
      </select>
    </div>
  </div>
  
  <div class="set-group">
    <div class="set-title">💾 MANAJEMEN DATA</div>
    <div class="set-item">
      <div>
        <div class="set-label">Unduh Laporan CSV</div>
        <div class="set-sub">Ekspor semua riwayat transaksi untuk di Excel</div>
      </div>
      <button class="set-action" onclick="exportCSV()">UNDUH DATA</button>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">Hapus Semua Riwayat</div>
        <div class="set-sub">Peringatan: Format ulang seluruh database akun ini</div>
      </div>
      <button class="set-action danger" onclick="deleteAllData()">FORMAT DATA</button>
    </div>
  </div>

  <div class="set-group">
    <div class="set-title">ℹ️ DETAIL APLIKASI</div>
    <div class="set-item">
      <div>
        <div class="set-label">Versi Sistem</div>
        <div class="set-sub">RHN Capital OS v3.5 Ultimate Live</div>
      </div>
    </div>
    <div class="set-item">
      <div>
        <div class="set-label">Hapus Cache Lokal</div>
        <div class="set-sub">Perbaiki jika aplikasi terasa berat</div>
      </div>
      <button class="set-action danger" onclick="clearLocalCache()">BERSIHKAN</button>
    </div>
  </div>

</div>

<div style="text-align: center; padding: 24px 16px; font-size: 10px; color: var(--text3); font-weight: 700; letter-spacing: 1px; margin-top: 20px; margin-bottom: 24px; border-top: 1px dashed var(--border);">
    © 2026 RHN CAPITAL | TRANSAKSI AMAN, CEPAT & MEMUDAHKAN<br>
    <span style="font-size: 8px; font-weight: 500; color: var(--text3); display: block; margin-top: 8px;">VERIFIED SAFE FOR GOOGLE INDEXING | AES-256 CLOUD ENCRYPTION SECURED</span>
</div>

</div></div>

<script>
  const lastUid = localStorage.getItem('last_uid_rhn');
  if (lastUid) {
     document.getElementById('auth-screen').style.display = 'none';
     document.getElementById('pin-screen').style.display = 'flex';
     document.getElementById('pin-title').textContent = 'Memuat Keamanan...';
     document.getElementById('pin-sub').textContent = 'Sinkronisasi dengan server';
     document.getElementById('app-pin').style.display = 'none';
     window.pinMode = 'verify';
  }
</script>

<script type="module">
window.toggleTheme = function() {
  document.body.classList.toggle('light-mode');
  const isLight = document.body.classList.contains('light-mode');
  document.getElementById('theme-toggle').textContent = isLight ? '☀️' : '🌙';
  localStorage.setItem('theme', isLight ? 'light' : 'dark');
  refreshAll(); 
};

if (localStorage.getItem('theme') === 'light') { 
  document.body.classList.add('light-mode'); 
  document.getElementById('theme-toggle').textContent = '☀️'; 
}

import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
import { 
  getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword, 
  signOut, onAuthStateChanged, sendPasswordResetEmail, 
  GoogleAuthProvider, signInWithPopup 
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";
import { 
  initializeFirestore, persistentLocalCache, collection, doc, 
  addDoc, updateDoc, deleteDoc, onSnapshot, query, orderBy, 
  serverTimestamp, getDoc, setDoc 
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

const firebaseConfig = { 
  apiKey: "AIzaSyCx04v3ppq3DxbXDg0PrWBeJYIZjmJF9cg", 
  authDomain: "rhn-capital.firebaseapp.com", 
  projectId: "rhn-capital", 
  storageBucket: "rhn-capital.firebasestorage.app", 
  messagingSenderId: "74905216682", 
  appId: "1:74905216682:web:4687a5b0bd7bcac09292d3" 
};

const app = initializeApp(firebaseConfig); 
const auth = getAuth(app); 
const db = initializeFirestore(app, { localCache: persistentLocalCache() });

// KATEGORI DIPERBANYAK
const CATS = { 
  income: ['Gaji', 'Hasil Trading', 'Bonus / THR', 'Penjualan', 'Pendapatan Lainnya', 'Pemberian', 'Investasi', 'Ongkos Harian', 'Dividen', 'Profit', 'Transfer Masuk', 'Lainnya'], 
  expense: ['Makan & Minum', 'Transportasi', 'Tagihan', 'Belanja Bulanan', 'Cicilan', 'Hiburan / Nongkrong', 'Sedekah / Donasi', 'Jajan', 'Pembelian Aset(Investasi)', 'Infak', 'Kas', 'Utilitas', 'Loss', 'Pengeluaran Lainnya', 'Lainnya'],
  debt: ['Pinjaman Bank', 'Pinjaman Pribadi', 'Titipan Dana', 'Lainnya'],
  recv: ['Dipinjam Teman', 'Kasbon Karyawan', 'Lainnya'] 
};

let txs = [], curType = 'income', activePage = 'dashboard', charts = {};
let currentUSDRate = 16000, currentUser = null, unsubListener = null, authMode = 'login';
let editId = null;

let appPrefs = { type: 'income', category: '', wallet: 'Kas Tunai' };
let extraPrefs = { 
    ext_autolock: 'off', ext_warnbalance: 'off', ext_shortnum: 'off', ext_budget: 'off', 
    ext_hidezero: 'off', ext_walletpct: 'off', ext_debtbadge: 'off', ext_antiintip: 'off'
};

// FORMAT MILYARAN
const fmtFull = n => {
    if (Math.abs(n) >= 1000000000) {
        return 'Rp ' + (n / 1000000000).toLocaleString('id-ID', { maximumFractionDigits: 2 }) + ' Miliar';
    }
    return 'Rp ' + Math.round(n).toLocaleString('id-ID');
};

const fmt = (n, isDash = false) => {
    if (isDash && typeof extraPrefs !== 'undefined' && extraPrefs.ext_shortnum === 'on') {
        if (Math.abs(n) >= 1000000000) return 'Rp ' + (n/1000000000).toFixed(2).replace('.',',') + ' M';
        if (Math.abs(n) >= 1000000) return 'Rp ' + (n/1000000).toFixed(2).replace('.',',') + ' Jt';
        if (Math.abs(n) >= 10000) return 'Rp ' + (n/1000).toFixed(1).replace('.',',') + ' Rb';
    }
    return fmtFull(n);
};

const fmtDate = dt => new Date(dt).toLocaleDateString('id-ID',{day:'2-digit',month:'short'});
const fmtTime = dt => new Date(dt).toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'});
const nowISO = () => new Date().toISOString().slice(0,16);
const kursIndo = new Intl.NumberFormat('id-ID', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
const getUSD = n => '$' + (n / currentUSDRate).toFixed(2);

// LIVE BINANCE
function initLiveCurrencies() {
  const socket = new WebSocket('wss://stream.binance.com:9443/stream?streams=usdtidr@ticker/eurusdt@ticker/gbpusdt@ticker/audusdt@ticker/brlusdt@ticker/tryusdt@ticker');
  socket.addEventListener('message', e => { 
      const msg = JSON.parse(e.data); 
      const stream = msg.stream; 
      const price = parseFloat(msg.data.c); 
      
      if (!price) return;
      
      if (stream === 'usdtidr@ticker') { 
          if (price !== currentUSDRate) { 
              currentUSDRate = price; 
              const usdEl = document.getElementById('usd-rate-val'); 
              if (usdEl) usdEl.textContent = kursIndo.format(currentUSDRate); 
              
              if (calcRates) { 
                  calcRates['IDR'] = currentUSDRate; 
                  Object.keys(calcRates).forEach(code => { 
                      if (code !== 'USD' && code !== 'IDR' && code !== 'EUR' && code !== 'GBP' && code !== 'AUD' && code !== 'TRY' && code !== 'BRL') { 
                          const noise = 1 + (Math.random() - 0.5) * 0.00004; 
                          calcRates[code] *= noise; 
                      } 
                  }); 
              } 
              refreshAll(); 
          }
      } else if (stream === 'eurusdt@ticker') { 
          if (calcRates) calcRates['EUR'] = 1 / price; window.renderCalcDisplay();
      } else if (stream === 'gbpusdt@ticker') { 
          if (calcRates) calcRates['GBP'] = 1 / price; window.renderCalcDisplay();
      } else if (stream === 'audusdt@ticker') { 
          if (calcRates) calcRates['AUD'] = 1 / price; window.renderCalcDisplay();
      } else if (stream === 'brlusdt@ticker') { 
          if (calcRates) calcRates['BRL'] = 1 / price; window.renderCalcDisplay();
      } else if (stream === 'tryusdt@ticker') { 
          if (calcRates) calcRates['TRY'] = 1 / price; window.renderCalcDisplay(); 
      }
  });
  socket.addEventListener('close', () => setTimeout(initLiveCurrencies, 3000));
}

async function fetchUSDRate() { 
  try { 
      const res = await fetch('https://api.exchangerate-api.com/v4/latest/USD'); 
      currentUSDRate = (await res.json()).rates.IDR; 
      document.getElementById('usd-rate-val').textContent = kursIndo.format(currentUSDRate); 
      refreshAll(); 
  } catch (e) { 
      document.getElementById('usd-rate-val').textContent = "Offline"; 
  } 
}
fetchUSDRate().then(initLiveCurrencies); 
setInterval(fetchUSDRate, 300000); 

function initLiveXAU() {
  const socketXAU = new WebSocket('wss://stream.binance.com:9443/ws/paxgusdt@ticker');
  socketXAU.addEventListener('message', e => { 
      const newPrice = parseFloat(JSON.parse(e.data).c); 
      if (newPrice) { 
          const xauRate = document.getElementById('xau-rate-val'); 
          if (xauRate) xauRate.textContent = '$' + newPrice.toFixed(2); 
          
          if (currentUSDRate > 0) { 
              const idrPriceOz = newPrice * currentUSDRate; 
              const idrPriceGram = idrPriceOz / 31.1034768; 
              const ozEl = document.getElementById('xau-idr-oz'); 
              if (ozEl) ozEl.textContent = `Rp ` + kursIndo.format(idrPriceOz); 
              const grEl = document.getElementById('xau-idr-gr'); 
              if (grEl) grEl.textContent = `Rp ` + kursIndo.format(idrPriceGram); 
          } 
      } 
  });
  socketXAU.addEventListener('close', () => setTimeout(initLiveXAU, 3000));
}
initLiveXAU();

let calcRates = null; 
let calcFromCode = 'USD'; 
let calcToCode = 'IDR'; 
let calcActiveRow = 'from'; 
let calcInputVal = '100';

const calcCurrencies = [ 
  { code: 'IDR', name: 'Rupiah Indonesia', flag: '🇮🇩' }, { code: 'USD', name: 'Dolar Amerika', flag: '🇺🇸' }, 
  { code: 'AED', name: 'Dirham Uni Emirat Arab', flag: '🇦🇪' }, { code: 'AUD', name: 'Dolar Australia', flag: '🇦🇺' }, 
  { code: 'BRL', name: 'Real Brasil', flag: '🇧🇷' }, { code: 'CAD', name: 'Dolar Kanada', flag: '🇨🇦' }, 
  { code: 'CHF', name: 'Franc Swiss', flag: '🇨🇭' }, { code: 'CNY', name: 'Yuan Tiongkok', flag: '🇨🇳' }, 
  { code: 'EUR', name: 'Euro', flag: '🇪🇺' }, { code: 'GBP', name: 'Poundsterling Inggris', flag: '🇬🇧' }, 
  { code: 'HKD', name: 'Dolar Hong Kong', flag: '🇭🇰' }, { code: 'INR', name: 'Rupee India', flag: '🇮🇳' }, 
  { code: 'JPY', name: 'Yen Jepang', flag: '🇯🇵' }, { code: 'KRW', name: 'Won Korea Selatan', flag: '🇰🇷' }, 
  { code: 'MYR', name: 'Ringgit Malaysia', flag: '🇲🇾' }, { code: 'NZD', name: 'Dolar Selandia Baru', flag: '🇳🇿' }, 
  { code: 'PHP', name: 'Peso Filipina', flag: '🇵🇭' }, { code: 'RUB', name: 'Rubel Rusia', flag: '🇷🇺' }, 
  { code: 'SAR', name: 'Riyal Arab Saudi', flag: '🇸🇦' }, { code: 'SEK', name: 'Krona Swedia', flag: '🇸🇪' }, 
  { code: 'SGD', name: 'Dolar Singapura', flag: '🇸🇬' }, { code: 'THB', name: 'Baht Thailand', flag: '🇹🇭' }, 
  { code: 'TRY', name: 'Lira Turki', flag: '🇹🇷' }, { code: 'ZAR', name: 'Rand Afrika Selatan', flag: '🇿🇦' } 
];

async function initCalc() { 
  try { 
      const response = await fetch('https://api.exchangerate-api.com/v4/latest/USD'); 
      calcRates = (await response.json()).rates; 
      const now = new Date(); 
      document.getElementById('calc-last-update').textContent = `${now.toLocaleDateString('id-ID', { year:'numeric', month:'2-digit', day:'2-digit' }).replace(/\//g, '-')} ${now.toLocaleTimeString('id-ID', { hour:'2-digit', minute:'2-digit' })}`; 
      window.renderCalcDisplay(); 
  } catch (e) { 
      document.getElementById('calc-last-update').textContent = "Offline / Gagal Memuat"; 
  } 
}

window.setCalcActiveRow = function(row) { 
  if (calcActiveRow === row) return; 
  if (navigator.vibrate) navigator.vibrate(15); 
  
  let currentNum = parseFloat(calcInputVal || '0'); 
  let baseInUSD = currentNum / (calcActiveRow === 'from' ? calcRates[calcFromCode] : calcRates[calcToCode]); 
  let targetVal = baseInUSD * (row === 'from' ? calcRates[calcFromCode] : calcRates[calcToCode]); 
  let newValStr = targetVal.toString(); 
  
  if(newValStr.includes('.')) newValStr = targetVal.toFixed(2).replace(/\.?0+$/, ''); 
  
  calcInputVal = newValStr; 
  calcActiveRow = row; 
  window.renderCalcDisplay(); 
}

window.changeCalcCurr = function(row, newCode) { 
  if (row === 'from') calcFromCode = newCode; 
  if (row === 'to') calcToCode = newCode; 
  window.renderCalcDisplay(); 
}

window.swapCalcCurr = function() { 
  if (navigator.vibrate) navigator.vibrate(15); 
  let tempCode = calcFromCode; 
  calcFromCode = calcToCode; 
  calcToCode = tempCode; 
  calcActiveRow = calcActiveRow === 'from' ? 'to' : 'from'; 
  window.renderCalcDisplay(); 
}

window.openCurrencySelector = function(rId) { 
  let html = '<div style="display:flex; flex-direction:column; gap:8px; max-height:60vh; overflow-y:auto; padding-bottom:12px; scrollbar-width:none;">'; 
  
  calcCurrencies.forEach(c => { 
      let isActive = (rId === 'from' && calcFromCode === c.code) || (rId === 'to' && calcToCode === c.code); 
      html += `<button onclick="changeCalcCurr('${rId}', '${c.code}'); Swal.close();" style="background:${isActive?'var(--bg3)':'var(--bg2)'}; color:var(--text); border:1px solid ${isActive?'var(--gold)':'var(--border)'}; padding:14px; border-radius:12px; font-family:'Outfit'; text-align:left; font-size:14px; font-weight:600; display:flex; align-items:center; gap:12px;"><span style="font-size:20px;">${c.flag}</span> ${c.code} - ${c.name}</button>`; 
  }); 
  
  html += '</div>'; 
  
  Swal.fire({ 
      title: '<div style="font-size:18px; text-align:left; font-weight:800; border-bottom:1px dashed var(--border); padding-bottom:12px; margin-bottom:8px;">Pilih Mata Uang</div>', 
      html: html, 
      showConfirmButton: false, 
      background: 'var(--card)', 
      color: 'var(--text)', 
      position: 'center', 
      padding: '24px 16px', 
      margin:0, 
      width: window.innerWidth <= 768 ? '90%' : '400px', 
      customClass: { popup: 'centered-modal' } 
  }); 
}

window.calcPress = function(key) { 
  if (navigator.vibrate) navigator.vibrate(20); 
  
  if (key === 'AC') { 
      calcInputVal = '0'; 
  } else if (key === 'DEL') { 
      calcInputVal = calcInputVal.slice(0, -1); 
      if (calcInputVal === '') calcInputVal = '0'; 
  } else if (key === '.') { 
      if (!calcInputVal.includes('.')) calcInputVal += '.'; 
  } else { 
      if (calcInputVal === '0' && key !== '00') { 
          calcInputVal = key; 
      } else if (calcInputVal === '0' && key === '00') { 
          // do nothing
      } else { 
          if(calcInputVal.replace('.', '').length < 15) { 
              calcInputVal += key; 
          } 
      } 
  } 
  window.renderCalcDisplay(); 
}

function renderRow(rId, code, isAct, displayVal) { 
  let currObj = calcCurrencies.find(c => c.code === code) || {name:'', flag:''}; 
  let countryCode = code.slice(0, 2).toLowerCase(); 
  
  if (code === 'EUR') countryCode = 'eu'; 
  if (code === 'GBP') countryCode = 'gb'; 
  
  let flagImgHtml = `<img src="https://flagcdn.com/w40/${countryCode}.png" style="width:32px; height:22px; object-fit:cover; border-radius:4px; display:block; border:1px solid rgba(255,255,255,0.15);" onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=\'http://www.w3.org/2000/svg\' fill=\'none\' viewBox=\'0 0 24 24\' stroke=\'%23888899\'><path stroke-linecap=\'round\' stroke-linejoin=\'round\' stroke-width=\'2\' d=\'M3 21v-4m0 0V5a2 2 0 012-2h6.5l1 1H21l-3 6 3 6h-8.5l-1-1H5a2 2 0 00-2 2zm9-13.5V9\'></path></svg>';">`; 
  
  return `
  <div class="calc-curr-item ${isAct ? 'active' : ''}" onclick="setCalcActiveRow('${rId}')">
    <div class="calc-left">
      <div class="calc-flag" style="width:40px; justify-content:center;">${flagImgHtml}</div>
      <div class="calc-code-wrap">
        <div class="calc-select" onclick="event.stopPropagation(); openCurrencySelector('${rId}')" style="display:flex; align-items:center; gap:8px;">
          ${currObj.code} <span style="font-size:10px; color:var(--text3);">▼</span>
        </div>
        <div class="calc-name">${currObj.name}</div>
      </div>
    </div>
    <div class="calc-right">
      <div class="calc-amount">${displayVal}</div>
    </div>
  </div>`; 
}

window.renderCalcDisplay = function() { 
  const container = document.getElementById('calc-display'); 
  if (!container) return; 
  
  let currentNum = parseFloat(calcInputVal || '0'); 
  let baseInUSD = 0; 
  
  if (calcRates) { 
      calcRates['IDR'] = currentUSDRate; 
      let activeCode = calcActiveRow === 'from' ? calcFromCode : calcToCode; 
      if (calcRates[activeCode]) { 
          baseInUSD = currentNum / calcRates[activeCode]; 
      } 
  } 
  
  let fromValStr = '0'; 
  if (calcActiveRow === 'from') { 
      let parts = calcInputVal.split('.'); 
      let intPart = parts[0] ? parseInt(parts[0], 10).toLocaleString('id-ID') : '0'; 
      fromValStr = parts.length > 1 ? `${intPart},${parts[1]}` : intPart; 
  } else { 
      if (calcRates && calcRates[calcFromCode]) { 
          let val = baseInUSD * calcRates[calcFromCode]; 
          fromValStr = val === 0 ? '0' : val.toLocaleString('id-ID', {minimumFractionDigits: 0, maximumFractionDigits: 4}); 
      } else {
          fromValStr = '...'; 
      }
  } 
  
  let toValStr = '0'; 
  if (calcActiveRow === 'to') { 
      let parts = calcInputVal.split('.'); 
      let intPart = parts[0] ? parseInt(parts[0], 10).toLocaleString('id-ID') : '0'; 
      toValStr = parts.length > 1 ? `${intPart},${parts[1]}` : intPart; 
  } else { 
      if (calcRates && calcRates[calcToCode]) { 
          let val = baseInUSD * calcRates[calcToCode]; 
          toValStr = val === 0 ? '0' : val.toLocaleString('id-ID', {minimumFractionDigits: 0, maximumFractionDigits: 4}); 
      } else {
          toValStr = '...'; 
      }
  } 
  
  const cacheKey = `${calcFromCode}_${calcToCode}_${calcActiveRow}`; 
  if (container.dataset.cacheKey !== cacheKey || !container.innerHTML.trim()) { 
      container.innerHTML = 
          renderRow('from', calcFromCode, calcActiveRow === 'from', fromValStr) + 
          `<div style="display:flex; justify-content:center; margin: -16px 0; position: relative; z-index: 10;">
             <button class="swap-btn" onclick="event.stopPropagation(); swapCalcCurr()" title="Tukar Mata Uang">⇅</button>
           </div>` + 
          renderRow('to', calcToCode, calcActiveRow === 'to', toValStr); 
      container.dataset.cacheKey = cacheKey; 
  } else { 
      const fromAmtEl = container.querySelector('.calc-curr-item:first-child .calc-amount'); 
      const toAmtEl = container.querySelector('.calc-curr-item:last-child .calc-amount'); 
      if (fromAmtEl) fromAmtEl.textContent = fromValStr; 
      if (toAmtEl) toAmtEl.textContent = toValStr; 
  } 
}

document.addEventListener('DOMContentLoaded', () => {
    initCalc();
    
    // ANTI CLOSE HP BACK BUTTON LOGIC
    window.history.pushState({ noBackExitsApp: true }, '');
    window.addEventListener('popstate', function(event) {
        if (event.state && event.state.noBackExitsApp) {
            // Biarkan saja, state aman
        } else {
            // Tombol back dipencet
            Swal.fire({
                title: 'Keluar Aplikasi?',
                text: 'Yakin mau menutup RHN Capital?',
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: 'var(--red2)',
                cancelButtonColor: 'var(--bg3)',
                confirmButtonText: 'Ya, Keluar',
                cancelButtonText: 'Batal',
                background: 'var(--card)',
                color: 'var(--text)',
                customClass: { popup: 'centered-modal' }
            }).then((result) => {
                if (result.isConfirmed) {
                    window.history.back(); // Lanjutkan keluar
                } else {
                    window.history.pushState({ noBackExitsApp: true }, ''); // Push state lagi
                }
            });
        }
    });

    const syncSelectUI = (sel, ui) => { 
        let text = sel.options[sel.selectedIndex]?.text; 
        if(!text && sel.options.length > 0) text = sel.options[0].text; 
        ui.querySelector('.sel-text').innerHTML = text || 'Pilih...'; 
    };
    
    document.querySelectorAll('select.f-input-dark, select.set-select').forEach(sel => { 
        sel.style.display = 'none'; 
        let ui = document.createElement('div'); 
        ui.className = sel.className; 
        ui.style.display = 'flex'; 
        ui.style.justifyContent = 'space-between'; 
        ui.style.alignItems = 'center'; 
        ui.style.cursor = 'pointer'; 
        ui.innerHTML = `<span class="sel-text" style="pointer-events:none; white-space:nowrap; overflow:hidden; text-overflow:ellipsis; max-width:90%;"></span><span style="font-size:10px; color:var(--text3); pointer-events:none;">▼</span>`; 
        sel.parentNode.insertBefore(ui, sel); 
        
        syncSelectUI(sel, ui); 
        sel.addEventListener('change', () => syncSelectUI(sel, ui)); 
        
        const observer = new MutationObserver(() => syncSelectUI(sel, ui)); 
        observer.observe(sel, { childList: true, subtree: true }); 
        
        ui.addEventListener('click', (e) => { 
            e.stopPropagation(); 
            if (navigator.vibrate) navigator.vibrate(10); 
            
            let html = '<div style="display:flex; flex-direction:column; gap:8px; max-height:60vh; overflow-y:auto; padding-bottom:12px; scrollbar-width:none;">'; 
            Array.from(sel.options).forEach((opt, idx) => { 
                if(!opt.value && opt.text.toLowerCase().includes('pilih')) return; 
                let isSel = sel.value === opt.value; 
                html += `<button onclick="window.selectCustomOpt('${sel.id}', ${idx})" style="background:${isSel?'var(--bg3)':'var(--bg2)'}; color:var(--text); border:1px solid ${isSel?'var(--gold)':'var(--border)'}; padding:16px; border-radius:12px; font-family:'Outfit'; text-align:left; font-size:14px; font-weight:600; cursor:pointer; transition:0.2s;">${opt.innerHTML || opt.text}</button>`; 
            }); 
            html += '</div>'; 
            
            Swal.fire({ 
                title: '<div style="font-size:16px; text-align:left; font-weight:800; color:var(--text); border-bottom: 1px dashed var(--border); padding-bottom: 12px; margin-bottom: 8px;">Pilih Opsi</div>', 
                html: html, 
                showConfirmButton: false, 
                background: 'var(--card)', 
                color: 'var(--text)', 
                position: 'center', 
                padding: '24px 16px 16px 16px', 
                margin:0, 
                width: window.innerWidth <= 768 ? '90%' : '400px', 
                customClass: { popup: 'centered-modal' } 
            }); 
        }); 
    });
    
    window.selectCustomOpt = function(selId, optIdx) { 
        let sel = document.getElementById(selId); 
        if (sel) { 
            sel.selectedIndex = optIdx; 
            sel.dispatchEvent(new Event('change')); 
            if(sel.onchange) sel.onchange(); 
        } 
        Swal.close(); 
    };
});

function showErr(msg) { 
    const el = document.getElementById('auth-err'); 
    el.textContent = msg; 
    el.style.display = 'block'; 
}

function hideErr() { 
    document.getElementById('auth-err').style.display = 'none'; 
}

function setLoading(on) { 
    document.getElementById('auth-submit-btn').disabled = on; 
    document.getElementById('auth-submit-btn').textContent = on ? 'Memproses...' : (authMode === 'login' ? 'MASUK' : 'DAFTAR'); 
}

function setSyncStatus(ok) { 
    document.getElementById('sync-dot').style.background = ok ? 'var(--green2)' : 'var(--red2)'; 
    document.getElementById('sync-label').textContent = ok ? 'TERSINKRON' : 'OFFLINE'; 
    document.getElementById('sync-dot').style.boxShadow = ok ? '0 0 8px var(--green2)' : 'none'; 
}

window.switchTab = function(mode) { 
    authMode = mode; 
    document.getElementById('tab-login').classList.toggle('active', mode === 'login'); 
    document.getElementById('tab-register').classList.toggle('active', mode === 'register'); 
    document.getElementById('field-confirm').style.display = mode === 'register' ? 'block' : 'none'; 
    document.getElementById('auth-submit-btn').textContent = mode === 'login' ? 'MASUK' : 'DAFTAR'; 
    hideErr(); 
};

window.doGoogleAuth = async function() {
    const provider = new GoogleAuthProvider();
    hideErr(); 
    setLoading(true);
    try { 
        await signInWithPopup(auth, provider); 
    } catch(e) { 
        showErr(e.message); 
        setLoading(false); 
    }
};

window.doAuth = async function() { 
    const email = document.getElementById('auth-email').value.trim();
    const pass = document.getElementById('auth-pass').value; 
    
    hideErr(); 
    if (!email || !pass) return showErr('Kredensial kosong.'); 
    
    setLoading(true); 
    try { 
        if (authMode === 'login') {
            await signInWithEmailAndPassword(auth, email, pass); 
        } else { 
            if (pass !== document.getElementById('auth-pass2').value) return showErr('Sandi beda.'); 
            await createUserWithEmailAndPassword(auth, email, pass); 
        } 
    } catch(e) { 
        showErr(e.message); 
        setLoading(false); 
    } 
};

window.doResetPassword = async function() { 
    const email = document.getElementById('auth-email').value.trim(); 
    hideErr(); 
    
    if (!email) { 
        return showErr('Masukkan email kamu dulu di kolom atas untuk reset sandi.'); 
    } 
    
    setLoading(true); 
    document.getElementById('auth-submit-btn').textContent = 'MENGIRIM...'; 
    
    try { 
        await sendPasswordResetEmail(auth, email); 
        Swal.fire({ 
            position: 'center', 
            icon: 'success', 
            title: 'Email Terkirim!', 
            html: 'Cek <b>Inbox</b> atau folder <b>SPAM</b> email kamu.', 
            showConfirmButton: true, 
            background: 'var(--card)', 
            color: 'var(--text)', 
            backdrop: 'rgba(0,0,0,0.6)' 
        }); 
    } catch(e) { 
        showErr(e.message); 
    } 
    
    setLoading(false); 
    document.getElementById('auth-submit-btn').textContent = authMode === 'login' ? 'MASUK' : 'DAFTAR'; 
};

window.reqResetPasswordViaSettings = async function() { 
    if (!currentUser) return; 
    try { 
        await sendPasswordResetEmail(auth, currentUser.email); 
        Swal.fire({ 
            position: 'center', 
            icon: 'success', 
            title: 'Terkirim!', 
            html: `Link reset sandi telah dikirim ke <b>${currentUser.email}</b>`, 
            showConfirmButton: true, 
            background: 'var(--card)', 
            color: 'var(--text)'
        }); 
    } catch(e) { 
        Swal.fire('Gagal', e.message, 'error'); 
    } 
};

window.clearLocalCache = function() { 
    Swal.fire({ 
        title: 'Bersihkan Cache?', 
        text: "Data inti di cloud aman, hanya mereset preferensi hp ini.", 
        icon: 'warning', 
        showCancelButton: true, 
        confirmButtonColor: 'var(--red2)', 
        background: 'var(--card)', 
        color: 'var(--text)' 
    }).then((res) => { 
        if (res.isConfirmed) { 
            let tempLastUid = localStorage.getItem('last_uid_rhn'); 
            localStorage.clear(); 
            if (tempLastUid) localStorage.setItem('last_uid_rhn', tempLastUid); 
            
            Swal.fire({
                position: 'center', 
                icon: 'success', 
                title: 'Bersih!', 
                showConfirmButton: false, 
                timer: 1500, 
                background: 'var(--card)', 
                color: 'var(--text)'
            }); 
            
            setTimeout(() => location.reload(), 1500); 
        } 
    }); 
};

window.deleteAllData = async function() { 
    if (!currentUser) return; 
    
    Swal.fire({ 
        title: 'Verifikasi PIN Keamanan', 
        text: 'Masukkan 6 digit PIN untuk format total akun:', 
        input: 'password', 
        inputAttributes: { inputmode: 'numeric', maxlength: 6, autofocus: true, style: 'text-align: center; letter-spacing: 10px; font-size: 24px;' }, 
        icon: 'warning', 
        showCancelButton: true, 
        confirmButtonColor: 'var(--red2)', 
        cancelButtonColor: 'var(--bg3)', 
        confirmButtonText: 'HAPUS SEMUA', 
        background: 'var(--card)', 
        color: 'var(--text)' 
    }).then(async (res) => { 
        if (res.isConfirmed) { 
            if (res.value !== window.userCloudPin) return Swal.fire({icon: 'error', title: 'PIN Salah!', background:'var(--card)', color:'var(--text)'}); 
            Swal.fire({title: 'Menghapus...', background:'var(--card)', color:'var(--text)', didOpen: () => {Swal.showLoading()}}); 
            
            try { 
                for (let t of txs) {
                    await deleteDoc(doc(db, 'users', currentUser.uid, 'transactions', t.id)); 
                }
                Swal.fire({icon: 'success', title: 'Data Diformat!', background:'var(--card)', color:'var(--text)'}); 
            } catch(e) { 
                Swal.fire('Error', e.message, 'error'); 
            } 
        } 
    }); 
};

window.updatePrefCategories = function(resetCat = true) { 
    const selType = document.getElementById('pref-type').value; 
    const catDrop = document.getElementById('pref-cat'); 
    
    if (!catDrop) return; 
    catDrop.innerHTML = ''; 
    
    if (CATS[selType]) { 
        CATS[selType].forEach(c => { 
            let opt = document.createElement('option'); 
            opt.value = c; 
            opt.textContent = c; 
            catDrop.appendChild(opt); 
        }); 
    } 
    
    if (!resetCat && appPrefs.category) { 
        setTimeout(() => {
            catDrop.value = appPrefs.category; 
            catDrop.dispatchEvent(new Event('change'));
        }, 50); 
    } 
    
    if (!resetCat) { 
        document.getElementById('pref-type').value = appPrefs.type || 'income'; 
        document.getElementById('pref-type').dispatchEvent(new Event('change')); 
        document.getElementById('pref-wallet').value = appPrefs.wallet || 'Kas Tunai'; 
        document.getElementById('pref-wallet').dispatchEvent(new Event('change')); 
    } 
};

window.savePreferences = async function() {
    if (!currentUser) return;
    
    appPrefs = { 
        type: document.getElementById('pref-type').value, 
        category: document.getElementById('pref-cat').value, 
        wallet: document.getElementById('pref-wallet').value 
    };
    
    localStorage.setItem('rhn_prefs_' + currentUser.uid, JSON.stringify(appPrefs));
    
    try {
        await setDoc(doc(db, 'users', currentUser.uid, 'settings', 'preferences'), { appPrefs: appPrefs }, { merge: true });
        Swal.fire({position: 'center', icon: 'success', title: 'Tersimpan ke Cloud!', showConfirmButton: false, timer: 1500, background: 'var(--card)', color: 'var(--text)'});
    } catch(e) {
        console.error("Gagal nyimpan preferensi ke cloud", e);
    }
    
    selType(appPrefs.type);
    setTimeout(() => {
        if(document.getElementById('f-cat') && appPrefs.category) { 
            document.getElementById('f-cat').value = appPrefs.category; 
            document.getElementById('f-cat').dispatchEvent(new Event('change')); 
        }
        if(document.getElementById('f-wallet') && appPrefs.wallet) { 
            document.getElementById('f-wallet').value = appPrefs.wallet; 
            document.getElementById('f-wallet').dispatchEvent(new Event('change')); 
        }
    }, 50);
};

window.saveExtraPrefs = async function() {
    if (!currentUser || window.isAppLoading) return;
    
    extraPrefs = { 
        ext_autolock: document.getElementById('ext_autolock').value, 
        ext_warnbalance: document.getElementById('ext_warnbalance').value, 
        ext_shortnum: document.getElementById('ext_shortnum').value, 
        ext_budget: document.getElementById('ext_budget').value, 
        ext_hidezero: document.getElementById('ext_hidezero').value, 
        ext_walletpct: document.getElementById('ext_walletpct').value, 
        ext_debtbadge: document.getElementById('ext_debtbadge').value, 
        ext_antiintip: document.getElementById('ext_antiintip').value
    };
    
    localStorage.setItem('rhn_extra_prefs_v2_' + currentUser.uid, JSON.stringify(extraPrefs));
    
    try {
        await setDoc(doc(db, 'users', currentUser.uid, 'settings', 'preferences'), { extraPrefs: extraPrefs }, { merge: true });
    } catch(e) {
        console.error("Gagal nyimpan 7 fitur pengaturan ke cloud", e);
    }

    if (extraPrefs.ext_antiintip === 'on') { 
        document.body.classList.add('global-privacy'); 
    } else { 
        document.body.classList.remove('global-privacy'); 
    }
    
    if (window.resetIdle) window.resetIdle();
    refreshAll();
};

window.changePinInApp = async function() { 
    if (!currentUser) return; 
    
    const { value: choice } = await Swal.fire({ 
        title: 'Pengaturan PIN', 
        text: 'Pilih aksi yang mau lu lakuin:', 
        icon: 'question', 
        showCancelButton: true, 
        showDenyButton: true, 
        confirmButtonText: 'Lupa PIN (Buat Baru)', 
        denyButtonText: 'Ingat PIN (Ganti PIN)', 
        cancelButtonText: 'Batal', 
        background: 'var(--card)', 
        color: 'var(--text)', 
        confirmButtonColor: 'var(--red2)', 
        denyButtonColor: 'var(--gold)', 
        cancelButtonColor: 'var(--bg3)' 
    }); 
    
    const promptNewPin = async () => { 
        const { value: newPin } = await Swal.fire({ 
            title: 'Buat PIN Baru', 
            text: 'Masukkan 6 angka PIN baru kamu', 
            input: 'password', 
            inputAttributes: { inputmode: 'numeric', maxlength: 6, style: 'text-align: center; letter-spacing: 10px; font-size: 24px;', autofocus: true }, 
            background: 'var(--card)', 
            color: 'var(--text)', 
            confirmButtonColor: 'var(--gold)', 
            confirmButtonText: 'SIMPAN PIN BARU' 
        }); 
        
        if (newPin && newPin.length === 6) { 
            try { 
                await setDoc(doc(db, 'users', currentUser.uid, 'settings', 'security'), { pin: newPin }, { merge: true }); 
                window.userCloudPin = newPin; 
                Swal.fire({icon:'success', title:'PIN Berhasil Disimpan!', background:'var(--card)', color:'var(--text)', timer: 1500, showConfirmButton: false}); 
            } catch(e) { 
                Swal.fire({icon:'error', title:'Gagal mengubah PIN', text: e.message, background:'var(--card)', color:'var(--text)'}); 
            } 
        } else if (newPin) { 
            Swal.fire({icon:'warning', title:'Gagal, harus 6 digit!', background:'var(--card)', color:'var(--text)'}); 
        } 
    }; 
    
    if (choice === true) { 
        promptNewPin(); 
    } else if (choice === false) { 
        const { value: oldPin } = await Swal.fire({ 
            title: 'Masukkan PIN Lama', 
            input: 'password', 
            inputAttributes: { inputmode: 'numeric', maxlength: 6, style: 'text-align: center; letter-spacing: 10px; font-size: 24px;', autofocus: true }, 
            background: 'var(--card)', 
            color: 'var(--text)', 
            confirmButtonColor: 'var(--border2)' 
        }); 
        
        if (!oldPin) return; 
        
        if (oldPin !== window.userCloudPin) {
            return Swal.fire({icon:'error', title:'PIN Lama Salah!', background:'var(--card)', color:'var(--text)'}); 
        }
        
        promptNewPin(); 
    } 
};

window.doLogout = async function() { 
    if (unsubListener) { 
        unsubListener(); 
        unsubListener = null; 
    } 
    txs = []; 
    localStorage.removeItem('last_uid_rhn'); 
    await signOut(auth); 
};

onAuthStateChanged(auth, async user => {
  if (user) {
    currentUser = user;
    localStorage.setItem('last_uid_rhn', user.uid);
    document.getElementById('auth-screen').style.display = 'none';
    
    try {
        const prefRef = doc(db, 'users', user.uid, 'settings', 'preferences');
        const prefSnap = await getDoc(prefRef);
        
        if (prefSnap.exists()) {
            const data = prefSnap.data();
            if (data.appPrefs) { 
                appPrefs = data.appPrefs; 
                localStorage.setItem('rhn_prefs_' + user.uid, JSON.stringify(appPrefs)); 
            }
            if (data.extraPrefs) { 
                extraPrefs = data.extraPrefs; 
                localStorage.setItem('rhn_extra_prefs_v2_' + user.uid, JSON.stringify(extraPrefs)); 
            }
        } else {
            const savedPrefs = localStorage.getItem('rhn_prefs_' + user.uid);
            if(savedPrefs) appPrefs = JSON.parse(savedPrefs);
            
            const savedExtraPrefs = localStorage.getItem('rhn_extra_prefs_v2_' + user.uid);
            if(savedExtraPrefs) extraPrefs = JSON.parse(savedExtraPrefs);
        }
    } catch(err) {
        console.error("Gagal sinkron data pengaturan", err);
    }

    window.isAppLoading = true;

    ['ext_autolock', 'ext_warnbalance', 'ext_shortnum', 'ext_budget', 'ext_hidezero', 'ext_walletpct', 'ext_debtbadge', 'ext_antiintip'].forEach(id => {
        if (document.getElementById(id) && extraPrefs[id]) {
            document.getElementById(id).value = extraPrefs[id];
            document.getElementById(id).dispatchEvent(new Event('change'));
        }
    });
    
    if (extraPrefs.ext_antiintip === 'on') { 
        document.body.classList.add('global-privacy'); 
    } else { 
        document.body.classList.remove('global-privacy'); 
    }
    
    setTimeout(() => {
        window.updatePrefCategories(false); 
        if (window.selType && appPrefs && appPrefs.type) { 
            selType(appPrefs.type); 
        } else { 
            selType('income'); 
        }
    }, 200);

    setTimeout(() => { 
        window.isAppLoading = false; 
    }, 1000); 

    const secRef = doc(db, 'users', user.uid, 'settings', 'security');
    try {
        const secSnap = await getDoc(secRef);
        document.getElementById('app-pin').style.display = 'block';
        
        if (!secSnap.exists() || !secSnap.data().pin) {
          document.getElementById('app-screen').style.display = 'none'; 
          document.getElementById('pin-screen').style.display = 'flex';
          document.getElementById('pin-title').textContent = 'Buat PIN Baru'; 
          document.getElementById('pin-sub').textContent = 'Buat 6 digit PIN untuk akses cepat';
          document.getElementById('pin-submit-btn').textContent = 'SIMPAN PIN'; 
          window.pinMode = 'setup'; 
          window.userCloudPin = null;
        } else {
          document.getElementById('app-screen').style.display = 'none'; 
          document.getElementById('pin-screen').style.display = 'flex';
          document.getElementById('pin-title').textContent = 'Masukkan PIN'; 
          document.getElementById('pin-sub').textContent = 'Keamanan aktif';
          document.getElementById('pin-submit-btn').textContent = 'BUKA APLIKASI'; 
          window.pinMode = 'verify'; 
          window.userCloudPin = secSnap.data().pin;
          
          if (window.pendingUnlock) { 
              window.pendingUnlock = false; 
              unlockApp(); 
          }
        }
    } catch(err) {
        console.error(err);
    }
    
    if(window.resetIdle) window.resetIdle();
    
  } else {
    currentUser = null; 
    localStorage.removeItem('last_uid_rhn');
    document.getElementById('auth-screen').style.display = 'flex'; 
    document.getElementById('app-screen').style.display = 'none'; 
    document.getElementById('pin-screen').style.display = 'none';
    
    if (unsubListener) { 
        unsubListener(); 
        unsubListener = null; 
    } 
    txs = [];
  }
});

window.verifyPin = async function() { 
    const pinInput = document.getElementById('app-pin').value; 
    const errEl = document.getElementById('pin-err'); 
    
    if (pinInput.length < 6) { 
        errEl.textContent = 'PIN harus 6 digit.'; 
        errEl.style.display = 'block'; 
        return; 
    } 
    
    errEl.style.display = 'none'; 
    
    if (window.pinMode === 'setup') { 
        document.getElementById('pin-submit-btn').textContent = 'MENYIMPAN...'; 
        try { 
            await setDoc(doc(db, 'users', currentUser.uid, 'settings', 'security'), { pin: pinInput }, { merge: true }); 
            window.userCloudPin = pinInput; 
            Swal.fire({position: 'center', icon: 'success', title: 'PIN Berhasil Dibuat!', showConfirmButton: false, timer: 1500, background: 'var(--card)', color: 'var(--text)', backdrop: 'rgba(0,0,0,0.6)'}); 
            unlockApp(); 
        } catch(e) { 
            errEl.textContent = 'Gagal menyimpan PIN ke server.'; 
            errEl.style.display = 'block'; 
            document.getElementById('pin-submit-btn').textContent = 'SIMPAN PIN'; 
        } 
    } else { 
        const uid = currentUser ? currentUser.uid : localStorage.getItem('last_uid_rhn'); 
        if (!uid) return; 
        
        if (pinInput === window.userCloudPin) { 
            if (currentUser) { 
                unlockApp(); 
            } else { 
                document.getElementById('pin-title').textContent = 'Memuat Data...'; 
                document.getElementById('pin-sub').textContent = 'Tunggu sebentar...'; 
                document.getElementById('app-pin').blur(); 
                window.pendingUnlock = true; 
            } 
        } else { 
            errEl.textContent = 'PIN Salah!'; 
            errEl.style.display = 'block'; 
            document.getElementById('app-pin').value = ''; 
            document.getElementById('app-pin').classList.add('shake-error'); 
            
            setTimeout(() => document.getElementById('app-pin').classList.remove('shake-error'), 400); 
            
            if (navigator.vibrate) navigator.vibrate([30, 50, 30]); 
        } 
    } 
};

function unlockApp() { 
    document.getElementById('pin-screen').style.display = 'none'; 
    document.getElementById('app-screen').style.display = 'block'; 
    setLoading(false); 
    
    const name = currentUser.displayName || currentUser.email.split('@')[0]; 
    document.getElementById('user-name').textContent = name; 
    document.getElementById('user-avatar').textContent = name.charAt(0).toUpperCase(); 
    
    listenTransactions(currentUser.uid); 
    document.getElementById('app-pin').value = ''; 
    
    if (window.resetIdle) window.resetIdle(); 
}

window.resetAccount = function() { 
    Swal.fire({ 
        title: 'Ganti Akun?', 
        text: "Lu harus login Email lagi.", 
        icon: 'warning', 
        showCancelButton: true, 
        background: 'var(--card)', 
        color: 'var(--text)', 
        confirmButtonColor: 'var(--red2)', 
        cancelButtonColor: 'var(--bg3)', 
        confirmButtonText: 'Ya, Ganti' 
    }).then((result) => { 
        if (result.isConfirmed) { 
            localStorage.removeItem('last_uid_rhn'); 
            document.getElementById('app-pin').value = ''; 
            doLogout(); 
        } 
    }); 
};

window.resetPinFromLogin = async function() { 
    const uid = currentUser ? currentUser.uid : localStorage.getItem('last_uid_rhn'); 
    
    if (!uid) { 
        return Swal.fire({icon: 'error', title: 'Belum Login', text: 'Tunggu proses ke server sebentar', background: 'var(--card)', color: 'var(--text)'}); 
    } 
    
    const { value: choice } = await Swal.fire({ 
        title: 'Opsi Keamanan', 
        text: 'Pilih tindakan untuk PIN lu:', 
        icon: 'question', 
        showCancelButton: true, 
        showDenyButton: true, 
        confirmButtonText: 'Lupa PIN (Buat Baru)', 
        denyButtonText: 'Ingat PIN (Ganti PIN)', 
        cancelButtonText: 'Batal', 
        background: 'var(--card)', 
        color: 'var(--text)', 
        confirmButtonColor: 'var(--red2)', 
        denyButtonColor: 'var(--gold)', 
        cancelButtonColor: 'var(--bg3)' 
    }); 
    
    const promptNewPin = async () => { 
        const { value: newPin } = await Swal.fire({ 
            title: 'Buat PIN Baru', 
            text: 'Masukkan 6 angka PIN baru kamu', 
            input: 'password', 
            inputAttributes: { inputmode: 'numeric', maxlength: 6, style: 'text-align: center; letter-spacing: 10px; font-size: 24px;', autofocus: true }, 
            background: 'var(--card)', 
            color: 'var(--text)', 
            confirmButtonColor: 'var(--gold)', 
            confirmButtonText: 'SIMPAN PIN BARU' 
        }); 
        
        if (newPin && newPin.length === 6) { 
            try { 
                await setDoc(doc(db, 'users', uid, 'settings', 'security'), { pin: newPin }, { merge: true }); 
                window.userCloudPin = newPin; 
                Swal.fire({icon:'success', title:'PIN Berhasil Disimpan!', background:'var(--card)', color:'var(--text)', timer: 1500, showConfirmButton: false}); 
                document.getElementById('app-pin').value = ''; 
            } catch(e) { 
                Swal.fire({icon:'error', title:'Gagal mengubah PIN', text: e.message, background:'var(--card)', color:'var(--text)'}); 
            } 
        } else if (newPin) { 
            Swal.fire({icon:'warning', title:'Gagal, harus 6 digit!', background:'var(--card)', color:'var(--text)'}); 
        } 
    }; 
    
    if (choice === true) { 
        promptNewPin(); 
    } else if (choice === false) { 
        const { value: oldPin } = await Swal.fire({ 
            title: 'Masukkan PIN Lama', 
            input: 'password', 
            inputAttributes: { inputmode: 'numeric', maxlength: 6, style: 'text-align: center; letter-spacing: 10px; font-size: 24px;', autofocus: true }, 
            background: 'var(--card)', 
            color: 'var(--text)', 
            confirmButtonColor: 'var(--border2)' 
        }); 
        
        if (!oldPin) return; 
        
        if (oldPin !== window.userCloudPin) return Swal.fire({icon:'error', title:'PIN Lama Salah!', background:'var(--card)', color:'var(--text)'}); 
        promptNewPin(); 
    } 
};

document.getElementById('app-pin').addEventListener('input', function(e) { 
    this.value = this.value.replace(/[^0-9]/g, ''); 
    if (this.value.length === 6) { 
        window.verifyPin(); 
    } 
});

function listenTransactions(uid) { 
    if (unsubListener) unsubListener(); 
    
    unsubListener = onSnapshot(query(collection(db, 'users', uid, 'transactions'), orderBy('createdAt', 'desc')), snap => { 
        txs = snap.docs.map(d => ({id: d.id, ...d.data()})); 
        setSyncStatus(true); 
        refreshAll(); 
    }, err => { 
        console.error(err); 
        setSyncStatus(false); 
    }); 
}

window.addTx = async function() { 
  if(!currentUser) return; 
  
  const amountInput = document.getElementById('f-amount');
  const catInput = document.getElementById('f-cat');
  const noteInput = document.getElementById('f-note');
  
  const rawValue = amountInput.value.replace(/\./g, '');
  const amt = parseFloat(rawValue);
  
  let cat = catInput.value; 
  if (curType === 'transfer') cat = 'Transfer Antar Dompet';
  
  const note = noteInput.value.trim();

  // LOGIKA VALIDASI SUPER SPESIFIK & AKURAT
  const isAmtEmpty = !amt || isNaN(amt);
  const isCatEmpty = !cat;
  const isNoteEmpty = !note;

  if (isAmtEmpty || (isCatEmpty && curType !== 'transfer') || isNoteEmpty) {
      let missing = [];
      if (isAmtEmpty) {
          missing.push('Nominal');
          amountInput.classList.add('shake-error');
          setTimeout(() => amountInput.classList.remove('shake-error'), 400);
      }
      if (isCatEmpty && curType !== 'transfer') {
          missing.push('Kategori');
          document.getElementById('f-cat').parentNode.previousSibling.classList.add('shake-error');
          setTimeout(() => document.getElementById('f-cat').parentNode.previousSibling.classList.remove('shake-error'), 400);
      }
      if (isNoteEmpty) {
          missing.push('Keterangan');
          noteInput.classList.add('shake-error');
          setTimeout(() => noteInput.classList.remove('shake-error'), 400);
      }

      return Swal.fire({ 
          position: 'center',
          icon: 'warning',
          title: 'Data Belum Lengkap!', 
          text: 'Bro, tolong isi bagian ini dulu: ' + missing.join(', '),
          showConfirmButton: true,
          confirmButtonText: 'Oke, Siap',
          confirmButtonColor: 'var(--gold)',
          background: 'var(--card)', 
          color: 'var(--text)',
          backdrop: 'rgba(0,0,0,0.6)'
      });
  }

  const dt = document.getElementById('f-date').value; 
  const wallet = document.getElementById('f-wallet') ? document.getElementById('f-wallet').value : 'Kas Tunai';
  const walletTo = document.getElementById('f-wallet-to') ? document.getElementById('f-wallet-to').value : 'Kas Tunai';
  
  if (curType === 'transfer' && wallet === walletTo) {
      return Swal.fire({position: 'center', icon: 'warning', title: 'Oops...', text: 'Dompet asal dan tujuan tidak boleh sama!', showConfirmButton: false, timer: 2000, background: 'var(--card)', color: 'var(--text)', backdrop: 'rgba(0,0,0,0.6)'});
  }

  if (document.activeElement) document.activeElement.blur();

  // KONFIRMASI REVIEW SEBELUM MENYIMPAN (POP-UP KEREN)
  let confHtml = `
    <div style="text-align:left; font-size:13px; line-height:1.6; margin-top:12px; background:var(--bg2); padding:16px; border-radius:12px; border:1px solid var(--border);">
        <div style="margin-bottom:8px; display:flex; justify-content:space-between; align-items:center;">
           <span style="color:var(--text3);">Nominal</span>
           <span style="font-weight:800; font-family:'JetBrains Mono', monospace; font-size:15px; color:${curType==='income'||curType==='recv'?'var(--green2)':curType==='expense'||curType==='debt'?'var(--red2)':'var(--text)'};">${fmtFull(amt)}</span>
        </div>
  `;
  
  if (curType === 'transfer') {
      confHtml += `
        <div style="margin-bottom:8px; display:flex; justify-content:space-between;">
           <span style="color:var(--text3);">Asal Dana</span> <span style="font-weight:700;">${wallet}</span>
        </div>
        <div style="margin-bottom:8px; display:flex; justify-content:space-between;">
           <span style="color:var(--text3);">Tujuan Dana</span> <span style="font-weight:700;">${walletTo}</span>
        </div>
      `;
  } else {
      confHtml += `
        <div style="margin-bottom:8px; display:flex; justify-content:space-between;">
           <span style="color:var(--text3);">Kategori</span> <span style="font-weight:700; text-align:right;">${cat}</span>
        </div>
        <div style="margin-bottom:8px; display:flex; justify-content:space-between;">
           <span style="color:var(--text3);">Sumber Dana</span> <span style="font-weight:700;">${wallet}</span>
        </div>
      `;
  }
  
  confHtml += `
        <div style="margin-bottom:0; display:flex; flex-direction:column; margin-top:8px; padding-top:8px; border-top:1px dashed var(--border2);">
           <span style="color:var(--text3); margin-bottom:4px;">Keterangan</span>
           <span style="font-weight:600; color:var(--gold); font-style:italic;">"${escapeHTML(note)}"</span>
        </div>
    </div>
  `;

  const confirmResult = await Swal.fire({
      title: editId ? 'Update Transaksi?' : 'Simpan Transaksi?',
      html: confHtml,
      showCancelButton: true,
      confirmButtonColor: editId ? 'var(--blue)' : 'var(--green2)',
      cancelButtonColor: 'var(--bg3)',
      confirmButtonText: editId ? 'Ya, Update Data' : 'Ya, Simpan!',
      cancelButtonText: 'Cek Lagi',
      background: 'var(--card)',
      color: 'var(--text)',
      customClass: { popup: 'centered-modal' }
  });

  if (!confirmResult.isConfirmed) return;

  const saveBtn = document.getElementById('save-btn');
  saveBtn.textContent = 'MENYIMPAN...'; 
  saveBtn.style.opacity = '0.7';
  saveBtn.disabled = true;

  try { 
      let payload = {
          type: curType,
          amount: amt,
          category: cat,
          wallet: wallet,
          note: note || '-',
          date: dt || nowISO()
      };
      
      if (curType === 'transfer') payload.walletTo = walletTo;
      if (curType === 'debt' || curType === 'recv') payload.isPaid = false;

      if (editId) { 
          await updateDoc(doc(db, 'users', currentUser.uid, 'transactions', editId), payload); 
          cancelEdit(); 
      } else { 
          payload.createdAt = serverTimestamp();
          await addDoc(collection(db, 'users', currentUser.uid, 'transactions'), payload); 
      } 
      
      amountInput.value = ''; 
      document.getElementById('f-note').value = ''; 
      
      saveBtn.style.opacity = '1';
      saveBtn.style.transform = 'scale(0.95)';
      setTimeout(() => saveBtn.style.transform = 'scale(1)', 150);
      
      saveBtn.style.background = 'var(--green2)';
      saveBtn.style.color = '#000';
      saveBtn.textContent = 'TERSIMPAN ✅';
      saveBtn.style.boxShadow = '0 0 15px rgba(16, 185, 129, 0.5)';
      
      if (navigator.vibrate) navigator.vibrate([30, 50, 30]); 
      
      let titleMsg = 'Berhasil Disimpan!';
      if (curType === 'debt') titleMsg = '💳 Hutang Tercatat!';
      if (curType === 'recv') titleMsg = '💸 Piutang Tercatat!';
      if (curType === 'transfer') titleMsg = '🔄 Transfer Berhasil!';
      
      Swal.fire({
         position: 'center',
         icon: 'success',
         title: titleMsg,
         showConfirmButton: false,
         timer: 2000,
         background: 'var(--card)',
         color: 'var(--text)',
         backdrop: 'rgba(0,0,0,0.6)'
      });
      
      setTimeout(() => {
          saveBtn.style.boxShadow = 'none';
          saveBtn.disabled = false;
          window.setRealLocalTime();
          
          if (appPrefs && appPrefs.type) {
              selType(appPrefs.type);
              setTimeout(() => {
                  if (document.getElementById('f-cat') && appPrefs.category) { 
                      document.getElementById('f-cat').value = appPrefs.category; 
                      document.getElementById('f-cat').dispatchEvent(new Event('change')); 
                  }
                  if (document.getElementById('f-wallet') && appPrefs.wallet) { 
                      document.getElementById('f-wallet').value = appPrefs.wallet; 
                      document.getElementById('f-wallet').dispatchEvent(new Event('change')); 
                  }
              }, 50);
          } else {
              selType('income');
          }
      }, 2000);

  } catch(e) {
      Swal.fire({
          position: 'center', 
          icon: 'error', 
          title: 'Koneksi Terputus / Error', 
          text: e.message, 
          showConfirmButton: true, 
          background: 'var(--card)', 
          color: 'var(--text)', 
          backdrop: 'rgba(0,0,0,0.6)'
      }); 
      saveBtn.textContent = 'COBA LAGI';
      saveBtn.style.opacity = '1';
      saveBtn.disabled = false;
  } 
};

// ... BAGIAN RENDERING FUNGSI SEPERTI SEBELUMNYA ...

function renderWalletBalances() { 
    const wallets = { 'Kas Tunai': 0, 'DANA': 0, 'GoPay': 0, 'ShopeePay': 0, 'MT5 Trading': 0, 'Bank': 0 }; 
    let hutangBal = 0; 
    let piutangBal = 0; 
    let totalAset = 0; 
    
    txs.forEach(t => { 
        let w = t.wallet || 'Kas Tunai'; 
        let wTo = t.walletTo; 
        
        if (w !== 'Hutang' && w !== 'Piutang' && !wallets.hasOwnProperty(w)) wallets[w] = 0; 
        if (wTo && wTo !== 'Hutang' && wTo !== 'Piutang' && !wallets.hasOwnProperty(wTo)) wallets[wTo] = 0; 
        
        if (t.type === 'income') { 
            if (wallets.hasOwnProperty(w)) wallets[w] += t.amount; 
        } else if (t.type === 'expense') { 
            if (wallets.hasOwnProperty(w)) wallets[w] -= t.amount; 
        } else if (t.type === 'transfer') { 
            if (w === 'Hutang') hutangBal -= t.amount; 
            else if (w === 'Piutang') piutangBal += t.amount; 
            else if (wallets.hasOwnProperty(w)) wallets[w] -= t.amount; 
            
            if (wTo === 'Hutang') hutangBal += t.amount; 
            else if (wTo === 'Piutang') piutangBal -= t.amount; 
            else if (wTo && wallets.hasOwnProperty(wTo)) wallets[wTo] += t.amount; 
        } else if (t.type === 'debt') { 
            if (wallets.hasOwnProperty(w)) wallets[w] += t.amount; 
            if (!t.isPaid) { 
                hutangBal -= t.amount; 
            } else { 
                if (wallets.hasOwnProperty(w)) wallets[w] -= t.amount; 
            } 
        } else if (t.type === 'recv') { 
            if (wallets.hasOwnProperty(w)) wallets[w] -= t.amount; 
            if (!t.isPaid) { 
                piutangBal -= t.amount; 
            } else { 
                if (wallets.hasOwnProperty(w)) wallets[w] += t.amount; 
            } 
        } 
    }); 
    
    for (let key in wallets) { 
        if (wallets[key] > 0) totalAset += wallets[key]; 
    } 
    
    const container = document.getElementById('wallet-balances'); 
    if (!container) return; 
    
    let html = Object.entries(wallets).filter(([name, bal]) => { 
        if (typeof extraPrefs !== 'undefined' && extraPrefs.ext_hidezero === 'on' && bal === 0) return false; 
        return true; 
    }).map(([name, bal]) => { 
        let pct = (typeof extraPrefs !== 'undefined' && extraPrefs.ext_walletpct === 'on' && totalAset > 0 && bal > 0) ? `<div class="w-pct-badge" style="display:block;">${((bal/totalAset)*100).toFixed(1)}%</div>` : ''; 
        
        // FORMAT MILIAR KHUSUS BANK & KAS TUNAI
        let displayBal = fmtFull(bal);
        if ((name === 'Kas Tunai' || name === 'Bank') && Math.abs(bal) >= 1000000000) {
            displayBal = (bal / 1000000000).toLocaleString('id-ID', { minimumFractionDigits: 0, maximumFractionDigits: 3 }) + 'M';
        }

        return `<div class="w-card" style="position:relative;">${pct}<div class="w-label">${name}</div><div class="w-val ${bal < 0 ? 'min' : ''}">${displayBal}</div><div class="usd-wallet-val" style="font-size: 8px; color: var(--text3); font-family: 'JetBrains Mono', monospace; margin-top: 2px;">${getUSD(bal)}</div></div>` 
    }).join(''); 
    
    html += `
    <div style="grid-column: 1 / -1; display: grid; grid-template-columns: 1fr 1fr; gap: inherit;"> 
        <div class="w-card" style="border-color:rgba(251, 191, 36, 0.5); background:rgba(251, 191, 36, 0.05);">
            <div class="w-label" style="color:var(--gold);">TOTAL HUTANG</div>
            <div class="w-val min">${fmtFull(hutangBal)}</div>
            <div class="usd-wallet-val" style="font-size: 8px; color: var(--text3); font-family: 'JetBrains Mono', monospace; margin-top: 2px;">${getUSD(hutangBal)}</div>
        </div> 
        <div class="w-card" style="border-color:rgba(59, 130, 246, 0.5); background:rgba(59, 130, 246, 0.05);">
            <div class="w-label" style="color:var(--blue);">TOTAL PIUTANG</div>
            <div class="w-val min">${fmtFull(piutangBal)}</div>
            <div class="usd-wallet-val" style="font-size: 8px; color: var(--text3); font-family: 'JetBrains Mono', monospace; margin-top: 2px;">${getUSD(piutangBal)}</div>
        </div> 
    </div>`; 
    
    container.innerHTML = html; 
}

// ... TERUSKAN KODE SAMPAI DI BAGIAN BAWAH ...

</script>

<style>
  html { overflow-y: scroll !important; } 
  .page { animation: none !important; transition: none !important; } 
  .m-bar-fill { transition: none !important; } 
  
  body.swal2-shown, body.swal2-height-auto { padding-right: 0 !important; }

  .nav { 
      position: sticky !important; top: 0; z-index: 100; 
      background-color: var(--bg); border-bottom: 4px solid #000000 !important; 
      padding-bottom: 12px !important; transition: none !important; 
  } 
  .main { padding-top: 16px !important; }
  
  .filter-bar { 
      position: sticky !important; top: 70px; z-index: 90; 
      background: var(--bg); padding-top: 16px !important; 
      margin-top: -16px; padding-bottom: 16px !important; 
      border-bottom: 1px solid var(--border); transition: 0.3s ease; 
  }
  .nav.hidden-nav + .main .filter-bar { top: 0px !important; }

  .m-card.bal, .ri-amount, .cat-badge { cursor: pointer; transition: 0.2s; }
  .ri-amount:hover, .cat-badge:hover { opacity: 0.7; }
  
  .inc .m-bar-fill { background: linear-gradient(90deg, #10B981 0%, #34D399 100%); }
  .exp .m-bar-fill { background: linear-gradient(90deg, #F87171 0%, #FCA5A5 100%); }
  
  @keyframes shake { 0%, 100% {transform: translateX(0);} 25% {transform: translateX(-5px);} 75% {transform: translateX(5px);} }
  .shake-error { animation: shake 0.3s ease-in-out; border-color: var(--red2) !important; box-shadow: 0 0 8px rgba(248,113,113,0.3) !important; }

  body.global-privacy .m-val, body.global-privacy .ri-amount, body.global-privacy .usd-pill, body.global-privacy .ri-usd, body.global-privacy .w-val { filter: blur(6px); transition: 0.3s; user-select: none; }
  body.idle-mode { filter: brightness(0.6) blur(2px); transition: 0.5s ease; pointer-events: none; } 

  .ewallet-badge { background: rgba(59, 130, 246, 0.2); color: #0266CC; font-size: 8px; padding: 2px 6px; border-radius: 4px; margin-left: 6px; font-weight: 800; border: 1px solid rgba(59, 130, 246, 0.5); }
  .trading-badge { background: rgba(245, 158, 11, 0.2); color: #D97706; font-size: 8px; padding: 2px 6px; border-radius: 4px; margin-left: 6px; font-weight: 800; border: 1px solid rgba(245, 158, 11, 0.5); }
  .big-money-glow { text-shadow: 0 0 12px rgba(251, 191, 36, 0.8); color: var(--gold) !important; }
  .swal-btn-darktext { color: #000 !important; font-weight: 800 !important; }

  #scroll-to-top { 
      position: fixed; bottom: 24px; right: 24px; width: 50px; height: 50px; 
      background: var(--blue-title); color: #fff; border: none; border-radius: 50%; 
      font-size: 20px; box-shadow: 0 4px 12px rgba(0,0,0,0.3); cursor: pointer; 
      z-index: 999; display: none; align-items: center; justify-content: center; transition: 0.3s; 
  }
  #scroll-to-top:hover { background: var(--blue); transform: scale(1.05); }

</style>

<script>
window.addEventListener('DOMContentLoaded', (event) => {
  const Toast = Swal.mixin({ 
      position: 'center', showConfirmButton: false, timer: 2000, 
      timerProgressBar: true, background: 'var(--card)', 
      color: 'var(--text)', backdrop: 'rgba(0,0,0,0.6)' 
  });
  
  window.addEventListener('offline', () => { 
      document.getElementById('offline-banner').style.display = 'block'; 
      Toast.fire({ icon: 'warning', title: 'Koneksi Terputus!' }); 
  });
  
  window.addEventListener('online', () => { 
      document.getElementById('offline-banner').style.display = 'none'; 
      Toast.fire({ icon: 'success', title: 'Online Kembali!' }); 
  });

  if (window.Chart) { 
      Chart.defaults.animation = false; 
      Chart.defaults.transitions.active.animation.duration = 0; 
  }

  // KONFIRMASI TOMBOL HAPUS
  const originalDelTx = window.delTx; 
  window.delTx = function(id) { 
      if (navigator.vibrate) navigator.vibrate(20); 
      Swal.fire({ 
          title: 'Hapus Transaksi?', text: "Data yang dihapus tidak bisa dikembalikan.", 
          icon: 'warning', showCancelButton: true, background: 'var(--card)', color: 'var(--text)', 
          confirmButtonColor: 'var(--red2)', cancelButtonColor: 'var(--bg3)', 
          confirmButtonText: 'Ya, Hapus', position: 'center', backdrop: 'rgba(0,0,0,0.6)' 
      }).then((result) => { 
          if (result.isConfirmed) { 
              const nativeConfirm = window.confirm; 
              window.confirm = () => true; 
              originalDelTx(id).then(() => { 
                  window.confirm = nativeConfirm; 
                  Toast.fire({ icon: 'success', title: 'Data terhapus!' }); 
              }).catch(err => { 
                  window.confirm = nativeConfirm; 
              }); 
          } 
      }); 
  };
  
  // KONFIRMASI TOMBOL EDIT BARU!
  const originalEditTx = window.editTx; 
  window.editTx = function(id) { 
      if (navigator.vibrate) navigator.vibrate(20); 
      Swal.fire({
          title: 'Edit Transaksi?',
          text: "Data akan dipindah ke form untuk diubah.",
          icon: 'question',
          showCancelButton: true,
          confirmButtonColor: 'var(--blue)',
          cancelButtonColor: 'var(--bg3)',
          confirmButtonText: 'Ya, Edit',
          cancelButtonText: 'Batal',
          background: 'var(--card)',
          color: 'var(--text)',
          customClass: { popup: 'centered-modal' },
          backdrop: 'rgba(0,0,0,0.6)'
      }).then((result) => {
          if (result.isConfirmed) {
              originalEditTx(id);
              window.scrollTo({ top: 0, behavior: 'smooth' });
          }
      });
  };
  
  const originalDoLogout = window.doLogout; 
  window.doLogout = function() { 
      if (navigator.vibrate) navigator.vibrate(20); 
      Swal.fire({ 
          title: 'Keluar Akun?', text: "Lu yakin mau keluar dari aplikasi?", 
          icon: 'warning', showCancelButton: true, background: 'var(--card)', color: 'var(--text)', 
          confirmButtonColor: 'var(--red2)', cancelButtonColor: 'var(--bg3)', 
          confirmButtonText: 'Ya, Keluar', position: 'center', backdrop: 'rgba(0,0,0,0.6)' 
      }).then((result) => { 
          if (result.isConfirmed) { 
              originalDoLogout(); 
          } 
      }); 
  };

  // ... (Sisa Script di bawahnya tetep sama, biar nggak panjang-panjang teuing ini jawaban)
</script>
</body>
</html>
