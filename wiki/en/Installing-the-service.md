[Italiano](../it/Installare-il-servizio.md) · **English**

# Installing the service

The **library's service** is a separate program, with no window, that keeps
the catalogue on one of the library's computers and answers the other
computers on the network, where the app runs. Everyone signs in with their own
name and password, and whoever runs the service decides what each one can do.
How the app connects is told in [Where the data lives](Where-the-data-lives.md#with-the-librarys-service);
this page tells how to set the service up.

If you use the catalogue on your own, you do not need the service: the app is
enough, [installed as usual](Installation.md).

## Before you start

- **A computer that stays on**, so the others can reach it: a 64-bit Windows
  PC, a Mac (Intel or Apple Silicon), a Linux server with systemd (amd64 or
  arm64), or Docker. The app is not needed on the service's computer.
- **The same version of the app.** The service and the app only talk to each
  other when they come from the same release: an app newer or older than the
  service is told “The service is at version … and this program at another”.
  When you update one, update the other too.
- **Where to keep the catalogue.** Out of the box the service keeps it in a
  file in its data folder, and nothing else needs installing. If the library
  already has a database — **PostgreSQL**, **MySQL**, **SQL Server** or
  **MongoDB** started as a replica set — the catalogue can live there: the
  rules are those of [The catalogue on a server](The-catalogue-on-a-server.md).
- **Port 7878** reachable from the other computers. It is the default, and it
  can be changed.

The files are on the [latest release
page](https://github.com/alexkill536ita/gestionale-libreria/releases/latest),
next to the app's.

## On Windows

The file is `Gestionale Libreria Servizio_0.7.5_x64-setup.exe`. It asks for
administrator rights, because it installs a Windows service; and as with the
app, **SmartScreen** warns that the program is not signed: **More info** →
**Run anyway**.

At start the installer asks for its language, Italian or English, proposing
the one of Windows. Its pages are four:

1. **The program folder**, by default `C:\Program Files\Gestionale Libreria
   Servizio`.
2. **Service configuration**. The proposed **Listening address** is
   `0.0.0.0:7878`, which answers the whole library network; `127.0.0.1:7878`
   answers this computer only. Below it you choose **Where the catalogue
   lives**: **On this computer**, a file in the data folder with the covers
   next to it, or **On a database**.
3. Only with **On a database**, two more pages: **The catalogue's database** —
   engine, host, port, database name, user, password and **Encrypted connection
   (TLS)**, with **Test the connection** to know right away whether it answers —
   and **The covers**: **Inside the database**, **In a folder** or **In an S3
   archive**. The proposed folder is `covers` in the data folder, and another
   one can be chosen. A network folder must give write permission to the
   `NT SERVICE\GestionaleLibreria` account, or the covers are not saved.
4. **The service has started**. The last page shows the address to type into
   the app — `https://COMPUTER-NAME:7878`, with this computer's IP addresses —
   the **Setup code** and the **Certificate fingerprint**, each with its
   **Copy** button. Keep them at hand: they are needed for the first
   connection.

What stays on the computer:

| | |
|---|---|
| the Windows service | `GestionaleLibreria` (“Gestionale Libreria - Servizio” in **Services**), which starts with the computer even when nobody is signed in, and runs as the `NT SERVICE\GestionaleLibreria` account |
| the data folder | `C:\ProgramData\Gestionale Libreria\servizio`, open only to SYSTEM, the administrators and the service: inside are `servizio.json`, the catalogue, the covers, the users, the certificate and the log `servizio.log` |
| the firewall | a “Gestionale Libreria Servizio” rule that opens the port on **Private** and **Domain** networks, not on public ones |

If the service does not start, the last page says so and shows the log, with
**Open the log**.

## On a Mac

The file is `Gestionale Libreria Servizio_0.7.5_universal.pkg`, a single one for
Intel Macs and Apple Silicon ones. Like the app, **it is not signed**: macOS
says it cannot be verified, and you go through **System Settings → Privacy &
Security → Open Anyway**.

The package:

- puts the program in `/usr/local/bin/gestionale-libreria-servizio`;
- creates the system user `_gestionalelibreria`, hidden and unable to sign in,
  which is the only one that reads the data folder;
- keeps the data in `/Library/Application Support/Gestionale Libreria/servizio`;
- starts the service right away and at every boot of the Mac, as the
  LaunchDaemon `it.alexkill536ita.gestionale-libreria.servizio`, listening on
  `0.0.0.0:7878`.

The catalogue starts as a file in the data folder; to keep it on a database you
edit `servizio.json`, as told [further down](#the-serviziojson-file). The last
page of the installer sums up the commands you need, the same ones as here.

The **setup code**, from the Terminal:

```
sudo cat "/Library/Application Support/Gestionale Libreria/servizio/codice-di-configurazione.txt"
```

The **certificate fingerprint**:

```
sudo -u _gestionalelibreria /usr/local/bin/gestionale-libreria-servizio --impronta
```

The **address** to type into the app is `https://NAME.local:7878`, where `NAME`
is what `scutil --get LocalHostName` answers; the Mac's IP address works too.

If the **macOS firewall** is on, incoming connections have to be allowed by
hand, because the service has no window to ask from:

```
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add /usr/local/bin/gestionale-libreria-servizio
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblockapp /usr/local/bin/gestionale-libreria-servizio
```

After changing `servizio.json`, the service is restarted with:

```
sudo launchctl kickstart -k system/it.alexkill536ita.gestionale-libreria.servizio
```

## On Linux

On **Debian and Ubuntu** there is a `.deb` package:
`gestionale-libreria-servizio_0.7.5_amd64.deb` for PCs and
`gestionale-libreria-servizio_0.7.5_arm64.deb` for ARM servers (a 64-bit
Raspberry Pi, for instance).

```
sudo apt install ./gestionale-libreria-servizio_0.7.5_amd64.deb
```

The package creates the system user `gestionale-libreria`, the data folder
`/var/lib/gestionale-libreria` open only to that user, a `servizio.json`
listening on `0.0.0.0:7878`, and turns on the systemd unit
`gestionale-libreria-servizio`, which starts on its own at every boot. **It does
not touch the firewall**: if there is one, port `7878/tcp` has to be opened by
hand.

For **other distributions with systemd** there is an archive,
`gestionale-libreria-servizio_0.7.5_linux-x86_64.tar.gz` or
`gestionale-libreria-servizio_0.7.5_linux-aarch64.tar.gz`. Inside are the
program, the systemd unit and `README.txt` (in Italian `LEGGIMI.txt`), with the
steps to do by hand: they are the same ones the `.deb` does by itself. The
program needs OpenSSL 3 and a glibc at least as recent as Ubuntu 22.04's.

The commands you need afterwards:

```
sudo cat /var/lib/gestionale-libreria/codice-di-configurazione.txt
sudo -u gestionale-libreria gestionale-libreria-servizio --impronta
sudo systemctl restart gestionale-libreria-servizio
journalctl -u gestionale-libreria-servizio
```

The program's commands are always given **as the service's user**
(`sudo -u gestionale-libreria …`): run as root, the files they write in the
data folder would belong to root, and the service could not open them.

## With Docker

There is no ready-made image: there is this `Dockerfile`, which downloads the
version's Linux archive from the release. Copy it into an empty folder.

```dockerfile
FROM debian:bookworm-slim

ARG VERSIONE=0.7.5
ARG ARCH=x86_64

RUN apt-get update \
 && apt-get install -y --no-install-recommends ca-certificates curl libssl3 libgssapi-krb5-2 \
 && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL "https://github.com/alexkill536ita/gestionale-libreria/releases/download/v${VERSIONE}/gestionale-libreria-servizio_${VERSIONE}_linux-${ARCH}.tar.gz" \
      | tar -xz -C /tmp \
 && install -m 0755 "/tmp/gestionale-libreria-servizio_${VERSIONE}_linux-${ARCH}/gestionale-libreria-servizio" /usr/local/bin/ \
 && rm -rf /tmp/gestionale-libreria-servizio_*

RUN useradd --system --user-group --no-create-home \
      --home-dir /var/lib/gestionale-libreria --shell /usr/sbin/nologin gestionale-libreria \
 && install -d -m 0750 -o gestionale-libreria -g gestionale-libreria /var/lib/gestionale-libreria

VOLUME /var/lib/gestionale-libreria
ENV GESTIONALE_LIBRERIA_ASCOLTA=0.0.0.0:7878
EXPOSE 7878
USER gestionale-libreria
ENTRYPOINT ["gestionale-libreria-servizio"]
```

`VERSIONE` is the version. On an ARM server the archive is a different one:
build with `--build-arg ARCH=aarch64`.

```
docker build -t gestionale-libreria-servizio .
docker run -d --name biblioteca --restart unless-stopped --stop-timeout 15 \
  -v biblioteca-dati:/var/lib/gestionale-libreria \
  -p 7878:7878 gestionale-libreria-servizio
```

The data lives in the `biblioteca-dati` **volume**, and outlives the
container: catalogue, users and above all the certificate, whose fingerprint
the connected computers remember. Use a named volume and not a folder of the
host: the service runs as a user of its own, and a host folder would usually
not let it write. `--stop-timeout 15` gives the service the time to finish
what it is doing before it stops: without it, Docker kills it after a few
seconds.

Setup code and fingerprint:

```
docker exec biblioteca cat /var/lib/gestionale-libreria/codice-di-configurazione.txt
docker exec biblioteca gestionale-libreria-servizio --impronta
```

`docker logs biblioteca` prints them too, at startup.

The address to type into the app is the one of the computer running Docker,
with the published port: `https://192.168.1.20:7878`, for instance.

Without `servizio.json` the catalogue is a file in the volume. For a database,
the file is written inside the volume and the container restarted:

```
docker exec -i biblioteca sh -c 'cat > /var/lib/gestionale-libreria/servizio.json' < servizio.json
docker restart biblioteca
```

The database password can stay out of the file, in a variable:
`-e GESTIONALE_LIBRERIA_PASSWORD=…` on `docker run`.

## The `servizio.json` file

The service reads its configuration from `servizio.json`, in the data folder.
The keys are three:

| | |
|---|---|
| `ascolta` | where it answers: `0.0.0.0:7878` for the whole network, `127.0.0.1:7878` for that computer only. Without it, it is the latter |
| `database` | where the catalogue lives. Without it, it is a file in the data folder, with the covers next to it |
| `dati` | another data folder; usually not needed |

Here is a catalogue on the library's PostgreSQL, with the covers in S3
storage:

```json
{
  "ascolta": "0.0.0.0:7878",
  "database": {
    "motore": "postgres",
    "host": "db.biblioteca.lan",
    "porta": 5432,
    "database": "libreria",
    "utente": "libreria",
    "password": "the-database-password",
    "tls": true,
    "copertine": "in_un_archivio",
    "archivio_indirizzo": "https://s3.eu-central-1.amazonaws.com",
    "archivio_contenitore": "copertine-biblioteca",
    "archivio_regione": "eu-central-1",
    "archivio_chiave": "the-access-key",
    "archivio_segreto": "the-secret"
  }
}
```

- `motore` (engine) is one of `postgres`, `mysql`, `sqlserver` and `mongodb`.
  MongoDB also has `database_autenticazione`, the database where the user is
  defined (by default `admin`).
- `copertine` (covers) is `nel_database`, `in_una_cartella` — with
  `cartella_copertine`, the path as the service's computer sees it — or
  `in_un_archivio`, with the five `archivio_*` fields; the region can be left
  out.
- The covers' place counts **when the catalogue does not have one yet**: a
  catalogue that has already decided where its covers live remembers it, and
  the storage's key and secret are always read from here. If the file names a
  different place, `servizio.log` says so at startup and the covers stay where the
  catalogue says.
- **The password** can stay in the file, which only the service and the
  administrators read, or in the `GESTIONALE_LIBRERIA_PASSWORD` environment
  variable. The listening address can be given with a variable too,
  `GESTIONALE_LIBRERIA_ASCOLTA`, which wins over the file.

An empty database is fine: the service installs the catalogue there by itself
at the first start. To know whether the connection works **before** restarting
the service, there is the `--prova` option, which tries the database of
`servizio.json`, says in one line how it went and exits:

```
sudo -u gestionale-libreria gestionale-libreria-servizio --prova
```

(on Windows, from a PowerShell opened as administrator:
`& "C:\Program Files\Gestionale Libreria Servizio\gestionale-libreria-servizio.exe" --prova`).

After every change the service has to be **restarted**: from **Services** on
Windows, with `launchctl kickstart -k` on a Mac, with `systemctl restart` on
Linux, with `docker restart` on Docker.

## Connecting the app

On every computer of the library, in the app:

1. **Settings → Database**, in the **In a library** group: **With the
   library's service**.
2. In the **Address** field type the service's, always with `https://` and the
   port: `https://192.168.1.20:7878`.
3. The first time, the app shows the **Fingerprint of the service**. Compare it
   with the one from the installation, or with the one `--impronta` prints: if
   they are the same, press **I trust it**. If they are not, do not trust it —
   someone is in the middle — and if the app says that “a program on this
   computer reads the connection”, it is usually an antivirus with HTTPS
   scanning on.
4. The **first** computer that connects creates the first administrator: the
   dialog asks for the **Setup code**, then a name and a password. The code
   works only once. The other computers sign in with their own name and
   password.

The details — a fingerprint that changes, the session, what you can do with
the catalogue on the service — are in [Where the data lives](Where-the-data-lives.md#with-the-librarys-service).

## Updating

**You install over the old one**, with the new version's file, and the
configuration stays as it is.

- **Windows**: the new installer recognises the previous one, skips the
  configuration pages and does not touch `servizio.json`.
- **Mac**: open the new `.pkg`; the data and `servizio.json` stay.
- **Debian and Ubuntu**: the same `sudo apt install`, with the new `.deb`; the
  service restarts on its own.
- **Linux archive**: stop the service, replace the program in `/usr/bin` and
  start it again.
- **Docker**: change `ARG VERSIONE` in the `Dockerfile` (or pass
  `--build-arg VERSIONE=…`), rebuild the image and recreate the container with
  the **same volume**.

Remember to update **the app too** on the library's computers, or they no
longer connect.

## Uninstalling

The data folder is deleted only if you ask: otherwise catalogue, users and
certificate stay, and a reinstalled service finds them as they were.

- **Windows**: from **Settings → Apps → Installed apps**, entry “Gestionale
  Libreria - Servizio”. The service, the firewall rule and the program go away,
  and before starting it asks whether to delete
  `C:\ProgramData\Gestionale Libreria\servizio` too; the proposed answer is
  “No”. Once deleted it cannot be recovered, and the connected computers will
  have to confirm the fingerprint of a new service. If the covers are in a
  folder chosen outside it, the question names it and “Yes” also deletes the
  images inside; subfolders and other files stay, and the folder goes only if
  it is left empty. A silent uninstall (`/S`) never deletes any of this.
- **Mac**:

  ```
  sudo /usr/local/share/gestionale-libreria-servizio/disinstalla.sh
  ```

  At the end it also says how to remove the data folder and the
  `_gestionalelibreria` user.
- **Debian and Ubuntu**: `sudo apt remove gestionale-libreria-servizio`. To
  really remove data and user:
  `sudo rm -rf /var/lib/gestionale-libreria` and
  `sudo deluser --system gestionale-libreria`.
- **Linux archive**: the steps are at the bottom of `README.txt`.
- **Docker**: `docker rm -f biblioteca`; the data stays in the volume until you
  remove it with `docker volume rm biblioteca-dati`.

## A lost code, or the administrator's password

The setup code is born at every start **as long as there are no users**. If the
administrator has lost the password, a new code is made on the service's
machine with the `--nuovo-codice` option: the program writes it in
`codice-di-configurazione.txt`, prints it and exits, without stopping the
service that is running.

```
sudo -u gestionale-libreria gestionale-libreria-servizio --nuovo-codice                                  # Linux
sudo -u _gestionalelibreria /usr/local/bin/gestionale-libreria-servizio --nuovo-codice                   # Mac
docker exec biblioteca gestionale-libreria-servizio --nuovo-codice                                       # Docker
```

On Windows, from a PowerShell opened as administrator:

```
& "C:\Program Files\Gestionale Libreria Servizio\gestionale-libreria-servizio.exe" --nuovo-codice
```

Then, in the app, create the administrator with that code: with the **name that
was there** it becomes administrator again with the new password, with a new
name an extra administrator is born.

## If it does not start

The service writes what it does in `servizio.log`, in its data folder, and at
every start it writes the fingerprint there too.

| | |
|---|---|
| Windows | `C:\ProgramData\Gestionale Libreria\servizio\servizio.log`, to be opened as administrator |
| Mac | `servizio.log` in the data folder; what it says before opening it — a `servizio.json` that cannot be read, for instance — is in `/Library/Logs/Gestionale Libreria/servizio.log` |
| Linux | `journalctl -u gestionale-libreria-servizio`, and `servizio.log` in `/var/lib/gestionale-libreria` |
| Docker | `docker logs biblioteca` |

The most common causes:

- **the database does not answer**, or user and password are wrong: `--prova`
  says so without starting anything;
- **the port is already used** by another program: change `ascolta` in
  `servizio.json`;
- **`servizio.json` cannot be read**: a comma too many, or a misspelt key;
- **the other computers do not reach it**, but the service's computer does: it
  is the firewall, or `ascolta` says `127.0.0.1`.
