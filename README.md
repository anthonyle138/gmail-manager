# Gmail Account Manager

A desktop app for managing a large set of Gmail accounts from one window. Each account gets its own isolated browser profile that stays signed in, so you can open any account in one click, log in automatically with its password and 2FA, read its live codes, see whether it is still alive, and hand its session to other tools. Everything runs on your own machine; this repository only hosts the installers and the auto-update feed.

**Download the latest version:** https://github.com/anthonyle138/gmail-manager/releases/latest

| File | Use |
|---|---|
| `GmailAccountManager-Setup-x.y.z.exe` | Windows installer. Updates itself from this page on launch. |
| `GmailAccountManager-x.y.z-win-portable.zip` | Unzip, run `win-unpacked\Gmail Account Manager.exe`. No install, no auto-update. |

## What it does

**Account list**
- Keeps all accounts in one list organised into groups: `email|password|recovery|totpSecret|proxy`.
- Table view with email, proxy, group, live 2FA code and health status. Search, filter by Live / Dead / New / Open, sort by column.
- Groups sidebar with counts. Add one account, paste a whole batch straight into a group, rename or delete groups, delete accounts singly or in bulk.

**Browser sessions**
- **Open** launches the account's own persistent browser profile, already signed in from last time. Several accounts can be open at once.
- **Auto login** opens the browser and types the email, password and TOTP code for you. Restricted accounts are taken straight to Google's appeal page.
- Engines: system Google Chrome, or A's Browser (anti-detect; enter your licence key in Settings).
- Per-account proxy, set one at a time or in bulk for a selection or a whole group. Browser timezone and location follow the proxy's exit IP.

**2FA and codes**
- Live TOTP code for every account with a countdown; click to copy, or copy the codes of all ticked accounts at once.
- **Read OTP** pulls the newest one-time code from the account's inbox over IMAP, using a Google app password the app creates for you (singly or in bulk).

**Health**
- Each time an account is opened its state is recorded: `INBOX` (live), `LOGIN` (needs sign-in), `RESTRICTED` / `BLOCKED` / `DISABLED` (dead). Counts show in the footer and per group.

**Phone verification**
- Rents a disposable number from 2ndline for Google's phone prompt, shows the number to paste, and rings a chime the moment the SMS code arrives, whichever account you are looking at.

**Hand-off to other tools**
- **Export sessions**: Google cookies of the ticked accounts for an external captcha solver.
- **Forward**: sets up mail forwarding from many accounts to one destination account.

**Housekeeping**
- Settings export/import bundle (accounts, SMS login, engine) to move to another machine. The A's Browser licence is machine-bound and is never included.
- System health page with one-click repairs; per-account storage view (compact cache, clear session).

## Quick start

1. Install and open the app.
2. Click **New** to add one account, or **Import** to paste many lines into a group.
3. Tick accounts and press **Auto login** the first time. After that, **Open** is enough; the session is kept.
4. The live 2FA code is in the detail panel and in the table. Right-click any row for the full menu.

Keyboard: `/` search · `↑↓` move · `Enter` open · `L` auto login · `C` copy code · `Space` select · `N` new · `E` edit.

## Where your data lives

Accounts, passwords, TOTP secrets, browser profiles and encrypted IMAP credentials are stored in the app's local data folder on your computer with restricted permissions. The app talks only to Google and the SMS provider through the browsers it launches, and to this page to check for updates. Nothing is uploaded here.

## Troubleshooting

| Symptom | What to do |
|---|---|
| Installer says the app cannot be closed | End `Gmail Account Manager.exe` in Task Manager, click Retry. |
| Open / Auto login does nothing with A's Browser | Its licence check goes through the account's proxy. Fix or clear a dead proxy. |
| Rented number never gets a code | The number is dead on the provider side. Cancel once the early-cancel window has passed and rent another. |
