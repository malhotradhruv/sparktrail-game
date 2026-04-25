# SparkTrail Deployment Setup

This guide explains how to host **SparkTrail: Photon Odyssey** on **CTFd** (or a similar CTF platform such as rCTF/FbCTF with equivalent challenge import features).

## 1. Upload Challenges (Markdown + Input Files)

1. Create challenge entries `C1` through `C11` in your platform admin panel.
2. For each challenge, paste the corresponding markdown from:
   - `challenges/C1/...` through `challenges/C11/...`
3. Upload all required input artifacts per challenge:
   - CSV/TXT files, PNG files, WAV files, and any other referenced assets.
4. Ensure each challenge uses the expected flag format (`SPARK{...}`).
5. Keep Roman numeral hints (`I` to `X`) visible in challenge descriptions where applicable.

## 2. Configure Scoring

Use this scoring policy:

- Easy: `100`
- Medium: `250-400`
- Hard: `500`
- Final Boss: `1000`

Recommended mapping:

- `C1-C2` -> Easy (`100` each)
- `C3-C6` -> Medium (`250`, `300`, `350`, `400`)
- `C7-C10` -> Hard (`500` each)
- `C11` -> Final Boss (`1000`)

If your platform supports dynamic scoring, set minimum/maximum values to preserve this range behavior while still keeping these target values as defaults.

## 3. Add Intro/Outro Screens

1. Upload the intro image:
   - `assets/intro_screen.png`
2. Upload the outro image:
   - `assets/outro_screen.png`
3. Add narrative pages or custom HTML blocks using:
   - `docs/intro_narrative.md`
   - `docs/outro_narrative.md`
4. Place intro content on the landing/home page and outro content on completion/win page (or as a final challenge completion message).

## 4. Enable Leaderboard Integration

1. Use the provided script to generate leaderboard data:
   - `python scripts/leaderboard.py`
2. This exports:
   - `leaderboard.json`
3. Connect `leaderboard.json` to your frontend widget/page:
   - Top players
   - Score totals
   - Flags collected
4. Configure periodic refresh (for example every 30-60 seconds) or regenerate the JSON after each submission event.

## Sample `config.json` Snippet

```json
{
  "game": "SparkTrail: Photon Odyssey",
  "flagFormat": "SPARK{...}",
  "challengeCount": 11,
  "scoring": {
    "Easy": 100,
    "Medium": [250, 300, 350, 400],
    "Hard": 500,
    "FinalBoss": 1000
  },
  "assets": {
    "introScreen": "assets/intro_screen.png",
    "outroScreen": "assets/outro_screen.png",
    "masterKey": "assets/master_key.png"
  },
  "leaderboard": {
    "enabled": true,
    "source": "leaderboard.json"
  }
}
```

## Deployment Checklist

- All 11 challenges imported
- All challenge input files uploaded and linked
- Scoring verified against tier policy
- Intro/outro assets and narratives published
- Leaderboard JSON generation and frontend binding verified
