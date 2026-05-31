# ASS Quality Checklist

Use this checklist after converting SRT subtitles into ASS.

## Format Checks

- `[Script Info]` exists
- `[V4+ Styles]` exists
- `[Events]` exists
- `Dialogue:` lines exist
- The script resolution matches the output video

## Timing Checks

- Every start time is before its end time
- Adjacent subtitles do not overlap for an unintended long duration
- The final subtitle reaches the later part of the video
- ASS timestamp formatting is valid

## Visual Checks

- No subtitle is too long for the frame
- No subtitle uses too many line breaks
- Subtitles do not render outside the visible area
- Speaker styles do not unexpectedly fall back to `Default`
- Color override tags are closed correctly when used

## Manual Spot Checks

At minimum, review these parts of the rendered test video.

- First minute
- A middle section
- Final minute
- Dense subtitle sections
- Speaker-switching sections

## Report Template

```text
ASS review complete
- Dialogue lines: 120
- Reversed timestamps: 0
- Overlong subtitles: 0
- Subtitles with 3+ lines: 0
- Speaker style issues: 0
```

