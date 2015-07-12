---
layout: post
title:  "片手間で始めるプロジェクトマネジメント"
date:   2015-02-25 00:00:00
categories: project_management
---

どうも、死にゆく2015年です。

今回は"片手間で始めるプロジェクトマネジメント"について語らせて頂きます。


## 想定する読者

- エンジニアを嗜む方
- プロジェクトが炎上している、もしくは炎上しかけている
- スケジュール管理という概念がさほどない
- もちろんリソース管理という概念もさほどない
- 管理業をしてくれる(or まともにできる)人がいない
- 管理を行う人数は5-10人程度


## 片手間PM第一歩目 -下準備-

まず、何はともあれツールが必要です。ケチってGoogle Spread SheetとかExcelとか使い出すとろくなことにならないので、ツールを見繕います。

今回、僕の選定のポイントとして

- 素人でもそれなりのガントチャートが引ける
- 複数人作業がしやすい(誰かしか編集できない、という状態にしない)
- UIがそれなりに分かりやすい
- APIやエクスポータなどで、ツール連携がしやすい
- Macで使える
- 導入が簡単(大企業対策)

の5つとしました。

以下に、大体有名なソフト辺りを適当に書きます。

- Microsoft Project
    - 見たことはあるけど使ったことない
    - なんか本業の人がみんな良いって言ってるのは聞く
    - 高い
    - Windowsしか使えない
        - Office365なら使える？
    - 共有はしやすそう
- OmniPlan
    - 大体MS Projectと同じらしい
    - それなりのお値段
        - $199.99
    - わりと使いやすい
    - Macしか使えない
    - でもiPadでは使える
    - プロジェクト管理のファイルをリポジトリという概念のWebDavサーバにアップロードできる
    - Omni系のソフトウェアとの親和性が高いらしい
- xPlan
    - MS Project互換(って触れ込み)
    - それなりのお値段
        - $100?
    - UIはそれなり
    - Macしか使えない
    - 共有系の機能が不明だった
- Backlog
    - チケット管理からガンチャ、バンチャまでこいつ一本でいけるWebApp
    - それなりのお値段
    - UI、分かりづらくはないが取っつきにくい(項目が多かったり)
    - WebAppなのでWindowsでもMacでも
    - WebAppらしく、共有とかそういうことは考えなくていい
    - 導入がめんどそう(大企業)

弊プロジェクトではチケット管理などは別のツールを使っていて、今回はガントチャートが引けることが大目標なのでOmniPlanを導入した。


### 片手間PM第二歩目 -基本的な考え方とか-

#### なぜ人類にガントチャートが必要か

[ガントチャートについてはこちら](http://ja.wikipedia.org/wiki/%E3%82%AC%E3%83%B3%E3%83%88%E3%83%81%E3%83%A3%E3%83%BC%E3%83%88)

いわゆるプロジェクトが燃えている状態と言っても多々あるが、ここでは特にリリースとそれに対するタスクを進行する上で何らかの要因により上手くいかない状況が多発していることを指す。

まず、そういった状況を簡単に分類し、要因などを挙げてみると

- リリース日が確定してる
    - タスクの総量も分かっていない状態では危険
    - 
- タスクの意味が不明
    - 仕様があやふやな状態
    - 論外なので開発を止めた方がいい
- タスクの依存関係が不明
    - 上流工程が、下流工程の作業を意識していない
    - コミュニケーションがとれていない
- タスクがありすぎる
    - そもそも現在の人数では回せない可能性がある
- 人的リソースが適切に配置されていない
    - シングルポイントでネックになる人が、全体を遅らせている
    - 個人個人で能力バランスが悪い







