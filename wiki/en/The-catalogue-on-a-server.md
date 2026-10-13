[Italiano](../it/Il-catalogo-su-un-server.md) · **English**

# The catalogue on a server

Out of the box the catalogue is a file on this computer. If you have a database
that answers over the network — a NAS, a home server, a rented service — the
catalogue can live **there**, and the pages read and write over there.

It is all done in **Settings → Database**, in the **On your own** group:
**On a database of yours**.

## What it is for, and what it is not

In the **On your own** group the section has two radio buttons, **On this
computer** and **On a database of yours** — the third, **With the library's
service**, is told in
[Where the data lives](Where-the-data-lives.md#with-the-librarys-service) — and
the one that is on says **which catalogue you are looking at**. Choosing «On a
database of yours» opens the server right away, **without a restart**: the pages
reload on their own, and from then on everything you do — a book, a loan, a
series — is written on the server.

**The catalogue on this computer stays untouched.** It is not emptied, not
moved and not kept up to date: these are **two catalogues**, not two copies
kept in step. Switching «On this computer» back on, you find your file exactly
as it was the day you left it.

And it is only fair to say what it is **not**: **it is not a multi-user
program.** There are no accounts and no permissions, and anyone with the
connection can do everything. Two computers can open the same catalogue, but
if two people change **the same book** at the same moment, whoever saves last
wins, and the other person's changes disappear without warning. For a family
sharing its shelves that is fine; for an office where ten people catalogue
together, it is not.

**For several people there is the library's service**, the third road: a
program that keeps the catalogue on one computer, where everyone signs in with
their own name and does only what their permissions allow, and where a book
opened by one person shows as “being edited” to the others instead of being
overwritten. How to install it is in
[Installing the service](Installing-the-service.md), how to work with it in
[Working in a library](Working-in-a-library.md).

## Which databases can hold the catalogue

You choose the family first — **SQL** or **MongoDB** — and then the **Engine**.

Four of them can receive a catalogue:

- **PostgreSQL**
- **MySQL**
- **SQL Server**
- **MongoDB**, on one condition: it has to be started as a **replica set**. A
  single node is fine, but a plain standalone server is refused with:

  > This MongoDB is a standalone server, and the catalogue needs a replica
  > set: without one, an interrupted restore would leave the catalogue empty.
  > A single node is fine, as long as it is started as a replica set.

The other two in the list, **MariaDB** and **SQLite (network file)**, can be
configured and tested, but **cannot receive a catalogue**. If you turn on «On a
database of yours» with one of them, the window stops on the screen of the catalogue that
will not open — with the network file the title is «The catalogue in the network
file will not open» — with the sentence:

> “mariadb” cannot receive a catalogue yet: for now PostgreSQL, MySQL, SQL
> Server and MongoDB can.

From there you go back with **Use the catalogue on this computer**.

## Filling in the connection

The fields are those of any program that talks to a database:

- **Host** — the name or address of the server;
- **Port** — **fills itself in** with the engine's port: 3306 for MySQL, 5432
  for PostgreSQL, 1433 for SQL Server, 27017 for MongoDB. Changing engine
  updates it; a port you typed yourself stays;
- **Database name** — the one where the catalogue will live;
- **User** and **Password**;
- **Encrypted connection (TLS)** — if the server offers it, user and password
  do not travel in the clear;
- **Authentication database**, which appears **only with MongoDB**: it is the
  database where the user is defined, which is not necessarily the one holding
  the data. An administrative user lives in `admin`, one created for this
  application in the database it uses. **Empty means `admin`.**

**The password is typed and stays as dots.** It does not appear on the screen
of the server that does not answer, nor in the
[activity log](The-activity-log.md), where a password change only says
`set` or `not set`.

**Everything saves itself**, like the rest of the window, even half-done: a
draft left halfway is not lost.

**If the server is already on**, changing the connection saves the new
configuration as you type, but the catalogue reopens **when you close the
settings**: that way a half-typed address does not make the window disappear.
If the new connection does not answer, closing brings up the screen of the
server that does not answer, with its two ways out.

## Where the covers live

Under **Covers**, three options say where the images of the catalogue on the
server live:

- **Inside the database** — the images travel with the database: one place to
  back up, and a database that grows fast;
- **Folder** — the database stays light and the images live in a shared
  folder, **which every computer** that opens that catalogue has to reach. Here
  a network folder is fine, unlike the catalogue on this computer: you pick it
  with **Browse** or type it, but it must be a full path;
- **S3 archive** — the images live on an S3-compatible service (Amazon S3,
  MinIO, Backblaze B2 and the like) that every computer reaches over the
  network: no shared disk to keep.

The starting choice is **Folder**.

The S3 archive needs five fields: **Service address**, **Bucket**, **Region**,
**Key** and **Secret**. The region is the only one you can leave empty, and
then it means `us-east-1`; the secret stays as dots, like the password.

### The catalogue decides the place

With the server's catalogue open, where the covers live **belongs to the
catalogue**: it holds for every computer that opens it, and the section says so
under the title. A line says **how many covers there are, how much they weigh,
where they are** and that this computer **can see them**.

The key and secret of an S3 archive **stay on each computer**, in the **This
computer's** box, and never enter the catalogue: every computer puts in its own.

### Changing place is a single action

Picking another option, or typing another folder, **saves nothing**: it is a
draft. Below it a box says how many covers go to the new place, where they
leave from and where they arrive, and carries **Move the covers here**.

The button **copies** the images with a bar that counts, and **only once the
copy is done** does the catalogue name the new place: until then every computer
keeps using the old one, so nobody ever sees an empty place. The copies left in
the old place are **not deleted by the program**: once you are sure they are all
in the new place, you remove them yourself. **Cancel** brings the draft back to
the catalogue's place.

The other computers notice on their own, within half a minute. If the new place
is an archive, whoever doesn't have its key sees the books with a spine and a
notice with two boxes to put it in: **Use this key** tests it before keeping it,
and says so if the archive refuses it.

**A drive letter belongs to one computer.** `Z:` on another computer may be
another disk, or be missing: for a shared folder the section suggests the
network path, such as `\\nas\libreria\copertine`. If this computer can't open
the catalogue's folder, a notice says so, with **Try again**.

If before this version this computer kept its covers in a place of its own,
different from the catalogue's, and some were left there, a notice counts them
and offers to move them where the catalogue keeps them, so everyone sees them.

With the catalogue **on this computer** the same choice says where the covers
will go when you take the catalogue to the server, and saves itself like the
rest of the section.

## Testing the connection

**Test the connection** lights up once host, port and database name are there,
and opens a real connection: user and password are checked all the way, and if
it works the green line gives the engine, the version the server declares and
how many milliseconds it took to answer.

The test looks at the covers too: a **Folder** is tested by **writing** a file
into it and deleting it, an **S3 archive** by writing, reading back and
deleting a test object. With MongoDB it also checks the replica set.

When it does not work, it says **which** thing does not work:

- “The server does not answer: check the address, the port, and that it is
  running.”
- “The server refused the user and password.”
- “There is no database called “libreria” on the server.”
- “The user cannot enter the database «libreria»: either it does not exist, or
  it has not been granted to them.”
- “This server asks for the password to be encrypted before it can check it:
  turn on «Encrypted connection (TLS)» and try again.” — the typical case of a
  freshly installed MySQL 8;
- “The encrypted connection failed: the server may not offer TLS.”
- “The server took too long to answer.”
- “I cannot write in the covers folder “…”.”
- “The cover archive does not answer: check the address, the bucket, and that
  the service is running.”
- and, if a field of the archive is missing, the sentence that says which one:
  the address, the bucket, the key or the secret.

The test says whether the server answers, not whether the catalogue inside it
is sound: that shows up when the catalogue opens, as «An empty database gets
itself ready» below explains.

## Bringing over the catalogue you have

The most common case is having two hundred books on this computer already and
wanting them on the server. That is **Bring this computer's catalogue here**,
at the bottom of the section.

The button asks for confirmation, and the confirmation counts the books **on
this computer**, that is, the ones about to leave:

> 212 books from this computer are about to be copied to
> nas.local:5432/libreria.

**Bring the catalogue** does the transfer: the covers first, then the books,
the series, the loans and the rest. At the end a green band says how many books
and how many covers arrived.

The transfer **brings the data, but does not change the catalogue you are
looking at**: that is up to the radio button. Once it is done, to work on the
server choose «On a database of yours». And the catalogue on this computer stays as it is:
a copy of it lands on the server.

The button stays off, or the action is refused, in these cases:

- **the connection is not complete**, or the automatic save has not yet
  written the last change: the transfer uses the saved configuration, and
  pressing earlier would talk to a different server from the one on screen.
  Wait a moment and it lights up again;
- **the engine cannot receive a catalogue** (MariaDB, SQLite): a line under the
  button says so;
- **the server already holds a catalogue**:

  > That server already holds a catalogue, with 40 books in it: moving this one
  > on top would mix two of them.

- **the catalogue on this computer is empty**:

  > The catalogue on this computer is empty: there is nothing to move to the
  > server.

In all these cases nothing is written, neither here nor there.

## An empty database gets itself ready

There is no need to prepare tables or collections by hand. **An empty database,
the first time the program opens it, becomes a catalogue**: that happens when
you turn on «On a database of yours» or when you bring this computer's catalogue over.

Two cases are refused instead, because neither fixes itself:

- a catalogue **left half-made**, interrupted while being created:

  > The catalogue on that server was left half-made, at version 3: it was
  > interrupted while being created, and starting over on top of what is there
  > would ruin it.

- a catalogue written by **another version** of the program:

  > That catalogue is at schema version 5, and this version of the program
  > writes a different one.

In the second case the way out is usually to update the program on this
computer, so that every computer opening that server has the same version.

## When the server does not answer

Server off, network not reaching it, password changed: the program **does not
fall back on the catalogue on this computer**, and does not show you a window
full of books that are not the ones you asked for. It stops on a screen:

> **The catalogue on the server will not open**

Below it is the server's address in the form `user@host:port/database` —
**never the password** — and the reason. You get out with two buttons:

- **Try again** — once the server is back on or the network is back, it reopens
  the catalogue **without a restart**;
- **Use the catalogue on this computer** — switches «On this computer» back on
  and reopens your file.

And the last line is the one that matters: **nothing has been deleted.** The
catalogue on the server is where it was, and the one on this computer has not
been touched.

**If the server goes down while you work, the screen comes up by itself.** The
program notices as soon as a page asks the server something, and also while you
are looking at a page that is standing still: every **30 seconds**, and only
while the window is visible, it checks that the server still answers.

## Covers that do not load

If the place of the covers does not answer — the shared folder is off, the S3
archive cannot be reached — the titles stay and the images become **drawn
spines**, as for a book that never had a cover (see [Covers](Covers.md)).

When the place is reachable again, **the images do not come back by
themselves**: they return when you change page or reopen the view.

The **reduced copies** of the covers — the small ones of the catalogue and of
the rows, and the intermediate ones of the larger panels — are made the first
time they are needed and **kept on this computer**. So after the first opening,
browsing is fast even with the images on a distant server. The flip side is
that a reduced copy can keep showing here even if the original over there is
gone.

## Backup, export, import and restore

All four work **with the catalogue on the server too**, and they concern the
catalogue you are looking at. How to use them is in
[Backup and restore](Backup-and-restore.md); with the server on, three things
change:

- **the backup is created in a folder on this computer**, the one in the Backup
  section, even though the catalogue lives over there. The same goes for the
  CSV file of the export. A backup taken from the server can also be restored
  on this computer, and the other way round;
- **importing from a spreadsheet** adds the books to the server's catalogue;
- **the restore does not restart the program.** It first takes a safety backup
  of the server's catalogue, then **replaces it in one go** with the one from
  the archive, and at the end says:

  > The catalogue on the server has been replaced with the one from the
  > archive.

  Remember that this catalogue **is used by every connected computer**: a
  restore takes them back too.

## The activity log

With the server on, the [activity log](The-activity-log.md) page shows **the
server's log**: what you do to books, series, publishers and loans is written
over there, next to the data it describes.

The events born from the settings — `Settings`, `Database configured`,
`Catalogue moved` and `Catalogue brought to the server` — stay instead **in
this computer's log**, because they are about this computer and not about the
catalogue. While you look at the server you do not see them: they come back
when you return to «On this computer».

The log is turned on and off from the Preferences, once for both catalogues.
Turning it off **empties both**: the server's, that is the events the
confirmation counted, and this computer's, where the settings events live. If
the server does not answer, the log **does not turn off**: the box stays on and
the error shows, instead of turning off while leaving over there what the
confirmation promised to delete. The server's log is trimmed to a year every time the catalogue opens, and a restore
leaves its «Restore» event over there.

## Where the configuration lives

The connection lives in `impostazioni.json`, in the data folder of this
computer; **the database password and the S3 archive secret do not**: they live
in the system keychain, under the entry “Gestionale Libreria - impostazioni”,
and stay in the file only if the keychain is missing or refuses them (see
[Where the data lives](Where-the-data-lives.md)). **None of this goes into
backups**: on another computer the connection has to be typed in again, and
the same after a reinstall.

One last thing that confuses: in the list of sections of the
[Settings](Settings.md), the line under **Database** counts the books **on this
computer**, not those on the server. Even while you work over there, that
number is about the file you have here.
