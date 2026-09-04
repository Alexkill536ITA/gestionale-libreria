[Italiano](../it/Installazione.md) · **English**

# Installation

The application runs on **Windows 10 and 11**, and since September 2026 every
version also carries a file for **macOS** — which nobody has opened on a Mac yet:
what to expect is in [On a Mac](#on-a-mac).

On Windows nothing else is needed: the system component that draws the window
(WebView2) is bundled inside the installer, so it is not downloaded during setup.

## Installing on Windows

1. Download `Gestionale Libreria_0.3.0_x64-setup.exe`.
2. Double-click it. The installer speaks Italian and asks very little.
3. Done: you get a shortcut **on the desktop** and **in the Start menu**.

The install is **for the current user only**: it does not ask for administrator
rights and does not touch the rest of the computer.

## “Windows protected your PC”

The first time you run the installer, Windows shows that blue SmartScreen
screen. It happens because **the program is not code-signed**, and it is not a
sign that the file has been tampered with: a certificate costs a yearly fee and,
on its own, would not even silence the warning.

To go on: **More info** → **Run anyway**.

## On a Mac

The file is `Gestionale Libreria_0.3.0_universal.dmg`, a single one for Intel Macs
and Apple Silicon ones: open it, drag the application into **Applications**, and
start it from there.

> [!WARNING]
> **Nobody has opened it on a Mac yet.** The file is built by the same automated
> procedure that produces the Windows one, but nothing on macOS has been tried by
> hand: the webcam, the covers and the rest may not work. If you try it and
> something is off, that is a
> [bug to report](https://github.com/alexkill536ita/gestionale-libreria/issues/new?template=bug.yml)
> — not a mistake of yours.

The first time you start it, macOS says the application **cannot be verified**,
for the same reason Windows shows SmartScreen: there is no certificate paid for to
Apple. Go to **System Settings → Privacy & Security**, where an **Open Anyway**
button appears.

Your data sits here, and everything the rest of this page says still holds:

```
~/Library/Application Support/it.alexkill536ita.gestionale-libreria/
```

## Where your data ends up

On Windows everything of yours sits in one folder:

```
%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\
```

Paste that path into the File Explorer address bar and you are there. Inside:

| | |
|---|---|
| `libreria.db` | the catalogue — this is the file that matters |
| `covers\` | the covers, one JPEG per book |
| `backups\` | the automatic copies, unless you picked another folder |
| `impostazioni.json` | theme, language, currency, API key, backup folder |

The **program** itself lives elsewhere, in `%LOCALAPPDATA%\Gestionale Libreria\` —
not in `Program Files`, which is where people usually look for it.

## Updating

**The application tells you when a new version is out**, but it does not download
it and does not install it: it opens the page the file comes from, and the rest is
up to you. The whole round is in [Updates](Updates.md).

To move to a newer version you **install over the old one**, just like the first
time: **your data stays where it is** and you find all of it again. There is no
need to uninstall first.

## Uninstalling

From **Windows Settings → Apps**, or with `uninstall.exe` in the program folder.

**Uninstalling does not delete your catalogue.** The program, the two shortcuts
and the entry in the apps list go away; the data folder stays put, and
reinstalling brings everything back. If you really want to start from scratch,
that folder has to be emptied by hand — but
[take a backup](Backup-and-restore.md) first and put it somewhere else.
