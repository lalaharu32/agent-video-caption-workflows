# Project Story

agent-video-caption-workflows started from a practical problem: AI agents can help with captioned video production, but the workflow has many small places where quality can break.

Speech-to-text output must be refined without breaking subtitle numbers or timestamps. ASS files must be checked before rendering. FFmpeg commands must preserve compatibility. Long videos need special care so the second half of the subtitles is not accidentally dropped.

This repository turns those practical checks into public, reusable workflow templates.

## Why Codex Helps

Codex can improve this project by reviewing workflow steps, adding missing failure cases, improving FFmpeg examples, expanding sample SRT and ASS files, and keeping the documentation clear.

Because the project is itself a set of workflows for AI agents, it is a natural fit for Codex-assisted maintenance.

