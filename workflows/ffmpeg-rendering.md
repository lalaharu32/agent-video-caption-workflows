# FFmpeg字幕焼き込み

ASS字幕を動画に焼き込むためのFFmpegコマンド例です。

## 基本コマンド

```bash
ffmpeg -i "input.mp4" -filter_complex "[0:v]scale=1920:1080,fps=30,format=yuv420p,ass='captions.ass'[v]" -map "[v]" -map 0:a -c:v libx264 -crf 23 -preset medium -c:a copy "output_captioned.mp4" -y
```

## 別音声を使う場合

```bash
ffmpeg -i "input.mp4" -i "final_audio.mp3" -filter_complex "[0:v]scale=1920:1080,fps=30,format=yuv420p,ass='captions.ass'[v]" -map "[v]" -map 1:a -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 160k "output_captioned.mp4" -y
```

## 短いテスト出力

最初の3分だけ確認する場合の例です。

```bash
ffmpeg -i "input.mp4" -filter_complex "[0:v]scale=1920:1080,fps=30,format=yuv420p,ass='captions.ass'[v]" -map "[v]" -map 0:a -c:v libx264 -crf 23 -preset medium -c:a copy -t 180 "test_3min.mp4" -y
```

## 確認事項

- `format=yuv420p` を入れて、一般的な動画プレイヤーで再生しやすくする
- テスト出力で字幕位置と音声ズレを確認してから本番を書き出す
- ASSファイルのパスに空白がある場合、引用符の扱いに注意する
- 出力ファイル名を固定名にせず、入力ファイル名や日付から分かる名前にする

