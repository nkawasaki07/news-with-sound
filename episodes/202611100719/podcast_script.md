## AIとWebの最前線 デイリーニュースキャスト
**2026年11月10日（火）** ｜ 本日のトピック: 4件 ｜ サブテーマ: インフラ・DevOps

本日は、翻訳特化のオープンウェイトLLM、AI生成のThree.jsコードを表示するライブラリ、AIエージェント用サンドボックス基盤のCNCF寄贈、Docker Desktopのセキュリティ修正を取り上げます。

---

### トピック1: プリファードネットワークス、翻訳特化LLM「PLaMo 3 Translate」をオープンウェイトで公開
📅 2026年11月5日公開（出典: AIPicks、Preferred Networksプレスリリース）

Preferred Networksが翻訳特化LLM **PLaMo 3 Translate** のモデル重みを公開しました。

- サイズは **0.8B／2B／8B／31B** の4種類、**日本語・英語を含む53言語** に対応
- スマートフォンやノートPCで **オンデバイス実行**、オフラインでも動作し **原文を社外に送らない**
- 日本語訳では **敬体／常体の指定** や **専門用語の対訳設定** が可能
- 独自の「PLaMoコミュニティライセンス」。**直近事業年度の売上・収入が10億円以下** の企業・個人は事前登録で商用利用可
- Hugging Faceで配布

※ 最小モデルでも他社の翻訳モデルを上回るという性能はPFN自身の主張です。

---

### トピック2: AIが書いたThree.jsコードを3D・AR・WebXRで表示する「Three-Live」
📅 2026年11月3日公開（出典: Google Open Source Blog）

AIが生成した **Three.jsコード** を、Web・Android・iOSで **3D／AR／WebXR** として表示するオープンソースライブラリ（**v1.0.0 開発者プレビュー、Apache 2.0**）です。

- Webでは **ネットワーク系APIを削除した隔離Web Worker** で実行、ネイティブはRust製のBoaエンジンを使用
- 実行時間とジオメトリ量に上限を設定
- **GLB（glTF 2.0）とUSDZ** を数ミリ秒で生成、WebGL2のPBRレンダラーとWebコンポーネントを提供
- バンドルは標準 **約45KB（gzip）**、ビューアー版約23KB

※ Google Antigravityで書かれた **非公式プロジェクト** で、Googleの公式製品ではありません。

---

### 🛠 トピック3: GoogleがAIエージェント基盤「Agent Substrate」とgVisorをCNCFに寄贈
📅 2026年11月5日公開（出典: Google Open Source Blog）

信頼できないAIエージェントを大規模に安全に動かすため、2つのプロジェクトが **CNCF Sandbox** として寄贈されました。

- **Agent Substrate**: Kubernetes上のアクターベースの制御・データプレーン。セッション状態を持つ **Actor** と、事前起動済みPodプールの **Worker** を分離し、アイドル時のリソース浪費を削減。中断したエージェントを **500ms未満で復元**
- **gVisor（runsc）**: ユーザー空間でシステムコールを処理し、**ホストカーネルから隔離** するサンドボックス。Cloud Hypervisor microVMにも対応
- 関連セッションは **KubeCon NA 2026（11月9〜12日）** で予定

---

### 🛠 トピック4: Docker Desktop 4.98.0公開、WSL 2でのAF_VSOCK制限回避を修正
📅 2026年11月3日公開（出典: Releasebot／Docker Desktopリリースノート）

- **CVE-2026-112917**: WSL 2バックエンドで、コンテナが **AF_VSOCKの制限を回避** できた問題を修正（**WSL 3.0.3以降が必要**）
- LinuxカーネルのIPv4 TCP処理のuse-after-free（CVE-2026-98432）にも対応
- Macでは特権ヘルパー **com.docker.vmnetd を削除**（旧版で入ったものは自動アンインストール）
- WSL 2からDocker VMMを使う際のコマンド対応拡張、Docker Offload v0.7.35、起動時の固着などの不具合修正

---

## まとめ

- **PLaMo 3 Translate**: 端末上で動く53言語対応の翻訳LLMがオープンウェイトに
- **Three-Live**: AI生成の3Dコードを隔離実行して3D・ARへ（非公式・プレビュー）
- **Agent Substrate＋gVisor**: AIエージェントのサンドボックス実行基盤がCNCFへ
- **Docker Desktop 4.98**: WSL 2利用者は **WSL 3.0.3以降と併せて更新** を

今日は「AIエージェントやAI生成コードをどう安全に動かすか」という流れが目立つ一日でした。
