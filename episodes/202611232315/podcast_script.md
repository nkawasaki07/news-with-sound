## AIとWebの最前線 デイリーニュースキャスト
**2026年11月23日（月）** ｜ 本日のトピック: 4件 ｜ サブテーマ: セキュリティ

本日は、テンセントの軽量モデル、Solid 2.0の安定版、そしてセキュリティコーナーからJava4ShellとCISAのKEV追加4件を取り上げます。

---

### トピック1: テンセントが低価格マルチモーダルモデル「Hy4 Flash」を公開
📅 2026年11月16日公開（出典: Unite.AI、OmniaKey）

- **文脈長約100万トークン**、最大出力約6.4万トークン、**テキスト＋画像入力**
- 総パラメータ約2,200億（発表時は2,240億と表記）、**アクティブ120億のMoE**
- APIは **OpenAI Chat Completions／Responses、Anthropic Messages互換**。モデルIDは `hy4-flash`、OpenRouter・Vercel AI Gatewayでも提供
- 上位のHy4より大幅に安いとされるが、**料金の通貨・金額は報道間で食い違い**あり
- オープンウェイトは「予定」とする報道と「Hugging Faceで公開済み（独自ライセンス）」とする報道があり、**未確認**
- 性能（WorkIndex等）は**テンセント自社評価**

---

### トピック2: Solid 2.0が正式リリース
📅 2026年11月17日公開（出典: Solid GitHub Releases、AlternativeTo）

- 3月ベータ → 8月RC → **23回のRCを経て安定版**
- 最大の変化は **非同期処理をリアクティブグラフに統合**。計算がPromiseや非同期イテレーターを返せ、競合状態や投機的状態の巻き戻しをフレームワークが処理
- **サーバー関数がコアに**（RPC形式、SSEによる持続接続）
- **削除されたAPI**: `createResource`、`batch`、`startTransition`、`on`、`produce`、`createComputed`、`createMutable`
- **SolidStartは役目を終了**し、コアとフレームワーク非依存のViteプラグインで代替
- 開発ビルドで安定したエラーコード・ウォーターフォール検出、Chrome Performance Tracks連携

---

### 🔒 トピック3: Javaの脆弱性「Java4Shell」（CVE-2026-114938）
📅 2026年11月18日公開（出典: The Hacker News）

- **AVX-512 VBMI**を使う高速版Base64デコーダーで、末尾に余分な「=」がある不正入力により**出力領域の外に62〜63バイト書き込み**
- Basic認証ヘッダーやSAML、CSRFトークン経由で**認証不要**で到達しうる
- **影響**: Java 17.0.6以降、21、25、27（GraalVM一部含む）。**x86-64のIce Lake以降・Zen 4以降のみ**、ARM64と通常のJava 8/11は対象外
- **修正版**: Oracle 17.0.21.1／21.0.13.1／25.0.5.1／27.0.1.1、Corretto・Azul Zuluも提供。Red Hatは記事時点で未提供
- CVSSはOracle 8.1、発見者（Calif）9.2、Red Hat暫定9.8
- 発見者はJira・Jenkins・Keycloak等でのRCEを主張するが、**他機関はクラッシュとメモリ漏えいまでの再現**。実悪用は記事時点で未確認
- **対処**: 更新 → **Javaサービス再起動・コンテナ再ビルド**。暫定策は `-XX:-UseBASE64Intrinsics` または `-XX:UseAVX=2`

---

### 🔒 トピック4: CISAがvCenter・Apache Rollerなど4件をKEVに追加
📅 2026年11月21日公開（出典: The Hacker News）

- CISAが11/20、**実悪用を理由に4件を追加**
- **VMware vCenter 認証回避 CVE-2026-123890（CVSS 9.8）**: 中国系とみられるグループがBeyondTrust Remote SupportのCVE-2026-102764と連鎖してバックドア設置と報道
- **Apache Roller CVE-2026-129448（CVSS 9.8）**: XML-RPCエンドポイントのデシリアライズで**認証不要RCE**
- **Cisco Expressway CVE-2026-76466（CVSS 9.8）**: ハードコード認証情報でroot権限のコマンド実行
- SAP NetWeaver Enterprise Portal CVE-2025-42884（CVSS 6.5）
- 該当製品は**最優先でパッチ適用**を

---

## まとめ

生成AIでは、**低価格・長文脈の軽量モデル**の競争が中国勢にも広がっています。Webでは**Solid 2.0**が非同期をリアクティブの中心に据えるという大胆な設計転換を果たしました。セキュリティでは、**Java4Shell**がCPUの命令セットに依存するという珍しい性質を持つため、まず自社サーバーのCPUとJDKバージョンの棚卸しから始めるのが合理的です。
