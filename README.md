# Floodlight Remote

A web app for controlling 12V RGB LED floodlights over Bluetooth, for when the original phone app is gone. It's a single HTML page with nothing to install. It talks to the light's Bluetooth controller straight from the browser (Web Bluetooth).

## What it does

- Turn the light on and off
- Pick any color from a color wheel, or tap a preset
- Change brightness
- Run the controller's built-in effects (jump, fade, strobe, breathe) and change their speed
- Show an activity log, let you pick the protocol yourself, and send raw bytes when a light isn't recognized

## Supported controllers

Most cheap Bluetooth RGB floodlights use one of these controller chips. The app works out which one it's talking to when it connects.

| Bluetooth name looks like | Original app | Protocol |
| --- | --- | --- |
| `ELK-BLEDOM`, `MELK-…`, `ELK-BLEDOB` | Lotus Lantern, duoCo Strip, Lotus Lamp X | ELK-BLEDOM (service `fff0`, char `fff3`) |
| `Triones-…`, `QHM-…`, `Dream~…` | HappyLighting, Triones | Triones (service `ffd5`, char `ffd9`) |
| `LEDBLE-…` | Magic Blue / LEDBLE | Triones commands on service `ffe5`, char `ffe9` |
| `BJ_LED`, `MohuanLED` | MohuanLED | BJ_LED (service `ffe0`, char `ee01`) |

Lights controlled over Wi-Fi (Magic Home, Tuya/Smart Life) or by infrared remote only won't work with this app.

## Where it runs

Web Bluetooth needs a secure (`https://`) page and a supporting browser:

- **Android, Windows, macOS, ChromeOS, Linux:** Chrome or Edge
- **iPhone / iPad:** Safari doesn't support Web Bluetooth. Use the free **Bluefy** browser from the App Store.

## Hosting it with GitHub Pages

1. Merge this branch into your default branch (or point Pages at this branch).
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick the branch and the `/ (root)` folder, then save.
4. After a minute the app is live at `https://<your-username>.github.io/<repo-name>/`. Open it on your phone and use the browser's **Add to Home screen** to get an app icon.

To try it on a computer without hosting, open `index.html` in Chrome. Chrome allows Bluetooth from local files.

## Troubleshooting

- Close any other app connected to the light, and turn the light's power off and on. These controllers accept only one connection at a time.
- On Android, Bluetooth **and** Location must be on.
- If the light isn't in the device list, open **Advanced & troubleshooting** and tick **Show every nearby Bluetooth device**.
- If it connects but doesn't react, try each option under **Controller protocol** in **Advanced**. The activity log shows each command as it's sent.
