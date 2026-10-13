[Italiano](../it/Lavorare-in-biblioteca.md) · **English**

# Working in a library

This page is for whoever works on a library's catalogue through its **service**,
with a name and permissions given by someone else. The rest of the guide holds
for you too — adding a book, searching, lending work the same way —, and here
there is only what changes when the catalogue belongs to everyone.

How the service is set up and how permissions are given are told in
[Installing the service](Installing-the-service.md) and
[Users, groups and permissions](Users-groups-and-permissions.md).

## Signing in

The first time you need the **service's address** and the way to sign in, which
whoever runs it gives you. The address goes into the [first-start
guide](Installation.md#first-start), choosing **In a library** and then **I'll
connect to the library's service**, or later into **Settings → Database**, **With
the library's service**. On the first connection the app shows the service's
fingerprint: compare it with the one whoever runs it gives you, and if it is the
same press **I trust it**.

Then the **Sign in to the service** dialog opens by itself. Depending on how the
service is set up, it asks for a name and password, for the domain account,
opens a sign-in provider's page in the browser, or offers **Sign in as …** with
your Windows name: each case is told in [Ways to sign in](Ways-to-sign-in.md).

Once you have signed in, **reopening the program you do not need to sign in
again** as long as the session is alive.

## The menu with your name

Your name shows in the top bar. Clicking it opens a menu, which says whether you
are an **Administrator** or a **User** and which service you are connected to,
and holds:

- **My loans…** — see below;
- **Users and groups…** — only for whoever manages the users;
- **Change password…** — only if you sign in with the service's password;
- **Sign out**, which ends the session and opens the sign-in dialog again.

## What you see, depending on your permissions

What you can do is decided by your groups. A reader (the **Lettore** group), for
example, sees the catalogue and nothing else; the desk (**Bancone**) lends and
takes back books; the editor (**Redattore**) catalogues. Whoever signs in from
the domain without being in any of the library's groups knows straight away,
from a notice: “You are signed in as a Reader”.

**The entries you do not need disappear from the bar.** Without the permission
to see loans there is no **Loans**, without the purchase-list one there is no
**To buy**, without the log one there is no **Activity log** in the gear menu.

**The actions you cannot take show switched off, and say why.** Under the button
a sentence names the missing permission:

> Your user doesn't have the “Back up the catalogue” permission: ask an
> administrator of the service for it.

It happens with backup, export, importing from a spreadsheet, restore, the log
switch and the purchase-list bar.

**A book you cannot edit opens read only.** The form is titled “The book, read
only”, under the title the same sentence names the permission, and at the bottom
only **Close** is left. Without the permission to add books there is no **Add
book**, and an empty catalogue only says “When someone adds a book, it will show
up here.”

**People's contacts may be missing.** Without the “See people's email and phone”
permission, in the loans people show with their name and nothing else: the
service does not send those contacts at all.

If an administrator takes a permission away while you work, the next action is
refused with “Your user isn't allowed to do this: ask an administrator of the
service.”

## A book someone else is editing

When someone opens a book to edit it, the service **holds** it for them: as long
as they keep it open, others can look at it but not save it. That way two
people do not overwrite each other.

In the catalogue, at the end of that book's row, in place of the buttons, a pill
shows the name of whoever is editing it: “Being edited by …: it opens read
only”. Opening it, the form says “… is editing it: here you see it as it's
saved now.”

- **When the other person saves**, your form rereads itself: the changed fields
  carry the “updated” mark, and at the bottom you read “… saved at …: the new
  version is already here.”;
- **when the other person closes it**, “… let it go.” appears, with **Edit
  now**: the form stays as it is until you ask;
- **if you need it right away**, and you have the “Remove someone else's
  reservation” permission, there is **Take the hold away**. It asks for
  confirmation — “Their form stops saving, and whatever they haven't saved yet
  is lost. The book passes to you.” — and the button is **Take it and edit**.

**The hold renews itself** as long as the form is open, and **runs out after two
minutes** in which the service no longer hears from that computer: a closed
laptop or a dropped network do not lock a book forever. Whoever loses the hold —
run out, or taken by someone else — is told so in their form, which from then on
**does not save any more**; what they wrote stays there until they close it, in
case they want to copy it, and **Throw the changes away** closes it.

The hold belongs to the computer, not to the person: the same book opened by you
on two different computers shows as “being edited” on the second.

## Other people's changes, live

What others do reaches you by itself: the catalogue, series, publishers, loans
and the purchase list **reread themselves without you doing anything**, without
a notice. If the connection drops for a moment, the app rereads everything when
it comes back.

## My loans

**My loans…**, from the menu with your name, shows the books you took from the
library, as the desk recorded them: first the ones to return, then the closed
ones. Anyone who has signed in sees it, with no separate permission, and it
shows **only yours**. The desk marks a book as returned when you bring it back.

For it to work, your user must be linked to your person in the loan register.
If it is not, the window says “You are not in the loan register yet”: whoever
manages the users links you, from **Users and groups**.

## My readings

With the service **everyone has their own readings**. A book's reading status —
To read, Reading, Read, Dropped — is **yours**: the catalogue's “Read” column,
the filter, the sort order and the read books counted in the publishers all
speak of your readings. **Nobody sees anyone else's**, not even an
administrator, and the status can be changed by a reader too.

- You change it by clicking the catalogue's **Read** cell, which opens a menu,
  or in the book's form, where it is saved right away, without “Save” — even
  when the book is read only;
- **Dropped** is a book started and put aside;
- the dates write themselves — when you start it, when you finish or drop it —
  and are corrected in the form's **My readings** strip, which lists every time
  you read it;
- **Read again**, on a book read or dropped, starts a new reading without
  deleting the others;
- going back to **To read** from a finished book asks for confirmation, because
  it deletes your record for that book. The others do not lose theirs.

Readings do not go into the [activity log](The-activity-log.md).

## The signed log

With the service, every row of the [activity log](The-activity-log.md) says
**who** took the action, in a “Who” column, with the name they signed in with.
The log can be seen with the “See the history” permission, and only when it is
on.

## When the service does not answer

If the service is off, or the network does not reach it, in place of the pages
**“The catalogue on the service will not open”** appears, even with work under
way. **Nothing has been deleted.** When the service is back, **Try again**;
**Use the catalogue on this computer** opens the catalogue you have here
instead, which is another catalogue.

If it is the session that has ended — run out, or closed by whoever runs the
service — **“The service asks you to sign in”** appears, with **Sign in**.

And if the app and the service are not the **same version**, they do not talk:
“The service is at version … and this program at another: update whichever of
the two is behind.” Usually it is the app's turn: update it as
[Updates](Updates.md) says, or ask whoever runs the service.
