# x-phone

Open-source telecom tooling. SIP, VoIP, RTP — tested, scriptable, no infrastructure required.

## Projects

| Project | Language | What it does |
|---|---|---|
| **[xphone-go](https://github.com/x-phone/xphone-go)** | Go | SIP telephony library — registration, calls, RTP media, codecs, DTMF, hold, transfer. Event-driven API. |
| **[fakepbx](https://github.com/x-phone/fakepbx)** | Go | In-process SIP server for tests. Real SIP over loopback — no Docker, no Asterisk. |

## Philosophy

Telecom testing shouldn't require spinning up infrastructure. Our tools run inside your test process, speak real protocols, and tear down automatically. No containers, no config files, no shared staging servers.
