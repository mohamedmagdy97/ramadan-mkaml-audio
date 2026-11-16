# ramadan-mkaml-audio

Narrations for «رمضان مكمّل» (story of each prophet, biography of the ten and the companions),
served from GitHub Pages so they don't add to the app's install size. The app downloads a file on
the first «اسمع» and keeps it on the device; after that it plays offline.

- URL: `https://mohamedmagdy97.github.io/ramadan-mkaml-audio/stories/<name>.m4a`
- Names: `story_<id>` (prophets), `bio_<id>` (the ten + companions), as in
  `docs/audio/stories_recording_script.md` in the app repo.
- Format: AAC 32 kbps, mono, 24 kHz, -16 LUFS (≈ 240 KB per minute).

## Adding recordings

From the app repo (this repo cloned next to it as `../ramadan-mkaml-audio`):

```bash
python3 tool/audio/install_story_clips.py tool/audio/stories_src   # wav → stories/*.m4a + StoryClips.names
cd ../ramadan-mkaml-audio && git add stories && git commit -m "stories: add …" && git push
```

Push here **before** releasing an app build that lists the new names, or «اسمع» will fail until the
file is up (the button just stops; nothing breaks).

## Rules

- Never replace a published file with different content under the same name — devices that already
  downloaded it keep the old one. Use a new name (e.g. `story_nuh_v2`) and regenerate `StoryClips`.
- Narrations only: no Quran recitation by TTS, no ayat read by anyone but a reciter. The story page
  shows ayat from the app's bundled dataset.
- No personal data, no analytics. GitHub Pages sees the request IP like any web server
  (stated in the app's privacy page).
