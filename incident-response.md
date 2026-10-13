# I Think I've Been Hacked

**The one-sentence version:** A hack is a mess to clean up, not
the end of the world — work the checklist in order, change the
important passwords from a clean device, and you'll be fine.

## First: stay calm, and don't wipe yet

Your instinct may be to turn everything off and reinstall
immediately. Resist that. **Disconnect the suspect machine from
the network** (unplug the cable, turn off Wi-Fi), but don't wipe
or reinstall yet — you may need what's on the disk to understand
what happened, and your [backups](backups.md) decide how you
recover, not panic.

## The ordered checklist

Do these in order. Each step protects the next one.

1. **Contain.** Disconnect the affected machine. If you think
   email is compromised, act from a different device you trust —
   your phone, a spare laptop.
2. **Secure email first.** Your email is the master key: almost
   every account can be reset through it. Change the email
   password from the clean device, then check for forwarding
   rules or filters the attacker added (they use these to read
   your mail silently), and revoke unknown sessions/devices.
   See [Passwords](passwords.md) and
   [Passkeys and Two-Factor Auth](passkeys-2fa.md).
3. **Enable two-factor auth** on email and anything financial,
   if it isn't already on. This cuts off most follow-up access
   even if the attacker still has a password.
4. **Change the rest**, starting with banks, then anything that
   holds your files or identity, then everything else.
5. **Decide: restore or rebuild.** If you have backups (see
   [Backups That Actually Restore](backups.md)), restore from a
   backup made *before* the incident. If you don't trust any
   backup — or don't have one — the honest answer is a full
   reinstall ("nuke and pave"), then change every password from
   scratch. A compromised machine that "seems fine now" isn't
   something to trust.
6. **Watch the money.** Check bank and card statements for
   charges you don't recognize. Call the bank about anything
   suspicious.

## When to call the bank or freeze credit

- Call the bank when: money moved, cards were used, or your
  online banking password was compromised.
- Freeze your credit when: identity documents (Social Security
  number, ID scans) were on the compromised machine. A freeze
  is free, reversible, and the single best defense against new
  accounts opened in your name. You freeze with each credit
  bureau individually.

## Symptom → fix

| Symptom | Likely cause | Fix |
|---|---|---|
| Friends get spam "from you" | Email password leaked, or session stolen | Change email password from a clean device; revoke sessions; enable 2FA |
| Password stops working | Attacker changed it | Use the account's recovery flow immediately, from a clean device |
| New forwarding rules / filters in email | Attacker wants to watch your inbox | Delete the rules; assume they read recent mail; change connected passwords |
| Unknown devices in account sessions | Stolen login session | Revoke all sessions, then change the password |
| Programs you didn't install; machine slow for no reason | Malware | Disconnect; scan or reinstall; see [Updates](updates.md) for how it got in |
| Ransomware note on screen | Malware encrypted your files | Don't pay; restore from backup or reinstall. A note about limits: some strains destroy backups too — this is why 3-2-1 backups matter (see [glossary](glossary.md)). |

## How to tell family — without shame

Getting hacked is common and it's not a character flaw. Tell the
people who need to know (anyone whose information shared your
machine or network) plainly: what happened, what you did about
it, and what they should watch for. No dramatic announcement
needed — one honest message beats silence, because silence is
what lets the attacker use *your* name against *them*.

**Next:** [Glossary](glossary.md)
