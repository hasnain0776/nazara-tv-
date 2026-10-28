# Nazara TV

**Free live TV from 31 countries. No ads, no sign-up.**

Nazara TV is a free live-TV website and Android app with 2,500+ channels from Asia, Africa and Europe, with a special focus on Pakistani and Indian channels (news, drama, kids, sports, music and more).

- Website: https://nazara-tv.netlify.app
- Android package: `com.nazara.tv`
- Created and designed by **Hasnain Hassni**

## Features

- **Fast start.** Playback begins after about 3 seconds of video, then keeps filling the buffer in the background so it does not stop on slow internet.
- **31 countries** across Asia, Africa and Europe, with flags and channel logos.
- **Channels listed A to Z**, with category tabs (News, Drama & Entertainment, Kids, Sports, Music and more).
- **Favorites.** Tap the heart on any channel to keep it in your Favorites row. Saved on the device.
- **Search** and a **Random** button.
- **Custom player** with zoom (Fit, Fill, 1.5x, 2x, 3x, pinch and pan), full screen and landscape.
- **Slow-network friendly:** tries backup links automatically if a stream fails.
- **Works on phone and PC**, with a two-column layout and keyboard shortcuts on desktop (Space, F, M, Z, arrows, /).
- **Lightweight** opening screen and batched channel lists, so it runs on low-end phones.
- **Region-locked channels** are marked and listed last.

## How it works

The website is one self-contained `index.html` (HTML, CSS, JavaScript and the channel data inside). Video plays with [hls.js](https://github.com/video-dev/hls.js) and falls back to the browser's native player.

The Android app is a [Capacitor](https://capacitorjs.com) shell that loads the website. When the site is updated on Netlify, the app updates automatically. A new APK is only needed when native Android code changes.

## Update the website

1. Open the Netlify project, then **Deploys**.
2. Drag in the folder that holds the new `index.html`.
3. Open the app. It shows the new version.

## Build the Android APK

The APK is built online with GitHub Actions. No computer setup is needed.

1. Put the project files in this repository (`package.json`, `capacitor.config.json`, `www/`, `assets/`, `tools/`).
2. Put the workflow at `.github/workflows/build.yml`.
3. Open the **Actions** tab, choose **Build Nazara TV APK**, then **Run workflow**.
4. When it finishes, download `Nazara-TV.apk` from the run or from **Releases**.

The workflow uses Ubuntu, Node 20 and Java 17. It creates the Android project, generates icons, applies `tools/patch_android.py` (keep-screen-on, full screen, and media request handling), and builds the APK.

## Project layout

```
.github/workflows/build.yml   APK build workflow
capacitor.config.json         App id, name and site URL
package.json
www/                          Bundled copy of the site and an offline error page
assets/                       App icon and splash images
tools/patch_android.py        Native Android tweaks
index.html                    The website (single file)
```

## Important notes

- Nazara TV does not host any video. It plays public streams provided by third parties, found in community lists such as [iptv-org](https://github.com/iptv-org/iptv) and [famelack-data](https://github.com/famelack/famelack-data).
- Free streams change often. Some channels may be offline or limited to certain countries.
- Channel owners who want a stream removed can open an issue in this repository.
- Streams that need a login, password or device token are not included.

## Credits

- Channel data: iptv-org and the community lists above
- Player: hls.js
- App shell: Capacitor

## Support the developer

The app is free with no ads. If you like it, you can support the developer from the **Support** button inside the app.

## License

No license has been chosen yet. Add a `LICENSE` file to set one.
