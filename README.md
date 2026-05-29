# ULTIMATE FLAME GAS CENTRE — Sales Portal

🔥 Real-time sales tracking system with instant sync across all devices.

**Live Demo:** https://YOUR_USERNAME.github.io/gas-sales-portal  
**Code:** https://github.com/YOUR_USERNAME/gas-sales-portal

---

## 📋 Features

✅ **Real-time sync** — Alvin's sales appear instantly for Winnie & Tedd  
✅ **Live inventory** — See filled/empty cylinders & burner/grill counts  
✅ **Owner dashboard** — Tedd sees all sales totals & can delete entries  
✅ **Payment tracking** — Record Cash or Till payments  
✅ **Multi-device** — Works on phones, tablets, laptops  
✅ **No login needed for setup** — Everything in one HTML file  

---

## 🚀 Setup (First Time Only)

### **Step 1: Set Up Firebase** (5 minutes)

1. Go to **https://firebase.google.com**
2. Click **"Get Started"** → Sign in with Google
3. Click **"Create a project"**
   - Name: `Ultimate Flame Gas Centre`
   - Disable Google Analytics
   - Click **"Create project"**
   - Wait for it to load...

4. Click **"Realtime Database"** (left menu)
5. Click **"Create Database"**
   - Location: Choose closest to Kenya
   - Security: **"Start in Test Mode"**
   - Click **"Create"**

6. Look at the top — you'll see a blue URL like:
   ```
   https://ultimate-flame-xxxxx.firebaseio.com
   ```
   **Copy this URL** (you'll need it soon)

### **Step 2: Get Your Firebase Config**

1. In Firebase Console, click ⚙️ **Settings** (gear icon, top left)
2. Click **"Project Settings"**
3. Scroll to **"Your apps"** section
4. Click **"Add App"** → pick **Web** icon
5. App name: `Sales Portal`
6. A code box appears with `firebaseConfig` object
7. **Copy the entire config** (all the {...} part)

### **Step 3: Edit the HTML File**

1. Download `index.html` (from the files below)
2. Open in a text editor (Notepad, VSCode, etc.)
3. Find this section (near the top):
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY_HERE",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     databaseURL: "https://YOUR_PROJECT.firebaseio.com",
     ...
   };
   ```
4. **Replace everything inside the `{}` with your config from Step 2**
5. Save the file

### **Step 4: Upload to GitHub**

#### **Option A: Use GitHub Web Interface (Easiest)**

1. Go to **https://github.com** → Sign in
2. Click **"New"** → Create repository
   - Name: `gas-sales-portal`
   - Description: `Ultimate Flame Gas Centre`
   - **Public** (so it's accessible)
   - Click **"Create repository"**

3. Click **"Add file"** → **"Upload files"**
4. Drag the edited `index.html` into GitHub
5. Rename it to **`index.html`** (if not already)
6. Click **"Commit changes"**

7. Go to **Settings** → **"Pages"** (left menu)
   - Source: **"Deploy from a branch"**
   - Branch: **"main"**
   - Folder: **"/ (root)"**
   - Click **"Save"**

8. Wait 1-2 minutes, then visit:
   ```
   https://YOUR_USERNAME.github.io/gas-sales-portal
   ```
   ✅ **It's live!**

#### **Option B: Use Git Command Line**

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/gas-sales-portal.git
cd gas-sales-portal

# Copy your edited file
cp /path/to/index.html .

# Commit & push
git add index.html
git commit -m "Add gas sales portal with Firebase"
git push origin main
```

---

## 👥 How to Use

### **For Employees (Alvin, Ken, Winnie)**

1. Open the link: `https://YOUR_USERNAME.github.io/gas-sales-portal`
2. Select your name & enter password:
   - **Alvin** / `Alvin123`
   - **Ken** / `Ken234`
   - **Winnie** / `Winnie254`
3. Pick a sale type: **Outrights**, **Full Set**, or **Refill**
4. Click a cylinder → Set quantity → Choose **Cash** or **Till**
5. Click **"✓ Record Sale"**
6. ✅ **Your sale is recorded instantly!**

**Real-time magic:** When Alvin records a sale, Winnie & Tedd **instantly see it** without refreshing!

---

### **For Owner (Tedd)**

1. Login: **Tedd** / `Tedd254`
2. You see extra sections at top:
   - **💰 Totals** — sales by Outrights/Full Set/Refill & **Grand Total**
   - **📦 Live Inventory** — filled/empty cylinders & accessory counts
   - **📥 Add Stock** — restock cylinders, burners, grills from factory

3. **Delete a sale:**
   - Click the **✕** button on any sale in the log
   - Stock is automatically restored

---

## 🔐 Change Passwords

To change staff passwords, edit `index.html`:

Find this section (near top):
```javascript
const USERS = [
  { name:"Alvin",   password:"Alvin123",  role:"employee" },
  { name:"Ken",     password:"Ken234",    role:"employee" },
  { name:"Winnie",  password:"Winnie254", role:"employee" },
  { name:"Tedd",    password:"Tedd254",   role:"owner"    },
];
```

Change passwords, then commit to GitHub:
```bash
git add index.html
git commit -m "Update staff passwords"
git push origin main
```

---

## 💰 Edit Prices

In `index.html`, find the `CYL_PRICES` section:
```javascript
const CYL_PRICES = {
  "mgas-6kg": { "Outrights":3000, "Full Set":3200, "Refill":1000 },
  "pgas-6kg": { "Outrights":4000, "Full Set":5000, "Refill":1450 },
  ...
};
```

Update any price, save, and push to GitHub. Changes go live in seconds! 🚀

---

## 🆘 Troubleshooting

| Problem | Solution |
|---------|----------|
| **Red error at top** | Your Firebase config is missing. Re-read Step 2 & 3 above. |
| **Data not syncing** | Refresh the page. Check you used **Test Mode** in Firebase. |
| **"Out of stock"** | Owner needs to add stock via **📥 Add Stock** section. |
| **Can't login** | Check password spelling (case-sensitive). |
| **Page is blank** | Browser cache issue — try `Ctrl+Shift+Delete` (clear cache) & refresh. |

---

## 📝 Firebase Database Structure

Your data is stored in Firebase like this:

```
sales/
  -abc123/
    employee: "Alvin"
    cylName: "K-Gas 6kg"
    tab: "Outrights"
    total: 4000
    time: 1234567890
    ...

inventory/
  filled/
    mgas-6kg: 4
    kgas-6kg: 3
  empty/
    mgas-6kg: 1
  burners: 9
  grills: 10
```

---

## 🔧 Customize for Your Business

### Add a new gas brand:

1. Edit `CYLINDERS` array:
   ```javascript
   const CYLINDERS = [
     { id:"newbrand-6kg", name:"New Brand 6kg" },
     ...
   ];
   ```

2. Add prices:
   ```javascript
   const CYL_PRICES = {
     "newbrand-6kg": { "Outrights":3500, "Full Set":4500, "Refill":1200 },
     ...
   };
   ```

3. Add starting stock:
   ```javascript
   const START_FILLED = {
     "newbrand-6kg": 5,
     ...
   };
   ```

4. Commit & push to GitHub

---

## 📞 Support

- **Firebase Issues?** Check [Firebase Docs](https://firebase.google.com/docs)
- **GitHub Pages not working?** Check your repository settings
- **Sales not syncing?** Check your internet connection & browser

---

## 📄 License

This project is free to use. Feel free to customize for your business!

---

**Built with ❤️ for ULTIMATE FLAME GAS CENTRE**
