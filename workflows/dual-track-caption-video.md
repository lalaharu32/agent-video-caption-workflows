# Dual-Track Captioned Video Workflow

Use this workflow for interviews, dialogues, or other videos with two audio tracks.

## 1. Check Inputs

Confirm the following before starting.

- The source video has two audio tracks
- You know which track belongs to which speaker
- The final audio source is decided
- Speaker tags use generic names

Recommended generic tags:

```text
[SpeakerA]
[SpeakerB]
```

## 2. Extract Audio Tracks

```bash
ffmpeg -i "input.mp4" -map 0:a:0 -c:a copy "speaker_a.m4a" -y
ffmpeg -i "input.mp4" -map 0:a:1 -c:a copy "speaker_b.m4a" -y
```

## 3. Generate Reference SRT Files

Generate reference SRT files from each speaker track.

```text
speaker_a.srt
speaker_b.srt
```

Reference SRT files are used for speaker attribution. They do not have to be the final timing source.

## 4. Generate Main SRT

Generate the main SRT from the final audio source.

```text
main.srt
```

## 5. Add Speaker Tags

Use the reference SRT files to add speaker tags to the main SRT.

```text
1
00:00:02,000 --> 00:00:04,500
[SpeakerA]Welcome to the session.

2
00:00:04,600 --> 00:00:07,000
[SpeakerB]Thanks for having me.
```

## 6. Refine SRT

Use `srt-refinement-checklist.md`.

Do not remove speaker tags while editing text.

## 7. Convert to ASS

Map speaker tags to ASS styles.

Example:

```text
[SpeakerA] -> StyleA
[SpeakerB] -> StyleB
```

## 8. Review ASS

Use `ass-quality-checklist.md`.

Check timing, line length, visual layout, and speaker style consistency.

## 9. Render Captioned Video

Use `ffmpeg-rendering.md` as a starting point.

Render a short test clip first.

## 10. Final Review

Confirm these items.

- Speaker tags were preserved until ASS style conversion
- Speaker colors remain consistent throughout the video
- Overlapping speech did not break the subtitles
- The final subtitle timestamp reaches the end of the content

