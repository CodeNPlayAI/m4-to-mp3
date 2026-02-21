# 🎵 M4A → MP3 変換アプリ（iPad Safari 完全対応版）

ブラウザ内で完結する音声ファイル変換アプリです。  
**サーバー不要・データ送信なし・プライバシー安全**

![対応ブラウザ](https://img.shields.io/badge/iPad_Safari-17+-blue)
![対応ブラウザ](https://img.shields.io/badge/Chrome-88+-green)
![対応ブラウザ](https://img.shields.io/badge/Firefox-78+-orange)
![ライセンス](https://img.shields.io/badge/License-MIT-yellow)

---

## 📱 特徴

- ✅ **iPad Safari で安定動作** - 入念なタッチイベント対策済み
- ✅ **クライアントサイド完結** - サーバー不要、データ送信なし
- ✅ **GitHub Pages 対応** - 静的ホスティングで動作
- ✅ **初学者フレンドリー** - 単一 HTML ファイルで簡単デプロイ
- ✅ **日本語 UI** - わかりやすいインターフェース

---

## 🚀 GitHub Pages へのデプロイ手順

### 方法1: GitHub Web UI からデプロイ（推奨・簡単）

1. **GitHub にログイン**
   - https://github.com にアクセス
   - アカウントがない場合は作成

2. **新しいリポジトリを作成**
   - 右上の `+` → `New repository` をクリック
   - Repository name: `m4a-to-mp3`（任意の名前）
   - Public を選択
   - `Create repository` をクリック

3. **ファイルをアップロード**
   - `uploading an existing file` リンクをクリック
   - `index.html` をドラッグ＆ドロップ
   - `Commit changes` をクリック

4. **GitHub Pages を有効化**
   - リポジトリの `Settings` タブを開く
   - 左メニューから `Pages` を選択
   - Source: `Deploy from a branch`
   - Branch: `main`、`/ (root)` を選択
   - `Save` をクリック

5. **公開 URL を確認**
   - 数分待つと、ページ上部に URL が表示される
   - 例: `https://your-username.github.io/m4a-to-mp3/`

### 方法2: Git コマンドでデプロイ

```bash
# リポジトリをクローン（または新規作成）
git clone https://github.com/your-username/m4a-to-mp3.git
cd m4a-to-mp3

# index.html をコピー
cp /path/to/index.html .

# コミット & プッシュ
git add index.html
git commit -m "Add M4A to MP3 converter"
git push origin main

# GitHub Pages を有効化（Web UI で設定）
```

---

## 📱 iPad での動作確認手順

### 事前準備

1. **iPad の Safari を最新版に更新**
   - 設定 → 一般 → ソフトウェア・アップデート

2. **テスト用 M4A ファイルを用意**
   - iCloud Drive または Files アプリに保存しておく

### 動作確認ステップ

1. **Safari で公開 URL にアクセス**
   ```
   https://your-username.github.io/m4a-to-mp3/
   ```

2. **初回ローディングを確認**
   - 紫色のローディング画面が表示される
   - 「アプリを準備しています...」のメッセージ
   - 初回は 10-30秒かかることがある

3. **ファイル選択をテスト**
   - 「📂 M4Aファイルを選択」ボタンをタップ
   - Files アプリのピッカーが開く
   - M4A ファイルを選択
   - ステータスが「✅ [ファイル名]」に変わることを確認

4. **変換をテスト**
   - 「🔄 MP3に変換」ボタンをタップ
   - プログレスバーが進むことを確認
   - 「⏳ 変換中...」→「🎉 変換完了」に変わる

5. **ダウンロードをテスト**
   - 「💾 MP3をダウンロード」ボタンをタップ
   - ダウンロードが開始される
   - Files アプリの「ダウンロード」フォルダに保存される

### 確認チェックリスト

| チェック項目 | 期待動作 |
|------------|---------|
| ローディング画面 | 表示後、自動で消える |
| ファイル選択ボタン | タップでピッカーが開く |
| ファイル選択後 | ファイル名が表示される |
| 変換ボタン | ファイル選択後に有効になる |
| プログレスバー | 0%→100%で進む |
| ダウンロード | タップでダウンロード開始 |

---

## ⚠️ 想定される不具合と回避策

### 1. 初回ロードが遅い / 失敗する

**原因**: ffmpeg.wasm（約25MB）のダウンロードに時間がかかる

**回避策**:
- Wi-Fi 環境で使用する
- ページを再読み込み（引き下げてリフレッシュ）
- Safari のキャッシュをクリアして再試行

```
設定 → Safari → 履歴とWebサイトデータを消去
```

### 2. ファイル選択ボタンが反応しない

**原因**: iPad Safari のタッチイベント処理の問題

**回避策**:
- ボタンの中心をしっかりタップ
- 長押しではなく短いタップで
- 画面の向きを変えて再試行

### 3. 変換中にアプリがクラッシュする

**原因**: メモリ不足（大きなファイルの場合）

**回避策**:
- 他のアプリを終了してメモリを確保
- 50MB 以下のファイルで試す
- iPad を再起動して再試行

### 4. 変換が途中で止まる

**原因**: Safari がバックグラウンドになった

**回避策**:
- 変換中は Safari を前面に維持
- 画面ロックを解除しておく
- 「画面を閉じないでください」の注意を守る

### 5. ダウンロードボタンが反応しない

**原因**: Blob URL の有効期限切れ、またはメモリ解放

**回避策**:
- 変換完了後、すぐにダウンロード
- ページを再読み込みして再変換

### 6. 変換後の音質が低い

**原因**: ビットレート設定が低い

**回避策**:
- 「256kbps」または「320kbps」を選択
- 元ファイルの音質を超えることはできない点に注意

---

## 🔧 技術的な詳細

### 使用ライブラリ

| ライブラリ | バージョン | 用途 |
|-----------|----------|------|
| ffmpeg.wasm | 0.12.10 | 音声変換エンジン |
| @ffmpeg/core | 0.12.6 | WebAssembly コア |
| @ffmpeg/util | 0.12.1 | ファイル操作ユーティリティ |

### iPad Safari 対策の実装ポイント

```javascript
// 1. 隠し input + ボタン連携
<input type="file" class="file-input-hidden" />
<button id="file-select-btn">ファイルを選択</button>

// 2. タッチイベントの信頼性確保
fileSelectBtn.addEventListener('click', handleFileSelectClick);
fileSelectBtn.addEventListener('touchend', (event) => {
  event.preventDefault();
  handleFileSelectClick(event);
}, { passive: false });

// 3. タッチ操作の CSS 安定化
.file-select-btn {
  touch-action: manipulation;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
}
```

### ファイルサイズ制限

| 制限 | 値 | 理由 |
|-----|---|-----|
| 推奨上限 | 50MB | メモリ安定性 |
| 警告表示 | 100MB | 処理時間の増大 |
| 理論上限 | なし | ただしクラッシュリスク増 |

---

## 📝 ライセンス

MIT License

このアプリは以下のオープンソースプロジェクトを使用しています：
- [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) - LGPL-2.1

---

## 🤝 貢献

Issue や Pull Request を歓迎します！

1. Fork する
2. Feature branch を作成 (`git checkout -b feature/amazing-feature`)
3. 変更をコミット (`git commit -m 'Add amazing feature'`)
4. Push する (`git push origin feature/amazing-feature`)
5. Pull Request を作成

---

## 📞 サポート

問題が発生した場合は、GitHub Issues でお知らせください。

---

**Made with ❤️ for iPad users**
