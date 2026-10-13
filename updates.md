# Keep Everything Updated

**The one-sentence version:** Most successful attacks don't use
clever new tricks — they use old, known holes in software that
already has a fix. Updating is how you close those holes.

## Patching, in plain words

Software ships with bugs. Some bugs are security holes: ways in
that an attacker can use. When the maker finds one, they publish
a fix (a **patch**) — and they *describe* the hole publicly so
everyone knows to install it. That description also tells attackers
exactly where the open door is.

So after a patch is released, there is a race: you installing the
fix vs. an attacker trying the now-documented hole. Every day you
wait, you are easier to hit. This is why updates are the single
highest-value security habit. Not the fanciest — the most valuable.

**What updates can't do:** they don't fix holes nobody knows about
yet (so-called "zero-days"), they don't stop phishing, and they
don't help if your password is `summer2024`. See
[threat-models.md](threat-models.md) for where updates fit in the
bigger picture.

## Turn on automatic updates

The best update is the one you never think about. Turn these on
once, then forget them:

| Device | Where to turn it on |
|---|---|
| Windows | Settings → Windows Update → turn on automatic updates |
| Mac | System Settings → General → Software Update → Automatic updates ON |
| iPhone | Settings → General → Software Update → Automatic Updates |
| Android | Settings → System → Software update (wording varies by brand) |
| Apps (phone) | App Store / Play Store → auto-update apps ON |

Automatic updates occasionally restart your machine or briefly
change something. That's the price, and it's cheap.

## Update your Linux box by hand (30 seconds)

On Debian/Ubuntu and relatives, this is the whole ritual:

```
sudo apt update && sudo apt upgrade
```

`update` refreshes the *list* of available fixes; `upgrade`
installs them. (Two steps, easy to confuse — `update` alone
changes nothing on your system.)

**Check:** run it again. When you're current, the end of the
output looks like this:

```
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

`0 upgraded` means there is nothing left to install. Done.

Other distros, same idea:

- Fedora/RHEL: `sudo dnf upgrade --refresh`
- Arch: `sudo pacman -Syu`

## The "restart when it asks" rule

Some updates only take effect after a restart — the kernel, the
browser, the SSH service. Until you restart, you are still running
the old, hole-y version. The update did its half; the restart is
yours.

**Symptom → fix:**

| Symptom | Fix |
|---|---|
| "Restart required" nag on Ubuntu | Restart. That's the whole fix. |
| Browser updated but a tab has been open for a month | Close and reopen the browser (or restart) |
| Phone installed an update overnight, asks to restart | Let it restart |

A machine that hasn't restarted in months is a machine running
months-old code. If you run servers, schedule a reboot window;
if you run a laptop, just close the lid-lesson: restart weekly.

## Don't forget the forgotten devices

- **Router firmware.** Log into your router (usually
  `http://192.168.1.1` or `http://192.168.0.1`) and check for a
  firmware update section. Routers are computers too, and old
  router firmware is a classic way in. See
  [home-network.md](home-network.md).
- **Apps, not just the OS.** Browsers, PDF readers, media players —
  update those too. Most can auto-update; let them.
- **IoT gadgets.** Cameras, smart plugs, thermostats: check the
  maker's app for firmware updates. If a gadget hasn't had an
  update in years and the maker is gone, treat it as untrustworthy
  — put it on the guest network (see
  [home-network.md](home-network.md)).

## The habit

1. Automatic updates: ON everywhere.
2. Linux servers: `sudo apt update && sudo apt upgrade` on a
   schedule (weekly is fine for a home box).
3. Restart when asked. No "remind me tomorrow" for a month.
4. Router and app firmware: check a few times a year.

**Next:** updates close the doors — [backups.md](backups.md) is
your plan for when something gets through anyway.
