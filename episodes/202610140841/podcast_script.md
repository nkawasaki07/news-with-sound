## AIとWebの最前線 デイリーニュースキャスト
**2026年10月14日（水）** ｜ 本日のトピック: 3件 ｜ サブテーマ: プログラミング言語

本日は、Metaの新フロンティアモデル、Denoの開発終了という大きな転換、そしてPython 3.15正式版の3本です。

---

### トピック1: Meta、新フロンティアモデル「Muse Wonder」を公開
📅 2026年10月12日公開（出典: Meta AI Blog、VentureBeat）

Meta Superintelligence Labsが **「Muse Wonder」と上位版「Muse Wonder Full」** を発表しました。

- **API提供は標準版のみ**（モデルID `muse-wonder-1.0`、Meta Model API）。料金は100万トークンあたり **入力$4・出力$20・キャッシュ入力$0.20**
- コンテキストは **約100万トークン**、入力はテキスト・画像・音声・動画
- **Active Memory**: 会話をまたいで重要な文脈を保持し、タスクに関連する情報を能動的に呼び出す
- **Active Focus**: 行き詰まっても別アプローチを試し、重要操作の前にはユーザーへ確認
- SWE-Marathon（長時間コーディング）ではWonder Fullが57.5とOpus 5.5（46.3）を上回る一方、**Artificial Analysis総合指数はFull 56／Wonder 52でOpus 5.5（58）に届かず**
- **Wonder FullはMuse Codeサブスクリプション限定**で従量APIなし、重みはいずれも非公開

> 注: 比較表には第三者評価とMeta自社評価が混在しており、ツール条件も統一されていません。

---

### トピック2: Deno開発元がCloudflareに合流、Denoの開発は終了へ
📅 2026年10月13日公開（出典: Publickey、発表は10月9日）

Deno LandがCloudflareへの合流を発表。開発者への影響が大きいのは以下の点です。

- **Deno本体の開発は終了**。今後 **1年間は月次のバグ修正・セキュリティ更新のみ**（コードはOSSのまま）
- **Deno Deployは6カ月後に終了予定**、**Cloudflare Workersへの移行サービス**を提供
- パッケージレジストリ **JSRはCloudflareのインフラへ移して継続**
- Ryan Dahl氏とBert Belder氏は、Workersのオープンソース実装 **workerdのセルフホスティングを第一級サポートにする取り組み** を主導。8月に公開したDurable Objects互換実装「celld」の成果もworkerdへマージ予定

**Deno Deploy利用者は早めの移行計画が必要** です。

---

### 💻 トピック3: Python 3.15.0 正式リリース
📅 2026年10月9日公開（出典: Python Insider）

異例の **3回目のリリース候補（rc3）** を経て、Python 3.15.0が正式リリースされました。

- **PEP 810: 明示的な遅延インポート**（`lazy import`）で起動を高速化
- **PEP 814: `frozendict` 組み込み型**、**PEP 661: `sentinel` 組み込み型**、**PEP 798: 内包表記内のアンパック**
- **PEP 686: デフォルトエンコーディングがUTF-8に**
- **PEP 799: プロファイリング専用パッケージ**、高頻度サンプリングプロファイラ **「Tachyon」** を同梱
- 型: `TypedDict` の追加項目型（PEP 728）、`TypeForm`（PEP 747）
- 性能: **実験的JITがx86-64 Linuxで標準インタプリタ比 約7〜8%高速**、AArch64 macOSでは末尾呼び出しインタプリタ比 約11〜12%高速
- フレームポインタが既定で有効化（PEP 831）、macOS公式バイナリはfree-threading対応を既定でインストール

> ⚠️ **macOS 27.0ではIDLE／tkinterのGUIアプリがダイアログを開く際にハングする問題** が報告されています。

---

## まとめ

- **Muse Wonder**: 長時間コーディングに強みを見せる一方、上位版はAPI非提供・重み非公開。数値はMeta自社評価を含む点に留意
- **Deno**: 本体は保守モードへ、**Deno Deployは半年で終了**。JSRは継続
- **Python 3.15**: 遅延インポート・frozendict・UTF-8既定化が中心。macOS 27.0のtkinter問題に注意

手元のプロジェクトに直接影響する話題が多い一日でした。環境への影響を一度確認しておきましょう。
