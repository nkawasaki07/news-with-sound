## AIとWebの最前線 デイリーニュースキャスト
**2026年10月08日（木曜日）** ｜ 本日のトピック: 3件 ｜ サブテーマ: モバイル・デスクトップ

本日は、端末上で動く埋め込みモデル、Next.jsの新しいキャッシュモデル、そしてAndroid開発をAIエージェントに任せるためのCLI強化をお届けします。

---

### トピック1: Google、スマホで動くマルチモーダル埋め込みモデル「EmbeddingGemma 2」を公開
📅 2026年10月7日公開（出典: gihyo.jp／Google発表は10月6日）

Googleが、スマートフォンやPC上で動作するオープンな埋め込みモデル **EmbeddingGemma 2** を公開しました。埋め込みモデルは、データを意味の近さで比較できるベクトルに変換するモデルで、検索・分類・クラスタリングに使われます。

- **テキスト・コード・画像・音声・動画を共通のベクトル空間で扱える**（初代はテキスト専用）
- パラメーター数 **7億4000万**、**Apache 2.0** ライセンス
- Gemma 4ベースで、テキストモデル2.7億・画像エンコーダー1.7億・音声エンコーダー3億の構成。**必要なエンコーダーだけを読み込める**
- 量子化により、Pixel 11 Proでの必要メモリは **テキストのみ約191MB、全形式で約567MB**
- コンテキスト長は初代の4倍の **8192トークン**、ベクトル次元は768から512／256／128に削減可能
- コード埋め込みのMTEB Codeは **68.76→78.68** に向上（Googleの評価）

重みはHugging FaceとKaggleで公開済み。**Gemma 4と組み合わせれば端末内で完結するオフラインRAG** を構築できます。Transformers.jsによるWebGPUでのブラウザー内デモも紹介されています。

---

### トピック2: Next.js 16.4リリース、Cache Componentsを全アプリに推奨
📅 2026年10月6日公開（出典: Next.js公式ブログ）

Next.js 16.4で、`use cache` によってコンポーネント単位でキャッシュを宣言する新モデル **Cache Componentsが全アプリに推奨** となりました。

- **create-next-appの新規アプリでは既定で有効**、**Next.js 17で標準**になる予定
- **`ensureStatic`**: ルートのシェル／プリフェッチ／ナビゲーションが静的であることを保証し、動的コンポーネントが混入するとビルドを失敗させる
- **`navigation()` / `prefetch()`**: プリフェッチ時に読み込む内容を段階的に制御
- **`next upgrade --agent`**: AIエージェントがバージョン確認から移行・検証まで実施。`experimental.agentUpgrade` で開発中にアップグレードを通知
- Turbopackの **ディスクキャッシュが20〜25%削減**、サーバーHMRの遅延適用、CSS Modulesのクラス名短縮などで本番バンドルも縮小
- **React 19.3を同梱**（View TransitionsとFragment Refsが安定版に）

既存アプリの移行には、Cache Components導入用のエージェント向けSkillsも用意されています。

---

### 📱 トピック3: Android CLIがデバイスストリーミングとAndroid skillsに対応
📅 2026年10月2日公開（出典: Android Developers Blog）

Googleが、コマンドラインツール **Android CLI** の機能拡張を発表しました。

- **Android Device Streamingを CLIから利用可能に**。エージェントが **ADB over SSL** で遠隔の実機をUSB接続と同様に操作し、ビルドのデプロイ、ログ・トレース収集、ヘッドレスでのスクリーンショット取得をターミナルから実行
- 公式ガイダンスを `SKILL.md` でエージェントに渡す **Android skillsが20種類以上**（Playポリシー監査、CameraX移行、Compose for TV移行、R8設定監査、Perfettoによる性能診断など）
- `android init` で初期設定、`android skills add` でプロジェクトに追加、`android skills update --all` で更新
- Wear OS向けの **wear-compose-m3** skillも紹介。FotMobは既存アプリのリスト8つを `TransformingLazyColumn` へ移行
- Android Studio・Antigravityのほか、**ClaudeやCodexなどサードパーティ製エージェントでも利用可能**

---

## まとめ

- **EmbeddingGemma 2**: 端末上で動くマルチモーダル埋め込みモデル。オフラインRAGの部品に
- **Next.js 16.4**: Cache Componentsを全面推奨、エージェントによるアップグレード支援
- **Android CLI**: 実機ストリーミングと公式スキルでエージェント駆動のAndroid開発を後押し

3本に共通するのは、**フレームワークやツールの側がAIエージェントを前提に設計され始めている**という流れです。
