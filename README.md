<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>แดชบอร์ด ควิกโค้ท</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&family=IBM+Plex+Mono:wght@400;600&display=swap" rel="stylesheet">
<style>
:root {
  --bg:        #ffffff;
  --surface:   #f8f9fa;
  --surface2:  #f0f1f3;
  --border:    #e2e5e9;
  --accent:    #e07b1e;
  --accent2:   #2563eb;
  --green:     #16a34a;
  --red:       #dc2626;
  --yellow:    #d97706;
  --text:      #111827;
  --muted:     #6b7280;
  --rebate:    #16a34a;
  --font:      'Sarabun', sans-serif;
  --mono:      'IBM Plex Mono', monospace;
  --radius:    10px;
  --c65: #6366f1;
  --c66: #0ea5e9;
  --c67: #10b981;
  --c68: #e07b1e;
  --c69: #d97706;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: var(--font);
  background: var(--bg);
  color: var(--text);
  font-size: 14px;
  min-height: 100vh;
  overflow-x: hidden;
}
.topbar {
  position: sticky; top: 0; z-index: 100;
  background: rgba(255,255,255,0.97);
  backdrop-filter: blur(12px);
  border-bottom: 2px solid var(--border);
  padding: 0 16px;
  display: flex; align-items: center; justify-content: space-between;
  height: 52px;
  box-shadow: 0 1px 6px rgba(0,0,0,0.07);
}
.brand { font-size: 15px; font-weight: 700; letter-spacing: .5px; color: var(--accent); }
.brand span { color: var(--text); font-weight: 300; }
.nav-tabs { display: flex; gap: 4px; overflow-x: auto; scrollbar-width: none; }
.nav-tabs::-webkit-scrollbar { display: none; }
.tab-btn {
  white-space: nowrap; background: none; border: none;
  color: var(--muted); font-family: var(--font);
  font-size: 13px; font-weight: 600;
  padding: 6px 12px; border-radius: 20px;
  cursor: pointer; transition: all .2s;
}
.tab-btn.active, .tab-btn:hover { color: var(--text); background: var(--surface2); }
.tab-btn.active { color: var(--accent); }
.data-btn {
  white-space: nowrap;
  background: linear-gradient(135deg, #16a34a, #15803d);
  border: none;
  color: #fff;
  font-family: var(--font);
  font-size: 12px; font-weight: 700;
  padding: 5px 11px; border-radius: 20px;
  cursor: pointer; transition: all .2s;
  text-decoration: none;
  display: inline-flex; align-items: center; gap: 5px;
  letter-spacing: .3px;
  box-shadow: 0 1px 4px rgba(22,163,74,.35);
  flex-shrink: 0;
}
.data-btn:hover { background: linear-gradient(135deg, #15803d, #166534); box-shadow: 0 2px 8px rgba(22,163,74,.45); transform: translateY(-1px); }
.data-btn svg { width: 12px; height: 12px; flex-shrink: 0; }
.nav-right { display: flex; align-items: center; gap: 6px; }

main { padding: 16px; max-width: 900px; margin: 0 auto; }
.page { display: none; animation: fadeIn .25s ease; }
.page.active { display: block; }
@keyframes fadeIn { from { opacity:0; transform:translateY(6px) } to { opacity:1; transform:translateY(0) } }

.section-title {
  font-size: 12px; font-weight: 700;
  letter-spacing: 1.5px; text-transform: uppercase;
  color: var(--muted); margin: 22px 0 11px;
  display: flex; align-items: center; gap: 8px;
}
.section-title::after { content: ''; flex: 1; height: 1px; background: var(--border); }

.stat-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
  gap: 8px; margin-bottom: 16px;
}
.stat-card {
  background: var(--surface);
  border: 1.5px solid var(--border);
  border-radius: var(--radius);
  padding: 12px 11px;
  transition: border-color .2s, box-shadow .2s;
}
.stat-card:hover { border-color: var(--accent2); box-shadow: 0 2px 8px rgba(0,0,0,0.07); }
.stat-card .year-label { font-size: 11px; color: var(--muted); font-weight: 600; letter-spacing: 1px; margin-bottom: 5px; }
.stat-card .value { font-family: var(--mono); font-size: 15px; font-weight: 600; color: var(--text); line-height: 1.2; }
.stat-card .sub { font-size: 11px; color: var(--muted); margin-top: 3px; }
.stat-card .badge { font-size: 11px; font-weight: 600; padding: 2px 7px; border-radius: 20px; display: inline-block; margin-top: 5px; }
.badge.up   { background: rgba(22,163,74,.12); color: var(--green); }
.badge.down { background: rgba(220,38,38,.10); color: var(--red); }
.stat-card.highlight { border-color: var(--accent); }
.stat-card.highlight .value { color: var(--accent); }

/* ── BAR CHART ── */
.chart-wrap {
  background: var(--surface);
  border: 1.5px solid var(--border);
  border-radius: var(--radius);
  padding: 14px 12px 10px;
  margin-bottom: 16px;
  overflow-x: auto;
}
.chart-title { font-size: 12px; font-weight: 700; color: var(--muted); letter-spacing: 1px; text-transform: uppercase; margin-bottom: 14px; }
.chart-legend { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 12px; }
.legend-item { display: flex; align-items: center; gap: 5px; font-size: 11px; color: var(--muted); font-weight: 600; }
.legend-dot { width: 10px; height: 10px; border-radius: 2px; flex-shrink: 0; }
.bar-chart {
  display: flex;
  align-items: flex-end;
  gap: 12px;
  height: 260px;
  min-width: 260px;
  padding-top: 20px;
}.bar {
  width: 100%;
  max-width: 50px;
}
.bar-group { display: flex; flex-direction: column; justify-content: flex-end; align-items: center; flex: 1; height: 100%;}
.bar {
  width: 100%; border-radius: 5px 5px 0 0;
  transition: height .6s cubic-bezier(.4,0,.2,1), opacity .2s;
  min-height: 4px; cursor: pointer;
  position: relative;
}
.bar:hover { opacity: 0.82; }
.bar:hover::after {
  content: attr(data-tip);
  position: absolute; bottom: calc(100% + 6px); left: 50%; transform: translateX(-50%);
  background: #1f2937; border: 1px solid #374151;
  color: #fff; font-size: 11px; padding: 4px 8px;
  border-radius: 6px; white-space: nowrap; pointer-events: none; z-index: 10;
}
.bar-label { font-size: 11px; color: var(--muted); text-align: center; font-weight: 600; }
.bar-val   { font-size: 10px; color: var(--muted); font-family: var(--mono); }

/* ── TABLE ── */
.tbl-wrap {
  background: var(--surface);
  border: 1.5px solid var(--border);
  border-radius: var(--radius);
  overflow: auto; margin-bottom: 16px;
}
table { width: 100%; border-collapse: collapse; min-width: 340px; }
thead th {
  background: var(--surface2);
  color: var(--muted); font-size: 11px; font-weight: 700;
  letter-spacing: .8px; text-transform: uppercase;
  padding: 9px 11px; text-align: right; white-space: nowrap;
  border-bottom: 1.5px solid var(--border);
}
thead th:first-child { text-align: left; position: sticky; left: 0; background: var(--surface2); }
tbody td {
  padding: 8px 11px; border-bottom: 1px solid var(--border);
  font-family: var(--mono); font-size: 12px; text-align: right; white-space: nowrap;
}
tbody td:first-child {
  text-align: left; font-family: var(--font); font-size: 13px;
  position: sticky; left: 0; background: var(--surface);
  border-right: 1px solid var(--border);
}
tbody tr:last-child td { border-bottom: none; }
tbody tr:nth-child(even) td { background: rgba(0,0,0,.02); }
tbody tr:nth-child(even) td:first-child { background: rgba(0,0,0,.02); }
tbody tr.total-row td { background: var(--surface2) !important; font-weight: 700; color: var(--accent); }
.pct.pos { color: var(--green); }
.pct.neg { color: var(--red); }
.pct.neutral { color: var(--muted); }
.yr2569 { color: var(--yellow) !important; font-weight: 600; }
.highlight-cell { color: var(--accent) !important; font-weight: 700; }

/* ── REBATE ── */
.rebate-summary { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 16px; }
@media (min-width: 480px) { .rebate-summary { grid-template-columns: repeat(4,1fr); } }
.rebate-item {
  background: var(--surface); border: 1.5px solid rgba(22,163,74,.4);
  border-radius: var(--radius); padding: 12px;
}
.rebate-item .r-label { font-size: 11px; color: var(--muted); margin-bottom: 4px; line-height: 1.4; }
.rebate-item .r-val { font-family: var(--mono); font-size: 15px; font-weight: 700; color: var(--rebate); }
.rebate-item .r-pct { font-size: 11px; color: var(--muted); margin-top: 3px; }

/* ── NOTE ── */
.note {
  background: rgba(217,119,6,.07); border: 1px solid rgba(217,119,6,.3);
  border-radius: var(--radius); padding: 10px 14px;
  font-size: 12px; color: var(--yellow); margin-bottom: 14px;
  display: flex; align-items: flex-start; gap: 8px;
}
.note::before { content: '⚠'; flex-shrink: 0; margin-top: 1px; }

.page-title { font-size: 19px; font-weight: 700; margin-bottom: 3px; color: var(--text); }
.page-sub   { font-size: 12px; color: var(--muted); margin-bottom: 18px; }

footer {
  text-align: center; padding: 20px 16px;
  font-size: 11px; color: var(--muted);
  border-top: 1px solid var(--border); margin-top: 28px;
}

/* ── PRODUCT TABLE (page 2) ── */
.prod-tbl-wrap {
  background: var(--surface); border: 1.5px solid var(--border);
  border-radius: var(--radius); overflow: auto; margin-bottom: 16px;
}
.prod-tbl-wrap table { min-width: 480px; }
.prod-name-cell { font-size: 12px !important; font-family: var(--font) !important; max-width: 160px; white-space: normal !important; line-height: 1.3; }

/* ── 4-month mini-cards row on page 1 ── */
.four-month-strip {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 7px; margin-bottom: 16px;
}
.fm-card {
  background: var(--surface); border: 1.5px solid var(--border);
  border-radius: var(--radius); padding: 10px 9px; text-align: center;
}
.fm-card .fm-year { font-size: 11px; color: var(--muted); font-weight: 700; letter-spacing: .8px; margin-bottom: 4px; }
.fm-card .fm-val  { font-family: var(--mono); font-size: 13px; font-weight: 700; }
.fm-card .fm-badge { font-size: 10px; font-weight: 600; padding: 2px 6px; border-radius: 20px; display: inline-block; margin-top: 4px; }

@media (max-width: 480px) {
  .topbar { height: 48px; }
  .brand { font-size: 13px; }
  .tab-btn { font-size: 12px; padding: 5px 9px; }
  main { padding: 10px; }
  .stat-grid { grid-template-columns: repeat(2,1fr); gap: 7px; }
  .stat-card .value { font-size: 14px; }
  .page-title { font-size: 16px; }
  .bar-chart { height: 95px; }
  .four-month-strip { grid-template-columns: repeat(3,1fr); }
}
</style>
</head>
<body>
<div class="topbar">
  <div class="brand">QUICK<span>COAT</span></div>
  <nav class="nav-tabs" id="navTabs"></nav>
</div>
<div id="dataBanner" style="background:linear-gradient(90deg,#dcfce7,#bbf7d0); border-bottom:2px solid #86efac; padding:8px 16px; display:flex; align-items:center; justify-content:space-between; gap:10px;">
  <span style="font-size:12px; color:#15803d; font-weight:600;">📊 ดูข้อมูลดิบ สินค้า 4 เดือน ใน Google Sheets</span>
  <a href="https://docs.google.com/spreadsheets/d/1aKR6KmUGosext5SE1d92VF-CVEHeCJEFfM_IvHE6gzY/edit?gid=246191077#gid=246191077" target="_blank" rel="noopener" style="background:#16a34a;color:#fff;font-family:'Sarabun',sans-serif;font-size:12px;font-weight:700;padding:6px 14px;border-radius:20px;text-decoration:none;display:inline-flex;align-items:center;gap:5px;white-space:nowrap;box-shadow:0 1px 4px rgba(22,163,74,.4)">
    <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
    เปิด Google Sheet
  </a>
</div>
<main id="mainContent"></main>
<footer>ข้อมูล ณ เดือนเม.ย. 2569 &nbsp;|&nbsp; หน่วย: บาท (ไม่รวม VAT)</footer>
<script>
const YEARS = [2565,2566,2567,2568,2569];
const MN = ["ม.ค.","ก.พ.","มี.ค.","เม.ย.","พ.ค.","มิ.ย.","ก.ค.","ส.ค.","ก.ย.","ต.ค.","พ.ย.","ธ.ค."];
// ── สีประจำปี ──
const YR_COL = {2565:'#6366f1',2566:'#0ea5e9',2567:'#10b981',2568:'#e07b1e',2569:'#d97706'};

// ══════════════════════════════════════════════════════
// 🔗 วาง URL Apps Script ที่ Deploy แล้วตรงนี้
// ══════════════════════════════════════════════════════
const APPS_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbwr3t8eeAp3J7Dnmp0rDFqZE3peOj6tGENhmNH6IFHQ2RKdDSD6SnZx9CiUX3I12ZaY/exec";
// ══════════════════════════════════════════════════════

// ── ข้อมูล fallback (ใช้เมื่อยังไม่ได้ตั้งค่า URL) ──
let monthlyTotals = {
  2565:[703500,625593,863409,614327,515879,739565,644794,663112,425047,566514,604533,543785],
  2566:[566617,558166,977196,591037,764234,1045746,953428,975150,949402,940318,799625,848979],
  2567:[723411,1122234,1100079,1010138,796879,745794,1056028,714654,801964,818682,721019,564056],
  2568:[906022,502019,1210079,897671,857208,1495712,872465,836232,937942,1291463,954669,1072340],
  2569:[706159,830421,1068785,1249813,0,0,0,0,0,0,0,0],
};
let yearlyTotals = {2565:7510059,2566:9969898,2567:10174939,2568:11833822,2569:3855178};
let quarterlyTotals = {
  2565:[2192503,1869771,1732953,1714832],
  2566:[2101979,2401017,2877979,2588922],
  2567:[2945724,2552811,2572647,2103757],
  2568:[2618120,3250592,2646639,3318472],
  2569:[2605365,0,0,0],
};
let rebateSummary = {
  2567:{total:211245,pct:2.076},
  2568:{total:313191,pct:2.647},
  "2569_current":167309,
  "2569_proposed":310666,
};
let products = [
  {
    name:"ปูนก่ออิฐมวลเบา ตราจิงโจ้ ม่วง (40กก.)",
    monthly:{
      2565:[389369,319977,454907,299159,224280,320626,214276,287738,225047,230673,269252,188879],
      2566:[243533,261858,474206,341589,404280,441895,489316,482243,458935,501093,449438,453045],
      2567:[446075,577888,689678,499764,302206,502336,569850,393308,542245,511178,311850,330336],
      2568:[530769,281308,780706,532718,458671,935288,562617,556547,556707,809426,647652,682745],
      2569:[465364,583411,578692,707991,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[2525,2075,2950,1940,1420,2030,1350,1790,1400,1435,1675,1175],
      2566:[1515,1629,2950,2125,2515,2749,3044,3000,2855,3115,2792,2814],
      2567:[2775,3595,4290,3109,1880,3125,3545,2445,3380,3280,1980,2125],
      2568:[3315,1750,4853,3314,2849,5814,3500,3553,3557,5180,4055,4270],
      2569:[2895,3625,3600,4400,0,0,0,0,0,0,0,0],
    },
    rebate2567:53549, rebate2568:73352, targetRebate:1500000,
  },
  {
    name:"ปูนฉาบอิฐมวลเบา ตราลูกดิ่ง (แดง)",
    monthly:{
      2565:[178178,123766,216419,186224,181318,235388,171266,200607,117757,194720,199766,157710],
      2566:[165701,188832,301122,218607,225000,350579,232150,357393,314579,253430,263271,183785],
      2567:[182944,237617,285729,340654,433178,130374,197579,170411,122804,163766,254103,144000],
      2568:[174673,128187,221636,170748,291028,315000,246449,95888,195561,163598,113551,202626],
      2569:[109346,109346,313318,393224,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[2325,1615,2824,2430,2230,2895,2090,2385,1400,2315,2375,1875],
      2566:[1970,2245,3580,2599,2675,4168,2760,4249,3740,3009,3130,2185],
      2567:[2175,2825,3395,4050,5150,1550,2349,2025,1460,1995,3095,1750],
      2568:[2075,1524,2635,2030,3460,3745,2930,1140,2325,1945,1350,2415],
      2569:[1300,1300,3725,4675,0,0,0,0,0,0,0,0],
    },
    rebate2567:0, rebate2568:0, targetRebate:0,
  },
  {
    name:"ปูนฉาบผิวบาง ตราลูกดิ่ง (เหลือง)",
    monthly:{
      2565:[128944,167832,178065,128944,102804,168598,199439,174766,82243,133645,113084,174766],
      2566:[143925,92523,164486,30841,127477,215888,187103,113084,145981,160374,71963,174766],
      2567:[71963,269346,100748,139813,39065,113084,267290,113084,127477,121308,143103,82243],
      2568:[176000,92523,200262,174766,98692,207664,49346,154206,145981,267290,184224,135495],
      2569:[94579,113084,164486,133645,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[630,820,870,630,500,820,970,850,400,650,550,850],
      2566:[700,450,800,150,620,1050,910,550,710,780,350,850],
      2567:[350,1310,490,680,190,550,1300,550,620,590,700,400],
      2568:[870,450,974,850,480,1010,240,750,710,1300,902,670],
      2569:[462,550,800,650,0,0,0,0,0,0,0,0],
    },
    rebate2567:8673, rebate2568:8183, targetRebate:500000,
  },
  {
    name:"ปูนฉาบผิวบาง ตราลูกดิ่ง (เทา)",
    monthly:{
      2565:[7009,14019,14019,0,7477,14953,59813,0,0,7477,22430,22430],
      2566:[13458,14953,37383,0,7477,37383,44860,22430,29907,25421,14953,37383],
      2567:[22430,37383,23925,29907,22430,0,1495,32897,4486,22430,11963,7477],
      2568:[14953,0,7477,19439,4486,11963,0,17944,14953,37383,0,0],
      2569:[22430,14953,7477,14953,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[50,100,100,0,50,100,400,7,3,50,150,150],
      2566:[90,100,250,0,50,250,300,150,200,170,100,250],
      2567:[150,250,160,200,150,0,10,220,30,150,80,50],
      2568:[100,0,50,130,30,80,0,120,100,250,0,0],
      2569:[150,100,50,100,0,0,0,0,0,0,0,0],
    },
    rebate2567:0, rebate2568:0, targetRebate:0,
  },
  {
    name:"ปูนเทปรับระดับพื้น ตราจิงโจ้ น้ำเงิน (40กก.)",
    monthly:{
      2565:[0,0,0,0,0,0,0,0,0,0,0,0],
      2566:[0,0,0,0,0,0,0,0,0,0,0,0],
      2567:[0,0,0,0,0,0,19813,4953,4953,0,0,0],
      2568:[9626,0,0,0,4332,25798,14054,11648,24739,13765,9241,51474],
      2569:[14439,9626,4813,0,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[0,0,0,0,0,0,0,0,0,0,0,0],
      2566:[0,0,0,0,0,0,0,0,0,0,0,0],
      2567:[0,0,0,0,0,0,200,50,50,0,0,0],
      2568:[100,0,0,0,45,276,150,126,265,150,100,550],
      2569:[150,100,50,0,0,0,0,0,0,0,0,0],
    },
    rebate2567:0, rebate2568:0, targetRebate:0,
  },
  {
    name:"ปูนกาวกระเบื้อง จิงโจ้ เขียว 20กก.",
    monthly:{
      2565:[0,0,0,0,0,0,0,0,0,0,0,0],
      2566:[0,0,0,0,0,0,0,0,0,0,0,0],
      2567:[0,0,0,0,0,0,0,0,0,0,0,0],
      2568:[0,0,0,0,0,0,0,0,0,0,0,6893],
      2569:[0,0,0,0,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[0,0,6,8,4,10,20,0,0,8,8,18],
      2566:[12,4,10,2,8,22,22,4,12,8,2,18],
      2567:[6,20,4,12,4,8,16,8,13,0,0,0],
      2568:[0,0,0,0,0,0,0,0,0,0,0,60],
      2569:[0,0,0,0,0,0,0,0,0,0,0,0],
    },
    rebate2567:0, rebate2568:0, targetRebate:0,
  },
  {
    name:"ปูนเทปรับระดับพื้น ตราจิงโจ้ น้ำตาล (40กก.)",
    monthly:{
      2565:[0,0,0,0,0,0,0,0,0,0,0,0],
      2566:[0,0,0,0,0,0,0,0,0,0,0,0],
      2567:[0,0,0,0,0,0,0,0,0,0,0,0],
      2568:[0,0,0,0,15327,1533,0,0,0,0,0,3065],
      2569:[0,0,0,0,0,0,0,0,0,0,0,0],
    },
    bags:{
      2565:[0,0,0,0,0,0,0,0,0,0,0,0],
      2566:[0,0,0,0,0,0,0,0,0,0,0,0],
      2567:[0,0,0,0,0,0,0,0,0,0,0,0],
      2568:[0,0,0,0,200,20,0,0,0,0,0,40],
      2569:[0,0,0,0,0,0,0,0,0,0,0,0],
    },
    rebate2567:0, rebate2568:0, targetRebate:0,
  },
];

// ── HELPERS ──
const fmt  = (n) => (n && n!==0) ? n.toLocaleString('th-TH',{maximumFractionDigits:0}) : '–';
const fmtM = (n) => {
  if(!n) return '–';
  if(n>=1e6) return (n/1e6).toFixed(2)+'M';
  if(n>=1e3) return (n/1e3).toFixed(0)+'K';
  return n.toLocaleString('th-TH',{maximumFractionDigits:0});
};
const pctStr = (a,b) => {
  if(!a) return '<span class="pct neutral">–</span>';
  const p = ((b-a)/a)*100;
  const cls = p>0?'pos':'neg';
  return `<span class="pct ${cls}">${p>0?'+':''}${p.toFixed(1)}%</span>`;
};
const pChange = (a,b) => a ? ((b-a)/a) : null;

// ── PAGE 1 — ภาพรวม ──
function buildPage1() {
  // Yearly stat cards
  let yearCards = YEARS.map(y => {
    const v = yearlyTotals[y];
    const prev = yearlyTotals[y-1];
    const chg = prev ? pChange(prev,v) : null;
    const col = YR_COL[y];
    const badge = (y===2569)
      ? `<span class="badge" style="background:rgba(217,119,6,.12);color:#d97706">4 เดือน</span>`
      : (chg!==null ? `<span class="badge ${chg>=0?'up':'down'}">${chg>=0?'+':''}${(chg*100).toFixed(1)}%</span>` : '');
    return `<div class="stat-card" style="${y===2568?'border-color:'+col:''}">
      <div class="year-label" style="color:${col}">ปี ${y}</div>
      <div class="value" style="color:${col}">${fmtM(v)}</div>
      <div class="sub">บาท</div>
      ${badge}
    </div>`;
  }).join('');

  // Yearly bar chart with per-year colors
  const legend = YEARS.map(y=>`
    <div class="legend-item">
      <div class="legend-dot" style="background:${YR_COL[y]}"></div>
      <span>ปี ${y}${y===2569?' (4 เดือน)':''}</span>
    </div>`).join('');

  const yBarData = YEARS.map(y=>yearlyTotals[y]);
  const yBarMax = Math.max(...yBarData);
  const yBars = yBarData.map((v,i)=>{
    const h = Math.max(3, Math.round((v/yBarMax)*100));
    const y = YEARS[i];
    const col = YR_COL[y];
    const note = y===2569 ? ' (4 เดือน)' : '';
    return `<div class="bar-group">
      <div class="bar" style="height:${h}%;background:${col}" data-tip="ปี ${y}: ${fmtM(v)}${note}"></div>
      <div class="bar-label" style="color:${col}">'${String(y).slice(2)}</div>
      <div class="bar-val">${fmtM(v)}</div>
    </div>`;
  }).join('');

  // ── ยอดซื้อ ม.ค.-เม.ย. mini strip (จาก page 2) ──
  const four = y => monthlyTotals[y].slice(0,4).reduce((a,b)=>a+b,0);
  const f4 = {}; YEARS.forEach(y=>f4[y]=four(y));
  const fmStrip = YEARS.map(y=>{
    const v=f4[y]; const prev=f4[y-1];
    const chg=prev?pChange(prev,v):null;
    const col=YR_COL[y];
    const badge = chg!==null
      ? `<span class="fm-badge ${chg>=0?'up':'down'}">${chg>=0?'+':''}${(chg*100).toFixed(1)}%</span>`
      : '';
    return `<div class="fm-card" style="${y===2569?'border-color:'+col:''}">
      <div class="fm-year" style="color:${col}">ปี ${y}</div>
      <div class="fm-val" style="color:${col}">${fmtM(v)}</div>
      ${badge}
    </div>`;
  }).join('');

  // ── รายไตรมาส ──
  let qRows = '';
  for(let q=0;q<4;q++){
    const cells = YEARS.map(y=>{
      const v=quarterlyTotals[y][q];
      const isSkip = y===2569 && q>0;
      const isCur  = y===2569 && q===0;
      return `<td class="${isCur?'yr2569':''}">${isSkip?'–':fmtM(v)}</td>`;
    }).join('');
    const c68=quarterlyTotals[2568][q], c69=q===0?quarterlyTotals[2569][0]:null;
    const chgCol = (q===0 && c69) ? `<td>${pctStr(c68,c69)}</td>` : `<td><span class="pct neutral">–</span></td>`;
    qRows += `<tr><td>Q${q+1}</td>${cells}${chgCol}</tr>`;
  }
  const yCellsQ = YEARS.map(y=>`<td class="highlight-cell">${fmtM(y===2569?quarterlyTotals[2569][0]:yearlyTotals[y])}</td>`).join('');
  qRows += `<tr class="total-row"><td>รวม</td>${yCellsQ}<td>–</td></tr>`;

  // ── รายเดือน ──
  let mRows = '';
  for(let m=0;m<12;m++){
    const cells = YEARS.map(y=>{
      const v=monthlyTotals[y][m];
      const skip=y===2569&&m>=4;
      return `<td class="${y===2569&&m<4?'yr2569':''}">${skip?'–':fmtM(v)}</td>`;
    }).join('');
    const v68=monthlyTotals[2568][m], v69=monthlyTotals[2569][m];
    const chg69 = m<4 ? pctStr(v68,v69) : '<span class="pct neutral">–</span>';
    mRows+=`<tr><td>${MN[m]}</td>${cells}<td>${chg69}</td></tr>`;
  }
  mRows+=`<tr class="total-row"><td>รวม</td>${YEARS.map(y=>`<td>${fmtM(yearlyTotals[y])}</td>`).join('')}<td>–</td></tr>`;

  // ── สรุปรีเบท ──
  const rebateItems = [
    {label:'รีเบทปี 2567', val:rebateSummary[2567].total, pct:rebateSummary[2567].pct},
    {label:'รีเบทปี 2568', val:rebateSummary[2568].total, pct:rebateSummary[2568].pct},
    {label:'รีเบท 2569 ที่คาดว่าทำได้จริง', val:rebateSummary['2569_current'], pct:null},
    {label:'รีเบท 2569 (ที่กำลังขอพิจารณา)', val:rebateSummary['2569_proposed'], pct:null},
  ];
  const rebCards = rebateItems.map(ri=>`
    <div class="rebate-item">
      <div class="r-label">${ri.label}</div>
      <div class="r-val">${fmtM(ri.val)}</div>
      ${ri.pct?`<div class="r-pct">${ri.pct.toFixed(2)}% ของยอดซื้อ</div>`:''}
    </div>`).join('');

  return `
  <div class="page-title">แดชบอร์ด ควิกโค้ท</div>
  <div class="page-sub">ยอดซื้อรวมทุกรายการ ปี 2565–2569</div>

  <div class="section-title">ยอดรวมรายปี</div>
  <div class="stat-grid">${yearCards}</div>

  <div class="section-title">ยอดซื้อ ม.ค.–เม.ย. เทียบทุกปี</div>
  <div class="four-month-strip">${fmStrip}</div>

  <div class="section-title">รายไตรมาส</div>
  <div class="note">ปี 2569: Q1 = ม.ค.–มี.ค. เท่านั้น (ไม่รวมเม.ย.)</div>
  <div class="tbl-wrap"><table>
    <thead><tr><th>ไตรมาส</th>${YEARS.map(y=>`<th class="${y===2569?'yr2569':''}">${y}</th>`).join('')}<th>68→69</th></tr></thead>
    <tbody>${qRows}</tbody>
  </table></div>

  <div class="section-title">รายเดือน</div>
  <div class="tbl-wrap"><table>
    <thead><tr><th>เดือน</th>${YEARS.map(y=>`<th class="${y===2569?'yr2569':''}">${y}</th>`).join('')}<th>68→69</th></tr></thead>
    <tbody>${mRows}</tbody>
  </table></div>

  <div class="section-title">สรุปรีเบท</div>
  <div class="rebate-summary">${rebCards}</div>
  `;
}

// ── PAGE 2 — รายการสินค้า ม.ค.–เม.ย. ทุกปี ──
function buildPage2() {
  // สร้างตารางรายสินค้า แต่ละปี ม.ค.-เม.ย.
  const prodRows = products.map(p => {
    // คำนวณ bags+amt สำหรับแต่ละปี ม.ค.-เม.ย.
    const data = YEARS.map(y => ({
      bags: p.bags[y].slice(0,4).reduce((a,b)=>a+b,0),
      amt:  p.monthly[y].slice(0,4).reduce((a,b)=>a+b,0),
    }));
    // ถ้าทุกปีไม่มีข้อมูลเลย ข้าม
    if(data.every(d=>d.bags===0 && d.amt===0)) return '';

    return `<tr>
      <td class="prod-name-cell">${p.name}</td>
      ${data.map((d,i)=>{
        const y=YEARS[i];
        const noData = d.bags===0 && d.amt===0;
        return `<td style="text-align:center;vertical-align:top;padding:7px 8px">
          ${noData ? '<span style="color:#ccc">–</span>' : `
            <div style="font-family:var(--mono);font-size:11px;font-weight:700;color:${YR_COL[y]}">${fmt(d.bags)} ถุง</div>
            <div style="font-family:var(--mono);font-size:11px;color:#555;margin-top:2px">${fmtM(d.amt)}</div>
          `}
        </td>`;
      }).join('')}
    </tr>`;
  }).filter(Boolean).join('');

  // แถวรวม
  const totalRow = YEARS.map(y=>{
    const bags = products.reduce((s,p)=>s+p.bags[y].slice(0,4).reduce((a,b)=>a+b,0),0);
    const amt  = products.reduce((s,p)=>s+p.monthly[y].slice(0,4).reduce((a,b)=>a+b,0),0);
    return `<td style="text-align:center;padding:7px 8px">
      <div style="font-family:var(--mono);font-size:11px;font-weight:700;color:${YR_COL[y]}">${fmt(bags)} ถุง</div>
      <div style="font-family:var(--mono);font-size:11px;color:#555;margin-top:2px">${fmtM(amt)}</div>
    </td>`;
  }).join('');

  // ตาราง ม.ค.-เม.ย. รายเดือน เทียบทุกปี (จาก page 2 เดิม)
  const four = y => monthlyTotals[y].slice(0,4).reduce((a,b)=>a+b,0);
  const f4 = {}; YEARS.forEach(y=>f4[y]=four(y));

  let mRows='';
  for(let m=0;m<4;m++){
    const cells=YEARS.map(y=>`<td class="${y===2569?'yr2569':''}">${fmtM(monthlyTotals[y][m])}</td>`).join('');
    const v68=monthlyTotals[2568][m],v69=monthlyTotals[2569][m];
    mRows+=`<tr><td>${MN[m]}</td>${cells}<td>${pctStr(v68,v69)}</td></tr>`;
  }
  mRows+=`<tr class="total-row"><td>รวม</td>${YEARS.map(y=>`<td>${fmtM(f4[y])}</td>`).join('')}<td>${pctStr(f4[2568],f4[2569])}</td></tr>`;

  // bar chart ม.ค.-เม.ย.
const f4Vals = YEARS.map(y => f4[y]);
const f4Max  = Math.max(...f4Vals);
const f4Min  = Math.min(...f4Vals.filter(v => v > 0));
const range  = f4Max - f4Min || 1;
  const legend = YEARS.map(y=>`
    <div class="legend-item">
      <div class="legend-dot" style="background:${YR_COL[y]}"></div><span>ปี ${y}</span>
    </div>`).join('');
  const barsH=f4Vals.map((v,i)=>{
   const h = ((v - f4Min) / range) * 220 + 25;
    const y=YEARS[i];
    return `<div class="bar-group">
      <div class="bar" style="height:${h}%;background:${YR_COL[y]}" data-tip="ปี ${y}: ${fmtM(v)}"></div>
      <div class="bar-label" style="color:${YR_COL[y]}">'${String(y).slice(2)}</div>
      <div class="bar-val">${fmtM(v)}</div>
    </div>`;
  }).join('');

  return `
  <div class="page-title">รายการสินค้า ม.ค.–เม.ย.</div>
  <div class="page-sub">จำนวนถุง และยอดซื้อ (บาท) เดือน 1–4 แยกตามสินค้าและปี</div>

  <div class="chart-wrap">
    <div class="chart-title">ยอดซื้อ ม.ค.–เม.ย. รายปี (บาท)</div>
    <div class="chart-legend">${legend}</div>
    <div class="bar-chart">${barsH}</div>
  </div>

  <div class="section-title">เทียบรายเดือน (ม.ค.–เม.ย.)</div>
  <div class="tbl-wrap"><table>
    <thead><tr><th>เดือน</th>${YEARS.map(y=>`<th class="${y===2569?'yr2569':''}">${y}</th>`).join('')}<th>68→69 ⭐</th></tr></thead>
    <tbody>${mRows}</tbody>
  </table></div>

  <div class="section-title">รายการสินค้า ม.ค.–เม.ย. ทุกปี</div>
  <div class="note">แถวละสินค้า — แสดงจำนวนถุง (บน) และยอดซื้อบาท (ล่าง) เฉพาะเดือน 1–4</div>
  <div class="prod-tbl-wrap">
    <table>
      <thead>
        <tr>
          <th style="min-width:150px">สินค้า</th>
          ${YEARS.map(y=>`<th style="text-align:center;color:${YR_COL[y]}">${y}</th>`).join('')}
        </tr>
      </thead>
      <tbody>
        ${prodRows}
        <tr class="total-row">
          <td>รวมทั้งหมด</td>
          ${totalRow}
        </tr>
      </tbody>
    </table>
  </div>
  `;
}

// ── ROUTER ──
const pages = [
  { id:'p0', label:'ภาพรวม',      build: buildPage1 },
  { id:'p1', label:'สินค้า 4 เดือน', build: buildPage2 },
];

const navTabs    = document.getElementById('navTabs');
const mainContent= document.getElementById('mainContent');

pages.forEach((pg,i)=>{
  const btn = document.createElement('button');
  btn.className = 'tab-btn' + (i===0?' active':'');
  btn.textContent = pg.label;
  btn.onclick = ()=> showPage(i);
  navTabs.appendChild(btn);
  const div = document.createElement('div');
  div.className = 'page' + (i===0?' active':'');
  div.id = pg.id;
  mainContent.appendChild(div);
});

let rendered = {};
function showPage(idx) {
  document.querySelectorAll('.tab-btn').forEach((b,i)=>b.classList.toggle('active',i===idx));
  document.querySelectorAll('.page').forEach((d,i)=>d.classList.toggle('active',i===idx));
  if(!rendered[idx]){
    document.getElementById(pages[idx].id).innerHTML = pages[idx].build();
    rendered[idx]=true;
  }
  window.scrollTo({top:0,behavior:'smooth'});
}
// ── FETCH จาก Google Apps Script ──
async function loadFromSheet() {
  if (!APPS_SCRIPT_URL || APPS_SCRIPT_URL === "YOUR_APPS_SCRIPT_URL_HERE") {
    // ยังไม่ตั้งค่า URL → ใช้ข้อมูล fallback
    showPage(0);
    return;
  }

  // แสดง loading
  document.getElementById('mainContent').innerHTML = `
    <div style="text-align:center;padding:60px 20px;color:#6b7280">
      <div style="font-size:28px;margin-bottom:12px">⏳</div>
      <div style="font-size:14px;font-weight:600">กำลังโหลดข้อมูลจาก Google Sheets…</div>
    </div>`;

  try {
    const res = await fetch(APPS_SCRIPT_URL);
    const d = await res.json();
    if (d.error) throw new Error(d.error);

    // อัพเดทตัวแปรทั้งหมด
    monthlyTotals   = d.monthlyTotals;
    yearlyTotals    = d.yearlyTotals;
    quarterlyTotals = d.quarterlyTotals;
    rebateSummary   = d.rebateSummary;
    products        = d.products;

    // แปลง key string → number ให้ทุก object
    const fixKeys = (obj) => {
      if (!obj || typeof obj !== 'object') return obj;
      [2565,2566,2567,2568,2569].forEach(y => {
        if (obj[String(y)] !== undefined) obj[y] = obj[String(y)];
      });
      return obj;
    };

    monthlyTotals   = fixKeys(d.monthlyTotals)   || monthlyTotals;
    yearlyTotals    = fixKeys(d.yearlyTotals)     || yearlyTotals;
    rebateSummary   = fixKeys(d.rebateSummary)    || rebateSummary;
    if (rebateSummary[2567]) fixKeys(rebateSummary[2567]);
    if (rebateSummary[2568]) fixKeys(rebateSummary[2568]);

    // คำนวณ quarterlyTotals จาก monthlyTotals (Script ส่งมาว่าง)
    quarterlyTotals = {};
    [2565,2566,2567,2568,2569].forEach(y => {
      const m = monthlyTotals[y] || new Array(12).fill(0);
      quarterlyTotals[y] = [
        m[0]+m[1]+m[2],
        m[3]+m[4]+m[5],
        m[6]+m[7]+m[8],
        m[9]+m[10]+m[11],
      ];
    });

    // แก้ products — fix keys และคำนวณ yearlyTotals จาก monthly ถ้าหาย
    products = (d.products || products).map(p => {
      fixKeys(p.monthly); fixKeys(p.bags);
      // ตรวจว่า array ยาว 12 หรือเปล่า ถ้าไม่ครบให้ตัดแค่ 12
      [2565,2566,2567,2568,2569].forEach(y => {
        if (p.monthly[y]) p.monthly[y] = p.monthly[y].slice(0,12).map(v=>v||0);
        if (p.bags[y])    p.bags[y]    = p.bags[y].slice(0,12).map(v=>v||0);
        // เติมให้ครบ 12
        while((p.monthly[y]||[]).length < 12) p.monthly[y].push(0);
        while((p.bags[y]||[]).length < 12)    p.bags[y].push(0);
      });
      return p;
    });

    // อัพเดท footer ด้วยเวลาล่าสุด
    if (d.updatedAt) {
      const dt = new Date(d.updatedAt);
      const ts = dt.toLocaleString('th-TH',{timeZone:'Asia/Bangkok',hour12:false});
      document.querySelector('footer').innerHTML =
        `ดึงข้อมูลจาก Google Sheets &nbsp;|&nbsp; อัพเดทล่าสุด: ${ts} &nbsp;|&nbsp; หน่วย: บาท (ไม่รวม VAT)`;
    }

  } catch (err) {
    console.warn('ดึงข้อมูลไม่ได้ ใช้ข้อมูลสำรองแทน:', err);
    document.getElementById('mainContent').innerHTML = `
      <div style="text-align:center;padding:40px 20px;color:#d97706">
        <div style="font-size:22px;margin-bottom:8px">⚠️</div>
        <div style="font-size:13px;font-weight:600">เชื่อมต่อ Google Sheets ไม่ได้ — แสดงข้อมูลสำรอง</div>
      </div>`;
    await new Promise(r => setTimeout(r, 1500));
  }

  // rebuild page divs (เพราะ innerHTML ถูก clear ระหว่าง loading)
  const mc = document.getElementById('mainContent');
  mc.innerHTML = '';
  rendered = {};
  pages.forEach((pg, i) => {
    const div = document.createElement('div');
    div.className = 'page' + (i===0?' active':'');
    div.id = pg.id;
    mc.appendChild(div);
  });

  showPage(0);
}

loadFromSheet();
</script>
</body>
</html>
