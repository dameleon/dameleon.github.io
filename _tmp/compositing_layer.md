# DOM と Compositing Layer と私

## 前提知識

以下の記事で Compositing Layer とはなんぞかという理解をしている上ですすめます

- [スムーズなアニメーションを実装するコツと仕組みを説明するよ。CPUとGPUを理解しハードウェアアクセラレーションを駆使するのだ！（Frontrend Advent Calendar 2013 – 06日目）](http://ginpen.com/2013/12/06/hardware-acceleration/)
- [Web描画パフォーマンスの改善](http://blog.cacoo.com/ja/2013/06/03/web-paint-performance/)
- [GPUアクセラレーションとposition: relativeによるレイヤー生成について](http://havelog.ayumusato.com/develop/performance/e556-compositing_border_and_layer.html)
- [ハイパフォーマンス・アニメーション](http://www.html5rocks.com/ja/tutorials/speed/high-performance-animations/#toc-composite-properties)
- [Accelerated Rendering in Chrome](http://www.html5rocks.com/ja/tutorials/speed/layers/) (※日本語訳が中途半端で終わってるので英語版がおすすめ)

Compositing Layer というのは、いわゆるハードウェアアクセラレーション
