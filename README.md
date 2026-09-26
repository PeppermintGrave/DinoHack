# DinoHack — PeppermintGrave Dino Engine

> A custom JavaScript enhancement panel for the Chrome Dino Game, built by **PeppermintGrave**.

A sleek, customizable control panel that lets you modify the Chrome Dino experience directly from the browser.

---

# Features

## Dino Engine

The **Dino Engine** provides a live control panel with:

- God Mode
- Custom game speed
- Multiple UI themes
- Custom accent colors
- Panel opacity control
- Adjustable glow strength
- Compact mode
- Minimize / expand panel
- Stop Engine
- Restart Engine
- Reset speed
- Smooth draggable interface
- Mobile-friendly controls
- Desktop support

---

# Themes

Dino Engine includes several built-in themes:

| Theme | Style |
|---|---|
| `Peppermint` | Neon green |
| `Rose` | Pink |
| `Ice` | Cyan / blue |
| `Violet` | Purple |
| `Gold` | Golden yellow |
| `Blood` | Red |
| `Custom` | Choose your own accent |

You can also select a completely custom accent color using the built-in color picker.

---

# God Mode

> **God Mode prevents the Dino game from triggering its normal `gameOver` behavior.**

When enabled:

```text
✓ God Mode
```

When disabled:

```text
ø God Mode
```

The engine also displays the current state:

```text
GOD MODE ACTIVE
```

or:

```text
GOD MODE OFF
```

---

# Speed Control

Dino Engine allows the game speed to be adjusted from:

```text
1x → 100x
```

Quick speed buttons are also available:

```text
10x
25x
75x
100x
```

The current speed is displayed directly inside the panel.

---

# Panel Customization

## Panel Opacity

The panel opacity can be adjusted from:

```text
35% → 100%
```

## Glow Strength

The panel glow can be adjusted from:

```text
0 → 5
```

This controls the intensity of the neon glow effect around the panel.

---

# Compact Mode

**Compact Mode** hides the main panel controls while keeping the engine panel available.

It switches between:

```text
Compact mode
```

and:

```text
Expand panel
```

---

# Minimize

The `−` button collapses the panel body.

When minimized, the button changes to:

```text
+
```

Press it again to restore the controls.

---

# Engine Controls

## Stop Engine

Stops the custom engine and restores the original Dino game behavior.

The panel changes to:

```text
STOPPED
```

and:

```text
ENGINE STOPPED
```

## Restart Engine

Reactivates the engine and restores the selected speed and God Mode state.

The panel returns to:

```text
ONLINE
```

and:

```text
ENGINE ACTIVE
```

## Reset Speed

Restores the original game speed.

---

# Dragging

The panel can be moved around the screen by dragging the **Dino Engine header**.

The position is constrained to the visible browser window so the panel cannot be dragged completely off-screen.

The interface uses pointer events for smooth desktop and touch dragging.

---

# Desktop

The desktop version uses a JavaScript bookmarklet.

## Requirements

- Google Chrome or Chromium-based browser
- Chrome Dino Game
- JavaScript enabled

## Usage

1. Open the Chrome Dino Game.
2. Create a browser bookmark.
3. Edit the bookmark.
4. Paste the desktop JavaScript below as the bookmark URL.
5. Save the bookmark.
6. Open the Dino Game.
7. Activate the bookmark.

> The script expects the Chrome Dino `Runner` object to be available.

If the Dino Game is not open, the script displays:

```text
Open Chrome Dino first!
```

## Desktop JavaScript

```javascript
javascript:(()=>{const old=document.getElementById("dino-engine-panel");if(old){old.remove();return}const r=window.Runner&&(Runner.instance_||Runner.getInstance());if(!r){alert("Open Chrome Dino first!");return}if(!window.dinoEngineOriginal)window.dinoEngineOriginal={gameOver:Runner.prototype.gameOver,speed:r.currentSpeed||6};const original=window.dinoEngineOriginal;let active=true,min=false,drag=false,ox=0,oy=0;const themes={Peppermint:["#00ff66%22,%22#07130d%22,%22#eaffef%22],Rose:[%22#ff4fa3%22,%22#1a0712%22,%22#fff0f7%22],Ice:[%22#55ddff%22,%22#06131c%22,%22#eafaff%22],Violet:[%22#b66bff%22,%22#10091b%22,%22#f5eaff%22],Gold:[%22#ffd45c%22,%22#1a1405%22,%22#fff9df%22],Blood:[%22#ff4242%22,%22#180606%22,%22#ffecec%22]};const%20p=document.createElement(%22div%22);p.id=%22dino-engine-panel%22;p.innerHTML=%60%3Cstyle%3E@keyframes%20pgGlow{0%,100%{box-shadow:0%200%2010px%20var(--a)}50%{box-shadow:0%200%2028px%20var(--a)}}@keyframes%20pgIn{from{opacity:0;transform:translateY(15px)%20scale(.96)}to{opacity:1;transform:none}}@keyframes%20pgPulse{50%{opacity:.45}}#dino-engine-panel{--a:#00ff66;--b:#07130d;--c:#eaffef;position:fixed;top:70px;left:20px;width:290px;max-width:92vw;z-index:2147483647;background:var(--b);color:var(--c);border:1px%20solid%20var(--a);border-radius:15px;overflow:hidden;font:13px%20Arial,sans-serif;animation:pgIn%20.3s%20ease-out,pgGlow%202.5s%20infinite;touch-action:pan-y}#pg-head{padding:12px;background:linear-gradient(110deg,var(--b),color-mix(in%20srgb,var(--a)%2022%,var(--b)));display:flex;justify-content:space-between;align-items:center;cursor:move;color:var(--a);font-weight:bold;letter-spacing:1px;touch-action:none;user-select:none;-webkit-user-select:none}#pg-body{padding:12px}#pg-body%20button,#pg-head%20button{background:var(--b);color:var(--a);border:1px%20solid%20var(--a);border-radius:7px;padding:7px;cursor:pointer}#pg-body%20button:hover{background:var(--a);color:var(--b)}#pg-body%20input[type=range]{width:100%;accent-color:var(--a)}#pg-body%20label{display:block;margin:9px%200%205px}#pg-body%20select{width:100%;padding:7px;background:var(--b);color:var(--c);border:1px%20solid%20var(--a);border-radius:6px}.pg-grid{display:grid;grid-template-columns:1fr%201fr;gap:6px;margin-top:8px}.pg-row{display:flex;gap:6px;align-items:center;justify-content:space-between}#pg-status{color:var(--a);margin-top:10px;font-size:11px;animation:pgPulse%202s%20infinite}#pg-foot{opacity:.65;font-size:10px;margin-top:9px;text-align:center}%3C/style%3E%3Cdiv%20id=%22pg-head%22%3E%3Cspan%3E%E2%9C%A6%20PEPPERMINTGRAVE%3C/span%3E%3Cspan%3E%3Cbutton%20id=%22pg-min%22%3E%E2%88%92%3C/button%3E%20%3Cbutton%20id=%22pg-close%22%3E%C3%97%3C/button%3E%3C/span%3E%3C/div%3E%3Cdiv%20id=%22pg-body%22%3E%3Cdiv%20class=%22pg-row%22%3E%3Cb%3EDINO%20ENGINE%3C/b%3E%3Cspan%20id=%22pg-mode%22%3EONLINE%3C/span%3E%3C/div%3E%3Clabel%3ETheme%3C/label%3E%3Cselect%20id=%22pg-theme%22%3E%3Coption%3EPeppermint%3C/option%3E%3Coption%3ERose%3C/option%3E%3Coption%3EIce%3C/option%3E%3Coption%3EViolet%3C/option%3E%3Coption%3EGold%3C/option%3E%3Coption%3EBlood%3C/option%3E%3Coption%3ECustom%3C/option%3E%3C/select%3E%3Clabel%3ECustom%20accent%20%3Cinput%20id=%22pg-color%22%20type=%22color%22%20value=%22#00ff66%22%20style=%22float:right%22%3E%3C/label%3E%3Clabel%3E%3Cspan%20id=%22pg-god-icon%22%3E%E2%9C%93%3C/span%3E%20God%20Mode%20%3Cinput%20id=%22pg-god%22%20type=%22checkbox%22%20checked%20style=%22display:none%22%3E%3C/label%3E%3Clabel%3ESpeed:%20%3Cb%20id=%22pg-speedtxt%22%3E75x%3C/b%3E%3C/label%3E%3Cinput%20id=%22pg-speed%22%20type=%22range%22%20min=%221%22%20max=%22100%22%20value=%2275%22%3E%3Cdiv%20class=%22pg-grid%22%3E%3Cbutton%20data-speed=%2210%22%3E10x%3C/button%3E%3Cbutton%20data-speed=%2225%22%3E25x%3C/button%3E%3Cbutton%20data-speed=%2275%22%3E75x%3C/button%3E%3Cbutton%20data-speed=%22100%22%3E100x%3C/button%3E%3C/div%3E%3Clabel%3EPanel%20opacity%20%3Cb%20id=%22pg-opval%22%3E96%%3C/b%3E%3C/label%3E%3Cinput%20id=%22pg-opacity%22%20type=%22range%22%20min=%2235%22%20max=%22100%22%20value=%2296%22%3E%3Clabel%3EGlow%20strength%20%3Cb%20id=%22pg-glowval%22%3E2%3C/b%3E%3C/label%3E%3Cinput%20id=%22pg-glow%22%20type=%22range%22%20min=%220%22%20max=%225%22%20value=%222%22%3E%3Cdiv%20class=%22pg-grid%22%3E%3Cbutton%20id=%22pg-compact%22%3ECompact%20mode%3C/button%3E%3Cbutton%20id=%22pg-reset%22%3EReset%20speed%3C/button%3E%3Cbutton%20id=%22pg-stop%22%3EStop%20Engine%3C/button%3E%3Cbutton%20id=%22pg-restart%22%3ERestart%20Engine%3C/button%3E%3C/div%3E%3Cdiv%20id=%22pg-status%22%3E%E2%97%8F%20ENGINE%20ACTIVE%3C/div%3E%3Cdiv%20id=%22pg-foot%22%3EPEPPERMINTGRAVE%20%E2%80%A2%20DINO%20ENGINE%3C/div%3E%3C/div%3E%60;document.body.appendChild(p);const%20$=id=%3Ep.querySelector(%22#%22+id),body=$(%22pg-body%22),head=$(%22pg-head%22),status=$(%22pg-status%22),speed=$(%22pg-speed%22);function%20color(c){p.style.setProperty(%22--a%22,c);$(%22pg-color%22).value=c;const%20rgb=parseInt(c.slice(1),16);const%20dark=%22#%22+[rgb%3E%3E16,(rgb%3E%3E8)&255,rgb&255].map(v=%3EMath.round(v*.12).toString(16).padStart(2,%220%22)).join(%22%22);p.style.setProperty(%22--b%22,dark);p.style.setProperty(%22--c%22,%22#f4fff7%22)}function%20setSpeed(v){v=Math.max(1,Math.min(100,+v||1));speed.value=v;$(%22pg-speedtxt%22).textContent=v+%22x%22;if(active)r.setSpeed(v)}function%20god(v){$(%22pg-god%22).checked=v;$(%22pg-god-icon%22).textContent=v?%22%E2%9C%93%22:%22%C3%B8%22;if(active)Runner.prototype.gameOver=r.gameOver=v?function(){}:original.gameOver;status.textContent=v?%22%E2%97%8F%20GOD%20MODE%20ACTIVE%22:%22%E2%97%8F%20GOD%20MODE%20OFF%22}function%20start(){active=true;Runner.prototype.gameOver=r.gameOver=function(){};setSpeed(speed.value);god($(%22pg-god%22).checked);$(%22pg-mode%22).textContent=%22ONLINE%22;status.textContent=%22%E2%97%8F%20ENGINE%20ACTIVE%22}function%20stop(){active=false;Runner.prototype.gameOver=original.gameOver;r.gameOver=original.gameOver;r.setSpeed(original.speed||6);$(%22pg-mode%22).textContent=%22STOPPED%22;$(%22pg-god%22).checked=false;$(%22pg-god-icon%22).textContent=%22%C3%B8%22;status.textContent=%22%E2%97%8F%20ENGINE%20STOPPED%22}function%20applyTheme(){const%20t=$(%22pg-theme%22).value;if(t===%22Custom%22)return;const%20c=themes[t];if(!c)return;color(c[0]);p.style.setProperty(%22--b%22,c[1]);p.style.setProperty(%22--c%22,c[2])}const%20theme=$(%22pg-theme%22);theme.addEventListener(%22change%22,applyTheme);theme.addEventListener(%22input%22,applyTheme);$(%22pg-color%22).oninput=e=%3E{$(%22pg-theme%22).value=%22Custom%22;color(e.target.value)};$(%22pg-speed%22).oninput=()=%3EsetSpeed(speed.value);p.querySelectorAll(%22[data-speed]%22).forEach(b=%3Eb.onclick=()=%3EsetSpeed(b.dataset.speed));$(%22pg-god%22).onchange=e=%3Egod(e.target.checked);$(%22pg-opacity%22).oninput=e=%3E{const%20v=e.target.value;$(%22pg-opval%22).textContent=v+%22%%22;p.style.opacity=v/100};$(%22pg-glow%22).oninput=e=%3E{const%20v=+e.target.value;$(%22pg-glowval%22).textContent=v;p.style.animationDuration=v===0?%220s%22:%222.5s%22;p.style.boxShadow=%600%200%20${v*10}px%20var(--a)%60};let%20compact=false;$(%22pg-compact%22).onclick=()=%3E{compact=!compact;body.style.display=compact?%22none%22:%22block%22;$(%22pg-compact%22).textContent=compact?%22Expand%20panel%22:%22Compact%20mode%22};$(%22pg-min%22).onclick=()=%3E{min=!min;body.style.display=min?%22none%22:%22block%22;$(%22pg-min%22).textContent=min?%22+%22:%22%E2%88%92%22};$(%22pg-close%22).onclick=()=%3Ep.remove();$(%22pg-reset%22).onclick=()=%3EsetSpeed(original.speed||6);$(%22pg-stop%22).onclick=stop;$(%22pg-restart%22).onclick=start;head.addEventListener(%22pointerdown%22,e=%3E{if(e.target.closest(%22button%22))return;drag=true;const%20rect=p.getBoundingClientRect();ox=e.clientX-rect.left;oy=e.clientY-rect.top;try{head.setPointerCapture(e.pointerId)}catch(err){}});head.addEventListener(%22pointermove%22,e=%3E{if(!drag)return;const%20x=Math.max(0,Math.min(window.innerWidth-p.offsetWidth,e.clientX-ox));const%20y=Math.max(0,Math.min(window.innerHeight-p.offsetHeight,e.clientY-oy));p.style.left=x+%22px%22;p.style.top=y+%22px%22;});const%20endDrag=()=%3E{drag=false};head.addEventListener(%22pointerup%22,endDrag);head.addEventListener(%22pointercancel%22,endDrag);color(themes.Peppermint[0]);start()})();
```

---

# Mobile

The mobile version is provided as a JavaScript bookmarklet and is designed for touch-based use.

It includes:

- God Mode
- Speed control
- Themes
- Custom colors
- Panel opacity
- Glow strength
- Compact mode
- Minimize
- Stop Engine
- Restart Engine
- Reset speed
- Touch-friendly dragging

## Mobile JavaScript

```javascript
(()=>{const e=document.getElementById("dino-engine-panel");if(e)return void e.remove();const t=window.Runner&&(Runner.instance_||Runner.getInstance());if(!t)return void alert("Open Chrome Dino first!");window.dinoEngineOriginal||(window.dinoEngineOriginal={gameOver:Runner.prototype.gameOver,speed:t.currentSpeed||6});const o=window.dinoEngineOriginal;let n=true,r=false,a=false,c=0,d=0;const i={Peppermint:["#00ff66","#07130d","#eaffef"],Rose:["#ff4fa3","#1a0712","#fff0f7"],Ice:["#55ddff","#06131c","#eafaff"],Violet:["#b66bff","#10091b","#f5eaff"],Gold:["#ffd45c","#1a1405","#fff9df"],Blood:["#ff4242","#180606","#ffecec"]},p=document.createElement("div");p.id="dino-engine-panel",p.innerHTML='<style>@keyframes pgGlow{0%,100%{box-shadow:0 0 10px var(--a)}50%{box-shadow:0 0 28px var(--a)}}@keyframes pgIn{from{opacity:0;transform:translateY(15px) scale(.96)}to{opacity:1;transform:none}}@keyframes pgPulse{50%{opacity:.45}}#dino-engine-panel{--a:#00ff66;--b:#07130d;--c:#eaffef;position:fixed;top:70px;left:20px;width:290px;max-width:92vw;z-index:2147483647;background:var(--b);color:var(--c);border:1px solid var(--a);border-radius:15px;overflow:hidden;font:13px Arial,sans-serif;animation:pgIn .3s ease-out,pgGlow 2.5s infinite;touch-action:pan-y}#pg-head{padding:12px;background:linear-gradient(110deg,var(--b),color-mix(in srgb,var(--a) 22%,var(--b)));display:flex;justify-content:space-between;align-items:center;cursor:move;color:var(--a);font-weight:bold;letter-spacing:1px;touch-action:none;user-select:none;-webkit-user-select:none}#pg-body{padding:12px}#pg-body button,#pg-head button{background:var(--b);color:var(--a);border:1px solid var(--a);border-radius:7px;padding:7px;cursor:pointer}#pg-body button:hover{background:var(--a);color:var(--b)}#pg-body input[type=range]{width:100%;accent-color:var(--a)}#pg-body label{display:block;margin:9px 0 5px}#pg-body select{width:100%;padding:7px;background:var(--b);color:var(--c);border:1px solid var(--a);border-radius:6px}.pg-grid{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-top:8px}.pg-row{display:flex;gap:6px;align-items:center;justify-content:space-between}#pg-status{color:var(--a);margin-top:10px;font-size:11px;animation:pgPulse 2s infinite}#pg-foot{opacity:.65;font-size:10px;margin-top:9px;text-align:center}</style><div id="pg-head"><span>✦ PEPPERMINTGRAVE</span><span><button id="pg-min">−</button> <button id="pg-close">×</button></span></div><div id="pg-body"><div class="pg-row"><b>DINO ENGINE</b><span id="pg-mode">ONLINE</span></div><label>Theme</label><select id="pg-theme"><option>Peppermint</option><option>Rose</option><option>Ice</option><option>Violet</option><option>Gold</option><option>Blood</option><option>Custom</option></select><label>Custom accent <input id="pg-color" type="color" value="#00ff66" style="float:right"></label><label><span id="pg-god-icon">✓</span> God Mode <input id="pg-god" type="checkbox" checked style="display:none"></label><label>Speed: <b id="pg-speedtxt">75x</b></label><input id="pg-speed" type="range" min="1" max="100" value="75"><div class="pg-grid"><button data-speed="10">10x</button><button data-speed="25">25x</button><button data-speed="75">75x</button><button data-speed="100">100x</button></div><label>Panel opacity <b id="pg-opval">96%</b></label><input id="pg-opacity" type="range" min="35" max="100" value="96"><label>Glow strength <b id="pg-glowval">2</b></label><input id="pg-glow" type="range" min="0" max="5" value="2"><div class="pg-grid"><button id="pg-compact">Compact mode</button><button id="pg-reset">Reset speed</button><button id="pg-stop">Stop Engine</button><button id="pg-restart">Restart Engine</button></div><div id="pg-status">● ENGINE ACTIVE</div><div id="pg-foot">PEPPERMINTGRAVE • DINO ENGINE</div></div>',document.body.appendChild(p);const s=e=>p.querySelector("#"+e),g=s("pg-body"),l=s("pg-head"),m=s("pg-status"),u=s("pg-speed");function f(e){p.style.setProperty("--a",e),s("pg-color").value=e;const t=parseInt(e.slice(1),16),o="#"+[t>>16,t>>8&255,255&t].map((e=>Math.round(.12*e).toString(16).padStart(2,"0"))).join("");p.style.setProperty("--b",o),p.style.setProperty("--c","#f4fff7")}function v(e){e=Math.max(1,Math.min(100,+e||1)),u.value=e,s("pg-speedtxt").textContent=e+"x",n&&t.setSpeed(e)}function y(e){s("pg-god").checked=e,s("pg-god-icon").textContent=e?"✓":"ø",n&&(Runner.prototype.gameOver=t.gameOver=e?function(){}:o.gameOver,m.textContent=e?"● GOD MODE ACTIVE":"● GOD MODE OFF")}function k(){n=true,Runner.prototype.gameOver=t.gameOver=function(){},v(u.value),y(s("pg-god").checked),s("pg-mode").textContent="ONLINE",m.textContent="● ENGINE ACTIVE"}function b(){n=false,Runner.prototype.gameOver=o.gameOver,t.gameOver=o.gameOver,t.setSpeed(o.speed||6),s("pg-mode").textContent="STOPPED",s("pg-god").checked=false,s("pg-god-icon").textContent="ø",m.textContent="● ENGINE STOPPED"}function h(){const e=s("pg-theme").value;if("Custom"!==e){const t=i[e];t&&(f(t[0]),p.style.setProperty("--b",t[1]),p.style.setProperty("--c",t[2]))}}const E=s("pg-theme");E.addEventListener("change",h),E.addEventListener("input",h),s("pg-color").oninput=(e=>{s("pg-theme").value="Custom",f(e.target.value)}),s("pg-speed").oninput=(()=>v(u.value)),p.querySelectorAll("[data-speed]").forEach((e=>e.onclick=(()=>v(e.dataset.speed)))),s("pg-god").onchange=(e=>y(e.target.checked)),s("pg-opacity").oninput=(e=>{const t=e.target.value;s("pg-opval").textContent=t+"%",p.style.opacity=t/100}),s("pg-glow").oninput=(e=>{const t=+e.target.value;s("pg-glowval").textContent=t,p.style.animationDuration=0===t?"0s":"2.5s",p.style.boxShadow=`0 0 ${10*t}px var(--a)`});let x=false;s("pg-compact").onclick=(()=>{x=!x,g.style.display=x?"none":"block",s("pg-compact").textContent=x?"Expand panel":"Compact mode"}),s("pg-min").onclick=(()=>{r=!r,g.style.display=r?"none":"block",s("pg-min").textContent=r?"+":"−"}),s("pg-close").onclick=(()=>e.remove()),s("pg-reset").onclick=(()=>v(o.speed||6)),s("pg-stop").onclick=b,s("pg-restart").onclick=k,l.addEventListener("pointerdown",(e=>{if(!e.target.closest("button")){a=true;const t=p.getBoundingClientRect();c=e.clientX-t.left,d=e.clientY-t.top;try{l.setPointerCapture(e.pointerId)}catch(e){}}})),l.addEventListener("pointermove",(e=>{if(a){const t=Math.max(0,Math.min(window.innerWidth-p.offsetWidth,e.clientX-c)),o=Math.max(0,Math.min(window.innerHeight-p.offsetHeight,e.clientY-d));p.style.left=t+"px",p.style.top=o+"px"}}));const S=()=>{a=false};l.addEventListener("pointerup",S),l.addEventListener("pointercancel",S),f(i.Peppermint[0]),k()})();
```

---

# Repository Structure

```text
DinoHack/
│
├── Scripts/
│   ├── Desktop
│   └── Mobile
│
└── README.md
```

> The scripts are separated by platform so users can choose the version appropriate for their device.

---

# How It Works

Dino Engine interacts with the Chrome Dino game's JavaScript `Runner` object.

Before modifying the game, the script stores the original state:

```javascript
window.dinoEngineOriginal
```

This allows the engine to restore the original game behavior when it is stopped.

The engine modifies:

```javascript
Runner.prototype.gameOver
```

and accesses the current Dino game instance through:

```javascript
Runner.instance_
```

or:

```javascript
Runner.getInstance()
```

The speed is controlled through the Dino Runner instance's:

```javascript
setSpeed()
```

method.

---

# Engine Lifecycle

```text
Open Chrome Dino
       ↓
Run Dino Engine
       ↓
Detect Runner
       ↓
Create Control Panel
       ↓
Apply Settings
       ↓
Engine Active
       ↓
Stop / Restart / Close
```

When the engine is stopped, the original `gameOver` behavior and stored game speed are restored.

---

# UI Design

The interface follows the **PeppermintGrave** aesthetic.

### Visual Elements

- Neon accent colors
- Dark backgrounds
- Rounded corners
- Animated glow
- Smooth entrance animation
- Pulsing engine status
- Minimal control layout
- Responsive width
- Touch-friendly interaction

The default theme is:

```text
PEPPERMINT
```

with a neon-green accent.

---

# Status Indicators

### Engine Active

```text
ENGINE ACTIVE
```

### Engine Stopped

```text
ENGINE STOPPED
```

### God Mode Active

```text
GOD MODE ACTIVE
```

### God Mode Disabled

```text
GOD MODE OFF
```

---

# Compatibility

Dino Engine relies on the internal JavaScript structure of the Chrome Dino Game.

Browser updates can change internal objects such as:

```javascript
Runner
Runner.instance_
Runner.getInstance()
Runner.prototype.gameOver
```

If Chrome changes these internals, parts of the engine may stop working until the script is updated.

---

# Troubleshooting

### `Open Chrome Dino first!`

Make sure the Chrome Dino Game is already open before running the script.

### The panel does not appear

Try:

1. Reloading the Dino Game.
2. Starting the Dino Game.
3. Running the script again.
4. Checking that JavaScript is enabled.

### Speed does not change

The engine depends on the Dino game's `Runner` instance and its `setSpeed()` method.

A browser update may change this behavior.

### Dragging does not work

Drag from the **DINO ENGINE header**, rather than directly from a button.

---

# Project Goals

DinoHack is designed to provide a clean and customizable interface for experimenting with the Chrome Dino game's client-side JavaScript.

Future versions may introduce additional customization and experimental controls.

---

# Creator

## PeppermintGrave

> **PEPPERMINTGRAVE • DINO ENGINE**

Built with:

```text
JavaScript
HTML
CSS
Chrome Dino Runner
```

---

# Disclaimer

DinoHack is an experimental browser-side JavaScript project intended for educational and personal experimentation with the Chrome Dino Game.

Use it responsibly and only in environments where modifying the game is permitted.

---

# Support

If you find the project interesting, consider giving the repository a star.

**Repository:**  
https://github.com/PeppermintGrave/DinoHack

---

> **PEPPERMINTGRAVE — DINO ENGINE**
>
> *Customize the run. Control the engine. Keep going.*
