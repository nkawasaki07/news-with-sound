## AIとWebの最前線 デイリーニュースキャスト
**2026年10月6日（火）** ｜ 本日のトピック: 4件 ｜ サブテーマ: 🛠 インフラ・DevOps

おはようございます。本日は生成AI・Web開発のメイン2本に加え、インフラ・DevOpsコーナーから**AIエージェント向けサンドボックス**の話題を2本お届けします。

---

### トピック1: GitHub Copilotがデスクトップアプリを直接操作できる「コンピューターユース」をプレビュー公開
📅 2026年10月1日公開（出典: GitHub Changelog）

GitHub Copilotに、画面を読み取り**クリック・文字入力・スクロール・ドラッグ**などを代行するコンピューターユース機能が**パブリックプレビュー**で追加されました。

- 対象: **Copilot CLI** と **macOS／Windows版 Copilotアプリ**
- 有効化: `/computer on`、またはアプリの設定 → Computer Use
- 操作前に**ユーザー承認が必須**、組織設定で機能を無効化可能（macOSではアクセシビリティと画面収録の権限が必要）
- 想定用途: **APIやCLIのないGUI専用の業務ソフト**の操作、E2Eテストの高速化

---

### トピック2: Chrome 155が安定版に、margin-trim・JPEG XL・耐量子暗号に対応
📅 2026年10月6日安定版リリース（10月1日ごろから段階配信開始）（出典: Chrome Platform Status、Chrome for Developers）

- **CSS**: 最初／最後の子要素の余白を取り除く **`margin-trim`**、カウンタースタイルをインライン定義できる **`symbols()`**、空白部分の下線を制御する `text-decoration-skip-spaces`
- **JavaScript**: `import … with { type: "text" }` で**テキストを文字列としてインポート**
- **画像**: Rust製のメモリ安全なデコーダーで **JPEG XL** に対応
- **WebCrypto**: **ML-KEM／ML-DSA／X-Wing** などの**耐量子暗号**と ChaCha20-Poly1305
- そのほかWebアプリのウィンドウ操作（`maximize()` など）、Digital Credentials APIの発行対応も

---

### 🛠 トピック3: Cloudflare ContainersがAIエージェント向けに刷新、起動が6倍高速に
📅 2026年9月30日公開（出典: Cloudflare Blog、Publickey）

スケジューリング基盤の再設計により、起動時間の中央値が**約4秒→648ミリ秒（約6倍高速）**に。

- コンテナイメージとインスタンスサイズを**実行時にコードから指定**可能に
- **ファイルシステムのスナップショット**（パブリックベータ）で作業環境を保存・復元
- Debian Trixie Slim＋Node.js 24 LTS入りの**ベースイメージ `cloudflare/debian-trixie`** を提供し、Dockerfileなしでサンドボックスを起動
- 注意: 新機能は**Durable Objects内の新API `ctx.container` 限定**。従来の Container／Sandbox クラスは**2026年12月31日まで維持**されるが新機能は追加されない

---

### 🛠 トピック4: GoogleがサンドボックスランタイムgVisorをCNCFに寄贈
📅 2026年10月2日公開（出典: gVisor公式ブログ、Publickey）

gVisorは、コンテナのシステムコールを**Go製のゲストカーネル**で受け止めて分離を強化する、**OCI準拠のコンテナランタイム**です。

- **CNCF Sandbox**プロジェクトとして受理（9月28日）、Incubation入りを数カ月以内に目指す
- 運営はGoogle単独から**メンテナー主体のガバナンス**へ移行し、Ant Group・Modal・Tinesの開発者もメンテナーに参加
- ライセンスは**Apache 2.0のまま**、`runsc` の使い方も変わらず
- Kubernetes／containerdとそのまま組み合わせ可能で、**ハードウェア仮想化が不要**
- 背景: AIコーディングエージェントの普及による**安全な実行環境への需要増**。macOS対応などGoogle単独では優先しにくい取り組みも進めやすくなる

---

## まとめ

本日は、**GitHub Copilotのコンピューターユース**、**Chrome 155の新機能**、そして**Cloudflare ContainersとgVisor**という2つのサンドボックス関連ニュースをお届けしました。インフラの2本に共通するのは「**AIエージェントに速く安全な実行環境をどう用意するか**」というテーマ。エージェントに何をどこまで任せるかの設計が、これからの開発者の重要な仕事になりそうです。
