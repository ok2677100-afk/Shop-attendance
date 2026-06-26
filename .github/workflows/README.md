# Shop Attendance APK

A punch in/out attendance app with **WiFi name (SSID) verification**, **public IP check**, and **fingerprint authentication**.  
Built with plain HTML + [Capacitor](https://capacitorjs.com) → compiled into an Android APK via GitHub Actions.

---

## ✅ Features
- 📶 Detects **WiFi name (SSID)** — blocks punch if not on shop network
- 🌐 Detects **public IP address** as a fallback check
- 🫆 **Fingerprint / biometric** authentication before each punch
- 🧾 Generates a **receipt image** with QR code
- 🔐 Admin panel to configure allowed WiFi name and IP

---

## 🚀 Baby-Step Guide: Get Your APK from GitHub

Follow these steps **exactly in order**.

---

### STEP 1 — Create a GitHub Account
1. Go to **https://github.com**
2. Click **Sign up** and create a free account
3. Verify your email

---

### STEP 2 — Create a New Repository
1. After logging in, click the **+** button (top right) → **New repository**
2. Fill in:
   - **Repository name:** `shop-attendance`
   - **Visibility:** Private ✅ (recommended) or Public
   - Leave everything else unchecked
3. Click **Create repository**

---

### STEP 3 — Upload Your Files to GitHub

You need to upload **all these files** (they are in the ZIP you downloaded):

```
shop-attendance/
├── www/
│   └── index.html          ← Your app
├── .github/
│   └── workflows/
│       └── build-apk.yml   ← Auto-build script
├── package.json
├── capacitor.config.json
└── .gitignore
```

**Easiest way (no Git experience needed):**

1. On your new repository page, click **"uploading an existing file"** link
2. Drag and drop **ALL files and folders** from the ZIP
3. At the bottom type: `Initial commit`
4. Click **Commit changes**

> ⚠️ Important: Make sure `.github/workflows/build-apk.yml` is uploaded — this is what builds your APK!

---

### STEP 4 — Watch the Build Run

1. Click the **Actions** tab at the top of your repository
2. You should see **"Build Shop Attendance APK"** running (yellow dot = in progress)
3. Wait **5–10 minutes** for it to finish (green checkmark = done ✅)

If you see a ❌ red cross, click on it to see the error log.

---

### STEP 5 — Download Your APK

1. Click on the green ✅ workflow run
2. Scroll down to **Artifacts** section
3. Click **ShopAttendance-debug-apk** to download a ZIP
4. Unzip it → you'll find **app-debug.apk**

---

### STEP 6 — Install the APK on Your Android Phone

1. Transfer `app-debug.apk` to your Android phone (via USB, WhatsApp, Google Drive, etc.)
2. On your phone, open **Settings → Security** (or Privacy)
3. Enable **"Install unknown apps"** or **"Allow from this source"**
4. Tap the APK file to install it
5. Open **Shop Attendance** from your app drawer

---

### STEP 7 — First-Time Setup on the Phone

1. Open the app
2. Tap **⚙ Admin: Shop Network Config** at the top
3. **WiFi Name field:** Type your shop WiFi name exactly (e.g. `ShopNet_5G`) → tap **SAVE**
4. **IP field:** (Optional) Enter your shop's public IP → tap **SAVE**
5. Now employees can only punch in/out while connected to that WiFi!

---

## 📋 Permissions the APK will request

| Permission | Why |
|---|---|
| `ACCESS_WIFI_STATE` | Read WiFi name (SSID) |
| `ACCESS_FINE_LOCATION` | Required by Android to read WiFi SSID (Android 9+) |
| `USE_BIOMETRIC` | Fingerprint authentication |
| `INTERNET` | Fetch public IP address |
| `ACCESS_NETWORK_STATE` | Check if connected to WiFi |

> Android requires **Location permission** to read the WiFi network name. This is an Android OS requirement — the app does not use GPS.

---

## 🔄 How to update the app later

1. Edit `www/index.html` on GitHub (click the file → pencil icon)
2. Commit the change
3. GitHub Actions will automatically rebuild the APK
4. Download the new APK from the Actions tab

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| UI | HTML + Tailwind CSS |
| Native bridge | Capacitor 6 |
| WiFi detection | `@capacitor-community/wifi-info` |
| Fingerprint | `capacitor-biometric-auth` |
| Build | GitHub Actions + Gradle |
| Output | Android APK (debug) |
