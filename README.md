# Rocky Speaks 🕷️

Translate English into "Rocky" sonic language (the Eridian alien from Andy
Weir's *Project Hail Mary*) and send messages between two devices **through
sound alone** — no network, no server, no backend.

**Live app:** https://chrisbot2026.github.io/rocky-speak/

## How to use it

1. Open the link above on two iPhones (or any devices with a speaker + mic).
2. Device A: **Speaker** tab → type a message → *Make Rocky Speak*.
3. Device B: **Listener** tab → *Start Listening* → hold it near device A.
4. The message appears character by character as Rocky sings it.

## How it works (v2 protocol)

- Each character maps to a **dual-tone chord** — one tone from a low set
  (720–1280 Hz), one from a high set (1600–2440 Hz), DTMF-style. 64 symbols
  cover a–z, 0–9, space, punctuation, plus START/END framing markers.
- Eridian decoration voices (sub-bass swells, vibrato, shimmer overtones,
  mood-driven tempo) ride on top but never touch the signal tones, so the
  alien sound stays fully decodable.
- The listener runs a live FFT on the mic, watches the 16 signal
  frequencies, and votes each chord into a character. Run-based decoding
  with a decaying-peak level tracker survives room echo, noise, and
  distance. Pure client-side math — Web Audio API only.
- A built-in 🧪 loopback self-test (Listener tab) renders a message through
  an OfflineAudioContext and decodes it back, so you can verify the whole
  pipeline without a microphone.

## Why hosted

iOS Safari only allows microphone access on real HTTPS pages — not plain
HTTP, not file previews. GitHub Pages provides that; the app itself is a
single static HTML file.

*Fan project for the Serrano Men's Book Club · 2026*
