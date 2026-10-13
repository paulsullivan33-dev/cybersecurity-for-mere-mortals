# Backups That Actually Restore

**The one-sentence version:** A backup you have never restored is
a hope, not a backup. Make copies of the irreplaceable stuff,
keep one copy somewhere else, and prove the copies work by
restoring from them.

## The 3-2-1 idea, in plain words

Forget the jargon; here's the shape of it:

- **3 copies** of anything important (the original counts as one).
- **2 different places** — e.g., your computer *and* an external
  drive. One fire, spill, or dead disk shouldn't take both.
- **1 copy somewhere else** — a different building. Cloud storage
  counts. Your desk drawer doesn't.

That's it. Three copies, two places, one off-site.

## Back up the irreplaceable, not everything

You don't need to back up your operating system or your apps —
those reinstall. Back up what you can't re-download:

- Photos and home videos
- Documents (taxes, deeds, writing, schoolwork)
- Financial records, password-manager exports
- Configuration files you spent hours tuning (dotfiles, server
  configs)

**Rule of thumb:** if losing it would make you sad or cost you a
weekend, it belongs in the backup.

## Local vs. cloud

| | External drive (local) | Cloud storage |
|---|---|---|
| Speed | Fast restores | Depends on your upload speed |
| Cost | One-time purchase | Monthly/annual fee |
| Survives house fire | No | Yes |
| Survives you forgetting the password | Yes | No — don't lose the login |
| Privacy | Nobody else holds your data | The provider holds your data |

Use both if you can: local for fast restores, cloud for the
off-site copy. That *is* 3-2-1 with one purchase and one
subscription.

## Versioning vs. mirroring — this distinction matters

- A **mirror** copies the *current* state. If you delete a file,
  the next mirror deletes the copy too. If a file gets corrupted,
  the corruption gets copied.
- **Versioning** keeps history: yesterday's version, last week's
  version. Delete something by accident and you can go back.

**Prefer versioning.** Most backup tools (Time Machine on Mac,
File History on Windows, restic/borg on Linux, and most cloud
backup services) keep versions by default. A plain folder-sync
(Dropbox-style syncing, rsync without history) is a mirror —
handy, but not a real backup on its own.

## The restore test (do this part)

A backup is only proven when you restore from it. Twice a year,
spend ten minutes:

1. Pick one real file — a photo, a document.
2. Rename the original (don't delete it yet).
3. Restore that file from your backup.
4. Open it. Compare: does it look right? Same size, same
   content?
5. Put the original back.

**Check:** the restored file opens and matches the original.
If it doesn't — wrong version, corrupted copy, backup job
silently failing — you just found out on a calm Tuesday
instead of during a crisis. Fix the backup, test again.

If your backup tool offers a "verify" feature, run it too, but
it doesn't replace an actual restore.

## The ransomware paragraph (one honest one)

**Ransomware** is malware that encrypts your files and demands
payment for the key. Here's the honest version: a versioned,
offline or off-site backup is the best defense an ordinary
person has, because you can wipe the machine and restore instead
of paying. But it is not magic — ransomware can also encrypt
backups it can reach (a permanently-attached external drive, a
synced cloud folder). That's why one copy should be *disconnected*
or *off-site*, and why versioning matters: it lets you restore
the version from *before* the encryption. Paying the ransom is
not recommended — it funds the next attack and doesn't guarantee
your files back. If it happens to you, see
[incident-response.md](incident-response.md).

## The habit

1. List the irreplaceable stuff (ten minutes, once).
2. Set up one local backup and one off-site backup.
3. Make sure versioning is on, not just mirroring.
4. Restore-test twice a year. Calendar it.

**Next:** [home-network.md](home-network.md) — the router and
Wi-Fi standing between your stuff and the internet.
