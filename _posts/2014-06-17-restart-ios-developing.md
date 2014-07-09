---
layout: post
title:  "iOSの勉強をやり直す"
date:   2014-06-17 02:00:00
categories: ios 
---

1年前に買ったまま、ちょっとしたアプリを作ったり mixi さんのアレをやったくらいで終わった僕の iOS 知識を基礎の基礎から再び満たすために下記の写経をするのです。

[プロの力を身につける iPhone/iPadアプリケーション開発の教科書](http://www.amazon.co.jp/dp/4797367180)

今更 Objective-C かよプゲラｗｗｗｗって言われそうだが結局 Swift でもなんでも Cocoa の上で動いてるのは変わりないと思うので、まぁやっててそんはないんじゃないでしょうか。既存のモノ含め全部がいきなり Swift で動くわけじゃないだろうし。

あと、俺的にどうでもいいっていうか雑学レベルの項目は飛ばしていくのでそこんとこよろしくな。あと、多分初歩的なことだけ書いて終わりにするからそこんとこもよろしくな。

## Objective-C 入門

### 1-1-3 基本構文 (P.20)

C と一緒。以上。


### 1-1-4 クラスやライブラリのインポート (P.21)

C の include を拡張した import を使う。

    #import <Foundation/NSObject.h>
    #import "MyViewController.h"

クラス名のみ使いたい場合(ヘッダファイルなどで実装がいらない時)は @class 構文で使用する ClassName を宣言できる。

    @class MyClassName


### 1-1-5 クラスの宣言 (P.21)

クラスの宣言はヘッダファイルに記述する。 @interface と @end の間には、プロパティ宣言とメソッド宣言を記述できる。

    @interface ClassName : ParentClassName
    
    // プロパティ宣言
    
    // メソッド宣言
    
    @end

**注意**

- 多重継承ができない
- クラス変数の宣言はできない



### 1-1-6 ルートクラス (P.22)

NSObject 。何でもかんでも NSObject 。ミミズだってオケラだって、アメンボだって　NSObject 。

クラス宣言時に親クラスの指定を忘れるとオブジェクトが生成できないので注意。



### 1-1-7 メソッド宣言 (P.22)

#### 基本的な宣言のやり方

    //// 基本
    - (戻り値の型)メソッド名
    
    //// インスタンスメソッドとクラスメソッド
    // インスタンスメソッドは "-" で宣言
    - (int)doSomething
    // クラスメソッドは "+" で宣言
    + (int)doSomething
    
    //// 引数有りのメソッド
    - (戻り値の型)メソッド名:(引数の型)引数名
    // 複数の引数を持つ場合はラベル名を指定する
    - (戻り値の型)メソッド名:(引数の型)引数名 ラベル:(引数の型)引数名 ラベル:(引数の型)引数名

#### コンストラクタの宣言

Objective-C にはコンストラクタのための機能はないため `init` で始まるメソッドを使用するのがイディオム。また、戻り値は必ず `id` 型となる。

NSObject にはデフォルトコンストラクタのための init メソッドが実装されているため、 init の宣言を省略することができる。


#### メソッドのスコープ

Objective-C にはメソッドのスコープを指定するための機能が無い。そのため、ヘッダファイルに宣言されたメソッドは全て public メソッドとなる。 private なメソッドを宣言する場合は、ヘッダファイルではなく実装だいるにメソッドを宣言し、擬似的に private なメソッドとすることがイディオムとなっている。


### 1-1-8 プロパティ (P.24)

Objective-C はプロパティというインスタンス変数を外部に公開するための仕組みが用意されている。プロパティは getter, setter のアクセサを自動生成し、インスタンス変数として利用するために "_" を接頭辞とした名前を自動で宣言する。

    @interface Hoge : NSObject
    
    // プロパティの宣言
    @property (nonatomic, strong) NSString *value;
    
    @end

@property 構文のあとの括弧内はオプションとなっており、下記が設定できる。

- オブジェクト参照:
    - `strong`:  オブジェクトを強い参照で保持する
    - `weak`: オブジェクトを弱い参照で保持する

    デフォルトは `strong`
- スレッドセーフ
    - `atomic`: スレッドセーフにする
    - `nonatomic`: スレッドセーフにしない

    デフォルトは `atomic`
- アクセサ指定
    - `readonly`: 読み取り専用にする (setter メソッドを生成しない)
    - `readwrite`: 読み書きできる

    デフォルトは `readwrite`


### 1-1-9 クラス宣言の例 (P.25)

ここまでの内容をまとめると

    @interface Point : NSObject
    
    // プロパティ宣言
    @property (nonatomic) int value;
    // クラスメソッド宣言
    + (id)pointWithX: (int)x withY:(int)y;
    // コンストラクタ宣言
    - (id)initWithX: (int)x withY:(int)y;
    // メソッド宣言
    - (int)add: (int)num1 withNum:(int)num2

何か、本だとクラスメソッド宣言とコンストラクタ宣言のところが withY(int)y ってなってたけど間違いなのかな…？間違いだよね…？


### 1-1-10 クラス型変数の定義 (P.25)

クラスのメソッドや関数の中で暮らす型の変数を定義するには以下の2つの方法がある

- クラスの方を明示的に指定する方法
- id 型を使用する方法

    // クラスを明示的に指定する
    NSString *hoge1;
    NSArray *piyo1;
    // id 型を使用する方法
    id hoge2;
    id piyo2;

クラスの方を明示的に指定する場合は、変数をポインタ変数として定義すること。


### 1-1-11 文字列 (P.26)

Objective-C の文字列は NSString クラスのオブジェクトとして扱われる。ダブルクォーテーションで囲み、先頭に @ を付ける。

    NSString *hoge = @"!!!!!!!! hell world !!!!!!!!";


### 1-1-12 メソッドの呼び方 (P.26)

Objective-C でオブジェクトのメソッドを呼び出す場合は、オブジェクトとメソッドを [, ] で囲む。

    // 引数無しのメソッド
    [オブジェクト メソッド]
    // 引数有りのメソッド
    [オブジェクト メソッド:引数];
    [オブジェクト メソッド:引数 ラベル:引数];


### 1-1-13 プロパティへのアクセス (P.27)

"." です。


### 1-1-14 self (P.27)

インスタンスメソッド内で実行中のオブジェクトを表すのは `self`


### 1-1-15 super (P.27)

親クラスに定義されてるメソッドやインスタンス変数、プロパティにアクセスする場合は `super`


### 1-1-16 オブジェクト（インスタンスの生成）(P.28)

alloc と init(WithHoge) メソッドを使う。前述のとおり、コンストラクタという機能は存在しないので、 init をイディオムとして使う。

    // 引数なし
    HogeClass *hoge = [[HogeClass alloc] init];
    // 引数あり
    HogeClass *hoge = [[HogeClass alloc] initWithName:@"hoge"];


### 1-1-17 クラスの実装 (P.28)

`@implementation` と `@end` の間に定義を書く。インスタンス変数は、`@implementation {  }` のカギ括弧内に書く。 

    @implementation HogeClass {
        // ここにインスタンス変数   
    }
    // ここにメソッド
    @end

### 1-1-18 メソッドの実装 (P.28)

    -(戻り値の型)メソッド名:(引数の型)引数1 ラベル:(引数の型)引数2
    {
        return 戻り値;   
    }

### 1-1-19 コンストラクタの実装 (P.29)

何かコンストラクタの実装って項目いっぱいあるけど恨みでもあるのか。

    -(id)init
    {
        self = [super init];   
        if (self) {
            // 初期化のコード 
        }
        return self;
    }

if (self) ってしてる理由はなんだろ。取れないこともあるの？


### 1-1-20 デストラクタの実装 (P.29)

参照カウントが0になった時に呼ばれるメソッド。プロパティやインスタンス変数の開放処理などを行う。NSObject クラスに定義されてる dealloc メソッドがデストラクタ。

    -(void)dealloc
    {
        // このへんに開放処理
        [super dealloc]; // ARC 環境の場合は必要ない
    }


### 1-1-21 インスタンス変数の宣言 (P.30)

インスタンス変数はヘッダファイルに宣言することもできるが、最近は実装ファイルに宣言するのが主流。(最近とは) Objective-C では、インスタンス変数には接頭辞として "_" を付けるのがイディオム。(プロパティ宣言した時も勝手につくし)

Objective-C では宣言と初期化を同時に行うことはできない。コンストラクタの中で行う。

スコープが設定でき、以下の3種類

- `@public` : どこからでもアクセスできる。が、原則使用禁止でプロパティを使うべきとのこと。
- `@protected` : そのクラス、もしくはサブクラス(そのクラスを間接的もしくは直接的にスーパークラスとしているクラス)からアクセスできる。無指定の場合はこれ。
- `@private` : そのクラス内のみ。

    @implementation HogeClass {
        NSString *_hoge;
        // 下記はコンパイルエラー
        NSString *_hoge = @"moge";
    
        // スコープの設定
        @protected
            NSString *_hoge;
        @private
            NSString *_hoge;
    }
    
    -(id)test
    {
        self = [super init];    
        if (self) {
            // 初期化
            _hoge = @"hoge";
        }
        return self;
    }


### 1-1-22 プロトコル (P.31)

プロトコルはオブジェクトの振る舞いを規定するための仕組み。Java や C# におけるインターフェースの元になった仕組みだそうです。

    @protocol
    メソッド宣言;
    
    // @optional 以下は実装してもしなくてもいいメソッド
    @optional
    メソッド宣言;
    
    @end

プロトコルの適用、導入はクラス宣言時に行う。

    @interface クラス名:親クラス名 <プロトコル1, プロトコル2>
    @end

プロトコルは複数指定することができる。実際の例は以下

    @protocol Comparable
    -(int)compareTo:(id)o;
    @optional
    -(int)hoge;
    @end
    
    @interface Hoge:NSObject <Comparable>
    // ここでメソッドを宣言する必要はない
    @end
    
    @implementation Hoge
    
    -(int)compareTo:(id)o
    {
        // 処理   
    }


### 1-1-23 例外 (P.31)

Objective-C には例外の仕組みが用意されている。実行時例外と NSError クラスを使う2つのパターンが有る。

#### 実行時例外

    -(void)hoge
    {
        @try {
            // 通常処理
        } @catch (NSException *e) {
            // 例外処理
        } @finally {
            // 最終処理 
        }    
    }

    // 例外を throw する
    if (isSomeError) {
        NSException *exception = [NSException exceptionWithName:@"Exception" reason:@"Reason" userInfo:nil];
        @throw exception;
    }


#### 検査例外の代わりに使う NSError

エラーの発生する可能性のあるメソッドに NSError オブジェクトを参照渡ししてエラーの検査を行う

    // メソッド定義
    -(BOOL)setCategory: (NSString*)category error:(NSError**)outError
    {
        if (isError) {
            *outError = [NSError errorWithDomain:@"ドメイン" code:-1 userInfo:nil];    
            return NO;
        }   
        return YES;
    }
    
    // 使ってみる
    AVAudioSession = *audioSession = [AVAudioSession sharedInstance];
    NSError *error = nil;
    
    [audioSession setCategory:AVAudioSessionCategoryPlayAndRecord error:&error];
    
    if (error) {
        // エラー処理 
    }

### 1-1-24 カテゴリ (P.34)

Objective-C にはカテゴリと呼ばれる、クラスに動的にメソッドを追加することが出来る仕組みがある。要はクラス拡張です。

    // NSString を拡張してみるテスト
    
    // Hoge はカテゴリ名
    @interface NSString (Hoge)
    - (BOOL)isNilOrEmoty;
    @end
    
    @implementation NSString (Hoge)
    -(BOOL)isNilOrEmoty
    {
        // 処理   
    }
    @end

### 1-1-25 セレクタ (P.34)

Objective-C にはセレクタと呼ばれるC言語の関数ポインタやC#のデリゲートに似た仕組みがある。セレクタの指定には `@selector` を使う。

    -(void)viewDidLoad
    {
        UIButton *button = [UIButton buttonWithType=UIButtonTypeRoundedRect];   
        // ボタンクリック時に呼び出されるメソッドの指定
        [button addTarget: self
                   action: @selector(buttonClick)
         forControlEvents: UIControlEventTouchDown];
    }

    -(void)buttonClick
    {
        // ボタンがクリックされた時の処理    
    }


### 1-1-26 コレクション (P.35)

省略。


### 1-1-27 数値オブジェクト (P.37)

Obj-C では NSNumber クラスを使って int, long, float, BOOL などの各型をオブジェクトとして扱う。

    NSNumber *num = @9;
    NSNumber *numUnsigned = @9U;
    NSNumber *numLong = @9L;
    NSNumber *numLongLong = @9LL;
    
    NSNumber *numFloat = @9.123456789;
    NSNumber *numDouble = @9.123456789l;
    
    NSNumber *numYes = @YES;
    NSNumber *numNo = @NO;


### 1-1-28 名前空間は存在しない (P.37)

そして神は第七の日に「グループ名を単語で区切ったの頭文字を大文字で先頭につければよくね」と仰り NS (NextStep) を創造されました。


### 1-1-29 プログラムのエントリーポイント

main です。


--------------------------------

ぶっとんで P.111 から

### 2-1-10 UIViewController クラス

UIViewController の役割は以下

- ビューを管理する機能

    そのビューの一番上位の UIView オブジェクトを `view` プロパティとして保持し、管理する。また各種ライフサイクルによって呼び出されるイベントメソッドがある。

- 他のビューコントローラに遷移させる機能

    ストーリーボードに定義されているセグエ (segue) を参照して、他のビューコントローラに制御を移す。

    セグエには

    - Modal
    - Push
    - Custom

    の3つが存在する。

    セグエは遷移時のアニメーションを設定することができる。


### 2-1-11 ビューコントローラの種類

#### 表示支援系

- UITableViewController

    テーブルビューを表示するための機能を提供するクラス。 UITableView と組み合わせて使う。

- UICollectionViewController

    コレクションビューを表示するための機能を提供するクラス。 UICollectionView と組み合わせて使う。


#### 画面遷移支援系

- UINavigationController

    ナビゲーションを使った画面遷移の機能を提供してくれるクラス。

- UISplitViewController

    スプリットを使った画面遷移の機能を提供してくれるクラス。

- UITabBarController

    タブを使った画面遷移の機能を提供してくれるクラス。

- UIPageViewController

    ページめくりを使った画面遷移の機能を提供してくれるクラス。


UIViewController, UITableViewController, UICollectionViewController はクラスを継承して使用する。

--------------------------------

疲れたのでここまで @ 2014/06/19 23:13
