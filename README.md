<div align="center">

<p align="center">
    <img src="./public/img/Phisap.png" alt="phisap">
</p>

# phisap
<ins>PHI</ins>gros(-like) <ins>S</ins>emi-<ins>A</ins>utomatic <ins>P</ins>layer

✨ A semi-automatic player for (Phigros-like) rhythm games ✨

**Supports Android devices only**

![Maximum Supported Version](https://img.shields.io/badge/Maximum%20Supported%20Version-Phigros%203.1.3-blue.svg)

_The phisap logo is created by [@ShintoKosei](https://github.com/ShintoKosei) and licensed for use in the phisap project. All rights are reserved by ShintoKosei._

</div>

---

You are currently on the `dev` branch, which includes the latest updates but does not guarantee stability. It is not recommended for regular users.

If you'd like to switch back to the stable branch of phisap, [click here](https://github.com/kvarenzn/phisap/tree/stable).

This branch has been tested under the following conditions:  
PC OS: Arch Linux x64  
Game device: OnePlus 7 Pro, Hydrogen OS 10.0.10.GM21

## Notifications
+ (2023/09/29) After upgrading the author’s phone from Android 10 (Hydrogen OS 10) to Android 13 (crDroid 9.9), the previously working OTG/HID backend completely stopped functioning. The issue involves the failure to register a multi-touch device through the AOAv2 protocol. The scrcpy backend is working without observed problems. The author is investigating and attempting to fix this issue.

## Table of Contents
- [Disclaimer](#disclaimer)
- [Inspiration](#inspiration)
- [Interface](#interface)
- [Showcase](#showcase)
- [How to Use](#how-to-use)
  - [Preparation](#preparation)
  - [Running](#running)
- [How It Works](#how-it-works)
- [Notes](#notes)
- [Unsupported Beatmaps](#unsupported-beatmaps)
- [Challenge Mode](#challenge-mode)
- [Having Issues?](#having-issues)
- [Acknowledgments](#acknowledgments)
- [License](#license)
- [Changelog](#changelog)

## Disclaimer
- This project is a personal interest project and is unrelated to Xiamen Pigeon Network Co., Ltd.
- **This project does not contain any copyrighted materials and is not a commercial project.**
- The server backend for the project uses [Genymobile/scrcpy](https://github.com/Genymobile/scrcpy). Special thanks to the authors and maintainers of scrcpy.
- As of now, the author has never promoted this project on any platform other than GitHub.

## Inspiration
> Tip: sudo board plays the game itself.

## Interface

![Phisap Interface](./public/img/screenshots/phisap_interface.png)

- Note: This screenshot was taken on Arch Linux, using the Kvantum theme for Qt and the GTK Materia Dark theme.
- Note 2: Screenshots may not always be up to date; please refer to the actual running results.

## Showcase

<details>
<summary>Two phone screenshots</summary>

![AT Complete](./public/img/screenshots/phone-shot1.jpg)

![IN Complete](./public/img/screenshots/phone-shot2.jpg)

</details>

## How to Use

### Preparation

0. **Install Python 3.11**
   - Use the stable version. **Do not use early developer preview versions.**
1. Install dependencies with `pip install -r requirements.txt`.
2. Install `Android Debug Bridge` (ADB). **Version 1.0.41 or higher is required.** Ensure that the corresponding environment variable is properly configured.
3. Prepare the Phigros game package or general data package. Supported versions are 2.0.0 to 3.1.3.
   - For the TapTap version of Phigros, only the game package is needed:
     - On \*nix systems (Linux or Mac OS), use the following `bash shell` command to extract the game package from the Android device:
       ```bash
       adb pull $(adb shell pm path com.PigeonGames.Phigros | cut -f2 -d:) ./Phigros.apk
       ```
     - On Windows, use the following `powershell` command:
       ```powershell
       adb pull (adb shell pm path com.PigeonGames.Phigros).Split(":")[1] ./Phigros.apk
       ```
   - For the Google Play version of Phigros, **do not extract the game package. Extract the data package** (with a `.obb` extension) instead, as beatmap data is not included in the game package:
     - The data package is usually located at `/sdcard/Android/obb/com.PigeonGames.Phigros/` on the game device.
     - The file name is similar to `main.82.com.PigeonGames.Phigros.obb` and is approximately 1.3GB in size.
     - Use `adb pull` or a file manager to copy it.
   - Alternatively, you can download a Phigros package or data package online. Ensure the version matches the requirements.
4. Prepare the server. Download `scrcpy-server-v2.0` from the [scrcpy releases page](https://github.com/Genymobile/scrcpy/releases). Do not download a different version. Once downloaded, place the file in the root directory of phisap (where `main.py` and other files are located) without renaming it. Otherwise, phisap will not recognize the file.
   - On \*nix systems, if `wget` is installed, the following command is equivalent to the above steps:
     ```bash
     cd phisap  # Navigate to the root directory of phisap
     wget https://github.com/Genymobile/scrcpy/releases/download/v2.0/scrcpy-server-v2.0
     ```

### Running

cd phisap # Set the Current Working Directory (CWD) to the root directory of phisap to locate the server file
python main.py
How It Works
Reads and caches all beatmap files from the game package.
Parses the beatmap files to analyze each note's position, method, and timing.
Converts these actions into touch event sequences:
Down, Move, and Up.
Sends these touch events to the device one by one during gameplay.
Notes
Although phisap is inspired by "sudo board plays the game itself," this program does not require root access to function.
Some devices may trigger three-finger screenshots or notification panels, causing misses. This depends on the manufacturer and device model.
Phisap currently fully supports up to version 3.1.3. All songs and difficulties can achieve AP (All Perfect), except for some special beatmaps (which do not affect RKS). These beatmaps are listed under Unsupported Beatmaps. If you encounter an issue:
Ensure timer synchronization is precise. If you achieve FULL COMBO but not AP, this indicates timer synchronization issues.
If timer synchronization is not the problem, try switching the planning algorithm. Some beatmaps require conservative algorithms, while others require aggressive ones. Most work with either.
If it still doesn’t work, consider opening an issue to report the problem.
Unsupported Beatmaps
Random in Single Song Selection
Currently, there is no reliable way to automate the identification of these beatmaps. If you have any ideas, please open an issue. Image recognition may be a feasible approach.

For now, phisap can extract all random beatmaps (IDs: Random.SobremSilentroom.<n>, where <n> ranges from 0 to 6). In theory, if you’re fast enough, you can handle these manually.

April Fools' Beatmaps
These are extremely complex and not within the scope of phisap’s goals for full AP. The author does not plan to improve planning algorithms specifically for these.

Challenge Mode
Phisap does not currently have special support for Challenge Mode. It may be added in the future.

vbnet
Copy code

Let me know if you need further tweaks! 😊
