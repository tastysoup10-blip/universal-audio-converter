# Universal Audio Converter

A static, browser-based audio converter powered by FFmpeg.wasm. Audio files are processed locally in the browser; this project does not upload files to a server.

## Run locally

Because the app uses JavaScript modules, open it through a local web server rather than opening `index.html` as a file. For example, with Python installed:

```bash
python -m http.server 8000
```

Then visit http://localhost:8000.

## Deploy with GitHub Pages

1. Open the repository's **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **main** and **/(root)**, then save.
4. Wait for the Pages deployment to finish.

The app is designed to run from a repository subpath (for example, `https://USERNAME.github.io/universal-audio-converter/`).

## Formats

The interface offers MP3, M4A/AAC, WAV, FLAC, AAC, OGG/Vorbis, Opus, and AIFF output. FFmpeg can decode many input formats, but exact support depends on the codecs included in the browser build. DRM-protected files are not supported.

## Notes

- The first conversion downloads the FFmpeg WebAssembly engine, so it may take a little while.
- Large files can exceed browser memory limits, especially on lower-memory devices.
- Converting a lossy source (such as MP3) to a lossless format (such as FLAC or WAV) cannot restore audio quality that was already lost.
- This project uses the single-threaded FFmpeg core build to avoid requiring cross-origin isolation headers.
