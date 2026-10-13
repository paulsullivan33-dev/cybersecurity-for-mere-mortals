# Passwords, Passphrases, and Password Managers

**The one-sentence version:** Use a *password manager* to give every
site its own long password, protect the manager with one strong
*master password*, and never reuse passwords.

## Why reuse is the real enemy

Password reuse is the single most common way accounts get taken over,
and the mechanism has a name: *credential stuffing*. Here's how it
works, plainly:

1. Some forum or shop you used years ago gets hacked and its password
   list leaks.
2. Attackers feed those email/password pairs into bots that try them
   on Gmail, banks, and everywhere else — automatically, by the
   millions.
3. If you reused the password, they're in.

They never had to guess anything. The weak link wasn't your password;
it was the *reusing*. One unique password per site ends this attack
completely.

## Passphrases vs. random strings

A **passphrase** is several ordinary words strung together
("correct horse battery staple" style — pick your own words, not
that one). A **random string** is gibberish like `k7#mQ9!zLp2`. Both
work. The practical difference:

| | Passphrase | Random string |
|---|---|---|
| Strength | High, if 4+ words | High, if 16+ characters |
| Typing from memory | Doable | Painful |
| Best use | Master password, Wi-Fi key | Everything a manager fills in |

You only need to *memorize* one password — the master password for
your manager. Make that one a long passphrase and let the manager
generate gibberish for everything else.

## How a password manager works

It stores your passwords in an encrypted vault, unlocked by your
master password. It fills logins in your browser for you, generates
random passwords, and — the part that matters — remembers which
password belongs to which site so you never reuse one. Look for:

- Open source or independently audited encryption
- Autofill that only fills on the *real* site (this blocks many
  phishing pages — see [Phishing](phishing.md))
- Export/import, so you're never locked in

## What NOT to do

- **Don't keep passwords in a spreadsheet, notes app, or email.**
  They're unencrypted and usually synced to cloud storage.
- **Don't let your browser be your only manager** if it has no
  master-password lock — anyone who sits at your unlocked computer
  can read them.
- **Don't share passwords by email or chat.** If someone needs
  access, most managers have a proper sharing feature.
- **Don't change passwords "every 90 days"** for no reason. Forced
  rotation makes people pick weaker passwords. Change a password when
  there's a breach, not on a calendar.

## Generate a real password (Linux)

Need a strong random password right now? The box can make one:

```
openssl rand -base64 24
```

**Check:** you get 32 characters of base64 text (24 random bytes),
looking something like:

```
o8D5tpsixw1wRbkrLpYPey4OF00CqF7v
```

Yours will look different — that's the point. The output is always
32 characters. Copy it into your manager and forget it. On Windows or Mac, your
password manager's generator does the same thing — no command needed.

**Next:** [Passkeys and Two-Factor Auth](passkeys-2fa.md)
