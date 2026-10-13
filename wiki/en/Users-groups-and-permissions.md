[Italiano](../it/Utenti-gruppi-e-permessi.md) · **English**

# Users, groups and permissions

With the catalogue on the [library's service](Installing-the-service.md),
everyone signs in with their own name, and every action — adding a book,
lending it, taking a backup — asks for its own **permission**. Permissions are
given through **groups**, and whoever runs the service decides who is in which
group.

This page is for whoever manages the users. How you sign in is told in
[Ways to sign in](Ways-to-sign-in.md); what someone who works on the catalogue
without being an administrator sees is told in
[Working in a library](Working-in-a-library.md).

**All of this only holds with the service.** On this computer and on a database
of yours there are no users and no permissions: whoever opens the program can do
everything.

## The administrator

The service's first user is the **administrator**: it is born with the setup
code, as [Ways to sign in](Ways-to-sign-in.md#the-first-administrator) says.
The administrator has **every permission**, including the ones future versions
will bring, and does not depend on groups.

There can be more than one administrator: in a user's details the
**Administrator** box makes them one. Two limits:

- **the last active administrator cannot be disabled and cannot lose the box**:
  make another one first;
- **whoever signs in through the domain, a sign-in provider or Kerberos does not
  become an administrator.** That takes a user with the service's own password.

## The “Users and groups” dialog

Your name, in the top bar, opens a menu; in it is **Users and groups…**, which
shows for administrators and for whoever has the “Manage users” permission.

The dialog has two sides, **Users** and **Groups**; only an administrator sees
the second. At the bottom a line reminds you: “Every change applies at once, on
every connected computer.”

In the list of users, next to the names, you may see **Administrator**,
**Disabled**, **you** and **waiting for the first sign-in** — the last one for
someone added from the domain who has not signed in yet.

### A new user

**New user** opens a dialog that asks for the name, then the **Password** and
**Repeat the password**: at least eight characters. The service sends no
messages, so you give the name and password to the person yourself. The button
is **Create the user**.

With Active Directory on, the dialog starts with **How they sign in**:

- **With a password** — the road above;
- **From the domain** — you write only the **Domain account**, and the button is
  **Add from the domain**. The password is the domain's, and none is chosen
  here. Display name and groups come from the domain at the first sign-in;
  until then the user stays “waiting for the first sign-in”. This also holds for
  those who sign in with Kerberos.

Whoever signs in through a sign-in provider (OIDC) is not added: they are
created by themselves at the first sign-in.

An administrator also ticks the new user's **groups**. With no group ticked, the
user joins the **Lettore** group (the readers) and sees only the catalogue.

### A user's details

Clicking a user opens their details:

- **Display name** — the one shown in the bar and in the lists, with **Save**.
  The name used to sign in, instead, **does not change**, and it is the one the
  log signs with. For someone from the domain or a provider, the display name
  comes from there, and is updated at every sign-in;
- **Reset password** — only for those who sign in with the service's password:
  choose the **New password**, **Repeat it** and press **Reset**. That person's
  open sessions are closed, and they sign in again with the new password;
- **Disable** — the user can no longer sign in, and their sessions are closed at
  once. Groups and permissions stay as they were, and apply again with **Enable
  again**, which lets them back in with their old password;
- **Sessions** — one for each computer they signed in from, with the last use
  and when it expires. **Close the session** signs that computer out: at its
  next action it is asked to sign in again. **Close all** closes them all;
- **In the loan register** — see below;
- **Administrator**, **Groups** and **Extra permissions** — only an
  administrator changes them.

**Users are not deleted**: they are disabled. The rows of the
[activity log](The-activity-log.md) they signed keep their name.

### Linking a user to a person in the loans

The service's users and the people in the [loan register](Loans.md) are two
different lists. In a user's details, **In the loan register** has **Link to a
person…**: you look the person up by first or last name — those with the same
name as the user come first — and press **Link**. **Unlink** removes the link.

From then on the user, in **My loans**, sees that person's loans and only
theirs. A person belongs to one user only: if they already belong to someone
else, unlink them from that user first.

## Groups

A user has **the sum of their groups' permissions**. Whoever is left without
groups goes back to the **Lettore** group, the one of whoever is in no other: so
it can be renamed but not deleted.

The service is born with three groups. Their names are data, written in Italian,
and stay the same whatever the language of the program:

- **Redattore** (editor) — whoever catalogues: books, series, publishers,
  dictionaries, the purchase list, the log, backup and export;
- **Bancone** (desk) — whoever lends: loans, returns and people, with their
  contacts;
- **Lettore** (reader) — sees the catalogue, and nothing else.

**Administrator is not a group**: it is a user's box, and in the matrix it is a
fixed column that has everything.

The **Groups** side of the dialog is a **matrix**: one row per permission, one
column per group, and a box to switch on or off at every crossing. Only an
administrator sees it and changes it.

- **New group** creates one with no permissions, as the last column;
- a group's menu has **Rename…**, **Delete the group…** — whoever was in it
  leaves and keeps the permissions of their other groups, and whoever is left
  with none goes back to Lettore —, **Active Directory group…** and **Keycloak
  group…** (with the provider's name), which tie it to a group of the domain or
  of the provider. Whoever signs in from there gets their groups that way, at
  every sign-in, and they cannot be changed in their details.

The three starting groups are born once, with the service: a deleted one does
not come back.

## All the permissions

| Permission | Redattore | Bancone | Lettore |
|---|:-:|:-:|:-:|
| See the catalogue | ✓ | ✓ | ✓ |
| Add books | ✓ | | |
| Edit books | ✓ | | |
| Delete books | ✓ | | |
| Import from a spreadsheet | ✓ | | |
| Remove someone else's reservation | | | |
| Create and edit series | ✓ | | |
| Delete series | ✓ | | |
| Merge publishers and remove aliases | ✓ | | |
| Rename, merge and delete dictionary entries | ✓ | | |
| See loans | ✓ | ✓ | |
| Lend a book | | ✓ | |
| Record a return | | ✓ | |
| Forget a person | | ✓ | |
| See people's email and phone | | ✓ | |
| See the purchase list | ✓ | ✓ | |
| Edit the purchase list | ✓ | | |
| See the history | ✓ | | |
| Turn the history on and off | | | |
| Manage users | | | |
| Back up the catalogue | ✓ | | |
| Export the catalogue | ✓ | | |
| Restore an archive | | | |
| Bring a catalogue to the service | | | |
| Move the covers | | | |

The administrator has them all. Three notes:

- **“See people's email and phone”** opens no action: whoever lacks it sees the
  people in the register without their contacts, and the service does not even
  send them;
- **“Move the covers”** sits under “Coming later”: it exists, but no action asks
  for it yet;
- **“Back up the catalogue”** also covers seeing the copies the service keeps
  and downloading one. Restore and “Bring a catalogue to the service” are in no
  starting group: out of the box only an administrator does them. How they work
  is in [Backup and restore](Backup-and-restore.md).

### Extra permissions

In a user's details, **Extra permissions** gives that user alone a permission
their groups do not have. It is **only on top**: nothing is taken away here, and
a permission that comes from a group shows on and locked, with “from group …”.
To take it away you change the matrix, or the user's groups.

## Managing users without being an administrator

The **Manage users** permission can be given to someone who is not an
administrator too. That person sees the dialog, but only its **Users** side, and
with some limits:

- **they create only readers**: a new user, with a password or from the domain,
  with no groups and no extra permissions;
- **they do not change groups, permissions or the Administrator box**: “Only an
  administrator changes groups and permissions.”;
- **they do not act on an administrator**: “Only an administrator acts on an
  administrator.”;
- **they act only on those who cannot do more than they can.** Resetting the
  password, changing the display name, disabling, enabling again and closing
  sessions succeed only on a user whose permissions are all within theirs.
  Otherwise the service answers: “This user can do things yours cannot: an
  administrator manages them, or someone with at least their permissions.”

That way nobody, while managing users, gets a foothold in someone else's
permissions.
