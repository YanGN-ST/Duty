**English | [简体中文](README.zh-CN.md)**

<p align="center">
  <img src="./assets/readme/hero-en-v2.svg" width="100%" alt="Duty: Keep your defaults yours.">
</p>

Duty keeps the default apps you choose from being taken over. It watches macOS file associations, restores your chosen app when another app overrides it, and can record each change when history is enabled.

## Features

- **Lock only what you choose**: set a default app for any extension (`.md` → Obsidian, `.pdf` → Preview), and protect only the types you select.
- **Restore quickly**: a DispatchSource watches the Launch Services secure plist and checks as soon as it changes; a timer covers missed events.
- **Clear per-file overrides**: remove a single file's “Always Open With” setting so it follows the system default again.
- **Add types without guessing**: search 93 built-in file types with English and Chinese names, or type an extension manually.
- **Review changes (optional)**: when history is enabled, each override and restore is recorded with the time, the expected app and the detected app.
- **Stay out of the way**: lives in the menu bar without a Dock icon, can launch at login, and keeps protecting after the window closes.
- **Follow your language**: English or Simplified Chinese, following the system by default.

## How it works

Duty detects and restores; it does not block changes at the system level. It listens for Launch Services changes, compares the current handler with your lock, and writes your choice back when needed.

- **Read**: parses `~/Library/Preferences/com.apple.LaunchServices/com.apple.launchservices.secure.plist` directly, bypassing delayed Launch Services caches; `LSCopy` APIs are fallbacks.
- **Write**: prefers `NSWorkspace.setDefaultApplication(at:toOpen:)`, then falls back to `LSSetDefaultRole` and handler APIs.
- **Optional duti**: resolves UTIs for uncommon extensions that `UTType` cannot identify; it does not read or write associations.

## Requirements

- macOS 14 (Sonoma) or later on Apple Silicon.
- No third-party runtime dependencies. All association work uses system Launch Services APIs.

## Install

Download `Duty.dmg` from [Releases](https://github.com/YanGN-ST/Duty/releases), open it and drag Duty into `/Applications`. Or install with Homebrew:

```sh
brew install --cask yangn-st/ygn/duty
```

Duty is not notarized. If macOS blocks the first launch, verify the download source and allow it in **System Settings → Privacy & Security**.

### Optional: duti

[duti](https://github.com/moretension/duti) is only needed when macOS cannot resolve an uncommon extension. Most users do not need it:

```sh
brew install duti
```

If you add an unregistered extension without duti, Duty shows an install prompt; you can also install it later in the **Enhancements** section of Settings.

## Get started

1. Open Duty from the shield icon in the menu bar.
2. Add a file type and choose its default application.
3. Turn on the lock for that extension.
4. Close the window when you are done; protection continues in the menu bar.

| Action | Behavior |
|---|---|
| Left-click the menu bar icon | Open or focus the main window |
| Right-click the menu bar icon | Open or quit |
| Close the main window | Keep running in the background |
| Quit from the menu | Stop protection completely |

## Build from source

<details>
<summary>Build and run</summary>

```sh
git clone https://github.com/YanGN-ST/Duty.git
cd Duty
./build_app.sh
open Duty.app
```

You can also open `Package.swift` in Xcode and run it. Source code lives in `Sources/Duty/`; built-in type data and localizations are in `Sources/Duty/Resources/`.

</details>

## License

[MIT](LICENSE) · [Follow YanGN on Xiaohongshu](https://www.xiaohongshu.com/user/profile/66a7e7ae000000001d023641)
