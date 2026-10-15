# ZQuest Classic Android Preview

Unofficial native Android player preview for testing ZQuest Classic quests.
This is not an official release from the ZQuest Classic maintainers.

## Download and install

Download `ZQuestClassic-Android-Preview.apk` from the latest GitHub Release. The
APK supports ARM64 Android phones (`arm64-v8a`) and x86-64 Android environments
such as Waydroid (`x86_64`). Android 6.0 (API 23) or newer is required.

Allow installation from the browser or file manager when Android prompts. On
Waydroid, install with:

```sh
waydroid app install ZQuestClassic-Android-Preview.apk
```

Open the app, then choose a `.qst` file or a `.zip` containing a quest. ZIP
imports select the first `.qst` and extract the archive's companion files into
a private per-quest folder. The quest runs offline. On-screen controls and
hardware keyboard input are enabled.

Because this is a debug-signed test build, Android may show a compatibility
notice on first launch; choose "Don't Show Again".

## Test status

Verified on a Pixel 10 Pro (Android 16) with PureZC's **The Official 7th
Quest** ZIP (ZC 2.53.1): ZIP import, quest loading, the intro and story
screens, the file select, and reaching the overworld with movement via both
the on-screen D-pad and the hardware keyboard. The app passes Android's 16 KB
page size compatibility check. This is a smoke test, not a full playthrough.

SHA-256: `d2e7f8d3800b235dfc300f5dce34c57a97cca2f2c6772b13e5770f5aeb845e9e`

## Rebuilding from source

Built from upstream source commit
[`3e5476411344a770489cb5aa44eb80de2eac164d`](https://github.com/ZQuestClassic/ZQuestClassic/commit/3e5476411344a770489cb5aa44eb80de2eac164d),
with the Android changes in [`android-port.patch`](android-port.patch).
Requires NDK r27 or newer.

```sh
git clone https://github.com/ZQuestClassic/ZQuestClassic.git
cd ZQuestClassic
git checkout 3e5476411344a770489cb5aa44eb80de2eac164d
curl -L -o /tmp/android-port.patch https://github.com/ueltyx/zquestclassic-android/releases/latest/download/android-port.patch
git apply /tmp/android-port.patch
./android/build.sh
```

The patch and application are distributed under the licenses of the upstream
project and its included components; see the upstream `LICENSE` file.
