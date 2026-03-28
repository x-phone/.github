<div align="center">

# x-phone

**Open-source SIP/RTP library for making real phone calls from code.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

</div>

---

xphone is a single library — no gateway, no PBX, no infrastructure to deploy. Add it to your project, point it at a SIP trunk, and you're making real phone calls. Available in **Go** and **Rust**.

<table>
<tr>
<td width="50%">

**Go** · [![Go Reference](https://pkg.go.dev/badge/github.com/x-phone/xphone-go.svg)](https://pkg.go.dev/github.com/x-phone/xphone-go)

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

phone.Connect(ctx) // ← that's it. Real calls.
```

[xphone-go](https://github.com/x-phone/xphone-go) · [pkg.go.dev](https://pkg.go.dev/github.com/x-phone/xphone-go)

</td>
<td width="50%">

**Rust** · [![Crates.io](https://img.shields.io/crates/v/xphone.svg)](https://crates.io/crates/xphone)

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

phone.connect()?; // ← that's it. Real calls.
```

[xphone-rust](https://github.com/x-phone/xphone-rust) · [docs.rs](https://docs.rs/xphone)

</td>
</tr>
</table>

SIP registration, RTP media, codec negotiation, NAT traversal — xphone handles the protocol complexity. You get clean PCM audio frames in and out.

Use xphone directly in Go or Rust for full control over calls and media. Use [xbridge](https://github.com/x-phone/xbridge) when you want REST/WebSocket access from any language without writing SIP code.

### Who is this for?

- **AI voice agent builders** — pipe call audio into your STT/LLM/TTS pipeline without a telephony platform
- **VoIP developers** — embed SIP calling into any app with a clean, testable API
- **Teams moving off hosted voice APIs** — own the media path, run on your infra

### What xphone handles

SIP signaling · RTP media · SRTP (SDES; see per-project docs for transport security details) · G.711, G.722, Opus, G.729 · H.264, VP8 · STUN/TURN/ICE-Lite · hold, transfer, mute, DTMF · SIP MESSAGE, presence, BLF

### Tested against

- **SIP trunks:** Telnyx, Twilio SIP, VoIP.ms, Vonage
- **PBXes:** Asterisk, FreeSWITCH, 3CX
- **Test infrastructure:** [fakepbx](https://github.com/x-phone/fakepbx) (in-process SIP server, real SIP over loopback) + [xpbx](https://github.com/x-phone/xpbx) (Dockerized Asterisk) in CI
- **Unit tests:** MockPhone & MockCall — test call flows without any SIP server

See each repo's README for detailed compatibility notes.

### What xphone is not

- **Not a hosted platform.** No cloud service, no dashboard, no managed infrastructure. You run it, you operate it.
- **Not a full Twilio replacement.** xphone is the voice data plane — SIP and media. Billing, number provisioning, call routing rules, recording storage, and HA are your responsibility.
- **Not batteries-included for security.** SRTP is SDES-based. DTLS-SRTP is not currently supported. See each repo's README for the current security surface.

### Status — Beta

xphone is in active development and used in internal production workloads. APIs may change between minor versions. If you're evaluating, start with the [examples](https://github.com/x-phone/demos) and [xphone-go](https://github.com/x-phone/xphone-go) (the more mature implementation).

## Other repositories

| Project | Status | What it does |
|---|---|---|
| [**xbridge**](https://github.com/x-phone/xbridge) | Active | Self-hosted voice gateway — exposes xphone as WebSocket audio + REST API. Single-node, stateless. For teams using Python, Node, or other languages without a native xphone library. |
| [**xpbx**](https://github.com/x-phone/xpbx) | Active | Dockerized Asterisk PBX with web UI — useful for local development and testing against a real PBX. |
| [**fakepbx**](https://github.com/x-phone/fakepbx) | Stable | In-process SIP server for Go tests. Real SIP over loopback — no Docker, no Asterisk. |
| [**fakepbx-rust**](https://github.com/x-phone/fakepbx-rust) | Stable | Same concept for Rust tests. |
| [**demos**](https://github.com/x-phone/demos) | Active | Working examples for the x-phone ecosystem. **Start here if you're evaluating.** |

---

<div align="center">

MIT Licensed · Built with Rust and Go

</div>
