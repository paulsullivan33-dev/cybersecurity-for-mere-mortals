# Exposing a Service Safely

**The one-sentence version:** A service on your home network is
only reachable by *your* devices — until you open a door in your
router, and then it's reachable by the entire internet, including
the automated scanners that probe every door, all day.

## LAN-only vs. internet-facing

When you run a service on a home machine, other devices on your
home Wi-Fi can reach it. That is **LAN-only**: your router blocks
everyone outside your network, by default. That's the safe
starting point — most things you run should stay there.

**Port forwarding** is a setting in your router's admin page that
says: "anything arriving at my public address on port X, send to
this computer inside my house." One rule exposes one service to
the entire internet. Before you forward anything, re-read
[Threat Models](threat-models.md): what happens if a stranger
gets into this service?

## Minimal exposure checklist

Do this *before* you create the forwarding rule, not after:

| Rule | Why |
|---|---|
| Forward **only** the ports you need | Every open port is a separate door. |
| Require strong authentication on everything | No anonymous logins, no default passwords. See [Passwords](passwords.md) and [Hardening SSH](ssh-hardening.md). |
| Keep the service updated | Most internet compromises use old, known bugs, not genius hacks. See [Updates](updates.md). |
| Disable what you don't use | UPnP, remote router admin, forgotten guest networks. See [Your Home Network](home-network.md). |
| Write down what you exposed | Port, service, date. Future you will forget. |

If any of this feels like too much work for what you want to
expose, that's a signal: don't expose it.

## Reverse proxies and tunnels, honestly

A **reverse proxy** is one gatekeeper that sits in front of your
services and decides what passes through. A **tunnel** is a
connection your home machine makes *outward* to an outside
service, which relays requests back in — so your router never
opens a port at all.

The honest version: these don't make a bad service safe. A
vulnerable app behind a tunnel is still vulnerable. What they give
you is one door to guard instead of five, and the ability to close
everything from one place. Worth learning once you have more than
one thing exposed — not before.

## Honeypots: what running one teaches you

A **honeypot** is a fake target that looks like a real server but
exists only to watch what attackers do. Here's the lesson every
home operator learns the week they set one up:

**Within hours of going online, your machine will see automated
login attempts.** Usernames like `admin` and `root`, passwords like
`123456` — tried over and over by bots that scan the entire
internet looking for weak machines. That's not personal. Nobody
chose *you*. The internet is simply scanned constantly, and your
public address is in the pile like everyone else's.

This is why default passwords, password-only SSH, and open admin
panels don't survive exposure. The bots aren't smart, but they're
relentless, and they only need one weak door among millions.

## Logs worth glancing at

Check these once a week for the first month after exposing
something:

- **Failed-login counts.** Hundreds of failed SSH attempts per
  day is background noise. One *successful* login from an
  address you don't recognize is an emergency — see
  [I Think I've Been Hacked](incident-response.md).
- **fail2ban status** (if installed): blocks IPs that fail login
  too many times.

  ```bash
  sudo fail2ban-client status sshd
  ```

  **Check:** a status line with a current ban count. (The `sshd`
  jail only exists if fail2ban was configured for SSH — run
  `sudo fail2ban-client status` to see your jail list.)
- **Your router's forwarding rules.** Look for ones you didn't
  create — some devices add them silently via UPnP.
- **The service's own log.** Find out where it lives *before*
  you need it.

**Next:** [Scams That Target Regular People](scams.md)
