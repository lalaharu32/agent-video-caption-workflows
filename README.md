# agent-video-caption-workflows

AIエージェントが、動画素材から字幕付き動画を作る作業を安全に進めるためのワークフロー集です。

Whisperなどで生成したSRTの推敲、ASS変換後の品質確認、字幕焼き込み、成果物整理までを、チェックリスト形式で扱います。

この公開版には、個人環境の絶対パス、認証情報、実際の動画名、配信先情報、非公開プロンプト、特定話者の固有情報は含めません。

## 想定する用途

- AIエージェントに字幕動画制作を依頼するときの手順書
- SRT推敲の抜け漏れ防止
- ASS変換後の表示崩れチェック
- FFmpegで字幕を焼き込む前の安全確認
- 1トラック動画と2トラック対談動画の作業分岐

## ワークフロー

- `workflows/single-track-caption-video.md`
  - 1つの音声トラックを使う字幕動画向けです
- `workflows/dual-track-caption-video.md`
  - 2つの音声トラックを扱う対談動画向けです
- `workflows/srt-refinement-checklist.md`
  - Whisper出力などのSRTを人間が読みやすい字幕に整えるための確認項目です
- `workflows/ass-quality-checklist.md`
  - ASS変換後の表示、改行、タイムスタンプを確認するための項目です
- `workflows/ffmpeg-rendering.md`
  - 字幕焼き込み動画を作るためのFFmpegコマンド例です

## 大事な考え方

字幕動画制作では、自動化だけでは拾いきれない小さな事故が起きます。たとえば、後半の字幕欠落、タイムスタンプ重複、長すぎる字幕、話者タグの消失、誤認識の見落としです。

このワークフロー集は、AIエージェントがそれらを見落としにくくするために、工程ごとの確認事項を明確にします。

## 使い方

1. 動画の種類に合わせて `single-track-caption-video.md` か `dual-track-caption-video.md` を選びます
2. SRT生成後に `srt-refinement-checklist.md` で推敲します
3. ASS変換後に `ass-quality-checklist.md` で表示品質を確認します
4. `ffmpeg-rendering.md` のコマンド例をもとに字幕付き動画を書き出します

## 公開範囲

このリポジトリは、実運用で得た知見のうち、公開しても問題が少ない汎用ワークフローだけをまとめたものです。

個別案件の保存先、音量の固定値、配信先、認証、個人名、固有ジャンルに依存するルールは含めません。

## ライセンス

MIT Licenseです。

