## AIとWebの最前線 デイリーニュースキャスト
**2026年10月01日（木曜日）** ｜ 本日のトピック: 3件 ｜ サブテーマ: モバイル・デスクトップ

---

### トピック1: Anthropic、「Claude Sonnet 5.5」を公開 — 30%以上高速化・最大30%コスト減
📅 2026年9月29日公開（出典: 窓の杜、マイナビニュース）

Anthropicが現地時間9月28日に **Claude Sonnet 5.5** を発表。前世代のSonnet 5比で **生成速度が30%以上向上**、同一タスクに必要なトークン数も削減され、**多くの作業でコストは最大30%安くなる** としています。

- 料金: 100万トークンあたり **入力$2 / 出力$10**
- APIモデル名: `claude-sonnet-5-5`、ゼロデータ保持に対応
- ベンチマークでは上位の **Opus 5.5** に及ばないものの、一部テストでは同等〜凌駕
- スクリーンショットのみで『ポケットモンスター 赤』をクリアした初のSonnetモデル
- 提供: **AWS / Google Cloud / Microsoft を含む全プラットフォームで提供中**
- 軽量版 **Haiku 5.5** は数週間のうちにリリース予定

---

### トピック2: Cloudflare、WordPressをTypeScriptで作り直したCMS「EmDash 1.0」を正式リリース
📅 2026年9月28日公開（出典: gihyo.jp、Cloudflare Blog）

CloudflareがオープンソースCMS **EmDash 1.0** を公開。WordPressの機能を **TypeScriptで再構築** し、**Astro** 上に構築されたスタックです。**175人超の開発者・1,800以上のコミット** を経て安定版に到達し、Cloudflare自身も2026年8月に自社ブログを移行して実運用検証済み。

- **サンドボックス型プラグイン**: プラグインは隔離環境で動作し、**明示的な宣言と承認がない限り** サイトコンテンツ・メディア・ユーザー・シークレット・ファイルシステムへアクセスできない。実行しようとする内容が表示され、許可された機能のみが動く
- **分散レジストリ**: 中央集権マーケットではなく、Blueskyが用いる **ATProtocol** を採用。ポータブルなAtmosphereアカウントで公開でき、配布側のインフラ負担を軽減。現時点は無料プラグインのみで、有料対応は今後
- 実行環境: Cloudflare上では **Dynamic Workers**、Node.js環境ではOSSの **workerd** ランタイム
- 開始コマンド: `npm create emdash@latest`

---

### 📱 トピック3: Microsoft、「WSL containers」を一般提供（GA）— Windows単体でLinuxコンテナ
📅 2026年9月29日公開（出典: Windows Developer Blog、Publickey）

Microsoftが **WSL containers（WSLC）** をGA。**Docker Desktop等のサードパーティ製ソフトなしに**、Windows上でLinuxコンテナの作成・実行・管理が可能になりました。操作は **CLI `wslc`** とAPIから行えます。

- 新たなCLI機能: コンテナの再起動、システム情報の照会、ネットワーク接続の管理
- 7月のパブリックプレビューからの改良: 既定ファイルシステムを **virtiofs** に切り替えて性能最適化
- 新ネットワークモード **consomme** により、コンテナが **Windowsアプリと同じネットワーク環境・セキュリティポリシー・企業統合** の恩恵を受けられる
- 企業管理: **Microsoft Intune / Microsoft Defender for Endpoint** と連携
- 設定ファイルで複数コンテナを扱う **`wslc compose`** は開発中
- 導入: WSLのアップデートコマンド、またはGitHubのWSLリリースページから最新版を取得

---

## まとめ

生成AIでは、Anthropicが **Sonnet 5.5** で速度とコストを同時に約3割改善し、中位モデルの実用性をさらに押し上げました。Webでは、Cloudflareの **EmDash 1.0** が、プラグインのサンドボックス化とATProtocolベースの分散レジストリという設計で、WordPressが長年抱えてきたプラグインのセキュリティ問題に正面から答えを出しています。モバイル・デスクトップでは、**WSL containers** のGAによってWindows単体でのLinuxコンテナ開発が現実的な選択肢になりました。いずれも今日から手元の環境で試せる変化です。
