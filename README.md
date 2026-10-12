<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Giữ gìn và phát huy chữ Quốc ngữ — Công tác sinh viên</title>
<meta name="theme-color" content="#43060D">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700;800&family=Fraunces:ital,wght@0,600;0,800;0,900;1,600&family=Playfair+Display:ital,wght@0,700;0,900;1,700&display=swap" rel="stylesheet">
<style>
/* ===== Chữ Quốc ngữ · bảng màu: đỏ son – vàng hoàng cung – kem giấy dó – xanh núi ===== */
:root{
 --do:#C1121F;--do2:#E23A2B;--dod:#7E0C16;--dodd:#43060D;
 --vang:#F5B700;--vang2:#FFD95A;--vangd:#8A6100;
 --kem:#FBF0D2;--kem2:#F3DFAE;
 --xanh:#2E6B4E;--xanhd:#1B4533;--xanhl:#79B58A;
 --muc:#33121A;--muc2:#6A3A3F;
 --fd:"Fraunces","Playfair Display",Georgia,"Times New Roman",serif;
 --fb:"Be Vietnam Pro",system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;
 --mx:0;--my:0;--ease:cubic-bezier(.2,.8,.2,1);--spring:cubic-bezier(.34,1.56,.64,1)
}
*{box-sizing:border-box;margin:0;padding:0}
html,body{height:100%;overflow:hidden;background:var(--dodd);font-family:var(--fb);color:var(--muc);-webkit-font-smoothing:antialiased;-webkit-tap-highlight-color:transparent}
button{font:inherit;color:inherit;background:none;border:0;cursor:pointer;text-align:inherit}
input,textarea{font:inherit;color:inherit}
ul,ol{list-style:none}
b{font-weight:700}
kbd{font:600 .72rem var(--fb);padding:2px 7px;border-radius:6px;background:rgba(255,255,255,.14);border:1px solid rgba(255,217,90,.4);margin:0 4px 0 12px}
:focus-visible{outline:3px solid var(--vang);outline-offset:3px;border-radius:8px}
h1,h2,h3,h4{font-family:var(--fd);line-height:1.1;letter-spacing:-.01em}

/* ===== canvas & khung ===== */
#rain{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:5}
#fx{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:95}
#deck{position:fixed;inset:0}
.slide{position:absolute;inset:0;display:flex;overflow-x:hidden;overflow-y:auto;visibility:hidden;pointer-events:none;
 padding:calc(60px + env(safe-area-inset-top,0px)) clamp(16px,4.5vw,72px) calc(92px + env(safe-area-inset-bottom,0px));scrollbar-width:thin;scrollbar-color:var(--do) transparent}
.slide.prev{visibility:visible;z-index:2}
.slide.active{visibility:visible;pointer-events:auto;z-index:3;animation:bloom 1.05s cubic-bezier(.65,0,.25,1) backwards}
@keyframes bloom{from{clip-path:circle(0% at var(--cx,50%) var(--cy,50%))}to{clip-path:circle(150% at var(--cx,50%) var(--cy,50%))}}
.wrap{position:relative;z-index:2;margin:auto;width:100%;max-width:1240px}

/* nền giấy dó / đỏ nhung / xanh núi */
.paper{color:var(--muc);background:
 radial-gradient(1100px 560px at 92% -8%,rgba(245,183,0,.26),transparent 62%),
 radial-gradient(900px 520px at -8% 108%,rgba(46,107,78,.20),transparent 60%),
 url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='180' height='180'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='2' stitchTiles='stitch'/%3E%3CfeColorMatrix values='0 0 0 0 .45 0 0 0 0 .3 0 0 0 0 .12 0 0 0 .11 0'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E"),
 var(--kem)}
.paper::before{content:"";position:absolute;inset:12px;border:1.5px solid rgba(193,18,31,.22);border-radius:10px;pointer-events:none;z-index:1}
.red{color:var(--kem);background:
 radial-gradient(900px 700px at 78% 45%,rgba(245,183,0,.24),transparent 60%),
 radial-gradient(1200px 800px at 10% 100%,rgba(0,0,0,.38),transparent 60%),
 linear-gradient(160deg,#A30F1B,#5E0A12 70%,#43060D)}
.green{color:var(--kem);background:
 radial-gradient(900px 600px at 85% 0%,rgba(245,183,0,.18),transparent 60%),
 linear-gradient(165deg,#2B6A4D,#1B4533 65%,#12301F)}

/* núi đồi nhiều tầng (parallax theo chuột) */
.scn{position:absolute;left:-6%;right:-6%;bottom:0;height:min(30vh,300px);z-index:1;pointer-events:none}
.scn svg{position:absolute;inset:0;width:100%;height:100%;will-change:transform}
.scn .l1{transform:translate3d(calc(var(--mx)*-12px),0,0)}
.scn .l2{transform:translate3d(calc(var(--mx)*-26px),0,0)}
.scn .l3{transform:translate3d(calc(var(--mx)*-44px),0,0)}
.paper .l1{fill:rgba(46,107,78,.10)}.paper .l2{fill:rgba(46,107,78,.16)}.paper .l3{fill:rgba(31,80,57,.22)}
.red .l1{fill:rgba(46,107,78,.38)}.red .l2{fill:#2A6247}.red .l3{fill:#173C2B}
.green .l1{fill:rgba(255,255,255,.07)}.green .l2{fill:rgba(0,0,0,.18)}.green .l3{fill:rgba(0,0,0,.32)}
.scn::before{content:"";position:absolute;left:0;right:0;bottom:12%;height:45%;z-index:2;background:radial-gradient(ellipse at 30% 60%,rgba(255,255,255,.26),transparent 62%);animation:mist 18s ease-in-out infinite alternate}
@keyframes mist{from{transform:translateX(-8%)}to{transform:translateX(22%)}}
.hero-s .scn,.dv .scn{height:min(36vh,360px)}

/* đèn lồng đung đưa */
.lan{position:absolute;top:0;z-index:2;width:46px;transform-origin:50% 0;animation:swing 4.2s ease-in-out infinite;pointer-events:none}
.lan::before{content:"";display:block;width:2px;height:var(--h,60px);margin:0 auto;background:linear-gradient(var(--vang),rgba(245,183,0,.3))}
.lan i{display:block;position:relative;width:46px;height:58px;border-radius:50% 50% 46% 46%/42% 42% 58% 58%;background:radial-gradient(circle at 35% 30%,#FF7A63,#C1121F 60%,#7E0C16);box-shadow:0 0 30px rgba(255,120,60,.55),inset 0 -6px 12px rgba(0,0,0,.25)}
.lan i::before,.lan i::after{content:"";position:absolute;left:50%;transform:translateX(-50%);width:22px;height:6px;background:var(--vang);border-radius:3px}
.lan i::before{top:-3px}.lan i::after{bottom:-3px}
.lan b{display:block;width:2px;height:24px;margin:3px auto 0;background:var(--vang);position:relative}
.lan b::after{content:"";position:absolute;left:-4px;bottom:-4px;width:10px;height:10px;border-radius:50%;background:var(--vang2)}
@keyframes swing{0%,100%{transform:rotate(-7deg)}50%{transform:rotate(7deg)}}

/* ===== hiệu ứng vào slide ===== */
.slide.active .rv{animation:rise .85s var(--ease) backwards;animation-delay:calc(var(--i,0)*70ms + 380ms)}
@keyframes rise{from{opacity:0;transform:translateY(34px) scale(.98)}to{opacity:1;transform:none}}
@keyframes fade{from{opacity:0}to{opacity:1}}
@keyframes pop{0%{opacity:0;transform:scale(.3) translateY(14px)}100%{opacity:1;transform:none}}
@keyframes blink{50%{opacity:0}}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}
@keyframes shine{to{background-position:-250% 0}}
@keyframes pulse{0%,100%{transform:scale(1);opacity:.9}50%{transform:scale(1.35);opacity:.5}}
@keyframes shake{0%,100%{transform:none}20%{transform:translateX(-9px)}40%{transform:translateX(8px)}60%{transform:translateX(-6px)}80%{transform:translateX(4px)}}
.shake{animation:shake .5s}

/* ===== HUD ===== */
#prog{position:fixed;left:0;top:0;height:5px;width:100%;z-index:50;background:rgba(0,0,0,.10)}
#prog i{display:block;height:100%;width:0;background:linear-gradient(90deg,var(--do),var(--vang),var(--xanhl));transition:width .8s var(--ease);box-shadow:0 0 12px var(--vang)}
#hud{position:fixed;top:14px;left:0;right:0;z-index:50;display:flex;align-items:center;gap:8px;padding:0 clamp(12px,3vw,40px);pointer-events:none;color:var(--hud,var(--muc))}
#hud>*{pointer-events:auto}
.hb{position:relative;overflow:hidden;white-space:nowrap;padding:7px 14px;border-radius:99px;background:var(--hbg,rgba(255,255,255,.6));backdrop-filter:blur(8px);-webkit-backdrop-filter:blur(8px);border:1px solid var(--hbd,rgba(193,18,31,.28));font-size:.78rem;font-weight:600;transition:transform .2s,background .2s}
.hb:hover{transform:translateY(-2px)}
.hb.on{background:var(--do);color:#fff}
#chap{font-family:var(--fd);font-weight:700;font-size:.98rem;margin-left:6px;opacity:.92}
.sp0{flex:1}
body[data-theme=dark]{--hud:var(--kem);--hbg:rgba(0,0,0,.30);--hbd:rgba(255,217,90,.38)}
body[data-theme=dark] .hb.on{background:var(--vang);color:var(--dodd)}
#nav{position:fixed;right:clamp(12px,3vw,40px);bottom:calc(16px + env(safe-area-inset-bottom,0px));z-index:50;display:flex;align-items:center;gap:10px;color:var(--hud,var(--muc))}
.nb{position:relative;overflow:hidden;width:52px;height:52px;border-radius:50%;display:grid;place-items:center;background:linear-gradient(135deg,var(--do),var(--do2));color:#FFF3D1;box-shadow:0 8px 20px rgba(126,12,22,.4);transition:transform .25s var(--spring)}
.nb:hover{transform:scale(1.12)}
.nb svg{width:22px;height:22px;stroke:currentColor;fill:none;stroke-width:2.6;stroke-linecap:round;stroke-linejoin:round}
body[data-theme=dark] .nb{background:linear-gradient(135deg,var(--vang),var(--vang2));color:var(--dodd)}
#ctr{font-family:var(--fd);font-weight:700;min-width:74px;text-align:center}
.rip{position:absolute;border-radius:50%;background:rgba(255,255,255,.5);transform:scale(0);animation:ripple .65s ease-out forwards;pointer-events:none}
@keyframes ripple{to{transform:scale(1);opacity:0}}

/* mục lục */
#menu{position:fixed;inset:0;z-index:80;background:rgba(43,6,13,.95);backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);display:none;overflow:auto;padding:70px clamp(16px,5vw,80px) 50px;color:var(--kem)}
#menu.on{display:block;animation:fade .3s}
#menu h3{font-size:clamp(1.6rem,3vw,2.4rem);color:var(--vang2);margin-bottom:6px}
.mg h4{font-size:1.15rem;color:var(--vang2);margin:22px 0 10px}
.mg div{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:10px}
.mi{padding:12px 14px;border-radius:14px;background:rgba(255,255,255,.07);border:1px solid rgba(255,217,90,.2);font-size:.9rem;transition:transform .25s var(--spring),background .2s;animation:pop .45s var(--spring) backwards;animation-delay:calc(var(--k)*22ms)}
.mi:hover,.mi.cur{background:rgba(245,183,0,.26);transform:translateY(-3px) scale(1.02)}
.mi small{display:block;color:var(--vang2);font-weight:700;font-size:.74rem}
#mclose{position:fixed;top:14px;right:16px;z-index:81;display:none}
#menu.on~#mclose{display:block}

/* toast & con trỏ */
#toast{position:fixed;left:50%;bottom:96px;transform:translate(-50%,30px);opacity:0;z-index:90;max-width:90vw;text-align:center;padding:12px 22px;border-radius:99px;background:linear-gradient(135deg,var(--vang),var(--vang2));color:var(--dodd);font-weight:700;box-shadow:0 12px 30px rgba(0,0,0,.35);transition:.5s var(--spring);pointer-events:none}
#toast.on{opacity:1;transform:translate(-50%,0)}
#cur{position:fixed;left:0;top:0;width:34px;height:34px;margin:-17px 0 0 -17px;border:2px solid rgba(245,183,0,.95);border-radius:50%;pointer-events:none;z-index:9999;box-shadow:0 0 18px rgba(245,183,0,.55);opacity:0;transition:width .2s,height .2s,margin .2s,background .2s,border-color .2s,opacity .3s}
#cur.vis{opacity:1}
#cur.h{width:58px;height:58px;margin:-29px 0 0 -29px;background:rgba(245,183,0,.2)}
body[data-theme=paper] #cur{border-color:rgba(193,18,31,.85);box-shadow:0 0 16px rgba(193,18,31,.35)}
body[data-theme=paper] #cur.h{background:rgba(193,18,31,.12)}
body.laser,body.laser *{cursor:none!important}
body.laser #cur{width:16px;height:16px;margin:-8px 0 0 -8px;border:0;background:#ff2a2a!important;box-shadow:0 0 0 7px rgba(255,42,42,.25),0 0 32px 12px rgba(255,42,42,.65)}

/* ===== chữ & tiện ích ===== */
h2.t{font-size:clamp(1.9rem,4.1vw,3.3rem);font-weight:800;color:var(--do);margin-bottom:.4em}
.red h2.t,.green h2.t{color:var(--vang2)}
.lead{font-size:clamp(1rem,1.45vw,1.18rem);line-height:1.62;max-width:64ch;margin-bottom:.7em}
.mu{color:var(--muc2);line-height:1.55}
.red .mu,.green .mu{color:rgba(251,240,210,.82)}
.small{font-size:.85rem}.foot{font-size:.78rem;opacity:.72;margin-top:.8em}
.gold-t{background:linear-gradient(100deg,var(--vang) 20%,#FFF3B0 40%,var(--vang) 60%,#FFC93C 80%);background-size:250% 100%;-webkit-background-clip:text;background-clip:text;color:transparent;animation:shine 5s linear infinite}
.slide.active .hl{background:linear-gradient(transparent 58%,rgba(245,183,0,.6) 58%) no-repeat;background-size:0 100%;animation:hlin 1.1s 1.1s var(--ease) forwards}
.slide.prev .hl{background:linear-gradient(transparent 58%,rgba(245,183,0,.6) 58%) no-repeat;background-size:100% 100%}
@keyframes hlin{to{background-size:100% 100%}}
.g2{display:grid;grid-template-columns:minmax(0,1.05fr) minmax(0,1fr);gap:clamp(20px,3.5vw,56px);align-items:center}
.g3{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:clamp(12px,2vw,26px)}
.row{display:flex;flex-wrap:wrap;gap:12px;align-items:center;margin-top:1.1em}
.tags{display:flex;flex-wrap:wrap;gap:8px;margin:1em 0}
.chip{display:inline-flex;align-items:center;gap:6px;padding:6px 14px;border-radius:99px;font-weight:600;font-size:.84rem;background:rgba(193,18,31,.10);color:var(--do);border:1px solid rgba(193,18,31,.28);transition:transform .25s var(--spring)}
.chip:hover{transform:translateY(-3px) rotate(-2deg)}
.chip.g{background:rgba(46,107,78,.13);color:var(--xanh);border-color:rgba(46,107,78,.32)}
.chip.y{background:rgba(245,183,0,.22);color:#6F4E00;border-color:rgba(245,183,0,.55)}
.red .chip,.green .chip{background:rgba(255,255,255,.1);color:var(--kem);border-color:rgba(255,217,90,.4)}
.red .chip.y,.green .chip.y{background:rgba(245,183,0,.25);color:var(--vang2)}
.btn{position:relative;overflow:hidden;display:inline-flex;align-items:center;justify-content:center;gap:8px;padding:12px 24px;border-radius:99px;font-weight:700;font-size:.95rem;transition:transform .25s var(--spring),box-shadow .25s,filter .2s}
.btn:hover{transform:translateY(-3px);filter:brightness(1.06)}
.btn:active{transform:scale(.96)}
.btn.pri{background:linear-gradient(135deg,var(--do),var(--do2));color:#FFF3D1;box-shadow:0 10px 22px rgba(126,12,22,.35)}
.btn.gold{background:linear-gradient(135deg,var(--vang),var(--vang2));color:var(--dodd);box-shadow:0 10px 24px rgba(245,183,0,.38)}
.btn.ghost{border:1.8px solid currentColor;background:transparent}
.btn.mini{padding:6px 14px;font-size:.78rem}
.mag{will-change:transform}
.card{background:rgba(255,255,255,.74);border:1px solid rgba(193,18,31,.15);border-radius:22px;padding:clamp(14px,1.8vw,24px);box-shadow:0 12px 30px rgba(126,12,22,.10)}
.red .card,.green .card{background:rgba(255,255,255,.09);border-color:rgba(255,217,90,.28);box-shadow:0 12px 30px rgba(0,0,0,.25)}
.card h3{font-size:1.25rem;margin-bottom:.5em;color:var(--do)}
.red .card h3,.green .card h3{color:var(--vang2)}

/* nghiêng 3D + ánh sáng theo chuột */
.tilt{position:relative;transform:perspective(900px) translateY(var(--ty,0)) rotateX(var(--rx,0deg)) rotateY(var(--ry,0deg));transition:transform .25s ease,box-shadow .25s}
.tilt:hover{--ty:-6px}
.tilt::after{content:"";position:absolute;inset:0;border-radius:inherit;background:radial-gradient(260px circle at var(--gx,50%) var(--gy,50%),rgba(255,255,255,.4),transparent 55%);opacity:0;transition:opacity .25s;pointer-events:none}
.tilt:hover::after{opacity:1}

/* tab có vệt trượt */
.tabs{position:relative;display:inline-flex;flex-wrap:wrap;gap:4px;padding:5px;margin:.4em 0 1em;max-width:100%;border-radius:26px;background:rgba(193,18,31,.08);border:1px solid rgba(193,18,31,.22)}
.tabs button{position:relative;z-index:1;padding:9px 18px;border-radius:99px;font-weight:700;font-size:.9rem;color:var(--do);transition:color .3s}
.tabs button.on{color:#FFF3D1}
.tabs .ink{position:absolute;z-index:0;left:0;top:5px;width:0;height:0;border-radius:99px;background:linear-gradient(135deg,var(--do),var(--do2));box-shadow:0 6px 14px rgba(126,12,22,.35);transition:left .45s var(--spring),top .3s,width .45s var(--spring),height .3s}
.red .tabs,.green .tabs{background:rgba(0,0,0,.22);border-color:rgba(255,217,90,.35)}
.red .tabs button,.green .tabs button{color:var(--kem)}
.red .tabs button.on,.green .tabs button.on{color:var(--dodd)}
.red .tabs .ink,.green .tabs .ink{background:linear-gradient(135deg,var(--vang),var(--vang2));box-shadow:0 6px 14px rgba(0,0,0,.3)}
.tp{display:none}
.tp.on{display:block;animation:tabin .6s var(--ease)}
@keyframes tabin{from{opacity:0;transform:translateX(30px)}to{opacity:1;transform:none}}
.chk li{position:relative;padding:8px 0 8px 34px;line-height:1.5}
.chk li::before{content:"✓";position:absolute;left:0;top:8px;width:24px;height:24px;border-radius:50%;display:grid;place-items:center;font-size:.8rem;font-weight:800;background:var(--xanh);color:#fff;transform:scale(0)}
.tp.on .chk li::before,.slide.active .chk li::before{animation:pop .5s var(--spring) forwards;animation-delay:calc(var(--k,0)*140ms + 300ms)}

/* ===== hộp thoại tin nhắn ===== */
.chat{display:flex;flex-direction:column;gap:11px}
.msg{display:flex;gap:8px;align-items:flex-end;max-width:94%}
.msg.me{align-self:flex-end;flex-direction:row-reverse}
.msg.sys{align-self:center;max-width:100%}
.av{flex:none;width:32px;height:32px;border-radius:50%;display:grid;place-items:center;font:700 .8rem var(--fb);color:#fff;background:var(--xanh);box-shadow:0 3px 8px rgba(0,0,0,.2)}
.msg.me .av{background:var(--do)}
.bub{position:relative;padding:10px 15px;border-radius:18px 18px 18px 4px;background:#fff;color:var(--muc);box-shadow:0 6px 18px rgba(75,7,14,.14);font-size:.95rem;line-height:1.48;transform-origin:0 100%;animation:pop .5s var(--spring) both}
.msg.me .bub{border-radius:18px 18px 4px 18px;background:linear-gradient(135deg,var(--do),#DC3A2A);color:#FFF3D1;transform-origin:100% 100%}
.msg.sys .bub{border-radius:16px;background:linear-gradient(135deg,var(--vang2),#FFE9A0);color:var(--dodd);transform-origin:50% 100%;text-align:center}
.nm{display:block;font-weight:700;font-size:.72rem;color:var(--xanh);margin-bottom:2px}
.typing .bub{padding:12px 16px;animation:pop .3s var(--spring) both}
.dots i{display:inline-block;width:7px;height:7px;margin:0 2px;border-radius:50%;background:#B79B8D;animation:bounce 1s infinite}
.msg.me .dots i{background:#FFD0C0}
.dots i:nth-child(2){animation-delay:.15s}.dots i:nth-child(3){animation-delay:.3s}
@keyframes bounce{0%,60%,100%{transform:none}30%{transform:translateY(-6px)}}
.w{display:inline-block;cursor:pointer;text-decoration:underline wavy var(--do2);text-underline-offset:4px;border-radius:5px;transition:background .2s}
.msg.me .w{text-decoration-color:var(--vang2)}
.w:hover{background:rgba(245,183,0,.38)}
.w.ok{text-decoration:none;background:rgba(121,181,138,.5);padding:0 4px;animation:okflip .5s var(--ease)}
.msg.me .w.ok{background:rgba(255,255,255,.28)}
@keyframes okflip{from{transform:rotateX(90deg);opacity:0}to{transform:none;opacity:1}}
.phone{width:min(350px,88vw);margin:0 auto;border-radius:38px;background:#1c0a0d;padding:10px;box-shadow:0 30px 60px rgba(67,6,13,.45),inset 0 0 0 2px rgba(245,183,0,.4);animation:float 6s ease-in-out infinite}
.screen{border-radius:30px;background:linear-gradient(180deg,#FFF8E4,#FBEBC0);height:min(540px,60vh);display:flex;flex-direction:column;overflow:hidden}
.ph-top{padding:12px 14px;background:linear-gradient(135deg,var(--do),var(--do2));color:#FFF3D1;display:flex;align-items:center;gap:10px}
.ph-top small{display:block;font-size:.7rem;opacity:.85}
.ph-top .av{background:var(--vang);color:var(--dodd)}
.ph-body{flex:1;padding:14px 12px;overflow-y:auto;scrollbar-width:none}
.ph-in{padding:10px 12px;display:flex;gap:8px;align-items:center;border-top:1px solid rgba(0,0,0,.08)}
.ph-in i{flex:1;background:#fff;border-radius:99px;padding:8px 14px;color:#9a8a80;font-style:normal;font-size:.85rem}
.ph-in span{width:32px;height:32px;border-radius:50%;display:grid;place-items:center;background:var(--do);color:#fff;font-size:.8rem}
.hint{margin-top:14px;font-size:.88rem;text-align:center;color:var(--muc2)}
.hint b{color:var(--do);font-size:1rem}
.red .hint,.green .hint{color:var(--kem)}
/* ===== BÌA, CHƯƠNG, CẢM ƠN ===== */
.hero{max-width:1240px}
.hero>*{max-width:min(720px,100%)}
.pre{font-family:var(--fd);font-style:italic;font-weight:600;font-size:clamp(1.05rem,2.1vw,1.7rem);color:var(--vang2);min-height:1.5em}
.caret{display:inline-block;width:2px;height:1.1em;margin-left:3px;background:var(--vang2);vertical-align:-.15em;animation:blink 1s steps(1) infinite}
.big{font-weight:900;font-size:clamp(3.6rem,11vw,9.4rem);line-height:.92;margin:.1em 0 .16em;letter-spacing:-.025em;color:var(--vang);text-shadow:0 6px 0 rgba(67,6,13,.5),0 0 50px rgba(245,183,0,.32)}
.big .ch{display:inline-block;transform-origin:50% 60%;white-space:pre}
.big .sw.fl{animation:flipc .85s var(--ease)}
@keyframes flipc{0%{transform:rotateX(0)}45%{transform:rotateX(90deg);color:#fff}100%{transform:rotateX(0)}}
.sub{font-size:clamp(1rem,1.5vw,1.2rem);line-height:1.5;opacity:.93}
.team{margin-top:1.4em}
#team{display:inline-block;padding:7px 16px;border-radius:99px;border:1.5px dashed rgba(255,217,90,.6);color:var(--vang2);font-weight:600;font-size:.9rem;outline:none;cursor:text;transition:background .2s,border-color .2s}
#team:hover,#team:focus{background:rgba(255,255,255,.1);border-style:solid}
.keys{margin-top:1.1em;font-size:.82rem;opacity:.85}
.thanks{font-size:clamp(2.2rem,6vw,5rem);font-weight:900;color:var(--vang);line-height:1.02;margin-bottom:.3em;text-shadow:0 5px 0 rgba(67,6,13,.45)}
.qa{margin-top:1.4em}

.drumbox{position:absolute;right:-9vw;top:50%;width:min(86vh,58vw);aspect-ratio:1;z-index:1;pointer-events:none;translate:calc(var(--mx)*-14px) calc(-50% + var(--my)*-10px)}
.drumbox.sm{width:min(70vh,50vw);right:-8vw;opacity:.5}
.drum{position:relative;width:100%;height:100%;filter:drop-shadow(0 0 24px rgba(245,183,0,.35))}
.slide.active .drum{animation:drumIn 2.4s var(--ease) backwards}
@keyframes drumIn{from{opacity:0;transform:scale(.55) rotate(-70deg)}to{opacity:1;transform:none}}
.drum svg{position:absolute;inset:0;width:100%;height:100%;overflow:visible}
.drum svg *{fill:none;stroke:var(--vang);stroke-width:1.6;stroke-linejoin:round;stroke-linecap:round}
.drum svg .f{fill:var(--vang);stroke:none;opacity:.88}
.drum .a1{animation:spin 120s linear infinite}.drum .a2{animation:spin 90s linear infinite reverse}.drum .a3{animation:spin 70s linear infinite}
.drum .a4{animation:spin 100s linear infinite reverse}.drum .a5{animation:spin 60s linear infinite}.drum .a6{animation:spin 140s linear infinite reverse}
@keyframes spin{to{transform:rotate(360deg)}}

.dv .wrap{max-width:1100px}
.dnum{font-family:var(--fd);font-weight:900;font-size:clamp(7rem,26vw,19rem);line-height:.8;color:transparent;-webkit-text-stroke:3px var(--vang);opacity:.92}
.dsm{font-family:var(--fd);font-style:italic;font-size:clamp(1.2rem,2.4vw,1.8rem);color:var(--vang2);margin-top:.2em}
.dt{font-size:clamp(1.9rem,4.6vw,3.8rem);font-weight:800;max-width:20ch;margin:.15em 0 .5em;color:var(--kem)}
.dli{display:flex;flex-wrap:wrap;gap:10px;max-width:900px}
.dli li{padding:8px 18px;border-radius:99px;border:1.5px solid rgba(255,217,90,.5);background:rgba(0,0,0,.22);font-weight:600;font-size:.95rem;transition:transform .3s var(--spring),background .3s}
.dli li:hover{transform:translateY(-4px) rotate(-2deg);background:rgba(245,183,0,.3)}

/* ===== MỤC LỤC ===== */
.ag{position:relative;display:grid;grid-template-columns:repeat(5,minmax(0,1fr));gap:14px;margin-top:2.4em}
.agpath{position:absolute;left:0;right:0;top:-40px;width:100%;height:80px;z-index:0;overflow:visible;pointer-events:none}
.agpath path{fill:none;stroke:var(--vang);stroke-width:3;stroke-linecap:round;stroke-dasharray:1 1;stroke-dashoffset:1}
.slide.active .agpath path{animation:draw 2.4s .6s var(--ease) forwards}
.slide.prev .agpath path{stroke-dashoffset:0}
@keyframes draw{to{stroke-dashoffset:0}}
.agc{position:relative;z-index:1;padding:22px 16px 18px;border-radius:20px;background:#fff;border:1px solid rgba(193,18,31,.16);box-shadow:0 14px 30px rgba(126,12,22,.12);text-align:left;overflow:hidden}
.agc::before{content:"";position:absolute;left:0;top:0;height:6px;width:100%;background:linear-gradient(90deg,var(--do),var(--vang),var(--xanh))}
.agc b{display:block;font-family:var(--fd);font-size:3.4rem;font-weight:900;color:var(--do);line-height:1}
.agc:nth-of-type(3) b{color:var(--xanh)}.agc:nth-of-type(5) b{color:var(--vangd)}
.agc h3{font-size:1.15rem;margin:.35em 0 .25em;color:var(--muc)}
.agc p{font-size:.86rem;line-height:1.45;color:var(--muc2)}
.agc ul{max-height:0;opacity:0;overflow:hidden;font-size:.82rem;color:var(--muc2);transition:max-height .5s var(--ease),opacity .4s,margin .4s}
.agc:hover ul,.agc:focus-visible ul{max-height:220px;opacity:1;margin-top:10px}
.agc li{padding:2px 0}.agc li::before{content:"✦ ";color:var(--vang)}
@media(hover:none){.agc ul{max-height:none;opacity:1;margin-top:10px}}

/* ===== MỞ ĐẦU ===== */
.note{margin-top:1em;padding:16px 20px;border-left:5px solid var(--do);border-radius:0 16px 16px 0;background:rgba(255,255,255,.72);font-size:1rem;line-height:1.6;box-shadow:0 8px 22px rgba(126,12,22,.08)}
.deep{margin-top:1em;padding:16px 20px;border-radius:18px;background:linear-gradient(135deg,rgba(245,183,0,.26),rgba(245,183,0,.1));border:1.5px dashed var(--vangd);font-weight:600;line-height:1.55}
.mini5{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:12px}
.mini5>div{padding:16px;border-radius:18px;background:#fff;box-shadow:0 10px 24px rgba(126,12,22,.1);font-size:.95rem;line-height:1.45;border-top:5px solid var(--do)}
.mini5>div:nth-child(even){border-top-color:var(--xanh)}
.mini5 b{display:block;font-family:var(--fd);font-size:2rem;color:var(--vang);margin-bottom:4px}
.mini4{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
.mini4 .card p{line-height:1.55;font-size:.96rem}
.tp.on .mini5>div,.tp.on .mini4>div,.tp.on .how4>div,.tp.on .fmts>div,.tp.on .conds>div{animation:pop .55s var(--spring) backwards;animation-delay:calc(var(--k,0)*90ms)}

/* ===== CHƯƠNG 1 ===== */
.stats{display:grid;grid-template-columns:1fr 1fr 1.6fr;gap:12px;margin:1em 0}
.stats>div{padding:14px;border-radius:18px;background:#fff;box-shadow:0 10px 24px rgba(126,12,22,.1);display:flex;flex-direction:column}
.stats b{font-family:var(--fd);font-size:2.5rem;font-weight:900;color:var(--do);line-height:1}
.stats>div:nth-child(3) b{font-size:1.5rem;padding-top:.5rem}
.stats span{font-size:.84rem;color:var(--muc2);margin-top:3px;line-height:1.35}
.nest{margin-top:1em}
.n1{padding:14px 16px 16px;border-radius:22px;border:2px dashed var(--xanh);background:rgba(46,107,78,.08);font-size:.88rem;color:var(--xanhd);font-weight:600}
.n2{margin-top:10px;padding:12px 16px;border-radius:16px;background:linear-gradient(135deg,var(--do),var(--do2));color:#FFF3D1;box-shadow:0 10px 22px rgba(126,12,22,.3);animation:glow 3s ease-in-out infinite}
.n2 b{display:block;font-family:var(--fd);font-size:1.15rem}
.n2 span{font-size:.84rem;opacity:.92;font-weight:500}
@keyframes glow{0%,100%{box-shadow:0 10px 22px rgba(126,12,22,.3)}50%{box-shadow:0 10px 38px rgba(226,58,43,.65)}}
.tone{text-align:center}
.tone h3{margin-bottom:.1em}
.glyph{font-family:var(--fd);font-weight:900;font-size:clamp(5rem,12vw,8.5rem);line-height:1.05;color:var(--muc);letter-spacing:-.02em}
.glyph .vv{color:var(--do);text-shadow:0 0 28px rgba(193,18,31,.35)}
.glyph.drop{animation:dropin .6s var(--spring)}
@keyframes dropin{0%{transform:translateY(-40px) scale(.7);opacity:0}100%{transform:none;opacity:1}}
.tchat{min-height:68px;align-items:flex-start;margin:.2em 0 .8em;text-align:left}
.tbtns{display:grid;grid-template-columns:repeat(6,1fr);gap:8px;margin-bottom:.8em}
.tb{padding:10px 2px;border-radius:14px;background:rgba(193,18,31,.07);border:1.5px solid rgba(193,18,31,.2);text-align:center;transition:transform .25s var(--spring),background .25s}
.tb b{display:block;font-family:var(--fd);font-size:1.5rem;color:var(--do)}
.tb small{font-size:.7rem;color:var(--muc2);font-weight:600}
.tb:hover{transform:translateY(-4px)}
.tb.on{background:linear-gradient(135deg,var(--do),var(--do2));border-color:transparent;transform:translateY(-4px) scale(1.06);box-shadow:0 10px 20px rgba(126,12,22,.35)}
.tb.on b,.tb.on small{color:#FFF3D1}

.tl{position:relative;height:150px;margin:1.6em 0 .6em}
.tl-line{position:absolute;left:6%;right:6%;top:62px;height:8px;border-radius:8px;background:rgba(193,18,31,.15)}
.tl-line i{display:block;height:100%;width:0;border-radius:8px;background:linear-gradient(90deg,var(--do),var(--vang));transition:width 1s var(--ease);box-shadow:0 0 14px rgba(245,183,0,.6)}
.tn{position:absolute;top:0;transform:translateX(-50%);width:clamp(70px,16%,170px);height:150px;text-align:center}
.tn i{position:absolute;left:50%;top:48px;width:26px;height:26px;margin-left:-13px;border-radius:50%;background:var(--kem);border:4px solid var(--do);transition:transform .35s var(--spring),background .3s;z-index:2}
.tn:hover i{transform:scale(1.35)}
.tn.on i{background:var(--vang);transform:scale(1.35)}
.tn b{position:absolute;left:0;right:0;top:88px;font-family:var(--fd);font-size:clamp(.8rem,1.3vw,1.08rem);color:var(--muc);line-height:1.2}
.tn.on b{color:var(--do)}
.tl-pin{position:absolute;left:6%;top:4px;margin-left:-26px;width:52px;height:52px;border-radius:50%;display:grid;place-items:center;background:radial-gradient(circle at 35% 30%,#E8333B,var(--dod));color:var(--vang2);font-family:var(--fd);font-weight:800;font-size:1.05rem;box-shadow:0 8px 20px rgba(126,12,22,.5),inset 0 0 0 3px rgba(255,217,90,.7);transition:left 1s var(--ease);z-index:3;animation:float 3s ease-in-out infinite;pointer-events:none}
.tl-card{max-width:900px;margin:0 auto;padding:20px 24px;border-radius:22px;background:#fff;box-shadow:0 14px 34px rgba(126,12,22,.15);border:1px solid rgba(193,18,31,.16);transform-origin:50% 0}
.tl-card.pop{animation:pop .55s var(--spring)}
.tl-card h3{font-size:1.4rem;margin:.5em 0 .35em;color:var(--muc)}
.tl-card p{line-height:1.62;font-size:1.02rem}

.defects{display:flex;flex-wrap:wrap;gap:8px;margin:.6em 0 1em}
.defects span{padding:6px 14px;border-radius:99px;background:rgba(193,18,31,.12);color:var(--do);font-weight:600;font-size:.84rem;border:1px solid rgba(193,18,31,.3);transition:all .5s}
.defects span.fixed{background:rgba(46,107,78,.15);color:var(--xanh);border-color:rgba(46,107,78,.4);text-decoration:line-through;text-decoration-color:var(--xanh)}
.mgrid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:12px}
.mcard{display:flex;align-items:center;gap:12px;padding:16px 18px;border-radius:20px;background:#fff;box-shadow:0 10px 24px rgba(126,12,22,.1);border:1.5px solid rgba(193,18,31,.15);text-align:left;transition:transform .3s var(--spring),border-color .3s}
.mcard:hover{transform:translateY(-4px)}
.mw{flex:1;min-width:0}
.mf{font-family:"Courier New",ui-monospace,monospace;font-weight:700;font-size:1.3rem;color:var(--do);min-height:1.5em;word-break:break-word}
.mcard.done{border-color:var(--xanh)}
.mcard.done .mf{color:var(--xanh);font-family:var(--fd);font-size:1.45rem}
.mcard small{display:block;font-size:.72rem;color:var(--muc2);font-weight:600;margin-top:2px}
.mcard .ar{font-size:1.4rem;color:var(--vangd)}
.mc{display:inline-block;white-space:pre}
.mc.fl{animation:mflip .45s ease-in-out}
@keyframes mflip{0%{transform:rotateX(0)}50%{transform:rotateX(90deg);color:var(--vang)}100%{transform:rotateX(0)}}

.acc{display:flex;gap:10px;height:clamp(300px,52vh,470px);margin-top:.4em}
.ap{position:relative;flex:1;min-width:0;overflow:hidden;border-radius:22px;padding:18px 16px;color:#FFF3D1;cursor:pointer;transition:flex .65s var(--ease),filter .3s;background:linear-gradient(160deg,var(--do),var(--dod))}
.ap:nth-child(2){background:linear-gradient(160deg,var(--xanh),var(--xanhd))}
.ap:nth-child(3){background:linear-gradient(160deg,#D99A00,#8A6100)}
.ap:nth-child(4){background:linear-gradient(160deg,#8E1B2A,#4B070E)}
.ap:nth-child(5){background:linear-gradient(160deg,#3B8A63,var(--xanhd))}
.ap.on{flex:5}
.ap .ico{display:block;font-size:2rem;margin-bottom:10px;transition:transform .5s var(--spring)}
.ap.on .ico{transform:scale(1.25) rotate(-6deg)}
.ap h3{font-size:1.1rem;color:var(--vang2);white-space:nowrap}
.ap:not(.on) h3{writing-mode:vertical-rl;transform:rotate(180deg);margin-top:6px}
.ap.on h3{font-size:1.5rem;white-space:normal}
.ap .ab{opacity:0;transform:translateY(16px);transition:opacity .4s,transform .5s var(--ease);margin-top:12px;font-size:.96rem;line-height:1.55;pointer-events:none}
.ap.on .ab{opacity:1;transform:none;transition-delay:.3s;pointer-events:auto}
.ap .ab p+p{margin-top:.7em}
.ap:hover:not(.on){filter:brightness(1.15)}

.split{display:flex;gap:12px;height:clamp(180px,30vh,260px);margin:.6em 0 1em}
.sp{flex:1;min-width:0;overflow:hidden;position:relative;border-radius:24px;padding:22px 24px;color:#FFF3D1;cursor:pointer;transition:flex .65s var(--ease)}
.sa{background:linear-gradient(150deg,var(--do),var(--dod))}
.sb{background:linear-gradient(150deg,#3B8A63,var(--xanhd))}
.sp.on{flex:2.4}
.sp h3{font-size:clamp(1.6rem,3vw,2.4rem);color:var(--vang2);margin-bottom:.3em}
.sp p{font-size:1rem;line-height:1.55;max-width:46ch;opacity:.95}
.sp::before{content:"";position:absolute;right:-30px;bottom:-40px;width:160px;height:160px;border-radius:50%;border:18px solid rgba(255,217,90,.18);transition:transform .8s var(--ease)}
.sp.on::before{transform:scale(1.7)}
.low{align-items:start}
.silk{position:relative;padding:24px 24px 20px 28px;border-radius:20px;background:linear-gradient(135deg,#FFF6D8,#F7E3A2);border:1px solid rgba(138,97,0,.3);box-shadow:0 12px 26px rgba(138,97,0,.18);font-family:var(--fd);font-style:italic;font-size:1.12rem;line-height:1.55}
.silk::before{content:"“";position:absolute;left:8px;top:-12px;font-size:4.5rem;color:var(--do);font-style:normal;line-height:1}
.silk cite{display:block;margin-top:.8em;font-style:normal;font-family:var(--fb);font-size:.9rem;color:var(--do);font-weight:600}
.sm-h{font-size:1.15rem;color:var(--do);margin-bottom:.6em}

.duties{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:16px;margin-top:.6em}
.duty{position:relative;overflow:hidden;padding:20px 22px 22px 70px;border-radius:22px;background:#fff;border:1.5px solid rgba(193,18,31,.16);box-shadow:0 12px 28px rgba(126,12,22,.1);cursor:pointer}
.duty .num{position:absolute;left:18px;top:18px;width:38px;height:38px;border-radius:50%;display:grid;place-items:center;font-family:var(--fd);font-weight:800;color:#fff;background:var(--do)}
.duty:nth-child(2) .num{background:var(--xanh)}.duty:nth-child(3) .num{background:#D99A00}.duty:nth-child(4) .num{background:var(--dod)}
.duty h3{font-size:1.2rem;margin-bottom:.35em;color:var(--muc)}
.duty p{font-size:.94rem;line-height:1.55;color:var(--muc2)}
.seal{position:absolute;right:16px;bottom:12px;padding:12px 12px;border:3px double var(--do);border-radius:50%;color:var(--do);font-family:var(--fd);font-weight:800;font-size:.82rem;transform:rotate(-14deg) scale(3);opacity:0;pointer-events:none}
.duty.on{border-color:var(--do);background:#FFF6EA}
.duty.on .seal{animation:stamp .55s var(--spring) forwards}
@keyframes stamp{0%{transform:rotate(-14deg) scale(3);opacity:0}60%{opacity:1}100%{transform:rotate(-14deg) scale(1);opacity:.9}}

/* ===== CHƯƠNG 2 ===== */
.bigcnt{position:relative;display:inline-flex;align-items:baseline;gap:14px;margin:.3em 0 .6em;padding:6px 6px 6px 0}
.bigcnt b{position:relative;z-index:1;font-family:var(--fd);font-weight:900;font-size:clamp(5rem,12vw,9rem);line-height:.9;color:var(--do)}
.bigcnt span{position:relative;z-index:1;font-family:var(--fd);font-size:clamp(1.3rem,2.4vw,2rem);font-weight:700;color:var(--xanh)}
.pulse{position:absolute;left:-10px;top:50%;width:130px;height:130px;margin-top:-65px;border-radius:50%;background:rgba(245,183,0,.35);animation:pulse 2.4s ease-in-out infinite}
.pulse.p2{animation-delay:1.2s}
.five{display:flex;flex-wrap:wrap;gap:8px;margin-top:1em}
.five span{padding:7px 14px;border-radius:12px;background:#fff;border:1.5px solid rgba(46,107,78,.35);color:var(--xanhd);font-weight:600;font-size:.84rem;box-shadow:0 4px 10px rgba(46,107,78,.1)}
.slide.active .five span{animation:pop .5s var(--spring) backwards;animation-delay:calc(var(--k,0)*110ms + 1.2s)}
.steps{position:relative}
.steps::before{content:"";position:absolute;left:17px;top:20px;bottom:20px;width:3px;background:rgba(193,18,31,.15)}
.steps::after{content:"";position:absolute;left:17px;top:20px;width:3px;height:var(--sp,0%);max-height:calc(100% - 40px);background:linear-gradient(var(--do),var(--vang));transition:height .6s linear;box-shadow:0 0 10px rgba(245,183,0,.6)}
.steps li{position:relative;display:flex;gap:14px;padding:9px 0;cursor:pointer}
.steps li>i{position:relative;z-index:1;flex:none;width:36px;height:36px;border-radius:50%;display:grid;place-items:center;font-style:normal;font-weight:800;font-family:var(--fd);background:var(--kem);border:3px solid rgba(193,18,31,.3);color:var(--do);transition:all .5s var(--spring)}
.steps li.on>i{background:var(--do);border-color:var(--do);color:#fff;transform:scale(1.15)}
.steps li b{display:block;font-family:var(--fd);font-size:1.05rem}
.steps li p{font-size:.88rem;line-height:1.45;color:var(--muc2)}
.warn{margin-top:1em;padding:14px 18px;border-radius:16px;background:rgba(245,183,0,.22);border:1.5px dashed var(--vangd);font-size:.92rem;line-height:1.5}

.gauges{display:grid;grid-template-columns:repeat(5,minmax(0,1fr));gap:14px;margin:.6em 0 1em}
.gauge{padding:16px 10px 14px;border-radius:22px;background:#fff;box-shadow:0 12px 26px rgba(126,12,22,.1);text-align:center;border:1px solid rgba(193,18,31,.12)}
.gw{position:relative;max-width:150px;margin:0 auto}
.gw svg{width:100%;display:block;overflow:visible}
.gw b{position:absolute;inset:0;display:grid;place-items:center;font-family:var(--fd);font-size:1.7rem;font-weight:900;color:var(--muc)}
.gauge .gb{fill:none;stroke:rgba(193,18,31,.12);stroke-width:9}
.gauge .gf{fill:none;stroke:var(--do);stroke-width:9;stroke-linecap:round;transition:stroke-dashoffset 1.8s var(--ease),stroke-width .3s,filter .3s}
.gauge:nth-child(2) .gf{stroke:var(--xanh)}.gauge:nth-child(3) .gf{stroke:#E39A00}.gauge:nth-child(4) .gf{stroke:var(--do2)}.gauge:nth-child(5) .gf{stroke:#3B8A63}
.gauge:hover .gf{stroke-width:13;filter:drop-shadow(0 0 8px rgba(245,183,0,.8))}
.gauge p{font-size:.88rem;font-weight:600;line-height:1.35;margin-top:8px;min-height:3.8em}
.gauge small{display:block;font-size:.75rem;color:var(--do);font-weight:700;opacity:0;max-height:0;transition:all .3s}
.gauge:hover small{opacity:1;max-height:30px}
.msg.summ{max-width:780px;margin:0 auto}
.msg.summ .av{background:var(--xanh)}

.bars{display:flex;flex-direction:column;gap:12px;margin:.6em 0 1em}
.brow{display:grid;grid-template-columns:minmax(150px,34%) 1fr;gap:14px;align-items:center}
.bl{font-size:.95rem;font-weight:600;line-height:1.35}
.bt{position:relative;height:30px;border-radius:99px;background:rgba(193,18,31,.1)}
.bf{position:absolute;left:0;top:0;bottom:0;width:0;border-radius:99px;background:linear-gradient(90deg,var(--do),var(--vang));transition:width 1.6s var(--ease)}
.bf::after{content:"";position:absolute;right:-5px;top:50%;width:16px;height:16px;margin-top:-8px;border-radius:50%;background:var(--vang2);box-shadow:0 0 12px 4px rgba(245,183,0,.75);animation:pulse 1.8s infinite}
.bv{position:absolute;right:14px;top:50%;transform:translateY(-50%);font-weight:800;font-size:.9rem;color:var(--muc)}
.brow:hover .bf{filter:brightness(1.1) saturate(1.2)}
.brow:hover .bl{color:var(--do)}

.ripbox{display:flex;flex-direction:column;align-items:center;gap:14px}
#ripSvg{width:min(100%,460px);height:auto;overflow:visible}
#ripSvg .rr{fill:none;stroke:rgba(193,18,31,.2);stroke-width:5;cursor:pointer;transition:stroke .5s,stroke-width .5s,filter .5s}
#ripSvg .rr:hover{stroke-width:8}
#ripSvg .rr.lit{stroke:var(--c);stroke-width:10;filter:drop-shadow(0 0 7px var(--c))}
#ripSvg .core{fill:var(--do);filter:drop-shadow(0 0 8px rgba(193,18,31,.6))}
#ripSvg .rn{cursor:pointer}
#ripSvg .rn circle{fill:var(--kem);stroke:var(--c);stroke-width:3;transition:fill .4s}
#ripSvg .rn.lit circle{fill:var(--c)}
#ripSvg .rn text{text-anchor:middle;font:800 12px var(--fb);fill:var(--muc);pointer-events:none}
#ripSvg .rn.lit text{fill:#fff}
#ripSvg .wave{fill:none;stroke:var(--c);stroke-width:3;transform-box:fill-box;transform-origin:center;animation:wave 1.6s ease-out forwards;pointer-events:none}
@keyframes wave{from{transform:scale(.3);opacity:.9}to{transform:scale(var(--k,5));opacity:0}}
.ripchat{max-height:min(46vh,420px);overflow-y:auto;padding:4px 6px 4px 0;scrollbar-width:thin}
.ripchat .bub{border-left:5px solid var(--c)}
.ripchat .bub b{color:var(--c)}
.ripchat .av{background:var(--c)}

.rowh{display:flex;flex-wrap:wrap;align-items:center;justify-content:space-between;gap:12px}
.fgrid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px;margin-top:.4em}
.fc{perspective:1100px;cursor:pointer;height:clamp(118px,19vh,170px)}
.fc3{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:14px;margin:.6em 0 1em}
.fc3 .fc{height:clamp(200px,32vh,260px)}
.fi{position:relative;width:100%;height:100%;transform-style:preserve-3d;transition:transform .8s var(--ease)}
.fc.on .fi{transform:rotateY(180deg)}
.fc:hover .fi{transform:rotateY(8deg)}
.fc.on:hover .fi{transform:rotateY(172deg)}
.ff,.fb{position:absolute;inset:0;backface-visibility:hidden;-webkit-backface-visibility:hidden;border-radius:20px;padding:14px 16px;overflow:auto;scrollbar-width:none}
.ff{background:#fff;border:1.5px solid rgba(193,18,31,.18);box-shadow:0 10px 22px rgba(126,12,22,.1)}
.fb{background:linear-gradient(150deg,var(--do),var(--dod));color:#FFF3D1;transform:rotateY(180deg);box-shadow:0 10px 24px rgba(126,12,22,.35)}
.fc:nth-child(3n+2) .fb{background:linear-gradient(150deg,var(--xanh),var(--xanhd))}
.fc:nth-child(3n) .fb{background:linear-gradient(150deg,#C98B00,#8A6100)}
.ff small,.fb small{display:block;font-weight:700;font-size:.72rem;color:var(--xanh)}
.fb small{color:var(--vang2)}
.ff h4{font-size:1.02rem;margin:.25em 0 .3em;color:var(--muc);padding-right:34px}
.ff p,.fb p{font-size:.85rem;line-height:1.45}
.ff em{display:block;margin-top:.4em;font-size:.8rem;color:var(--muc2)}
.ff .no{position:absolute;right:12px;top:6px;font-family:var(--fd);font-weight:900;font-size:1.8rem;color:rgba(193,18,31,.2)}
.fb .ex{display:flex;flex-wrap:wrap;gap:5px 8px;margin-top:6px;font-size:.8rem}
.fb .ex s{padding:1px 8px;border-radius:99px;background:rgba(0,0,0,.28);text-decoration-color:var(--vang2)}
.fb .ex u{text-decoration:none;padding:1px 8px;border-radius:99px;background:rgba(255,255,255,.92);color:var(--xanhd);font-weight:700}

.eval{align-items:stretch;margin-top:.6em}
.ev p{line-height:1.6;font-size:.98rem}
.ev.ok{border-top:6px solid var(--xanh)}.ev.ok h3{color:var(--xanh)}
.ev.bad{border-top:6px solid var(--do)}
.ev.todo{border-top:6px solid var(--vang)}.ev.todo h3{color:var(--vangd)}
#todo li{position:relative;padding:9px 12px 9px 46px;margin-bottom:8px;border-radius:14px;background:rgba(245,183,0,.14);cursor:pointer;font-size:.9rem;line-height:1.4;transition:background .3s,transform .3s var(--spring)}
#todo li::before{content:"";position:absolute;left:12px;top:50%;width:22px;height:22px;margin-top:-11px;border-radius:7px;border:2.5px solid var(--vangd);background:#fff;transition:all .3s}
#todo li::after{content:"";position:absolute;left:19px;top:50%;width:7px;height:12px;margin-top:-9px;border:solid #fff;border-width:0 3px 3px 0;transform:rotate(45deg) scale(0);transition:transform .35s var(--spring)}
#todo li:hover{transform:translateX(4px)}
#todo li.on{background:rgba(46,107,78,.18)}
#todo li.on::before{background:var(--xanh);border-color:var(--xanh)}
#todo li.on::after{transform:rotate(45deg) scale(1)}
.pbar{height:10px;border-radius:99px;background:rgba(0,0,0,.08);overflow:hidden;margin:12px 0 8px}
.pbar i{display:block;height:100%;width:0;background:linear-gradient(90deg,var(--vang),var(--xanh));transition:width .7s var(--ease)}

/* ===== CHƯƠNG 3 ===== */
.stairs{position:relative;display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:16px;align-items:end;margin-top:1.4em}
.st{position:relative;padding:20px 20px 18px;border-radius:22px;background:#fff;border:1.5px solid rgba(193,18,31,.16);box-shadow:0 14px 30px rgba(126,12,22,.12)}
.st1{margin-top:80px;border-bottom:8px solid var(--do)}.st2{margin-top:40px;border-bottom:8px solid var(--vang)}.st3{border-bottom:8px solid var(--xanh)}
.step{position:absolute;right:16px;top:6px;font-family:var(--fd);font-weight:900;font-size:3.2rem;color:rgba(193,18,31,.14)}
.st h3{font-size:1.2rem;margin-bottom:.4em;max-width:80%}
.st p{font-size:.93rem;line-height:1.55}
.how{margin-top:.8em;padding:10px 12px;border-radius:12px;background:rgba(46,107,78,.1);font-size:.86rem;line-height:1.5;color:var(--xanhd)}
.flag{position:absolute;right:7%;top:-50px;width:46px;height:32px;display:grid;place-items:center;background:var(--do);color:var(--vang);font-style:normal;font-size:1rem;transform-origin:0 50%;animation:wave2 1.6s ease-in-out infinite;box-shadow:0 4px 10px rgba(126,12,22,.35)}
.flag::before{content:"";position:absolute;left:-3px;top:-6px;width:3px;height:84px;background:#7a5a3a}
@keyframes wave2{0%,100%{transform:skewY(-4deg) scaleX(1)}50%{transform:skewY(4deg) scaleX(.94)}}

.learn{display:flex;flex-direction:column;gap:12px;margin-top:.6em}
.lc{display:flex;gap:14px;align-items:flex-start;padding:16px 18px;border-radius:20px;background:#fff;box-shadow:0 10px 24px rgba(126,12,22,.1);border-left:6px solid var(--do)}
.lc:nth-child(2){border-left-color:var(--vang)}.lc:nth-child(3){border-left-color:var(--xanh)}
.lc>b{flex:none;width:36px;height:36px;border-radius:50%;display:grid;place-items:center;font-family:var(--fd);background:var(--do);color:#fff}
.lc:nth-child(2)>b{background:#D99A00}.lc:nth-child(3)>b{background:var(--xanh)}
.lc h3{font-size:1.05rem;margin-bottom:.25em}.lc p{font-size:.9rem;line-height:1.5;color:var(--muc2)}
.notebook{position:relative;background:repeating-linear-gradient(transparent 0 33px,rgba(46,107,78,.22) 33px 34px),#FFFBEF;padding-left:clamp(40px,5vw,60px)}
.notebook::before{content:"";position:absolute;left:30px;top:0;bottom:0;width:2px;background:rgba(193,18,31,.4)}
.notebook h3{margin-bottom:10px}
#nbList{min-height:136px;max-height:204px;overflow-y:auto;margin-bottom:10px;scrollbar-width:thin}
#nbList li{display:flex;align-items:center;gap:10px;height:34px;font-size:1rem;animation:pop .5s var(--spring)}
#nbList s{color:var(--do);text-decoration-thickness:2px}
#nbList b{color:var(--xanh);font-family:var(--fd);font-size:1.1rem}
.stp{margin-left:auto;font-style:normal;font-size:.66rem;font-weight:800;color:var(--xanh);border:2px solid var(--xanh);padding:0 6px;border-radius:6px;transform:rotate(-8deg);animation:stamp2 .5s var(--spring) .2s backwards}
@keyframes stamp2{from{transform:rotate(-8deg) scale(3);opacity:0}to{transform:rotate(-8deg) scale(1);opacity:1}}
.nbform{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-bottom:8px}
.nbform input{flex:1;min-width:110px;padding:9px 14px;border-radius:12px;border:1.5px solid rgba(193,18,31,.3);background:#fff;outline:none}
.nbform input:focus{border-color:var(--do);box-shadow:0 0 0 4px rgba(193,18,31,.12)}
.nbform>span{color:var(--vangd);font-weight:800}

.meter{display:flex;align-items:center;gap:12px;font-weight:700;font-size:.9rem;margin-bottom:.7em}
.mbar{position:relative;flex:1;height:14px;border-radius:99px;background:rgba(0,0,0,.08);overflow:hidden}
.mbar i{position:absolute;inset:0;border-radius:99px;background:linear-gradient(90deg,var(--xanh),var(--vang),var(--do));clip-path:inset(0 75% 0 0 round 99px);transition:clip-path .8s var(--ease)}
#meterV{min-width:3.2ch;text-align:right;color:var(--do)}
.rule{font-size:.98rem;line-height:1.6}

.big79{display:flex;align-items:center;gap:16px;margin:.4em 0 .8em;flex-wrap:wrap}
.big79 b{font-family:var(--fd);font-weight:900;font-size:clamp(3.4rem,7.5vw,5.6rem);line-height:1;color:var(--do);white-space:nowrap}
.big79 span{flex:1;min-width:220px;font-size:1rem;line-height:1.5;color:var(--muc2)}
.donutcard{display:flex;flex-direction:column;align-items:center;text-align:center;gap:10px}
.donut{position:relative;width:min(220px,60vw)}
.donut svg{width:100%;display:block;transform:rotate(-90deg)}
.donut circle{fill:none;stroke-width:22;transition:stroke-dashoffset 1.6s var(--ease),stroke-width .3s,opacity .3s}
.dc{position:absolute;inset:0;display:grid;place-content:center;text-align:center}
.dc b{font-family:var(--fd);font-size:2.1rem;font-weight:900;color:var(--muc)}
.dc small{font-size:.8rem;font-weight:700;color:var(--muc2)}
.legend{display:flex;flex-wrap:wrap;gap:8px;justify-content:center}
.legend li{display:flex;align-items:center;gap:6px;padding:4px 12px;border-radius:99px;background:rgba(0,0,0,.05);font-size:.82rem;font-weight:600;cursor:pointer;transition:transform .25s var(--spring)}
.legend li:hover{transform:translateY(-3px)}
.legend i{width:12px;height:12px;border-radius:50%}
.twoside{display:flex;flex-wrap:wrap;gap:8px;margin:12px 0}

.how4{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px;margin-bottom:.8em}
.hw{display:flex;gap:12px;padding:14px 16px;border-radius:18px;background:#fff;box-shadow:0 10px 22px rgba(126,12,22,.1);font-size:.92rem;line-height:1.5;border-left:5px solid var(--do)}
.hw>b{flex:none;width:30px;height:30px;border-radius:50%;display:grid;place-items:center;background:var(--do);color:#fff;font-family:var(--fd)}
.hw:nth-child(2){border-left-color:var(--vang)}.hw:nth-child(2)>b{background:#D99A00}
.hw:nth-child(3){border-left-color:var(--xanh)}.hw:nth-child(3)>b{background:var(--xanh)}
.hw:nth-child(4){border-left-color:var(--dod)}.hw:nth-child(4)>b{background:var(--dod)}
.fmts{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:12px;margin-bottom:.8em}
.fmt{display:flex;flex-direction:column;gap:6px;padding:16px;border-radius:20px;background:#fff;box-shadow:0 10px 24px rgba(126,12,22,.1);border-top:5px solid var(--xanh)}
.fmt:nth-child(odd){border-top-color:var(--do)}
.fmt small{font-weight:700;color:var(--xanh);font-size:.74rem}
.fmt h4{font-size:1.05rem}.fmt p{font-size:.86rem;line-height:1.5;color:var(--muc2);flex:1}
.fmt .chip{align-self:flex-start}

.q3{display:flex;flex-direction:column;gap:12px;margin-top:1em}
.q3 li{display:flex;gap:14px;align-items:center;padding:14px 18px;border-radius:18px;background:rgba(255,255,255,.1);border:1px solid rgba(255,217,90,.3);font-size:1.02rem;line-height:1.45}
.q3 li>b{flex:none;width:38px;height:38px;border-radius:50%;display:grid;place-items:center;background:var(--vang);color:var(--dodd);font-family:var(--fd);font-size:1.1rem}
.post{background:#fff;color:var(--muc);border-radius:24px;padding:18px;box-shadow:0 24px 50px rgba(0,0,0,.35)}
.post-h{display:flex;gap:10px;align-items:center;margin-bottom:10px}
.post-h small{display:block;color:#8a7d73;font-size:.75rem}
.post textarea{width:100%;resize:none;border:1.5px solid rgba(0,0,0,.12);border-radius:14px;padding:12px 14px;font-size:1.02rem;line-height:1.5;outline:none;background:#FFFBF0;transition:border-color .2s,box-shadow .2s}
.post textarea:focus{border-color:var(--do);box-shadow:0 0 0 4px rgba(193,18,31,.12)}
.qchat{margin:12px 0 0;gap:8px}
.qchat .bub{font-size:.9rem;padding:8px 13px}
.qchat .bub.good{background:#E3F5E8}.qchat .bub.bad{background:#FFE3E0}
.feed{margin-top:10px}
.fpost{padding:12px 14px;border-radius:16px;background:#F3FBF5;border:1px solid rgba(46,107,78,.3);animation:pop .6s var(--spring)}
.fpost small{color:#6f8478}
.fpost .lk{margin-top:6px;font-weight:700;color:var(--do);font-size:.9rem}

.kv{display:grid;gap:8px;margin:.4em 0 1em}
.kv>div{display:grid;grid-template-columns:150px 1fr;gap:14px;padding:11px 16px;border-radius:14px;background:#fff;box-shadow:0 6px 16px rgba(126,12,22,.07);font-size:.92rem;line-height:1.5;transition:background .3s}
.kv dt{font-weight:800;color:var(--do);font-family:var(--fd)}
.kv>div:hover{background:#FFF6EA}
.weeks12{display:flex;flex-wrap:wrap;gap:8px;align-items:center}
.wk{width:44px;height:44px;border-radius:50%;display:grid;place-items:center;font-weight:800;font-size:.8rem;background:rgba(193,18,31,.1);color:var(--do);border:2px solid rgba(193,18,31,.3);transition:all .35s var(--spring)}
.wk:hover{transform:scale(1.2)}
.wk.on{background:var(--do);color:#fff;transform:scale(1.1);box-shadow:0 6px 14px rgba(126,12,22,.35)}
.gantt{display:flex;gap:6px;height:64px;margin-top:6px}
.gantt>div{display:flex;flex-direction:column;justify-content:center;padding:10px 12px;border-radius:14px;color:#FFF3D1;background:linear-gradient(135deg,var(--do),var(--dod));transform-origin:0 50%;transition:transform .3s var(--spring)}
.gantt>div:nth-child(2){background:linear-gradient(135deg,var(--xanh),var(--xanhd))}
.gantt>div:nth-child(3){background:linear-gradient(135deg,#D99A00,#8A6100)}
.gantt>div:hover{transform:scaleY(1.14)}
.gantt b{font-size:.85rem}.gantt small{opacity:.9;font-size:.74rem}
.tp.on .gantt>div{animation:grow .9s var(--ease) backwards}
.tp.on .gantt>div:nth-child(2){animation-delay:.25s}.tp.on .gantt>div:nth-child(3){animation-delay:.5s}
@keyframes grow{from{transform:scaleX(0);opacity:0}to{transform:none;opacity:1}}
.conds{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:12px}
.cd{display:flex;gap:12px;padding:14px 16px;border-radius:18px;background:#fff;box-shadow:0 10px 22px rgba(126,12,22,.1);font-size:.92rem;line-height:1.5}
.cd>b{flex:none;width:30px;height:30px;border-radius:50%;display:grid;place-items:center;background:var(--xanh);color:#fff;font-family:var(--fd)}

.bil{display:grid;grid-template-columns:repeat(auto-fit,minmax(118px,1fr));gap:10px;margin:.4em 0 1em}
.bc{perspective:800px;height:84px;cursor:pointer}
.bc .fi{transition:transform .7s var(--ease)}
.bc.en .fi{transform:rotateX(180deg)}
.bc .ff,.bc .fb{display:grid;place-items:center;text-align:center;font-family:var(--fd);font-weight:800;font-size:1.05rem;padding:8px}
.bc .fb{transform:rotateX(180deg);background:linear-gradient(150deg,var(--xanh),var(--xanhd));color:#FFF3D1}
.bc .ff{color:var(--do)}
.hue p{line-height:1.6;font-size:.96rem}
.dots8{display:flex;gap:8px;margin:10px 0}
.dots8 i{width:22px;height:22px;border-radius:50%;background:rgba(245,183,0,.25);border:2px solid var(--vangd);transition:all .4s var(--spring)}
.dots8 i.on{background:var(--vang);box-shadow:0 0 14px 3px rgba(245,183,0,.7);transform:scale(1.2)}

.tech{display:flex;flex-direction:column;gap:12px;margin-top:.6em}
.tc{display:flex;gap:14px;align-items:flex-start;padding:16px 18px;border-radius:20px;background:#fff;box-shadow:0 10px 24px rgba(126,12,22,.1);border-left:6px solid var(--xanh)}
.tc:nth-child(2){border-left-color:var(--vang)}.tc:nth-child(3){border-left-color:var(--do)}
.tc>b{flex:none;width:36px;height:36px;border-radius:50%;display:grid;place-items:center;font-family:var(--fd);background:var(--xanh);color:#fff}
.tc:nth-child(2)>b{background:#D99A00}.tc:nth-child(3)>b{background:var(--do)}
.tc h3{font-size:1.05rem;margin-bottom:.25em}.tc p{font-size:.9rem;line-height:1.5;color:var(--muc2)}
.quiz{min-height:350px;display:flex;flex-direction:column;gap:12px}
.qtop{display:flex;align-items:center;gap:6px}
.qtop i{flex:1;height:8px;border-radius:8px;background:rgba(193,18,31,.15);transition:background .4s}
.qtop i.ok{background:var(--xanh)}.qtop i.no{background:var(--do)}.qtop i.cur{background:var(--vang)}
.qq{font-family:var(--fd);font-size:1.3rem;line-height:1.4;font-weight:700}
.qq u{display:inline-block;min-width:4.4em;border-bottom:3px dashed var(--do);text-decoration:none;text-align:center;color:var(--do)}
.qo{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.qo button{padding:14px;border-radius:16px;background:#fff;border:2px solid rgba(193,18,31,.25);font-weight:700;font-size:1.05rem;text-align:center;transition:transform .25s var(--spring),background .3s,border-color .3s}
.qo button:hover:not(:disabled){transform:translateY(-3px)}
.qo button.ok{background:#E3F5E8;border-color:var(--xanh);color:var(--xanhd)}
.qo button.no{background:#FFE3E0;border-color:var(--do);color:var(--dod);animation:shake .45s}
.qo button:disabled{cursor:default}
.qfb{min-height:56px;font-size:.92rem;line-height:1.5}
.qres{text-align:center}
.qres b{font-family:var(--fd);font-size:3.6rem;color:var(--do);display:block;line-height:1.1}

.weeks{display:flex;flex-direction:column;gap:10px;margin:.6em 0}
.weeks li{display:flex;gap:12px;padding:12px 16px;border-radius:16px;background:#fff;box-shadow:0 8px 18px rgba(126,12,22,.08);font-size:.95rem;line-height:1.5;border-left:6px solid var(--do);transition:transform .3s,background .3s}
.weeks li:nth-child(2){border-left-color:#D99A00}.weeks li:nth-child(3){border-left-color:var(--xanh)}
.weeks li>b{flex:none;min-width:58px;font-family:var(--fd);color:var(--do)}
.weeks li.hot{background:#FFF3D1;transform:translateX(8px)}
.cal{display:flex;flex-direction:column;align-items:center;gap:14px}
.calring{position:relative;width:150px;height:150px}
.calring svg{width:100%;height:100%}
.calring .gb{fill:none;stroke:rgba(193,18,31,.13);stroke-width:10}
.calring .gf{fill:none;stroke:var(--do);stroke-width:10;stroke-linecap:round;stroke-dasharray:314.16;stroke-dashoffset:314.16;transition:stroke-dashoffset .5s var(--ease),stroke .4s}
.calring>div{position:absolute;inset:0;display:grid;place-content:center;text-align:center}
.calring b{font-family:var(--fd);font-size:2.6rem;font-weight:900;line-height:1}
.calring small{font-size:.78rem;color:var(--muc2);font-weight:700}
.days{display:grid;grid-template-columns:repeat(7,minmax(0,1fr));gap:8px;width:min(100%,430px)}
.dy{aspect-ratio:1;border-radius:14px;display:grid;place-items:center;font-weight:800;font-size:.95rem;color:var(--do);background:rgba(193,18,31,.09);border:2px solid rgba(193,18,31,.25);transition:all .35s var(--spring)}
.dy.w2{color:#8A6100;background:rgba(245,183,0,.14);border-color:rgba(245,183,0,.5)}
.dy.w3{color:var(--xanhd);background:rgba(46,107,78,.12);border-color:rgba(46,107,78,.4)}
.dy:hover{transform:translateY(-4px) scale(1.1)}
.dy.on{color:#fff;background:var(--do);border-color:var(--do);transform:scale(1.05);box-shadow:0 6px 14px rgba(126,12,22,.35)}
.dy.w2.on{background:#D99A00;border-color:#D99A00}.dy.w3.on{background:var(--xanh);border-color:var(--xanh)}

.orbit{position:relative;width:min(480px,88vw);aspect-ratio:1;margin:0 auto}
.orbit::before,.orbit::after{content:"";position:absolute;border-radius:50%;border:2px dashed rgba(255,217,90,.35)}
.orbit::before{inset:6%}.orbit::after{inset:26%}
.core{position:absolute;left:50%;top:50%;width:30%;aspect-ratio:1;margin:-15% 0 0 -15%;border-radius:50%;display:grid;place-content:center;text-align:center;background:radial-gradient(circle at 35% 30%,var(--vang2),var(--vang) 60%,#B98500);color:var(--dodd);font-family:var(--fd);font-weight:800;font-size:1.05rem;animation:glow2 3s ease-in-out infinite;z-index:2}
.core small{font-family:var(--fb);font-weight:600;font-size:.7rem}
@keyframes glow2{0%,100%{box-shadow:0 0 30px rgba(245,183,0,.5)}50%{box-shadow:0 0 64px rgba(245,183,0,.95)}}
.arm{position:absolute;inset:0;animation:orb 48s linear infinite}
.arm.i{inset:20%;animation-duration:36s;animation-direction:reverse}
@keyframes orb{from{transform:rotate(var(--a))}to{transform:rotate(calc(var(--a) + 360deg))}}
.nd{position:absolute;left:50%;top:0;width:100px;margin-left:-50px;margin-top:-36px;text-align:center;font-size:.76rem;font-weight:700;line-height:1.25;cursor:pointer;animation:orbr 48s linear infinite;z-index:3}
.arm.i .nd{animation-duration:36s;animation-direction:reverse}
@keyframes orbr{from{transform:rotate(calc(var(--a)*-1))}to{transform:rotate(calc(var(--a)*-1 - 360deg))}}
.nd i{display:grid;place-items:center;width:62px;height:62px;margin:0 auto 4px;border-radius:50%;font-style:normal;font-size:1.6rem;background:rgba(255,255,255,.16);border:2px solid var(--vang2);transition:transform .3s var(--spring),background .3s}
.nd:hover i,.nd.on i{transform:scale(1.2);background:var(--vang)}
.orbit:hover .arm,.orbit:hover .nd{animation-play-state:paused}

.bigq{font-family:var(--fd);font-weight:700;font-size:clamp(1.4rem,2.8vw,2.3rem);line-height:1.3;color:var(--kem)}
.bigq .hl{color:var(--vang2)}
.klchat{max-height:min(66vh,560px);overflow-y:auto;padding:4px 8px 4px 0;scrollbar-width:none}
.klchat .bub{font-size:.95rem}
.klchat .av{background:var(--vang);color:var(--dodd)}

.refq{width:100%;max-width:560px;margin:.4em 0 1em;padding:12px 18px;border-radius:99px;border:2px solid rgba(193,18,31,.3);background:#fff;font-size:1rem;outline:none}
.refq:focus{border-color:var(--do);box-shadow:0 0 0 5px rgba(193,18,31,.12)}
.refs{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px;counter-reset:r}
.refs li{position:relative;padding:12px 16px 12px 54px;border-radius:16px;background:#fff;box-shadow:0 6px 16px rgba(126,12,22,.08);font-size:.88rem;line-height:1.45;transition:transform .3s var(--spring),box-shadow .3s}
.refs li::before{counter-increment:r;content:counter(r);position:absolute;left:14px;top:12px;width:28px;height:28px;border-radius:50%;display:grid;place-items:center;background:var(--do);color:#fff;font-family:var(--fd);font-weight:800;font-size:.85rem}
.refs li:hover{transform:translateX(6px);box-shadow:0 10px 22px rgba(126,12,22,.15)}
.refs li.hide{display:none}
.refs mark{background:rgba(245,183,0,.5);color:inherit;border-radius:4px;padding:0 2px}

/* ===== RESPONSIVE ===== */
@media(max-width:980px){
 .g2,.g3{grid-template-columns:1fr}
 .ag{grid-template-columns:repeat(2,minmax(0,1fr))}.agpath{display:none}
 .gauges{grid-template-columns:repeat(3,minmax(0,1fr))}
 .fgrid{grid-template-columns:repeat(2,minmax(0,1fr))}
 .fc3{grid-template-columns:1fr}
 .stairs{grid-template-columns:1fr}.st1,.st2{margin-top:0}.flag{display:none}
 .duties,.how4,.refs{grid-template-columns:1fr}
 .kv>div{grid-template-columns:1fr;gap:2px}
 .acc{flex-direction:column;height:auto}
 .ap{flex:none;max-height:78px;transition:max-height .6s var(--ease)}
 .ap.on{flex:none;max-height:560px}
 .ap:not(.on) h3{writing-mode:horizontal-tb;transform:none;margin-top:0}
 .ap h3{display:inline}.ap .ico{display:inline-block;margin:0 10px 0 0}
 .split{flex-direction:column;height:auto}
 .drumbox{right:-38vw;top:32%;width:92vw;opacity:.4}
 .stats{grid-template-columns:1fr 1fr}.stats>div:nth-child(3){grid-column:1/-1}
 #bLaser,#bFs{display:none}
 .brow{grid-template-columns:1fr;gap:6px}
 .tl-card{padding:16px}
}
@media(max-width:560px){
 .gauges{grid-template-columns:repeat(2,minmax(0,1fr))}.fgrid{grid-template-columns:1fr}
 .tbtns{grid-template-columns:repeat(3,1fr)}.ag{grid-template-columns:1fr}.keys{display:none}
 .qo{grid-template-columns:1fr}#chap{display:none}
}
@media(prefers-reduced-motion:reduce){*,*::before,*::after{animation-duration:.01ms!important;animation-iteration-count:1!important;transition-duration:.01ms!important}}
/* ===== chỉnh bổ sung ===== */
.hero>.big{max-width:min(660px,100%);font-size:clamp(3.2rem,8.8vw,8rem)}
.big .wd{display:inline-block;white-space:nowrap}
.qchat .bub.good{background:#E3F5E8;color:var(--xanhd)}
.qchat .bub.bad{background:#FFE3E0;color:var(--dod)}
#orbInfo.pp{animation:pop .5s var(--spring)}
.green #orbInfo h3{color:var(--vang2)}
@media(max-height:820px){
 .fc{height:clamp(112px,17.5vh,150px)}
 .fc3 .fc{height:clamp(190px,30vh,240px)}
 .ff p,.fb p{font-size:.78rem;line-height:1.38}
 .ff h4{font-size:.95rem}
 .glyph{font-size:clamp(4rem,10vw,6.4rem)}
 .acc{height:clamp(280px,48vh,400px)}
}
@media(max-width:980px){.hero>.big{font-size:clamp(3rem,13vw,6rem)}}

.agc{display:flex;flex-direction:column;align-items:flex-start;justify-content:flex-start}
.scn::before{left:-30%;right:-30%;background:radial-gradient(ellipse 28% 55% at 50% 60%,rgba(255,255,255,.3),transparent 100%);animation:mist 20s ease-in-out infinite alternate}
@keyframes mist{from{transform:translateX(-12%)}to{transform:translateX(12%)}}
.nest .small{margin-top:10px}
.drumbox{overflow:hidden}
#s-hoatdong .lead{font-size:1rem;line-height:1.5}
#s-hoatdong .kv>div{padding:8px 14px}
#s-hoatdong .kv{gap:6px;margin-bottom:.7em}
</style></head>
<body data-theme="dark" data-mode="hero">
<canvas id="rain"></canvas>
<div id="deck">

<!-- 1 · BÌA -->
<section class="slide red hero-s" id="s-hero" data-mode="hero" data-theme="dark" data-ch="Mở đầu" data-title="Trang bìa">
  <div class="drumbox"><div class="drum" data-drum></div></div>
  <div class="wrap hero">
    <p class="pre rv"><span id="preTxt"></span><i class="caret"></i></p>
    <h1 class="big rv" id="bigT" aria-label="Chữ Quốc ngữ"></h1>
    <p class="sub rv">Khảo sát sinh viên năm nhất Trường Đại học Ngoại ngữ, Đại học Huế</p>
    <div class="row rv">
      <button class="btn gold mag" data-next>Bắt đầu thuyết trình</button>
      <button class="btn ghost mag" data-menu>Xem mục lục</button>
    </div>
    <p class="team rv"><span id="team" contenteditable="true" spellcheck="false" role="textbox" aria-label="Tên nhóm thực hiện">Nhóm thực hiện: bấm để ghi tên nhóm</span></p>
    <p class="keys rv"><kbd>←</kbd><kbd>→</kbd>chuyển slide<kbd>L</kbd>bút laser<kbd>F</kbd>toàn màn hình<kbd>M</kbd>mục lục<kbd>S</kbd>âm thanh</p>
  </div>
</section>

<!-- 2 · MỤC LỤC -->
<section class="slide paper" id="s-agenda" data-mode="paper" data-theme="paper" data-ch="Mở đầu" data-title="Mục lục">
  <div class="wrap">
    <h2 class="t rv">Hành trình của bài thuyết trình</h2>
    <p class="lead rv">Từ cội nguồn của chữ viết đến những việc sinh viên có thể làm ngay hôm nay. Bấm vào một chặng để đi thẳng tới đó.</p>
    <div class="ag">
      <svg class="agpath" viewBox="0 0 1000 80" preserveAspectRatio="none" aria-hidden="true"><path d="M0 40 C100 0 150 80 250 40 S400 0 500 40 S650 80 750 40 S900 0 1000 40" pathLength="1"/></svg>
      <button class="agc tilt rv" data-go="s-lydo"><b>0</b><h3>Mở đầu</h3><p>Lý do, mục đích, đối tượng, phạm vi</p><ul><li>Lý do chọn đề tài</li><li>Mục đích, đối tượng, phạm vi</li></ul></button>
      <button class="agc tilt rv" data-go="c1"><b>1</b><h3>Chương 1</h3><p>Cơ sở lý luận về chữ Quốc ngữ</p><ul><li>Khái niệm</li><li>Hình thành và phát triển</li><li>Vai trò</li><li>Giữ gìn và phát huy</li></ul></button>
      <button class="agc tilt rv" data-go="c2"><b>2</b><h3>Chương 2</h3><p>Thực trạng giữ gìn và phát huy chữ Quốc ngữ của sinh viên</p><ul><li>Khảo sát</li><li>Nhận thức và biểu hiện</li><li>Hạn chế và nguyên nhân</li></ul></button>
      <button class="agc tilt rv" data-go="c3"><b>3</b><h3>Chương 3</h3><p>Hoạt động và công tác sinh viên giữ gìn, phát huy chữ Quốc ngữ</p><ul><li>Học tập và giao tiếp</li><li>Mạng xã hội, công nghệ</li><li>Mô hình “21 ngày viết rõ”</li></ul></button>
      <button class="agc tilt rv" data-go="s-ketluan"><b>★</b><h3>Kết luận</h3><p>Giá trị của chữ Quốc ngữ và vai trò chủ thể của sinh viên</p><ul><li>Thông điệp chính</li><li>Tài liệu tham khảo</li></ul></button>
    </div>
  </div>
</section>

<!-- 3 · LÝ DO -->
<section class="slide paper" id="s-lydo" data-mode="paper" data-theme="paper" data-ch="Mở đầu" data-title="Lý do chọn đề tài">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Vì sao chọn đề tài này?</h2>
      <p class="lead rv">Quốc ngữ là hệ thống chữ viết giữ vai trò chủ đạo trong giao tiếp, giáo dục, hành chính, khoa học và truyền thông của xã hội Việt Nam hiện đại.</p>
      <p class="lead rv">Cùng với Internet và mạng xã hội, cách giới trẻ dùng tiếng Việt đang biến đổi rõ rệt. Sinh viên dùng ngôn ngữ với tần suất cao trên nền tảng số, nên có thể tác động đến xu hướng sử dụng tiếng Việt trong tương lai.</p>
      <div class="tags rv"><span class="chip">viết tắt</span><span class="chip y">teencode</span><span class="chip g">từ vay mượn</span><span class="chip">biến đổi chính tả</span><span class="chip y">pha trộn tiếng Anh</span><span class="chip g">lạm dụng ngôn ngữ mạng</span></div>
      <blockquote class="note rv">Không đánh đồng mọi biến đổi ngôn ngữ với “sự xuống cấp của tiếng Việt”. Ngôn ngữ luôn biến đổi; vấn đề là <span class="hl">biến đổi trong bối cảnh nào, với chức năng gì và có phù hợp với chuẩn mực giao tiếp hay không</span>.</blockquote>
    </div>
    <div class="rv">
      <div class="phone"><div class="screen">
        <div class="ph-top"><span class="av">L</span><div><b>Nhóm lớp</b><small>đang hoạt động</small></div></div>
        <div class="ph-body chat" id="chat-lydo" data-cnt="#fx-lydo"></div>
        <div class="ph-in"><i>Nhập tin nhắn…</i><span>➤</span></div>
      </div></div>
      <p class="hint">Bấm vào chữ gạch đỏ để sửa lỗi: <b id="fx-lydo">0/6</b></p>
      <div class="row" style="justify-content:center;margin-top:6px"><button class="btn mini ghost" data-replay="lydo">Phát lại</button><button class="btn mini pri" data-fixall>Sửa tất cả</button></div>
    </div>
  </div>
</section>

<!-- 4 · MỤC ĐÍCH / ĐỐI TƯỢNG / PHẠM VI -->
<section class="slide paper" id="s-mucdich" data-mode="paper" data-theme="paper" data-ch="Mở đầu" data-title="Mục đích, đối tượng, phạm vi">
  <div class="wrap">
    <h2 class="t rv">Đề tài hướng tới điều gì?</h2>
    <div class="tabs rv" data-tabs><i class="ink"></i><button class="on" data-t="a">Mục đích</button><button data-t="b">Đối tượng nghiên cứu</button><button data-t="c">Phạm vi</button></div>
    <div class="tp on" data-p="a">
      <p class="lead">Khảo sát và phân tích nhận thức, thái độ và hành vi sử dụng Quốc ngữ của sinh viên trong học tập và giao tiếp, đặc biệt trong môi trường truyền thông số.</p>
      <ul class="chk">
        <li style="--k:0">Làm rõ vai trò của sinh viên trong việc duy trì và phát triển văn hóa ngôn ngữ Việt Nam.</li>
        <li style="--k:1">Nhận diện xu hướng sử dụng Quốc ngữ của sinh viên, nhất là trên mạng xã hội và giao tiếp trực tuyến.</li>
        <li style="--k:2">Phân tích mối quan hệ giữa ngôn ngữ chuẩn và các biến thể ngôn ngữ trong môi trường số.</li>
        <li style="--k:3">Đề xuất giải pháp để sinh viên dùng Quốc ngữ linh hoạt nhưng có ý thức: hiệu quả giao tiếp mà vẫn tôn trọng chuẩn mực.</li>
      </ul>
      <div class="deep">Mục tiêu sâu hơn: không chỉ “giữ nguyên” Quốc ngữ, mà bảo tồn giá trị cốt lõi đồng thời phát huy khả năng thích ứng của ngôn ngữ trong xã hội hiện đại.</div>
    </div>
    <div class="tp" data-p="b">
      <p class="lead">Hoạt động sử dụng và thái độ của sinh viên đối với chữ Quốc ngữ trong ba môi trường giao tiếp: học tập – học thuật, đời sống thường nhật và không gian mạng.</p>
      <div class="mini5">
        <div class="tilt"><b>1</b>Nhận thức về vai trò và giá trị của Quốc ngữ</div>
        <div class="tilt"><b>2</b>Thói quen dùng tiếng Việt khi giao tiếp trực tiếp và trực tuyến</div>
        <div class="tilt"><b>3</b>Dùng từ viết tắt, teencode, tiếng lóng, từ vay mượn, ngôn ngữ mạng</div>
        <div class="tilt"><b>4</b>Ý thức chính tả và ngữ pháp trong văn bản học tập</div>
        <div class="tilt"><b>5</b>Quan điểm về quan hệ giữa ngôn ngữ mạng và chuẩn mực tiếng Việt</div>
      </div>
    </div>
    <div class="tp" data-p="c">
      <div class="mini4">
        <div class="card tilt"><h3>Về đối tượng</h3><p>Sinh viên các trường đại học, ưu tiên nhóm thanh niên.</p></div>
        <div class="card tilt"><h3>Về không gian</h3><p>Môi trường đại học và không gian giao tiếp số: mạng xã hội, ứng dụng nhắn tin phổ biến.</p></div>
        <div class="card tilt"><h3>Về nội dung</h3><p>Ba phương diện: nhận thức; thực trạng dùng Quốc ngữ trong giao tiếp và học tập; vai trò và giải pháp của sinh viên.</p></div>
        <div class="card tilt"><h3>Về ngôn ngữ</h3><p>Không khảo sát toàn bộ tiếng Việt; tập trung vào chữ viết, chính tả, từ ngữ và cách dùng trong giao tiếp của sinh viên.</p></div>
      </div>
    </div>
  </div>
</section>

<!-- 5 · CHƯƠNG 1 -->
<section class="slide red dv" id="c1" data-mode="div" data-theme="dark" data-ch="Chương 1" data-title="Chương 1 · Cơ sở lý luận">
  <div class="drumbox sm"><div class="drum" data-drum></div></div>
  <div class="wrap">
    <div class="dnum rv">1</div>
    <p class="dsm rv">Chương 1</p>
    <h2 class="dt rv">Cơ sở lý luận về chữ Quốc ngữ</h2>
    <ul class="dli"><li class="rv">Khái niệm</li><li class="rv">Hình thành và phát triển</li><li class="rv">Vai trò</li><li class="rv">Giữ gìn và phát huy</li><li class="rv">Vai trò của sinh viên</li></ul>
  </div>
</section>

<!-- 6 · 1.1 KHÁI NIỆM + SÁU THANH -->
<section class="slide paper" id="s-khainiem" data-mode="paper" data-theme="paper" data-ch="Chương 1" data-title="1.1 Khái niệm chữ Quốc ngữ">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Chữ Quốc ngữ là gì?</h2>
      <p class="lead rv">Chữ viết chính thức của tiếng Việt hiện nay: dùng ký tự Latin, bổ sung các dấu phụ để ghi lại âm và thanh điệu.</p>
      <div class="stats rv">
        <div><b class="cnt" data-to="29">0</b><span>chữ cái</span></div>
        <div><b class="cnt" data-to="6">0</b><span>thanh điệu</span></div>
        <div><b>Ghi âm</b><span>học bảng chữ cái và cách ghép vần là đọc, viết được</span></div>
      </div>
      <p class="mu rv">Khác chữ Hán và chữ Nôm (tượng hình, biểu ý), chữ Quốc ngữ ghi âm trực tiếp nên học nhanh và phổ cập nhanh.</p>
      <div class="nest rv">
        <div class="n1"><span>Tiếng Việt: lời nói và chữ viết, cùng các biến thể vùng miền</span><div class="n2"><b>Chữ Quốc ngữ</b><span>hệ thống chữ viết ghi lại tiếng Việt</span></div></div>
        <p class="small mu">Tiếng nói có trước, chữ viết có sau, nên không thể đồng nhất hai khái niệm.</p>
      </div>
    </div>
    <div class="card tone rv">
      <h3>Sáu thanh, sáu nghĩa</h3>
      <div class="glyph" id="glyph">má</div>
      <div class="chat tchat" id="toneChat"></div>
      <div class="tbtns" id="tbtns"></div>
      <p class="mu small">Bỏ dấu dễ khiến người đọc hiểu nhầm nghĩa.</p>
    </div>
  </div>
</section>

<!-- 7 · 1.2 HÌNH THÀNH -->
<section class="slide paper" id="s-hinhthanh" data-mode="paper" data-theme="paper" data-ch="Chương 1" data-title="1.2 Hình thành và phát triển">
  <div class="wrap">
    <h2 class="t rv">Chữ Quốc ngữ ra đời như thế nào?</h2>
    <p class="lead rv">Bấm vào từng mốc thời gian, hoặc để dấu ấn tự chạy dọc dòng lịch sử.</p>
    <div class="tl rv" id="tl"><div class="tl-line"><i id="tlFill"></i></div><div id="tlNodes"></div><div class="tl-pin" id="tlPin">★</div></div>
    <div class="tl-card" id="tlCard"></div>
  </div>
</section>

<!-- 8 · CHỮ ĐƯỢC NÂNG CẤP -->
<section class="slide paper" id="s-morph" data-mode="paper" data-theme="paper" data-ch="Chương 1" data-title="Từ chữ dính liền đến chữ có dấu">
  <div class="wrap">
    <h2 class="t rv">Từ chữ “dính liền” đến chữ có dấu</h2>
    <p class="lead rv">Giai đoạn đầu, chữ Quốc ngữ còn nhiều khuyết điểm. Bấm vào từng thẻ để xem chữ được “nâng cấp”.</p>
    <div class="defects rv" id="defects"><span>Chưa có dấu thanh</span><span>Viết dính nhau</span><span>Thiếu nhiều nguyên âm</span><span>Chưa có phụ âm đơn đ, x, v</span></div>
    <div class="mgrid rv" id="mgrid"></div>
    <div class="row rv"><button class="btn pri" id="morphAll">Nâng cấp tất cả</button><button class="btn ghost" id="morphReset">Về chữ thuở sơ khai</button></div>
  </div>
</section>

<!-- 9 · 1.3 VAI TRÒ -->
<section class="slide paper" id="s-vaitro" data-mode="paper" data-theme="paper" data-ch="Chương 1" data-title="1.3 Vai trò của chữ Quốc ngữ">
  <div class="wrap">
    <h2 class="t rv">Chữ Quốc ngữ giữ vai trò gì?</h2>
    <p class="lead rv">Di chuột hoặc bấm vào từng mảng để mở rộng.</p>
    <div class="acc rv" id="acc1">
      <article class="ap on" tabindex="0"><span class="ico">📚</span><h3>Học tập và giáo dục</h3><div class="ab"><p><b>Xóa mù chữ, nâng cao dân trí.</b> Chữ ghi âm vị, dễ học dễ nhớ, loại bỏ rào cản phức tạp của chữ Hán, chữ Nôm.</p><p><b>Giáo dục đại trà.</b> Là công cụ chính thức trong nhà trường từ bậc tiểu học đến đại học, chuẩn hóa chương trình và phổ cập giáo dục cho toàn dân.</p></div></article>
      <article class="ap" tabindex="0"><span class="ico">🔬</span><h3>Nghiên cứu và học thuật</h3><div class="ab"><p><b>Phiên dịch, chuyển ngữ.</b> Thuận lợi cho việc tiếp thu và chuyển ngữ các thuật ngữ khoa học.</p><p><b>Nền học thuật độc lập.</b> Dễ lưu trữ, biên soạn tài liệu, thúc đẩy nền khoa học và tri thức nước nhà.</p></div></article>
      <article class="ap" tabindex="0"><span class="ico">💬</span><h3>Giao tiếp hằng ngày</h3><div class="ab"><p><b>Thống nhất ngôn ngữ toàn quốc.</b> Phá vỡ giới hạn vùng miền, tạo phương tiện giao tiếp chung, liền mạch, chuẩn mực.</p><p><b>Gắn kết cộng đồng.</b> Là sợi dây kết nối tình cảm, tư tưởng giữa các thế hệ.</p></div></article>
      <article class="ap" tabindex="0"><span class="ico">🌐</span><h3>Môi trường số</h3><div class="ab"><p><b>Tương thích công nghệ toàn cầu.</b> Hệ ký tự Latin chuẩn dễ tích hợp vào mã hóa, cơ sở dữ liệu và internet.</p><p><b>Hội nhập trên không gian mạng.</b> Giúp văn hóa và tiếng nói người Việt hòa nhập mạnh mẽ.</p></div></article>
      <article class="ap" tabindex="0"><span class="ico">🎓</span><h3>Đối với sinh viên</h3><div class="ab"><p>Công cụ nền tảng để tiếp thu tri thức, nghiên cứu khoa học và gìn giữ bản sắc văn hóa dân tộc trong thời đại số.</p><p>Giúp đọc hiểu, ghi chép, tổng hợp tài liệu; rèn tư duy phản biện và kỹ năng giao tiếp; hiểu và trân trọng di sản của cha ông.</p></div></article>
    </div>
  </div>
</section>

<!-- 10 · 1.4–1.5 GIỮ GÌN & PHÁT HUY -->
<section class="slide paper" id="s-giugin" data-mode="paper" data-theme="paper" data-ch="Chương 1" data-title="1.4–1.5 Giữ gìn và phát huy">
  <div class="wrap">
    <h2 class="t rv">Giữ gìn và phát huy: hai việc, một mục tiêu</h2>
    <div class="split rv" id="split">
      <div class="sp sa on" tabindex="0"><h3>Giữ gìn</h3><p>Bảo tồn ngôn ngữ dân tộc khỏi bị mai một giữa dòng chảy hiện đại.</p></div>
      <div class="sp sb" tabindex="0"><h3>Phát huy</h3><p>Làm mới, nghiên cứu và phát triển tiếng Việt bằng tinh thần sáng tạo, để tiếng Việt không nằm yên trong quá khứ mà tiếp tục sống động trong hiện tại.</p></div>
    </div>
    <div class="g2 low">
      <blockquote class="silk rv">Như con ong hút ngàn vạn nhụy hoa mới tạo thành được một giọt mật. Trải qua nhiều gian nan mới có thể trở thành một thứ tiếng đẹp, một thứ tiếng hay.<cite>Giữ gìn và phát huy chữ Quốc ngữ là sử dụng tiếng Việt có ý thức, tôn trọng giá trị ngôn ngữ dân tộc.</cite></blockquote>
      <div class="rv"><h3 class="sm-h">Ý nghĩa của việc giữ gìn và phát huy</h3><div class="chat" id="chat-yn"></div></div>
    </div>
  </div>
</section>

<!-- 11 · 1.6 VAI TRÒ SINH VIÊN -->
<section class="slide paper" id="s-sinhvien" data-mode="paper" data-theme="paper" data-ch="Chương 1" data-title="1.6 Vai trò của sinh viên">
  <div class="wrap">
    <h2 class="t rv">Sinh viên cần làm gì?</h2>
    <p class="lead rv">Bấm vào từng nhiệm vụ để “đóng dấu nhận việc”: <b id="dutyN">0/4</b></p>
    <div class="duties">
      <div class="duty tilt rv" tabindex="0" role="button"><span class="num">1</span><h3>Tự hào và bảo vệ bản sắc</h3><p>Tôn trọng và bảo vệ giá trị truyền thống: yêu nước, ý chí tự cường, đoàn kết, nhân ái, khoan dung, trọng nghĩa tình, cần cù lao động sáng tạo.</p><span class="seal">Đã nhận</span></div>
      <div class="duty tilt rv" tabindex="0" role="button"><span class="num">2</span><h3>Học hỏi và sáng tạo</h3><p>Tiếp thu tinh hoa văn hóa nhân loại, đồng thời phát triển nét mới phù hợp với thời đại và bối cảnh đất nước.</p><span class="seal">Đã nhận</span></div>
      <div class="duty tilt rv" tabindex="0" role="button"><span class="num">3</span><h3>Tích cực trong hoạt động văn hóa</h3><p>Tham gia văn hóa, văn nghệ, thể thao, du lịch để làm giàu và đa dạng hóa nền văn hóa Việt Nam.</p><span class="seal">Đã nhận</span></div>
      <div class="duty tilt rv" tabindex="0" role="button"><span class="num">4</span><h3>Tham gia hoạt động xã hội</h3><p>Tình nguyện, từ thiện, bảo vệ môi trường: thể hiện sự quan tâm và trách nhiệm với cộng đồng và Tổ quốc.</p><span class="seal">Đã nhận</span></div>
    </div>
  </div>
</section>

<!-- 12 · CHƯƠNG 2 -->
<section class="slide red dv" id="c2" data-mode="div" data-theme="dark" data-ch="Chương 2" data-title="Chương 2 · Thực trạng">
  <div class="drumbox sm"><div class="drum" data-drum></div></div>
  <div class="wrap">
    <div class="dnum rv">2</div>
    <p class="dsm rv">Chương 2</p>
    <h2 class="dt rv">Thực trạng giữ gìn và phát huy chữ Quốc ngữ của sinh viên</h2>
    <ul class="dli"><li class="rv">Thiết kế khảo sát</li><li class="rv">Nhận thức</li><li class="rv">Biểu hiện tích cực</li><li class="rv">Hạn chế</li><li class="rv">Nguyên nhân</li><li class="rv">Đánh giá chung</li></ul>
  </div>
</section>

<!-- 13 · 2.1 KHẢO SÁT -->
<section class="slide paper" id="s-khaosat" data-mode="paper" data-theme="paper" data-ch="Chương 2" data-title="2.1 Thiết kế khảo sát">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Khảo sát được làm như thế nào?</h2>
      <div class="bigcnt rv"><i class="pulse"></i><i class="pulse p2"></i><b class="cnt" data-to="100">0</b><span>phiếu hợp lệ</span></div>
      <div class="tags rv"><span class="chip">Khảo sát trực tuyến</span><span class="chip y">Google Forms, 20 câu, 6–8 phút</span><span class="chip g">Không thu họ tên, mã sinh viên, số điện thoại, email</span></div>
      <p class="mu rv">Đối tượng chính là sinh viên năm nhất Trường Đại học Ngoại ngữ, Đại học Huế: nhóm đang làm quen với email học tập, tiểu luận, thuyết trình nhóm và quy cách trình bày văn bản ở bậc đại học.</p>
      <div class="five rv" id="five"><span>Thông tin chung</span><span>Nhận thức</span><span>Hành vi viết</span><span>Tình huống giao tiếp</span><span>Mức độ sẵn sàng tham gia hoạt động</span></div>
    </div>
    <div>
      <ol class="steps rv" id="steps">
        <li><i>1</i><div><b>Thử nghiệm phiếu</b><p>5–8 sinh viên làm thử, sửa các câu hỏi chưa rõ.</p></div></li>
        <li><i>2</i><div><b>Khảo sát chính thức</b><p>Mở biểu mẫu trong 7–10 ngày.</p></div></li>
        <li><i>3</i><div><b>Xuất dữ liệu</b><p>Đóng biểu mẫu, xuất sang Excel.</p></div></li>
        <li><i>4</i><div><b>Lọc phiếu</b><p>Loại phiếu không đồng ý tham gia, bỏ trống câu bắt buộc hoặc có dấu hiệu trả lời ngẫu nhiên.</p></div></li>
        <li><i>5</i><div><b>Báo cáo</b><p>Ghi rõ tổng số phản hồi, số phiếu bị loại và số phiếu hợp lệ.</p></div></li>
      </ol>
      <div class="warn rv"><b>Giới hạn:</b> chọn mẫu thuận tiện, dữ liệu tự báo cáo, nên kết quả chỉ phản ánh nhóm tham gia và không khái quát cho toàn trường.</div>
      <p class="foot rv">Số liệu trong chương này là số liệu minh họa phục vụ bài thuyết trình.</p>
    </div>
  </div>
</section>

<!-- 14 · 2.2 NHẬN THỨC -->
<section class="slide paper" id="s-nhanthuc" data-mode="paper" data-theme="paper" data-ch="Chương 2" data-title="2.2 Nhận thức của sinh viên">
  <div class="wrap">
    <h2 class="t rv">Sinh viên nhận thức ra sao?</h2>
    <p class="lead rv">Tỷ lệ sinh viên đồng ý với từng nhận định. Di chuột vào từng vòng để xem rõ hơn.</p>
    <div class="gauges rv" id="gauges"></div>
    <div class="msg summ rv"><span class="av">KS</span><div class="bub">Nhìn chung, sinh viên có nhận thức khá tích cực về việc giữ gìn và sử dụng chữ Quốc ngữ đúng chuẩn.</div></div>
    <p class="foot rv">Số liệu minh họa phục vụ bài thuyết trình.</p>
  </div>
</section>

<!-- 15 · 2.3 BIỂU HIỆN TÍCH CỰC -->
<section class="slide paper" id="s-tichcuc" data-mode="paper" data-theme="paper" data-ch="Chương 2" data-title="2.3 Biểu hiện tích cực">
  <div class="wrap">
    <h2 class="t rv">Những biểu hiện tích cực</h2>
    <p class="lead rv">Tỷ lệ sinh viên thực hiện từng hành vi (khảo sát minh họa).</p>
    <div class="bars rv" id="bars"></div>
    <div class="row rv"><button class="btn pri" id="sortBars">Sắp xếp theo tỷ lệ</button></div>
    <div class="msg summ rv"><span class="av">KS</span><div class="bub">Những kết quả trên cho thấy nhận thức về chữ Quốc ngữ đã được thể hiện qua nhiều hành động cụ thể trong học tập và đời sống.</div></div>
  </div>
</section>

<!-- 16 · 2.4 HẠN CHẾ (GỢN SÓNG) -->
<section class="slide paper" id="s-hanche" data-mode="paper" data-theme="paper" data-ch="Chương 2" data-title="2.4 Những hạn chế">
  <div class="wrap g2">
    <div class="ripbox rv"><svg id="ripSvg" viewBox="-250 -250 500 500" aria-label="Sáu vòng ảnh hưởng lan tỏa"></svg><button class="btn pri" id="drop">Thả một lỗi sai</button></div>
    <div>
      <h2 class="t rv">Một lỗi nhỏ, ảnh hưởng lớn</h2>
      <p class="lead rv">Dùng chữ Quốc ngữ chưa phù hợp không chỉ ảnh hưởng đến cách giao tiếp mà còn tác động đến học tập, hình ảnh cá nhân và việc giữ gìn tiếng Việt.</p>
      <div class="chat ripchat" id="ripChat"></div>
    </div>
  </div>
</section>

<!-- 17 · 2.5 NGUYÊN NHÂN -->
<section class="slide paper" id="s-nguyennhan" data-mode="paper" data-theme="paper" data-ch="Chương 2" data-title="2.5 Nguyên nhân">
  <div class="wrap">
    <div class="rowh"><h2 class="t rv">Vì sao sinh viên dùng chữ chưa chuẩn?</h2><button class="btn ghost rv" id="flipAll">Lật tất cả thẻ</button></div>
    <div class="fgrid rv" id="fgrid"></div>
  </div>
</section>

<!-- 18 · 2.6 ĐÁNH GIÁ CHUNG -->
<section class="slide paper" id="s-danhgia" data-mode="paper" data-theme="paper" data-ch="Chương 2" data-title="2.6 Đánh giá chung">
  <div class="wrap">
    <h2 class="t rv">Đánh giá chung</h2>
    <div class="g3 eval">
      <div class="card ev ok tilt rv"><h3>Mặt tích cực</h3><p>Phần lớn sinh viên vẫn có ý thức sử dụng chữ Quốc ngữ trong học tập và giao tiếp. Sinh viên tiếp cận công nghệ nhanh, sáng tạo trong dùng ngôn ngữ và ngày càng quan tâm đến kỹ năng giao tiếp, viết và trình bày.</p></div>
      <div class="card ev bad tilt rv"><h3>Mặt còn hạn chế</h3><p>Vẫn còn tình trạng viết tắt, sai chính tả, dùng tiếng lóng, ngôn ngữ mạng và xen ngoại ngữ không cần thiết. Một số sinh viên chưa phân biệt ngôn ngữ thân mật với ngôn ngữ cần dùng trong môi trường học tập, trang trọng.</p></div>
      <div class="card ev todo rv"><h3>Cần khắc phục</h3>
        <ul id="todo">
          <li>Nâng cao ý thức và trách nhiệm giữ gìn chữ Quốc ngữ</li>
          <li>Hạn chế lạm dụng ngôn ngữ mạng, tiếng lóng, viết tắt và ngoại ngữ</li>
          <li>Hình thành thói quen đọc sách để mở rộng vốn từ, nâng cao khả năng diễn đạt</li>
          <li>Luôn kiểm tra, sửa lỗi chính tả trước khi gửi hoặc nộp văn bản</li>
          <li>Chọn cách dùng ngôn ngữ phù hợp với từng đối tượng và hoàn cảnh</li>
        </ul>
        <div class="pbar"><i id="todoBar"></i></div>
        <p class="small mu">Bấm từng mục để đánh dấu đã cam kết.</p>
      </div>
    </div>
  </div>
</section>

<!-- 19 · CHƯƠNG 3 -->
<section class="slide red dv" id="c3" data-mode="div" data-theme="dark" data-ch="Chương 3" data-title="Chương 3 · Hoạt động và công tác sinh viên">
  <div class="drumbox sm"><div class="drum" data-drum></div></div>
  <div class="wrap">
    <div class="dnum rv">3</div>
    <p class="dsm rv">Chương 3</p>
    <h2 class="dt rv">Hoạt động và công tác sinh viên giữ gìn, phát huy chữ Quốc ngữ</h2>
    <ul class="dli"><li class="rv">Nâng cao nhận thức</li><li class="rv">Học tập</li><li class="rv">Giao tiếp</li><li class="rv">Mạng xã hội</li><li class="rv">Tự tổ chức hoạt động</li><li class="rv">Lợi thế ngoại ngữ</li><li class="rv">Công nghệ</li><li class="rv">21 ngày viết rõ</li><li class="rv">Điều kiện hỗ trợ</li></ul>
  </div>
</section>

<!-- 20 · 3.1 NÂNG CAO NHẬN THỨC -->
<section class="slide paper" id="s-nangcao" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.1 Nâng cao nhận thức và trách nhiệm">
  <div class="wrap">
    <h2 class="t rv">Nâng cao nhận thức và trách nhiệm</h2>
    <p class="lead rv">Ba bậc thang từ hiểu biết đến hành động.</p>
    <div class="stairs">
      <i class="flag" aria-hidden="true">★</i>
      <article class="st st1 tilt rv"><span class="step">1</span><h3>Tự tìm hiểu giá trị</h3><p>Nhận thức chữ Quốc ngữ không chỉ là công cụ giao tiếp mà là di sản văn hóa kết tinh công sức nhiều thế hệ, từ đó thêm trân trọng sự giàu đẹp và uyển chuyển của tiếng mẹ đẻ.</p><div class="how"><b>Cách thực hiện:</b> chủ động tìm đọc tài liệu lịch sử, bài viết, sách nghiên cứu về quá trình hình thành chữ Quốc ngữ.</div></article>
      <article class="st st2 tilt rv"><span class="step">2</span><h3>Xác định trách nhiệm cá nhân</h3><p>Mỗi người trẻ có nghĩa vụ bảo vệ sự trong sáng của ngôn ngữ dân tộc trước nguy cơ bị lai tạp, cẩu thả.</p><div class="how"><b>Cách thực hiện:</b> đọc tác phẩm văn học kinh điển, thơ ca tiếng Việt để cảm nhận độ tinh tế, giàu đẹp và uyển chuyển của ngôn từ.</div></article>
      <article class="st st3 tilt rv"><span class="step">3</span><h3>Hành động thiết thực</h3><p>Chuyển nhận thức thành thói quen: đọc lại văn bản trước khi gửi, kiểm tra chính tả, trích dẫn đúng nguồn và chịu trách nhiệm về nội dung đăng tải trên không gian mạng.</p><div class="how"><b>Cách thực hiện:</b> thường xuyên theo dõi các chuyên mục giữ gìn sự trong sáng của tiếng Việt trên báo chí, truyền hình, mạng xã hội (kể cả trang do nhóm xây dựng).</div></article>
    </div>
  </div>
</section>

<!-- 21 · 3.2 HỌC TẬP -->
<section class="slide paper" id="s-hoctap" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.2 Rèn luyện trong học tập">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Rèn luyện trong học tập</h2>
      <div class="learn">
        <div class="lc tilt rv"><b>1</b><div><h3>Lập sổ tay chính tả cá nhân, sửa lỗi cùng bạn bè</h3><p>Ghi ngay từ hay viết sai, quy tắc dễ nhầm; mỗi tuần lướt xem lại.</p></div></div>
        <div class="lc tilt rv"><b>2</b><div><h3>Thực hành văn bản đặc thù ở đại học</h3><p>Email gửi giảng viên, báo cáo tiểu luận, slide thuyết trình: ngắn gọn, súc tích, không lỗi chính tả.</p></div></div>
        <div class="lc tilt rv"><b>3</b><div><h3>Đọc sách và luyện diễn đạt mỗi ngày</h3><p>Dành 15 đến 30 phút mỗi ngày; ghi lại cấu trúc câu hay, từ ngữ đắt giá để dùng vào bài viết.</p></div></div>
      </div>
    </div>
    <div class="card notebook rv">
      <h3>Sổ tay chính tả của tôi</h3>
      <ul id="nbList"></ul>
      <div class="nbform"><input id="nbA" placeholder="Từ hay viết sai" maxlength="30" autocomplete="off"><span>→</span><input id="nbB" placeholder="Viết đúng" maxlength="30" autocomplete="off"><button class="btn pri" id="nbAdd">Ghi vào sổ</button></div>
      <p class="small mu">Thử ghi một từ bạn hay viết sai: nó sẽ được đóng dấu vào sổ.</p>
    </div>
  </div>
</section>

<!-- 22 · 3.3 GIAO TIẾP PHÙ HỢP -->
<section class="slide paper" id="s-giaotiep" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.3 Giao tiếp phù hợp">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Nói với ai, viết thế ấy</h2>
      <p class="lead rv">Phân biệt không gian giao tiếp thân mật với không gian học tập, công vụ giúp sinh viên biết lựa lời mà nói, dùng từ đúng chỗ, đúng đối tượng.</p>
      <div class="tabs rv" data-tabs="sc"><i class="ink"></i><button class="on" data-t="ban">Nhắn cho bạn</button><button data-t="gv">Gửi giảng viên</button></div>
      <div class="card rv">
        <div class="meter"><span>Mức trang trọng</span><div class="mbar"><i id="meterI"></i></div><b id="meterV">25%</b></div>
        <p id="rule" class="rule"></p>
      </div>
      <div class="row rv"><button class="btn pri" id="formalize">Chỉnh cho trang trọng</button><button class="btn ghost" data-replay="gt">Phát lại cuộc trò chuyện</button></div>
    </div>
    <div class="rv">
      <div class="phone"><div class="screen">
        <div class="ph-top"><span class="av" id="gtAv">B</span><div><b id="gtName">Bạn thân</b><small>đang hoạt động</small></div></div>
        <div class="ph-body chat" id="chat-gt"></div>
        <div class="ph-in"><i>Nhập tin nhắn…</i><span>➤</span></div>
      </div></div>
    </div>
  </div>
</section>

<!-- 23 · 3.4 MẠNG XÃ HỘI -->
<section class="slide paper" id="s-mxh" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.4 Vì sao bắt đầu từ mạng xã hội">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Vì sao bắt đầu từ mạng xã hội?</h2>
      <div class="big79 rv"><b class="cnt" data-to="79" data-suf=" triệu">0</b><span>người dùng mạng xã hội ở Việt Nam (báo cáo Digital 2026), tăng 7,2% so với năm trước</span></div>
      <div class="bars rv" id="mxhBars"></div>
      <p class="foot rv">Số người dùng đầu năm 2024 (triệu); TikTok tính từ 18 tuổi trở lên. Nguồn: We Are Social, Vietnam Digital 2024.</p>
      <p class="mu rv">Với sinh viên, ô bình luận, tin nhắn và chú thích video là nơi chữ Quốc ngữ được gõ nhiều nhất.</p>
    </div>
    <div>
      <div class="card donutcard rv">
        <div class="donut"><svg viewBox="0 0 160 160" id="donut"></svg><div class="dc"><b id="dcV">75,4%</b><small id="dcL">Trung lập</small></div></div>
        <ul class="legend" id="donutLg"></ul>
        <p class="small mu">Thái độ với các biến thể ngôn ngữ của giới trẻ, theo khảo sát của nhóm sinh viên các trường đại học tại TP.HCM.</p>
      </div>
      <div class="twoside rv"><span class="chip g">Mặt sáng tạo: thể hiện sáng tạo và bản sắc nhóm</span><span class="chip">Mặt đáng lo: viết tắt, chêm xen tùy tiện</span></div>
      <blockquote class="note rv">Giữ gìn chữ Quốc ngữ hôm nay vì vậy trước hết là giữ gìn <span class="hl">cách mình gõ chữ mỗi ngày</span>. Đề xuất của nhóm không cấm cái mới, mà giúp sinh viên có tiêu chí để tự lựa chọn.</blockquote>
    </div>
  </div>
</section>

<!-- 24 · BA ĐỀ XUẤT -->
<section class="slide paper" id="s-dexuat" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.4 Ba đề xuất trên mạng xã hội">
  <div class="wrap">
    <h2 class="t rv">Ba đề xuất cho không gian mạng</h2>
    <div class="tabs rv" data-tabs><i class="ink"></i><button class="on" data-t="a">1 · Viết có dấu, kiểm tra chính tả</button><button data-t="b">2 · Ngôn ngữ văn minh</button><button data-t="c">3 · Tạo nội dung có giá trị</button></div>
    <div class="tp on" data-p="a">
      <p class="lead"><b>Vì sao quan trọng:</b> dấu thanh là nét đặc trưng của chữ Quốc ngữ; bỏ dấu dễ khiến người đọc hiểu nhầm nghĩa.</p>
      <div class="how4">
        <div class="hw tilt"><b>1</b>Mặc định gõ đủ dấu ở nơi có người lạ đọc: bài đăng công khai, bình luận dưới bài của trường/khoa, email, nhóm lớp có giảng viên.</div>
        <div class="hw tilt"><b>2</b>Đọc lại một lần trước khi bấm đăng; soát dấu thanh, chữ hoa đầu câu, các cặp dễ nhầm (s/x, ch/tr, d/gi/r, dấu hỏi/ngã).</div>
        <div class="hw tilt"><b>3</b>Dùng kiểm tra chính tả của bàn phím, trình soạn thảo như bước phụ trợ, không thay cho việc tự đọc lại.</div>
        <div class="hw tilt"><b>4</b>Phân biệt hai “phòng”: nhắn riêng với bạn thân thì thoải mái, ra “phòng chung” thì chuyển sang chuẩn. Giữ khả năng chuyển đổi, không ép mọi tin nhắn thành văn bản hành chính.</div>
      </div>
      <div class="row"><button class="btn gold" data-go="s-dang">Thử “Quy tắc 3 câu hỏi” ngay</button></div>
    </div>
    <div class="tp" data-p="b">
      <p class="lead">Sinh viên cần hạn chế ba hành vi. Bấm vào thẻ để xem cách thay thế.</p>
      <div class="fc3">
        <div class="fc" tabindex="0" role="button"><div class="fi"><div class="ff"><small>Hành vi hạn chế</small><h4>Cổ súy cách viết sai lệch</h4><p>Cố tình viết sai chính tả để câu view, đua trend biến dạng chữ.</p><em>Vì sao: người xem, nhất là các bạn nhỏ tuổi, dễ bắt chước.</em></div><div class="fb"><small>Cách thay thế</small><p>Giữ sáng tạo ở cách diễn đạt, không ở việc viết sai chữ; nếu chơi chữ thì đủ dấu để vẫn đọc được.</p></div></div></div>
        <div class="fc" tabindex="0" role="button"><div class="fi"><div class="ff"><small>Hành vi hạn chế</small><h4>Chia sẻ nội dung thiếu kiểm chứng</h4><p>Thông tin sai thường kèm ngôn ngữ giật gân.</p><em>Vì sao: làm xuống cấp cả nội dung lẫn cách dùng từ.</em></div><div class="fb"><small>Cách thay thế</small><p>Kiểm tra 3 điểm trước khi chia sẻ: nguồn là ai, đăng khi nào, có nguồn gốc và đối chiếu được không.</p></div></div></div>
        <div class="fc" tabindex="0" role="button"><div class="fi"><div class="ff"><small>Hành vi hạn chế</small><h4>Dùng từ xúc phạm người khác</h4><p>Lời lẽ nặng nề trong bình luận, tin nhắn.</p><em>Vì sao: ngôn ngữ trên mạng cũng là lời nói nơi công cộng.</em></div><div class="fb"><small>Cách thay thế</small><p>Phản biện vào ý kiến, không vào con người; dùng câu hỏi thay vì chửi.</p></div></div></div>
      </div>
      <p class="mu small">Ghi chú: ngôn ngữ giới trẻ có cả mặt tích cực lẫn tiêu cực, nên tiêu chí là tác động lên người đọc (gây hiểu nhầm, gây tổn thương), không phải “từ nào cũ hay mới”.</p>
    </div>
    <div class="tp" data-p="c">
      <p class="lead">Giữ gìn không chỉ là tránh sai mà còn là tạo ra nội dung tốt để lấp vào dòng thời gian. Video giữ vị trí quan trọng trên TikTok và YouTube, sinh viên có thể thử các định dạng sau.</p>
      <div class="fmts">
        <div class="fmt tilt"><small>Bài viết ngắn</small><h4>“Một chữ – một câu chuyện”</h4><p>Nguồn gốc, nghĩa gốc và cách dùng một từ quen thuộc.</p><span class="chip y">200–300 chữ</span></div>
        <div class="fmt tilt"><small>Video ngắn</small><h4>“Hai cách nói – một ý”</h4><p>So sánh cách nói thường ngày và cách nói trang trọng, cho thấy khi nào dùng cách nào.</p><span class="chip y">30–60 giây</span></div>
        <div class="fmt tilt"><small>Podcast</small><h4>“Nghe chữ”</h4><p>Sinh viên Văn – Báo chí phỏng vấn giảng viên, người làm biên tập, hoặc bạn lưu học sinh học tiếng Việt về những lỗi hay gặp.</p><span class="chip y">8–12 phút/tập</span></div>
        <div class="fmt tilt"><small>Thơ lục bát tương tác</small><h4>Lục bát ngắn</h4><p>Đăng dạng video/ảnh, lấy cảm hứng từ cuộc thi lục bát “Tiếng Việt giàu đẹp” ở Đường Sách TP Thủ Đức (hơn 40 bài dự thi, 8 bài đạt giải).</p><span class="chip y">4 câu</span></div>
        <div class="fmt tilt"><small>Nội dung văn hóa</small><h4>Chuỗi bài văn hóa Việt</h4><p>Bám các mốc như Ngày tôn vinh tiếng Việt và Ngày Văn hóa Việt Nam 24/11.</p><span class="chip y">Theo tuần</span></div>
      </div>
      <div class="tags"><span class="chip g">Đúng chính tả</span><span class="chip g">Nêu nguồn nếu trích tư liệu</span><span class="chip g">Có giá trị cho người xem</span><span class="chip g">Tôn trọng người khác</span></div>
    </div>
  </div>
</section>

<!-- 25 · QUY TẮC 3 CÂU HỎI -->
<section class="slide green" id="s-dang" data-mode="div" data-theme="dark" data-ch="Chương 3" data-title="Quy tắc 3 câu hỏi trước khi đăng">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Quy tắc 3 câu hỏi trước khi bấm Đăng</h2>
      <p class="lead rv">Đề xuất của nhóm: đọc lại một lần và tự hỏi ba câu. Hãy thử với bài đăng bên cạnh, hoặc gõ câu của riêng bạn.</p>
      <ol class="q3 rv">
        <li><b>1</b>Người đọc có hiểu đúng ý mình không?</li>
        <li><b>2</b>Có chỗ nào đổi nghĩa vì thiếu dấu hoặc viết tắt không?</li>
        <li><b>3</b>Nếu lời này được in thành bản tin, mình có ngại không?</li>
      </ol>
    </div>
    <div class="post rv">
      <div class="post-h"><span class="av">B</span><div><b>Bạn</b><small>Công khai</small></div></div>
      <textarea id="draft" rows="3" maxlength="240" spellcheck="false">Mai nộp bài r mà mik chưa làm j hết, toang thiệt 😭</textarea>
      <div class="chat qchat" id="qchat"></div>
      <div class="row"><button class="btn gold" id="postBtn">Đăng</button><button class="btn ghost" id="fixDraft">Sửa giúp mình</button><button class="btn mini ghost" id="resetDraft">Bản nháp ban đầu</button></div>
      <div class="feed" id="feed"></div>
    </div>
  </div>
</section>

<!-- 26 · 3.5 TỰ TỔ CHỨC HOẠT ĐỘNG -->
<section class="slide paper" id="s-hoatdong" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.5 Sinh viên tự tổ chức hoạt động">
  <div class="wrap">
    <h2 class="t rv">Sinh viên tự tổ chức hoạt động</h2>
    <p class="lead rv">Nhiều hoạt động giữ gìn tiếng Việt do cơ quan, tổ chức phát động. Sinh viên có lợi thế riêng: hiểu ngôn ngữ của cộng đồng mình và tự có kênh truyền thông. Lễ hội Chữ Hàn 2024 thu hút hơn 1.000 sinh viên là một ví dụ về tiềm năng ấy.</p>
    <div class="tabs rv" data-tabs><i class="ink"></i><button class="on" data-t="a">Hoạt động 1: Mỗi tuần một lỗi tiếng Việt</button><button data-t="b">Hoạt động 2: Sổ tay lỗi tiếng Việt</button><button data-t="c">Điều kiện để đi vào thực chất</button></div>
    <div class="tp on" data-p="a">
      <dl class="kv">
        <div><dt>Người tham gia</dt><dd>Nhóm 5–7 sinh viên làm ban biên tập (1 trưởng nhóm, 2 sưu tầm lỗi, 2 thiết kế, 1 truyền thông); người xem là sinh viên toàn khoa/trường.</dd></div>
        <div><dt>Thời gian</dt><dd>12 tuần (một học kỳ), đăng vào sáng thứ Hai hằng tuần.</dd></div>
        <div><dt>Cách thực hiện</dt><dd>(1) Mỗi tuần chọn một lỗi phổ biến (nhầm s/x, thiếu dấu, dùng sai từ Hán Việt, câu thiếu chủ ngữ…) lấy từ bài làm, email, bình luận đã ẩn danh. (2) Giải thích ngắn: sai ở đâu, vì sao, cách sửa, mẹo nhớ. (3) Đăng dưới dạng ảnh/video 30 giây trên fanpage, nhóm lớp. (4) Cuối tuần có câu hỏi trắc nghiệm nhanh 3 câu.</dd></div>
        <div><dt>Sản phẩm đầu ra</dt><dd>12 bài đăng (ảnh/video); bộ 36 câu trắc nghiệm; báo cáo cuối kỳ.</dd></div>
        <div><dt>Đánh giá</dt><dd>Đo trước – sau: làm bài kiểm tra 20 câu chính tả ở tuần 1 và tuần 12 trên cùng nhóm sinh viên; thống kê lượt xem, lượt chia sẻ, tỷ lệ trả lời đúng trắc nghiệm hằng tuần. Ghi rõ hạn chế: mẫu nhỏ, không đại diện toàn trường.</dd></div>
      </dl>
      <div class="weeks12" id="weeks12"></div>
    </div>
    <div class="tp" data-p="b">
      <dl class="kv">
        <div><dt>Người tham gia</dt><dd>Ban biên soạn 6–8 sinh viên (ưu tiên có bạn ngành Văn, Báo chí, Ngôn ngữ) và cộng tác viên từ các khoa khác.</dd></div>
        <div><dt>Thời gian</dt><dd>8–10 tuần: 2 tuần thiết kế khung, 5 tuần thu thập – biên soạn, 2 tuần biên tập – phát hành.</dd></div>
        <div><dt>Cách thực hiện</dt><dd>(1) Thống nhất cấu trúc mỗi mục: lỗi sai – cách đúng – giải thích – ví dụ – mẹo nhớ. (2) Lấy tư liệu từ hoạt động 1 và 3, từ bài làm đã ẩn danh. (3) Phân nhóm: chính tả, dấu thanh, dùng từ, câu, ngôn ngữ trên mạng. (4) Kiểm tra chéo từng mục với từ điển/chuẩn chính tả hiện hành và giảng viên góp ý. (5) Phát hành bản điện tử, in nhỏ cho thư viện khoa.</dd></div>
        <div><dt>Sản phẩm đầu ra</dt><dd>Sổ tay 40–60 mục (PDF/in), kèm bản rút gọn dạng ảnh đăng mạng xã hội.</dd></div>
        <div><dt>Đánh giá</dt><dd>Số lượt tải/đọc; khảo sát 30 người dùng về độ dễ hiểu, độ hữu ích; giảng viên rà lại tính chính xác; có kế hoạch cập nhật mỗi học kỳ.</dd></div>
      </dl>
      <div class="gantt" id="gantt"><div style="flex:2"><b>Thiết kế khung</b><small>2 tuần</small></div><div style="flex:5"><b>Thu thập, biên soạn</b><small>5 tuần</small></div><div style="flex:2"><b>Biên tập, phát hành</b><small>2 tuần</small></div></div>
    </div>
    <div class="tp" data-p="c">
      <div class="conds">
        <div class="cd tilt"><b>1</b><p>Xác định mục tiêu đo được từ đầu (ví dụ: 30 người tham gia, giảm 20% lỗi mỗi 100 chữ trong mẫu của nhóm). Chỉ số là mục tiêu tự đặt, không phải kết quả đã đạt.</p></div>
        <div class="cd tilt"><b>2</b><p>Phối hợp với Đoàn – Hội, khoa Ngữ văn/Báo chí, thư viện để có địa điểm, cố vấn, phần thưởng nhỏ.</p></div>
        <div class="cd tilt"><b>3</b><p>Chạy thử nhỏ trong một lớp trước khi mở rộng.</p></div>
        <div class="cd tilt"><b>4</b><p>Tránh biến hoạt động thành phong trào “bắt lỗi”: dùng giọng khích lệ, ẩn danh, không chế giễu.</p></div>
        <div class="cd tilt"><b>5</b><p>Tránh cực đoan “thuần Việt”: mục tiêu là dùng có ý thức, không loại bỏ mọi từ ngoại ngữ.</p></div>
        <div class="cd tilt"><b>6</b><p>Duy trì: gắn với mốc 24/11 để tổng kết hằng năm.</p></div>
      </div>
    </div>
  </div>
</section>

<!-- 27 · 3.6 SINH VIÊN NGOẠI NGỮ -->
<section class="slide paper" id="s-ngoaingu" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.6 Lợi thế của sinh viên ngoại ngữ">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Lợi thế của sinh viên ngoại ngữ</h2>
      <div class="chat" id="chat-nn"></div>
      <div class="tags rv"><span class="chip">Sản phẩm song ngữ</span><span class="chip g">Lớp tiếng Việt cho sinh viên quốc tế</span><span class="chip y">Câu lạc bộ trao đổi ngôn ngữ</span></div>
    </div>
    <div>
      <div class="rowh rv"><h3 class="sm-h">Văn hóa Huế bằng hai ngôn ngữ</h3><div class="tabs" data-tabs="lang"><i class="ink"></i><button class="on" data-t="vi">Tiếng Việt</button><button data-t="en">English</button></div></div>
      <div class="bil rv" id="bil"></div>
      <div class="card hue rv">
        <p><b>Huế là “giáo trình sống”.</b> Nhã nhạc là di sản phi vật thể đầu tiên của Việt Nam được UNESCO ghi danh (11/2003). Huế là địa phương duy nhất của Việt Nam có 8 di sản được UNESCO công nhận.</p>
        <div class="dots8" id="dots8"></div>
        <p class="small mu">Di sản phi vật thể chỉ được giữ gìn khi truyền qua các thế hệ, nên video song ngữ của sinh viên chính là một mắt xích truyền thừa.</p>
      </div>
    </div>
  </div>
</section>

<!-- 28 · 3.7 CÔNG NGHỆ -->
<section class="slide paper" id="s-congnghe" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.7 Ứng dụng công nghệ">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Ứng dụng công nghệ</h2>
      <div class="tech">
        <div class="tc tilt rv"><b>1</b><div><h3>Công cụ hỗ trợ để kiểm tra, chuẩn hóa văn bản</h3><p>Dùng kiểm tra chính tả, dấu câu, định dạng của phần mềm văn phòng và từ điển trực tuyến uy tín; tập thói quen chạy công cụ rà soát lỗi trước khi nộp bài lớn, tiểu luận, đồ án.</p></div></div>
        <div class="tc tilt rv"><b>2</b><div><h3>Sân chơi trực tuyến, thư viện số học tập</h3><p>Trò chơi nhỏ kiểm tra chính tả; thư viện chung gồm mẫu email chuẩn, sổ tay chính tả điện tử, video ngắn hướng dẫn dùng từ.</p></div></div>
        <div class="tc tilt rv"><b>3</b><div><h3>Tư duy phản biện và ý thức kiểm chứng</h3><p>Phần mềm hay AI chỉ hỗ trợ, không thay thế tư duy, cảm xúc và sự nhạy cảm ngôn ngữ của con người. Nhận gợi ý xong, luôn tự đọc lại toàn bộ văn bản.</p></div></div>
      </div>
    </div>
    <div class="card quiz rv" id="quiz"></div>
  </div>
</section>

<!-- 29 · 3.8 21 NGÀY VIẾT RÕ -->
<section class="slide paper" id="s-21ngay" data-mode="paper" data-theme="paper" data-ch="Chương 3" data-title="3.8 Mô hình “21 ngày viết rõ”">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Mô hình “21 ngày viết rõ”</h2>
      <ol class="weeks rv">
        <li><b>Tuần 1</b><span>Nhận diện lỗi trong email, bài tập và bài đăng cá nhân.</span></li>
        <li><b>Tuần 2</b><span>Luyện viết và sửa chéo theo tiêu chí chính tả, dùng từ, câu và phong cách.</span></li>
        <li><b>Tuần 3</b><span>Mỗi cá nhân hoặc nhóm tạo một bài viết, video, trang sổ tay hoặc sản phẩm song ngữ.</span></li>
      </ol>
      <p class="mu rv">Hiệu quả được đánh giá bằng bài kiểm tra trước – sau và số lỗi trên 100 chữ.</p>
      <div class="row rv"><button class="btn pri" id="play21">Chạy thử 21 ngày</button><button class="btn ghost" id="reset21">Làm lại</button></div>
    </div>
    <div class="cal rv">
      <div class="calring"><svg viewBox="0 0 120 120"><circle class="gb" cx="60" cy="60" r="50"/><circle class="gf" id="ring21" cx="60" cy="60" r="50" transform="rotate(-90 60 60)"/></svg><div><b id="d21">0</b><small>/ 21 ngày</small></div></div>
      <div class="days" id="days"></div>
      <p class="small mu" id="dayInfo">Di chuột vào một ngày; bấm để đánh dấu đã hoàn thành.</p>
    </div>
  </div>
</section>

<!-- 30 · 3.9 ĐIỀU KIỆN HỖ TRỢ -->
<section class="slide green" id="s-hotro" data-mode="div" data-theme="dark" data-ch="Chương 3" data-title="3.9 Điều kiện hỗ trợ">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Điều kiện hỗ trợ</h2>
      <p class="lead rv">Sinh viên là chủ thể lên ý tưởng, phân công và thực hiện. Giảng viên góp ý chuyên môn; lớp, khoa hoặc câu lạc bộ hỗ trợ không gian và truyền thông khi cần.</p>
      <div class="card rv" id="orbInfo"><h3>Chạm vào một vệ tinh</h3><p>Mỗi bên đóng một vai trò riêng quanh sinh viên.</p></div>
      <p class="mu rv">Sự hỗ trợ này không thay thế trách nhiệm chuẩn bị nội dung và đánh giá kết quả của sinh viên.</p>
    </div>
    <div class="orbit rv" id="orbit"></div>
  </div>
</section>

<!-- 31 · KẾT LUẬN -->
<section class="slide red dv" id="s-ketluan" data-mode="div" data-theme="dark" data-ch="Kết luận" data-title="Kết luận">
  <div class="wrap g2">
    <div>
      <h2 class="t rv">Kết luận</h2>
      <p class="bigq rv">Chính cách viết hằng ngày của sinh viên sẽ quyết định chữ Quốc ngữ được sử dụng <span class="hl">cẩn trọng, rõ ràng và có trách nhiệm</span> đến mức nào.</p>
      <div class="row rv"><button class="btn mini ghost" data-replay="kl">Phát lại</button></div>
    </div>
    <div class="chat klchat" id="chat-kl"></div>
  </div>
</section>

<!-- 32 · TÀI LIỆU THAM KHẢO -->
<section class="slide paper" id="s-tailieu" data-mode="paper" data-theme="paper" data-ch="Kết luận" data-title="Tài liệu tham khảo">
  <div class="wrap">
    <h2 class="t rv">Tài liệu tham khảo</h2>
    <input id="refQ" class="refq rv" placeholder="Gõ để lọc tài liệu: Báo, ĐHQG, Digital…" autocomplete="off" aria-label="Lọc tài liệu tham khảo">
    <ol class="refs" id="refs"></ol>
  </div>
</section>

<!-- 33 · CẢM ƠN -->
<section class="slide red dv" id="s-camon" data-mode="hero" data-theme="dark" data-ch="Kết thúc" data-title="Cảm ơn">
  <div class="drumbox"><div class="drum" data-drum></div></div>
  <div class="wrap hero">
    <h2 class="thanks rv">Cảm ơn thầy cô và các bạn đã lắng nghe</h2>
    <p class="sub rv">Giữ gìn chữ Quốc ngữ bắt đầu từ cách ta viết mỗi ngày.</p>
    <div class="row rv"><button class="btn gold mag" id="fireBtn">Bắn pháo hoa</button><button class="btn ghost mag" data-go="s-hero">Về trang bìa</button></div>
    <div class="chat qa rv"><div class="msg"><span class="av">?</span><div class="bub">Thầy cô và các bạn có câu hỏi nào cho nhóm không ạ?</div></div></div>
  </div>
</section>

</div><!-- /deck -->

<canvas id="fx"></canvas>
<div id="prog"><i></i></div>
<div id="hud">
  <button class="hb" id="bMenu">Mục lục</button><span id="chap"></span><span class="sp0"></span>
  <button class="hb" id="bSnd">Âm thanh: tắt</button><button class="hb" id="bLaser">Bút laser</button><button class="hb" id="bFs">Toàn màn hình</button>
</div>
<div id="nav">
  <button class="nb" id="bPrev" aria-label="Slide trước"><svg viewBox="0 0 24 24"><path d="M15 5l-7 7 7 7"/></svg></button>
  <span id="ctr">01 / 33</span>
  <button class="nb" id="bNext" aria-label="Slide sau"><svg viewBox="0 0 24 24"><path d="M9 5l7 7-7 7"/></svg></button>
</div>
<div id="menu"><h3>Mục lục</h3><div id="menuList"></div></div>
<button class="hb" id="mclose">Đóng (Esc)</button>
<div id="toast" role="status"></div>
<div id="cur"></div>
<script>
(()=>{
'use strict';
/* ================= tiện ích ================= */
const $=(s,r=document)=>r.querySelector(s),$$=(s,r=document)=>Array.from(r.querySelectorAll(s));
const sleep=ms=>new Promise(r=>setTimeout(r,ms));
const pick=a=>a[Math.random()*a.length|0];
const rnd=(a,b)=>a+Math.random()*(b-a);
const clamp=(v,a,b)=>Math.min(b,Math.max(a,v));
const fmt=(n,d=0)=>n.toFixed(d).replace('.',',');
const esc=s=>String(s).replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]));
const RM=matchMedia('(prefers-reduced-motion: reduce)').matches;
const TOUCH=matchMedia('(pointer: coarse)').matches;
const store={get(k){try{return localStorage.getItem(k)}catch(e){return null}},set(k,v){try{localStorage.setItem(k,v)}catch(e){}}};
const GOLD=['#F5B700','#FFD95A','#FFF3B0','#E8A100'],MIX=['#F5B700','#FFD95A','#C1121F','#E23A2B','#FBF0D2','#79B58A'];
let mx=-999,my=-999;

/* ================= âm thanh (WebAudio, mặc định tắt) ================= */
const sfx=(()=>{let ctx=null,on=false;
 const ac=()=>ctx||(ctx=new(window.AudioContext||window.webkitAudioContext)());
 const tone=(f,d=.12,t='sine',v=.07,f2)=>{if(!on)return;try{const a=ac(),o=a.createOscillator(),g=a.createGain(),n=a.currentTime;o.type=t;o.frequency.setValueAtTime(f,n);if(f2)o.frequency.exponentialRampToValueAtTime(f2,n+d);g.gain.setValueAtTime(v,n);g.gain.exponentialRampToValueAtTime(.0001,n+d);o.connect(g);g.connect(a.destination);o.start(n);o.stop(n+d)}catch(e){}};
 return{
  toggle(){on=!on;if(on){try{ac().resume()}catch(e){}}return on},
  pop:()=>tone(480,.09,'sine',.08,900),
  ok:()=>{tone(660,.1,'triangle');setTimeout(()=>tone(990,.14,'triangle'),90)},
  bad:()=>tone(170,.22,'sawtooth',.05,90),
  whoosh:()=>tone(320,.35,'sine',.04,80),
  boom:()=>tone(130,.45,'triangle',.1,40),
  tick:()=>tone(1200,.04,'square',.03)}})();

/* ================= hạt: sao vàng, cánh hoa, tim, pháo hoa ================= */
const fx=(()=>{
 const c=$('#fx'),x=c.getContext('2d');let W=0,H=0,ps=[],run=false,dpr=1;
 const rs=()=>{dpr=Math.min(devicePixelRatio||1,2);W=c.width=innerWidth*dpr;H=c.height=innerHeight*dpr};
 addEventListener('resize',rs);rs();
 const star=(r,rot)=>{x.beginPath();for(let i=0;i<10;i++){const rr=i%2?r*.45:r,a=rot+i*Math.PI/5-Math.PI/2;x.lineTo(Math.cos(a)*rr,Math.sin(a)*rr)}x.closePath()};
 function loop(){
  x.setTransform(1,0,0,1,0,0);x.clearRect(0,0,W,H);
  for(let i=ps.length-1;i>=0;i--){const p=ps[i];
   p.vy+=p.g;p.vx*=p.fr;p.vy*=p.fr;p.x+=p.vx;p.y+=p.vy;p.rot+=p.vr;p.life-=p.dec;
   if(p.life<=0||p.y>innerHeight+60){ps.splice(i,1);continue}
   x.setTransform(dpr,0,0,dpr,p.x*dpr,p.y*dpr);x.rotate(p.rot);x.globalAlpha=clamp(p.life*1.6,0,1);x.fillStyle=p.col;
   if(p.k==='star'){star(p.r,0);x.fill()}
   else if(p.k==='petal'){x.beginPath();x.ellipse(0,0,p.r*.5,p.r,0,0,7);x.fill()}
   else if(p.k==='heart'){x.font=`${p.r*2}px serif`;x.textAlign='center';x.fillText('♥',0,0)}
   else{x.shadowColor=p.col;x.shadowBlur=10;x.beginPath();x.arc(0,0,p.r*.5,0,7);x.fill();x.shadowBlur=0}
  }
  if(ps.length)requestAnimationFrame(loop);else{run=false;x.setTransform(1,0,0,1,0,0);x.clearRect(0,0,W,H)}
 }
 const add=p=>{if(ps.length>700)ps.shift();ps.push(p);if(!run){run=true;requestAnimationFrame(loop)}};
 const api={
  burst(px,py,n=18,o={}){if(RM)n=Math.min(n,5);for(let i=0;i<n;i++){const a=rnd(0,6.283),s=(o.sp||6)*rnd(.35,1);add({x:px,y:py,vx:Math.cos(a)*s,vy:Math.sin(a)*s-(o.up??2),g:o.g??.16,fr:o.fr||.985,life:1,dec:o.dec||rnd(.012,.024),r:(o.r||8)*rnd(.6,1.3),rot:rnd(0,6),vr:rnd(-.2,.2),k:o.k||pick(['star','star','petal']),col:pick(o.cols||MIX)})}},
  trail(px,py,col){add({x:px,y:py,vx:rnd(-.4,.4),vy:rnd(-.6,.2),g:.01,fr:.96,life:1,dec:.05,r:rnd(3,7),rot:0,vr:0,k:'spark',col})},
  heart(px,py){add({x:px,y:py,vx:rnd(-.8,.8),vy:rnd(-3.2,-2),g:-.01,fr:.99,life:1,dec:.014,r:rnd(9,16),rot:rnd(-.3,.3),vr:0,k:'heart',col:pick(['#E23A2B','#FF5A6E','#C1121F'])})},
  fire(n=6){for(let i=0;i<n;i++)setTimeout(()=>{const px=rnd(innerWidth*.15,innerWidth*.85),py=rnd(innerHeight*.12,innerHeight*.5);sfx.boom();api.burst(px,py,70,{k:'spark',sp:8,g:.08,fr:.975,dec:.012,r:6,cols:MIX,up:0})},i*420)},
  confetti(){for(let i=0;i<5;i++)setTimeout(()=>api.burst(innerWidth*(.1+.2*i),innerHeight*.92,22,{sp:13,up:10,g:.22,r:9}),i*120)}
 };
 return api})();

const toast=(()=>{let t;const el=$('#toast');return m=>{el.textContent=m;el.classList.add('on');clearTimeout(t);t=setTimeout(()=>el.classList.remove('on'),2800)}})();

/* ================= con trỏ phát sáng, vệt sao, tham số parallax ================= */
const cur=$('#cur');let cx=-999,cy=-999,lx=0,ly=0;
if(TOUCH)cur.style.display='none';
addEventListener('pointermove',e=>{
 mx=e.clientX;my=e.clientY;
 const rt=document.documentElement.style;
 rt.setProperty('--mx',((mx/innerWidth-.5)*2).toFixed(3));rt.setProperty('--my',((my/innerHeight-.5)*2).toFixed(3));
 if(e.pointerType==='touch')return;
 if(cx<-900){cx=mx;cy=my}
 cur.classList.add('vis');
 if(Math.hypot(mx-lx,my-ly)>16&&!RM){lx=mx;ly=my;fx.trail(mx,my,document.body.classList.contains('laser')?'#ff3b3b':pick(GOLD))}
 cur.classList.toggle('h',!!(e.target.closest&&e.target.closest('button,a,[role=button],[tabindex],input,textarea')));
},{passive:true});
document.addEventListener('pointerleave',()=>cur.classList.remove('vis'));
(function loop(){cx+=(mx-cx)*.24;cy+=(my-cy)*.24;cur.style.transform=`translate(${cx}px,${cy}px)`;requestAnimationFrame(loop)})();

/* ================= mưa chữ có dấu (canvas) ================= */
const rain=(()=>{
 if(RM)return{setMode(){}};
 const c=$('#rain'),x=c.getContext('2d');let W,H,dpr=1,ps=[],mode='hero',alpha=.5,tgt=.5;
 const CH='aăâbcdđeêghiklmnoôơpqrstuưvxyáàảãạấầẩẫậắằẳẵặéèẻẽẹếềểễệíìỉĩịóòỏõọốồổỗộớờởỡợúùủũụứừửữựýỳỷỹỵ'.split('');
 const P={hero:{n:62,a:.6,cols:['#F5B700','#FFD95A','#FBF0D2']},div:{n:36,a:.4,cols:['#F5B700','#FFD95A','#FBF0D2']},paper:{n:12,a:.17,cols:['#C1121F','#2E6B4E','#B98500']}};
 const rs=()=>{dpr=Math.min(devicePixelRatio||1,2);W=innerWidth;H=innerHeight;c.width=W*dpr;c.height=H*dpr};
 addEventListener('resize',rs);rs();
 const spawn=init=>ps.push({x:rnd(0,W),y:init?rnd(-H,H):rnd(-60,-10),vy:rnd(.6,1.7),vx:rnd(-.15,.15),ch:pick(CH),sz:rnd(16,42),rot:rnd(-.5,.5),vr:rnd(-.01,.01),col:pick(P[mode].cols),ph:rnd(0,6.28)});
 (function loop(){
  x.setTransform(dpr,0,0,dpr,0,0);x.clearRect(0,0,W,H);
  alpha+=(tgt-alpha)*.04;x.globalAlpha=alpha;
  const n=P[mode].n;
  if(ps.length<n&&Math.random()<.5)spawn(false);
  for(let i=ps.length-1;i>=0;i--){const p=ps[i];
   p.y+=p.vy;p.x+=p.vx+Math.sin(p.ph+p.y*.012)*.35;p.rot+=p.vr;
   const dx=p.x-mx,dy=p.y-my,d=Math.hypot(dx,dy);
   if(d<120&&d>1){p.x+=dx/d*(120-d)*.07;p.y+=dy/d*(120-d)*.03}
   if(p.y>H+50||(ps.length>n+8&&Math.random()<.02)){ps.splice(i,1);continue}
   x.save();x.translate(p.x,p.y);x.rotate(p.rot);x.fillStyle=p.col;x.font=`700 ${p.sz}px Fraunces,Georgia,serif`;x.textAlign='center';x.fillText(p.ch,0,0);x.restore();
  }
  requestAnimationFrame(loop)})();
 for(let i=0;i<40;i++)spawn(true);
 return{setMode(m){mode=P[m]?m:'paper';tgt=P[mode].a;ps.forEach(p=>p.col=pick(P[mode].cols))}}})();

/* ================= núi đồi, trống đồng, đèn lồng ================= */
const mulberry=a=>()=>{a|=0;a=a+0x6D2B79F5|0;let t=Math.imul(a^a>>>15,1|a);t=t+Math.imul(t^t>>>7,61|t)^t;return((t^t>>>14)>>>0)/4294967296};
function ridge(seed,base,amp){
 const r=mulberry(seed),n=10,p=[];
 for(let i=0;i<=n;i++)p.push([i*1440/n,base-r()*amp]);
 let d=`M0 400 L0 ${p[0][1].toFixed(1)}`;
 for(let i=1;i<p.length;i++){const a=p[i-1],b=p[i];d+=` Q${a[0].toFixed(1)} ${a[1].toFixed(1)} ${((a[0]+b[0])/2).toFixed(1)} ${((a[1]+b[1])/2).toFixed(1)}`}
 return d+` L1440 ${p[n][1].toFixed(1)} L1440 400Z`}
function scenery(s,i){
 const d=document.createElement('div');d.className='scn';
 d.innerHTML=[1,2,3].map(k=>`<svg class="l l${k}" viewBox="0 0 1440 320" preserveAspectRatio="none" aria-hidden="true"><path d="${ridge(i*7+k*13+3,[110,165,225][k-1],[110,90,70][k-1])}"/></svg>`).join('');
 s.prepend(d)}
function lanterns(s,list){list.forEach(([x,h,dl])=>{const l=document.createElement('div');l.className='lan';l.style.cssText=`left:${x}%;--h:${h}px;animation-delay:${dl}s`;l.innerHTML='<i></i><b></b>';s.append(l)})}
function buildDrum(el){
 const c=(r,sw)=>`<circle r="${r}"${sw?` style="stroke-width:${sw}"`:''}/>`;
 const P=(n,r1,r2,rot=0)=>{let d='';for(let i=0;i<n*2;i++){const r=i%2?r2:r1,a=rot+i*Math.PI/n-Math.PI/2;d+=(i?'L':'M')+(Math.cos(a)*r).toFixed(1)+' '+(Math.sin(a)*r).toFixed(1)}return d+'Z'};
 const rep=(n,fn)=>Array.from({length:n},(_,i)=>fn(i*360/n)).join('');
 const V='viewBox="-300 -300 600 600"';
 el.innerHTML=
  `<svg class="a1" ${V}><path class="f" d="${P(14,96,36)}"/>${c(104)}${c(112)}<circle class="f" r="20"/></svg>`+
  `<svg class="a2" ${V}>${c(120)}${rep(28,a=>`<path class="f" d="M0 -150 L8 -128 L-8 -128Z" transform="rotate(${a})"/>`)}${c(156)}</svg>`+
  `<svg class="a3" ${V}>${c(166)}${rep(56,a=>`<circle class="f" cx="0" cy="-178" r="2.6" transform="rotate(${a})"/>`)}${c(190)}</svg>`+
  `<svg class="a4" ${V}>${rep(18,a=>`<path d="M0 -236 Q11 -216 0 -194 Q-11 -216 0 -236Z" transform="rotate(${a})"/>`)}${c(198)}${c(244)}</svg>`+
  `<svg class="a5" ${V}><path d="${P(72,262,250)}"/>${c(250)}</svg>`+
  `<svg class="a6" ${V}>${rep(120,a=>`<path d="M0 -282 L0 -272" transform="rotate(${a})"/>`)}${c(290,2.4)}${c(298)}</svg>`}

/* ================= quản lý slide: vết mực loang ================= */
const S=$$('.slide'),N=S.length;let cur0=-1;
const hooks={},leaves={},resets={};
const on=(id,fn,rs)=>{(hooks[id]=hooks[id]||[]).push(fn);if(rs)(resets[id]=resets[id]||[]).push(rs)};
const onLeave=(id,fn)=>{(leaves[id]=leaves[id]||[]).push(fn)};
const T=[];const later=(f,ms)=>{const t=setTimeout(f,ms);T.push(t);return t};
const clearT=()=>T.splice(0).forEach(clearTimeout);

function counters(s){$$('.cnt',s).forEach(e=>{const to=+e.dataset.to,dec=+e.dataset.dec||0,suf=e.dataset.suf||'',t0=performance.now(),dur=1500;cancelAnimationFrame(e._r);const f=t=>{const k=clamp((t-t0)/dur,0,1),v=to*(1-Math.pow(1-k,3));e.textContent=fmt(v,dec)+suf;if(k<1)e._r=requestAnimationFrame(f)};e._r=requestAnimationFrame(f)})}
const gaugesIn=s=>$$('.gf[data-v]',s).forEach(c=>{c.style.strokeDashoffset=(+c.dataset.c)*(1-(+c.dataset.v)/100)});
const barsIn=s=>$$('.bf[data-w]',s).forEach(b=>{b.style.width=b.dataset.w+'%'});
function reset(i){const s=S[i];$$('.cnt',s).forEach(e=>{cancelAnimationFrame(e._r);e.textContent='0'+(e.dataset.suf||'')});$$('.gf[data-v]',s).forEach(c=>{c.style.strokeDashoffset=c.dataset.c});$$('.bf[data-w]',s).forEach(b=>{b.style.width='0'});(resets[s.id]||[]).forEach(f=>f(s))}
function leave(i){clearT();const s=S[i];$$('.chat',s).forEach(b=>{b._tk=(b._tk||0)+1});(leaves[s.id]||[]).forEach(f=>f(s));setTimeout(()=>{if(i!==cur0)reset(i)},1250)}
function enter(i){
 const s=S[i];s.scrollTop=0;
 document.body.dataset.theme=s.dataset.theme||'paper';document.body.dataset.mode=s.dataset.mode||'paper';
 rain.setMode(s.dataset.mode==='hero'?'hero':s.dataset.mode==='div'?'div':'paper');
 $('#chap').textContent=s.dataset.ch||'';$('#ctr').textContent=String(i+1).padStart(2,'0')+' / '+N;
 $('#prog i').style.width=(i/(N-1)*100)+'%';
 $$('.rv',s).forEach((e,k)=>e.style.setProperty('--i',Math.min(k,16)));
 later(()=>{counters(s);gaugesIn(s);barsIn(s)},560);
 $$('[data-tabs]',s).forEach(t=>t._set&&setTimeout(t._set,80));
 (hooks[s.id]||[]).forEach(f=>f(s));
 try{history.replaceState(null,'','#'+s.id)}catch(e){}
}
function go(i,e){
 i=clamp(i,0,N-1);if(i===cur0)return;
 const fwd=i>cur0,from=S[cur0],to=S[i],pi=cur0;
 let ox='50%',oy='50%';
 if(pi>=0){if(e&&e.detail>0&&e.clientX!=null){ox=e.clientX+'px';oy=e.clientY+'px'}else{ox=fwd?'94%':'6%';oy='92%'}}
 to.style.setProperty('--cx',ox);to.style.setProperty('--cy',oy);
 S.forEach(s=>{if(s!==from&&s!==to)s.classList.remove('active','prev')});
 if(from){from.classList.remove('active');from.classList.add('prev')}
 to.classList.remove('prev');to.classList.add('active');
 cur0=i;
 if(pi>=0){leave(pi);sfx.whoosh()}
 enter(i);
 setTimeout(()=>{if(pi>=0&&pi!==cur0)S[pi].classList.remove('prev')},1150);
}
const next=e=>go(cur0+1,e),prev=e=>go(cur0-1,e);

/* ================= mục lục, bút laser, âm thanh, toàn màn hình ================= */
function buildMenu(){
 const g={};S.forEach((s,i)=>{(g[s.dataset.ch]=g[s.dataset.ch]||[]).push(i)});
 $('#menuList').innerHTML=Object.entries(g).map(([n,ids])=>`<div class="mg"><h4>${esc(n)}</h4><div>${ids.map(i=>`<button class="mi" style="--k:${i}" data-i="${i}"><small>${String(i+1).padStart(2,'0')}</small>${esc(S[i].dataset.title)}</button>`).join('')}</div></div>`).join('')}
const menu=$('#menu');
const openMenu=()=>{$$('.mi').forEach(b=>b.classList.toggle('cur',+b.dataset.i===cur0));menu.classList.add('on')};
const closeMenu=()=>menu.classList.remove('on');
const toggleMenu=()=>menu.classList.contains('on')?closeMenu():openMenu();
function laser(){const on=document.body.classList.toggle('laser');$('#bLaser').classList.toggle('on',on);toast(on?'Bút laser bật: di chuột để chỉ. Bấm L để tắt':'Đã tắt bút laser')}
function snd(){const on=sfx.toggle();const b=$('#bSnd');b.textContent='Âm thanh: '+(on?'bật':'tắt');b.classList.toggle('on',on);if(on)sfx.ok()}
function fs(){try{const d=document,el=d.documentElement;if(!d.fullscreenElement){const f=el.requestFullscreen||el.webkitRequestFullscreen;const p=f&&f.call(el);if(p&&p.catch)p.catch(()=>toast('Khung này chặn toàn màn hình. Hãy mở trang ở tab riêng.'))}else d.exitFullscreen()}catch(e){toast('Khung này chặn toàn màn hình. Hãy mở trang ở tab riêng.')}}

$('#bMenu').addEventListener('click',toggleMenu);
$('#mclose').addEventListener('click',closeMenu);
$('#bPrev').addEventListener('click',prev);$('#bNext').addEventListener('click',next);
$('#bSnd').addEventListener('click',snd);$('#bLaser').addEventListener('click',laser);$('#bFs').addEventListener('click',fs);

document.addEventListener('click',e=>{
 const t=e.target;
 if(!t.closest)return;
 const g=t.closest('[data-go]');if(g){const k=S.findIndex(s=>s.id===g.dataset.go);if(k>=0)go(k,e);return}
 if(t.closest('[data-next]')){next(e);return}
 if(t.closest('[data-menu]')){openMenu();return}
 const mi=t.closest('.mi');if(mi){closeMenu();go(+mi.dataset.i,e);return}
 const b=t.closest('.btn,.hb,.nb');
 if(b){const r=b.getBoundingClientRect(),d=Math.max(r.width,r.height)*2,k=e.detail>0,sp=document.createElement('span');sp.className='rip';sp.style.cssText=`width:${d}px;height:${d}px;left:${(k?e.clientX-r.left:r.width/2)-d/2}px;top:${(k?e.clientY-r.top:r.height/2)-d/2}px`;b.append(sp);setTimeout(()=>sp.remove(),700)}
 if(e.detail>0&&!document.body.classList.contains('laser')&&!t.closest('input,textarea,#menu'))fx.burst(e.clientX,e.clientY,8,{sp:4,r:6});
});

/* ================= bàn phím, cuộn chuột, vuốt ================= */
addEventListener('keydown',e=>{
 const t=e.target,k=e.key;
 if(k==='Escape'){closeMenu();return}
 if(t.closest&&t.closest('input,textarea,select,[contenteditable="true"]'))return;
 if(e.ctrlKey||e.metaKey||e.altKey)return;
 if((k==='Enter'||k===' ')&&t.matches&&t.matches('[tabindex]:not(button):not(body)')){e.preventDefault();t.click();return}
 if((k==='Enter'||k===' ')&&t.closest&&t.closest('button'))return;
 const s=S[cur0],scrollable=s.scrollHeight>s.clientHeight+6;
 if(k==='ArrowDown'&&scrollable&&s.scrollTop+s.clientHeight<s.scrollHeight-4)return;
 if(k==='ArrowUp'&&scrollable&&s.scrollTop>4)return;
 if(['ArrowRight','ArrowDown','PageDown',' '].includes(k)){e.preventDefault();next()}
 else if(['ArrowLeft','ArrowUp','PageUp','Backspace'].includes(k)){e.preventDefault();prev()}
 else if(k==='Home')go(0);else if(k==='End')go(N-1);
 else if(k==='f'||k==='F')fs();else if(k==='l'||k==='L')laser();else if(k==='m'||k==='M')toggleMenu();else if(k==='s'||k==='S')snd();
});
let wLast=0;
const canScroll=(el,dy)=>{for(;el&&el!==document.body;el=el.parentElement){const o=getComputedStyle(el).overflowY;if((o==='auto'||o==='scroll')&&el.scrollHeight>el.clientHeight+3){if(dy>0&&el.scrollTop+el.clientHeight<el.scrollHeight-3)return true;if(dy<0&&el.scrollTop>3)return true}}return false};
addEventListener('wheel',e=>{
 const now=performance.now(),gap=now-wLast;wLast=now;
 if(menu.classList.contains('on')||gap<220||Math.abs(e.deltaY)<18)return;
 if(canScroll(e.target,e.deltaY))return;
 if(e.deltaY>0)next();else prev();
},{passive:true});
let tx=0,ty=0,tt=0,tok=false;
addEventListener('touchstart',e=>{const p=e.touches[0];tx=p.clientX;ty=p.clientY;tt=Date.now();tok=!e.target.closest('input,textarea,[data-noswipe],.ripchat,.klchat,.tl,#nbList,.ph-body,#menu')},{passive:true});
addEventListener('touchend',e=>{if(!tok)return;const p=e.changedTouches[0],dx=p.clientX-tx,dy=p.clientY-ty;if(Math.abs(dx)>70&&Math.abs(dx)>Math.abs(dy)*1.6&&Date.now()-tt<700){if(dx<0)next();else prev()}},{passive:true});

/* ================= nghiêng 3D, nút từ tính ================= */
let tl=null;
addEventListener('pointermove',e=>{
 if(e.pointerType==='touch')return;
 const t=e.target.closest&&e.target.closest('.tilt');
 if(tl&&tl!==t){tl.style.setProperty('--rx','0deg');tl.style.setProperty('--ry','0deg');tl=null}
 if(t){tl=t;const r=t.getBoundingClientRect(),px=(e.clientX-r.left)/r.width,py=(e.clientY-r.top)/r.height;
  t.style.setProperty('--ry',((px-.5)*12).toFixed(2)+'deg');t.style.setProperty('--rx',((.5-py)*12).toFixed(2)+'deg');
  t.style.setProperty('--gx',(px*100).toFixed(1)+'%');t.style.setProperty('--gy',(py*100).toFixed(1)+'%')}
 const s=S[cur0];if(!s)return;
 $$('.mag',s).forEach(b=>{const r=b.getBoundingClientRect(),dx=e.clientX-(r.left+r.width/2),dy=e.clientY-(r.top+r.height/2);b.style.transform=Math.hypot(dx,dy)<120?`translate(${(dx*.2).toFixed(1)}px,${(dy*.28).toFixed(1)}px)`:''});
},{passive:true});

/* ================= hộp thoại tin nhắn nhảy ra ================= */
const mkw=t=>esc(t).replace(/\{([^|}]+)\|([^}]+)\}/g,(m,a,b)=>`<span class="w" data-fix="${b}" tabindex="0" role="button">${a}</span>`);
const msgEl=m=>{
 const d=document.createElement('div');d.className='msg'+(m.me?' me':'')+(m.sys?' sys':'');
 const av=m.sys?'':`<span class="av"${m.c?` style="background:${m.c}"`:''}>${esc((m.av||m.n||'T').slice(0,2))}</span>`;
 d.innerHTML=av+`<div class="bub">${m.n&&!m.me&&!m.sys?`<small class="nm">${esc(m.n)}</small>`:''}${m.raw?m.t:mkw(m.t)}</div>`;
 return d};
const countFix=script=>script.reduce((n,m)=>n+((m.t||'').match(/\{[^|}]+\|[^}]+\}/g)||[]).length,0);
function updFix(box){
 if(box.dataset.cnt){const el=$(box.dataset.cnt);if(el)el.textContent=$$('.w.ok',box).length+'/'+(box._tot||0)}
 box.dispatchEvent(new CustomEvent('fix'))}
async function playChat(box,script){
 if(!box)return;
 const tk=box._tk=(box._tk||0)+1;box.innerHTML='';box._tot=countFix(script);updFix(box);
 for(const m of script){
  if(box._tk!==tk)return;
  if(!m.sys&&m.d!==0){
   const ty=document.createElement('div');ty.className='msg typing'+(m.me?' me':'');
   ty.innerHTML=`${m.me?'':'<span class="av">·</span>'}<div class="bub"><span class="dots"><i></i><i></i><i></i></span></div>`;
   box.append(ty);box.scrollTop=box.scrollHeight;await sleep(m.d||750);
   if(box._tk!==tk)return;ty.remove();
  }else await sleep(260);
  if(box._tk!==tk)return;
  box.append(msgEl(m));sfx.pop();box.scrollTop=box.scrollHeight;updFix(box);
  await sleep(m.w||330);
 }
}
function fixWord(w){
 if(w.classList.contains('ok'))return;
 w.animate([{transform:'rotateX(0)'},{transform:'rotateX(90deg)'}],{duration:150});
 setTimeout(()=>{w.textContent=w.dataset.fix;w.classList.add('ok');const b=w.closest('.chat');if(b)updFix(b)},150);
 const r=w.getBoundingClientRect();fx.burst(r.left+r.width/2,r.top,10,{sp:4,r:6,k:'star'});sfx.ok()}

const SC={
 lydo:[
  {n:'Linh',t:'Mai gặp ở {trg|trường} nhé 😄',d:800},
  {me:1,t:'Ok luôn, {hok|không} quên đâu!',d:900},
  {n:'Linh',t:'Deadline toang tới nơi {r|rồi}, {mik|mình} chưa làm {j|gì} 😭',d:1100},
  {me:1,t:'Chill đi, tối nay {ko|không} rảnh thì mai làm 🙃',d:1000}],
 yn:[
  {av:'1',c:'#C1121F',t:'Dùng tiếng Việt cẩu thả làm suy giảm khả năng diễn đạt, tư duy ngôn ngữ và ý thức văn hóa của người trẻ. Giữ gìn sự trong sáng của tiếng Việt vì thế còn là nhiệm vụ giáo dục nhân cách.',d:900},
  {av:'2',c:'#2E6B4E',t:'Tiếng Việt là linh hồn của văn hóa Việt Nam. Có tiếng Việt trong sáng, ta thêm hiểu, thêm yêu văn hóa, lịch sử; củng cố ý thức cội nguồn và lòng tự hào dân tộc.',d:900},
  {av:'3',c:'#D99A00',t:'Hội nhập là điều không tránh khỏi, nên càng phải giữ gốc rễ của mình, không chạy theo thứ ngôn ngữ nửa vời, pha tạp.',d:900}],
 nn:[
  {av:'1',c:'#2E6B4E',t:'Thành thạo ít nhất một ngoại ngữ, nên dịch và diễn đạt song ngữ chính xác, tự nhiên.',d:800},
  {av:'2',c:'#C1121F',t:'Hiểu sự khác biệt giữa các ngôn ngữ, từ đó giải thích tiếng Việt (dấu thanh, thanh điệu) dễ hiểu hơn cho người nước ngoài.',d:900},
  {av:'3',c:'#D99A00',t:'Có cơ hội giao lưu thường xuyên với sinh viên và du khách quốc tế, nên dễ lan tỏa văn hóa.',d:900}],
 kl:[
  {av:'1',t:'Giữ gìn và phát huy chữ Quốc ngữ không phải việc xa vời: nó bắt đầu từ cách viết một bài tập, gửi một email, bình luận trên mạng xã hội hay chọn từ trong giao tiếp hằng ngày.',d:900},
  {av:'2',t:'Viết tắt, tiếng lóng và từ ngoại ngữ không phải lúc nào cũng tiêu cực. Vấn đề là dùng đúng hoàn cảnh, đúng đối tượng và bảo đảm người đọc hiểu chính xác.',d:1000},
  {av:'3',t:'Mỗi sinh viên cần đọc lại văn bản, kiểm tra chính tả, dùng từ rõ nghĩa, trích dẫn đúng nguồn và chịu trách nhiệm về nội dung mình đăng tải.',d:1000},
  {av:'4',t:'Sổ tay lỗi tiếng Việt, sửa bài cho nhau, “Mỗi tuần một lỗi tiếng Việt”, sản phẩm song ngữ và “21 ngày viết rõ” giúp chuyển nhận thức thành hành động cụ thể.',d:1000},
  {av:'5',t:'Theo nhóm, giá trị của chữ Quốc ngữ chỉ được duy trì khi người dùng vừa tôn trọng chuẩn mực, vừa biết thích ứng linh hoạt với môi trường giao tiếp hiện đại.',d:1000}]
};
let gtStart=()=>{};
document.addEventListener('click',e=>{
 const t=e.target;if(!t.closest)return;
 const w=t.closest('.w');if(w){fixWord(w);return}
 const rp=t.closest('[data-replay]');
 if(rp){const k=rp.dataset.replay;if(k==='gt')gtStart();else playChat($('#chat-'+k),SC[k]);return}
 const fa=t.closest('[data-fixall]');
 if(fa){$$('.w:not(.ok)',fa.closest('.slide')).forEach((x,k)=>setTimeout(()=>fixWord(x),k*380));return}
 const f=t.closest('.fc');if(f){f.classList.toggle('on');sfx.tick();return}
 const b=t.closest('.bub');
 if(b&&!t.closest('.dots')){const r=b.getBoundingClientRect();for(let i=0;i<3;i++)setTimeout(()=>fx.heart(r.left+r.width*rnd(.2,.8),r.top),i*120);sfx.pop()}
});

/* ================= tab có vệt trượt ================= */
function tabs(root,cb){
 const bs=$$('button',root),ink=$('.ink',root);
 const set=(b,silent)=>{bs.forEach(x=>x.classList.toggle('on',x===b));ink.style.left=b.offsetLeft+'px';ink.style.top=b.offsetTop+'px';ink.style.width=b.offsetWidth+'px';ink.style.height=b.offsetHeight+'px';if(cb)cb(b.dataset.t,!!silent)};
 bs.forEach(b=>b.addEventListener('click',()=>{if(!b.classList.contains('on')){sfx.tick();set(b)}}));
 root._set=()=>set($('button.on',root)||bs[0],true);
 setTimeout(root._set,60);return root}
const panelTabs=root=>tabs(root,t=>{const sc=root.closest('.wrap');$$('.tp',sc).forEach(p=>p.classList.toggle('on',p.dataset.p===t))});

/* ================= bìa: chữ được "thêm dấu" ================= */
function heroInit(){
 const big=$('#bigT'),pre=$('#preTxt'),team=$('#team'),DT='Nhóm thực hiện: bấm để ghi tên nhóm';let tok={v:1};
 const words=[[['C'],['h'],['u','ữ']],[['Q'],['u'],['o','ố'],['c']],[['n'],['g'],['u','ữ']]];
 const build=()=>{big.innerHTML=words.map(w=>`<span class="wd">${w.map(([c,to])=>`<span class="ch${to?' sw':''}"${to?` data-to="${to}"`:''}>${c}</span>`).join('')}</span>`).join(' ')};
 build();
 const saved=store.get('qn-team');if(saved)team.textContent=saved;
 team.addEventListener('input',()=>store.set('qn-team',team.textContent.trim()));
 team.addEventListener('blur',()=>{if(!team.textContent.trim()){team.textContent=DT;store.set('qn-team','')}});
 team.addEventListener('focus',()=>{if(team.textContent===DT){const r=document.createRange();r.selectNodeContents(team);const s=getSelection();s.removeAllRanges();s.addRange(r)}});
 team.addEventListener('keydown',e=>{if(e.key==='Enter'){e.preventDefault();team.blur()}});
 team.addEventListener('paste',e=>{e.preventDefault();const t=(e.clipboardData||window.clipboardData).getData('text').replace(/\s+/g,' ').slice(0,80);document.execCommand('insertText',false,t)});
 async function run(){
  const my=tok={v:0};build();pre.textContent='';
  const line='Công tác sinh viên giữ gìn và phát huy';
  await sleep(700);
  for(let i=1;i<=line.length;i++){if(my.v)return;pre.textContent=line.slice(0,i);await sleep(38)}
  await sleep(500);
  for(const sw of $$('.sw',big)){
   if(my.v)return;
   sw.classList.add('fl');setTimeout(()=>{sw.textContent=sw.dataset.to},380);
   const r=sw.getBoundingClientRect();fx.burst(r.left+r.width/2,r.top+r.height*.2,12,{sp:5,r:7,k:'star',cols:GOLD});sfx.ok();
   await sleep(760);
  }
 }
 on('s-hero',run);onLeave('s-hero',()=>{tok.v=1});
}

/* ================= dấu thanh: sáu thanh, sáu nghĩa ================= */
const TONES=[['ngang','ma','con ma'],['huyền','mà','“nhưng mà”, “mà”'],['sắc','má','mẹ (cách gọi ở nhiều vùng), gò má'],['hỏi','mả','mồ mả'],['ngã','mã','con ngựa, mã số'],['nặng','mạ','cây mạ, tức lúa non']];
function toneInit(){
 const box=$('#tbtns'),gl=$('#glyph'),ch=$('#toneChat');let manual=false;
 box.innerHTML=TONES.map((t,i)=>`<button class="tb" data-i="${i}"><b>${t[1]}</b><small>${t[0]}</small></button>`).join('');
 const set=(i,user)=>{
  if(user)manual=true;const t=TONES[i];
  $$('.tb',box).forEach((b,k)=>b.classList.toggle('on',k===i));
  gl.innerHTML='m<span class="vv">'+t[1].slice(1)+'</span>';
  gl.classList.remove('drop');void gl.offsetWidth;gl.classList.add('drop');
  ch.innerHTML=`<div class="msg"><span class="av">${t[1]}</span><div class="bub"><b>${t[1]}</b>: ${esc(t[2])}</div></div>`;sfx.pop()};
 box.addEventListener('click',e=>{const b=e.target.closest('.tb');if(b)set(+b.dataset.i,true)});
 on('s-khainiem',()=>{manual=false;set(2);let k=2;const auto=()=>{if(manual)return;k=(k+1)%6;set(k);later(auto,2300)};later(auto,2800)});
}

/* ================= dòng thời gian: dấu ấn chạy dọc lịch sử ================= */
const TL=[
 {y:'Đầu thế kỷ XVII',ph:'Giai đoạn khởi đầu',c:'',t:'Giáo sĩ phương Tây đến truyền giáo',d:'Chữ Quốc ngữ hình thành đầu thế kỷ XVII, khi các giáo sĩ phương Tây đến truyền giáo ở Đàng Trong và Đàng Ngoài. Đó là công trình của cả một tập thể giáo sĩ (Bồ Đào Nha, Ý, Pháp…) với mục đích ban đầu là truyền đạo. Francisco de Pina được coi là người đã sáng lập ra chữ Quốc ngữ.'},
 {y:'1626',ph:'Giai đoạn cải tiến (thế kỷ XVII–XVIII)',c:'y',t:'Chữ được viết rời ra',d:'Đầu năm 1626, chữ Quốc ngữ được viết rời ra, không còn dính vào nhau. Trước đó còn nhiều khuyết điểm: chưa có dấu thanh, viết dính nhau, thiếu nhiều nguyên âm và chưa có các phụ âm đơn đ, x, v.'},
 {y:'1632',ph:'Giai đoạn cải tiến (thế kỷ XVII–XVIII)',c:'y',t:'Hệ thống chữ trở nên hoàn thiện',d:'Năm 1632, hệ thống phụ âm, nguyên âm và các dấu đã trở nên hoàn thiện hơn rất nhiều (ví dụ: “đàng ngoày” thành “đàng ngoài”).'},
 {y:'1651',ph:'Giai đoạn cải tiến (thế kỷ XVII–XVIII)',c:'y',t:'Alexandre de Rhodes',d:'Alexandre de Rhodes có công trong giai đoạn phôi thai của chữ Quốc ngữ, với bản song ngữ “Phép giảng tám ngày” và cuốn từ điển phiên âm Dictionarium Annamiticum Lusitanum et Latinum (Việt – Bồ – La) năm 1651.'},
 {y:'Cuối XIX – đầu XX',ph:'Phổ biến rộng rãi',c:'g',t:'Từ công cụ hành chính thành “vũ khí khai trí”',d:'Chính quyền Pháp thúc đẩy dùng chữ Quốc ngữ trong hành chính và giáo dục vì dễ học, dễ phổ biến, giảm ảnh hưởng của tầng lớp Nho sĩ. Nhưng người Việt đã biến công cụ này thành vũ khí khai trí: phong trào Đông kinh nghĩa thục, báo chí quốc ngữ, sách giáo khoa, văn học hiện đại bùng nổ.'}];
function tlInit(){
 const nodes=$('#tlNodes'),pin=$('#tlPin'),fill=$('#tlFill'),card=$('#tlCard');let manual=false,idx=0;
 nodes.innerHTML=TL.map((t,i)=>`<button class="tn" data-i="${i}" style="left:${6+i*22}%"><i></i><b>${esc(t.y)}</b></button>`).join('');
 const set=(i,user)=>{
  if(user)manual=true;idx=i;
  $$('.tn',nodes).forEach((n,k)=>n.classList.toggle('on',k===i));
  pin.style.left=(6+i*22)+'%';fill.style.width=(i/(TL.length-1)*100)+'%';
  const t=TL[i];card.innerHTML=`<span class="chip ${t.c}">${esc(t.ph)}</span><h3>${esc(t.t)}</h3><p>${esc(t.d)}</p>`;
  card.classList.remove('pop');void card.offsetWidth;card.classList.add('pop');sfx.pop()};
 nodes.addEventListener('click',e=>{const n=e.target.closest('.tn');if(n)set(+n.dataset.i,true)});
 on('s-hinhthanh',()=>{manual=false;set(0);const auto=()=>{if(manual||idx>=TL.length-1)return;set(idx+1);later(auto,4600)};later(auto,5000)});
}

/* ================= chữ được "nâng cấp" (lật từng ký tự) ================= */
const MP=[['Quanmguya','Quảng Ngãi','viết dính, thiếu dấu và nguyên âm'],['Tuijciam biêt','tui chẳng biết','tách chữ, thêm dấu thanh'],['dj','đ','phụ âm đơn'],['sc','x','phụ âm đơn'],['b','v','phụ âm đơn'],['đàng ngoày','đàng ngoài','1632: hoàn thiện vần'],['nhà thương đây','nhà thượng đài','1632: hoàn thiện dấu']];
function morphInit(){
 const g=$('#mgrid');
 g.innerHTML=MP.map((m,i)=>`<button class="mcard" data-i="${i}"><div class="mw"><div class="mf"></div><small>${esc(m[2])}</small></div><span class="ar">↻</span></button>`).join('');
 const mf=i=>$$('.mf',g)[i],state=MP.map(()=>0);
 const show=(i,txt)=>{mf(i).innerHTML=[...txt].map(c=>`<span class="mc">${esc(c)}</span>`).join('')};
 const reset=()=>{MP.forEach((m,i)=>{state[i]=0;show(i,m[0]);g.children[i].classList.remove('done')});$$('#defects span').forEach(s=>s.classList.remove('fixed'))};
 const up=i=>{
  const m=MP[i],a=[...(state[i]?m[1]:m[0])],b=[...(state[i]?m[0]:m[1])];state[i]^=1;
  const n=Math.max(a.length,b.length),st=state[i];
  mf(i).innerHTML=Array.from({length:n},(_,k)=>`<span class="mc">${esc(a[k]||'')}</span>`).join('');
  [...mf(i).children].forEach((sp,k)=>setTimeout(()=>{sp.classList.add('fl');setTimeout(()=>{sp.textContent=b[k]||''},220)},k*70));
  setTimeout(()=>{g.children[i].classList.toggle('done',!!st);sfx.pop()},n*70+260)};
 g.addEventListener('click',e=>{const c=e.target.closest('.mcard');if(c)up(+c.dataset.i)});
 $('#morphAll').addEventListener('click',()=>{
  MP.forEach((m,i)=>{if(!state[i])setTimeout(()=>up(i),i*420)});
  $$('#defects span').forEach((s,k)=>setTimeout(()=>s.classList.add('fixed'),MP.length*420+k*350));
  setTimeout(()=>{sfx.ok();fx.confetti()},MP.length*420+1500)});
 $('#morphReset').addEventListener('click',reset);
 on('s-morph',reset);
}

/* ================= panel mở rộng, thẻ tách đôi, đóng dấu nhận việc ================= */
function accInit(root,item){
 if(!root)return;const items=$$(item,root);
 const open=el=>items.forEach(x=>x.classList.toggle('on',x===el));
 const hov=matchMedia('(hover:hover)').matches;
 items.forEach(el=>{el.addEventListener('click',()=>{if(!el.classList.contains('on')){open(el);sfx.tick()}});if(hov)el.addEventListener('mouseenter',()=>{if(!el.classList.contains('on'))open(el)})})}
function dutyInit(){
 const ds=$$('.duty'),n=$('#dutyN');
 ds.forEach(d=>d.addEventListener('click',()=>{
  d.classList.toggle('on');const k=ds.filter(x=>x.classList.contains('on')).length;n.textContent=k+'/4';
  if(d.classList.contains('on')){const r=d.getBoundingClientRect();fx.burst(r.right-60,r.bottom-40,12,{sp:5,r:7});sfx.ok()}
  if(k===4){fx.confetti();toast('Đã nhận đủ 4 nhiệm vụ!')}}));
 on('s-sinhvien',()=>{},()=>{ds.forEach(d=>d.classList.remove('on'));n.textContent='0/4'});
}

/* ================= chương 2: khảo sát, vòng tròn tiến độ, thanh tỷ lệ ================= */
function surveyInit(){
 const st=$$('#steps li'),box=$('#steps');
 const lit=i=>{st.forEach((x,k)=>x.classList.toggle('on',k<=i));box.style.setProperty('--sp',(Math.max(i,0)/(st.length-1)*100)+'%')};
 on('s-khaosat',()=>{lit(-1);st.forEach((l,i)=>later(()=>{lit(i);sfx.tick()},1100+i*800))},()=>{st.forEach(x=>x.classList.remove('on'));box.style.setProperty('--sp','0%')});
 st.forEach((l,i)=>l.addEventListener('click',()=>{clearT();lit(i);sfx.pop()}));
}
const GA=[{v:90,t:'Viết đúng chính tả là quan trọng'},{v:86,t:'Dùng dấu câu đúng là cần thiết'},{v:88,t:'Viết hoa đúng quy tắc là quan trọng'},{v:94,t:'Dùng tiếng Việt có dấu là cần thiết'},{v:92,t:'Nhận thức được vai trò của chữ Quốc ngữ trong học tập và giao tiếp'}];
const BA=[{v:78,t:'Thường xuyên kiểm tra chính tả trước khi nộp bài'},{v:65,t:'Chủ động tra từ điển khi không chắc cách dùng từ'},{v:82,t:'Dùng tiếng Việt đầy đủ trong email và bài tập'},{v:70,t:'Có thói quen đọc sách hoặc tài liệu bằng tiếng Việt'},{v:55,t:'Từng tham gia viết bài, thuyết trình, hùng biện hoặc sáng tạo nội dung bằng tiếng Việt'}];
const CIR=2*Math.PI*46;
function buildGauges(){
 $('#gauges').innerHTML=GA.map(g=>`<div class="gauge tilt"><div class="gw"><svg viewBox="0 0 120 120"><circle class="gb" cx="60" cy="60" r="46"/><circle class="gf" cx="60" cy="60" r="46" transform="rotate(-90 60 60)" stroke-dasharray="${CIR.toFixed(2)}" stroke-dashoffset="${CIR.toFixed(2)}" data-v="${g.v}" data-c="${CIR.toFixed(2)}"/></svg><b class="cnt" data-to="${g.v}" data-suf="%">0%</b></div><p>${esc(g.t)}</p><small>${g.v} trên 100 sinh viên</small></div>`).join('')}
function buildBars(el,items,o={}){
 const max=o.max||100,suf=o.suf||'%',dec=o.dec||0;
 el.innerHTML=items.map(b=>`<div class="brow" data-v="${b.v}"><span class="bl">${esc(b.t)}</span><div class="bt"><i class="bf" data-w="${(b.v/max*100).toFixed(1)}"></i><b class="bv cnt" data-to="${b.v}" data-dec="${dec}" data-suf="${suf}">0${suf}</b></div></div>`).join('')}
function sortInit(){
 let sorted=false;const box=$('#bars'),btn=$('#sortBars');
 btn.addEventListener('click',()=>{
  sorted=!sorted;const kids=[...box.children],first=kids.map(k=>k.getBoundingClientRect().top);
  [...kids].sort((a,b)=>sorted?b.dataset.v-a.dataset.v:BA.findIndex(x=>x.v==a.dataset.v)-BA.findIndex(x=>x.v==b.dataset.v)).forEach(k=>box.append(k));
  kids.forEach((k,i)=>{const dy=first[i]-k.getBoundingClientRect().top;k.style.transition='none';k.style.transform=`translateY(${dy}px)`});
  void box.offsetHeight;
  kids.forEach(k=>{k.style.transition='transform .75s cubic-bezier(.2,.8,.2,1)';k.style.transform=''});
  btn.textContent=sorted?'Về thứ tự ban đầu':'Sắp xếp theo tỷ lệ';sfx.whoosh()});
}

/* ================= gợn sóng lan tỏa: một lỗi nhỏ, ảnh hưởng lớn ================= */
const RING=[
 {t:'Khả năng giao tiếp',d:'Dùng từ thiếu chính xác, viết tắt quá mức hoặc diễn đạt không rõ ràng có thể khiến người đọc khó hiểu, thậm chí hiểu sai thông tin.',c:'#C1121F'},
 {t:'Kết quả học tập',d:'Sai chính tả, dùng từ không phù hợp và trình bày thiếu chuẩn mực có thể làm giảm chất lượng bài viết, bài kiểm tra, bài thuyết trình và các sản phẩm học tập.',c:'#E2572B'},
 {t:'Khả năng viết văn bản',d:'Quen dùng ngôn ngữ mạng và viết tắt có thể gây khó khăn khi viết báo cáo, tiểu luận, email hoặc văn bản mang tính học thuật.',c:'#E9A600'},
 {t:'Hình ảnh của sinh viên',d:'Cách dùng ngôn ngữ thể hiện sự chuyên nghiệp và ý thức của mỗi người; viết sai chính tả có thể tạo ấn tượng thiếu cẩn thận, thiếu chuyên nghiệp.',c:'#9AA528'},
 {t:'Sự trong sáng của tiếng Việt',d:'Nếu cách viết sai, viết tắt và lạm dụng tiếng lóng được dùng thường xuyên, chúng có thể làm giảm tính chuẩn mực và sự trong sáng của tiếng Việt.',c:'#4E9B6B'},
 {t:'Bản sắc văn hóa dân tộc',d:'Tiếng Việt là bộ phận quan trọng của văn hóa dân tộc, nên dùng tiếng Việt đúng và có ý thức cũng là góp phần bảo vệ bản sắc văn hóa Việt Nam.',c:'#2E6B4E'}];
function ripInit(){
 const svg=$('#ripSvg'),chat=$('#ripChat'),R=[40,76,112,148,184,220];
 svg.innerHTML=R.map((r,i)=>`<circle class="rr" data-i="${i}" r="${r}" style="--c:${RING[i].c}"/>`).join('')+'<circle class="core" r="13"/>'+
  R.map((r,i)=>`<g class="rn" data-i="${i}" style="--c:${RING[i].c}" transform="translate(0 ${-r})"><circle r="11"/><text y="4.2">${i+1}</text></g>`).join('');
 const lit=i=>{
  const rr=$(`.rr[data-i="${i}"]`,svg),rn=$(`.rn[data-i="${i}"]`,svg);if(rr.classList.contains('lit'))return;
  rr.classList.add('lit');rn.classList.add('lit');
  svg.insertAdjacentHTML('beforeend',`<circle class="wave" r="40" style="--c:${RING[i].c};--k:${(R[i]/40).toFixed(2)}"/>`);
  const w=svg.lastElementChild;setTimeout(()=>w.remove(),1700);
  const g=document.createElement('div');g.className='msg';g.style.setProperty('--c',RING[i].c);
  g.innerHTML=`<span class="av">${i+1}</span><div class="bub"><b>${esc(RING[i].t)}</b><br>${esc(RING[i].d)}</div>`;
  chat.append(g);chat.scrollTop=chat.scrollHeight;sfx.pop()};
 const clear=()=>{$$('.lit',svg).forEach(x=>x.classList.remove('lit'));$$('.wave',svg).forEach(w=>w.remove());chat.innerHTML=''};
 $('#drop').addEventListener('click',()=>{clear();clearT();$('#drop').textContent='Thả lại';RING.forEach((_,i)=>later(()=>lit(i),300+i*900));later(()=>toast('Một lỗi nhỏ có thể lan rất xa'),300+RING.length*900)});
 svg.addEventListener('click',e=>{const t=e.target.closest('[data-i]');if(t)lit(+t.dataset.i)});
 on('s-hanche',clear,()=>{clear();$('#drop').textContent='Thả một lỗi sai'});
}

/* ================= chín nguyên nhân: thẻ lật 3D ================= */
const CA=[
 {t:'Ảnh hưởng của mạng xã hội',d:'Thường xuyên tiếp xúc Facebook, TikTok, Messenger… nên dễ viết theo ngôn ngữ mạng, viết tắt, bỏ dấu hoặc dùng ký hiệu.',ex:[['ko','không'],['mik','mình'],['j','gì'],['r','rồi'],['hok','không']]},
 {t:'Thói quen viết nhanh, viết tắt',d:'Để tiết kiệm thời gian khi nhắn tin, rút gọn từ, bỏ dấu hoặc bỏ qua việc kiểm tra chính tả.',ex:[['M đi học chưa?','Bạn đi học chưa?'],['mai gặp ở trg nhé','Mai gặp ở trường nhé']]},
 {t:'Tâm lý chạy theo xu hướng',d:'Dùng cách nói đang phổ biến trên mạng để thể hiện sự trẻ trung, hòa nhập, dù không cần thiết trong câu tiếng Việt.',w:['chill','flex','slay','healing']},
 {t:'Ảnh hưởng của tiếng lóng',d:'Tiếng lóng xuất hiện nhiều trong giao tiếp hằng ngày, rồi bị dùng cả khi cần nghiêm túc: bài thuyết trình, văn bản học tập trang trọng.',w:['xịn','toang','chill','cháy']},
 {t:'Ảnh hưởng của ngoại ngữ',d:'Học và tiếp xúc thường xuyên với ngoại ngữ nên dễ xen từ nước ngoài vào câu tiếng Việt.',ex:[['Deadline của mình sắp tới rồi','Hạn nộp bài của mình sắp đến rồi']]},
 {t:'Thói quen ít đọc sách',d:'Văn hóa đọc suy giảm khiến hụt vốn từ, kém cảm thụ ngôn ngữ. Chỉ đọc đoạn văn ngắn, rời rạc trên mạng làm năng lực tư duy logic chuỗi câu giảm sút.'},
 {t:'Chưa chú trọng kiểm tra, sửa lỗi',d:'Cẩu thả và chủ quan sau khi soạn thảo; thiếu thói quen rà soát chính tả, cấu trúc câu và phong cách trước khi bấm gửi.'},
 {t:'Chưa phân biệt hoàn cảnh giao tiếp',d:'Thiếu tri thức ngữ dụng: ai (đối tượng), làm gì (mục đích), ở đâu (bối cảnh). Cào bằng văn phong trò chuyện với văn phong học thuật, công vụ.',ex:[['Cô ơi, mai em nghỉ nha','Thưa cô, ngày mai em xin phép nghỉ học ạ']]},
 {t:'Nhận thức trách nhiệm còn hạn chế',d:'Chưa thấy đủ rằng chữ viết là di sản văn hóa, là công cụ định hình tư duy và bản sắc; xem nhẹ lỗi ngôn ngữ, coi là lỗi nhỏ nên làm suy giảm tính chuẩn mực.'}];
function causesInit(){
 const g=$('#fgrid');
 const ex=c=>c.ex?'<div class="ex">'+c.ex.map(p=>`<s>${esc(p[0])}</s><u>→ ${esc(p[1])}</u>`).join('')+'</div>':c.w?'<div class="ex">'+c.w.map(w=>`<u>${esc(w)}</u>`).join('')+'</div>':'';
 g.innerHTML=CA.map((c,i)=>`<div class="fc" tabindex="0" role="button" aria-label="Nguyên nhân ${i+1}: ${esc(c.t)}"><div class="fi"><div class="ff"><span class="no">${i+1}</span><small>Nguyên nhân ${i+1}</small><h4>${esc(c.t)}</h4><em>Bấm để lật xem ví dụ</em></div><div class="fb"><small>${esc(c.t)}</small><p>${esc(c.d)}</p>${ex(c)}</div></div></div>`).join('');
 const btn=$('#flipAll');
 btn.addEventListener('click',()=>{const all=[...g.children],want=all.some(x=>!x.classList.contains('on'));all.forEach((x,i)=>setTimeout(()=>x.classList.toggle('on',want),i*90));btn.textContent=want?'Úp tất cả thẻ':'Lật tất cả thẻ';sfx.whoosh()});
 on('s-nguyennhan',()=>{},()=>{$$('.fc',g).forEach(x=>x.classList.remove('on'));btn.textContent='Lật tất cả thẻ'});
}
function todoInit(){
 const li=$$('#todo li'),bar=$('#todoBar');
 li.forEach(l=>l.addEventListener('click',()=>{
  l.classList.toggle('on');const k=li.filter(x=>x.classList.contains('on')).length;
  bar.style.width=(k/li.length*100)+'%';sfx.tick();
  if(k===li.length){fx.confetti();toast('Năm cam kết đã sẵn sàng!');sfx.ok()}}));
}

/* ================= chương 3: sổ tay chính tả ================= */
function nbInit(){
 const list=$('#nbList'),A=$('#nbA'),B=$('#nbB');
 const add=(a,b,quiet)=>{const li=document.createElement('li');li.innerHTML=`<s>${esc(a)}</s><span>→</span><b>${esc(b)}</b><i class="stp">đã sửa</i>`;list.append(li);list.scrollTop=list.scrollHeight;if(!quiet)sfx.ok()};
 [['sắp sếp','sắp xếp'],['sữa chữa','sửa chữa'],['chân trọng','trân trọng']].forEach(p=>add(p[0],p[1],true));
 const btn=$('#nbAdd');
 btn.addEventListener('click',()=>{
  const a=A.value.trim(),b=B.value.trim();
  if(!a||!b){toast('Điền cả từ viết sai và từ viết đúng nhé');return}
  add(a,b);A.value='';B.value='';A.focus();
  const r=btn.getBoundingClientRect();fx.burst(r.left+r.width/2,r.top,10,{sp:5,r:7})});
 [A,B].forEach(i=>i.addEventListener('keydown',e=>{if(e.key==='Enter')btn.click()}));
}

/* ================= giao tiếp: bạn bè hay giảng viên ================= */
const GT={
 ban:{name:'Bạn thân',av:'B',meter:25,rule:'Giữa bạn bè: thoải mái dùng từ gần gũi, từ lóng hoặc viết tắt để tạo sự gắn kết, vui vẻ.',
  s:[{me:1,t:'Hm ni ôkê hơm?',d:700},{n:'Minh',t:'Ôkê luôn, chiều gặp nha 😆',d:1000},{me:1,t:'Chốt! Mik mang sách cho 📚',d:900},{sys:1,t:'✔ Giữa bạn bè, thân mật như vậy là ổn: người nghe hiểu ngay.'}]},
 gv:{name:'Giảng viên',av:'GV',meter:35,rule:'Trong giao tiếp trang trọng: bắt buộc viết đúng chính tả, đủ cấu trúc câu, dùng từ lịch sự, chuẩn mực; không lạm dụng từ lóng hay viết tắt khi gửi email, báo cáo hoặc làm việc với giảng viên.',
  s:[{me:1,t:'Dạ em chào thầy/cô, em xin phép hỏi thầy/cô về nội dung bài tập ạ.',d:800},{n:'Giảng viên',av:'GV',t:'Chào em, em cứ hỏi nhé.',d:1100},{me:1,t:'{Cô ơi|Thưa cô}, {mai|ngày mai} em {nghỉ nha|xin phép nghỉ học ạ}',d:1100},{sys:1,t:'✖ Tin nhắn cuối quá suồng sã với giảng viên. Bấm vào chữ gạch đỏ để sửa.'}]}
};
let gtSc='ban';
function gtInit(){
 const chat=$('#chat-gt');
 const setM=v=>{$('#meterI').style.clipPath=`inset(0 ${100-v}% 0 0 round 99px)`;$('#meterV').textContent=Math.round(v)+'%'};
 gtStart=()=>{const g=GT[gtSc];$('#gtName').textContent=g.name;$('#gtAv').textContent=g.av;$('#rule').textContent=g.rule;setM(g.meter);playChat(chat,g.s)};
 tabs($('[data-tabs="sc"]'),t=>{if(t!==gtSc){gtSc=t;gtStart()}});
 chat.addEventListener('fix',()=>{if(gtSc==='gv'&&chat._tot)setM(GT.gv.meter+55*($$('.w.ok',chat).length/chat._tot))});
 $('#formalize').addEventListener('click',()=>{
  if(gtSc==='ban'){toast('Giữa bạn bè không cần chỉnh. Thử tab “Gửi giảng viên” nhé!');return}
  $$('.w:not(.ok)',chat).forEach((w,k)=>setTimeout(()=>fixWord(w),k*450))});
 on('s-giaotiep',()=>later(gtStart,900));
}

/* ================= mạng xã hội: thanh người dùng và biểu đồ tròn ================= */
function mxhInit(){
 buildBars($('#mxhBars'),[{v:72.7,t:'Facebook'},{v:67.7,t:'TikTok'},{v:63,t:'YouTube'}],{max:80,dec:1,suf:' triệu'});
 const SEG=[{v:75.4,c:'#2E6B4E',l:'Trung lập'},{v:3.5,c:'#C1121F',l:'Tiêu cực'},{v:21.1,c:'#D9B75E',l:'Phần còn lại'}];
 const C=2*Math.PI*60,svg=$('#donut'),lg=$('#donutLg');let acc=0;
 svg.innerHTML=SEG.map((s,i)=>{const st=acc/100*360,len=s.v/100*C;acc+=s.v;return `<circle class="seg" data-i="${i}" cx="80" cy="80" r="60" stroke="${s.c}" stroke-dasharray="${len.toFixed(2)} ${C.toFixed(2)}" stroke-dashoffset="${len.toFixed(2)}" data-len="${len.toFixed(2)}" transform="rotate(${st.toFixed(2)} 80 80)"/>`}).join('');
 lg.innerHTML=SEG.map((s,i)=>`<li data-i="${i}"><i style="background:${s.c}"></i>${s.l} ${fmt(s.v,1)}%</li>`).join('');
 const show=i=>{$('#dcV').textContent=fmt(SEG[i].v,1)+'%';$('#dcL').textContent=SEG[i].l;$$('.seg',svg).forEach((c,k)=>{c.style.opacity=k===i?1:.35;c.style.strokeWidth=k===i?26:22})};
 const back=()=>{$$('.seg',svg).forEach(c=>{c.style.opacity=1;c.style.strokeWidth=22});$('#dcV').textContent='75,4%';$('#dcL').textContent='Trung lập'};
 lg.addEventListener('pointerover',e=>{const l=e.target.closest('li');if(l)show(+l.dataset.i)});
 lg.addEventListener('pointerleave',back);
 lg.addEventListener('click',e=>{const l=e.target.closest('li');if(l){show(+l.dataset.i);sfx.pop()}});
 on('s-mxh',()=>later(()=>$$('.seg',svg).forEach(c=>{c.style.strokeDashoffset=0}),650),()=>{$$('.seg',svg).forEach(c=>{c.style.strokeDashoffset=c.dataset.len});back()});
}

/* ================= hộp đăng bài: quy tắc 3 câu hỏi ================= */
function composeInit(){
 const ta=$('#draft'),q=$('#qchat'),feed=$('#feed'),DEF=ta.value;
 const BADW='r|mik|j|ko|hok|trg|đc|dc|ntn|k',SLW='toang|chill|flex|slay|healing|cháy|xịn';
 const mkRe=(w,f)=>new RegExp(`(^|[^\\p{L}])(${w})(?=[^\\p{L}]|$)`,f);
 const reB=mkRe(BADW,'iu'),reS=mkRe(SLW,'iu'),reBg=mkRe(BADW,'giu'),reSg=mkRe(SLW,'giu');
 const DICT={r:'rồi',mik:'mình',j:'gì',ko:'không',hok:'không',trg:'trường','đc':'được',dc:'được',ntn:'như thế nào',k:'không'};
 const SLD={toang:'rắc rối to',chill:'thư giãn',flex:'khoe',slay:'xuất sắc',healing:'thư giãn','cháy':'hết mình','xịn':'tốt'};
 const fixText=t=>t.replace(reBg,(m,a,w)=>a+DICT[w.toLowerCase()]).replace(reSg,(m,a,w)=>a+SLD[w.toLowerCase()]).replace(/(^|[^\p{L}])thiệt(?=[^\p{L}]|$)/giu,(m,a)=>a+'thật');
 const noDia=t=>t.length>12&&!/[àáảãạăằắẳẵặâầấẩẫậèéẻẽẹêềếểễệìíỉĩịòóỏõọôồốổỗộơờớởỡợùúủũụưừứửữựỳýỷỹỵđ]/i.test(t);
 const publish=t=>{
  const d=document.createElement('div');d.className='fpost';
  d.innerHTML=`<b>Bạn</b> <small>vừa xong</small><p>${esc(t)}</p><div class="lk">♥ <span class="n">0</span></div>`;
  feed.prepend(d);while(feed.children.length>2)feed.lastChild.remove();
  fx.confetti();sfx.ok();toast('Đăng thành công!');
  let n=0;const iv=setInterval(()=>{const el=d.querySelector('.n');if(!el||!document.body.contains(d)){clearInterval(iv);return}n+=Math.ceil(rnd(1,4));el.textContent=n;const r=d.getBoundingClientRect();fx.heart(r.left+40+rnd(0,30),r.top+30);if(n>=24)clearInterval(iv)},260)};
 const ask=async()=>{
  const t=ta.value.trim();q.innerHTML='';
  if(!t){toast('Hãy viết gì đó trước khi đăng nhé');return}
  const tk=q._tk=(q._tk||0)+1,hasB=reB.test(t),hasS=reS.test(t);
  const tests=[
   {q:'Người đọc có hiểu đúng ý mình không?',bad:hasB},
   {q:'Có chỗ nào đổi nghĩa vì thiếu dấu hoặc viết tắt không?',bad:hasB||noDia(t)},
   {q:'Nếu lời này được in thành bản tin, mình có ngại không?',bad:hasS||hasB}];
  let fails=0;
  for(const [i,x] of tests.entries()){
   if(q._tk!==tk)return;
   q.append(msgEl({n:'Trợ lý chính tả',av:'?',t:`${i+1}. ${x.q}`}));sfx.pop();await sleep(750);
   if(q._tk!==tk)return;
   const ok=!x.bad;if(!ok)fails++;
   const d=document.createElement('div');d.className='msg me';
   d.innerHTML=`<span class="av">B</span><div class="bub ${ok?'good':'bad'}">${ok?'✔ Ổn':'✖ Chưa ổn'}</div>`;
   q.append(d);if(ok)sfx.ok();else sfx.bad();await sleep(650);
  }
  if(q._tk!==tk)return;
  if(fails){ta.classList.remove('shake');void ta.offsetWidth;ta.classList.add('shake');q.append(msgEl({sys:1,t:`Còn ${fails} câu chưa ổn. Bấm “Sửa giúp mình” hoặc tự chỉnh rồi đăng lại nhé.`}))}
  else publish(t)};
 $('#postBtn').addEventListener('click',ask);
 $('#fixDraft').addEventListener('click',async()=>{
  const t=fixText(ta.value);if(t===ta.value){toast('Không thấy chỗ nào cần sửa');return}
  ta.value='';for(const c of t){ta.value+=c;await sleep(14)}sfx.ok()});
 $('#resetDraft').addEventListener('click',()=>{ta.value=DEF;q._tk=(q._tk||0)+1;q.innerHTML=''});
}

/* ================= hoạt động sinh viên tự tổ chức ================= */
function actInit(){
 const w=$('#weeks12');
 w.innerHTML=Array.from({length:12},(_,i)=>`<span class="wk" title="Tuần ${i+1}: đăng vào sáng thứ Hai">T${i+1}</span>`).join('');
 const off=()=>$$('.wk',w).forEach(x=>x.classList.remove('on'));
 on('s-hoatdong',()=>{off();$$('.wk',w).forEach((x,i)=>later(()=>x.classList.add('on'),1400+i*160))},off);
}

/* ================= sinh viên ngoại ngữ: thẻ song ngữ, tám di sản ================= */
const BI=[['Ẩm thực','Cuisine'],['Ca Huế','Hue folk singing'],['Nón lá','Conical hat'],['Di sản','Heritage'],['Nhã nhạc','Royal court music']];
function langInit(){
 const box=$('#bil');
 box.innerHTML=BI.map(b=>`<div class="bc" tabindex="0" role="button"><div class="fi"><div class="ff">${esc(b[0])}</div><div class="fb">${esc(b[1])}</div></div></div>`).join('');
 tabs($('[data-tabs="lang"]'),(t,silent)=>{if(!silent)$$('.bc',box).forEach((c,i)=>setTimeout(()=>c.classList.toggle('en',t==='en'),i*110))});
 box.addEventListener('click',e=>{const c=e.target.closest('.bc');if(c){c.classList.toggle('en');sfx.tick()}});
 const dots=$('#dots8');dots.innerHTML='<i></i>'.repeat(8);
 on('s-ngoaingu',()=>{$$('i',dots).forEach((d,i)=>later(()=>d.classList.add('on'),1400+i*200))},()=>$$('i',dots).forEach(d=>d.classList.remove('on')));
}

/* ================= công nghệ: trò chơi kiểm tra chính tả ================= */
const QZ=[
 {q:'Hai bạn cùng ___ lịch học để hoàn thành bài tập nhóm.',o:['sắp xếp','sắp sếp'],a:0,e:'“Xếp” viết với x. “Sếp” là cách gọi người đứng đầu.'},
 {q:'Em xin phép ___ lại bài viết trước khi nộp.',o:['sửa','sữa'],a:0,e:'“Sửa” (dấu hỏi) là chỉnh cho đúng; “sữa” (dấu ngã) là chất lỏng để uống.'},
 {q:'Cô ấy luôn ___ trọng ý kiến của mọi người.',o:['chân','trân'],a:1,e:'“Trân trọng” (tr) là coi quý, coi trọng. “Chân” đi với “chân thành”.'},
 {q:'Bạn ấy ___ tiền để mua sách.',o:['dành dụm','giành dụm'],a:0,e:'“Dành dụm” là tiết kiệm từng chút; “giành” nghĩa là tranh lấy.'},
 {q:'Cậu ấy học rất ___ sắc.',o:['xuất','suất'],a:0,e:'“Xuất sắc” viết với x; “suất” như “suất ăn”, “suất học bổng”.'}];
function quizInit(){
 const box=$('#quiz');let i=0,score=0,locked=false;const res=[];
 const render=()=>{
  if(i>=QZ.length){
   const good=score>=4;
   box.innerHTML=`<div class="qres"><h3>Kết quả</h3><b>${score}/${QZ.length}</b><p>${score===QZ.length?'Tuyệt đối! Bạn đúng cả 5 câu.':good?'Rất tốt! Chỉ còn một chút nữa là hoàn hảo.':'Cố lên! Chơi lại để nhớ các cặp dễ nhầm nhé.'}</p><div class="row" style="justify-content:center"><button class="btn pri" id="qAgain">Chơi lại</button></div></div>`;
   $('#qAgain').onclick=()=>{i=0;score=0;res.length=0;render()};
   if(good){fx.confetti();sfx.ok()}return}
  const q=QZ[i];
  box.innerHTML=`<h3>Thử một ván chính tả</h3><div class="qtop">${QZ.map((_,k)=>`<i class="${res[k]===1?'ok':res[k]===0?'no':k===i?'cur':''}"></i>`).join('')}</div><div class="qq">${esc(q.q).replace('___','<u>&nbsp;&nbsp;&nbsp;&nbsp;</u>')}</div><div class="qo">${q.o.map((o,k)=>`<button data-k="${k}">${esc(o)}</button>`).join('')}</div><div class="qfb"></div>`;
  locked=false};
 box.addEventListener('click',e=>{
  const b=e.target.closest('.qo button');if(!b||locked)return;locked=true;
  const q=QZ[i],k=+b.dataset.k,ok=k===q.a;
  $$('.qo button',box).forEach((x,j)=>{x.disabled=true;if(j===q.a)x.classList.add('ok');else if(j===k)x.classList.add('no')});
  res[i]=ok?1:0;
  if(ok){score++;sfx.ok();const r=b.getBoundingClientRect();fx.burst(r.left+r.width/2,r.top,14,{sp:5,r:7})}else sfx.bad();
  $('.qfb',box).innerHTML=`<b>${ok?'Chính xác! ':'Chưa đúng. '}</b>${esc(q.e)} <button class="btn mini pri" id="qNext">${i<QZ.length-1?'Câu tiếp':'Xem kết quả'}</button>`;
  $('#qNext').onclick=()=>{i++;render()}});
 render();
 on('s-congnghe',()=>{i=0;score=0;res.length=0;render()});
}

/* ================= 21 ngày viết rõ ================= */
function d21Init(){
 const box=$('#days'),ring=$('#ring21'),num=$('#d21'),info=$('#dayInfo'),C=314.16;
 const WK=['Tuần 1: nhận diện lỗi','Tuần 2: luyện viết và sửa chéo','Tuần 3: tạo sản phẩm'];let timer=null;
 box.innerHTML=Array.from({length:21},(_,i)=>`<button class="dy w${Math.floor(i/7)+1}" data-i="${i}">${i+1}</button>`).join('');
 const upd=()=>{
  const k=$$('.dy.on',box).length;num.textContent=k;ring.style.strokeDashoffset=C*(1-k/21);
  ring.style.stroke=k>14?'#2E6B4E':k>7?'#D99A00':'#C1121F';
  $$('.weeks li').forEach((li,w)=>li.classList.toggle('hot',k>0&&Math.floor((k-1)/7)===w));return k};
 const finish=()=>{fx.fire(4);toast('Hoàn thành 21 ngày viết rõ!')};
 box.addEventListener('click',e=>{const d=e.target.closest('.dy');if(!d)return;d.classList.toggle('on');sfx.tick();if(upd()===21)finish()});
 box.addEventListener('pointerover',e=>{const d=e.target.closest('.dy');if(d)info.textContent=`Ngày ${+d.dataset.i+1} · ${WK[Math.floor(d.dataset.i/7)]}`});
 const clr=()=>{clearInterval(timer);$$('.dy',box).forEach(d=>d.classList.remove('on'));upd()};
 $('#play21').addEventListener('click',()=>{
  clr();let i=0;
  timer=setInterval(()=>{const d=$$('.dy',box)[i++];if(!d){clearInterval(timer);return}
   d.classList.add('on');sfx.tick();const r=d.getBoundingClientRect();fx.burst(r.left+r.width/2,r.top+r.height/2,3,{sp:3,r:5});
   if(upd()===21){clearInterval(timer);finish()}},170)});
 $('#reset21').addEventListener('click',clr);
 on('s-21ngay',()=>{},clr);
}

/* ================= quỹ đạo hỗ trợ ================= */
const ORB=[
 {i:'🧑‍🏫',n:'Giảng viên',d:'Góp ý chuyên môn cho nội dung và cách trình bày.',a:0,r:'o'},
 {i:'🏫',n:'Lớp, khoa, câu lạc bộ',d:'Hỗ trợ không gian và truyền thông khi cần.',a:120,r:'o'},
 {i:'🤝',n:'Đoàn – Hội',d:'Phối hợp để có địa điểm, cố vấn và phần thưởng nhỏ.',a:240,r:'o'},
 {i:'✍️',n:'Khoa Ngữ văn, Báo chí',d:'Phối hợp để có cố vấn chuyên môn về ngôn ngữ và truyền thông.',a:60,r:'i'},
 {i:'📚',n:'Thư viện',d:'Phối hợp để có địa điểm tổ chức; nơi đặt bản in nhỏ của sổ tay.',a:240,r:'i'}];
function orbitInit(){
 const box=$('#orbit'),info=$('#orbInfo');
 const arm=(o,k)=>`<div class="arm${o.r==='i'?' i':''}" style="--a:${o.a}deg"><div class="nd" tabindex="0" role="button" data-k="${k}"><i>${o.i}</i>${esc(o.n)}</div></div>`;
 box.innerHTML='<div class="core">Sinh viên<small>chủ thể</small></div>'+ORB.map(arm).join('');
 const show=k=>{
  const o=ORB[k];$$('.nd',box).forEach((n,j)=>n.classList.toggle('on',j===k));
  info.innerHTML=`<h3>${esc(o.n)}</h3><p>${esc(o.d)}</p>`;info.classList.remove('pp');void info.offsetWidth;info.classList.add('pp');sfx.pop()};
 box.addEventListener('click',e=>{const n=e.target.closest('.nd');if(n)show(+n.dataset.k)});
 box.addEventListener('pointerover',e=>{const n=e.target.closest('.nd');if(n&&!n.classList.contains('on'))show(+n.dataset.k)});
}

/* ================= tài liệu tham khảo (lọc không dấu) và cảm ơn ================= */
const REF=[
 'Bách khoa toàn thư Việt Nam, tập 1 (khái niệm chữ Quốc ngữ).',
 'Marketer REVU Vietnam, “Influencer Marketing Việt Nam 2026…” (tổng hợp từ Digital Vietnam 2026).',
 'We Are Social, Vietnam Digital 2024.',
 '“Giữ tiếng Việt trong nhịp sống số”, Báo Nhân Dân.',
 '“Ngôn ngữ ‘teen’ và giữ gìn sự trong sáng của tiếng Việt cho học sinh…”, ĐHQG Hà Nội.',
 'Nghiên cứu về ngôn ngữ mạng, teencode với sinh viên, Cổng thông tin KH&CN quốc gia.',
 'Nguyễn Ngọc Quang, Hoàng Quốc, “Biến thể ngôn ngữ trong phong cách khẩu ngữ của học sinh THPT…”, 2023.',
 '“Giao lưu chuyên đề ‘Tiếng Việt – cho hôm nay, cho ngày mai!’”, Báo Văn hóa.',
 '“‘Tiếng Việt trong tim con’…”, VietnamPlus (nhắc Ngày tôn vinh tiếng Việt và Ngày Văn hóa Việt Nam 24/11).',
 '“Phát động cuộc thi Tìm kiếm Sứ giả tiếng Việt ở nước ngoài năm 2023”, Báo Pháp luật Việt Nam.',
 '“Hơn 1.000 sinh viên tham gia Lễ hội Chữ Hàn 2024”, Báo Văn hóa.'];
function refsInit(){
 const ul=$('#refs'),q=$('#refQ');
 ul.innerHTML=REF.map(r=>`<li>${esc(r)}</li>`).join('');
 const norm=s=>s.toLowerCase().normalize('NFD').replace(/[\u0300-\u036f]/g,'').replace(/đ/g,'d');
 q.addEventListener('input',()=>{const v=norm(q.value.trim());$$('li',ul).forEach(li=>li.classList.toggle('hide',!!v&&!norm(li.textContent).includes(v)))});
}
function thanksInit(){on('s-camon',()=>later(()=>fx.fire(5),900));$('#fireBtn').addEventListener('click',()=>fx.fire(6))}

/* ================= khởi tạo ================= */
function init(){
 S.forEach((s,i)=>scenery(s,i));
 S.filter(s=>['s-hero','c1','c2','c3','s-camon'].includes(s.id)).forEach(s=>lanterns(s,[[60,50,0],[68,120,-1.1],[76,80,-2.3]]));
 $$('[data-drum]').forEach(buildDrum);
 ['.conds','.how4','.fmts','.mini5','.mini4','.five','.defects'].forEach(sel=>$$(sel).forEach(g=>[...g.children].forEach((c,k)=>c.style.setProperty('--k',k))));
 on('s-lydo',()=>later(()=>playChat($('#chat-lydo'),SC.lydo),900));
 on('s-giugin',()=>later(()=>playChat($('#chat-yn'),SC.yn),1300));
 on('s-ketluan',()=>later(()=>playChat($('#chat-kl'),SC.kl),1100));
 on('s-ngoaingu',()=>later(()=>playChat($('#chat-nn'),SC.nn),900));
 buildMenu();heroInit();toneInit();tlInit();morphInit();
 accInit($('#acc1'),'.ap');accInit($('#split'),'.sp');dutyInit();surveyInit();
 buildGauges();buildBars($('#bars'),BA);sortInit();ripInit();causesInit();todoInit();
 nbInit();gtInit();mxhInit();composeInit();actInit();langInit();quizInit();d21Init();orbitInit();refsInit();thanksInit();
 $$('[data-tabs=""]').forEach(panelTabs);
 addEventListener('resize',()=>$$('[data-tabs]').forEach(t=>t._set&&t._set()));
 if(document.fonts&&document.fonts.ready)document.fonts.ready.then(()=>$$('[data-tabs]').forEach(t=>t._set&&t._set()));
 const h=location.hash.slice(1);go(Math.max(0,S.findIndex(s=>s.id===h)));
}
init();
})();
</script>
</body></html>
