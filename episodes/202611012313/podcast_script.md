## AIとWebの最前線 デイリーニュースキャスト
**2026年11月01日（日）** ｜ 本日のトピック: 3件 ｜ サブテーマ: プログラミング言語

本日は、1兆パラメータ級オープンウェイトモデル、Firefoxの新CSS機能、そしてPHPのパッケージ管理に入ったサプライチェーン対策をお届けします。

---

### トピック1: Mistral AI、1兆パラメータの「Mistral Large 4」の重みを公開
📅 2026年10月29日公開（出典: The Next Web、Developers Digest）

Mistral AIが**総パラメータ約1兆のMistral Large 4の重みをHugging Faceで公開**しました（`mistralai/Mistral-Large-4-1T-A52B`）。

- **MoE（混合エキスパート）構成**で、1トークンあたりのアクティブは**約49B**（埋め込み等を含めて52B）
- コンテキストは**約100万トークン**、推論モードはlow／medium／high
- **vLLM・SGLang**に対応、NVFP4やllama.cpp向けGGUFビルドもあり
- ライセンスは改変MIT系で**商用利用可**、ただし**Model-as-a-Service事業は別途商用ライセンスが必要**

注意点として、4ビット版でも**複数GPUノードが必要**（量子化版はB200/B300の4基で動作）で、Terminal-Bench 4.0で41%などの**ベンチマークはMistral自社の測定**です。

---

### トピック2: Firefox 159、CSSスクロール連動アニメーションを既定で有効化
📅 2026年10月27日公開（出典: MDN Web Docs、gihyo.jp）

Firefox 159で**CSSのスクロール連動アニメーション（Scroll-driven Animations）が既定で有効**になりました。時間ではなくスクロール位置をタイムラインにアニメーションを進められ、**JavaScriptなしで読み進めバーなどを実装**しやすくなります。

ほかの主な変更:
- **スコープ付きカスタム要素レジストリ**: シャドウツリーごとに`CustomElementRegistry`を持て、Webコンポーネントの**名前衝突を回避**
- **HTML Sanitizer API**の`setHTML()`がパース時に不要な要素を除去する方式に
- WebGLの`EXT_clip_control`等の拡張に対応
- Nightly限定だった**旧masonry構文を削除**し、`display: grid-lanes`へ移行

---

### 💻 トピック3: Composer 2.11、新しい版の導入を待つ「クールダウン」機能
📅 2026年10月29日公開（出典: Packagist Blog、Freek Van der Herten's blog、Composer GitHub Releases）

PHPのパッケージマネージャー**Composer 2.11**が公開されました。目玉は**cooldownポリシー**で、**公開されたばかりのパッケージ版を設定期間インストールしない**ことで、乗っ取られたリリースを掴むリスクを下げます。急ぎのセキュリティ修正は`--no-cooldown`で回避できます。

- **破壊的変更**: 2.10で暫定追加された`source-fallback`を削除し、dist取得失敗時にソースへ切り替えない
- カスタムポリシーの`block-scope`で**`composer install`時のブロック**も可能に
- **セキュリティ修正**: 危殆化した**eMudhra中間証明書を拒否**、binプロキシのシェルメタ文字対策、`secure-http`の検出強化
- `audit --direct`、429応答と`Retry-After`への対応、依存解決の高速化

※機能の詳細は2.11.0-RC1のリリースノートに基づきます。

---

## まとめ

- **Mistral Large 4**: 1兆パラメータ級のオープンウェイトモデル。ただし動かすには大規模GPU環境が前提
- **Firefox 159**: スクロール連動アニメーションが既定で有効になり、CSSだけで書ける表現が広がった
- **Composer 2.11**: 新しい版をあえて待つクールダウンで、PHPのサプライチェーン対策が一歩前進

巨大モデルが手元で試せる形で公開される一方、パッケージ管理では**新しい版をあえて待つ**守りの設計が広がっています。
