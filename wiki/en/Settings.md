[Italiano](../it/Impostazioni.md) · **English**

# Settings

**The gear top right always opens a menu**: “Library dictionaries”, “Activity
log” when it is on, and under a separator **Settings**, which opens this window,
and **Licence**. Both of those pages have a chapter of their own —
[Library dictionaries](Library-dictionaries.md) and
[The activity log](The-activity-log.md); above the separator are the entries that
take you elsewhere, below it the ones that open a window.

## The window

Five sections on a rail down the left: “Preferences”, “Metadata”, “Database”,
“Backup” and “Updates”.

![Preferences](images/impostazioni-preferenze.png)

**Changes save themselves**, with no Save button. The confirmation is not a word:
it is the line under each rail entry, summing up the state right now —
`Dark · English · EUR`, `key set · 1/s`, `usual folder · 227 books`,
`today, 12:41 · 4 copies`, `0.1.0 · checked at startup` — and it rewrites
itself the moment you change
something, even from another section. With the log on, the Preferences line
takes `· log` at the end.

**The line under “Database” always speaks about this computer**: it names the
folder of the catalogue here and counts the books in it, even while you are
working on the server.

## Preferences

**Theme** — Light, Dark, or **Match the system**, which follows Windows even when
it switches at sunset. Light and dark, in contrast, stay put.

**Language** — Italian or English. Changes right away, no restart, and it covers
error messages too. What does **not** change is the data you typed: genres, tags,
shelves and book languages stay written the way you entered them.

**Currency** — EUR, USD, GBP, CHF, JPY. This is the currency a new book **starts
in**: in the form you change it book by book, and books already catalogued stay
as they are.

**Catalogue order** — it says **where the catalogue starts from** when it opens,
not where it is right now. A dropdown with seven entries: “Recently added” plus
the six sortable columns — Title, Author, Year, Genre, Shelf, Read — and next to
it the **Ascending** / **Descending** track.

Clicking a column header in the catalogue changes the order **for that session**,
and it does not come back here: the next time you open it, you start from this
choice again. With nothing chosen it is “Recently added”, which is what the
catalogue has always done — and then the direction track is off, because the
books you catalogued last stay on top and that direction is not up for
discussion.

**Activity log** — a box, and it starts off. Turned on, it records what you do —
a book created, a field changed, a loan — and shows it in the page the gear adds
to its menu: the rest is in [The activity log](The-activity-log.md).

**Turning it off deletes what it has recorded**, and it asks you first: the
question appears under the box, saying how many events it is taking away, with
**Turn off and delete** and **Keep it on**. The tick does not move until you
confirm — turning it off and deleting are the same gesture, and a box already
unticked would say the thing was done. Turning it on asks nothing, because it
takes nothing away.

Under the box there is also the line saying **how far back the log goes**: it
keeps one year, and older events are deleted on startup. That cap is fixed and
not something you pick.

None of these choices goes into the catalogue or the backups: they live in a
separate file, on this computer.

The events the log records are another matter: those live in the catalogue, so
they go into the backups, and a restore replaces them too.

## Metadata

The sources in cascade order, numbered.

![The Metadata section](images/impostazioni-metadati.png)

### 1 · OpenLibrary

Leads the cascade: where it answers, its values are the ones that end up in the
book.

There is a single box, **Contact address**, and it is optional. OpenLibrary
accepts **one request per second** from anyone who does not introduce themselves
and **three** from anyone leaving an address. Without it everything still works,
just slower.

### 2 · Google Books

![The Google Books key](images/impostazioni-metadati-google.png)

Fills in what OpenLibrary does not know, and it is **the only one that knows
niche Italian publishing**. It wants an API key, free from the Google Cloud
Console.

- the key goes in the box and stays **masked**; the eye reveals it;
- **Verify** tries it out and says straight away whether it works;
- **clearing the box removes the key** from the application. With no key, Google
  Books is simply skipped.

The free quotas are 1,000 requests a day and 100 a minute, and looking up a book
spends **one**: cataloguing by hand you will not reach them.

### 3 · OPAC SBN

The Italian library catalogue. **Nothing to set**: it answers with no key and no
introductions.

### 4 · NiceBooks

Last to fill the gaps, and the one that carries **the Italian publishing the
others do not know** — manga included. **Nothing to set**: no key, no sign-up, a
rate of one request a second fixed in the program.

For every book it makes **two requests** instead of one, which is also why an
ISBN lookup takes a couple of seconds longer. That is the price of the coverage:
it comes last, so it only works where the other three had no answer.

### AniList — outside the cascade

![AniList](images/impostazioni-metadati-anilist.png)

Manga and Japanese comics. It does not know ISBNs, so it stays out of the cascade
and only shows up in the search by title. No key, no settings.

## Database

![The Database section](images/impostazioni-database.png)

“Where the data lives: in a folder on this computer, on a database of yours, or
on the library's service. The radio button picks which one is used.” There are
three roads in two groups: **On your own** holds **On this computer** and **On a
database of yours**, **In a library** holds **With the library's service**.

**On this computer** says which folder the database and the covers are in, and
lets you take them elsewhere: move the catalogue — which **copies and deletes
nothing** —, open one that already exists, start a new one, go back to the
default folder. The whole round, the screen that shows up when that folder is
gone, and the network folders that are refused are in
[Where the data lives](Where-the-data-lives.md).

**On a database of yours** puts the catalogue on a database on the network — PostgreSQL,
MySQL, SQL Server or MongoDB — with the covers inside the database, in a shared
folder or in an S3 archive. **Choosing that radio opens the catalogue over
there, without restarting**, and from then on the pages read and write on the
server; the catalogue on this computer stays as it was, and the other radio
takes you back to it. Connection, test, covers and **Bring this computer's
catalogue here** are in [The catalogue on a server](The-catalogue-on-a-server.md).

**With the library's service** talks to the program the library keeps on its
server, the only one that sees the database: all it needs here is its
**Address**, which starts with `https://` and is the one of the computer the
service runs on. On the first connection the section shows the service's
fingerprint and asks **I trust it**: first you compare it with the one the
service prints when it starts, and until you trust it this computer sends it
nothing. Name and password are not here: a dialog that opens by itself when
needed asks for them, and who is signed in shows in the top bar. With the
catalogue on the service, backup, export, restore and **Bring
this computer's catalogue here** stay off until they arrive, while importing
from a spreadsheet works; the rest is in
[Where the data lives](Where-the-data-lives.md#with-the-librarys-service).

## Backup

![The Backup section](images/impostazioni-backup.png)

Everything here is told in full in [Backup and restore](Backup-and-restore.md). In
short:

- **the folder** the files end up in, changeable with Browse;
- **Back up now**, **Open folder**, **Export to CSV**;
- the **Import from a spreadsheet** block: **Pick a CSV file…** reads a
  spreadsheet — the one “Export to CSV” writes, or one written by hand — and
  before writing anything says how many books would come in and which rows stay
  out. It adds and replaces nothing: the books already there stay where they
  are;
- the **Restore** block, ringed in red because it replaces everything.

Backup, export, import and restore work on the catalogue you are using, whether
it is on this computer or on the server.

## Updates

![The Updates section](images/impostazioni-aggiornamenti.png)

The installed version, a button to **check right now** for a newer one, and the
**Check for updates at startup** box, which you can untick.

If something new is out you get its number, its date and its notes, with the
button that takes you to the page to download from. **Nothing is downloaded and
nothing installs itself**: why, and what the notice's three buttons do, is in
[Updates](Updates.md).

## Where these settings live

In `impostazioni.json`, in this computer's data folder, **outside the database
and outside the backups**. It holds:

- the preferences — theme, language, currency, catalogue order, log on or off;
- the contact address and the Google Books key;
- where the catalogue lives: the choice between “On this computer”, “On a
  database of yours” and “With the library's service”, and the catalogue folder
  when it is not the default one;
- the server connection, **with its password**, and the covers archive, **with
  its secret**;
- the address of the library's service and the fingerprint you trusted. The
  service's session is not there: it lives in the system keychain;
- the backup folder, the scanner's camera, the update check and the version you
  chose to skip.

That is not a detail: a restored archive does not bring you another computer's
theme, API key and camera. These are *this* machine's preferences, and they stay
put even after a restore — and even after the catalogue has moved to another
folder, because that file always stays in the starting folder.

**Do not share it**, and do not attach it to a report: the keys and passwords
you gave the program are inside.

## Licence

It says **who the program belongs to and who owns what is inside it**, which are
two different things. At the top, the licence of Gestionale Libreria: you can use
it, copy it, modify it and distribute it, even to make something of your own, as
long as the notice stays with it — and under that line the licence text sits
**in full**, not as a summary.

Below it, the components written by other people that the program includes: there
are more than a thousand, each one stays with its authors under the licence they
chose, and **Open the notices** opens the file that lists them all. That file
travels with the program, so no internet is needed to read it; if you built the
application yourself and have not made a full build yet, the dialogue says so
rather than staying quiet. The same list is in
[Third-party licenses](Third-party-licenses.md).
