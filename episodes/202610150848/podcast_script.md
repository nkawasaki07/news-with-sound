## AIとWebの最前線 デイリーニュースキャスト
**2026年10月15日（木）** ｜ 本日のトピック: 3件 ｜ サブテーマ: モバイル・デスクトップ

本日は、AIコーディングエージェントの大型アップデート、既存Webアプリをそのまま載せられる新しいサーバーレス方式、そしてAndroid開発への最新モデル統合をお届けします。

---

### トピック1: OpenCode 2.0公開、ターミナル・Web・デスクトップでセッション共有
📅 2026年10月12日公開（出典: OpenCode公式ブログ／gihyo.jp）

オープンソースのAIコーディングエージェント **OpenCode 2.0** がリリースされました。

- **ユーザーごとの常駐バックグラウンドサービス**が、セッション・設定・権限・ツール実行を管理。ターミナル、Web UI、デスクトップアプリが**同じセッションを共有**
- エージェントがJavaScriptで複数ツールを組み合わせる **Code Mode が標準化**（MCPツール呼び出しの既定に）。独立した呼び出しは並列実行可能
- **サブエージェントや長いテスト・ビルドをバックグラウンド実行**、サブエージェントごとに別モデル指定も可
- `@opencode/client`、`@opencode/sdk` などのSDKを整備、CLIプラグインが安定版に
- 注意点: **V2は現時点でLSP非対応**。V1プラグインはV2向けに書き直しが必要。移行は `opencode upgrade --major`

---

### トピック2: AWS、既存WebアプリをそのままデプロイできるLambda Web Functionsを提供開始
📅 2026年10月12日公開（出典: AWS発表／gihyo.jp）

ExpressやNext.jsなどの **Node.jsアプリを、Lambda用イベントハンドラーに書き換えずに動かせる** 新しい実行方式です。従来のLambda関数は「Lambda Event Functions」に改称されました。

- アプリは環境変数 `AWS_LAMBDA_HTTP_ENDPOINT` のポートで待ち受け、**HTTPリクエストを直接処理**（アダプター不要）
- **1つの実行環境で複数リクエストを同時処理**、同時実行上限は1〜128（既定64）、アクセスがなければゼロまでスケール
- 課金は**実際のCPU使用時間ベース**。I/O待ちの多いアプリで有利
- 注意点: 同一プロセスを共有するため**グローバル変数にリクエスト固有データを置かない**こと。HTTP/1.1のためネイティブgRPCや双方向ストリーミングは非対応
- 提供開始時点は **Arm64上のNode.js 24**、**東京リージョンを含む5リージョン**

---

### 📱 トピック3: Gemini 4 ArgonがAndroid Studio・Firebase AI Logicに登場
📅 2026年10月13日公開（出典: Android Developers Blog）

今日のモバイル・デスクトップコーナーです。Googleが最新モデル **Gemini 4 Argon** をAndroid開発者向けツールに提供開始しました。

- 提供先: **Android Studio／Google AI Studio**（Gemini API有料ティア）、**Firebase AI Logic**（モバイル・Webアプリのクライアント側から利用）、Android Studio Canary内のGoogle Antigravity（AI Ultra加入者）
- **ビルドの自己修復ループ**: GradleデーモンやKotlinコンパイラのログから原因を診断し、ASTを活用して修正を反復
- **Jetpack Composeのシェーダー対応**: AGSLシェーダーを `Modifier.graphicsLayer` やシェーダーブラシに組み込み、すりガラス・動的ライティング・リップル効果などを支援
- Android CLI連携は `agy plugin install android-cli-plugin` または `android init`
- 導入価格は **2026年11月30日まで**

---

## まとめ

- **OpenCode 2.0**: 常駐サービスによるセッション共有とCode Mode標準化。ただしLSP非対応に注意
- **Lambda Web Functions**: 既存Node.jsアプリをそのままサーバーレス化、並行処理とCPU時間課金が特徴
- **Gemini 4 Argon × Android**: ビルド自己修復とComposeシェーダー支援で、Android開発のエージェント化が一段進む

いずれも**既存の開発スタイルを大きく崩さずに新しい仕組みを取り込める**点が共通しています。
