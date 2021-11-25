class: middle, center

<img src="./assets/logo.svg" align="center" width="200" />

Deno の これまで と これから

---
アジェンダ

- Deno の始まり
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
Deno のゴール

1. セキュリティ
2. ES Module
3. TypeScript ビルトイン
4. 実行ファイル単体で動く
5. モダンな開発環境を使う
6. 可能な限り Web 互換

(詳細は後述します)

---
Deno プロジェクトの始動

- 発表後一時的にDeno ブームのような状況に
- 数ヶ月程度するとブームが収まって地道な開発が始まる

---
class: inverse middle center

その後

---
2020

- 5月 Deno v1.0 リリース
  - ここからは6週(2021年からは4週)に1回リリースペースとなる
- 9月 Deno の会社が設立

2021

- 3月 Deno Deploy 発表
- 11月 Deno v1.16 リリース

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
