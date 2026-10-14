# RIZQ admin setup (one time, ~15 minutes)

`admin.html` lets you add, edit and delete products, upload photos and mark items out of stock from your phone. Changes show on the shop straight away. It uses two free services: **Firebase** (data + login) and **Cloudinary** (photos). No card needed.

## 1. Firebase
1. Go to console.firebase.google.com, **Add project** (name it `rizq`, Analytics off).
2. Click the **`</>`** web icon, register an app, and copy the `firebaseConfig` values into `firebase-config.js` (`apiKey`, `authDomain`, `projectId`, `appId`).
3. **Build → Authentication → Get started → Email/Password → enable.** On the **Users** tab, **Add user** with your own email and password. This is your admin login.
4. **Build → Firestore Database → Create database** (location `asia-south1`, production mode). On the **Rules** tab paste this and **Publish**:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /products/{id} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /settings/{id} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

## 2. Cloudinary
1. Sign up at cloudinary.com. Copy the **Cloud name** into `firebase-config.js` (`cloud`).
2. **Settings → Upload → Upload presets → Add upload preset**, set **Signing mode: Unsigned**, save, and copy the preset name into `firebase-config.js` (`preset`).

## 3. Upload to GitHub
Upload `index.html`, `admin.html`, `firebase-config.js` to the repo root. Make sure the names are exact (no `-1` or `(1)` added). Delete the old `style.css`, `script.js`, `admin.css`, `admin.js`.

## 4. First use
Open `your-site/admin.html`, sign in, tap **Import current products** once, then edit anything. Until you import, the shop shows the built-in list inside `index.html`.

If a change does not appear, refresh the page (or clear the browser cache).
