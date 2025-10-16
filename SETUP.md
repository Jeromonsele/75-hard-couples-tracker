# 75 HARD Couples Tracker - Setup Guide

This guide will walk you through setting up your shared 75 HARD tracker with Firebase (100% FREE).

## 🎯 Overview

Your tracker now syncs between devices using Google Firebase. Both partners can check in from their phones, and progress updates automatically every 3 seconds!

## 📋 Step-by-Step Setup (15 minutes)

### Step 1: Create a Free Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **"Add project"** or **"Create a project"**
3. Enter a project name (e.g., "75-hard-tracker")
4. You can disable Google Analytics (not needed for this app)
5. Click **"Create project"** and wait for it to finish

### Step 2: Set Up Firestore Database

1. In your Firebase project, click **"Firestore Database"** in the left menu
2. Click **"Create database"**
3. Choose **"Start in test mode"** (we'll secure it in a moment)
4. Select a Firestore location (choose closest to you)
5. Click **"Enable"**

### Step 3: Configure Firestore Security Rules

1. In Firestore, click the **"Rules"** tab at the top
2. Replace the rules with this:

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

3. Click **"Publish"**

> **Note:** These rules allow anyone to read/write. Since it's just for you two, this is fine. For more security, you could add Firebase Authentication later.

### Step 4: Get Your Firebase Configuration

1. In Firebase Console, click the **gear icon** ⚙️ next to "Project Overview"
2. Click **"Project settings"**
3. Scroll down to **"Your apps"** section
4. Click the **Web icon** `</>` (it says "Add an app")
5. Give your app a nickname (e.g., "75 Hard Web")
6. **Do NOT** check "Set up Firebase Hosting"
7. Click **"Register app"**
8. You'll see code that looks like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyAbc123...",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

9. **Copy this entire firebaseConfig object**

### Step 5: Update Your HTML File

1. Open `75hard-tracker.html` in a text editor
2. Find this section (around line 515):

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY_HERE",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

3. **Replace it with your config from Step 4**
4. Save the file

### Step 6: Test It Out!

1. Open `75hard-tracker.html` in your web browser
2. Select "Partner 1" or "Partner 2"
3. Check a task or two
4. You should see "✅ Saved [time]" in the bottom right corner
5. Open the same file in another browser or device
6. Select the other partner
7. You should see the same data!

## 📱 Access from Your Phones

You have several options:

### Option A: Simple File Hosting (Easiest)

1. Upload your files to a free hosting service:
   - **Firebase Hosting** (recommended, free): See instructions below
   - **Netlify Drop** ([app.netlify.com/drop](https://app.netlify.com/drop)) - Just drag and drop your files
   - **GitHub Pages** - Free if you have a GitHub account

### Option B: Firebase Hosting (Recommended)

1. Install Firebase CLI:
   ```bash
   npm install -g firebase-tools
   ```

2. Login to Firebase:
   ```bash
   firebase login
   ```

3. In your project folder, initialize hosting:
   ```bash
   firebase init hosting
   ```
   - Select your Firebase project
   - Set public directory to: `.` (current directory)
   - Configure as single-page app: `No`
   - Don't overwrite existing files

4. Deploy:
   ```bash
   firebase deploy --only hosting
   ```

5. You'll get a URL like: `https://your-project.web.app`

6. Save this URL to your phone's home screen:
   - **iPhone**: Open in Safari > Tap Share > "Add to Home Screen"
   - **Android**: Open in Chrome > Menu (⋮) > "Add to Home screen"

### Option C: Local Network Access

If both phones are on the same WiFi:

1. Find your computer's IP address:
   - **Mac**: System Settings > Network > Your connection > IP address
   - **Windows**: Open CMD, type `ipconfig`, look for IPv4 Address

2. Start a simple web server in your project folder:
   ```bash
   # Python 3
   python3 -m http.server 8000
   
   # Or Python 2
   python -m SimpleHTTPServer 8000
   ```

3. On your phones, visit: `http://YOUR_IP_ADDRESS:8000/75hard-tracker.html`

## 🎉 You're Done!

Both of you can now:
- ✅ Check in from your phones
- ✅ See each other's progress
- ✅ Updates sync every 3 seconds automatically
- ✅ Add reflections and track your journey together

## 🔧 Troubleshooting

### "Firebase not configured" message
- Make sure you replaced the `firebaseConfig` with your actual config
- Check that all values are in quotes

### "Permission denied" error
- Make sure you published the Firestore security rules in Step 3

### Changes not syncing
- Check the sync indicator in the bottom right
- Make sure both devices have internet connection
- Try refreshing the page

### Can't access from phone
- Make sure your HTML file includes your Firebase config
- Try clearing your browser cache

## 🔐 Security Notes

- The current setup allows anyone with the link to read/write data
- This is fine for private use between two people
- For more security, you can add Firebase Authentication later
- Don't share your deployed URL publicly

## 💪 Tips

- Save the URL to both phones' home screens for easy access
- Turn on notifications (if you add that feature later)
- Check in together every day for accountability!

---

**Need help?** Check the [Firebase Documentation](https://firebase.google.com/docs/firestore) or leave a comment.

**Want to customize?** The HTML file is fully self-contained - edit it however you like!


