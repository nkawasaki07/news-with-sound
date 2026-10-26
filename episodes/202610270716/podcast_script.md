## AIとWebの最前線 デイリーニュースキャスト
**2026年10月27日（火）** ｜ 本日のトピック: 4件 ｜ サブテーマ: インフラ・DevOps

本日は、Mistralの音声AIスイート、Interop 2027に向けたCSSの注目機能、Terraform 1.17.0、DuckDB 2.0 LTSの4本をお届けします。

---

### トピック1: Mistral AIが音声AIスイート「Voxtral 3」を公開
📅 2026年10月20日公開（出典: OrcaRouter Blog／AIPicks）

Mistral AIが音声モデル群 **Voxtral 3** を発表しました。

- **文字起こし**: Small Transcribe 3とMini Transcribe 3（4B）が**50以上の言語**と話者分離に対応。Mini版は**$0.0035/分**
- **リアルタイム版**: Mini Transcribe Realtime 3は**500ms未満**（Mistralの主張）
- **音声合成**: TTSは**35以上の言語・50以上の方言**に対応し、料金は100万文字あたり$13
- **音声エージェントSDK**: LiveKitベースで、SIP電話・WebRTC・IVRと連携

前世代とは異なり、**オープンウェイトの配布は案内されていません**。提供形態はAPI、Studio、自社環境への配備です。WERの一部はArtificial Analysisの独立評価で、それ以外はベンダー側の測定値です。

---

### トピック2: 「Interop 2027」に向けて注目したいCSS機能トップ10
📅 2026年10月20日公開（出典: Josh W. Comeau ブログ）

Josh W. Comeau氏が、**Interop 2027**で取り上げてほしいCSS機能を10個挙げました。Interopは主要ブラウザが同じ機能をそろって実装するための共同の取り組みです。

- **`@function`**: CSSの中で関数を定義して値を返せる
- **`corner-shape` / `border-shape`**: 角をsquircleやbevelにしたり、境界の形を自由に描いたりできる
- **`interpolate-size` / `calc-size()`**: `height: auto`へのアニメーションを可能にする
- **その他**: Anchored Container Queries、スクロールトリガーアニメーション、`reading-flow`、gap decorations、Scroll state queries、`inherit()`

多くは**Chrome/Edgeのみの対応**で、FirefoxとSafariが追いつけるかが焦点です。Interop 2027の対象は**まだ決まっておらず**、このリストは筆者の希望です。

---

### 🛠 トピック3: Terraform 1.17.0がリリース
📅 2026年10月21日公開（出典: hashicorp/terraform GitHub Releases／Dev Digest）

- **provider requirementsで変数・localsが使える**ようになりました
- **`-minimal-refresh`**: 変更予定のリソースだけをリフレッシュし、大きな構成で計画を作る時間を短縮
- **Terraform PolicyがGA**: `plan`・`apply`・`query`の`-policies`フラグが実験扱いでなくなりました
- テストで、ephemeral resourceに`mock_provider`を使えるようになりました

⚠️ JSON出力に**`format_version`フィールドが追加**されました。出力を解析するツールでは、最新の`terraform-json`と`terraform-exec`を使うよう推奨されています。

---

### 🛠 トピック4: DuckDB 2.0が長期サポート版として登場
📅 2026年10月22日公開（出典: gihyo.jp／Publickey）

10月21日、**DuckDB 2.0.0 LTS**（コードネーム Cinnamon Teal）が公開されました。サポートは**少なくとも2027年10月まで**続きます。

- **`CONNECT`文**: DuckDB（Quackプロトコル）・PostgreSQL・MySQLにクエリを委譲できる。CLIには`-serve`と`-connect`を追加
- **非同期I/O**: S3などからParquet・CSVを読むとき、取得と処理を並列に実行
- **CLIエージェントモード**: 結果をコンパクトなMarkdown表で返し、エラーはJSONで返す
- **PEGパーサーの既定化**、トリガー、NEAREST JOIN、DuckLake 1.1

⚠️ 新しい形式のDBファイルは**2.0より前のバージョンでは開けません**。旧ラムダ構文はデフォルトで無効になり、ゼロ除算はエラーになるなど、**破壊的な変更**があります。

---

## まとめ

- **生成AI**: Voxtral 3で、文字起こし・音声合成・エージェントSDKが1つのスイートにそろいました
- **Web**: CSSの新機能の多くはChromium系が先行しており、Interop 2027がブラウザ間の差を埋められるかが注目点です
- **インフラ**: Terraform 1.17とDuckDB 2.0は、どちらも**出力やファイル形式に関わる変更**を含んでいます。アップデートの前に移行の注意点を確認しましょう
