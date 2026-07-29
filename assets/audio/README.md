# Audio Assets

These shipping files are derived from user-authored source recordings kept outside the repository at `C:\Users\joshu\Music\Audio\mobile game sounds`. The original files are read-only inputs and are never changed by the build.

Regenerate with a current ffmpeg on `PATH`:

```sh
npm run build:audio
```

Set `FORGEBORN_AUDIO_SOURCE` to use a different source directory. Temporary trimmed WAV files are written only under `art-src/audio-build`.

## `sfx/` — the 33-cue authored library (C70)

`sfx/` holds one mp3 per SFX cue, and **the filename is the cue id**: `src/app/audio.ts`'s `SfxCue` union is the authoritative list, and the loader fetches `assets/audio/sfx/<cue>.mp3`. A renamed or missing file is a 404, which falls back to a synth voice — audible, but not the authored sound. `test/audioSfxSamples.test.ts` asserts every cue in the union has a file on disk.

**`npm run build:audio` does NOT produce this library.** It only knows about `music/`, `ambient/`, and one `sfx/select.mp3` built from `Selecting Sound.mp3` — so running it will **overwrite `sfx/select.mp3` with the older synthesised version** and leave the other 32 cues untouched. Extend `scripts/build-audio.mjs` (or drop its `select.mp3` block) before relying on it again.
