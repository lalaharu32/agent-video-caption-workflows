# agent-video-caption-workflows

Workflow templates for AI agents that create captioned videos.

This repository helps agents move safely from source video to refined subtitles, ASS quality checks, FFmpeg rendering, and final artifact review.

It is designed for workflows that use speech-to-text tools such as Whisper, then ask an AI coding agent to review and prepare subtitles for publishing.

This public version does not include private paths, credentials, real project names, destination URLs, private prompts, or speaker-specific business rules.

## Use Cases

- Give an AI agent a safe, repeatable caption-video workflow
- Prevent missing subtitle sections in long videos
- Review SRT files without damaging numbering or timestamps
- Check ASS subtitles before rendering
- Handle both single-track videos and two-speaker videos
- Keep FFmpeg rendering commands predictable and reviewable

## Workflows

- `workflows/single-track-caption-video.md`
  - A workflow for videos that use one primary audio track
- `workflows/dual-track-caption-video.md`
  - A workflow for interview or dialogue videos with two audio tracks
- `workflows/srt-refinement-checklist.md`
  - A checklist for refining speech-to-text SRT output
- `workflows/ass-quality-checklist.md`
  - A checklist for ASS formatting, timing, styles, and visual review
- `workflows/ffmpeg-rendering.md`
  - FFmpeg command examples for burning ASS subtitles into video

## Core Idea

Captioned video production has small failure modes that are easy to miss:

- the final subtitle block is missing
- timestamps overlap or move backward
- speaker tags disappear midway through the file
- subtitles become too long to read
- line breaks split words or phrases awkwardly
- the rendered video uses a format that does not play reliably

These workflow templates make those checks explicit so an AI agent can follow them step by step.

## Recommended Flow

1. Choose `single-track-caption-video.md` or `dual-track-caption-video.md`
2. Generate an SRT file with your speech-to-text tool
3. Refine the SRT with `srt-refinement-checklist.md`
4. Convert SRT to ASS using your preferred tool
5. Review the ASS file with `ass-quality-checklist.md`
6. Render a short test video with `ffmpeg-rendering.md`
7. Render the final captioned video

## Public Scope

This repository only contains generic workflow templates and sample files.

It intentionally excludes private client data, credentials, service-specific upload steps, real filenames, private prompts, and environment-specific paths.

## License

MIT License.

