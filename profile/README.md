<h1 align="center">Flottille</h1>

<p align="center">
  <strong>Small tools for people who run their own servers.</strong>
</p>

<p align="center">
  <a href="https://gabier.nebulabs.org"><img alt="Site" src="https://img.shields.io/badge/site-gabier.nebulabs.org-e8613a?style=flat-square&labelColor=0f1b2d"></a>
  <img alt="Rust" src="https://img.shields.io/badge/Rust-e8613a?style=flat-square&labelColor=0f1b2d&logo=rust&logoColor=f4efe6">
  <img alt="License MIT" src="https://img.shields.io/badge/license-MIT-2bb5a0?style=flat-square&labelColor=0f1b2d">
</p>

A *flottille* is a handful of small boats sailing together. That is the whole
idea here: one repository, one tool, one job — documented well enough that
somebody else can actually run it.

The names come from the same place. A **gabier** is the sailor posted up in the
rigging whose only job is to watch and call out what he sees. When the daemon
starts, that is exactly what it says: `Gabier est dans la hune`.

---

## ⚓ [gabier](https://github.com/Flottille/gabier) — know who boards your server

A Rust daemon that reads your sshd logs and posts a Discord or Slack
notification on every SSH login, in under a second.

<p align="center">
  <img src="https://gabier.nebulabs.org/media/how-it-works.gif"
       alt="An accepted SSH login becomes a Discord notification in under a second; a 43-attempt scan produces a single summary."
       width="760">
</p>

The notification is the easy part. The hard part is the silence: a VPS with
port 22 open takes thousands of attempts a day, and a channel that reports all
of them gets muted — which is the same as having nothing. So failures are
throttled per IP, the first few going out immediately and the rest summarised
in one message at the end of the window. Successful logins are never grouped.

One binary, zero runtime dependencies, running under a dedicated account with
no shell. Reads journald, or `/var/log/auth.log` on a distribution without
systemd. It observes and never bans — `fail2ban` still has its place next to it.

[Install](https://gabier.nebulabs.org/install/) ·
[Documentation](https://gabier.nebulabs.org) ·
[Throttling](https://gabier.nebulabs.org/docs/throttling/) ·
Rust · MIT

---

## How things get built here

- **Rust for whatever runs on a server.** Something you copy once and then stop
  thinking about, rather than a runtime to keep alive underneath it.
- **Quiet until it matters.** A tool that notifies everything gets muted. Noise
  control is a feature, not a setting somebody will tune later.
- **The documentation ships with the tool.** If it is not written down, it does
  not work.
- **MIT, all of it.** Take it, fork it, no need to ask.

## Contributing

Issues and patches are welcome on any repository here.
[gabier's CONTRIBUTING](https://github.com/Flottille/gabier/blob/main/CONTRIBUTING.md)
covers what fits, what CI runs, and how to add a notification destination — the
code is laid out for it. Found a vulnerability?
[SECURITY.md](https://github.com/Flottille/gabier/blob/main/SECURITY.md),
privately, not in an issue.

<p align="center">
  <sub>Built by <a href="https://github.com/ThibaultPointurier">Thibault Pointurier</a>.</sub>
</p>
