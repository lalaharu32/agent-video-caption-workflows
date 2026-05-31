# Single-Track Captioned Video Workflow

Use this workflow when a video has one primary audio track.

## 1. Check Inputs

Confirm the following before starting.

- The source video or source audio exists
- The duration matches the expected content
- Work files and final artifacts are kept in separate directories
- Original source files will not be overwritten

## 2. Extract Audio

Example command:

```bash
ffmpeg -i "input.mp4" -map 0:a:0 -c:a copy "audio_track.m4a" -y
```

Check available audio streams:

```bash
ffprobe -show_streams -select_streams a "input.mp4"
```

## 3. Generate SRT

Use your preferred speech-to-text tool to generate an SRT file.

Example output name:

```text
audio_track.srt
```

## 4. Refine SRT

Use `srt-refinement-checklist.md`.

The goal is to improve readability without damaging subtitle numbers, timestamps, or meaning.

## 5. Convert SRT to ASS

Convert the refined SRT into ASS using your preferred converter.

ASS allows you to control font, position, outline, color, and line breaks.

## 6. Review ASS

Use `ass-quality-checklist.md`.

Check visual layout, long subtitles, timestamp overlaps, and missing final subtitles.

## 7. Render Captioned Video

Use `ffmpeg-rendering.md` as a starting point.

Render a short test clip before rendering the final video.

## 8. Final Review

Confirm these items.

- Subtitles appear at the beginning and end of the video
- The second half of the video still has subtitles
- Audio and subtitles are reasonably aligned
- Seeking works in common video players
- The final output was not confused with an intermediate file

