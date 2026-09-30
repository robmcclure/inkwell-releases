# Testing Inkwell on Windows

Thanks for trying this. Inkwell is a personal project — one person's fountain pen tracker, not a
product — and **this is the first Windows build that has ever run.** Everything up to now has been
Mac-only, so you're likely to find things nobody has seen.

That makes you useful. Be blunt about anything that looks wrong.

The full user guide is inside the app, under **Help**.

---

## Installing

Download it from **github.com/robmcclure/inkwell-releases** and run the installer
(`Inkwell-Setup-windows-x64.exe`).

**Windows will try to stop you.** You'll get a blue "Windows protected your PC" screen. Click
**More info**, then **Run anyway**.

That's expected and it isn't a judgement about the app. SmartScreen warns about any installer
without a code-signing certificate, which costs a few hundred a year and needs a hardware token —
not yet worth it for a handful of testers. The Mac version is signed and notarized; Windows just
hasn't got there.

If you'd rather not click through that, don't. It's a reasonable thing to refuse.

It installs for your user account only, so there's no administrator prompt, and it puts shortcuts
on the desktop and in the Start menu.

---

## Before you start

**Your collection stays on your machine.** No account, no server, nothing sent anywhere. The
database is a single file, and it *should* be at:

```
%APPDATA%\Inkwell\data.db
```

Paste that path into Explorer's address bar to find it.

**Worth checking that it really is there**, once you've opened the app. That location comes from a
line of code that has never been watched running on Windows: it asks the system for `%APPDATA%`
and adds `Inkwell`. If the folder can't be created for any reason, the code falls back to whatever
directory the app happened to start in — which would be a poor place for a database, and nothing
would tell you it had happened.

So: open `%APPDATA%\Inkwell` after the app has run once. You should see `data.db`, plus
`data.db-shm` and `data.db-wal` alongside it while the app is open. If that folder is empty or
missing, please say — it means the backup advice below, and the uninstall instructions at the end,
are both pointing at the wrong place.

**Back up anything you care about.** This is early software with no undo. If you're entering real
pens, set a backups folder on the Settings page first.

---

## What's missing on Windows, by design

Two features are macOS-only, and the app hides them rather than offering something broken:

- **Apple Mail import.** The Import page won't show that tab. Everything else there works —
  **Email File** takes a saved `.eml` (or `.mbox`), and **Paste Text** takes a message's text or
  raw source. Both parse identically to the Mac version. If you use classic Outlook, it saves
  messages only as `.msg`, which Inkwell can't read — use Paste Text instead. The new Outlook for
  Windows and Outlook on the web save `.eml`, so Email File works with them.
- **The Choose… folder buttons** on Settings and Export. You type or paste a folder path instead.
  If that's awkward, say so — it's fixable, just not yet done.

**Updates install themselves**, as on the Mac. Inkwell checks for a newer version while it's
running, downloads it in the background, and installs it when you quit — or straight away from
Settings → Updates. Your collection isn't touched by an update. This is new on Windows: if an
update fails, shows an error in Settings, or asks you anything unexpected (a SmartScreen warning,
say), please report it.

**Some PDF invoices can't be read**, on any platform. A few invoicing systems save their text in a
way that loses the characters — readable on screen, but nothing underneath for a program to
extract. Inkwell says so rather than quietly finding nothing. Copy the text out of your PDF reader
and use the **Paste Text** tab instead.

---

## What's most useful to report

This build has never run on Windows before you, so the bar is low — anything odd is worth
mentioning.

Particularly:

1. **Anything that stops you.** A crash, a page that won't load, a save that doesn't save. Most
   valuable of all: **the app failing to start**, or your collection not loading — that would mean
   the database engine isn't working on Windows, which nothing here can work around.
2. **The database landing somewhere other than `%APPDATA%\Inkwell`** — see above. Quiet, and it
   makes several other things wrong.
3. **Anything that looks wrong rather than broken.** Cut-off text, overlapping controls, the wrong
   font, a window that opens too small. The layout has only ever been seen on a Mac.
4. **An invoice that imports wrongly.** Tell me the retailer and what it got wrong; attach the
   saved `.eml` or PDF if you can, after checking it for anything you'd rather not share.
5. **Anything that made you hesitate** — a label you had to re-read, a button that didn't do what
   you expected.

### What to include

- **The version and build**, shown at the top of the Collection page — something like
  `Inkwell v1.63.0 · 18 Sep 2026 · a3f9c21`. Quote the whole line. (**About** in the sidebar shows
  the same thing.)
- **What you did**, in enough detail to try the same thing.
- **What happened**, and what you expected instead.

### Where to send it

Email **hello@inkwell-the-app.com**. The easiest way is **About → Send feedback** in the app, which opens
your own email app with the version line already filled in; nothing is sent until you send it.

Please don't use GitHub for reports: anything posted there is public, and an invoice carries your
name and address.

### Please don't send your database

`data.db` holds your whole collection, including anything you paid. It isn't needed. If a bug
seems to depend on your data, say so and we'll find a narrower way to reproduce it.

---

## Getting rid of it

Uninstall from Settings → Apps, or the Start menu entry. Your collection stays behind in
`%APPDATA%\Inkwell\` until you delete that folder too — deliberately, so reinstalling loses
nothing. Delete the folder if you want it properly gone.
