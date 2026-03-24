<div align="center">

# x-phone

**Embed real phone calls in any app. Open-source, no Twilio, no PBX.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

</div>

---

Open-source telephony libraries and tools for AI voice agents, softphones, and call automation. SIP signaling, RTP/SRTP media, audio and video codecs, NAT traversal, and clean PCM access — everything you need to build on real phone infrastructure without platform lock-in.

### Who is this for?

- **AI voice agent builders** — pipe call audio straight into your STT/LLM/TTS pipeline
- **VoIP developers** — embed a SIP phone into any app with a clean API
- **Teams replacing Twilio** — self-host your voice stack, keep your audio on your infra
- **Telecom tinkerers** — scriptable, testable telephony with no black boxes

## How it fits together

```
                        ┌─────────────────────────────────────────┐
                        │             Your Application            │
                        │      (AI agent, softphone, IVR, ...)    │
                        └──────────┬──────────────┬───────────────┘
                                   │              │
                          PCM audio/API    WebSocket + REST
                                   │              │
                        ┌──────────┴───┐   ┌──────┴──────┐
                        │    xphone    │   │   xbridge   │
                        │  (Rust / Go) │   │  (gateway)  │
                        └──────────┬───┘   └──────┬──────┘
                                   │              │
                              SIP / RTP      SIP / RTP
                                   │              │
                        ┌──────────┴──────────────┴───────────────┐
                        │          Phone Network / PBX            │
                        │   (SIP trunks, Asterisk, FreeSWITCH)    │
                        └─────────────────────────────────────────┘
```

**xphone** — use directly in Rust or Go for full control over calls and media.
**xbridge** — deploy as a standalone gateway; your app talks WebSocket + REST in any language.

## Core Libraries

<table>
<tr>
<td width="50%">

### xphone for Rust
[![Crates.io](https://img.shields.io/crates/v/xphone.svg)](https://crates.io/crates/xphone)
[![docs.rs](https://docs.rs/xphone/badge.svg)](https://docs.rs/xphone)

```rust
let phone = Phone::new(Config {
    username: "agent".into(),
    password: "secret".into(),
    host: "sip.provider.com".into(),
    ..Config::default()
});

phone.on_incoming(|call| {
    call.accept()?;
    // call.pcm_reader() → your STT pipeline
    Ok(())
});
```

[xphone-rust](https://github.com/x-phone/xphone-rust)

</td>
<td width="50%">

### xphone for Go
[![Go Reference](https://pkg.go.dev/badge/github.com/x-phone/xphone-go.svg)](https://pkg.go.dev/github.com/x-phone/xphone-go)
[![Go Report Card](https://goreportcard.com/badge/github.com/x-phone/xphone-go)](https://goreportcard.com/report/github.com/x-phone/xphone-go)

```go
phone := xphone.New(
    xphone.WithCredentials(
        "agent", "secret", "sip.provider.com",
    ),
)

phone.OnIncoming(func(call xphone.Call) {
    call.Accept()
    // call.PCMReader() → your STT pipeline
})
```

[xphone-go](https://github.com/x-phone/xphone-go)

</td>
</tr>
</table>

**Highlights:** G.711, G.722, Opus, G.729 audio · H.264, VP8 video · SRTP encryption · STUN/TURN/ICE-Lite · hold, transfer, mute, DTMF · SIP MESSAGE, presence, BLF · MockPhone & MockCall for tests

## Infrastructure & Tools

| Project | What it does |
|---|---|
| [**xbridge**](https://github.com/x-phone/xbridge) | Self-hosted voice gateway — WebSocket audio + REST call control. Drop-in Twilio replacement. Deploy one binary, connect from any language. |
| [**xpbx**](https://github.com/x-phone/xpbx) | Dockerized Asterisk PBX with web management UI — extensions, trunks, and dialplan out of the box. |

## Testing

| Project | What it does |
|---|---|
| [**fakepbx**](https://github.com/x-phone/fakepbx) | In-process SIP server for Go tests. Real SIP over loopback — no Docker, no Asterisk, no hardcoded ports. |
| [**fakepbx-rust**](https://github.com/x-phone/fakepbx-rust) | Same concept for Rust. Spin up a SIP server in your test, tear it down when done. |
| [**demos**](https://github.com/x-phone/demos) | Working examples and tutorials for the full x-phone ecosystem. |

## Quick Links

[Rust docs](https://docs.rs/xphone) · [Go docs](https://pkg.go.dev/github.com/x-phone/xphone-go) · [Examples](https://github.com/x-phone/demos) · [xbridge Docker image](https://ghcr.io/x-phone/xbridge)

---

<div align="center">

MIT Licensed · Built with Rust and Go

</div>
