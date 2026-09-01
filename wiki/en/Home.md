[Italiano](../it/Home.md) · **English**

# Gestionale Libreria

A personal catalogue for paper books, on Windows. It lives on one computer, asks
for no account and works offline — except when you go looking up a book's
details, which come from four public catalogues.

Since September 2026 every version also carries a file for **macOS**, which
nobody has opened on a Mac yet: what to expect is in
[Installation](Installation.md).

![The catalogue](images/catalogo.png)

## What it does

| | |
|---|---|
| **[The catalogue](The-catalogue.md)** | The table of your books: sorting, paging, editing, deleting |
| **[Adding a book](Adding-a-book.md)** | The form, the twenty fields, what is required (very little) |
| **[Looking up metadata](Looking-up-metadata.md)** | One button fills the record from OpenLibrary, Google Books, SBN and AniList |
| **[Covers](Covers.md)** | They come down on their own, or you supply one from a file or a web address |
| **[Search and filters](Search-and-filters.md)** | The top bar, the nine filters, the fallback when you mistype |
| **[Series](Series.md)** | Which volumes you are missing, shown as gaps in a row of spines |
| **[Scanning the barcode](Scanning-the-barcode.md)** | The webcam reads the ISBN off the back cover |
| **[Settings](Settings.md)** | Theme, language, currency, the metadata sources, the backup folder |
| **[Backup and restore](Backup-and-restore.md)** | A copy a day, the CSV export, the way back |
| **[Updates](Updates.md)** | It tells you when a new version is out, and installs nothing by itself |
| **[FAQ](FAQ.md)** | When something does not add up |

## The whole round, in four moves

1. **[Install it](Installation.md)** and open it: the catalogue starts empty.
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

**The data is yours and it sits on your disk.** No account, no sync, no cloud.
The flip side is that if the disk dies the catalogue goes with it: every now and
then copy a backup onto a USB stick — [Backup and restore](Backup-and-restore.md)
says where to find them.

## A note on the language

The interface speaks Italian and English, and switches instantly from
[Settings](Settings.md). **Your catalogue data does not translate**: genres, tags,
shelves and book languages stay written the way you typed them. So do the CSV
column headers — a file that changes its header with the language does not open
the same way twice.
