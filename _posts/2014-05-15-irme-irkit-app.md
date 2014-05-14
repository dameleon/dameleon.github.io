---
layout: post
title:  "ぼくと IRKit と irme"
date:   2014-05-15 02:20:00
categories: irme nodejs angularjs
---

[IRKit][irkit] が届いた週にノリと勢いで [node-irkit][node-irkit] というものを書いていた。node.js から IRKit を操作するためのベースライブラリみたいなものだ。

最近は会社で AngularJS ばかり触っているのだが、慣れてきたこともあって1つ何か作ってみようと思うところで [irme][irme] という Web アプリを書いてみようと思う。

### irme

簡単にいえば、よくある汎用リモコンを Web App で作ってみよう、というもの。

ブラウザ画面上に自由にボタンを配置することができ、ボタンの機能自体も Web 上で設定できるようにするとかなり便利な気がしている。特に、これは僕が欲しいだけなんだけどいろいろなリモコンの信号を組み合わせて1つのボタンにするとかできるとかなり捗る気がする。

サーバーサイドもつくろうと思っているので、外から赤外線の ON, OFF も可能。

どうせならステータスの保存なんかもしておくと便利な気がする。(受信先の状態に依存するので完璧にはいかないが)

相変わらず気長に作る気なので、気長に見守ってあげてください。

--------------

あ、あとメモ書きする md をどうせなら公開できるようなサイトが欲しかったので jekyll と Github で作ってみた。割といいかんじである。

[irme]: https://github.com/dameleon/irme
[irkit]: http://getirkit.com/
[node-irkit]: https://github.com/dameleon/node-irkit
