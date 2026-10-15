# TIDAL plugin for OxiTide

Adds the **TIDAL** source to [OxiTide](https://github.com/yelanxin/OxiTide)
for Windows: browse, search and stream TIDAL, bit-perfect, next to your local
music.

**Who needs it:** the Microsoft Store version of OxiTide, which is a local
music player out of the box. The Windows installer and portable zip from
[OxiTide's Releases](https://github.com/yelanxin/OxiTide/releases) already
include TIDAL, and so do the Linux and macOS builds — nothing to install there.

**Requirements**

- OxiTide for Windows 0.2.2 or later
- A TIDAL subscription to sign in and stream

## Download

[**tidal.oxplugin**](https://github.com/yelanxin/oxitide-tidal-plugin/releases/latest/download/tidal.oxplugin)
— the plugin is this one small file, not meant to be opened: just put it in
place. Every version is on the
[Releases](https://github.com/yelanxin/oxitide-tidal-plugin/releases) page.

## Install

1. Close OxiTide.
2. Put `tidal.oxplugin` in this folder, creating the `plugins` folder if it is not
   there:

   ```
   %LOCALAPPDATA%\OxiTide\plugins
   ```

   Paste the line above into the File Explorer address bar to go there.
3. Start OxiTide. Click the account button at the bottom of the sidebar:
   **TIDAL** is now listed under Media Source. Pick it and sign in.

Or do all of it from PowerShell:

```powershell
$dir = "$env:LOCALAPPDATA\OxiTide\plugins"
New-Item -ItemType Directory -Force $dir | Out-Null
Invoke-WebRequest https://github.com/yelanxin/oxitide-tidal-plugin/releases/latest/download/tidal.oxplugin -OutFile "$dir\tidal.oxplugin"
```

Then start OxiTide.

## Update

When a new version is released here, download it again over the old
`tidal.oxplugin` and restart OxiTide. Your TIDAL sign-in is kept.

## Uninstall

Delete `%LOCALAPPDATA%\OxiTide\plugins\tidal.oxplugin` and restart OxiTide. The
TIDAL source disappears; your local music is untouched.

## Troubleshooting

**TIDAL does not appear after a restart.** Check that the file is named
exactly `tidal.oxplugin` — not `tidal.oxplugin.txt` (turn on *View → File name
extensions* in File Explorer to see) — and that it sits directly inside
`plugins`. OxiTide's log says whether it found the plugin; for the Store
version the log is

```
%LOCALAPPDATA%\Packages\Oxidacdeveloper.OxiTide_ej1vgmwh34gze\LocalCache\Local\OxiTide\oxitide.log
```

Look for a line `TIDAL plugin: …` (found) or `no TIDAL plugin` (not found).
A file that is there but damaged is reported as `TIDAL plugin skipped: …`;
download it again.

Anything else: open an issue in
[OxiTide's Issues](https://github.com/yelanxin/OxiTide/issues).

## About

The plugin holds the client settings OxiTide signs in to TIDAL with. OxiTide
signs in through TIDAL's own login page and
talks to TIDAL directly; nothing goes through any other server. See
[OxiTide's privacy policy](https://oxitide.com/privacy.html).

OxiTide and this plugin are independent projects, not affiliated with or
endorsed by TIDAL. You need your own TIDAL subscription, and TIDAL's terms of
service apply to your use of it.
