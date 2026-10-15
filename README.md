# ZQuest Classic Android Preview

Unofficial native Android player preview; not an official ZQuest Classic release.

Download `ZQuestClassic-Android-Preview.apk` below. It supports ARM64 phones and
x86-64 Android environments, Android 6.0/API 23 or newer. It is a debug-signed
build, so dismiss Android's first-launch test-app notice.

Open the app to see the quest library. Choose a folder (the picker opens in
Downloads) to browse `.qst` and `.zip` quests there, or import an individual file.
ZIP companion files are kept, and duplicate imports reuse the existing copy.

In game, **Home** returns to the library, **Menu** opens ZC's pause menu, and
**Pad** toggles the on-screen controls. Touches elsewhere in the game no longer
open the pause menu; use Menu or Escape. The Pad choice is remembered.

## Test status

Tested on a Pixel 10 Pro with six quests from `Download/quests`; all imported,
started and played. Menu, Home and Pad were exercised. A neutral gameplay-area
tap was verified not to open the menu, and the explicit Menu button still does.
Smoke test, not a full playthrough. The APK passes Android's 16 KB page-size
compatibility checks. A teardown crash and bundled placeholder quest entries
were also fixed.

SHA-256: `3ac6a70cb6a4f76bc0925f710908bd111728f4463e3039cde968c68a6280225f`

## Source

Patch applies to upstream base
[`3e5476411344a770489cb5aa44eb80de2eac164d`](https://github.com/ZQuestClassic/ZQuestClassic/commit/3e5476411344a770489cb5aa44eb80de2eac164d).
Requires NDK r27 or newer.

```sh
git clone https://github.com/ZQuestClassic/ZQuestClassic.git
cd ZQuestClassic
git checkout 3e5476411344a770489cb5aa44eb80de2eac164d
curl -L -o /tmp/android-port.patch https://github.com/ueltyx/zquestclassic-android/releases/latest/download/android-port.patch
git apply /tmp/android-port.patch
./android/build.sh
```
