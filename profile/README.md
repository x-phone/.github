# x-phone

Telephony libraries for AI voice agents and embedded softphones. SIP signaling, RTP/SRTP media, audio and video codecs, NAT traversal, and clean PCM/RTP access — no PBX required.

## xphone

Embed real phone calls in any application. xphone handles SIP registration, call state, codec negotiation, SRTP encryption, NAT traversal (STUN/TURN/ICE), and hands you clean audio and video frames — ready to pipe into speech models, recording pipelines, or a full softphone UI.

| | Rust | Go |
|---|---|---|
| **Repository** | [xphone-rust](https://github.com/x-phone/xphone-rust) | [xphone-go](https://github.com/x-phone/xphone-go) |
| **Package** | [crates.io/crates/xphone](https://crates.io/crates/xphone) | [pkg.go.dev/github.com/x-phone/xphone-go](https://pkg.go.dev/github.com/x-phone/xphone-go) |
| **Version** | v0.1.0 | v0.3.1 |

### Highlights

- **Audio**: G.711 (PCMU/PCMA), G.722, Opus, G.729 — PCM frames in/out via channels
- **Video**: H.264, VP8 — mid-call upgrade/downgrade via re-INVITE
- **Security**: SRTP (AES_CM_128_HMAC_SHA1_80), SRTCP, replay protection, key zeroization
- **NAT**: STUN, TURN relay, ICE-Lite
- **Call control**: hold, resume, blind & attended transfer, mute, DTMF (RFC 4733 + SIP INFO)
- **Messaging**: SIP MESSAGE, SUBSCRIBE/NOTIFY, MWI, BLF, presence
- **Testing**: MockPhone & MockCall for unit tests — no real SIP server needed

## Other projects

| Project | Language | What it does |
|---|---|---|
| [xbridge](https://github.com/x-phone/xbridge) | Rust | WebSocket-to-SIP bridge for browser-based voice agents |
| [fakepbx](https://github.com/x-phone/fakepbx) | Go | In-process SIP server for tests. Real SIP over loopback — no Docker, no Asterisk. |
| [fakepbx-rust](https://github.com/x-phone/fakepbx-rust) | Rust | Same concept, for Rust test suites. |
