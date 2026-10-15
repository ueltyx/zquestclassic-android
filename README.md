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

Because this is a debug-signed test build, Android may show a compatibility
notice on first launch; choose "Don't Show Again".

## Using it

Opening the app shows the **quest library**:

- **On this device** lists quests already imported into the app.
- **Choose folder** picks a folder once with the system folder picker (it opens
  in Downloads). Everything under **In \<folder name>** is then read from that
  folder, sub-folders included.
- **Import file** does a one-off import of a single `.qst` or `.zip`.

Tapping a quest imports it if needed and starts playing offline. Re-importing the
same archive reopens the copy already there instead of adding a duplicate.

In game, the top-right bar has **Home** (stop and return to the library),
**Menu** (ZQuest Classic's own pause menu, the one Escape opens), and **Pad**
(show or hide the on-screen controls, remembered between sessions). A hardware
keyboard works too.

## Test status

Verified on a Pixel 10 Pro (Android 16) against the six quests in
`Download/quests`: `q1.zip`, `q2.zip`, `q321_FunintheSun8bitExtraordinare.zip`,
`q569_PassageThroughTime.zip`, `q845_TheOfficial7thQuest.zip` and
`q853_MetdroidPlanetXX32.zip`. All six import, start and play with no crashes.
The touch controls, the pause menu, the pad toggle and the Home button were all
exercised. This is a smoke test, not a full playthrough of any quest.

The APK passes Android's 16 KB page size compatibility check.

Known rough edges: ZC draws its pause menu small in the top-left corner and
leaves a sliver of it painted briefly after closing; stopping the game ends that
process with a SIGSEGV inside Allegro's teardown, which is harmless here because
the library runs in its own process; and imported quests cannot yet be deleted
from the library.

SHA-256: `45d2f9ecd8950f34f81b85495afe8d449bb2fc4a0535e4ae84b44f30a48a1f5a`

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
