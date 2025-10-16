# 🚀 Quick Start Guide (5 Minutes)

Get your 75 HARD Couples Tracker running in 5 minutes!

## What You Need

- A Google account (for Firebase - it's free!)
- Your HTML file (`75hard-tracker.html`)
- 5 minutes

## Step 1: Create Firebase Project (2 min)

1. Go to: https://console.firebase.google.com/
2. Click **"Add project"**
3. Name it: `75-hard-tracker`
4. Disable Google Analytics (optional)
5. Click **"Create project"**

## Step 2: Enable Firestore (1 min)

1. Click **"Firestore Database"** in left menu
2. Click **"Create database"**
3. Choose **"Start in test mode"**
4. Pick your region → Click **"Enable"**
5. Click **"Rules"** tab → Replace with:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /challenges/{challengeId} {
         allow read, write: if true;
       }
     }
   }
   ```
6. Click **"Publish"**

## Step 3: Get Config & Update HTML (2 min)

1. Click ⚙️ gear icon → **"Project settings"**
2. Scroll to **"Your apps"** → Click **Web icon** `</>`
3. Name it: `75 Hard Web`
4. Click **"Register app"**
5. **COPY** the `firebaseConfig` object
6. Open `75hard-tracker.html` in a text editor
7. Find line ~515 with:
   ```javascript
   const firebaseConfig = {
       apiKey: "YOUR_API_KEY_HERE",
       ...
   ```
8. **PASTE** your config there
9. **Save** the file

## Step 4: Test It! (30 sec)

1. Open `75hard-tracker.html` in browser
2. Select Partner 1 or 2
3. Check a task
4. Look for "✅ Saved [time]" in bottom right
5. Open same file in another tab/device
6. See the same data? **SUCCESS!** 🎉

## Step 5: Use on Phones

**Easiest Method**: Deploy to web

1. In your Firebase project, click **"Hosting"** in left menu
2. Click **"Get started"**
3. Install Firebase tools:
   ```bash
   npm install -g firebase-tools
   firebase login
   cd "/Users/eromonselejj/Downloads/75 Hard"
   firebase init hosting
   ```
   - Select your project
   - Public directory: `.` (just type a dot)
   - Single-page app: `No`
   - Don't overwrite files
4. Deploy:
   ```bash
   firebase deploy --only hosting
   ```
5. You'll get a URL like: `https://75-hard-tracker.web.app`
6. **Save URL to both phones' home screens**

**Alternative**: Use Netlify Drop

1. Go to: https://app.netlify.com/drop
2. Drag all 3 files (HTML, manifest.json, and .md files)
3. Get your URL instantly
4. Save to both phones' home screens

## 📱 Add to Home Screen

**iPhone**: Open in Safari → Tap Share icon → "Add to Home Screen"

**Android**: Open in Chrome → Menu (⋮) → "Add to Home screen"

## ✅ That's It!

You're ready to start your 75 HARD journey together!

---

**Having issues?** Check [SETUP.md](./SETUP.md) for detailed troubleshooting.

**First time?** Read [README.md](./README.md) to learn all the features.

**Let's go!** 💪🔥


