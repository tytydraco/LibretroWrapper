# LibRetroWrapper
A LibRetro-powered ROM packager for portable emulation

# Philosophy
The current state of emulation on Android is excellent relative to other methods of emulation. However, the experience is not **seamless** and it is not **universal**. Allow me to elaborate. By seamless, I mean to say that there are very few steps involved between opening the application and actually playing the game. With most emulators from a fresh install, one must open the application, download a core (i.e. RetroArch), locate their rom, and then begin playing, totally at least two steps of interference. Contrarily, LibRetroWrapper reduces the process down to one simple step: open the application. The core, rom, controls, core settings, and everything else is already configured. In terms of universality, one cannot easily duplicate their configuration across devices without repeating the steps for each device. Instead, LibRetroWrapper is a simple APK with all configuration already prepared, so installing an exact duplicate of the game is as easy as installing any other APK.

# Purpose
The goal of LibRetroWrapper is to increase the level of abstraction for emulation on Android.

Here's a diagram of how most Android emulators are configured:

```
└── Generic Emulator App
    ├── Roms
    │   ├── rom1.gba
    │   ├── rom2.gba
    │   └── rom3.gba
    ├── Saves
    │   ├── rom1.sav
    │   ├── rom2.sav
    │   └── rom3.sav
    └── States
        ├── rom1.state
        ├── rom2.state
        └── rom3.state
```

Here's how LibRetroWrapper is configured:

```
└── LibRetroDroid
    ├── rom.gba
    ├── rom.sav
    └── rom.state
```

# Features
- LibRetro core is fetched once on first launch
- ROM is packaged inside the APK, no external importing required
- Save state support (single slot)
- SRAM is saved when the application loses focus
- All-in-one package, can be easily distributed once packaged
- Android TV and external controller support

# Libraries
- [LibretroDroid](https://github.com/Swordfish90/LibretroDroid): Our LibRetro frontend that interacts with RetroArch cores
- [RadialGamePad](https://github.com/Swordfish90/RadialGamePad): Intuitive touchscreen controls
- [RetroArch](http://buildbot.libretro.com/nightly/): LibRetro emulator cores for Android

# Configuration
- Copy `rom.properties.sample` to `rom.properties`
- Edit `rom.properties` and change your configuration
- Place your rom in `system/`, and make sure the file name matches the configuration file's `romName`
- Place any other core assets in the system directory

# Building
It is usually best to build a release build to reduce the total file size and improve performance.
- `./gradlew assembleRelease`

This uses the official LibRetroWrapper keystore to sign the APK. This is available in the root directory of the project. Feel free to use this key for your personal projects.

The output APK is located here: `app/build/outputs/apk/release/app-release.apk`
