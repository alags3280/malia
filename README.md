<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Malia — Personal Finance</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet"/>
<style>
:root {
  --bg: #f5f2ec;
  --bg2: #edeae2;
  --card: #ffffff;
  --ink: #1a1814;
  --ink2: #6b6760;
  --ink3: #b0ada8;
  --gold: #c8963c;
  --gold-light: #f5e6cc;
  --green: #2d6a4f;
  --green-light: #d8ede5;
  --red: #b83232;
  --red-light: #f5dada;
  --blue: #2c4a7c;
  --blue-light: #dce5f5;
  --border: #e0ddd6;
  --shadow: 0 2px 16px rgba(26,24,20,.07);
  --shadow-lg: 0 8px 40px rgba(26,24,20,.12);
  --radius: 16px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
html{font-size:16px;}
body{background:var(--bg);color:var(--ink);font-family:'Syne',sans-serif;min-height:100vh;padding-bottom:80px;}
::-webkit-scrollbar{width:4px;height:4px;}
::-webkit-scrollbar-track{background:transparent;}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:4px;}

/* NAV */
.nav{position:fixed;bottom:0;left:0;right:0;background:var(–card);border-top:1px solid var(–border);display:flex;justify-content:space-around;align-items:center;padding:8px 0 14px;z-index:100;box-shadow:0 -4px 20px rgba(0,0,0,.06);}
.nav-btn{display:flex;flex-direction:column;align-items:center;gap:3px;background:none;border:none;cursor:pointer;color:var(–ink3);font-family:‘Syne’,sans-serif;font-size:9px;letter-spacing:.02em;padding:2px 6px;border-radius:12px;transition:all .2s;}
.nav-btn.active{color:var(–gold);}
.nav-btn svg{width:20px;height:20px;}
.nav-icon{width:36px;height:36px;background:var(–gold);border-radius:50%;display:flex;align-items:center;justify-content:center;box-shadow:0 4px 12px rgba(200,150,60,.35);}
.nav-icon svg{width:18px;height:18px;color:#fff;}

/* PAGES */
.page{display:none;padding:0;animation:fadeIn .25s ease;}
.page.active{display:block;}
@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}

/* HEADER */
.page-header{padding:52px 20px 20px;background:linear-gradient(160deg,#1a1814 0%,#2e2a22 100%);position:relative;overflow:hidden;}
.page-header::before{content:’’;position:absolute;top:-40px;right:-40px;width:200px;height:200px;background:radial-gradient(circle,rgba(200,150,60,.18) 0%,transparent 70%);pointer-events:none;}
.page-header::after{content:’’;position:absolute;bottom:-20px;left:20px;width:120px;height:120px;background:radial-gradient(circle,rgba(200,150,60,.1) 0%,transparent 70%);pointer-events:none;}
.greeting{font-size:12px;color:rgba(255,255,255,.45);letter-spacing:.1em;margin-bottom:4px;}
.page-title{font-family:‘Instrument Serif’,serif;font-size:28px;color:#fff;font-style:italic;font-weight:400;}
.page-title span{color:var(–gold);font-style:normal;}
.header-badge{display:inline-block;background:rgba(200,150,60,.15);border:1px solid rgba(200,150,60,.3);color:var(–gold);font-size:11px;padding:4px 12px;border-radius:20px;margin-top:10px;letter-spacing:.06em;}

/* NET WORTH STRIP */
.networth-strip{background:linear-gradient(135deg,var(–gold) 0%,#e8b05a 100%);margin:0 20px;margin-top:-1px;border-radius:0 0 var(–radius) var(–radius);padding:18px 20px;display:flex;justify-content:space-between;align-items:center;box-shadow:0 8px 24px rgba(200,150,60,.3);}
.nw-label{font-size:11px;color:rgba(255,255,255,.7);letter-spacing:.08em;}
.nw-value{font-family:‘Instrument Serif’,serif;font-size:26px;color:#fff;font-weight:400;}
.nw-sub{font-size:11px;color:rgba(255,255,255,.75);margin-top:2px;}
.nw-change{text-align:right;}

/* CARDS */
.section{padding:20px 20px 0;}
.section-title{font-size:11px;color:var(–ink2);letter-spacing:.1em;margin-bottom:14px;display:flex;justify-content:space-between;align-items:center;}
.section-title a{color:var(–gold);font-size:11px;cursor:pointer;text-decoration:none;}
.card{background:var(–card);border-radius:var(–radius);border:1px solid var(–border);box-shadow:var(–shadow);overflow:hidden;}
.card+.card{margin-top:12px;}

/* SUMMARY GRID */
.summary-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;}
.sum-card{background:var(–card);border:1px solid var(–border);border-radius:var(–radius);padding:18px;position:relative;overflow:hidden;}
.sum-card::before{content:’’;position:absolute;top:0;left:0;right:0;height:3px;}
.sum-card.income::before{background:var(–green);}
.sum-card.expense::before{background:var(–red);}
.sum-icon{width:36px;height:36px;border-radius:10px;display:flex;align-items:center;justify-content:center;margin-bottom:12px;font-size:16px;}
.sum-card.income .sum-icon{background:var(–green-light);}
.sum-card.expense .sum-icon{background:var(–red-light);}
.sum-label{font-size:10px;letter-spacing:.08em;color:var(–ink2);}
.sum-value{font-family:‘Instrument Serif’,serif;font-size:22px;margin-top:2px;}
.sum-card.income .sum-value{color:var(–green);}
.sum-card.expense .sum-value{color:var(–red);}
.sum-count{font-size:10px;color:var(–ink3);margin-top:4px;}

/* TRANSACTIONS */
.txn-item{display:flex;align-items:center;gap:14px;padding:14px 18px;border-bottom:1px solid var(–border);transition:background .15s;}
.txn-item:last-child{border-bottom:none;}
.txn-item:hover{background:var(–bg);}
.txn-icon{width:40px;height:40px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0;}
.txn-body{flex:1;min-width:0;}
.txn-name{font-size:14px;font-weight:500;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.txn-meta{font-size:11px;color:var(–ink3);margin-top:2px;}
.txn-amount{font-family:‘Instrument Serif’,serif;font-size:17px;text-align:right;white-space:nowrap;}
.txn-amount.income{color:var(–green);}
.txn-amount.expense{color:var(–red);}
.txn-del{background:none;border:none;color:var(–ink3);font-size:14px;cursor:pointer;padding:4px;margin-left:6px;transition:color .2s;flex-shrink:0;}
.txn-del:hover{color:var(–red);}

/* PILL */
.pill{display:inline-block;padding:3px 10px;border-radius:20px;font-size:10px;letter-spacing:.05em;font-weight:600;}
.pill-green{background:var(–green-light);color:var(–green);}
.pill-red{background:var(–red-light);color:var(–red);}
.pill-gold{background:var(–gold-light);color:var(–gold);}
.pill-blue{background:var(–blue-light);color:var(–blue);}

/* SAVINGS GOALS */
.goal-card{padding:18px;border-bottom:1px solid var(–border);}
.goal-card:last-child{border-bottom:none;}
.goal-header{display:flex;align-items:flex-start;gap:12px;margin-bottom:12px;}
.goal-emoji{font-size:24px;width:44px;height:44px;background:var(–bg2);border-radius:12px;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.goal-info{flex:1;}
.goal-name{font-size:15px;font-weight:600;}
.goal-target{font-size:11px;color:var(–ink2);margin-top:2px;}
.goal-saved{font-family:‘Instrument Serif’,serif;font-size:20px;color:var(–gold);margin-top:2px;}
.goal-actions{display:flex;gap:6px;margin-top:2px;}
.goal-add-btn{background:var(–gold-light);border:none;color:var(–gold);font-size:11px;font-family:‘Syne’,sans-serif;padding:5px 12px;border-radius:8px;cursor:pointer;font-weight:600;transition:all .2s;}
.goal-add-btn:hover{background:var(–gold);color:#fff;}
.goal-del-btn{background:var(–red-light);border:none;color:var(–red);font-size:11px;font-family:‘Syne’,sans-serif;padding:5px 10px;border-radius:8px;cursor:pointer;transition:all .2s;}
.goal-del-btn:hover{background:var(–red);color:#fff;}
.progress-bar{height:8px;background:var(–bg2);border-radius:4px;overflow:hidden;}
.progress-fill{height:100%;border-radius:4px;background:linear-gradient(90deg,var(–gold),#e8b05a);transition:width .5s cubic-bezier(.4,0,.2,1);}
.progress-fill.complete{background:linear-gradient(90deg,var(–green),#5aa87a);}
.goal-pct{font-size:11px;color:var(–ink3);margin-top:6px;}

/* BILLS */
.bill-item{display:flex;align-items:center;gap:14px;padding:14px 18px;border-bottom:1px solid var(–border);transition:background .15s;}
.bill-item:last-child{border-bottom:none;}
.bill-item:hover{background:var(–bg);}
.bill-icon{width:40px;height:40px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0;background:var(–bg2);}
.bill-body{flex:1;min-width:0;}
.bill-name{font-size:14px;font-weight:500;}
.bill-date{font-size:11px;color:var(–ink3);margin-top:2px;}
.bill-amount{font-family:‘Instrument Serif’,serif;font-size:17px;color:var(–ink);text-align:right;white-space:nowrap;}
.bill-status{font-size:10px;margin-top:2px;text-align:right;}
.bill-overdue{color:var(–red);}
.bill-soon{color:var(–gold);}
.bill-ok{color:var(–green);}
.bill-del{background:none;border:none;color:var(–ink3);font-size:14px;cursor:pointer;padding:4px;margin-left:6px;transition:color .2s;}
.bill-del:hover{color:var(–red);}

/* MODAL */
.overlay{position:fixed;inset:0;background:rgba(26,24,20,.55);backdrop-filter:blur(4px);z-index:200;display:none;align-items:flex-end;justify-content:center;}
.overlay.open{display:flex;}
.modal{background:var(–card);border-radius:24px 24px 0 0;width:100%;max-width:480px;padding:28px 24px 40px;animation:slideUp .3s cubic-bezier(.4,0,.2,1);}
@keyframes slideUp{from{transform:translateY(100%)}to{transform:none}}
.modal-handle{width:40px;height:4px;background:var(–border);border-radius:2px;margin:0 auto 24px;}
.modal-title{font-family:‘Instrument Serif’,serif;font-size:22px;font-style:italic;margin-bottom:20px;}
.form-group{margin-bottom:14px;}
.form-label{font-size:11px;color:var(–ink2);letter-spacing:.08em;margin-bottom:6px;display:block;}
.form-input{width:100%;background:var(–bg);border:1px solid var(–border);color:var(–ink);font-family:‘Syne’,sans-serif;font-size:14px;padding:12px 14px;border-radius:12px;outline:none;transition:border-color .2s;}
.form-input:focus{border-color:var(–gold);}
.form-input::placeholder{color:var(–ink3);}
select.form-input option{background:#fff;}
.type-toggle{display:flex;background:var(–bg2);border-radius:12px;padding:4px;gap:4px;margin-bottom:14px;}
.type-btn{flex:1;border:none;padding:10px;border-radius:9px;font-size:12px;letter-spacing:.05em;font-family:‘Syne’,sans-serif;cursor:pointer;font-weight:600;transition:all .2s;}
.type-btn.expense-on{background:var(–red-light);color:var(–red);}
.type-btn.income-on{background:var(–green-light);color:var(–green);}
.type-btn.off{background:none;color:var(–ink3);}
.submit-btn{width:100%;background:linear-gradient(135deg,var(–gold),#e8b05a);border:none;color:#fff;font-family:‘Syne’,sans-serif;font-size:14px;font-weight:700;padding:15px;border-radius:14px;cursor:pointer;letter-spacing:.06em;margin-top:4px;box-shadow:0 4px 16px rgba(200,150,60,.35);transition:opacity .2s;}
.submit-btn:hover{opacity:.9;}
.cancel-btn{width:100%;background:none;border:none;color:var(–ink3);font-family:‘Syne’,sans-serif;font-size:13px;padding:12px;cursor:pointer;margin-top:4px;transition:color .2s;}
.cancel-btn:hover{color:var(–ink);}

/* FAB */
.fab{position:fixed;bottom:80px;right:20px;width:52px;height:52px;background:linear-gradient(135deg,var(–gold),#e8b05a);border:none;border-radius:50%;display:flex;align-items:center;justify-content:center;cursor:pointer;box-shadow:0 4px 20px rgba(200,150,60,.4);z-index:99;transition:transform .2s;}
.fab:hover{transform:scale(1.08);}
.fab svg{width:24px;height:24px;color:#fff;}

/* EMPTY */
.empty{text-align:center;padding:40px 20px;color:var(–ink3);}
.empty-icon{font-size:40px;margin-bottom:12px;}
.empty-text{font-size:13px;}

/* SIMPLE HEADER for other pages */
.simple-header{padding:52px 20px 20px;background:linear-gradient(160deg,#1a1814 0%,#2e2a22 100%);}
.simple-header .page-title{font-family:‘Instrument Serif’,serif;font-size:26px;color:#fff;font-style:italic;}
.simple-header .page-title span{color:var(–gold);font-style:normal;}

/* BILLS DUE BANNER */
.due-banner{margin:20px 20px 0;background:linear-gradient(135deg,#7c2c2c,#b83232);border-radius:var(–radius);padding:16px 18px;display:flex;align-items:center;gap:14px;}
.due-banner-icon{font-size:24px;}
.due-banner-text{flex:1;}
.due-banner-title{font-size:13px;color:#fff;font-weight:600;}
.due-banner-sub{font-size:11px;color:rgba(255,255,255,.65);margin-top:2px;}

/* MONTH SELECTOR */
.month-row{display:flex;align-items:center;gap:8px;padding:16px 20px 0;}
.month-btn{background:none;border:none;color:var(–ink2);font-size:18px;cursor:pointer;padding:4px 8px;border-radius:8px;transition:color .2s;}
.month-btn:hover{color:var(–gold);}
.month-label{flex:1;text-align:center;font-size:14px;font-weight:600;letter-spacing:.04em;}

/* CATEGORY MANAGER */
.add-cat-btn{width:100%;background:var(–card);border:1.5px dashed var(–border);color:var(–gold);font-family:‘Syne’,sans-serif;font-size:13px;font-weight:600;padding:13px;border-radius:var(–radius);cursor:pointer;transition:all .2s;letter-spacing:.04em;}
.add-cat-btn:hover{background:var(–gold-light);border-color:var(–gold);}
.cat-item{display:flex;align-items:center;gap:12px;padding:13px 18px;border-bottom:1px solid var(–border);transition:background .15s;}
.cat-item:last-child{border-bottom:none;}
.cat-item:hover{background:var(–bg);}
.cat-emoji{width:36px;height:36px;background:var(–bg2);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0;}
.cat-name-text{flex:1;font-size:14px;font-weight:500;}
.cat-default-tag{font-size:10px;color:var(–ink3);background:var(–bg2);padding:2px 8px;border-radius:10px;margin-right:4px;}
.cat-edit-btn{background:var(–gold-light);border:none;color:var(–gold);font-size:11px;font-family:‘Syne’,sans-serif;padding:5px 10px;border-radius:8px;cursor:pointer;font-weight:600;transition:all .2s;margin-right:4px;}
.cat-edit-btn:hover{background:var(–gold);color:#fff;}
.cat-del-btn{background:var(–red-light);border:none;color:var(–red);font-size:11px;font-family:‘Syne’,sans-serif;padding:5px 8px;border-radius:8px;cursor:pointer;transition:all .2s;}
.cat-del-btn:hover{background:var(–red);color:#fff;}
.cat-chart{padding:18px;}
.cat-row-chart{margin-bottom:10px;}
.cat-row-chart:last-child{margin-bottom:0;}
.cat-row-top{display:flex;justify-content:space-between;font-size:12px;margin-bottom:5px;}
.cat-name{color:var(–ink2);}
.bar-bg{height:8px;background:var(–bg2);border-radius:4px;overflow:hidden;}
.bar-fill{height:100%;border-radius:4px;background:linear-gradient(90deg,var(–red),#d97070);transition:width .5s;}

/* BILL MARK PAID */
.mark-paid-btn{background:var(–green-light);border:none;color:var(–green);font-size:10px;font-family:‘Syne’,sans-serif;padding:4px 10px;border-radius:8px;cursor:pointer;font-weight:600;margin-top:4px;transition:all .2s;}
.mark-paid-btn:hover{background:var(–green);color:#fff;}
.paid-badge{font-size:10px;color:var(–green);font-weight:600;margin-top:4px;}

@media(max-width:360px){.nw-value{font-size:22px;}.sum-value{font-size:18px;}}
</style>

</head>
<body>

<!-- PAGES -->

<!-- HOME -->

<div id="page-home" class="page active">
  <div class="page-header">
    <div class="greeting">WELCOME BACK</div>
    <div class="page-title">Your <span>Malia</span></div>
    <div class="header-badge" id="monthBadge"></div>
  </div>
  <div class="networth-strip">
    <div>
      <div class="nw-label">NET BALANCE</div>
      <div class="nw-value" id="netBalance">AED 0</div>
    </div>
    <div class="nw-change" id="nwChange"></div>
  </div>

  <div class="section" style="margin-top:20px;">
    <div class="summary-grid">
      <div class="sum-card income">
        <div class="sum-icon">💰</div>
        <div class="sum-label">INCOME</div>
        <div class="sum-value" id="homeTotalIncome">AED 0</div>
        <div class="sum-count" id="homeIncomeCount">0 transactions</div>
      </div>
      <div class="sum-card expense">
        <div class="sum-icon">📤</div>
        <div class="sum-label">EXPENSES</div>
        <div class="sum-value" id="homeTotalExpense">AED 0</div>
        <div class="sum-count" id="homeExpenseCount">0 transactions</div>
      </div>
    </div>
  </div>

  <div class="section" style="margin-top:20px;">
    <div class="section-title">RECENT TRANSACTIONS <a onclick="showPage('transactions')">See all</a></div>
    <div class="card" id="recentTxns"></div>
  </div>

  <div class="section" style="margin-top:20px;">
    <div class="section-title">SAVINGS GOALS <a onclick="showPage('savings')">See all</a></div>
    <div class="card" id="homeGoals"></div>
  </div>

  <div id="upcomingBillsBanner"></div>
</div>

<!-- TRANSACTIONS -->

<div id="page-transactions" class="page">
  <div class="simple-header">
    <div class="page-title">Trans<span>actions</span></div>
  </div>
  <div class="month-row">
    <button class="month-btn" onclick="changeMonth(-1)">‹</button>
    <div class="month-label" id="txnMonthLabel"></div>
    <button class="month-btn" onclick="changeMonth(1)">›</button>
  </div>
  <div class="section" style="margin-top:16px;">
    <div class="summary-grid">
      <div class="sum-card income">
        <div class="sum-label">INCOME</div>
        <div class="sum-value" id="txnIncome">AED 0</div>
      </div>
      <div class="sum-card expense">
        <div class="sum-label">EXPENSES</div>
        <div class="sum-value" id="txnExpense">AED 0</div>
      </div>
    </div>
  </div>
  <div class="section" style="margin-top:16px;">
    <div class="section-title">CATEGORY BREAKDOWN</div>
    <div class="card"><div class="cat-chart" id="catChart"></div></div>
  </div>
  <div class="section" style="margin-top:16px;">
    <div class="section-title">ALL TRANSACTIONS</div>
    <div class="card" id="allTxns"></div>
  </div>
</div>

<!-- SAVINGS -->

<div id="page-savings" class="page">
  <div class="simple-header">
    <div class="page-title">Savings <span>Goals</span></div>
  </div>
  <div class="section" style="margin-top:20px;">
    <div class="section-title">YOUR GOALS</div>
    <div class="card" id="goalsList"></div>
  </div>
</div>

<!-- REPORTS -->

<div id="page-reports" class="page">
  <div class="simple-header">
    <div class="page-title">Re<span>ports</span></div>
  </div>
  <div class="month-row">
    <button class="month-btn" onclick="changeReportMonth(-1)">‹</button>
    <div class="month-label" id="reportMonthLabel"></div>
    <button class="month-btn" onclick="changeReportMonth(1)">›</button>
  </div>

  <!-- 1. Income vs Expense Bar Chart -->

  <div class="section" style="margin-top:16px;">
    <div class="section-title">MONTHLY INCOME VS EXPENSE</div>
    <div class="card" style="padding:20px;">
      <canvas id="barChart" height="200"></canvas>
      <div id="barLegend" style="display:flex;justify-content:center;gap:20px;margin-top:14px;font-size:11px;"></div>
    </div>
  </div>

  <!-- 2. Spending by Category Donut -->

  <div class="section" style="margin-top:16px;">
    <div class="section-title">SPENDING BY CATEGORY</div>
    <div class="card" style="padding:20px;">
      <div style="display:flex;align-items:center;gap:20px;flex-wrap:wrap;">
        <canvas id="donutChart" width="160" height="160" style="flex-shrink:0;"></canvas>
        <div id="donutLegend" style="flex:1;min-width:120px;font-size:12px;"></div>
      </div>
    </div>
  </div>

  <!-- 3. Savings Goals Progress -->

  <div class="section" style="margin-top:16px;">
    <div class="section-title">SAVINGS GOALS PROGRESS</div>
    <div class="card" id="reportGoals"></div>
  </div>

  <!-- 4. Bills Summary -->

  <div class="section" style="margin-top:16px;">
    <div class="section-title">BILLS SUMMARY</div>
    <div class="card" id="reportBills"></div>
  </div>
</div>

<!-- BILLS -->

<div id="page-bills" class="page">
  <div class="simple-header">
    <div class="page-title">Bill <span>Reminders</span></div>
  </div>
  <div class="section" style="margin-top:20px;">
    <div class="section-title">UPCOMING BILLS</div>
    <div class="card" id="billsList"></div>
  </div>
</div>

<!-- SETTINGS -->

<div id="page-settings" class="page">
  <div class="simple-header">
    <div class="page-title">Set<span>tings</span></div>
  </div>

  <!-- UPDATE APP -->

  <div class="section" style="margin-top:20px;">
    <div class="section-title">APP VERSION</div>
    <div class="card" style="padding:18px;">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
        <div style="width:44px;height:44px;background:var(--gold-light);border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:22px;flex-shrink:0;">⚡</div>
        <div>
          <div style="font-size:14px;font-weight:600;">Malia Finance</div>
          <div style="font-size:11px;color:var(--ink3);margin-top:2px;" id="appVersionLabel">Tap below to check for updates</div>
        </div>
      </div>
      <div style="font-size:12px;color:var(--ink2);margin-bottom:14px;line-height:1.6;">
        Tap <strong>Update App</strong> to get the latest features. Your data (transactions, goals, bills) is always kept safe — it lives in your browser storage, not in the app code.
      </div>
      <button onclick="updateApp()" id="updateBtn" style="width:100%;background:linear-gradient(135deg,var(--gold),#e8b05a);border:none;color:#fff;font-family:'Syne',sans-serif;font-size:13px;font-weight:700;padding:14px;border-radius:12px;cursor:pointer;letter-spacing:.06em;box-shadow:0 4px 16px rgba(200,150,60,.3);transition:opacity .2s;">
        ⚡ UPDATE APP
      </button>
      <div id="updateStatus" style="margin-top:10px;font-size:12px;text-align:center;color:var(--ink3);display:none;"></div>
    </div>
  </div>

  <div class="section" style="margin-top:20px;">
    <div class="section-title">EXPENSE CATEGORIES</div>
    <div class="card" id="expCatList"></div>
    <button class="add-cat-btn" onclick="openCatModal('expense')" style="margin-top:10px;">+ Add Expense Category</button>
  </div>
  <div class="section" style="margin-top:20px;">
    <div class="section-title">INCOME CATEGORIES</div>
    <div class="card" id="incCatList"></div>
    <button class="add-cat-btn" onclick="openCatModal('income')" style="margin-top:10px;">+ Add Income Category</button>
  </div>
  <div class="section" style="margin-top:20px;">
    <div class="section-title">DANGER ZONE</div>
    <div class="card" style="padding:16px 18px;">
      <div style="font-size:13px;color:var(--ink2);margin-bottom:12px;">Reset all categories back to defaults. Your transactions will not be deleted.</div>
      <button onclick="resetCategories()" style="background:var(--red-light);border:none;color:var(--red);font-family:'Syne',sans-serif;font-size:13px;font-weight:600;padding:10px 20px;border-radius:10px;cursor:pointer;width:100%;">Reset to Default Categories</button>
    </div>
  </div>
</div>

<!-- CAT MODAL -->

<div class="overlay" id="catOverlay" onclick="closeCatModal(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <div class="modal-title" id="catModalTitle">Add Category</div>
    <div class="form-group">
      <label class="form-label">EMOJI</label>
      <input class="form-input" type="text" id="catEmoji" placeholder="e.g. 🏋️" maxlength="2"/>
    </div>
    <div class="form-group">
      <label class="form-label">CATEGORY NAME</label>
      <input class="form-input" type="text" id="catName" placeholder="e.g. Gym & Fitness"/>
    </div>
    <button class="submit-btn" id="catSubmitBtn" onclick="saveCategory()">ADD CATEGORY</button>
    <button class="cancel-btn" onclick="closeCatModal()">Cancel</button>
  </div>
</div>

<!-- NAV -->

<nav class="nav">
  <button class="nav-btn active" onclick="showPage('home')" id="nav-home">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
    Home
  </button>
  <button class="nav-btn" onclick="showPage('transactions')" id="nav-transactions">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="8" y1="6" x2="21" y2="6"/><line x1="8" y1="12" x2="21" y2="12"/><line x1="8" y1="18" x2="21" y2="18"/><line x1="3" y1="6" x2="3.01" y2="6"/><line x1="3" y1="12" x2="3.01" y2="12"/><line x1="3" y1="18" x2="3.01" y2="18"/></svg>
    Transactions
  </button>
  <button class="nav-btn" onclick="openTxnModal()">
    <div class="nav-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div>
    Add
  </button>
  <button class="nav-btn" onclick="showPage('savings')" id="nav-savings">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2a10 10 0 1 0 10 10A10 10 0 0 0 12 2zm0 18a8 8 0 1 1 8-8 8 8 0 0 1-8 8z"/><path d="M12 6v6l4 2"/></svg>
    Goals
  </button>
  <button class="nav-btn" onclick="showPage('reports')" id="nav-reports">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>
    Reports
  </button>
  <button class="nav-btn" onclick="showPage('bills')" id="nav-bills">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
    Bills
  </button>
  <button class="nav-btn" onclick="showPage('settings')" id="nav-settings">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 2.83-2.83l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>
    Settings
  </button>
</nav>

<!-- ADD TRANSACTION MODAL -->

<div class="overlay" id="txnOverlay" onclick="closeTxnModal(event)">
  <div class="modal" onclick="e=>e.stopPropagation()">
    <div class="modal-handle"></div>
    <div class="modal-title">Add Transaction</div>
    <div class="type-toggle">
      <button id="btnExp" class="type-btn expense-on" onclick="setTxnType('expense')">— Expense</button>
      <button id="btnInc" class="type-btn off" onclick="setTxnType('income')">+ Income</button>
    </div>
    <div class="form-group">
      <label class="form-label">AMOUNT (AED)</label>
      <input class="form-input" type="number" id="txnAmount" placeholder="0.00" min="0" step="0.01"/>
    </div>
    <div class="form-group">
      <label class="form-label">CATEGORY</label>
      <select class="form-input" id="txnCategory"></select>
    </div>
    <div class="form-group">
      <label class="form-label">NOTE</label>
      <input class="form-input" type="text" id="txnNote" placeholder="Optional note"/>
    </div>
    <div class="form-group">
      <label class="form-label">DATE</label>
      <input class="form-input" type="date" id="txnDate"/>
    </div>
    <button class="submit-btn" onclick="saveTxn()">ADD TRANSACTION</button>
    <button class="cancel-btn" onclick="closeTxnModal()">Cancel</button>
  </div>
</div>

<!-- ADD / EDIT GOAL MODAL -->

<div class="overlay" id="goalOverlay" onclick="closeGoalModal(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <div class="modal-title" id="goalModalTitle">New Savings Goal</div>

```
<!-- Emoji Picker -->
<div class="form-group">
  <label class="form-label">PICK AN EMOJI</label>
  <div id="emojiPicker" style="display:flex;flex-wrap:wrap;gap:8px;background:var(--bg2);border-radius:12px;padding:12px;"></div>
  <div style="display:flex;align-items:center;gap:8px;margin-top:8px;">
    <div id="selectedEmojiPreview" style="width:42px;height:42px;background:var(--bg2);border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:24px;flex-shrink:0;border:2px solid var(--gold);">🎯</div>
    <input class="form-input" type="text" id="goalEmoji" placeholder="Or type any emoji..." style="font-size:18px;" oninput="updateEmojiPreview(this.value)"/>
  </div>
</div>

<div class="form-group">
  <label class="form-label">GOAL NAME</label>
  <input class="form-input" type="text" id="goalName" placeholder="e.g. Dubai Holiday"/>
</div>
<div class="form-group">
  <label class="form-label">TARGET AMOUNT (AED)</label>
  <input class="form-input" type="number" id="goalTarget" placeholder="0.00" min="0"/>
</div>
<div class="form-group">
  <label class="form-label">AMOUNT ALREADY SAVED (AED)</label>
  <input class="form-input" type="number" id="goalSaved" placeholder="0.00" min="0"/>
</div>
<div class="form-group">
  <label class="form-label">TARGET DEADLINE</label>
  <input class="form-input" type="month" id="goalDeadline"/>
</div>
<button class="submit-btn" id="goalSubmitBtn" onclick="saveGoal()">CREATE GOAL</button>
<button class="cancel-btn" onclick="closeGoalModal()">Cancel</button>
```

  </div>
</div>

<!-- ADD TO GOAL MODAL -->

<div class="overlay" id="addGoalOverlay" onclick="closeAddGoalModal(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <div class="modal-title" id="addGoalTitle">Add to Goal</div>
    <div class="form-group">
      <label class="form-label">AMOUNT TO ADD (AED)</label>
      <input class="form-input" type="number" id="addGoalAmount" placeholder="0.00" min="0"/>
    </div>
    <button class="submit-btn" onclick="confirmAddToGoal()">ADD SAVINGS</button>
    <button class="cancel-btn" onclick="closeAddGoalModal()">Cancel</button>
  </div>
</div>

<!-- ADD BILL MODAL -->

<div class="overlay" id="billOverlay" onclick="closeBillModal(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <div class="modal-title">Add Bill Reminder</div>
    <div class="form-group">
      <label class="form-label">BILL NAME</label>
      <input class="form-input" type="text" id="billName" placeholder="e.g. Etisalat"/>
    </div>
    <div class="form-group">
      <label class="form-label">EMOJI</label>
      <input class="form-input" type="text" id="billEmoji" placeholder="📱" maxlength="2"/>
    </div>
    <div class="form-group">
      <label class="form-label">AMOUNT (AED)</label>
      <input class="form-input" type="number" id="billAmount" placeholder="0.00" min="0"/>
    </div>
    <div class="form-group">
      <label class="form-label">DUE DATE</label>
      <input class="form-input" type="date" id="billDue"/>
    </div>
    <button class="submit-btn" onclick="saveBill()">ADD BILL</button>
    <button class="cancel-btn" onclick="closeBillModal()">Cancel</button>
  </div>
</div>

<!-- PAGE-SPECIFIC FABS -->

<button class="fab" id="mainFab" onclick="handleFab()">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
</button>

<script>
const STORE = 'malia-v1';
const DEFAULT_EXP_CATS = ['Food & Dining','Transport','Shopping','Housing','Health','Entertainment','Bills','Education','Other'];
const DEFAULT_INC_CATS = ['Salary','Freelance','Investment','Gift','Rental','Other'];

let data = JSON.parse(localStorage.getItem(STORE) || '{"txns":[],"goals":[],"bills":[],"expCats":null,"incCats":null}');
if (!data.expCats) data.expCats = [...DEFAULT_EXP_CATS];
if (!data.incCats) data.incCats = [...DEFAULT_INC_CATS];

// Helpers to get current cats
const getExpCats = () => data.expCats;
const getIncCats = () => data.incCats;
let txnType = 'expense';
let currentPage = 'home';
let viewMonth = new Date().getMonth();
let viewYear = new Date().getFullYear();
let addGoalId = null;

const fmt = n => 'AED ' + n.toLocaleString('en-AE', {minimumFractionDigits:2, maximumFractionDigits:2});
const todayStr = () => new Date().toISOString().split('T')[0];
const save = () => localStorage.setItem(STORE, JSON.stringify(data));

function showPage(p) {
  currentPage = p;
  document.querySelectorAll('.page').forEach(x => x.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(x => x.classList.remove('active'));
  document.getElementById('page-' + p).classList.add('active');
  const nb = document.getElementById('nav-' + p);
  if (nb) nb.classList.add('active');
  // Update FAB icon/visibility
  const fab = document.getElementById('mainFab');
  fab.style.display = ['home','transactions','reports','settings'].includes(p) ? 'none' : 'flex';
  renderPage(p);
}

function handleFab() {
  if (currentPage === 'savings') openGoalModal();
  else if (currentPage === 'bills') openBillModal();
  else openTxnModal();
}

function renderPage(p) {
  if (p === 'home') renderHome();
  if (p === 'transactions') renderTransactions();
  if (p === 'savings') renderSavings();
  if (p === 'reports') renderReports();
  if (p === 'settings') renderSettings();
}

// ── MONTH HELPERS ──
const MONTHS = ['January','February','March','April','May','June','July','August','September','October','November','December'];
function changeMonth(d) {
  viewMonth += d;
  if (viewMonth > 11) { viewMonth = 0; viewYear++; }
  if (viewMonth < 0) { viewMonth = 11; viewYear--; }
  renderTransactions();
}
function txnsForMonth() {
  return data.txns.filter(t => {
    const d = new Date(t.date);
    return d.getMonth() === viewMonth && d.getFullYear() === viewYear;
  });
}
function txnsForCurrentMonth() {
  const now = new Date();
  return data.txns.filter(t => {
    const d = new Date(t.date);
    return d.getMonth() === now.getMonth() && d.getFullYear() === now.getFullYear();
  });
}

// ── HOME ──
function renderHome() {
  const now = new Date();
  document.getElementById('monthBadge').textContent = MONTHS[now.getMonth()].toUpperCase() + ' ' + now.getFullYear();
  const monthly = txnsForCurrentMonth();
  const income = monthly.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0);
  const expense = monthly.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0);
  const bal = income - expense;
  document.getElementById('netBalance').textContent = fmt(bal);
  document.getElementById('homeTotalIncome').textContent = fmt(income);
  document.getElementById('homeTotalExpense').textContent = fmt(expense);
  document.getElementById('homeIncomeCount').textContent = monthly.filter(t=>t.type==='income').length + ' transactions';
  document.getElementById('homeExpenseCount').textContent = monthly.filter(t=>t.type==='expense').length + ' transactions';

  const nwEl = document.getElementById('nwChange');
  nwEl.innerHTML = `<div class="nw-label">THIS MONTH</div><div style="font-size:18px;color:${bal>=0?'#fff':'rgba(255,255,255,.7)'};font-family:'Instrument Serif',serif;">${bal>=0?'+':''}${fmt(bal)}</div>`;

  // Recent txns (last 5)
  const recent = [...data.txns].sort((a,b)=>new Date(b.date)-new Date(a.date)).slice(0,5);
  const rEl = document.getElementById('recentTxns');
  rEl.innerHTML = recent.length ? recent.map(t=>txnHTML(t)).join('') : '<div class="empty"><div class="empty-icon">📋</div><div class="empty-text">No transactions yet</div></div>';

  // Goals preview
  const gEl = document.getElementById('homeGoals');
  gEl.innerHTML = data.goals.length ? data.goals.slice(0,3).map(g => goalMiniHTML(g)).join('') : '<div class="empty"><div class="empty-icon">🎯</div><div class="empty-text">No savings goals yet</div></div>';

  // Upcoming bills banner
  const today = new Date(); today.setHours(0,0,0,0);
  const overdue = data.bills.filter(b => !b.paid && new Date(b.due) < today);
  const soon = data.bills.filter(b => {
    if(b.paid) return false;
    const diff = (new Date(b.due) - today) / 86400000;
    return diff >= 0 && diff <= 7;
  });
  const bannerEl = document.getElementById('upcomingBillsBanner');
  if (overdue.length > 0) {
    bannerEl.innerHTML = `<div class="due-banner"><div class="due-banner-icon">⚠️</div><div class="due-banner-text"><div class="due-banner-title">${overdue.length} bill${overdue.length>1?'s':''} overdue!</div><div class="due-banner-sub">Tap Bills to review</div></div></div>`;
  } else if (soon.length > 0) {
    bannerEl.innerHTML = `<div class="due-banner" style="background:linear-gradient(135deg,#7c5c1a,#c8963c)"><div class="due-banner-icon">🔔</div><div class="due-banner-text"><div class="due-banner-title">${soon.length} bill${soon.length>1?'s':''} due soon</div><div class="due-banner-sub">Within the next 7 days</div></div></div>`;
  } else bannerEl.innerHTML = '';
}

function txnHTML(t) {
  const icons = {'Food & Dining':'🍽️','Transport':'🚗','Shopping':'🛍️','Housing':'🏠','Health':'💊','Entertainment':'🎬','Bills':'📄','Education':'📚','Other':'📌','Salary':'💼','Freelance':'💻','Investment':'📈','Gift':'🎁','Rental':'🏢'};
  const icon = icons[t.category] || '💳';
  const d = new Date(t.date+'T00:00:00');
  const dateStr = d.toLocaleDateString('en-AE',{day:'numeric',month:'short'});
  return `<div class="txn-item">
    <div class="txn-icon" style="background:${t.type==='income'?'var(--green-light)':'var(--red-light)'}">${icon}</div>
    <div class="txn-body">
      <div class="txn-name">${t.note || t.category}</div>
      <div class="txn-meta">${t.category} · ${dateStr}</div>
    </div>
    <div class="txn-amount ${t.type}">${t.type==='income'?'+':'-'}${fmt(t.amount)}</div>
    <button class="txn-del" onclick="deleteTxn(${t.id})">✕</button>
  </div>`;
}

function goalMiniHTML(g) {
  const pct = Math.min(100, g.target > 0 ? (g.saved/g.target*100) : 0);
  return `<div style="padding:14px 18px;border-bottom:1px solid var(--border);">
    <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px;">
      <span style="font-size:20px">${g.emoji||'🎯'}</span>
      <span style="font-size:14px;font-weight:600;flex:1">${g.name}</span>
      <span style="font-family:'Instrument Serif',serif;font-size:16px;color:var(--gold)">${fmt(g.saved)}</span>
    </div>
    <div class="progress-bar"><div class="progress-fill ${pct>=100?'complete':''}" style="width:${pct}%"></div></div>
    <div class="goal-pct">${pct.toFixed(0)}% of ${fmt(g.target)}</div>
  </div>`;
}

// ── TRANSACTIONS ──
function renderTransactions() {
  document.getElementById('txnMonthLabel').textContent = MONTHS[viewMonth] + ' ' + viewYear;
  const txns = txnsForMonth().sort((a,b)=>new Date(b.date)-new Date(a.date));
  const income = txns.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0);
  const expense = txns.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0);
  document.getElementById('txnIncome').textContent = fmt(income);
  document.getElementById('txnExpense').textContent = fmt(expense);

  // Category chart
  const expTxns = txns.filter(t=>t.type==='expense');
  const catMap = expTxns.reduce((m,t) => { m[t.category]=(m[t.category]||0)+t.amount; return m; }, {});
  const sorted = Object.entries(catMap).sort((a,b)=>b[1]-a[1]);
  const chartEl = document.getElementById('catChart');
  if (sorted.length === 0) { chartEl.innerHTML = '<div class="empty-text" style="text-align:center;color:var(--ink3);font-size:13px;padding:8px">No expenses this month</div>'; }
  else {
    const max = sorted[0][1];
    chartEl.innerHTML = sorted.map(([cat,amt]) => `
      <div class="cat-row-chart">
        <div class="cat-row-top"><span class="cat-name">${cat}</span><span>${fmt(amt)}</span></div>
        <div class="bar-bg"><div class="bar-fill" style="width:${(amt/max*100).toFixed(1)}%"></div></div>
      </div>`).join('');
  }

  const listEl = document.getElementById('allTxns');
  listEl.innerHTML = txns.length ? txns.map(t=>txnHTML(t)).join('') : '<div class="empty"><div class="empty-icon">📋</div><div class="empty-text">No transactions this month</div></div>';
}

function deleteTxn(id) {
  data.txns = data.txns.filter(t=>t.id!==id);
  save(); renderPage(currentPage); if(currentPage!=='home') renderHome();
}

// ── SAVINGS ──
function renderSavings() {
  const el = document.getElementById('goalsList');
  el.innerHTML = data.goals.length ? data.goals.map(g => goalHTML(g)).join('') : '<div class="empty"><div class="empty-icon">🎯</div><div class="empty-text">No goals yet. Tap + to add one.</div></div>';
}

function goalHTML(g) {
  const pct = Math.min(100, g.target > 0 ? (g.saved/g.target*100) : 0);
  const remaining = Math.max(0, g.target - g.saved);

  // ── PROJECTION ENGINE ──
  let projectionHTML = '';
  if (g.deadline && remaining > 0) {
    const now = new Date();
    const [dy, dm] = g.deadline.split('-').map(Number);
    const deadlineDate = new Date(dy, dm - 1, 1); // first of deadline month
    // months remaining INCLUDING deadline month
    const monthsLeft = (dy - now.getFullYear()) * 12 + (dm - 1 - now.getMonth());

    if (monthsLeft <= 0) {
      projectionHTML = `
        <div style="margin:0 18px 16px;background:var(--red-light);border-radius:12px;padding:14px 16px;">
          <div style="font-size:12px;color:var(--red);font-weight:700;margin-bottom:4px">⚠️ Deadline Passed</div>
          <div style="font-size:12px;color:var(--red);">You still need ${fmt(remaining)} to reach your goal.</div>
        </div>`;
    } else {
      const monthlyNeeded = remaining / monthsLeft;
      // Avg monthly savings over last 3 months from goal additions (approximate via saved/months since creation)
      const createdMonthsAgo = Math.max(1, Math.round((now - new Date(g.id)) / (1000*60*60*24*30)));
      const avgMonthlySaved = g.saved / createdMonthsAgo;
      const onTrack = avgMonthlySaved >= monthlyNeeded;
      const projectedSaved = g.saved + avgMonthlySaved * monthsLeft;
      const projectedPct = Math.min(100, (projectedSaved / g.target) * 100);
      const shortfall = Math.max(0, g.target - projectedSaved);

      // Build month-by-month mini timeline (next 6 months or till deadline)
      const timelineMonths = Math.min(monthsLeft, 6);
      const timelineItems = [];
      for (let i = 1; i <= timelineMonths; i++) {
        const mDate = new Date(now.getFullYear(), now.getMonth() + i, 1);
        const mLabel = MONTHS[mDate.getMonth()].slice(0,3) + ' ' + String(mDate.getFullYear()).slice(2);
        const cumulative = Math.min(g.target, g.saved + monthlyNeeded * i);
        const mPct = (cumulative / g.target * 100).toFixed(0);
        const isLast = i === timelineMonths && monthsLeft <= 6;
        timelineItems.push({mLabel, cumulative, mPct, isLast});
      }

      projectionHTML = `
        <div style="margin:0 18px 16px;">
          <!-- Status banner -->
          <div style="background:${onTrack?'var(--green-light)':'var(--gold-light)'};border-radius:12px;padding:14px 16px;margin-bottom:12px;">
            <div style="display:flex;align-items:center;gap:8px;margin-bottom:8px;">
              <span style="font-size:18px">${onTrack?'✅':'⚡'}</span>
              <span style="font-size:13px;font-weight:700;color:${onTrack?'var(--green)':'var(--gold)'}">
                ${onTrack ? 'On Track!' : 'Needs Attention'}
              </span>
              <span style="margin-left:auto;font-size:11px;color:var(--ink2)">${monthsLeft} month${monthsLeft!==1?'s':''} left</span>
            </div>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
              <div style="background:rgba(255,255,255,.6);border-radius:8px;padding:10px;">
                <div style="font-size:10px;color:var(--ink2);letter-spacing:.06em;margin-bottom:3px">SAVE PER MONTH</div>
                <div style="font-family:'Instrument Serif',serif;font-size:18px;color:${onTrack?'var(--green)':'var(--red)'}">${fmt(monthlyNeeded)}</div>
                <div style="font-size:10px;color:var(--ink3);margin-top:2px">required</div>
              </div>
              <div style="background:rgba(255,255,255,.6);border-radius:8px;padding:10px;">
                <div style="font-size:10px;color:var(--ink2);letter-spacing:.06em;margin-bottom:3px">AVG SAVED/MO</div>
                <div style="font-family:'Instrument Serif',serif;font-size:18px;color:var(--ink)">${fmt(avgMonthlySaved)}</div>
                <div style="font-size:10px;color:var(--ink3);margin-top:2px">current pace</div>
              </div>
            </div>
            ${!onTrack && shortfall > 0 ? `<div style="margin-top:10px;padding:8px 10px;background:rgba(184,50,50,.1);border-radius:8px;font-size:12px;color:var(--red);">
              At this pace you'll be <strong>${fmt(shortfall)}</strong> short by ${MONTHS[dm-1]} ${dy}. Increase monthly savings by <strong>${fmt(monthlyNeeded - avgMonthlySaved)}</strong>.
            </div>` : ''}
            ${onTrack ? `<div style="margin-top:10px;padding:8px 10px;background:rgba(45,106,79,.1);border-radius:8px;font-size:12px;color:var(--green);">
              Great pace! Keep saving ${fmt(monthlyNeeded)} monthly and you'll hit your goal by ${MONTHS[dm-1]} ${dy}. 🎉
            </div>` : ''}
          </div>

          <!-- Month-by-month timeline -->
          <div style="font-size:11px;color:var(--ink2);letter-spacing:.06em;margin-bottom:10px;">SAVINGS ROADMAP</div>
          <div style="display:flex;flex-direction:column;gap:8px;">
            ${timelineItems.map((item,i) => `
              <div style="display:flex;align-items:center;gap:10px;">
                <div style="width:52px;font-size:11px;color:${item.isLast?'var(--gold)':'var(--ink2)'};font-weight:${item.isLast?'700':'400'};flex-shrink:0">${item.mLabel}</div>
                <div style="flex:1;height:8px;background:var(--bg2);border-radius:4px;overflow:hidden;">
                  <div style="height:100%;width:${item.mPct}%;border-radius:4px;background:${item.isLast?'linear-gradient(90deg,var(--gold),#e8b05a)':'linear-gradient(90deg,var(--green),#5aa87a)'};transition:width .5s;"></div>
                </div>
                <div style="width:38px;font-size:11px;color:var(--ink2);text-align:right">${item.mPct}%</div>
                <div style="width:70px;font-size:11px;font-family:'Instrument Serif',serif;color:${item.isLast?'var(--gold)':'var(--ink)'};text-align:right">${fmt(item.cumulative)}</div>
              </div>`).join('')}
            ${monthsLeft > 6 ? `<div style="font-size:11px;color:var(--ink3);text-align:center;padding:4px 0">... and ${monthsLeft-6} more month${monthsLeft-6>1?'s':''} to go</div>` : ''}
          </div>
        </div>`;
    }
  } else if (!g.deadline && remaining > 0) {
    projectionHTML = `<div style="margin:0 18px 16px;background:var(--bg2);border-radius:10px;padding:12px 14px;font-size:12px;color:var(--ink2);">💡 Set a deadline when creating a goal to see your savings projection.</div>`;
  }

  return `<div class="goal-card">
    <div class="goal-header">
      <div class="goal-emoji">${g.emoji||'🎯'}</div>
      <div class="goal-info">
        <div class="goal-name">${g.name}</div>
        <div class="goal-target">Target: ${fmt(g.target)}${g.deadline?' · Due '+MONTHS[parseInt(g.deadline.split('-')[1])-1]+' '+g.deadline.split('-')[0]:''}</div>
        <div class="goal-saved">${fmt(g.saved)} saved</div>
        <div class="goal-actions">
          <button class="goal-add-btn" onclick="openAddGoalModal(${g.id})">+ Add Savings</button>
          <button class="goal-add-btn" style="background:var(--blue-light);color:var(--blue);" onclick="openEditGoalModal(${g.id})">✏️ Edit</button>
          <button class="goal-del-btn" onclick="deleteGoal(${g.id})">Delete</button>
        </div>
      </div>
    </div>
    <div class="progress-bar" style="margin:0 0 6px"><div class="progress-fill ${pct>=100?'complete':''}" style="width:${pct}%"></div></div>
    <div class="goal-pct" style="margin-bottom:${projectionHTML?'14px':'0'}">${pct.toFixed(0)}% complete · ${fmt(remaining)} remaining${pct>=100?' · 🎉 Goal reached!':''}</div>
    ${projectionHTML}
  </div>`;
}

function deleteGoal(id) { data.goals=data.goals.filter(g=>g.id!==id); save(); renderSavings(); }

// ── BILLS ──
function renderBills() {
  const today = new Date(); today.setHours(0,0,0,0);
  const sorted = [...data.bills].sort((a,b)=>new Date(a.due)-new Date(b.due));
  const el = document.getElementById('billsList');
  el.innerHTML = sorted.length ? sorted.map(b => billHTML(b, today)).join('') : '<div class="empty"><div class="empty-icon">📅</div><div class="empty-text">No bills yet. Tap + to add one.</div></div>';
}

function billHTML(b, today) {
  const due = new Date(b.due); due.setHours(0,0,0,0);
  const diff = Math.round((due - today) / 86400000);
  let statusHTML = '';
  if (b.paid) { statusHTML = '<div class="paid-badge">✓ Paid</div>'; }
  else if (diff < 0) { statusHTML = `<div class="bill-status bill-overdue">Overdue by ${Math.abs(diff)} day${Math.abs(diff)>1?'s':''}</div>`; }
  else if (diff === 0) { statusHTML = '<div class="bill-status bill-soon">Due today!</div>'; }
  else if (diff <= 7) { statusHTML = `<div class="bill-status bill-soon">Due in ${diff} day${diff>1?'s':''}</div>`; }
  else { statusHTML = `<div class="bill-status bill-ok">Due in ${diff} days</div>`; }
  const dateStr = new Date(b.due+'T00:00:00').toLocaleDateString('en-AE',{day:'numeric',month:'short',year:'numeric'});
  return `<div class="bill-item">
    <div class="bill-icon">${b.emoji||'📄'}</div>
    <div class="bill-body">
      <div class="bill-name">${b.name}</div>
      <div class="bill-date">${dateStr}</div>
      ${!b.paid ? `<button class="mark-paid-btn" onclick="markBillPaid(${b.id})">Mark Paid</button>` : ''}
    </div>
    <div>
      <div class="bill-amount">${fmt(b.amount)}</div>
      ${statusHTML}
    </div>
    <button class="bill-del" onclick="deleteBill(${b.id})">✕</button>
  </div>`;
}

function markBillPaid(id) { const b=data.bills.find(b=>b.id===id); if(b) b.paid=true; save(); renderBills(); renderHome(); }
function deleteBill(id) { data.bills=data.bills.filter(b=>b.id!==id); save(); renderBills(); }

// ── MODALS ──
function openTxnModal() {
  document.getElementById('txnDate').value = todayStr();
  document.getElementById('txnAmount').value = '';
  document.getElementById('txnNote').value = '';
  setTxnType('expense');
  document.getElementById('txnOverlay').classList.add('open');
}
function closeTxnModal(e) { if(!e||e.target===document.getElementById('txnOverlay')) document.getElementById('txnOverlay').classList.remove('open'); }
function setTxnType(t) {
  txnType = t;
  document.getElementById('btnExp').className='type-btn '+(t==='expense'?'expense-on':'off');
  document.getElementById('btnInc').className='type-btn '+(t==='income'?'income-on':'off');
  const sel = document.getElementById('txnCategory');
  const cats = t==='expense'? getExpCats() : getIncCats();
  sel.innerHTML = cats.map(c => {
    const parts = c.split('|');
    const name = parts.length > 1 ? parts[1] : parts[0];
    return `<option value="${name}">${parts.length > 1 ? parts[0]+' ' : ''}${name}</option>`;
  }).join('');
}
function saveTxn() {
  const amt = parseFloat(document.getElementById('txnAmount').value);
  if(!amt||amt<=0) return;
  data.txns.push({ id: Date.now(), type: txnType, amount: amt, category: document.getElementById('txnCategory').value, note: document.getElementById('txnNote').value.trim(), date: document.getElementById('txnDate').value||todayStr() });
  save(); closeTxnModal(); renderHome(); if(currentPage==='transactions') renderTransactions();
}

const GOAL_EMOJIS = ['🎯','✈️','🏠','🚗','💍','📱','💻','🎓','👶','🏖️','⛵','🏋️','🎸','📷','🛍️','💰','🏦','🌍','🎁','🏥','🐾','🍽️','☕','🧳','🎬','🏕️','🚀','💎','🌱','🎉'];

function renderEmojiPicker(selected) {
  const picker = document.getElementById('emojiPicker');
  picker.innerHTML = GOAL_EMOJIS.map(e =>
    `<button onclick="selectEmoji('${e}')" style="width:38px;height:38px;border:2px solid ${e===selected?'var(--gold)':'transparent'};border-radius:10px;background:${e===selected?'var(--gold-light)':'transparent'};font-size:20px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .15s;" id="epick-${encodeURIComponent(e)}">${e}</button>`
  ).join('');
}

function selectEmoji(e) {
  document.getElementById('goalEmoji').value = e;
  document.getElementById('selectedEmojiPreview').textContent = e;
  renderEmojiPicker(e);
}

function updateEmojiPreview(val) {
  if (val.trim()) {
    document.getElementById('selectedEmojiPreview').textContent = val.trim();
    renderEmojiPicker('__custom__');
  }
}

let editingGoalId = null;

function openGoalModal() {
  editingGoalId = null;
  document.getElementById('goalModalTitle').textContent = 'New Savings Goal';
  document.getElementById('goalSubmitBtn').textContent = 'CREATE GOAL';
  document.getElementById('goalName').value = '';
  document.getElementById('goalEmoji').value = '';
  document.getElementById('goalTarget').value = '';
  document.getElementById('goalSaved').value = '';
  const now = new Date();
  document.getElementById('goalDeadline').value = `${now.getFullYear()}-${String(now.getMonth()+2).padStart(2,'0')}`;
  document.getElementById('selectedEmojiPreview').textContent = '🎯';
  renderEmojiPicker('🎯');
  document.getElementById('goalOverlay').classList.add('open');
}

function openEditGoalModal(id) {
  editingGoalId = id;
  const g = data.goals.find(g => g.id === id);
  if (!g) return;
  document.getElementById('goalModalTitle').textContent = 'Edit Goal';
  document.getElementById('goalSubmitBtn').textContent = 'SAVE CHANGES';
  document.getElementById('goalName').value = g.name;
  document.getElementById('goalEmoji').value = g.emoji || '🎯';
  document.getElementById('goalTarget').value = g.target;
  document.getElementById('goalSaved').value = g.saved || 0;
  document.getElementById('goalDeadline').value = g.deadline || '';
  document.getElementById('selectedEmojiPreview').textContent = g.emoji || '🎯';
  renderEmojiPicker(g.emoji || '🎯');
  document.getElementById('goalOverlay').classList.add('open');
}

function closeGoalModal(e) { if(!e||e.target===document.getElementById('goalOverlay')) document.getElementById('goalOverlay').classList.remove('open'); }

function saveGoal() {
  const name = document.getElementById('goalName').value.trim();
  const target = parseFloat(document.getElementById('goalTarget').value);
  const saved = parseFloat(document.getElementById('goalSaved').value) || 0;
  const deadline = document.getElementById('goalDeadline').value;
  const emoji = document.getElementById('selectedEmojiPreview').textContent.trim() || '🎯';
  if (!name || !target || target <= 0 || !deadline) return;

  if (editingGoalId !== null) {
    const g = data.goals.find(g => g.id === editingGoalId);
    if (g) { g.name = name; g.emoji = emoji; g.target = target; g.saved = saved; g.deadline = deadline; }
  } else {
    data.goals.push({ id: Date.now(), name, emoji, target, saved, deadline });
  }
  save();
  closeGoalModal();
  renderSavings();
  renderHome();
}

function openAddGoalModal(id) {
  addGoalId=id; const g=data.goals.find(g=>g.id===id);
  document.getElementById('addGoalTitle').textContent='Add to: '+g.name;
  document.getElementById('addGoalAmount').value='';
  document.getElementById('addGoalOverlay').classList.add('open');
}
function closeAddGoalModal(e) { if(!e||e.target===document.getElementById('addGoalOverlay')) document.getElementById('addGoalOverlay').classList.remove('open'); }
function confirmAddToGoal() {
  const amt=parseFloat(document.getElementById('addGoalAmount').value); if(!amt||amt<=0) return;
  const g=data.goals.find(g=>g.id===addGoalId); if(g) g.saved+=amt;
  save(); closeAddGoalModal(); renderSavings(); renderHome();
}

function openBillModal() { document.getElementById('billName').value=''; document.getElementById('billEmoji').value=''; document.getElementById('billAmount').value=''; document.getElementById('billDue').value=''; document.getElementById('billOverlay').classList.add('open'); }
function closeBillModal(e) { if(!e||e.target===document.getElementById('billOverlay')) document.getElementById('billOverlay').classList.remove('open'); }
function saveBill() {
  const name=document.getElementById('billName').value.trim(); const amt=parseFloat(document.getElementById('billAmount').value); const due=document.getElementById('billDue').value;
  if(!name||!amt||amt<=0||!due) return;
  data.bills.push({ id: Date.now(), name, emoji: document.getElementById('billEmoji').value||'📄', amount: amt, due, paid: false });
  save(); closeBillModal(); renderBills();
}

// ── REPORTS ──
let reportMonth = new Date().getMonth();
let reportYear = new Date().getFullYear();

function changeReportMonth(d) {
  reportMonth += d;
  if (reportMonth > 11) { reportMonth = 0; reportYear++; }
  if (reportMonth < 0) { reportMonth = 11; reportYear--; }
  renderReports();
}

function renderReports() {
  document.getElementById('reportMonthLabel').textContent = MONTHS[reportMonth] + ' ' + reportYear;
  const txns = data.txns.filter(t => {
    const d = new Date(t.date);
    return d.getMonth() === reportMonth && d.getFullYear() === reportYear;
  });
  drawBarChart(txns);
  drawDonutChart(txns);
  renderGoalsReport();
  renderBillsReport();
}

function drawBarChart(txns) {
  const canvas = document.getElementById('barChart');
  const ctx = canvas.getContext('2d');
  const dpr = window.devicePixelRatio || 1;
  const W = canvas.parentElement.clientWidth - 40;
  const H = 200;
  canvas.width = W * dpr; canvas.height = H * dpr;
  canvas.style.width = W + 'px'; canvas.style.height = H + 'px';
  ctx.scale(dpr, dpr);
  ctx.clearRect(0, 0, W, H);

  // Last 6 months data
  const months = [];
  for (let i = 5; i >= 0; i--) {
    let m = reportMonth - i, y = reportYear;
    if (m < 0) { m += 12; y--; }
    const mt = data.txns.filter(t => { const d = new Date(t.date); return d.getMonth()===m && d.getFullYear()===y; });
    months.push({
      label: MONTHS[m].slice(0,3),
      income: mt.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0),
      expense: mt.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0)
    });
  }

  const maxVal = Math.max(...months.map(m=>Math.max(m.income,m.expense)), 1);
  const pad = { top: 10, bottom: 30, left: 10, right: 10 };
  const chartH = H - pad.top - pad.bottom;
  const slotW = (W - pad.left - pad.right) / 6;
  const barW = slotW * 0.28;
  const gap = slotW * 0.06;

  months.forEach((m, i) => {
    const x = pad.left + i * slotW + slotW / 2;
    const incH = (m.income / maxVal) * chartH;
    const expH = (m.expense / maxVal) * chartH;

    // Income bar
    ctx.fillStyle = '#d8ede5';
    ctx.beginPath();
    ctx.roundRect(x - barW - gap/2, pad.top + chartH - incH, barW, incH, [4,4,0,0]);
    ctx.fill();

    // Expense bar
    ctx.fillStyle = '#f5dada';
    ctx.beginPath();
    ctx.roundRect(x + gap/2, pad.top + chartH - expH, barW, expH, [4,4,0,0]);
    ctx.fill();

    // Highlight current month
    if (i === 5) {
      ctx.fillStyle = '#2d6a4f';
      ctx.beginPath();
      ctx.roundRect(x - barW - gap/2, pad.top + chartH - incH, barW, incH, [4,4,0,0]);
      ctx.fill();
      ctx.fillStyle = '#b83232';
      ctx.beginPath();
      ctx.roundRect(x + gap/2, pad.top + chartH - expH, barW, expH, [4,4,0,0]);
      ctx.fill();
    }

    // Label
    ctx.fillStyle = i === 5 ? '#1a1814' : '#b0ada8';
    ctx.font = (i===5?'600 ':'400 ') + '10px Syne, sans-serif';
    ctx.textAlign = 'center';
    ctx.fillText(m.label, x, H - 8);
  });

  // Legend
  document.getElementById('barLegend').innerHTML = `
    <span style="display:flex;align-items:center;gap:5px;"><span style="width:12px;height:12px;border-radius:3px;background:#2d6a4f;display:inline-block"></span>Income</span>
    <span style="display:flex;align-items:center;gap:5px;"><span style="width:12px;height:12px;border-radius:3px;background:#b83232;display:inline-block"></span>Expense</span>`;
}

function drawDonutChart(txns) {
  const canvas = document.getElementById('donutChart');
  const ctx = canvas.getContext('2d');
  const dpr = window.devicePixelRatio || 1;
  canvas.width = 160 * dpr; canvas.height = 160 * dpr;
  canvas.style.width = '160px'; canvas.style.height = '160px';
  ctx.scale(dpr, dpr);
  ctx.clearRect(0, 0, 160, 160);

  const expTxns = txns.filter(t=>t.type==='expense');
  const total = expTxns.reduce((s,t)=>s+t.amount, 0);
  const catMap = expTxns.reduce((m,t) => { m[t.category]=(m[t.category]||0)+t.amount; return m; }, {});
  const entries = Object.entries(catMap).sort((a,b)=>b[1]-a[1]);

  const COLORS = ['#c8963c','#2d6a4f','#b83232','#2c4a7c','#7c5c2c','#4a7c2c','#7c2c6a','#2c6a7c','#6a2c2c'];

  if (entries.length === 0) {
    ctx.strokeStyle = '#e0ddd6'; ctx.lineWidth = 22 * dpr / dpr;
    ctx.beginPath(); ctx.arc(80, 80, 58, 0, Math.PI * 2); ctx.stroke();
    ctx.fillStyle = '#b0ada8'; ctx.font = '11px Syne,sans-serif'; ctx.textAlign = 'center';
    ctx.fillText('No data', 80, 84);
    document.getElementById('donutLegend').innerHTML = '<span style="color:var(--ink3);font-size:12px">No expenses this month</span>';
    return;
  }

  let startAngle = -Math.PI / 2;
  entries.forEach(([cat, amt], i) => {
    const slice = (amt / total) * Math.PI * 2;
    ctx.beginPath();
    ctx.moveTo(80, 80);
    ctx.arc(80, 80, 68, startAngle, startAngle + slice);
    ctx.closePath();
    ctx.fillStyle = COLORS[i % COLORS.length];
    ctx.fill();
    startAngle += slice;
  });

  // Donut hole
  ctx.beginPath(); ctx.arc(80, 80, 44, 0, Math.PI * 2);
  ctx.fillStyle = '#fff'; ctx.fill();

  // Center text
  ctx.fillStyle = '#1a1814'; ctx.font = 'bold 11px Syne,sans-serif'; ctx.textAlign = 'center';
  ctx.fillText('TOTAL', 80, 76);
  ctx.font = '600 12px Instrument Serif,serif'; ctx.fillStyle = '#c8963c';
  ctx.fillText('AED ' + total.toLocaleString('en-AE',{maximumFractionDigits:0}), 80, 92);

  // Legend
  document.getElementById('donutLegend').innerHTML = entries.map(([cat,amt],i) =>
    `<div style="display:flex;align-items:center;gap:7px;margin-bottom:7px;">
      <span style="width:10px;height:10px;border-radius:2px;background:${COLORS[i%COLORS.length]};flex-shrink:0;display:inline-block"></span>
      <span style="flex:1;color:var(--ink2);overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${cat}</span>
      <span style="color:var(--ink);font-weight:600">${(amt/total*100).toFixed(0)}%</span>
    </div>`).join('');
}

function renderGoalsReport() {
  const el = document.getElementById('reportGoals');
  if (data.goals.length === 0) { el.innerHTML = '<div class="empty"><div class="empty-icon">🎯</div><div class="empty-text">No savings goals yet</div></div>'; return; }
  const totalTarget = data.goals.reduce((s,g)=>s+g.target,0);
  const totalSaved = data.goals.reduce((s,g)=>s+g.saved,0);
  el.innerHTML = `
    <div style="padding:16px 18px;border-bottom:1px solid var(--border);display:grid;grid-template-columns:1fr 1fr;gap:12px;">
      <div><div style="font-size:10px;color:var(--ink2);letter-spacing:.08em;margin-bottom:4px">TOTAL SAVED</div><div style="font-family:'Instrument Serif',serif;font-size:20px;color:var(--gold)">${fmt(totalSaved)}</div></div>
      <div><div style="font-size:10px;color:var(--ink2);letter-spacing:.08em;margin-bottom:4px">TOTAL TARGET</div><div style="font-family:'Instrument Serif',serif;font-size:20px;">${fmt(totalTarget)}</div></div>
    </div>
    ${data.goals.map(g => {
      const pct = Math.min(100, g.target > 0 ? (g.saved/g.target*100) : 0);
      const remaining = Math.max(0, g.target - g.saved);
      return `<div style="padding:14px 18px;border-bottom:1px solid var(--border);">
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:10px;">
          <span style="font-size:20px">${g.emoji||'🎯'}</span>
          <div style="flex:1">
            <div style="font-size:14px;font-weight:600">${g.name}</div>
            <div style="font-size:11px;color:var(--ink3);margin-top:1px">${fmt(g.saved)} of ${fmt(g.target)}</div>
          </div>
          <div style="text-align:right">
            <div style="font-size:16px;font-family:'Instrument Serif',serif;color:${pct>=100?'var(--green)':'var(--gold)'}">${pct.toFixed(0)}%</div>
            ${pct<100?`<div style="font-size:10px;color:var(--ink3)">AED ${remaining.toLocaleString('en-AE',{maximumFractionDigits:0})} left</div>`:'<div style="font-size:10px;color:var(--green)">✓ Done!</div>'}
          </div>
        </div>
        <div class="progress-bar"><div class="progress-fill ${pct>=100?'complete':''}" style="width:${pct}%"></div></div>
      </div>`;
    }).join('')}`;
}

function renderBillsReport() {
  const el = document.getElementById('reportBills');
  if (data.bills.length === 0) { el.innerHTML = '<div class="empty"><div class="empty-icon">📅</div><div class="empty-text">No bills added yet</div></div>'; return; }
  const today = new Date(); today.setHours(0,0,0,0);
  const paid = data.bills.filter(b=>b.paid);
  const unpaid = data.bills.filter(b=>!b.paid);
  const overdue = unpaid.filter(b=>new Date(b.due)<today);
  const upcoming = unpaid.filter(b=>new Date(b.due)>=today);
  const totalUnpaid = unpaid.reduce((s,b)=>s+b.amount,0);
  const totalPaid = paid.reduce((s,b)=>s+b.amount,0);

  el.innerHTML = `
    <div style="padding:16px 18px;border-bottom:1px solid var(--border);display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;text-align:center;">
      <div><div style="font-size:10px;color:var(--red);letter-spacing:.06em;margin-bottom:4px">OVERDUE</div><div style="font-family:'Instrument Serif',serif;font-size:20px;color:var(--red)">${overdue.length}</div></div>
      <div><div style="font-size:10px;color:var(--gold);letter-spacing:.06em;margin-bottom:4px">UPCOMING</div><div style="font-family:'Instrument Serif',serif;font-size:20px;color:var(--gold)">${upcoming.length}</div></div>
      <div><div style="font-size:10px;color:var(--green);letter-spacing:.06em;margin-bottom:4px">PAID</div><div style="font-family:'Instrument Serif',serif;font-size:20px;color:var(--green)">${paid.length}</div></div>
    </div>
    <div style="padding:14px 18px;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;">
      <div style="font-size:13px;color:var(--ink2)">Total unpaid</div>
      <div style="font-family:'Instrument Serif',serif;font-size:18px;color:var(--red)">${fmt(totalUnpaid)}</div>
    </div>
    <div style="padding:14px 18px;display:flex;justify-content:space-between;align-items:center;">
      <div style="font-size:13px;color:var(--ink2)">Total paid</div>
      <div style="font-family:'Instrument Serif',serif;font-size:18px;color:var(--green)">${fmt(totalPaid)}</div>
    </div>
    ${overdue.length>0?`<div style="padding:0 18px 14px;"><div style="background:var(--red-light);border-radius:10px;padding:12px 14px;"><div style="font-size:11px;color:var(--red);font-weight:600;margin-bottom:8px">⚠️ OVERDUE BILLS</div>${overdue.map(b=>`<div style="display:flex;justify-content:space-between;font-size:13px;padding:3px 0;"><span>${b.emoji||'📄'} ${b.name}</span><span style="color:var(--red);font-weight:600">${fmt(b.amount)}</span></div>`).join('')}</div></div>`:''}`;
}

// ── SETTINGS & CATEGORIES ──
let editingCatType = null;
let editingCatIndex = null;

function renderSettings() {
  renderCatList('expense');
  renderCatList('income');
}

function renderCatList(type) {
  const cats = type === 'expense' ? data.expCats : data.incCats;
  const defaults = type === 'expense' ? DEFAULT_EXP_CATS : DEFAULT_INC_CATS;
  const elId = type === 'expense' ? 'expCatList' : 'incCatList';
  const el = document.getElementById(elId);
  if (!el) return;

  const catIcons = {'Food & Dining':'🍽️','Transport':'🚗','Shopping':'🛍️','Housing':'🏠','Health':'💊','Entertainment':'🎬','Bills':'📄','Education':'📚','Salary':'💼','Freelance':'💻','Investment':'📈','Gift':'🎁','Rental':'🏢','Other':'📌'};

  el.innerHTML = cats.map((cat, i) => {
    const parts = cat.split('|');
    const emoji = parts.length > 1 ? parts[0] : (catIcons[parts[0]] || '📌');
    const name = parts.length > 1 ? parts[1] : parts[0];
    const isDefault = defaults.includes(cat) || defaults.includes(name);
    return `<div class="cat-item">
      <div class="cat-emoji">${emoji}</div>
      <div class="cat-name-text">${name}</div>
      ${isDefault ? '<span class="cat-default-tag">default</span>' : ''}
      <button class="cat-edit-btn" onclick="openEditCatModal('${type}', ${i})">Edit</button>
      <button class="cat-del-btn" onclick="deleteCat('${type}', ${i})">✕</button>
    </div>`;
  }).join('') || '<div class="empty" style="padding:20px"><div class="empty-text">No categories. Add one below.</div></div>';
}

function getCatDisplay(cat) {
  const parts = cat.split('|');
  if (parts.length > 1) return { emoji: parts[0], name: parts[1] };
  const icons = {'Food & Dining':'🍽️','Transport':'🚗','Shopping':'🛍️','Housing':'🏠','Health':'💊','Entertainment':'🎬','Bills':'📄','Education':'📚','Salary':'💼','Freelance':'💻','Investment':'📈','Gift':'🎁','Rental':'🏢','Other':'📌'};
  return { emoji: icons[parts[0]] || '📌', name: parts[0] };
}

function openCatModal(type) {
  editingCatType = type;
  editingCatIndex = null;
  document.getElementById('catModalTitle').textContent = `Add ${type === 'expense' ? 'Expense' : 'Income'} Category`;
  document.getElementById('catSubmitBtn').textContent = 'ADD CATEGORY';
  document.getElementById('catEmoji').value = '';
  document.getElementById('catName').value = '';
  document.getElementById('catOverlay').classList.add('open');
}

function openEditCatModal(type, index) {
  editingCatType = type;
  editingCatIndex = index;
  const cats = type === 'expense' ? data.expCats : data.incCats;
  const { emoji, name } = getCatDisplay(cats[index]);
  document.getElementById('catModalTitle').textContent = 'Edit Category';
  document.getElementById('catSubmitBtn').textContent = 'SAVE CHANGES';
  document.getElementById('catEmoji').value = emoji;
  document.getElementById('catName').value = name;
  document.getElementById('catOverlay').classList.add('open');
}

function closeCatModal(e) {
  if (!e || e.target === document.getElementById('catOverlay'))
    document.getElementById('catOverlay').classList.remove('open');
}

function saveCategory() {
  const name = document.getElementById('catName').value.trim();
  const emoji = document.getElementById('catEmoji').value.trim() || '📌';
  if (!name) return;
  const entry = `${emoji}|${name}`;
  const cats = editingCatType === 'expense' ? data.expCats : data.incCats;

  if (editingCatIndex !== null) {
    cats[editingCatIndex] = entry;
  } else {
    cats.push(entry);
  }
  save();
  closeCatModal();
  renderSettings();
  // Refresh transaction form dropdown if open
  setTxnType(txnType);
}

function deleteCat(type, index) {
  const cats = type === 'expense' ? data.expCats : data.incCats;
  if (cats.length <= 1) { alert('You must have at least one category.'); return; }
  cats.splice(index, 1);
  save();
  renderSettings();
  setTxnType(txnType);
}

function resetCategories() {
  if (!confirm('Reset all categories to defaults?')) return;
  data.expCats = [...DEFAULT_EXP_CATS];
  data.incCats = [...DEFAULT_INC_CATS];
  save();
  renderSettings();
  setTxnType(txnType);
}

// ── UPDATE APP ──
async function updateApp() {
  const btn = document.getElementById('updateBtn');
  const status = document.getElementById('updateStatus');
  const versionLabel = document.getElementById('appVersionLabel');

  btn.disabled = true;
  btn.textContent = '⏳ Fetching latest version...';
  btn.style.opacity = '0.7';
  status.style.display = 'block';
  status.style.color = 'var(--ink3)';
  status.textContent = 'Connecting to Claude API...';

  try {
    const prompt = `You are a code delivery assistant. Output ONLY the complete raw HTML code for the Malia personal finance app — a single self-contained HTML file with no markdown, no explanation, no code fences. 

The app must include ALL of these features:
- 6-tab navigation: Home, Transactions, Add (gold circle button), Goals, Reports, Bills, Settings
- AED currency throughout
- Income & expense tracking with dynamic categories (editable in Settings)
- Savings goals with emoji picker grid, deadline, projection engine (monthly required savings, roadmap timeline, on-track status)
- Bill reminders with mark-paid, overdue detection
- Reports page: 6-month bar chart, donut chart by category, goals progress report, bills summary
- Settings page: expense & income category manager (add/edit/delete with emoji), reset to defaults, Update App button (this same feature — calls Claude API at https://api.anthropic.com/v1/messages using fetch with model claude-sonnet-4-20250514, no API key in headers since it's handled by proxy)
- All data stored in localStorage key 'malia-v1' with fields: txns, goals, bills, expCats, incCats
- Fonts: Syne + Instrument Serif from Google Fonts
- Color scheme: warm cream background #f5f2ec, dark header #1a1814, gold accent #c8963c
- The update function must use fetch to POST to https://api.anthropic.com/v1/messages with this exact prompt to regenerate itself, then replace document.open/write/close with the response

Output ONLY the HTML. Start with <!DOCTYPE html> and end with </html>.`;

    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 8000,
        messages: [{ role: 'user', content: prompt }]
      })
    });

    if (!response.ok) throw new Error('API error: ' + response.status);

    const result = await response.json();
    const newCode = result.content.map(c => c.text || '').join('').trim();

    if (!newCode.includes('<!DOCTYPE') && !newCode.includes('<html')) {
      throw new Error('Invalid response received');
    }

    status.textContent = '✅ Got latest version! Backing up your data...';

    // Back up all data before reload
    const backup = localStorage.getItem('malia-v1');

    status.textContent = '💾 Applying update...';

    // Write new app into page
    document.open();
    document.write(newCode);
    document.close();

    // Restore data after page rewrites
    if (backup) localStorage.setItem('malia-v1', backup);

  } catch (err) {
    btn.disabled = false;
    btn.textContent = '⚡ UPDATE APP';
    btn.style.opacity = '1';
    status.style.color = 'var(--red)';
    status.textContent = '❌ Update failed: ' + (err.message || 'Unknown error. Try again.');
    console.error('Update error:', err);
  }
}

// ── INIT ──
document.getElementById('mainFab').style.display = 'none';
setTxnType('expense');
const now = new Date(); viewMonth = now.getMonth(); viewYear = now.getFullYear();
reportMonth = now.getMonth(); reportYear = now.getFullYear();
renderHome();
</script>

</body>
</html>
