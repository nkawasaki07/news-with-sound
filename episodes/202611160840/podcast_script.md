## AIとWebの最前線 デイリーニュースキャスト
**2026年11月16日（月）** ｜ 本日のトピック: 4件 ｜ サブテーマ: セキュリティ

本日は、IBMのプロンプトインジェクション対策モデル、Firefox 160の新機能、そしてセキュリティコーナーとしてChromeのゼロデイとFortinetの11月定例をお届けします。

---

### トピック1: IBM、プロンプトインジェクションに強いGranite 4.1 LLMONプレビューを公開
📅 2026年11月12日公開（出典: Hugging Face モデルカード、AI Weekly）

IBMがGranite 4.1ベースの実験モデル **LLMONプレビュー（3B／8B）** を公開。

- **LLMON（LLM Object Notation）**: プロンプトを `instr`・`data`・`doc`・`tool` などのブロックに分け、`exec` ブロックで実行する指示と入力を明示する記法。予約トークンで区切る
- **データやツール結果に含まれる命令には従わない**よう学習（間接プロンプトインジェクション対策）
- IBMの自社テスト（OPI・ASB・StruQ）で攻撃成功率が **53〜100% → 0.02〜5.6%** に低下
- 通常のチャット形式は想定外入力で品質低下。**「学習による振る舞いで保証ではない」** とIBM自身が注意喚起
- **Apache 2.0**、`apply_chat_template` で利用、vLLM・SGLangに対応

---

### トピック2: Firefox 160公開、WebTransportとオンデバイス音声認識を強化
📅 2026年11月10日公開（出典: MDN Firefox 160 リリースノート）

- **WebTransport**: コンストラクターに `headers` オプション、`responseHeaders` でサーバー応答ヘッダー取得
- `datagramsReadableType: "bytes"` でデータグラムを **BYOBリーダーで再利用バッファに読み込み可能**
- ⚠️ **破壊的変更**: `exportKeyingMaterial()` の `context` 引数が必須に、`outputLength` を追加
- 非標準の `incomingHighWaterMark` 等を削除し `incomingMaxBufferedDatagrams` 等へ
- **Web Speech APIがデスクトップで40言語のオンデバイス音声認識**に対応（Androidは非対応）
- CSS: `::-webkit-input-placeholder` を `::placeholder` の別名としてサポート

---

### 🔒 トピック3: ChromeのXML処理にゼロデイ CVE-2026-125350、悪用を確認
📅 2026年11月9日公開（出典: BleepingComputer）

- XMLパーサーの **Use-After-Free**（重要度High）
- Googleは **実環境での悪用を確認**、**2026年8件目のChromeゼロデイ**
- 修正: デスクトップ **157.0.8103.50 以降**（Mac は .50/.51）
- EdgeやElectronアプリなど **Chromiumベース製品も更新確認を**。CISA KEV登録済み（期限11/24）

---

### 🔒 トピック4: Fortinet 11月定例、FortiMailなどにCritical多数
📅 2026年11月10日公開（出典: Rescana、Fortinet PSIRT）

- **FortiMail**: 認証不要のパストラバーサル・コマンドインジェクション・SQLインジェクション（**CVSS 9.4〜9.8**）
- **FortiManager**（FGFM認可不備）、**FortiAuthenticator**（ハードコードパスワード等）にもCritical
- **FortiOS**: OSPF認証バイパス CVE-2026-126253（隣接ネットワーク限定）、SSH・WADプロキシの脆弱性
- 修正例: FortiOS **8.0.2／7.6.8／7.4.13／7.2.14**、FortiMail **8.0.2／7.6.7／7.4.9**
- **悪用は未確認**だが、外部公開機器から優先して更新を

---

## まとめ

- AI: **LLMON**のように「指示とデータを構造で分ける」アプローチがモデル側にも入ってきた。ただし単独の防御策にはしないこと
- Web: Firefox 160は **WebTransportの破壊的変更**に注意
- セキュリティ: **Chromeは悪用中**、まずブラウザ更新を。Fortinet製品を運用しているなら11月定例の適用を
