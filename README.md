[index.html](https://github.com/user-attachments/files/26680304/index.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>محجر الدولية - نظام الإدارة</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --primary:#1a5276;--primary-light:#2980b9;--accent:#f39c12;
  --bg:#f4f6f8;--card:#fff;--border:#dde1e7;--text:#2c3e50;--muted:#7f8c8d;
  --success:#27ae60;--danger:#e74c3c;--warning:#f39c12;--info:#2980b9;
  --sidebar-w:240px;--topbar-h:56px;
}
body{font-family:'Cairo',sans-serif;background:var(--bg);color:var(--text);font-size:14px;-webkit-text-size-adjust:100%;overflow-x:hidden;max-width:100vw}
#app{display:flex;min-height:100vh}

/* ===== SIDEBAR ===== */
#sidebar{width:var(--sidebar-w);background:var(--primary);color:#fff;display:flex;flex-direction:column;position:fixed;top:0;right:0;height:100vh;overflow-y:auto;z-index:200;transition:transform .3s ease}
.logo-area{padding:16px;border-bottom:1px solid rgba(255,255,255,0.1);display:flex;align-items:center;gap:10px}
.logo-area-info h2{font-size:14px;font-weight:700;line-height:1.3}
.logo-area-info p{font-size:10px;opacity:0.7;margin-top:2px}
.nav-section{padding:6px 0}
.nav-label{font-size:10px;text-transform:uppercase;opacity:0.5;padding:6px 14px 3px;letter-spacing:1px}
.nav-item{display:flex;align-items:center;gap:9px;padding:10px 14px;cursor:pointer;transition:background .15s;font-size:13px;border-right:3px solid transparent;user-select:none}
.nav-item:hover{background:rgba(255,255,255,.08)}
.nav-item.active{background:rgba(255,255,255,.15);border-right-color:var(--accent)}
.nav-item .icon{font-size:15px;width:20px;text-align:center;flex-shrink:0}

/* ===== MAIN ===== */
#main{margin-right:var(--sidebar-w);flex:1;display:flex;flex-direction:column;min-width:0;overflow-x:hidden}
#topbar{background:var(--card);border-bottom:1px solid var(--border);padding:10px 20px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100;height:var(--topbar-h)}
#topbar h1{font-size:16px;font-weight:700;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.topbar-meta{font-size:11px;color:var(--muted);display:none}
.user-badge{background:var(--primary);color:#fff;padding:5px 10px;border-radius:20px;font-size:12px;cursor:pointer;white-space:nowrap}
#content{padding:16px;flex:1;overflow-x:hidden;min-width:0}

/* Hamburger button - hidden on desktop */
#menu-toggle{display:none;background:none;border:none;cursor:pointer;padding:6px;color:var(--primary);font-size:22px;margin-left:10px;flex-shrink:0}
#sidebar-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:150}
.card{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:20px}
.card-title{font-size:15px;font-weight:700;margin-bottom:16px;padding-bottom:12px;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:8px}
.stat-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(155px,1fr));gap:12px;margin-bottom:20px}
.stat-card{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:16px;text-align:center}
.stat-num{font-size:22px;font-weight:700;margin:4px 0}
.stat-label{font-size:11px;color:var(--muted);text-transform:uppercase}
.stat-card.blue{border-top:3px solid var(--info)}
.stat-card.green{border-top:3px solid var(--success)}
.stat-card.orange{border-top:3px solid var(--warning)}
.stat-card.red{border-top:3px solid var(--danger)}
.table-wrap{overflow-x:auto;max-width:100%;-webkit-overflow-scrolling:touch}
table{width:100%;border-collapse:collapse;font-size:13px}
th{background:#f8f9fa;padding:9px 10px;text-align:right;font-weight:600;border-bottom:2px solid var(--border);white-space:nowrap}
td{padding:9px 10px;border-bottom:1px solid var(--border);vertical-align:middle}
tr:hover td{background:#fafbfc}
.form-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:12px}
.form-group{display:flex;flex-direction:column;gap:4px}
.form-group label{font-size:12px;font-weight:600;color:var(--muted)}
.form-group input,.form-group select,.form-group textarea{padding:8px 10px;border:1px solid var(--border);border-radius:6px;font-family:'Cairo',sans-serif;font-size:13px;outline:none;background:var(--card);color:var(--text);transition:border-color .15s}
.form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--primary-light)}
.form-group textarea{resize:vertical;min-height:60px}
.btn{padding:7px 14px;border:none;border-radius:6px;cursor:pointer;font-family:'Cairo',sans-serif;font-size:13px;font-weight:600;transition:all .15s;display:inline-flex;align-items:center;gap:6px}
.btn-primary{background:var(--primary);color:#fff}.btn-primary:hover{background:#154360}
.btn-success{background:var(--success);color:#fff}.btn-success:hover{background:#1e8449}
.btn-danger{background:var(--danger);color:#fff}.btn-danger:hover{background:#c0392b}
.btn-warning{background:var(--warning);color:#fff}.btn-warning:hover{background:#d68910}
.btn-info{background:var(--info);color:#fff}.btn-info:hover{background:#1a6fa0}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--text)}.btn-outline:hover{background:#f8f9fa}
.btn-sm{padding:4px 9px;font-size:12px}
.badge{padding:3px 8px;border-radius:12px;font-size:11px;font-weight:600;display:inline-block}
.badge-success{background:#d5f5e3;color:#1e8449}
.badge-danger{background:#fadbd8;color:#c0392b}
.badge-warning{background:#fef9e7;color:#b7950b}
.badge-info{background:#d6eaf8;color:#1a5276}
.badge-gray{background:#f2f3f4;color:#566573}
.badge-purple{background:#e8daef;color:#6c3483}
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:200;display:flex;align-items:flex-start;justify-content:center;padding:20px;overflow-y:auto}
.modal{background:var(--card);border-radius:12px;width:100%;max-width:750px;margin:auto}
.modal-header{padding:18px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:var(--card);border-radius:12px 12px 0 0;z-index:2}
.modal-header h3{font-size:15px;font-weight:700}
.modal-body{padding:20px}
.modal-footer{padding:14px 20px;border-top:1px solid var(--border);display:flex;justify-content:flex-end;gap:8px}
.close-btn{background:none;border:none;font-size:20px;cursor:pointer;color:var(--muted);padding:4px}
#login-screen{position:fixed;inset:0;background:linear-gradient(135deg,#1a5276,#2980b9);display:flex;align-items:center;justify-content:center;z-index:9999}
.login-card{background:#fff;border-radius:16px;padding:40px;width:360px;text-align:center;box-shadow:0 20px 60px rgba(0,0,0,.3)}
.login-card h2{font-size:22px;font-weight:700;margin-bottom:4px}
.login-card p{color:var(--muted);margin-bottom:24px;font-size:13px}
.login-field{text-align:right;margin-bottom:16px}
.login-field label{font-size:12px;font-weight:600;color:var(--muted);display:block;margin-bottom:4px}
.login-field input{width:100%;padding:10px 14px;border:1px solid var(--border);border-radius:8px;font-family:'Cairo',sans-serif;font-size:14px;outline:none}
.login-field input:focus{border-color:var(--primary)}
.tabs{display:flex;gap:0;border-bottom:2px solid var(--border);margin-bottom:20px;flex-wrap:wrap}
.tab{padding:9px 14px;cursor:pointer;font-size:13px;font-weight:600;color:var(--muted);border-bottom:2px solid transparent;margin-bottom:-2px;transition:all .15s}
.tab.active{color:var(--primary);border-bottom-color:var(--primary)}
.tab:hover:not(.active){color:var(--text)}
.search-bar{display:flex;gap:8px;align-items:center;margin-bottom:16px;flex-wrap:wrap}
.search-bar input,.search-bar select{padding:7px 10px;border:1px solid var(--border);border-radius:6px;font-family:'Cairo',sans-serif;font-size:13px;outline:none}
.search-bar input[type=text]{flex:1;min-width:180px}
.divider{height:1px;background:var(--border);margin:16px 0}
.text-muted{color:var(--muted)}.text-danger{color:var(--danger)}.text-success{color:var(--success)}.text-info{color:var(--info)}
.text-right{text-align:right}
.flex{display:flex}.gap-8{gap:8px}.gap-12{gap:12px}.items-center{align-items:center}.justify-between{justify-content:space-between}.flex-wrap{flex-wrap:wrap}
.mb-8{margin-bottom:8px}.mb-12{margin-bottom:12px}.mb-16{margin-bottom:16px}.mb-20{margin-bottom:20px}
.mt-8{margin-top:8px}.mt-12{margin-top:12px}.mt-16{margin-top:16px}
.w-full{width:100%}
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.price-row{background:#f0f7ff;border:1px solid #bee3f8;border-radius:8px;padding:12px;margin-bottom:12px}
.highlight-row{background:#fff8e1;border:1px solid #ffe082;border-radius:8px;padding:12px}
/* ===== MOBILE TABLE CARDS ===== */
@media(max-width:600px){
  .mobile-cards table thead{display:none}
  .mobile-cards table tr{display:block;background:var(--card);border:1px solid var(--border);border-radius:8px;margin-bottom:10px;padding:10px}
  .mobile-cards table td{display:flex;justify-content:space-between;align-items:center;padding:4px 0;border:none;font-size:12px}
  .mobile-cards table td:before{content:attr(data-label);font-weight:600;color:var(--muted);font-size:11px;margin-left:8px;flex-shrink:0}
  .mobile-cards table td:last-child{border-top:1px solid var(--border);margin-top:6px;padding-top:8px;justify-content:flex-end}
}
/* Sticky action buttons on mobile */
@media(max-width:768px){
  .sticky-fab{position:fixed;bottom:20px;left:20px;z-index:99;border-radius:50%;width:52px;height:52px;font-size:22px;box-shadow:0 4px 16px rgba(0,0,0,.25);display:flex;align-items:center;justify-content:center;padding:0}
  .page-actions{flex-direction:column-reverse;gap:8px}
  .page-actions .btn{width:100%;justify-content:center}
  .inline-actions{gap:4px}
  .inline-actions .btn-sm{padding:4px 6px;font-size:11px}
}
@media (max-width:768px){
  :root{--sidebar-w:260px}
  #sidebar{transform:translateX(100%)}
  #sidebar.open{transform:translateX(0)}
  #sidebar-overlay.open{display:block}
  #main{margin-right:0}
  #menu-toggle{display:flex;align-items:center;justify-content:center}
  #topbar{padding:10px 12px}
  #topbar h1{font-size:15px}
  .topbar-meta{display:none}
  #content{padding:12px}
  .stat-grid{grid-template-columns:repeat(2,1fr);gap:8px}
  .stat-num{font-size:18px}
  .stat-card{padding:12px}
  .form-grid{grid-template-columns:1fr}
  .grid-2{grid-template-columns:1fr}
  .modal{max-width:100%;margin:0;border-radius:12px 12px 0 0}
  .modal-overlay{align-items:flex-end;padding:0}
  .search-bar{flex-direction:column;align-items:stretch}
  .search-bar input[type=text],.search-bar input[type=date],.search-bar select{width:100%;min-width:unset}
  .btn{font-size:12px;padding:7px 10px}
  .btn-sm{font-size:11px;padding:4px 8px}
  table{font-size:12px}
  th,td{padding:7px 6px}
  .tabs{overflow-x:auto;flex-wrap:nowrap;-webkit-overflow-scrolling:touch}
  .tab{white-space:nowrap;font-size:12px;padding:8px 10px}
  .card{padding:14px}
  .card-title{font-size:14px}
  #topbar .flex.gap-12{gap:6px}
  .sidebar-logout{padding:12px}
}
@media (max-width:480px){
  .stat-grid{grid-template-columns:repeat(2,1fr)}
  .stat-num{font-size:16px}
  #topbar h1{font-size:14px;max-width:160px}
  .user-badge{font-size:11px;padding:4px 8px}
  table{font-size:11px}
  th,td{padding:6px 4px}
}
@media (min-width:769px){
  .topbar-meta{display:block}
}
@media print{#sidebar,#topbar,.no-print,#menu-toggle,#sidebar-overlay{display:none!important}#main{margin-right:0}.modal-overlay{position:static;background:none}.modal{box-shadow:none;max-height:none}}

/* ===== RESPONSIVE TABLES - CARD VIEW ON MOBILE ===== */
@media(max-width:900px){
  /* Hide less important columns on tablets */
  .hide-md{display:none!important}
}
@media(max-width:650px){
  /* Convert ALL tables to card view on mobile */
  .table-wrap table thead{display:none}
  .table-wrap table,
  .table-wrap tbody,
  .table-wrap tr,
  .table-wrap td{display:block;width:100%}
  .table-wrap tr{
    background:var(--card);
    border:1px solid var(--border);
    border-radius:8px;
    margin-bottom:10px;
    padding:10px 12px;
    position:relative;
  }
  .table-wrap tr:hover{background:var(--card)}
  .table-wrap td{
    display:flex;
    justify-content:space-between;
    align-items:center;
    padding:5px 0;
    border:none;
    border-bottom:1px solid #f0f0f0;
    font-size:13px;
    min-height:32px;
  }
  .table-wrap td:last-child{border-bottom:none;padding-top:8px;justify-content:flex-end;gap:6px}
  .table-wrap td:before{
    content:attr(data-label);
    font-weight:600;
    color:var(--muted);
    font-size:12px;
    min-width:90px;
    flex-shrink:0;
  }
  .table-wrap td:last-child:before{display:none}
  /* Hide # column on mobile */
  .table-wrap td[data-label="#"]{display:none}
}
</style>
</head>
<body>

<div id="login-screen">
  <div class="login-card">
    <div style="font-size:40px;margin-bottom:12px">⛏️</div>
    <h2>محجر الدولية</h2>
    <p>نظام إدارة المحجر المتكامل</p>
    <div class="login-field"><label>اسم المستخدم</label><input type="text" id="login-user" name="username" autocomplete="username" placeholder="أدخل اسم المستخدم"></div>
    <div class="login-field"><label>كلمة المرور</label><input type="password" id="login-pass" name="password" autocomplete="current-password" placeholder="أدخل كلمة المرور"></div>
    <div id="login-err" style="color:#e74c3c;font-size:12px;margin-bottom:8px;display:none">بيانات غير صحيحة</div>
    <button class="btn btn-primary w-full" onclick="doLogin()">دخول</button>
  </div>
</div>

<div id="app" style="display:none">
  <div id="sidebar">
    <div class="logo-area">
      <div id="logo-display" style="font-size:32px;flex-shrink:0">⛏️</div>
      <div class="logo-area-info">
        <h2 id="company-name-display">محجر الدولية</h2>
        <p id="company-sub-display">نظام الإدارة المتكامل</p>
      </div>
    </div>
    <div class="nav-section">
      <div class="nav-label">الرئيسية</div>
      <div class="nav-item" onclick="navigate('dashboard')"><span class="icon">🏠</span> لوحة التحكم</div>
    </div>
    <div class="nav-section">
      <div class="nav-label">العمليات</div>
      <div class="nav-item" onclick="navigate('receipts')"><span class="icon">📋</span> إيصالات التحميل</div>
      <div class="nav-item" onclick="navigate('materials')"><span class="icon">🪨</span> الخامات والأسعار</div>
      <div class="nav-item" onclick="navigate('customers')"><span class="icon">👥</span> العملاء</div>
      <div class="nav-item" onclick="navigate('vehicles')"><span class="icon">🚛</span> السيارات</div>
      <div class="nav-item" onclick="navigate('equipment')"><span class="icon">🏗️</span> المعدات</div>
    </div>
    <div class="nav-section">
      <div class="nav-label">الحسابات</div>
      <div class="nav-item" onclick="navigate('accounts-customers')"><span class="icon">💳</span> حساب العملاء</div>
      <div class="nav-item" onclick="navigate('accounts-equipment')"><span class="icon">⚙️</span> حساب المعدات</div>
      <div class="nav-item" onclick="navigate('accounts-masrec')"><span class="icon">🏛️</span> جهاز مستقبل مصر</div>
      <div class="nav-item" onclick="navigate('expenses')"><span class="icon">💸</span> المصروفات</div>
      <div class="nav-item" onclick="navigate('revenues')"><span class="icon">💰</span> الإيرادات</div>
      <div class="nav-item" onclick="navigate('salaries')"><span class="icon">👷</span> المرتبات</div>
      <div class="nav-item" onclick="navigate('treasury')"><span class="icon">🏦</span> الخزينة</div>
    </div>
    <div class="nav-section">
      <div class="nav-label">الإدارة</div>
      <div class="nav-item" onclick="navigate('settings')"><span class="icon">⚙️</span> الإعدادات</div>
    </div>
    <div style="padding:16px;margin-top:auto;border-top:1px solid rgba(255,255,255,.1)" class="sidebar-logout">
      <div style="font-size:12px;opacity:.7;margin-bottom:8px" id="current-user-display">مرحباً، admin</div>
      <button class="btn btn-outline" style="width:100%;color:#fff;border-color:rgba(255,255,255,.3)" onclick="doLogout()">تسجيل الخروج</button>
    </div>
  </div>

  <div id="sidebar-overlay" onclick="closeSidebar()"></div>
  <div id="main">
    <div id="topbar">
      <div class="flex items-center gap-8">
        <button id="menu-toggle" onclick="toggleSidebar()">☰</button>
        <h1 id="page-title">لوحة التحكم</h1>
      </div>
      <div class="flex items-center gap-12">
        <div class="topbar-meta" id="topbar-date"></div>
        <div class="user-badge" id="topbar-user">admin</div>
      </div>
    </div>
    <div id="content"></div>
  </div>
</div>

<div id="modal-container"></div>

<style>
.price-row{background:#f0f7ff;border:1px solid #bee3f8;border-radius:8px;padding:12px;margin-bottom:12px}
.badge-purple{background:#e8daef;color:#6c3483}
.mt-8{margin-top:8px}.mt-12{margin-top:12px}.mt-16{margin-top:16px}
.mb-8{margin-bottom:8px}.mb-12{margin-bottom:12px}.mb-16{margin-bottom:16px}.mb-20{margin-bottom:20px}
</style>
<script>
// =========================================================
// ===== SUPABASE CONFIG =====
// =========================================================
const SUPA_URL = 'https://gwhatwkwrygfewxzoliq.supabase.co';
const SUPA_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imd3aGF0d2t3cnlnZmV3eHpvbGlxIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzU5NDY1MjUsImV4cCI6MjA5MTUyMjUyNX0.dAScV-PA-bQqD8BXENrTVRNlPdAjfQEmJkVE69G-n1w';

const HEADERS = {
  'Content-Type': 'application/json',
  'apikey': SUPA_KEY,
  'Authorization': 'Bearer ' + SUPA_KEY,
  'Prefer': 'return=representation'
};

// =========================================================
// ===== CORE API HELPERS =====
// =========================================================

async function sbFetch(path, options={}) {
  const url = SUPA_URL + '/rest/v1/' + path;
  const res = await fetch(url, { headers: HEADERS, ...options });
  if (!res.ok) {
    const err = await res.text();
    throw new Error('Supabase error: ' + res.status + ' ' + err);
  }
  const text = await res.text();
  return text ? JSON.parse(text) : null;
}

// GET all rows from table with optional filters
async function dbGetAll(table) {
  const map = TABLE_MAP[table];
  if (!map) return [];
  const rows = await sbFetch(map.name + '?order=id.asc&limit=10000');
  return (rows || []).map(r => map.fromDB(r));
}

// GET single row by id
async function dbGet(table, id) {
  const map = TABLE_MAP[table];
  if (!map) return null;
  const rows = await sbFetch(map.name + '?id=eq.' + id + '&limit=1');
  if (!rows || !rows.length) return null;
  return map.fromDB(rows[0]);
}

// INSERT or UPDATE (upsert by id)
async function dbPut(table, record) {
  const map = TABLE_MAP[table];
  if (!map) return null;
  const dbRecord = map.toDB(record);
  // If has id → update, else insert
  if (dbRecord.id) {
    const id = dbRecord.id;
    delete dbRecord.id;
    const rows = await sbFetch(map.name + '?id=eq.' + id, {
      method: 'PATCH',
      body: JSON.stringify(dbRecord)
    });
    return id;
  } else {
    const rows = await sbFetch(map.name, {
      method: 'POST',
      body: JSON.stringify(dbRecord)
    });
    return rows && rows[0] ? rows[0].id : null;
  }
}

// UPDATE specific fields
async function dbUpdate(table, id, changes) {
  const map = TABLE_MAP[table];
  if (!map) return;
  const dbChanges = map.toDB(changes);
  delete dbChanges.id;
  await sbFetch(map.name + '?id=eq.' + id, {
    method: 'PATCH',
    body: JSON.stringify(dbChanges)
  });
}

// DELETE by id
async function dbDelete(table, id) {
  const map = TABLE_MAP[table];
  if (!map) return;
  await sbFetch(map.name + '?id=eq.' + id, { method: 'DELETE' });
}

// GET settings (singleton)
async function dbGetSettings() {
  const rows = await sbFetch('settings?id=eq.1&limit=1');
  if (!rows || !rows.length) return {};
  const r = rows[0];
  return {
    companyName: r.company_name || 'محجر الدولية',
    address: r.address || '',
    phone: r.phone || '',
    email: r.email || '',
    taxCard: r.tax_card || '',
    tradeReg: r.trade_reg || '',
    logo: r.logo || null,
    masrecPricePerM3: r.masrec_price_per_m3 || 0
  };
}

async function dbSaveSettings(obj) {
  await sbFetch('settings?id=eq.1', {
    method: 'PATCH',
    body: JSON.stringify({
      company_name: obj.companyName,
      address: obj.address,
      phone: obj.phone,
      email: obj.email,
      tax_card: obj.taxCard,
      trade_reg: obj.tradeReg,
      logo: obj.logo,
      masrec_price_per_m3: obj.masrecPricePerM3
    })
  });
}

// =========================================================
// ===== TABLE MAPPING (JS field names ↔ DB column names) =====
// =========================================================
const TABLE_MAP = {
  users: {
    name: 'users',
    fromDB: r => ({ id: r.id, username: r.username, password: r.password, name: r.name, role: r.role }),
    toDB: o => ({ id: o.id, username: o.username, password: o.password, name: o.name, role: o.role })
  },
  materials: {
    name: 'materials',
    fromDB: r => ({ id: r.id, name: r.name, defaultPrice: r.default_price, notes: r.notes || '' }),
    toDB: o => ({ id: o.id, name: o.name, default_price: o.defaultPrice, notes: o.notes })
  },
  customers: {
    name: 'customers',
    fromDB: r => ({
      id: r.id, name: r.name, company: r.company || '', phone: r.phone || '',
      type: r.type || 'account', balance: r.balance || 0,
      address: r.address || '', notes: r.notes || '',
      prices: r.prices || []
    }),
    toDB: o => ({
      id: o.id, name: o.name, company: o.company, phone: o.phone,
      type: o.type, balance: o.balance, address: o.address,
      notes: o.notes, prices: o.prices
    })
  },
  vehicles: {
    name: 'vehicles',
    fromDB: r => ({
      id: r.id, tractorNum: r.tractor_num || '', trailerNum: r.trailer_num || '',
      driver: r.driver || '', phone: r.phone || '',
      capacity: r.capacity || 0, notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, tractor_num: o.tractorNum, trailer_num: o.trailerNum,
      driver: o.driver, phone: o.phone, capacity: o.capacity, notes: o.notes
    })
  },
  equipment: {
    name: 'equipment',
    fromDB: r => ({
      id: r.id, name: r.name, type: r.type || 'fixed',
      pricePerMeter: r.price_per_meter || 0, pricePerHour: r.price_per_hour || 0,
      totalMeters: r.total_meters || 0, totalHours: r.total_hours || 0,
      status: r.status || 'active', notes: r.notes || '',
      custody: r.custody || []
    }),
    toDB: o => ({
      id: o.id, name: o.name, type: o.type,
      price_per_meter: o.pricePerMeter, price_per_hour: o.pricePerHour,
      total_meters: o.totalMeters, total_hours: o.totalHours,
      status: o.status, notes: o.notes, custody: o.custody
    })
  },
  receipts: {
    name: 'receipts',
    fromDB: r => ({
      id: r.id, date: r.date,
      customerType: r.customer_type || 'cash', customerId: r.customer_id,
      customerName: r.customer_name || '', companyName: r.company_name || '',
      waterBon: r.water_bon || '', loadBon: r.load_bon || '',
      materialId: r.material_id, materialName: r.material_name || '',
      materialPrice: r.material_price || 0, qty: r.qty || 0,
      customerTotal: r.customer_total || 0, tip: r.tip || 0,
      payMethod: r.pay_method || 'cash',
      tractorNum: r.tractor_num || '', trailerNum: r.trailer_num || '',
      equipId: r.equip_id, equipType: r.equip_type || '',
      equipPricePerM: r.equip_price_per_m || 0, equipPricePerH: r.equip_price_per_h || 0
    }),
    toDB: o => ({
      id: o.id, date: o.date,
      customer_type: o.customerType, customer_id: o.customerId || null,
      customer_name: o.customerName, company_name: o.companyName,
      water_bon: o.waterBon, load_bon: o.loadBon,
      material_id: o.materialId || null, material_name: o.materialName,
      material_price: o.materialPrice, qty: o.qty,
      customer_total: o.customerTotal, tip: o.tip,
      pay_method: o.payMethod,
      tractor_num: o.tractorNum, trailer_num: o.trailerNum,
      equip_id: o.equipId || null, equip_type: o.equipType,
      equip_price_per_m: o.equipPricePerM, equip_price_per_h: o.equipPricePerH
    })
  },
  payments: {
    name: 'payments',
    fromDB: r => ({
      id: r.id, date: r.date, customerId: r.customer_id,
      customerName: r.customer_name || '', amount: r.amount || 0,
      method: r.method || 'cash', notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, date: o.date, customer_id: o.customerId || null,
      customer_name: o.customerName, amount: o.amount,
      method: o.method, notes: o.notes
    })
  },
  expenses: {
    name: 'expenses',
    fromDB: r => ({
      id: r.id, date: r.date, category: r.category || 'متنوع',
      desc: r.description || '', amount: r.amount || 0,
      payMethod: r.pay_method || 'cash', notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, date: o.date, category: o.category,
      description: o.desc, amount: o.amount,
      pay_method: o.payMethod, notes: o.notes
    })
  },
  employees: {
    name: 'employees',
    fromDB: r => ({
      id: r.id, name: r.name, role: r.role || '',
      salary: r.salary || 0, salaryDay: r.salary_day || 1,
      phone: r.phone || '', notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, name: o.name, role: o.role,
      salary: o.salary, salary_day: o.salaryDay,
      phone: o.phone, notes: o.notes
    })
  },
  salary_payments: {
    name: 'salary_payments',
    fromDB: r => ({
      id: r.id, date: r.date, empId: r.emp_id,
      empName: r.emp_name || '', amount: r.amount || 0,
      method: r.method || 'cash', paidBy: r.paid_by || '', notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, date: o.date, emp_id: o.empId || null,
      emp_name: o.empName, amount: o.amount,
      method: o.method, paid_by: o.paidBy, notes: o.notes
    })
  },
  treasury: {
    name: 'treasury',
    fromDB: r => ({
      id: r.id, date: r.date, type: r.type || 'in',
      category: r.category || '', description: r.description || '',
      amount: r.amount || 0, ref: r.ref_id
    }),
    toDB: o => ({
      id: o.id, date: o.date, type: o.type,
      category: o.category, description: o.description,
      amount: o.amount, ref_id: o.ref || null
    })
  },
  banks: {
    name: 'banks',
    fromDB: r => ({ id: r.id, name: r.name, type: r.type || 'بنك', balance: r.balance || 0 }),
    toDB: o => ({ id: o.id, name: o.name, type: o.type, balance: o.balance })
  },
  equipment_hours: {
    name: 'equipment_hours',
    fromDB: r => ({
      id: r.id, date: r.date, eqId: r.eq_id,
      hours: r.hours || 0, notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, date: o.date, eq_id: o.eqId,
      hours: o.hours, notes: o.notes
    })
  },
  masrec_payments: {
    name: 'masrec_payments',
    fromDB: r => ({
      id: r.id, date: r.date, amount: r.amount || 0,
      method: r.method || 'cash', ref: r.ref || '', notes: r.notes || ''
    }),
    toDB: o => ({
      id: o.id, date: o.date, amount: o.amount,
      method: o.method, ref: o.ref, notes: o.notes
    })
  }
};

// =========================================================
// ===== BACKUP & RESTORE =====
// =========================================================
async function doBackup() {
  const tables = ['settings','users','materials','customers','vehicles','equipment',
    'receipts','payments','expenses','employees','salary_payments',
    'treasury','banks','equipment_hours','masrec_payments'];
  const data = {};
  for (const t of tables) {
    if (t === 'settings') data[t] = await dbGetSettings();
    else data[t] = await dbGetAll(t);
  }
  const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'mahgar_backup_' + today() + '.json';
  a.click();
}

async function doRestore(input) {
  const file = input.files[0]; if (!file) return;
  if (!confirm('هل تريد فعلاً استعادة البيانات؟ سيتم حذف البيانات الحالية.')) return;
  const reader = new FileReader();
  reader.onload = async (e) => {
    try {
      const data = JSON.parse(e.target.result);
      alert('⏳ جاري الاستعادة... قد تستغرق بضع دقائق');
      // Restore tables one by one
      const tables = ['materials','customers','vehicles','equipment','receipts',
        'payments','expenses','employees','salary_payments','treasury',
        'banks','equipment_hours','masrec_payments'];
      for (const t of tables) {
        if (data[t] && Array.isArray(data[t]) && data[t].length > 0) {
          const map = TABLE_MAP[t];
          // Delete all existing rows
          try { await sbFetch(map.name + '?id=gte.0', { method: 'DELETE' }); } catch(e){}
          try { await sbFetch(map.name + '?id=lt.0', { method: 'DELETE' }); } catch(e){}
          // Insert in batches of 50
          const batch = data[t];
          for(let i=0; i<batch.length; i+=50){
            const chunk = batch.slice(i,i+50).map(rec=>{
              const dbRec = map.toDB(rec);
              delete dbRec.id;
              return dbRec;
            });
            await sbFetch(map.name, { method: 'POST', body: JSON.stringify(chunk) });
          }
        }
      }
      if (data.settings) await dbSaveSettings(data.settings);
      alert('✅ تم استعادة البيانات بنجاح');
      location.reload();
    } catch(err) {
      console.error(err);
      alert('❌ خطأ في الاستعادة: ' + err.message);
    }
  };
  reader.readAsText(file);
}

// =========================================================
// ===== INIT CHECK =====
// =========================================================
async function initData() {
  try {
    await dbGetSettings();
    // Ensure admin user exists
    const users = await dbGetAll('users');
    if(!users.length || !users.find(u=>u.username==='admin')){
      await sbFetch('users', {method:'POST', body: JSON.stringify({username:'admin',password:'1234',name:'المدير',role:'admin'})});
    }
    console.log('✅ Supabase connected');
  } catch(e) {
    console.error('❌ Supabase connection failed:', e);
    throw e;
  }
}

// ===== APP GLOBALS =====
// =========================================================
let currentUser = null, currentPage = 'dashboard';
function genId(){ return Date.now() + Math.floor(Math.random() * 9999); }
function fmt(n){ return (n||0).toLocaleString('ar-EG',{minimumFractionDigits:2,maximumFractionDigits:2}); }
function today(){ return new Date().toISOString().split('T')[0]; }
function showModal(html){ document.getElementById('modal-container').innerHTML=`<div class="modal-overlay" onclick="closeModalOutside(event)">${html}</div>`; }
function closeModal(){ document.getElementById('modal-container').innerHTML=''; }
function closeModalOutside(e){ if(e.target.classList.contains('modal-overlay')) closeModal(); }

// =========================================================
// ===== AUTH =====
// =========================================================
async function doLogin(){
  const u = document.getElementById('login-user').value.trim();
  const p = document.getElementById('login-pass').value.trim();
  const errEl = document.getElementById('login-err');
  errEl.style.display = 'none';
  if(!u || !p){ errEl.textContent = 'يرجى إدخال اسم المستخدم وكلمة المرور'; errEl.style.display='block'; return; }
  try {
    const users = await dbGetAll('users');
    const found = users.find(x => x.username===u && x.password===p);
    if(found){
      currentUser = found;
      document.getElementById('login-screen').style.display = 'none';
      document.getElementById('app').style.display = 'flex';
      document.getElementById('current-user-display').textContent = 'مرحباً، ' + found.name;
      document.getElementById('topbar-user').textContent = found.name;
      const s = await dbGetSettings();
      if(s.companyName) document.getElementById('company-name-display').textContent = s.companyName;
      if(s.logo) document.getElementById('logo-display').innerHTML = `<img src="${s.logo}" style="width:50px;height:50px;border-radius:8px;object-fit:cover">`;
      setInterval(()=>{ document.getElementById('topbar-date').textContent = new Date().toLocaleDateString('ar-EG',{weekday:'long',year:'numeric',month:'long',day:'numeric'}); }, 1000);
      navigate('dashboard');
    } else {
      errEl.textContent = 'اسم المستخدم أو كلمة المرور غير صحيحة';
      errEl.style.display = 'block';
    }
  } catch(err) {
    errEl.textContent = 'خطأ في الاتصال: ' + err.message;
    errEl.style.display = 'block';
    console.error('Login error:', err);
  }
}
document.getElementById('login-user').addEventListener('keydown', e=>{ if(e.key==='Enter') document.getElementById('login-pass').focus(); });
document.getElementById('login-pass').addEventListener('keydown', e=>{ if(e.key==='Enter') doLogin(); });
function doLogout(){ currentUser=null; document.getElementById('login-screen').style.display='flex'; document.getElementById('app').style.display='none'; }

// =========================================================
// ===== NAVIGATION =====
// =========================================================
const pageTitles = {
  dashboard:'لوحة التحكم', receipts:'إيصالات التحميل', materials:'الخامات والأسعار',
  customers:'العملاء', vehicles:'السيارات', equipment:'المعدات',
  'accounts-customers':'حساب العملاء', 'accounts-equipment':'حساب المعدات',
  'accounts-masrec':'جهاز مستقبل مصر', expenses:'المصروفات',
  revenues:'الإيرادات', salaries:'المرتبات', treasury:'الخزينة', settings:'الإعدادات'
};

function navigate(page){
  currentPage = page;
  closeSidebar();
  document.querySelectorAll('.nav-item').forEach(el => el.classList.toggle('active', el.getAttribute('onclick')===`navigate('${page}')`));
  document.getElementById('page-title').textContent = pageTitles[page]||page;
  document.getElementById('content').innerHTML = '<div style="text-align:center;padding:40px;color:var(--muted)">⏳ جاري التحميل...</div>';
  const renders = {
    dashboard: renderDashboard, receipts: renderReceipts, materials: renderMaterials,
    customers: renderCustomers, vehicles: renderVehicles, equipment: renderEquipment,
    'accounts-customers': renderAccountsCustomers, 'accounts-equipment': renderAccountsEquipment,
    'accounts-masrec': renderMasrec, expenses: renderExpenses,
    revenues: renderRevenues, salaries: renderSalaries,
    treasury: renderTreasury, settings: renderSettings
  };
  if(renders[page]) renders[page]();
}

// =========================================================
// ===== PRINT HELPER =====
// =========================================================
async function printSection(title, html, dateRange=''){
  const s = await dbGetSettings();
  const win = window.open('','_blank','width=900,height=700');
  win.document.write(`<!DOCTYPE html><html dir="rtl"><head><meta charset="UTF-8">
  <style>body{font-family:Arial,sans-serif;padding:20px;font-size:13px}
  h2{text-align:center;margin-bottom:4px}p.sub{text-align:center;color:#666;margin-bottom:16px;font-size:12px}
  table{width:100%;border-collapse:collapse}td,th{padding:7px 9px;border:1px solid #ccc;text-align:right}
  th{background:#f0f0f0;font-weight:bold}.total-row{font-weight:bold;background:#e8f4fd}
  .print-header{border-bottom:2px solid #333;padding-bottom:12px;margin-bottom:16px;display:flex;justify-content:space-between;align-items:center}
  </style></head><body>
  <div class="print-header">
    <div><h2 style="margin:0">${s.companyName||'محجر الدولية'}</h2><p style="margin:0;color:#666;font-size:11px">${s.address||''} | ${s.phone||''}</p></div>
    <div style="text-align:left"><b>${title}</b>${dateRange?'<br><small>'+dateRange+'</small>':''}</div>
  </div>${html}
  <p style="text-align:center;color:#999;font-size:11px;margin-top:20px">تاريخ الطباعة: ${new Date().toLocaleDateString('ar-EG')}</p>
  </body></html>`);
  win.document.close();
  setTimeout(()=>win.print(), 600);
}

// =========================================================
// ===== DASHBOARD =====
// =========================================================
async function renderDashboard(){
  const [receipts, expenses, customers, payments] = await Promise.all([
    dbGetAll('receipts'), dbGetAll('expenses'), dbGetAll('customers'), dbGetAll('payments')
  ]);
  const today_str = today();
  const todayR = receipts.filter(r=>r.date===today_str);
  const totalRevToday = todayR.reduce((s,r)=>s+(r.customerTotal||0),0);
  const cashRecs = receipts.filter(r=>r.payMethod==='cash');
  const totalCashRev = cashRecs.reduce((s,r)=>s+(r.customerTotal||0),0);
  const totalExp = expenses.reduce((s,e)=>s+(e.amount||0),0);
  const totalPay = payments.reduce((s,p)=>s+(p.amount||0),0);
  const lastFive = receipts.slice(-5).reverse();
  document.getElementById('content').innerHTML=`
  <div class="stat-grid">
    <div class="stat-card blue"><div class="stat-label">إيصالات اليوم</div><div class="stat-num">${todayR.length}</div></div>
    <div class="stat-card green"><div class="stat-label">مبيعات اليوم (ج.م)</div><div class="stat-num">${fmt(totalRevToday)}</div></div>
    <div class="stat-card orange"><div class="stat-label">إجمالي العملاء</div><div class="stat-num">${customers.length}</div></div>
    <div class="stat-card red"><div class="stat-label">إجمالي المصروفات</div><div class="stat-num">${fmt(totalExp)}</div></div>
  </div>
  <div class="grid-2 mb-20">
    <div class="card">
      <div class="card-title">📊 ملخص مالي</div>
      <table style="width:100%;font-size:13px">
        <tr><td class="text-muted">مبيعات كاش</td><td class="text-right text-success">${fmt(totalCashRev)} ج.م</td></tr>
        <tr><td class="text-muted">دفعات مستلمة</td><td class="text-right text-success">${fmt(totalPay)} ج.م</td></tr>
        <tr><td class="text-muted">المصروفات</td><td class="text-right text-danger">${fmt(totalExp)} ج.م</td></tr>
        <tr style="border-top:2px solid var(--border)"><td><b>صافي الربح</b></td><td class="text-right"><b>${fmt(totalCashRev+totalPay-totalExp)} ج.م</b></td></tr>
      </table>
    </div>
    <div class="card">
      <div class="card-title">📋 آخر الإيصالات</div>
      ${lastFive.map(r=>`
        <div class="flex justify-between items-center mb-12" style="border-bottom:1px solid var(--border);padding-bottom:8px">
          <div>
            <div style="font-weight:600;font-size:13px">${r.customerName||'عميل نقدي'}</div>
            <div class="text-muted" style="font-size:11px">${r.date} | ${r.materialName||''}</div>
          </div>
          <div class="text-success" style="font-weight:700">${fmt(r.customerTotal)} ج.م</div>
        </div>`).join('')}
    </div>
  </div>
  <div class="card">
    <div class="card-title">⚡ إجراءات سريعة</div>
    <div class="flex gap-8 flex-wrap">
      <button class="btn btn-primary" onclick="navigate('receipts')">➕ إيصال تحميل جديد</button>
      <button class="btn btn-success" onclick="navigate('customers')">👤 إضافة عميل</button>
      <button class="btn btn-warning" onclick="navigate('expenses')">💸 تسجيل مصروف</button>
      <button class="btn btn-info" onclick="navigate('materials')">🪨 إدارة الخامات</button>
    </div>
  </div>`;
}

// =========================================================
// ===== MATERIALS =====
// =========================================================
async function renderMaterials(){
  const mats = await dbGetAll('materials');
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16">
    <h3>إجمالي الخامات: ${mats.length}</h3>
    <button class="btn btn-primary no-print" onclick="showMaterialModal()">➕ خامة جديدة</button>
  </div>
  <div class="card">
    <div class="card-title">🪨 قائمة الخامات والأسعار الافتراضية</div>
    <p class="text-muted mb-16" style="font-size:12px">السعر الافتراضي يظهر تلقائياً في إيصال التحميل. يمكن تحديد سعر خاص لكل عميل من صفحة العملاء.</p>
    <div class="table-wrap">
      <table>
        <thead><tr><th>#</th><th>اسم الخامة</th><th>السعر الافتراضي (ج.م/م³)</th><th>ملاحظات</th><th>إجراءات</th></tr></thead>
        <tbody>${mats.map((m,i)=>`
          <tr>
            <td>${i+1}</td><td><b>${m.name}</b></td>
            <td class="text-success"><b>${fmt(m.defaultPrice)} ج.م</b></td>
            <td>${m.notes||'-'}</td>
            <td>
              <button class="btn btn-sm btn-outline" onclick="showMaterialModal(${m.id})">✏️</button>
              <button class="btn btn-sm btn-danger" onclick="deleteMaterial(${m.id})">🗑️</button>
            </td>
          </tr>`).join('')}
        </tbody>
      </table>
    </div>
  </div>`;
}

async function showMaterialModal(id=null){
  const m = id ? await dbGet('materials', id) : {};
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>${id?'✏️ تعديل':'➕ إضافة'} خامة</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>اسم الخامة</label><input type="text" id="m-name" value="${m.name||''}"></div>
        <div class="form-group"><label>السعر الافتراضي (ج.م/م³)</label><input type="number" id="m-price" value="${m.defaultPrice||0}" min="0"></div>
        <div class="form-group" style="grid-column:1/-1"><label>ملاحظات</label><textarea id="m-notes">${m.notes||''}</textarea></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveMaterial(${id||'null'})">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveMaterial(id){
  const name = document.getElementById('m-name').value.trim();
  if(!name){ alert('يرجى إدخال اسم الخامة'); return; }
  const obj = { name, defaultPrice: parseFloat(document.getElementById('m-price').value)||0, notes: document.getElementById('m-notes').value };
  if(id) await dbUpdate('materials', id, obj);
  else   await dbPut('materials', obj);
  closeModal(); renderMaterials();
}

async function deleteMaterial(id){
  if(!confirm('حذف؟')) return;
  await dbDelete('materials', id);
  renderMaterials();
}

// =========================================================
// ===== RECEIPTS =====
// =========================================================
async function renderReceipts(){
  const receipts = await dbGetAll('receipts');
  const mats = await dbGetAll('materials');
  document.getElementById('content').innerHTML=`
  <div class="mb-12 no-print">
    <div class="search-bar">
      <input type="text" id="rec-search" placeholder="بحث باسم العميل أو رقم الجرار..." oninput="filterReceipts()">
      <input type="date" id="rec-from" onchange="filterReceipts()">
      <input type="date" id="rec-to" onchange="filterReceipts()">
      <select id="rec-mat" onchange="filterReceipts()">
        <option value="">كل الخامات</option>
        ${mats.map(m=>`<option value="${m.id}">${m.name}</option>`).join('')}
      </select>
    </div>
    <div class="flex gap-8 flex-wrap">
      <button class="btn btn-outline" onclick="printFilteredReceipts()">🖨️ طباعة</button>
      <button class="btn btn-primary" onclick="showReceiptModal()">➕ إيصال جديد</button>
    </div>
  </div>
  <div class="card">
    <div class="table-wrap mobile-cards">
      <table id="receipts-table">
        <thead><tr>
          <th>#</th><th>التاريخ</th><th>العميل</th><th>الخامة</th><th class="hide-md">الجرار</th><th class="hide-md">المقطورة</th><th>الكمية(م³)</th><th class="hide-md">سعر الخامة</th><th>الإجمالي</th><th>الدفع</th><th>إجراءات</th>
        </tr></thead>
        <tbody id="receipts-body"></tbody>
      </table>
    </div>
  </div>`;
  renderReceiptsTable(receipts);
}

async function getFilteredReceipts(){
  let receipts = await dbGetAll('receipts');
  const q   = (document.getElementById('rec-search')?.value||'').toLowerCase();
  const from = document.getElementById('rec-from')?.value||'';
  const to   = document.getElementById('rec-to')?.value||'';
  const mat  = document.getElementById('rec-mat')?.value||'';
  if(q)    receipts = receipts.filter(r=>(r.customerName||'').toLowerCase().includes(q)||(r.tractorNum||'').includes(q)||(r.trailerNum||'').includes(q));
  if(from) receipts = receipts.filter(r=>r.date>=from);
  if(to)   receipts = receipts.filter(r=>r.date<=to);
  if(mat)  receipts = receipts.filter(r=>String(r.materialId)===String(mat));
  return receipts;
}

async function filterReceipts(){ renderReceiptsTable(await getFilteredReceipts()); }

function renderReceiptsTable(receipts){
  const tb = document.getElementById('receipts-body'); if(!tb) return;
  tb.innerHTML = receipts.slice().reverse().map((r,i)=>`
    <tr>
      <td data-label="#">${receipts.length-i}</td>
      <td data-label="التاريخ">${r.date}</td>
      <td data-label="العميل">${r.customerName||'<span class="badge badge-gray">نقدي</span>'}</td>
      <td data-label="الخامة"><span class="badge badge-info">${r.materialName||'-'}</span></td>
      <td data-label="الجرار">${r.tractorNum||'-'}</td>
      <td data-label="المقطورة">${r.trailerNum||'-'}</td>
      <td data-label="الكمية">${r.qty} م³</td>
      <td data-label="السعر">${fmt(r.materialPrice)}</td>
      <td data-label="الإجمالي"><b class="text-success">${fmt(r.customerTotal)} ج.م</b></td>
      <td data-label="الدفع"><span class="badge ${r.payMethod==='cash'?'badge-success':'badge-info'}">${r.payMethod==='cash'?'كاش':'حساب'}</span></td>
      <td class="no-print">
        <button class="btn btn-sm btn-info" onclick="showEditReceiptModal(${r.id})">✏️</button>
        <button class="btn btn-sm btn-outline" onclick="printReceipt(${r.id})">🖨️</button>
        <button class="btn btn-sm btn-danger" onclick="deleteReceipt(${r.id})">🗑️</button>
      </td>
    </tr>`).join('');
}

async function printFilteredReceipts(){
  const recs = (await getFilteredReceipts()).slice().reverse();
  const from = document.getElementById('rec-from')?.value||'';
  const to   = document.getElementById('rec-to')?.value||'';
  const totalQty = recs.reduce((s,r)=>s+r.qty,0);
  const totalAmt = recs.reduce((s,r)=>s+(r.customerTotal||0),0);
  const html = `<table>
    <thead><tr><th>#</th><th>التاريخ</th><th>العميل</th><th>الخامة</th><th>الجرار</th><th>المقطورة</th><th>الكمية</th><th>السعر</th><th>الإجمالي</th><th>الدفع</th></tr></thead>
    <tbody>${recs.map((r,i)=>`<tr><td>${i+1}</td><td>${r.date}</td><td>${r.customerName||'نقدي'}</td><td>${r.materialName}</td><td>${r.tractorNum||'-'}</td><td>${r.trailerNum||'-'}</td><td>${r.qty}</td><td>${fmt(r.materialPrice)}</td><td>${fmt(r.customerTotal)}</td><td>${r.payMethod==='cash'?'كاش':'حساب'}</td></tr>`).join('')}
    <tr class="total-row"><td colspan="6">الإجمالي</td><td>${totalQty} م³</td><td>-</td><td>${fmt(totalAmt)} ج.م</td><td>-</td></tr>
    </tbody></table>`;
  await printSection('إيصالات التحميل', html, from&&to?`من ${from} إلى ${to}`:'');
}


// ===== RECEIPT FORM STATE PRESERVATION =====
let _savedReceiptState = null;

function captureReceiptFormState(){
  const ids = ['r-date','r-ctype','r-customer','r-cashname','r-wbon','r-lbon',
    'r-tractor','r-trailer','r-qty','r-material','r-mat-price','r-tip','r-pay','r-equip'];
  const state = {};
  ids.forEach(id => {
    const el = document.getElementById(id);
    if(el) state[id] = el.value;
  });
  return state;
}

function restoreReceiptFormState(state){
  if(!state) return;
  Object.entries(state).forEach(([id, val]) => {
    const el = document.getElementById(id);
    if(el) el.value = val;
  });
  // Restore visibility
  const ct = document.getElementById('r-ctype')?.value;
  if(ct){
    const cg = document.getElementById('r-customer-group');
    const ng = document.getElementById('r-cashname-group');
    if(cg) cg.style.display = ct==='account' ? '' : 'none';
    if(ng) ng.style.display = ct==='cash' ? '' : 'none';
  }
  // Recalculate total
  calcReceiptTotal();
}

async function showReceiptModal(){
  const [customers, materials, vehicles, equipment] = await Promise.all([
    dbGetAll('customers'), dbGetAll('materials'), dbGetAll('vehicles'), dbGetAll('equipment')
  ]);
  const acctCusts = customers.filter(c=>c.type==='account');
  const activeEq  = equipment.filter(e=>e.status==='active');
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>📋 إيصال تحميل جديد</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="r-date" value="${today()}"></div>
        <div class="form-group"><label>نوع العميل</label>
          <select id="r-ctype" onchange="onReceiptCustomerTypeChange()">
            <option value="account">عميل حساب</option>
            <option value="cash">عميل نقدي (كاش)</option>
          </select>
        </div>
        <div class="form-group" id="r-customer-group"><label>العميل</label>
          <div class="flex gap-8">
            <select id="r-customer" onchange="onReceiptCustomerChange()" style="flex:1">
              <option value="">-- اختر عميل --</option>
              ${acctCusts.map(c=>`<option value="${c.id}">${c.name}${c.company?' - '+c.company:''}</option>`).join('')}
            </select>
            <button type="button" class="btn btn-success btn-sm" onclick="showQuickCustomerModal()" title="إضافة عميل جديد">➕</button>
          </div>
        </div>
        <div class="form-group" id="r-cashname-group" style="display:none"><label>اسم العميل النقدي</label><input type="text" id="r-cashname" placeholder="اختياري"></div>
        <div class="form-group"><label>البون المائي</label><input type="text" id="r-wbon"></div>
        <div class="form-group"><label>بون التحميل</label><input type="text" id="r-lbon"></div>
      </div>

      <div class="divider"></div>
      <div class="flex items-center justify-between mb-12">
        <div style="font-weight:600">🚛 بيانات السيارة</div>
        <button type="button" class="btn btn-success btn-sm" onclick="showQuickVehicleModal()">➕ إضافة سيارة جديدة</button>
      </div>
      <div class="form-grid">
        <div class="form-group">
          <label>رقم الجرار</label>
          <input type="text" id="r-tractor" placeholder="اكتب رقم الجرار..." oninput="onTractorInput(this.value)" autocomplete="off" list="tractors-list">
          <datalist id="tractors-list">
            ${vehicles.map(v=>`<option value="${v.tractorNum}"></option>`).join('')}
          </datalist>
          <small id="r-tractor-hint" class="text-muted" style="min-height:16px;display:block;margin-top:2px"></small>
        </div>
        <div class="form-group"><label>رقم المقطورة</label><input type="text" id="r-trailer" placeholder="يظهر تلقائياً أو اكتب يدوياً"></div>
        <div class="form-group"><label>التكعيب / الكمية (م³)</label><input type="number" id="r-qty" value="" min="0" step="0.01" placeholder="يظهر تلقائياً أو اكتب يدوياً" oninput="calcReceiptTotal()"></div>
      </div>

      <div class="divider"></div>
      <div style="font-weight:600;margin-bottom:12px">🪨 بيانات الخامة</div>
      <div class="form-grid">
        <div class="form-group"><label>الخامة</label>
          <select id="r-material" onchange="onReceiptMaterialChange()">
            <option value="">-- اختر خامة --</option>
            ${materials.map(m=>`<option value="${m.id}" data-price="${m.defaultPrice}">${m.name}</option>`).join('')}
          </select>
        </div>
        <div class="form-group">
          <label>سعر الخامة للعميل (ج.م/م³)</label>
          <input type="number" id="r-mat-price" value="0" min="0" step="0.01" oninput="calcReceiptTotal()">
          <small class="text-muted" id="r-price-hint"></small>
        </div>
        <div class="form-group"><label>اكرامية المكتب (ج.م)</label><input type="number" id="r-tip" value="0" min="0"></div>
        <div class="form-group"><label>طريقة الدفع *</label>
          <select id="r-pay">
            <option value="" disabled selected>-- اختر طريقة الدفع --</option>
            <option value="cash">كاش</option>
            <option value="account">يضاف للحساب</option>
          </select>
        </div>
        <div class="form-group"><label>المعدة المستخدمة</label>
          <select id="r-equip" onchange="calcReceiptTotal()">
            <option value="">-- اختر معدة --</option>
            ${activeEq.map(e=>`<option value="${e.id}" data-ppm="${e.pricePerMeter||0}" data-pph="${e.pricePerHour||0}" data-type="${e.type}">${e.name}</option>`).join('')}
          </select>
        </div>
      </div>

      <div class="divider"></div>
      <div class="price-row">
        <div class="flex justify-between items-center">
          <div>
            <div class="text-muted" style="font-size:12px">إجمالي العميل (سعر الخامة × الكمية)</div>
            <div style="font-size:20px;font-weight:700;color:var(--success)" id="r-total-display">0.00 ج.م</div>
          </div>
          <div style="text-align:left">
            <div class="text-muted" style="font-size:12px">تكلفة المعدة (في حساب المعدات)</div>
            <div style="font-size:14px;color:var(--info)" id="r-equip-cost-display">-</div>
          </div>
        </div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveReceipt()">💾 حفظ الإيصال</button>
    </div>
  </div>`);
}

function onReceiptCustomerTypeChange(){
  const ct = document.getElementById('r-ctype').value;
  document.getElementById('r-customer-group').style.display = ct==='account'?'':'none';
  document.getElementById('r-cashname-group').style.display  = ct==='cash'?'':'none';
  if(ct==='cash') document.getElementById('r-pay').value = 'cash';
  onReceiptCustomerChange();
}

async function onReceiptCustomerChange(){
  const custId  = parseInt(document.getElementById('r-customer')?.value||0);
  const matId   = parseInt(document.getElementById('r-material')?.value||0);
  if(custId && matId) await setCustomerMaterialPrice(custId, matId);
}

async function onReceiptMaterialChange(){
  const matId  = parseInt(document.getElementById('r-material')?.value||0);
  const custId = parseInt(document.getElementById('r-customer')?.value||0);
  const ct     = document.getElementById('r-ctype').value;
  const hint   = document.getElementById('r-price-hint');
  if(!matId){ calcReceiptTotal(); return; }
  const mat = await dbGet('materials', matId);
  if(!mat){ calcReceiptTotal(); return; }
  if(ct==='account' && custId){
    await setCustomerMaterialPrice(custId, matId);
  } else {
    document.getElementById('r-mat-price').value = mat.defaultPrice;
    if(hint) hint.textContent = `السعر الافتراضي: ${fmt(mat.defaultPrice)} ج.م`;
  }
  calcReceiptTotal();
}

async function setCustomerMaterialPrice(custId, matId){
  const [cu, mat] = await Promise.all([dbGet('customers', custId), dbGet('materials', matId)]);
  if(!cu||!mat) return;
  const custPrice = cu.prices?.find(p=>p.materialId===matId);
  const hint = document.getElementById('r-price-hint');
  if(custPrice){
    document.getElementById('r-mat-price').value = custPrice.price;
    if(hint) hint.textContent = `سعر خاص للعميل: ${fmt(custPrice.price)} ج.م`;
  } else {
    document.getElementById('r-mat-price').value = mat.defaultPrice;
    if(hint) hint.textContent = `السعر الافتراضي: ${fmt(mat.defaultPrice)} ج.م`;
  }
  calcReceiptTotal();
}

async function onTractorInput(val){
  const hint      = document.getElementById('r-tractor-hint');
  const trailerEl = document.getElementById('r-trailer');
  const qtyEl     = document.getElementById('r-qty');
  if(!val.trim()){ if(hint) hint.textContent=''; return; }
  const vehicles = await dbGetAll('vehicles');
  const match = vehicles.find(v=>v.tractorNum.trim()===val.trim())
             || vehicles.find(v=>v.tractorNum.trim().includes(val.trim()));
  if(match){
    trailerEl.value = match.trailerNum||'';
    if(match.capacity){ qtyEl.value=match.capacity; calcReceiptTotal(); }
    if(hint) hint.textContent=`✅ ${match.driver||''}${match.driver?' | ':''}مقطورة: ${match.trailerNum} | تكعيب: ${match.capacity} م³`;
  } else {
    if(hint) hint.textContent='';
  }
}

function calcReceiptTotal(){
  const qty      = parseFloat(document.getElementById('r-qty')?.value)||0;
  const matPrice = parseFloat(document.getElementById('r-mat-price')?.value)||0;
  const total    = qty * matPrice;
  const el = document.getElementById('r-total-display');
  if(el) el.textContent = fmt(total)+' ج.م';
  const equipSel = document.getElementById('r-equip');
  const opt = equipSel?.options[equipSel.selectedIndex];
  const costEl = document.getElementById('r-equip-cost-display');
  if(opt && opt.value && costEl){
    if(opt.dataset.type==='fixed'){ const ppm=parseFloat(opt.dataset.ppm)||0; costEl.textContent=fmt(qty*ppm)+' ج.م ('+ppm+' ج.م/م³)'; }
    else costEl.textContent='يُحسب بالساعة';
  } else if(costEl) costEl.textContent='-';
}


// Recalculate customer balance from actual receipts and payments
async function recalcCustomerBalance(custId) {
  if(!custId) return;
  const [allRecs, allPays] = await Promise.all([dbGetAll('receipts'), dbGetAll('payments')]);
  const totalDebit  = allRecs.filter(r=>r.customerId===custId && r.payMethod==='account')
                             .reduce((s,r)=>s+(r.customerTotal||0), 0);
  const totalCredit = allPays.filter(p=>p.customerId===custId)
                             .reduce((s,p)=>s+(p.amount||0), 0);
  const balance = totalDebit - totalCredit;
  await dbUpdate('customers', custId, { balance });
}

async function saveReceipt(){
  // Validate required fields
  const ct = document.getElementById('r-ctype').value;
  const missing = [];
  if(!document.getElementById('r-tractor').value.trim()) missing.push('رقم الجرار');
  if(!document.getElementById('r-trailer').value.trim()) missing.push('رقم المقطورة');
  if(!document.getElementById('r-qty').value || parseFloat(document.getElementById('r-qty').value)<=0) missing.push('الكمية / التكعيب');
  if(!document.getElementById('r-material').value) missing.push('الخامة');
  if(!document.getElementById('r-mat-price').value || parseFloat(document.getElementById('r-mat-price').value)<=0) missing.push('سعر الخامة');
  if(!document.getElementById('r-date').value) missing.push('التاريخ');
  if(ct==='account' && !document.getElementById('r-customer').value) missing.push('العميل');
  if(!document.getElementById('r-pay').value) missing.push('طريقة الدفع');
  if(missing.length){
    alert('⚠️ يرجى ملء البيانات الإجبارية:\n• ' + missing.join('\n• '));
    return;
  }
  const custId = ct==='account'?(parseInt(document.getElementById('r-customer').value)||null):null;
  const cu     = custId ? await dbGet('customers', custId) : null;
  const custName = ct==='account'?(cu?.name||''):(document.getElementById('r-cashname').value||'عميل نقدي');
  const matId  = parseInt(document.getElementById('r-material').value)||null;
  const mat    = matId ? await dbGet('materials', matId) : null;
  const qty    = parseFloat(document.getElementById('r-qty').value)||0;
  const matPrice     = parseFloat(document.getElementById('r-mat-price').value)||0;
  const customerTotal = qty * matPrice;
  const equipSel  = document.getElementById('r-equip');
  const equipId   = parseInt(equipSel.value)||null;
  const equipOpt  = equipSel.options[equipSel.selectedIndex];
  const payMethod = document.getElementById('r-pay').value;

  const rec = {
    date: document.getElementById('r-date').value,
    customerType: ct, customerId: custId, customerName: custName,
    companyName: cu?.company||'',
    waterBon: document.getElementById('r-wbon').value,
    loadBon:  document.getElementById('r-lbon').value,
    materialId: matId, materialName: mat?.name||'',
    materialPrice: matPrice, qty, customerTotal,
    tip: parseFloat(document.getElementById('r-tip').value)||0,
    payMethod,
    tractorNum: document.getElementById('r-tractor').value.trim(),
    trailerNum: document.getElementById('r-trailer').value.trim(),
    equipId,
    equipType:    equipOpt&&equipOpt.value ? equipOpt.dataset.type : '',
    equipPricePerM: equipOpt&&equipOpt.value ? parseFloat(equipOpt.dataset.ppm)||0 : 0,
    equipPricePerH: equipOpt&&equipOpt.value ? parseFloat(equipOpt.dataset.pph)||0 : 0,
  };

  const recId = await dbPut('receipts', rec);

  // update equipment meters
  if(equipId && rec.equipType==='fixed'){
    const eq = await dbGet('equipment', equipId);
    if(eq) await dbUpdate('equipment', equipId, { totalMeters: (eq.totalMeters||0)+qty });
  }

  // update customer balance by recalculation
  if(custId && payMethod==='account'){
    await recalcCustomerBalance(custId);
  }

  // treasury - cash sales
  if(payMethod==='cash'){
    await dbPut('treasury', { date: rec.date, type:'in', category:'مبيعات كاش', description:`إيصال تحميل - ${custName} - ${mat?.name||''}`, amount: customerTotal, ref: recId });
  }
  // treasury - office tip (always, regardless of pay method)
  if(rec.tip > 0){
    await dbPut('treasury', { date: rec.date, type:'in', category:'اكرامية مكتب', description:`اكرامية - ${custName}`, amount: rec.tip, ref: recId });
  }

  closeModal(); navigate('receipts');
}

async function deleteReceipt(id){
  if(!confirm('هل تريد حذف هذا الإيصال؟')) return;
  const r = await dbGet('receipts', id);
  if(!r) return;
  // Delete receipt
  await dbDelete('receipts', id);
  // Reverse equipment meters
  if(r.equipId && r.equipType==='fixed'){
    const eq = await dbGet('equipment', r.equipId);
    if(eq) await dbUpdate('equipment', r.equipId, { totalMeters: Math.max(0,(eq.totalMeters||0)-r.qty) });
  }
  // Recalculate customer balance from remaining receipts
  if(r.customerId && r.payMethod==='account'){
    await recalcCustomerBalance(r.customerId);
  }
  // Remove related treasury entry
  const tr = await dbGetAll('treasury');
  const related = tr.find(t=>t.ref===id);
  if(related) await dbDelete('treasury', related.id);
  navigate('receipts');
}


async function showEditReceiptModal(id){
  const r = await dbGet('receipts', id);
  if(!r) return;
  const [customers, materials, vehicles, equipment] = await Promise.all([
    dbGetAll('customers'), dbGetAll('materials'), dbGetAll('vehicles'), dbGetAll('equipment')
  ]);
  const acctCusts = customers.filter(c=>c.type==='account');
  const activeEq  = equipment.filter(e=>e.status==='active');
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>✏️ تعديل إيصال</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="er-date" value="${r.date}"></div>
        <div class="form-group"><label>نوع العميل</label>
          <select id="er-ctype">
            <option value="account" ${r.customerType==='account'?'selected':''}>عميل حساب</option>
            <option value="cash" ${r.customerType==='cash'?'selected':''}>عميل نقدي</option>
          </select>
        </div>
        <div class="form-group"><label>اسم العميل</label>
          <select id="er-customer">
            <option value="">-- اختر عميل --</option>
            ${acctCusts.map(c=>'<option value="'+c.id+'"'+(r.customerId===c.id?' selected':'')+'>'+c.name+'</option>').join('')}
          </select>
        </div>
        <div class="form-group"><label>البون المائي</label><input type="text" id="er-wbon" value="${r.waterBon||''}"></div>
        <div class="form-group"><label>بون التحميل</label><input type="text" id="er-lbon" value="${r.loadBon||''}"></div>
        <div class="form-group"><label>رقم الجرار</label><input type="text" id="er-tractor" value="${r.tractorNum||''}"></div>
        <div class="form-group"><label>رقم المقطورة</label><input type="text" id="er-trailer" value="${r.trailerNum||''}"></div>
        <div class="form-group"><label>الخامة</label>
          <select id="er-material">
            ${materials.map(m=>'<option value="'+m.id+'"'+(r.materialId===m.id?' selected':'')+'>'+m.name+'</option>').join('')}
          </select>
        </div>
        <div class="form-group"><label>الكمية (م³)</label><input type="number" id="er-qty" value="${r.qty}" min="0" step="0.01" oninput="calcEditTotal()"></div>
        <div class="form-group"><label>سعر الخامة (ج.م)</label><input type="number" id="er-price" value="${r.materialPrice}" min="0" step="0.01" oninput="calcEditTotal()"></div>
        <div class="form-group"><label>اكرامية المكتب</label><input type="number" id="er-tip" value="${r.tip||0}" min="0"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="er-pay">
            <option value="cash" ${r.payMethod==='cash'?'selected':''}>كاش</option>
            <option value="account" ${r.payMethod==='account'?'selected':''}>يضاف للحساب</option>
          </select>
        </div>
        <div class="form-group"><label>المعدة</label>
          <select id="er-equip">
            <option value="">-- بدون معدة --</option>
            ${activeEq.map(e=>'<option value="'+e.id+'"'+(r.equipId===e.id?' selected':'')+' data-type="'+e.type+'" data-ppm="'+(e.pricePerMeter||0)+'">'+e.name+'</option>').join('')}
          </select>
        </div>
      </div>
      <div class="price-row mt-12">
        <div class="flex justify-between items-center">
          <div><div class="text-muted" style="font-size:12px">إجمالي العميل</div>
          <div style="font-size:20px;font-weight:700;color:var(--success)" id="er-total-display">${fmt(r.customerTotal)} ج.م</div></div>
        </div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveEditReceipt(${id})">💾 حفظ التعديل</button>
    </div>
  </div>`);
}

function calcEditTotal(){
  const qty = parseFloat(document.getElementById('er-qty')?.value)||0;
  const price = parseFloat(document.getElementById('er-price')?.value)||0;
  const el = document.getElementById('er-total-display');
  if(el) el.textContent = fmt(qty*price) + ' ج.م';
}

async function saveEditReceipt(id){
  const oldRec = await dbGet('receipts', id);
  if(!oldRec) return;
  const qty = parseFloat(document.getElementById('er-qty').value)||0;
  const price = parseFloat(document.getElementById('er-price').value)||0;
  const custId = parseInt(document.getElementById('er-customer').value)||null;
  const matSel = document.getElementById('er-material');
  const matId = parseInt(matSel.value)||null;
  const matName = matSel.options[matSel.selectedIndex]?.text||'';
  const payMethod = document.getElementById('er-pay').value;
  const equipSel = document.getElementById('er-equip');
  const equipId = parseInt(equipSel.value)||null;
  const customerTotal = qty * price;

  // Reverse old equipment meters
  if(oldRec.equipId && oldRec.equipType==='fixed'){
    const eq = await dbGet('equipment', oldRec.equipId);
    if(eq) await dbUpdate('equipment', oldRec.equipId, { totalMeters: Math.max(0,(eq.totalMeters||0)-oldRec.qty) });
  }

  // Apply new equipment meters
  if(equipId){
    const equipOpt = equipSel.options[equipSel.selectedIndex];
    if(equipOpt?.dataset?.type==='fixed'){
      const eq = await dbGet('equipment', equipId);
      if(eq) await dbUpdate('equipment', equipId, { totalMeters: (eq.totalMeters||0)+qty });
    }
  }

  // Update receipt
  await dbUpdate('receipts', id, {
    date: document.getElementById('er-date').value,
    customer_type: document.getElementById('er-ctype').value,
    customer_id: custId, customer_name: document.getElementById('er-customer').options[document.getElementById('er-customer').selectedIndex]?.text||oldRec.customerName,
    water_bon: document.getElementById('er-wbon').value,
    load_bon: document.getElementById('er-lbon').value,
    tractor_num: document.getElementById('er-tractor').value,
    trailer_num: document.getElementById('er-trailer').value,
    material_id: matId, material_name: matName,
    material_price: price, qty, customer_total: customerTotal,
    tip: parseFloat(document.getElementById('er-tip').value)||0,
    pay_method: payMethod,
    equip_id: equipId
  });

  // Recalculate customer balance
  const affectedCustomers = new Set([oldRec.customerId, custId].filter(Boolean));
  for(const cid of affectedCustomers) await recalcCustomerBalance(cid);

  closeModal(); navigate('receipts');
}
async function printReceipt(id){
  const r = await dbGet('receipts', id); if(!r) return;
  const s = await dbGetSettings();
  const win = window.open('','_blank','width=800,height=600');
  win.document.write(`<!DOCTYPE html><html dir="rtl"><head><meta charset="UTF-8">
  <style>body{font-family:Arial,sans-serif;padding:20px;font-size:14px}h2{text-align:center;margin-bottom:4px}
  p.sub{text-align:center;color:#666;margin-bottom:20px;font-size:12px}
  table{width:100%;border-collapse:collapse}td,th{padding:8px;border:1px solid #ddd;text-align:right}th{background:#f5f5f5}
  .total{font-size:18px;font-weight:bold;text-align:center;margin-top:16px;border:2px solid #333;padding:8px;background:#f9f9f9}
  .sig{display:grid;grid-template-columns:1fr 1fr;gap:40px;margin-top:40px;text-align:center}.sig div{border-top:1px solid #333;padding-top:8px}
  </style></head><body>
  <h2>${s.companyName||'محجر الدولية'}</h2><p class="sub">${s.address||''} | ${s.phone||''}</p>
  <h3 style="text-align:center;background:#eee;padding:8px;margin-bottom:16px">إيصال تحميل</h3>
  <table>
    <tr><td><b>التاريخ</b></td><td>${r.date}</td><td><b>العميل</b></td><td>${r.customerName||'نقدي'}${r.companyName?' ('+r.companyName+')':''}</td></tr>
    <tr><td><b>البون المائي</b></td><td>${r.waterBon||'-'}</td><td><b>بون التحميل</b></td><td>${r.loadBon||'-'}</td></tr>
    <tr><td><b>الخامة</b></td><td>${r.materialName||'-'}</td><td><b>طريقة الدفع</b></td><td>${r.payMethod==='cash'?'كاش':'على الحساب'}</td></tr>
    <tr><td><b>رقم الجرار</b></td><td>${r.tractorNum||'-'}</td><td><b>رقم المقطورة</b></td><td>${r.trailerNum||'-'}</td></tr>
    <tr><td><b>الكمية (م³)</b></td><td>${r.qty}</td><td><b>سعر الخامة</b></td><td>${fmt(r.materialPrice)} ج.م/م³</td></tr>
    <tr><td><b>اكرامية المكتب</b></td><td>${fmt(r.tip||0)} ج.م</td><td></td><td></td></tr>
  </table>
  <div class="total">إجمالي النقلة: ${fmt(r.customerTotal)} ج.م</div>
  <div class="sig"><div>توقيع المكتب</div><div>توقيع العميل / السائق</div></div>
  </body></html>`);
  win.document.close(); setTimeout(()=>win.print(),500);
}

// quick add vehicle/customer from receipt modal
async function showQuickVehicleModal(){
  // Save current receipt form state
  _savedReceiptState = captureReceiptFormState();
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>🚛 إضافة سيارة جديدة</h3><button class="close-btn" onclick="closeModal();showReceiptModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>رقم الجرار</label><input type="text" id="qv-tractor" placeholder="رقم الجرار"></div>
        <div class="form-group"><label>رقم المقطورة</label><input type="text" id="qv-trailer" placeholder="رقم المقطورة"></div>
        <div class="form-group"><label>السائق</label><input type="text" id="qv-driver"></div>
        <div class="form-group"><label>الهاتف</label><input type="text" id="qv-phone"></div>
        <div class="form-group"><label>الكمية / التكعيب (م³)</label><input type="number" id="qv-cap" min="0" step="0.01"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal();showReceiptModal()">إلغاء</button>
      <button class="btn btn-success" onclick="saveQuickVehicle()">💾 حفظ وإضافة</button>
    </div>
  </div>`);
}

async function saveQuickVehicle(){
  const tractor = document.getElementById('qv-tractor').value.trim();
  if(!tractor){ alert('يرجى إدخال رقم الجرار'); return; }
  await dbPut('vehicles',{ tractorNum:tractor, trailerNum:document.getElementById('qv-trailer').value.trim(), driver:document.getElementById('qv-driver').value.trim(), phone:document.getElementById('qv-phone').value.trim(), capacity:parseFloat(document.getElementById('qv-cap').value)||0, notes:'' });
  closeModal(); await showReceiptModal();
  setTimeout(()=>{
    restoreReceiptFormState(_savedReceiptState);
    const inp=document.getElementById('r-tractor');
    if(inp){ inp.value=tractor; onTractorInput(tractor); }
    _savedReceiptState=null;
  },150);
}

async function showQuickCustomerModal(){
  _savedReceiptState = captureReceiptFormState();
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>👤 إضافة عميل جديد</h3><button class="close-btn" onclick="closeModal();showReceiptModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>اسم العميل</label><input type="text" id="qc-name"></div>
        <div class="form-group"><label>اسم الشركة</label><input type="text" id="qc-company" placeholder="اختياري"></div>
        <div class="form-group"><label>الهاتف</label><input type="text" id="qc-phone"></div>
        <div class="form-group"><label>النوع</label>
          <select id="qc-type"><option value="account">صاحب حساب</option><option value="cash">عميل نقدي</option></select>
        </div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal();showReceiptModal()">إلغاء</button>
      <button class="btn btn-success" onclick="saveQuickCustomer()">💾 حفظ وإضافة</button>
    </div>
  </div>`);
}

async function saveQuickCustomer(){
  const name = document.getElementById('qc-name').value.trim();
  if(!name){ alert('يرجى إدخال اسم العميل'); return; }
  const newId = await dbPut('customers',{ name, company:document.getElementById('qc-company').value.trim(), phone:document.getElementById('qc-phone').value.trim(), type:document.getElementById('qc-type').value, address:'', notes:'', prices:[], balance:0 });
  closeModal(); await showReceiptModal();
  setTimeout(()=>{
    restoreReceiptFormState(_savedReceiptState);
    const sel=document.getElementById('r-customer');
    if(sel && newId){ sel.value=newId; onReceiptCustomerChange(); }
    _savedReceiptState=null;
  },150);
}

// =========================================================
// ===== CUSTOMERS =====
// =========================================================
async function renderCustomers(){
  const customers = await dbGetAll('customers');
  const mats = await dbGetAll('materials');
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16 no-print">
    <div class="search-bar" style="flex:1;margin-bottom:0">
      <input type="text" id="cust-search" placeholder="بحث بالاسم أو الشركة أو الهاتف..." oninput="filterCustomers()">
      <select id="cust-type" onchange="filterCustomers()">
        <option value="">كل الأنواع</option>
        <option value="account">أصحاب حسابات</option>
        <option value="cash">عملاء نقديون</option>
      </select>
    </div>
    <button class="btn btn-primary no-print" onclick="showCustomerModal()" style="margin-right:12px;white-space:nowrap">➕ عميل جديد</button>
  </div>
  <div class="card">
    <div class="table-wrap">
      <table>
        <thead><tr><th>#</th><th>الاسم</th><th class="hide-md">اسم الشركة</th><th class="hide-md">الهاتف</th><th>النوع</th><th class="hide-md">أسعار الخامات</th><th>الرصيد</th><th>إجراءات</th></tr></thead>
        <tbody id="customers-body"></tbody>
      </table>
    </div>
  </div>`;
  renderCustomersTable(customers, mats);
}

async function filterCustomers(){
  let custs = await dbGetAll('customers');
  const mats = await dbGetAll('materials');
  const q = (document.getElementById('cust-search')?.value||'').toLowerCase();
  const t = document.getElementById('cust-type')?.value||'';
  if(q) custs = custs.filter(x=>x.name.toLowerCase().includes(q)||(x.company||'').toLowerCase().includes(q)||x.phone.includes(q));
  if(t) custs = custs.filter(x=>x.type===t);
  renderCustomersTable(custs, mats);
}

function renderCustomersTable(customers, mats){
  const tb = document.getElementById('customers-body'); if(!tb) return;
  tb.innerHTML = customers.map((c,i)=>`
    <tr>
      <td data-label="#">${i+1}</td><td data-label="الاسم"><b>${c.name}</b></td><td data-label="الشركة" class="hide-md">${c.company||'-'}</td>
      <td data-label="الهاتف" class="hide-md" dir="ltr">${c.phone}</td>
      <td><span class="badge ${c.type==='account'?'badge-info':'badge-gray'}">${c.type==='account'?'حساب':'نقدي'}</span></td>
      <td>${(c.prices||[]).map(p=>{const m=mats.find(x=>x.id===p.materialId);return m?`<span class="badge badge-purple">${m.name}: ${fmt(p.price)}</span> `:''}).join('')||'<span class="text-muted" style="font-size:11px">الافتراضي</span>'}</td>
      <td class="${(c.balance||0)>0?'text-danger':'text-success'}"><b>${fmt(c.balance||0)} ج.م</b></td>
      <td>
        <button class="btn btn-sm btn-outline" onclick="showCustomerModal(${c.id})">✏️</button>
        <button class="btn btn-sm btn-success" onclick="showPaymentModal(${c.id})">💰</button>
        <button class="btn btn-sm btn-danger" onclick="deleteCustomer(${c.id})">🗑️</button>
      </td>
    </tr>`).join('');
}

async function showCustomerModal(id=null){
  const c    = id ? await dbGet('customers', id) : {};
  const mats = await dbGetAll('materials');
  const prices = c.prices||[];
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>${id?'✏️ تعديل':'➕ إضافة'} عميل</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>اسم العميل</label><input type="text" id="c-name" value="${c.name||''}"></div>
        <div class="form-group"><label>اسم الشركة</label><input type="text" id="c-company" value="${c.company||''}" placeholder="اختياري"></div>
        <div class="form-group"><label>الهاتف</label><input type="text" id="c-phone" value="${c.phone||''}"></div>
        <div class="form-group"><label>النوع</label>
          <select id="c-type">
            <option value="account" ${c.type==='account'?'selected':''}>صاحب حساب</option>
            <option value="cash"    ${c.type==='cash'   ?'selected':''}>عميل نقدي</option>
          </select>
        </div>
        <div class="form-group"><label>العنوان</label><input type="text" id="c-addr"  value="${c.address||''}"></div>
        <div class="form-group"><label>ملاحظات</label><input type="text" id="c-notes" value="${c.notes||''}"></div>
      </div>
      <div class="divider"></div>
      <div style="font-weight:600;margin-bottom:8px">🪨 أسعار الخامات الخاصة</div>
      <p class="text-muted mb-12" style="font-size:12px">إذا لم تحدد سعراً ستُستخدم الأسعار الافتراضية</p>
      ${mats.map(m=>{
        const cp = prices.find(p=>p.materialId===m.id);
        return `<div class="flex items-center gap-8 mb-8" style="background:#f8f9fa;padding:10px;border-radius:6px">
          <span style="flex:1;font-weight:600">${m.name}</span>
          <label style="font-size:12px;color:var(--muted)">سعر خاص</label>
          <input type="checkbox" id="cp-check-${m.id}" ${cp?'checked':''} onchange="toggleCustomerPrice(${m.id})">
          <input type="number" id="cp-price-${m.id}" value="${cp?cp.price:m.defaultPrice}" min="0" step="0.01"
            style="width:110px;padding:6px;border:1px solid var(--border);border-radius:4px;font-family:Cairo,sans-serif;display:${cp?'block':'none'}">
          <span style="font-size:12px;color:var(--muted)" id="cp-default-${m.id}" ${cp?'style="display:none"':''}>افتراضي: ${fmt(m.defaultPrice)}</span>
        </div>`;
      }).join('')}
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveCustomer(${id||'null'})">💾 حفظ</button>
    </div>
  </div>`);
}

function toggleCustomerPrice(matId){
  const checked = document.getElementById(`cp-check-${matId}`).checked;
  document.getElementById(`cp-price-${matId}`).style.display = checked?'block':'none';
  const def = document.getElementById(`cp-default-${matId}`);
  if(def) def.style.display = checked?'none':'inline';
}

async function saveCustomer(id){
  const nameVal = document.getElementById('c-name')?.value.trim();
  const phoneVal = document.getElementById('c-phone')?.value.trim();
  if(!id && nameVal){
    const existing = await dbGetAll('customers');
    const dup = existing.find(c=>c.name===nameVal || (phoneVal && c.phone===phoneVal && phoneVal));
    if(dup){
      alert('⚠️ العميل "'+nameVal+'" مسجل من قبل!');
      return;
    }
  }
  const mats  = await dbGetAll('materials');
  const prices = [];
  mats.forEach(m=>{
    if(document.getElementById(`cp-check-${m.id}`)?.checked)
      prices.push({ materialId:m.id, price: parseFloat(document.getElementById(`cp-price-${m.id}`)?.value)||0 });
  });
  const name = document.getElementById('c-name').value.trim();
  if(!name){ alert('يرجى إدخال اسم العميل'); return; }
  const obj = { name, company:document.getElementById('c-company').value.trim(), phone:document.getElementById('c-phone').value.trim(), type:document.getElementById('c-type').value, address:document.getElementById('c-addr').value.trim(), notes:document.getElementById('c-notes').value.trim(), prices };
  if(id){
    const existing = await dbGet('customers', id);
    await dbUpdate('customers', id, { ...obj, balance: existing?.balance||0 });
  } else {
    await dbPut('customers', { ...obj, balance:0 });
  }
  closeModal(); navigate('customers');
}

async function deleteCustomer(id){
  if(!confirm('حذف؟')) return;
  await dbDelete('customers', id);
  navigate('customers');
}

async function showPaymentModal(custId){
  const c = await dbGet('customers', custId); if(!c) return;
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>💰 دفعة من: ${c.name}</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="stat-card blue mb-16"><div class="stat-label">الرصيد المستحق</div><div class="stat-num text-danger">${fmt(c.balance||0)} ج.م</div></div>
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="pay-date" value="${today()}"></div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="pay-amount" min="0"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="pay-method"><option value="cash">كاش</option><option value="bank">تحويل بنكي</option><option value="check">شيك</option></select>
        </div>
        <div class="form-group"><label>ملاحظات</label><input type="text" id="pay-notes"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-success" onclick="savePayment(${custId})">💾 تسجيل الدفعة</button>
    </div>
  </div>`);
}

async function savePayment(custId){
  const amount = parseFloat(document.getElementById('pay-amount').value)||0;
  if(!amount){ alert('يرجى إدخال المبلغ'); return; }
  // Recalculate balance from actual data
  await recalcCustomerBalance(custId);
  const p = { date:document.getElementById('pay-date').value, customerId:custId, customerName:c.name, amount, method:document.getElementById('pay-method').value, notes:document.getElementById('pay-notes').value };
  const pId = await dbPut('payments', p);
  await dbPut('treasury', { date:p.date, type:'in', category:'دفعة عميل', description:`دفعة من ${c.name}`, amount, ref:pId });
  closeModal(); navigate('customers');
}

// =========================================================
// ===== VEHICLES =====
// =========================================================
async function renderVehicles(){
  const vehicles = await dbGetAll('vehicles');
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16">
    <h3>إجمالي السيارات: ${vehicles.length}</h3>
    <button class="btn btn-primary" onclick="showVehicleModal()">➕ سيارة جديدة</button>
  </div>
  <div class="card">
    <p class="text-muted mb-12" style="font-size:12px">💡 اكتب رقم الجرار في الإيصال وستظهر بياناته تلقائياً</p>
    <div class="table-wrap">
      <table>
        <thead><tr><th>#</th><th>رقم الجرار</th><th>رقم المقطورة</th><th>السائق</th><th class="hide-md">الهاتف</th><th>التكعيب (م³)</th><th class="hide-md">ملاحظات</th><th>إجراءات</th></tr></thead>
        <tbody>${vehicles.map((v,i)=>`
          <tr>
            <td>${i+1}</td><td><b>${v.tractorNum}</b></td><td>${v.trailerNum}</td>
            <td>${v.driver}</td><td dir="ltr">${v.phone||'-'}</td>
            <td><span class="badge badge-info">${v.capacity||0} م³</span></td>
            <td>${v.notes||'-'}</td>
            <td>
              <button class="btn btn-sm btn-outline" onclick="showVehicleModal(${v.id})">✏️</button>
              <button class="btn btn-sm btn-danger" onclick="deleteVehicle(${v.id})">🗑️</button>
            </td>
          </tr>`).join('')}
        </tbody>
      </table>
    </div>
  </div>`;
}

async function showVehicleModal(id=null){
  const v = id ? await dbGet('vehicles', id) : {};
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>${id?'تعديل':'إضافة'} سيارة</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>رقم الجرار</label><input type="text" id="v-tractor" value="${v.tractorNum||''}"></div>
        <div class="form-group"><label>رقم المقطورة</label><input type="text" id="v-trailer" value="${v.trailerNum||''}"></div>
        <div class="form-group"><label>السائق</label><input type="text" id="v-driver" value="${v.driver||''}"></div>
        <div class="form-group"><label>الهاتف</label><input type="text" id="v-phone" value="${v.phone||''}"></div>
        <div class="form-group"><label>التكعيب (م³)</label><input type="number" id="v-cap" value="${v.capacity||''}"></div>
        <div class="form-group"><label>ملاحظات</label><input type="text" id="v-notes" value="${v.notes||''}"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveVehicle(${id||'null'})">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveVehicle(id){
  const tractorVal = document.getElementById('v-tractor').value.trim();
  if(!id && tractorVal){
    const existing = await dbGetAll('vehicles');
    if(existing.find(v=>v.tractorNum===tractorVal)){
      alert('⚠️ رقم الجرار "'+tractorVal+'" مسجل من قبل!');
      return;
    }
  }
  const obj = { tractorNum:document.getElementById('v-tractor').value.trim(), trailerNum:document.getElementById('v-trailer').value.trim(), driver:document.getElementById('v-driver').value.trim(), phone:document.getElementById('v-phone').value.trim(), capacity:parseFloat(document.getElementById('v-cap').value)||0, notes:document.getElementById('v-notes').value };
  if(!obj.tractorNum){ alert('يرجى إدخال رقم الجرار'); return; }
  if(id) await dbUpdate('vehicles', id, obj);
  else   await dbPut('vehicles', obj);
  closeModal(); renderVehicles();
}
async function deleteVehicle(id){ if(!confirm('حذف؟')) return; await dbDelete('vehicles',id); renderVehicles(); }

// =========================================================
// ===== EQUIPMENT =====
// =========================================================
async function renderEquipment(){
  const eq = await dbGetAll('equipment');
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16">
    <h3>إجمالي المعدات: ${eq.length}</h3>
    <button class="btn btn-primary" onclick="showEquipmentModal()">➕ معدة جديدة</button>
  </div>
  <div class="card">
    <div class="table-wrap">
      <table>
        <thead><tr><th>#</th><th>الاسم</th><th>النوع</th><th>السعر</th><th>الحالة</th><th>إجراءات</th></tr></thead>
        <tbody>${eq.map((e,i)=>`
          <tr>
            <td>${i+1}</td><td><b>${e.name}</b></td>
            <td><span class="badge ${e.type==='fixed'?'badge-info':'badge-warning'}">${e.type==='fixed'?'ثابتة (بالأمتار)':'إيجار (بالساعة)'}</span></td>
            <td>${e.type==='fixed'?fmt(e.pricePerMeter||0)+' ج.م/م³':fmt(e.pricePerHour||0)+' ج.م/ساعة'}</td>
            <td><span class="badge ${e.status==='active'?'badge-success':'badge-danger'}">${e.status==='active'?'نشطة':'متوقفة'}</span></td>
            <td>
              <button class="btn btn-sm btn-outline" onclick="showEquipmentModal(${e.id})">✏️</button>
              <button class="btn btn-sm btn-danger" onclick="deleteEquip(${e.id})">🗑️</button>
            </td>
          </tr>`).join('')}
        </tbody>
      </table>
    </div>
  </div>`;
}

async function showEquipmentModal(id=null){
  const e = id ? await dbGet('equipment', id) : {};
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>${id?'تعديل':'إضافة'} معدة</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>الاسم</label><input type="text" id="e-name" value="${e.name||''}"></div>
        <div class="form-group"><label>النوع</label>
          <select id="e-type" onchange="toggleEquipPrice()">
            <option value="fixed"  ${e.type==='fixed' ?'selected':''}>ثابتة (تحاسب بالأمتار)</option>
            <option value="rental" ${e.type==='rental'?'selected':''}>إيجار (تحاسب بالساعة)</option>
          </select>
        </div>
        <div class="form-group" id="e-pm-group" ${e.type==='rental'?'style="display:none"':''}><label>سعر المتر (ج.م/م³)</label><input type="number" id="e-pm" value="${e.pricePerMeter||0}"></div>
        <div class="form-group" id="e-ph-group" ${e.type!=='rental'?'style="display:none"':''}><label>سعر الساعة (ج.م/ساعة)</label><input type="number" id="e-ph" value="${e.pricePerHour||0}"></div>
        <div class="form-group"><label>الحالة</label>
          <select id="e-status">
            <option value="active"  ${e.status==='active' ?'selected':''}>نشطة</option>
            <option value="stopped" ${e.status==='stopped'?'selected':''}>متوقفة</option>
          </select>
        </div>
        <div class="form-group" style="grid-column:1/-1"><label>ملاحظات</label><textarea id="e-notes">${e.notes||''}</textarea></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveEquipment(${id||'null'})">💾 حفظ</button>
    </div>
  </div>`);
}

function toggleEquipPrice(){
  const t = document.getElementById('e-type').value;
  document.getElementById('e-pm-group').style.display = t==='fixed' ?'':'none';
  document.getElementById('e-ph-group').style.display = t==='rental'?'':'none';
}

async function saveEquipment(id){
  const type = document.getElementById('e-type').value;
  const name = document.getElementById('e-name').value.trim();
  if(!name){ alert('يرجى إدخال الاسم'); return; }
  const obj = { name, type, pricePerMeter:type==='fixed'?parseFloat(document.getElementById('e-pm').value)||0:0, pricePerHour:type==='rental'?parseFloat(document.getElementById('e-ph').value)||0:0, status:document.getElementById('e-status').value, notes:document.getElementById('e-notes').value };
  if(id){
    const existing = await dbGet('equipment', id);
    await dbUpdate('equipment', id, { ...obj, totalMeters:existing.totalMeters||0, totalHours:existing.totalHours||0, custody:existing.custody||[] });
  } else {
    await dbPut('equipment', { ...obj, totalMeters:0, totalHours:0, custody:[] });
  }
  closeModal(); renderEquipment();
}
async function deleteEquip(id){ if(!confirm('حذف؟')) return; await dbDelete('equipment',id); renderEquipment(); }

// =========================================================
// ===== ACCOUNTS - CUSTOMERS =====
// =========================================================
async function renderAccountsCustomers(){
  const customers = await dbGetAll('customers');
  const accts = customers.filter(c=>c.type==='account');
  document.getElementById('content').innerHTML=`
  <div class="card mb-16 no-print">
    <div class="form-grid">
      <div class="form-group"><label>اختر العميل</label>
        <select id="acc-cust-sel" onchange="loadCustomerAccount()">
          <option value="">-- اختر عميل --</option>
          ${accts.map(c=>`<option value="${c.id}">${c.name}${c.company?' - '+c.company:''}</option>`).join('')}
        </select>
      </div>
      <div class="form-group"><label>من تاريخ</label><input type="date" id="acc-from" onchange="loadCustomerAccount()"></div>
      <div class="form-group"><label>إلى تاريخ</label><input type="date" id="acc-to"   onchange="loadCustomerAccount()"></div>
      <div class="form-group" style="align-self:flex-end">
        <button class="btn btn-primary" onclick="loadCustomerAccount()">🔍 عرض</button>
        <button class="btn btn-outline" style="margin-right:6px" onclick="printCustomerAccount()">🖨️ طباعة</button>
      </div>
    </div>
  </div>
  <div class="tabs no-print">
    <div class="tab active" id="acc-tab-stmt" onclick="switchAccTab('stmt')">كشف الحساب</div>
    <div class="tab"        id="acc-tab-recs" onclick="switchAccTab('recs')">إيصالات التحميل</div>
  </div>
  <div id="acc-result"></div>`;
}

let accTab='stmt';
function switchAccTab(t){ accTab=t; document.getElementById('acc-tab-stmt').classList.toggle('active',t==='stmt'); document.getElementById('acc-tab-recs').classList.toggle('active',t==='recs'); loadCustomerAccount(); }

async function loadCustomerAccount(){
  const custId = parseInt(document.getElementById('acc-cust-sel')?.value||0);
  const from   = document.getElementById('acc-from')?.value||'';
  const to     = document.getElementById('acc-to')?.value||'';
  const res    = document.getElementById('acc-result'); if(!res) return;
  if(!custId){ res.innerHTML=''; return; }
  const [c, allRecs, allPays] = await Promise.all([dbGet('customers',custId), dbGetAll('receipts'), dbGetAll('payments')]);
  if(!c){ res.innerHTML=''; return; }
  let receipts = allRecs.filter(r=>r.customerId===custId&&r.payMethod==='account');
  let payments = allPays.filter(p=>p.customerId===custId);
  if(from){ receipts=receipts.filter(r=>r.date>=from); payments=payments.filter(p=>p.date>=from); }
  if(to)  { receipts=receipts.filter(r=>r.date<=to);   payments=payments.filter(p=>p.date<=to);   }

  if(accTab==='recs'){
    const totalQty=receipts.reduce((s,r)=>s+r.qty,0), totalAmt=receipts.reduce((s,r)=>s+(r.customerTotal||0),0);
    res.innerHTML=`<div class="card"><div class="card-title">📋 إيصالات: ${c.name}${c.company?' ('+c.company+')':''}</div>
    <div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>الخامة</th><th>الجرار</th><th>المقطورة</th><th>الكمية</th><th>سعر الخامة</th><th>الإجمالي</th><th class="no-print">طباعة</th></tr></thead>
      <tbody>${receipts.map(r=>`<tr><td>${r.date}</td><td>${r.materialName}</td><td>${r.tractorNum||'-'}</td><td>${r.trailerNum||'-'}</td><td>${r.qty} م³</td><td>${fmt(r.materialPrice)}</td><td class="text-danger"><b>${fmt(r.customerTotal)}</b></td><td class="no-print"><button class="btn btn-sm btn-outline" onclick="printReceipt(${r.id})">🖨️</button></td></tr>`).join('')}</tbody>
      <tfoot><tr style="font-weight:700;background:#f0f7ff"><td colspan="4">الإجمالي</td><td>${totalQty} م³</td><td>-</td><td>${fmt(totalAmt)} ج.م</td><td></td></tr></tfoot>
    </table></div></div>`; return;
  }

  const allTx=[];
  receipts.forEach(r=>allTx.push({date:r.date,desc:`إيصال - ${r.materialName||''} - جرار: ${r.tractorNum||'-'}`,debit:r.customerTotal||0,credit:0}));
  payments.forEach(p=>allTx.push({date:p.date,desc:`دفعة مستلمة - ${p.method}`,debit:0,credit:p.amount}));
  allTx.sort((a,b)=>a.date.localeCompare(b.date));
  let bal=0;
  const rows=allTx.map(t=>{ bal+=t.debit-t.credit; return `<tr><td>${t.date}</td><td>${t.desc}</td><td class="text-danger">${t.debit?fmt(t.debit):'-'}</td><td class="text-success">${t.credit?fmt(t.credit):'-'}</td><td class="${bal>0?'text-danger':'text-success'}"><b>${fmt(bal)}</b></td></tr>`; }).join('');
  const totalDebit=receipts.reduce((s,r)=>s+(r.customerTotal||0),0), totalCredit=payments.reduce((s,p)=>s+p.amount,0);
  res.innerHTML=`
  <div class="stat-grid mb-16">
    <div class="stat-card red">  <div class="stat-label">إجمالي المديونية</div><div class="stat-num">${fmt(totalDebit)} ج.م</div></div>
    <div class="stat-card green"><div class="stat-label">إجمالي المدفوع</div>  <div class="stat-num">${fmt(totalCredit)} ج.م</div></div>
    <div class="stat-card ${c.balance>0?'red':'green'}"><div class="stat-label">الرصيد الحالي</div><div class="stat-num">${fmt(c.balance||0)} ج.م</div></div>
  </div>
  <div class="card"><div class="card-title">📊 كشف حساب: ${c.name}${c.company?' ('+c.company+')':''}</div>
  <div class="table-wrap"><table>
    <thead><tr><th>التاريخ</th><th>البيان</th><th>مدين (ج.م)</th><th>دائن (ج.م)</th><th>الرصيد (ج.م)</th></tr></thead>
    <tbody>${rows}</tbody>
  </table></div></div>`;
}

async function printCustomerAccount(){
  const custId=parseInt(document.getElementById('acc-cust-sel')?.value||0);
  if(!custId){ alert('اختر عميل أولاً'); return; }
  const from=document.getElementById('acc-from')?.value||'', to=document.getElementById('acc-to')?.value||'';
  const [c, allRecs, allPays]=await Promise.all([dbGet('customers',custId),dbGetAll('receipts'),dbGetAll('payments')]);
  if(!c) return;
  let receipts=allRecs.filter(r=>r.customerId===custId&&r.payMethod==='account');
  let payments=allPays.filter(p=>p.customerId===custId);
  if(from){receipts=receipts.filter(r=>r.date>=from);payments=payments.filter(p=>p.date>=from);}
  if(to)  {receipts=receipts.filter(r=>r.date<=to);  payments=payments.filter(p=>p.date<=to);}
  const allTx=[];
  receipts.forEach(r=>allTx.push({date:r.date,desc:`إيصال - ${r.materialName}`,debit:r.customerTotal||0,credit:0}));
  payments.forEach(p=>allTx.push({date:p.date,desc:'دفعة مستلمة',debit:0,credit:p.amount}));
  allTx.sort((a,b)=>a.date.localeCompare(b.date));
  let bal=0;
  const rows=allTx.map((t,i)=>{bal+=t.debit-t.credit;return `<tr><td>${i+1}</td><td>${t.date}</td><td>${t.desc}</td><td>${t.debit?fmt(t.debit):'-'}</td><td>${t.credit?fmt(t.credit):'-'}</td><td>${fmt(bal)}</td></tr>`;}).join('');
  const html=`<h3 style="text-align:center">كشف حساب: ${c.name}${c.company?' ('+c.company+')':''}</h3>
  <table><thead><tr><th>#</th><th>التاريخ</th><th>البيان</th><th>مدين</th><th>دائن</th><th>الرصيد</th></tr></thead><tbody>${rows}</tbody>
  <tfoot><tr class="total-row"><td colspan="3">الرصيد النهائي</td><td>${fmt(receipts.reduce((s,r)=>s+(r.customerTotal||0),0))}</td><td>${fmt(payments.reduce((s,p)=>s+p.amount,0))}</td><td>${fmt(c.balance||0)}</td></tr></tfoot></table>`;
  await printSection('كشف حساب عميل',html,from&&to?`من ${from} إلى ${to}`:'');
}

// =========================================================
// ===== ACCOUNTS - EQUIPMENT =====
// =========================================================
async function renderAccountsEquipment(){
  const eq = await dbGetAll('equipment');
  document.getElementById('content').innerHTML=`
  <div class="card mb-16 no-print">
    <div class="form-grid">
      <div class="form-group"><label>اختر المعدة</label>
        <select id="eq-sel" onchange="loadEquipmentAccount()">
          <option value="">-- اختر معدة --</option>
          ${eq.map(e=>`<option value="${e.id}">${e.name} (${e.type==='fixed'?'ثابتة':'إيجار'})</option>`).join('')}
        </select>
      </div>
      <div class="form-group"><label>من تاريخ</label><input type="date" id="eq-from" onchange="loadEquipmentAccount()"></div>
      <div class="form-group"><label>إلى تاريخ</label><input type="date" id="eq-to"   onchange="loadEquipmentAccount()"></div>
      <div class="form-group" style="align-self:flex-end">
        <button class="btn btn-outline" onclick="printEquipAccount()">🖨️ طباعة</button>
      </div>
    </div>
  </div>
  <div class="tabs no-print">
    <div class="tab active" id="eq-tab-main"    onclick="switchEqTab('main')">الحركة</div>
    <div class="tab"        id="eq-tab-custody" onclick="switchEqTab('custody')">العهد</div>
  </div>
  <div id="eq-acc-result">
    <div class="stat-grid">
      ${eq.map(e=>`
        <div class="stat-card ${e.type==='fixed'?'blue':'orange'}" onclick="document.getElementById('eq-sel').value=${e.id};loadEquipmentAccount()" style="cursor:pointer">
          <div class="stat-label">${e.name}</div>
          <div class="stat-num">${e.type==='fixed'?(e.totalMeters||0).toFixed(1)+' م³':(e.totalHours||0)+' ساعة'}</div>
          <div style="font-size:12px;color:var(--muted)">الإجمالي: ${fmt(e.type==='fixed'?(e.totalMeters||0)*(e.pricePerMeter||0):(e.totalHours||0)*(e.pricePerHour||0))} ج.م</div>
        </div>`).join('')}
    </div>
  </div>`;
}

let eqTab='main';
function switchEqTab(t){ eqTab=t; document.getElementById('eq-tab-main')?.classList.toggle('active',t==='main'); document.getElementById('eq-tab-custody')?.classList.toggle('active',t==='custody'); loadEquipmentAccount(); }

async function loadEquipmentAccount(){
  const eqId = parseInt(document.getElementById('eq-sel')?.value||0);
  const res  = document.getElementById('eq-acc-result'); if(!res) return;
  if(!eqId){ res.innerHTML=''; return; }
  const e    = await dbGet('equipment', eqId); if(!e) return;
  const from = document.getElementById('eq-from')?.value||'';
  const to   = document.getElementById('eq-to')?.value||'';

  if(eqTab==='custody'){
    const cust = e.custody||[];
    res.innerHTML=`
    <div class="card mb-16">
      <div class="card-title">📦 إضافة عهدة - ${e.name}</div>
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="cu-date" value="${today()}"></div>
        <div class="form-group"><label>المسؤول</label><input type="text" id="cu-person"></div>
        <div class="form-group" style="grid-column:1/-1"><label>البيان</label><textarea id="cu-desc"></textarea></div>
      </div>
      <button class="btn btn-primary mt-8" onclick="saveCustody(${eqId})">➕ إضافة</button>
    </div>
    <div class="card"><div class="card-title">📦 سجل العهد: ${e.name}</div>
    <div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>المسؤول</th><th>البيان</th><th>إجراءات</th></tr></thead>
      <tbody>${cust.map(c=>`<tr><td>${c.date}</td><td>${c.person}</td><td>${c.desc}</td><td><button class="btn btn-sm btn-danger" onclick="deleteCustody(${eqId},'${c.id}')">🗑️</button></td></tr>`).join('')||'<tr><td colspan="4" class="text-muted" style="text-align:center">لا توجد عهد</td></tr>'}</tbody>
    </table></div></div>`; return;
  }

  if(e.type==='fixed'){
    let recs = await dbGetAll('receipts');
    recs = recs.filter(r=>r.equipId===eqId);
    if(from) recs=recs.filter(r=>r.date>=from); if(to) recs=recs.filter(r=>r.date<=to);
    const totalM=recs.reduce((s,r)=>s+r.qty,0), totalAmt=totalM*(e.pricePerMeter||0);
    res.innerHTML=`
    <div class="stat-grid mb-16">
      <div class="stat-card blue">  <div class="stat-label">إجمالي الأمتار</div><div class="stat-num">${totalM.toFixed(2)} م³</div></div>
      <div class="stat-card green"> <div class="stat-label">سعر المتر</div>       <div class="stat-num">${fmt(e.pricePerMeter)} ج.م</div></div>
      <div class="stat-card orange"><div class="stat-label">إجمالي المستحق</div>  <div class="stat-num">${fmt(totalAmt)} ج.م</div></div>
    </div>
    <div class="card"><div class="card-title">📊 حركة المعدة: ${e.name}</div>
    <div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>الخامة</th><th>الجرار</th><th>المقطورة</th><th>الكمية</th><th>تكلفة المعدة</th></tr></thead>
      <tbody>${recs.slice().reverse().map(r=>`<tr><td>${r.date}</td><td>${r.materialName||'-'}</td><td>${r.tractorNum||'-'}</td><td>${r.trailerNum||'-'}</td><td>${r.qty} م³</td><td>${fmt(r.qty*(e.pricePerMeter||0))} ج.م</td></tr>`).join('')}</tbody>
      <tfoot><tr style="font-weight:700;background:#f0f7ff"><td colspan="4">الإجمالي</td><td>${totalM.toFixed(2)} م³</td><td>${fmt(totalAmt)} ج.م</td></tr></tfoot>
    </table></div></div>`;
  } else {
    let hours = await dbGetAll('equipment_hours');
    hours = hours.filter(h=>h.eqId===eqId);
    if(from) hours=hours.filter(h=>h.date>=from); if(to) hours=hours.filter(h=>h.date<=to);
    const totalH=hours.reduce((s,h)=>s+h.hours,0), totalAmt=totalH*(e.pricePerHour||0);
    res.innerHTML=`
    <div class="stat-grid mb-16">
      <div class="stat-card blue">  <div class="stat-label">إجمالي الساعات</div><div class="stat-num">${totalH} ساعة</div></div>
      <div class="stat-card green"> <div class="stat-label">سعر الساعة</div>    <div class="stat-num">${fmt(e.pricePerHour)} ج.م</div></div>
      <div class="stat-card orange"><div class="stat-label">الإجمالي</div>       <div class="stat-num">${fmt(totalAmt)} ج.م</div></div>
    </div>
    <div class="card mb-16"><div class="card-title">➕ إضافة ساعات عمل</div>
    <div class="form-grid">
      <div class="form-group"><label>التاريخ</label><input type="date" id="eq-h-date" value="${today()}"></div>
      <div class="form-group"><label>عدد الساعات</label><input type="number" id="eq-h-hours" min="0" step="0.5"></div>
      <div class="form-group"><label>ملاحظات</label><input type="text" id="eq-h-notes"></div>
      <div class="form-group" style="align-self:flex-end"><button class="btn btn-primary" onclick="saveEquipHours(${eqId})">💾 حفظ</button></div>
    </div></div>
    <div class="card"><div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>الساعات</th><th>الإجمالي</th><th>ملاحظات</th><th>حذف</th></tr></thead>
      <tbody>${hours.slice().reverse().map(h=>`<tr><td>${h.date}</td><td>${h.hours}</td><td>${fmt(h.hours*(e.pricePerHour||0))}</td><td>${h.notes||'-'}</td><td><button class="btn btn-sm btn-danger" onclick="deleteEquipHours(${h.id},${eqId})">🗑️</button></td></tr>`).join('')}</tbody>
    </table></div></div>`;
  }
}

async function saveCustody(eqId){
  const e = await dbGet('equipment', eqId); if(!e) return;
  const person = document.getElementById('cu-person').value.trim();
  if(!person){ alert('يرجى إدخال اسم المسؤول'); return; }
  const custody = [...(e.custody||[]), { id:String(genId()), date:document.getElementById('cu-date').value, person, desc:document.getElementById('cu-desc').value }];
  await dbUpdate('equipment', eqId, { custody });
  loadEquipmentAccount();
}

async function deleteCustody(eqId, cId){
  if(!confirm('حذف؟')) return;
  const e = await dbGet('equipment', eqId); if(!e) return;
  await dbUpdate('equipment', eqId, { custody: (e.custody||[]).filter(c=>c.id!==cId) });
  loadEquipmentAccount();
}

async function saveEquipHours(eqId){
  const h = parseFloat(document.getElementById('eq-h-hours').value)||0;
  if(!h){ alert('يرجى إدخال عدد الساعات'); return; }
  await dbPut('equipment_hours', { eqId, date:document.getElementById('eq-h-date').value, hours:h, notes:document.getElementById('eq-h-notes').value });
  const e = await dbGet('equipment', eqId);
  if(e) await dbUpdate('equipment', eqId, { totalHours: (e.totalHours||0)+h });
  loadEquipmentAccount();
}

async function deleteEquipHours(id, eqId){
  if(!confirm('حذف؟')) return;
  const h = await dbGet('equipment_hours', id);
  if(h){ const e=await dbGet('equipment',eqId); if(e) await dbUpdate('equipment',eqId,{totalHours:Math.max(0,(e.totalHours||0)-h.hours)}); }
  await dbDelete('equipment_hours', id);
  loadEquipmentAccount();
}

async function printEquipAccount(){
  const eqId=parseInt(document.getElementById('eq-sel')?.value||0);
  if(!eqId){ alert('اختر معدة أولاً'); return; }
  const e=await dbGet('equipment',eqId); if(!e) return;
  const from=document.getElementById('eq-from')?.value||'', to=document.getElementById('eq-to')?.value||'';
  let html='';
  if(e.type==='fixed'){
    let recs=await dbGetAll('receipts'); recs=recs.filter(r=>r.equipId===eqId);
    if(from) recs=recs.filter(r=>r.date>=from); if(to) recs=recs.filter(r=>r.date<=to);
    const totalM=recs.reduce((s,r)=>s+r.qty,0);
    html=`<h3 style="text-align:center">حساب المعدة: ${e.name}</h3>
    <table><thead><tr><th>التاريخ</th><th>الخامة</th><th>الجرار</th><th>المقطورة</th><th>الكمية</th><th>التكلفة</th></tr></thead>
    <tbody>${recs.map(r=>`<tr><td>${r.date}</td><td>${r.materialName||'-'}</td><td>${r.tractorNum||'-'}</td><td>${r.trailerNum||'-'}</td><td>${r.qty}</td><td>${fmt(r.qty*(e.pricePerMeter||0))}</td></tr>`).join('')}</tbody>
    <tfoot><tr class="total-row"><td colspan="4">الإجمالي</td><td>${totalM.toFixed(2)} م³</td><td>${fmt(totalM*(e.pricePerMeter||0))} ج.م</td></tr></tfoot></table>`;
  } else {
    let hours=await dbGetAll('equipment_hours'); hours=hours.filter(h=>h.eqId===eqId);
    if(from) hours=hours.filter(h=>h.date>=from); if(to) hours=hours.filter(h=>h.date<=to);
    const totalH=hours.reduce((s,h)=>s+h.hours,0);
    html=`<h3 style="text-align:center">حساب المعدة: ${e.name}</h3>
    <table><thead><tr><th>التاريخ</th><th>الساعات</th><th>الإجمالي</th><th>ملاحظات</th></tr></thead>
    <tbody>${hours.map(h=>`<tr><td>${h.date}</td><td>${h.hours}</td><td>${fmt(h.hours*(e.pricePerHour||0))}</td><td>${h.notes||'-'}</td></tr>`).join('')}</tbody>
    <tfoot><tr class="total-row"><td>الإجمالي</td><td>${totalH}</td><td>${fmt(totalH*(e.pricePerHour||0))}</td><td></td></tr></tfoot></table>`;
  }
  await printSection('حساب المعدات', html, from&&to?`من ${from} إلى ${to}`:'');
}

// =========================================================
// ===== MASREC =====
// =========================================================
async function renderMasrec(){
  const s = await dbGetSettings();
  const masrecPrice = s.masrecPricePerM3||0;
  const [receipts, payments] = await Promise.all([dbGetAll('receipts'), dbGetAll('masrec_payments')]);
  const totalQty  = receipts.reduce((s,r)=>s+r.qty,0);
  const totalDue  = totalQty * masrecPrice;
  const totalPaid = payments.reduce((s,p)=>s+p.amount,0);
  const remaining = totalDue - totalPaid;
  document.getElementById('content').innerHTML=`
  <div class="card mb-16">
    <div class="card-title">🏛️ إعدادات جهاز مستقبل مصر - جدول الأسعار</div>
    <p class="text-muted mb-12" style="font-size:12px">يمكن تحديد سعر مختلف لكل فترة زمنية — الحساب يتم تلقائياً حسب تاريخ كل إيصال</p>
    <div class="form-grid">
      <div class="form-group"><label>من تاريخ</label><input type="date" id="mp-from-date" value="${today()}"></div>
      <div class="form-group"><label>إلى تاريخ (اتركه فارغاً = مفتوح)</label><input type="date" id="mp-to-date"></div>
      <div class="form-group"><label>السعر (ج.م/م³)</label><input type="number" id="masrec-price-new" min="0" step="0.01" placeholder="0"></div>
      <div class="form-group" style="align-self:flex-end"><button class="btn btn-primary" onclick="addMasrecPriceRule()">➕ إضافة فترة سعر</button></div>
    </div>
    <div id="masrec-price-rules" class="mt-12"></div>
  </div>
  <div class="stat-grid mb-16">
    <div class="stat-card blue">  <div class="stat-label">إجمالي الكميات (م³)</div><div class="stat-num">${totalQty.toFixed(2)}</div></div>
    <div class="stat-card orange"><div class="stat-label">سعر المتر المكعب</div>   <div class="stat-num">${fmt(masrecPrice)} ج.م</div></div>
    <div class="stat-card red">   <div class="stat-label">إجمالي المستحق</div>    <div class="stat-num">${fmt(totalDue)} ج.م</div></div>
    <div class="stat-card green"> <div class="stat-label">إجمالي المدفوع</div>    <div class="stat-num">${fmt(totalPaid)} ج.م</div></div>
    <div class="stat-card ${remaining>0?'red':'green'}"><div class="stat-label">المتبقي</div><div class="stat-num">${fmt(remaining)} ج.م</div></div>
  </div>
  <div class="tabs no-print">
    <div class="tab active" id="mas-tab-stmt" onclick="switchMasTab('stmt')">كشف الحساب</div>
    <div class="tab"        id="mas-tab-pays" onclick="switchMasTab('pays')">سجل التوريد</div>
  </div>
  <div class="flex gap-8 mb-16 no-print flex-wrap">
    <input type="date" id="masrec-from" onchange="renderMasrecContent()">
    <input type="date" id="masrec-to"   onchange="renderMasrecContent()">
    <button class="btn btn-outline" onclick="printMasrec()">🖨️ طباعة</button>
    <button class="btn btn-success" onclick="showMasrecPayModal()">➕ توريد دفعة</button>
  </div>
  <div id="masrec-content"></div>`;
  renderMasrecContent();
}

let masTab='stmt';
function switchMasTab(t){ masTab=t; document.getElementById('mas-tab-stmt')?.classList.toggle('active',t==='stmt'); document.getElementById('mas-tab-pays')?.classList.toggle('active',t==='pays'); renderMasrecContent(); }

async function renderMasrecContent(){
  const s=await dbGetSettings(), masrecPrice=s.masrecPricePerM3||0;
  const from=document.getElementById('masrec-from')?.value||'', to=document.getElementById('masrec-to')?.value||'';
  const c=document.getElementById('masrec-content'); if(!c) return;
  if(masTab==='pays'){
    const pays=await dbGetAll('masrec_payments');
    c.innerHTML=`<div class="card"><div class="card-title">💳 سجل التوريد</div>
    <div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>المبلغ</th><th>طريقة الدفع</th><th>المرجع</th><th>ملاحظات</th><th>حذف</th></tr></thead>
      <tbody>${pays.slice().reverse().map(p=>`<tr><td>${p.date}</td><td class="text-danger"><b>${fmt(p.amount)}</b></td><td>${p.method}</td><td>${p.ref||'-'}</td><td>${p.notes||'-'}</td><td><button class="btn btn-sm btn-danger" onclick="deleteMasrecPay(${p.id})">🗑️</button></td></tr>`).join('')}</tbody>
    </table></div></div>`; return;
  }
  let recs=await dbGetAll('receipts');
  if(from) recs=recs.filter(r=>r.date>=from); if(to) recs=recs.filter(r=>r.date<=to);
  const totalQty=recs.reduce((s,r)=>s+r.qty,0);
  c.innerHTML=`<div class="card"><div class="card-title">📊 كشف حساب جهاز مستقبل مصر</div>
  <div class="table-wrap"><table>
    <thead><tr><th>التاريخ</th><th>العميل</th><th>الخامة</th><th>الكمية (م³)</th><th>سعر الجهاز</th><th>المستحق</th></tr></thead>
    <tbody>${recs.slice().reverse().map(r=>`<tr><td>${r.date}</td><td>${r.customerName||'نقدي'}</td><td>${r.materialName||'-'}</td><td>${r.qty}</td><td>${fmt(masrecPrice)}</td><td class="text-danger">${fmt(r.qty*masrecPrice)}</td></tr>`).join('')}</tbody>
    <tfoot><tr style="font-weight:700;background:#fdecea"><td colspan="3">الإجمالي</td><td>${totalQty.toFixed(2)} م³</td><td>${fmt(masrecPrice)}</td><td>${fmt(totalQty*masrecPrice)} ج.م</td></tr></tfoot>
  </table></div></div>`;
}


// Masrec price rules stored in settings as JSON
async function getMasrecPriceRules(){
  const s = await dbGetSettings();
  return s.masrecPriceRules || [{fromDate:'2000-01-01', toDate:'', price: s.masrecPricePerM3||0}];
}

async function addMasrecPriceRule(){
  const fromDate = document.getElementById('mp-from-date').value;
  const toDate   = document.getElementById('mp-to-date').value;
  const price    = parseFloat(document.getElementById('masrec-price-new').value)||0;
  if(!fromDate || !price){ alert('يرجى إدخال التاريخ والسعر'); return; }
  const s = await dbGetSettings();
  const rules = s.masrecPriceRules || [];
  rules.push({fromDate, toDate, price});
  rules.sort((a,b)=>a.fromDate.localeCompare(b.fromDate));
  s.masrecPriceRules = rules;
  s.masrecPricePerM3 = price; // keep latest as default
  await dbSaveSettings(s);
  renderMasrec();
}

async function deleteMasrecPriceRule(idx){
  if(!confirm('حذف هذه الفترة؟')) return;
  const s = await dbGetSettings();
  const rules = s.masrecPriceRules || [];
  rules.splice(idx, 1);
  s.masrecPriceRules = rules;
  await dbSaveSettings(s);
  renderMasrec();
}

function getMasrecPriceForDate(rules, date){
  // Find the applicable price rule for a given date
  const applicable = rules
    .filter(r => r.fromDate <= date && (!r.toDate || r.toDate >= date))
    .sort((a,b)=>b.fromDate.localeCompare(a.fromDate));
  return applicable.length ? applicable[0].price : (rules[rules.length-1]?.price || 0);
}

async function renderMasrecPriceRules(){
  const rules = await getMasrecPriceRules();
  const el = document.getElementById('masrec-price-rules');
  if(!el) return;
  el.innerHTML = `<div class="table-wrap"><table>
    <thead><tr><th>من تاريخ</th><th>إلى تاريخ</th><th>السعر (ج.م/م³)</th><th>حذف</th></tr></thead>
    <tbody>${rules.map((r,i)=>`<tr>
      <td>${r.fromDate}</td>
      <td>${r.toDate||'مفتوح'}</td>
      <td class="text-success"><b>${fmt(r.price)}</b></td>
      <td><button class="btn btn-sm btn-danger" onclick="deleteMasrecPriceRule(${i})">🗑️</button></td>
    </tr>`).join('')}</tbody>
  </table></div>`;
}

async function saveMasrecPrice(){
  const s=await dbGetSettings();
  s.masrecPricePerM3=parseFloat(document.getElementById('masrec-price').value)||0;
  await dbSaveSettings(s);
  alert('✅ تم حفظ سعر المتر المكعب');
  renderMasrec();
}

async function showMasrecPayModal(){
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>🏛️ توريد دفعة لجهاز مستقبل مصر</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="mp-date" value="${today()}"></div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="mp-amount" min="0"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="mp-method"><option value="cash">كاش</option><option value="bank">تحويل بنكي</option><option value="check">شيك</option></select>
        </div>
        <div class="form-group"><label>رقم المرجع</label><input type="text" id="mp-ref" placeholder="اختياري"></div>
        <div class="form-group" style="grid-column:1/-1"><label>ملاحظات</label><textarea id="mp-notes"></textarea></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveMasrecPay()">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveMasrecPay(){
  const amount=parseFloat(document.getElementById('mp-amount').value)||0;
  if(!amount){ alert('يرجى إدخال المبلغ'); return; }
  const p={ date:document.getElementById('mp-date').value, amount, method:document.getElementById('mp-method').value, ref:document.getElementById('mp-ref').value, notes:document.getElementById('mp-notes').value };
  const pId=await dbPut('masrec_payments',p);
  await dbPut('treasury',{ date:p.date, type:'out', category:'جهاز مستقبل مصر', description:'توريد لجهاز مستقبل مصر', amount, ref:pId });
  closeModal(); renderMasrec();
}

async function deleteMasrecPay(id){ if(!confirm('حذف؟')) return; await dbDelete('masrec_payments',id); renderMasrec(); }

async function printMasrec(){
  const s=await dbGetSettings(), masrecPrice=s.masrecPricePerM3||0;
  const from=document.getElementById('masrec-from')?.value||'', to=document.getElementById('masrec-to')?.value||'';
  let recs=await dbGetAll('receipts');
  if(from) recs=recs.filter(r=>r.date>=from); if(to) recs=recs.filter(r=>r.date<=to);
  const pays=await dbGetAll('masrec_payments');
  const totalQty=recs.reduce((s,r)=>s+r.qty,0), totalPaid=pays.reduce((s,p)=>s+p.amount,0);
  const html=`<table><thead><tr><th>التاريخ</th><th>العميل</th><th>الخامة</th><th>الكمية</th><th>السعر</th><th>المستحق</th></tr></thead>
  <tbody>${recs.map(r=>`<tr><td>${r.date}</td><td>${r.customerName||'نقدي'}</td><td>${r.materialName||'-'}</td><td>${r.qty}</td><td>${fmt(masrecPrice)}</td><td>${fmt(r.qty*masrecPrice)}</td></tr>`).join('')}</tbody>
  <tfoot><tr class="total-row"><td colspan="3">الإجمالي</td><td>${totalQty.toFixed(2)}</td><td></td><td>${fmt(totalQty*masrecPrice)}</td></tr>
  <tr class="total-row"><td colspan="5">إجمالي المدفوع</td><td>${fmt(totalPaid)}</td></tr>
  <tr class="total-row"><td colspan="5">المتبقي</td><td>${fmt(totalQty*masrecPrice-totalPaid)}</td></tr></tfoot></table>`;
  await printSection('حساب جهاز مستقبل مصر', html, from&&to?`من ${from} إلى ${to}`:'');
}

// =========================================================
// ===== EXPENSES =====
// =========================================================
async function renderExpenses(){
  const exp = await dbGetAll('expenses');
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16 no-print flex-wrap gap-8">
    <div class="search-bar" style="flex:1;margin-bottom:0">
      <input type="text" id="exp-search" placeholder="بحث..." oninput="filterExpenses()">
      <input type="date" id="exp-from" onchange="filterExpenses()">
      <input type="date" id="exp-to"   onchange="filterExpenses()">
    </div>
    <div class="flex gap-8">
      <button class="btn btn-outline" onclick="printExpenses()">🖨️ طباعة</button>
      <button class="btn btn-danger"  onclick="showExpenseModal()">➕ مصروف</button>
    </div>
  </div>
  <div class="stat-card red mb-16" style="max-width:250px">
    <div class="stat-label">إجمالي المصروفات</div>
    <div class="stat-num">${fmt(exp.reduce((s,e)=>s+e.amount,0))} ج.م</div>
  </div>
  <div class="card"><div class="table-wrap"><table>
    <thead><tr><th>#</th><th>التاريخ</th><th>البيان</th><th class="hide-md">الفئة</th><th>المبلغ</th><th class="hide-md">الدفع</th><th class="no-print">حذف</th></tr></thead>
    <tbody id="exp-body"></tbody>
  </table></div></div>`;
  renderExpensesTable(exp);
}

async function filterExpenses(){
  let exp=await dbGetAll('expenses');
  const q=(document.getElementById('exp-search')?.value||'').toLowerCase();
  const f=document.getElementById('exp-from')?.value||'', t=document.getElementById('exp-to')?.value||'';
  if(q) exp=exp.filter(e=>e.desc.toLowerCase().includes(q)||(e.category||'').toLowerCase().includes(q));
  if(f) exp=exp.filter(e=>e.date>=f); if(t) exp=exp.filter(e=>e.date<=t);
  renderExpensesTable(exp);
}

function renderExpensesTable(exp){
  const tb=document.getElementById('exp-body'); if(!tb) return;
  tb.innerHTML=exp.slice().reverse().map((e,i)=>`
    <tr><td data-label="#">${exp.length-i}</td><td data-label="التاريخ">${e.date}</td><td data-label="البيان">${e.desc}</td>
    <td data-label="الفئة" class="hide-md"><span class="badge badge-gray">${e.category||'عام'}</span></td>
    <td data-label="المبلغ" class="text-danger"><b>${fmt(e.amount)} ج.م</b></td>
    <td data-label="الدفع" class="hide-md">${e.payMethod||'كاش'}</td>
    <td class="no-print"><button class="btn btn-sm btn-danger" onclick="deleteExpense(${e.id})">🗑️</button></td></tr>`).join('');
}

async function showExpenseModal(){
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>💸 مصروف جديد</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="ex-date" value="${today()}"></div>
        <div class="form-group"><label>الفئة</label>
          <div class="flex gap-8">
            <select id="ex-cat" style="flex:1" onchange="toggleCustomCat(this)">
              <option>رواتب</option><option>وقود</option><option>صيانة</option>
              <option>إيجار معدات</option><option>مشتريات</option>
              <option>كهرباء ومياه</option><option>اتصالات</option><option>متنوع</option>
              <option value="__new__">➕ فئة جديدة...</option>
            </select>
          </div>
          <input type="text" id="ex-cat-custom" placeholder="اكتب اسم الفئة الجديدة" style="display:none;margin-top:6px">
        </div>
        <div class="form-group" style="grid-column:1/-1"><label>البيان</label><input type="text" id="ex-desc" placeholder="وصف المصروف"></div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="ex-amount" min="0"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="ex-pay"><option value="cash">كاش</option><option value="bank">تحويل بنكي</option><option value="check">شيك</option></select>
        </div>
        <div class="form-group" id="ex-bank-group"><label>البنك / الصندوق</label>
          <select id="ex-bank-sel">
            <option value="">-- اختر (اختياري) --</option>
          </select>
        </div>
        <div class="form-group" style="grid-column:1/-1"><label>ملاحظات</label><textarea id="ex-notes"></textarea></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-danger" onclick="saveExpense()">💾 حفظ</button>
    </div>
  </div>`);
}


function toggleCustomCat(sel){
  const inp = document.getElementById('ex-cat-custom');
  if(!inp) return;
  inp.style.display = sel.value==='__new__' ? 'block' : 'none';
  if(sel.value==='__new__') inp.focus();
}

async function loadBanksIntoExpModal(){
  const banks = await dbGetAll('banks');
  const sel = document.getElementById('ex-bank-sel');
  if(!sel) return;
  banks.forEach(b=>{
    const opt = document.createElement('option');
    opt.value = b.id; opt.textContent = b.name + ' (' + b.type + ')';
    sel.appendChild(opt);
  });
}

async function saveExpense(){
  const amount=parseFloat(document.getElementById('ex-amount').value)||0;
  if(!amount){ alert('يرجى إدخال المبلغ'); return; }
  const desc=document.getElementById('ex-desc').value.trim()||'مصروف';
  const catSel=document.getElementById('ex-cat');
  const catCustom=document.getElementById('ex-cat-custom');
  const category=catSel.value==='__new__'?(catCustom?.value.trim()||'متنوع'):catSel.value;
  const e={ date:document.getElementById('ex-date').value, category, desc, amount, payMethod:document.getElementById('ex-pay').value, notes:document.getElementById('ex-notes').value };
  const eId=await dbPut('expenses',e);
  await dbPut('treasury',{ date:e.date, type:'out', category:e.category, description:desc, amount, ref:eId });
  closeModal(); renderExpenses();
}
async function deleteExpense(id){ if(!confirm('حذف؟')) return; await dbDelete('expenses',id); renderExpenses(); }

async function printExpenses(){
  let exp=await dbGetAll('expenses');
  const f=document.getElementById('exp-from')?.value||'', t=document.getElementById('exp-to')?.value||'';
  if(f) exp=exp.filter(e=>e.date>=f); if(t) exp=exp.filter(e=>e.date<=t);
  const total=exp.reduce((s,e)=>s+e.amount,0);
  const html=`<table><thead><tr><th>#</th><th>التاريخ</th><th>البيان</th><th>الفئة</th><th>المبلغ</th><th>الدفع</th></tr></thead>
  <tbody>${exp.slice().reverse().map((e,i)=>`<tr><td>${i+1}</td><td>${e.date}</td><td>${e.desc}</td><td>${e.category}</td><td>${fmt(e.amount)}</td><td>${e.payMethod}</td></tr>`).join('')}</tbody>
  <tfoot><tr class="total-row"><td colspan="4">الإجمالي</td><td>${fmt(total)}</td><td></td></tr></tfoot></table>`;
  await printSection('المصروفات', html, f&&t?`من ${f} إلى ${t}`:'');
}

// =========================================================
// ===== REVENUES =====
// =========================================================

async function showAddPaymentFromRevenues(){
  const customers = await dbGetAll('customers');
  const accts = customers.filter(c=>c.type==='account' && (c.balance||0)>0);
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>💰 استلام دفعة من عميل</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>العميل</label>
          <select id="rp-cust" onchange="showRevPayBalance()">
            <option value="">-- اختر عميل --</option>
            ${accts.map(c=>'<option value="'+c.id+'" data-bal="'+fmt(c.balance)+'">'+c.name+(c.company?' - '+c.company:'')+'  ('+fmt(c.balance)+' ج.م)</option>').join('')}
          </select>
        </div>
        <div class="form-group"><label>التاريخ</label><input type="date" id="rp-date" value="${today()}"></div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="rp-amount" min="0" placeholder="0"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="rp-method"><option value="cash">كاش</option><option value="bank">تحويل بنكي</option><option value="check">شيك</option></select>
        </div>
        <div class="form-group"><label>ملاحظات</label><input type="text" id="rp-notes"></div>
      </div>
      <div id="rp-balance-info" class="mt-8"></div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-success" onclick="saveRevPayment()">💾 تسجيل الدفعة</button>
    </div>
  </div>`);
}

function showRevPayBalance(){
  const sel = document.getElementById('rp-cust');
  const opt = sel.options[sel.selectedIndex];
  const el  = document.getElementById('rp-balance-info');
  if(el && opt.value) el.innerHTML = '<div class="stat-card red" style="max-width:200px"><div class="stat-label">الرصيد المستحق</div><div class="stat-num">'+opt.dataset.bal+' ج.م</div></div>';
}

async function saveRevPayment(){
  const custId = parseInt(document.getElementById('rp-cust').value)||null;
  const amount = parseFloat(document.getElementById('rp-amount').value)||0;
  if(!custId){ alert('يرجى اختيار العميل'); return; }
  if(!amount){ alert('يرجى إدخال المبلغ'); return; }
  const c = await dbGet('customers', custId);
  await dbUpdate('customers', custId, { balance: (c.balance||0)-amount });
  const p = { date:document.getElementById('rp-date').value, customerId:custId, customerName:c.name, amount, method:document.getElementById('rp-method').value, notes:document.getElementById('rp-notes').value };
  const pId = await dbPut('payments', p);
  await dbPut('treasury', { date:p.date, type:'in', category:'دفعة عميل', description:'دفعة من '+c.name, amount, ref:pId });
  closeModal();
  navigate('revenues');
}

async function renderRevenues(){
  const [recs, payments] = await Promise.all([dbGetAll('receipts'), dbGetAll('payments')]);
  const cashRecs=recs.filter(r=>r.payMethod==='cash');
  const tips=recs.reduce((s,r)=>s+(r.tip||0),0);
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16 no-print flex-wrap gap-8">
    <div class="search-bar" style="flex:1;margin-bottom:0">
      <input type="date" id="rev-from" onchange="filterRevenues()">
      <input type="date" id="rev-to"   onchange="filterRevenues()">
    </div>
    <div class="flex gap-8">
      <button class="btn btn-success" onclick="showAddPaymentFromRevenues()">💰 استلام دفعة من عميل</button>
      <button class="btn btn-outline" onclick="printRevenues()">🖨️ طباعة</button>
    </div>
  </div>
  <div class="stat-grid mb-16">
    <div class="stat-card green"><div class="stat-label">مبيعات كاش</div>       <div class="stat-num">${fmt(cashRecs.reduce((s,r)=>s+(r.customerTotal||0),0))} ج.م</div></div>
    <div class="stat-card blue"> <div class="stat-label">دفعات العملاء</div>     <div class="stat-num">${fmt(payments.reduce((s,p)=>s+p.amount,0))} ج.م</div></div>
    <div class="stat-card orange"><div class="stat-label">اكراميات المكتب</div>  <div class="stat-num">${fmt(tips)} ج.م</div></div>
    <div class="stat-card green"><div class="stat-label">إجمالي الإيرادات</div>  <div class="stat-num">${fmt(cashRecs.reduce((s,r)=>s+(r.customerTotal||0),0)+payments.reduce((s,p)=>s+p.amount,0)+tips)} ج.م</div></div>
  </div>
  <div class="tabs no-print">
    <div class="tab active" id="rev-tab-cash" onclick="switchRevTab('cash')">مبيعات كاش</div>
    <div class="tab"        id="rev-tab-pay"  onclick="switchRevTab('pay')">دفعات العملاء</div>
  </div>
  <div id="rev-content"></div>`;
  showRevTab('cash');
}

let revTab='cash';
function switchRevTab(t){ revTab=t; document.getElementById('rev-tab-cash')?.classList.toggle('active',t==='cash'); document.getElementById('rev-tab-pay')?.classList.toggle('active',t==='pay'); showRevTab(t); }
async function filterRevenues(){ showRevTab(revTab); }

async function showRevTab(t){
  const c=document.getElementById('rev-content'); if(!c) return;
  const from=document.getElementById('rev-from')?.value||'', to=document.getElementById('rev-to')?.value||'';
  if(t==='cash'){
    let recs=(await dbGetAll('receipts')).filter(r=>r.payMethod==='cash');
    if(from) recs=recs.filter(r=>r.date>=from); if(to) recs=recs.filter(r=>r.date<=to);
    const total=recs.reduce((s,r)=>s+(r.customerTotal||0),0);
    c.innerHTML=`<div class="card"><div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>العميل</th><th>الخامة</th><th>الكمية</th><th>الإجمالي</th><th>اكرامية</th></tr></thead>
      <tbody>${recs.slice().reverse().map(r=>`<tr><td>${r.date}</td><td>${r.customerName||'نقدي'}</td><td>${r.materialName||'-'}</td><td>${r.qty}</td><td class="text-success"><b>${fmt(r.customerTotal)}</b></td><td>${fmt(r.tip||0)}</td></tr>`).join('')}</tbody>
      <tfoot><tr style="font-weight:700;background:#eafaf1"><td colspan="4">الإجمالي</td><td>${fmt(total)}</td><td></td></tr></tfoot>
    </table></div></div>`;
  } else {
    let pays=await dbGetAll('payments');
    if(from) pays=pays.filter(p=>p.date>=from); if(to) pays=pays.filter(p=>p.date<=to);
    const total=pays.reduce((s,p)=>s+p.amount,0);
    c.innerHTML=`<div class="card"><div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>العميل</th><th>المبلغ</th><th>طريقة الدفع</th><th>ملاحظات</th></tr></thead>
      <tbody>${pays.slice().reverse().map(p=>`<tr><td>${p.date}</td><td>${p.customerName}</td><td class="text-success"><b>${fmt(p.amount)}</b></td><td>${p.method}</td><td>${p.notes||'-'}</td></tr>`).join('')}</tbody>
      <tfoot><tr style="font-weight:700;background:#eafaf1"><td colspan="2">الإجمالي</td><td>${fmt(total)}</td><td colspan="2"></td></tr></tfoot>
    </table></div></div>`;
  }
}

async function printRevenues(){
  const from=document.getElementById('rev-from')?.value||'', to=document.getElementById('rev-to')?.value||'';
  let cashRecs=(await dbGetAll('receipts')).filter(r=>r.payMethod==='cash'), pays=await dbGetAll('payments');
  if(from){cashRecs=cashRecs.filter(r=>r.date>=from);pays=pays.filter(p=>p.date>=from);}
  if(to)  {cashRecs=cashRecs.filter(r=>r.date<=to);  pays=pays.filter(p=>p.date<=to);}
  const totalCash=cashRecs.reduce((s,r)=>s+(r.customerTotal||0),0), totalPay=pays.reduce((s,p)=>s+p.amount,0);
  const html=`<h3>مبيعات كاش</h3>
  <table><thead><tr><th>التاريخ</th><th>العميل</th><th>الخامة</th><th>الكمية</th><th>الإجمالي</th></tr></thead>
  <tbody>${cashRecs.map(r=>`<tr><td>${r.date}</td><td>${r.customerName||'نقدي'}</td><td>${r.materialName||'-'}</td><td>${r.qty}</td><td>${fmt(r.customerTotal)}</td></tr>`).join('')}</tbody>
  <tfoot><tr class="total-row"><td colspan="4">إجمالي الكاش</td><td>${fmt(totalCash)}</td></tr></tfoot></table>
  <br><h3>دفعات العملاء</h3>
  <table><thead><tr><th>التاريخ</th><th>العميل</th><th>المبلغ</th><th>طريقة الدفع</th></tr></thead>
  <tbody>${pays.map(p=>`<tr><td>${p.date}</td><td>${p.customerName}</td><td>${fmt(p.amount)}</td><td>${p.method}</td></tr>`).join('')}</tbody>
  <tfoot><tr class="total-row"><td colspan="2">إجمالي الدفعات</td><td>${fmt(totalPay)}</td><td></td></tr>
  <tr class="total-row"><td colspan="2">إجمالي الإيرادات</td><td>${fmt(totalCash+totalPay)}</td><td></td></tr></tfoot></table>`;
  await printSection('الإيرادات', html, from&&to?`من ${from} إلى ${to}`:'');
}

// =========================================================
// ===== SALARIES =====
// =========================================================
async function renderSalaries(){
  const [emp, sal] = await Promise.all([dbGetAll('employees'), dbGetAll('salary_payments')]);
  document.getElementById('content').innerHTML=`
  <div class="flex justify-between items-center mb-16 flex-wrap gap-8">
    <h3>المعاملون: ${emp.length}</h3>
    <div class="flex gap-8">
      <button class="btn btn-outline" onclick="printSalaries()">🖨️ طباعة</button>
      <button class="btn btn-primary" onclick="showEmployeeModal()">➕ إضافة معامل</button>
    </div>
  </div>
  <div class="card mb-20">
    <div class="card-title">👷 قائمة المعاملين</div>
    <div class="table-wrap"><table>
      <thead><tr><th>#</th><th>الاسم</th><th>الوظيفة</th><th>الراتب</th><th>ميعاد الراتب</th><th>إجراءات</th></tr></thead>
      <tbody>${emp.map((e,i)=>`<tr><td>${i+1}</td><td><b>${e.name}</b></td><td>${e.role||'-'}</td><td class="text-success">${fmt(e.salary)} ج.م</td><td>يوم ${e.salaryDay||1} كل شهر</td>
        <td>
          <button class="btn btn-sm btn-success" onclick="showSalaryPayModal(${e.id})">💵 صرف</button>
          <button class="btn btn-sm btn-outline" onclick="showEmployeeModal(${e.id})">✏️</button>
          <button class="btn btn-sm btn-danger"  onclick="deleteEmployee(${e.id})">🗑️</button>
        </td></tr>`).join('')}
      </tbody>
    </table></div>
  </div>
  <div class="card">
    <div class="card-title">📊 سجل صرف الرواتب</div>
    <div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>الموظف</th><th>المبلغ</th><th class="hide-md">طريقة الدفع</th><th class="hide-md">المسؤول</th><th class="hide-md">ملاحظات</th></tr></thead>
      <tbody>${sal.slice().reverse().map(s=>`<tr>
  <td data-label="التاريخ">${s.date}</td>
  <td data-label="الموظف">${s.empName}</td>
  <td data-label="المبلغ" class="text-danger"><b>${fmt(s.amount)}</b></td>
  <td data-label="طريقة الدفع" class="hide-md">${s.method}</td>
  <td data-label="المسؤول" class="hide-md">${s.paidBy||'-'}</td>
  <td data-label="ملاحظات" class="hide-md">${s.notes||'-'}</td>
  <td>
    <button class="btn btn-sm btn-outline" onclick="showEditSalaryModal(${s.id})">✏️</button>
    <button class="btn btn-sm btn-danger" onclick="deleteSalaryPayment(${s.id})">🗑️</button>
  </td>
</tr>`).join('')}</tbody>
    </table></div>
  </div>`;
}

async function showEmployeeModal(id=null){
  const e = id ? await dbGet('employees', id) : {};
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>${id?'تعديل':'إضافة'} معامل</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>الاسم</label><input type="text" id="em-name" value="${e.name||''}"></div>
        <div class="form-group"><label>الوظيفة</label><input type="text" id="em-role" value="${e.role||''}"></div>
        <div class="form-group"><label>الراتب (ج.م)</label><input type="number" id="em-sal" value="${e.salary||0}"></div>
        <div class="form-group"><label>يوم صرف الراتب</label><input type="number" id="em-day" min="1" max="31" value="${e.salaryDay||1}"></div>
        <div class="form-group"><label>الهاتف</label><input type="text" id="em-phone" value="${e.phone||''}"></div>
        <div class="form-group"><label>ملاحظات</label><input type="text" id="em-notes" value="${e.notes||''}"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveEmployee(${id||'null'})">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveEmployee(id){
  const name=document.getElementById('em-name').value.trim();
  if(!name){ alert('يرجى إدخال الاسم'); return; }
  const obj={ name, role:document.getElementById('em-role').value, salary:parseFloat(document.getElementById('em-sal').value)||0, salaryDay:parseInt(document.getElementById('em-day').value)||1, phone:document.getElementById('em-phone').value, notes:document.getElementById('em-notes').value };
  if(id) await dbUpdate('employees',id,obj); else await dbPut('employees',obj);
  closeModal(); renderSalaries();
}
async function deleteEmployee(id){ if(!confirm('حذف؟')) return; await dbDelete('employees',id); renderSalaries(); }

async function showSalaryPayModal(empId){
  const e=await dbGet('employees',empId); if(!e) return;
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>💵 صرف راتب: ${e.name}</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="sp-date" value="${today()}"></div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="sp-amount" value="${e.salary||0}"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="sp-method"><option value="cash">كاش</option><option value="bank">تحويل بنكي</option></select>
        </div>
        <div class="form-group"><label>مين الي دفع</label><input type="text" id="sp-by"></div>
        <div class="form-group" style="grid-column:1/-1"><label>ملاحظات</label><input type="text" id="sp-notes"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-success" onclick="saveSalaryPay(${empId})">💾 صرف</button>
    </div>
  </div>`);
}

async function saveSalaryPay(empId){
  const e=await dbGet('employees',empId);
  const amount=parseFloat(document.getElementById('sp-amount').value)||0;
  if(!amount){ alert('يرجى إدخال المبلغ'); return; }
  const sp={ date:document.getElementById('sp-date').value, empId, empName:e.name, amount, method:document.getElementById('sp-method').value, paidBy:document.getElementById('sp-by').value, notes:document.getElementById('sp-notes').value };
  const spId=await dbPut('salary_payments',sp);
  await dbPut('treasury',{ date:sp.date, type:'out', category:'رواتب', description:`راتب ${e.name}`, amount, ref:spId });
  closeModal(); renderSalaries();
}


async function deleteSalaryPayment(id){
  if(!confirm('حذف هذا الراتب وإلغاء تأثيره من الخزينة؟')) return;
  // Remove from treasury
  const tr = await dbGetAll('treasury');
  const related = tr.find(t=>t.ref===id && t.category==='رواتب');
  if(related) await dbDelete('treasury', related.id);
  await dbDelete('salary_payments', id);
  renderSalaries();
}

async function showEditSalaryModal(id){
  const s = await dbGet('salary_payments', id);
  if(!s) return;
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>✏️ تعديل راتب: ${s.empName}</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>التاريخ</label><input type="date" id="es-date" value="${s.date}"></div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="es-amount" value="${s.amount}"></div>
        <div class="form-group"><label>طريقة الدفع</label>
          <select id="es-method">
            <option value="cash" ${s.method==='cash'?'selected':''}>كاش</option>
            <option value="bank" ${s.method==='bank'?'selected':''}>تحويل بنكي</option>
          </select>
        </div>
        <div class="form-group"><label>مين الي دفع</label><input type="text" id="es-by" value="${s.paidBy||''}"></div>
        <div class="form-group" style="grid-column:1/-1"><label>ملاحظات</label><input type="text" id="es-notes" value="${s.notes||''}"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveEditSalary(${id},${s.amount})">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveEditSalary(id, oldAmount){
  const newAmount = parseFloat(document.getElementById('es-amount').value)||0;
  if(!newAmount){ alert('يرجى إدخال المبلغ'); return; }
  // Update salary payment
  await dbUpdate('salary_payments', id, {
    date: document.getElementById('es-date').value,
    amount: newAmount,
    method: document.getElementById('es-method').value,
    paid_by: document.getElementById('es-by').value,
    notes: document.getElementById('es-notes').value
  });
  // Update related treasury entry
  const tr = await dbGetAll('treasury');
  const related = tr.find(t=>t.ref===id && t.category==='رواتب');
  if(related) await dbUpdate('treasury', related.id, { amount: newAmount });
  closeModal();
  renderSalaries();
}

async function printSalaries(){
  const sal=await dbGetAll('salary_payments');
  const total=sal.reduce((s,p)=>s+p.amount,0);
  const html=`<table><thead><tr><th>التاريخ</th><th>الموظف</th><th>المبلغ</th><th class="hide-md">طريقة الدفع</th><th class="hide-md">المسؤول</th><th class="hide-md">ملاحظات</th></tr></thead>
  <tbody>${sal.slice().reverse().map(s=>`<tr><td>${s.date}</td><td>${s.empName}</td><td>${fmt(s.amount)}</td><td>${s.method}</td><td>${s.paidBy||'-'}</td><td>${s.notes||'-'}</td></tr>`).join('')}</tbody>
  <tfoot><tr class="total-row"><td colspan="2">الإجمالي</td><td>${fmt(total)}</td><td colspan="3"></td></tr></tfoot></table>`;
  await printSection('سجل الرواتب', html);
}

// =========================================================
// ===== TREASURY =====
// =========================================================
async function renderTreasury(){
  const [tr, banks] = await Promise.all([dbGetAll('treasury'), dbGetAll('banks')]);
  const totalIn  = tr.filter(x=>x.type==='in').reduce((s,x)=>s+x.amount,0);
  const totalOut = tr.filter(x=>x.type==='out').reduce((s,x)=>s+x.amount,0);
  const balance  = totalIn - totalOut;
  const totalBanks = banks.reduce((s,b)=>s+b.balance,0);
  document.getElementById('content').innerHTML=`
  <div class="stat-grid mb-16">
    <div class="stat-card green"><div class="stat-label">إجمالي الإيرادات</div><div class="stat-num">${fmt(totalIn)} ج.م</div></div>
    <div class="stat-card red">  <div class="stat-label">إجمالي المصروفات</div><div class="stat-num">${fmt(totalOut)} ج.م</div></div>
    <div class="stat-card ${balance>=0?'green':'red'}"><div class="stat-label">رصيد الخزينة</div><div class="stat-num">${fmt(balance)} ج.م</div></div>
    <div class="stat-card blue"> <div class="stat-label">أرصدة البنوك</div><div class="stat-num">${fmt(totalBanks)} ج.م</div></div>
  </div>
  <div class="tabs no-print">
    <div class="tab active" id="tr-tab-all"   onclick="switchTrTab('all')">كل الحركات</div>
    <div class="tab"        id="tr-tab-banks" onclick="switchTrTab('banks')">البنوك والصناديق</div>
  </div>
  <div id="tr-content"></div>`;
  showTrTab('all');
}

let trTab='all';
function switchTrTab(t){ trTab=t; document.getElementById('tr-tab-all')?.classList.toggle('active',t==='all'); document.getElementById('tr-tab-banks')?.classList.toggle('active',t==='banks'); showTrTab(t); }

async function showTrTab(t){
  const c=document.getElementById('tr-content'); if(!c) return;
  if(t==='banks'){
    const banks=await dbGetAll('banks');
    c.innerHTML=`
    <div class="flex justify-between items-center mb-16">
      <h3>البنوك والصناديق: ${banks.length}</h3>
      <button class="btn btn-primary" onclick="showBankModal()">➕ إضافة</button>
    </div>
    <div class="card"><div class="table-wrap"><table>
      <thead><tr><th>الاسم</th><th>النوع</th><th>الرصيد</th><th>إجراءات</th></tr></thead>
      <tbody>${banks.map(b=>`<tr><td><b>${b.name}</b></td><td><span class="badge badge-info">${b.type||'بنك'}</span></td><td class="text-success"><b>${fmt(b.balance)}</b></td>
        <td><button class="btn btn-sm btn-outline" onclick="showBankTxModal(${b.id})">➕ حركة</button>
        <button class="btn btn-sm btn-danger" onclick="deleteBank(${b.id})">🗑️</button></td></tr>`).join('')}
      </tbody>
    </table></div></div>`;
  } else {
    c.innerHTML=`
    <div class="search-bar mb-16 no-print flex-wrap">
      <input type="date" id="tr-from" onchange="filterTreasury()">
      <input type="date" id="tr-to"   onchange="filterTreasury()">
      <select id="tr-type" onchange="filterTreasury()">
        <option value="">الكل</option><option value="in">إيرادات</option><option value="out">مصروفات</option>
      </select>
      <button class="btn btn-outline" onclick="printTreasury()">🖨️ طباعة</button>
    </div>
    <div class="card"><div class="table-wrap"><table>
      <thead><tr><th>التاريخ</th><th>البيان</th><th class="hide-md">الفئة</th><th>وارد</th><th>صادر</th><th>الرصيد</th></tr></thead>
      <tbody id="tr-body"></tbody>
    </table></div></div>`;
    renderTreasuryTable(await dbGetAll('treasury'));
  }
}

async function filterTreasury(){
  let tr=await dbGetAll('treasury');
  const f=document.getElementById('tr-from')?.value||'', t=document.getElementById('tr-to')?.value||'', type=document.getElementById('tr-type')?.value||'';
  if(f) tr=tr.filter(x=>x.date>=f); if(t) tr=tr.filter(x=>x.date<=t); if(type) tr=tr.filter(x=>x.type===type);
  renderTreasuryTable(tr);
}

function renderTreasuryTable(tr){
  const tb=document.getElementById('tr-body'); if(!tb) return;
  let balance=0;
  const sorted=tr.slice().sort((a,b)=>a.date.localeCompare(b.date));
  tb.innerHTML=sorted.map(t=>{ if(t.type==='in') balance+=t.amount; else balance-=t.amount;
    return `<tr><td data-label="التاريخ">${t.date}</td><td data-label="البيان">${t.description}</td><td data-label="الفئة" class="hide-md"><span class="badge badge-gray">${t.category||'-'}</span></td><td data-label="وارد" class="text-success">${t.type==='in'?fmt(t.amount):'-'}</td><td data-label="صادر" class="text-danger">${t.type==='out'?fmt(t.amount):'-'}</td><td data-label="الرصيد" class="${balance>=0?'text-success':'text-danger'}"><b>${fmt(balance)}</b></td></tr>`;
  }).reverse().join('');
}

async function printTreasury(){
  let tr=await dbGetAll('treasury');
  const f=document.getElementById('tr-from')?.value||'', t=document.getElementById('tr-to')?.value||'';
  if(f) tr=tr.filter(x=>x.date>=f); if(t) tr=tr.filter(x=>x.date<=t);
  let balance=0;
  const rows=tr.slice().sort((a,b)=>a.date.localeCompare(b.date)).map((x,i)=>{ if(x.type==='in') balance+=x.amount; else balance-=x.amount; return `<tr><td>${i+1}</td><td>${x.date}</td><td>${x.description}</td><td>${x.category||'-'}</td><td>${x.type==='in'?fmt(x.amount):'-'}</td><td>${x.type==='out'?fmt(x.amount):'-'}</td><td>${fmt(balance)}</td></tr>`; }).join('');
  const html=`<table><thead><tr><th>#</th><th>التاريخ</th><th>البيان</th><th>الفئة</th><th>وارد</th><th>صادر</th><th>الرصيد</th></tr></thead><tbody>${rows}</tbody></table>`;
  await printSection('الخزينة - كل الحركات', html, f&&t?`من ${f} إلى ${t}`:'');
}

async function showBankModal(){
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>🏦 إضافة بنك/صندوق</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>الاسم</label><input type="text" id="bk-name" placeholder="مثال: بنك QNB"></div>
        <div class="form-group"><label>النوع</label>
          <select id="bk-type"><option value="بنك">بنك</option><option value="كاش في المكتب">كاش في المكتب</option><option value="صندوق">صندوق</option></select>
        </div>
        <div class="form-group"><label>الرصيد الافتتاحي (ج.م)</label><input type="number" id="bk-bal" value="0" min="0"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveBank()">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveBank(){
  const name=document.getElementById('bk-name').value.trim(); if(!name){ alert('يرجى إدخال الاسم'); return; }
  await dbPut('banks',{ name, type:document.getElementById('bk-type').value, balance:parseFloat(document.getElementById('bk-bal').value)||0 });
  closeModal(); showTrTab('banks');
}

async function showBankTxModal(bankId){
  const b=await dbGet('banks',bankId); if(!b) return;
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>💳 ${b.name} - رصيد: ${fmt(b.balance)} ج.م</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>النوع</label>
          <select id="bd-type"><option value="deposit">إيداع (+)</option><option value="withdraw">سحب (-)</option></select>
        </div>
        <div class="form-group"><label>المبلغ (ج.م)</label><input type="number" id="bd-amount" min="0"></div>
        <div class="form-group"><label>التاريخ</label><input type="date" id="bd-date" value="${today()}"></div>
        <div class="form-group"><label>البيان</label><input type="text" id="bd-desc"></div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveBankTx(${bankId})">💾 تأكيد</button>
    </div>
  </div>`);
}

async function saveBankTx(bankId){
  const amount=parseFloat(document.getElementById('bd-amount').value)||0; if(!amount) return;
  const t=document.getElementById('bd-type').value;
  const b=await dbGet('banks',bankId);
  await dbUpdate('banks',bankId,{ balance: t==='deposit'?b.balance+amount:b.balance-amount });
  const desc=document.getElementById('bd-desc').value||`${t==='deposit'?'إيداع':'سحب'} - ${b.name}`;
  await dbPut('treasury',{ date:document.getElementById('bd-date').value, type:t==='deposit'?'in':'out', category:b.name, description:desc, amount, ref:bankId });
  closeModal(); showTrTab('banks');
}
async function deleteBank(id){ if(!confirm('حذف؟')) return; await dbDelete('banks',id); showTrTab('banks'); }

// =========================================================
// ===== SETTINGS =====
// =========================================================
async function renderSettings(){
  document.getElementById('content').innerHTML=`
  <div class="tabs">
    <div class="tab active" id="set-tab-company" onclick="switchSetTab('company')">بيانات الشركة</div>
    <div class="tab"        id="set-tab-users"   onclick="switchSetTab('users')">المستخدمين</div>
    <div class="tab"        id="set-tab-backup"  onclick="switchSetTab('backup')">النسخ الاحتياطي</div>
  </div>
  <div id="settings-content"></div>`;
  showSetTab('company');
}

function switchSetTab(t){ ['company','users','backup'].forEach(x=>document.getElementById('set-tab-'+x)?.classList.toggle('active',x===t)); showSetTab(t); }

async function showSetTab(t){
  const c=document.getElementById('settings-content'); if(!c) return;
  const s=await dbGetSettings();
  if(t==='company'){
    c.innerHTML=`<div class="card">
      <div class="card-title">🏢 بيانات الشركة</div>
      <div class="form-grid">
        <div class="form-group"><label>اسم الشركة</label><input type="text" id="s-name" value="${s.companyName||''}"></div>
        <div class="form-group"><label>العنوان</label><input type="text" id="s-addr" value="${s.address||''}"></div>
        <div class="form-group"><label>الهاتف</label><input type="text" id="s-phone" value="${s.phone||''}"></div>
        <div class="form-group"><label>البريد الإلكتروني</label><input type="email" id="s-email" value="${s.email||''}"></div>
        <div class="form-group"><label>السجل التجاري</label><input type="text" id="s-treg" value="${s.tradeReg||''}"></div>
        <div class="form-group"><label>البطاقة الضريبية</label><input type="text" id="s-tax" value="${s.taxCard||''}"></div>
      </div>
      <div class="form-group mt-12">
        <label>شعار الشركة</label>
        <input type="file" id="s-logo" accept="image/*" onchange="previewLogo(this)">
        <div id="logo-preview" style="margin-top:8px">${s.logo?`<img src="${s.logo}" style="width:80px;height:80px;object-fit:cover;border-radius:8px">`:''}</div>
      </div>
      <button class="btn btn-primary mt-16" onclick="saveSettings()">💾 حفظ البيانات</button>
    </div>`;
  } else if(t==='users'){
    const users=await dbGetAll('users');
    c.innerHTML=`
    <div class="flex justify-between items-center mb-16">
      <h3>المستخدمين: ${users.length}</h3>
      <button class="btn btn-primary" onclick="showUserModal()">➕ مستخدم جديد</button>
    </div>
    <div class="card"><div class="table-wrap"><table>
      <thead><tr><th>#</th><th>الاسم</th><th>اسم المستخدم</th><th>الصلاحية</th><th>إجراءات</th></tr></thead>
      <tbody>${users.map((u,i)=>`<tr><td>${i+1}</td><td>${u.name}</td><td>${u.username}</td>
        <td><span class="badge ${u.role==='admin'?'badge-danger':'badge-info'}">${u.role==='admin'?'مدير':'موظف'}</span></td>
        <td><button class="btn btn-sm btn-outline" onclick="showUserModal(${u.id})">✏️</button>
        ${u.id!==currentUser.id?`<button class="btn btn-sm btn-danger" onclick="deleteUser(${u.id})">🗑️</button>`:''}</td></tr>`).join('')}
      </tbody>
    </table></div></div>`;
  } else {
    c.innerHTML=`<div class="card">
      <div class="card-title">💾 النسخ الاحتياطي والاستعادة</div>
      <div class="flex gap-8 mb-16" style="flex-wrap:wrap">
        <div style="background:#e8f4fd;border:1px solid #bee3f8;border-radius:8px;padding:12px;flex:1;min-width:200px">
          <div style="font-weight:600;margin-bottom:4px">📦 قاعدة البيانات</div>
          <div style="font-size:12px;color:var(--muted)">Supabase PostgreSQL - سحابية مشتركة</div>
          <div style="font-size:12px;color:var(--success);margin-top:4px">✅ البيانات متاحة من أي جهاز</div>
        </div>
      </div>
      <p class="text-muted mb-16" style="font-size:13px">قم بتنزيل نسخة احتياطية أو استعادة بيانات من ملف سابق.</p>
      <div class="flex gap-12 flex-wrap">
        <button class="btn btn-success" onclick="doBackup()">⬇️ تنزيل نسخة احتياطية</button>
        <label class="btn btn-warning" style="cursor:pointer">⬆️ استعادة بيانات<input type="file" accept=".json" style="display:none" onchange="doRestore(this)"></label>
      </div>
      <div class="divider"></div>
      <p class="text-danger" style="font-size:12px">⚠️ تحذير: عملية الاستعادة ستحل محل جميع البيانات الحالية.</p>
    </div>`;
  }
}

function previewLogo(input){
  const file=input.files[0]; if(!file) return;
  const reader=new FileReader();
  reader.onload=e=>{ document.getElementById('logo-preview').innerHTML=`<img src="${e.target.result}" style="width:80px;height:80px;object-fit:cover;border-radius:8px">`; document.getElementById('logo-preview').dataset.logo=e.target.result; };
  reader.readAsDataURL(file);
}

async function saveSettings(){
  const s=await dbGetSettings();
  const logo=document.getElementById('logo-preview')?.dataset?.logo||s.logo||null;
  const ns={ ...s, companyName:document.getElementById('s-name').value, address:document.getElementById('s-addr').value, phone:document.getElementById('s-phone').value, email:document.getElementById('s-email').value, tradeReg:document.getElementById('s-treg').value, taxCard:document.getElementById('s-tax').value, logo };
  await dbSaveSettings(ns);
  document.getElementById('company-name-display').textContent=ns.companyName;
  if(logo) document.getElementById('logo-display').innerHTML=`<img src="${logo}" style="width:50px;height:50px;border-radius:8px;object-fit:cover">`;
  alert('✅ تم حفظ البيانات');
}

async function showUserModal(id=null){
  const u=id?await dbGet('users',id):{};
  showModal(`
  <div class="modal">
    <div class="modal-header"><h3>${id?'تعديل':'إضافة'} مستخدم</h3><button class="close-btn" onclick="closeModal()">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="form-group"><label>الاسم الكامل</label><input type="text" id="u-name" value="${u.name||''}"></div>
        <div class="form-group"><label>اسم المستخدم</label><input type="text" id="u-username" value="${u.username||''}"></div>
        <div class="form-group"><label>كلمة المرور</label><input type="password" id="u-pass" placeholder="${id?'اتركها فارغة للإبقاء':'أدخل كلمة المرور'}"></div>
        <div class="form-group"><label>الصلاحية</label>
          <select id="u-role"><option value="admin" ${u.role==='admin'?'selected':''}>مدير</option><option value="user" ${u.role==='user'?'selected':''}>موظف</option></select>
        </div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal()">إلغاء</button>
      <button class="btn btn-primary" onclick="saveUser(${id||'null'})">💾 حفظ</button>
    </div>
  </div>`);
}

async function saveUser(id){
  const name=document.getElementById('u-name').value.trim(), username=document.getElementById('u-username').value.trim(), pass=document.getElementById('u-pass').value, role=document.getElementById('u-role').value;
  if(!name||!username){ alert('يرجى إدخال الاسم واسم المستخدم'); return; }
  if(id){
    const existing=await dbGet('users',id);
    await dbUpdate('users',id,{ name, username, role, password:pass||existing.password });
  } else {
    if(!pass){ alert('يرجى إدخال كلمة المرور'); return; }
    await dbPut('users',{ name, username, password:pass, role });
  }
  closeModal(); switchSetTab('users');
}
async function deleteUser(id){ if(!confirm('حذف؟')) return; await dbDelete('users',id); switchSetTab('users'); }

// =========================================================
// ===== SIDEBAR TOGGLE =====
// =========================================================
function toggleSidebar(){ document.getElementById('sidebar').classList.toggle('open'); document.getElementById('sidebar-overlay').classList.toggle('open'); }
function closeSidebar(){ document.getElementById('sidebar').classList.remove('open'); document.getElementById('sidebar-overlay').classList.remove('open'); }

// =========================================================
// ===== BOOTSTRAP =====
// =========================================================
async function boot(){
  try {
    await initData();
    document.getElementById('topbar-date').textContent = new Date().toLocaleDateString('ar-EG',{weekday:'long',year:'numeric',month:'long',day:'numeric'});
    // Pre-load settings for login screen display
    const s = await dbGetSettings();
    if(s.companyName) document.getElementById('company-name-display').textContent = s.companyName;
  } catch(err){
    console.error('Boot error:', err);
    alert('خطأ في تهيئة قاعدة البيانات: ' + err.message);
  }
}
boot();
</script>
</body></html>

