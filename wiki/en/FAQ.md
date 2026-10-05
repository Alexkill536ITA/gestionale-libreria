[Italiano](../it/Domande-frequenti.md) · **English**

# Frequently asked questions

## Windows says the program is not safe

SmartScreen warns because **the program is not code-signed**. It is not a sign
that the file has been tampered with. **More info** → **Run anyway**. The reasons
are in [Installation](Installation.md).

## Does it run on a Mac?

Yes. Every version carries a `.dmg`, a single one for Intel Macs and Apple
Silicon ones, and it has been opened and tried. The program was built for
Windows, but it works on a Mac.

macOS still warns you the first time, because there is no certificate paid for to
Apple: how to get past that warning is in [Installation](Installation.md), along
with the file to download. If something does not add up, do say so — above all
the webcam scanner and the covers, the two pieces that lean hardest on the
system.

## I uninstalled it — have I lost my catalogue?

No. **Uninstalling does not delete your data.** Reinstall and you find everything
again. The catalogue lives in
`%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\` and stays there —
unless you moved it to another folder, in which case it is where you put it,
or it lives on a server, which uninstalling does not reach at all. Settings →
Database tells you exactly where it is; the rest is in [Where the data
lives](Where-the-data-lives.md).

## I cannot find the program in `Program Files`

It is not there: the install is for the current user only, so the program sits in
`%LOCALAPPDATA%\Gestionale Libreria\`.

## I looked up an ISBN and it found nothing

It means **none of the four sources knows that edition**. This happens with
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

`Google answered with an error (HTTP 503)` and the like come **from the source's
service**, not from the application. They are nearly always passing: try again
in a few minutes. The other sources have answered in the meantime anyway.

If **Google Books** is always wrong, check the key in Settings → Metadata with
the **Verify** button.

## Where do I find this guide from the program?

The **question mark** at the top right, next to the gear: it opens these pages
in the browser, in the language you are using. Change the language in
[Settings](Settings.md) and the page that opens changes with it.

## The labels next to the icons at the top have gone

The window is too narrow for them to fit. **Catalogue**, **Series**,
**Publishers** and **Loans** stay where they are as icons, and resting the
pointer on one tells you its name: widen the window and the labels come back on
their own.

The search box sits at the centre of the window, and to stay there it needs the
same room on the left as on the right: when there is not enough, the labels are
what gives way — they used to end up *on top of* the search box.

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

## I cannot delete a book: it says somebody has it

It is on loan, and while it is away it cannot be deleted — neither with the
catalogue's bin nor with the tick that takes a series' volumes along. The message
names whoever has it: get it back from **Loans → Record a return**, and then
delete it.

This is not excessive caution: the open loan is the only thing saying that volume
is not on the shelf, and taking it away would make the book look available while
it sits in somebody's house.

## I scanned the barcode of a book coming back, and it says it is at home

It means that as far as the register is concerned that book never went out, and
there are two possibilities: either you never recorded it as a loan, or **the
code you read belongs to another book**. A volume has two or three printed on it
— the price, the shop's own code — and the scanner reads whatever lands in front
of it.

Try again framing the code under the ISBN, or take the other route: **Who is
bringing it back**, which shows only the books that person really has out. The
whole round is in [Loans](Loans.md).

## Who did I lend this book to?

You do not need to open the loans page: in the catalogue, the book's **Read**
cell carries a mark next to the reading state, and resting the pointer on it
reads out the name, the date and how long it has been away.

To see them all together, the **Loan → on loan** filter, or the **Loans** entry
in the bar.

## How do I note down a book I still have to buy?

Not in the catalogue: there is **To buy**, the entry to the right of the search
box. Type the ISBN or the title, pick the edition, and the volume stays there
with its price until you buy it — then **Add to the catalogue** brings it in
already filled. The list fills up **one volume at a time**: it does not tell you
which number of a series you are missing, because the sources do not give that.
It is all in [To buy](To-buy.md).

## I have two identical genres: `Manga` and `manga`

This should not happen any more: the application reuses the spelling you chose
the first time, whatever the case or accents. And if two entries came from
before, you do not have to go through the books: **tags, authors, genres,
imprints, shelves and languages** are fixed in [Library
dictionaries](Library-dictionaries.md), where `Manga` and `manga` become one
with **Merge into another**.

The only values left out of that page are the **publisher**, which has its own —
[Publishers](Publishers.md), with the aliases — and the **series** values, fixed
from [Series](Series.md).

## One author shows up twice, once in Japanese and once in Latin letters

Those are two names for the same person, and no comparison of letters can join
them: Japanese sources write `アネコユサギ`, the others `Yusagi Aneko`. You join
them in **Library dictionaries** — from the gear at the top right — with **Merge
into another**: you pick the name that stays, and the other one's books move to
it. The same holds for two tags that say the same thing.

From there you can also **rename** a wrong spelling and **remove** a value
nobody uses any more. The whole round is in
[Library dictionaries](Library-dictionaries.md).

## I turned the activity log off: where did what it recorded go?

Deleted — and the question that appears when you clear the checkbox says so,
along with how many events it takes away. «Off» here means that nothing is left
of what you did, not that it stops writing onto a list that stays. Turning it
back on starts from scratch, and the first event recorded is the switching on
itself. All of it in [The activity log](The-activity-log.md).

## I sort the catalogue by year, reopen it, and it is back as it was

The click on the heading holds for this session and is not remembered. The order
the catalogue **starts** from is chosen in Settings → Preferences → **Library
sort order**, and without a choice it is the most recently added. It is
deliberate: an order that saved itself would move the goalposts on every
absent-minded click.

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

With a backup. Make one with **Back up now** — none is ever made on its own —
copy the `.zip`, install the application on the new computer and use **Restore
from a backup…**. Books and covers come back; theme, language, API key and the
server connection, if you use one, you set again by hand: they live in the
settings, which never go into a backup.
The whole round is in [Backup and restore](Backup-and-restore.md).

If the catalogue lives on a server, there is nothing to move: on the new
computer set up the connection again from Settings → Database, and the books are
the usual ones. How is in [The catalogue on a
server](The-catalogue-on-a-server.md).

## Can I use it on two computers at once?

Yes, **by putting the catalogue on a server**: PostgreSQL, MySQL, SQL Server or
MongoDB. The covers go somewhere every computer can reach — **inside the
database**, **in an S3 archive** or in a **shared folder** — and from then on
every computer sees the same books. The round is in [The catalogue on a
server](The-catalogue-on-a-server.md).

It is not a program for several people, though: there are no accounts, and if
two people edit the same book at once whoever saves last wins, without the other
knowing.

Two copies of this computer's catalogue, on the other hand, stay two separate
catalogues: they do not talk to each other, and restoring one over the other
would wipe the second one's work. And the catalogue folder can sit inside
OneDrive or Dropbox, but open **on one computer at a time**: two writes at once
on the database file **damage** it. The reason is in [Where the data
lives](Where-the-data-lives.md).

## How do I take my books to the server?

From Settings → Database, with the connection filled in, **Bring this
computer's catalogue here** and then **Bring the catalogue**. A **copy** arrives
on the server, covers included; this computer's catalogue stays as it was. To
work over there, then, pick **On a database of yours**.

It only goes into a server catalogue that is still empty: if there are books
over there already, the move refuses rather than mix two together. All of it in
[The catalogue on a server](The-catalogue-on-a-server.md).

## The server does not answer — what do I do?

If the server stops answering — switched off, the network not reaching it,
credentials changed — the pages give way to «The catalogue on the server will
not open». **Nothing has been lost**, neither there nor here. When the server is
back, **Try again**; if you need to work right away, **Use the catalogue on this
computer**, knowing that it is a different catalogue (see below). The rest is in
[The catalogue on a server](The-catalogue-on-a-server.md).

## MongoDB will not do: it says it is a standalone server

The catalogue on MongoDB needs a **replica set**, because without one there are
no operations that roll back all together — and an interrupted restore would
leave the catalogue empty. A single node is fine, as long as it is started as a
replica set. How to do it is in [The catalogue on a
server](The-catalogue-on-a-server.md).

## Can I go back to this computer's catalogue?

Yes: Settings → Database, the **On this computer** radio. But they are **two
catalogues, not two copies**: what you did on the server stays on the server,
and here you find the catalogue as it was when you left it.

To bring the work done over there back here: with the server still chosen, make
a backup with **Back up now**, then switch to **On this computer** and
[restore](Backup-and-restore.md) that archive. This computer's catalogue is
replaced whole.

## Can I back up the catalogue on the server?

Yes, with the same button: **Back up now** archives the catalogue you are using,
and with the server chosen that is the one over there, with its covers wherever
they live. The zip still ends up **on this computer**, in the backup folder.
Details in [Backup and restore](Backup-and-restore.md).

## I restored onto the server and it did not restart

That is how it should be, and the confirmation says so. On the
server there is no file to swap at restart: the catalogue is emptied and
reloaded in one go, the pages reload straight away, and the outcome is «The
catalogue on the server has been replaced with the one from the archive.» The
restart is only for this computer's catalogue.

## I changed where the covers live: do they move on their own?

No, and the choice doesn't even save itself: with the catalogue on a server it
is a draft, and the place only changes with **Move the covers here**, which
copies them and, once the copy is done, writes it into the catalogue for every
computer. The old ones stay where they are.

## Why does a cover show up as a spine?

A drawn spine is what the application shows in place of an image it does not
have: either that book has no cover, or **the place the covers live did not
answer** — a shared folder out of reach, an S3 archive switched off. In the
second case the covers come back by themselves once that place answers again,
**when you change page or reopen the view**: as long as the view stays the same,
so does the spine. See [Covers](Covers.md).

## I deleted a book by mistake

It cannot be undone. The only way is
[restoring a backup](Backup-and-restore.md) — if you made one, because the
program makes none by itself — and it brings the **whole** catalogue back to
that day's state anyway, activity log included, so you also lose whatever you
did afterwards. With the catalogue on a server, the restore rewrites the
catalogue of **every** computer connected to it.

## The application starts in Italian

The language lives in Settings and **changes right away**, no restart. If it
changed on its own, somebody changed it there: Settings → Preferences →
Language.

## I changed a series' total but the book's form does not follow

The two places do not do the same thing. The total **belongs to the series**: you
correct it in `/serie`, and from there you can also remove it. The box in the
book's form is for writing it the first time — clearing it does not reset it, on
purpose. Explained in [Series](Series.md).
