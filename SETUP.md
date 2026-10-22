# Măsurători: setup guide

The app records measurements for rolete and plase without internet. When the phone is on Wi‑Fi and the app is open, each saved sheet (fișă) uploads to a folder in your Google Drive.

Setup takes about 20 minutes and is free. There are three parts.

## 1. Put the app online (GitHub Pages)

1. Create a free account at https://github.com
2. Click **New repository**. Name it `masuratori`, set it to **Public**, and create it.
3. Click **uploading an existing file**. Upload `index.html`, `sw.js`, `manifest.webmanifest`, `icon-192.png` and `icon-512.png`, then click **Commit changes**.
4. Go to **Settings → Pages**. Under "Branch", choose `main` and `/ (root)`, then click **Save**.
5. After a minute or two, the app is at `https://YOUR-USERNAME.github.io/masuratori/`

## 2. Let the app use Google Drive (Google Cloud)

1. Go to https://console.cloud.google.com and create a new project (for example "Masuratori").
2. Open **APIs & Services → Library**, search for **Google Drive API**, and click **Enable**.
3. Open **Google Auth Platform** (also called "OAuth consent screen") and click **Get started**:
   - App name: Masuratori. Support email: your email.
   - Audience: **External**.
   - Contact email: your email. Accept and create.
4. Under **Audience → Test users**, add the Gmail address of every person who will use the app.
5. Under **Clients**, click **Create client**:
   - Application type: **Web application**
   - Authorized JavaScript origins: `https://YOUR-USERNAME.github.io` (only this, without `/masuratori`)
   - Click **Create** and copy the **Client ID** (it ends in `.apps.googleusercontent.com`).

The Client ID isn't a secret, so it's fine that the app is public.

## 3. Install on the Android phone

1. Open the app link in **Chrome** on the phone.
2. Open **Setări**, paste the Client ID, and set the **Folder în Drive** name.
3. Tap **Conectare la Google**. Google warns that the app isn't verified. That's expected for your own private app: tap **Continue** and allow access.
4. In Chrome's menu (⋮), tap **Add to Home screen** or **Install app**.

From now on, open it from the home screen icon. It works without internet.

## Using it

- Under **Măsurare**, write the client name, then add positions one by one. One sheet can mix rolete and plase.
  - **Rolete:** material (PVC is only white; Aluminiu is alb, maro or antracit), lățime × înălțime (mm), acționare.
  - **Plase:** model (ISO, Mobilă, Plisee, Culisantă), color, interior or exterior dimension, lățime × înălțime (mm).
- After adding a position, the product, material or model, color, and interior/exterior choice stay selected for the next one. Acționare must be picked every time.
- What you're writing is kept even if you close the app or the phone restarts.
- **Salvează fișa** saves the sheet on the phone as **În așteptare**. It uploads by itself on Wi‑Fi while the app is open. On mobile data, you can tap **Încarcă acum**.
- Google sign-in lasts about an hour. After that, when sheets are waiting, the top bar shows **Conectare**: one tap and they upload.
- Each sheet becomes one file, like `2026-10-22_14-30 Popescu Ion.txt`. In **Setări** you can switch to `.csv`, which opens as a table in Excel.

## Good to know

- **The app only sees its own files in Drive.** If you already had a folder with the same name, the app makes a new one next to it.
- **Don't clear Chrome's data for this site.** Sheets that haven't been uploaded are stored in Chrome on the phone. Use **Descarcă copia** in Setări if you're unsure.
- **Updating the app:** after changing files, open `sw.js` and change `masuratori-v1` to `masuratori-v2` (and so on), then upload again. Phones pick up the new version after opening the app twice while online.
