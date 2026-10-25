# YouTube Ad-free Android TV

An experimental, unofficial YouTube TV client for Android TV / Google TV, with a Pride play-button icon and an injected ad-filter userscript.

**Experimental release:** the injector and playback have been tested, but reliable suppression of every ad has not been established. “Ad-free” is the project name and goal, not a guarantee. This does not unlock YouTube Premium or other paid entitlements.

## Download

- [Download the APK — v0.1.0](https://github.com/Benjamingitgit/YouTube-Ad-free-Android-TV/releases/download/v0.1.0/youtube-ad-free-android-tv.apk)
- [Release notes and SHA256 checksum](https://github.com/Benjamingitgit/YouTube-Ad-free-Android-TV/releases/tag/v0.1.0)

### Compatibility

- Requires Android 12 / API 31 or newer and support for **32-bit ARM (`armeabi-v7a`)** applications. Not a universal build.
- The Android 12 compatibility variant was tested on a Philips TPM191E TV, including playback. This release includes the corrected Android TV launcher banner.
- Other TVs are unverified. ARM64-only devices and x86 devices are not supported by this APK.
- Not for Samsung Tizen, LG webOS, Apple TV, or the mobile YouTube app.
- Google sign-in, HDR/DRM and long playback sessions have not been exhaustively validated.

## 1. Remote-only installation: Downloader

1. Install **Downloader by AFTVnews** from your TV's app store, where available.
2. Open Downloader and enter `https://github.com/Benjamingitgit/YouTube-Ad-free-Android-TV`.
3. Follow the Download APK link above.
4. If prompted, allow **Downloader** to install unknown apps, then select Install. Setting names vary by TV; some firmware hides this permission behind developer settings.

No Downloader numeric short code has been registered yet. Use the repository URL for now. Official Downloader instructions: https://www.aftvnews.com/downloader/documentation/

## 2. Developer mode already enabled: install from your phone

Use [atvTools](https://atvtools.app/) on iPhone or Android:

1. Download the APK onto your phone.
2. Put phone and TV on the same local network.
3. Enable the TV's applicable USB/network/wireless debugging option and connect in atvTools.
4. Approve your phone on the TV, then use atvTools' APK installation function.

Pairing and network-debugging behavior varies by firmware. Disable debugging when you no longer need it.

## 3. ADB installation

Download the APK, authorize your computer on the TV, then replace `TV_IP` with your TV's address:

```sh
adb connect TV_IP:5555
adb -s TV_IP:5555 install -r youtube-ad-free-android-tv.apk
```

This example uses legacy network ADB. TVs requiring wireless pairing must first use their firmware's pairing flow.

The package is `io.github.jonathaniel.youtubetv.test`. It installs alongside stock YouTube; do not uninstall or clear the stock app. Updates signed with the same project key can be installed in place with `-r`.

## What changes

- Optional ad-filter userscript from the upstream patch project.
- Pride-coloured play button, with the original wordmark retained.
- Correctly sized launcher banner for the tested Android TV launcher.
- An optional “please subscribe” support prompt, limited to two displays per retained app-data installation. **Subscribe** opens the channel; it never automatically subscribes. **Later** leaves a second opportunity; **Skip (permanently)** stops future prompts. Clearing app data or uninstalling can reset the count.
- A narrowly guarded compatibility adjustment lets a denied Play Services call follow an existing error path rather than terminate the clone. The service denial remains; this does not bypass attestation or grant Google privileges.

## Privacy, security and source status

This is a modified Google client, not a new privacy-focused replacement. Google's original client can still communicate with Google and perform its normal telemetry. No independent security audit has been completed.

This repository currently hosts download/installation documentation and release artifacts. A portable, reviewed publication of our local build/patch sources is not included yet. The original Google APK input, private signing keys, credentials, device logs and account data are not repository contents.

Verify downloads using the release's `SHA256SUMS.txt`. Keep stock YouTube as a fallback. Please report device model, Android version and reproduction steps without posting account tokens or private logs.

## Credits and rights

- Google YouTube TV 7.25.302 is the underlying proprietary application.
- [ysamjo/morphe-patches](https://github.com/ysamjo/morphe-patches): injected TV ad-filter patch; its own verification notes document limitations.
- [Morphe Desktop](https://github.com/MorpheApp/morphe-desktop) and [Morphe patches](https://github.com/MorpheApp/morphe-patches): patching and clone-app tooling.

Not affiliated with or endorsed by Google, YouTube or Morphe. Original components, trademarks and upstream code retain their owners' rights and applicable licenses. See [NOTICE.md](NOTICE.md). Redistribution of modified Google software can be subject to copyright claims or takedown.
