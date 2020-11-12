-------------------------------------------------------------------------------
# Audio Techniques for Film, Video and Multimedia

**Source**: [Audio Techniques for Film, Video and Multimedia (LinkedIn Learning)](https://www.linkedin.com/learning/audio-techniques-for-film-video-and-multimedia) by Scott Hirsch

<!-- MarkdownTOC -->

- [1. Exporting media from video editor](#1-exporting-media-from-video-editor)
- [2. Stems](#2-stems)
- [3. Templates](#3-templates)
- [4. Importing media to DAW](#4-importing-media-to-daw)
- [5. Loudness](#5-loudness)
- [6. Listening environment](#6-listening-environment)
- [7. Mixing](#7-mixing)

<!-- /MarkdownTOC -->

-------------------------------------------------------------------------------
## 1. Exporting media from video editor

1. **Audio track**
    - .aaf is a file container with all audio data
2. **Video reference**
    - with audio (for comparison and sync check)
    - with timecode burned in (for sync check)
    - with countdown leader
    - with **two-pop** (sync-pop 2s before the first frame) and **tail-pop** (sync-pop 2s after the last frame)


## 2. Stems

**Stems** are categorized, broken-out elements of a soundtrack.

1. **Dialogue** (DX)
2. **Effects** (FX)
3. **Music** (MX)

Stems make project's audio much more flexible and future-proof (i.e., for revisions, reedits, dubbing, music replacement, etc.).

Additional stems:

- voiceover narration (VO)
- natural production sound without dialogue (Nat)
- music and effects combined (M&E)
- music without volume changes (Mix Minus, or MX undipped)


## 3. Templates

Prepare templates for different types of projects:

- general preparation
- audio routing
- default plugins and their settings (EQ, denoise, reverb sends, etc.)


## 4. Importing media to DAW

0. Check sync.
    - two-pop and tail-pop are aligned between the audio track and video reference
    - check with ears (no phasing, no echo)
1. Copy all tracks, lock them in place and hide (for backup).
2. Listen to tracks and mute unuseful parts (too much noise, no sound, etc.).
3. Set up scene markers.
4. Use item FX, plugin settings automation, etc.

**Track layout**:

1. *Checkerboard method* (for narrative, short or feature films; groups of dialogue tracks attached to scenes)

    <p style="text-align:center;"><img src="data/layout checkerboard.png" width="500" title="checkerboard method"></p>

2. *Standard method* (for documentary films; each track has its own settings throughout the whole project)

    <p style="text-align:center;"><img src="data/layout standard.png" width="500" title="standard method"></p>


## 5. Loudness

```
1 LU ~ 1 dB
LUFS = LU to full scale
LKFS = LU to K-weighted full scale
LUFS ~ LKFS
```

1. **Broadcasting and cable**
    - there are regulations and recommendations (e.g., CALM Act 2010, USA) 
    - average: `-24 ± 2 LUFS`
    - True Peak: `-2 LUFS`
2. **Internet**
    - no legal standards
    - average: `-18 — -16 LUFS`
3. **Theatres**
    - no legal standards
    - average `-30 — -27 LUFS`
    - more freedom for dynamic range

- plugins can have different presets for different weighting settings (e.g., ITU 1770)
- make two versions of a project (with a ceiling knob of a limiter): *broadcast level mix* and *web level mix*


## 6. Listening environment

Sound is subjective, so listen to your ears and not to meters when there is a conflict. What is ok for meters might sound harsh, brash, unintelligible, or too quiet in real life.

<p style="text-align:center;"><img src="data/room treatment.png" width="220" title="room treatment"></p>

- speakers placed symmetrically in a room, along the short wall
- equilateral triangle between your head and speakers
- ears at the same height as the tweeters
- acoustic treatment
- speaker loudness calibration (SPL meter phone app)


## 7. Mixing

- Dialogue EQ:

    ```
    0   - 80   Hz  : cut
    80  - 200  Hz  : low end
    200 - 1000 Hz  : boominess and muddiness
      1 - 3    kHz : middle range, honkiness, nasal sounds
      3 - 6    kHz : presence
      6 - 20   kHz : air
    ```

- EQ automation (can use snapshot automation)
- boom vs. lavalier: use what's sounding best or combine mics (but phase align them!)
- add room tone if needed
- fade-ins, fade-outs and crossfades

