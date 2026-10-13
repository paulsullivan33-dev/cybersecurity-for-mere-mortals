# Think in Threat Models

**The one-sentence version:** A *threat model* is just a clear-eyed
answer to three questions: what am I protecting, from whom, and what
happens if it breaks.

## Why this comes first

Security advice is endless, and most of it conflicts. Threat modeling
is how you decide which advice matters *to you*. A home laptop and a
bank have different threats, so they need different defenses. Without
a threat model, you either do nothing (bad) or try to do everything
(burnout). Neither works.

## The three questions

**1. What am I protecting?**
List what would hurt to lose: family photos, tax documents, your
email account, access to your bank, a work laptop. Be specific — "my
stuff" is too vague to defend.

**2. From whom?**
Be realistic. For most people, the attackers are:

| Attacker | Realistic example |
|---|---|
| Automated crooks | Bots probing SSH ports, mass phishing |
| A nosy acquaintance | Guesses your password on a shared computer |
| A data thief | Steals your laptop from your car |
| A dishonest insider | Rare for home users — skip this |

You do *not* need to model nation-states or movie plots. Defend
against what will actually happen, not what makes a good story.

**3. What happens if it breaks?**
Inconvenience (lose a weekend), real loss (photos gone forever), or
serious harm (bank account drained). This decides how much effort a
threat deserves.

## Two worked examples

**Example A: family photos on a laptop.**
Protecting: irreplaceable photos. From whom: theft, ransomware,
hardware failure (a bigger threat than hackers here!). If it breaks:
devastating — photos can't be recreated. Decision: *backups*
matter more than firewalls. See [Backups](backups.md).

**Example B: a home server with SSH open to the internet.**
Protecting: the server itself (it can be abused to attack others).
From whom: automated bots scanning for weak passwords —
constantly, around the clock. If it breaks: your machine becomes someone else's
attack platform, and your IP gets flagged. Decision: key-based login
only, no password logins, and fail2ban or equivalent. That's a few
minutes of setup that kills the entire automated-threat category.

## What a threat model can't do

It can't predict everything — it's a planning tool, not a guarantee.
It also doesn't replace responding well when something happens; see
[Incident Response](incident-response.md). Review yours when things
change: new device, new account, new hobby server.

**Next:** [Passwords, Passphrases, and Password Managers](passwords.md)
