# GameGuide JP AdSense 運用ランブック

**作成: 2026-05-17 / 想定 Claude 停止: 2026-05-24**

5/24 以降、Claude 支援なしで AdSense 承認・不承認・運用変更に対応できることを目的としたランブック。

---

## TL;DR — 現在の状態（2026-05-17 時点）

- **AdSense 申請: 完了・審査中**（pub-9726522155839126 を使用 / staypdf.com と同じアカウント）
- **申請ドメイン: gameguidejp.com（apex）**
- **公開サブドメイン: windrose.gameguidejp.com のみ**（dragonkin / everwind は noindex+robots Disallow で一時非公開）
- **CMP（同意管理）設定: 完了**（3択型: 同意する / 同意しない / オプションを管理する）
- **AdSense スクリプト設置: 完了**
- **ads.txt 配置: 完了**（apex + windrose）

| 日付目安 | やること |
|---|---|
| 5/17〜23 | 審査待ち。毎日 AdSense 管理画面・登録メール確認 |
| 5/24 まで | 承認: ✅ 自動配信開始 / 不承認: 理由メール保存 |
| 5/24 後 | Claude なしで承認/不承認対応 |

---

## 0. 現在の構成

### サイト
- **apex**: https://gameguidejp.com / GitHub Pages（`musasabin/gameguidejp-com` リポジトリの master ブランチ）
- **windrose**: https://windrose.gameguidejp.com / GitHub Pages（`windrose-jp/windrose-jp.github.io` リポジトリの main ブランチ）
- **dragonkin（非公開中）**: https://dragonkin.gameguidejp.com / `dragonkin-jp/dragonkin-jp.github.io`
- **everwind（非公開中）**: https://everwind.gameguidejp.com / `everwind-jp/everwind-jp.github.io`

### DNS / Cloudflare
- Cloudflare で各サブドメインの CNAME を `<repo>.github.io` に向けている（DNS only モード = グレー雲）
- HTTPS は GitHub Pages の Let's Encrypt 自動発行

### AdSense
- **pub-ID**: `ca-pub-9726522155839126`（staypdf.com と共用 / 1人1アカウント制）
- **スニペット**: apex 全 HTML（index/about/privacy/contact）+ windrose の `theme/head.hbs`
- **ads.txt**: `google.com, pub-9726522155839126, DIRECT, f08c47fec0942fa0`
- **CMP**: Google 標準 CMP の3択型を選択（GDPR 準拠）

### Google Analytics
- **windrose**: G-9LKY6PPWE7
- **dragonkin**: G-V4Q4BJQFJ4
- **everwind**: G-8NY90P6BJT
- **apex**: 未設置（コンテンツ少ないため任意）

### Search Console
- 登録済みプロパティ:
  - `https://windrose.gameguidejp.com/`（URL prefix）
  - `https://gameguidejp.com/`（URL prefix）
  - 各サブドメインも個別登録の可能性あり
- 所有権確認ファイル: `googlea09a7a225e1f583e.html` 等（リポジトリルートにある HTML）

---

## 1. 審査結果が来たら

### 承認の場合
1. AdSense 管理画面で「広告配信開始」が表示される
2. 自動広告（Auto Ads）が gameguidejp.com / windrose.gameguidejp.com で配信開始
3. **何もしなくて OK**（スクリプトが既に設置済みのため）
4. 翌日以降、AdSense 管理画面でクリック数・表示回数を確認
5. 1週間以内に最初の収益データが見える

### 不承認の場合
1. **理由メールの全文を保存**（スクリーンショット + コピーをパスワードマネージャ等に）
2. AdSense 管理画面の「サイト」→ 該当ドメインを開き、詳細な不承認理由を確認
3. 下記「不承認だった場合の対応」へ

---

## 2. 不承認だった場合の対応

### よくある不承認理由と対応

| 理由 | 対応 |
|---|---|
| 「有用性の低いコンテンツ」 | windrose の薄ページを充実させる。ranged-weapons / building/styles を SUMMARY.md に戻して内容追加 |
| 「価値の低い広告枠」 | head.hbs に AdSense スクリプトがあるか確認、apex の各 HTML も同様 |
| 「Google ポリシー違反」 | 具体URL指摘があればそのページ精査、なければ全コンテンツの「翻訳まとめ」「実プレイ」等の表記を再点検 |
| 「ナビゲーションが困難」 | apex から windrose への導線増強、windrose の内部リンク密度を上げる |
| 「サイトの停止または利用不可」 | GitHub Pages デプロイ反映の遅れ。24時間後に再申請 |
| 「重複コンテンツ」 | windrose の各ページの canonical を確認 |

### 再申請手順
1. 不承認理由を解消する変更をコミット・プッシュ
2. GitHub Pages のデプロイ完了確認（数分〜10分）
3. Search Console で変更ページの URL 検査 → インデックスリクエスト
4. 1〜2 週間待つ（インデックス再促進）
5. AdSense 管理画面 → サイト → 該当ドメイン → 「審査をリクエスト」

**注意**: 同じ問題で何度落ちても通らないため、必ず変更を加えてから再申請する。

---

## 3. デプロイの仕組み

### gameguidejp.com（apex）
- リポジトリ: `musasabin/gameguidejp-com`
- ブランチ: `master`
- デプロイ: GitHub Pages 標準（リポジトリの Settings > Pages 設定）
- `git push origin master` で自動デプロイ
- 反映: 通常 1〜5 分

### windrose / dragonkin / everwind
- mdBook + GitHub Actions
- リポジトリ: `<game>-jp/<game>-jp.github.io`
- ブランチ: windrose / dragonkin = `main` / everwind = `master`
- `.github/workflows/deploy.yml` で `mdbook build` → `book/` を Pages へアップロード
- 反映: 通常 2〜5 分

### よくある問題
- **「Pages のビルドが失敗」**: GitHub Actions のログを確認。SUMMARY.md と実ファイルの不整合が多い
- **「カスタムドメインが効かない」**: Cloudflare の DNS 設定を確認、proxy（オレンジ雲）を OFF にする
- **「HTTPS 証明書エラー」**: GitHub Pages 設定で `Enforce HTTPS` を一旦 OFF→ON で再発行

---

## 4. dragonkin / everwind を再公開する手順

windrose 単体での AdSense 承認後、品質改修を経て両サブドメインを再公開する場合：

1. **品質改修**:
   - dragonkin: `playerauctions.com` 等 Tier 3 サイト引用を全削除（5ファイル）、「攻略まとめ」「翻訳・引用」表記を中立化、SlashingCreeps 依存ページの独自リライト
   - everwind: 各ページ冒頭の `📌 情報源: EverwindWiki` 削除、「情報収集中」プレースホルダー（162箇所）を埋めるか SUMMARY から除外
2. **noindex 解除**:
   - `theme/head.hbs` の `<meta name="robots" content="noindex, nofollow">` を削除
   - `robots.txt` を `Disallow: /` から `Allow: /` に戻す
3. **apex に再表示**:
   - `gameguidejp-com/index.html` にカードと解説セクションを復活
   - `about.html` の運営サイト一覧に追加
4. **AdSense サイト追加**:
   - AdSense 管理画面で `dragonkin.gameguidejp.com` `everwind.gameguidejp.com` をサブドメイン単位で個別追加
   - apex 承認済みなので継承される可能性もある（要確認）

---

## 5. 5/24 アカウント停止後でも継続するための準備

### アクセス情報の保管場所
- **GitHub `musasabin/*` `windrose-jp/*` 等**: パブリックリポジトリ。push 権限のある Git 認証情報を保存
- **Cloudflare**: アカウント情報をパスワードマネージャに保存
- **Search Console**: Google アカウントで管理。**停止前に追加管理者を1人登録推奨**
- **AdSense**: Google アカウント単独。アカウント停止と連動する可能性 → サポート申請の準備
- **Web3Forms**: contact.html 内に access_key `93ac96ab-f6df-4b2e-b35b-33bd1b74d8ff`（変更不要）

### 引き継ぎが必要な場合の最低限のドキュメント
- このランブック（`docs/adsense-runbook.md`）
- `D:/Code/game-wiki/CLAUDE.md`（ネットワーク全体の方針）
- `D:/Code/game-wiki/.claude/research-policy.md`（情報源ポリシー）
- 各リポジトリの `CLAUDE.md`（個別の編集方針）

---

## 6. トラブルシューティング

### 「GitHub Pages デプロイが反映されない」
- GitHub Actions のログを確認（リポジトリの Actions タブ）
- 強制再デプロイ: `git commit --allow-empty -m "redeploy" && git push`
- 反映に最大 10 分

### 「Search Console で URL がインデックス対象外」
- robots.txt 確認: `https://gameguidejp.com/robots.txt` / `https://windrose.gameguidejp.com/robots.txt`
- 該当ページの `<meta name="robots">` を確認
- canonical が他URLを指していないか
- dragonkin / everwind は意図的に noindex 中（正常）

### 「AdSense スクリプトが読み込まれない」
- DevTools の Console で AdSense 関連エラー確認
- CSP（Content Security Policy）でブロックされていないか
- ad blocker が有効になっていないか（自分の環境）

### 「重複コンテンツ警告」
- canonical タグが正しいか確認
- subdomain（windrose）と apex で同じコンテンツがないか

### 「CMP（同意バナー）が表示されない」
- EEA/UK/Swiss IP からのみ表示される設定なので、日本からは見えない（正常）
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
| apex sitemap | `D:/Code/game-wiki/gameguidejp-com/sitemap.xml` |
| apex robots | `D:/Code/game-wiki/gameguidejp-com/robots.txt` |
| windrose プライバシー | `D:/Code/game-wiki/windrose-jp/privacy.md` |
| windrose 運営者情報 | `D:/Code/game-wiki/windrose-jp/about.md` |
| windrose head | `D:/Code/game-wiki/windrose-jp/theme/head.hbs` |
| windrose deploy | `D:/Code/game-wiki/windrose-jp/.github/workflows/deploy.yml` |
| ネットワーク共通方針 | `D:/Code/game-wiki/CLAUDE.md` |
| 情報源ポリシー | `D:/Code/game-wiki/.claude/research-policy.md` |

---

## 8. 5/24 までのチェックリスト

### 必須
- [x] 5/17: AdSense 申請完了・CMP 設定完了
- [ ] 5/17〜23: 毎日 AdSense 管理画面・登録メール確認
- [ ] 結果次第（承認/不承認）で対応

### あると安心
- [ ] Search Console に追加管理者を1人登録
- [ ] AdSense 登録メール・パスワードをパスワードマネージャに保存
- [ ] このランブックを Google ドライブ等にコピー
- [ ] 承認後: 1週間以内のクリック数・表示回数を確認

---

## 9. 5/24 後の運用

### コンテンツ更新
- 各 wiki リポジトリで `.md` を編集 → commit → push で自動デプロイ
- changelog.md / README.md の更新履歴を最新化（windrose は `[wiki]` プレフィックスで自動生成）

### 新しいゲーム wiki を追加する場合
1. 新リポジトリ作成（`<game>-jp/<game>-jp.github.io`）
2. mdBook 構築（`D:/Code/game-wiki/CLAUDE.md` の手順参照）
3. `theme/head.hbs` に AdSense スクリプトと canonical / OGP 追加
4. `ads.txt` 配置
5. apex の `index.html` にカード追加
6. Cloudflare で CNAME 追加
7. AdSense 管理画面で「サブドメインを追加」（または apex 承認の継承確認）

### 収益が想定より低い場合
- 自動広告だけだと配置が最適でない場合あり → 手動広告ユニットを記事内に挿入を検討
- Google AdSense ヘルプ「広告配置の最適化」参照

---

## 付録: 関連リンク

- AdSense 管理画面: https://www.google.com/adsense/
- Search Console: https://search.google.com/search-console
- Cloudflare 管理画面: https://dash.cloudflare.com/
- GitHub Pages 設定: 各リポジトリの Settings > Pages
