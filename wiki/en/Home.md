[Italiano](../it/Home.md) · **English**

# Gestionale Libreria

A catalogue for paper books, on Windows and macOS. On your own it asks for no
account: out of the box it lives on this computer and works offline — except
when you go looking up a book's details, which come from five public
catalogues. If you like, the catalogue can live **on a database on the
network** instead, and then the network is needed for everything:
[The catalogue on a server](The-catalogue-on-a-server.md) tells that story.

In a library, the catalogue is kept by the **library's service**, on one
computer, and everyone signs in to it with their own name and permissions:
[Installing the service](Installing-the-service.md) and
[Working in a library](Working-in-a-library.md) tell that story.

Since September 2026 it also runs on **macOS**: every version carries a file of
its own, and how to install it is in [Installation](Installation.md).

![The catalogue](images/catalogo.png)

## What it does

| | |
|---|---|
| **[The catalogue](The-catalogue.md)** | The table of your books: sorting, paging, editing, deleting |
| **[Adding a book](Adding-a-book.md)** | The form, the twenty fields, what is required (very little) |
| **[Looking up metadata](Looking-up-metadata.md)** | One button fills the record from OpenLibrary, Google Books, SBN, NiceBooks and AniList |
| **[Covers](Covers.md)** | They come down on their own, or you supply one from a file or a web address |
| **[Search and filters](Search-and-filters.md)** | The top bar, the eleven filters, the fallback when you mistype |
| **[Series](Series.md)** | Which volumes you are missing, and the values a series passes to its volumes |
| **[Publishers](Publishers.md)** | One publisher at a time: its works in a carousel, and the rule that holds its different names together |
| **[Loans](Loans.md)** | Who has which book, for how long, and how you get it back |
| **[To buy](To-buy.md)** | The volumes you do not have yet: what they cost all together, and how they join the catalogue with one click |
| **[Scanning the barcode](Scanning-the-barcode.md)** | The webcam reads the ISBN off the back cover |
| **[The activity log](The-activity-log.md)** | What you changed and when, if you turn it on — and what happens when you turn it off |
| **[Library dictionaries](Library-dictionaries.md)** | Tags, authors, genres, imprints, shelves and languages: rename them, merge two names for the same thing, remove the ones nobody uses |
| **[Settings](Settings.md)** | The five entries of the rail: Preferences, Metadata, Database, Backup and Updates |
| **[Where the data lives](Where-the-data-lives.md)** | The catalogue folder, how to move it without losing anything, and the connection to a server |
| **[The catalogue on a server](The-catalogue-on-a-server.md)** | When the server becomes the catalogue in use: the engines that can do it, where the covers go, how you bring over what you already have |
| **[Installing the service](Installing-the-service.md)** | The library's catalogue on one computer, and the others signing in to it with their own name: Windows, Mac, Linux and Docker |
| **[Ways to sign in](Ways-to-sign-in.md)** | The service's password, Active Directory, a sign-in provider like Keycloak, Kerberos: how you sign in, how long the session lasts, how they are switched on |
| **[Users, groups and permissions](Users-groups-and-permissions.md)** | Who signs in to the service and what they can do: the “Users and groups” dialog, the three starting groups, every permission |
| **[Working in a library](Working-in-a-library.md)** | For whoever works on the service's catalogue: what you see depending on your permissions, a book “being edited” by someone else, your loans, your readings |
| **[Backup and restore](Backup-and-restore.md)** | A copy when you ask for one, the CSV export, importing from a spreadsheet, the way back |
| **[Updates](Updates.md)** | It tells you when a new version is out, and installs nothing by itself |
| **[FAQ](FAQ.md)** | When something does not add up |
| **[Third-party licenses](Third-party-licenses.md)** | Whose code the program embeds, and under which license |

These pages open **from the program**: the question mark at the top right, next
to the gear, brings you here in the language you are using.

## The whole round, in four moves

1. **[Install it](Installation.md)** and open it. The [first-start
   guide](Installation.md#first-start) asks how you will use the program: on
   your own, on this computer, the catalogue starts empty.
2. Press **Add book**. If the book is in your hands, press **Scan** and point the
   camera at the barcode; otherwise type the ISBN, or even just the title.
3. Press **Look up metadata**: title, authors, publisher, year, pages and cover
   arrive on their own. Where two sources disagree, a pill appears under the
   field and you pick.
4. Add what no source can know — where the book sits on the shelf, what you paid,
   whether you have read it — and **Save**.

## Two things worth knowing up front

**The title is the only required field.** Everything else can be left empty and
filled in later.

**The data is yours and it sits where you say.** Out of the box — **On this
computer** — on your disk: no account, no sync, no cloud. If you pick **On a
database of yours**, on the database you pointed it to; **With the library's
service**, wherever the service keeps it; and nowhere else. The
flip side is that if that disk dies the catalogue goes with it, and no backup is ever made on
its own: every now and then make one and copy it onto a USB stick —
[Backup and restore](Backup-and-restore.md) explains how.

## A note on the language

The interface speaks Italian and English, and switches instantly from
[Settings](Settings.md). **Your catalogue data does not translate**: genres, tags,
shelves and book languages stay written the way you typed them. So do the CSV
column headers — a file that changes its header with the language does not open
the same way twice.
