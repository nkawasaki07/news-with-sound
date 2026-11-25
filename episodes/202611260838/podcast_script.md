## AIとWebの最前線 デイリーニュースキャスト
**2026年11月26日（木）** ｜ 本日のトピック: 3件 ｜ サブテーマ: モバイル・デスクトップ

本日は、Baiduのオープンウェイト大規模モデル、webpackの新機能、Android開発者認証の世界展開をお届けします。

---

### トピック1: Baidu、ERNIE 5.5 Flash Previewの重みをApache 2.0で公開
📅 2026年11月23日公開（出典: OrcaRouter Blog、ERNIE公式リリースページ）

Baiduが11/11に発表した **ERNIE 5.5 Flash Preview** の重みを、**11/23にHugging Faceで公開**。

- **総280B・アクティブ14BのMoE**、文脈長 **約100万トークン**、テキスト入出力で思考は常時オン
- ライセンスは **Apache 2.0**（地域制限・売上条件のあるBase版とは別条件）
- **SGLang / vLLM 0.32.0＋Baiduプラグイン** での実行例あり。既定版（FP8＋MXFP4）でも重みだけで約166GB、**80GB GPU×4程度が必要**
- Terminal-Bench 4.0で46.5、DeepSWE v1.1で71.2などの数値は **Baiduの自己申告**。公式も **「事後学習途中のチェックポイント」** と明記

---

### トピック2: webpack 5.113、HTMLの `<style module>` でCSS Modulesに対応
📅 2026年11月19日公開（出典: webpack公式ブログ）

- HTMLエントリー内の **`<style module>` をCSS Modulesとして処理**し、markupの `class` 属性も自動で書き換え
- `<style module="card">` と `class="card.button"` で同名クラスの衝突を区別可能
- **JS内のセレクター文字列は書き換えない**ため、JSフックには `data-*` 属性を推奨
- SVG/XML最適化 `optimization.minimizeOptions.xml`、ローダーの `sourceTest` 条件、**CommonJSのツリーシェイキング改善**、HMR修正、`output.allowOutside` 追加
- 破壊的変更: `JavascriptParser.extend` と実験的 `TypeScriptPlugin` を削除

---

### 📱 トピック3: Androidのデベロッパー認証、2027年1月から全世界へ拡大
📅 2026年11月19日公開（出典: Android Developers Blog）

- 9/30からブラジル・インドネシア・シンガポール・タイで先行実施
- **2027年1月から、Google Play・Galaxy Store・Honor・Oppo・Xiaomi・Transsion・Vivoの7配信元でグローバル展開開始**、数か月かけて全ての国・認定端末上の全インストール経路へ
- 登録は1アプリ10分未満、すでに **インストールの99%超** をカバー
- **限定配布アカウントの端末上限が20台→50台** に。CI向けのDeveloper ID Status API・Developer Console APIも案内
- **Play外で配布する開発者はAndroid Developer Consoleアカウントの作成が必要**。Play開発者はPlay Consoleで登録状況を確認

---

## まとめ

- **AI**: ERNIE 5.5 Flash PreviewがApache 2.0で重み公開。ただし巨大で、性能は自己申告段階
- **Web**: webpack 5.113でHTML内CSS Modulesが利用可能に。JSセレクターは対象外に注意
- **モバイル**: Android開発者認証が2027年1月から世界展開。Play外配布の開発者は早めの登録確認を
