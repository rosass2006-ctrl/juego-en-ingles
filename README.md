<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>English Grammar Quest</title>
<link href="https://fonts.googleapis.com/css2?family=Exo+2:wght@300;400;600;700;900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
:root {
  --c: #00ffe7;
  --m: #ff2d78;
  --y: #ffe600;
  --p: #bf5fff;
  --b: #050510;
  --panel: rgba(255,255,255,0.035);
  --border: rgba(0,255,231,0.18);
  --glow-c: rgba(0,255,231,0.45);
  --glow-m: rgba(255,45,120,0.45);
}
*{margin:0;padding:0;box-sizing:border-box}
html,body{width:100%;height:100%;overflow:hidden}
body{font-family:'Exo 2',sans-serif;background:var(--b);color:#fff;}

body::before{
  content:'';position:fixed;inset:0;z-index:999;pointer-events:none;
  background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,0,0,0.08) 2px,rgba(0,0,0,0.08) 4px);
  animation:scanMove 8s linear infinite;
}
@keyframes scanMove{0%{background-position:0 0}100%{background-position:0 100px}}

.bg{position:fixed;inset:0;z-index:0;overflow:hidden}
.bg-hex{
  position:absolute;inset:-10%;
  background-image:
    radial-gradient(circle at 20% 20%, rgba(191,95,255,0.18) 0%,transparent 45%),
    radial-gradient(circle at 80% 80%, rgba(0,255,231,0.15) 0%,transparent 45%),
    radial-gradient(circle at 50% 50%, rgba(255,45,120,0.1) 0%,transparent 60%);
  animation:bgDrift 12s ease-in-out infinite alternate;
}
@keyframes bgDrift{0%{transform:scale(1) rotate(0deg)}100%{transform:scale(1.1) rotate(3deg)}}
.bg-grid{
  position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(0,255,231,0.04) 1px,transparent 1px),
    linear-gradient(90deg,rgba(0,255,231,0.04) 1px,transparent 1px);
  background-size:60px 60px;
  animation:gridSlide 25s linear infinite;
}
@keyframes gridSlide{0%{background-position:0 0}100%{background-position:60px 60px}}

.bg-lines{position:absolute;inset:0;overflow:hidden}
.speed-line{position:absolute;height:1px;background:linear-gradient(90deg,transparent,var(--c),transparent);animation:speedLine linear infinite;opacity:0;}
@keyframes speedLine{0%{left:-20%;opacity:0}10%{opacity:1}90%{opacity:0.6}100%{left:110%;opacity:0}}

.particle{position:absolute;border-radius:50%;pointer-events:none;animation:particleFloat linear infinite;opacity:0;}
@keyframes particleFloat{0%{transform:translateY(110vh) scale(0);opacity:0}5%{opacity:1}95%{opacity:0.7}100%{transform:translateY(-10vh) scale(1.5);opacity:0}}

/* ══ SCREENS ══ */
.screen{
  position:relative;z-index:10;width:100%;height:100vh;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  padding:20px;overflow-y:auto;
}
.hidden{display:none!important}

/* ══ INICIO ══ */
#inicio{justify-content:flex-start;padding-top:90px}
.logo-wrap{text-align:center;margin-bottom:30px;width:100%}
.logo-eyebrow{
  font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:10px;
  color:var(--c);opacity:0.7;margin-bottom:12px;position:relative;display:inline-block;
}
.logo-eyebrow::before,.logo-eyebrow::after{content:'';position:absolute;top:50%;width:30px;height:1px;background:var(--c);opacity:0.5;}
.logo-eyebrow::before{right:calc(100% + 12px)}
.logo-eyebrow::after{left:calc(100% + 12px)}
.logo-title{font-size:clamp(32px,5.5vw,72px);font-weight:900;line-height:0.88;letter-spacing:-2px;position:inherit;display:block;width:100%;text-align:center;}
.logo-title .line1{display:block;-webkit-text-stroke:2px var(--c);color:transparent;text-shadow:0 0 40px var(--glow-c),0 0 80px rgba(0,255,231,0.3);animation:titleFlicker 5s infinite;}
@keyframes titleFlicker{0%,96%,100%{opacity:1}97%{opacity:0.6}98%{opacity:1}99%{opacity:0.7}}
.logo-title .line2{display:block;background:linear-gradient(90deg,var(--m),var(--y),var(--c));-webkit-background-clip:text;-webkit-text-fill-color:transparent;filter:drop-shadow(0 0 20px var(--m));animation:gradientShift 4s linear infinite;background-size:200% 100%;}
@keyframes gradientShift{0%{background-position:0% 50%}100%{background-position:200% 50%}}
.logo-title .line3{display:block;color:var(--y);-webkit-text-stroke:1px var(--y);text-shadow:0 0 30px rgba(255,230,0,0.7);}
.logo-tag{font-family:'Share Tech Mono',monospace;font-size:13px;letter-spacing:6px;color:rgba(255,255,255,0.35);margin-top:14px;}
.logo-tag {
  margin-top: 25px !important; /* Aumenta este valor según necesites */
}
/* ══ NOMBRE ══ */
.input-wrap{position:relative;margin:8px 0}
.input-label{font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:4px;color:var(--c);opacity:0.6;margin-bottom:8px;display:block;}
input[type="text"]{
  width:340px;padding:15px 20px;font-size:16px;font-family:'Exo 2',sans-serif;font-weight:600;
  background:rgba(0,255,231,0.06);border:1.5px solid rgba(0,255,231,0.3);
  border-radius:10px;color:#fff;outline:none;letter-spacing:1px;transition:all 0.3s;
}
input[type="text"]:focus{border-color:var(--c);background:rgba(0,255,231,0.07);box-shadow:0 0 0 3px rgba(0,255,231,0.08),0 0 30px rgba(0,255,231,0.15);}
input[type="text"]::placeholder{color:rgba(255,255,255,0.2)}
.welcome-back{
  font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:3px;
  color:var(--c);margin-bottom:6px;text-align:center;opacity:0.8;
}

/* ══ NIVEL SELECTOR ══ */
.level-selector{display:flex;gap:14px;margin:14px 0}
.level-card{
  width:118px;padding:18px 10px;border-radius:14px;cursor:pointer;text-align:center;
  transition:all 0.3s;background:rgba(255,255,255,0.03);border:1.5px solid rgba(255,255,255,0.1);
  position:relative;overflow:hidden;
}
.level-card::after{content:'';position:absolute;inset:0;opacity:0;transition:opacity 0.3s;background:radial-gradient(circle at 50% 0%,currentColor 0%,transparent 70%);}
.level-card:hover::after,.level-card.active::after{opacity:0.12}
.level-card:hover,.level-card.active{transform:translateY(-4px)}
.lv-easy{color:var(--c);border-color:rgba(0,255,231,0.3)}
.lv-easy.active,.lv-easy:hover{border-color:var(--c);box-shadow:0 0 24px rgba(0,255,231,0.35),inset 0 0 24px rgba(0,255,231,0.06),0 8px 30px rgba(0,255,231,0.2)}
.lv-med{color:var(--y);border-color:rgba(255,230,0,0.3)}
.lv-med.active,.lv-med:hover{border-color:var(--y);box-shadow:0 0 24px rgba(255,230,0,0.35),inset 0 0 24px rgba(255,230,0,0.06),0 8px 30px rgba(255,230,0,0.2)}
.lv-hard{color:var(--m);border-color:rgba(255,45,120,0.3)}
.lv-hard.active,.lv-hard:hover{border-color:var(--m);box-shadow:0 0 24px rgba(255,45,120,0.35),inset 0 0 24px rgba(255,45,120,0.06),0 8px 30px rgba(255,45,120,0.2)}
.lv-icon{font-size:30px;margin-bottom:8px}
.lv-name{font-family:'Share Tech Mono',monospace;font-size:12px;font-weight:700;letter-spacing:3px}
.lv-pts{font-size:11px;margin-top:5px;opacity:0.6;letter-spacing:1px}

/* Botón start */
.start-btn{
  padding:16px 28px;margin-top:14px;
  font-family:'Share Tech Mono',monospace;font-size:15px;letter-spacing:5px;
  border:none;border-radius:10px;cursor:pointer;position:relative;overflow:hidden;
  background:linear-gradient(90deg,var(--m),var(--p),var(--c));background-size:200% 100%;
  color:#050510;font-weight:700;transition:all 0.3s;
  box-shadow:0 4px 30px rgba(255,45,120,0.4),0 0 60px rgba(0,255,231,0.15);
  animation:btnGlow 3s ease-in-out infinite alternate;
  width:auto;max-width:340px;
}
@keyframes btnGlow{
  0%{box-shadow:0 4px 30px rgba(255,45,120,0.4),0 0 60px rgba(0,255,231,0.15);background-position:0% 50%}
  100%{box-shadow:0 4px 50px rgba(0,255,231,0.5),0 0 80px rgba(191,95,255,0.2);background-position:100% 50%}
}
.start-btn::before{content:'';position:absolute;top:0;left:-100%;width:60%;height:100%;background:linear-gradient(90deg,transparent,rgba(255,255,255,0.25),transparent);transform:skewX(-20deg);animation:btnShine 2.5s infinite;}
@keyframes btnShine{0%{left:-100%}35%{left:150%}100%{left:150%}}
.start-btn:hover{transform:scale(1.04) translateY(-2px);letter-spacing:6px}
.start-btn:active{transform:scale(0.98)}

/* ══ INTRO SCREEN ══ */
.intro-box{
  width:100%;max-width:720px;padding:40px 44px;
  background:rgba(0,0,0,0.72);border:1.5px solid var(--border);border-radius:24px;
  backdrop-filter:blur(30px);position:relative;overflow:hidden;
  box-shadow:0 20px 60px rgba(0,0,0,0.7),0 0 60px rgba(0,255,231,0.08);
  max-height:85vh;overflow-y:auto;
}
.intro-box::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--c),var(--p),var(--m),transparent);animation:hudLine 3s linear infinite;background-size:200% 100%;}
@keyframes hudLine{0%{background-position:0%}100%{background-position:200%}}
.intro-title{
  font-family:'Share Tech Mono',monospace;font-size:22px;letter-spacing:5px;font-weight:700;
  text-align:center;margin-bottom:6px;
  background:linear-gradient(90deg,var(--c),var(--p),var(--m));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-size:200%;animation:gradientShift 3s linear infinite;
}
.intro-subtitle{font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:4px;color:rgba(255,255,255,0.3);text-align:center;margin-bottom:28px;}
.intro-topics{display:flex;flex-direction:column;gap:12px;margin-bottom:28px;}
.intro-topic{
  display:flex;align-items:flex-start;gap:16px;padding:18px 22px;
  background:rgba(255,255,255,0.05);border:1.5px solid rgba(0,255,231,0.15);border-radius:14px;
  transition:all 0.3s;
}
.intro-topic:hover{background:rgba(0,255,231,0.04);border-color:rgba(0,255,231,0.2);}
.topic-num{
  font-family:'Share Tech Mono',monospace;font-size:22px;font-weight:700;color:var(--c);
  min-width:40px;line-height:1;opacity:0.7;
}
.topic-info{}
.topic-name{font-family:'Share Tech Mono',monospace;font-size:13px;font-weight:700;letter-spacing:2px;color:var(--c);margin-bottom:4px;}
.topic-desc{font-size:13px;color:rgba(255,255,255,0.65);line-height:1.6;}
.topic-subs{display:flex;gap:6px;margin-top:8px;flex-wrap:wrap;}
.sub-tag{
  font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:2px;
  padding:3px 10px;border-radius:20px;
  background:rgba(0,255,231,0.08);color:var(--c);border:1px solid rgba(0,255,231,0.2);
}
.continue-btn{
  width:100%;padding:15px;font-family:'Share Tech Mono',monospace;font-size:13px;
  letter-spacing:5px;border:none;border-radius:12px;cursor:pointer;font-weight:700;
  background:linear-gradient(90deg,var(--c),var(--p));color:#050510;
  box-shadow:0 4px 25px rgba(0,255,231,0.35);transition:all 0.3s;
}
.continue-btn:hover{transform:scale(1.03) translateY(-2px);box-shadow:0 8px 35px rgba(0,255,231,0.5);}
.continue-btn:active{transform:scale(0.98)}

/* ══ TOPIC SELECTOR ══ */
.topic-selector-box{
  width:100%;max-width:700px;padding:36px 40px;
  background:rgba(0,0,0,0.72);border:1.5px solid var(--border);border-radius:24px;
  backdrop-filter:blur(30px);position:relative;overflow:hidden;
  box-shadow:0 20px 60px rgba(0,0,0,0.7);
  max-height:88vh;overflow-y:auto;
}
.topic-selector-box::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--c),var(--p),var(--m),transparent);animation:hudLine 3s linear infinite;background-size:200% 100%;}
.ts-header{text-align:center;margin-bottom:22px;}
.ts-greeting{font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:4px;color:var(--c);opacity:0.7;margin-bottom:6px;}
.ts-title{font-family:'Share Tech Mono',monospace;font-size:20px;letter-spacing:5px;font-weight:700;background:linear-gradient(90deg,var(--c),var(--p));-webkit-background-clip:text;-webkit-text-fill-color:transparent;margin-bottom:4px;}
.ts-level{font-size:11px;letter-spacing:3px;color:rgba(255,255,255,0.3);}

.topics-grid{display:flex;flex-direction:column;gap:10px;}
.topic-card{
  border-radius:14px;cursor:pointer;overflow:hidden;
  border:1.5px solid rgba(0,255,231,0.15);
  background:rgba(255,255,255,0.04);transition:all 0.3s;
}
.topic-card:hover{border-color:rgba(0,255,231,0.35);background:rgba(0,255,231,0.04);transform:translateX(5px);}
.topic-card-header{
  display:flex;align-items:center;gap:14px;padding:16px 20px;cursor:pointer;
}
.topic-card-icon{font-size:24px;min-width:36px;text-align:center;}
.topic-card-title{font-family:'Share Tech Mono',monospace;font-size:13px;font-weight:700;letter-spacing:2px;color:var(--c);}
.topic-card-sub{font-size:12px;color:rgba(255,255,255,0.4);margin-top:2px;letter-spacing:1px;}
.topic-card-arrow{margin-left:auto;font-size:18px;color:var(--c);opacity:0.5;transition:transform 0.3s;}
.topic-card.open .topic-card-arrow{transform:rotate(90deg)}

.sub-topics{
  display:none;padding:0 20px 14px;
  display:none;
  gap:8px;flex-direction:column;
}
.topic-card.open .sub-topics{display:flex;}
.sub-topic-btn{
  padding:12px 18px;border-radius:10px;cursor:pointer;
  background:rgba(0,0,0,0.25);border:1.5px solid rgba(0,255,231,0.2);
  font-family:'Share Tech Mono',monospace;font-size:12px;letter-spacing:2px;
  color:rgba(255,255,255,0.8);transition:all 0.25s;text-align:left;
  display:flex;align-items:center;gap:10px;
}
.sub-topic-btn::before{content:'▶';font-size:9px;color:var(--c);opacity:0.6;}
.sub-topic-btn:hover{background:rgba(0,255,231,0.08);border-color:var(--c);color:#fff;transform:translateX(6px);}
.sub-topic-btn:active{transform:scale(0.98)}

/* ══ SUB-TOPIC INTRO ══ */
.subtopic-intro-box{
  width:100%;max-width:660px;padding:40px 44px;
  background:rgba(0,0,0,0.72);border:1.5px solid var(--border);border-radius:24px;
  backdrop-filter:blur(30px);position:relative;overflow:hidden;
  box-shadow:0 20px 60px rgba(0,0,0,0.7);
  max-height:88vh;overflow-y:auto;
}
.subtopic-intro-box::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--c),var(--p),var(--m),transparent);animation:hudLine 3s linear infinite;background-size:200% 100%;}
.si-eyebrow{font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:5px;color:var(--p);opacity:0.7;margin-bottom:10px;}
.si-title{font-family:'Share Tech Mono',monospace;font-size:20px;font-weight:700;letter-spacing:3px;color:var(--c);margin-bottom:6px;}
.si-subtitle{font-family:'Share Tech Mono',monospace;font-size:13px;letter-spacing:3px;color:var(--y);margin-bottom:20px;}
.si-body{font-size:15px;line-height:1.8;color:rgba(255,255,255,0.78);margin-bottom:20px;}
.si-examples{
  background:rgba(0,0,0,0.4);border-left:3px solid var(--c);
  border-radius:0 12px 12px 0;padding:16px 20px;margin-bottom:22px;
}
.si-ex-title{font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:4px;color:var(--c);margin-bottom:10px;opacity:0.7;}
.si-ex-item{font-size:13px;color:rgba(255,255,255,0.65);margin-bottom:6px;font-family:'Share Tech Mono',monospace;letter-spacing:0.5px;}
.si-ex-item span{color:var(--y);}
.si-tip{
  display:flex;gap:12px;align-items:flex-start;padding:14px 16px;margin-bottom:24px;
  background:rgba(191,95,255,0.06);border:1px solid rgba(191,95,255,0.2);border-radius:12px;
}
.si-tip-icon{font-size:18px;}
.si-tip-text{font-size:12px;color:rgba(255,255,255,0.55);line-height:1.6;}
.si-btn-row{display:flex;gap:12px;}
.si-back-btn{
  padding:13px 22px;font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:3px;
  border-radius:10px;cursor:pointer;border:1.5px solid rgba(255,255,255,0.15);
  background:rgba(255,255,255,0.04);color:rgba(255,255,255,0.6);transition:all 0.2s;
}
.si-back-btn:hover{background:rgba(255,255,255,0.08);color:#fff;}
.si-play-btn{
  flex:1;padding:15px;font-family:'Share Tech Mono',monospace;font-size:13px;letter-spacing:4px;
  border:none;border-radius:10px;cursor:pointer;font-weight:700;
  background:linear-gradient(90deg,var(--c),var(--p));color:#050510;
  box-shadow:0 4px 25px rgba(0,255,231,0.3);transition:all 0.3s;
}
.si-play-btn:hover{transform:scale(1.03);box-shadow:0 8px 35px rgba(0,255,231,0.5);}

/* ══ HUD ══ */
.hud{
  display:flex;align-items:center;justify-content:space-between;
  width:100%;max-width:900px;padding:16px 26px;margin-bottom:12px;gap:20px;
  background:rgba(0,0,0,0.62);border:1.5px solid var(--border);border-radius:16px;
  backdrop-filter:blur(20px);box-shadow:0 0 30px rgba(0,0,0,0.5),inset 0 1px 0 rgba(255,255,255,0.06);
  position:relative;overflow:hidden;flex-wrap:wrap;justify-content:center;
}
.hud::before{content:'';position:absolute;bottom:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--c),var(--p),var(--m),transparent);animation:hudLine 3s linear infinite;background-size:200% 100%;}
.hud-item{display:flex;flex-direction:column;align-items:center;gap:3px}
.hud-label{font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:3px;color:rgba(255,255,255,0.3)}
.hud-value{font-family:'Share Tech Mono',monospace;font-size:19px;font-weight:700;color:var(--c)}
.hud-value.gold{color:var(--y);font-size:24px;text-shadow:0 0 20px rgba(255,230,0,0.5)}
.hud-value.pink{color:var(--m)}
.hud-controls{display:flex;gap:10px;margin-left:auto;margin-right:20px}
.control-btn{padding:10px 14px;font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:2px;
  border-radius:8px;cursor:pointer;border:1.5px solid rgba(255,255,255,0.2);background:rgba(255,255,255,0.05);
  color:rgba(255,255,255,0.7);transition:all 0.3s;font-weight:600}
.control-btn:hover{background:rgba(255,255,255,0.1);border-color:rgba(255,255,255,0.4);color:#fff}
.control-btn.pause{border-color:var(--c);color:var(--c);background:rgba(0,255,231,0.1)}
.control-btn.abandon{border-color:var(--m);color:var(--m);background:rgba(255,45,120,0.1)}

.timer-wrap{position:relative;width:64px;height:64px}
.timer-wrap svg{position:absolute;inset:0;transform:rotate(-90deg)}
.timer-bg{fill:none;stroke:rgba(255,255,255,0.08);stroke-width:5}
.timer-fg{fill:none;stroke:var(--c);stroke-width:5;stroke-linecap:round;transition:stroke-dashoffset 1s linear,stroke 0.4s}
.timer-num{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-family:'Share Tech Mono',monospace;font-size:17px;font-weight:700;color:var(--c);transition:color 0.4s;}

.progress-wrap{width:100%;max-width:780px;margin-bottom:10px}
.progress-track{height:5px;background:rgba(255,255,255,0.08);border-radius:4px;overflow:hidden;box-shadow:inset 0 1px 3px rgba(0,0,0,0.5);}
.progress-fill{height:100%;border-radius:4px;background:linear-gradient(90deg,var(--c),var(--p),var(--m));background-size:200% 100%;transition:width 0.6s cubic-bezier(0.34,1.56,0.64,1);box-shadow:0 0 12px var(--glow-c);animation:progressGlow 2s linear infinite;}
@keyframes progressGlow{0%{background-position:0%}100%{background-position:200%}}
.progress-info{display:flex;justify-content:space-between;font-family:'Share Tech Mono',monospace;font-size:10px;color:rgba(255,255,255,0.25);margin-top:5px;letter-spacing:2px;}

.question-box{
  width:100%;max-width:780px;padding:24px 30px;margin-bottom:12px;
  background:rgba(0,0,0,0.52);border:1.5px solid var(--border);border-radius:18px;
  backdrop-filter:blur(20px);position:relative;overflow:hidden;box-shadow:0 8px 40px rgba(0,0,0,0.4);
}
.question-box::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px;background:linear-gradient(180deg,var(--c),var(--p),var(--m));border-radius:3px 0 0 3px;}
.question-box::after{content:'';position:absolute;inset:0;border-radius:18px;background:radial-gradient(ellipse at 0% 50%,rgba(0,255,231,0.04) 0%,transparent 60%);pointer-events:none;}
.q-label{font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:4px;color:var(--p);margin-bottom:8px;opacity:0.8;}
.q-topic-tag{font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:3px;color:rgba(255,255,255,0.3);margin-bottom:4px;}
#question{font-size:clamp(16px,2.2vw,22px);font-weight:600;line-height:1.6;color:rgba(255,255,255,0.95);}
.q-hint{margin-top:10px;font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:3px;color:rgba(255,255,255,0.38)}

.options-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;width:100%;max-width:780px;}
.option-btn{
  padding:15px 19px;font-family:'Exo 2',sans-serif;font-size:15px;font-weight:600;letter-spacing:0.5px;
  background:rgba(255,255,255,0.05);border:1.5px solid rgba(0,255,231,0.2);
  border-radius:12px;color:rgba(255,255,255,0.88);cursor:pointer;transition:all 0.2s;
  text-align:left;position:relative;overflow:hidden;
}
.option-btn::before{content:'';position:absolute;inset:0;opacity:0;background:linear-gradient(90deg,rgba(0,255,231,0.08),transparent);transition:opacity 0.2s;}
.option-btn:hover:not(:disabled)::before{opacity:1}
.option-btn:hover:not(:disabled){border-color:rgba(0,255,231,0.5);background:rgba(0,255,231,0.06);transform:translateX(5px);box-shadow:0 0 20px rgba(0,255,231,0.1),4px 0 0 var(--c);color:#fff;}
.opt-letter{display:inline-flex;align-items:center;justify-content:center;width:26px;height:26px;border-radius:7px;background:rgba(0,255,231,0.12);font-family:'Share Tech Mono',monospace;font-size:12px;color:var(--c);margin-right:10px;flex-shrink:0;border:1px solid rgba(0,255,231,0.2);}
.option-btn.correct{border-color:var(--c)!important;background:rgba(0,255,231,0.12)!important;box-shadow:0 0 30px rgba(0,255,231,0.25),4px 0 0 var(--c)!important;color:#fff!important;}
.option-btn.wrong{border-color:var(--m)!important;background:rgba(255,45,120,0.12)!important;box-shadow:0 0 20px rgba(255,45,120,0.2)!important;}
.option-btn:disabled{cursor:not-allowed;opacity:0.7}

#result{min-height:36px;font-family:'Share Tech Mono',monospace;font-size:13px;letter-spacing:2px;text-align:center;padding:6px;animation:fadeIn 0.3s ease;}
@keyframes fadeIn{from{opacity:0;transform:translateY(-5px)}to{opacity:1;transform:none}}

/* ══ ROBOT ══ */
.char-wrap{position:fixed;bottom:0;right:24px;width:130px;height:170px;z-index:200;pointer-events:none;transition:transform 0.4s cubic-bezier(0.34,1.56,0.64,1);filter:drop-shadow(0 0 20px rgba(0,255,231,0.3));}
.char-wrap.idle{animation:charIdle 2.8s ease-in-out infinite}
@keyframes charIdle{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}
.char-wrap.correct{animation:charJump 0.7s cubic-bezier(0.34,1.56,0.64,1) forwards}
@keyframes charJump{0%{transform:translateY(0) scale(1)}35%{transform:translateY(-70px) rotate(-8deg) scale(1.15)}65%{transform:translateY(-75px) rotate(8deg) scale(1.2)}85%{transform:translateY(-12px) scale(1.05)}100%{transform:translateY(0) scale(1)}}
.char-wrap.wrong{animation:charShake 0.5s ease forwards}
@keyframes charShake{0%,100%{transform:translateX(0)}20%{transform:translateX(-14px) rotate(-6deg)}40%{transform:translateX(12px) rotate(5deg)}60%{transform:translateX(-8px) rotate(-3deg)}80%{transform:translateX(5px)}}
.char-wrap.timeout{animation:charTimeout 0.6s ease forwards}
@keyframes charTimeout{0%{transform:translateY(0)}50%{transform:translateY(18px) rotate(12deg)}100%{transform:translateY(0) rotate(0)}}
.char-wrap.win{animation:charWin 0.9s cubic-bezier(0.34,1.56,0.64,1) infinite}
@keyframes charWin{0%,100%{transform:translateY(0) scale(1)}50%{transform:translateY(-55px) scale(1.18)}}
.char-wrap.lose{animation:charLose 3s ease-in-out infinite}
@keyframes charLose{0%,100%{transform:translateY(0)}50%{transform:translateY(-6px) rotate(-2deg)}}

.speech-bubble{
  position:fixed;bottom:170px;right:148px;z-index:201;
  background:rgba(5,5,20,0.95);border:1.5px solid var(--c);border-radius:16px 16px 4px 16px;
  padding:10px 14px;font-family:'Share Tech Mono',monospace;font-size:11px;
  color:var(--c);letter-spacing:1px;max-width:160px;text-align:center;pointer-events:none;
  opacity:0;transform:scale(0.7) translateY(10px);transition:all 0.3s cubic-bezier(0.34,1.56,0.64,1);
  box-shadow:0 0 25px rgba(0,255,231,0.25),0 0 50px rgba(0,255,231,0.1);
}
.speech-bubble.show{opacity:1;transform:scale(1) translateY(0)}
.speech-bubble::after{content:'';position:absolute;bottom:-10px;right:14px;border:5px solid transparent;border-top-color:var(--c);}

.top-bar{
  position:fixed;
  top:16px;
  left:50%;
  transform:translateX(-50%);
  z-index:1000;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  width:calc(100% - 32px);
  max-width:760px;
  padding:14px 20px;
  border-radius:16px;
  background:rgba(5,5,20,0.95);
  border:1.5px solid rgba(255,255,255,0.1);
  box-shadow:0 18px 40px rgba(0,0,0,0.3);
}
.score-indicator,
.difficulty-indicator{
  font-family:'Share Tech Mono',monospace;
  font-size:12px;
  color:rgba(255,255,255,0.82);
}
.score-indicator::before{content:'⭐';margin-right:6px;color:var(--y);}
.difficulty-indicator{font-weight:700;color:var(--c);white-space:nowrap;}

.intro-head{display:flex;justify-content:space-between;align-items:flex-start;gap:16px;margin-bottom:18px;flex-wrap:wrap;}
.intro-summary{font-size:15px;color:rgba(255,255,255,0.78);line-height:1.8;margin-bottom:24px;}
.intro-summary p{margin-bottom:14px;}
.intro-summary ul{list-style:none;padding-left:0;display:grid;gap:10px;}
.intro-summary li{position:relative;padding-left:24px;}
.intro-summary li::before{content:'•';position:absolute;left:0;top:0;color:var(--c);font-size:18px;line-height:1;}
.intro-back-btn{padding:10px 18px;font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:2px;border-radius:12px;border:1.5px solid rgba(255,255,255,0.16);background:rgba(255,255,255,0.05);color:#fff;cursor:pointer;transition:all 0.25s;}
.intro-back-btn:hover{background:rgba(0,255,231,0.08);border-color:rgba(0,255,231,0.25);}

.ts-btn-row{display:flex;gap:10px;justify-content:center;padding:16px 0 0 0;border-top:1px solid rgba(255,255,255,0.08);margin-top:16px;flex-wrap:wrap;}
.ts-nav-btn{padding:11px 18px;font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:2px;border-radius:10px;border:1.5px solid rgba(255,255,255,0.12);background:rgba(255,255,255,0.04);color:rgba(255,255,255,0.75);cursor:pointer;transition:all 0.25s;}
.ts-nav-btn:hover{background:rgba(0,255,231,0.06);border-color:rgba(0,255,231,0.3);color:#fff;}
.ts-nav-btn.secondary{border-color:rgba(255,45,120,0.2);background:rgba(255,45,120,0.04);}
.ts-nav-btn.secondary:hover{background:rgba(255,45,120,0.08);border-color:rgba(255,45,120,0.35);}

.star-burst{position:fixed;pointer-events:none;z-index:202;font-size:18px;animation:starFly 1s ease forwards;}
@keyframes starFly{0%{opacity:1;transform:translate(0,0) scale(1.2)}100%{opacity:0;transform:translate(var(--dx),var(--dy)) scale(0.3)}}

.floating-pts{position:fixed;font-family:'Share Tech Mono',monospace;font-size:22px;font-weight:700;pointer-events:none;z-index:100;animation:floatUp 1.5s ease forwards;}
@keyframes floatUp{0%{opacity:1;transform:translateY(0) scale(1.2)}100%{opacity:0;transform:translateY(-90px) scale(0.7)}}

.streak-badge{position:fixed;top:20px;right:20px;z-index:50;display:none;font-family:'Share Tech Mono',monospace;font-size:14px;font-weight:700;padding:8px 18px;border-radius:30px;background:linear-gradient(135deg,var(--y),var(--m));color:#050510;animation:badgePop 0.4s cubic-bezier(0.34,1.56,0.64,1);box-shadow:0 4px 20px rgba(255,230,0,0.4);}
@keyframes badgePop{from{transform:scale(0) rotate(-10deg)}to{transform:scale(1) rotate(0)}}

/* ══ FINAL ══ */
.final-box{
  width:100%;max-width:640px;padding:44px 44px;background:rgba(0,0,0,0.72);
  border:1.5px solid var(--border);border-radius:24px;backdrop-filter:blur(30px);
  text-align:center;position:relative;overflow:hidden;
  box-shadow:0 20px 60px rgba(0,0,0,0.7),0 0 60px rgba(0,255,231,0.08);
}
.final-box::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--c),var(--p),var(--m),transparent);animation:hudLine 3s linear infinite;background-size:200% 100%;}
.final-box::after{content:'';position:absolute;inset:0;background:radial-gradient(ellipse at 50% 0%,rgba(0,255,231,0.05) 0%,transparent 60%);pointer-events:none;}
.trophy-icon{font-size:60px;margin-bottom:12px;display:block;animation:trophyFloat 2s ease-in-out infinite}
@keyframes trophyFloat{0%,100%{transform:translateY(0) rotate(-3deg)}50%{transform:translateY(-14px) rotate(3deg)}}
.final-title{font-family:'Share Tech Mono',monospace;font-size:28px;font-weight:700;letter-spacing:6px;margin-bottom:4px;background:linear-gradient(90deg,var(--c),var(--p),var(--m));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-size:200% 100%;animation:gradientShift 3s linear infinite;}
.final-player{font-size:16px;color:rgba(255,255,255,0.5);letter-spacing:3px;margin-bottom:16px}
.final-topic-tag{font-family:'Share Tech Mono',monospace;font-size:9px;letter-spacing:3px;color:var(--p);margin-bottom:8px;}
.lvl-tag{display:inline-block;padding:4px 14px;border-radius:20px;font-family:'Share Tech Mono',monospace;font-size:10px;font-weight:700;letter-spacing:3px;margin-bottom:20px;}
.tag-easy{background:rgba(0,255,231,0.1);color:var(--c);border:1px solid var(--c)}
.tag-medium{background:rgba(255,230,0,0.1);color:var(--y);border:1px solid var(--y)}
.tag-hard{background:rgba(255,45,120,0.1);color:var(--m);border:1px solid var(--m)}
.stats-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:18px}
.stat-card{padding:16px;background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.08);border-radius:14px;transition:transform 0.3s,box-shadow 0.3s;}
.stat-card:hover{transform:translateY(-3px);box-shadow:0 8px 25px rgba(0,255,231,0.1)}
.stat-val{font-family:'Share Tech Mono',monospace;font-size:28px;font-weight:700;color:var(--c)}
.stat-lbl{font-size:10px;letter-spacing:2px;color:rgba(255,255,255,0.35);margin-top:4px}
.rank-badge{display:inline-block;padding:8px 24px;border-radius:30px;font-family:'Share Tech Mono',monospace;font-size:13px;font-weight:700;letter-spacing:4px;margin-bottom:22px;}
.final-btns{display:flex;gap:12px;justify-content:center;flex-wrap:wrap}
.final-btn{padding:13px 28px;font-family:'Share Tech Mono',monospace;font-size:12px;font-weight:700;letter-spacing:3px;border-radius:10px;cursor:pointer;transition:all 0.2s;border:none;}
.btn-restart{background:linear-gradient(90deg,var(--c),var(--p));color:#050510;box-shadow:0 4px 20px rgba(0,255,231,0.3);}
.btn-restart:hover{transform:scale(1.05) translateY(-2px);box-shadow:0 8px 30px rgba(0,255,231,0.45)}
.btn-restart:active{transform:scale(0.97)}
.btn-exit{background:rgba(255,255,255,0.06);border:1.5px solid rgba(255,45,120,0.3)!important;color:rgba(255,255,255,0.7);}
.btn-exit:hover{background:rgba(255,45,120,0.12);border-color:var(--m)!important;color:#fff;box-shadow:0 4px 20px rgba(255,45,120,0.25);transform:scale(1.03);}
.btn-exit:active{transform:scale(0.97)}

/* ══ GOODBYE ══ */
.goodbye-box{text-align:center;padding:54px 44px;background:rgba(0,0,0,0.72);border:1.5px solid var(--border);border-radius:24px;backdrop-filter:blur(30px);box-shadow:0 20px 60px rgba(0,0,0,0.7);max-width:500px;width:100%;}
.goodbye-icon{font-size:72px;margin-bottom:20px;display:block;animation:trophyFloat 2s ease-in-out infinite}
.goodbye-title{font-family:'Share Tech Mono',monospace;font-size:34px;font-weight:700;letter-spacing:8px;background:linear-gradient(90deg,var(--c),var(--p));-webkit-background-clip:text;-webkit-text-fill-color:transparent;margin-bottom:16px;}
.goodbye-sub{font-size:18px;color:rgba(255,255,255,0.55);line-height:1.9;letter-spacing:1px;}
.goodbye-sub span{color:var(--c);font-weight:700;letter-spacing:3px}

/* ══ PAUSE MODAL ══ */
.pause-modal{display:none;position:fixed;inset:0;background:rgba(0,0,0,0.85);z-index:500;align-items:center;justify-content:center;backdrop-filter:blur(5px)}
.pause-modal.show{display:flex}
.pause-box{background:rgba(0,0,0,0.85);border:2px solid var(--c);border-radius:20px;padding:44px 40px;text-align:center;max-width:400px;
  box-shadow:0 0 60px rgba(0,255,231,0.35);animation:pauseScale 0.3s cubic-bezier(0.34,1.56,0.64,1)}
@keyframes pauseScale{from{transform:scale(0.8);opacity:0}to{transform:scale(1);opacity:1}}
.pause-title{font-family:'Share Tech Mono',monospace;font-size:32px;font-weight:700;color:var(--c);margin-bottom:16px;letter-spacing:3px}
.pause-score{font-family:'Share Tech Mono',monospace;font-size:18px;color:var(--y);margin-bottom:24px;
  padding:16px;background:rgba(255,230,0,0.05);border-radius:12px;border:1px solid rgba(255,230,0,0.2)}
.pause-btns{display:flex;flex-direction:column;gap:12px}
.pause-btn{padding:13px 24px;font-family:'Share Tech Mono',monospace;font-size:13px;letter-spacing:2px;
  border:none;border-radius:10px;cursor:pointer;font-weight:700;transition:all 0.3s}
.btn-resume{background:linear-gradient(90deg,var(--c),var(--p));color:#050510;box-shadow:0 4px 20px rgba(0,255,231,0.3)}
.btn-resume:hover{transform:scale(1.05);box-shadow:0 8px 30px rgba(0,255,231,0.5)}
.btn-abandon-modal{background:rgba(255,45,120,0.15);border:1.5px solid var(--m);color:var(--m)}
.btn-abandon-modal:hover{background:rgba(255,45,120,0.25);box-shadow:0 4px 20px rgba(255,45,120,0.3)}

/* ══ MEDIUM MODE: SELECT 2 PARTS ══ */
.parts-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;width:100%;max-width:780px;margin-top:16px}
.part-label{font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:2px;color:var(--p);margin-bottom:6px;opacity:0.8}
.part-options{display:flex;flex-direction:column;gap:8px}
.part-btn{padding:10px 14px;font-family:'Exo 2',sans-serif;font-size:13px;font-weight:600;
  background:rgba(255,255,255,0.04);border:1.5px solid rgba(255,255,255,0.1);
  border-radius:10px;color:rgba(255,255,255,0.85);cursor:pointer;transition:all 0.2s;
  text-align:left;position:relative;overflow:hidden}
.part-btn:hover:not(.selected):not(:disabled){border-color:rgba(0,255,231,0.5);background:rgba(0,255,231,0.06);transform:translateX(3px);box-shadow:0 0 20px rgba(0,255,231,0.1)}
.part-btn.selected{border-color:var(--c);background:rgba(0,255,231,0.15);box-shadow:0 0 30px rgba(0,255,231,0.25);color:#fff}
.part-btn.correct{border-color:var(--c);background:rgba(0,255,231,0.15);box-shadow:0 0 30px rgba(0,255,231,0.25);color:#fff}
.part-btn.wrong{border-color:var(--m);background:rgba(255,45,120,0.12);box-shadow:0 0 20px rgba(255,45,120,0.2)}

/* ══ HARD MODE: WRITE ANSWERS ══ */
.input-answer{padding:12px 16px;font-family:'Exo 2',sans-serif;font-size:14px;font-weight:600;
  background:rgba(255,255,255,0.04);border:1.5px solid rgba(255,255,255,0.1);
  border-radius:10px;color:#fff;outline:none;letter-spacing:1px;transition:all 0.3px;
  width:100%;max-width:250px}
.input-answer:focus{border-color:var(--c);background:rgba(0,255,231,0.07);box-shadow:0 0 0 3px rgba(0,255,231,0.08),0 0 30px rgba(0,255,231,0.15)}
.input-answer::placeholder{color:rgba(255,255,255,0.2)}

/* ══ SCROLLBAR ══ */
::-webkit-scrollbar{width:5px;}
::-webkit-scrollbar-track{background:rgba(0,0,0,0.2);}
::-webkit-scrollbar-thumb{background:rgba(0,255,231,0.3);border-radius:10px;}
</style>
</head>
<body>

<div class="bg">
  <div class="bg-hex"></div>
  <div class="bg-grid"></div>
  <div class="bg-lines" id="bgLines"></div>
</div>
<div id="particles"></div>

<!-- ══ ROBOT ══ -->
<div class="char-wrap idle" id="charWrap">
  <svg viewBox="0 0 120 160" xmlns="http://www.w3.org/2000/svg" width="130" height="170">
    <defs>
      <filter id="glow"><feGaussianBlur stdDeviation="2" result="c"/><feMerge><feMergeNode in="c"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
      <linearGradient id="bodyGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" style="stop-color:#0f2040"/>
        <stop offset="100%" style="stop-color:#060e1f"/>
      </linearGradient>
    </defs>
    <line x1="60" y1="10" x2="60" y2="28" stroke="#00ffe7" stroke-width="2.5" stroke-linecap="round" filter="url(#glow)"/>
    <circle cx="60" cy="8" r="5" fill="#bf5fff" id="antenna-dot">
      <animate attributeName="r" values="4;6;4" dur="1.5s" repeatCount="indefinite"/>
      <animate attributeName="fill" values="#bf5fff;#00ffe7;#bf5fff" dur="1.5s" repeatCount="indefinite"/>
    </circle>
    <rect x="20" y="26" width="80" height="60" rx="14" fill="url(#bodyGrad)" stroke="#00ffe7" stroke-width="2" filter="url(#glow)"/>
    <rect x="28" y="34" width="64" height="42" rx="8" fill="#000b18" stroke="#0d2540" stroke-width="1.5"/>
    <g id="eye-l-g">
      <circle cx="47" cy="54" r="9" fill="#00080f" id="eye-l-bg"/>
      <circle cx="47" cy="54" r="6" fill="#00ffe7" id="eye-l" opacity="0.9" filter="url(#glow)"/>
      <circle cx="49" cy="52" r="2" fill="white" opacity="0.7"/>
      <path d="M41 54 Q47 46 53 54" fill="#00ff88" stroke="none" id="eye-l-happy" opacity="0" transform="translate(0,4)"/>
      <g id="eye-l-sad" opacity="0">
        <line x1="42" y1="49" x2="52" y2="59" stroke="#ff2d78" stroke-width="3" stroke-linecap="round"/>
        <line x1="52" y1="49" x2="42" y2="59" stroke="#ff2d78" stroke-width="3" stroke-linecap="round"/>
      </g>
    </g>
    <g id="eye-r-g">
      <circle cx="73" cy="54" r="9" fill="#00080f" id="eye-r-bg"/>
      <circle cx="73" cy="54" r="6" fill="#00ffe7" id="eye-r" opacity="0.9" filter="url(#glow)"/>
      <circle cx="75" cy="52" r="2" fill="white" opacity="0.7"/>
      <path d="M67 54 Q73 46 79 54" fill="#00ff88" stroke="none" id="eye-r-happy" opacity="0" transform="translate(0,4)"/>
      <g id="eye-r-sad" opacity="0">
        <line x1="68" y1="49" x2="78" y2="59" stroke="#ff2d78" stroke-width="3" stroke-linecap="round"/>
        <line x1="78" y1="49" x2="68" y2="59" stroke="#ff2d78" stroke-width="3" stroke-linecap="round"/>
      </g>
    </g>
    <rect x="44" y="65" width="32" height="5" rx="2.5" fill="#00ffe7" id="mouth-normal" filter="url(#glow)"/>
    <path d="M40 62 Q60 77 80 62" fill="none" stroke="#00ff88" stroke-width="3" stroke-linecap="round" id="mouth-happy" opacity="0"/>
    <path d="M40 71 Q60 61 80 71" fill="none" stroke="#ff2d78" stroke-width="3" stroke-linecap="round" id="mouth-sad" opacity="0"/>
    <ellipse cx="30" cy="62" rx="7" ry="4" fill="#ff2d78" id="blush-l" opacity="0"/>
    <ellipse cx="90" cy="62" rx="7" ry="4" fill="#ff2d78" id="blush-r" opacity="0"/>
    <path d="M38 36 Q47 32 56 36" fill="none" stroke="#ffe600" stroke-width="2.5" stroke-linecap="round" id="brow-l" opacity="0"/>
    <path d="M64 36 Q73 32 82 36" fill="none" stroke="#ffe600" stroke-width="2.5" stroke-linecap="round" id="brow-r" opacity="0"/>
    <path d="M38 34 Q47 38 56 34" fill="none" stroke="#ff2d78" stroke-width="2.5" stroke-linecap="round" id="brow-sad-l" opacity="0"/>
    <path d="M64 34 Q73 38 82 34" fill="none" stroke="#ff2d78" stroke-width="2.5" stroke-linecap="round" id="brow-sad-r" opacity="0"/>
    <rect x="26" y="88" width="68" height="50" rx="12" fill="url(#bodyGrad)" stroke="#00ffe7" stroke-width="2"/>
    <rect x="36" y="96" width="48" height="30" rx="7" fill="#000b18" stroke="#0d2540" stroke-width="1"/>
    <circle cx="48" cy="107" r="4.5" fill="#00ffe7" id="led1"><animate attributeName="opacity" values="1;0.2;1" dur="1s" repeatCount="indefinite"/></circle>
    <circle cx="60" cy="107" r="4.5" fill="#bf5fff" id="led2"><animate attributeName="opacity" values="1;0.2;1" dur="1s" begin="0.33s" repeatCount="indefinite"/></circle>
    <circle cx="72" cy="107" r="4.5" fill="#ff2d78" id="led3"><animate attributeName="opacity" values="1;0.2;1" dur="1s" begin="0.66s" repeatCount="indefinite"/></circle>
    <rect x="38" y="117" width="44" height="5" rx="2.5" fill="#0d2540"/>
    <rect x="38" y="117" width="28" height="5" rx="2.5" fill="#00ffe7"><animate attributeName="width" values="8;44;8" dur="2s" repeatCount="indefinite"/></rect>
    <rect x="6" y="90" width="18" height="40" rx="9" fill="url(#bodyGrad)" stroke="#00ffe7" stroke-width="2" id="arm-l"/>
    <rect x="96" y="90" width="18" height="40" rx="9" fill="url(#bodyGrad)" stroke="#00ffe7" stroke-width="2" id="arm-r"/>
    <rect x="34" y="138" width="22" height="22" rx="8" fill="url(#bodyGrad)" stroke="#00ffe7" stroke-width="2"/>
    <rect x="64" y="138" width="22" height="22" rx="8" fill="url(#bodyGrad)" stroke="#00ffe7" stroke-width="2"/>
    <ellipse cx="42" cy="68" rx="3" ry="5" fill="#60c8ff" id="tear-l" opacity="0">
      <animate attributeName="cy" values="68;88;68" dur="1s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0;0.9;0" dur="1s" repeatCount="indefinite"/>
    </ellipse>
    <ellipse cx="78" cy="68" rx="3" ry="5" fill="#60c8ff" id="tear-r" opacity="0">
      <animate attributeName="cy" values="68;88;68" dur="1s" begin="0.4s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0;0.9;0" dur="1s" begin="0.4s" repeatCount="indefinite"/>
    </ellipse>
    <circle cx="15" cy="92" r="3.5" fill="#ffe600" id="conf1" opacity="0"/>
    <circle cx="105" cy="92" r="3.5" fill="#ff2d78" id="conf2" opacity="0"/>
  </svg>
</div>
<div class="speech-bubble" id="speechBubble">Let's go!</div>
<div class="streak-badge" id="streakBadge"></div>
<div class="top-bar" id="topBar">
  <div class="score-indicator" id="scoreIndicator">⭐ Puntos acumulados: 0</div>
  <div class="difficulty-indicator" id="difficultyIndicator">Nivel: EASY</div>
</div>

<!-- ══ SCREEN: INICIO ══ -->
<div id="inicio" class="screen">
  <div class="logo-wrap">
    <div class="logo-eyebrow">◈ EDUCATIONAL GAME ◈</div>
    <div class="logo-title">
      <span class="line1">ENGLISH</span>
      <span class="line2">GRAMMAR</span>
      <span class="line3">QUEST</span>
    </div>
    <div class="logo-tag">// TEST YOUR GRAMMAR SKILLS</div>
  </div>

  <div id="welcomeBack" class="welcome-back hidden"></div>

  <div class="level-selector">
    <div class="level-card lv-easy active" onclick="selectLevel('easy',this)">
      <div class="lv-icon">🟢</div>
      <div class="lv-name">EASY</div>
      <div class="lv-pts">+10 pts · 20s</div>
    </div>
    <div class="level-card lv-med" onclick="selectLevel('medium',this)">
      <div class="lv-icon">🟡</div>
      <div class="lv-name">MEDIUM</div>
      <div class="lv-pts">+20 pts · 15s</div>
    </div>
    <div class="level-card lv-hard" onclick="selectLevel('hard',this)">
      <div class="lv-icon">🔴</div>
      <div class="lv-name">HARD</div>
      <div class="lv-pts">+30 pts · 10s</div>
    </div>
  </div>

  <div class="input-wrap">
    <span class="input-label">// PLAYER NAME</span>
    <input type="text" id="nombre" placeholder="Enter your name..." maxlength="20">
  </div>
  <button class="start-btn" onclick="comenzar()">⚡ START QUEST</button>
</div>

<!-- ══ SCREEN: INTRO GENERAL ══ -->
<div id="introGeneral" class="screen hidden">
  <div class="intro-box">
    <div class="intro-head">
      <div>
        <div class="intro-title">WELCOME TO ENGLISH GRAMMAR QUEST</div>
        <div class="intro-subtitle">// PRACTICE, SCORE & IMPROVE</div>
      </div>
      <button class="intro-back-btn" onclick="goBackToLevelSelect()">← CHANGE DIFFICULTY</button>
    </div>
    <div class="intro-summary">
      <p>Welcome to the English practice game. Through clear exercises and progressive levels, you'll test your grammar and verb structures while earning points and improving your confidence.</p>
      <ul>
        <li>Complete each exercise correctly to earn points and improve your performance.</li>
        <li>Progress through topics and levels as you master the structures.</li>
        <li>Practice consistently to strengthen your English in a fun way.</li>
      </ul>
    </div>
    <div class="intro-topics">
      <div class="intro-topic">
        <div class="topic-num">01</div>
        <div class="topic-info">
          <div class="topic-name">⚡ SIMPLE PAST</div>
          <div class="topic-desc">Learn to use verbs in the past tense, questions, and interrogatives clearly</div>
          <div class="topic-subs">
            <span class="sub-tag">AFFIRMATIVE</span>
            <span class="sub-tag">NEGATIVE</span>
            <span class="sub-tag">INTERROGATIVE</span>
          </div>
        </div>
      </div>
      <div class="intro-topic">
        <div class="topic-num">02</div>
        <div class="topic-info">
          <div class="topic-name">📊 COMPARATIVES & SUPERLATIVES</div>
          <div class="topic-desc">Master comparatives and superlatives with clear examples and practical exercises.</div>
          <div class="topic-subs">
             <span class="sub-tag">COMP SHORT</span>
            <span class="sub-tag">COMP LONG</span>
            <span class="sub-tag">SUPER SHORT</span>
            <span class="sub-tag">SUPER LONG</span>
          </div>
        </div>
      </div>
      <div class="intro-topic">
        <div class="topic-num">03</div>
        <div class="topic-info">
          <div class="topic-name">✅ PRESENT PERFECT</div>
          <div class="topic-desc">Connect the past with the present using have/has + past participle.</div>
          <div class="topic-subs">
            <span class="sub-tag">AFFIRMATIVE</span>
            <span class="sub-tag">NEGATIVE</span>
            <span class="sub-tag">INTERROGATIVE</span>
          </div>
        </div>
      </div>
      <div class="intro-topic">
        <div class="topic-num">04</div>
        <div class="topic-info">
          <div class="topic-name">✅ SIMPLE FUTURE</div>
          <div class="topic-desc">Talk about plans, predictions and future intentions. Learn to use "will" and "going to" correctly.</div>
          <div class="topic-subs">
            <span class="sub-tag">AFFIRMATIVE</span>
            <span class="sub-tag">NEGATIVE</span>
            <span class="sub-tag">INTERROGATIVE</span>
          </div>
        </div>
      </div>
    </div>
    <button class="continue-btn" onclick="showTopicSelector()">▶ CHOOSE YOUR TOPIC</button>
  </div>
</div>

<!-- ══ SCREEN: TOPIC SELECTOR ══ -->
<div id="topicSelector" class="screen hidden">
  <div class="topic-selector-box">
    <div class="ts-header">
      <div class="ts-greeting" id="tsGreeting">WELCOME, PLAYER</div>
      <div class="ts-title">SELECT TOPIC</div>
      <div class="ts-level" id="tsLevel">EASY MODE • +10 PTS PER QUESTION</div>
    </div>
    <div class="topics-grid">

      <!-- TEMA 1 -->
      <div class="topic-card" id="card-t1">
        <div class="topic-card-header" onclick="toggleTopic('t1')">
          <div class="topic-card-icon">⚡</div>
          <div>
            <div class="topic-card-title">TOPIC 1: SIMPLE PAST</div>
            <div class="topic-card-sub">Regular and Irregular Verbs</div>
          </div>
          <div class="topic-card-arrow">›</div>
        </div>
        <div class="sub-topics" id="sub-t1">
          <button class="sub-topic-btn" onclick="selectSubTopic('simplePast','affirmative','Simple Past','Affirmative')">Affirmative</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('simplePast','negative','Simple Past','Negative')">Negative</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('simplePast','interrogative','Simple Past','Interrogative')">Interrogative</button>
        </div>
      </div>

      <!-- TEMA 2 -->
      <div class="topic-card" id="card-t2">
        <div class="topic-card-header" onclick="toggleTopic('t2')">
          <div class="topic-card-icon">📊</div>
          <div>
            <div class="topic-card-title">TOPIC 2: COMPARATIVES & SUPERLATIVES</div>
            <div class="topic-card-sub">Short and Long Adjectives</div>
          </div>
          <div class="topic-card-arrow">›</div>
        </div>
        <div class="sub-topics" id="sub-t2">
          <button class="sub-topic-btn" onclick="selectSubTopic('comparatives','compShort','Comparatives & Superlatives','Comparatives (Short Adj)')">Comparatives (Short Adj)</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('comparatives','compLong','Comparatives & Superlatives','Comparatives (Long Adj)')">Comparatives (Long Adj)</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('comparatives','superShort','Comparatives & Superlatives','Superlatives (Short Adj)')">Superlatives (Short Adj)</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('comparatives','superLong','Comparatives & Superlatives','Superlatives (Long Adj)')">Superlatives (Long Adj)</button>
        </div>
      </div>

      <!-- TEMA 3 -->
      <div class="topic-card" id="card-t3">
        <div class="topic-card-header" onclick="toggleTopic('t3')">
          <div class="topic-card-icon">✅</div>
          <div>
            <div class="topic-card-title">TOPIC 3: PRESENT PERFECT</div>
            <div class="topic-card-sub">Have / Has + Past Participle</div>
          </div>
          <div class="topic-card-arrow">›</div>
        </div>
        <div class="sub-topics" id="sub-t3">
          <button class="sub-topic-btn" onclick="selectSubTopic('presentPerfect','affirmative','Present Perfect','Affirmative')">Affirmative</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('presentPerfect','negative','Present Perfect','Negative')">Negative</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('presentPerfect','interrogative','Present Perfect','Interrogative')">Interrogative</button>
        </div>
      </div>

      <!-- TEMA 4 -->
      <div class="topic-card" id="card-t4">
        <div class="topic-card-header" onclick="toggleTopic('t4')">
          <div class="topic-card-icon">🚀</div>
          <div>
            <div class="topic-card-title">TOPIC 4: SIMPLE FUTURE</div>
            <div class="topic-card-sub">Will & Going to</div>
          </div>
          <div class="topic-card-arrow">›</div>
        </div>
        <div class="sub-topics" id="sub-t4">
          <button class="sub-topic-btn" onclick="selectSubTopic('simpleFuture','affirmative','Simple Future','Affirmative')">Affirmative</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('simpleFuture','negative','Simple Future','Negative')">Negative</button>
          <button class="sub-topic-btn" onclick="selectSubTopic('simpleFuture','interrogative','Simple Future','Interrogative')">Interrogative</button>
        </div>
      </div>

    </div>
    <div class="ts-btn-row">
      <button class="ts-nav-btn" onclick="goBackToLevelSelect()">← CHANGE LEVEL</button>
      <button class="ts-nav-btn secondary" onclick="goToIntroGeneral()">📖 SEE RULES</button>
    </div>
  </div>
</div>

<!-- ══ SCREEN: SUBTOPIC INTRO ══ -->
<div id="subtopicIntro" class="screen hidden">
  <div class="subtopic-intro-box">
    <div class="si-eyebrow" id="siEyebrow">◈ TOPIC 1 ◈</div>
    <div class="si-title" id="siTitle">SIMPLE PAST</div>
    <div class="si-subtitle" id="siSubtitle">AFFIRMATIVE FORM</div>
    <div class="si-body" id="siBody"></div>
    <div class="si-examples" id="siExamples"></div>
    <div class="si-tip" id="siTip"></div>
    <div class="si-btn-row">
      <button class="si-back-btn" onclick="show('topicSelector')">← BACK</button>
      <button class="si-play-btn" onclick="startGame()">⚡ START CHALLENGE</button>
    </div>
  </div>
</div>

<!-- ══ SCREEN: JUEGO ══ -->
<div id="juego" class="screen hidden">
  <div class="hud">
    <div class="hud-item">
      <div class="hud-label">PLAYER</div>
      <div class="hud-value" id="hud-player" style="font-size:14px;letter-spacing:2px">---</div>
    </div>
    <div class="hud-item">
      <div class="hud-label">SCORE</div>
      <div class="hud-value gold" id="hud-pts">0</div>
    </div>
    <div class="hud-item">
      <div class="timer-wrap">
        <svg viewBox="0 0 64 64">
          <circle class="timer-bg" cx="32" cy="32" r="28"/>
          <circle class="timer-fg" id="timerRing" cx="32" cy="32" r="28"/>
        </svg>
        <div class="timer-num" id="timerNum">20</div>
      </div>
    </div>
    <div class="hud-item">
      <div class="hud-label">STREAK</div>
      <div class="hud-value pink" id="hud-streak">🔥 0</div>
    </div>

    <div class="hud-item">
      <div class="hud-label">LEVEL</div>
      <div class="hud-value" id="hud-level" style="font-size:13px">EASY</div>
    </div>
    <div class="hud-controls">
      <button class="control-btn pause" id="pauseBtn" onclick="togglePause()">⏸ PAUSE</button>
      <button class="control-btn abandon" id="abandonBtn" onclick="showAbandonConfirm()">✕ ABANDON</button>
    </div>
  </div>

  <div class="progress-wrap">
    <div class="progress-track"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>
    <div class="progress-info">
      <span id="progressTopicLabel">SIMPLE PAST · AFFIRMATIVE</span>
      <span id="progressLabel">0 / 0</span>
    </div>
  </div>

  <div class="question-box">
    <div class="q-topic-tag" id="qTopicTag"></div>
    <div class="q-label" id="qNumber">QUESTION 01</div>
    <div id="question"></div>
    <div class="q-hint" id="qHint"></div>
  </div>

  <div class="options-grid">
    <button class="option-btn" id="btn1"></button>
    <button class="option-btn" id="btn2"></button>
    <button class="option-btn" id="btn3"></button>
    <button class="option-btn" id="btn4"></button>
  </div>
  <div id="result"></div>
</div>

<!-- ══ SCREEN: FINAL ══ -->
<div id="final" class="screen hidden">
  <div class="final-box">
    <span class="trophy-icon" id="trophyIcon">🏆</span>
    <div class="final-title">QUEST COMPLETE</div>
    <div class="final-player" id="finalPlayer"></div>
    <div class="final-topic-tag" id="finalTopicTag"></div>
    <div class="lvl-tag" id="finalLvlTag"></div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-val" id="finalPts">0</div><div class="stat-lbl">SCORE</div></div>
      <div class="stat-card"><div class="stat-val" id="finalAcc">0%</div><div class="stat-lbl">ACCURACY</div></div>
      <div class="stat-card"><div class="stat-val" id="finalStreak">0</div><div class="stat-lbl">BEST STREAK</div></div>
    </div>
    <div class="rank-badge" id="rankBadge"></div>
    <div class="final-btns">
      <button class="final-btn btn-restart" id="btnRestart">🔄 PLAY AGAIN</button>
      <button class="final-btn btn-exit" id="btnExit">✕ EXIT</button>
    </div>
  </div>
</div>

<!-- ══ SCREEN: GOODBYE ══ -->
<div id="goodbye" class="screen hidden">
  <div class="goodbye-box">
    <span class="goodbye-icon">👋</span>
    <div class="goodbye-title">SEE YOU!</div>
    <div class="goodbye-sub">Thanks for playing,<br><span id="goodbyeName"></span></div>
    <button class="start-btn" style="margin-top:28px;width:280px" id="btnBackHome">🏠 BACK TO START</button>
  </div>
</div>

<!-- ══ PAUSE MODAL ══ -->
<div id="pauseModal" class="pause-modal">
  <div class="pause-box">
    <div class="pause-title">⏸ PAUSED</div>
    <div class="pause-score">
      <div style="font-size:12px;color:rgba(255,255,255,0.6);margin-bottom:8px">ACCUMULATED POINTS</div>
      <div style="font-size:28px;font-weight:700;color:var(--y)" id="pauseScore">0</div>
    </div>
    <div class="pause-btns">
      <button class="pause-btn btn-resume" onclick="togglePause()">▶ RESUME GAME</button>
      <button class="pause-btn btn-abandon-modal" onclick="confirmAbandon()">✕ ABANDON GAME</button>
    </div>
  </div>
</div>

<script>
/* ══ PARTICLES & LINES ══ */
(function(){
  const pc=document.getElementById('particles');
  for(let i=0;i<30;i++){
    const p=document.createElement('div');p.className='particle';
    p.style.cssText=`left:${Math.random()*100}%;width:${2+Math.random()*3}px;height:${2+Math.random()*3}px;animation-duration:${10+Math.random()*15}s;animation-delay:${Math.random()*20}s;background:${['#00ffe7','#bf5fff','#ff2d78'][Math.floor(Math.random()*3)]};`;
    pc.appendChild(p);
  }
  const bl=document.getElementById('bgLines');
  for(let i=0;i<8;i++){
    const l=document.createElement('div');l.className='speed-line';
    l.style.cssText=`top:${Math.random()*100}%;width:${100+Math.random()*200}px;animation-duration:${3+Math.random()*5}s;animation-delay:${Math.random()*8}s;opacity:0.4;`;
    bl.appendChild(l);
  }
})();

/* ══ ROBOT ══ */
const MSGS={
  idle:['Let\'s go!','Ready?','You got this!','Focus! ⚡'],
  correct:['PERFECT! 🌟','GREAT! ⚡','AWESOME! 🎉','GENIUS! 🏆','NAILED IT! 💥'],
  wrong:['Ohh... 😢','Don\'t give up!','Try harder! 😭','So close... 😿'],
  timeout:['Too slow! ⏱','Time\'s up! 😰','Hurry! ⚡'],
  win:['CHAMPION! 🏆','YOU DID IT! 🎊','INCREDIBLE! ⭐'],
  lose:['Keep trying! 💪','Study more! 📚','Don\'t give up 😢']
};
let charTO=null;
function setChar(state){
  const w=document.getElementById('charWrap');w.className='char-wrap '+state;
  const ids=['eye-l','eye-r','eye-l-happy','eye-r-happy','eye-l-sad','eye-r-sad','mouth-normal','mouth-happy','mouth-sad','blush-l','blush-r','brow-l','brow-r','brow-sad-l','brow-sad-r','tear-l','tear-r','conf1','conf2'];
  const [eL,eR,eLH,eRH,eLS,eRS,mN,mH,mS,bL,bR,brL,brR,brSL,brSR,tL,tR,c1,c2]=ids.map(id=>document.getElementById(id));
  [eL,eR].forEach(e=>{e.setAttribute('opacity','0.9');e.setAttribute('fill','#00ffe7')});
  [eLH,eRH,eLS,eRS,mH,mS,bL,bR,brL,brR,brSL,brSR,tL,tR,c1,c2].forEach(e=>e.setAttribute('opacity','0'));
  mN.setAttribute('opacity','1');
  if(state==='correct'||state==='win'){[eL,eR].forEach(e=>e.setAttribute('opacity','0'));[eLH,eRH,mH,brL,brR,c1,c2].forEach(e=>e.setAttribute('opacity','1'));[bL,bR].forEach(e=>e.setAttribute('opacity','0.7'));mN.setAttribute('opacity','0');if(state==='correct')launchStars();}
  if(state==='wrong'||state==='timeout'||state==='lose'){[eL,eR].forEach(e=>e.setAttribute('opacity','0'));[eLS,eRS,mS,brSL,brSR].forEach(e=>e.setAttribute('opacity','1'));[tL,tR].forEach(e=>e.setAttribute('opacity','0.9'));mN.setAttribute('opacity','0');}
  const msgs=MSGS[state]||MSGS.idle;
  showBubble(msgs[Math.floor(Math.random()*msgs.length)]);
  if(state!=='idle'&&state!=='win'&&state!=='lose'){clearTimeout(charTO);charTO=setTimeout(()=>setChar('idle'),2600);}
}
function showBubble(msg){const b=document.getElementById('speechBubble');b.textContent=msg;b.classList.remove('show');void b.offsetWidth;b.classList.add('show');clearTimeout(b._t);b._t=setTimeout(()=>b.classList.remove('show'),2300);}
function launchStars(){
  const e=['⭐','✨','💥','🌟','🎉','💫','⚡','🔥'];
  const r=document.getElementById('charWrap').getBoundingClientRect();
  const cx=r.left+r.width/2,cy=r.top+r.height/3;
  for(let i=0;i<9;i++){const el=document.createElement('div');el.className='star-burst';el.textContent=e[Math.floor(Math.random()*e.length)];const a=(i/9)*Math.PI*2,d=65+Math.random()*65;el.style.cssText=`left:${cx}px;top:${cy}px;--dx:${Math.cos(a)*d}px;--dy:${Math.sin(a)*d}px;animation-delay:${Math.random()*0.2}s`;document.body.appendChild(el);setTimeout(()=>el.remove(),1300);}
}

/* ══ NIVELES ══ */
const LEVELS={
  easy:  {pts:10,time:20,label:'EASY',  color:'#00ffe7',tag:'tag-easy'},
  medium:{pts:20,time:20,label:'MEDIUM',color:'#ffe600',tag:'tag-medium'},
  hard:  {pts:30,time:20,label:'HARD',  color:'#ff2d78',tag:'tag-hard'}
};

const MODE_HINTS={
  medium:'Select the two key parts of the structure.',
  hard:'Write the two key parts of the structure.'
};

const MEDIUM_LABELS={
  simplePast:{
    affirmative:['PAST VERB','COMPLEMENT'],
    negative:['DIDN\'T / DID NOT','BASE VERB'],
    interrogative:['DID','BASE VERB']
  },
  comparatives:{
    compShort:['ADJ-ER','THAN'],
    compLong:['MORE','ADJECTIVE'],
    superShort:['THE','ADJ-EST'],
    superLong:['THE MOST','ADJECTIVE']
  },
  presentPerfect:{
    affirmative:['HAVE/HAS','PAST PARTICIPLE'],
    negative:['HAVE NOT / HAS NOT','PAST PARTICIPLE'],
    interrogative:['HAVE/HAS','PAST PARTICIPLE']
  }
};

const MEDIUM_POOLS={
  simplePast:{
    affirmative:[
      ['went','watched','finished','wrote','travelled','slept','baked','passed','stayed','left'],
      ['yesterday','last night','before dinner','last week','last summer','all day yesterday','for her birthday','successfully','for two weeks','at home']
    ],
    negative:[
      ["didn't",'did not','don\'t','doesn\'t'],
      ['go','watch','find','understand','stay','read','finish','see','eat']
    ],
    interrogative:[
      ['Did','Do','Does','Was'],
      ['call','arrive','go','finish','say','enjoy','learn','meet','stay','write']
    ]
  },
  comparatives:{
    compShort:[
      ['taller','bigger','faster','warmer','easier','newer','smaller','older'],
      ['than','as','from','to']
    ],
    compLong:[
      ['more','most','less','as'],
      ['difficult','expensive','detailed','interesting','convenient','ambitious','effective','important']
    ],
    superShort:[
      ['the','a','an','this'],
      ['tallest','smallest','fastest','highest','oldest','longest','youngest','easiest']
    ],
    superLong:[
      ['the most','most','more','the'],
      ['interesting','expensive','important','beautiful','comfortable','difficult','dangerous','effective']
    ]
  },
  presentPerfect:{
    affirmative:[
      ['have','has'],
      ['done','arrived','eaten','worked','visited','written','known','finished','seen','lived']
    ],
    negative:[
      ["haven't","hasn't"],
      ['finished','met','been','eaten','received','studied','decided','visited','completed','answered']
    ],
    interrogative:[
      ['have','has'],
      ['been','finished','tried','worked','told','visited','seen','completed','received']
    ]
  }
};


function shuffle(arr){
  const a=[...arr];
  for(let i=a.length-1;i>0;i--){
    const j=Math.floor(Math.random()*(i+1));
    [a[i],a[j]]=[a[j],a[i]];
  }
  return a;
}

function buildOptions(correct,pool,count){
  const norm=(v)=>String(v||'').trim().toLowerCase();
  const opts=[correct];
  const filtered=(pool||[]).filter(p=>norm(p)!==norm(correct));
  while(opts.length<Math.min(count,(filtered.length+1))){
    const pick=filtered[Math.floor(Math.random()*filtered.length)];
    if(!opts.some(o=>norm(o)===norm(pick)))opts.push(pick);
  }
  return shuffle(opts);
}

function getMediumLabels(topic,sub){
  return (MEDIUM_LABELS[topic]&&MEDIUM_LABELS[topic][sub])?MEDIUM_LABELS[topic][sub]:[];
}

function getMediumPools(topic,sub){
  return (MEDIUM_POOLS[topic]&&MEDIUM_POOLS[topic][sub])?MEDIUM_POOLS[topic][sub]:[];
}
////////////////////////////////////////////////////////////////////////////////////////////////////////////////
function escapeRegExp(value){
  return String(value).replace(/[.*+?^${}()|[\]\\]/g,'\\$&');
}

function replaceFirstInsensitive(text, search, replacement){
  const regex=new RegExp(escapeRegExp(search),'i');
  return text.replace(regex,replacement);
}

/* ══ NORMALIZACIÓN DE RESPUESTAS: Maneja equivalencias gramaticales ══ */
function normalizeGrammarAnswer(answer){
  const norm=String(answer||'').trim().toLowerCase();
  
  // Mapeo de equivalencias gramaticales (forma extendida → forma contraída Y VICEVERSA)
  const equivalences={
    "didn't":"didn't",
    "did not":"didn't",
    "don't":"don't",
    "do not":"don't",
    "doesn't":"doesn't",
    "does not":"doesn't",
    "haven't":"haven't",
    "have not":"haven't",
    "hasn't":"hasn't",
    "has not":"hasn't",
    "won't":"won't",
    "will not":"won't",
    "isn't":"isn't",
    "is not":"isn't",
    "aren't":"aren't",
    "are not":"aren't",
    "wasn't":"wasn't",
    "was not":"wasn't",
    "weren't":"weren't",
    "were not":"weren't"
  };
  
  // Si encontramos una equivalencia, retornamos la forma normalizada
  if(equivalences[norm]){
    return equivalences[norm];
  }
  
  // Si no hay equivalencia directa, retornamos la forma lowercase normalizada
  return norm;
}

function buildQuestionText(question, answers){
  if(!Array.isArray(answers) || answers.length===0) return question;
  let text=question;
  answers.forEach((ans)=>{
    const value=String(ans||'').trim();
    if(!value) return;
    if(text.toLowerCase().includes(value.toLowerCase())){
      text=replaceFirstInsensitive(text,value,'___');
    }
  });
  return text;
}
///////////////////////////////////////////////////////////////////////
/* ══ BANCO DE PREGUNTAS POR TEMA Y SUBTEMA ══ */
/* Estructura: Easy = 4 opciones, Medium = seleccionar 2 partes, Hard = escribir 2 partes */
const QS = {
  simplePast: {
    affirmative: [
      {
        p:"She ___ to the market yesterday.",
        o:["go","goes","went","going"],
        r:"went",
        medium:{parts:["went (past verb)","yesterday (complement)"],answers:["went","yesterday"]},
        hard:{parts:["What is the past verb?","What is the complement?"],answers:["went","yesterday"]}
      },
      {
        p:"They ___ a great movie last night.",
        o:["watch","watched","watches","watching"],
        r:"watched",
        medium:{parts:["watched (past verb)","last night (complement)"],answers:["watched","last night"]},
        hard:{parts:["Past verb:","Time complement:"],answers:["watched","last night"]}
      },
      {
        p:"He ___ his homework before dinner.",
        o:["finish","finishes","finished","finishing"],
        r:"finished",
        medium:{parts:["finished (verb)","before dinner (complement)"],answers:["finished","before dinner"]},
        hard:{parts:["Verb in past:","When (complement):"],answers:["finished","before dinner"]}
      },
      {
        p:"I ___ a letter to my friend last week.",
        o:["write","writes","wrote","written"],
        r:"wrote",
        medium:{parts:["wrote (past verb)","last week (complement)"],answers:["wrote","last week"]},
        hard:{parts:["Past form:","Temporal complement:"],answers:["wrote","last week"]}
      },
      {
        p:"We ___ to the beach last summer.",
        o:["travel","travelled","travels","travelling"],
        r:"travelled",
        medium:{parts:["travelled (verb)","last summer (complement)"],answers:["travelled","last summer"]},
        hard:{parts:["Past verb:","Time frame:"],answers:["travelled","last summer"]}
      },
      {
        p:"The dog ___ all day yesterday.",
        o:["sleep","sleeps","slept","sleeping"],
        r:"slept",
        medium:{parts:["slept (verb)","all day yesterday (complement)"],answers:["slept","all day yesterday"]},
        hard:{parts:["Verb:","Duration:"],answers:["slept","all day yesterday"]}
      },
      {
        p:"She ___ a delicious cake for her birthday.",
        o:["bake","baked","bakes","baking"],
        r:"baked",
        medium:{parts:["baked (verb)","for her birthday (complement)"],answers:["baked","for her birthday"]},
        hard:{parts:["Past verb:","Purpose:"],answers:["baked","for her birthday"]}
      },
      {
        p:"Tom ___ the exam successfully.",
        o:["pass","passed","passes","passing"],
        r:"passed",
        medium:{parts:["passed (verb)","successfully (adverb)"],answers:["passed","successfully"]},
        hard:{parts:["Verb:","Adverb:"],answers:["passed","successfully"]}
      },
      {
        p:"They ___ in Paris for two weeks.",
        o:["stay","stayed","stays","staying"],
        r:"stayed",
        medium:{parts:["stayed (verb)","for two weeks (complement)"],answers:["stayed","for two weeks"]},
        hard:{parts:["Past verb:","Duration:"],answers:["stayed","for two weeks"]}
      },
      {
        p:"I ___ my keys at home this morning.",
        o:["leave","leaved","left","leaving"],
        r:"left",
        medium:{parts:["left (verb)","at home (location)"],answers:["left","at home"]},
        hard:{parts:["Past verb:","Where:"],answers:["left","at home"]}
      }
    ],
    negative: [
      {
        p:"She ___ to the party last night.",
        o:["didn't go","doesn't go","wasn't going","hadn't gone"],
        r:"didn't go",
        medium:{parts:["didn't (negation)","go (base verb)"],answers:["didn't","go"]},
        hard:{parts:["Didn't or Did Not:","Base verb:"],answers:["didn't","go"]}
      },
      {
        p:"They ___ the match on TV.",
        o:["didn't watch","doesn't watch","weren't watching","hadn't watched"],
        r:"didn't watch",
        medium:{parts:["didn't (negation)","watch (base verb)"],answers:["didn't","watch"]},
        hard:{parts:["Didn't or Did Not:","Base verb:"],answers:["didn't","watch"]}
      },
      {
        p:"He ___ his keys this morning.",
        o:["didn't find","doesn't find","wasn't finding","hadn't found"],
        r:"didn't find",
        medium:{parts:["didn't (negation)","find (base verb)"],answers:["didn't","find"]},
        hard:{parts:["Didn't or Did Not:","Verb:"],answers:["didn't","find"]}
      },
      {
        p:"I ___ what she said.",
        o:["didn't understand","doesn't understand","wasn't understanding","hadn't understood"],
        r:"didn't understand",
        medium:{parts:["didn't (negation)","understand (base verb)"],answers:["didn't","understand"]},
        hard:{parts:["Didn't or Did Not:","Main verb:"],answers:["didn't","understand"]}
      },
      {
        p:"We ___ in that hotel last year.",
        o:["didn't stay","doesn't stay","weren't staying","hadn't stayed"],
        r:"didn't stay",
        medium:{parts:["didn't (negation)","stay (base verb)"],answers:["didn't","stay"]},
        hard:{parts:["Didn't or Did Not:","Action:"],answers:["didn't","stay"]}
      },
      {
        p:"The children ___ to school yesterday.",
        o:["didn't go","doesn't go","weren't going","hadn't gone"],
        r:"didn't go",
        medium:{parts:["didn't (negation)","go (base verb)"],answers:["didn't","go"]},
        hard:{parts:["Didn't or Did Not:","Main verb:"],answers:["didn't","go"]}
      },
      {
        p:"She ___ the book before the exam.",
        o:["didn't read","doesn't read","wasn't reading","hadn't read"],
        r:"didn't read",
        medium:{parts:["didn't (negation)","read (base verb)"],answers:["didn't","read"]},
        hard:{parts:["Didn't or Did Not:","Verb:"],answers:["didn't","read"]}
      },
      {
        p:"They ___ finish the project on time.",
        o:["didn't","doesn't","weren't","hadn't"],
        r:"didn't",
        medium:{parts:["didn't (past negation)","finish (base verb)"],answers:["didn't","finish"]},
        hard:{parts:["Didn't or Did Not:","Base verb:"],answers:["didn't","finish"]}
      },
      {
        p:"I ___ see anyone at the park.",
        o:["didn't","doesn't","wasn't","hadn't"],
        r:"didn't",
        medium:{parts:["didn't (negation)","see (base verb)"],answers:["didn't","see"]},
        hard:{parts:["Didn't or Did Not:","Verb:"],answers:["didn't","see"]}
      },
      {
        p:"He ___ eat breakfast this morning.",
        o:["didn't","doesn't","wasn't","hadn't"],
        r:"didn't",
        medium:{parts:["didn't (negation)","eat (base verb)"],answers:["didn't","eat"]},
        hard:{parts:["Didn't or Did Not:","Main verb:"],answers:["didn't","eat"]}
      }
    ],
    interrogative: [
      {
        p:"___ she call you last night?",
        o:["Did","Does","Was","Had"],
        r:"Did",
        medium:{parts:["Did (question form)","call (base verb)"],answers:["Did","call"]},
        hard:{parts:["Question auxiliary:","Main verb:"],answers:["Did","call"]}
      },
      {
        p:"___ they arrive on time?",
        o:["Did","Do","Were","Have"],
        r:"Did",
        medium:{parts:["Did (question form)","arrive (base verb)"],answers:["Did","arrive"]},
        hard:{parts:["Question form:","Verb:"],answers:["Did","arrive"]}
      },
      {
        p:"Where ___ you go last weekend?",
        o:["did","do","were","have"],
        r:"did",
        medium:{parts:["did (question auxiliary)","go (base verb)"],answers:["did","go"]},
        hard:{parts:["Did form:","Action verb:"],answers:["did","go"]}
      },
      {
        p:"___ he finish his project yesterday?",
        o:["Did","Does","Was","Had"],
        r:"Did",
        medium:{parts:["Did (interrogative)","finish (base verb)"],answers:["Did","finish"]},
        hard:{parts:["Question auxiliary:","Main verb:"],answers:["Did","finish"]}
      },
      {
        p:"What ___ she say to you?",
        o:["did","does","was","had"],
        r:"did",
        medium:{parts:["did (question form)","say (base verb)"],answers:["did","say"]},
        hard:{parts:["Did:","Verb:"],answers:["did","say"]}
      },
      {
        p:"___ they enjoy the trip?",
        o:["Did","Do","Were","Have"],
        r:"Did",
        medium:{parts:["Did (interrogative)","enjoy (base verb)"],answers:["Did","enjoy"]},
        hard:{parts:["Question form:","Verb:"],answers:["Did","enjoy"]}
      },
      {
        p:"When ___ you learn to drive?",
        o:["did","do","were","have"],
        r:"did",
        medium:{parts:["did (question)","learn (base verb)"],answers:["did","learn"]},
        hard:{parts:["Did form:","Main verb:"],answers:["did","learn"]}
      },
      {
        p:"___ they meet at the café?",
        o:["Did","Do","Were","Have"],
        r:"Did",
        medium:{parts:["Did (interrogative)","meet (base verb)"],answers:["Did","meet"]},
        hard:{parts:["Auxiliary:","Action verb:"],answers:["Did","meet"]}
      },
      {
        p:"How long ___ you stay there?",
        o:["did","do","were","have"],
        r:"did",
        medium:{parts:["did (question)","stay (base verb)"],answers:["did","stay"]},
        hard:{parts:["Question form:","Verb:"],answers:["did","stay"]}
      },
      {
        p:"___ she write the email?",
        o:["Did","Does","Was","Had"],
        r:"Did",
        medium:{parts:["Did (interrogative)","write (base verb)"],answers:["Did","write"]},
        hard:{parts:["Question auxiliary:","Main verb:"],answers:["Did","write"]}
      }
    ]
  },
  comparatives: {
    compShort: [
      {p:"My brother is ___ than me.", o:["taller","more tall","the tallest","most tall"], r:"taller",medium:{parts:["ADJ-ER","THAN"],answers:["taller","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["taller","than"]}},
      {p:"This bag is ___ than that one.", o:["bigger","more big","the biggest","most big"], r:"bigger",medium:{parts:["ADJ-ER","THAN"],answers:["bigger","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["bigger","than"]}},
      {p:"She runs ___ than her friend.", o:["faster","more fast","the fastest","most fast"], r:"faster",medium:{parts:["ADJ-ER","THAN"],answers:["faster","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["faster","than"]}},
      {p:"Today is ___ than yesterday.", o:["warmer","more warm","the warmest","most warm"], r:"warmer",medium:{parts:["ADJ-ER","THAN"],answers:["warmer","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["warmer","than"]}},
      {p:"This test is ___ than the last one.", o:["easier","more easy","the easiest","most easy"], r:"easier",medium:{parts:["ADJ-ER","THAN"],answers:["easier","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["easier","than"]}},
      {p:"Your phone is ___ than mine.", o:["newer","more new","the newest","most new"], r:"newer",medium:{parts:["ADJ-ER","THAN"],answers:["newer","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["newer","than"]}},
      {p:"The blue car is ___ than the red car.", o:["smaller","more small","the smallest","most small"], r:"smaller",medium:{parts:["ADJ-ER","THAN"],answers:["smaller","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["smaller","than"]}},
      {p:"This river is ___ than the lake.", o:["longer","more long","the longest","most long"], r:"longer",medium:{parts:["ADJ-ER","THAN"],answers:["longer","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["longer","than"]}},
      {p:"Her hair is ___ than mine.", o:["shorter","more short","the shortest","most short"], r:"shorter",medium:{parts:["ADJ-ER","THAN"],answers:["shorter","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["shorter","than"]}},
      {p:"This chair is ___ than that one.", o:["softer","more soft","the softest","most soft"], r:"softer",medium:{parts:["ADJ-ER","THAN"],answers:["softer","than"]},hard:{parts:["Comparative adjective (-er):","Connector (than):"],answers:["softer","than"]}}
    ],
    compLong: [
      {p:"Math is ___ than history.", o:["more difficult","the most difficult","difficulter","most difficult"], r:"more difficult",medium:{parts:["MORE","ADJECTIVE"],answers:["more","difficult"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","difficult"]}},
      {p:"This hotel is ___ than the other one.", o:["more expensive","the most expensive","expensiver","most expensive"], r:"more expensive",medium:{parts:["MORE","ADJECTIVE"],answers:["more","expensive"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","expensive"]}},
      {p:"Her explanation is ___ than mine.", o:["more detailed","the most detailed","detailer","most detailed"], r:"more detailed",medium:{parts:["MORE","ADJECTIVE"],answers:["more","detailed"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","detailed"]}},
      {p:"The movie was ___ than the book.", o:["more interesting","the most interesting","interestinger","most interesting"], r:"more interesting",medium:{parts:["MORE","ADJECTIVE"],answers:["more","interesting"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","interesting"]}},
      {p:"This route is ___ than the highway.", o:["more convenient","the most convenient","convenienter","most convenient"], r:"more convenient",medium:{parts:["MORE","ADJECTIVE"],answers:["more","convenient"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","convenient"]}},
      {p:"Our project is ___ than last year.", o:["more ambitious","the most ambitious","ambitiouser","most ambitious"], r:"more ambitious",medium:{parts:["MORE","ADJECTIVE"],answers:["more","ambitious"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","ambitious"]}},
      {p:"That solution is ___ than this one.", o:["more effective","the most effective","effectiver","most effective"], r:"more effective",medium:{parts:["MORE","ADJECTIVE"],answers:["more","effective"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","effective"]}},
      {p:"His plan is ___ than ours.", o:["more complicated","the most complicated","complicateder","most complicated"], r:"more complicated",medium:{parts:["MORE","ADJECTIVE"],answers:["more","complicated"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","complicated"]}},
      {p:"This method is ___ than the old one.", o:["more efficient","the most efficient","efficienter","most efficient"], r:"more efficient",medium:{parts:["MORE","ADJECTIVE"],answers:["more","efficient"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","efficient"]}},
      {p:"The city is ___ than the village.", o:["more crowded","the most crowded","crowdeder","most crowded"], r:"more crowded",medium:{parts:["MORE","ADJECTIVE"],answers:["more","crowded"]},hard:{parts:["Modifier (more):","Long adjective:"],answers:["more","crowded"]}}
    ],
    superShort: [
      {p:"He is ___ student in the class.", o:["the tallest","taller","most tall","the most tall"], r:"the tallest",medium:{parts:["THE","ADJ-EST"],answers:["the","tallest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","tallest"]}},
      {p:"This is ___ room in the house.", o:["the smallest","smaller","most small","the most small"], r:"the smallest",medium:{parts:["THE","ADJ-EST"],answers:["the","smallest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","smallest"]}},
      {p:"She is ___ runner on the team.", o:["the fastest","faster","most fast","the most fast"], r:"the fastest",medium:{parts:["THE","ADJ-EST"],answers:["the","fastest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","fastest"]}},
      {p:"Mount Everest is ___ mountain in the world.", o:["the highest","higher","most high","the most high"], r:"the highest",medium:{parts:["THE","ADJ-EST"],answers:["the","highest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","highest"]}},
      {p:"That was ___ day of my life.", o:["the longest","longer","most long","the most long"], r:"the longest",medium:{parts:["THE","ADJ-EST"],answers:["the","longest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","longest"]}},
      {p:"He is ___ student in his group.", o:["the youngest","younger","most young","the most young"], r:"the youngest",medium:{parts:["THE","ADJ-EST"],answers:["the","youngest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","youngest"]}},
      {p:"This is ___ test in the course.", o:["the easiest","easier","most easy","the most easy"], r:"the easiest",medium:{parts:["THE","ADJ-EST"],answers:["the","easiest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","easiest"]}},
      {p:"It was ___ night of the year.", o:["the coldest","colder","most cold","the most cold"], r:"the coldest",medium:{parts:["THE","ADJ-EST"],answers:["the","coldest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","coldest"]}},
      {p:"That is ___ street in town.", o:["the narrowest","narrower","most narrow","the most narrow"], r:"the narrowest",medium:{parts:["THE","ADJ-EST"],answers:["the","narrowest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","narrowest"]}},
      {p:"This is ___ star in the sky.", o:["the brightest","brighter","most bright","the most bright"], r:"the brightest",medium:{parts:["THE","ADJ-EST"],answers:["the","brightest"]},hard:{parts:["Article (the):","Superlative adjective (-est):"],answers:["the","brightest"]}}
    ],
    superLong: [
      {p:"This is ___ movie I have seen.", o:["the most interesting","more interesting","most interesting","the more interesting"], r:"the most interesting",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","interesting"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","interesting"]}},
      {p:"She bought ___ phone in the store.", o:["the most expensive","more expensive","most expensive","the more expensive"], r:"the most expensive",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","expensive"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","expensive"]}},
      {p:"It was ___ decision of the year.", o:["the most important","more important","most important","the more important"], r:"the most important",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","important"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","important"]}},
      {p:"That was ___ view on the trip.", o:["the most beautiful","more beautiful","most beautiful","the more beautiful"], r:"the most beautiful",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","beautiful"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","beautiful"]}},
      {p:"This chair is ___ in the room.", o:["the most comfortable","more comfortable","most comfortable","the more comfortable"], r:"the most comfortable",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","comfortable"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","comfortable"]}},
      {p:"It was ___ exam of all.", o:["the most difficult","more difficult","most difficult","the more difficult"], r:"the most difficult",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","difficult"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","difficult"]}},
      {p:"That is ___ job in the company.", o:["the most dangerous","more dangerous","most dangerous","the more dangerous"], r:"the most dangerous",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","dangerous"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","dangerous"]}},
      {p:"She is ___ student in the class.", o:["the most intelligent","more intelligent","most intelligent","the more intelligent"], r:"the most intelligent",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","intelligent"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","intelligent"]}},
      {p:"That was ___ performance tonight.", o:["the most impressive","more impressive","most impressive","the more impressive"], r:"the most impressive",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","impressive"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","impressive"]}},
      {p:"This is ___ restaurant in the city.", o:["the most popular","more popular","most popular","the more popular"], r:"the most popular",medium:{parts:["THE MOST","ADJECTIVE"],answers:["the most","popular"]},hard:{parts:["Superlative form (the most):","Long adjective:"],answers:["the most","popular"]}}
    ]
  },
  presentPerfect: {
    affirmative: [
      {p:"She ___ already ___ her homework.", o:["has / done","have / done","has / did","have / did"], r:"has / done",medium:{parts:["has (auxiliary)","done (past participle)"],answers:["has","done"]},hard:{parts:["Auxiliary verb:","Past participle:"],answers:["has","done"]}},
      {p:"They ___ just ___ from Paris.", o:["have / arrived","has / arrived","have / arrive","had / arrived"], r:"have / arrived",medium:{parts:["have (auxiliary)","arrived (past participle)"],answers:["have","arrived"]},hard:{parts:["Have/Has:","Past participle:"],answers:["have","arrived"]}},
      {p:"I ___ never ___ sushi before.", o:["have / eaten","has / eaten","have / ate","had / eaten"], r:"have / eaten",medium:{parts:["have (auxiliary)","eaten (past participle)"],answers:["have","eaten"]},hard:{parts:["Auxiliary:","Past participle:"],answers:["have","eaten"]}},
      {p:"He ___ worked here for five years.", o:["has","have","had","is"], r:"has",medium:{parts:["has (auxiliary)","for five years (time)"],answers:["has","for five years"]},hard:{parts:["Auxiliary verb:","Duration:"],answers:["has","for five years"]}},
      {p:"We ___ visited three countries this year.", o:["have","has","had","were"], r:"have",medium:{parts:["have (auxiliary)","visited (past participle)"],answers:["have","visited"]},hard:{parts:["Have/Has:","Past participle:"],answers:["have","visited"]}},
      {p:"She ___ written a new book.", o:["has","have","had","was"], r:"has",medium:{parts:["has (auxiliary)","written (past participle)"],answers:["has","written"]},hard:{parts:["Auxiliary verb:","Past participle:"],answers:["has","written"]}},
      {p:"They ___ known each other since 2010.", o:["have","has","had","were"], r:"have",medium:{parts:["have (auxiliary)","known (past participle)"],answers:["have","known"]},hard:{parts:["Have/Has:","Past participle:"],answers:["have","known"]}},
      {p:"I ___ just finished my project.", o:["have","has","had","was"], r:"have",medium:{parts:["have (auxiliary)","finished (past participle)"],answers:["have","finished"]},hard:{parts:["Auxiliary verb:","Past participle:"],answers:["have","finished"]}},
      {p:"You ___ never seen this movie before.", o:["have","has","had","are"], r:"have",medium:{parts:["have (auxiliary)","seen (past participle)"],answers:["have","seen"]},hard:{parts:["Have/Has:","Past participle:"],answers:["have","seen"]}},
      {p:"She ___ lived in this city for 10 years.", o:["has","have","had","is"], r:"has",medium:{parts:["has (auxiliary)","lived (past participle)"],answers:["has","lived"]},hard:{parts:["Auxiliary verb:","Past participle:"],answers:["has","lived"]}}
    ],
    negative: [
      {p:"She ___ finished her report yet.", o:["hasn't","haven't","didn't","doesn't"], r:"hasn't",medium:{parts:["hasn't (negative auxiliary)","finished (past participle)"],answers:["hasn't","finished"]},hard:{parts:["Negative auxiliary:","Past participle:"],answers:["hasn't","finished"]}},
      {p:"They ___ met him before.", o:["haven't","hasn't","didn't","don't"], r:"haven't",medium:{parts:["haven't (negative)","met (past participle)"],answers:["haven't","met"]},hard:{parts:["Negative form:","Past participle:"],answers:["haven't","met"]}},
      {p:"I ___ been to Japan.", o:["haven't","hasn't","didn't","wasn't"], r:"haven't",medium:{parts:["haven't (negative)","been (past participle)"],answers:["haven't","been"]},hard:{parts:["Negative auxiliary:","Past participle:"],answers:["haven't","been"]}},
      {p:"He ___ eaten breakfast this morning.", o:["hasn't","haven't","didn't","doesn't"], r:"hasn't",medium:{parts:["hasn't (negative)","eaten (past participle)"],answers:["hasn't","eaten"]},hard:{parts:["Has not:","Past participle:"],answers:["hasn't","eaten"]}},
      {p:"We ___ received any news yet.", o:["haven't","hasn't","didn't","don't"], r:"haven't",medium:{parts:["haven't (negative)","received (past participle)"],answers:["haven't","received"]},hard:{parts:["Negative form:","Past participle:"],answers:["haven't","received"]}},
      {p:"She ___ studied for the exam.", o:["hasn't","haven't","didn't","doesn't"], r:"hasn't",medium:{parts:["hasn't (negative)","studied (past participle)"],answers:["hasn't","studied"]},hard:{parts:["Negative auxiliary:","Past participle:"],answers:["hasn't","studied"]}},
      {p:"They ___ decided what to do yet.", o:["haven't","hasn't","didn't","don't"], r:"haven't",medium:{parts:["haven't (negative)","decided (past participle)"],answers:["haven't","decided"]},hard:{parts:["Negative form:","Past participle:"],answers:["haven't","decided"]}},
      {p:"I ___ never visited Paris.", o:["haven't","hasn't","didn't","didn't"], r:"haven't",medium:{parts:["haven't (negative)","visited (past participle)"],answers:["haven't","visited"]},hard:{parts:["Negative auxiliary:","Past participle:"],answers:["haven't","visited"]}},
      {p:"You ___ completed the assignment.", o:["haven't","hasn't","didn't","doesn't"], r:"haven't",medium:{parts:["haven't (negative)","completed (past participle)"],answers:["haven't","completed"]},hard:{parts:["Negative form:","Past participle:"],answers:["haven't","completed"]}},
      {p:"He ___ answered my calls.", o:["hasn't","haven't","didn't","doesn't"], r:"hasn't",medium:{parts:["hasn't (negative)","answered (past participle)"],answers:["hasn't","answered"]},hard:{parts:["Negative auxiliary:","Past participle:"],answers:["hasn't","answered"]}}
    ],
    interrogative: [
      {p:"___ she ever been to New York?", o:["Has","Have","Did","Was"], r:"Has",medium:{parts:["Has (question)","been (past participle)"],answers:["Has","been"]},hard:{parts:["Question auxiliary:","Past participle:"],answers:["Has","been"]}},
      {p:"___ they finished the project?", o:["Have","Has","Did","Were"], r:"Have",medium:{parts:["Have (question)","finished (past participle)"],answers:["Have","finished"]},hard:{parts:["Have/Has:","Past participle:"],answers:["Have","finished"]}},
      {p:"___ you ever tried surfing?", o:["Have","Has","Did","Were"], r:"Have",medium:{parts:["Have (question)","tried (past participle)"],answers:["Have","tried"]},hard:{parts:["Question auxiliary:","Past participle:"],answers:["Have","tried"]}},
      {p:"How long ___ she worked here?", o:["has","have","did","was"], r:"has",medium:{parts:["has (question)","worked (past participle)"],answers:["has","worked"]},hard:{parts:["Auxiliary verb:","Past participle:"],answers:["has","worked"]}},
      {p:"___ he told you the news yet?", o:["Has","Have","Did","Was"], r:"Has",medium:{parts:["Has (question)","told (past participle)"],answers:["Has","told"]},hard:{parts:["Question auxiliary:","Past participle:"],answers:["Has","told"]}},
      {p:"How many times ___ they visited Spain?", o:["have","has","did","were"], r:"have",medium:{parts:["have (question)","visited (past participle)"],answers:["have","visited"]},hard:{parts:["Have/Has:","Past participle:"],answers:["have","visited"]}},
      {p:"___ you ever seen a shooting star?", o:["Have","Has","Did","Were"], r:"Have",medium:{parts:["Have (question)","seen (past participle)"],answers:["Have","seen"]},hard:{parts:["Question auxiliary:","Past participle:"],answers:["Have","seen"]}},
      {p:"___ she completed her studies?", o:["Has","Have","Did","Was"], r:"Has",medium:{parts:["Has (question)","completed (past participle)"],answers:["Has","completed"]},hard:{parts:["Question auxiliary:","Past participle:"],answers:["Has","completed"]}},
      {p:"Where ___ you been recently?", o:["have","has","did","were"], r:"have",medium:{parts:["have (question)","been (past participle)"],answers:["have","been"]},hard:{parts:["Have/Has:","Past participle:"],answers:["have","been"]}},
      {p:"___ they received the package yet?", o:["Have","Has","Did","Were"], r:"Have",medium:{parts:["Have (question)","received (past participle)"],answers:["Have","received"]},hard:{parts:["Question auxiliary:","Past participle:"],answers:["Have","received"]}}
    ]
  },
  simpleFuture: {
    affirmative: [
      {p:"She ___ call you tomorrow.", o:["will","is going to","would","shall"], r:"will",medium:{parts:["will (auxiliary)","call (base verb)"],answers:["will","call"]},hard:{parts:["Future form:","Main verb:"],answers:["will","call"]}},
      {p:"They ___ visit us next month.", o:["are going to","will be","were going to","would"], r:"are going to",medium:{parts:["are going to (structure)","visit (base verb)"],answers:["are going to","visit"]},hard:{parts:["Going to form:","Base verb:"],answers:["are going to","visit"]}},
      {p:"I think it ___ rain this afternoon.", o:["will","is going to","would","shall"], r:"will",medium:{parts:["will (auxiliary)","rain (base verb)"],answers:["will","rain"]},hard:{parts:["Future auxiliary:","Verb:"],answers:["will","rain"]}},
      {p:"We ___ have a meeting at 3 PM.", o:["are going to","were going to","will be","would"], r:"are going to",medium:{parts:["are going to (structure)","have (base verb)"],answers:["are going to","have"]},hard:{parts:["Going to form:","Action verb:"],answers:["are going to","have"]}},
      {p:"He ___ become a doctor someday.", o:["will","is going to","would","shall"], r:"will",medium:{parts:["will (auxiliary)","become (base verb)"],answers:["will","become"]},hard:{parts:["Will form:","Main verb:"],answers:["will","become"]}},
      {p:"Look at those clouds! It ___ snow.", o:["is going to","will","would","shall"], r:"is going to",medium:{parts:["is going to (structure)","snow (base verb)"],answers:["is going to","snow"]},hard:{parts:["Going to form:","Verb:"],answers:["is going to","snow"]}},
      {p:"I promise I ___ help you.", o:["will","am going to","would","shall"], r:"will",medium:{parts:["will (auxiliary)","help (base verb)"],answers:["will","help"]},hard:{parts:["Future form:","Action verb:"],answers:["will","help"]}},
      {p:"She ___ start her new job next week.", o:["is going to","will be","were going to","would"], r:"is going to",medium:{parts:["is going to (structure)","start (base verb)"],answers:["is going to","start"]},hard:{parts:["Going to form:","Verb:"],answers:["is going to","start"]}},
      {p:"We ___ travel to Italy this summer.", o:["are going to","will be","were going to","would"], r:"are going to",medium:{parts:["are going to (structure)","travel (base verb)"],answers:["are going to","travel"]},hard:{parts:["Going to form:","Action verb:"],answers:["are going to","travel"]}},
      {p:"You ___ love this movie.", o:["will","are going to","would","shall"], r:"will",medium:{parts:["will (auxiliary)","love (base verb)"],answers:["will","love"]},hard:{parts:["Will form:","Main verb:"],answers:["will","love"]}}
    ],
    negative: [
      {p:"She ___ come to the party tomorrow.", o:["won't","isn't going to","wouldn't","shan't"], r:"won't",medium:{parts:["won't (negative)","come (base verb)"],answers:["won't","come"]},hard:{parts:["Will not:","Main verb:"],answers:["won't","come"]}},
      {p:"They ___ finish the project on time.", o:["aren't going to","won't be","weren't going to","wouldn't"], r:"aren't going to",medium:{parts:["aren't going to (negative)","finish (base verb)"],answers:["aren't going to","finish"]},hard:{parts:["Negative going to:","Verb:"],answers:["aren't going to","finish"]}},
      {p:"I ___ tell anyone your secret.", o:["won't","am not going to","wouldn't","shan't"], r:"won't",medium:{parts:["won't (negative)","tell (base verb)"],answers:["won't","tell"]},hard:{parts:["Will not:","Action verb:"],answers:["won't","tell"]}},
      {p:"He ___ accept that offer.", o:["won't","isn't going to","wouldn't","shan't"], r:"won't",medium:{parts:["won't (negative)","accept (base verb)"],answers:["won't","accept"]},hard:{parts:["Negative form:","Main verb:"],answers:["won't","accept"]}},
      {p:"We ___ travel this summer because of work.", o:["aren't going to","won't be","weren't going to","wouldn't"], r:"aren't going to",medium:{parts:["aren't going to (negative)","travel (base verb)"],answers:["aren't going to","travel"]},hard:{parts:["Negative going to:","Action verb:"],answers:["aren't going to","travel"]}},
      {p:"She ___ buy a new phone this month.", o:["isn't going to","won't be","wasn't going to","wouldn't"], r:"isn't going to",medium:{parts:["isn't going to (negative)","buy (base verb)"],answers:["isn't going to","buy"]},hard:{parts:["Negative going to:","Verb:"],answers:["isn't going to","buy"]}},
      {p:"It ___ be easy, but we can do it.", o:["won't","isn't going to","wouldn't","shan't"], r:"won't",medium:{parts:["won't (negative)","be (base verb)"],answers:["won't","be"]},hard:{parts:["Will not:","Main verb:"],answers:["won't","be"]}},
      {p:"They ___ attend the conference.", o:["aren't going to","won't be","weren't going to","wouldn't"], r:"aren't going to",medium:{parts:["aren't going to (negative)","attend (base verb)"],answers:["aren't going to","attend"]},hard:{parts:["Negative going to:","Action verb:"],answers:["aren't going to","attend"]}},
      {p:"I ___ give up on my dreams.", o:["won't","am not going to","wouldn't","shan't"], r:"won't",medium:{parts:["won't (negative)","give up (base verb)"],answers:["won't","give up"]},hard:{parts:["Will not:","Verb phrase:"],answers:["won't","give up"]}},
      {p:"He ___ pass the test if he doesn't study.", o:["won't","isn't going to","wouldn't","shan't"], r:"won't",medium:{parts:["won't (negative)","pass (base verb)"],answers:["won't","pass"]},hard:{parts:["Will not:","Main verb:"],answers:["won't","pass"]}}
    ],
    interrogative: [
      {p:"___ you help me move next Saturday?", o:["Will","Are going to","Would","Shall"], r:"Will",medium:{parts:["Will (question)","help (base verb)"],answers:["Will","help"]},hard:{parts:["Question form:","Main verb:"],answers:["Will","help"]}},
      {p:"___ they visit us this holiday?", o:["Are going to","Will be","Were going to","Would"], r:"Are going to",medium:{parts:["Are going to (question)","visit (base verb)"],answers:["Are going to","visit"]},hard:{parts:["Question going to:","Verb:"],answers:["Are going to","visit"]}},
      {p:"What ___ you do after graduation?", o:["will","are going to","would","shall"], r:"will",medium:{parts:["will (question)","do (base verb)"],answers:["will","do"]},hard:{parts:["Future form:","Action verb:"],answers:["will","do"]}},
      {p:"___ she be at the meeting tomorrow?", o:["Will","Is going to","Would","Shall"], r:"Will",medium:{parts:["Will (question)","be (base verb)"],answers:["Will","be"]},hard:{parts:["Question form:","Main verb:"],answers:["Will","be"]}},
      {p:"Where ___ you travel next year?", o:["are going to","will be","were going to","would"], r:"are going to",medium:{parts:["are going to (question)","travel (base verb)"],answers:["are going to","travel"]},hard:{parts:["Question going to:","Action verb:"],answers:["are going to","travel"]}},
      {p:"___ it be cold this weekend?", o:["Will","Is going to","Would","Shall"], r:"Will",medium:{parts:["Will (question)","be (base verb)"],answers:["Will","be"]},hard:{parts:["Question form:","Verb:"],answers:["Will","be"]}},
      {p:"___ he apply for that job?", o:["Is going to","Will be","Was going to","Would"], r:"Is going to",medium:{parts:["Is going to (question)","apply (base verb)"],answers:["Is going to","apply"]},hard:{parts:["Question going to:","Action verb:"],answers:["Is going to","apply"]}},
      {p:"When ___ you arrive at home?", o:["will","are going to","would","shall"], r:"will",medium:{parts:["will (question)","arrive (base verb)"],answers:["will","arrive"]},hard:{parts:["Future form:","Main verb:"],answers:["will","arrive"]}},
      {p:"___ they get married next year?", o:["Are going to","Will be","Were going to","Would"], r:"Are going to",medium:{parts:["Are going to (question)","get married (base verb)"],answers:["Are going to","get married"]},hard:{parts:["Question going to:","Action verb:"],answers:["Are going to","get married"]}},
      {p:"Who ___ win the game?", o:["will","are going to","would","shall"], r:"will",medium:{parts:["will (question)","win (base verb)"],answers:["will","win"]},hard:{parts:["Future form:","Action verb:"],answers:["will","win"]}}
    ]
  }
};


/* ══ INTRO DATA ══ */
const SUBTOPIC_INTRO = {
  simplePast: {
    affirmative: {
      eyebrow:'◈ TOPIC 1 ◈',
      title:'SIMPLE PAST',
      subtitle:'AFFIRMATIVE FORM',
      body:'The Simple Past Affirmative is used to talk about actions or events that were completed at a specific time in the past. Regular verbs add <b style="color:#00ffe7">-ed</b> to form the past tense, while irregular verbs have their own unique forms that you must memorize.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + Verb (past) + ...'},
        {label:'Regular:', val:'She <span>worked</span> all day.'},
        {label:'Regular:', val:'They <span>played</span> soccer.'},
        {label:'Irregular:', val:'I <span>went</span> to the store.'},
        {label:'Irregular:', val:'He <span>ate</span> a sandwich.'}
      ],
      tipIcon:'💡',
      tip:'Common irregular verbs: go→went, eat→ate, write→wrote, take→took, have→had, see→saw, come→came.'
    },
    negative: {
      eyebrow:'◈ TOPIC 1 ◈',
      title:'SIMPLE PAST',
      subtitle:'NEGATIVE FORM',
      body:'To make the Simple Past Negative, we use the auxiliary <b style="color:#ff2d78">did not (didn\'t)</b> followed by the base form of the verb. Notice that the main verb goes back to its base form — we never use the past form with "didn\'t".',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + didn\'t + Verb (base) + ...'},
        {label:'Example:', val:'She <span>didn\'t go</span> to school.'},
        {label:'Example:', val:'They <span>did not watch</span> TV.'},
        {label:'Careful!', val:'She <span>didn\'t went</span> ❌ → didn\'t go ✅'}
      ],
      tipIcon:'⚠️',
      tip:'Remember: after "didn\'t" always use the base form of the verb, NOT the past form. "didn\'t went" is WRONG!'
    },
    interrogative: {
      eyebrow:'◈ TOPIC 1 ◈',
      title:'SIMPLE PAST',
      subtitle:'INTERROGATIVE FORM',
      body:'To form Simple Past questions, we place the auxiliary <b style="color:#ffe600">Did</b> at the beginning of the sentence, followed by the subject and the base form of the verb. For question words (who, what, where, when, why, how), place them before "Did".',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Did + Subject + Verb (base) + ?'},
        {label:'Yes/No:', val:'<span>Did</span> she call you?'},
        {label:'Wh-Q:', val:'Where <span>did</span> you go?'},
        {label:'Wh-Q:', val:'What <span>did</span> he say?'}
      ],
      tipIcon:'💡',
      tip:'Short answers: "Yes, she did." / "No, she didn\'t." — never use the full verb in short answers!'
    }
  },
  comparatives: {
    compShort: {
      eyebrow:'◈ TOPIC 2 ◈',
      title:'COMPARATIVES',
      subtitle:'SHORT ADJECTIVES',
      body:'Use <b style="color:#00ffe7">-er</b> with short adjectives to compare two things. The structure is: <b style="color:#00ffe7">Subject + verb + adjective-er + than + complement</b>.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + verb + adj-er + than + complement'},
        {label:'Example:', val:'She is <span>taller</span> than her sister.'},
        {label:'Example:', val:'My bag is <span>smaller</span> than yours.'}
      ],
      tipIcon:'📏',
      tip:'If the adjective ends in y, change y to i: happy → happier. Double the last consonant: big → bigger.'
    },
    compLong: {
      eyebrow:'◈ TOPIC 2 ◈',
      title:'COMPARATIVES',
      subtitle:'LONG ADJECTIVES',
      body:'With long adjectives, use <b style="color:#00ffe7">more + adjective + than</b> to compare two things.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + verb + more + adjective + than + complement'},
        {label:'Example:', val:'This test is <span>more difficult</span> than the last one.'},
        {label:'Example:', val:'Her explanation is <span>more interesting</span> than mine.'}
      ],
      tipIcon:'💡',
      tip:'Long adjectives (3+ syllables) use more/most. Avoid "difficulter" or "beautifuller".'
    },
    superShort: {
      eyebrow:'◈ TOPIC 2 ◈',
      title:'SUPERLATIVES',
      subtitle:'SHORT ADJECTIVES',
      body:'Superlatives show the highest degree. With short adjectives, use <b style="color:#00ffe7">the + adjective-est</b>.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + verb + the + adj-est + complement'},
        {label:'Example:', val:'He is <span>the tallest</span> student in the class.'},
        {label:'Example:', val:'This is <span>the fastest</span> runner on the team.'}
      ],
      tipIcon:'⭐',
      tip:'Always use "the" before a superlative: the fastest, the biggest, the highest.'
    },
    superLong: {
      eyebrow:'◈ TOPIC 2 ◈',
      title:'SUPERLATIVES',
      subtitle:'LONG ADJECTIVES',
      body:'With long adjectives, use <b style="color:#00ffe7">the most + adjective</b> to show the highest degree.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + verb + the most + adjective + complement'},
        {label:'Example:', val:'This is <span>the most interesting</span> movie I have seen.'},
        {label:'Example:', val:'That is <span>the most expensive</span> phone in the store.'}
      ],
      tipIcon:'🏆',
      tip:'Do not use -est with long adjectives. Say "the most beautiful", not "beautifullest".'
    }
  },
  presentPerfect: {
    affirmative: {
      eyebrow:'◈ TOPIC 3 ◈',
      title:'PRESENT PERFECT',
      subtitle:'AFFIRMATIVE FORM',
      body:'The Present Perfect connects the past to the present. It is formed with <b style="color:#00ffe7">have/has + past participle</b>. Use it for experiences, recent actions, or situations that started in the past and continue now.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + have/has + past participle'},
        {label:'I/You/We/They:', val:'I <span>have eaten</span> sushi.'},
        {label:'He/She/It:', val:'She <span>has worked</span> here for 5 years.'},
        {label:'With "just":', val:'He <span>has just arrived</span>.'}
      ],
      tipIcon:'⏰',
      tip:'Key words: already, yet, just, ever, never, for, since. "I have lived here since 2010." / "She has just called."'
    },
    negative: {
      eyebrow:'◈ TOPIC 3 ◈',
      title:'PRESENT PERFECT',
      subtitle:'NEGATIVE FORM',
      body:'To make the Present Perfect Negative, add <b style="color:#ff2d78">not</b> between the auxiliary and the past participle: <b style="color:#ff2d78">have not (haven\'t) / has not (hasn\'t)</b>. Often used with "yet" to say something hasn\'t happened up to now.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Subject + haven\'t/hasn\'t + past participle'},
        {label:'Example:', val:'She <span>hasn\'t finished</span> yet.'},
        {label:'Example:', val:'They <span>haven\'t met</span> him before.'},
        {label:'Example:', val:'I <span>haven\'t been</span> to Japan.'}
      ],
      tipIcon:'💡',
      tip:'"Haven\'t/Hasn\'t + yet" is very common for actions that haven\'t happened but are expected to happen soon.'
    },
    interrogative: {
      eyebrow:'◈ TOPIC 3 ◈',
      title:'PRESENT PERFECT',
      subtitle:'INTERROGATIVE FORM',
      body:'To form Present Perfect questions, move <b style="color:#ffe600">Have/Has</b> to the beginning of the sentence. Use "ever" to ask about life experiences. Use "yet" to ask if something expected has happened.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'STRUCTURE:', val:'Have/Has + Subject + past participle?'},
        {label:'Example:', val:'<span>Have</span> you ever been to Paris?'},
        {label:'Example:', val:'<span>Has</span> she finished her work yet?'},
        {label:'How long:', val:'How long <span>have</span> you lived here?'}
      ],
      tipIcon:'❓',
      tip:'Short answers: "Yes, I have." / "No, I haven\'t." / "Yes, she has." / "No, she hasn\'t." — always use have/has!'
    }
  },
  simpleFuture: {
    affirmative: {
      eyebrow:'◈ TOPIC 4 ◈',
      title:'SIMPLE FUTURE',
      subtitle:'AFFIRMATIVE FORM',
      body:'English has two main ways to express the future: <b style="color:#00ffe7">will + base verb</b> (for predictions, spontaneous decisions, promises) and <b style="color:#00ffe7">be going to + base verb</b> (for plans and intentions, or when there is evidence something will happen).',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'Will:', val:'Subject + <span>will</span> + verb (base)'},
        {label:'Will:', val:'I <span>will help</span> you. (spontaneous)'},
        {label:'Going to:', val:'Subject + <span>is/are going to</span> + verb'},
        {label:'Going to:', val:'She <span>is going to study</span> medicine. (plan)'}
      ],
      tipIcon:'🚀',
      tip:'Use "will" for promises, offers, and predictions without evidence. Use "going to" for pre-made plans or when there\'s visible evidence.'
    },
    negative: {
      eyebrow:'◈ TOPIC 4 ◈',
      title:'SIMPLE FUTURE',
      subtitle:'NEGATIVE FORM',
      body:'For future negatives: with "will" add <b style="color:#ff2d78">not → won\'t</b>. With "going to" add <b style="color:#ff2d78">not</b> after the auxiliary be: <b style="color:#ff2d78">isn\'t/aren\'t going to</b>.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'Will not:', val:'Subject + <span>won\'t</span> + verb (base)'},
        {label:'Example:', val:'I <span>won\'t tell</span> anyone.'},
        {label:'Not going to:', val:'She <span>isn\'t going to</span> come.'},
        {label:'Example:', val:'They <span>aren\'t going to</span> travel.'}
      ],
      tipIcon:'⚠️',
      tip:'"Will not" contracts to "won\'t". Do not say "willn\'t" — it does not exist! "Won\'t" is the only correct negative contraction.'
    },
    interrogative: {
      eyebrow:'◈ TOPIC 4 ◈',
      title:'SIMPLE FUTURE',
      subtitle:'INTERROGATIVE FORM',
      body:'To form future questions with "will", place <b style="color:#ffe600">Will</b> at the beginning. With "going to", use the correct form of <b style="color:#ffe600">be</b> (is/are) at the start of the question.',
      exTitle:'STRUCTURE & EXAMPLES',
      examples:[
        {label:'Will:', val:'<span>Will</span> + Subject + verb (base) + ?'},
        {label:'Example:', val:'<span>Will</span> you come tomorrow?'},
        {label:'Going to:', val:'<span>Are/Is</span> + Subject + going to + verb?'},
        {label:'Example:', val:'<span>Are</span> you going to study tonight?'}
      ],
      tipIcon:'❓',
      tip:'Short answers with "will": "Yes, I will." / "No, I won\'t." With "going to": "Yes, I am." / "No, I\'m not."'
    }
  }
};


/* ══ ESTADO ══ */
const SCORE_STORAGE_KEY='eqg_total_score';
const LAST_PLAYER_KEY='eqg_last_player';
let nivelKey='easy', preguntas=[], indice=0, puntos=0;
let totalScore=0;
let jugador='', racha=0, mejorRacha=0, correctas=0;
let timerVal=20, timerInterval=null;
let currentTopic='', currentSubTopic='', currentTopicName='', currentSubTopicName='';
const CIRCUM=2*Math.PI*28;
let isPaused=false, timerPausedVal=0;

/* ══ NOMBRE GUARDADO ══ */
window.addEventListener('DOMContentLoaded',()=>{
  const saved=localStorage.getItem('eqg_player');
  const storedScore=parseInt(localStorage.getItem(SCORE_STORAGE_KEY),10);
  if(!Number.isNaN(storedScore) && storedScore>0){
    totalScore=storedScore;
  }
  if(saved){
    document.getElementById('nombre').value=saved;
    const wb=document.getElementById('welcomeBack');
    wb.textContent='⚡ WELCOME BACK, '+saved.toUpperCase()+' !';
    wb.classList.remove('hidden');
  }
  updateTopBar();
  setChar('idle');
});

/* ══ PANTALLAS ══ */
function show(id){
  ['inicio','introGeneral','topicSelector','subtopicIntro','juego','final','goodbye']
    .forEach(s=>document.getElementById(s).classList.toggle('hidden',s!==id));
}

function selectLevel(k,el){
  nivelKey=k;
  document.querySelectorAll('.level-card').forEach(c=>c.classList.remove('active'));
  el.classList.add('active');
  updateTopBar();
}

function comenzar(){
  jugador=document.getElementById('nombre').value.trim();
  if(!jugador){
    const inp=document.getElementById('nombre');
    inp.style.borderColor='var(--m)';inp.style.boxShadow='0 0 20px rgba(255,45,120,0.3)';
    inp.focus();setTimeout(()=>{inp.style.borderColor='';inp.style.boxShadow='';},1500);
    return;
  }
  // Verificar si el jugador cambió
  const lastPlayer=localStorage.getItem(LAST_PLAYER_KEY);
  if(lastPlayer && lastPlayer!==jugador){
    // Jugador cambió - reiniciar puntos acumulados
    totalScore=0;
    localStorage.setItem(SCORE_STORAGE_KEY,0);
  }
  // Guardar nombre actual como último jugador
  localStorage.setItem(LAST_PLAYER_KEY,jugador);
  localStorage.setItem('eqg_player',jugador);
  const wb=document.getElementById('welcomeBack');
  wb.textContent='⚡ WELCOME BACK, '+jugador.toUpperCase()+' !';
  wb.classList.remove('hidden');
  updateTopBar();

  show('introGeneral');
  setChar('idle');
}

function showTopicSelector(){
  // Actualizar header del selector
  document.getElementById('tsGreeting').textContent='GOOD LUCK, '+jugador.toUpperCase()+'!';
  const lv=LEVELS[nivelKey];
  document.getElementById('tsLevel').textContent=lv.label+' MODE • +'+lv.pts+' PTS PER QUESTION';
  updateTopBar();
  // Cerrar todos los acordeones
  ['t1','t2','t3','t4'].forEach(id=>{
    document.getElementById('card-'+id).classList.remove('open');
  });
  show('topicSelector');
}

function goBackToLevelSelect(){
  show('inicio');
  setChar('idle');
}

function goToIntroGeneral(){
  show('introGeneral');
  setChar('idle');
}

function updateTopBar(){
  const scoreEl=document.getElementById('scoreIndicator');
  const diffEl=document.getElementById('difficultyIndicator');
  if(scoreEl){
    scoreEl.textContent='⭐ Puntos acumulados: '+totalScore;
  }
  if(diffEl){
    const label = LEVELS[nivelKey] ? LEVELS[nivelKey].label : 'EASY';
    diffEl.textContent='Nivel: '+label;
  }
}

function addTotalScore(points){
  if(typeof points!=='number' || points<=0) return;
  totalScore += points;
  localStorage.setItem(SCORE_STORAGE_KEY, totalScore);
  updateTopBar();
}

function toggleTopic(id){
  const card=document.getElementById('card-'+id);
  const wasOpen=card.classList.contains('open');
  ['t1','t2','t3','t4'].forEach(t=>document.getElementById('card-'+t).classList.remove('open'));
  if(!wasOpen) card.classList.add('open');
}

function selectSubTopic(topic, sub, topicName, subName){
  currentTopic=topic;
  currentSubTopic=sub;
  currentTopicName=topicName;
  currentSubTopicName=subName;
  const data=SUBTOPIC_INTRO[topic][sub];
  document.getElementById('siEyebrow').textContent=data.eyebrow;
  document.getElementById('siTitle').textContent=data.title;
  document.getElementById('siSubtitle').textContent=data.subtitle;
  document.getElementById('siBody').innerHTML=data.body;
  // Examples
  let exHtml=`<div class="si-ex-title">${data.exTitle}</div>`;
  data.examples.forEach(ex=>{
    exHtml+=`<div class="si-ex-item"><span style="color:rgba(255,255,255,0.4);margin-right:8px">${ex.label}</span>${ex.val}</div>`;
  });
  document.getElementById('siExamples').innerHTML=exHtml;
  // Tip
  document.getElementById('siTip').innerHTML=`<div class="si-tip-icon">${data.tipIcon}</div><div class="si-tip-text">${data.tip}</div>`;
  show('subtopicIntro');
  setChar('idle');
}

function startGame(){
  const allQuestions=[...QS[currentTopic][currentSubTopic]];
  preguntas=[];
  for(let i=0;i<Math.min(7,allQuestions.length);i++){
    const idx=Math.floor(Math.random()*allQuestions.length);
    preguntas.push(allQuestions[idx]);
    allQuestions.splice(idx,1);
  }
  indice=0;puntos=0;racha=0;mejorRacha=0;correctas=0;isPaused=false;
  document.getElementById('pauseBtn').textContent='⏸ PAUSE';
  document.getElementById('hud-player').textContent=jugador.toUpperCase().slice(0,12);
  document.getElementById('hud-level').textContent=LEVELS[nivelKey].label;
  document.getElementById('hud-level').style.color=LEVELS[nivelKey].color;
  document.getElementById('progressTopicLabel').textContent=currentTopicName.toUpperCase()+' · '+currentSubTopicName.toUpperCase();
  document.getElementById('qTopicTag').textContent='◈ '+currentTopicName.toUpperCase()+' — '+currentSubTopicName.toUpperCase()+' ◈';
  show('juego');
  setChar('idle');
  showQuestion();
}

function showQuestion(){
  if(indice>=preguntas.length){endGame();return;}
  const q=preguntas[indice];
  document.getElementById('qNumber').textContent='QUESTION '+String(indice+1).padStart(2,'0');
  const questionText = (nivelKey==='medium' || nivelKey==='hard')
    ? buildQuestionText(q.p, q[nivelKey] && q[nivelKey].answers ? q[nivelKey].answers : [])
    : q.p;
  document.getElementById('question').textContent=questionText;
  const hintEl=document.getElementById('qHint');
  if(hintEl){
    if(nivelKey==='medium') hintEl.textContent=MODE_HINTS.medium;
    else if(nivelKey==='hard') hintEl.textContent=MODE_HINTS.hard;
    else hintEl.textContent='';
  }
  document.getElementById('hud-pts').textContent=puntos;
  document.getElementById('hud-streak').textContent='🔥 '+racha;
  const total=preguntas.length;
  document.getElementById('progressFill').style.width=(indice/total*100)+'%';
  document.getElementById('progressLabel').textContent=indice+' / '+total;
  document.getElementById('result').textContent='';
  
  if(nivelKey==='easy'){showQuestionEasy(q);}
  else if(nivelKey==='medium'){showQuestionMedium(q);}
  else if(nivelKey==='hard'){showQuestionHard(q);}
  startTimer();
}

function showQuestionEasy(q){
  const letters=['A','B','C','D'];
  const btns=['btn1','btn2','btn3','btn4'].map(id=>document.getElementById(id));
  const opts=[...q.o].sort(()=>Math.random()-0.5);
  btns.forEach((btn,i)=>{
    btn.innerHTML=`<span class="opt-letter">${letters[i]}</span>${opts[i]}`;
    btn.dataset.val=opts[i];btn.className='option-btn';btn.disabled=false;btn.style.display='block';
    btn.onclick=()=>checkAnswerEasy(opts[i],btn,btns,q.r);
  });
}

function showQuestionMedium(q){
  const btns=['btn1','btn2','btn3','btn4'].map(id=>document.getElementById(id));
  btns.forEach(b=>b.style.display='none');
  
  const ogrid=document.querySelector('.options-grid');
  if(!document.getElementById('mediumContainer')){
    const div=document.createElement('div');div.id='mediumContainer';div.style.display='grid';
    div.style.gridTemplateColumns='1fr 1fr';div.style.gap='12px';div.style.width='100%';
    div.style.maxWidth='600px';div.style.margin='0 auto';ogrid.parentNode.insertBefore(div,ogrid.nextSibling);
  }
  const cont=document.getElementById('mediumContainer');cont.innerHTML='';
  const answers=(q.medium&&q.medium.answers)?q.medium.answers:[];
  const labels=getMediumLabels(currentTopic,currentSubTopic);
  const pools=getMediumPools(currentTopic,currentSubTopic);
  const partCount=Math.max(answers.length,2);
  const mediumData={selected:new Array(partCount),correct:answers};
  
  for(let idx=0;idx<partCount;idx++){
    const partDiv=document.createElement('div');
    const label=document.createElement('div');label.className='part-label';
    label.textContent=(labels[idx]||('PART '+(idx+1)));partDiv.appendChild(label);
    const optionsDiv=document.createElement('div');optionsDiv.className='part-options';
    const pool=(pools&&pools[idx]&&pools[idx].length)?pools[idx]:(q.o||[]);
    const opts=buildOptions(answers[idx],pool,4);
    opts.forEach((opt)=>{
      const btn=document.createElement('button');btn.className='part-btn';btn.textContent=opt;
      btn.onclick=()=>{
        mediumData.selected[idx]=opt;
        document.querySelectorAll(`[data-part="${idx}"]`).forEach(b=>b.classList.remove('selected'));
        btn.classList.add('selected');btn.dataset.part=idx;
      };btn.dataset.part=idx;
      optionsDiv.appendChild(btn);
    });
    partDiv.appendChild(optionsDiv);
    cont.appendChild(partDiv);
  }
  
  const submitDiv=document.createElement('div');submitDiv.style.gridColumn='1 / -1';submitDiv.style.textAlign='center';
  const submitBtn=document.createElement('button');submitBtn.textContent='✓ CHECK';
  submitBtn.style.marginTop='16px';submitBtn.style.padding='12px 24px';
  submitBtn.style.background='linear-gradient(90deg,#00ffe7,#a755ff)';submitBtn.style.border='none';
  submitBtn.style.borderRadius='8px';submitBtn.style.color='#050510';submitBtn.style.fontWeight='700';
  submitBtn.style.cursor='pointer';submitBtn.style.fontSize='14px';submitBtn.style.fontFamily="'Share Tech Mono',monospace";
  submitBtn.style.letterSpacing='2px';
  submitBtn.onclick=()=>{checkAnswerMedium(mediumData.selected,mediumData.correct,q);};
  submitDiv.appendChild(submitBtn);cont.appendChild(submitDiv);
  window.mediumData=mediumData;
}

function showQuestionHard(q){
  const btns=['btn1','btn2','btn3','btn4'].map(id=>document.getElementById(id));
  btns.forEach(b=>b.style.display='none');
  
  const ogrid=document.querySelector('.options-grid');
  if(!document.getElementById('hardContainer')){
    const div=document.createElement('div');div.id='hardContainer';div.style.display='grid';
    div.style.gridTemplateColumns='1fr 1fr';div.style.gap='16px';div.style.width='100%';
    div.style.maxWidth='600px';div.style.margin='0 auto';ogrid.parentNode.insertBefore(div,ogrid.nextSibling);
  }
  const cont=document.getElementById('hardContainer');cont.innerHTML='';
  const parts=q.hard.parts;const answers=q.hard.answers;
  const hardData={inputs:[],correct:answers};
  
  parts.forEach((part,idx)=>{
    const partDiv=document.createElement('div');
    const label=document.createElement('div');label.className='part-label';
    label.textContent=part.toUpperCase();partDiv.appendChild(label);
    const inp=document.createElement('input');inp.className='input-answer';inp.type='text';
    inp.placeholder='Type answer...';hardData.inputs[idx]=inp;
    partDiv.appendChild(inp);
    cont.appendChild(partDiv);
  });
  
  const submitDiv=document.createElement('div');submitDiv.style.gridColumn='1 / -1';submitDiv.style.textAlign='center';
  const submitBtn=document.createElement('button');submitBtn.textContent='✓ CHECK';
  submitBtn.style.marginTop='16px';submitBtn.style.padding='12px 24px';
  submitBtn.style.background='linear-gradient(90deg,#00ffe7,#a755ff)';submitBtn.style.border='none';
  submitBtn.style.borderRadius='8px';submitBtn.style.color='#050510';submitBtn.style.fontWeight='700';
  submitBtn.style.cursor='pointer';submitBtn.style.fontSize='14px';submitBtn.style.fontFamily="'Share Tech Mono',monospace";
  submitBtn.style.letterSpacing='2px';
  submitBtn.onclick=()=>{checkAnswerHard(hardData.inputs,hardData.correct,q);};
  submitDiv.appendChild(submitBtn);cont.appendChild(submitDiv);
  window.hardData=hardData;
}

function startTimer(startVal){
  clearInterval(timerInterval);
  timerVal=(typeof startVal==='number')?startVal:LEVELS[nivelKey].time;
  updateTimer();
  timerInterval=setInterval(()=>{
    if(!isPaused){timerVal--;updateTimer();if(timerVal<=0){clearInterval(timerInterval);timeOut();}}
  },1000);
}

function updateTimer(){
  const ratio=timerVal/LEVELS[nivelKey].time;
  const offset=CIRCUM*(1-ratio);
  const ring=document.getElementById('timerRing');
  const num=document.getElementById('timerNum');
  ring.style.strokeDasharray=CIRCUM;ring.style.strokeDashoffset=offset;num.textContent=timerVal;
  const col=timerVal>7?'#00ffe7':timerVal>3?'#ffe600':'#ff2d78';
  ring.style.stroke=col;num.style.color=col;
}

function timeOut(){
  const q=preguntas[indice];
  const btns=['btn1','btn2','btn3','btn4'].map(id=>document.getElementById(id));
  
  if(nivelKey==='easy'){
    btns.forEach(b=>{b.disabled=true;if(b.dataset.val===q.r)b.classList.add('correct');});
    document.getElementById('result').textContent='⏱ TIME OUT! Correct: '+q.r;
  } else if(nivelKey==='medium'){
    document.querySelectorAll('.part-btn').forEach(b=>b.disabled=true);
    document.getElementById('result').textContent='⏱ TIME OUT! Correct: '+q.medium.answers.join(' + ');
  } else if(nivelKey==='hard'){
    document.querySelectorAll('.input-answer').forEach(b=>b.disabled=true);
    document.getElementById('result').textContent='⏱ TIME OUT! Correct: '+q.hard.answers.join(' + ');
  }
  
  racha=0;document.getElementById('hud-streak').textContent='🔥 0';
  document.getElementById('result').style.color='#ff2d78';
  setChar('timeout');indice++;
  setTimeout(()=>{
    document.getElementById('result').textContent='';
    const hcont=document.getElementById('hardContainer');const mcont=document.getElementById('mediumContainer');
    if(hcont)hcont.remove();if(mcont)mcont.remove();
    showQuestion();
  },2300);
}

function checkAnswerEasy(val,btnClicked,allBtns,correct){
  clearInterval(timerInterval);allBtns.forEach(b=>b.disabled=true);
  const ok=normalizeGrammarAnswer(val)===normalizeGrammarAnswer(correct);
  if(ok){
    btnClicked.classList.add('correct');puntos+=LEVELS[nivelKey].pts;addTotalScore(LEVELS[nivelKey].pts);racha++;correctas++;
    if(racha>mejorRacha)mejorRacha=racha;floatPts('+'+LEVELS[nivelKey].pts,btnClicked);
    if(racha>=3)showStreak();
    document.getElementById('result').style.color='#00ffe7';
    document.getElementById('result').textContent='✅ CORRECT! +'+LEVELS[nivelKey].pts+' pts';
    setChar('correct');
  } else {
    btnClicked.classList.add('wrong');allBtns.forEach(b=>{if(b.dataset.val===correct)b.classList.add('correct');});
    racha=0;document.getElementById('result').style.color='#ff2d78';
    document.getElementById('result').textContent='❌ Wrong! Correct: '+correct;
    setChar('wrong');
  }
  document.getElementById('hud-pts').textContent=puntos;
  document.getElementById('hud-streak').textContent='🔥 '+racha;
  indice++;setTimeout(()=>{document.getElementById('result').textContent='';showQuestion();},2400);
}

function checkAnswerMedium(selected,correct,q){
  clearInterval(timerInterval);
  const allBtns=document.querySelectorAll('.part-btn');
  allBtns.forEach(b=>b.disabled=true);
  const norm=(v)=>normalizeGrammarAnswer(v);
  
  let allCorrect=true;
  correct.forEach((ans,idx)=>{
    if(!selected[idx]||norm(selected[idx])!==norm(ans)){allCorrect=false;}
  });
  
  if(allCorrect){
    puntos+=LEVELS[nivelKey].pts;addTotalScore(LEVELS[nivelKey].pts);racha++;correctas++;
    if(racha>mejorRacha)mejorRacha=racha;
    if(racha>=3)showStreak();
    document.getElementById('result').style.color='#00ffe7';
    document.getElementById('result').textContent='✅ CORRECT! +'+LEVELS[nivelKey].pts+' pts';
    setChar('correct');
  } else {
    document.querySelectorAll('.part-btn').forEach(b=>{
      const idx=parseInt(b.dataset.part);
      if(b.classList.contains('selected')){
        if(!selected[idx]||norm(selected[idx])!==norm(correct[idx])){b.classList.add('wrong');b.classList.remove('selected');}
        else{b.classList.add('correct');}
      }
    });
    racha=0;
    document.getElementById('result').style.color='#ff2d78';
    document.getElementById('result').textContent='❌ Wrong! Correct: '+correct.join(' + ');
    setChar('wrong');
  }
  document.getElementById('hud-pts').textContent=puntos;
  document.getElementById('hud-streak').textContent='🔥 '+racha;
  indice++;setTimeout(()=>{
    document.getElementById('result').textContent='';
    const hcont=document.getElementById('hardContainer');const mcont=document.getElementById('mediumContainer');
    if(hcont)hcont.remove();if(mcont)mcont.remove();
    showQuestion();
  },2400);
}

function checkAnswerHard(inputs,correct,q){
  clearInterval(timerInterval);
  const submitBtn=document.querySelector('#hardContainer button');
  if(submitBtn)submitBtn.disabled=true;
  
  let allCorrect=true;
  inputs.forEach((inp,idx)=>{
    if(!inp){allCorrect=false;return;}
    const userAnswer=normalizeGrammarAnswer(inp.value);
    const correctAnswer=normalizeGrammarAnswer(correct[idx]);
    if(userAnswer!==correctAnswer){allCorrect=false;}
  });
  
  if(allCorrect){
    puntos+=LEVELS[nivelKey].pts;addTotalScore(LEVELS[nivelKey].pts);racha++;correctas++;
    if(racha>mejorRacha)mejorRacha=racha;
    if(racha>=3)showStreak();
    document.getElementById('result').style.color='#00ffe7';
    document.getElementById('result').textContent='✅ CORRECT! +'+LEVELS[nivelKey].pts+' pts';
    setChar('correct');
  } else {
    inputs.forEach((inp,idx)=>{
      if(!inp)return;
      const userAnswer=normalizeGrammarAnswer(inp.value);
      const correctAnswer=normalizeGrammarAnswer(correct[idx]);
      if(userAnswer===correctAnswer){inp.style.borderColor='#00ffe7';}
      else{inp.style.borderColor='#ff2d78';}
    });
    racha=0;
    document.getElementById('result').style.color='#ff2d78';
    document.getElementById('result').textContent='❌ Wrong! Correct: '+correct.join(' + ');
    setChar('wrong');
  }
  document.getElementById('hud-pts').textContent=puntos;
  document.getElementById('hud-streak').textContent='🔥 '+racha;
  indice++;setTimeout(()=>{
    document.getElementById('result').textContent='';
    const hcont=document.getElementById('hardContainer');const mcont=document.getElementById('mediumContainer');
    if(hcont)hcont.remove();if(mcont)mcont.remove();
    showQuestion();
  },2400);
}

function checkAnswer(val,btnClicked,allBtns,correct){
  checkAnswerEasy(val,btnClicked,allBtns,correct);
}

function floatPts(txt,btn){
  const el=document.createElement('div');el.className='floating-pts';el.textContent=txt;el.style.color='#ffe600';
  const r=btn.getBoundingClientRect();el.style.left=r.left+r.width/2+'px';el.style.top=r.top+'px';
  document.body.appendChild(el);setTimeout(()=>el.remove(),1700);
}

function showStreak(){
  const b=document.getElementById('streakBadge');b.textContent='🔥 '+racha+' STREAK!';b.style.display='block';
  b.style.animation='none';void b.offsetWidth;b.style.animation='badgePop 0.4s cubic-bezier(0.34,1.56,0.64,1)';
  clearTimeout(b._t);b._t=setTimeout(()=>b.style.display='none',2200);
}

function endGame(){
  clearInterval(timerInterval);
  const total=preguntas.length;const acc=Math.round(correctas/total*100);
  const maxPts=LEVELS[nivelKey].pts*total;const pct=Math.round(puntos/maxPts*100);
  let rank,rankBg,rankCol,icon;
  if(pct>=90)      {rank='S — LEGENDARY';    rankBg='linear-gradient(135deg,#ffe600,#ff2d78)';rankCol='#050510';icon='🏆';}
  else if(pct>=70) {rank='A — EXPERT';       rankBg='linear-gradient(135deg,#00ffe7,#bf5fff)';rankCol='#050510';icon='⭐';}
  else if(pct>=50) {rank='B — ADVANCED';     rankBg='linear-gradient(135deg,#bf5fff,#00ffe7)';rankCol='#050510';icon='🎯';}
  else if(pct>=30) {rank='C — INTERMEDIATE'; rankBg='linear-gradient(135deg,#ffe600,#ff8c00)';rankCol='#050510';icon='📚';}
  else             {rank='D — KEEP TRYING';  rankBg='rgba(255,255,255,0.1)';rankCol='#fff';icon='💪';}
  document.getElementById('trophyIcon').textContent=icon;
  document.getElementById('finalPlayer').textContent=jugador.toUpperCase();
  document.getElementById('finalTopicTag').textContent='◈ '+currentTopicName.toUpperCase()+' — '+currentSubTopicName.toUpperCase()+' ◈';
  document.getElementById('finalPts').textContent=puntos;
  document.getElementById('finalAcc').textContent=acc+'%';
  document.getElementById('finalStreak').textContent=mejorRacha;
  const lt=document.getElementById('finalLvlTag');
  lt.textContent=LEVELS[nivelKey].label+' MODE';lt.className='lvl-tag '+LEVELS[nivelKey].tag;
  const rb=document.getElementById('rankBadge');rb.textContent=rank;rb.style.background=rankBg;rb.style.color=rankCol;
  show('final');setChar(pct>=50?'win':'lose');
}

/* ══ BOTONES FINALES ══ */
function pauseGame(){
  if(isPaused) return;
  isPaused=true;
  clearInterval(timerInterval);
  timerPausedVal=timerVal;
  document.getElementById('pauseScore').textContent=puntos;
  document.getElementById('pauseModal').classList.add('show');
  document.getElementById('pauseBtn').textContent='▶ RESUME';
}

function resumeGame(){
  if(!isPaused) return;
  isPaused=false;
  document.getElementById('pauseModal').classList.remove('show');
  document.getElementById('pauseBtn').textContent='⏸ PAUSE';
  startTimer(timerPausedVal);
}

function togglePause(){
  if(isPaused) resumeGame();
  else pauseGame();
}

function showAbandonConfirm(){
  pauseGame();
}

function confirmAbandon(){
  clearInterval(timerInterval);
  document.getElementById('pauseModal').classList.remove('show');
  isPaused=false;
  document.getElementById('pauseBtn').textContent='⏸ PAUSE';
  endGame();
}

document.getElementById('btnRestart').addEventListener('click',function(){
  setChar('idle');show('topicSelector');
  // Actualizar datos del selector
  document.getElementById('tsGreeting').textContent='GOOD LUCK, '+jugador.toUpperCase()+'!';
  const lv=LEVELS[nivelKey];
  document.getElementById('tsLevel').textContent=lv.label+' MODE • +'+lv.pts+' PTS PER QUESTION';
  ['t1','t2','t3','t4'].forEach(id=>document.getElementById('card-'+id).classList.remove('open'));
});
document.getElementById('btnExit').addEventListener('click',function(){
  document.getElementById('goodbyeName').textContent=jugador.toUpperCase();
  show('goodbye');setChar('idle');
});
document.getElementById('btnBackHome').addEventListener('click',function(){
  show('inicio');setChar('idle');
});
</script>
</body>
</html>
