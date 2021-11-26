class: middle, center

<img src="./assets/logo.svg" align="center" width="200" />

Deno の これまで と これから

---
アジェンダ

- Deno とは
- Deno のこれまでのロードマップ
- Deno のこれからのロードマップ

---
# 話す人

<img src="./assets/hinosawa.jpg" align="right" width="300" />

日野澤歓也 twitter @kt3k

- GREE (2012 - 2013)
- Recruit (2015 - 2019)
- Deno Land (2021 -)

<small>2018年から Deno にコントリビュートを開始。2020年作者に誘われ Deno Land に転職。現在はフルタイムで Deno と Deno Deploy を開発中。</small>

---
class: inverse middle center

Deno とは

---
class: inverse middle center

3年前

---
class: jsconfeu2018

JSConf EU 2018

---
「Node.js について後悔している10の事」

- Node.js の作者 Ryan Dahl が Node.js の現状のデザインについて、今の視点からみて後悔している7つの事を発表
- それを克服する新しい処理系として Deno プロジェクトを提案

<p style="text-align: center">
  <img src="assets/jsconfeu2018-2.jpg" width="400" />
</p>

---
7つの後悔

- 後悔1: Promise を使わなかった
- 後悔2: Security Sandbox を使わなかった
- 後悔3: GYP を使い続けてしまった
- 後悔4: package.json
- 後悔5: node_modules
- 後悔6: モジュール解決時の拡張子省略
- 後悔7: index.js

(詳細は Deno アドベントカレンダー「7つの後悔を振り返る」を参照)

---
対案としての Deno 、そのゴール

1. セキュリティ
2. ES Module
3. TypeScript ビルトイン
4. 実行ファイル単体で動く
5. モダンな開発環境を使う
6. 可能な限り Web 互換

などの目標が掲げられた (詳細は後述)

---
Deno とは

- サーバーサイド JavaScript 処理系
- TypeScript ビルトインサポート
- Web 互換 API (fetch, Web Crypto etc)
- Rust で書かれている (高速 & セキュア)
- サンドボックスセキュリティ機能 (後述)

---
class: middle center

# 要は

---
class: middle center

# Deno is

---
class: middle center

# Deno is "改良版" Node.js

---
class: middle center

<img src="./assets/node-sort-deno-tweet.png" align="center" width="600" />

---
class: inverse middle center
Deno のこれまで

---
Deno のこれまでのロードマップ
- Web 互換性
- TypeScript サポート
- V8 サンドボックスセキュリティ
- HTTPパフォーマンス

---
class: inverse middle center

Web 互換性

---
Web 互換性

- Deno には可能な限り Web 互換 API を取り入れるというデザイン方針がある

---
Web 互換性

- http client - fetch API
- バイナリ処理 - TypedArray API (Uint8Array, etc)
- ストリーミング処理 - Web Stream API
- URL parse - URL API
- PubSub - EventTarget API

---
Web 互換性

- 暗号 - Web Crypto API
- GPU - WebGPU
- http server - Request, Response API
- データ保存 - Web Storage API

---
Web 互換性 - 最近の進捗 - WPT

- 2021年1月 Web Platform テストを CI に導入
- Web Platform Test = ブラウザが共通で通している Web API のテストスイートがある
- コミット毎に Web 互換性をチェックするように

<p class="text-align: center">
<a href="https://wpt.fyi/results/?label=master&product=chrome%5Bexperimental%5D&product=edge%5Bexperimental%5D&product=firefox%5Bexperimental%5D&product=safari%5Bexperimental%5D&product=deno&aligned">
<img src="./assets/wpt.png" align="center" width="600" /></a>
</p>

---
Web 互換性 - 最近の進捗 - MDN

- 2021年8月 MDN への掲載が始まる

<p class="text-align: center">
  <img src="./assets/mdn.png" width="600" />
</p>


---
class: inverse middle center

TypeScript サポート

---
TypeScript サポート

- TypeScript をそのまま実行できる。

```ts
// sample.ts
const res = await fetch("https://example.com")
console.log(res.body.text);
```

```
$ deno run sample.ts  
Check file:///Users/kt3k/sample.ts
error: TS2531 [ERROR]: Object is possibly 'null'.
console.log(res.body.text);
            ~~~~~~~~
```

---
TypeScript サポート - 最近の進捗

- 2020年8月 `deno lsp` コマンドの導入
- VSCode とシームレスな連携 & Deno 固有な型情報の補完が出来るように

<p class="text-align: center">
  <img src="./assets/deno-vscode.png" width="600" />
</p>


---
class: inverse middle center

サンドボックスセキュリティ

---
サンドボックスセキュリティ

- V8 はブラウザ用 JavaScript エンジン
- ブラウザ上で JavaScript を安全に実行するため、実行環境が厳格にサンドボックス化されている。

---
サンドボックスセキュリティ

<p class="text-align: center">
  <img src="./assets/deno-diagram.svg" width="750" />
</p>

---
サンドボックスセキュリティ

- V8 Sandbox から出て runtime の機能を使う際に opcallSync / opcallAsync という関数を必ず通るデザインになっている
- その際に使おうとしてる機能に即したパーミッションを持っているかどうかをチェックする

---
サンドボックスセキュリティ

- 7種類のパーミッションがあり、コマンドライン引数で渡す
- `--allow-read` ファイル読み取り
- `--allow-write` ファイル書き込み
- `--allow-net` ネットワーク
- `--allow-env` 環境変数読み取り
- `--allow-run` プロセス実行
- `--allow-ffi` ネイティブ拡張の使用を許可
- `--allow-hrtime` 高精度タイマーの使用を許可

---
サンドボックスセキュリティ

各セキュリティに範囲指定が実装されています

カレントディレクトリのみ読み込み許可
```
deno run --allow-read=. program.ts
```

`dist/` ディレクトリのみ書き込み許可

```
deno run --allow-write=dist/ program.ts
```

---
サンドボックスセキュリティ

特定のドメイン・ポートのみネットワークアクセス許可

```
deno run --allow-net=example.com:80 program.ts
```

※攻撃コードが混入してしまった時に威力を発揮

---
サンドボックスセキュリティ - 最近の進捗

AWS のクレデンシャルの環境変数のみ使用許可

```
deno run \
  --allow-env=AWS_ACCESS_KEY_ID,AWS_SECRET_ACCESS_KEY \
  program.ts
```

git コマンドだけ使用許可

```
deno run --allow-run=git program.ts
```

---
class: middle center

Deno のユニークなデザインは<br />一定の評価を受けつつある

---
Deno の採用例

GitHub

---
Deno の採用例

Jake Archibold

---
Deno の採用例

Slack

---
class: inverse middle center
Deno のこれから

---
これからロードマップ

- 大まかな方向性には大きな変更は無し。(Web 互換性、TypeScript サポート、セキュリティには引き続き注力)

---
class: inverse middle center

2021年10月<br />
大きめのロードマップが追加

---
class: middle center

<img src="./assets/node-compat.png" width="750" />

---
class: inverse middle center

Node.js 互換性

---
Node.js 互換性をなぜやるか

- Deno は自体は良く出来ているが、Node.js と違いすぎるため使えないという意見が多い
- 実際 Deno の新規インストール数は、横ばい気味

---
Chicken and Egg problem

- Joel Spolsky の記事

---
Chicken and Egg problem

- あるプラットフォームを構築したい場合に
  - そのプラットフォームのユーザーが少なければそのプラットフォームで動くソフトは増えない
  - そのプラットフォームで動くソフトが少なければ、ユーザーは増えない

---
Chicken and Egg problem

- ユーザーが増えればソフトが増える、ソフトが増えればユーザーが増える
- どっちが先に増える?

---
Chicken and Egg problem

- ユーザーが増えればソフトが増える、ソフトが増えればユーザーが増える
- どっちが先に増える?

=> そのままではどちらも急には増えない

---
Chicken and Egg problem

- この問題を解決する方法が、前プラットフォームとの互換性をとること
- 例. windows 3.1
  - MS-DOS と互換性をとったため、最初から使えるソフトが多かった

---
Chicken and Egg problem

- 前プラットフォームとの互換性を取る事をしないプラットフォームは開発費が嵩むだけで、やがて力尽きるパターンが多い
- Deno はまさにこの状態になっていると Ryan Dahl は考えた(ようです)

---
Node.js 互換性

```
deno run --compat index.js
```

とすると、Node.js 用に書かれた index.js がそのまま動くという機能

デモ

---
Node.js 互換性

- 2022年Q2リリース予定

---
class: inverse middle center

まとめ

---
まとめ

- Deno は (大雑把に言うと) "改良版" Node.js
- Deno はこれまで Web 互換性、セキュリティ、TypeScript サポートに力を入れてきて、一定の成果をあげた
- Deno はこれから Node.js 互換性に力を入れる

---
class: middle center

<img src="./assets/logo.svg" align="center" width="200" />

End
