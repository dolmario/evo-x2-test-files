# Whisper Turbo on the NPU: EVO-X2 test (31 Oct 2026)

Measurement files for the Dolmario Local AI video. No model weights, no private images, no voice-reference audio.

**Setup:** GMKtec EVO-X2, AMD Ryzen AI Max+ 395 (Strix Halo), 64 GB shared memory, Windows. FastFlowLM 1.0.11, `whisper-v3:turbo` on the XDNA2 NPU via the local `/v1/audio/transcriptions` endpoint. Prerecorded synthetic English/German test files with known reference text.

| Test | Result |
|---|---|
| Short English clip | 27.84 s audio in 9.62 s (about 2.9x real time) |
| Short German clip | 29.2 s audio in 11.31 s (about 2.6x) |
| Longer repeated-file phase | 529 s audio in 92 s (about 5.8x real time) |
| Integrated GPU during that phase | 3.9 % average, NPU 50.3 % (HWiNFO) |

Spelling differences only: audio books / audiobooks and Haus-Assistenten / Hausassistenten. Clean synthetic voices, not a noisy meeting; no live captions.

HWiNFO values describe the processor package, not wall power or isolated NPU/GPU power. Different runtimes and quantisations are not a hardware efficiency ranking.

Files: `METHODOLOGY.txt`, `NPU-*`, `GPU-*`, `WHISPER-TRANSCRIPT-*.json`, `REFERENCE-TEXTS.json`, `SOURCE-PROOF.json`. Integrity: see `SHA256SUMS.txt`.

Affiliate links in the video description are marked as advertising (PartnerBoost).

---

## Deutsch
Messdateien zum Dolmario-Local-AI-Video. Keine Modellgewichte, keine privaten Bilder, keine Stimm-Referenzen.

**Aufbau:** GMKtec EVO-X2, Ryzen AI Max+ 395, 64 GB gemeinsamer Speicher, Windows. FastFlowLM 1.0.11, `whisper-v3:turbo` auf der NPU. Vorab aufgenommene synthetische Testdateien mit bekanntem Text.

Kurzer englischer Clip etwa 2,9-fach Echtzeit, kurzer deutscher etwa 2,6-fach, längere wiederholte Dateiphase etwa 5,8-fach (529 s Audio in 92 s). Die integrierte GPU lag dabei bei 3,9 % im Mittel, die NPU bei 50,3 %. Unterschiede nur in der Schreibweise. Saubere synthetische Stimmen, kein verrauschtes Meeting, keine Live-Untertitel.

HWiNFO-Werte zeigen das Prozessorpaket, keine Steckdosen- oder Einzelwerte von NPU/GPU. Prüfsummen: `SHA256SUMS.txt`.
