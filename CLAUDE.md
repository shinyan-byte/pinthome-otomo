# CLAUDE.md — おとも内見 LP プロジェクト

このファイルは Claude Code 向けのプロジェクト固有ルールです。
作業前に必ず一読してください。詳細な経緯は `HANDOFF.md` を参照。

## プロジェクトのスタンス

- **対象ユーザー**：石井優香（@yuka_pinthome）の Instagram 発信を**すでに見ているフォロワー**
- **トーン**：説得より共感、理屈より体感。ただし「友達口調」になりすぎず「ですます」基調を守る
- **ブランドカラー**：濃紺 #0f172a、アクセント #1d4ed8、LINE緑 #06c755
- **構造**：単一HTMLファイル（`index.html`）。ビルド工程・フレームワークなし

## 言語ルール

### 必ず使う表現
- 「物件情報」（**「物件URL」はNG**）
- 「内見日までに〜お渡しします」（**「その日のうちに」はNG**）
- 「ご自身で物件を探された場合でもかかる費用」（仲介手数料の説明）
- 「価値観・ライフステージの近い同じ担当者が伴走」

### 使わない表現（同業者コンフリクト・誤解を生むもの）
- SUUMO / HOMES などポータルサイトの**具体名**
- 「ポータルサイトから問い合わせると…」のような業界批判
- 「どの仲介会社でも同じ金額」（過大表現）
- 「内見後の営業は一切しません」の**過剰な繰り返し**（1〜2回まで）
- 「PINT HOMEが特別高いわけではありません」のような防衛表現
- 「絶対」「100%」「No.1」など景品表示法に抵触し得る最上級表現

### トーン
- 一人称：「私」
- 絵文字：最小限。`☀️` `☺️` を Mini-Speaker と Profile メッセージ部分のみ
- 体言止めの多用を避け、文を完結させる
- カジュアルなオノマトペ（ぽんと／ぐっと／ぱっと）は不使用

## 編集ルール

### 構造変更
- セクション順序の変更は、ロジックの流れ（共感→根拠→呼びかけ）を崩さない
- 重複セクションの統合・分離は HANDOFF.md の構成表を更新

### CSS
- すべての PC 用メディアクエリは `@media (min-width: 99999px)` に**意図的に無効化済**
  → モバイル幅 430px 固定のため。**復活させない**
- カラーは CSS 変数（`var(--ink)` 等）を優先
- アニメーション追加時は `html.js-anim` プレフィックスと `prefers-reduced-motion` 対応を必ず入れる

### アニメーション
- 既存パターン：`.reveal`（単体fade）／`.reveal-stagger > *`（子要素を順次fade）
- 新規セクション追加時は適切な方を付与
- IntersectionObserver の発火後は `unobserve` する（一度きり）

### Hero 動画
- `assets/hero.mp4` は約 33MB。差し替え時は **5〜10MB を目標**に圧縮（Handbrake等）
- 必ず `<source>` + `<img>` のフォールバック構造を維持
- `autoplay muted loop playsinline preload="metadata"` 属性は必須

## やってはいけないこと

| 操作 | 理由 |
|---|---|
| README.md の自動生成 | ユーザーが明示要求した場合のみOK |
| 個人情報を含む状態でPublic公開（リポジトリ可視性変更） | ユーザーの明示承認必須。Claude Code 側もブロックされる |
| Voice（お客様の声）の言い回し改変 | 原文尊重。誤字以外は触らない |
| 「物件URL」「ポータルサイト」「営業しません強調」を復活させる | 過去に修正済み。再発NG |
| `@media (min-width: xxx)` の min-width を 99999px 未満に戻す | モバイル幅固定設計の根幹 |

## 確認方法

```bash
# ローカルプレビュー
cd /Users/snynkmt/Downloads/pinthome-otomo
python3 -m http.server 8000
# → http://localhost:8000
```

または `.claude/launch.json` に `pinthome-otomo` サーバー定義済み。

## 主要なファイルパス

- LP本体：`index.html`
- 画像：`assets/`
- 引き継ぎ詳細：`HANDOFF.md`
- 元LP参考（旧版）：https://pinthome-house-viewing.lp.ina-gr.com/
- デザインテイスト元：`/Users/snynkmt/Desktop/housing-seminar/index.html`（PINT HOME 別LP、同じデザイントークン使用）

## 連絡先・URL

- LINE 友だち追加：`https://il9fo0d8.autosns.app/addfriend/s/VI9Jw20ZLk/@074himyv`
- Instagram：https://www.instagram.com/yuka_pinthome/
- GitHub：https://github.com/shinyan-byte/pinthome-otomo

---

質問や不明点があれば、まずユーザー（石井さん）に確認してください。
特に「言葉遣いの細部」「業界ルールに関わる表現」「個人情報公開可否」は**必ず確認**。
