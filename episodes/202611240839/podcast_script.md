## AIとWebの最前線 デイリーニュースキャスト
**2026年11月24日（火）** ｜ 本日のトピック: 4件 ｜ サブテーマ: インフラ・DevOps

本日は、Z.aiの新フラッグシップ **GLM-5.4**、Vue向け **Nuxt UI 4.13**、インフラ・DevOpsコーナーから **AWS CDK 2.278.0** と **CloudWatch Container Insights for EKS** の拡張をお届けします。

---

### トピック1: Z.aiが初のループ型トランスフォーマー「GLM-5.4」を公開
📅 2026年11月23日公開（出典: DataCamp、i10x News）

- **ループトランスフォーマー**を採用し、GLM-5ベースの**28層を重み共有のまま2回通す**設計（パラメータを増やさず推論の深さを稼ぐ）
- 総パラメータは**約750B**とされるが、**Z.aiは未確認**
- **100万トークン**のコンテキスト、今回から**画像入力に対応**
- **GLM Coding Plan・ZCode・Z.ai Chat**で提供中、週次クォータは**GLM-5.3比50%増**
- **APIとオープンウェイトは安全性評価後に公開予定**（日付未定）、**公式ベンチマークも未公開**

性能評価は続報待ちです。

---

### トピック2: Nuxt UI 4.13でトグルやチャット添付などのコンポーネントを追加
📅 2026年11月18日公開（出典: Nuxt Changelog）

- 新コンポーネント **Toggle / ToggleGroup**（`type="multiple"` で複数選択）
- **ChatPrompt** が `v-model:files` によるファイル添付に対応、新しい **ChatAttachment** を追加
- ストリーミング中のメッセージを溜める **`v-model:queue`**
- **`useToast` に `promise` メソッド**を追加し、非同期処理の進行・成功・失敗を一括表示
- Tailwindクラスをテーマと照合する **`@nuxt/ui/eslint`** 設定を同梱

直前の **4.12.1 / 4.12.2 では重大なXSS修正**が入っているため、旧版利用者は合わせて更新を。

---

### 🛠 トピック3: AWS CDK 2.278.0、L1コンストラクトの生成元が変わり破壊的変更も
📅 2026年11月20日公開（出典: AWS CDK GitHub Releases）

- **L1コンストラクトが公開のCloudFormation Resource Schemasから自動生成**されると明記
- **破壊的変更**: Bedrock AgentCore（`PaymentManager`関連）の型名変更、Service Catalog `AcceptedPortfolioShare` の `Id` 属性削除
- 新機能: Lambda Managed Instancesの **AcceleratorConfig**、**IPAMによるサブネットCIDR割り当て**、ALB/NLBの**CNSA 1.0（RFC 9151）SSLポリシー**とリスナー条件の**正規表現**、セルフマネージドKafkaのキュー消費モード
- 依存の **minimatch を 11.0.8 に更新**（脆弱性対応）

更新前に **`cdk diff`** で差分確認を。

---

### 🛠 トピック4: CloudWatch Container InsightsがEKS上のKarpenterやvLLMを標準で監視
📅 2026年11月20〜21日公開（出典: AWS What's New、Dev Digest／daily-aws経由）

- **組み込み監視の対象**: Karpenter、KEDA、vLLM、SGLang、KServe、Ray、Knative Serving
- **ServiceMonitor / PodMonitor** によるPrometheus形式の独自メトリクス取り込みと**テレメトリのフィルタリング**に対応
- 要件: **CloudWatch Observability EKSアドオン（またはHelmチャート）8.0.0以降**

GPU推論基盤をEKSで運用するチームはダッシュボード自作の手間が減りそうです。

---

## まとめ

- **GLM-5.4**: ループ構造の新フラッグシップ。ただし**API・重み・公式ベンチは未公開**
- **Nuxt UI 4.13**: Toggle系とAIチャット向け機能を強化
- **AWS CDK 2.278.0**: L1生成元の変更と**破壊的変更**に注意
- **Container Insights for EKS**: Karpenter・vLLMなどを標準で可視化

新モデルの数字は自社発表が中心です。実際に試して確かめていきましょう。
