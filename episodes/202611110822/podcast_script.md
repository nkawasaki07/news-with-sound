## AIとWebの最前線 デイリーニュースキャスト
**2026年11月11日（水）** ｜ 本日のトピック: 4件 ｜ サブテーマ: プログラミング言語

本日は、Thinking Machinesの新MoEモデル、Chrome 157の新Web機能、.NET 11正式版、MCP Ruby SDKのTier 1入りをお届けします。

---

### トピック1: Thinking Machines、新モデル「Inkling 2 Small」を公開
📅 2026年11月5日公開（出典: Thinking Machines、gihyo.jp）

Thinking Machinesが新モデル **Inkling 2 Small** を発表。**総約5940億・アクティブ約170億パラメータのMoE**で、テキストと画像を入力できます。

- **複数ステップのタスク**や**Webページの見た目の確認**、さまざまな実行環境への適応が得意とされる
- **Tinker API**で推論とファインチューニングを即日提供
- 学習の全工程で**NVFP4（4ビット浮動小数点）**を使用
- 重みは**外部の安全性テスト後に公開予定**
- ベンチマーク（AA Index v5.0で30.6、DeepSWE v1.1で72.1%など）は**発表元の数値**

---

### トピック2: Chrome 157安定版、HTMLをcanvasに描ける機能が正式搭載
📅 2026年11月4日公開（出典: Chrome Geek、Web Standards、Chrome Platform Status）

**11月3日**にChrome 157安定版が公開されました。目玉は **HTML-in-canvas**。本物のHTML要素をcanvasに描画でき、ブラウザからは通常のページ内容として扱われます。

- **`corner`ショートハンド**: `border-radius`と`corner-shape`をまとめて指定
- **`text-overflow`に任意の文字列**: 切り詰め時に「(more)」などを表示
- **HTML挿入・ストリーミング系メソッド**: `appendHTML()`などの位置指定メソッドで`insertAdjacentHTML`を実質置き換え、ストリーミング版は**WritableStream**で受け取りながら解析
- **`position-visibility`**に`anchor-valid`・`anchor-visible`（複数形は非推奨エイリアス）
- **Long Animation Frames**に`styleDuration`などを追加し、スタイルとレイアウトの時間を分離
- セキュリティ修正は**213件**（Critical 7件）

---

### 💻 トピック3: .NET 11正式版リリース、C# 15のユニオン型が使えるように
📅 2026年11月11日公開（出典: Publickey）

マイクロソフトが **.NET Conf 2026** で **.NET 11正式版**を発表しました。

- **C# 15のユニオン型**: 決められた複数の型のうち1つを保持し、switchの**網羅性をコンパイラがチェック**
- **ランタイムネイティブasync**: 非同期処理をランタイムが直接扱いオーバーヘッドを低減
- **JIT**: 配列の範囲チェックやオーバーフローチェックの削減、小さなswitchの分岐なし展開
- **AOT**: 複数インターフェイス呼び出しの共有ディスパッチで高速化・小型化
- 新ツール **dotnetup**でSDKやランタイムのバージョンを管理
- 論理プロセッサ1024個の上限撤廃、一方で**Pentium 4などの古いCPUはサポート外**に
- **.NET 11は2年サポートのSTS**。業務システムには**LTSの.NET 10**が推奨

---

### 💻 トピック4: MCPの公式Ruby SDKが最上位のTier 1に
📅 2026年11月9日公開（出典: Publickey）

AIエージェントと外部ツールをつなぐ規格 **MCP** の公式Ruby SDKが **Tier 1** に到達しました。

- **Tier 1**: サーバー・クライアント両方の実装が仕様に準拠（非推奨と明記された2機能を除く）
- **ステートレス接続**を含む最新仕様の全機能に対応
- TypeScript・Python・C#・Go・Rustに続く**6言語目**
- 次期MCP仕様（**2027年3月下旬予定**）にも対応する計画

---

## まとめ

- **生成AI**: Inkling 2 SmallがTinkerで利用可能に、重み公開は近日予定
- **Web**: Chrome 157で**HTML-in-canvas**とHTMLストリーミング挿入が正式搭載
- **言語**: **.NET 11とC# 15のユニオン型**が正式版に、**MCP Ruby SDK**がTier 1入り

Chromeは自動更新で新APIがすぐ届くので、HTML-in-canvasやストリーミング挿入を試すには良いタイミングです。
