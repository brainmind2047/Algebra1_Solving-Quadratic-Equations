<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Solving Quadratic Equations</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }

  /* v4 celebration */
  .v4conf{position:fixed;inset:0;width:100vw;height:100vh;pointer-events:none;z-index:9999;}
  .v4ban{background:linear-gradient(135deg,var(--gold-soft),var(--card));border:2px solid var(--gold);border-radius:18px;padding:18px 14px 16px;margin:-4px 0 18px;text-align:center;animation:v4pop .55s cubic-bezier(.2,1.6,.4,1);}
  @keyframes v4pop{0%{transform:scale(.6);opacity:0}100%{transform:scale(1);opacity:1}}
  .v4trophy{font-size:54px;line-height:1;animation:v4bob 1.4s ease-in-out infinite;}
  @keyframes v4bob{0%,100%{transform:translateY(0) rotate(-6deg)}50%{transform:translateY(-6px) rotate(6deg)}}
  .v4h{font-size:28px;font-weight:800;color:var(--accent-text);margin-top:6px;}
  .v4m{font-size:19px;color:var(--ink);margin-top:4px;}
  .v4pills{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-top:12px;}
  .v4p{font-size:16px;font-weight:700;border-radius:999px;padding:6px 12px;}
  .v4p.g{background:var(--success-soft);color:var(--success);} .v4p.o{background:var(--gold-soft);color:var(--retry-text);}
  .v4p.r{background:var(--danger-soft);color:var(--danger);} .v4p.s{background:var(--rule);color:var(--ink);}
  .v4next{margin-top:14px;} .v4go{font-size:18px !important;padding:13px 20px !important;}
  .v4rec td.v4g{color:var(--success);font-weight:700;} .v4rec td.v4o{color:var(--retry-text);font-weight:700;} .v4rec td.v4r{color:var(--danger);font-weight:700;}
  .v4rec tr.v4tot td{font-weight:800;border-top:2px solid var(--rule);}
  .v4rec th{font-size:12.5px;padding:6px 3px !important;white-space:nowrap;} .v4rec td{font-size:15px;padding:7px 3px !important;text-align:center;}
  .v4rec td:first-child,.v4rec th:first-child{text-align:left;white-space:normal;min-width:92px;max-width:150px;font-size:14.5px;}
  @media(max-width:460px){ .v4left{display:none;} }
  .v4leg{font-size:14.5px;color:var(--ink-soft);margin:2px 0 8px;line-height:1.5;}
  body.v4done .fab-q,body.v4done #qFab{display:none;}
  .v4sum{font-size:16px;margin-top:10px;}
  /* v4 larger reading sizes */
  body{font-size:18px;}
  .chapter-title{font-size:38px !important;line-height:1.15;}
  .chapter-sub{font-size:17px !important;}
  .tab-btn{font-size:16.5px !important;}
  .sec-sub{font-size:16.5px !important;}
  .qtext{font-size:21px !important;line-height:1.6 !important;}
  .qnum{width:38px !important;height:38px !important;font-size:17px !important;}
  .opt{font-size:19.5px !important;padding:13px 15px !important;}
  .step-line{font-size:19.5px !important;line-height:2.1 !important;}
  .blank-input{font-size:18px !important;min-height:40px;}
  .sol-line{font-size:18px !important;line-height:1.6;}
  .feedback{font-size:16.5px !important;}
  .note h2{font-size:29px !important;}
  .note h3{font-size:22px !important;}
  .note h4{font-size:20px !important;}
  .note p,.note li,.note td,.note th{font-size:18.5px !important;line-height:1.7 !important;}
  .ex .exh{font-size:19px !important;} .ex .exl{font-size:18px !important;}
  .keybox{font-size:18px !important;}
  .hub-card p{font-size:17.5px !important;} .hub-btn{font-size:16.5px !important;}
  .review-q,.review-ans{font-size:17.5px !important;}
  .rec-table td{font-size:16px;}
  .vkb-k{font-size:19px !important;}
  .fq{font-size:0.95em;}
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Algebra 1 · Chapter 9</div>
  <div class="chapter-title">Solving Quadratic Equations</div>
  <div class="chapter-sub">Theory Notes · Practice by Section · Learning Assessment</div><div class="chapter-credit">Follows the sections of Big Ideas Math Algebra 1, Chapter 9</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Algebra 1 · Chapter 9<br>Lessons follow the chapter and section structure of <i>Big Ideas Math Algebra 1</i> (2015), Chapter 9. Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^[a-z]=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every section of the chapter, with rules in boxes, graphs, common mistakes and worked examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n91\">9.1 notes</button><button class=\"hub-btn\" data-jump=\"n92\">9.2 notes</button><button class=\"hub-btn\" data-jump=\"n93\">9.3 notes</button><button class=\"hub-btn\" data-jump=\"n94\">9.4 notes</button><button class=\"hub-btn\" data-jump=\"n95\">9.5 notes</button><button class=\"hub-btn\" data-jump=\"n96\">9.6 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by section</h3><p>One practice sheet for each section, easy to hard, mixing multiple-choice and fill-in-the-blank questions, with real-life problems and error-analysis items.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">9.1 · Properties of Radicals</button><button class=\"hub-btn\" data-go=\"s2\">9.2 · Solving Quadratic Equations by Graphing</button><button class=\"hub-btn\" data-go=\"s3\">9.3 · Solving Quadratic Equations Using Square Roots</button><button class=\"hub-btn\" data-go=\"s4\">9.4 · Solving Quadratic Equations by Completing the Square</button><button class=\"hub-btn\" data-go=\"s5\">9.5 · Solving Quadratic Equations Using the Quadratic Formula</button><button class=\"hub-btn\" data-go=\"s6\">9.6 · Solving Nonlinear Systems of Equations</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments mixing all six sections, one per skill area. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s7\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s8\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s9\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s10\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>A <b>quadratic equation</b> can be written as <b>ax² + bx + c = 0</b> with a ≠ 0. Its solutions are the <b>x-intercepts</b> (zeros) of the graph of y = ax² + bx + c. In this chapter you meet five ways to find them: graphing, square roots, completing the square, the Quadratic Formula and (from Chapter 7) factoring. Many solutions are irrational, so the chapter starts with the rules for simplifying square roots. It ends with systems in which a line meets a parabola.</p><h4>Maintaining mathematical proficiency</h4><p>These skills from earlier chapters are used throughout. Check that each example makes sense before you start 9.1.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Skill</th><th>Key idea</th><th>Example</th></tr><tr><td>Perfect squares and square roots</td><td>√n is the non-negative number whose square is n.</td><td class=\"mono\">√81 = 9 ; √0.25 = 0.5 ; 13² = 169</td></tr><tr><td>Factoring x² + bx + c</td><td>Find two numbers with product c and sum b.</td><td class=\"mono\">x² − x − 12 = (x − 4)(x + 3)</td></tr><tr><td>Zero-Product Property</td><td>If ab = 0, then a = 0 or b = 0.</td><td class=\"mono\">(x − 4)(x + 3) = 0 → x = 4 or −3</td></tr><tr><td>Graphing y = ax² + bx + c</td><td>Axis of symmetry x = −b ÷ (2a); the vertex lies on it.</td><td class=\"mono\">y = x² − 4x + 1: axis x = 2, vertex (2, −3)</td></tr><tr><td>Solving a linear system by substitution</td><td>Replace one variable with an equal expression.</td><td class=\"mono\">y = 2x, x + y = 9 → 3x = 9, (3, 6)</td></tr></table></div><div class=\"ex\"><div class=\"exh\">Warm-up example · Solve x² + 2x − 15 = 0 by factoring</div><div class=\"exl\">Two numbers with product −15 and sum 2: 5 and −3.<br>(x + 5)(x − 3) = 0.<br><b>x = −5 or x = 3</b>.</div></div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Sheet</th><th>Section</th><th>Learning target</th></tr><tr><td>9.1</td><td>Properties of Radicals</td><td>I can use the Product and Quotient Properties of Square Roots to simplify radicals, rationalize denominators, and add, subtract and multiply radical expressions.</td></tr><tr><td>9.2</td><td>Solving Quadratic Equations by Graphing</td><td>I can solve a quadratic equation by graphing, find the zeros of a quadratic function, and estimate solutions that are not integers.</td></tr><tr><td>9.3</td><td>Solving Quadratic Equations Using Square Roots</td><td>I can solve equations of the form ax² + c = 0 and a(x − h)² = k by taking square roots, and approximate the solutions.</td></tr><tr><td>9.4</td><td>Solving Quadratic Equations by Completing the Square</td><td>I can complete the square, solve quadratic equations by completing the square, and use it to write a quadratic function in vertex form.</td></tr><tr><td>9.5</td><td>Solving Quadratic Equations Using the Quadratic Formula</td><td>I can solve any quadratic equation with the Quadratic Formula, use the discriminant to count real solutions, and choose an efficient method.</td></tr><tr><td>9.6</td><td>Solving Nonlinear Systems of Equations</td><td>I can solve a system of a linear and a quadratic equation (or two quadratics) by graphing, substitution or elimination.</td></tr></table></div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Simplifying radicals and solving quadratics by each method.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>How solutions and radicals change as the numbers change.</td></tr><tr><td>C</td><td>Communicating</td><td>Vocabulary, notation, explaining steps, spotting and correcting errors.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Falling objects, areas, profit and paths, and whether answers make sense.</td></tr></table></div><p><b>Tools:</b> ⏱ at the top times each tab (pause or reset it). ✏️ opens a scratchpad for rough work. Some questions have a 🧮 calculator or 📈 Desmos button. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> type square roots with the √ key (or the word <span class=\"mono\">sqrt</span>), e.g. <span class=\"mono\">3√5</span>, <span class=\"mono\">2+√7</span> or <span class=\"mono\">(-3+√13)/2</span>; any equivalent exact form is accepted. When a question says <i>simplest form a√b</i>, type the number in front and the number under the root in separate boxes. Round decimals as the question says. For a list of integer solutions type them with a comma, e.g. <span class=\"mono\">-2, 5</span>; type a point as <span class=\"mono\">(3, -1)</span>.</p></section><section class=\"note\" id=\"n91\"><h2>9.1 Properties of Radicals</h2><p class=\"lt\"><b>Learning target:</b> I can use the Product and Quotient Properties of Square Roots to simplify radicals, rationalize denominators, and add, subtract and multiply radical expressions.</p><h4>Key vocabulary</h4><ul><li><b>Radical expression:</b> an expression that contains a radical, such as √12 or 3 + ∛x.</li><li><b>Simplest form</b> of a radical: no perfect-square factor (other than 1) under the √, no fraction under the √, and no radical in a denominator.</li><li><b>Rationalizing the denominator:</b> rewriting a fraction so its denominator has no radical.</li><li><b>Conjugates:</b> a + √b and a − √b. Their product a² − b has no radical.</li><li><b>Like radicals:</b> radicals with the same index and the same radicand, such as 4√3 and −√3.</li></ul><h4>Properties of square roots (a, b ≥ 0)</h4><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Property</th><th>Rule</th><th>Example</th></tr><tr><td>Product Property</td><td class=\"mono\">√(ab) = √a · √b</td><td class=\"mono\">√48 = √16 · √3 = 4√3</td></tr><tr><td>Quotient Property (b ≠ 0)</td><td class=\"mono\">√(a/b) = √a / √b</td><td class=\"mono\">√(5/9) = √5 / 3</td></tr><tr><td>Cube roots</td><td class=\"mono\">∛(ab) = ∛a · ∛b</td><td class=\"mono\">∛40 = ∛8 · ∛5 = 2∛5</td></tr></table></div><p>To simplify √n, split n into a product with the <b>largest perfect square</b> you can find (4, 9, 16, 25, 36, 49, 64, 81, 100, …). For variables, √(x²) = x when x ≥ 0, so √(x³) = x√x.</p><div class=\"ex\"><div class=\"exh\">Worked example 1 · Product Property</div><div class=\"exl\">Simplify √200.<br>200 = 100 · 2, and 100 is a perfect square.<br>√200 = √100 · √2 = <b>10√2</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 2 · Rationalize a denominator</div><div class=\"exl\">Simplify 6 / √8.<br>First √8 = 2√2, so 6 / √8 = 3 / √2.<br>Multiply by √2 / √2: <b>3√2 / 2</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 3 · Use the conjugate</div><div class=\"exl\">Simplify 2 / (√7 + √5).<br>Multiply top and bottom by √7 − √5: the denominator becomes 7 − 5 = 2.<br>2(√7 − √5) / 2 = <b>√7 − √5</b>.</div></div><h4>Adding, subtracting and multiplying</h4><p>Add or subtract <b>like radicals</b> by combining their coefficients, exactly as with like terms: 5√2 + 3√2 = 8√2. Simplify each radical first, because some radicals only become “like” after simplifying. Multiply radicals with the Product Property and the Distributive Property (or FOIL).</p><div class=\"ex\"><div class=\"exh\">Worked example 4 · Simplify first, then combine</div><div class=\"exl\">Simplify √75 − 2√3 + √12.<br>√75 = 5√3 and √12 = 2√3.<br>5√3 − 2√3 + 2√3 = <b>5√3</b>.</div></div><div class=\"keybox\"><b>Common mistake.</b> There is no “sum property”: √(a + b) is <b>not</b> √a + √b. For example √(16 + 9) = √25 = 5, but √16 + √9 = 7. Also, √2 + √3 cannot be combined, because the radicands differ.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 9.1 →</button></div></section><section class=\"note\" id=\"n92\"><h2>9.2 Solving Quadratic Equations by Graphing</h2><p class=\"lt\"><b>Learning target:</b> I can solve a quadratic equation by graphing, find the zeros of a quadratic function, and estimate solutions that are not integers.</p><p>A <b>quadratic equation</b> in <b>standard form</b> is ax² + bx + c = 0 (a ≠ 0). The solutions of the equation are the x-intercepts of the graph of y = ax² + bx + c. They are also called the <b>zeros</b> of the function f(x) = ax² + bx + c, because f(x) = 0 there; an x-value where f(x) = 0 is also called a <b>root</b> of the equation.</p><div class=\"keybox\"><b>Solving ax² + bx + c = 0 by graphing</b><br>1. Write the equation in standard form (everything on one side, 0 on the other).<br>2. Graph y = ax² + bx + c: find the axis x = −b ÷ (2a), the vertex and a few points on each side.<br>3. Read the x-intercepts. Check each one by substituting.</div><svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Zeros at x = −1 and x = 3</text><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"45.8\" y1=\"214.0\" x2=\"45.8\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"75.6\" y1=\"214.0\" x2=\"75.6\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"105.3\" y1=\"214.0\" x2=\"105.3\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"164.9\" y1=\"214.0\" x2=\"164.9\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"194.7\" y1=\"214.0\" x2=\"194.7\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"224.4\" y1=\"214.0\" x2=\"224.4\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"254.2\" y1=\"214.0\" x2=\"254.2\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"196.2\" x2=\"284.0\" y2=\"196.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"178.4\" x2=\"284.0\" y2=\"178.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"160.5\" x2=\"284.0\" y2=\"160.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"142.7\" x2=\"284.0\" y2=\"142.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"124.9\" x2=\"284.0\" y2=\"124.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"107.1\" x2=\"284.0\" y2=\"107.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"89.3\" x2=\"284.0\" y2=\"89.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"71.5\" x2=\"284.0\" y2=\"71.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"53.6\" x2=\"284.0\" y2=\"53.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"35.8\" x2=\"284.0\" y2=\"35.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"18.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"124.9\" x2=\"284.0\" y2=\"124.9\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"18.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"133.9\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"75.6\" y=\"133.9\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"194.7\" y=\"133.9\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"254.2\" y=\"133.9\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"131.1\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"131.1\" y=\"178.4\" text-anchor=\"end\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"131.1\" y=\"142.7\" text-anchor=\"end\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"131.1\" y=\"107.1\" text-anchor=\"end\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"131.1\" y=\"71.5\" text-anchor=\"end\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"131.1\" y=\"35.8\" text-anchor=\"end\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"280.0\" y=\"116.9\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"143.1\" y=\"24.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c23273\"><rect x=\"16.0\" y=\"18.0\" width=\"268.0\" height=\"196.0\"/></clipPath><path d=\"M16.0,-249.3 L16.7,-245.3 L17.3,-241.3 L18.0,-237.3 L18.7,-233.4 L19.3,-229.5 L20.0,-225.5 L20.7,-221.7 L21.4,-217.8 L22.0,-213.9 L22.7,-210.1 L23.4,-206.3 L24.0,-202.5 L24.7,-198.7 L25.4,-194.9 L26.0,-191.2 L26.7,-187.4 L27.4,-183.7 L28.1,-180.0 L28.7,-176.4 L29.4,-172.7 L30.1,-169.1 L30.7,-165.4 L31.4,-161.8 L32.1,-158.3 L32.8,-154.7 L33.4,-151.1 L34.1,-147.6 L34.8,-144.1 L35.4,-140.6 L36.1,-137.1 L36.8,-133.7 L37.4,-130.2 L38.1,-126.8 L38.8,-123.4 L39.5,-120.0 L40.1,-116.6 L40.8,-113.3 L41.5,-110.0 L42.1,-106.6 L42.8,-103.3 L43.5,-100.1 L44.1,-96.8 L44.8,-93.6 L45.5,-90.3 L46.2,-87.1 L46.8,-83.9 L47.5,-80.8 L48.2,-77.6 L48.8,-74.5 L49.5,-71.4 L50.2,-68.3 L50.8,-65.2 L51.5,-62.1 L52.2,-59.1 L52.8,-56.1 L53.5,-53.1 L54.2,-50.1 L54.9,-47.1 L55.5,-44.1 L56.2,-41.2 L56.9,-38.3 L57.5,-35.4 L58.2,-32.5 L58.9,-29.6 L59.5,-26.8 L60.2,-24.0 L60.9,-21.2 L61.6,-18.4 L62.2,-15.6 L62.9,-12.8 L63.6,-10.1 L64.2,-7.4 L64.9,-4.7 L65.6,-2.0 L66.2,0.7 L66.9,3.3 L67.6,5.9 L68.3,8.6 L68.9,11.1 L69.6,13.7 L70.3,16.3 L70.9,18.8 L71.6,21.3 L72.3,23.8 L73.0,26.3 L73.6,28.8 L74.3,31.2 L75.0,33.7 L75.6,36.1 L76.3,38.5 L77.0,40.9 L77.6,43.2 L78.3,45.6 L79.0,47.9 L79.7,50.2 L80.3,52.5 L81.0,54.7 L81.7,57.0 L82.3,59.2 L83.0,61.4 L83.7,63.6 L84.3,65.8 L85.0,68.0 L85.7,70.1 L86.3,72.2 L87.0,74.3 L87.7,76.4 L88.4,78.5 L89.0,80.5 L89.7,82.6 L90.4,84.6 L91.0,86.6 L91.7,88.6 L92.4,90.5 L93.0,92.5 L93.7,94.4 L94.4,96.3 L95.1,98.2 L95.7,100.1 L96.4,101.9 L97.1,103.8 L97.7,105.6 L98.4,107.4 L99.1,109.2 L99.8,110.9 L100.4,112.7 L101.1,114.4 L101.8,116.1 L102.4,117.8 L103.1,119.5 L103.8,121.1 L104.4,122.8 L105.1,124.4 L105.8,126.0 L106.5,127.6 L107.1,129.1 L107.8,130.7 L108.5,132.2 L109.1,133.7 L109.8,135.2 L110.5,136.7 L111.1,138.1 L111.8,139.6 L112.5,141.0 L113.2,142.4 L113.8,143.8 L114.5,145.1 L115.2,146.5 L115.8,147.8 L116.5,149.1 L117.2,150.4 L117.8,151.7 L118.5,153.0 L119.2,154.2 L119.8,155.4 L120.5,156.6 L121.2,157.8 L121.9,159.0 L122.5,160.1 L123.2,161.3 L123.9,162.4 L124.5,163.5 L125.2,164.5 L125.9,165.6 L126.5,166.6 L127.2,167.7 L127.9,168.7 L128.6,169.7 L129.2,170.6 L129.9,171.6 L130.6,172.5 L131.2,173.4 L131.9,174.3 L132.6,175.2 L133.2,176.1 L133.9,176.9 L134.6,177.7 L135.3,178.5 L135.9,179.3 L136.6,180.1 L137.3,180.9 L137.9,181.6 L138.6,182.3 L139.3,183.0 L139.9,183.7 L140.6,184.3 L141.3,185.0 L142.0,185.6 L142.6,186.2 L143.3,186.8 L144.0,187.4 L144.6,187.9 L145.3,188.5 L146.0,189.0 L146.7,189.5 L147.3,190.0 L148.0,190.4 L148.7,190.9 L149.3,191.3 L150.0,191.7 L150.7,192.1 L151.3,192.5 L152.0,192.8 L152.7,193.2 L153.3,193.5 L154.0,193.8 L154.7,194.1 L155.4,194.4 L156.0,194.6 L156.7,194.8 L157.4,195.0 L158.0,195.2 L158.7,195.4 L159.4,195.6 L160.1,195.7 L160.7,195.8 L161.4,195.9 L162.1,196.0 L162.7,196.1 L163.4,196.1 L164.1,196.2 L164.7,196.2 L165.4,196.2 L166.1,196.2 L166.8,196.1 L167.4,196.1 L168.1,196.0 L168.8,195.9 L169.4,195.8 L170.1,195.6 L170.8,195.5 L171.4,195.3 L172.1,195.1 L172.8,194.9 L173.4,194.7 L174.1,194.5 L174.8,194.2 L175.5,193.9 L176.1,193.6 L176.8,193.3 L177.5,193.0 L178.1,192.7 L178.8,192.3 L179.5,191.9 L180.2,191.5 L180.8,191.1 L181.5,190.6 L182.2,190.2 L182.8,189.7 L183.5,189.2 L184.2,188.7 L184.8,188.2 L185.5,187.6 L186.2,187.1 L186.8,186.5 L187.5,185.9 L188.2,185.3 L188.9,184.6 L189.5,184.0 L190.2,183.3 L190.9,182.6 L191.5,181.9 L192.2,181.2 L192.9,180.4 L193.6,179.7 L194.2,178.9 L194.9,178.1 L195.6,177.3 L196.2,176.4 L196.9,175.6 L197.6,174.7 L198.2,173.8 L198.9,172.9 L199.6,172.0 L200.2,171.1 L200.9,170.1 L201.6,169.1 L202.3,168.1 L202.9,167.1 L203.6,166.1 L204.3,165.0 L204.9,163.9 L205.6,162.9 L206.3,161.8 L206.9,160.6 L207.6,159.5 L208.3,158.3 L209.0,157.2 L209.6,156.0 L210.3,154.7 L211.0,153.5 L211.6,152.3 L212.3,151.0 L213.0,149.7 L213.7,148.4 L214.3,147.1 L215.0,145.7 L215.7,144.4 L216.3,143.0 L217.0,141.6 L217.7,140.2 L218.3,138.8 L219.0,137.3 L219.7,135.9 L220.3,134.4 L221.0,132.9 L221.7,131.3 L222.4,129.8 L223.0,128.3 L223.7,126.7 L224.4,125.1 L225.0,123.5 L225.7,121.8 L226.4,120.2 L227.1,118.5 L227.7,116.9 L228.4,115.2 L229.1,113.4 L229.7,111.7 L230.4,109.9 L231.1,108.2 L231.7,106.4 L232.4,104.6 L233.1,102.7 L233.8,100.9 L234.4,99.0 L235.1,97.2 L235.8,95.3 L236.4,93.3 L237.1,91.4 L237.8,89.4 L238.4,87.5 L239.1,85.5 L239.8,83.5 L240.4,81.5 L241.1,79.4 L241.8,77.3 L242.5,75.3 L243.1,73.2 L243.8,71.1 L244.5,68.9 L245.1,66.8 L245.8,64.6 L246.5,62.4 L247.2,60.2 L247.8,58.0 L248.5,55.7 L249.2,53.5 L249.8,51.2 L250.5,48.9 L251.2,46.6 L251.8,44.3 L252.5,41.9 L253.2,39.5 L253.8,37.2 L254.5,34.7 L255.2,32.3 L255.9,29.9 L256.5,27.4 L257.2,24.9 L257.9,22.5 L258.5,19.9 L259.2,17.4 L259.9,14.9 L260.6,12.3 L261.2,9.7 L261.9,7.1 L262.6,4.5 L263.2,1.8 L263.9,-0.8 L264.6,-3.5 L265.2,-6.2 L265.9,-8.9 L266.6,-11.6 L267.2,-14.4 L267.9,-17.1 L268.6,-19.9 L269.3,-22.7 L269.9,-25.5 L270.6,-28.4 L271.3,-31.2 L271.9,-34.1 L272.6,-37.0 L273.3,-39.9 L273.9,-42.8 L274.6,-45.8 L275.3,-48.7 L276.0,-51.7 L276.6,-54.7 L277.3,-57.7 L278.0,-60.8 L278.6,-63.8 L279.3,-66.9 L280.0,-70.0 L280.6,-73.1 L281.3,-76.2 L282.0,-79.4 L282.7,-82.5 L283.3,-85.7 L284.0,-88.9\" clip-path=\"url(#c23273)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"242.3\" y=\"68.7\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x² − 2x − 3</text><circle cx=\"105.3\" cy=\"124.9\" r=\"3.4\" style=\"fill:var(--ink)\"/><text class=\"lb\" x=\"111.3\" y=\"115.9\" text-anchor=\"start\" dominant-baseline=\"middle\">(−1, 0)</text><circle cx=\"224.4\" cy=\"124.9\" r=\"3.4\" style=\"fill:var(--ink)\"/><text class=\"lb\" x=\"230.4\" y=\"115.9\" text-anchor=\"start\" dominant-baseline=\"middle\">(3, 0)</text></svg><div class=\"ex\"><div class=\"exh\">Worked example 1 · Read the zeros</div><div class=\"exl\">Solve x² − 2x − 3 = 0 by graphing.<br>Axis x = −(−2) ÷ 2 = 1; vertex (1, −4); the graph crosses the x-axis at −1 and 3.<br><b>x = −1 or x = 3</b>. Check: (−1)² + 2 − 3 = 0 ✓ and 9 − 6 − 3 = 0 ✓</div></div><h4>How many solutions?</h4><p>A parabola can cross the x-axis twice, touch it once (the vertex is on the axis) or miss it altogether.</p><svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Number of x-intercepts = number of real solutions</text><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"83.0\" y1=\"214.0\" x2=\"83.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"116.5\" y1=\"214.0\" x2=\"116.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"217.0\" y1=\"214.0\" x2=\"217.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"250.5\" y1=\"214.0\" x2=\"250.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"196.2\" x2=\"284.0\" y2=\"196.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"178.4\" x2=\"284.0\" y2=\"178.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"160.5\" x2=\"284.0\" y2=\"160.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"142.7\" x2=\"284.0\" y2=\"142.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"124.9\" x2=\"284.0\" y2=\"124.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"107.1\" x2=\"284.0\" y2=\"107.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"89.3\" x2=\"284.0\" y2=\"89.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"71.5\" x2=\"284.0\" y2=\"71.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"53.6\" x2=\"284.0\" y2=\"53.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"35.8\" x2=\"284.0\" y2=\"35.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"18.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"142.7\" x2=\"284.0\" y2=\"142.7\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"18.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"151.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"83.0\" y=\"151.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"217.0\" y=\"151.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"284.0\" y=\"151.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"146.0\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"146.0\" y=\"178.4\" text-anchor=\"end\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"146.0\" y=\"107.1\" text-anchor=\"end\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"146.0\" y=\"71.5\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"146.0\" y=\"35.8\" text-anchor=\"end\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"280.0\" y=\"134.7\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"158.0\" y=\"24.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c94758\"><rect x=\"16.0\" y=\"18.0\" width=\"268.0\" height=\"196.0\"/></clipPath><path d=\"M16.0,-88.9 L16.7,-86.1 L17.3,-83.2 L18.0,-80.4 L18.7,-77.6 L19.4,-74.8 L20.0,-72.1 L20.7,-69.3 L21.4,-66.6 L22.0,-63.8 L22.7,-61.1 L23.4,-58.4 L24.0,-55.7 L24.7,-53.1 L25.4,-50.4 L26.0,-47.7 L26.7,-45.1 L27.4,-42.5 L28.1,-39.9 L28.7,-37.3 L29.4,-34.7 L30.1,-32.2 L30.7,-29.6 L31.4,-27.1 L32.1,-24.6 L32.8,-22.1 L33.4,-19.6 L34.1,-17.1 L34.8,-14.7 L35.4,-12.2 L36.1,-9.8 L36.8,-7.4 L37.4,-5.0 L38.1,-2.6 L38.8,-0.2 L39.5,2.1 L40.1,4.5 L40.8,6.8 L41.5,9.1 L42.1,11.4 L42.8,13.7 L43.5,16.0 L44.1,18.3 L44.8,20.5 L45.5,22.7 L46.1,24.9 L46.8,27.2 L47.5,29.3 L48.2,31.5 L48.8,33.7 L49.5,35.8 L50.2,37.9 L50.8,40.1 L51.5,42.2 L52.2,44.3 L52.9,46.3 L53.5,48.4 L54.2,50.4 L54.9,52.5 L55.5,54.5 L56.2,56.5 L56.9,58.5 L57.5,60.5 L58.2,62.4 L58.9,64.4 L59.5,66.3 L60.2,68.2 L60.9,70.1 L61.6,72.0 L62.2,73.9 L62.9,75.7 L63.6,77.6 L64.2,79.4 L64.9,81.2 L65.6,83.0 L66.2,84.8 L66.9,86.6 L67.6,88.4 L68.3,90.1 L68.9,91.8 L69.6,93.5 L70.3,95.3 L70.9,96.9 L71.6,98.6 L72.3,100.3 L73.0,101.9 L73.6,103.6 L74.3,105.2 L75.0,106.8 L75.6,108.4 L76.3,109.9 L77.0,111.5 L77.6,113.0 L78.3,114.6 L79.0,116.1 L79.7,117.6 L80.3,119.1 L81.0,120.6 L81.7,122.0 L82.3,123.5 L83.0,124.9 L83.7,126.3 L84.3,127.7 L85.0,129.1 L85.7,130.5 L86.4,131.9 L87.0,133.2 L87.7,134.5 L88.4,135.9 L89.0,137.2 L89.7,138.5 L90.4,139.7 L91.0,141.0 L91.7,142.2 L92.4,143.5 L93.0,144.7 L93.7,145.9 L94.4,147.1 L95.1,148.3 L95.7,149.4 L96.4,150.6 L97.1,151.7 L97.7,152.8 L98.4,153.9 L99.1,155.0 L99.8,156.1 L100.4,157.2 L101.1,158.2 L101.8,159.2 L102.4,160.3 L103.1,161.3 L103.8,162.2 L104.4,163.2 L105.1,164.2 L105.8,165.1 L106.5,166.1 L107.1,167.0 L107.8,167.9 L108.5,168.8 L109.1,169.7 L109.8,170.5 L110.5,171.4 L111.1,172.2 L111.8,173.0 L112.5,173.8 L113.1,174.6 L113.8,175.4 L114.5,176.2 L115.2,176.9 L115.8,177.6 L116.5,178.4 L117.2,179.1 L117.8,179.8 L118.5,180.4 L119.2,181.1 L119.9,181.7 L120.5,182.4 L121.2,183.0 L121.9,183.6 L122.5,184.2 L123.2,184.8 L123.9,185.3 L124.5,185.9 L125.2,186.4 L125.9,186.9 L126.5,187.5 L127.2,187.9 L127.9,188.4 L128.6,188.9 L129.2,189.3 L129.9,189.8 L130.6,190.2 L131.2,190.6 L131.9,191.0 L132.6,191.4 L133.2,191.7 L133.9,192.1 L134.6,192.4 L135.3,192.7 L135.9,193.0 L136.6,193.3 L137.3,193.6 L137.9,193.9 L138.6,194.1 L139.3,194.4 L139.9,194.6 L140.6,194.8 L141.3,195.0 L142.0,195.2 L142.6,195.3 L143.3,195.5 L144.0,195.6 L144.6,195.7 L145.3,195.8 L146.0,195.9 L146.7,196.0 L147.3,196.1 L148.0,196.1 L148.7,196.2 L149.3,196.2 L150.0,196.2 L150.7,196.2 L151.3,196.2 L152.0,196.1 L152.7,196.1 L153.3,196.0 L154.0,195.9 L154.7,195.8 L155.4,195.7 L156.0,195.6 L156.7,195.5 L157.4,195.3 L158.0,195.2 L158.7,195.0 L159.4,194.8 L160.0,194.6 L160.7,194.4 L161.4,194.1 L162.1,193.9 L162.7,193.6 L163.4,193.3 L164.1,193.0 L164.7,192.7 L165.4,192.4 L166.1,192.1 L166.8,191.7 L167.4,191.4 L168.1,191.0 L168.8,190.6 L169.4,190.2 L170.1,189.8 L170.8,189.3 L171.4,188.9 L172.1,188.4 L172.8,187.9 L173.5,187.5 L174.1,186.9 L174.8,186.4 L175.5,185.9 L176.1,185.3 L176.8,184.8 L177.5,184.2 L178.1,183.6 L178.8,183.0 L179.5,182.4 L180.2,181.7 L180.8,181.1 L181.5,180.4 L182.2,179.8 L182.8,179.1 L183.5,178.4 L184.2,177.6 L184.8,176.9 L185.5,176.2 L186.2,175.4 L186.8,174.6 L187.5,173.8 L188.2,173.0 L188.9,172.2 L189.5,171.4 L190.2,170.5 L190.9,169.7 L191.5,168.8 L192.2,167.9 L192.9,167.0 L193.5,166.1 L194.2,165.1 L194.9,164.2 L195.6,163.2 L196.2,162.2 L196.9,161.3 L197.6,160.3 L198.2,159.2 L198.9,158.2 L199.6,157.2 L200.2,156.1 L200.9,155.0 L201.6,153.9 L202.3,152.8 L202.9,151.7 L203.6,150.6 L204.3,149.4 L204.9,148.3 L205.6,147.1 L206.3,145.9 L207.0,144.7 L207.6,143.5 L208.3,142.2 L209.0,141.0 L209.6,139.7 L210.3,138.5 L211.0,137.2 L211.6,135.9 L212.3,134.5 L213.0,133.2 L213.7,131.9 L214.3,130.5 L215.0,129.1 L215.7,127.7 L216.3,126.3 L217.0,124.9 L217.7,123.5 L218.3,122.0 L219.0,120.6 L219.7,119.1 L220.3,117.6 L221.0,116.1 L221.7,114.6 L222.4,113.0 L223.0,111.5 L223.7,109.9 L224.4,108.4 L225.0,106.8 L225.7,105.2 L226.4,103.6 L227.0,101.9 L227.7,100.3 L228.4,98.6 L229.1,96.9 L229.7,95.3 L230.4,93.5 L231.1,91.8 L231.7,90.1 L232.4,88.4 L233.1,86.6 L233.8,84.8 L234.4,83.0 L235.1,81.2 L235.8,79.4 L236.4,77.6 L237.1,75.7 L237.8,73.9 L238.4,72.0 L239.1,70.1 L239.8,68.2 L240.5,66.3 L241.1,64.4 L241.8,62.4 L242.5,60.5 L243.1,58.5 L243.8,56.5 L244.5,54.5 L245.1,52.5 L245.8,50.4 L246.5,48.4 L247.2,46.3 L247.8,44.3 L248.5,42.2 L249.2,40.1 L249.8,37.9 L250.5,35.8 L251.2,33.7 L251.8,31.5 L252.5,29.3 L253.2,27.2 L253.8,24.9 L254.5,22.7 L255.2,20.5 L255.9,18.3 L256.5,16.0 L257.2,13.7 L257.9,11.4 L258.5,9.1 L259.2,6.8 L259.9,4.5 L260.5,2.1 L261.2,-0.2 L261.9,-2.6 L262.6,-5.0 L263.2,-7.4 L263.9,-9.8 L264.6,-12.2 L265.2,-14.7 L265.9,-17.1 L266.6,-19.6 L267.2,-22.1 L267.9,-24.6 L268.6,-27.1 L269.3,-29.6 L269.9,-32.2 L270.6,-34.7 L271.3,-37.3 L271.9,-39.9 L272.6,-42.5 L273.3,-45.1 L273.9,-47.7 L274.6,-50.4 L275.3,-53.1 L276.0,-55.7 L276.6,-58.4 L277.3,-61.1 L278.0,-63.8 L278.6,-66.6 L279.3,-69.3 L280.0,-72.1 L280.7,-74.8 L281.3,-77.6 L282.0,-80.4 L282.7,-83.2 L283.3,-86.1 L284.0,-88.9\" clip-path=\"url(#c94758)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"230.4\" y=\"86.5\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">2 solutions</text><path d=\"M16.0,-142.4 L16.7,-139.5 L17.3,-136.7 L18.0,-133.9 L18.7,-131.1 L19.4,-128.3 L20.0,-125.5 L20.7,-122.8 L21.4,-120.0 L22.0,-117.3 L22.7,-114.6 L23.4,-111.9 L24.0,-109.2 L24.7,-106.5 L25.4,-103.8 L26.0,-101.2 L26.7,-98.6 L27.4,-96.0 L28.1,-93.4 L28.7,-90.8 L29.4,-88.2 L30.1,-85.6 L30.7,-83.1 L31.4,-80.6 L32.1,-78.0 L32.8,-75.5 L33.4,-73.1 L34.1,-70.6 L34.8,-68.1 L35.4,-65.7 L36.1,-63.3 L36.8,-60.8 L37.4,-58.4 L38.1,-56.0 L38.8,-53.7 L39.5,-51.3 L40.1,-49.0 L40.8,-46.6 L41.5,-44.3 L42.1,-42.0 L42.8,-39.7 L43.5,-37.5 L44.1,-35.2 L44.8,-33.0 L45.5,-30.7 L46.1,-28.5 L46.8,-26.3 L47.5,-24.1 L48.2,-21.9 L48.8,-19.8 L49.5,-17.6 L50.2,-15.5 L50.8,-13.4 L51.5,-11.3 L52.2,-9.2 L52.9,-7.1 L53.5,-5.1 L54.2,-3.0 L54.9,-1.0 L55.5,1.0 L56.2,3.0 L56.9,5.0 L57.5,7.0 L58.2,9.0 L58.9,10.9 L59.5,12.8 L60.2,14.7 L60.9,16.7 L61.6,18.5 L62.2,20.4 L62.9,22.3 L63.6,24.1 L64.2,26.0 L64.9,27.8 L65.6,29.6 L66.2,31.4 L66.9,33.1 L67.6,34.9 L68.3,36.6 L68.9,38.4 L69.6,40.1 L70.3,41.8 L70.9,43.5 L71.6,45.2 L72.3,46.8 L73.0,48.5 L73.6,50.1 L74.3,51.7 L75.0,53.3 L75.6,54.9 L76.3,56.5 L77.0,58.0 L77.6,59.6 L78.3,61.1 L79.0,62.6 L79.7,64.1 L80.3,65.6 L81.0,67.1 L81.7,68.6 L82.3,70.0 L83.0,71.5 L83.7,72.9 L84.3,74.3 L85.0,75.7 L85.7,77.0 L86.4,78.4 L87.0,79.8 L87.7,81.1 L88.4,82.4 L89.0,83.7 L89.7,85.0 L90.4,86.3 L91.0,87.5 L91.7,88.8 L92.4,90.0 L93.0,91.2 L93.7,92.4 L94.4,93.6 L95.1,94.8 L95.7,96.0 L96.4,97.1 L97.1,98.2 L97.7,99.4 L98.4,100.5 L99.1,101.6 L99.8,102.6 L100.4,103.7 L101.1,104.7 L101.8,105.8 L102.4,106.8 L103.1,107.8 L103.8,108.8 L104.4,109.8 L105.1,110.7 L105.8,111.7 L106.5,112.6 L107.1,113.5 L107.8,114.4 L108.5,115.3 L109.1,116.2 L109.8,117.1 L110.5,117.9 L111.1,118.8 L111.8,119.6 L112.5,120.4 L113.1,121.2 L113.8,121.9 L114.5,122.7 L115.2,123.5 L115.8,124.2 L116.5,124.9 L117.2,125.6 L117.8,126.3 L118.5,127.0 L119.2,127.6 L119.9,128.3 L120.5,128.9 L121.2,129.5 L121.9,130.2 L122.5,130.7 L123.2,131.3 L123.9,131.9 L124.5,132.4 L125.2,133.0 L125.9,133.5 L126.5,134.0 L127.2,134.5 L127.9,135.0 L128.6,135.4 L129.2,135.9 L129.9,136.3 L130.6,136.7 L131.2,137.1 L131.9,137.5 L132.6,137.9 L133.2,138.3 L133.9,138.6 L134.6,139.0 L135.3,139.3 L135.9,139.6 L136.6,139.9 L137.3,140.2 L137.9,140.4 L138.6,140.7 L139.3,140.9 L139.9,141.1 L140.6,141.3 L141.3,141.5 L142.0,141.7 L142.6,141.9 L143.3,142.0 L144.0,142.1 L144.6,142.3 L145.3,142.4 L146.0,142.5 L146.7,142.5 L147.3,142.6 L148.0,142.7 L148.7,142.7 L149.3,142.7 L150.0,142.7 L150.7,142.7 L151.3,142.7 L152.0,142.7 L152.7,142.6 L153.3,142.5 L154.0,142.5 L154.7,142.4 L155.4,142.3 L156.0,142.1 L156.7,142.0 L157.4,141.9 L158.0,141.7 L158.7,141.5 L159.4,141.3 L160.0,141.1 L160.7,140.9 L161.4,140.7 L162.1,140.4 L162.7,140.2 L163.4,139.9 L164.1,139.6 L164.7,139.3 L165.4,139.0 L166.1,138.6 L166.8,138.3 L167.4,137.9 L168.1,137.5 L168.8,137.1 L169.4,136.7 L170.1,136.3 L170.8,135.9 L171.4,135.4 L172.1,135.0 L172.8,134.5 L173.5,134.0 L174.1,133.5 L174.8,133.0 L175.5,132.4 L176.1,131.9 L176.8,131.3 L177.5,130.7 L178.1,130.2 L178.8,129.5 L179.5,128.9 L180.2,128.3 L180.8,127.6 L181.5,127.0 L182.2,126.3 L182.8,125.6 L183.5,124.9 L184.2,124.2 L184.8,123.5 L185.5,122.7 L186.2,121.9 L186.8,121.2 L187.5,120.4 L188.2,119.6 L188.9,118.8 L189.5,117.9 L190.2,117.1 L190.9,116.2 L191.5,115.3 L192.2,114.4 L192.9,113.5 L193.5,112.6 L194.2,111.7 L194.9,110.7 L195.6,109.8 L196.2,108.8 L196.9,107.8 L197.6,106.8 L198.2,105.8 L198.9,104.7 L199.6,103.7 L200.2,102.6 L200.9,101.6 L201.6,100.5 L202.3,99.4 L202.9,98.2 L203.6,97.1 L204.3,96.0 L204.9,94.8 L205.6,93.6 L206.3,92.4 L207.0,91.2 L207.6,90.0 L208.3,88.8 L209.0,87.5 L209.6,86.3 L210.3,85.0 L211.0,83.7 L211.6,82.4 L212.3,81.1 L213.0,79.8 L213.7,78.4 L214.3,77.0 L215.0,75.7 L215.7,74.3 L216.3,72.9 L217.0,71.5 L217.7,70.0 L218.3,68.6 L219.0,67.1 L219.7,65.6 L220.3,64.1 L221.0,62.6 L221.7,61.1 L222.4,59.6 L223.0,58.0 L223.7,56.5 L224.4,54.9 L225.0,53.3 L225.7,51.7 L226.4,50.1 L227.0,48.5 L227.7,46.8 L228.4,45.2 L229.1,43.5 L229.7,41.8 L230.4,40.1 L231.1,38.4 L231.7,36.6 L232.4,34.9 L233.1,33.1 L233.8,31.4 L234.4,29.6 L235.1,27.8 L235.8,26.0 L236.4,24.1 L237.1,22.3 L237.8,20.4 L238.4,18.5 L239.1,16.7 L239.8,14.7 L240.5,12.8 L241.1,10.9 L241.8,9.0 L242.5,7.0 L243.1,5.0 L243.8,3.0 L244.5,1.0 L245.1,-1.0 L245.8,-3.0 L246.5,-5.1 L247.2,-7.1 L247.8,-9.2 L248.5,-11.3 L249.2,-13.4 L249.8,-15.5 L250.5,-17.6 L251.2,-19.8 L251.8,-21.9 L252.5,-24.1 L253.2,-26.3 L253.8,-28.5 L254.5,-30.7 L255.2,-33.0 L255.9,-35.2 L256.5,-37.5 L257.2,-39.7 L257.9,-42.0 L258.5,-44.3 L259.2,-46.6 L259.9,-49.0 L260.5,-51.3 L261.2,-53.7 L261.9,-56.0 L262.6,-58.4 L263.2,-60.8 L263.9,-63.3 L264.6,-65.7 L265.2,-68.1 L265.9,-70.6 L266.6,-73.1 L267.2,-75.5 L267.9,-78.0 L268.6,-80.6 L269.3,-83.1 L269.9,-85.6 L270.6,-88.2 L271.3,-90.8 L271.9,-93.4 L272.6,-96.0 L273.3,-98.6 L273.9,-101.2 L274.6,-103.8 L275.3,-106.5 L276.0,-109.2 L276.6,-111.9 L277.3,-114.6 L278.0,-117.3 L278.6,-120.0 L279.3,-122.8 L280.0,-125.5 L280.7,-128.3 L281.3,-131.1 L282.0,-133.9 L282.7,-136.7 L283.3,-139.5 L284.0,-142.4\" clip-path=\"url(#c94758)\" style=\"fill:none;stroke:var(--accent-text);stroke-width:2.2;stroke-dasharray:6 4\"/><text x=\"86.4\" y=\"71.4\" text-anchor=\"middle\" style=\"fill:var(--accent-text);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">1 solution</text><path d=\"M16.0,-178.0 L16.7,-175.2 L17.3,-172.3 L18.0,-169.5 L18.7,-166.7 L19.4,-163.9 L20.0,-161.2 L20.7,-158.4 L21.4,-155.6 L22.0,-152.9 L22.7,-150.2 L23.4,-147.5 L24.0,-144.8 L24.7,-142.1 L25.4,-139.5 L26.0,-136.8 L26.7,-134.2 L27.4,-131.6 L28.1,-129.0 L28.7,-126.4 L29.4,-123.8 L30.1,-121.3 L30.7,-118.7 L31.4,-116.2 L32.1,-113.7 L32.8,-111.2 L33.4,-108.7 L34.1,-106.2 L34.8,-103.8 L35.4,-101.3 L36.1,-98.9 L36.8,-96.5 L37.4,-94.1 L38.1,-91.7 L38.8,-89.3 L39.5,-86.9 L40.1,-84.6 L40.8,-82.3 L41.5,-80.0 L42.1,-77.7 L42.8,-75.4 L43.5,-73.1 L44.1,-70.8 L44.8,-68.6 L45.5,-66.4 L46.1,-64.1 L46.8,-61.9 L47.5,-59.8 L48.2,-57.6 L48.8,-55.4 L49.5,-53.3 L50.2,-51.1 L50.8,-49.0 L51.5,-46.9 L52.2,-44.8 L52.9,-42.8 L53.5,-40.7 L54.2,-38.7 L54.9,-36.6 L55.5,-34.6 L56.2,-32.6 L56.9,-30.6 L57.5,-28.6 L58.2,-26.7 L58.9,-24.7 L59.5,-22.8 L60.2,-20.9 L60.9,-19.0 L61.6,-17.1 L62.2,-15.2 L62.9,-13.4 L63.6,-11.5 L64.2,-9.7 L64.9,-7.9 L65.6,-6.1 L66.2,-4.3 L66.9,-2.5 L67.6,-0.7 L68.3,1.0 L68.9,2.7 L69.6,4.5 L70.3,6.2 L70.9,7.9 L71.6,9.5 L72.3,11.2 L73.0,12.8 L73.6,14.5 L74.3,16.1 L75.0,17.7 L75.6,19.3 L76.3,20.9 L77.0,22.4 L77.6,24.0 L78.3,25.5 L79.0,27.0 L79.7,28.5 L80.3,30.0 L81.0,31.5 L81.7,32.9 L82.3,34.4 L83.0,35.8 L83.7,37.2 L84.3,38.6 L85.0,40.0 L85.7,41.4 L86.4,42.8 L87.0,44.1 L87.7,45.4 L88.4,46.8 L89.0,48.1 L89.7,49.4 L90.4,50.6 L91.0,51.9 L91.7,53.1 L92.4,54.4 L93.0,55.6 L93.7,56.8 L94.4,58.0 L95.1,59.2 L95.7,60.3 L96.4,61.5 L97.1,62.6 L97.7,63.7 L98.4,64.8 L99.1,65.9 L99.8,67.0 L100.4,68.1 L101.1,69.1 L101.8,70.1 L102.4,71.2 L103.1,72.2 L103.8,73.2 L104.4,74.1 L105.1,75.1 L105.8,76.0 L106.5,77.0 L107.1,77.9 L107.8,78.8 L108.5,79.7 L109.1,80.6 L109.8,81.4 L110.5,82.3 L111.1,83.1 L111.8,83.9 L112.5,84.7 L113.1,85.5 L113.8,86.3 L114.5,87.1 L115.2,87.8 L115.8,88.6 L116.5,89.3 L117.2,90.0 L117.8,90.7 L118.5,91.3 L119.2,92.0 L119.9,92.7 L120.5,93.3 L121.2,93.9 L121.9,94.5 L122.5,95.1 L123.2,95.7 L123.9,96.3 L124.5,96.8 L125.2,97.3 L125.9,97.9 L126.5,98.4 L127.2,98.9 L127.9,99.3 L128.6,99.8 L129.2,100.2 L129.9,100.7 L130.6,101.1 L131.2,101.5 L131.9,101.9 L132.6,102.3 L133.2,102.6 L133.9,103.0 L134.6,103.3 L135.3,103.6 L135.9,103.9 L136.6,104.2 L137.3,104.5 L137.9,104.8 L138.6,105.0 L139.3,105.3 L139.9,105.5 L140.6,105.7 L141.3,105.9 L142.0,106.1 L142.6,106.2 L143.3,106.4 L144.0,106.5 L144.6,106.6 L145.3,106.7 L146.0,106.8 L146.7,106.9 L147.3,107.0 L148.0,107.0 L148.7,107.1 L149.3,107.1 L150.0,107.1 L150.7,107.1 L151.3,107.1 L152.0,107.0 L152.7,107.0 L153.3,106.9 L154.0,106.8 L154.7,106.7 L155.4,106.6 L156.0,106.5 L156.7,106.4 L157.4,106.2 L158.0,106.1 L158.7,105.9 L159.4,105.7 L160.0,105.5 L160.7,105.3 L161.4,105.0 L162.1,104.8 L162.7,104.5 L163.4,104.2 L164.1,103.9 L164.7,103.6 L165.4,103.3 L166.1,103.0 L166.8,102.6 L167.4,102.3 L168.1,101.9 L168.8,101.5 L169.4,101.1 L170.1,100.7 L170.8,100.2 L171.4,99.8 L172.1,99.3 L172.8,98.9 L173.5,98.4 L174.1,97.9 L174.8,97.3 L175.5,96.8 L176.1,96.3 L176.8,95.7 L177.5,95.1 L178.1,94.5 L178.8,93.9 L179.5,93.3 L180.2,92.7 L180.8,92.0 L181.5,91.3 L182.2,90.7 L182.8,90.0 L183.5,89.3 L184.2,88.6 L184.8,87.8 L185.5,87.1 L186.2,86.3 L186.8,85.5 L187.5,84.7 L188.2,83.9 L188.9,83.1 L189.5,82.3 L190.2,81.4 L190.9,80.6 L191.5,79.7 L192.2,78.8 L192.9,77.9 L193.5,77.0 L194.2,76.0 L194.9,75.1 L195.6,74.1 L196.2,73.2 L196.9,72.2 L197.6,71.2 L198.2,70.1 L198.9,69.1 L199.6,68.1 L200.2,67.0 L200.9,65.9 L201.6,64.8 L202.3,63.7 L202.9,62.6 L203.6,61.5 L204.3,60.3 L204.9,59.2 L205.6,58.0 L206.3,56.8 L207.0,55.6 L207.6,54.4 L208.3,53.1 L209.0,51.9 L209.6,50.6 L210.3,49.4 L211.0,48.1 L211.6,46.8 L212.3,45.4 L213.0,44.1 L213.7,42.8 L214.3,41.4 L215.0,40.0 L215.7,38.6 L216.3,37.2 L217.0,35.8 L217.7,34.4 L218.3,32.9 L219.0,31.5 L219.7,30.0 L220.3,28.5 L221.0,27.0 L221.7,25.5 L222.4,24.0 L223.0,22.4 L223.7,20.9 L224.4,19.3 L225.0,17.7 L225.7,16.1 L226.4,14.5 L227.0,12.8 L227.7,11.2 L228.4,9.5 L229.1,7.9 L229.7,6.2 L230.4,4.5 L231.1,2.7 L231.7,1.0 L232.4,-0.7 L233.1,-2.5 L233.8,-4.3 L234.4,-6.1 L235.1,-7.9 L235.8,-9.7 L236.4,-11.5 L237.1,-13.4 L237.8,-15.2 L238.4,-17.1 L239.1,-19.0 L239.8,-20.9 L240.5,-22.8 L241.1,-24.7 L241.8,-26.7 L242.5,-28.6 L243.1,-30.6 L243.8,-32.6 L244.5,-34.6 L245.1,-36.6 L245.8,-38.7 L246.5,-40.7 L247.2,-42.8 L247.8,-44.8 L248.5,-46.9 L249.2,-49.0 L249.8,-51.1 L250.5,-53.3 L251.2,-55.4 L251.8,-57.6 L252.5,-59.8 L253.2,-61.9 L253.8,-64.1 L254.5,-66.4 L255.2,-68.6 L255.9,-70.8 L256.5,-73.1 L257.2,-75.4 L257.9,-77.7 L258.5,-80.0 L259.2,-82.3 L259.9,-84.6 L260.5,-86.9 L261.2,-89.3 L261.9,-91.7 L262.6,-94.1 L263.2,-96.5 L263.9,-98.9 L264.6,-101.3 L265.2,-103.8 L265.9,-106.2 L266.6,-108.7 L267.2,-111.2 L267.9,-113.7 L268.6,-116.2 L269.3,-118.7 L269.9,-121.3 L270.6,-123.8 L271.3,-126.4 L271.9,-129.0 L272.6,-131.6 L273.3,-134.2 L273.9,-136.8 L274.6,-139.5 L275.3,-142.1 L276.0,-144.8 L276.6,-147.5 L277.3,-150.2 L278.0,-152.9 L278.6,-155.6 L279.3,-158.4 L280.0,-161.2 L280.7,-163.9 L281.3,-166.7 L282.0,-169.5 L282.7,-172.3 L283.3,-175.2 L284.0,-178.0\" clip-path=\"url(#c94758)\" style=\"fill:none;stroke:var(--success);stroke-width:2.2\"/><text x=\"186.8\" y=\"78.5\" text-anchor=\"middle\" style=\"fill:var(--success);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">0 solutions</text></svg><div class=\"ex\"><div class=\"exh\">Worked example 2 · Standard form first</div><div class=\"exl\">Solve x² + 9 = 6x by graphing.<br>Standard form: x² − 6x + 9 = 0. The vertex of y = x² − 6x + 9 is (3, 0), on the x-axis.<br>The graph touches the x-axis once, so there is <b>one solution, x = 3</b>.</div></div><h4>Estimating solutions</h4><p>When a zero is not an integer, find two consecutive integers where f(x) changes sign. Then test tenths between them, or use the <i>zero</i> feature of a graphing calculator.</p><div class=\"ex\"><div class=\"exh\">Worked example 3 · Estimate to the nearest tenth</div><div class=\"exl\">Estimate the positive solution of x² − 5 = 0.<br>f(2) = −1 and f(3) = 4, so the zero is between 2 and 3.<br>f(2.2) = −0.16 and f(2.3) = 0.29. −0.16 is closer to 0, so <b>x ≈ 2.2</b> (the other zero is about −2.2 by symmetry).</div></div><div class=\"ex\"><div class=\"exh\">Worked example 4 · Real life</div><div class=\"exl\">A ball is kicked up from the ground; its height is h = −5t² + 20t metres after t seconds. When does it land?<br>Solve −5t² + 20t = 0: the graph meets the t-axis at t = 0 and t = 4.<br>It lands after <b>4 seconds</b> (t = 0 is the moment it was kicked).</div></div><div class=\"keybox\"><b>Common mistake.</b> The solutions are where the graph meets the <b>x-axis</b>, not where it meets the y-axis, and not the vertex. Also write the equation as “… = 0” before graphing: graphing y = x² − 6x for x² − 6x = −9 gives the wrong intercepts.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 9.2 →</button></div></section><section class=\"note\" id=\"n93\"><h2>9.3 Solving Quadratic Equations Using Square Roots</h2><p class=\"lt\"><b>Learning target:</b> I can solve equations of the form ax² + c = 0 and a(x − h)² = k by taking square roots, and approximate the solutions.</p><p>Every positive number has <b>two</b> square roots: one positive and one negative. So x² = d has two solutions, x = ±√d, when d &gt; 0.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>x² = d</th><th>Number of real solutions</th><th>Example</th></tr><tr><td>d &gt; 0</td><td>two: x = √d and x = −√d</td><td class=\"mono\">x² = 36 → x = ±6</td></tr><tr><td>d = 0</td><td>one: x = 0</td><td class=\"mono\">x² = 0 → x = 0</td></tr><tr><td>d &lt; 0</td><td>none (no real number squared is negative)</td><td class=\"mono\">x² = −4 → no real solutions</td></tr></table></div><div class=\"keybox\"><b>Solving by square roots</b><br>1. Isolate the squared part: x² = d or (x − h)² = d.<br>2. Take the square root of both sides and write <b>±</b>.<br>3. Solve the two resulting equations, simplify any radicals, and round only at the end if a decimal is asked for.</div><div class=\"ex\"><div class=\"exh\">Worked example 1 · ax² + c = 0</div><div class=\"exl\">Solve 4x² − 100 = 0.<br>Add 100 and divide by 4: x² = 25.<br>x = ±√25, so <b>x = 5 or x = −5</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 2 · A squared binomial</div><div class=\"exl\">Solve (x + 1)² = 12.<br>x + 1 = ±√12 = ±2√3.<br><b>x = −1 + 2√3 ≈ 2.46 or x = −1 − 2√3 ≈ −4.46</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 3 · Irrational solutions</div><div class=\"exl\">Solve 3x² + 4 = 25 and round to the nearest hundredth.<br>3x² = 21, so x² = 7.<br>x = ±√7 ≈ <b>±2.65</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 4 · Real life</div><div class=\"exl\">A stone is dropped from 80 m. Its height is h = −4.9t² + 80. When does it land?<br>0 = −4.9t² + 80 → t² = 80 ÷ 4.9 ≈ 16.33.<br>t ≈ ±4.04; time cannot be negative, so it lands after <b>about 4.04 s</b>.</div></div><div class=\"keybox\"><b>Common mistake.</b> Taking the square root gives <b>two</b> answers: x² = 49 means x = 7 <b>or</b> x = −7. Also isolate the square first: in 2x² = 18, divide by 2 before taking roots (x² = 9, x = ±3), not x = ±√18 ÷ 2.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 9.3 →</button></div></section><section class=\"note\" id=\"n94\"><h2>9.4 Solving Quadratic Equations by Completing the Square</h2><p class=\"lt\"><b>Learning target:</b> I can complete the square, solve quadratic equations by completing the square, and use it to write a quadratic function in vertex form.</p><p>A <b>perfect square trinomial</b> factors as the square of a binomial: x² + 6x + 9 = (x + 3)². <b>Completing the square</b> means adding the number that turns x² + bx into a perfect square trinomial.</p><svg class=\"figsvg\" viewBox=\"0 0 300 190\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect x=\"70\" y=\"22\" width=\"110\" height=\"110\" style=\"fill:var(--card);stroke:var(--ink);stroke-width:1.6\"/><rect x=\"180\" y=\"22\" width=\"44\" height=\"110\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1.6\"/><rect x=\"70\" y=\"132\" width=\"110\" height=\"44\" style=\"fill:var(--paper-2);stroke:var(--ink);stroke-width:1.6\"/><rect x=\"180\" y=\"132\" width=\"44\" height=\"44\" style=\"fill:none;stroke:var(--danger);stroke-width:1.8;stroke-dasharray:5 4\"/><text class=\"lb\" x=\"125.0\" y=\"77.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x²</text><text class=\"lb\" x=\"202.0\" y=\"77.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x</text><text class=\"lb\" x=\"125.0\" y=\"154.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x</text><text class=\"al\" x=\"202.0\" y=\"154.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">9</text><text class=\"lb\" x=\"125.0\" y=\"12.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"202.0\" y=\"12.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"lb\" x=\"60.0\" y=\"77.0\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"60.0\" y=\"154.0\" text-anchor=\"end\" dominant-baseline=\"middle\">3</text></svg><div class=\"keybox\"><b>Completing the square</b><br>For x² + bx, add <b>(b ÷ 2)²</b>: x² + bx + (b ÷ 2)² = (x + b ÷ 2)².<br>Example: x² + 6x needs (6 ÷ 2)² = 9, the missing corner of the square above.</div><div class=\"keybox\"><b>Solving ax² + bx + c = 0 by completing the square</b><br>1. If a ≠ 1, divide every term by a.<br>2. Move the constant to the right side: x² + bx = d.<br>3. Add (b ÷ 2)² to <b>both</b> sides.<br>4. Write the left side as (x + b ÷ 2)² and solve by square roots.</div><div class=\"ex\"><div class=\"exh\">Worked example 1 · Integer solutions</div><div class=\"exl\">Solve x² − 8x + 7 = 0.<br>x² − 8x = −7. Add (−8 ÷ 2)² = 16 to both sides: x² − 8x + 16 = 9.<br>(x − 4)² = 9 → x − 4 = ±3 → <b>x = 7 or x = 1</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 2 · a ≠ 1 and irrational solutions</div><div class=\"exl\">Solve 2x² + 4x − 3 = 0.<br>Divide by 2: x² + 2x = {3/2}. Add 1: (x + 1)² = {5/2}.<br>x = −1 ± √({5/2}) ≈ <b>0.58 or −2.58</b>.</div></div><h4>Vertex form</h4><p>Completing the square on the <b>function</b> y = ax² + bx + c gives <b>vertex form</b> y = a(x − h)² + k, with vertex (h, k). Add and subtract (b ÷ 2)² on the same side so the function does not change.</p><div class=\"ex\"><div class=\"exh\">Worked example 3 · Find the vertex</div><div class=\"exl\">Write y = x² + 10x + 18 in vertex form.<br>y = (x² + 10x + 25) − 25 + 18 = (x + 5)² − 7.<br>The vertex is <b>(−5, −7)</b>; the minimum value is −7.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 4 · Real life</div><div class=\"exl\">A garden is 6 m longer than it is wide and has area 55 m². Find its width.<br>w(w + 6) = 55 → w² + 6w = 55. Add 9: (w + 3)² = 64.<br>w + 3 = ±8, so w = 5 or −11. A width is positive: <b>5 m by 11 m</b>.</div></div><div class=\"keybox\"><b>Common mistake.</b> Add (b ÷ 2)² to <b>both</b> sides of an equation. And complete the square only when the coefficient of x² is 1: for 3x² + 12x = 9, divide by 3 first (x² + 4x = 3), then add 4.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 9.4 →</button></div></section><section class=\"note\" id=\"n95\"><h2>9.5 Solving Quadratic Equations Using the Quadratic Formula</h2><p class=\"lt\"><b>Learning target:</b> I can solve any quadratic equation with the Quadratic Formula, use the discriminant to count real solutions, and choose an efficient method.</p><p>Completing the square on ax² + bx + c = 0 in general gives a formula that solves <b>every</b> quadratic equation.</p><div class=\"keybox\"><b>The Quadratic Formula</b><br>The solutions of ax² + bx + c = 0 (a ≠ 0) are<br><span class=\"mono\" style=\"font-size:1.1em\">x = (−b ± √(b² − 4ac)) / (2a)</span></div><h4>The discriminant</h4><p>The expression under the radical, <b>b² − 4ac</b>, is the <b>discriminant</b>. It tells you how many real solutions there are without solving.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>b² − 4ac</th><th>Real solutions</th><th>Graph of y = ax² + bx + c</th></tr><tr><td>positive</td><td>two</td><td>crosses the x-axis twice</td></tr><tr><td>zero</td><td>one</td><td>touches the x-axis at the vertex</td></tr><tr><td>negative</td><td>none</td><td>does not meet the x-axis</td></tr></table></div><div class=\"ex\"><div class=\"exh\">Worked example 1 · Integer solutions</div><div class=\"exl\">Solve 2x² − x − 6 = 0.<br>a = 2, b = −1, c = −6. b² − 4ac = 1 + 48 = 49.<br>x = (1 ± 7) / 4, so <b>x = 2 or x = −{3/2}</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 2 · Irrational solutions</div><div class=\"exl\">Solve x² + 4x − 2 = 0.<br>b² − 4ac = 16 + 8 = 24, and √24 = 2√6.<br>x = (−4 ± 2√6) / 2 = <b>−2 ± √6</b> ≈ 0.45 or −4.45.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 3 · Use the discriminant</div><div class=\"exl\">How many real solutions does 3x² − 2x + 4 = 0 have?<br>b² − 4ac = 4 − 48 = −44.<br>The discriminant is negative, so there are <b>no real solutions</b>.</div></div><h4>Choosing a method</h4><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Method</th><th>Best when</th><th>Example</th></tr><tr><td>Factoring</td><td>the trinomial factors easily</td><td class=\"mono\">x² − 5x + 6 = 0</td></tr><tr><td>Square roots</td><td>there is no x-term (b = 0), or it is (x − h)² = k</td><td class=\"mono\">3x² = 48</td></tr><tr><td>Completing the square</td><td>a = 1 and b is even</td><td class=\"mono\">x² + 8x − 1 = 0</td></tr><tr><td>Quadratic Formula</td><td>any equation; especially when it does not factor</td><td class=\"mono\">5x² + 2x − 4 = 0</td></tr><tr><td>Graphing</td><td>an approximate answer or a picture is enough</td><td class=\"mono\">x² = 2x + 5</td></tr></table></div><div class=\"ex\"><div class=\"exh\">Worked example 4 · Real life</div><div class=\"exl\">A rock is thrown upward from a 30 m cliff: h = −4.9t² + 12t + 30. When does it hit the beach below the cliff (h = 0)?<br>b² − 4ac = 144 + 588 = 732; t = (−12 − √732) / (−9.8).<br>t ≈ <b>3.99 s</b> (the other root, about −1.54, is not a sensible time).</div></div><div class=\"keybox\"><b>Common mistake.</b> Write the equation in standard form first and take the signs of a, b and c with them. In x² − 4x − 5 = 0, b = −4, so −b = <b>+4</b> and b² = <b>+16</b>. The whole numerator −b ± √(b² − 4ac) is divided by 2a.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 9.5 →</button></div></section><section class=\"note\" id=\"n96\"><h2>9.6 Solving Nonlinear Systems of Equations</h2><p class=\"lt\"><b>Learning target:</b> I can solve a system of a linear and a quadratic equation (or two quadratics) by graphing, substitution or elimination.</p><p>A <b>system of nonlinear equations</b> has at least one equation that is not linear. In this section one equation is usually quadratic. A <b>solution</b> is a point (x, y) that lies on <b>both</b> graphs.</p><svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A line meeting a parabola twice</text><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"83.0\" y1=\"214.0\" x2=\"83.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"116.5\" y1=\"214.0\" x2=\"116.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"217.0\" y1=\"214.0\" x2=\"217.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"250.5\" y1=\"214.0\" x2=\"250.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"192.2\" x2=\"284.0\" y2=\"192.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"170.4\" x2=\"284.0\" y2=\"170.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"148.7\" x2=\"284.0\" y2=\"148.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"126.9\" x2=\"284.0\" y2=\"126.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"105.1\" x2=\"284.0\" y2=\"105.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"83.3\" x2=\"284.0\" y2=\"83.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"61.6\" x2=\"284.0\" y2=\"61.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"39.8\" x2=\"284.0\" y2=\"39.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"18.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"170.4\" x2=\"284.0\" y2=\"170.4\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"18.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"179.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"83.0\" y=\"179.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"217.0\" y=\"179.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"284.0\" y=\"179.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"146.0\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"146.0\" y=\"126.9\" text-anchor=\"end\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"146.0\" y=\"83.3\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"146.0\" y=\"39.8\" text-anchor=\"end\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"280.0\" y=\"162.4\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"158.0\" y=\"24.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c79918\"><rect x=\"16.0\" y=\"18.0\" width=\"268.0\" height=\"196.0\"/></clipPath><path d=\"M16.0,-178.0 L16.7,-174.5 L17.3,-171.1 L18.0,-167.6 L18.7,-164.2 L19.4,-160.8 L20.0,-157.4 L20.7,-154.0 L21.4,-150.7 L22.0,-147.3 L22.7,-144.0 L23.4,-140.7 L24.0,-137.4 L24.7,-134.2 L25.4,-130.9 L26.0,-127.7 L26.7,-124.5 L27.4,-121.3 L28.1,-118.1 L28.7,-114.9 L29.4,-111.8 L30.1,-108.7 L30.7,-105.6 L31.4,-102.5 L32.1,-99.4 L32.8,-96.3 L33.4,-93.3 L34.1,-90.3 L34.8,-87.3 L35.4,-84.3 L36.1,-81.3 L36.8,-78.4 L37.4,-75.4 L38.1,-72.5 L38.8,-69.6 L39.5,-66.7 L40.1,-63.8 L40.8,-61.0 L41.5,-58.2 L42.1,-55.4 L42.8,-52.6 L43.5,-49.8 L44.1,-47.0 L44.8,-44.3 L45.5,-41.5 L46.1,-38.8 L46.8,-36.1 L47.5,-33.5 L48.2,-30.8 L48.8,-28.2 L49.5,-25.6 L50.2,-23.0 L50.8,-20.4 L51.5,-17.8 L52.2,-15.2 L52.9,-12.7 L53.5,-10.2 L54.2,-7.7 L54.9,-5.2 L55.5,-2.7 L56.2,-0.3 L56.9,2.1 L57.5,4.6 L58.2,6.9 L58.9,9.3 L59.5,11.7 L60.2,14.0 L60.9,16.4 L61.6,18.7 L62.2,21.0 L62.9,23.2 L63.6,25.5 L64.2,27.7 L64.9,29.9 L65.6,32.1 L66.2,34.3 L66.9,36.5 L67.6,38.7 L68.3,40.8 L68.9,42.9 L69.6,45.0 L70.3,47.1 L70.9,49.2 L71.6,51.2 L72.3,53.2 L73.0,55.2 L73.6,57.2 L74.3,59.2 L75.0,61.2 L75.6,63.1 L76.3,65.0 L77.0,66.9 L77.6,68.8 L78.3,70.7 L79.0,72.6 L79.7,74.4 L80.3,76.2 L81.0,78.0 L81.7,79.8 L82.3,81.6 L83.0,83.3 L83.7,85.1 L84.3,86.8 L85.0,88.5 L85.7,90.2 L86.4,91.8 L87.0,93.5 L87.7,95.1 L88.4,96.7 L89.0,98.3 L89.7,99.9 L90.4,101.4 L91.0,103.0 L91.7,104.5 L92.4,106.0 L93.0,107.5 L93.7,109.0 L94.4,110.4 L95.1,111.9 L95.7,113.3 L96.4,114.7 L97.1,116.1 L97.7,117.4 L98.4,118.8 L99.1,120.1 L99.8,121.4 L100.4,122.7 L101.1,124.0 L101.8,125.3 L102.4,126.5 L103.1,127.8 L103.8,129.0 L104.4,130.2 L105.1,131.3 L105.8,132.5 L106.5,133.6 L107.1,134.8 L107.8,135.9 L108.5,137.0 L109.1,138.0 L109.8,139.1 L110.5,140.1 L111.1,141.1 L111.8,142.1 L112.5,143.1 L113.1,144.1 L113.8,145.0 L114.5,146.0 L115.2,146.9 L115.8,147.8 L116.5,148.7 L117.2,149.5 L117.8,150.4 L118.5,151.2 L119.2,152.0 L119.9,152.8 L120.5,153.6 L121.2,154.3 L121.9,155.1 L122.5,155.8 L123.2,156.5 L123.9,157.2 L124.5,157.9 L125.2,158.5 L125.9,159.2 L126.5,159.8 L127.2,160.4 L127.9,161.0 L128.6,161.5 L129.2,162.1 L129.9,162.6 L130.6,163.1 L131.2,163.6 L131.9,164.1 L132.6,164.6 L133.2,165.0 L133.9,165.4 L134.6,165.8 L135.3,166.2 L135.9,166.6 L136.6,167.0 L137.3,167.3 L137.9,167.6 L138.6,167.9 L139.3,168.2 L139.9,168.5 L140.6,168.7 L141.3,169.0 L142.0,169.2 L142.6,169.4 L143.3,169.6 L144.0,169.7 L144.6,169.9 L145.3,170.0 L146.0,170.1 L146.7,170.2 L147.3,170.3 L148.0,170.4 L148.7,170.4 L149.3,170.4 L150.0,170.4 L150.7,170.4 L151.3,170.4 L152.0,170.4 L152.7,170.3 L153.3,170.2 L154.0,170.1 L154.7,170.0 L155.4,169.9 L156.0,169.7 L156.7,169.6 L157.4,169.4 L158.0,169.2 L158.7,169.0 L159.4,168.7 L160.0,168.5 L160.7,168.2 L161.4,167.9 L162.1,167.6 L162.7,167.3 L163.4,167.0 L164.1,166.6 L164.7,166.2 L165.4,165.8 L166.1,165.4 L166.8,165.0 L167.4,164.6 L168.1,164.1 L168.8,163.6 L169.4,163.1 L170.1,162.6 L170.8,162.1 L171.4,161.5 L172.1,161.0 L172.8,160.4 L173.5,159.8 L174.1,159.2 L174.8,158.5 L175.5,157.9 L176.1,157.2 L176.8,156.5 L177.5,155.8 L178.1,155.1 L178.8,154.3 L179.5,153.6 L180.2,152.8 L180.8,152.0 L181.5,151.2 L182.2,150.4 L182.8,149.5 L183.5,148.7 L184.2,147.8 L184.8,146.9 L185.5,146.0 L186.2,145.0 L186.8,144.1 L187.5,143.1 L188.2,142.1 L188.9,141.1 L189.5,140.1 L190.2,139.1 L190.9,138.0 L191.5,137.0 L192.2,135.9 L192.9,134.8 L193.5,133.6 L194.2,132.5 L194.9,131.3 L195.6,130.2 L196.2,129.0 L196.9,127.8 L197.6,126.5 L198.2,125.3 L198.9,124.0 L199.6,122.7 L200.2,121.4 L200.9,120.1 L201.6,118.8 L202.3,117.4 L202.9,116.1 L203.6,114.7 L204.3,113.3 L204.9,111.9 L205.6,110.4 L206.3,109.0 L207.0,107.5 L207.6,106.0 L208.3,104.5 L209.0,103.0 L209.6,101.4 L210.3,99.9 L211.0,98.3 L211.6,96.7 L212.3,95.1 L213.0,93.5 L213.7,91.8 L214.3,90.2 L215.0,88.5 L215.7,86.8 L216.3,85.1 L217.0,83.3 L217.7,81.6 L218.3,79.8 L219.0,78.0 L219.7,76.2 L220.3,74.4 L221.0,72.6 L221.7,70.7 L222.4,68.8 L223.0,66.9 L223.7,65.0 L224.4,63.1 L225.0,61.2 L225.7,59.2 L226.4,57.2 L227.0,55.2 L227.7,53.2 L228.4,51.2 L229.1,49.2 L229.7,47.1 L230.4,45.0 L231.1,42.9 L231.7,40.8 L232.4,38.7 L233.1,36.5 L233.8,34.3 L234.4,32.1 L235.1,29.9 L235.8,27.7 L236.4,25.5 L237.1,23.2 L237.8,21.0 L238.4,18.7 L239.1,16.4 L239.8,14.0 L240.5,11.7 L241.1,9.3 L241.8,6.9 L242.5,4.6 L243.1,2.1 L243.8,-0.3 L244.5,-2.7 L245.1,-5.2 L245.8,-7.7 L246.5,-10.2 L247.2,-12.7 L247.8,-15.2 L248.5,-17.8 L249.2,-20.4 L249.8,-23.0 L250.5,-25.6 L251.2,-28.2 L251.8,-30.8 L252.5,-33.5 L253.2,-36.1 L253.8,-38.8 L254.5,-41.5 L255.2,-44.3 L255.9,-47.0 L256.5,-49.8 L257.2,-52.6 L257.9,-55.4 L258.5,-58.2 L259.2,-61.0 L259.9,-63.8 L260.5,-66.7 L261.2,-69.6 L261.9,-72.5 L262.6,-75.4 L263.2,-78.4 L263.9,-81.3 L264.6,-84.3 L265.2,-87.3 L265.9,-90.3 L266.6,-93.3 L267.2,-96.3 L267.9,-99.4 L268.6,-102.5 L269.3,-105.6 L269.9,-108.7 L270.6,-111.8 L271.3,-114.9 L271.9,-118.1 L272.6,-121.3 L273.3,-124.5 L273.9,-127.7 L274.6,-130.9 L275.3,-134.2 L276.0,-137.4 L276.6,-140.7 L277.3,-144.0 L278.0,-147.3 L278.6,-150.7 L279.3,-154.0 L280.0,-157.4 L280.7,-160.8 L281.3,-164.2 L282.0,-167.6 L282.7,-171.1 L283.3,-174.5 L284.0,-178.0\" clip-path=\"url(#c79918)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"86.4\" y=\"84.8\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x²</text><path d=\"M16.0,214.0 L16.7,213.6 L17.3,213.1 L18.0,212.7 L18.7,212.3 L19.4,211.8 L20.0,211.4 L20.7,211.0 L21.4,210.5 L22.0,210.1 L22.7,209.6 L23.4,209.2 L24.0,208.8 L24.7,208.3 L25.4,207.9 L26.0,207.5 L26.7,207.0 L27.4,206.6 L28.1,206.2 L28.7,205.7 L29.4,205.3 L30.1,204.9 L30.7,204.4 L31.4,204.0 L32.1,203.5 L32.8,203.1 L33.4,202.7 L34.1,202.2 L34.8,201.8 L35.4,201.4 L36.1,200.9 L36.8,200.5 L37.4,200.1 L38.1,199.6 L38.8,199.2 L39.5,198.8 L40.1,198.3 L40.8,197.9 L41.5,197.4 L42.1,197.0 L42.8,196.6 L43.5,196.1 L44.1,195.7 L44.8,195.3 L45.5,194.8 L46.1,194.4 L46.8,194.0 L47.5,193.5 L48.2,193.1 L48.8,192.7 L49.5,192.2 L50.2,191.8 L50.8,191.4 L51.5,190.9 L52.2,190.5 L52.9,190.0 L53.5,189.6 L54.2,189.2 L54.9,188.7 L55.5,188.3 L56.2,187.9 L56.9,187.4 L57.5,187.0 L58.2,186.6 L58.9,186.1 L59.5,185.7 L60.2,185.3 L60.9,184.8 L61.6,184.4 L62.2,183.9 L62.9,183.5 L63.6,183.1 L64.2,182.6 L64.9,182.2 L65.6,181.8 L66.2,181.3 L66.9,180.9 L67.6,180.5 L68.3,180.0 L68.9,179.6 L69.6,179.2 L70.3,178.7 L70.9,178.3 L71.6,177.8 L72.3,177.4 L73.0,177.0 L73.6,176.5 L74.3,176.1 L75.0,175.7 L75.6,175.2 L76.3,174.8 L77.0,174.4 L77.6,173.9 L78.3,173.5 L79.0,173.1 L79.7,172.6 L80.3,172.2 L81.0,171.8 L81.7,171.3 L82.3,170.9 L83.0,170.4 L83.7,170.0 L84.3,169.6 L85.0,169.1 L85.7,168.7 L86.4,168.3 L87.0,167.8 L87.7,167.4 L88.4,167.0 L89.0,166.5 L89.7,166.1 L90.4,165.7 L91.0,165.2 L91.7,164.8 L92.4,164.3 L93.0,163.9 L93.7,163.5 L94.4,163.0 L95.1,162.6 L95.7,162.2 L96.4,161.7 L97.1,161.3 L97.7,160.9 L98.4,160.4 L99.1,160.0 L99.8,159.6 L100.4,159.1 L101.1,158.7 L101.8,158.2 L102.4,157.8 L103.1,157.4 L103.8,156.9 L104.4,156.5 L105.1,156.1 L105.8,155.6 L106.5,155.2 L107.1,154.8 L107.8,154.3 L108.5,153.9 L109.1,153.5 L109.8,153.0 L110.5,152.6 L111.1,152.2 L111.8,151.7 L112.5,151.3 L113.1,150.8 L113.8,150.4 L114.5,150.0 L115.2,149.5 L115.8,149.1 L116.5,148.7 L117.2,148.2 L117.8,147.8 L118.5,147.4 L119.2,146.9 L119.9,146.5 L120.5,146.1 L121.2,145.6 L121.9,145.2 L122.5,144.7 L123.2,144.3 L123.9,143.9 L124.5,143.4 L125.2,143.0 L125.9,142.6 L126.5,142.1 L127.2,141.7 L127.9,141.3 L128.6,140.8 L129.2,140.4 L129.9,140.0 L130.6,139.5 L131.2,139.1 L131.9,138.6 L132.6,138.2 L133.2,137.8 L133.9,137.3 L134.6,136.9 L135.3,136.5 L135.9,136.0 L136.6,135.6 L137.3,135.2 L137.9,134.7 L138.6,134.3 L139.3,133.9 L139.9,133.4 L140.6,133.0 L141.3,132.6 L142.0,132.1 L142.6,131.7 L143.3,131.2 L144.0,130.8 L144.6,130.4 L145.3,129.9 L146.0,129.5 L146.7,129.1 L147.3,128.6 L148.0,128.2 L148.7,127.8 L149.3,127.3 L150.0,126.9 L150.7,126.5 L151.3,126.0 L152.0,125.6 L152.7,125.1 L153.3,124.7 L154.0,124.3 L154.7,123.8 L155.4,123.4 L156.0,123.0 L156.7,122.5 L157.4,122.1 L158.0,121.7 L158.7,121.2 L159.4,120.8 L160.0,120.4 L160.7,119.9 L161.4,119.5 L162.1,119.0 L162.7,118.6 L163.4,118.2 L164.1,117.7 L164.7,117.3 L165.4,116.9 L166.1,116.4 L166.8,116.0 L167.4,115.6 L168.1,115.1 L168.8,114.7 L169.4,114.3 L170.1,113.8 L170.8,113.4 L171.4,113.0 L172.1,112.5 L172.8,112.1 L173.5,111.6 L174.1,111.2 L174.8,110.8 L175.5,110.3 L176.1,109.9 L176.8,109.5 L177.5,109.0 L178.1,108.6 L178.8,108.2 L179.5,107.7 L180.2,107.3 L180.8,106.9 L181.5,106.4 L182.2,106.0 L182.8,105.5 L183.5,105.1 L184.2,104.7 L184.8,104.2 L185.5,103.8 L186.2,103.4 L186.8,102.9 L187.5,102.5 L188.2,102.1 L188.9,101.6 L189.5,101.2 L190.2,100.8 L190.9,100.3 L191.5,99.9 L192.2,99.4 L192.9,99.0 L193.5,98.6 L194.2,98.1 L194.9,97.7 L195.6,97.3 L196.2,96.8 L196.9,96.4 L197.6,96.0 L198.2,95.5 L198.9,95.1 L199.6,94.7 L200.2,94.2 L200.9,93.8 L201.6,93.4 L202.3,92.9 L202.9,92.5 L203.6,92.0 L204.3,91.6 L204.9,91.2 L205.6,90.7 L206.3,90.3 L207.0,89.9 L207.6,89.4 L208.3,89.0 L209.0,88.6 L209.6,88.1 L210.3,87.7 L211.0,87.3 L211.6,86.8 L212.3,86.4 L213.0,85.9 L213.7,85.5 L214.3,85.1 L215.0,84.6 L215.7,84.2 L216.3,83.8 L217.0,83.3 L217.7,82.9 L218.3,82.5 L219.0,82.0 L219.7,81.6 L220.3,81.2 L221.0,80.7 L221.7,80.3 L222.4,79.8 L223.0,79.4 L223.7,79.0 L224.4,78.5 L225.0,78.1 L225.7,77.7 L226.4,77.2 L227.0,76.8 L227.7,76.4 L228.4,75.9 L229.1,75.5 L229.7,75.1 L230.4,74.6 L231.1,74.2 L231.7,73.8 L232.4,73.3 L233.1,72.9 L233.8,72.4 L234.4,72.0 L235.1,71.6 L235.8,71.1 L236.4,70.7 L237.1,70.3 L237.8,69.8 L238.4,69.4 L239.1,69.0 L239.8,68.5 L240.5,68.1 L241.1,67.7 L241.8,67.2 L242.5,66.8 L243.1,66.3 L243.8,65.9 L244.5,65.5 L245.1,65.0 L245.8,64.6 L246.5,64.2 L247.2,63.7 L247.8,63.3 L248.5,62.9 L249.2,62.4 L249.8,62.0 L250.5,61.6 L251.2,61.1 L251.8,60.7 L252.5,60.2 L253.2,59.8 L253.8,59.4 L254.5,58.9 L255.2,58.5 L255.9,58.1 L256.5,57.6 L257.2,57.2 L257.9,56.8 L258.5,56.3 L259.2,55.9 L259.9,55.5 L260.5,55.0 L261.2,54.6 L261.9,54.2 L262.6,53.7 L263.2,53.3 L263.9,52.8 L264.6,52.4 L265.2,52.0 L265.9,51.5 L266.6,51.1 L267.2,50.7 L267.9,50.2 L268.6,49.8 L269.3,49.4 L269.9,48.9 L270.6,48.5 L271.3,48.1 L271.9,47.6 L272.6,47.2 L273.3,46.7 L273.9,46.3 L274.6,45.9 L275.3,45.4 L276.0,45.0 L276.6,44.6 L277.3,44.1 L278.0,43.7 L278.6,43.3 L279.3,42.8 L280.0,42.4 L280.7,42.0 L281.3,41.5 L282.0,41.1 L282.7,40.6 L283.3,40.2 L284.0,39.8\" clip-path=\"url(#c79918)\" style=\"fill:none;stroke:var(--accent-text);stroke-width:2.2;stroke-dasharray:6 4\"/><text x=\"42.8\" y=\"189.6\" text-anchor=\"middle\" style=\"fill:var(--accent-text);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x + 2</text><circle cx=\"116.5\" cy=\"148.7\" r=\"3.4\" style=\"fill:var(--ink)\"/><text class=\"lb\" x=\"122.5\" y=\"139.7\" text-anchor=\"start\" dominant-baseline=\"middle\">(−1, 1)</text><circle cx=\"217.0\" cy=\"83.3\" r=\"3.4\" style=\"fill:var(--ink)\"/><text class=\"lb\" x=\"223.0\" y=\"74.3\" text-anchor=\"start\" dominant-baseline=\"middle\">(2, 4)</text></svg><p>A line and a parabola can meet in <b>0, 1 or 2</b> points. Two different parabolas can also meet in 0, 1 or 2 points.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Method</th><th>How</th></tr><tr><td>Graphing</td><td>Graph both equations and read the intersection points; check them.</td></tr><tr><td>Substitution</td><td>Solve one equation for y (or x) and substitute into the other; you get a quadratic equation in one variable.</td></tr><tr><td>Elimination</td><td>Subtract the equations so that y cancels, then solve the quadratic that remains.</td></tr></table></div><div class=\"ex\"><div class=\"exh\">Worked example 1 · Substitution</div><div class=\"exl\">Solve y = x² and y = x + 2.<br>x² = x + 2 → x² − x − 2 = 0 → (x − 2)(x + 1) = 0.<br>x = 2 gives y = 4; x = −1 gives y = 1. Solutions: <b>(2, 4) and (−1, 1)</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 2 · Elimination</div><div class=\"exl\">Solve y = x² + 2x − 1 and y = −x² + 3.<br>Subtract: 0 = 2x² + 2x − 4, so x² + x − 2 = 0 and x = 1 or x = −2.<br>y = 1 + 2 − 1 = 2 and y = 4 − 4 − 1 = −1. Solutions: <b>(1, 2) and (−2, −1)</b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example 3 · No solution</div><div class=\"exl\">Solve y = x² + 3 and y = 2x.<br>x² − 2x + 3 = 0 has discriminant 4 − 12 = −8 &lt; 0.<br>The line misses the parabola: <b>no solution</b>.</div></div><h4>Approximating solutions</h4><p>To solve an equation such as x² − 1 = −x + 2, graph y = x² − 1 and y = −x + 2: the x-coordinates of the intersection points are the solutions. When they are not integers, use the Quadratic Formula or a graphing calculator’s <i>intersect</i> feature and round.</p><div class=\"ex\"><div class=\"exh\">Worked example 4 · Real life</div><div class=\"exl\">A company’s revenue is R = −x² + 14x and its cost is C = 4x + 16 (thousands of dollars, x thousand items). Find the break-even points.<br>−x² + 14x = 4x + 16 → x² − 10x + 16 = 0 → (x − 2)(x − 8) = 0.<br>Break-even at <b>2 thousand and 8 thousand items</b>.</div></div><div class=\"keybox\"><b>Common mistake.</b> After finding x, substitute back to get y, and write each solution as a <b>point</b>. Use the simpler equation (often the linear one) to find y, then check the point in the other equation.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 9.6 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>I can use the Product and Quotient Properties of Square Roots to simplify radicals, rationalize denominators, and add, subtract and multiply radical expressions.</li><li>I can solve a quadratic equation by graphing, find the zeros of a quadratic function, and estimate solutions that are not integers.</li><li>I can solve equations of the form ax² + c = 0 and a(x − h)² = k by taking square roots, and approximate the solutions.</li><li>I can complete the square, solve quadratic equations by completing the square, and use it to write a quadratic function in vertex form.</li><li>I can solve any quadratic equation with the Quadratic Formula, use the discriminant to count real solutions, and choose an efficient method.</li><li>I can solve a system of a linear and a quadratic equation (or two quadratics) by graphing, substitution or elimination.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s7\">Assessment A</button><button class=\"hub-btn\" data-go=\"s8\">Assessment B</button><button class=\"hub-btn\" data-go=\"s9\">Assessment C</button><button class=\"hub-btn\" data-go=\"s10\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s7", "A", "Knowing and understanding"], ["s8", "B", "Investigating patterns"], ["s9", "C", "Communicating"], ["s10", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "9.1 Properties of Radicals", "sub": "I can use the Product and Quotient Properties of Square Roots to simplify radicals, rationalize denominators, and add, subtract and multiply radical expressions.", "slides": [{"kind": "mcq", "text": "Simplify √72.", "opts": ["36√2", "6√3", "6√2", "2√6"], "correct": 2, "tag": "", "sol": "72 = 36 · 2 and 36 is the largest perfect-square factor. √72 = √36 · √2 = 6√2. (2√6 and 6√3 do not equal √72: (2√6)² = 24 and (6√3)² = 108.)"}, {"kind": "blank", "p": "Write each radical in simplest form a√b.", "tag": "", "marks": "", "flat": [{"t": "a) √50 = __B1__√__B2__", "a": {"B1": "5", "B2": "2"}}, {"t": "b) √108 = __B1__√__B2__", "a": {"B1": "6", "B2": "3"}}, {"t": "c) √180 = __B1__√__B2__", "a": {"B1": "6", "B2": "5"}}], "sol": "50 = 25 · 2, so √50 = 5√2.\n108 = 36 · 3, so √108 = 6√3.\n180 = 36 · 5, so √180 = 6√5."}, {"kind": "mcq", "text": "Simplify √(45/4).", "opts": ["(3√5)/2", "(9√5)/2", "(5√3)/2", "(3√5)/4"], "correct": 0, "tag": "", "sol": "Quotient Property: √45 / √4. √45 = √9 · √5 = 3√5 and √4 = 2, so the answer is (3√5)/2. ((3√5)/4 forgets to take the square root of 4.)"}, {"kind": "blank", "p": "Simplify the cube roots.", "tag": "", "marks": "", "flat": [{"t": "a) ∛54 = __B1__∛__B2__", "a": {"B1": "3", "B2": "2"}}, {"t": "b) ∛(−16) = __B1__∛__B2__", "a": {"B1": "-2", "B2": "2"}}, {"t": "c) ∛(27/8) = __B1__", "a": {"B1": "3/2"}, "accept": ["1.5"]}], "sol": "54 = 27 · 2 and ∛27 = 3, so ∛54 = 3∛2.\n−16 = (−8) · 2 and ∛(−8) = −2, so ∛(−16) = −2∛2.\n∛27 / ∛8 = 3/2."}, {"kind": "mcq", "text": "Simplify 6 / √3.", "opts": ["2√3", "6√3", "2√6", "√2"], "correct": 0, "tag": "", "sol": "Multiply by √3 / √3: 6√3 / 3 = 2√3. (6√3 forgets that the denominator becomes 3.)"}, {"kind": "blank", "p": "Rationalize the denominator of 5 / √10.", "tag": "", "marks": "", "flat": [{"t": "Multiply top and bottom by √10: 5 / √10 = 5√10 / __B1__", "a": {"B1": "10"}}, {"t": "Simplify: 5√10 / 10 = √10 / __B1__", "a": {"B1": "2"}}], "sol": "√10 · √10 = 10, so the denominator becomes 10.\nDivide 5 and 10 by 5: √10 / 2."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Ravi wrote √(9 + 16) = √9 + √16 = 7. Which is correct?", "opts": ["√(9 + 16) = 9 + 16 = 25", "√(9 + 16) = √9 · √16 = 12", "Ravi is correct: the answer is 7", "√(9 + 16) = √25 = 5"], "correct": 3, "tag": "", "sol": "Add inside the radical first: 9 + 16 = 25 and √25 = 5. The Product Property splits products, not sums, so √(a + b) ≠ √a + √b."}, {"kind": "blank", "p": "Simplify 4 / (3 − √5) using the conjugate.", "tag": "", "marks": "", "flat": [{"t": "The conjugate of 3 − √5 is 3 + √__B1__", "a": {"B1": "5"}}, {"t": "The new denominator is 3² − (√5)² = __B1__", "a": {"B1": "4"}}, {"t": "4 / (3 − √5) = __B1__", "a": {"B1": "3+√5"}, "expr": "calc", "accept": ["√5+3"]}], "sol": "Change the sign between the terms: 3 + √5.\n(3 − √5)(3 + √5) = 9 − 5 = 4.\n4(3 + √5) / 4 = 3 + √5."}, {"kind": "mcq", "text": "Simplify 3√2 + 5√8.", "opts": ["13√2", "13√4", "8√10", "8√2"], "correct": 0, "tag": "", "sol": "√8 = 2√2, so 5√8 = 10√2. Then 3√2 + 10√2 = 13√2. (8√10 adds the radicands, which is never allowed.)"}, {"kind": "blank", "p": "Simplify 4√3 − √27 + 2√12.", "tag": "", "marks": "", "flat": [{"t": "√27 = __B1__√3", "a": {"B1": "3"}}, {"t": "2√12 = __B1__√3", "a": {"B1": "4"}}, {"t": "4√3 − √27 + 2√12 = __B1__√3", "a": {"B1": "5"}}], "sol": "27 = 9 · 3, so √27 = 3√3.\n√12 = 2√3, so 2√12 = 4√3.\n4√3 − 3√3 + 4√3 = 5√3."}, {"kind": "mcq", "text": "Simplify √6 · √15.", "opts": ["9√10", "√21", "3√10", "10√3"], "correct": 2, "tag": "", "sol": "√6 · √15 = √90 = √9 · √10 = 3√10. (√21 adds 6 and 15 instead of multiplying.)"}, {"kind": "blank", "p": "A square floor tile has an area of 180 cm².", "tag": "", "marks": "", "flat": [{"t": "Exact side length: __B1__√__B2__ cm", "a": {"B1": "6", "B2": "5"}}, {"t": "Side length to 1 decimal place: __B1__ cm", "a": {"B1": "13.4"}}], "sol": "s² = 180, so s = √180 = √36 · √5 = 6√5 cm.\n6√5 ≈ 6 × 2.236 ≈ 13.4 cm.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "The time t (seconds) for an object to fall h feet is t = √(h/16). How long does it take to fall 48 feet?", "opts": ["3 s", "√(1/3) ≈ 0.58 s", "4√3 ≈ 6.93 s", "√3 ≈ 1.73 s"], "correct": 3, "tag": "", "sol": "t = √(48/16) = √3 ≈ 1.73 s. (3 s forgets the square root; 4√3 comes from √48.)", "tools": ["calc"], "desmos": []}, {"kind": "blank", "p": "Multiply and simplify.", "tag": "", "marks": "", "flat": [{"t": "(2 + √3)(2 − √3) = __B1__", "a": {"B1": "1"}}, {"t": "(1 + √2)² = __B1__ + __B2__√2", "a": {"B1": "3", "B2": "2"}}], "sol": "Conjugates: 2² − (√3)² = 4 − 3 = 1.\n(1 + √2)(1 + √2) = 1 + √2 + √2 + 2 = 3 + 2√2."}]}, {"id": "s2", "label": "9.2 Solving by Graphing", "sub": "I can solve a quadratic equation by graphing, find the zeros of a quadratic function, and estimate solutions that are not integers.", "slides": [{"kind": "mcq", "text": "The graph of y = x² − x − 6 is shown. What are the solutions of x² − x − 6 = 0?", "opts": ["x = 2 and x = −3", "x = −6 only", "x = −2 and x = 3", "x = {1/2} only"], "correct": 2, "tag": "", "sol": "The solutions are the x-intercepts: the graph crosses the x-axis at −2 and 3. Check: 4 + 2 − 6 = 0 ✓ and 9 − 3 − 6 = 0 ✓ (−6 is the y-intercept and {1/2} is the axis of symmetry.)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"42.8\" y1=\"214.0\" x2=\"42.8\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"69.6\" y1=\"214.0\" x2=\"69.6\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"96.4\" y1=\"214.0\" x2=\"96.4\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"123.2\" y1=\"214.0\" x2=\"123.2\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"176.8\" y1=\"214.0\" x2=\"176.8\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"203.6\" y1=\"214.0\" x2=\"203.6\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"230.4\" y1=\"214.0\" x2=\"230.4\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"257.2\" y1=\"214.0\" x2=\"257.2\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"198.2\" x2=\"284.0\" y2=\"198.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"182.3\" x2=\"284.0\" y2=\"182.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"166.5\" x2=\"284.0\" y2=\"166.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"150.6\" x2=\"284.0\" y2=\"150.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"134.8\" x2=\"284.0\" y2=\"134.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"118.9\" x2=\"284.0\" y2=\"118.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"103.1\" x2=\"284.0\" y2=\"103.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"87.2\" x2=\"284.0\" y2=\"87.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"71.4\" x2=\"284.0\" y2=\"71.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"55.5\" x2=\"284.0\" y2=\"55.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"39.7\" x2=\"284.0\" y2=\"39.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"23.8\" x2=\"284.0\" y2=\"23.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"8.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"103.1\" x2=\"284.0\" y2=\"103.1\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"8.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"112.1\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"69.6\" y=\"112.1\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"123.2\" y=\"112.1\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"176.8\" y=\"112.1\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"230.4\" y=\"112.1\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"284.0\" y=\"112.1\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"146.0\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−7</text><text class=\"po\" x=\"146.0\" y=\"182.3\" text-anchor=\"end\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"146.0\" y=\"150.6\" text-anchor=\"end\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"146.0\" y=\"118.9\" text-anchor=\"end\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"146.0\" y=\"87.2\" text-anchor=\"end\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"146.0\" y=\"55.5\" text-anchor=\"end\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"146.0\" y=\"23.8\" text-anchor=\"end\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"280.0\" y=\"95.1\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"158.0\" y=\"14.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c82199\"><rect x=\"16.0\" y=\"8.0\" width=\"268.0\" height=\"206.0\"/></clipPath><path d=\"M16.0,-277.2 L16.7,-272.9 L17.3,-268.6 L18.0,-264.2 L18.7,-260.0 L19.4,-255.7 L20.0,-251.4 L20.7,-247.2 L21.4,-243.0 L22.0,-238.8 L22.7,-234.6 L23.4,-230.5 L24.0,-226.4 L24.7,-222.3 L25.4,-218.2 L26.0,-214.1 L26.7,-210.0 L27.4,-206.0 L28.1,-202.0 L28.7,-198.0 L29.4,-194.0 L30.1,-190.1 L30.7,-186.2 L31.4,-182.2 L32.1,-178.4 L32.8,-174.5 L33.4,-170.6 L34.1,-166.8 L34.8,-163.0 L35.4,-159.2 L36.1,-155.4 L36.8,-151.7 L37.4,-147.9 L38.1,-144.2 L38.8,-140.5 L39.5,-136.8 L40.1,-133.2 L40.8,-129.6 L41.5,-125.9 L42.1,-122.3 L42.8,-118.8 L43.5,-115.2 L44.1,-111.7 L44.8,-108.2 L45.5,-104.7 L46.2,-101.2 L46.8,-97.7 L47.5,-94.3 L48.2,-90.9 L48.8,-87.5 L49.5,-84.1 L50.2,-80.7 L50.8,-77.4 L51.5,-74.1 L52.2,-70.8 L52.9,-67.5 L53.5,-64.3 L54.2,-61.0 L54.9,-57.8 L55.5,-54.6 L56.2,-51.4 L56.9,-48.3 L57.5,-45.1 L58.2,-42.0 L58.9,-38.9 L59.6,-35.8 L60.2,-32.8 L60.9,-29.7 L61.6,-26.7 L62.2,-23.7 L62.9,-20.7 L63.6,-17.8 L64.2,-14.8 L64.9,-11.9 L65.6,-9.0 L66.2,-6.1 L66.9,-3.3 L67.6,-0.4 L68.3,2.4 L68.9,5.2 L69.6,8.0 L70.3,10.8 L70.9,13.5 L71.6,16.2 L72.3,18.9 L72.9,21.6 L73.6,24.3 L74.3,26.9 L75.0,29.6 L75.6,32.2 L76.3,34.7 L77.0,37.3 L77.6,39.9 L78.3,42.4 L79.0,44.9 L79.7,47.4 L80.3,49.8 L81.0,52.3 L81.7,54.7 L82.3,57.1 L83.0,59.5 L83.7,61.9 L84.3,64.2 L85.0,66.5 L85.7,68.8 L86.4,71.1 L87.0,73.4 L87.7,75.7 L88.4,77.9 L89.0,80.1 L89.7,82.3 L90.4,84.4 L91.0,86.6 L91.7,88.7 L92.4,90.8 L93.0,92.9 L93.7,95.0 L94.4,97.0 L95.1,99.1 L95.7,101.1 L96.4,103.1 L97.1,105.0 L97.7,107.0 L98.4,108.9 L99.1,110.8 L99.8,112.7 L100.4,114.6 L101.1,116.5 L101.8,118.3 L102.4,120.1 L103.1,121.9 L103.8,123.7 L104.4,125.4 L105.1,127.2 L105.8,128.9 L106.5,130.6 L107.1,132.2 L107.8,133.9 L108.5,135.5 L109.1,137.1 L109.8,138.7 L110.5,140.3 L111.1,141.9 L111.8,143.4 L112.5,144.9 L113.1,146.4 L113.8,147.9 L114.5,149.3 L115.2,150.8 L115.8,152.2 L116.5,153.6 L117.2,155.0 L117.8,156.3 L118.5,157.7 L119.2,159.0 L119.9,160.3 L120.5,161.5 L121.2,162.8 L121.9,164.0 L122.5,165.3 L123.2,166.5 L123.9,167.6 L124.5,168.8 L125.2,169.9 L125.9,171.1 L126.5,172.2 L127.2,173.2 L127.9,174.3 L128.6,175.3 L129.2,176.4 L129.9,177.4 L130.6,178.3 L131.2,179.3 L131.9,180.2 L132.6,181.2 L133.2,182.1 L133.9,182.9 L134.6,183.8 L135.3,184.6 L135.9,185.5 L136.6,186.3 L137.3,187.1 L137.9,187.8 L138.6,188.6 L139.3,189.3 L139.9,190.0 L140.6,190.7 L141.3,191.3 L142.0,192.0 L142.6,192.6 L143.3,193.2 L144.0,193.8 L144.6,194.4 L145.3,194.9 L146.0,195.4 L146.7,195.9 L147.3,196.4 L148.0,196.9 L148.7,197.3 L149.3,197.7 L150.0,198.2 L150.7,198.5 L151.3,198.9 L152.0,199.3 L152.7,199.6 L153.3,199.9 L154.0,200.2 L154.7,200.4 L155.4,200.7 L156.0,200.9 L156.7,201.1 L157.4,201.3 L158.0,201.5 L158.7,201.6 L159.4,201.8 L160.0,201.9 L160.7,202.0 L161.4,202.0 L162.1,202.1 L162.7,202.1 L163.4,202.1 L164.1,202.1 L164.7,202.1 L165.4,202.0 L166.1,202.0 L166.8,201.9 L167.4,201.8 L168.1,201.6 L168.8,201.5 L169.4,201.3 L170.1,201.1 L170.8,200.9 L171.4,200.7 L172.1,200.4 L172.8,200.2 L173.5,199.9 L174.1,199.6 L174.8,199.3 L175.5,198.9 L176.1,198.5 L176.8,198.2 L177.5,197.7 L178.1,197.3 L178.8,196.9 L179.5,196.4 L180.2,195.9 L180.8,195.4 L181.5,194.9 L182.2,194.4 L182.8,193.8 L183.5,193.2 L184.2,192.6 L184.8,192.0 L185.5,191.3 L186.2,190.7 L186.8,190.0 L187.5,189.3 L188.2,188.6 L188.9,187.8 L189.5,187.1 L190.2,186.3 L190.9,185.5 L191.5,184.6 L192.2,183.8 L192.9,182.9 L193.5,182.1 L194.2,181.2 L194.9,180.2 L195.6,179.3 L196.2,178.3 L196.9,177.4 L197.6,176.4 L198.2,175.3 L198.9,174.3 L199.6,173.2 L200.2,172.2 L200.9,171.1 L201.6,169.9 L202.3,168.8 L202.9,167.6 L203.6,166.5 L204.3,165.3 L204.9,164.0 L205.6,162.8 L206.3,161.5 L207.0,160.3 L207.6,159.0 L208.3,157.7 L209.0,156.3 L209.6,155.0 L210.3,153.6 L211.0,152.2 L211.6,150.8 L212.3,149.3 L213.0,147.9 L213.7,146.4 L214.3,144.9 L215.0,143.4 L215.7,141.9 L216.3,140.3 L217.0,138.7 L217.7,137.1 L218.3,135.5 L219.0,133.9 L219.7,132.2 L220.3,130.6 L221.0,128.9 L221.7,127.2 L222.4,125.4 L223.0,123.7 L223.7,121.9 L224.4,120.1 L225.0,118.3 L225.7,116.5 L226.4,114.6 L227.0,112.7 L227.7,110.8 L228.4,108.9 L229.1,107.0 L229.7,105.0 L230.4,103.1 L231.1,101.1 L231.7,99.1 L232.4,97.0 L233.1,95.0 L233.8,92.9 L234.4,90.8 L235.1,88.7 L235.8,86.6 L236.4,84.4 L237.1,82.3 L237.8,80.1 L238.4,77.9 L239.1,75.7 L239.8,73.4 L240.5,71.1 L241.1,68.8 L241.8,66.5 L242.5,64.2 L243.1,61.9 L243.8,59.5 L244.5,57.1 L245.1,54.7 L245.8,52.3 L246.5,49.8 L247.2,47.4 L247.8,44.9 L248.5,42.4 L249.2,39.9 L249.8,37.3 L250.5,34.7 L251.2,32.2 L251.8,29.6 L252.5,26.9 L253.2,24.3 L253.8,21.6 L254.5,18.9 L255.2,16.2 L255.9,13.5 L256.5,10.8 L257.2,8.0 L257.9,5.2 L258.5,2.4 L259.2,-0.4 L259.9,-3.3 L260.5,-6.1 L261.2,-9.0 L261.9,-11.9 L262.6,-14.8 L263.2,-17.8 L263.9,-20.7 L264.6,-23.7 L265.2,-26.7 L265.9,-29.7 L266.6,-32.8 L267.2,-35.8 L267.9,-38.9 L268.6,-42.0 L269.3,-45.1 L269.9,-48.3 L270.6,-51.4 L271.3,-54.6 L271.9,-57.8 L272.6,-61.0 L273.3,-64.3 L273.9,-67.5 L274.6,-70.8 L275.3,-74.1 L276.0,-77.4 L276.6,-80.7 L277.3,-84.1 L278.0,-87.5 L278.6,-90.9 L279.3,-94.3 L280.0,-97.7 L280.7,-101.2 L281.3,-104.7 L282.0,-108.2 L282.7,-111.7 L283.3,-115.2 L284.0,-118.8\" clip-path=\"url(#c82199)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"254.5\" y=\"11.9\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x² − x − 6</text></svg>"}, {"kind": "blank", "p": "Solve x² − 4x + 3 = 0 by graphing y = x² − 4x + 3.", "tag": "", "marks": "", "flat": [{"t": "Axis of symmetry: x = __B1__", "a": {"B1": "2"}}, {"t": "Vertex: (2, __B1__)", "a": {"B1": "-1"}}, {"t": "Solutions: x = __B1__", "a": {"B1": "1, 3"}, "expr": "set"}], "sol": "x = −b ÷ (2a) = 4 ÷ 2 = 2.\ny = 4 − 8 + 3 = −1.\nThe parabola opens up from (2, −1) and crosses the x-axis at x = 1 and x = 3 (1 − 4 + 3 = 0 and 9 − 12 + 3 = 0).", "tools": ["desmos"], "desmos": ["y=x^{2}-4x+3"]}, {"kind": "mcq", "text": "The graph of y = x² + 4x + 4 is shown. How many solutions does x² + 4x + 4 = 0 have?", "opts": ["Two: x = 2 and x = −2", "One: x = 2", "None", "One: x = −2"], "correct": 3, "tag": "", "sol": "The vertex (−2, 0) touches the x-axis, so there is exactly one solution, x = −2. Check: 4 − 8 + 4 = 0 ✓", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"45.8\" y1=\"214.0\" x2=\"45.8\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"75.6\" y1=\"214.0\" x2=\"75.6\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"105.3\" y1=\"214.0\" x2=\"105.3\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"164.9\" y1=\"214.0\" x2=\"164.9\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"194.7\" y1=\"214.0\" x2=\"194.7\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"224.4\" y1=\"214.0\" x2=\"224.4\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"254.2\" y1=\"214.0\" x2=\"254.2\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"191.1\" x2=\"284.0\" y2=\"191.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"168.2\" x2=\"284.0\" y2=\"168.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"145.3\" x2=\"284.0\" y2=\"145.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"122.4\" x2=\"284.0\" y2=\"122.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"99.6\" x2=\"284.0\" y2=\"99.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"76.7\" x2=\"284.0\" y2=\"76.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"53.8\" x2=\"284.0\" y2=\"53.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"30.9\" x2=\"284.0\" y2=\"30.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"8.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"168.2\" x2=\"284.0\" y2=\"168.2\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"194.7\" y1=\"214.0\" x2=\"194.7\" y2=\"8.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"177.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">−6</text><text class=\"po\" x=\"75.6\" y=\"177.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"135.1\" y=\"177.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"254.2\" y=\"177.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"190.7\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"190.7\" y=\"122.4\" text-anchor=\"end\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"190.7\" y=\"76.7\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"190.7\" y=\"30.9\" text-anchor=\"end\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"280.0\" y=\"160.2\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"202.7\" y=\"14.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c26070\"><rect x=\"16.0\" y=\"8.0\" width=\"268.0\" height=\"206.0\"/></clipPath><path d=\"M16.0,-198.0 L16.7,-193.9 L17.3,-189.8 L18.0,-185.7 L18.7,-181.7 L19.3,-177.7 L20.0,-173.7 L20.7,-169.7 L21.4,-165.8 L22.0,-161.9 L22.7,-158.0 L23.4,-154.1 L24.0,-150.2 L24.7,-146.4 L25.4,-142.6 L26.1,-138.8 L26.7,-135.0 L27.4,-131.3 L28.1,-127.6 L28.7,-123.9 L29.4,-120.2 L30.1,-116.6 L30.7,-113.0 L31.4,-109.4 L32.1,-105.8 L32.8,-102.2 L33.4,-98.7 L34.1,-95.2 L34.8,-91.7 L35.4,-88.3 L36.1,-84.8 L36.8,-81.4 L37.4,-78.0 L38.1,-74.7 L38.8,-71.3 L39.4,-68.0 L40.1,-64.7 L40.8,-61.4 L41.5,-58.2 L42.1,-54.9 L42.8,-51.7 L43.5,-48.6 L44.1,-45.4 L44.8,-42.3 L45.5,-39.2 L46.2,-36.1 L46.8,-33.0 L47.5,-30.0 L48.2,-26.9 L48.8,-23.9 L49.5,-21.0 L50.2,-18.0 L50.8,-15.1 L51.5,-12.2 L52.2,-9.3 L52.8,-6.5 L53.5,-3.6 L54.2,-0.8 L54.9,2.0 L55.5,4.7 L56.2,7.5 L56.9,10.2 L57.5,12.9 L58.2,15.6 L58.9,18.2 L59.6,20.8 L60.2,23.4 L60.9,26.0 L61.6,28.6 L62.2,31.1 L62.9,33.6 L63.6,36.1 L64.2,38.6 L64.9,41.0 L65.6,43.4 L66.2,45.8 L66.9,48.2 L67.6,50.5 L68.3,52.9 L68.9,55.2 L69.6,57.4 L70.3,59.7 L70.9,61.9 L71.6,64.1 L72.3,66.3 L72.9,68.5 L73.6,70.6 L74.3,72.7 L75.0,74.8 L75.6,76.9 L76.3,78.9 L77.0,81.0 L77.6,83.0 L78.3,84.9 L79.0,86.9 L79.7,88.8 L80.3,90.7 L81.0,92.6 L81.7,94.5 L82.3,96.3 L83.0,98.1 L83.7,99.9 L84.3,101.7 L85.0,103.4 L85.7,105.1 L86.3,106.8 L87.0,108.5 L87.7,110.2 L88.4,111.8 L89.0,113.4 L89.7,115.0 L90.4,116.6 L91.0,118.1 L91.7,119.6 L92.4,121.1 L93.0,122.6 L93.7,124.0 L94.4,125.4 L95.1,126.8 L95.7,128.2 L96.4,129.5 L97.1,130.9 L97.7,132.2 L98.4,133.5 L99.1,134.7 L99.8,135.9 L100.4,137.2 L101.1,138.3 L101.8,139.5 L102.4,140.7 L103.1,141.8 L103.8,142.9 L104.4,143.9 L105.1,145.0 L105.8,146.0 L106.5,147.0 L107.1,148.0 L107.8,149.0 L108.5,149.9 L109.1,150.8 L109.8,151.7 L110.5,152.5 L111.1,153.4 L111.8,154.2 L112.5,155.0 L113.2,155.8 L113.8,156.5 L114.5,157.2 L115.2,157.9 L115.8,158.6 L116.5,159.3 L117.2,159.9 L117.8,160.5 L118.5,161.1 L119.2,161.7 L119.8,162.2 L120.5,162.7 L121.2,163.2 L121.9,163.7 L122.5,164.1 L123.2,164.6 L123.9,165.0 L124.5,165.3 L125.2,165.7 L125.9,166.0 L126.5,166.3 L127.2,166.6 L127.9,166.9 L128.6,167.1 L129.2,167.3 L129.9,167.5 L130.6,167.7 L131.2,167.8 L131.9,168.0 L132.6,168.1 L133.2,168.1 L133.9,168.2 L134.6,168.2 L135.3,168.2 L135.9,168.2 L136.6,168.2 L137.3,168.1 L137.9,168.0 L138.6,167.9 L139.3,167.8 L139.9,167.6 L140.6,167.4 L141.3,167.2 L142.0,167.0 L142.6,166.8 L143.3,166.5 L144.0,166.2 L144.6,165.9 L145.3,165.5 L146.0,165.2 L146.7,164.8 L147.3,164.4 L148.0,163.9 L148.7,163.5 L149.3,163.0 L150.0,162.5 L150.7,162.0 L151.3,161.4 L152.0,160.9 L152.7,160.3 L153.3,159.6 L154.0,159.0 L154.7,158.3 L155.4,157.6 L156.0,156.9 L156.7,156.2 L157.4,155.4 L158.0,154.7 L158.7,153.8 L159.4,153.0 L160.1,152.2 L160.7,151.3 L161.4,150.4 L162.1,149.5 L162.7,148.5 L163.4,147.6 L164.1,146.6 L164.7,145.6 L165.4,144.5 L166.1,143.5 L166.8,142.4 L167.4,141.3 L168.1,140.1 L168.8,139.0 L169.4,137.8 L170.1,136.6 L170.8,135.4 L171.4,134.2 L172.1,132.9 L172.8,131.6 L173.4,130.3 L174.1,128.9 L174.8,127.6 L175.5,126.2 L176.1,124.8 L176.8,123.4 L177.5,121.9 L178.1,120.4 L178.8,118.9 L179.5,117.4 L180.2,115.9 L180.8,114.3 L181.5,112.7 L182.2,111.1 L182.8,109.4 L183.5,107.8 L184.2,106.1 L184.8,104.4 L185.5,102.7 L186.2,100.9 L186.8,99.1 L187.5,97.3 L188.2,95.5 L188.9,93.6 L189.5,91.8 L190.2,89.9 L190.9,88.0 L191.5,86.0 L192.2,84.1 L192.9,82.1 L193.6,80.1 L194.2,78.0 L194.9,76.0 L195.6,73.9 L196.2,71.8 L196.9,69.7 L197.6,67.5 L198.2,65.4 L198.9,63.2 L199.6,60.9 L200.2,58.7 L200.9,56.4 L201.6,54.1 L202.3,51.8 L202.9,49.5 L203.6,47.1 L204.3,44.8 L204.9,42.4 L205.6,39.9 L206.3,37.5 L206.9,35.0 L207.6,32.5 L208.3,30.0 L209.0,27.4 L209.6,24.9 L210.3,22.3 L211.0,19.7 L211.6,17.0 L212.3,14.4 L213.0,11.7 L213.7,9.0 L214.3,6.3 L215.0,3.5 L215.7,0.7 L216.3,-2.1 L217.0,-4.9 L217.7,-7.7 L218.3,-10.6 L219.0,-13.5 L219.7,-16.4 L220.3,-19.3 L221.0,-22.3 L221.7,-25.3 L222.4,-28.3 L223.0,-31.3 L223.7,-34.4 L224.4,-37.4 L225.0,-40.5 L225.7,-43.7 L226.4,-46.8 L227.1,-50.0 L227.7,-53.2 L228.4,-56.4 L229.1,-59.6 L229.7,-62.9 L230.4,-66.2 L231.1,-69.5 L231.7,-72.8 L232.4,-76.2 L233.1,-79.5 L233.8,-82.9 L234.4,-86.4 L235.1,-89.8 L235.8,-93.3 L236.4,-96.8 L237.1,-100.3 L237.8,-103.8 L238.4,-107.4 L239.1,-111.0 L239.8,-114.6 L240.4,-118.2 L241.1,-121.9 L241.8,-125.5 L242.5,-129.2 L243.1,-133.0 L243.8,-136.7 L244.5,-140.5 L245.1,-144.3 L245.8,-148.1 L246.5,-151.9 L247.2,-155.8 L247.8,-159.7 L248.5,-163.6 L249.2,-167.5 L249.8,-171.5 L250.5,-175.5 L251.2,-179.5 L251.8,-183.5 L252.5,-187.5 L253.2,-191.6 L253.8,-195.7 L254.5,-199.8 L255.2,-204.0 L255.9,-208.1 L256.5,-212.3 L257.2,-216.5 L257.9,-220.8 L258.5,-225.0 L259.2,-229.3 L259.9,-233.6 L260.6,-237.9 L261.2,-242.3 L261.9,-246.7 L262.6,-251.1 L263.2,-255.5 L263.9,-259.9 L264.6,-264.4 L265.2,-268.9 L265.9,-273.4 L266.6,-277.9 L267.2,-282.5 L267.9,-287.1 L268.6,-291.7 L269.3,-296.3 L269.9,-301.0 L270.6,-305.6 L271.3,-310.3 L271.9,-315.1 L272.6,-319.8 L273.3,-324.6 L273.9,-329.4 L274.6,-334.2 L275.3,-339.0 L276.0,-343.9 L276.6,-348.8 L277.3,-353.7 L278.0,-358.6 L278.6,-363.5 L279.3,-368.5 L280.0,-373.5 L280.6,-378.5 L281.3,-383.6 L282.0,-388.7 L282.7,-393.7 L283.3,-398.9 L284.0,-404.0\" clip-path=\"url(#c26070)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"212.5\" y=\"14.7\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x² + 4x + 4</text></svg>"}, {"kind": "blank", "p": "Solve x² + 3 = 0 by graphing y = x² + 3.", "tag": "", "marks": "", "flat": [{"t": "The vertex is (0, __B1__)", "a": {"B1": "3"}}, {"t": "Number of real solutions: __B1__", "a": {"B1": "0"}, "accept": ["none", "zero", "no solutions", "no real solutions", "no solution"]}], "sol": "There is no x-term, so the axis is x = 0 and y = 0 + 3 = 3.\nThe parabola opens up from (0, 3), above the x-axis, so it never meets it: no real solutions."}, {"kind": "mcq", "text": "To solve x² = 2x + 8 by graphing, you first write it in standard form. What are the solutions?", "opts": ["x = −2 and x = 4", "x = −8 only", "x = 1 and x = 8", "x = 2 and x = −4"], "correct": 0, "tag": "", "sol": "Standard form: x² − 2x − 8 = 0. The graph of y = x² − 2x − 8 crosses the x-axis at −2 and 4. Check: 4 = −4 + 8 ✓ and 16 = 8 + 8 ✓", "tools": ["desmos"], "desmos": ["y=x^{2}-2x-8"]}, {"kind": "blank", "p": "The graph of f(x) = −x² + 6x − 5 is shown.", "tag": "", "marks": "", "flat": [{"t": "Zeros of f: x = __B1__", "a": {"B1": "1, 5"}, "expr": "set"}, {"t": "Maximum value of f: __B1__", "a": {"B1": "4"}}], "sol": "The graph crosses the x-axis at 1 and 5: f(1) = −1 + 6 − 5 = 0 and f(5) = −25 + 30 − 5 = 0.\nThe vertex is at x = 3: f(3) = −9 + 18 − 5 = 4.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"83.0\" y1=\"214.0\" x2=\"83.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"116.5\" y1=\"214.0\" x2=\"116.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"217.0\" y1=\"214.0\" x2=\"217.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"250.5\" y1=\"214.0\" x2=\"250.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"195.3\" x2=\"284.0\" y2=\"195.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"176.5\" x2=\"284.0\" y2=\"176.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"157.8\" x2=\"284.0\" y2=\"157.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"139.1\" x2=\"284.0\" y2=\"139.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"120.4\" x2=\"284.0\" y2=\"120.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"101.6\" x2=\"284.0\" y2=\"101.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"82.9\" x2=\"284.0\" y2=\"82.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"64.2\" x2=\"284.0\" y2=\"64.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"45.5\" x2=\"284.0\" y2=\"45.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"26.7\" x2=\"284.0\" y2=\"26.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"8.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"101.6\" x2=\"284.0\" y2=\"101.6\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"8.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"110.6\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"83.0\" y=\"110.6\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"150.0\" y=\"110.6\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"217.0\" y=\"110.6\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"284.0\" y=\"110.6\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><text class=\"po\" x=\"45.5\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−6</text><text class=\"po\" x=\"45.5\" y=\"176.5\" text-anchor=\"end\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"45.5\" y=\"139.1\" text-anchor=\"end\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"45.5\" y=\"64.2\" text-anchor=\"end\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"45.5\" y=\"26.7\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"280.0\" y=\"93.6\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"57.5\" y=\"14.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c49771\"><rect x=\"16.0\" y=\"8.0\" width=\"268.0\" height=\"206.0\"/></clipPath><path d=\"M16.0,326.4 L16.7,323.4 L17.3,320.4 L18.0,317.4 L18.7,314.5 L19.3,311.6 L20.0,308.7 L20.7,305.8 L21.4,302.9 L22.0,300.0 L22.7,297.1 L23.4,294.3 L24.0,291.5 L24.7,288.7 L25.4,285.9 L26.1,283.1 L26.7,280.3 L27.4,277.6 L28.1,274.9 L28.7,272.1 L29.4,269.4 L30.1,266.7 L30.7,264.1 L31.4,261.4 L32.1,258.8 L32.8,256.1 L33.4,253.5 L34.1,250.9 L34.8,248.3 L35.4,245.8 L36.1,243.2 L36.8,240.7 L37.4,238.2 L38.1,235.6 L38.8,233.1 L39.5,230.7 L40.1,228.2 L40.8,225.8 L41.5,223.3 L42.1,220.9 L42.8,218.5 L43.5,216.1 L44.1,213.7 L44.8,211.4 L45.5,209.0 L46.2,206.7 L46.8,204.4 L47.5,202.1 L48.2,199.8 L48.8,197.5 L49.5,195.3 L50.2,193.0 L50.8,190.8 L51.5,188.6 L52.2,186.4 L52.9,184.2 L53.5,182.1 L54.2,179.9 L54.9,177.8 L55.5,175.7 L56.2,173.5 L56.9,171.5 L57.5,169.4 L58.2,167.3 L58.9,165.3 L59.6,163.2 L60.2,161.2 L60.9,159.2 L61.6,157.2 L62.2,155.3 L62.9,153.3 L63.6,151.4 L64.2,149.5 L64.9,147.5 L65.6,145.7 L66.2,143.8 L66.9,141.9 L67.6,140.1 L68.3,138.2 L68.9,136.4 L69.6,134.6 L70.3,132.8 L70.9,131.0 L71.6,129.3 L72.3,127.5 L72.9,125.8 L73.6,124.1 L74.3,122.4 L75.0,120.7 L75.6,119.0 L76.3,117.4 L77.0,115.7 L77.6,114.1 L78.3,112.5 L79.0,110.9 L79.7,109.3 L80.3,107.7 L81.0,106.2 L81.7,104.7 L82.3,103.1 L83.0,101.6 L83.7,100.1 L84.3,98.7 L85.0,97.2 L85.7,95.8 L86.4,94.3 L87.0,92.9 L87.7,91.5 L88.4,90.1 L89.0,88.8 L89.7,87.4 L90.4,86.1 L91.0,84.7 L91.7,83.4 L92.4,82.1 L93.0,80.8 L93.7,79.6 L94.4,78.3 L95.1,77.1 L95.7,75.9 L96.4,74.7 L97.1,73.5 L97.7,72.3 L98.4,71.1 L99.1,70.0 L99.8,68.9 L100.4,67.7 L101.1,66.6 L101.8,65.6 L102.4,64.5 L103.1,63.4 L103.8,62.4 L104.4,61.4 L105.1,60.4 L105.8,59.4 L106.5,58.4 L107.1,57.4 L107.8,56.5 L108.5,55.5 L109.1,54.6 L109.8,53.7 L110.5,52.8 L111.1,51.9 L111.8,51.1 L112.5,50.2 L113.1,49.4 L113.8,48.6 L114.5,47.8 L115.2,47.0 L115.8,46.2 L116.5,45.5 L117.2,44.7 L117.8,44.0 L118.5,43.3 L119.2,42.6 L119.9,41.9 L120.5,41.2 L121.2,40.6 L121.9,39.9 L122.5,39.3 L123.2,38.7 L123.9,38.1 L124.5,37.5 L125.2,37.0 L125.9,36.4 L126.5,35.9 L127.2,35.4 L127.9,34.9 L128.6,34.4 L129.2,33.9 L129.9,33.5 L130.6,33.0 L131.2,32.6 L131.9,32.2 L132.6,31.8 L133.2,31.4 L133.9,31.0 L134.6,30.7 L135.3,30.4 L135.9,30.0 L136.6,29.7 L137.3,29.4 L137.9,29.2 L138.6,28.9 L139.3,28.6 L139.9,28.4 L140.6,28.2 L141.3,28.0 L142.0,27.8 L142.6,27.6 L143.3,27.5 L144.0,27.3 L144.6,27.2 L145.3,27.1 L146.0,27.0 L146.7,26.9 L147.3,26.8 L148.0,26.8 L148.7,26.8 L149.3,26.7 L150.0,26.7 L150.7,26.7 L151.3,26.8 L152.0,26.8 L152.7,26.8 L153.3,26.9 L154.0,27.0 L154.7,27.1 L155.4,27.2 L156.0,27.3 L156.7,27.5 L157.4,27.6 L158.0,27.8 L158.7,28.0 L159.4,28.2 L160.0,28.4 L160.7,28.6 L161.4,28.9 L162.1,29.2 L162.7,29.4 L163.4,29.7 L164.1,30.0 L164.7,30.4 L165.4,30.7 L166.1,31.0 L166.8,31.4 L167.4,31.8 L168.1,32.2 L168.8,32.6 L169.4,33.0 L170.1,33.5 L170.8,33.9 L171.4,34.4 L172.1,34.9 L172.8,35.4 L173.5,35.9 L174.1,36.4 L174.8,37.0 L175.5,37.5 L176.1,38.1 L176.8,38.7 L177.5,39.3 L178.1,39.9 L178.8,40.6 L179.5,41.2 L180.2,41.9 L180.8,42.6 L181.5,43.3 L182.2,44.0 L182.8,44.7 L183.5,45.5 L184.2,46.2 L184.8,47.0 L185.5,47.8 L186.2,48.6 L186.8,49.4 L187.5,50.2 L188.2,51.1 L188.9,51.9 L189.5,52.8 L190.2,53.7 L190.9,54.6 L191.5,55.5 L192.2,56.5 L192.9,57.4 L193.5,58.4 L194.2,59.4 L194.9,60.4 L195.6,61.4 L196.2,62.4 L196.9,63.4 L197.6,64.5 L198.2,65.6 L198.9,66.6 L199.6,67.7 L200.2,68.9 L200.9,70.0 L201.6,71.1 L202.3,72.3 L202.9,73.5 L203.6,74.7 L204.3,75.9 L204.9,77.1 L205.6,78.3 L206.3,79.6 L207.0,80.8 L207.6,82.1 L208.3,83.4 L209.0,84.7 L209.6,86.1 L210.3,87.4 L211.0,88.8 L211.6,90.1 L212.3,91.5 L213.0,92.9 L213.7,94.3 L214.3,95.8 L215.0,97.2 L215.7,98.7 L216.3,100.1 L217.0,101.6 L217.7,103.1 L218.3,104.7 L219.0,106.2 L219.7,107.7 L220.3,109.3 L221.0,110.9 L221.7,112.5 L222.4,114.1 L223.0,115.7 L223.7,117.4 L224.4,119.0 L225.0,120.7 L225.7,122.4 L226.4,124.1 L227.0,125.8 L227.7,127.5 L228.4,129.3 L229.1,131.0 L229.7,132.8 L230.4,134.6 L231.1,136.4 L231.7,138.2 L232.4,140.1 L233.1,141.9 L233.8,143.8 L234.4,145.7 L235.1,147.5 L235.8,149.5 L236.4,151.4 L237.1,153.3 L237.8,155.3 L238.4,157.2 L239.1,159.2 L239.8,161.2 L240.5,163.2 L241.1,165.3 L241.8,167.3 L242.5,169.4 L243.1,171.5 L243.8,173.5 L244.5,175.7 L245.1,177.8 L245.8,179.9 L246.5,182.1 L247.2,184.2 L247.8,186.4 L248.5,188.6 L249.2,190.8 L249.8,193.0 L250.5,195.3 L251.2,197.5 L251.8,199.8 L252.5,202.1 L253.2,204.4 L253.8,206.7 L254.5,209.0 L255.2,211.4 L255.9,213.7 L256.5,216.1 L257.2,218.5 L257.9,220.9 L258.5,223.3 L259.2,225.8 L259.9,228.2 L260.5,230.7 L261.2,233.1 L261.9,235.6 L262.6,238.2 L263.2,240.7 L263.9,243.2 L264.6,245.8 L265.2,248.3 L265.9,250.9 L266.6,253.5 L267.2,256.1 L267.9,258.8 L268.6,261.4 L269.3,264.1 L269.9,266.7 L270.6,269.4 L271.3,272.1 L271.9,274.9 L272.6,277.6 L273.3,280.3 L273.9,283.1 L274.6,285.9 L275.3,288.7 L276.0,291.5 L276.6,294.3 L277.3,297.1 L278.0,300.0 L278.6,302.9 L279.3,305.8 L280.0,308.7 L280.7,311.6 L281.3,314.5 L282.0,317.4 L282.7,320.4 L283.3,323.4 L284.0,326.4\" clip-path=\"url(#c49771)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"193.5\" y=\"51.4\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">f(x) = −x² + 6x − 5</text></svg>"}, {"kind": "mcq", "text": "<b>Error analysis.</b> Mia used the graph of y = x² − 6x + 9 and said the solutions of x² − 6x + 9 = 0 are x = 3 and x = 9. What is correct?", "opts": ["Mia is correct: x = 3 and x = 9", "Only x = 3, where the vertex touches the x-axis", "No solutions, since the graph does not cross the axis", "x = −3 and x = 3, by symmetry"], "correct": 1, "tag": "", "sol": "The parabola touches the x-axis only at its vertex (3, 0), so there is one solution, x = 3. The point (0, 9) is where it meets the y-axis, not a solution: 81 − 54 + 9 = 36 ≠ 0.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"83.0\" y1=\"214.0\" x2=\"83.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"116.5\" y1=\"214.0\" x2=\"116.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"217.0\" y1=\"214.0\" x2=\"217.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"250.5\" y1=\"214.0\" x2=\"250.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"196.8\" x2=\"284.0\" y2=\"196.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"179.7\" x2=\"284.0\" y2=\"179.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"162.5\" x2=\"284.0\" y2=\"162.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"145.3\" x2=\"284.0\" y2=\"145.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"128.2\" x2=\"284.0\" y2=\"128.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"111.0\" x2=\"284.0\" y2=\"111.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"93.8\" x2=\"284.0\" y2=\"93.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"76.7\" x2=\"284.0\" y2=\"76.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"59.5\" x2=\"284.0\" y2=\"59.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"42.3\" x2=\"284.0\" y2=\"42.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"25.2\" x2=\"284.0\" y2=\"25.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"8.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"179.7\" x2=\"284.0\" y2=\"179.7\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"8.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"188.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"83.0\" y=\"188.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"150.0\" y=\"188.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"217.0\" y=\"188.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"284.0\" y=\"188.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><text class=\"po\" x=\"45.5\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"45.5\" y=\"145.3\" text-anchor=\"end\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"45.5\" y=\"111.0\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"45.5\" y=\"76.7\" text-anchor=\"end\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"45.5\" y=\"42.3\" text-anchor=\"end\" dominant-baseline=\"middle\">8</text><text class=\"po\" x=\"45.5\" y=\"8.0\" text-anchor=\"end\" dominant-baseline=\"middle\">10</text><text class=\"po\" x=\"280.0\" y=\"171.7\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"57.5\" y=\"14.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c2591\"><rect x=\"16.0\" y=\"8.0\" width=\"268.0\" height=\"206.0\"/></clipPath><path d=\"M16.0,-95.0 L16.7,-92.3 L17.3,-89.5 L18.0,-86.8 L18.7,-84.1 L19.3,-81.4 L20.0,-78.8 L20.7,-76.1 L21.4,-73.5 L22.0,-70.8 L22.7,-68.2 L23.4,-65.6 L24.0,-63.0 L24.7,-60.5 L25.4,-57.9 L26.1,-55.3 L26.7,-52.8 L27.4,-50.3 L28.1,-47.8 L28.7,-45.3 L29.4,-42.8 L30.1,-40.3 L30.7,-37.9 L31.4,-35.5 L32.1,-33.0 L32.8,-30.6 L33.4,-28.2 L34.1,-25.8 L34.8,-23.5 L35.4,-21.1 L36.1,-18.8 L36.8,-16.5 L37.4,-14.1 L38.1,-11.8 L38.8,-9.6 L39.5,-7.3 L40.1,-5.0 L40.8,-2.8 L41.5,-0.5 L42.1,1.7 L42.8,3.9 L43.5,6.1 L44.1,8.2 L44.8,10.4 L45.5,12.6 L46.2,14.7 L46.8,16.8 L47.5,18.9 L48.2,21.0 L48.8,23.1 L49.5,25.2 L50.2,27.2 L50.8,29.3 L51.5,31.3 L52.2,33.3 L52.9,35.3 L53.5,37.3 L54.2,39.3 L54.9,41.2 L55.5,43.2 L56.2,45.1 L56.9,47.0 L57.5,48.9 L58.2,50.8 L58.9,52.7 L59.6,54.5 L60.2,56.4 L60.9,58.2 L61.6,60.0 L62.2,61.8 L62.9,63.6 L63.6,65.4 L64.2,67.2 L64.9,68.9 L65.6,70.7 L66.2,72.4 L66.9,74.1 L67.6,75.8 L68.3,77.5 L68.9,79.1 L69.6,80.8 L70.3,82.4 L70.9,84.1 L71.6,85.7 L72.3,87.3 L72.9,88.9 L73.6,90.4 L74.3,92.0 L75.0,93.5 L75.6,95.1 L76.3,96.6 L77.0,98.1 L77.6,99.6 L78.3,101.1 L79.0,102.5 L79.7,104.0 L80.3,105.4 L81.0,106.8 L81.7,108.2 L82.3,109.6 L83.0,111.0 L83.7,112.4 L84.3,113.7 L85.0,115.1 L85.7,116.4 L86.4,117.7 L87.0,119.0 L87.7,120.3 L88.4,121.5 L89.0,122.8 L89.7,124.0 L90.4,125.3 L91.0,126.5 L91.7,127.7 L92.4,128.9 L93.0,130.1 L93.7,131.2 L94.4,132.4 L95.1,133.5 L95.7,134.6 L96.4,135.7 L97.1,136.8 L97.7,137.9 L98.4,139.0 L99.1,140.0 L99.8,141.0 L100.4,142.1 L101.1,143.1 L101.8,144.1 L102.4,145.1 L103.1,146.0 L103.8,147.0 L104.4,147.9 L105.1,148.8 L105.8,149.8 L106.5,150.7 L107.1,151.5 L107.8,152.4 L108.5,153.3 L109.1,154.1 L109.8,154.9 L110.5,155.8 L111.1,156.6 L111.8,157.4 L112.5,158.1 L113.1,158.9 L113.8,159.6 L114.5,160.4 L115.2,161.1 L115.8,161.8 L116.5,162.5 L117.2,163.2 L117.8,163.8 L118.5,164.5 L119.2,165.1 L119.9,165.8 L120.5,166.4 L121.2,167.0 L121.9,167.6 L122.5,168.1 L123.2,168.7 L123.9,169.2 L124.5,169.8 L125.2,170.3 L125.9,170.8 L126.5,171.3 L127.2,171.7 L127.9,172.2 L128.6,172.6 L129.2,173.1 L129.9,173.5 L130.6,173.9 L131.2,174.3 L131.9,174.7 L132.6,175.0 L133.2,175.4 L133.9,175.7 L134.6,176.0 L135.3,176.3 L135.9,176.6 L136.6,176.9 L137.3,177.2 L137.9,177.4 L138.6,177.7 L139.3,177.9 L139.9,178.1 L140.6,178.3 L141.3,178.5 L142.0,178.7 L142.6,178.8 L143.3,179.0 L144.0,179.1 L144.6,179.2 L145.3,179.3 L146.0,179.4 L146.7,179.5 L147.3,179.6 L148.0,179.6 L148.7,179.6 L149.3,179.7 L150.0,179.7 L150.7,179.7 L151.3,179.6 L152.0,179.6 L152.7,179.6 L153.3,179.5 L154.0,179.4 L154.7,179.3 L155.4,179.2 L156.0,179.1 L156.7,179.0 L157.4,178.8 L158.0,178.7 L158.7,178.5 L159.4,178.3 L160.0,178.1 L160.7,177.9 L161.4,177.7 L162.1,177.4 L162.7,177.2 L163.4,176.9 L164.1,176.6 L164.7,176.3 L165.4,176.0 L166.1,175.7 L166.8,175.4 L167.4,175.0 L168.1,174.7 L168.8,174.3 L169.4,173.9 L170.1,173.5 L170.8,173.1 L171.4,172.6 L172.1,172.2 L172.8,171.7 L173.5,171.3 L174.1,170.8 L174.8,170.3 L175.5,169.8 L176.1,169.2 L176.8,168.7 L177.5,168.1 L178.1,167.6 L178.8,167.0 L179.5,166.4 L180.2,165.8 L180.8,165.1 L181.5,164.5 L182.2,163.8 L182.8,163.2 L183.5,162.5 L184.2,161.8 L184.8,161.1 L185.5,160.4 L186.2,159.6 L186.8,158.9 L187.5,158.1 L188.2,157.4 L188.9,156.6 L189.5,155.8 L190.2,154.9 L190.9,154.1 L191.5,153.3 L192.2,152.4 L192.9,151.5 L193.5,150.7 L194.2,149.8 L194.9,148.8 L195.6,147.9 L196.2,147.0 L196.9,146.0 L197.6,145.1 L198.2,144.1 L198.9,143.1 L199.6,142.1 L200.2,141.0 L200.9,140.0 L201.6,139.0 L202.3,137.9 L202.9,136.8 L203.6,135.7 L204.3,134.6 L204.9,133.5 L205.6,132.4 L206.3,131.2 L207.0,130.1 L207.6,128.9 L208.3,127.7 L209.0,126.5 L209.6,125.3 L210.3,124.0 L211.0,122.8 L211.6,121.5 L212.3,120.3 L213.0,119.0 L213.7,117.7 L214.3,116.4 L215.0,115.1 L215.7,113.7 L216.3,112.4 L217.0,111.0 L217.7,109.6 L218.3,108.2 L219.0,106.8 L219.7,105.4 L220.3,104.0 L221.0,102.5 L221.7,101.1 L222.4,99.6 L223.0,98.1 L223.7,96.6 L224.4,95.1 L225.0,93.5 L225.7,92.0 L226.4,90.4 L227.0,88.9 L227.7,87.3 L228.4,85.7 L229.1,84.1 L229.7,82.4 L230.4,80.8 L231.1,79.1 L231.7,77.5 L232.4,75.8 L233.1,74.1 L233.8,72.4 L234.4,70.7 L235.1,68.9 L235.8,67.2 L236.4,65.4 L237.1,63.6 L237.8,61.8 L238.4,60.0 L239.1,58.2 L239.8,56.4 L240.5,54.5 L241.1,52.7 L241.8,50.8 L242.5,48.9 L243.1,47.0 L243.8,45.1 L244.5,43.2 L245.1,41.2 L245.8,39.3 L246.5,37.3 L247.2,35.3 L247.8,33.3 L248.5,31.3 L249.2,29.3 L249.8,27.2 L250.5,25.2 L251.2,23.1 L251.8,21.0 L252.5,18.9 L253.2,16.8 L253.8,14.7 L254.5,12.6 L255.2,10.4 L255.9,8.2 L256.5,6.1 L257.2,3.9 L257.9,1.7 L258.5,-0.5 L259.2,-2.8 L259.9,-5.0 L260.5,-7.3 L261.2,-9.6 L261.9,-11.8 L262.6,-14.1 L263.2,-16.5 L263.9,-18.8 L264.6,-21.1 L265.2,-23.5 L265.9,-25.8 L266.6,-28.2 L267.2,-30.6 L267.9,-33.0 L268.6,-35.5 L269.3,-37.9 L269.9,-40.3 L270.6,-42.8 L271.3,-45.3 L271.9,-47.8 L272.6,-50.3 L273.3,-52.8 L273.9,-55.3 L274.6,-57.9 L275.3,-60.5 L276.0,-63.0 L276.6,-65.6 L277.3,-68.2 L278.0,-70.8 L278.6,-73.5 L279.3,-76.1 L280.0,-78.8 L280.7,-81.4 L281.3,-84.1 L282.0,-86.8 L282.7,-89.5 L283.3,-92.3 L284.0,-95.0\" clip-path=\"url(#c2591)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"237.1\" y=\"56.6\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x² − 6x + 9</text></svg>"}, {"kind": "blank", "p": "Estimate the positive solution of x² − 7 = 0 using f(x) = x² − 7.", "tag": "", "marks": "", "flat": [{"t": "f(2) = __B1__", "a": {"B1": "-3"}}, {"t": "f(3) = __B1__", "a": {"B1": "2"}}, {"t": "f(2.6) = −0.24 and f(2.7) = 0.29, so to the nearest tenth x ≈ __B1__", "a": {"B1": "2.6"}}], "sol": "2² − 7 = −3.\n3² − 7 = 2. The sign changes, so a zero lies between 2 and 3.\n−0.24 is closer to 0 than 0.29, so x ≈ 2.6 (√7 ≈ 2.646).", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "Which function has zeros x = 2 and x = −5?", "opts": ["f(x) = x² − 3x + 10", "f(x) = x² + 7x − 10", "f(x) = x² − 3x − 10", "f(x) = x² + 3x − 10"], "correct": 3, "tag": "", "sol": "Zeros 2 and −5 mean f(x) = (x − 2)(x + 5) = x² + 3x − 10. Check: 4 + 6 − 10 = 0 ✓ and 25 − 15 − 10 = 0 ✓"}, {"kind": "blank", "p": "A football is kicked from the ground. Its height is h = −16t² + 32t feet after t seconds.", "tag": "", "marks": "", "flat": [{"t": "It lands (h = 0, t > 0) after __B1__ s", "a": {"B1": "2"}}, {"t": "Its maximum height is __B1__ ft", "a": {"B1": "16"}}], "sol": "−16t² + 32t = −16t(t − 2) = 0, so t = 0 or t = 2. It lands at t = 2.\nThe vertex is halfway, at t = 1: h = −16 + 32 = 16 ft.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 320 220\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"160.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Height of a kicked ball</text><line x1=\"40.0\" y1=\"190.0\" x2=\"40.0\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"40.0\" y=\"201.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"93.2\" y1=\"190.0\" x2=\"93.2\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"93.2\" y=\"201.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0.5</text><line x1=\"146.4\" y1=\"190.0\" x2=\"146.4\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"146.4\" y=\"201.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"199.6\" y1=\"190.0\" x2=\"199.6\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"199.6\" y=\"201.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1.5</text><line x1=\"252.8\" y1=\"190.0\" x2=\"252.8\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"252.8\" y=\"201.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line x1=\"306.0\" y1=\"190.0\" x2=\"306.0\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"306.0\" y=\"201.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2.5</text><line x1=\"40.0\" y1=\"190.0\" x2=\"306.0\" y2=\"190.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"35.0\" y=\"190.0\" text-anchor=\"end\" dominant-baseline=\"middle\">0</text><line x1=\"40.0\" y1=\"156.4\" x2=\"306.0\" y2=\"156.4\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"35.0\" y=\"156.4\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><line x1=\"40.0\" y1=\"122.8\" x2=\"306.0\" y2=\"122.8\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"35.0\" y=\"122.8\" text-anchor=\"end\" dominant-baseline=\"middle\">8</text><line x1=\"40.0\" y1=\"89.2\" x2=\"306.0\" y2=\"89.2\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"35.0\" y=\"89.2\" text-anchor=\"end\" dominant-baseline=\"middle\">12</text><line x1=\"40.0\" y1=\"55.6\" x2=\"306.0\" y2=\"55.6\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"35.0\" y=\"55.6\" text-anchor=\"end\" dominant-baseline=\"middle\">16</text><line x1=\"40.0\" y1=\"22.0\" x2=\"306.0\" y2=\"22.0\" style=\"stroke:var(--rule)\"/><text class=\"po\" x=\"35.0\" y=\"22.0\" text-anchor=\"end\" dominant-baseline=\"middle\">20</text><line x1=\"40.0\" y1=\"190.0\" x2=\"306.0\" y2=\"190.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"40.0\" y1=\"190.0\" x2=\"40.0\" y2=\"22.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"306.0\" y=\"213.0\" text-anchor=\"end\" dominant-baseline=\"middle\">t</text><text class=\"po\" x=\"44.0\" y=\"28.0\" text-anchor=\"start\" dominant-baseline=\"middle\">h</text><path d=\"M40.0,190.0 L40.9,187.8 L41.8,185.6 L42.7,183.4 L43.5,181.2 L44.4,179.0 L45.3,176.9 L46.2,174.8 L47.1,172.7 L48.0,170.6 L48.9,168.5 L49.8,166.5 L50.6,164.5 L51.5,162.5 L52.4,160.5 L53.3,158.5 L54.2,156.5 L55.1,154.6 L56.0,152.7 L56.8,150.8 L57.7,148.9 L58.6,147.1 L59.5,145.2 L60.4,143.4 L61.3,141.6 L62.2,139.8 L63.1,138.1 L63.9,136.3 L64.8,134.6 L65.7,132.9 L66.6,131.2 L67.5,129.5 L68.4,127.9 L69.3,126.2 L70.1,124.6 L71.0,123.0 L71.9,121.5 L72.8,119.9 L73.7,118.4 L74.6,116.8 L75.5,115.3 L76.4,113.8 L77.2,112.4 L78.1,110.9 L79.0,109.5 L79.9,108.1 L80.8,106.7 L81.7,105.3 L82.6,104.0 L83.4,102.6 L84.3,101.3 L85.2,100.0 L86.1,98.8 L87.0,97.5 L87.9,96.3 L88.8,95.0 L89.7,93.8 L90.5,92.6 L91.4,91.5 L92.3,90.3 L93.2,89.2 L94.1,88.1 L95.0,87.0 L95.9,85.9 L96.7,84.9 L97.6,83.8 L98.5,82.8 L99.4,81.8 L100.3,80.8 L101.2,79.9 L102.1,78.9 L103.0,78.0 L103.8,77.1 L104.7,76.2 L105.6,75.3 L106.5,74.5 L107.4,73.7 L108.3,72.9 L109.2,72.1 L110.0,71.3 L110.9,70.5 L111.8,69.8 L112.7,69.1 L113.6,68.4 L114.5,67.7 L115.4,67.0 L116.3,66.4 L117.1,65.8 L118.0,65.2 L118.9,64.6 L119.8,64.0 L120.7,63.4 L121.6,62.9 L122.5,62.4 L123.3,61.9 L124.2,61.4 L125.1,61.0 L126.0,60.5 L126.9,60.1 L127.8,59.7 L128.7,59.3 L129.6,59.0 L130.4,58.6 L131.3,58.3 L132.2,58.0 L133.1,57.7 L134.0,57.4 L134.9,57.2 L135.8,56.9 L136.6,56.7 L137.5,56.5 L138.4,56.4 L139.3,56.2 L140.2,56.1 L141.1,55.9 L142.0,55.8 L142.9,55.7 L143.7,55.7 L144.6,55.6 L145.5,55.6 L146.4,55.6 L147.3,55.6 L148.2,55.6 L149.1,55.7 L149.9,55.7 L150.8,55.8 L151.7,55.9 L152.6,56.1 L153.5,56.2 L154.4,56.4 L155.3,56.5 L156.2,56.7 L157.0,56.9 L157.9,57.2 L158.8,57.4 L159.7,57.7 L160.6,58.0 L161.5,58.3 L162.4,58.6 L163.2,59.0 L164.1,59.3 L165.0,59.7 L165.9,60.1 L166.8,60.5 L167.7,61.0 L168.6,61.4 L169.5,61.9 L170.3,62.4 L171.2,62.9 L172.1,63.4 L173.0,64.0 L173.9,64.6 L174.8,65.2 L175.7,65.8 L176.5,66.4 L177.4,67.0 L178.3,67.7 L179.2,68.4 L180.1,69.1 L181.0,69.8 L181.9,70.5 L182.8,71.3 L183.6,72.1 L184.5,72.9 L185.4,73.7 L186.3,74.5 L187.2,75.3 L188.1,76.2 L189.0,77.1 L189.8,78.0 L190.7,78.9 L191.6,79.9 L192.5,80.8 L193.4,81.8 L194.3,82.8 L195.2,83.8 L196.1,84.9 L196.9,85.9 L197.8,87.0 L198.7,88.1 L199.6,89.2 L200.5,90.3 L201.4,91.5 L202.3,92.6 L203.1,93.8 L204.0,95.0 L204.9,96.3 L205.8,97.5 L206.7,98.8 L207.6,100.0 L208.5,101.3 L209.4,102.6 L210.2,104.0 L211.1,105.3 L212.0,106.7 L212.9,108.1 L213.8,109.5 L214.7,110.9 L215.6,112.4 L216.4,113.8 L217.3,115.3 L218.2,116.8 L219.1,118.4 L220.0,119.9 L220.9,121.5 L221.8,123.0 L222.7,124.6 L223.5,126.2 L224.4,127.9 L225.3,129.5 L226.2,131.2 L227.1,132.9 L228.0,134.6 L228.9,136.3 L229.7,138.1 L230.6,139.8 L231.5,141.6 L232.4,143.4 L233.3,145.2 L234.2,147.1 L235.1,148.9 L236.0,150.8 L236.8,152.7 L237.7,154.6 L238.6,156.5 L239.5,158.5 L240.4,160.5 L241.3,162.5 L242.2,164.5 L243.0,166.5 L243.9,168.5 L244.8,170.6 L245.7,172.7 L246.6,174.8 L247.5,176.9 L248.4,179.0 L249.3,181.2 L250.1,183.4 L251.0,185.6 L251.9,187.8 L252.8,190.0\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/></svg>"}, {"kind": "mcq", "text": "A diver jumps from a platform. Her height above the water is h = −5t² + 10t + 15 metres after t seconds. When does she reach the water?", "opts": ["After 3 s", "After 15 s", "After −1 s and 3 s", "After 1 s"], "correct": 0, "tag": "", "sol": "Solve −5t² + 10t + 15 = 0 → t² − 2t − 3 = 0 → (t − 3)(t + 1) = 0. t = −1 is before she jumped, so she reaches the water after 3 s.", "tools": ["desmos"], "desmos": ["y=-5x^{2}+10x+15"]}, {"kind": "blank", "p": "The vertex of f(x) = x² − 6x + k is (3, k − 9). Find the number of real solutions of f(x) = 0.", "tag": "", "marks": "", "flat": [{"t": "k = 5: __B1__ solutions", "a": {"B1": "2"}, "accept": ["two"]}, {"t": "k = 9: __B1__ solution", "a": {"B1": "1"}, "accept": ["one"]}, {"t": "k = 12: __B1__ solutions", "a": {"B1": "0"}, "accept": ["none", "zero", "no solutions", "no real solutions", "no solution"]}], "sol": "The vertex is (3, −4), below the x-axis, and the parabola opens up: it crosses twice.\nThe vertex is (3, 0), on the x-axis: one solution.\nThe vertex is (3, 3), above the x-axis: no real solutions."}, {"kind": "mcq", "text": "<b>Reasoning.</b> The graph of y = ax² + bx + c crosses the x-axis at x = −4 and x = 2. What is its axis of symmetry?", "opts": ["x = −1", "x = −2", "x = 3", "x = 1"], "correct": 0, "tag": "", "sol": "The axis of symmetry is halfway between the zeros: (−4 + 2) ÷ 2 = −1."}, {"kind": "blank", "p": "Solve x² − 1 = 3 by graphing y = x² − 1 and y = 3 and finding where they meet.", "tag": "", "marks": "", "flat": [{"t": "x = __B1__", "a": {"B1": "-2, 2"}, "expr": "set"}, {"t": "At both points the y-coordinate is __B1__", "a": {"B1": "3"}}], "sol": "x² − 1 = 3 → x² = 4: the parabola meets the line y = 3 at x = −2 and x = 2.\nThe points are (−2, 3) and (2, 3), on the line y = 3.", "tools": ["desmos"], "desmos": ["y=x^{2}-1", "y=3"]}]}, {"id": "s3", "label": "9.3 Using Square Roots", "sub": "I can solve equations of the form ax² + c = 0 and a(x − h)² = k by taking square roots, and approximate the solutions.", "slides": [{"kind": "mcq", "text": "Solve x² = 49.", "opts": ["x = 7 or x = −7", "x = ±24.5", "x = 7 only", "x = 24.5"], "correct": 0, "tag": "", "sol": "Both 7² and (−7)² equal 49, so x = ±7. (24.5 divides by 2 instead of taking the square root.)"}, {"kind": "blank", "p": "Solve 3x² − 75 = 0.", "tag": "", "marks": "", "flat": [{"t": "x² = __B1__", "a": {"B1": "25"}}, {"t": "x = __B1__", "a": {"B1": "-5, 5"}, "expr": "set"}], "sol": "Add 75: 3x² = 75. Divide by 3: x² = 25.\nx = ±√25 = ±5."}, {"kind": "mcq", "text": "Solve x² + 16 = 0.", "opts": ["x = 4 or x = −4", "x = −4 only", "No real solutions", "x = 16 or x = −16"], "correct": 2, "tag": "", "sol": "x² = −16, and no real number squared is negative. There are no real solutions."}, {"kind": "blank", "p": "Solve (x − 3)² = 16.", "tag": "", "marks": "", "flat": [{"t": "x − 3 = ±__B1__", "a": {"B1": "4"}}, {"t": "x = __B1__", "a": {"B1": "-1, 7"}, "expr": "set"}], "sol": "Take the square root of both sides: x − 3 = ±4.\nx = 3 + 4 = 7 or x = 3 − 4 = −1."}, {"kind": "mcq", "text": "How many real solutions does 5x² + 7 = 7 have?", "opts": ["Two: x = ±7", "None", "Two: x = ±√7", "One: x = 0"], "correct": 3, "tag": "", "sol": "Subtract 7: 5x² = 0, so x² = 0 and x = 0. When the squared part equals 0 there is exactly one solution."}, {"kind": "blank", "p": "Solve x² − 18 = 0.", "tag": "", "marks": "", "flat": [{"t": "Exact positive solution: x = __B1__", "a": {"B1": "3√2"}, "expr": "calc", "accept": ["√18"]}, {"t": "Both solutions to 2 decimal places: x ≈ ±__B1__", "a": {"B1": "4.24"}}], "sol": "x² = 18, so x = ±√18 = ±3√2.\n3√2 ≈ 4.2426 ≈ 4.24, so x ≈ ±4.24.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "<b>Error analysis.</b> Leo solved x² = 36 and wrote x = 6. What is wrong?", "opts": ["Nothing; x = 6 is the only solution", "He missed the negative root: x = 6 or x = −6", "The solution is x = ±√6", "He should divide by 2: x = 18"], "correct": 1, "tag": "", "sol": "6² = 36 and (−6)² = 36, so there are two solutions. When you take the square root of both sides, write ±."}, {"kind": "blank", "p": "Solve (2x + 1)² = 9.", "tag": "", "marks": "", "flat": [{"t": "2x + 1 = 3 or 2x + 1 = __B1__", "a": {"B1": "-3"}}, {"t": "x = __B1__", "a": {"B1": "-2, 1"}, "expr": "set"}], "sol": "Take square roots: 2x + 1 = ±3.\n2x + 1 = 3 → x = 1; 2x + 1 = −3 → 2x = −4 → x = −2."}, {"kind": "mcq", "text": "Solve 4(x + 2)² = 20.", "opts": ["x = −2 ± 2√5", "x = −2 ± √5", "x = 2 ± √5", "x = −2 ± 5"], "correct": 1, "tag": "", "sol": "Divide by 4: (x + 2)² = 5. Then x + 2 = ±√5 and x = −2 ± √5. (−2 ± 2√5 comes from taking √20 without dividing by 4 first.)"}, {"kind": "blank", "p": "A circular rug has an area of 50 ft². Use A = πr².", "tag": "", "marks": "", "flat": [{"t": "r ≈ __B1__ ft (2 decimal places)", "a": {"B1": "3.99"}}, {"t": "Only the positive root is used, because a radius cannot be __B1__ (negative / zero).", "a": {"B1": "negative"}, "expr": "words", "accept": ["negative number", "less than zero"]}], "sol": "r² = 50 ÷ π ≈ 15.915, so r = √15.915 ≈ 3.99 ft.\nr = −3.99 also solves the equation, but a length cannot be negative.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "A ball is dropped from 144 ft. Its height is h = −16t² + 144 feet after t seconds. When does it hit the ground?", "opts": ["After 9 s", "After ±3 s", "After 3 s", "After 12 s"], "correct": 2, "tag": "", "sol": "0 = −16t² + 144 → t² = 9 → t = ±3. A time after the drop is positive, so it lands after 3 s. (9 s forgets to take the square root.)"}, {"kind": "blank", "p": "Solve x² − 2x + 1 = 7.", "tag": "", "marks": "", "flat": [{"t": "The left side is a perfect square: (x − __B1__)² = 7", "a": {"B1": "1"}}, {"t": "Larger solution (exact): x = __B1__", "a": {"B1": "1+√7"}, "expr": "calc", "accept": ["√7+1"]}, {"t": "Smaller solution to 2 decimal places: x ≈ __B1__", "a": {"B1": "-1.65"}}], "sol": "x² − 2x + 1 = (x − 1)².\nx − 1 = ±√7, so x = 1 + √7 or x = 1 − √7.\n1 − √7 ≈ 1 − 2.6458 = −1.6458 ≈ −1.65.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "<b>Reasoning.</b> For which value of d does x² = d have no real solutions?", "opts": ["d = 9", "d = 0", "d = −4", "d = 4"], "correct": 2, "tag": "", "sol": "A square is never negative, so x² = −4 has no real solutions. d = 0 gives one solution and d = 4 or 9 give two."}, {"kind": "blank", "p": "Square spaces.", "tag": "", "marks": "", "flat": [{"t": "A square solar panel has an area of 2.25 m². Its side length is __B1__ m", "a": {"B1": "1.5"}}, {"t": "A square courtyard has an area of 300 m². Its side to 1 decimal place is __B1__ m", "a": {"B1": "17.3"}}], "sol": "s² = 2.25 → s = √2.25 = 1.5 m (−1.5 is rejected).\ns = √300 = 10√3 ≈ 17.32 ≈ 17.3 m.", "tools": ["calc"], "desmos": []}]}, {"id": "s4", "label": "9.4 Completing the Square", "sub": "I can complete the square, solve quadratic equations by completing the square, and use it to write a quadratic function in vertex form.", "slides": [{"kind": "mcq", "text": "What value of c makes x² + 10x + c a perfect square trinomial?", "opts": ["100", "5", "25", "10"], "correct": 2, "tag": "", "sol": "Add (b ÷ 2)² = (10 ÷ 2)² = 25: x² + 10x + 25 = (x + 5)². (100 squares b without halving it.)"}, {"kind": "blank", "p": "Complete the square for x² − 14x + c.", "tag": "", "marks": "", "flat": [{"t": "c = __B1__", "a": {"B1": "49"}}, {"t": "x² − 14x + c = (x − __B1__)²", "a": {"B1": "7"}}], "sol": "(−14 ÷ 2)² = (−7)² = 49.\nx² − 14x + 49 = (x − 7)²."}, {"kind": "mcq", "text": "What value of c makes x² + 5x + c a perfect square trinomial?", "opts": ["25", "{25/4}", "{5/2}", "{25/2}"], "correct": 1, "tag": "", "sol": "(5 ÷ 2)² = {25/4}. Then x² + 5x + {25/4} = (x + {5/2})²."}, {"kind": "blank", "p": "Solve x² + 6x = 16 by completing the square.", "tag": "", "marks": "", "flat": [{"t": "Add __B1__ to both sides", "a": {"B1": "9"}}, {"t": "(x + 3)² = __B1__", "a": {"B1": "25"}}, {"t": "x = __B1__", "a": {"B1": "-8, 2"}, "expr": "set"}], "sol": "(6 ÷ 2)² = 9.\n16 + 9 = 25.\nx + 3 = ±5, so x = 2 or x = −8."}, {"kind": "mcq", "text": "Solve x² − 4x − 1 = 0 by completing the square.", "opts": ["x = 4 ± √5", "x = 2 ± √3", "x = 2 ± √5", "x = −2 ± √5"], "correct": 2, "tag": "", "sol": "x² − 4x = 1. Add 4: (x − 2)² = 5. So x − 2 = ±√5 and x = 2 ± √5. (2 ± √3 comes from adding 4 to the left side only.)"}, {"kind": "blank", "p": "Solve 2x² + 8x − 10 = 0 by completing the square.", "tag": "", "marks": "", "flat": [{"t": "Divide by 2 and move the constant: x² + 4x = __B1__", "a": {"B1": "5"}}, {"t": "Add 4: (x + 2)² = __B1__", "a": {"B1": "9"}}, {"t": "x = __B1__", "a": {"B1": "-5, 1"}, "expr": "set"}], "sol": "x² + 4x − 5 = 0, so x² + 4x = 5.\n5 + 4 = 9.\nx + 2 = ±3, so x = 1 or x = −5."}, {"kind": "mcq", "text": "<b>Error analysis.</b> To solve x² + 8x = 9, Zoe added 16 to the left side only and wrote (x + 4)² = 9. What is correct?", "opts": ["Add 16 to both sides: (x + 4)² = 25, so x = 1 or x = −9", "Add 64 to both sides: (x + 8)² = 73", "Add 4 to both sides: (x + 2)² = 13", "Zoe is correct: x = −1 or x = −7"], "correct": 0, "tag": "", "sol": "Whatever is added to one side must be added to the other: x² + 8x + 16 = 9 + 16 = 25. Then x + 4 = ±5, so x = 1 or x = −9. Check: 1 + 8 = 9 ✓ and 81 − 72 = 9 ✓"}, {"kind": "blank", "p": "Write y = x² + 6x + 11 in vertex form.", "tag": "", "marks": "", "flat": [{"t": "y = (x + 3)² + __B1__", "a": {"B1": "2"}}, {"t": "Vertex: __B1__", "a": {"B1": "(-3, 2)"}, "expr": "coord"}, {"t": "The vertex is a __B1__ point (minimum / maximum).", "a": {"B1": "minimum"}, "expr": "words", "accept": ["min", "lowest"]}], "sol": "y = (x² + 6x + 9) − 9 + 11 = (x + 3)² + 2.\ny = (x − (−3))² + 2, so the vertex is (−3, 2).\na = 1 > 0, so the parabola opens up and the vertex is the lowest point."}, {"kind": "mcq", "text": "Find the maximum value of y = −x² + 8x − 3 by completing the square.", "opts": ["13, at x = 4", "13, at x = −4", "−3, at x = 0", "−19, at x = 4"], "correct": 0, "tag": "", "sol": "y = −(x² − 8x) − 3 = −(x² − 8x + 16) + 16 − 3 = −(x − 4)² + 13. The maximum is 13 when x = 4. (−19 forgets that −(+16) must be balanced by +16.)"}, {"kind": "blank", "p": "Solve x² + 3x − 1 = 0 by completing the square.", "tag": "", "marks": "", "flat": [{"t": "x² + 3x = 1. Add __B1__ to both sides", "a": {"B1": "9/4"}, "expr": "fv"}, {"t": "(x + {3/2})² = __B1__", "a": {"B1": "13/4"}, "expr": "fv"}, {"t": "Larger solution (exact): x = __B1__", "a": {"B1": "(-3+√13)/2"}, "expr": "calc", "accept": ["-3/2+√13/2", "-1.5+√13/2"]}], "sol": "(3 ÷ 2)² = {9/4}.\n1 + {9/4} = {13/4}.\nx + {3/2} = ±√13 / 2, so x = (−3 ± √13)/2; the larger is (−3 + √13)/2 ≈ 0.30."}, {"kind": "mcq", "text": "A rectangular garden is 4 m longer than it is wide, and its area is 60 m². What are its dimensions? (x² + 4x = 60)", "opts": ["4 m by 8 m", "6 m by 10 m", "5 m by 12 m", "10 m by 14 m"], "correct": 1, "tag": "", "sol": "Add 4: (x + 2)² = 64, so x + 2 = ±8 and x = 6 (x = −10 is not a length). The garden is 6 m by 10 m: 6 × 10 = 60 ✓ (5 by 12 has the right area but the sides differ by 7.)"}, {"kind": "blank", "p": "A ball is thrown upward. Its height is h = −16t² + 64t + 4 feet. Completing the square gives h = −16(t − 2)² + 68.", "tag": "", "marks": "", "flat": [{"t": "The ball is highest after __B1__ s", "a": {"B1": "2"}}, {"t": "Its maximum height is __B1__ ft", "a": {"B1": "68"}}], "sol": "−16(t² − 4t) + 4 = −16(t² − 4t + 4) + 64 + 4 = −16(t − 2)² + 68; the vertex is at t = 2.\nAt t = 2 the squared part is 0, so h = 68 ft."}, {"kind": "mcq", "text": "Completing the square on x² − 10x + 18 = 0 gives which equation?", "opts": ["(x + 5)² = 7", "(x − 5)² = 7", "(x − 10)² = 82", "(x − 5)² = 43"], "correct": 1, "tag": "", "sol": "x² − 10x = −18. Add (−10 ÷ 2)² = 25: (x − 5)² = −18 + 25 = 7. (43 comes from 25 + 18, moving the 18 with the wrong sign.)"}, {"kind": "blank", "p": "Solve 3x² − 12x + 7 = 0 by completing the square.", "tag": "", "marks": "", "flat": [{"t": "Divide by 3 and complete the square: (x − 2)² = __B1__", "a": {"B1": "5/3"}, "expr": "fv"}, {"t": "Larger solution to 2 decimal places: x ≈ __B1__", "a": {"B1": "3.29"}}, {"t": "Smaller solution to 2 decimal places: x ≈ __B1__", "a": {"B1": "0.71"}}], "sol": "x² − 4x = −{7/3}. Add 4: (x − 2)² = 4 − {7/3} = {5/3}.\nx = 2 + √({5/3}) ≈ 2 + 1.291 = 3.29.\nx = 2 − √({5/3}) ≈ 2 − 1.291 = 0.71.", "tools": ["calc"], "desmos": []}]}, {"id": "s5", "label": "9.5 Quadratic Formula", "sub": "I can solve any quadratic equation with the Quadratic Formula, use the discriminant to count real solutions, and choose an efficient method.", "slides": [{"kind": "mcq", "text": "For 2x² − 5x − 3 = 0, what are a, b and c?", "opts": ["a = 2, b = −5, c = 3", "a = 2, b = 5, c = 3", "a = −5, b = 2, c = −3", "a = 2, b = −5, c = −3"], "correct": 3, "tag": "", "sol": "Match ax² + bx + c = 0 and keep each sign: a = 2, b = −5, c = −3."}, {"kind": "blank", "p": "Solve x² + 2x − 15 = 0 with the Quadratic Formula.", "tag": "", "marks": "", "flat": [{"t": "b² − 4ac = __B1__", "a": {"B1": "64"}}, {"t": "x = __B1__", "a": {"B1": "-5, 3"}, "expr": "set"}], "sol": "a = 1, b = 2, c = −15: 4 − 4(1)(−15) = 4 + 60 = 64.\nx = (−2 ± 8) / 2, so x = 3 or x = −5."}, {"kind": "mcq", "text": "What is the discriminant of 3x² − 6x + 3 = 0, and what does it tell you?", "opts": ["72; two real solutions", "0; one real solution", "−36; no real solutions", "0; no real solutions"], "correct": 1, "tag": "", "sol": "b² − 4ac = 36 − 4(3)(3) = 36 − 36 = 0. A zero discriminant means exactly one real solution (here x = 1)."}, {"kind": "blank", "p": "Use the discriminant to find the number of real solutions.", "tag": "", "marks": "", "flat": [{"t": "a) x² + x + 5 = 0: __B1__", "a": {"B1": "0"}, "accept": ["none", "zero", "no solutions", "no real solutions", "no solution"]}, {"t": "b) 4x² − 4x + 1 = 0: __B1__", "a": {"B1": "1"}, "accept": ["one"]}, {"t": "c) 2x² + 3x − 4 = 0: __B1__", "a": {"B1": "2"}, "accept": ["two"]}], "sol": "1 − 20 = −19 < 0: no real solutions.\n16 − 16 = 0: one real solution.\n9 + 32 = 41 > 0: two real solutions."}, {"kind": "mcq", "text": "Solve x² − 6x + 4 = 0.", "opts": ["x = 3 ± 2√5", "x = −3 ± √5", "x = 6 ± √5", "x = 3 ± √5"], "correct": 3, "tag": "", "sol": "b² − 4ac = 36 − 16 = 20 and √20 = 2√5. x = (6 ± 2√5) / 2 = 3 ± √5. (3 ± 2√5 divides only the 6 by 2.)"}, {"kind": "blank", "p": "Solve 2x² + 3x − 1 = 0.", "tag": "", "marks": "", "flat": [{"t": "b² − 4ac = __B1__", "a": {"B1": "17"}}, {"t": "Larger solution (exact): x = __B1__", "a": {"B1": "(-3+√17)/4"}, "expr": "calc", "accept": ["-3/4+√17/4", "-0.75+√17/4"]}, {"t": "Smaller solution to 2 decimal places: x ≈ __B1__", "a": {"B1": "-1.78"}}], "sol": "9 − 4(2)(−1) = 9 + 8 = 17.\nx = (−3 ± √17) / 4; the larger is (−3 + √17)/4 ≈ 0.28.\n(−3 − √17)/4 ≈ (−3 − 4.123)/4 ≈ −1.78.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "<b>Error analysis.</b> Solving x² − 4x − 5 = 0, Arjun wrote x = (−4 ± √(16 + 20)) / 2 and got x = 1 or x = −5. What is correct?", "opts": ["−b is +4: x = (4 ± √36) / 2, so x = 5 or x = −1", "His work is correct: x = 1 or x = −5", "b² should be −16: x = (4 ± √4) / 2", "The denominator should be 2c = −10"], "correct": 0, "tag": "", "sol": "b = −4, so −b = 4. b² − 4ac = 16 + 20 = 36. x = (4 ± 6) / 2 = 5 or −1. Check: 25 − 20 − 5 = 0 ✓"}, {"kind": "blank", "p": "Solve 5x² = 2x + 1.", "tag": "", "marks": "", "flat": [{"t": "In standard form 5x² − 2x + c = 0, c = __B1__", "a": {"B1": "-1"}}, {"t": "b² − 4ac = __B1__", "a": {"B1": "24"}}, {"t": "Solutions to 2 decimal places: larger __B1__, smaller __B2__", "a": {"B1": "0.69", "B2": "-0.29"}}], "sol": "Subtract 2x and 1 from both sides: 5x² − 2x − 1 = 0.\n4 − 4(5)(−1) = 4 + 20 = 24.\nx = (2 ± √24) / 10 = (1 ± √6)/5 ≈ 0.69 or −0.29.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "Which method is most efficient for solving 4x² − 81 = 0?", "opts": ["Square roots", "Graphing", "Quadratic Formula", "Completing the square"], "correct": 0, "tag": "", "sol": "There is no x-term, so isolate x²: x² = {81/4}, x = ±{9/2}. (The formula also works, with a = 4, b = 0, c = −81, but it takes longer; graphing only gives estimates.)"}, {"kind": "blank", "p": "A model rocket is launched from a 2 m platform. Its height is h = −4.9t² + 30t + 2 metres after t seconds.", "tag": "", "marks": "", "flat": [{"t": "b² − 4ac = __B1__", "a": {"B1": "939.2"}}, {"t": "It hits the ground after t ≈ __B1__ s (2 decimal places)", "a": {"B1": "6.19"}}], "sol": "30² − 4(−4.9)(2) = 900 + 39.2 = 939.2.\nt = (−30 − √939.2) / (−9.8) ≈ (30 + 30.646) / 9.8 ≈ 6.19 s; the other root is negative.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "A 3 in by 5 in photo has a frame of uniform width x. The photo and frame together cover 35 in². Find x. ((3 + 2x)(5 + 2x) = 35)", "opts": ["2 in", "5 in", "1 in", "0.5 in"], "correct": 2, "tag": "", "sol": "Expand: 4x² + 16x + 15 = 35 → 4x² + 16x − 20 = 0 → x² + 4x − 5 = 0. x = (−4 ± √36)/2 = 1 or −5. A width is positive: x = 1 in. Check: 5 × 7 = 35 ✓"}, {"kind": "blank", "p": "<b>Reasoning.</b> Look at x² + 6x + k = 0.", "tag": "", "marks": "", "flat": [{"t": "It has exactly one solution when k = __B1__", "a": {"B1": "9"}}, {"t": "It has two real solutions when k is __B1__ than 9 (less / greater).", "a": {"B1": "less"}, "expr": "words", "accept": ["smaller", "lower"]}], "sol": "b² − 4ac = 36 − 4k = 0 when k = 9.\n36 − 4k > 0 when 4k < 36, that is k < 9."}, {"kind": "mcq", "text": "The discriminant of ax² + bx + c = 0 is negative. What does the graph of y = ax² + bx + c do?", "opts": ["It passes through the origin", "It touches the x-axis at its vertex", "It does not meet the x-axis", "It crosses the x-axis twice"], "correct": 2, "tag": "", "sol": "A negative discriminant means no real solutions, so the parabola has no x-intercepts."}, {"kind": "blank", "p": "A stall's daily profit is P = −2x² + 40x − 150 dollars when it sells x dozen samosas. Find the break-even points (P = 0).", "tag": "", "marks": "", "flat": [{"t": "Divide by −2: x² − 20x + 75 = 0. Its discriminant is __B1__", "a": {"B1": "100"}}, {"t": "Break-even at x = __B1__ dozen", "a": {"B1": "5, 15"}, "expr": "set"}], "sol": "400 − 4(1)(75) = 400 − 300 = 100.\nx = (20 ± 10) / 2 = 15 or 5."}]}, {"id": "s6", "label": "9.6 Nonlinear Systems", "sub": "I can solve a system of a linear and a quadratic equation (or two quadratics) by graphing, substitution or elimination.", "slides": [{"kind": "mcq", "text": "How many solutions can a system of one linear equation and one quadratic equation have?", "opts": ["0 or infinitely many", "0, 1 or 2", "Exactly 2", "1, 2 or 3"], "correct": 1, "tag": "", "sol": "A line can miss a parabola, touch it once (tangent) or cross it twice. It cannot meet it three times."}, {"kind": "blank", "p": "Solve y = x² and y = x + 2 by substitution.", "tag": "", "marks": "", "flat": [{"t": "x² = x + 2 gives x = __B1__", "a": {"B1": "-1, 2"}, "expr": "set"}, {"t": "Solution with the smaller x: __B1__", "a": {"B1": "(-1, 1)"}, "expr": "coord"}, {"t": "Solution with the larger x: __B1__", "a": {"B1": "(2, 4)"}, "expr": "coord"}], "sol": "x² − x − 2 = 0 → (x − 2)(x + 1) = 0 → x = 2 or −1.\nx = −1: y = −1 + 2 = 1.\nx = 2: y = 2 + 2 = 4. Check: 2² = 4 ✓"}, {"kind": "mcq", "text": "Use the graph to solve the system y = x² − 4 and y = 2x − 1.", "opts": ["(−1, −3) and (3, 5)", "(−2, 0) and (2, 0)", "(−1, 3) and (3, −5)", "(1, −3) and (−3, 5)"], "correct": 0, "tag": "", "sol": "The graphs meet at (−1, −3) and (3, 5). Check: (−1)² − 4 = −3 = 2(−1) − 1 ✓; 9 − 4 = 5 = 6 − 1 ✓ ((±2, 0) are only the parabola's x-intercepts.)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"45.8\" y1=\"214.0\" x2=\"45.8\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"75.6\" y1=\"214.0\" x2=\"75.6\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"105.3\" y1=\"214.0\" x2=\"105.3\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"164.9\" y1=\"214.0\" x2=\"164.9\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"194.7\" y1=\"214.0\" x2=\"194.7\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"224.4\" y1=\"214.0\" x2=\"224.4\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"254.2\" y1=\"214.0\" x2=\"254.2\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"196.8\" x2=\"284.0\" y2=\"196.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"179.7\" x2=\"284.0\" y2=\"179.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"162.5\" x2=\"284.0\" y2=\"162.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"145.3\" x2=\"284.0\" y2=\"145.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"128.2\" x2=\"284.0\" y2=\"128.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"111.0\" x2=\"284.0\" y2=\"111.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"93.8\" x2=\"284.0\" y2=\"93.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"76.7\" x2=\"284.0\" y2=\"76.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"59.5\" x2=\"284.0\" y2=\"59.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"42.3\" x2=\"284.0\" y2=\"42.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"25.2\" x2=\"284.0\" y2=\"25.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"8.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"128.2\" x2=\"284.0\" y2=\"128.2\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"8.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"137.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"75.6\" y=\"137.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"194.7\" y=\"137.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"254.2\" y=\"137.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"131.1\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"131.1\" y=\"179.7\" text-anchor=\"end\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"131.1\" y=\"145.3\" text-anchor=\"end\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"131.1\" y=\"111.0\" text-anchor=\"end\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"131.1\" y=\"76.7\" text-anchor=\"end\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"131.1\" y=\"42.3\" text-anchor=\"end\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"131.1\" y=\"8.0\" text-anchor=\"end\" dominant-baseline=\"middle\">7</text><text class=\"po\" x=\"280.0\" y=\"120.2\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"143.1\" y=\"14.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c62533\"><rect x=\"16.0\" y=\"8.0\" width=\"268.0\" height=\"206.0\"/></clipPath><path d=\"M16.0,-77.8 L16.7,-74.8 L17.3,-71.7 L18.0,-68.6 L18.7,-65.6 L19.3,-62.6 L20.0,-59.6 L20.7,-56.6 L21.4,-53.7 L22.0,-50.7 L22.7,-47.8 L23.4,-44.9 L24.0,-42.0 L24.7,-39.1 L25.4,-36.3 L26.0,-33.4 L26.7,-30.6 L27.4,-27.8 L28.1,-25.0 L28.7,-22.3 L29.4,-19.5 L30.1,-16.8 L30.7,-14.1 L31.4,-11.4 L32.1,-8.7 L32.8,-6.0 L33.4,-3.4 L34.1,-0.7 L34.8,1.9 L35.4,4.5 L36.1,7.0 L36.8,9.6 L37.4,12.1 L38.1,14.7 L38.8,17.2 L39.5,19.7 L40.1,22.1 L40.8,24.6 L41.5,27.0 L42.1,29.5 L42.8,31.9 L43.5,34.2 L44.1,36.6 L44.8,39.0 L45.5,41.3 L46.2,43.6 L46.8,45.9 L47.5,48.2 L48.2,50.5 L48.8,52.7 L49.5,54.9 L50.2,57.2 L50.8,59.3 L51.5,61.5 L52.2,63.7 L52.8,65.8 L53.5,68.0 L54.2,70.1 L54.9,72.2 L55.5,74.2 L56.2,76.3 L56.9,78.3 L57.5,80.3 L58.2,82.3 L58.9,84.3 L59.5,86.3 L60.2,88.3 L60.9,90.2 L61.6,92.1 L62.2,94.0 L62.9,95.9 L63.6,97.7 L64.2,99.6 L64.9,101.4 L65.6,103.2 L66.2,105.0 L66.9,106.8 L67.6,108.6 L68.3,110.3 L68.9,112.0 L69.6,113.7 L70.3,115.4 L70.9,117.1 L71.6,118.8 L72.3,120.4 L73.0,122.0 L73.6,123.6 L74.3,125.2 L75.0,126.8 L75.6,128.3 L76.3,129.9 L77.0,131.4 L77.6,132.9 L78.3,134.4 L79.0,135.8 L79.7,137.3 L80.3,138.7 L81.0,140.1 L81.7,141.5 L82.3,142.9 L83.0,144.3 L83.7,145.6 L84.3,146.9 L85.0,148.2 L85.7,149.5 L86.3,150.8 L87.0,152.1 L87.7,153.3 L88.4,154.5 L89.0,155.7 L89.7,156.9 L90.4,158.1 L91.0,159.2 L91.7,160.4 L92.4,161.5 L93.0,162.6 L93.7,163.7 L94.4,164.7 L95.1,165.8 L95.7,166.8 L96.4,167.8 L97.1,168.8 L97.7,169.8 L98.4,170.8 L99.1,171.7 L99.8,172.6 L100.4,173.5 L101.1,174.4 L101.8,175.3 L102.4,176.2 L103.1,177.0 L103.8,177.8 L104.4,178.6 L105.1,179.4 L105.8,180.2 L106.5,180.9 L107.1,181.7 L107.8,182.4 L108.5,183.1 L109.1,183.8 L109.8,184.4 L110.5,185.1 L111.1,185.7 L111.8,186.3 L112.5,186.9 L113.2,187.5 L113.8,188.1 L114.5,188.6 L115.2,189.1 L115.8,189.6 L116.5,190.1 L117.2,190.6 L117.8,191.1 L118.5,191.5 L119.2,191.9 L119.8,192.3 L120.5,192.7 L121.2,193.1 L121.9,193.4 L122.5,193.8 L123.2,194.1 L123.9,194.4 L124.5,194.7 L125.2,194.9 L125.9,195.2 L126.5,195.4 L127.2,195.6 L127.9,195.8 L128.6,196.0 L129.2,196.2 L129.9,196.3 L130.6,196.4 L131.2,196.5 L131.9,196.6 L132.6,196.7 L133.2,196.8 L133.9,196.8 L134.6,196.8 L135.3,196.8 L135.9,196.8 L136.6,196.8 L137.3,196.7 L137.9,196.7 L138.6,196.6 L139.3,196.5 L139.9,196.4 L140.6,196.2 L141.3,196.1 L142.0,195.9 L142.6,195.7 L143.3,195.5 L144.0,195.3 L144.6,195.1 L145.3,194.8 L146.0,194.5 L146.7,194.3 L147.3,193.9 L148.0,193.6 L148.7,193.3 L149.3,192.9 L150.0,192.5 L150.7,192.1 L151.3,191.7 L152.0,191.3 L152.7,190.9 L153.3,190.4 L154.0,189.9 L154.7,189.4 L155.4,188.9 L156.0,188.4 L156.7,187.8 L157.4,187.2 L158.0,186.7 L158.7,186.1 L159.4,185.4 L160.1,184.8 L160.7,184.1 L161.4,183.5 L162.1,182.8 L162.7,182.1 L163.4,181.3 L164.1,180.6 L164.7,179.8 L165.4,179.1 L166.1,178.3 L166.8,177.5 L167.4,176.6 L168.1,175.8 L168.8,174.9 L169.4,174.0 L170.1,173.1 L170.8,172.2 L171.4,171.3 L172.1,170.3 L172.8,169.4 L173.4,168.4 L174.1,167.4 L174.8,166.4 L175.5,165.3 L176.1,164.3 L176.8,163.2 L177.5,162.1 L178.1,161.0 L178.8,159.9 L179.5,158.7 L180.2,157.6 L180.8,156.4 L181.5,155.2 L182.2,154.0 L182.8,152.7 L183.5,151.5 L184.2,150.2 L184.8,149.0 L185.5,147.7 L186.2,146.3 L186.8,145.0 L187.5,143.7 L188.2,142.3 L188.9,140.9 L189.5,139.5 L190.2,138.1 L190.9,136.6 L191.5,135.2 L192.2,133.7 L192.9,132.2 L193.6,130.7 L194.2,129.2 L194.9,127.7 L195.6,126.1 L196.2,124.5 L196.9,122.9 L197.6,121.3 L198.2,119.7 L198.9,118.0 L199.6,116.4 L200.2,114.7 L200.9,113.0 L201.6,111.3 L202.3,109.5 L202.9,107.8 L203.6,106.0 L204.3,104.2 L204.9,102.4 L205.6,100.6 L206.3,98.8 L206.9,96.9 L207.6,95.0 L208.3,93.2 L209.0,91.3 L209.6,89.3 L210.3,87.4 L211.0,85.4 L211.6,83.4 L212.3,81.5 L213.0,79.4 L213.7,77.4 L214.3,75.4 L215.0,73.3 L215.7,71.2 L216.3,69.1 L217.0,67.0 L217.7,64.9 L218.3,62.7 L219.0,60.6 L219.7,58.4 L220.3,56.2 L221.0,54.0 L221.7,51.7 L222.4,49.5 L223.0,47.2 L223.7,44.9 L224.4,42.6 L225.0,40.3 L225.7,37.9 L226.4,35.6 L227.1,33.2 L227.7,30.8 L228.4,28.4 L229.1,26.0 L229.7,23.5 L230.4,21.0 L231.1,18.6 L231.7,16.1 L232.4,13.6 L233.1,11.0 L233.8,8.5 L234.4,5.9 L235.1,3.3 L235.8,0.7 L236.4,-1.9 L237.1,-4.5 L237.8,-7.2 L238.4,-9.9 L239.1,-12.6 L239.8,-15.3 L240.4,-18.0 L241.1,-20.7 L241.8,-23.5 L242.5,-26.3 L243.1,-29.1 L243.8,-31.9 L244.5,-34.7 L245.1,-37.5 L245.8,-40.4 L246.5,-43.3 L247.2,-46.2 L247.8,-49.1 L248.5,-52.0 L249.2,-55.0 L249.8,-58.0 L250.5,-60.9 L251.2,-63.9 L251.8,-67.0 L252.5,-70.0 L253.2,-73.0 L253.8,-76.1 L254.5,-79.2 L255.2,-82.3 L255.9,-85.4 L256.5,-88.6 L257.2,-91.7 L257.9,-94.9 L258.5,-98.1 L259.2,-101.3 L259.9,-104.5 L260.6,-107.8 L261.2,-111.1 L261.9,-114.3 L262.6,-117.6 L263.2,-120.9 L263.9,-124.3 L264.6,-127.6 L265.2,-131.0 L265.9,-134.4 L266.6,-137.8 L267.2,-141.2 L267.9,-144.6 L268.6,-148.1 L269.3,-151.6 L269.9,-155.1 L270.6,-158.6 L271.3,-162.1 L271.9,-165.6 L272.6,-169.2 L273.3,-172.8 L273.9,-176.4 L274.6,-180.0 L275.3,-183.6 L276.0,-187.2 L276.6,-190.9 L277.3,-194.6 L278.0,-198.3 L278.6,-202.0 L279.3,-205.7 L280.0,-209.5 L280.6,-213.2 L281.3,-217.0 L282.0,-220.8 L282.7,-224.6 L283.3,-228.5 L284.0,-232.3\" clip-path=\"url(#c62533)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"45.8\" y=\"35.3\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x² − 4</text><path d=\"M16.0,282.7 L16.7,281.9 L17.3,281.1 L18.0,280.3 L18.7,279.6 L19.3,278.8 L20.0,278.0 L20.7,277.3 L21.4,276.5 L22.0,275.7 L22.7,274.9 L23.4,274.2 L24.0,273.4 L24.7,272.6 L25.4,271.9 L26.0,271.1 L26.7,270.3 L27.4,269.5 L28.1,268.8 L28.7,268.0 L29.4,267.2 L30.1,266.4 L30.7,265.7 L31.4,264.9 L32.1,264.1 L32.8,263.4 L33.4,262.6 L34.1,261.8 L34.8,261.0 L35.4,260.3 L36.1,259.5 L36.8,258.7 L37.4,257.9 L38.1,257.2 L38.8,256.4 L39.5,255.6 L40.1,254.9 L40.8,254.1 L41.5,253.3 L42.1,252.5 L42.8,251.8 L43.5,251.0 L44.1,250.2 L44.8,249.4 L45.5,248.7 L46.2,247.9 L46.8,247.1 L47.5,246.4 L48.2,245.6 L48.8,244.8 L49.5,244.0 L50.2,243.3 L50.8,242.5 L51.5,241.7 L52.2,241.0 L52.8,240.2 L53.5,239.4 L54.2,238.6 L54.9,237.9 L55.5,237.1 L56.2,236.3 L56.9,235.5 L57.5,234.8 L58.2,234.0 L58.9,233.2 L59.5,232.5 L60.2,231.7 L60.9,230.9 L61.6,230.1 L62.2,229.4 L62.9,228.6 L63.6,227.8 L64.2,227.0 L64.9,226.3 L65.6,225.5 L66.2,224.7 L66.9,224.0 L67.6,223.2 L68.3,222.4 L68.9,221.6 L69.6,220.9 L70.3,220.1 L70.9,219.3 L71.6,218.5 L72.3,217.8 L73.0,217.0 L73.6,216.2 L74.3,215.5 L75.0,214.7 L75.6,213.9 L76.3,213.1 L77.0,212.4 L77.6,211.6 L78.3,210.8 L79.0,210.1 L79.7,209.3 L80.3,208.5 L81.0,207.7 L81.7,207.0 L82.3,206.2 L83.0,205.4 L83.7,204.6 L84.3,203.9 L85.0,203.1 L85.7,202.3 L86.3,201.6 L87.0,200.8 L87.7,200.0 L88.4,199.2 L89.0,198.5 L89.7,197.7 L90.4,196.9 L91.0,196.1 L91.7,195.4 L92.4,194.6 L93.0,193.8 L93.7,193.1 L94.4,192.3 L95.1,191.5 L95.7,190.7 L96.4,190.0 L97.1,189.2 L97.7,188.4 L98.4,187.6 L99.1,186.9 L99.8,186.1 L100.4,185.3 L101.1,184.6 L101.8,183.8 L102.4,183.0 L103.1,182.2 L103.8,181.5 L104.4,180.7 L105.1,179.9 L105.8,179.2 L106.5,178.4 L107.1,177.6 L107.8,176.8 L108.5,176.1 L109.1,175.3 L109.8,174.5 L110.5,173.7 L111.1,173.0 L111.8,172.2 L112.5,171.4 L113.2,170.7 L113.8,169.9 L114.5,169.1 L115.2,168.3 L115.8,167.6 L116.5,166.8 L117.2,166.0 L117.8,165.2 L118.5,164.5 L119.2,163.7 L119.8,162.9 L120.5,162.2 L121.2,161.4 L121.9,160.6 L122.5,159.8 L123.2,159.1 L123.9,158.3 L124.5,157.5 L125.2,156.7 L125.9,156.0 L126.5,155.2 L127.2,154.4 L127.9,153.7 L128.6,152.9 L129.2,152.1 L129.9,151.3 L130.6,150.6 L131.2,149.8 L131.9,149.0 L132.6,148.3 L133.2,147.5 L133.9,146.7 L134.6,145.9 L135.3,145.2 L135.9,144.4 L136.6,143.6 L137.3,142.8 L137.9,142.1 L138.6,141.3 L139.3,140.5 L139.9,139.8 L140.6,139.0 L141.3,138.2 L142.0,137.4 L142.6,136.7 L143.3,135.9 L144.0,135.1 L144.6,134.3 L145.3,133.6 L146.0,132.8 L146.7,132.0 L147.3,131.3 L148.0,130.5 L148.7,129.7 L149.3,128.9 L150.0,128.2 L150.7,127.4 L151.3,126.6 L152.0,125.8 L152.7,125.1 L153.3,124.3 L154.0,123.5 L154.7,122.8 L155.4,122.0 L156.0,121.2 L156.7,120.4 L157.4,119.7 L158.0,118.9 L158.7,118.1 L159.4,117.4 L160.1,116.6 L160.7,115.8 L161.4,115.0 L162.1,114.3 L162.7,113.5 L163.4,112.7 L164.1,111.9 L164.7,111.2 L165.4,110.4 L166.1,109.6 L166.8,108.9 L167.4,108.1 L168.1,107.3 L168.8,106.5 L169.4,105.8 L170.1,105.0 L170.8,104.2 L171.4,103.4 L172.1,102.7 L172.8,101.9 L173.4,101.1 L174.1,100.4 L174.8,99.6 L175.5,98.8 L176.1,98.0 L176.8,97.3 L177.5,96.5 L178.1,95.7 L178.8,94.9 L179.5,94.2 L180.2,93.4 L180.8,92.6 L181.5,91.9 L182.2,91.1 L182.8,90.3 L183.5,89.5 L184.2,88.8 L184.8,88.0 L185.5,87.2 L186.2,86.5 L186.8,85.7 L187.5,84.9 L188.2,84.1 L188.9,83.4 L189.5,82.6 L190.2,81.8 L190.9,81.0 L191.5,80.3 L192.2,79.5 L192.9,78.7 L193.6,78.0 L194.2,77.2 L194.9,76.4 L195.6,75.6 L196.2,74.9 L196.9,74.1 L197.6,73.3 L198.2,72.5 L198.9,71.8 L199.6,71.0 L200.2,70.2 L200.9,69.5 L201.6,68.7 L202.3,67.9 L202.9,67.1 L203.6,66.4 L204.3,65.6 L204.9,64.8 L205.6,64.0 L206.3,63.3 L206.9,62.5 L207.6,61.7 L208.3,61.0 L209.0,60.2 L209.6,59.4 L210.3,58.6 L211.0,57.9 L211.6,57.1 L212.3,56.3 L213.0,55.6 L213.7,54.8 L214.3,54.0 L215.0,53.2 L215.7,52.5 L216.3,51.7 L217.0,50.9 L217.7,50.1 L218.3,49.4 L219.0,48.6 L219.7,47.8 L220.3,47.1 L221.0,46.3 L221.7,45.5 L222.4,44.7 L223.0,44.0 L223.7,43.2 L224.4,42.4 L225.0,41.6 L225.7,40.9 L226.4,40.1 L227.1,39.3 L227.7,38.6 L228.4,37.8 L229.1,37.0 L229.7,36.2 L230.4,35.5 L231.1,34.7 L231.7,33.9 L232.4,33.1 L233.1,32.4 L233.8,31.6 L234.4,30.8 L235.1,30.1 L235.8,29.3 L236.4,28.5 L237.1,27.7 L237.8,27.0 L238.4,26.2 L239.1,25.4 L239.8,24.7 L240.4,23.9 L241.1,23.1 L241.8,22.3 L242.5,21.6 L243.1,20.8 L243.8,20.0 L244.5,19.2 L245.1,18.5 L245.8,17.7 L246.5,16.9 L247.2,16.2 L247.8,15.4 L248.5,14.6 L249.2,13.8 L249.8,13.1 L250.5,12.3 L251.2,11.5 L251.8,10.7 L252.5,10.0 L253.2,9.2 L253.8,8.4 L254.5,7.7 L255.2,6.9 L255.9,6.1 L256.5,5.3 L257.2,4.6 L257.9,3.8 L258.5,3.0 L259.2,2.2 L259.9,1.5 L260.6,0.7 L261.2,-0.1 L261.9,-0.8 L262.6,-1.6 L263.2,-2.4 L263.9,-3.2 L264.6,-3.9 L265.2,-4.7 L265.9,-5.5 L266.6,-6.2 L267.2,-7.0 L267.9,-7.8 L268.6,-8.6 L269.3,-9.3 L269.9,-10.1 L270.6,-10.9 L271.3,-11.7 L271.9,-12.4 L272.6,-13.2 L273.3,-14.0 L273.9,-14.7 L274.6,-15.5 L275.3,-16.3 L276.0,-17.1 L276.6,-17.8 L277.3,-18.6 L278.0,-19.4 L278.6,-20.2 L279.3,-20.9 L280.0,-21.7 L280.6,-22.5 L281.3,-23.2 L282.0,-24.0 L282.7,-24.8 L283.3,-25.6 L284.0,-26.3\" clip-path=\"url(#c62533)\" style=\"fill:none;stroke:var(--accent-text);stroke-width:2.2;stroke-dasharray:6 4\"/><text x=\"263.2\" y=\"11.3\" text-anchor=\"middle\" style=\"fill:var(--accent-text);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = 2x − 1</text></svg>"}, {"kind": "blank", "p": "Solve y = x² + 1 and y = 2x.", "tag": "", "marks": "", "flat": [{"t": "Substitute: x² − 2x + 1 = 0 has discriminant __B1__", "a": {"B1": "0"}}, {"t": "The only solution is __B1__", "a": {"B1": "(1, 2)"}, "expr": "coord"}], "sol": "(−2)² − 4(1)(1) = 0, so there is one solution: the line touches the parabola.\nx² − 2x + 1 = (x − 1)² = 0, so x = 1 and y = 2(1) = 2."}, {"kind": "mcq", "text": "Solve by elimination: y = x² + 3x − 1 and y = −x² + x + 3.", "opts": ["(1, 3) only", "(1, 3) and (−2, −3)", "(1, 3) and (2, 9)", "(−1, −3) and (2, 9)"], "correct": 1, "tag": "", "sol": "Subtract: 0 = 2x² + 2x − 4 → x² + x − 2 = 0 → x = 1 or −2. y(1) = 1 + 3 − 1 = 3; y(−2) = 4 − 6 − 1 = −3. Check in the second: −1 + 1 + 3 = 3 ✓ and −4 − 2 + 3 = −3 ✓"}, {"kind": "blank", "p": "Solve y = 3 − x² and y = x + 1.", "tag": "", "marks": "", "flat": [{"t": "Substitute: x² + x + __B1__ = 0", "a": {"B1": "-2"}}, {"t": "x = __B1__", "a": {"B1": "-2, 1"}, "expr": "set"}, {"t": "The sum of the y-coordinates of the two solutions is __B1__", "a": {"B1": "1"}}], "sol": "3 − x² = x + 1 → 0 = x² + x − 2.\n(x + 2)(x − 1) = 0 → x = −2 or x = 1.\ny = −2 + 1 = −1 and y = 1 + 1 = 2: points (−2, −1) and (1, 2); −1 + 2 = 1."}, {"kind": "mcq", "text": "<b>Error analysis.</b> To solve the system y = x² and y = −1, Kiran wrote x² = −1, so x = ±1. What is correct?", "opts": ["There is no solution: no real number squared is −1", "x = 0, so the solution is (0, −1)", "Kiran is right: (1, −1) and (−1, −1)", "Only (−1, −1) works"], "correct": 0, "tag": "", "sol": "(±1)² = 1, not −1. The parabola y = x² never goes below the x-axis, so the line y = −1 never meets it: no solution."}, {"kind": "blank", "p": "Solve y = x² + 4 and y = x.", "tag": "", "marks": "", "flat": [{"t": "x² − x + 4 = 0 has discriminant __B1__", "a": {"B1": "-15"}}, {"t": "Number of solutions of the system: __B1__", "a": {"B1": "0"}, "accept": ["none", "zero", "no solutions", "no real solutions", "no solution"]}], "sol": "(−1)² − 4(1)(4) = 1 − 16 = −15.\nThe discriminant is negative, so the line misses the parabola: no solution."}, {"kind": "mcq", "text": "Solve y = x² and y = x + 3. Round to 2 decimal places.", "opts": ["(−2.30, 0.70) and (1.30, 4.30)", "(3.00, 6.00) and (−1.00, 2.00)", "(2.30, 5.30) and (1.30, 4.30)", "(2.30, 5.30) and (−1.30, 1.70)"], "correct": 3, "tag": "", "sol": "x² − x − 3 = 0 → x = (1 ± √13)/2 ≈ 2.30 or −1.30. Then y = x + 3 ≈ 5.30 or 1.70.", "tools": ["calc", "desmos"], "desmos": ["y=x^{2}", "y=x+3"]}, {"kind": "blank", "p": "A ball's path is y = −0.1x² + 2x and a straight ramp follows y = 0.5x (x and y in metres).", "tag": "", "marks": "", "flat": [{"t": "Apart from x = 0, the ball meets the ramp at x = __B1__ m", "a": {"B1": "15"}}, {"t": "at a height of __B1__ m", "a": {"B1": "7.5"}}], "sol": "−0.1x² + 2x = 0.5x → −0.1x² + 1.5x = 0 → −0.1x(x − 15) = 0, so x = 0 or x = 15.\ny = 0.5(15) = 7.5 m. Check: −0.1(225) + 30 = 7.5 ✓", "tools": ["desmos"], "desmos": ["y=-0.1x^{2}+2x", "y=0.5x"]}, {"kind": "mcq", "text": "A firm's revenue is R = −x² + 12x and its cost is C = 2x + 9 (thousands of dollars; x thousand units). When does it break even (R = C)?", "opts": ["At 1 thousand and 9 thousand units", "At 2 thousand and 6 thousand units", "At 3 thousand units only", "It never breaks even"], "correct": 0, "tag": "", "sol": "−x² + 12x = 2x + 9 → x² − 10x + 9 = 0 → (x − 1)(x − 9) = 0 → x = 1 or x = 9."}, {"kind": "blank", "p": "Solve the equation x² − 1 = −x + 1 by writing it as a system y = x² − 1 and y = −x + 1.", "tag": "", "marks": "", "flat": [{"t": "x = __B1__", "a": {"B1": "-2, 1"}, "expr": "set"}, {"t": "For the solution with negative x, y = __B1__", "a": {"B1": "3"}}], "sol": "x² − 1 = −x + 1 → x² + x − 2 = 0 → (x + 2)(x − 1) = 0.\nx = −2: y = −(−2) + 1 = 3; check (−2)² − 1 = 3 ✓", "tools": ["desmos"], "desmos": ["y=x^{2}-1", "y=-x+1"]}, {"kind": "mcq", "text": "Solve the system y = x² − 4 and y = −x² + 4.", "opts": ["(0, −4) and (0, 4)", "No solution", "(−2, 0) and (2, 0)", "(−2, 4) and (2, 4)"], "correct": 2, "tag": "", "sol": "x² − 4 = −x² + 4 → 2x² = 8 → x = ±2, and y = 4 − 4 = 0. Both parabolas pass through (−2, 0) and (2, 0)."}, {"kind": "blank", "p": "Solve y = 2x² − 3x and y = x + 6.", "tag": "", "marks": "", "flat": [{"t": "2x² − 4x − 6 = 0 gives x = __B1__", "a": {"B1": "-1, 3"}, "expr": "set"}, {"t": "The larger y-coordinate is __B1__", "a": {"B1": "9"}}], "sol": "Divide by 2: x² − 2x − 3 = 0 → (x − 3)(x + 1) = 0.\nx = 3: y = 9; x = −1: y = 5. Check: 2(9) − 9 = 9 ✓ and 2 + 3 = 5 ✓"}]}, {"id": "s7", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "Simplify √98.", "opts": ["14√7", "2√7", "49√2", "7√2"], "correct": 3, "tag": "", "sol": "98 = 49 · 2, so √98 = 7√2."}, {"kind": "blank", "p": "Solve 2x² = 50.", "tag": "", "marks": "", "flat": [{"t": "x² = __B1__", "a": {"B1": "25"}}, {"t": "x = __B1__", "a": {"B1": "-5, 5"}, "expr": "set"}], "sol": "Divide by 2: x² = 25.\nx = ±5."}, {"kind": "mcq", "text": "Simplify 3 / √6.", "opts": ["√6 / 2", "√2", "3√6 / 36", "3√6"], "correct": 0, "tag": "", "sol": "Multiply by √6 / √6: 3√6 / 6 = √6 / 2."}, {"kind": "blank", "p": "Solve x² + 8x + 7 = 0 by completing the square.", "tag": "", "marks": "", "flat": [{"t": "x² + 8x = −7. Add __B1__ to both sides", "a": {"B1": "16"}}, {"t": "x = __B1__", "a": {"B1": "-7, -1"}, "expr": "set"}], "sol": "(8 ÷ 2)² = 16.\n(x + 4)² = 9 → x + 4 = ±3 → x = −1 or x = −7."}, {"kind": "mcq", "text": "How many real solutions does x² − 3x + 5 = 0 have?", "opts": ["None, because b² − 4ac = −11", "Two, because b² − 4ac = 29", "One, because b² − 4ac = 0", "Two, because c is positive"], "correct": 0, "tag": "", "sol": "b² − 4ac = 9 − 20 = −11 < 0, so there are no real solutions."}, {"kind": "blank", "p": "Solve x² − 5x + 2 = 0 with the Quadratic Formula.", "tag": "", "marks": "", "flat": [{"t": "Larger solution (exact): x = __B1__", "a": {"B1": "(5+√17)/2"}, "expr": "calc", "accept": ["5/2+√17/2", "2.5+√17/2"]}, {"t": "Smaller solution to 2 decimal places: x ≈ __B1__", "a": {"B1": "0.44"}}], "sol": "b² − 4ac = 25 − 8 = 17, so x = (5 ± √17)/2.\n(5 − √17)/2 ≈ (5 − 4.123)/2 ≈ 0.44.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "Use the graph of y = x² + 2x − 3 to solve x² + 2x − 3 = 0.", "opts": ["x = −3 only", "x = −3 and x = 1", "x = −1 and x = −4", "x = 3 and x = −1"], "correct": 1, "tag": "", "sol": "The graph crosses the x-axis at −3 and 1. Check: 9 − 6 − 3 = 0 ✓ and 1 + 2 − 3 = 0 ✓ ((−1, −4) is the vertex.)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"83.0\" y1=\"214.0\" x2=\"83.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"116.5\" y1=\"214.0\" x2=\"116.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"217.0\" y1=\"214.0\" x2=\"217.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"250.5\" y1=\"214.0\" x2=\"250.5\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"195.3\" x2=\"284.0\" y2=\"195.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"176.5\" x2=\"284.0\" y2=\"176.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"157.8\" x2=\"284.0\" y2=\"157.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"139.1\" x2=\"284.0\" y2=\"139.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"120.4\" x2=\"284.0\" y2=\"120.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"101.6\" x2=\"284.0\" y2=\"101.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"82.9\" x2=\"284.0\" y2=\"82.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"64.2\" x2=\"284.0\" y2=\"64.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"45.5\" x2=\"284.0\" y2=\"45.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"26.7\" x2=\"284.0\" y2=\"26.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"8.0\" x2=\"284.0\" y2=\"8.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"120.4\" x2=\"284.0\" y2=\"120.4\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"8.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"129.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"83.0\" y=\"129.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"150.0\" y=\"129.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"217.0\" y=\"129.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"284.0\" y=\"129.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"179.5\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"179.5\" y=\"176.5\" text-anchor=\"end\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"179.5\" y=\"139.1\" text-anchor=\"end\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"179.5\" y=\"101.6\" text-anchor=\"end\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"179.5\" y=\"64.2\" text-anchor=\"end\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"179.5\" y=\"26.7\" text-anchor=\"end\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"280.0\" y=\"112.4\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"191.5\" y=\"14.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c26633\"><rect x=\"16.0\" y=\"8.0\" width=\"268.0\" height=\"206.0\"/></clipPath><path d=\"M16.0,-104.4 L16.7,-101.4 L17.3,-98.4 L18.0,-95.4 L18.7,-92.5 L19.3,-89.6 L20.0,-86.7 L20.7,-83.8 L21.4,-80.9 L22.0,-78.0 L22.7,-75.1 L23.4,-72.3 L24.0,-69.5 L24.7,-66.7 L25.4,-63.9 L26.0,-61.1 L26.7,-58.3 L27.4,-55.6 L28.1,-52.9 L28.7,-50.1 L29.4,-47.4 L30.1,-44.7 L30.7,-42.1 L31.4,-39.4 L32.1,-36.8 L32.8,-34.1 L33.4,-31.5 L34.1,-28.9 L34.8,-26.3 L35.4,-23.8 L36.1,-21.2 L36.8,-18.7 L37.4,-16.2 L38.1,-13.6 L38.8,-11.1 L39.5,-8.7 L40.1,-6.2 L40.8,-3.8 L41.5,-1.3 L42.1,1.1 L42.8,3.5 L43.5,5.9 L44.1,8.3 L44.8,10.6 L45.5,13.0 L46.2,15.3 L46.8,17.6 L47.5,19.9 L48.2,22.2 L48.8,24.5 L49.5,26.7 L50.2,29.0 L50.8,31.2 L51.5,33.4 L52.2,35.6 L52.9,37.8 L53.5,39.9 L54.2,42.1 L54.9,44.2 L55.5,46.3 L56.2,48.5 L56.9,50.5 L57.5,52.6 L58.2,54.7 L58.9,56.7 L59.5,58.8 L60.2,60.8 L60.9,62.8 L61.6,64.8 L62.2,66.7 L62.9,68.7 L63.6,70.6 L64.2,72.5 L64.9,74.5 L65.6,76.3 L66.2,78.2 L66.9,80.1 L67.6,81.9 L68.3,83.8 L68.9,85.6 L69.6,87.4 L70.3,89.2 L70.9,91.0 L71.6,92.7 L72.3,94.5 L73.0,96.2 L73.6,97.9 L74.3,99.6 L75.0,101.3 L75.6,103.0 L76.3,104.6 L77.0,106.3 L77.6,107.9 L78.3,109.5 L79.0,111.1 L79.7,112.7 L80.3,114.3 L81.0,115.8 L81.7,117.3 L82.3,118.9 L83.0,120.4 L83.7,121.9 L84.3,123.3 L85.0,124.8 L85.7,126.2 L86.4,127.7 L87.0,129.1 L87.7,130.5 L88.4,131.9 L89.0,133.2 L89.7,134.6 L90.4,135.9 L91.0,137.3 L91.7,138.6 L92.4,139.9 L93.0,141.2 L93.7,142.4 L94.4,143.7 L95.1,144.9 L95.7,146.1 L96.4,147.3 L97.1,148.5 L97.7,149.7 L98.4,150.9 L99.1,152.0 L99.8,153.1 L100.4,154.3 L101.1,155.4 L101.8,156.4 L102.4,157.5 L103.1,158.6 L103.8,159.6 L104.4,160.6 L105.1,161.6 L105.8,162.6 L106.5,163.6 L107.1,164.6 L107.8,165.5 L108.5,166.5 L109.1,167.4 L109.8,168.3 L110.5,169.2 L111.1,170.1 L111.8,170.9 L112.5,171.8 L113.1,172.6 L113.8,173.4 L114.5,174.2 L115.2,175.0 L115.8,175.8 L116.5,176.5 L117.2,177.3 L117.8,178.0 L118.5,178.7 L119.2,179.4 L119.9,180.1 L120.5,180.8 L121.2,181.4 L121.9,182.1 L122.5,182.7 L123.2,183.3 L123.9,183.9 L124.5,184.5 L125.2,185.0 L125.9,185.6 L126.5,186.1 L127.2,186.6 L127.9,187.1 L128.6,187.6 L129.2,188.1 L129.9,188.5 L130.6,189.0 L131.2,189.4 L131.9,189.8 L132.6,190.2 L133.2,190.6 L133.9,191.0 L134.6,191.3 L135.3,191.6 L135.9,192.0 L136.6,192.3 L137.3,192.6 L137.9,192.8 L138.6,193.1 L139.3,193.4 L139.9,193.6 L140.6,193.8 L141.3,194.0 L142.0,194.2 L142.6,194.4 L143.3,194.5 L144.0,194.7 L144.6,194.8 L145.3,194.9 L146.0,195.0 L146.7,195.1 L147.3,195.2 L148.0,195.2 L148.7,195.2 L149.3,195.3 L150.0,195.3 L150.7,195.3 L151.3,195.2 L152.0,195.2 L152.7,195.2 L153.3,195.1 L154.0,195.0 L154.7,194.9 L155.4,194.8 L156.0,194.7 L156.7,194.5 L157.4,194.4 L158.0,194.2 L158.7,194.0 L159.4,193.8 L160.0,193.6 L160.7,193.4 L161.4,193.1 L162.1,192.8 L162.7,192.6 L163.4,192.3 L164.1,192.0 L164.7,191.6 L165.4,191.3 L166.1,191.0 L166.8,190.6 L167.4,190.2 L168.1,189.8 L168.8,189.4 L169.4,189.0 L170.1,188.5 L170.8,188.1 L171.4,187.6 L172.1,187.1 L172.8,186.6 L173.5,186.1 L174.1,185.6 L174.8,185.0 L175.5,184.5 L176.1,183.9 L176.8,183.3 L177.5,182.7 L178.1,182.1 L178.8,181.4 L179.5,180.8 L180.2,180.1 L180.8,179.4 L181.5,178.7 L182.2,178.0 L182.8,177.3 L183.5,176.5 L184.2,175.8 L184.8,175.0 L185.5,174.2 L186.2,173.4 L186.8,172.6 L187.5,171.8 L188.2,170.9 L188.9,170.1 L189.5,169.2 L190.2,168.3 L190.9,167.4 L191.5,166.5 L192.2,165.5 L192.9,164.6 L193.5,163.6 L194.2,162.6 L194.9,161.6 L195.6,160.6 L196.2,159.6 L196.9,158.6 L197.6,157.5 L198.2,156.4 L198.9,155.4 L199.6,154.3 L200.2,153.1 L200.9,152.0 L201.6,150.9 L202.3,149.7 L202.9,148.5 L203.6,147.3 L204.3,146.1 L204.9,144.9 L205.6,143.7 L206.3,142.4 L207.0,141.2 L207.6,139.9 L208.3,138.6 L209.0,137.3 L209.6,135.9 L210.3,134.6 L211.0,133.2 L211.6,131.9 L212.3,130.5 L213.0,129.1 L213.7,127.7 L214.3,126.2 L215.0,124.8 L215.7,123.3 L216.3,121.9 L217.0,120.4 L217.7,118.9 L218.3,117.3 L219.0,115.8 L219.7,114.3 L220.3,112.7 L221.0,111.1 L221.7,109.5 L222.4,107.9 L223.0,106.3 L223.7,104.6 L224.4,103.0 L225.0,101.3 L225.7,99.6 L226.4,97.9 L227.0,96.2 L227.7,94.5 L228.4,92.7 L229.1,91.0 L229.7,89.2 L230.4,87.4 L231.1,85.6 L231.7,83.8 L232.4,81.9 L233.1,80.1 L233.8,78.2 L234.4,76.3 L235.1,74.5 L235.8,72.5 L236.4,70.6 L237.1,68.7 L237.8,66.7 L238.4,64.8 L239.1,62.8 L239.8,60.8 L240.5,58.8 L241.1,56.7 L241.8,54.7 L242.5,52.6 L243.1,50.5 L243.8,48.5 L244.5,46.3 L245.1,44.2 L245.8,42.1 L246.5,39.9 L247.2,37.8 L247.8,35.6 L248.5,33.4 L249.2,31.2 L249.8,29.0 L250.5,26.7 L251.2,24.5 L251.8,22.2 L252.5,19.9 L253.2,17.6 L253.8,15.3 L254.5,13.0 L255.2,10.6 L255.9,8.3 L256.5,5.9 L257.2,3.5 L257.9,1.1 L258.5,-1.3 L259.2,-3.8 L259.9,-6.2 L260.5,-8.7 L261.2,-11.1 L261.9,-13.6 L262.6,-16.2 L263.2,-18.7 L263.9,-21.2 L264.6,-23.8 L265.2,-26.3 L265.9,-28.9 L266.6,-31.5 L267.2,-34.1 L267.9,-36.8 L268.6,-39.4 L269.3,-42.1 L269.9,-44.7 L270.6,-47.4 L271.3,-50.1 L271.9,-52.9 L272.6,-55.6 L273.3,-58.3 L273.9,-61.1 L274.6,-63.9 L275.3,-66.7 L276.0,-69.5 L276.6,-72.3 L277.3,-75.1 L278.0,-78.0 L278.6,-80.9 L279.3,-83.8 L280.0,-86.7 L280.7,-89.6 L281.3,-92.5 L282.0,-95.4 L282.7,-98.4 L283.3,-101.4 L284.0,-104.4\" clip-path=\"url(#c26633)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"237.1\" y=\"61.7\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = x² + 2x − 3</text></svg>"}, {"kind": "blank", "p": "Solve the system y = x² − 2 and y = x.", "tag": "", "marks": "", "flat": [{"t": "x = __B1__", "a": {"B1": "-1, 2"}, "expr": "set"}, {"t": "The sum of the y-coordinates of the solutions is __B1__", "a": {"B1": "1"}}], "sol": "x² − 2 = x → x² − x − 2 = 0 → x = 2 or −1.\nThe points are (2, 2) and (−1, −1): 2 + (−1) = 1."}, {"kind": "mcq", "text": "Simplify 2√5 · 3√10.", "opts": ["6√15", "15√2", "60√5", "30√2"], "correct": 3, "tag": "", "sol": "2 · 3 = 6 and √5 · √10 = √50 = 5√2, so the product is 6 · 5√2 = 30√2."}]}, {"id": "s8", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "Look at the solutions of x² = k as k changes.", "tag": "", "marks": "", "flat": [{"t": "k = 16: x = __B1__", "a": {"B1": "-4, 4"}, "expr": "set"}, {"t": "k = 0: number of solutions = __B1__", "a": {"B1": "1"}, "accept": ["one"]}, {"t": "k = −16: number of real solutions = __B1__", "a": {"B1": "0"}, "accept": ["none", "zero", "no solutions", "no real solutions", "no solution"]}], "sol": "x = ±√16 = ±4.\nOnly 0² = 0, so one solution.\nNo real number squared is negative: none."}, {"kind": "mcq", "text": "x² + 2x + 1 = (x + 1)², x² + 4x + 4 = (x + 2)², x² + 6x + 9 = (x + 3)². Following the pattern, which c makes x² + 20x + c a perfect square?", "opts": ["100", "20", "40", "400"], "correct": 0, "tag": "", "sol": "The constant is always (b ÷ 2)²: (20 ÷ 2)² = 100, and x² + 20x + 100 = (x + 10)²."}, {"kind": "blank", "p": "√2 = 1√2, √8 = 2√2, √18 = 3√2. Continue the pattern √(2n²) = n√2.", "tag": "", "marks": "", "flat": [{"t": "√32 = __B1__√2", "a": {"B1": "4"}}, {"t": "√50 = __B1__√2", "a": {"B1": "5"}}, {"t": "√200 = __B1__√2", "a": {"B1": "10"}}], "sol": "32 = 2 · 4², so √32 = 4√2.\n50 = 2 · 5², so √50 = 5√2.\n200 = 2 · 10², so √200 = 10√2."}, {"kind": "mcq", "text": "For which values of c does x² + 4x + c = 0 have two real solutions?", "opts": ["c > 4", "every value of c", "c < 4", "c = 4"], "correct": 2, "tag": "", "sol": "b² − 4ac = 16 − 4c > 0 when c < 4. When c = 4 there is one solution and when c > 4 there are none."}, {"kind": "blank", "p": "Compare each equation's solutions with its coefficients.", "tag": "", "marks": "", "flat": [{"t": "x² − 7x + 10 = 0 has solutions x = __B1__", "a": {"B1": "2, 5"}, "expr": "set"}, {"t": "x² − 9x + 14 = 0: the sum of the solutions is __B1__", "a": {"B1": "9"}}, {"t": "x² − 9x + 14 = 0: the product of the solutions is __B1__", "a": {"B1": "14"}}], "sol": "(x − 2)(x − 5) = 0: x = 2 or 5. Note 2 + 5 = 7 and 2 × 5 = 10.\n(x − 2)(x − 7) = 0: 2 + 7 = 9, the opposite of b.\n2 × 7 = 14, equal to c."}, {"kind": "mcq", "text": "The vertex of y = (x − h)² + k is (h, k). When does y = (x − h)² + k have two x-intercepts?", "opts": ["When h < 0", "When k = 0", "When k < 0", "When k > 0"], "correct": 2, "tag": "", "sol": "The parabola opens up from (h, k). It crosses the x-axis twice only if the vertex is below it, k < 0."}, {"kind": "blank", "p": "A line y = mx meets the parabola y = x² + 1 where x² − mx + 1 = 0, whose discriminant is m² − 4.", "tag": "", "marks": "", "flat": [{"t": "m = 1: number of intersection points = __B1__", "a": {"B1": "0"}, "accept": ["none", "zero", "no solutions", "no real solutions", "no solution"]}, {"t": "m = 2: number of intersection points = __B1__", "a": {"B1": "1"}, "accept": ["one"]}, {"t": "m = 3: number of intersection points = __B1__", "a": {"B1": "2"}, "accept": ["two"]}], "sol": "1 − 4 = −3 < 0: none.\n4 − 4 = 0: one (the line is tangent at (1, 2)).\n9 − 4 = 5 > 0: two."}, {"kind": "mcq", "text": "Using the pattern (√a + √b)(√a − √b) = a − b, simplify (√7 + √3)(√7 − √3).", "opts": ["√21", "10", "2", "4"], "correct": 3, "tag": "", "sol": "a − b = 7 − 3 = 4. The middle terms −√21 and +√21 cancel."}, {"kind": "blank", "p": "An object falls d = 16t² feet in t seconds, so t = √d / 4.", "tag": "", "marks": "", "flat": [{"t": "d = 64: t = __B1__ s", "a": {"B1": "2"}}, {"t": "d = 144: t = __B1__ s", "a": {"B1": "3"}}, {"t": "d = 100: t = __B1__ s", "a": {"B1": "2.5"}}], "sol": "√64 / 4 = 8 / 4 = 2.\n√144 / 4 = 12 / 4 = 3.\n√100 / 4 = 10 / 4 = 2.5. To fall twice as long, an object must fall 4 times as far."}]}, {"id": "s9", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "mcq", "text": "In the Quadratic Formula, what is the expression b² − 4ac called?", "opts": ["The discriminant", "The vertex", "The radicand of the axis", "The conjugate"], "correct": 0, "tag": "", "sol": "b² − 4ac is the discriminant: its sign tells you how many real solutions there are."}, {"kind": "blank", "p": "Complete the vocabulary.", "tag": "", "marks": "", "flat": [{"t": "√(ab) = √a · √b is the __B1__ Property of Square Roots (Product / Quotient).", "a": {"B1": "product"}, "expr": "words"}, {"t": "Removing radicals from a denominator is called __B1__ the denominator.", "a": {"B1": "rationalizing"}, "expr": "words", "accept": ["rationalising", "rationalize", "rationalise"]}], "sol": "It splits the square root of a product.\nFor example 1/√2 = √2/2 rationalizes the denominator."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Ben says √(x² + 9) = x + 3 for every x. Which reply is correct?", "opts": ["It is true because 9 is a perfect square", "It is false: for x = 4, √25 = 5 but 4 + 3 = 7", "It is true only when x is negative", "It is true by the Product Property"], "correct": 1, "tag": "", "sol": "There is no sum property for square roots. One counterexample is enough: x = 4 gives 5 ≠ 7."}, {"kind": "blank", "p": "Explain how to solve (x − 4)² = 25.", "tag": "", "marks": "", "flat": [{"t": "First take the __B1__ root of both sides.", "a": {"B1": "square"}, "expr": "words", "accept": ["square root"]}, {"t": "x = __B1__", "a": {"B1": "-1, 9"}, "expr": "set"}], "sol": "x − 4 = ±5.\nx = 4 + 5 = 9 or x = 4 − 5 = −1."}, {"kind": "mcq", "text": "Which statement is true?", "opts": ["If the discriminant is zero, the parabola touches the x-axis at its vertex", "x² = −9 has the solutions 3 and −3", "A quadratic equation can have exactly three real solutions", "Every quadratic equation can be solved by factoring with integers"], "correct": 0, "tag": "", "sol": "A zero discriminant gives one solution, the x-coordinate of the vertex, where the graph touches the axis. The other statements are false."}, {"kind": "blank", "p": "<b>Error analysis.</b> Ana solved 2x² + 12x = 14 by adding 36 to both sides. Correct her method.", "tag": "", "marks": "", "flat": [{"t": "First divide every term by __B1__", "a": {"B1": "2"}}, {"t": "x² + 6x = 7. Then add __B1__ to both sides", "a": {"B1": "9"}}, {"t": "x = __B1__", "a": {"B1": "-7, 1"}, "expr": "set"}], "sol": "The coefficient of x² must be 1 before completing the square.\n(6 ÷ 2)² = 9, giving (x + 3)² = 16.\nx + 3 = ±4, so x = 1 or x = −7."}, {"kind": "mcq", "text": "What does x = −3 ± √2 mean?", "opts": ["x = −1 or x = −5", "x = −3 + √2 or x = −3 − √2", "x = 3 + √2 or x = 3 − √2", "x = −3 + √2 only"], "correct": 1, "tag": "", "sol": "± means “plus or minus”, giving two solutions."}, {"kind": "blank", "p": "Which is larger, 4√3 or √50? Compare their squares.", "tag": "", "marks": "", "flat": [{"t": "(4√3)² = __B1__", "a": {"B1": "48"}}, {"t": "The larger number is the __B1__ one (first / second).", "a": {"B1": "second"}, "expr": "words"}], "sol": "16 × 3 = 48, while (√50)² = 50.\n50 > 48 and both are positive, so √50 is larger."}, {"kind": "mcq", "text": "What is a solution of a system made of a line and a parabola?", "opts": ["The y-intercept of the line", "A point that lies on both graphs", "The vertex of the parabola", "A point where the parabola crosses the x-axis"], "correct": 1, "tag": "", "sol": "A solution makes both equations true at once, so it lies on both graphs: an intersection point."}]}, {"id": "s10", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "mcq", "text": "A square park has an area of 2,500 m². How much fencing goes around it?", "opts": ["100 m", "200 m", "50 m", "625 m"], "correct": 1, "tag": "", "sol": "Side = √2500 = 50 m, so the perimeter is 4 × 50 = 200 m."}, {"kind": "blank", "p": "A stone is dropped from a 100 m bridge: h = −4.9t² + 100.", "tag": "", "marks": "", "flat": [{"t": "It hits the water after t ≈ __B1__ s (2 decimal places)", "a": {"B1": "4.52"}}], "sol": "0 = −4.9t² + 100 → t² = 100 ÷ 4.9 ≈ 20.41 → t ≈ 4.52 s (the negative root is rejected).", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "A basketball's height is h = −16t² + 20t + 6 feet. At which times is it 10 ft high?", "opts": ["It never reaches 10 ft", "1 s only", "0.5 s and 2 s", "0.25 s and 1 s"], "correct": 3, "tag": "", "sol": "−16t² + 20t + 6 = 10 → 16t² − 20t + 4 = 0 → 4t² − 5t + 1 = 0 → (4t − 1)(t − 1) = 0, so t = 0.25 or t = 1: once going up and once coming down."}, {"kind": "blank", "p": "A rectangular field is 10 m longer than it is wide and has an area of 1,200 m².", "tag": "", "marks": "", "flat": [{"t": "w² + 10w − 1200 = 0 gives the width w = __B1__ m", "a": {"B1": "30"}}, {"t": "Length = __B1__ m", "a": {"B1": "40"}}], "sol": "(w + 40)(w − 30) = 0, so w = 30 (w = −40 is not a width).\n30 + 10 = 40 m. Check: 30 × 40 = 1200 ✓"}, {"kind": "mcq", "text": "<b>Is this reasonable?</b> A student models a stone falling from a 45 m cliff with 4.9t² = 45 and reports “t = ±3.03 s”. What should she conclude?", "opts": ["Only t ≈ 3.03 s makes sense; a negative time is before the stone was dropped", "Only t ≈ −3.03 s makes sense, because the stone moves down", "Both answers are reasonable, because the equation has two solutions", "Neither is reasonable; t should be 45 ÷ 4.9 ≈ 9.18 s"], "correct": 0, "tag": "", "sol": "t² = 45 ÷ 4.9 ≈ 9.18 gives t ≈ ±3.03, but the context needs t > 0. The stone lands after about 3.03 s."}, {"kind": "blank", "p": "A tailoring unit's monthly profit is P = −5x² + 100x − 320 (₹ thousand) when it makes x hundred shirts.", "tag": "", "marks": "", "flat": [{"t": "Break-even (P = 0) at x = __B1__", "a": {"B1": "4, 16"}, "expr": "set"}, {"t": "The maximum profit is ₹__B1__ thousand", "a": {"B1": "180"}}], "sol": "Divide by −5: x² − 20x + 64 = 0 → (x − 4)(x − 16) = 0.\nThe vertex is halfway, x = 10: −500 + 1000 − 320 = 180."}, {"kind": "mcq", "text": "A ball's path is y = −0.05x² + x + 1.5 and the ground slopes up along y = 0.2x (metres). Where does the ball land? (Round to 2 decimal places.)", "opts": ["x ≈ 21.58 m, height ≈ 4.32 m", "x ≈ 17.70 m, height ≈ 3.54 m", "x ≈ −1.70 m, height ≈ −0.34 m", "x ≈ 8.00 m, height ≈ 1.60 m"], "correct": 1, "tag": "", "sol": "−0.05x² + x + 1.5 = 0.2x → x² − 16x − 30 = 0 → x = 8 ± √94. The positive root is 8 + 9.695 ≈ 17.70 m, and y = 0.2(17.70) ≈ 3.54 m.", "tools": ["calc", "desmos"], "desmos": ["y=-0.05x^{2}+x+1.5", "y=0.2x"]}, {"kind": "blank", "p": "Water leaving a tank from height h metres flows at v = √(19.6h) m/s. Find v for h = 5 m.", "tag": "", "marks": "", "flat": [{"t": "Exact: v = __B1__√__B2__ m/s", "a": {"B1": "7", "B2": "2"}}, {"t": "To 2 decimal places: v ≈ __B1__ m/s", "a": {"B1": "9.9"}, "accept": ["9.9"]}], "sol": "19.6 × 5 = 98 = 49 · 2, so v = √98 = 7√2.\n7 × 1.41421 ≈ 9.90 m/s.", "tools": ["calc"], "desmos": []}, {"kind": "mcq", "text": "A square table has a top of area 1.44 m². A square tablecloth hangs 0.15 m over each edge. What is the area of the cloth?", "opts": ["1.59 m²", "1.82 m²", "2.25 m²", "1.74 m²"], "correct": 2, "tag": "", "sol": "Table side = √1.44 = 1.2 m. Cloth side = 1.2 + 2(0.15) = 1.5 m, so its area is 1.5² = 2.25 m². (1.74 adds 0.3 to the area instead of to the side.)"}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-bim-ch9';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Solving Quadratic Equations</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_CALC=[['7','8','9','x','(',')'],['4','5','6','+','−','^'],['1','2','3','×','/','²'],['0','.','e','eˣ','√','ln'],['sin','cos','tan','t','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC,calc:KEYS_CALC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };


/* ================= v4: attempt classification ================= */
function v4Class(item){
  if(!item) return 'un';
  if(item.status==='skipped') return 'sk';
  if(item.status==='unanswered') return 'un';
  if(item.stepStates){ // step question
    if(item.status!=='correct' && item.status!=='revealed') return 'un';
    if(item.status==='revealed' || item.stepStates.some(function(s){return s.status==='revealed';})) return 'w';
    return item.stepStates.some(function(s){return (s.attempts||0)>0;}) ? 'c2' : 'c1';
  }
  if(item.status==='revealed') return 'w';
  if(item.status==='correct') return (item.attempts||0)>0 ? 'c2' : 'c1';
  if(item.status==='wrong'||item.status==='incorrect') return 'w';
  return 'un';
}
function v4Counts(items){ var c={n:items.length,c1:0,c2:0,w:0,sk:0,un:0}; items.forEach(function(it){ c[v4Class(it)]++; }); return c; }

/* ================= v4: My record with attempt columns ================= */
renderRecord = function(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var title=(document.querySelector('.chapter-title')||{}).textContent||'';
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+(title?' · '+esc(title):'')+'</p>';
  var st=appState.learning;
  h+='<h3>📘 Learning Sheet — attempts</h3><p class="v4leg"><b>1st ✓</b> correct on the first attempt · <b>2nd ✓</b> correct on the second attempt · <b>Wrong</b> still wrong after two attempts (answer revealed) · <b>Skip</b> skipped<span class="v4left"> · <b>Left</b> not done yet</span></p>';
  if(!st){ h+='<p class="rec-empty">Not started yet.</p>'; }
  else {
    var T={n:0,c1:0,c2:0,w:0,sk:0,un:0};
    h+='<div class="rec-table-wrap"><table class="rec-table v4rec"><thead><tr><th>Sheet</th><th>Qs</th><th>1st ✓</th><th>2nd ✓</th><th>Wrong</th><th>Skip</th><th class="v4left">Left</th></tr></thead><tbody>';
    TAB_DEFS.forEach(function(td){ var tt=st.tabs[td.id]; if(!tt||!tt.items||!tt.items.length) return; var c=v4Counts(tt.items);
      ['n','c1','c2','w','sk','un'].forEach(function(k){ T[k]+=c[k]; });
      h+='<tr><td>'+td.label+'</td><td>'+c.n+'</td><td class="v4g">'+c.c1+'</td><td class="v4o">'+c.c2+'</td><td class="v4r">'+c.w+'</td><td>'+c.sk+'</td><td class="v4left">'+c.un+'</td></tr>'; });
    h+='<tr class="v4tot"><td>Total</td><td>'+T.n+'</td><td class="v4g">'+T.c1+'</td><td class="v4o">'+T.c2+'</td><td class="v4r">'+T.w+'</td><td>'+T.sk+'</td><td class="v4left">'+T.un+'</td></tr>';
    h+='</tbody></table></div>';
    var doneN=T.c1+T.c2+T.w; if(doneN){ h+='<p class="v4sum">Of '+doneN+' questions answered: <b>'+Math.round(T.c1/doneN*100)+'%</b> right first time, <b>'+Math.round(T.c2/doneN*100)+'%</b> right on the second try, <b>'+Math.round(T.w/doneN*100)+'%</b> still wrong after two tries.</p>'; }
  }
  var q=appState.quiz;
  h+='<h3>📝 Quiz Mode</h3>';
  if(!q){ h+='<p class="rec-empty">Not started yet.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table v4rec"><thead><tr><th>Sheet</th><th>Qs</th><th>Status</th><th>Correct</th><th>Wrong</th></tr></thead><tbody>';
    TAB_DEFS.forEach(function(td){ var tt=q.tabs[td.id]; if(!tt||!tt.items||!tt.items.length) return; var n=tt.items.length, cor=0, att=0;
      tt.items.forEach(function(it){ if(it.status!=='unanswered'||it.choice!==undefined) att++; });
      var rec=records.filter(function(r){ return r.mode==='quiz'&&r.tab===td.id; })[0];
      if(rec){ cor=rec.correct; att=Math.max(att,rec.total); }
      h+='<tr><td>'+td.label+'</td><td>'+n+'</td><td>'+(rec?'Finished':att+' / '+n)+'</td><td class="v4g">'+(rec?cor:'—')+'</td><td class="v4r">'+(rec?(rec.total-cor):'—')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><div class="rec-card"><h3>Finished sheets (latest first)</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sheets finished yet. Each time you finish a sheet, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table v4rec"><thead><tr><th>When</th><th>Mode</th><th>Sheet</th><th>Score</th><th>1st ✓</th><th>2nd ✓</th><th>Wrong</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+'</td><td>'+(r.c1!=null?r.c1:'—')+'</td><td>'+(r.c2!=null?r.c2:'—')+'</td><td>'+(r.w!=null?r.w:(r.mode==='quiz'?r.total-r.correct:'—'))+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){ if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker(); });
  window.scrollTo({top:0});
};
var _v4add = addRecord;
addRecord = function(mode, tabId, correct, revealed, skipped, total){
  _v4add(mode, tabId, correct, revealed, skipped, total);
  try{ if(mode==='learning'&&records[0]){ var c=v4Counts(state.tabs[tabId].items); records[0].c1=c.c1; records[0].c2=c.c2; records[0].w=c.w; saveState(); } }catch(e){}
};

/* ================= v4: celebration ================= */
function v4Cracker(){
  var ctx=ensureAudio(); if(!ctx) return; try{ if(ctx.state==='suspended') ctx.resume(); }catch(e){}
  var now=ctx.currentTime;
  function pop(t, vol, dur, hp){
    var len=Math.floor(ctx.sampleRate*dur), buf=ctx.createBuffer(1,len,ctx.sampleRate), d=buf.getChannelData(0);
    for(var i=0;i<len;i++){ d[i]=(Math.random()*2-1)*Math.pow(1-i/len,3); }
    var src=ctx.createBufferSource(); src.buffer=buf;
    var f=ctx.createBiquadFilter(); f.type='highpass'; f.frequency.value=hp;
    var g=ctx.createGain(); g.gain.setValueAtTime(vol,t); g.gain.exponentialRampToValueAtTime(0.001,t+dur);
    src.connect(f); f.connect(g); g.connect(ctx.destination); src.start(t); src.stop(t+dur+0.02);
  }
  pop(now,0.9,0.35,300);                                   // big bang
  for(var k=0;k<14;k++){ pop(now+0.35+Math.random()*1.3, 0.25+Math.random()*0.35, 0.05+Math.random()*0.08, 1500+Math.random()*2500); } // crackles
  [523.25,659.25,783.99,1046.5].forEach(function(fq,i){ var o=ctx.createOscillator(), g=ctx.createGain(); o.type='triangle'; o.frequency.value=fq;
    var t=now+0.15+i*0.12; g.gain.setValueAtTime(0.0001,t); g.gain.exponentialRampToValueAtTime(0.18,t+0.03); g.gain.exponentialRampToValueAtTime(0.001,t+0.5);
    o.connect(g); g.connect(ctx.destination); o.start(t); o.stop(t+0.55); });
}
function v4Confetti(){
  var cv=document.createElement('canvas'); cv.className='v4conf'; document.body.appendChild(cv);
  var W=cv.width=window.innerWidth*(window.devicePixelRatio||1), H=cv.height=window.innerHeight*(window.devicePixelRatio||1), s=(window.devicePixelRatio||1);
  var ctx=cv.getContext('2d'), cols=['#e8b13a','#d9534f','#2e86de','#27ae60','#9b59b6','#f39c12','#1abc9c','#ff6b9a'], P=[];
  function burst(x,y,n){ for(var i=0;i<n;i++){ var a=Math.random()*Math.PI*2, v=(4+Math.random()*9)*s;
    P.push({x:x,y:y,vx:Math.cos(a)*v,vy:Math.sin(a)*v-6*s,w:(6+Math.random()*7)*s,h:(4+Math.random()*5)*s,r:Math.random()*6,vr:(Math.random()-.5)*.4,c:cols[i%cols.length],life:0,flyer:Math.random()<.25}); } }
  burst(W*0.2,H*0.35,90); burst(W*0.8,H*0.35,90); setTimeout(function(){ burst(W*0.5,H*0.25,120); },380); setTimeout(function(){ burst(W*0.35,H*0.3,70); burst(W*0.65,H*0.3,70); },800);
  var t0=performance.now();
  (function frame(t){
    ctx.clearRect(0,0,W,H);
    P.forEach(function(p){ p.vy+=0.22*s; p.vx*=0.985; p.vy*=0.985; p.x+=p.vx; p.y+=p.vy; p.r+=p.vr; p.life++;
      ctx.save(); ctx.translate(p.x,p.y); ctx.rotate(p.r); ctx.fillStyle=p.c;
      if(p.flyer){ ctx.fillRect(-p.w*1.4,-1.5*s,p.w*2.8,3*s); } else { ctx.fillRect(-p.w/2,-p.h/2,p.w,p.h*Math.abs(Math.cos(p.life/6))); }
      ctx.restore(); });
    if(t-t0<4200) requestAnimationFrame(frame); else cv.remove();
  })(t0);
}
function v4NextTab(){
  var i=TAB_DEFS.findIndex(function(t){return t.id===activeTab;});
  for(var j=i+1;j<TAB_DEFS.length;j++){ var id=TAB_DEFS[j].id; if(id!=='theory' && SLIDES[id] && SLIDES[id].length) return TAB_DEFS[j]; }
  return null;
}
function v4Celebrate(){
  var done=document.querySelector('#wrap .done-card'); if(!done || done.dataset.v4) return; done.dataset.v4='1';
  var ts=state.tabs[activeTab], c=v4Counts(ts.items), n=ts.items.length;
  var first=(student&&student.name)?String(student.name).split(' ')[0]:'';
  var pct=MODE==='quiz'?null:Math.round((c.c1+c.c2)/Math.max(n,1)*100);
  var msg = pct===null ? 'You finished this sheet!' : (pct>=90?'Outstanding work!':pct>=75?'Excellent effort!':pct>=50?'Well done — keep going!':'Great persistence — every try makes you stronger!');
  var banner=document.createElement('div'); banner.className='v4ban';
  banner.innerHTML='<div class="v4trophy">🏆</div><div class="v4h">Congratulations'+(first?', '+esc(first):'')+'!</div><div class="v4m">'+msg+'</div>'+
    (MODE==='quiz'?'':'<div class="v4pills"><span class="v4p g">✅ '+c.c1+' first attempt</span><span class="v4p o">🔁 '+c.c2+' second attempt</span><span class="v4p r">❌ '+c.w+' finally wrong</span>'+(c.sk?'<span class="v4p s">⏭ '+c.sk+' skipped</span>':'')+'</div>');
  done.insertBefore(banner, done.firstChild);
  var nx=v4NextTab(), wrapB=document.createElement('div'); wrapB.className='v4next';
  if(nx){ wrapB.innerHTML='<button class="btn btn-primary v4go" id="v4Next">Next sheet: '+nx.label+' →</button>'; }
  else if(SLIDES.report!==undefined || TAB_DEFS.some(function(t){return t.id==='report';})){ wrapB.innerHTML='<button class="btn btn-primary v4go" id="v4Next">📊 View my report →</button>'; }
  else { wrapB.innerHTML='<button class="btn btn-primary v4go" id="v4Next">⌂ Back to the home page</button>'; }
  banner.appendChild(wrapB);
  document.getElementById('v4Next').addEventListener('click',function(){
    var t=nx?nx.id:(TAB_DEFS.some(function(x){return x.id==='report';})?'report':(TAB_DEFS[0]&&TAB_DEFS[0].id));
    activeTab=t; showChrome(true); buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  setTimeout(function(){ var r=banner.getBoundingClientRect(); window.scrollBy({top:r.top-110,behavior:'smooth'}); },60);
  v4Confetti(); v4Cracker();
}
var _v4rf = renderFinished;
renderFinished = function(){ _v4rf.apply(this,arguments); try{ v4Celebrate(); }catch(e){ console.log('v4',e); } };


/* ================= calculus answer mode ================= */
function calcCompile(src){
  var s=String(src).replace(/\s+/g,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/π/g,'#').replace(/eˣ/g,'e^x');
  if(s.indexOf('=')>=0) s=s.slice(s.lastIndexOf('=')+1);
  var FN=['sqrt','abs','ln','log','exp','sin','cos','tan','sec','csc','cot','pi'];
  var i=0,toks=[];
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length&&/[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(ch==='√'){ toks.push({k:'f',v:'sqrt'}); i++; continue; }
    if(/[a-zA-Z#]/.test(ch)){
      var hit=null; for(var q=0;q<FN.length;q++){ if(s.substr(i,FN[q].length).toLowerCase()===FN[q]){ hit=FN[q]; break; } }
      if(hit==='pi'){ toks.push({k:'v',v:'#'}); i+=2; continue; }
      if(hit){ toks.push({k:'f',v:hit}); i+=hit.length; continue; }
      toks.push({k:'v',v:ch}); i++; continue; }
    if('+-*/^()|'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  // absolute value bars -> abs( )
  var t2=[],open=false; for(var a=0;a<toks.length;a++){ var tk=toks[a]; if(tk.k==='|'){ if(!open){ t2.push({k:'f',v:'abs'}); t2.push({k:'('}); open=true; } else { t2.push({k:')'}); open=false; } } else t2.push(tk); }
  toks=t2;
  var out=[];
  for(var t=0;t<toks.length;t++){ var A=toks[t], B=out[out.length-1];
    if(B&&(B.k==='n'||B.k==='v'||B.k===')')&&(A.k==='n'||A.k==='v'||A.k==='('||A.k==='f')) out.push({k:'&'});
    out.push(A); }
  var p=0; function pk(){ return out[p]; }
  var F={sqrt:Math.sqrt,ln:Math.log,log:function(x){return Math.log(x)/Math.LN10;},exp:Math.exp,sin:Math.sin,cos:Math.cos,tan:Math.tan,
    sec:function(x){return 1/Math.cos(x);},csc:function(x){return 1/Math.sin(x);},cot:function(x){return 1/Math.tan(x);},abs:Math.abs};
  function E(){ var n=T(); while(pk()&&(pk().k==='+'||pk().k==='-')){ var o=out[p++].k,r=T(); n=(function(l,r,o){return function(e){return o==='+'?l(e)+r(e):l(e)-r(e);};})(n,r,o);} return n; }
  function T(){ var n=I(); while(pk()&&(pk().k==='*'||pk().k==='/')){ var o=out[p++].k,r=I(); n=(function(l,r,o){return function(e){return o==='*'?l(e)*r(e):l(e)/r(e);};})(n,r,o);} return n; }
  function I(){ var n=U(); while(pk()&&pk().k==='&'){ p++; var r=P(); n=(function(l,r){return function(e){return l(e)*r(e);};})(n,r);} return n; }
  function U(){ if(pk()&&pk().k==='-'){ p++; var u=U(); return function(e){return -u(e);}; } if(pk()&&pk().k==='+'){ p++; return U(); } return P(); }
  function P(){ var b=Aa(); if(pk()&&pk().k==='^'){ p++; var x=U(); return function(e){return Math.pow(b(e),x(e));}; } return b; }
  function Aa(){ var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){return t.v;};
    if(t.k==='v'){ if(t.v==='#') return function(){return Math.PI;}; if(t.v==='e') return function(){return Math.E;}; return function(e){return e[t.v];}; }
    if(t.k==='('){ var n=E(); if(!pk()||pk().k!==')') throw 0; p++; return n; }
    if(t.k==='f'){ var fn=F[t.v]; var ex=null;
      if(pk()&&pk().k==='^'){ p++; ex=Aa(); if(pk()&&pk().k==='&') p++; }            // sin^2(x)
      var arg; if(pk()&&pk().k==='('){ p++; arg=E(); if(!pk()||pk().k!==')') throw 0; p++; } else arg=P();
      return ex? function(e){ return Math.pow(fn(arg(e)),ex(e)); } : function(e){ return fn(arg(e)); }; }
    throw 0; }
  try{ var f=E(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function calcEqual(input,answer){
  var f=calcCompile(input), g=calcCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<14;trial++){
    var env={}; 'abcdfghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=0.35+Math.random()*2.3; });
    var x=f(env), y=g(env); if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-6*Math.max(1,Math.abs(x),Math.abs(y))) return false; hits++;
  }
  return hits>=4;
}
(function(){
  var _am=answerMatches;
  answerMatches=function(input,answer,accept,expr){
    if(expr==='calc'){ if(input===undefined||input===null||String(input).trim()==='') return false;
      if(calcEqual(input,answer)) return true; return (accept||[]).some(function(a){ return calcEqual(input,a); }); }
    return _am.apply(this,arguments); };
  var _kl=kbLayoutFor;
  kbLayoutFor=function(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; if(stp.expr==='calc') return 'calc'; }catch(e){} return _kl(inp); };
  var _kp=kbPress;
  kbPress=function(k){ var m={'eˣ':'e^(','√':'√(','ln':'ln(','sin':'sin(','cos':'cos(','tan':'tan('}; if(KB.page==='calc'&&m[k]){ kbInsert(m[k]); return; } return _kp(k); };
})();

renderLogin();
})();
</script>
</body>
</html>
