## AIとWebの最前線 デイリーニュースキャスト

**2026年08月29日（土曜日）** ｜ 本日のトピック: 4件 ｜ サブテーマ: インフラ・DevOps

---

### トピック1: Z.aiがGLM-5.3-Flashを公開、3200億パラメータのMoEをMITライセンスで
📅 2026年8月26日公開（出典: MarkTechPost / llm-stats）

中国のZ.aiが新しい大規模言語モデル **GLM-5.3-Flash** を公開しました。**総パラメータ3200億・アクティブ180億**のMoE（混合エキスパート）構成で、GLM-5シリーズ初の**ネイティブマルチモーダル**（画像・動画入力対応）。コンテキスト長は**約104万8千トークン**に達します。

重みは**MITライセンスでHugging Faceに公開**済み。Z.aiの説明では、前世代のGLM-5.2を各種ベンチマークで上回りつつ**価格はおよそ10分の1**、社内コーディングベンチではClaude Opus 4.8と0.5ポイント差に迫ったとしています。公開前の1週間は「Ox Alpha」の匿名名でOpenCode／OpenRouter上に置かれ、**中国国産AIチップのみで推論を提供**していたと報じられています。

---

### トピック2: pnpm 12.0がRust書き直しの安定版として登場
📅 2026年8月27日公開（出典: JSer.info / pnpm公式ブログ）

JavaScriptパッケージマネージャ **pnpm のバージョン12** が安定版としてリリースされました。最大の変更は**実装全体のRust書き直し**ですが、**pnpm 11のコマンド・設定・lockfile形式はそのまま引き継がれる**互換重視の設計です。

新機能は、GitHub/GitLab/Bitbucketの**Git依存を正規化したHTTPS URLでlockfileに記録**、`pnpm-workspace.yaml`の**未知の設定項目の報告**、`globalShims`によるproject-aware global bins、Registry revisions、`pnpm update --patches`、`pnpm stage approve`の一括承認など。大規模でサイクルの多いワークスペースでは**解決が2〜3倍高速・メモリ約25%削減**と報告されています。今週はBun 1.4のZig→Rust移行も重なり、**JSツールチェーンのRust移行**が明確な潮流になりつつあります。

---

### 🛠 トピック3: Kubernetes v1.37「Garhwal」リリース
📅 2026年8月26日公開（出典: Kubernetes公式ブログ / Network World / Techzine）

**Kubernetes v1.37**（コードネーム Garhwal）が公開されました。**67項目の変更**で、内訳は**Stable 16件・Beta 23件・Alpha 27件・Deprecation 1件**。

目玉は3つ。まず**Gang Scheduling がBeta昇格** — 分散AI学習のように「複数Podが揃って起動しないと意味がない」ワークロードを**all-or-nothing**で扱え、学習ジョブのデッドロックを防ぎます。次に **HPAのscale-to-zero がBetaかつデフォルト有効** — `spec.minReplicas: 0` でアイドル時に完全停止し需要復帰で再起動、**GPUの待機コスト削減**に直結します（object／externalメトリクス限定）。そして**9年間Betaに滞留していたMetrics APIがついにGA**。ほかにDRAのdevice taints/tolerations、コンテナ単位のulimit、Alphaで**Pod単位のcheckpoint/restore**（KEP-5823）が入りました。整理面では kube-proxy の **ipvsモードや cgroup v1 が廃止方向**へ進んでいます。

---

### 🛠 トピック4: AKSのNode Auto-Provisioning、停止制御は「二層」で
📅 2026年8月28日公開（出典: InfoQ / AKS Engineering Blog）

Azure Kubernetes Service の **Node Auto-Provisioning（NAP）** について、マイクロソフトが**disruption（停止）制御の新ガイダンス**を公開しました。NAPはOSSの **Karpenter** をベースに、保留中ワークロードに応じてノードを自動追加し、低稼働ノードを自動削除する仕組みです。

ガイダンスの中心的な主張は、**制御をワークロード層とインフラ層の二層でかける**こと。アプリ側は **PodDisruptionBudget（PDB）** で最低稼働Pod数を守り、インフラ側は NodePool の **consolidation policy**（いつ統合を許すか）と **disruption budgets**（一度に何ノードまで止めてよいか）でクラスタ全体の変動速度を抑えます。**PDBはノード予算の代わりにはならない** — 両方が必要だと明確に整理された点が実務上のポイントです。

---

## まとめ

本日の4本を通して見えるのは、**「性能を出す」から「安く・安定して回す」へ**という軸のシフトです。

- **生成AI**: GLM-5.3-Flashは、大規模MoEを**MITライセンス＋低価格**で投げ込む路線。自前ホスティングという選択肢が現実味を増しています。
- **Web開発**: pnpm 12のRust書き直しは、Bun 1.4に続く**ツールチェーンのネイティブ化**の流れ。しかも**互換性を壊さない**移行という点が評価に値します。
- **インフラ・DevOps**: Kubernetes 1.37はGang SchedulingとHPAゼロスケールで**AIワークロードのコスト構造**に踏み込み、AKSのNAPガイダンスは**自動化された削除をどう飼いならすか**という運用側の答えを提示しました。
