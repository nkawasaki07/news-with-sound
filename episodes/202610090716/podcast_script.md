## AIとWebの最前線 デイリーニュースキャスト
**2026年10月9日（金）** ｜ 本日のトピック: 4件 ｜ サブテーマ: 🔒 セキュリティ

本日は、Anthropicの新しい小型モデル、9月のブラウザ新機能のまとめ、そしてセキュリティコーナーでAtlassian製品とAndroidの脆弱性情報をお届けします。

---

### トピック1: Anthropicが小型モデル「Claude Haiku 5.5」を公開
📅 2026年10月7日（米国時間）発表（出典: 窓の杜 / Impress Watch）

Anthropicが軽量モデル **Claude Haiku 5.5**（APIモデル名: `claude-haiku-5-5`）を発表しました。Haiku 4.5から約1年ぶりの更新です。

- **料金**（100万トークンあたり）: 入力 **$0.10**、出力 **$0.50**。Haiku 4.5（$1 / $5）の **10分の1**
- 新しいトークナイザーでトークン数はやや増えるものの、同じ作業の平均コストは **約75%減**
- Haikuとして初めて **effort設定** に対応し、性能とコストのバランスを選べる
- 想定用途は要約・分類・会話の圧縮・カスタマーサポート、そしてOpus 5.5やSonnet 5.5と組み合わせる **サブエージェント**
- Claude Platform、AWS、Google Cloud、Microsoft Azureで提供開始。同じ日にSonnet 5.5のキャッシュ読み込み料金も半額に

---

### トピック2: Safari 27でカスタマイズ可能な`<select>`などが利用可能に
📅 2026年10月2日公開（出典: web.dev）

web.devが9月にブラウザへ入った新機能のまとめ「New to the web platform in September」を公開しました。

- **Safari 27**: `appearance: base-select` と `<selectedcontent>` による **カスタマイズ可能な`<select>`**、遅延読み込み画像の `sizes="auto"`、`revert-rule`、`ReadableStream.from()`、**Service Worker Static Routing API**
- **Chrome 153**: ユーザー操作をもとにカメラやマイクの許可を求める **`<camera>` / `<microphone>`要素**、`Iterator.zip()`
- **Firefox 155**: CSSの `progress()` 関数、`Promise.allKeyed()`
- **Chrome 156ベータ**: CSSの **`random()`関数**、`import defer`、Webアプリのインストールを促す **`<install>`要素**

---

### 🔒 トピック3: Atlassian製品の重大な脆弱性CVE-2026-21589、悪用を確認
📅 2026年10月8日公開（出典: Infosecurity Magazine）

Atlassianが10月5日に公表した **CVE-2026-21589（CVSS 9.3）** で、悪用が確認されました。

- 対象は **Data Center版のみ**: Jira Software、Jira Service Management、Confluence、Bitbucket、Bamboo、Crowd、Crucible、Fisheye
- 製品共通の `atlassian-plugins-webresource` ライブラリのパス処理に問題があり、**ログイン不要でファイルを読み取れる**（パストラバーサル対策の回避）
- watchTowrの実証では、Jiraの `crowd.properties` から認証情報を盗み、**Jira管理者権限まで到達**
- **10月7日にVulnCheckがKEVに追加**し、Bambooを狙った悪用を確認（記事の時点ではCISAのKEVは未追加）
- 対策: **修正版への更新が最優先**（例: Confluence 9.2.26 / 10.2.19、Jira Software 9.12.40 / 10.3.26 / 11.3.12）。すぐに更新できない場合はWAFルールやTomcat RewriteValveで遮断し、侵害の痕跡も確認する

---

### 🔒 トピック4: Androidの10月セキュリティ情報、25件を修正
📅 2026年10月6日公開（出典: 窓の杜）

Googleが10月5日（米国時間）、**2026年10月のAndroidセキュリティ情報** を公開しました。

- 修正は **25件**、そのうち **Critical 7件**（System 6件、Framework 1件）
- 最も深刻なのは、**ユーザー操作なしで権限を奪えるSystemのローカル権限昇格**
- 現時点で **悪用の報告はなし**
- パッチレベルは **2026-10-01** のみ。対象はAndroid 14、15、16、16-QPR2、17
- 3件はGoogle Playシステムアップデート（Project Mainline）でも配信

---

## まとめ

- **生成AI**: Haiku 5.5は前の世代の10分の1の料金で、**サブエージェントや大量処理向けの選択肢**が広がりました
- **Web**: カスタマイズ可能な`<select>`がSafariにも入り、**主要ブラウザで使える範囲**が広がっています
- **セキュリティ**: Atlassian Data Centerは **悪用が始まっているため最優先で更新**、Androidはテスト端末を含めて10月パッチの適用を
