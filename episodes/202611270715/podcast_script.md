## AIとWebの最前線 デイリーニュースキャスト
**2026年11月27日（金）** ｜ 本日のトピック: 4件 ｜ サブテーマ: 🔒 セキュリティ

本日は、Google WorkspaceのMCPサーバー一般提供、Svelteのカスタムレンダラー、そして悪用中のDrupal脆弱性とApache Tomcatのクラスター認証の脆弱性をお届けします。

---

### トピック1: Google Workspace MCPサーバーとCLIが一般提供開始
📅 2026年11月26日公開（出典: Publickey、Google Workspace Updates）

Googleが、AIエージェント向けの **Google Workspace MCP Server** と **Google Workspace CLI** を **一般提供（GA）** しました。

- 対応: **Gmail・ドライブ・ドキュメント・スプレッドシート・スライド・カレンダー・チャット・タスクの8サーバー**（Keepは近日対応）
- REST APIより**トークン効率が高い**、ユーザー確認・監査ログ・安全な既定の管理者設定を備えるとされる
- Google DeepMindのPhilipp Schmid氏の投稿（11/24）によると、ワンクリックの **Personal mode** ならEnterpriseプランや支払いカードは不要、**製品ごとに1日5,000リクエストまで無料**。送信・共有には**人間の確認**が組み込み
- エージェントからのアクセスは**2027年2月までにREST APIからMCPへの移行**が求められると報じられている（公式情報で要確認）

---

### トピック2: Svelte 5.59でカスタムレンダラーAPIが登場
📅 2026年11月20日公開（出典: Svelte GitHub Releases）

**svelte 5.59.0** で、DOM以外の描画先にコンポーネントを出力できる **カスタムレンダラーAPI** が追加されました（PR #18042）。

- コンパイラオプション **`experimental.customRenderer`** にレンダラーのモジュールを指定（実験的扱い）
- `svelte/renderer` の `createRenderer` で、`createElement`・`insert`・`setAttribute`・`addEventListener` などを実装
- 想定用途: **Svelte Native（NativeScript）、Lynx、ターミナル描画**など
- **制限**: 通常要素への `bind:`、`transition:`/`animate:`、`svelte:window`/`svelte:head` 等、ハイドレーションは非対応（PR時点の記載で、リリース版と差がある可能性あり）
- 同日の5.58.1では、実験的async モードで **`getAbortSignal()` を `await` より前に呼ぶ必要がある** という破壊的変更も

---

### 🔒 トピック3: Drupalで悪用中のサイト乗っ取り脆弱性を追加修正
📅 2026年11月26日公開（出典: The Hacker News、innovatopia）

Drupalが11/25に **SA-CORE-2026-019（CVE-2026-136716）** を公開。**実環境での悪用を確認**しています。

- 11/18修正のインストーラー関連脆弱性 **CVE-2026-132165（SA-CORE-2026-017）** の修正後も、**インストールが不完全な状態などのサイトで乗っ取りが可能**だった
- Drupal独自のリスク評価は **21/25（Highly critical）**。CVE-2026-132165は11/24に**CISA KEV**入り
- **修正版: 11.4.14 / 11.3.23 / 10.6.23**。更新後に **`/update.php`（または `drush updatedb`）の実行が必要**
- 推奨対応: user 1のメールアドレス確認・パスワード再設定の検討、**`core/install.php` の遮断**（403/404を確認）、ログ確認
- 11.0〜11.2、10.5以前はサポート終了で修正なし

---

### 🔒 トピック4: Apache Tomcatのクラスター認証に重大な脆弱性
📅 2026年11月26日公開（出典: JVN、情報処理の東大）

Apache Tomcatのクラスタリング機能に **CVE-2026-133325** が公表されました（JVN JVNVU92527429、11/25）。

- **TLS 1.3＋TLS-PSK** を使うクラスター構成でピア認証に不備があり、**不正なノードがクラスターに参加しセッション情報が漏えい**するおそれ
- 影響: **11.0.28〜11.0.29、10.1.62、9.0.124**
- 深刻度: CCB Belgiumは **CVSS 9.8**、Red Hatは **8.1** と評価が分かれる。悪用の報告は記事中になし
- 修正はソースに入ったが、**修正版（11.0.30 / 10.1.63 / 9.0.125）は11/26時点で未リリース**
- **回避策: クラスター設定の `pskProtocol` を TLSv1.2 に**、クラスター通信を隔離ネットワークに限定、不明なピアのログ確認

---

## まとめ

- **AI**: Google WorkspaceがMCPを公式の主経路に。Workspace連携を作るなら**MCP前提の設計**を検討する時期
- **Web**: Svelteがカスタムレンダラーでネイティブ・ターミナルへ。まだ**実験的**なので制限を確認のうえで
- **セキュリティ**: **Drupalは悪用中**のため即時更新＋update.php実行、**TomcatはpskProtocolの回避策**を
