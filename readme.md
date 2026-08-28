# Edge-TTS Playground

A Jupyter notebook UI for exploring Microsoft Edge's free text-to-speech
voices via the [`edge-tts`](https://github.com/rany2/edge-tts) Python library.
Pick a voice from a dropdown, adjust rate/pitch, type some text, and generate
an MP3 with a matching SRT subtitle file — all from `ipywidgets` controls, no
web frontend required.

## Features

- Voice list pulled live from `edge_tts.list_voices()`, filterable by locale
- Dropdown labeled with each voice's Microsoft-provided personality tags
  (e.g. "Andrew · Male · Warm, Confident") instead of just the raw voice ID
- Rate (%) and pitch (Hz) sliders
- Inline audio playback after generation
- Optional saving of the MP3 + SRT to `./audio/`; otherwise both are deleted
  after playback, with the SRT still downloadable as a self-contained
  base64 link

## Setup

```bash
uv sync
```

Open `edge_tts_playground.ipynb` in VS Code (with the
[Jupyter extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)),
select the `.venv` created by `uv sync` as the kernel, and run the cells top
to bottom.

## Notes

- `edge-tts` talks to the same backend Microsoft Edge uses for its "Read
  Aloud" feature — no API key required.
- If synthesis fails with a connection or 403 error, the Edge endpoint
  contract may have shifted; try `uv lock --upgrade-package edge-tts`.
