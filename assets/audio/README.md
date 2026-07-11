# Audio Assets

These shipping files are derived from user-authored source recordings kept outside the repository at `C:\Users\joshu\Music\Audio\mobile game sounds`. The original files are read-only inputs and are never changed by the build.

Regenerate with a current ffmpeg on `PATH`:

```sh
npm run build:audio
```

Set `FORGEBORN_AUDIO_SOURCE` to use a different source directory. Temporary trimmed WAV files are written only under `art-src/audio-build`.
