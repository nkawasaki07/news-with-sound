## AIとWebの最前線 デイリーニュースキャスト
**2026年11月17日（火）** ｜ 本日のトピック: 4件 ｜ サブテーマ: インフラ・DevOps

---

### トピック1: Google、判断専用の「Gemini Decisions API」を公開
📅 2026年11月11日公開（出典: Google Blog）

Googleが、閉じた選択肢から答えを選ぶことに特化した **Gemini Decisions API** と新モデル **Gemini Decision 1（gemini-decision-1）** を発表。文章を生成せず、**選択肢を1回のフォワードパスでスコア付けし、確率と0〜1の信頼度を返す**。

- 質問タイプ: **Yes/No（noul）・choice（2〜255択）・score（順序付きルーブリック）**
- 入力は最大256Kトークン（テキスト・画像・音声・動画・PDF）、**1リクエスト最大1,000問**
- 応答 **150〜250ms**、料金は **入力$0.10/100万トークン・出力無料**
- Gemini API・AI Studioで提供、Google Cloudは近日対応

エージェントのルーティングや分類に向く。ただし較正誤差やレイテンシの優位性は**Google自身の発表値**。

---

### トピック2: Playwright 1.65、テストランナーのBun実行を正式サポート
📅 2026年11月12日公開（出典: Publickey、Playwright公式リリースノート）

**`bunx --bun playwright test`** でテストランナーをBun上で実行可能に。BunがTypeScriptを直接トランスパイルするため **Babelとそのキャッシュが不要** に。

- Bunでの制限: **ウォッチモードなし**、`--tsconfig`無効、カスタムESMローダー未対応など
- 新機能: 失敗だけを表示する **`failures`レポーター**、`onlyFailures`オプション、排他実行の `-exclusive-` ロック
- **破壊的変更**: Cookieが**RFC 6265準拠**に、**プロキシ認証情報をWebサイトに送らない**、inert要素の操作は解除まで待機、`useDefineForClassFields`に追従
- Node.js 20はテスト対象外に（22/24/26を推奨）

---

### 🛠 トピック3: KubeConでAKSがアップグレード保護とFleet Managerの新機能を発表
📅 2026年11月10日公開（出典: Microsoft Open Source Blog）

KubeCon North America 2026に合わせ、MicrosoftがAKSの新機能を発表。

- **アップグレードインサイト**: PDB制約・**非推奨API**・クォータやサブネット上限を事前検出
- **アップグレードヘルスゲート**: 健全性低下時に**アップグレードを自動停止**（独自監視のシグナルも取り込み可）
- **Azure Kubernetes Fleet Manager**: **ドリフト検出・Takeover・Eviction・アノテーション配置がGA**
- GPUノードプール向け **マネージドDRA**、RDMA向けDRANET、マルチNIC
- Azure Container LinuxでIPE（監査モード）がGA

※ インサイト・ヘルスゲート・DRA関連は**提供段階（プレビュー/GA）が記事で明記されていない**。

---

### 🛠 トピック4: AIエージェント基盤「Agent Substrate」が1.0に到達
📅 2026年11月10日公開（出典: ITOps Times）

Solo.ioが、Googleと共同メンテナンスする **Agent Substrate 1.0** の公開と、開発者向けツール **kagent の一般提供** を発表。

- **アイドルセッションを一時停止→必要時に再開**し、既存のKubernetesで大量のエージェントセッションを処理
- サーバーレス規模の拡張、**サンドボックス分離**、統制された接続性を組み合わせ
- 企業版はagentgatewayで入出力の**ID・ポリシー制御**
- 本番計画用の**サイジング計算ツール**も提供

---

## まとめ

本日は、**判断特化のGemini Decisions API**、**Bun対応のPlaywright 1.65**、そしてKubeConから **AKSのアップグレード保護** と **Agent Substrate 1.0** をお届けしました。AIを「生成」でなく「判断」に使う流れと、エージェントを本番運用するための基盤整備が並行して進んでいます。Playwrightは破壊的変更が多いので、更新前の確認をお忘れなく。
