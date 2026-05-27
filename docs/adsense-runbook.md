# GameGuide JP AdSense 運用ランブック

**作成: 2026-05-17 / 大幅改訂: 2026-05-27 / 想定 Claude 停止: 2026-05-24**

5/24 以降、Claude 支援なしで AdSense 承認・運用変更・コンテンツ追加に対応できることを目的としたランブック。

---

## ⚠️ 重要：戦略を抜本的に変更しました

### 当初の楽観的計画（誤り）
- 5/17 申請 → 数日で承認 → 5/24 までに広告配信開始

### 不承認後に判明した事実（証拠付き）
- **「有用性の低いコンテンツ」不承認の中央値ライン: 独自ドメイン × 20-30記事 × 各 800-2,500字 × ドメイン年齢 3-6ヶ月以上**（[stackedbuddy 2025 Checklist](https://www.stackedbuddy.com/google-adsense-approval-2025-9-step-checklist/) / [theguidex 2026](https://theguidex.com/google-adsense-approval/) / [squarearth 2025](https://squarearth.shop/)）
- AdSense は **apex を主評価**。サブドメイン（windrose.gameguidejp.com の70+ページ）は審査スコアにほぼ寄与しない（[Google 公式](https://support.google.com/adsense/answer/2784438?hl=ja) / [Strategy by ipe](https://ipeinc.jp/media/sub-domain-adsense/)）
- ドメイン年齢 1ヶ月では足りない。3ヶ月以上を待つべき
- 3記事の追加では覆せない構造的問題

### 新しい計画（証拠ベース）
- **5/27 時点で apex に 13 記事を配置済み**（3カテゴリ整理: 攻略 / ジャンル比較 / 情報源）
- **2026-06 から月8記事ペースで追加運用**
- **2026-07末（ドメイン年齢3ヶ月、記事 25本超）で再申請**

---

## 申請履歴

| 日付 | アクション | 結果 |
|---|---|---|
| 2026-05-17 | 初回申請 | **不承認**（理由: 有用性の低いコンテンツ） |
| 2026-05-17 | apex に独自記事3本追加、コンテンツサイト化 | デプロイ完了 |
| 2026-05-27 | apex に独自記事10本追加（計13本）、About 大幅加筆 | デプロイ完了 |
| **2026-06〜07** | 月8記事ペースで追加運用 | user 単独で実施 |
| **2026-07末** | 2回目の再申請 | 結果待ち |

---

## 0. 現在の構成（2026-05-27 時点）

### apex 配下のコンテンツ
- ポータルトップ（index.html）：Windrose カード + 解説 + 運営方針 + 最新記事カード
- About / Privacy / Contact / 404
- **記事13本**（articles/）
  - 攻略ガイド（Windrose）: 4本（early-pitfalls / poise-parry / build-philosophy / multiplayer）
  - ジャンル比較・考察: 4本（survival-ship-comparison / casual-vs-hardcore / soulslike-survival / 2026-survival-ea-trends）
  - 情報源の使い方・メタ: 5本（why-no-japanese-wiki / fextralife-fandom / discord-guide / slang-glossary / steam-ea-checklist）

### サブドメイン
- **windrose**: https://windrose.gameguidejp.com / 70+ ページ（mdBook）/ 公開中
- **dragonkin**（一時非公開）: noindex + robots Disallow
- **everwind**（一時非公開）: noindex + robots Disallow

### AdSense
- **pub-ID**: `ca-pub-9726522155839126`（staypdf.com と共用 / 1人1アカウント制）
- **スニペット**: apex 全 HTML（index / articles/ 全ファイル / about / privacy / contact）+ windrose の `theme/head.hbs`
- **ads.txt**: `google.com, pub-9726522155839126, DIRECT, f08c47fec0942fa0`（apex + windrose）
- **CMP**: Google 標準 CMP の3択型（GDPR 準拠）

### Search Console
- 登録済みプロパティ:
  - `https://gameguidejp.com/`
  - `https://windrose.gameguidejp.com/`
- 所有権確認ファイル: `googlea09a7a225e1f583e.html` 等

---

## 1. 6月〜7月のコンテンツロードマップ（user 単独で実行）

### 月8記事ペースの設計
- 週2記事 = 月8記事 × 2ヶ月 = 16本追加 → 7月末で計29本（目標 20-25本超え）

### テーマ案ストック（記事タイトル候補）

**攻略ガイド系（windrose 中心）:**
1. Windrose の食料・薬・バフ食材の選び方
2. Windrose の島ごとのリソース最適周回ルート
3. Windrose のクラフトステーション解放順
4. Windrose のクエスト報酬ベストピック
5. Windrose の派閥（Faction）名声の上げ方
6. Windrose のソロ vs マルチで変わる戦略
7. Windrose の終盤コンテンツ（追加され次第）
8. Windrose 大型パッチごとのメタ変化まとめ

**ジャンル比較・考察系:**
9. Subnautica 2 の Early Access 評価（リリース後）
10. Enshrouded vs Valheim の建築設計の違い
11. PvE専用サバイバル vs PvPサバイバル の選び方
12. インディーEA成功例（Hades, Valheim, Slay the Spire）に共通する設計パターン
13. 2026 後半の海外PCゲーム注目作（夏〜秋リリース予定）
14. ゲーム実況・配信から攻略情報を集めるコツ

**情報源・メタ系:**
15. Reddit のサブレディットを定期巡回するコツ
16. wiki.gg と Fandom の違い（Fandom 離脱トレンド）
17. Steam Workshop の MOD で公式攻略が崩れる事例
18. 海外攻略動画（YouTube）と日本語動画の情報差
19. 海外実況者（Twitch / YouTube）のおすすめチャンネル
20. ゲームジャンルごとの英語用語サマリ（ARPG / FPS / MMO）

### 記事執筆ルール（必須）
- **各記事 1,500-3,000字**
- **Tier 1 引用必須**（Steam Community / Reddit / Fextralife / 公式 Discord / wiki.gg）
- **独自視点30%以上**（複数ソース比較 / 構造的考察 / 具体的失敗例）
- **AI生成感を避ける**（定型表現「〜について解説します」「最後に」は禁止）
- **既存記事への内部リンク**（最低2本）
- **末尾に Tier 1 参考情報源リスト**

### 記事執筆テンプレート
新規記事は `articles/windrose-early-pitfalls.html` をコピーして使う。差し替え箇所:
- `<title>` / `<meta description>` / `<link canonical>`
- `<script type="application/ld+json">` の headline / url
- `<h1>` と breadcrumb
- 本文・参考情報源
- 公開後: `articles/index.html` / `sitemap.xml` / `index.html`（最新記事カード）に追加

---

## 2. 7月末の再申請手順

### 2-1. 申請前の最終チェック（必須）
- [ ] 記事数 20+ 達成（理想 25+）
- [ ] 各記事インデックス済（Search Console「ページ」レポートで確認）
- [ ] AdSense スクリプトが全 HTML に挿入されている
- [ ] ads.txt が `https://gameguidejp.com/ads.txt` で表示される
- [ ] 全リンクが切れていない（404 が出ない）
- [ ] DevTools の Console エラーゼロ
- [ ] スマホ表示確認（レスポンシブ崩れチェック）

### 2-2. 申請手順
1. https://www.google.com/adsense/ にログイン
2. 左ナビ「サイト」→ `gameguidejp.com` のステータス確認
3. 「審査をリクエスト」ボタンを押下
4. 審査開始（通常 1〜14 日）

### 2-3. 申請後
- 結果は AdSense 管理画面 + 登録メール
- **承認**: 自動広告（Auto Ads）が gameguidejp.com / windrose.gameguidejp.com で配信開始
- **不承認**: 理由メールを必ず全文保存（スクリーンショット + コピー）

---

## 3. 不承認だった場合の対応

### よくある不承認理由と対応

| 理由 | 対応 |
|---|---|
| 「有用性の低いコンテンツ」 | 記事を5本以上追加（各 2,000字+）、最低1ヶ月空けてから再申請 |
| 「価値の低い広告枠」 | AdSense スクリプトの全 HTML 配置を再確認、ads.txt の存在確認 |
| 「Google ポリシー違反」 | 具体URL指摘があればそのページ精査、なければ「翻訳まとめ」「AI生成」表記の有無を全文検索 |
| 「ナビゲーションが困難」 | breadcrumb / 内部リンク密度・記事カテゴリ整理を強化 |
| 「サイトの停止または利用不可」 | デプロイ反映遅れ。24時間後に再申請 |
| 「重複コンテンツ」 | canonical タグを全 HTML で確認 |

### 再申請のクールダウン
- 不承認後、最低 **1〜2 週間**は記事追加 + インデックス促進をしてから再申請
- 同じ問題で連続不承認すると審査が厳格化する（経験則）

---

## 4. デプロイの仕組み

### gameguidejp.com（apex）
- リポジトリ: `musasabin/gameguidejp-com`
- ブランチ: `master`
- デプロイ: GitHub Pages 標準（Settings > Pages）
- `git push origin master` で自動デプロイ
- 反映: 通常 1〜5 分

### windrose / dragonkin / everwind
- mdBook + GitHub Actions
- リポジトリ: `<game>-jp/<game>-jp.github.io`
- ブランチ: windrose / dragonkin = `main` / everwind = `master`
- `.github/workflows/deploy.yml` で `mdbook build` → `book/` を Pages へアップロード
- 反映: 通常 2〜5 分

---

## 5. アクセス情報の保管場所（Claude 停止前にチェック）

- **GitHub `musasabin/*` `windrose-jp/*` 等**: パブリックリポジトリ。push 権限のある Git 認証情報を保存
- **Cloudflare**: アカウント情報をパスワードマネージャに保存
- **Search Console**: Google アカウントで管理。**追加管理者を1人登録推奨**
- **AdSense**: Google アカウント単独
- **Web3Forms**: contact.html 内に access_key `93ac96ab-f6df-4b2e-b35b-33bd1b74d8ff`

---

## 6. トラブルシューティング

### 「GitHub Pages デプロイが反映されない」
- GitHub Actions のログを確認（リポジトリの Actions タブ）
- 強制再デプロイ: `git commit --allow-empty -m "redeploy" && git push`
- 反映に最大 10 分

### 「Search Console で URL がインデックス対象外」
- robots.txt 確認: `https://gameguidejp.com/robots.txt`
- 該当ページの `<meta name="robots">` を確認
- canonical が他URLを指していないか
- dragonkin / everwind は意図的に noindex 中（正常）

### 「AdSense スクリプトが読み込まれない」
- DevTools の Console で AdSense 関連エラー確認
- CSP（Content Security Policy）でブロックされていないか
- ad blocker が有効になっていないか（自分の環境）

### 「CMP（同意バナー）が表示されない」
- EEA/UK/Swiss IP からのみ表示される設定（日本からは見えない）
- VPN で EU IP に切り替えて確認可能

---

## 7. 重要ファイル早見表

| 何か | パス |
|---|---|
| AdSense ID | `ca-pub-9726522155839126`（多数のHTML内）/ 各 `ads.txt` |
| Web3Forms access_key | `D:/Code/game-wiki/gameguidejp-com/contact.html` 内 |
| apex プライバシー | `D:/Code/game-wiki/gameguidejp-com/privacy.html` |
| apex 運営者情報 | `D:/Code/game-wiki/gameguidejp-com/about.html` |
| apex コンタクト | `D:/Code/game-wiki/gameguidejp-com/contact.html` |
| apex 記事 | `D:/Code/game-wiki/gameguidejp-com/articles/*.html` |
| apex sitemap | `D:/Code/game-wiki/gameguidejp-com/sitemap.xml` |
| apex robots | `D:/Code/game-wiki/gameguidejp-com/robots.txt` |
| windrose プライバシー | `D:/Code/game-wiki/windrose-jp/privacy.md` |
| windrose 運営者情報 | `D:/Code/game-wiki/windrose-jp/about.md` |
| windrose head | `D:/Code/game-wiki/windrose-jp/theme/head.hbs` |
| windrose deploy | `D:/Code/game-wiki/windrose-jp/.github/workflows/deploy.yml` |
| ネットワーク共通方針 | `D:/Code/game-wiki/CLAUDE.md` |
| 情報源ポリシー | `D:/Code/game-wiki/.claude/research-policy.md` |

---

## 8. 主要な参考エビデンス

このランブックの判断根拠（再申請時期・記事数目安・apex 主評価原則）は以下のソースに基づきます。

- [Google 公式: AdSense サイトURL登録](https://support.google.com/adsense/answer/2784438?hl=ja)
- [Google 公式: ads.txt FAQ](https://support.google.com/adsense/answer/9785052?hl=ja)
- [stackedbuddy: AdSense Approval 2025 9-Step Checklist](https://www.stackedbuddy.com/google-adsense-approval-2025-9-step-checklist/)
- [theguidex: AdSense Approval 2026](https://theguidex.com/google-adsense-approval/)
- [trulyspeaks: Real Low Value Content Fix 2025](https://www.trulyspeaks.com/2025/11/adsense-low-value-content-fix.html)
- [zenn beachone: 有用性の低いコンテンツ審査対応 2025](https://zenn.dev/beachone1155/articles/20251101-adsense-low-value-content-fix)
- [squarearth: 10回落ちた人の合格秘訣](https://squarearth.shop/google%E3%82%A2%E3%83%89%E3%82%BB%E3%83%B3%E3%82%B9%E5%90%88%E6%A0%BC%E7%A7%98%E8%A8%A3/)
- [Strategy by ipe: サブドメインAdSense](https://ipeinc.jp/media/sub-domain-adsense/)
- [digitalapplied: Scaled Content Abuse March 2026](https://www.digitalapplied.com/blog/scaled-content-abuse-google-march-update-ai-pages-decimated)
- [GitHub Pages AdSense 合格事例](https://sonotato6.github.io/github-pages-adsense/)

---

## 9. 関連リンク

- AdSense 管理画面: https://www.google.com/adsense/
- Search Console: https://search.google.com/search-console
- Cloudflare 管理画面: https://dash.cloudflare.com/
- GitHub Pages 設定: 各リポジトリの Settings > Pages
- Google Search Central: AI 生成コンテンツについて https://developers.google.com/search/blog/2023/02/google-search-and-ai-content
