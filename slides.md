class: middle, center

<img src="./assets/logo.svg" align="center" width="200" />

Deno の これまで と これから

---
class: middle center

Deno 知ってますか? 🙋‍♀️🙋‍♂️

---
class: middle center

Deno 使ってますか? 🙋‍♀️🙋‍♂️

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

3年前

---
class: jsconfeu2018

JSConf EU 2018

---
~~10~~ 7 things I regret about Node.js

- Regret 1: Promise を使わなかった
- Regret 2: Security Sandbox を使わなかった
- Regret 3: GYP を使い続けてしまった
- Regret 4: package.json
- Regret 5: node_modules
- Regret 6: Extensionless module resolution
- Regret 7: index.js 

---
~~10~~ 7 things I regret about Node.js

- 1 -> Promise ベース API を 0 からデザイン ✅
- 2 -> V8 から出るときに権限をチェック ✅
- 3 -> 最初から GN を使う ✅
- 4 -> URL imports による依存解決 ✅
- 5 -> URL imports による依存解決 ✅
- 6 -> ブラウザ互換なモジュール解決 ✅
- 7 -> ブラウザ互換なモジュール解決 ✅

---
Deno とは

- 2018年に開発が始まった新しい JavaScript / TypeScript 実行環境。
- Ryan Dahl は改めて Node.js を使い始めようとしたが、いくつかの点で Node.js はデザインがおかしいと感じたため、新しいランタイムを 0 からデザインしようと考えた


---
class: inverse middle center

Deno のこれまで

---
Deno のこれまでのロードマップ
- Web 互換性
- TypeScript サポート
- ESM サポート
- V8 サンドボックスセキュリティ
- HTTPパフォーマンス

---
Deno のこれまでのロードマップ
- Web 互換性 ▲
- TypeScript サポート ✅
- ESM サポート ✅
- V8 サンドボックスセキュリティ ✅
- HTTPパフォーマンス ❌

v1.0 時点

---
Deno のこれまでのロードマップ
- Web 互換性 ✅
- TypeScript サポート ✅
- ESM サポート ✅
- V8 サンドボックスセキュリティ ✅
- HTTPパフォーマンス ▲

v1.16 (最新) では大部分達成

---
class: inverse middle center

Web 互換性

---
class: inverse middle center

TypeScript サポート

---
class: inverse middle center

ESM サポート

---
class: inverse middle center

サンドボックスセキュリティ

---
class: inverse middle center

HTTPパフォーマンス

---
class: inverse middle center
Deno のこれから

---
これからロードマップ
- HTTPパフォーマンス
- Node.js 互換性

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

- Deno が始まったのは Node.js の不満点を解決するため
- Deno は Web 互換性、セキュリティ、モジュールシステム、TypeScript サポートに力を入れてきて、一定の成果をあげた
- Deno はこれからは Node.js 互換性に力を入れる

---
class: middle center

<img src="./assets/logo.svg" align="center" width="200" />

End
