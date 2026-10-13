# Passkeys and Two-Factor Auth

**The one-sentence version:** *Two-factor authentication* (2FA) means
proving it's you in two different ways; a *passkey* is the newest,
strongest way to do the second (and often the first) factor.

## What 2FA is

Logging in with just a password is one factor: *something you know*.
2FA adds a second, different kind: *something you have* (your phone)
or *something you are* (your fingerprint). An attacker who steals
your password still can't get in without the second factor. That's
the whole idea — one stolen secret is no longer enough.

## Authenticator apps vs. SMS

Not all second factors are equal:

| Method | How it works | Weakness |
|---|---|---|
| SMS code | A text with a 6-digit code | Phone-number theft (*SIM swapping*), texts can be intercepted |
| Authenticator app | Time-based codes (TOTP) on your phone | You must keep the secret backed up |
| Hardware key / passkey | Cryptography on a device or phone | Costs money (hardware keys); newest tech |

SMS is the weakest because your phone number isn't really
* yours* — a carrier employee can be tricked into moving it to an
attacker's SIM, and then *your* codes go to *their* phone. This
actually happens. Use an authenticator app or a passkey instead of
SMS whenever the site offers it. (SMS 2FA still beats no 2FA — don't
turn it off because the better option isn't there yet.)

## What a passkey is, and why it beats phishing

A passkey is a cryptographic key pair: your device keeps the private
half, the website gets the public half. When you log in, your device
proves it holds the private key — usually by unlocking with your
fingerprint or face — and the website verifies the math.

Here's the magic part: the private key is *bound to the real site's
address*. A fake login page at `g00gle.com` can't use it — the
handshake simply fails. Phishing (see [Phishing](phishing.md)) stops
working, not because you're careful, but because the math won't
cooperate with the attacker. Passkeys are the first login method
that defeats phishing *structurally*.

## Where to enable it first

**Your email accounts first — the keys to everything.** Almost every
"forgot password" flow sends a reset link to your email. If someone
owns your email, they own everything tied to it. Priority order:

1. Primary email (Gmail, Outlook, iCloud...)
2. Banking and financial accounts
3. Password manager (yes, the manager itself)
4. Everything else

## Backup and recovery codes

When you set up 2FA, the site gives you one-time *recovery codes*.
They're your spare key if you lose your phone. Treat them like one:

- Print them or write them down and store them somewhere physical
  (a desk drawer beats a text file on the same laptop)
- Each code works once; never share one with anyone — "support" will
  never ask for them
- Test one recovery code after setup, then re-save the rest

## What 2FA can't do

2FA doesn't protect you from malware on your own device, from giving
away the code yourself on a phishing page, or from a site that gets
breached on its own end. It's one strong layer, not a guarantee.

**Next:** [Phishing and Social Engineering](phishing.md)
