## AIとWebの最前線 デイリーニュースキャスト
**2026年09月26日（土曜日）** ｜ 本日のトピック: 4件 ｜ サブテーマ: インフラ・DevOps

---

### トピック1: Anthropicが「Claude Marketplace」を開設、コネクタ・プラグイン2000件超を集約
📅 2026年9月23日公開（出典: AI Watch）

Anthropicが**Claude Marketplace**を開設。Claudeに外部ツールを接続する**コネクタ**と、機能を拡張する**プラグインが2000件以上**集約されている。

参加パートナーはAtlassian、Google、Microsoft、Salesforce、Snowflakeなどの大手に加え、Cursor、Lovable、CrowdStrike、Harveyといった開発者向けサービス、さらにAccenture、BCG、Deloitteなどのコンサルティング企業も名を連ねる。

開発者にとっての要点は、出品の土台が**MCP（Model Context Protocol）とAgent Skills**という公開仕様に揃えられていること。ベンダー独自形式ではなく標準仕様に沿って作ったツールを、そのままClaudeの法人顧客向け流通経路に載せられる。

---

### トピック2: Microsoft Edge 154、Webプラットフォーム更新を公開
📅 2026年9月24日公開（出典: Microsoft Learn / Edge Web Platform Release Notes）

Edge 154のWebプラットフォーム更新が公開。開発者向けの主な追加は以下。

- **`frame-sizing` CSSプロパティ** — `<iframe>`を中の文書サイズに追従させられる。従来はpostMessage＋JSで高さを計算する力技が定番だった領域に、標準の手段が入った
- **FontFace APIの`width`属性 / CSSの`font-width`** — いずれも従来の`stretch`のエイリアスとして扱われ、文字幅指定の記述が揃う
- **Worker内でのCSSStyleValue系公開** — `CSSKeywordValue`／`CSSNumericValue`／`CSSStyleValue`／`CSSUnitValue`／`CSSUnparsedValue`がworkerグローバルで利用可能に
- **Background Fetch APIがCORSとLocal Network Accessを強制** — 通常のFetchと同じ検査が働くようになった
- **AbortControllerの`reason`転送** — 中断理由が`Response`のメソッドや`ReadableStream`側にも渡る

オリジントライアルでは`<install>`要素、Digital Credentials API、Container Timingなど18以上の実験的APIが提供中。

---

### 🛠 トピック3: Kubernetes v1.37、未使用PVCの検出が標準機能に（Beta昇格）
📅 2026年9月21日公開（出典: Kubernetes公式ブログ）

`PersistentVolumeClaimUnusedSinceTime`フィーチャーゲートが**Betaに昇格し、既定で有効化**。PVC保護コントローラーが各PVCに**`Unused` condition**を自動付与するようになった。

```yaml
status:
  conditions:
    - type: Unused
      status: "True"
      reason: UnusedSinceTime
      lastProbeTime: 2026-09-21T10:00:00Z
```

背景はコストだ。Kubernetesはデータ損失を避けるため、Podを削除してもPVCを自動削除しない。結果として**孤立PVCが蓄積し、クラウドのストレージ料金だけが増え続ける**問題が大規模クラスタで起きがちだった。

Beta昇格により、(1)フィーチャーゲートが既定で有効、(2)condition定義がAPI仕様として固定化、(3)**自前ツールなしで未使用ストレージを洗い出せる**、の3点が変わる。自動クリーンアップやコスト監視の実装がAPIベースで書けるようになる。

---

### 🛠 トピック4: GitHub Copilotアプリにローカルサンドボックス、パブリックプレビュー開始
📅 2026年9月23日公開（出典: GitHub Changelog）

Copilotアプリが**ローカルサンドボックス**に対応。AIエージェントが触れる範囲を明示的に制限する仕組みで、制御対象は3つ。

| 領域 | 制御できること |
|---|---|
| **ファイルシステム** | 読み書き可／読み取り専用／アクセス禁止のフォルダをリスト指定 |
| **ネットワーク** | インターネット接続とローカルネットワーク接続の可否 |
| **認証情報** | Git認証情報とGitHub CLI認証を渡すかどうか |

**既定はオフ**。アプリ設定からプロジェクトを選び「Sandbox new sessions」をオンにするか、実行中のセッションで`/sandbox on`を打つと有効になる。

適用範囲は**ローカルリポジトリとワーキングツリーのセッション**のみで、クラウドサンドボックスやリモートホスト上のセッションは対象外。パブリックプレビューのため仕様変更の可能性あり。

---

## まとめ

本日のキーワードは **「標準化」** と **「境界線」** の2つ。

**標準化**の側では、Claude MarketplaceがMCPという共通仕様の上にツールの流通経路を作り、Edge 154は`frame-sizing`でJSの力技をCSS標準に引き上げ、Kubernetesは各社が自前ツールで書いていた未使用PVC検出をAPI仕様として固定した。いずれも「各自が独自に作っていたもの」を共通の土台に移す動きだ。

**境界線**の側は、GitHub Copilotのローカルサンドボックス。エージェントにどこまで触らせるかを、ファイル・ネットワーク・認証情報の3軸で明示する。自動化が進むほど、共通の土台と安全な囲いの両方が要る——その流れが見えた一週間だった。
