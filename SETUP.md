# Kt: setup

Kt (K Timeline) is a small web app you install from Safari, built the same way as Kj and Kn. It works offline, and syncs through one file in a **private GitHub repository** that only you can read. If Kj and Kn are already set up, this takes about 10 minutes, once.

## 1. GitHub (once, on the iMac)

1. **Data repository.** Click **+ → New repository**. Name it `kt-data`, choose **Private**, tick **Add a README**, then **Create repository**. Your timeline will live here as `timeline.json`.
2. **App repository.** Make another one called `kt`, this time **Public** (free hosting needs it public; it holds only the app's code, never your timeline). Tick **Add a README** and create it.
3. In `kt`, click **Add file → Upload files**, drag in these files from this folder: `index.html`, `sw.js`, `manifest.webmanifest`, `icon.svg`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`. Then **Commit changes**. (Leave out `SETUP.md` and the `previews` and `icon-options` folders.)
4. In `kt`, go to **Settings → Pages**. Under *Build and deployment* choose **Deploy from a branch**, branch **main**, folder **/ (root)**, and **Save**. After a minute or two your app is at
   `https://YOUR-USERNAME.github.io/kt/`
5. **Access token.** Pick one:
   - **A separate token (recommended).** Profile picture → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**. Name it `kt`, choose the longest expiration, **Only select repositories → kt-data**, **Repository permissions → Contents: Read and write**, then **Generate token** and save it in the Passwords app.
   - **Reuse an existing token.** Open the `kj` or `kn` token on the same page, click **Edit**, add `kt-data` under *Only select repositories*, and **Update**. If you ever revoke it, every app using it stops syncing.

## 2. iMac and MacBook

1. Open `https://YOUR-USERNAME.github.io/kt/` in **Safari**.
2. Choose **File → Add to Dock**, then **Add**.
3. Open Kt from the Dock, click **sync** at the bottom of the page, enter `YOUR-USERNAME/kt-data` and the token, and click **connect**. The status at the top right should say *synced*.

Repeat on the other Mac.

## 3. iPhone

1. Open the same address in **Safari**.
2. Tap **Share → Add to Home Screen**. Make sure **Open as Web App** is on, then tap **Add**.
3. Open Kt from the Home Screen, scroll to the bottom, tap **sync**, enter the repository and token, and tap **connect**.

## How it behaves

- Opens on an empty box, ready to type, dated today. **Cmd + Enter** or **new entry** starts another.
- Above the box: tap the **date** to log something on another day (a film you watched yesterday), and choose **me** or **world**. A date other than today shows brighter, so you notice it.
- The timeline is one line, newest day first. The date sits in the margin beside the first event of each day; events within a day are in the order you wrote them.
- **Open dot = me, filled dot = world.** Tap a dot to switch it. Tap the empty margin beside an event (or its date) to move it to another day.
- **The circle** next to the dark/light square chooses what you see: half-filled shows everything, hollow shows only me, solid shows only the world. Each device remembers its own setting.
- **Search** (or **Cmd + F**) filters as you type and highlights matches; it also matches dates ("Nov 26") and "me" or "world". **Esc** clears it.
- Emptying an event deletes it.
- **copy all as text** copies every event as `Tue 24 Nov 26 · me` followed by its text. Pasting that into **import** (in the sync panel) brings them back, without duplicates.
- Saved on the device as you type, synced a few seconds after you stop, whenever you return to it, and every minute while open. If two devices edit the same event, the newest edit wins. Every sync is a commit in `kt-data`, so you have a full history.

## Good to know

- **Privacy.** The timeline sits in a private repository, and Kt refuses to connect to a public one. It is not encrypted, so GitHub itself could in principle read it.
- **Shared address.** Kj, Kn and Kt live at the same `github.io` address. Each keeps its own storage and offline copy, so they never interfere.
- **Lost device.** Delete the token on GitHub, make a new one, and reconnect your other devices.
- **Updating the app later.** Upload the new files to the `kt` repository. Each device picks up the change the next time it's opened twice.
