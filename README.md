# カットリスト撮影（cutlist-camera）

出張フォトグラファーが一眼の横で使う、撮り忘れ防止・撮影進行管理PWA。
カメラ機能は持たず、撮影前に決めたカットを現場で1つずつ潰していくためのアプリです。

- アプリ名：カットリスト撮影（ホーム画面名：カットリスト）
- リポジトリ：hanaphoto/cutlist-camera
- 公開URL（予定）：https://hanaphoto.github.io/cutlist-camera/
- 仕様書：`~/workspace/cutlist-app/カットリスト撮影アプリ_仕様書_v0.1.md`

## 使い方（要点）
1. 案件を作り、ジャンルを選ぶとテンプレートのカットが入る。追加・削除・並べ替え（↑↓）で整える
2. 撮影中モードで「撮影済みにする（要確認）」を押していく
3. 一眼の再生で確認できたら、カット一覧で「確認完了」まで進める
4. 終わったら撮影後チェック（人数・目つぶり・バックアップ等）→ CSV / JSON書き出し

## ファイル
- `index.html` 本体（フレームワーク・外部ライブラリ無し、保存は localStorage）
- `manifest.webmanifest` / `sw.js`（キャッシュ名 cutlist-v1）
- `icon-180.png` / `icon-192.png` / `icon-512.png` / `icon-maskable-512.png`
  - デザイン：紺地に白いリスト用紙＋琥珀色のチェック円。`make_icons.py` で再生成可

## 公開時の注意
- 公開対象は `index.html / manifest.webmanifest / sw.js / icon-*.png / README.md` のみ
- `make_icons.py`（アイコン生成用・内部パスを含む）と、書き出したJSON／CSVバックアップはリポジトリに入れない
- アプリのコードに個人情報は含まれない。利用時に入力した案件名・メモは端末の localStorage にだけ保存され、外部送信の仕組みは無い

## 状態
- v0.1 MVP公開済み（2026-11-18、初回コミット b401663、https://hanaphoto.github.io/cutlist-camera/ で表示確認済み）。iPhone実機確認は未実施
- 並べ替えはドラッグではなく ↑↓ ボタンで実装（仕様の「並べ替えができる」を満たす簡易形）
