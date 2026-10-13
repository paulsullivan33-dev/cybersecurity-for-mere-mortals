# Hardening SSH

**The one-sentence version:** If you log into machines remotely,
stop using passwords for it. Use cryptographic keys instead,
then tell the server to refuse passwords entirely.

**SSH** (Secure Shell) is how you get a terminal on another
computer over the network. It's encrypted and safe *in transit* —
the risk is at the login step: password-guessing bots hammer
every SSH server on the internet, all day, trying common
usernames and passwords.

## Keys from scratch (on your own computer)

A key pair is two mathematically linked files. The **private
key** proves who you are (guard it); the **public key** can go
on any server you want to log into (it's safe to share).

Generate one (Linux and Mac: Terminal; Windows: PowerShell —
Windows 10/11 ships OpenSSH, or use PuTTYgen with PuTTY):

```
ssh-keygen -t ed25519
```

Accept the defaults. Set a **passphrase** when asked — it's a
password that protects the key file itself, so a stolen laptop
doesn't mean stolen server access.

**Check:** list what was created.

```
ls -l ~/.ssh/
```

Expected: `id_ed25519` (private — permissions should read
`-rw-------`, only you can read it) and `id_ed25519.pub`
(public — safe to copy anywhere).

| File | What it is | Share it? |
|---|---|---|
| `~/.ssh/id_ed25519` | Private key — your identity | **Never.** Not by email, not in chat. |
| `~/.ssh/id_ed25519.pub` | Public key — a lock your private key opens | Yes — paste it onto servers. |

## Copy the public key to the server

```
ssh-copy-id user@host
```

(Replace `user` with your username on the server, `host` with
its address.) It asks for your password *one last time* and
installs the public key. Windows PuTTY users: copy the public
key text into `~/.ssh/authorized_keys` on the server manually.

**Check — and order matters:** prove the key works *before* you
disable passwords. From your computer:

```
ssh -o PasswordAuthentication=no user@host
```

If you get in with no password prompt, keys work. If it fails,
**stop** — fix the key setup first. Disabling passwords before
keys work locks *you* out. There is no undo from the outside.

## Server side: refuse passwords

Edit `/etc/ssh/sshd_config` on the server (as root or with
sudo), then restart the SSH service. Real directives, real
syntax:

```
# No password logins — keys only
PasswordAuthentication no

# Nobody logs in directly as root, ever
PermitRootLogin no

# Only these users may connect via SSH at all
AllowUsers your-username
```

Apply the change:

```
sudo systemctl restart sshd
```

(On some distros the service is called `ssh` instead of
`sshd`. Debian/Ubuntu use `ssh`; Fedora/RHEL/Arch use `sshd`.)

**Check:** dump the server's effective config and confirm:

```
sudo sshd -T | grep -Ei 'passwordauthentication|permitrootlogin|allowusers'
```

Expected:

```
passwordauthentication no
permitrootlogin no
allowusers your-username
```

`sshd -T` shows what the server *actually* enforces, which
beats re-reading the file.

## Changing the port: obscurity, not security

You'll see advice to move SSH off port 22:

```
Port 2222
```

Honest label: this is **obscurity, not security**. A port scan
finds it in seconds; it stops zero targeted attacks. What it
does do is cut the background noise — the bot spray mostly
knocks on port 22, so your logs get quieter and fail2ban (below)
has less to chew on. Fine to do, wrong to rely on.

## fail2ban: the bouncer

**fail2ban** watches the server's logs. When an address fails
too many logins, it temporarily blocks that address at the
firewall. Plain words: fail too many times in a row and you're
ignored for a while. It doesn't make keys stronger — it makes guessing
expensive and keeps logs readable.

```
sudo apt install fail2ban
sudo systemctl enable --now fail2ban
```

The default configuration already protects SSH; you don't need
to write rules for the basic case.

**Check:**

```
sudo systemctl status fail2ban
```

Expected: `active (running)`. To see who's currently banned:

```
sudo fail2ban-client status sshd
```

## The standard recipe

1. `ssh-keygen -t ed25519` — key pair, passphrase set.
2. `ssh-copy-id user@host` — public key onto the server.
3. `ssh -o PasswordAuthentication=no user@host` — **prove keys
   work before touching the server config.**
4. On the server: `PasswordAuthentication no`,
   `PermitRootLogin no`, `AllowUsers your-username` in
   `sshd_config`; restart sshd; verify with `sshd -T`.
5. Install fail2ban. Optional: move the port for quieter logs.

Key-only login plus fail2ban is the standard home-server
setup. It defeats the entire password-guessing industry in one
move: there is no password *to* guess.

**Related:** exposing SSH to the internet at all deserves the
full treatment in [public-services.md](public-services.md); if
something already went wrong, see
[incident-response.md](incident-response.md).
