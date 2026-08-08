# Moonlight Android Fork for Mi TV Stick 4K Gen 2/Gen 1

![Example stream output](docs/images/example-stream.jpg)

This repository is a fork of **Moonlight Android** with device-focused fixes for **Mi TV Stick 4K Gen 2 and Gen 1**, mainly for:

- HEVC streaming stability/compatibility
- GPU composition behavior on Android TV

## What is changed in this fork

The fork includes patches around:

- HEVC low-latency decoder option handling on affected Xiaomi/Amlogic devices 
- HEVC decoder/RFI behavior tuning for Android TV
- GPU composition forcing logic to reduce stutter scenarios on TV sticks
- Additional renderer/frame-pacing enhancements 

## Build instructions

1. Install prerequisites:
   - Android Studio
   - Android NDK
2. Clone this repository.
3. Initialize submodules:
   - `git submodule update --init --recursive`
4. Create `local.properties` in repo root and set your NDK path:
   - `ndk.dir=...`
5. Open the project in Android Studio (or use Gradle).
6. Build APK:
   - Android Studio: **Build > Build APK(s)**
   - or CLI: `./gradlew :app:assembleDebug` (Windows: `gradlew.bat :app:assembleDebug`)

## Default settings in this fork

Current defaults are tuned for the target device profile:

- Resolution: **Full HD (1920x1080)**
- Codec preference: **HEVC**
- Frame pacing: **Balanced**
- Android TV force GPU composition: **Enabled**

## Tested configuration

Validated on:

- Device: **Mi TV Stick 4K Gen 2**
- Streaming profile: **2K 60 FPS**
- Frame pacing: **Balanced**
- Tested using **vibepollo**

Low-latency mode can cause freezes on some affected configurations.

## Known issues

- Streaming can still hang at random times (root cause is not fully understood yet).
- Smoothness may degrade when the large performance stats overlay is enabled.

## TV settings recommendations

To reduce latency, it is recommended to:

- Enable **Game Mode** on your TV.
- Disable **Auto Motion Plus** (or equivalent frame interpolation/motion smoothing features).

## Contributing

Issues and pull requests are welcome.

If you reproduce freezes/hangs, please include:

- device model (`Build.MODEL` / `Build.DEVICE`)
- decoder name 
- codec/resolution/FPS/frame pacing settings
- a short reproduction sequence

## Credits

- [Moonlight Android](https://github.com/moonlight-stream/moonlight-android)
- [Nun-z/moonlight-android](https://github.com/Nun-z/moonlight-android)
- [Viktsolovevwork278/moonlight-android-hevc-fix](https://github.com/Viktsolovevwork278/moonlight-android-hevc-fix)

## Development note

GitHub Copilot was used during development.  
All resulting changes were manually reviewed and tested by a human software engineer.
