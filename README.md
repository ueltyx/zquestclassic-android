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

## Test status

The debug APK was tested on a Pixel 10 Pro with PureZC's **The Official 7th
Quest** ZIP (ZC 2.53.1). ZIP import, quest loading, the opening text, on-screen
A input, and directional keyboard input were verified. This was a smoke test,
not a full playthrough. Android showed a non-fatal 16 KB page-size compatibility
warning for some bundled native libraries; the app still launched and played.

SHA-256: `d2db37a85094f7383ff8992233e0894209868932df7bf423332bfe399f920931`

## Rebuilding from source

Built from upstream source commit
[`3e5476411344a770489cb5aa44eb80de2eac164d`](https://github.com/ZQuestClassic/ZQuestClassic/commit/3e5476411344a770489cb5aa44eb80de2eac164d),
with the Android changes in [`android-port.patch`](android-port.patch).

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
