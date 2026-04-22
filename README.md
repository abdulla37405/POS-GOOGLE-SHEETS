# 🌿 Horti Club POS — Complete Setup Guide
### Windows Desktop + Android Mobile · Google Sheets Sync

---

## 📦 Aapko kya milega

| Device | Kaise chalega |
|--------|---------------|
| Windows PC | Electron desktop app (.exe installer) |
| Android Phone | PWA — browser se "Add to Home Screen" |
| Any Browser | Directly open karo `pwa/index.html` |

**Sab devices ek hi Google Sheet se sync hote hain — real time!**

---

## 🪟 WINDOWS DESKTOP APP

### Ek baar ka setup:

**Step 1 — Node.js install karo** (sirf ek baar)
1. https://nodejs.org kholo
2. **LTS** version download karo (e.g. v20.x.x)
3. Install karo — sab "Next" dabate jao
4. Installation ke baad PC restart karo

**Step 2 — App setup karo**
1. `electron` folder kholo
2. Us folder mein `INSTALL_WINDOWS.bat` double-click karo
3. ✅ App khul jayegi!

**Step 3 — Google Sheet connect karo** (sirf pehli baar)
- App mein Google Apps Script URL enter karo
- Agar pehle se setup hai to same URL use karo

### .exe Installer banana (doosre PCs ke liye):
```
cd electron
npm run build-win
```
→ `electron/dist/` mein `Horti Club POS Setup 1.0.0.exe` ban jayegi
→ Yeh file kisi bhi Windows PC pe double-click se install hogi

---

## 📱 ANDROID MOBILE APP (PWA)

### Option A — Local network se (WiFi pe same network)
1. Ek PC pe `pwa` folder kisi web server se serve karo:
   ```
   cd pwa
   npx serve .
   ```
   Ya Windows pe: `python -m http.server 8080`
2. PC ka local IP dekho (e.g. `192.168.1.5`)
3. Android phone pe Chrome mein kholo: `http://192.168.1.5:8080`
4. Menu (⋮) → **"Add to Home Screen"** → Install
5. ✅ Home screen pe Horti POS icon aa jayega!

### Option B — Internet pe host karo (recommended — sab jagah se access)
Free hosting options:
- **GitHub Pages** (free): `pwa` folder GitHub pe upload karo → Pages enable karo
- **Netlify** (free): netlify.com pe drag-and-drop `pwa` folder
- **Firebase Hosting** (free): Google ka service

Phir koi bhi phone browser mein woh URL khol kar install kar sakta hai.

### Option C — Same HTML file phone pe kholo
- `pwa/index.html` ko phone ke storage mein copy karo
- Chrome se open karo
- Same Google Sheet URL enter karo
- Kaam karega (PWA features nahi milenge lekin app chalega)

---

## 🔄 SYNC KAISE KAAM KARTA HAI

```
┌─────────────────────────────────────────────────────┐
│                   Google Sheets                      │
│              (Central Database / Server)              │
└────────┬──────────────────────────┬─────────────────┘
         │ Auto-sync har 60 sec     │ Auto-sync har 60 sec
         ▼                          ▼
┌─────────────────┐        ┌─────────────────┐
│  Lahore PC      │        │  Rawalpindi PC   │
│  (Windows App)  │        │  (Windows App)   │
└─────────────────┘        └─────────────────┘
         │                          │
         │ Auto-sync har 60 sec     │
         ▼                          ▼
┌─────────────────┐        ┌─────────────────┐
│  Android Phone  │        │  Android Phone   │
│  (PWA)          │        │  (PWA)           │
└─────────────────┘        └─────────────────┘
```

- **Koi bhi device pe product add/edit karo** → 60 sec mein sab devices update
- **App foreground mein aaye** → automatic sync hota hai
- **Internet nahi** → local cached data se kaam hota hai
- **Internet wapas aaye** → automatic sync resume ho jata hai

---

## ⌨️ KEYBOARD SHORTCUTS (Desktop)

| Shortcut | Kaam |
|----------|------|
| `Ctrl + F` | Products search |
| `Ctrl + N` | Bill clear / New sale |
| `Ctrl + P` | Bill generate / Print |
| `Ctrl + R` | Abhi sync karo |
| `F5` | Sync (global) |
| `Escape` | Modal band karo |

---

## ❓ COMMON PROBLEMS

**"node" command nahi mila:**
→ Node.js install karo: https://nodejs.org → PC restart karo

**npm install slow hai ya fail hua:**
→ Internet check karo → Antivirus temporarily off karo → Dobara try karo

**App mein products nahi dikh rahe:**
→ Google Sheet URL check karo → Help → Reset karo → URL dobara enter karo

**Android pe "Add to Home Screen" nahi aa raha:**
→ Chrome browser use karo (Firefox pe PWA install nahi hota)
→ HTTPS URL hona chahiye (localhost pe bhi kaam karta hai)

**Sync nahi ho raha:**
→ Google Apps Script mein "Anyone" access check karo
→ Internet connection check karo

---

## 📂 FOLDER STRUCTURE

```
horti-pos-v2/
├── electron/              ← Windows Desktop App
│   ├── INSTALL_WINDOWS.bat   ← Double-click to start!
│   ├── package.json
│   ├── main.js
│   ├── preload.js
│   └── app/
│       ├── index.html        ← Main POS app
│       ├── manifest.json
│       ├── sw.js
│       └── icons/
│
└── pwa/                   ← Mobile/Browser App
    ├── index.html            ← Same app, open in any browser
    ├── manifest.json
    ├── sw.js
    └── icons/
```

**Note:** `electron/app/` aur `pwa/` mein same app hai — ek hi codebase, do platforms!

---

*Horti Club POS v1.0.0 · Built with Electron + PWA + Google Sheets*



when i want to edit this i open html file in any editor then after editting i will save it. then i have to copy the path of electron file and paste it to cmd. then have to run this command to make .exe file :
npm run build-win
