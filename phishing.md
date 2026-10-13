# Phishing and Social Engineering

**The one-sentence version:** *Phishing* is tricking you into handing
over access yourself; *social engineering* is the broader art of
manipulating people instead of hacking computers.

## What phishing looks like today

- **Email phishing:** "Your account will be suspended — verify now."
  Still one of the most common ways people get compromised, and the
  most polished.
- **Smishing (SMS):** "USPS: your package couldn't be delivered,
  confirm your address here." You weren't expecting a package.
- **Vishing (voice):** A caller claims to be your bank, the IRS, or
  tech support. Caller ID is trivially faked.
- **QR codes:** A sticker or flyer with a QR code that leads to a
  credential-harvesting page. You can't "read" a QR code before
  scanning — that's what makes them effective.

## The 5-second checks

Before you click, type, or call back, run these:

1. **Read the sender address, not just the name.** "PayPal Support"
   means nothing; `support@paypa1-secure.ru` is a confession.
2. **Hover the link (or long-press on mobile).** Does the real
   address match the company? A mismatch is a hard stop.
3. **Urgency is a red flag.** "Act in the next 10 minutes or your
   account closes" is how they stop you from thinking. Real
   companies don't do this.
4. **They contacted you — don't use their path.** Got a scary bank
   text? Open the bank's app yourself or call the number on your
   card. Never use the number they gave you.
5. **Attachments you didn't ask for stay closed.** Especially
   unexpected invoices, "resumes," or zipped files.

## What to do if you clicked

Don't panic — act fast instead:

1. **Disconnect** — close the tab/window immediately.
2. **If you typed a password,** change it *now*, from a fresh
   browser tab you opened yourself. Start with the password — see
   [Passwords](passwords.md).
3. **If you entered card or bank details,** call your bank. They
   deal with this daily; that's what fraud departments are for.
4. **If you installed something,** treat the machine as compromised
   until checked — see [Incident Response](incident-response.md).

Speed matters more than embarrassment. Every minute you wait because
you feel silly is a minute the attacker uses.

## Why even careful people fall for it

No shaming here — this is worth understanding. Phishing works
because it targets *attention*, not intelligence:

- You're tired, rushed, or checking mail on a phone — the attacker
  only needs one distracted minute.
- Modern phishing pages are pixel-perfect copies; "looks legit" is
  no longer a test anyone can pass by eye.
- Authority and urgency short-circuit deliberation — that's a human
  feature, not a bug.

The fix isn't "be smarter." It's structural: a password manager that
refuses to autofill on fake sites, passkeys that can't be phished
(see [Passkeys and Two-Factor Auth](passkeys-2fa.md)), and the habit
of never following the attacker's path — always navigate to the
site yourself.

**Next:** [Backups](backups.md)
