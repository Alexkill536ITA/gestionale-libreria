[Italiano](../it/Impostazioni.md) · **English**

# Settings

**The gear top right always opens a menu**: “Library dictionaries”, “Activity
log” when it is on, and under a separator **Settings**, which opens this window.
Both of those pages have a chapter of their own —
[Library dictionaries](Library-dictionaries.md) and
[The activity log](The-activity-log.md).

Four sections on a rail down the left.

![Preferences](images/impostazioni-preferenze.png)

**Changes save themselves**, with no Save button. The confirmation is not a word:
it is the line under each rail entry, summing up the state right now —
`Dark · English · EUR`, `key set · 1/s`, `today, 12:41 · 4 copies`,
`0.1.0 · checked at startup` — and it rewrites itself the moment you change
something, even from another section. With the log on, the Preferences line
takes `· log` at the end.

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

## Backup

![The Backup section](images/impostazioni-backup.png)

Everything here is told in full in [Backup and restore](Backup-and-restore.md). In
short:

- **the folder** the files end up in, changeable with Browse;
- **Back up now**, **Open folder**, **Export to CSV**;
- the **Restore** block, ringed in red because it replaces everything.

## Updates

![The Updates section](images/impostazioni-aggiornamenti.png)

The installed version, a button to **check right now** for a newer one, and the
**Check for updates at startup** box, which you can untick.

If something new is out you get its number, its date and its notes, with the
button that takes you to the page to download from. **Nothing is downloaded and
nothing installs itself**: why, and what the notice's three buttons do, is in
[Updates](Updates.md).

## Where these settings live

In `impostazioni.json`, in the data folder, **outside the database and outside
the backups**.

That is not a detail: a restored archive does not bring you another computer's
theme, API key and camera. These are *this* machine's preferences, and they stay
put even after a restore.
