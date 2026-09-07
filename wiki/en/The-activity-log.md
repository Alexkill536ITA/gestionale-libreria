[Italiano](../it/Lo-storico-delle-azioni.md) · **English**

# The activity log

It answers one question: **what changed, and when?** A book catalogued, a price
corrected, a loan recorded, two publishers merged — every gesture that touches
the catalogue leaves a row, most recent first.

**It starts off**, and while it is off it records nothing.

## Turning it on, and what turning it off means

The **Activity log** checkbox lives in [Settings](Settings.md), under
**Preferences**. Turn it on and from then on what you do gets recorded: the first
event in the log is the switch-on itself.

| What you do | What happens |
|---|---|
| You **turn on** the checkbox | recording begins, no questions asked: nothing is taken away |
| You **turn off** the checkbox | the tick **does not move** until you confirm |

**Turning it off deletes what it has recorded**, and that is the most important
thing on this page. A question appears under the checkbox — *«Turning the log off
deletes what it has recorded»* — and it says **how many events it is about to
take away**: *«The 352 events recorded so far are deleted, and cannot be
recovered. Turning it back on starts from scratch.»* The two buttons are **Turn
off and delete** and **Keep it on**.

"Off" here means that nothing is left of what you did, not that it stops writing
on top of a pile that stays. If you turn it off by mistake, the way back is
[restoring a backup](Backup-and-restore.md) taken earlier — which brings back
*the whole* catalogue, though, not just the log.

## How to get there

The **gear** at the top right is a menu, and it holds three entries:
[Library dictionaries](Library-dictionaries.md), **Activity log** and,
underneath, **Settings**.

With the log off **that entry is not there**, and two are left: there is no log
to open.

## How to read the table

Top left, the tally of events — `352 events` — and on the right, when the last
one landed: *«the last one today at 18:20»*.

| Column | What it shows |
|---|---|
| When | the time above, the day below |
| Event | the action pill: `Created`, `Changed`, `Deleted`, `Loan`, `Return`, `Backup`, `Restore`… |
| Item | the cover with the title, and underneath the line that tells it apart |
| Detail | what changed |
| History | the button that opens the full history of that item |

Rows come **fifty to a page**, with **Previous** and **Next** at the foot of the
card as in [the catalogue](The-catalogue.md). Change page and the list goes back
to the top by itself.

The cover is read **now**, so it is there for books still in the catalogue. For
everything else — a series, a publisher, a person, the library itself — a
coloured tile with the initials of what it is takes its place.

## What changed

A **Changed** row says it field by field, and that is why this page exists: in a
box you get the field name, the previous value struck through, the arrow, and the
new value — `Price · 12.90 → 13.90`.

- **two pairs** fit in the cell, and the rest becomes a `+3`. Rest the pointer on
  it and you read them all;
- a value that was not there before reads *empty* in italics. An empty box would
  look like lost data, and it is not;
- the field names are **the form's own**, so `Publisher` here is `Publisher`
  where you typed it, and a very long value is cut with an `…`.

**A mass event states the number instead of becoming that many rows**: `41 books`
next to a merge of two publishers, `3 volumes` next to a series deleted along
with its volumes.

Where there is nothing to compare, the detail carries a note: the ISBN of the
book just created, the name of whoever borrowed a book, the file of a backup.

## The full history of an item

The button at the end of every row opens the whole history of that book — or of
that series, that publisher, that person. There the details read **in full**,
with no `+N`, and the row you came from is marked, so you do not lose it among
seven events.

**That history does not go through the page's filters**, because "full" means
full: with **Returns** on, the table shows two rows for that volume and the
dialog shows three.

## Filtering

Above the table:

- the **search box** looks in the titles, in the notes and **inside the changed
  fields** — so "Einaudi" also finds the event where the publisher became
  Einaudi;
- the **row of seven states** — **All** plus the six verbs: Created, Changed,
  Deleted, Loans, Returns, System — each with its own tally;
- **Scope** narrows to Book, Series, Publisher, Person or Library;
- **Period** offers Today, Last 7 days and Last 30 days. **Any** removes the
  filter.

**The tallies look at the other filters, not at the whole log.** A tally of zero
does not say that kind of event never happened: it says that *choosing this, with
the filters you have now, nothing is left*. The seven states stay in line even
when they read zero: a row that changes its number of entries while you filter is
worse than an entry that says zero.

With a filter on, the tally at the top becomes `12 of 352`, and **Clear the
filters** turns up beside it and removes them all in one go.

## A deleted book stays readable

The title appears **struck through**, with the tile in place of the cover; open
its full history and a pill says it: *«No longer in the library»*.

That works because the event carries a **copy** of the title, not a pointer to a
book that has to still exist. Without that copy the log would go mute the day
after a deletion, which is precisely the day you go and read it.

## What never enters the log

- **the Google Books key never lands in it.** If you change it, the row says
  `set` or `not set` and nothing more: a secret does not belong anywhere that
  gets copied and pasted;
- **description and notes record only the fact that they changed.** They change a
  thousand characters at a time, and what you need to know is *that* it happened:
  the field shows up, and both values stay *empty*;
- **importing a cover is not an action.** It writes a file and does not touch the
  catalogue, and you might never save that book. A changed cover reads as the
  `Cover` field inside the book's change, which is when it really happens.

## A restore replaces the log too

**It is right that it does** — that log described *that* catalogue — but it has
to be said beforehand rather than found out after, and the restore confirmation
says it in full: *«The activity log is replaced along with the catalogue: the
archive's log takes the place of the current one.»* The round is in
[Backup and restore](Backup-and-restore.md).

## When the page has no rows

They are three different things, and the page tells them apart:

| What you read | What it means |
|---|---|
| **The log is off** | the checkbox under Preferences is not on: from here on nothing gets recorded |
| **Nothing here yet** | it is on, and you have not done anything worth recording yet |
| **No event matches these filters** | the events are there, but these filters let none of them through: remove one |
