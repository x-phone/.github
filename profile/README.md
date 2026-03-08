# x-phone

Telephony libraries for AI voice agents and embedded softphones. SIP, RTP, codecs, and clean PCM audio — no PBX required.

## xphone

Embed real phone calls in any application. xphone handles SIP signaling, RTP media, codecs, and call state so you can focus on what your application does with the audio.

| Language | Repository | Package |
|---|---|---|
| **Rust** | [xphone-rust](https://github.com/x-phone/xphone-rust) | [crates.io/crates/xphone](https://crates.io/crates/xphone) |
| **Go** | [xphone-go](https://github.com/x-phone/xphone-go) | [pkg.go.dev/github.com/x-phone/xphone-go](https://pkg.go.dev/github.com/x-phone/xphone-go) |

## Testing tools

| Project | Language | What it does |
|---|---|---|
| [fakepbx](https://github.com/x-phone/fakepbx) | Go | In-process SIP server for tests. Real SIP over loopback — no Docker, no Asterisk. |
| [fakepbx-rust](https://github.com/x-phone/fakepbx-rust) | Rust | Same concept, for Rust test suites. |
