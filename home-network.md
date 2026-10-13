# Your Home Network

**The one-sentence version:** Your router is the front door of
your digital house. Change its locks (default password), keep it
maintained (firmware), and don't give every gadget the master key
(guest network for IoT).

## Router hygiene

Your router is a small computer that every device in your house
trusts. Treat it like one.

**1. Change the default admin password.** Routers ship with
well-known logins (often printed on a sticker — and in the
manual, which is online for everyone). Anyone who reaches your
router's login page and knows the model can look up the default.
Log in (usually `http://192.168.1.1` or `http://192.168.0.1`),
find Administration/Management, and set a strong, unique
password. Store it in your password manager.

**2. Update the firmware.** Same logic as
[updates.md](updates.md): old router firmware has known holes.
Check the router's admin page for a firmware update section a
few times a year. Some routers auto-update — turn that on if
offered.

**3. Turn off UPnP.** **UPnP** (Universal Plug and Play) lets
devices *inside* your network automatically open ports to the
internet — no password, no confirmation. It was meant for games
and video chat; in practice, malware on any device can use it
to punch holes in your router for the outside world to walk
through. Turn it off in the router settings. If something you
actually use breaks (an older game console, a self-hosted
service), open just that port manually — see
[public-services.md](public-services.md).

## Wi-Fi: the settings that matter

| Setting | What to choose | Why |
|---|---|---|
| Security mode | **WPA3** if all devices support it, else **WPA2** | These encrypt your Wi-Fi traffic. Never WEP or "Open" — both are trivially broken. |
| Wi-Fi password | Long passphrase, unique to the network | This is the key to your network; a short one can be guessed offline. |
| Network name (SSID) | Anything; hiding it adds nothing | A hidden network is still visible to anyone looking — obscurity, not security. |

**Use the guest network.** Most routers can run a second Wi-Fi
network. Put two kinds of things on it:

- **Visitors.** They get internet without getting access to
  your computers, file shares, and printer.
- **IoT gadgets** — smart bulbs, cameras, thermostats, the
  printer. These devices get infrequent updates and have a
  poor security track record. If one is compromised, the guest
  network keeps it away from your laptop and your files.

Your printer does not need to see your main network. It needs
to print.

## What a firewall does (one paragraph)

A **firewall** is a bouncer: it decides which network traffic
gets in. Your router has one (it blocks unsolicited connections
from the internet by default — nobody outside can just knock on
your laptop), and your computer's operating system has one too
(Windows Firewall, macOS's built-in firewall, `ufw` on Linux).
Leave both on. What a firewall *can't* do: stop you from
clicking a phishing link, opening a bad attachment, or
installing a malicious app — that traffic looks like *you*
inviting it in, and the bouncer lets invited guests through.

## VPNs: when they help and when they don't

A **VPN** (virtual private network) encrypts your traffic
between your device and the VPN provider's server. Honest
assessment:

**Helps when:**

- You're on untrusted Wi-Fi (coffee shop, airport, hotel). The
  VPN keeps the local network snoop from reading your traffic.
- You want your internet provider to see less of your browsing.

**Doesn't help when:**

- You're already home on your own trusted network — there's
  little to hide from.
- Against malware, phishing, or tracking cookies. A VPN is a
  private tunnel, not a bodyguard.
- With anonymity. The VPN provider can see everything your ISP
  used to see — you've moved your trust, not removed it.

**Bottom line:** a VPN is a tool for untrusted networks, not a
general-purpose invisibility cloak. Don't pay for one out of
fear; get one if you actually work from coffee shops.

## The habit

1. Router admin password: changed, stored in password manager.
2. Router firmware: check quarterly; auto-update if offered.
3. UPnP: off.
4. Wi-Fi: WPA2 or WPA3, strong passphrase.
5. Guest network: on, holding visitors and IoT.

**Next:** [ssh-hardening.md](ssh-hardening.md) — if you run a
server at home (or anywhere), lock down remote access properly.
