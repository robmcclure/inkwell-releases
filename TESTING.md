# Testing Inkwell

Thanks for trying this. Inkwell is a personal project — one person's fountain pen tracker, not a
product — so it's rough in places and I'd rather hear about that than not.

This page is short on purpose. The full user guide is inside the app, under **Help**.

---

## Before you start

**Download it from github.com/robmcclure/inkwell-releases**, open the download, and drag Inkwell
into Applications. It's signed and notarized by Apple, so it opens without warnings.

**You need an Apple Silicon Mac.** Builds are arm64 only at the moment. On an Intel Mac the app
won't launch, and that's a build target rather than a bug — tell me and I'll produce one.

**Your collection stays on your machine.** No account, no server, nothing sent anywhere. The
database is a single file at `~/Library/Application Support/Inkwell/data.db`.

**Back up anything you care about.** This is early software with no undo. If you're entering a
real collection, set a backups folder on the Settings page first — see the guide.

---

## Have a look around first

The app starts empty, and an empty collection tracker tells you very little. On the Collection
page there's a **Load a sample collection** button: five pens, six nibs and five inks, real
products with photos, so you can click through the whole app before deciding whether to type
anything in.

Once loaded, a banner sits at the top of the Collection page with a **Remove sample data** button.

**Remove it before you start entering real pens.** Not because anything breaks if you don't —
removing the samples only deletes the sample rows, never anything you added — but because a
collection that's half demonstration and half real is confusing to look at and harder for me to
reason about if you report something.

The load button only appears while the collection is completely empty, so the samples can't get
mixed into real data later on.

---

## Installing

Open the DMG and drag Inkwell to Applications, then launch it from there.

It's signed and notarized by Apple, so it should open without a warning. **If macOS says it can't
be opened or that the developer can't be verified, stop and tell me** — that means something is
wrong with the build, and it's exactly the kind of thing I can't test on my own machine.

---

## What will look alarming but isn't

**A permission prompt about Apple Mail.** Only if you use the Apple Mail import tab. macOS asks
whether Inkwell may control Mail; it can't read anything without that. Declining is fine — the tab
disappears and the Email File tab does the same job.

**A folder chooser that opens behind the window.** The Choose… buttons on Settings and Export open
a real Finder panel, and it belongs to a helper process rather than to Inkwell, so it sometimes
appears behind. Check the Dock if one seems not to have opened.

**Dragging an email onto the app doing nothing.** Mail apps don't hand a file to a web view
directly — you drag the message to your Desktop first, then drop the saved `.eml` on Inkwell. The
app now says so rather than failing silently, but it's still two steps.

**A prompt when you quit.** If you've changed something since the last backup, Inkwell asks
whether to back up before closing. Settings can make it do that without asking. Quitting after a
session where you changed nothing closes straight away.

---

## Known rough edges

Things I already know about, so no need to report them:

- **Updates download themselves, then wait.** Inkwell checks for a newer version while it's
  running and fetches it in the background, but nothing installs until you quit — a red notice
  appears beside the version on the Collection page, leading to Settings, where you can see what's
  in it, restart straight away, or skip that version. You can turn checking off entirely there.
  Worth knowing because the version may change between sessions, which is why it's worth quoting
  when you report something. Your collection isn't touched by an update.
- **Insights and how estimated value works** aren't in the guide yet. Insights also covers pens
  only — inks and nibs don't appear there.
- **Invoice parsing is imperfect.** It's been tuned against a specific set of retailers. A
  confirmation from somewhere new may come out wrong, or not at all — that one *is* worth
  reporting, see below.
- **Some PDFs can't be read at all.** A few invoicing systems save their text in a way that loses
  the characters: readable on screen, but nothing underneath for any program to extract. Inkwell
  says so rather than quietly finding nothing. Open it in Preview, copy the text, and use the
  **Paste Text** tab instead — Preview can usually reconstruct what the file can't hand over.

---

## What's most useful to report

In rough order:

1. **Anything that stops you** — a crash, a page that won't load, a save that doesn't save.
2. **An invoice that imports wrongly.** The most valuable single thing, because every fix becomes
   permanent. Tell me the retailer and what it got wrong; if you can, attach the saved `.eml` or
   PDF, though check it for anything you'd rather not share first.

   Worth trying before you report: on a long invoice, select the rows and use the **Bulk changes**
   panel above the table — set the type, set one brand across them all, or divide the prices by
   quantity when the invoice printed line totals. If a whole invoice comes from a maker who never
   puts their own name in a listing, add them under **Settings → Single-brand retailers** and
   future invoices from them arrive correct.
3. **Anything that made you hesitate.** A label you had to re-read, a button that didn't do what
   you expected. That's harder for me to notice than a crash and often matters more.
4. **Anything missing** that you'd want in a collection tracker.

### What to include

- **The version and build**, shown at the top of the Collection page — something like
  `Inkwell v1.63.0 · 18 Sep 2026 · a3f9c21`. That last part identifies the exact build, which the
  version alone can't, so please quote the whole line. Updates can change it between sessions.
  (**About** in the sidebar shows the same thing, if that's easier to find.)
- **What you did**, in enough detail that I can try the same thing.
- **What happened**, and what you expected instead.

### Where to send it

Email **hello@inkwell-the-app.com**. The easiest way is **About → Send feedback** in the app, which opens
your own email app with the version line already filled in; nothing is sent until you send it.

Please don't use GitHub for reports: anything posted there is public, and an invoice carries your
name and address.

### Please don't send your database

`data.db` contains your whole collection, including anything you paid. I don't need it. If a bug
seems to depend on your data, tell me and we'll find a narrower way to reproduce it.

---

## Getting rid of it

Drag Inkwell from Applications to the Trash. Your collection stays behind at
`~/Library/Application Support/Inkwell/` until you delete that folder too — deliberately, so that
reinstalling doesn't lose anything. Delete the folder if you want it properly gone.
