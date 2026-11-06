# ジャイロOFFカメラ

iPhoneのSafariで開いて使う、傾きセンサー（ジャイロ）を見ないカメラです。
真下に向けて撮っても写真の向きが変わりません。

- 公開URL: https://nekko131.github.io/gyro-off-camera/
- 使い方: 「カメラをはじめる」→ 白いボタンで撮影 → 左下のサムネイル →「◯枚を保存」→ 共有メニューの「画像を保存」
- ホーム画面に追加すると、アプリのように起動できます

## 仕組み

カメラの映像（getUserMedia）をそのまま画像にします。向きの情報（EXIFの回転）は付きません。
画面が回転しているときは、その回転ぶんを戻してから保存するので、本体をどう持っていても同じ向きになります。

## ファイル

- `index.html` … アプリ本体（1ファイル）
- `manifest.webmanifest` / `icon-*.png` … ホーム画面追加用

## 背景除去

- アプリ内：一覧の「まとめて背景を消す」。iPhoneの中でAI（ISNet）が動く。精度は中くらい
- おすすめ：Apple純正の背景削除を複数枚まとめて使うショートカット
  - 入れる: https://nekko131.github.io/gyro-off-camera/背景を削除.shortcut
  - 使う: 写真アプリで複数選択 → 共有 → 「背景を削除」 → 透明PNGが写真アプリに保存される
  - 白背景にしたいときは、アプリの一覧「透明の写真を白背景にする」
- ショートカットの中身: `is.workflow.actions.image.removebackground` → `is.workflow.actions.savetocameraroll`（Macの `shortcuts sign --mode anyone` で署名ずみ）
