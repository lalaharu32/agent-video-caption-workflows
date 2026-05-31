# FFmpeg Rendering

Use these examples to burn ASS subtitles into a video.

## Basic Command

```bash
ffmpeg -i "input.mp4" -filter_complex "[0:v]scale=1920:1080,fps=30,format=yuv420p,ass='captions.ass'[v]" -map "[v]" -map 0:a -c:v libx264 -crf 23 -preset medium -c:a copy "output_captioned.mp4" -y
```

## Use Separate Final Audio

```bash
ffmpeg -i "input.mp4" -i "final_audio.mp3" -filter_complex "[0:v]scale=1920:1080,fps=30,format=yuv420p,ass='captions.ass'[v]" -map "[v]" -map 1:a -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 160k "output_captioned.mp4" -y
```

## Short Test Render

Render the first three minutes before rendering the full video.

```bash
ffmpeg -i "input.mp4" -filter_complex "[0:v]scale=1920:1080,fps=30,format=yuv420p,ass='captions.ass'[v]" -map "[v]" -map 0:a -c:v libx264 -crf 23 -preset medium -c:a copy -t 180 "test_3min.mp4" -y
```

## Checks

- Keep `format=yuv420p` for broad playback compatibility
- Run a short test render before the final render
- Quote ASS paths carefully when paths contain spaces
- Avoid fixed output filenames that can overwrite another project
- Verify subtitle position and audio sync in the rendered output

