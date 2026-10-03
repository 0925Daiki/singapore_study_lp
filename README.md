# シンガポール探究留学 LP（10日間 / 10〜17歳対象）

## Overview
WINNING English Academy Singapore が主催し、日本窓口を B.Bgarden（国内で英会話教室・フリースクールを運営）が担う「シンガポール探究留学（10日間）」の集客用ランディングページ。
主なゴールは **公式LINEへの友だち追加（相談・資料請求）** への誘導です。対象は 10〜17歳の子どもを持つ保護者。

## About the Design Files
同梱の `シンガポール探究留学LP.html` は **HTMLで作成したデザインリファレンス（プロトタイプ）** です。そのまま本番に載せるコードではありません。
実装担当は、対象コードベースの既存環境（React / Next.js / Vue / WordPress テーマ等）とその設計パターンで **このデザインを再現** してください。環境がまだ無い場合は、静的LPに適した構成（例：Astro や Next.js の静的出力、または素の HTML/CSS + 軽量JS）を選んで実装してください。

## Fidelity
**High-fidelity（hifi）**。色・タイポグラフィ・余白・形状・アニメーション・コピーは最終版です。ピクセル単位で再現してください。
ただし下記「未確定・要差し替え」の項目は仮の値です。

### 未確定・要差し替え（本番前に必ず対応）
- LINE URL：`https://lin.ee/XXXXXXX`（全CTA共通・8か所）→ 正式URLに置き換え
- フッターの運営者名：「（仮）運営会社名」
- フッターリンク（お問い合わせ先 / プライバシーポリシー / 特定商取引法に基づく表記）：`href="#"`
- B.Bgarden ロゴ：`placehold.co` の仮画像（推奨 400×120、`object-fit:contain`）
- `output-english-report.png` は AI 生成のイメージ画像（生徒名・日付は架空）

---

## ページ構成（上から順・`data-screen-label`）
単一ページの縦スクロールLP。セクション間は SVG の波形 / 斜線（`.wave-wrap`、高さ48px）で区切ります。背景は白（`#FFFFFF`）と淡いクリーム（`#FFF8EF`、`.sec.alt`）を交互に使います。

| # | id | ラベル | 背景 |
|---|----|------|----|
| 0 | `.hdr` | ヘッダー（FV上に絶対配置。ロゴ＋1024px以上でLINEボタン） | 透明 |
| 1 | `#fv` | 01 FV（ファーストビュー） | メイン青 `#2B59C3` ＋ 黄・橙の円装飾 |
| 2 | `#numbers` | 01b 数字で見るシンガポールでの10日間（＋写真の横スクロールマーキー） | alt |
| 3 | `#change` | 02 Change（Before → After・3つの変化） | 白 |
| 4 | `#safety` | 03 Safety（4つの安全体制）＋ CTA | alt |
| 5 | `#course` | 04 Course（2コース）＋ CTA | 白 |
| 6 | `#schedule` | 05 Schedule（10日間タイムライン） | alt |
| 7 | `#output` | 06 Output（4つの成果物） | 白 |
| 8 | `#price` | 07 Price（留学のご料金）＋ CTA | alt |
| 9 | `#faq` | 08 FAQ（`<details>` アコーディオン 9問） | 白 |
| 10 | `#support` | 08.5 お問い合わせ窓口（B.Bgarden）＋ 3ステップ | alt |
| 11 | `#cta` | 09 最終CTA | 青 |
| 12 | `.ftr` | フッター（ロゴ・募集概要 dl・リンク・コピーライト） | 濃紺 |
| — | `#fixedCta` | スマホ下部の固定LINEボタン（768px未満のみ） | — |

### 1. FV `#fv`
- padding：モバイル `84px 0 40px` / 1024px以上 `120px 0 56px`
- 背景：`#2B59C3` に radial-gradient で装飾円を2つ重ねる（右上：黄 `#FFD23F` 半径110px、左下：橙 `#FF6B5B` 半径170px）。さらに白のドットパターンと blob を重ねます。
- レイアウト：モバイルは1カラム。1024px以上は `grid-template-columns:1.05fr 1fr; gap:48px`（左にコピー、右にコラージュ）。
- 要素：
  - `.fv-tag`：白いピル、文字色はメイン青、13px / 800
  - `.fv-catch`（h1）：`clamp(28px,8vw,52px)` / line-height 1.4 / Zen Maru Gothic。マーカー部分は下40%を橙 `#FF6B5B` で塗る。
  - `.fv-sub`：15px / 500。背景 `rgba(15,28,85,.22)`、角丸12px。`<strong>` は黄色。
  - コラージュ（`.collage`、2カラムのグリッド、gap 10px / 14px）
    - `.c-main`：2カラムぶち抜き、aspect 3/2、`clip-path:polygon(9% 0,100% 0,91% 100%,0 100%)` の斜めカット。画像 `hero-main-v2.png`、`object-position:50% 40%`
    - `.c-s1`：1/1。画像 `hero-sub-left.png`、`object-position:40% 60%`
    - `.c-s2`：1/1。画像 `hero-sub-right.png`、`object-position:35% 60%`
    - 形状（円・面取り）の詳細は HTML 内 v3 スタイルブロックの「FV collage」を参照
  - バッジ3つ（`.badges`）：モバイルは横スクロール＋scroll-snap（各78%幅）、768px以上は3等分。白カード、15px / 700。数字部分 `.bn` は Lexend。
    - 「講師**1:生徒6**の超少人数×完全英語イマージョン」
    - 「安心の**24H**サポート＆名門華僑中学校ドミトリー滞在」
    - （3つ目は HTML 参照）
  - CTA：マイクロコピー「早期割引受付中」（黄色のピル）＋ LINEボタン

### 2. 数字で見るシンガポールでの10日間 `#numbers`
- 見出し：「数字で見る<br>シンガポールでの<span class=ac>10日間</span>」
- 数字カード（`.n-cap` のキャプション付き）に続き、写真8枚を横に流すマーキー（同じ8枚を `aria-hidden` で複製して無限ループ）。使用写真は photo-04/19/15/08/21/16/24/23。

### 3. Change `#change`
- `.ba`：モバイルは縦積み。768px以上は `minmax(0,1fr) 48px minmax(0,2.2fr)`。
- Before：グレーのカード `#EEF1F4`、文字 `#718096`、×印付きのリスト。
- 矢印：橙の三角（モバイルは下向き、768px以上は右向き）。
- After：3枚のカード（`.a-card`、画像 4/3 ＋ 黄色の丸番号 46px）。768px以上は3カラム。
  - 01「英語で交渉・プレゼンする圧倒的自信」→ `final-presentation.png`（`object-position:70% 50%`）
  - 02 → photo-25.jpg（都市模型）
  - 03 → photo-13.jpg（修了証、`object-fit:contain; background:#fff`）

### 4. Safety `#safety`
- 4カード（モバイル1列 / 768px以上2列 / 1024px以上4列）。画像 4/3、左下に「SAFETY 0X」ラベル（青地・白文字、Lexend 14px、右上角丸16px）。
- タグ `.s-tag`：橙の枠付きピル。
  1. 華僑中学校の寮（photo-10.jpg）— 24時間セキュリティ・カードキー管理
  2. 保護者専用LINEグループ（`line-report.png`）
  3. 夜間スマホ回収＆点呼ルール（22:00、photo-14.jpg）
  4. 1:6の超少人数・日英スタッフ帯同（photo-24.jpg）

### 5. Course `#course`
- 2カード（1024px以上は2カラム、gap 32px）。上部に画像と「COURSE A/B」ラベル。
  - A：ファイナンシャルコース（`course-finance.png`）
  - B：都市計画系コース（photo-22.jpg）
- 学習トピックの小見出しにはインラインSVGアイコンを付けます。

### 6. Schedule `#schedule`
- 縦のタイムライン（`.timeline`）。ドットはモバイル小 / 768px以上76px。写真付きの項目（`.has-ph`）があります。
- Day 最終：「帰国・保護者のもとへ / 各国際線の空港へ」
- 最終成果発表会＆修了式 → `final-ceremony.png`（`object-position:40% 35%`）

### 7. Output `#output`
- 見出し：「未来を切り拓く<br>4つの成果物」（サブ見出しなし）
- 4カード（モバイル1列 / 768px以上2列 / 1024px以上4列）。画像は 600×400 比率。
  1. Recommendation Letter 英文推薦状 — `output-letter.png`（`object-fit:cover; object-position:50% 0; background:#fff`）
  2. English Assessment Report ケンブリッジ基準 英語能力評価レポート — `output-english-report.png`
  3. Certificate 専門プログラム修了証 — photo-13.jpg（contain）
  4. Digital Portfolio デジタル学習ポートフォリオ — `output-portfolio.png`（`object-position:50% 40%`）

### 8. Price `#price`
- 見出し：「留学のご料金」（キャンセルポリシーは削除済み。再追加しないこと）
- 価格カード：リボン「早期割引」、タイトル「シンガポール探究留学（10日間）」、通常価格 `$3,300`（取り消し線）、下向き矢印、**早期割引価格（12月30日まで） $3,000（米ドル）**
- 含まれるもの（7項目）／含まれないもの（4項目）：768px以上は `1.3fr 1fr` の2カラム。チェックアイコン付きのタイル。
  - 含む：登録料 / 宿泊費（9泊・3食付）/ 現地交通費 / アクティビティ代 / 事前/事後オンライン学習（6時間）/ 動画撮影・記録費 / 教材費（ドローン本体等）
  - 含まない：往復航空券 / 海外旅行傷害保険 / コインランドリー / 個人的なお小遣い

### 9. FAQ `#faq`
- `<details>/<summary>`。Q と A は丸いバッジ（`.qa`、A は別色）。9問。コピーは HTML のとおり（支払い方法のQは「費用の支払い方法は？」→「銀行振込・カード決済に対応しています。」）。

### 10. Support `#support`
- 中央寄せのカード（1024px以上は padding 32px 36px）。
- ロゴ枠（B.Bgarden、仮）→ h2「お問い合わせ・お申込みの窓口は<br>「B.Bgarden」です」
- リード文：「日本国内で英会話教室・フリースクールを運営する「B.Bgarden」が、本プログラムの日本窓口を務めています。ご紹介から説明会のご案内、お申込みの手続きまで、日本語で丁寧にサポートいたします。…」
- 3ステップ（ご紹介・ご相談 → 説明会・個別相談 → お申込み）。768px以上は `1fr 24px 1fr 24px 1fr` で横並び。
- 補足：「窓口：B.Bgarden（英会話教室・フリースクール運営）／お問い合わせ：公式LINE」

### 11. 最終CTA `#cta` ／ 12. フッター
- CTAボタンの文言：「LINEで気軽に相談してみる（無料）」。下に注記「お問い合わせ窓口：B.Bgarden」。
- フッター：WINNING ロゴ、募集概要の `<dl>`、リンク、`© {現在の年} …`（JSで年を差し込む）。

---

## Interactions & Behavior
- **LINEボタン `.btn-line`**：ピル型、最小高さ64px（768px以上は72px）、背景 `#06C755`、立体シャドウ `0 6px 0 #049A42, 0 12px 24px rgba(6,199,85,.35)`
  - 待機中：`breathe` アニメーション（scale 1→1.025、2.8s ease-in-out infinite）
  - hover：translateY(-4px)、シャドウを強める、アニメーションを一時停止（transition .2s）
  - active：translateY(3px)、シャドウを弱める
  - 全て `target="_blank" rel="noopener"`
- **スクロール表示 `.rv`**：初期 `opacity:0; translateY(28px)` → IntersectionObserver（rootMargin `0px 0px -8% 0px`、threshold .08）で `.in` を付与し、opacity と transform を .7s ease で戻す。一度表示したら監視を解除。保険として、1.5秒以内に監視が反応しない環境では全要素を表示。
- **固定CTA `#fixedCta`**（768px未満のみ）：FV を通過したら表示し、最終CTA `#cta` が画面内にある間は非表示。`aria-hidden` と `tabIndex` も連動させる。
- **FAQ**：ネイティブの `<details>` で開閉。
- **写真マーキー**：CSS animation による無限横スクロール。
- **`prefers-reduced-motion: reduce`**：全アニメーション・トランジションを無効にし、`.rv` は最初から表示。
- スムーススクロール（`html{scroll-behavior:smooth}`）。ロゴは `#fv` へのリンク。

### Responsive
- ブレークポイント：**768px**（タブレット）、**1024px**（デスクトップ）。モバイルファースト。
- `.inner`：max-width 1120px、左右 padding 20px（768px以上は32px）
- `.sec`：padding 72px 0（768px以上は96px 0）

## State Management
静的LPのため、アプリ状態はほぼありません。
- `pastFv` / `atCta`（boolean）→ 固定CTAの表示切替
- `.rv` 要素ごとの表示済みフラグ（クラスで管理）
- データ取得なし。フォームなし（問い合わせはすべてLINEへ遷移）。

## Design Tokens
```css
--main:#2B59C3;      /* メイン青 */
--main-l:#5B8DEF;    /* ライト青 */
--orange:#FF6B5B;    /* アクセント橙（マーカー・強調数字・タグ） */
--yellow:#FFD23F;    /* アクセント黄（マーカー・バッジ・番号） */
--line:#06C755;      /* LINE緑 */
--line-d:#049A42;    /* LINE緑（影） */
--bg:#FFFFFF;
--bg2:#FFF8EF;       /* alt セクション背景 */
--text:#28304A;
--muted:#718096;
--gray:#A0AEC0;
/* 補助色：#4A5568（本文の弱め）, #EEF1F4 / #CBD5E0（Before カード）, #4A3600（黄の上の文字） */
--radius:16px;
--shadow:0 8px 28px rgba(20,32,90,.10),0 2px 6px rgba(20,32,90,.06);
```
- **フォント**（Google Fonts）
  - 見出し：`Zen Maru Gothic` 500 / 700 / 900（h1–h4 は weight 800 指定）
  - 本文：`Zen Kaku Gothic New` 400 / 500 / 700、16px、line-height 1.8
  - 英字・数字：`Lexend` 600 / 800
- **タイプスケール**：h1 `clamp(28px,8vw,52px)`、h2（`.sec-title`）`clamp(24px,6.2vw,38px)`、カード見出し 17–19px、本文 15–16px、ラベル類 13–14px
- **強調の表現**
  - `.mk`：黄色のマーカー `linear-gradient(transparent 58%, rgba(255,210,63,.55) 58%)`
  - `.big`：1.25em、橙
  - `.ac`：メイン青
- **形状（v3 シャープ系）**
  - `.card`：`border-radius:0 20px 20px 20px`（左上だけ角）
  - `.sec-en`：青地・白文字の平行四辺形 `clip-path:polygon(10px 0,100% 0,calc(100% - 10px) 100%,0 100%)`、Lexend 13px / letter-spacing .18em
  - `.sec-title::after`：64×6px の橙の平行四辺形アンダーライン
  - 装飾：ドット（16pxグリッド）、blob（opacity .14）、ストライプ、黄色の三角
- **角丸**：16 / 20 / 12 / 999px（ピル）
- **余白**：セクション 72 / 96px、見出し下 40 / 52px、グリッドの gap 16–32px、CTAブロック上 48px

## Assets（`assets/`）
| ファイル | 用途 | 出典 |
|---|---|---|
| `winning-logo.png` | ヘッダー・フッターのロゴ（1024×388） | クライアント提供 |
| `photos/hero-main-v2.png` | FV メイン（マーライオン＋横断幕、元画像は透過PNG） | クライアント提供 |
| `photos/hero-sub-left.png` / `hero-sub-right.png` | FV サブ（NUS前・PC作業） | クライアント提供 |
| `photos/line-report.png` | Safety 02 | クライアント提供 |
| `photos/course-finance.png` | Course A | クライアント提供 |
| `photos/final-presentation.png` | Change 01 | クライアント提供 |
| `photos/final-ceremony.png` | Schedule 最終発表会 | クライアント提供 |
| `photos/output-letter.png` / `output-portfolio.png` | Output 01 / 04 | クライアント提供 |
| `photos/output-english-report.png` | Output 02 | AI生成（イメージ） |
| `photos/photo-XX.jpg` | 各セクションの活動写真 | クライアント提供 |
| B.Bgarden ロゴ | Support | **未提供（仮画像）** |
| LINEアイコン | ボタン内（インラインSVG sprite `#ico-line`） | HTML内に定義 |

※ PNG は 1〜2MB と大きいため、本番では WebP / AVIF に変換し、`srcset` でのレスポンシブ配信と `loading="lazy"`（FV以外）を推奨します。

## Files
- `シンガポール探究留学LP.html`：デザインリファレンス本体（CSS・JS ともインライン）。v3 の形状スタイルは2つ目の `<style>` ブロックにあり、1つ目を上書きしています。
- `assets/`：上記の画像
