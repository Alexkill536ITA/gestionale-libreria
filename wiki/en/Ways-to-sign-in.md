[Italiano](../it/I-modi-di-entrare.md) · **English**

# Ways to sign in

With the catalogue on the [library's service](Installing-the-service.md),
everyone signs in with their own name, and the service knows who they are and
what they may do. There are four ways to sign in: **the service's password**,
**Active Directory**, **an OIDC sign-in provider** (Keycloak, for example) and
**Kerberos**. Which ones are on is decided by whoever runs the service, in its
`servizio.json` file; out of the box only the password is.

Whatever the way, what you can do afterwards does not change: that is set by
groups and permissions, told in
[Users, groups and permissions](Users-groups-and-permissions.md).

## With the service's password

This is the starting way. When the catalogue is on the service and this
computer has not signed in yet, the **Sign in to the service** dialog opens by
itself, with the address and the confirmed fingerprint at the top, **Name** and
**Password**, and the **Sign in** button. Whoever runs the service gives you the
name and password.

### The first administrator

A freshly installed service has no users, and then the dialog is **Create the
first administrator**: it asks for the **Setup code**, then **Name**,
**Password** and **Repeat the password**, and the button is **Create the
administrator**. The password needs at least eight characters.

The service writes the code in the file `codice-di-configurazione.txt`, in its
data folder, and in its log at startup; on Windows the last page of the
installation shows it too. It is twelve letters and digits, without the ones
that get confused (0 and O, 1, I and L), and **it works only once**: once the
administrator exists, the file is gone.

Whoever lost the administrator's password makes a new code on the service's
machine with the `--nuovo-codice` option — the commands for each system are in
[Installing the service](Installing-the-service.md#a-lost-code-or-the-administrators-password).
With that code you go back to the dialog: with the **name that was there**, that
user becomes administrator again with the new password; with a new name, one
more administrator is born.

## With Active Directory

The service asks the domain whether the name and password are right, over an
encrypted **LDAPS** connection: the domain password never travels in clear, and
the service does not keep it.

The dialog becomes **Domain account** and **Domain password**. The account is
written as `name`, or with the domain in front: `BIBLIO\name`.

**Being in the domain is not enough: you have to have been added.** An
administrator creates the user from **Users and groups → New user**, chooses
**From the domain** and presses **Add from the domain**, writing only the
account: the password is the domain's, and none is chosen here. Until the first
sign-in the user stays “waiting for the first sign-in”; when they sign in, the
service takes the **display name** and the **groups** from the domain. Someone
the domain recognises but nobody has added gets the same answer as a wrong
password.

**Groups come from the domain, at every sign-in.** In the groups matrix, a
group's menu has **Active Directory group…**, which ties it to a domain group;
nested groups count too. Whoever is in no tied group signs in as a **Reader**,
and a notice tells them: “You are signed in as a Reader”.

If the domain does not answer, administrators have **Sign in as an administrator
of the service**: their service password, which does not go through the domain.

A domain password that has expired, or that the domain wants changed, is
changed in Windows — Ctrl+Alt+Del and “Change a password” — and then you sign in
with the new one.

> **Not yet tested on a real machine.** Active Directory has been tested only
> against a Samba domain. On a real Windows domain three things are still
> missing: channel binding, LDAP signing enforced by the domain, and
> certificates handed out by group policy; and the expired-password message has
> only been seen by the tests.

## With a sign-in provider (OIDC)

If the library already has a sign-in provider — Keycloak, or another that
speaks OIDC — you sign in from there. The dialog shows **Sign in with Keycloak**
(or with the provider's name the service declares), with “This computer's
browser will open.” below it.

Once pressed, the provider's page opens in the **system browser**, and the
dialog becomes **Continue in the browser**. You sign in there, as you always do
with that provider; when you are done, the app notices by itself and the dialog
closes. If you cannot see the page:

- **Reopen the browser** opens it again;
- **Copy the address** copies it, to paste by hand into the browser you want;
- **Cancel**, or Esc, stops everything.

The attempt stays open for **five minutes**: after that you start again from
“Sign in”. **Sign in with another name** makes the provider ask for the
credentials again, when the browser already remembers someone.

**Here nobody needs to be added**: the user is created by itself at the first
sign-in. Groups come from the provider at every sign-in, and in the matrix they
are tied with **Keycloak group…** (with the provider's name). Whoever is in no
tied group signs in as a **Reader**.

## With Kerberos

On a computer in the domain, Windows already knows who you are: with Kerberos on,
the dialog shows the **Windows account** you opened the session with,
“verified”, and the **Sign in as …** button with your name. No password is
typed, but **you sign in with a click**, not by yourself. **Sign in with another
name** leads to the name and password fields; **Back to …** brings you back to
your account.

As with Active Directory, **the user must have been added** by an administrator
with **Add from the domain**, and the groups are the domain's tied in the
matrix. Someone who has not been added gets the same answer as a wrong password.

> **Not yet tested on a real machine.** Kerberos has never been run on a Windows
> computer inside a real domain, nor on a Mac: on the Mac the program builds,
> but nobody has signed in that way yet.

## Several ways together

The ways can be switched on together, and the dialog shows the ones that are on:
for example **Sign in with Keycloak**, “or”, and the name and password fields.

Two rules always hold:

- **the administrators' password always works**, even when the password is not
  among the ways: it is the emergency exit when the domain or the provider do
  not answer. In that case, though, it works **only for administrators**;
- **whoever signs in through the domain, a provider or Kerberos does not become
  an administrator.** That takes a user with the service's own password.

## The session

Once in, the session stays **on this computer**, in the system keychain
(Credential Manager on Windows, Keychain on a Mac) and not in
`impostazioni.json`. **Reopening the program you do not need to sign in
again**, as long as the session is alive.

| | ends |
|---|---|
| with the service's password | after **thirty days without use**: every action renews it |
| through the domain, a provider, Kerberos | **twelve hours after signing in**, even while you are using it |

It ends sooner if whoever runs the service closes it from **Users and groups**,
if your password is reset or if your user is disabled. Then the dialog opens
again by itself. Every computer has its own session: signing in again from the
same computer replaces the previous one.

**After five wrong attempts in a row** on the same name you have to wait: **a
minute** with the service's password, **a quarter of an hour** with a domain
name.

**The catalogue on this computer stays without sign-in**: names and passwords
only hold on the service.

### Signing out and changing the password

Your name, in the top bar, opens a menu. In it:

- **Sign out**, which ends the session on the service, forgets it on this
  computer — even if the service does not answer — and opens the dialog again;
- **Change password…**, only for those who sign in with the service's password:
  it asks for the **Current password** and the **New password**. Your sessions on
  other computers are closed, and there you sign in with the new one; this one
  stays open. A domain password, instead, is changed in the domain.

## The `accesso` block of `servizio.json`

This part is for whoever runs the service. The ways are switched on in the
`accesso` block of `servizio.json`, in the service's data folder — where it is
on each system is in [Installing the service](Installing-the-service.md#the-serviziojson-file).
**The installers do not write it**: out of the box it is missing, and only the
password holds. It is written by hand, and afterwards the service needs a
restart.

`modi` lists the ways that are on, among `password`, `ldap`, `oidc` and
`kerberos`; without it, `["password"]` holds. Every way that is on needs its
block, and a block without its way is refused. **A key the service does not
know makes it refuse the file**: the service does not start and the log says
which key, so a misspelt key does not pass in silence.

Active Directory, next to the password:

```json
{
  "ascolta": "0.0.0.0:7878",
  "accesso": {
    "modi": ["password", "ldap"],
    "ldap": {
      "indirizzo": "ldaps://dc1.biblio.local:636",
      "dominio": "BIBLIO",
      "ca": "ca-dominio.pem"
    }
  }
}
```

- `indirizzo` always starts with `ldaps://`: the service does not talk to the
  domain in clear;
- `dominio` is the domain's short name, the one written in front of the name;
- `ca` is the PEM file with the certificate that signed the domain
  controller's, in the same folder as `servizio.json`;
- `account_di_servizio` and `password_di_servizio` are optional: an account the
  service uses to look users up in the domain. Kerberos needs them.

An OIDC provider:

```json
{
  "accesso": {
    "modi": ["password", "oidc"],
    "oidc": {
      "issuer": "https://keycloak.biblio.local/realms/biblioteca",
      "client_id": "gestionale-libreria"
    }
  }
}
```

- `issuer` is the provider's address, in `https://`;
- `client_id` is the name the provider knows the service by;
- optional: `segreto` (if the provider asks for one), `ca` (if the provider's
  certificate is not from a public authority), `claim_dei_gruppi` (where the
  provider writes the groups; `groups` by default) and `fornitore`, the name the
  button shows (`Keycloak` by default).

Kerberos, which also needs the `ldap` block with the service account:

```json
{
  "accesso": {
    "modi": ["password", "kerberos"],
    "ldap": {
      "indirizzo": "ldaps://dc1.biblio.local:636",
      "dominio": "BIBLIO",
      "ca": "ca-dominio.pem",
      "account_di_servizio": "svc-gestionale",
      "password_di_servizio": "the-account-password"
    },
    "kerberos": {
      "realm": "BIBLIO.LOCAL",
      "keytab": "biblioteca.keytab"
    }
  }
}
```

- `realm` is the domain's Kerberos realm;
- `keytab` is the file with the service's keys; without it, the system's holds.
  On Windows, without a keytab, Windows itself checks the tickets;
- `principale` is optional: without it, every key in the keytab holds.

The secrets can stay out of the file, in three environment variables that, when
present, win over `servizio.json`:

| | |
|---|---|
| `GESTIONALE_LIBRERIA_SEGRETO_OIDC` | the OIDC provider's `segreto` |
| `GESTIONALE_LIBRERIA_PASSWORD_DI_SERVIZIO` | the domain's `password_di_servizio` |
| `GESTIONALE_LIBRERIA_KEYTAB` | the path of the `keytab` |

At startup the service's log says which ways you can sign in with, and whether
the password works only for administrators.

### Testing before restarting

The `--prova` option reads `servizio.json`, tests what is written there and
says in one line how it went, without starting to serve:

- the database, if there is one;
- with the `ldap` block, that the domain answers over LDAPS — and, if there is
  a service account, that the domain accepts it;
- with the `oidc` block, that the provider answers and introduces itself with
  the `issuer` written in the file;
- with the `kerberos` block, that the keytab can be read and holds the
  service's key for that realm.

The commands to run it on each system are in
[Installing the service](Installing-the-service.md#the-serviziojson-file).
