# Inkwell

A fountain pen collection tracker for your own computer. Your collection stays on your machine.

**Inkwell is in private testing, and these builds are for invited testers only.** If you were
sent here, thank you. Please don't pass this page or the downloads on; if someone else would like
to try it, ask them to get in touch at hello@inkwell-the-app.com. Inkwell is proprietary: receiving a
copy is for evaluation and gives no right to redistribute it.

**Open this page on the computer you're installing on.** If you scanned the QR code with your
phone, send yourself this address and open it there:
**github.com/robmcclure/inkwell-releases**

Current version: **1.67.0**

## Mac

[**Download for Mac**](https://github.com/robmcclure/inkwell-releases/releases/latest/download/Inkwell-mac-arm64.dmg)

- For Macs with Apple silicon (M1 or later).
- Open the download and drag Inkwell into Applications. It's signed and checked by Apple, so it
  opens without warnings.
- Before you start: read the [Mac testing guide](TESTING.md).

## Windows

[**Download for Windows**](https://github.com/robmcclure/inkwell-releases/releases/latest/download/Inkwell-Setup-windows-x64.exe)

- For 64-bit Windows 10 or 11.
- The installer isn't signed yet, so Windows shows **"Windows protected your PC"**. Click
  **More info**, then **Run anyway**. Only do this for a file you downloaded from this page.
- Before you start: read the [Windows testing guide](TESTING-WIN.md).

## Updates

Once installed, Inkwell checks this page for new versions and updates itself when you quit it.
You won't need to download it again.

## Checking your download

To confirm a download is exactly the published file, compare its SHA-256 fingerprint with the
one below. On a Mac: `shasum -a 256 <file>` in Terminal. On Windows: `certutil -hashfile <file>
SHA256` in Command Prompt.

- Mac (`Inkwell-mac-arm64.dmg`, 1.67.0): `0ecebae52ae165d8cf4daa93fa031c3e936639445ec52dc27fbb6e0bc0de05ef`
- Windows (`Inkwell-Setup-windows-x64.exe`, 1.67.0): `bb37a159360504f6690fa46d277cdeba7fea3370ec305b70f5010a59dd360eb5`

## Privacy

GitHub counts how many times each file is downloaded. That number is all Inkwell's author sees:
no names, no IP addresses. The app itself sends nothing about you or your collection anywhere.
It goes online for two things only: checking this page for updates, and, when you import an
order, fetching the product photos that order links to from the retailer's site.

[All versions and release notes](https://github.com/robmcclure/inkwell-releases/releases)
