# UnknownBear Hub

This GitHub project is the **download shelf** for UnknownBear English translations.

You do **not** need to know Git to use it. There are two kinds of things here:

1. **Small text files** in the repository (`catalog.json`, `app_manifest.json`). These are the menus.
2. **Big files** on GitHub Releases (Translator, Downloader, and `.ubp` patches). These are what people actually download.

Players never browse folders. The apps read the menus, then download the matching file.

## How the three apps use this Hub

| App | Who uses it | What it does with GitHub |
|---|---|---|
| **Patch Creator** | You (the translator) | Publishes a new or updated `.ubp` to the `patches` Release and updates `catalog.json` |
| **Translator** | Players | Reads `catalog.json`, downloads the current `.ubp`, applies it to their Japanese game. If they already have an English install, it can **update the translation without wiping saves** |
| **Downloader** | Players | Reads `app_manifest.json` and downloads the current **Translator** (and can update itself) |

## GitHub Releases (the actual files)

| Tag | What it holds | When you make a new one |
|---|---|---|
| `translator-v1.0.0` | `UnknownBearTranslator.exe` | When you ship a new Translator |
| `downloader-v1.0.0` | `UnknownBearTranslatorDownloader.exe` + WebView2 DLLs | When you ship a new Downloader |
| `patches` | Current `.ubp` for every game, plus dated history copies | Stay on this one tag. Patch Creator uploads here |

Do not use GitHub’s “Latest” button as a download link. Each app looks up an exact tag from the JSON menus.

### Patch files on `patches`

Each game has **one live `.ubp`**. Same filename is overwritten. A new version string in Patch Creator updates `catalog.json` so Translator offers **UPDATE TRANSLATION (KEEP SAVES)**.

Do not keep extra history copies on the release — they waste storage and show up as Unlisted files.

Players who already translated the game open Translator, drop their English folder, and click **UPDATE TRANSLATION (KEEP SAVES)**.

### Downloader files

Players need all four files from `downloader-v1.0.0` in the **same folder**:

- `UnknownBearTranslatorDownloader.exe`
- `Microsoft.Web.WebView2.Core.dll`
- `Microsoft.Web.WebView2.WinForms.dll`
- `WebView2Loader.dll`

They also need the Microsoft Edge WebView2 Runtime. The Downloader then fetches Translator from `translator-v1.0.0`.

## Repository files (the menus)

- `catalog.json` — list of games, current patch version, download URL
- `app_manifest.json` — current Translator and Downloader versions and download URLs
- `README.md` — this file

These are the only files that belong in git. Never commit `.ubp` or `.exe` files here.

## Support

- Patreon: https://patreon.com/UnknownBear
- Tip jar: https://buymeacoffee.com/unknownbear
- F95zone: https://f95zone.to/members/unknownbear
