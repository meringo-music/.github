# Meringo

**A bit-perfect Jellyfin music client for Android DAPs.**

Primary target: the FiiO M21. Runs on any Android 13+ device.

---

### How to get a build

Closed testing, free in exchange for playback feedback.

1. Join the [closed-testing Google Group](https://groups.google.com/g/meringo-android-closed-testing-group) with the Google account you'll test from.
2. Wait a couple of minutes for Play Store to register your account.
3. Install via the [Play Store closed-testing link](https://play.google.com/apps/testing/app.meringo).

Feedback or questions: **support@meringo.app**

### Where's the code?

Meringo is closed-source. This org hosts things that don't need to ship in the APK — eventually a public changelog, an issue tracker, and any isolated DSP modules that make sense as standalone FOSS. Right now there's nothing public to read.

### What it actually does, briefly

Opens AAudio at the file's native sample rate and bit depth, rides AudioFlinger's MIXER thread as a passthrough under rate-parity + single-client + unity-gain, and flips a UI badge amber the moment any of those conditions breaks (notification chime, ReplayGain non-unity scalar, crossfade animating volume). No claim of AudioFlinger bypass — just an honest description of the conditions under which the passthrough holds.

Parametric EQ in IEEE 754 binary64 end-to-end with TPDF dither at every integer-PCM output stage and a C¹-continuous cubic soft-clip gated on active processing. Cross-source dedup across Local + Jellyfin via a four-arm match chain ending in Chromaprint Hamming distance. Thermal-aware background workers tuned for the M21's Snapdragon 680.

### About

Solo project. No team. No funding. Built for people who care about what 24/192 actually sounds like and who want their Jellyfin library to feel like one library, not a streaming-vs-local schism.
