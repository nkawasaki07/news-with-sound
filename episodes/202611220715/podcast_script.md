## AIとWebの最前線 デイリーニュースキャスト
**2026年11月22日（日）** ｜ 本日のトピック: 3件 ｜ サブテーマ: プログラミング言語

本日は、ループ型の小型オープンモデル、Chrome 158の新機能、PHP 8.6の正式リリースを取り上げます。

---

### トピック1: Thinking Machines、ループ型の小型モデル「Inkling 2 Mini」をオープンウェイトで公開
📅 2026年11月20日公開（出典: Thinking Machines Lab 公式ニュース）

Thinking Machines Labが**Inkling 2 Mini**を公開し、**重みをHugging Face（thinkingmachines/Inkling-2-Mini）で配布**しました。

- **総約264億パラメータのMoE**（アクティブ数はページ内で34億／54億と表記が揺れている）
- 24層を6層ずつ4ブロックに分け、**中央の2ブロックを3回繰り返す「ループ型」**で、保存は24層・実行は1トークンあたり48層分
- 大半の層を**NVFP4で学習し、そのままの精度で配布**。メモリは**約20GB**、**32GB以上のMacならOllamaで動作**
- vLLM・SGLang・Ollama・Unsloth（GGUF）・llama.cppなどに対応、TinkerでAPI推論・ファインチューニングも可能

DeepSWE v1.1で48.2%など「100B未満のオープンモデルで首位」としていますが、**ベンチは自社測定**です。多数の制約を含む指示やマルチターン対話は弱いと発表元自身が明記しています。

---

### トピック2: Chrome 158安定版、`<install>`要素とメディア用の新しい疑似クラス
📅 2026年11月17日公開（出典: Chrome Platform Status、Frontend Focus）

**Chrome 158**が安定版になりました。主な変更点:

- **`<install>`要素と`navigator.install()`（Web Install API）**で、ページ上からWebアプリのインストールを開始できる
- 音声・動画向けの疑似クラス **`:playing`・`:paused`・`:buffering`・`:muted`** などが使えるようになり、**JSなしで再生状態に応じたスタイル**を当てられる
- `::highlight(*)`（詳細度ゼロのカスタムハイライト全体指定）、`flow-start`／`flow-end`の配置キーワード
- プログラムからのフォーカス移動を制限する **`focus-without-user-activation`** 権限ポリシー
- WebTransportに`draining`や`reliability`を追加、AndroidでもWebHIDが利用可能に（Android 17以上）

---

### 💻 トピック3: PHP 8.6が正式リリース、部分適用（Partial Function Application）を導入
📅 2026年11月19日公開（出典: php.net、Linuxiac）

本日のプログラミング言語コーナーです。**PHP 8.6.0**がリリースされました。

- **部分適用**: `version_compare(?, '8.6', '>=')`のように、プレースホルダー`?`と`...`で引数の一部を先に固定したクロージャを作れる
- **`\Time\Duration`クラス**: 日付やタイムゾーンに依存しない時間の長さをナノ秒精度で扱う
- **ポーリングAPI（`Io\Poll`）**: epoll・kqueueなどを使い、`stream_select()`の制約を回避。ReactPHPやAMPHPの基盤を想定
- **`clamp()`関数**、`SortDirection` enum、readonlyプロパティの既定値も追加

**挙動変更に注意**: `session.use_strict_mode`と`session.cookie_httponly`が**既定で有効**、SameSiteの既定は**Lax**に。`trim()`がフォームフィードも削除し、範囲外の値で`ValueError`を投げる関数が増えました。`mb_ereg()`や`spl_object_hash()`などは非推奨です。

---

## まとめ

- **生成AI**: Inkling 2 Miniは、層を繰り返すことで**小さなメモリで大きなモデル並みの計算**をする設計。ローカルLLMの選択肢が増えた
- **Web**: Chrome 158は**`<install>`要素とメディア疑似クラス**で、JSに頼っていた処理を宣言的に書けるように
- **言語**: PHP 8.6は**部分適用**でパイプ演算子と組み合わせやすくなった一方、**セッションの既定値変更**は移行時に要確認
