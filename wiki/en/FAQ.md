[Italiano](../it/Domande-frequenti.md) · **English**

# Frequently asked questions

## Windows says the program is not safe

SmartScreen warns because **the program is not code-signed**. It is not a sign
that the file has been tampered with. **More info** → **Run anyway**. The reasons
are in [Installation](Installation.md).

## Does it run on a Mac?

Every version carries a `.dmg`, a single one for Intel Macs and Apple Silicon
ones — but **nobody has opened it on a Mac yet**, so it is not a promise: it is an
attempt. The program was built for Windows, and Windows is where it was tried in a
real window, feature by feature.

If you do try it, the most useful thing is to say how it went — above all the
webcam scanner and the covers, the two pieces that lean hardest on the system.
Which file to download, and how to get past the macOS warning, are in
[Installation](Installation.md).

## I uninstalled it — have I lost my catalogue?

No. **Uninstalling does not delete your data.** Reinstall and you find everything
again. The catalogue lives in
`%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\` and stays there.

## I cannot find the program in `Program Files`

It is not there: the install is for the current user only, so the program sits in
`%LOCALAPPDATA%\Gestionale Libreria\`.

## I looked up an ISBN and it found nothing

It means **none of the three sources knows that edition**. This happens with
Italian non-fiction from small publishers and with certain niche editions.

What to try, in order:

1. **search by title** — clear the ISBN, type title and author, and press the
   same button;
2. if it is **manga**, search by title anyway: AniList only shows up there, and
   on manga it is the best source;
3. **check the digits** of the ISBN: if one is missing the application refuses it
   («Not a valid ISBN: …»), whereas if there are thirteen but the code is not a
   book's, it asks whether to save it anyway — and in that case no source will
   ever know it, however many times you try;
4. fill it in by hand. That is not a defeat: the sources do not know everything.

## A source answers with an HTTP error

`Google answered with an error (HTTP 503)` and the like come **from the remote
catalogue**, not from the application. They are nearly always passing: try again
in a few minutes. The other sources have answered in the meantime anyway.

If **Google Books** is always wrong, check the key in Settings → Metadata with
the **Verify** button.

## The webcam viewfinder is black

Windows has picked a virtual camera (OBS, FaceRig, NVIDIA Broadcast) that is not
transmitting. Use the **Camera** dropdown under the viewfinder and pick the real
one. Details in [Scanning the barcode](Scanning-the-barcode.md).

## At startup it told me a new version is out — did it update itself?

No. **The application downloads nothing and installs nothing.** The notice reads
the list of published versions and tells you what changed; “Update now” only opens
the page in your browser, where you download the file whenever you want. Then you
install over the top, and your data stays where it is.

If that version does not interest you, **Skip this version**: it will not remind
you again until another one is out. If you want no startup check at all, untick
the box in Settings → Updates. The whole round is in [Updates](Updates.md).

## I pressed “Check for updates” and it says no version has been published

Not a fault: it means **no version has been published yet**, and the one you have
is the only one there is. That is the answer until the first one goes online.

## I have the same book twice

If the two rows really are two copies of yours, that is fine: they are two items,
maybe one is out on loan. If it is a mistaken duplicate, delete one row with the
bin.

When you scan an ISBN you already have, the application says so — *«you already
have one with this ISBN»* — but does not stop you, precisely because two copies
are legitimate.

## I have two identical genres: `Manga` and `manga`

This should not happen any more: the application reuses the spelling you chose
the first time, whatever the case or accents. If you have two entries from
before, reopen the books with the wrong spelling and pick the right one **from
the suggestions** rather than retyping it: when the last book leaves it, the
entry disappears from the filters.

## I see a dash in the Author column

The field is empty, there is no error. This holds for every column: `—` means
«not filled in».

## The search will not find a book that is there

Three things to check:

- **is a filter on?** The count at the top and the chips under the title say so.
  Try **Clear all**;
- **are you searching an indexed field?** The bar looks at title, subtitle,
  authors, tags, publisher, imprint and notes — **not** the description, nor the
  series name;
- **are you searching the start of a word?** The search works by prefix: `camil`
  finds `Camilleri`, but a chunk taken from the middle of a word will not.

If you mistyped, the application notices on its own and shows the books that come
close.

## How do I move everything to another computer?

With a backup. Copy the most recent `.zip`, install the application on the new
computer and use **Restore from a backup…**. Books and covers come back; theme,
language and API key you set again by hand.
The whole round is in [Backup and restore](Backup-and-restore.md).

## Can I use it on two computers at once?

No, and it is not worth trying. There is no sync: they would become two separate
catalogues, and restoring one over the other would wipe the second one's work.

Worse still is putting the data folder inside OneDrive or Dropbox: syncing
database files can **corrupt** them. Sync the backups, not the catalogue.

## I deleted a book by mistake

It cannot be undone. The only way is
[restoring a backup](Backup-and-restore.md), which brings the **whole** catalogue
back to that day's state — so you also lose whatever you did afterwards.

## The application starts in Italian

The language lives in Settings and applies from the next start. If it changed on
its own, somebody changed it there: Settings → Preferences → Language.

## I changed a series' total but the book's form does not follow

The two places do not do the same thing. The total **belongs to the series**: you
correct it in `/serie`, and from there you can also remove it. The box in the
book's form is for writing it the first time — clearing it does not reset it, on
purpose. Explained in [Series](Series.md).
