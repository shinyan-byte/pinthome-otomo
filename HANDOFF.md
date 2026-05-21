# 引き継ぎ書 — おとも内見 LP

## プロジェクト概要

| 項目 | 内容 |
|---|---|
| プロダクト名 | **おとも内見** (by PINT HOME) |
| 担当者 | 石井 優香 / [@yuka_pinthome](https://www.instagram.com/yuka_pinthome/) |
| 運営会社 | INA&Associates株式会社 |
| ファイル形式 | Vanilla HTML + CSS + JavaScript（フレームワークなし） |
| 想定デバイス | スマートフォン専用（PCでも430px幅でセンタリング表示） |
| GitHub | https://github.com/shinyan-byte/pinthome-otomo（**現在private**、Public化＋GitHub Pages有効化はユーザー実行待ち） |
| 本番URL候補 | `https://shinyan-byte.github.io/pinthome-otomo/`（Pages有効化後） |
| LINE CTA URL | `https://il9fo0d8.autosns.app/addfriend/s/VI9Jw20ZLk/@074himyv` |

## ターゲット・コンセプト

- **対象ユーザー**：石井さんのInstagram発信を既に見ているフォロワー（ウォームリード）
  - LPに来る人は「ゆかさんを既に知っている」前提
  - 新規説得型ではなく、**「一緒に内見に行きたい」と思わせるワクワク重視**の構成
- **訴求軸**：「何を探すか」より「**誰と探すか**」
- **メインターゲット属性**：子育て世代のご家族／共働きご夫婦／はじめての住宅購入
- **対応エリア**：関東圏（東京23区・神奈川東部・千葉/埼玉の一部）

## ファイル構成

```
pinthome-otomo/
├── index.html           # メインLPファイル（単一ページ・約1300行）
├── HANDOFF.md           # 本ファイル
├── CLAUDE.md            # Claude Code 向けプロジェクトルール
├── .gitignore
└── assets/
    ├── hero.mp4         # Hero背景動画（33MB、圧縮検討）
    ├── yuka-hero.jpg    # Heroポスター画像／videoフォールバック
    ├── yuka-avatar.jpg  # Profile・MiniSpeakerアバター
    ├── why.png          # Whyセクションの点と線イラスト
    ├── prep-report.png  # Prepセクションの査定報告書イメージ
    ├── report.jpg       # （現在未使用）
    ├── market.jpg       # （現在未使用）
    ├── property.jpg     # （現在未使用）
    └── why.jpg          # （現在未使用）
```

`report.jpg / market.jpg / property.jpg / why.jpg` は構成変更により未使用。整理可（ただし `.git`履歴には残る）。

## セクション構成（上から順）

| # | セクション | id | 内容 |
|---|---|---|---|
| 1 | Header | – | ロゴ「おとも内見 by PINT HOME」＋ LINE CTA |
| 2 | Hero | `#top` | 動画背景 + 「知ってる人と、一緒に見に行く。」 |
| 3 | Mini-Speaker | – | さりげない自己紹介バンド（石井優香） |
| 4 | Concept | `#concept` | おとも内見とは（3カード） |
| 5 | Eligibility | `#eligibility` | 対応できる方／難しいケース |
| 6 | Mid-CTA | – | LINEで物件情報を送る |
| 7 | Trust | `#trust` | 「不動産屋さんへの問い合わせって、ハードル高いですよね。」 |
| 8 | Concern | `#concern` | FOR YOU（5項目の悩み） |
| 9 | Why | `#why` | 探し方が"点"のままだから（点と線イラスト） |
| 10 | Change | `#change` | WHAT CHANGES（Before/After 4枚） |
| 11 | Voice | `#voice` | ご一緒した方の声（3件） |
| 12 | Profile | `#speaker` | 石井優香プロフィール詳細 |
| 13 | Instagram | `#instagram` | Instagramへのリンクボックス |
| 14 | Prep | `#prep` | 査定報告書イメージ（フル幅画像1枚） |
| 15 | How It Works | `#how` | 他にも一緒にできること（4項目） |
| 16 | Price | `#price` | 料金（2行テーブル + 補足） |
| 17 | Flow | `#flow` | 内見の流れ（3STEP） |
| 18 | FAQ | `#faq` | よくあるご質問（6問） |
| 19 | Final CTA | `#cta` | 物件情報、お待ちしております |
| 20 | Footer | – | INA&Associates 著作 |

## 技術仕様

### モバイル幅固定の仕組み
- `body { max-width: 430px; margin: 0 auto }` でスマホ幅にロック
- すべてのPC用メディアクエリ `@media (min-width: xxx)` の値を **99999px** に書き換えて無効化
- `html { background: #0a1020 }` でフレーム外の暗背景
- `.sticky-cta` は `left:50%; transform: translate(-50%, ...)` で中央寄せ固定

### アニメーション
- IntersectionObserver で `.reveal` / `.reveal-stagger` クラスに `in-view` を付与
- `html.js-anim` がCSSセレクタに付くことで、**JSオフ時はフォールバック表示**（最初から表示される）
- `prefers-reduced-motion: reduce` 設定の人はアニメーション完全無効化
- Hero 動画は `autoplay muted loop playsinline preload="metadata"`、`<source>` 失敗時は `<img>` フォールバック

### デザイントークン（CSS変数）
```css
--ink:#0f172a       /* メイン濃紺 */
--accent:#1d4ed8    /* アクセントブルー */
--line-app:#06c755  /* LINEブランドカラー */
--bg-soft:#f5f7fa   /* セクション背景 */
--warm:#fef7e8      /* 引用・暖色ブロック */
```

### フォント
- 日本語：Noto Sans JP / Hiragino Kaku Gothic ProN / Yu Gothic
- 欧文：Inter
- `font-feature-settings: "palt" 1`（プロポーショナル詰め）

## 重要な意思決定・表現ルール

### ✅ Do（守るルール）
- **「ですます」基調＋謙譲表現**を維持
- 絵文字は最小限（☀️/☺️ など、Mini-Speaker・Profileメッセージのみ）
- お客様の声は**原文のまま**残す（言い回しを勝手に変えない）
- 業界ルール（他社問い合わせ済み物件はサポート不可）の説明は維持
- 料金は「**ご自身で探した場合でも、不動産会社を通せばかかる費用**」と表現

### ❌ Don't（絶対NG表現）
| NG表現 | 理由 | 代替 |
|---|---|---|
| 「物件URL」 | 一律で表現統一済 | **「物件情報」** |
| 「SUUMO」「HOMES」具体名 | 同業者コンフリクト | 「気になる物件」など中立に |
| 「ポータルサイトから問い合わせると…」 | 業界批判と取られる | 削除済 |
| 「どの仲介会社でも同じ金額」 | 過大表現（値引きあり） | 「不動産会社を通せばかかる費用」 |
| 「その日のうちに事前レポート完了」 | 実態と異なる | 「内見日までに整えてお渡し」 |
| 「営業しません」の繰り返し | 押しすぎ感 | 1〜2回までに留める |

### 削除済み機能・要素（再追加注意）
- KPI数値ブロック（伴走スタイル/24時間/0円）
- 「営業しないお約束」の冗長な強調
- FAQの「本当に営業しないんですか？」「住宅ローン相談だけ可？」「平日昼間しか動けない」「なぜ営業しないで成立？」
- 「特別高いわけではありません」（防衛的表現）

## 開発・確認方法

### ローカルプレビュー
```bash
cd /Users/snynkmt/Downloads/pinthome-otomo
python3 -m http.server 8000
```
→ http://localhost:8000

または `.claude/launch.json` 設定済みで Claude Code の `preview_start` でも起動可。

### Git
```bash
cd /Users/snynkmt/Downloads/pinthome-otomo
git remote -v  # origin: https://github.com/shinyan-byte/pinthome-otomo
```

## 残課題 / TODO

### 🔴 ユーザー側で実行待ち
1. **GitHubリポジトリのPublic化**（個人情報公開のためClaudeから実行不可）
   ```bash
   gh repo edit shinyan-byte/pinthome-otomo --visibility public --accept-visibility-change-consequences
   ```
2. **GitHub Pages有効化**
   ```bash
   gh api -X POST repos/shinyan-byte/pinthome-otomo/pages -f 'source[branch]=main' -f 'source[path]=/'
   ```

### 🟡 今後対応したい
- **hero.mp4 圧縮**（33MB → 5-10MB目標）。Handbrake で H.264 / Web Optimized、ビットレート 2-3Mbps 推奨
- **Voice のアバター画像**を実物 or 似顔絵に差し替え（現状は dicebear.com の生成画像）
- **お客様の声3件の本人許諾確認**（実名・属性掲載の最終確認）
- **未使用画像の整理**（assets/report.jpg, market.jpg, property.jpg, why.jpg）
- **OGP画像の作成**（1200×630px、現状未設定）

### 🟢 拡張アイデア
- Instagramの最新投稿を3〜6枚埋め込む（公式 oEmbed or サードパーティ）
- 独自ドメインの設定（CNAME）
- 計測タグ（GA4 / Meta Pixel など）の追加

## 過去の主な変更履歴（要点）

1. 初期版：説得型コールドリード向け17セクション構成
2. ファン向けに全面リライト（10セクション、絵文字多め）→ ユーザーから「言葉遣い変、丁寧に」指摘
3. 全面書き直し前の構成に巻き戻し
4. SPEAKER → PROFILE 名称変更
5. 重複・冗長・矛盾の全体リファイン（PREP vs HOW IT WORKS の役割分担など）
6. スクロールアニメーション実装
7. **PC でもスマホ幅固定**（全 @media 無効化）
8. Hero 画像 → 動画化
9. 料金表記の見直し（具体金額削除→計算式のみ）
10. Eligibility「中古マンション / 戸建て / リノベ前提」削除

## 参考リンク

- INA&Associates：https://www.ina-gr.com/
- 元のLP（参考、現行は別ブランディング）：https://pinthome-house-viewing.lp.ina-gr.com/
- デザインテイスト参考（同社の他LP）：`/Users/snynkmt/Desktop/housing-seminar/index.html`

---

不明点や追加修正があれば、CLAUDE.md と合わせて参照してください。
