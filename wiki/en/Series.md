[Italiano](../it/Le-serie.md) · **English**

# Series

The **Series** entry in the bar answers one question: **which volumes am I
missing?**

![The series view](images/serie.png)

A series turns up here as soon as you type its name in a book's form. There is
nothing to set up first.

## How to read a row

![A series row](images/serie-riga.png)

From the left:

- **the name** of the series;
- **how many you have out of how many** — `2 / 20`. The total sits in an editable
  box: correct it right there, it saves itself;
- **which ones are missing**, with the gaps merged: `missing 2, 4–20` instead of
  eighteen numbers in a row;
- on the right, the pill with the tally: `18 volumes missing`;
- underneath, **the row of spines**: real cover for the volumes you have, dashed
  box with the number for the ones you do not.

The list is not alphabetical: **wrong totals come first** — the series where you
hold more volumes than the total claims, which is the sign of a wrong total —
then the ones missing the least, and the complete ones last.

## Adding a series

**Add series**, top right.

![Adding a series](images/serie-aggiungi.png)

The name is enough. The total can be left empty, and it is worth doing while the
series is still running: with no total, the application will never tell you that
the volume after your last one is missing.

The volumes get catalogued later, from a book's form, by typing that name in the
Series field.

## Editing and deleting

Hover a row: the pencil and the bin appear on the right.

![A series' actions](images/serie-riga-azioni.png)

The pencil changes name and total. The bin asks first:

![The delete confirmation](images/serie-elimina.png)

Mind the checkbox, which is **ticked by default**:

- **ticked** — the catalogued volumes go too, covers and all;
- **unticked** — the volumes stay in the catalogue and only lose their series and
  number.

It cannot be undone. A series with no volumes shows no checkbox, because there is
nothing to take along.

## The total volumes: two routes

The same number can be touched in two places, and they do not do the same thing:

| Where | What clearing the box does |
|---|---|
| **Here, in `/serie`** | the total really goes |
| In a book's form | **nothing**: the total stays |

The difference is deliberate. That number belongs to the series, not to the
single copy: if clearing the box in the form reset it, saving *one* volume would
wipe the total for all the others. The box in the form is there because that is
where the total arrives from AniList without you having to type it.

## An empty series does not vanish

A series added by hand stays in the list even with no volumes, and even after a
restart. If you do not want it any more, its bin removes it.
