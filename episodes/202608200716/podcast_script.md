## AIとWebの最前線 デイリーニュースキャスト
**2026年08月20日（木曜日）** ｜ 本日のトピック: 4件 ｜ サブテーマ: モバイル・デスクトップ

---

### トピック1: AIの自動修正が新たな脆弱性を作り込んだ、Copilot Autofixの実例
📅 2026年8月17日公開（出典: Wiz）

セキュリティ企業Wizの調査チームが、**GitHub Copilot Autofixが当てた修正パッチ自体が脆弱性を生んだ**事例を報告しました。Snowflakeの公開リポジトリ `snowflake-connector-net` で、安全だった入力パターンが**GitHub Issueのタイトルを生の文字列補間で埋め込む書き方に置き換えられ**、シェルインジェクションの穴が発生。

さらに `pull_request.user.login` を見る条件分岐が、Issueイベントでは `pull_request` が null になるため**素通りしてしまい**、未認証の攻撃者でも到達可能な状態でした。結果として細工されたIssueタイトルによりJiraトークンが外部に持ち出されたとのこと。**AI生成パッチも人間のレビュー対象**という原則を裏付ける事例です。

---

### トピック2: Chrome 152の安定版が公開、CSSとWeb APIに実用的な追加
📅 2026年8月13日公開（出典: PiunikaWeb / Chrome for Developers）

Chrome 152の安定版ロールアウトが8月13日に開始されました。UIの変化はほぼありませんが、**開発者向けの追加は実用性が高い**内容です。

CSS関連:

- **メディア疑似クラス** `:playing` `:paused` `:seeking` `:buffering` `:stalled` `:muted` `:volume-locked` が `<audio>` / `<video>` の状態に直接マッチ（Interop 2026の重点領域）
- **相対アルファ色** — CSS Color 5 の `alpha()` で、元の色を参照して**透明度だけを変更**できる
- **`window-drag` プロパティ** — 既存の `app-region` を標準化・改名し、値を `move` / `none` に整理
- `CSSPseudoElement` が `::backdrop` `::scroll-marker` `::view-transition` に対応

Web API関連:

- **CPU Performance API** — 端末のCPU性能ティアを取得し、Compute Pressure APIと組み合わせて体験を最適化
- **Connection Allowlists** — サーバーがHTTPレスポンスヘッダーで許可エンドポイントを配布し、Fetch等の接続先を事前検証
- **`OpaqueRange`** — フォームコントロールの値テキストをRange的に扱える

なお**クライアントサイドXSLTは廃止が進行中**で、Chrome 158での削除が予告されています（移行猶予用のdeprecation trialあり）。

---

### 📱 トピック3: Expo SDK 57がHermes V1のメモリ問題を解消
📅 2026年8月13日公開（出典: Expo Changelog）

Expoが `expo@57.0.9` を公開し、**React Nativeを0.86.2へ更新**しました。これによりSDK 56から引き継いでいた**Hermes V1のメモリ使用量リグレッションが解消**されます。

対象は `react-native-worklets` または `react-native-reanimated` をimportしているアプリで、メモリ使用量が大幅に増加する問題（expo/expo#46519）。**該当アプリでは57.0.9以降への更新が必須級**とされています。回避策として使われていたWorklets bundle modeは実験的・非推奨のため、更新での対処が推奨。

未解決の既知問題として、**開発時のみ起動時間が伸びる**別のHermes V1リグレッションが残っており、Hermes側に修正はマージ済みだが未リリースです。

---

### 📱 トピック4: BlockがエージェントデスクトップアプリBerdをオープンソース公開
📅 2026年8月18日公開（出典: Crypto Briefing）

Blockが、AIエージェント基盤 **Goose** をまたいでエージェント・ファイル・スキル・セッションを一元管理する**ネイティブデスクトップアプリ「Berd」**を公開しました。

- **Tauri 2 + React 19** 構成で macOS / Windows / Linux 対応
- **会話履歴はクラウドではなくローカル保存**
- ライセンスは **Apache 2.0**（GitHub公開）

ただし運営方針は独特で、**外部からのプルリクエストは受け付けない**とのこと。フォークして社内向けに改変する用途は認められており、「公開はするが開発権はBlockが握る」形の企業主導オープンソースです。

---

## まとめ

本日は**AIが生成したコードの検証**という論点が軸になりました。トピック1のCopilot Autofixの事例は、AI提案パッチがそのままマージされるリスクを具体的な被害まで含めて示しています。一方でトピック4のBerdのように、**エージェントの実行環境をローカルデスクトップに寄せる**動きも進行中です。

足元の実装環境では、Chrome 152がメディア疑似クラスやCPU Performance APIといった実用的な機能を追加し、Expo SDK 57はモバイルアプリのメモリ問題を解消しました。いずれも**すぐに手元のコードへ反映できる**アップデートです。
