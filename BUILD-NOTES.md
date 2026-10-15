# Android-only workflow

## 1. Edit on the phone
Install Termux from its official F-Droid/GitHub distribution, then:
```sh
pkg update
pkg install git python nano
mkdir -p ~/projects
cd ~/projects
```
Unzip this starter and edit files with `nano` or a code editor.

## 2. Preview the UI
From the project folder:
```sh
cd prototype
python -m http.server 8080
```
Open `http://127.0.0.1:8080` in the phone browser.

## 3. Build a real PS4 app
A native PS4 app needs the OpenOrbis PS4 toolchain, PS4-compatible libraries, an EBOOT, and package metadata/packaging tools. Official OpenOrbis documentation recommends using a prebuilt release/installer and describes the toolchain and PKG workflow:
https://github.com/OpenOrbis/OpenOrbis-PS4-Toolchain

Because Android phones use ARM64 while common prebuilt Linux toolchain binaries target desktop Linux, do not assume the complete toolchain will run directly in Termux. Practical route: use the phone browser to access a cloud Linux development environment (for example, a Codespaces-like environment) and run the documented Linux build there. Availability/limits depend on the service/account.

## 4. Video playback is a separate milestone
The native SDL2 shell does not yet implement HLS/DASH decoding, audio, or network streaming. A compatible PS4 playback backend must be selected and tested on the actual console. Test with an authorized, public stream first.

## 5. Acceptance checklist
- [ ] Arabic UI fits a TV screen
- [ ] D-pad changes focus; X selects; O returns
- [ ] Channel list loads from JSON
- [ ] Invalid/offline URL shows an error instead of freezing
- [ ] Video and audio playback verified on the target PS4
- [ ] PKG built and installed successfully on the target console
