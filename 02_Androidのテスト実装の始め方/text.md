どうも”おもり”です。

Androidのテスト手法についてネットの情報は結構あるのですが、テストに触れたことが無い人にとっては実装まで進めるのが難しいと思います。この記事では、テストとは何なのか、どうやって実装するのかまで伝えられたら良いなと思います。

# テストとは？

テストとは、アプリケーションの動作が予想通りに動くことを確かめることです。
予想通りとは、ソフトウェアエンジニアっぽく言うと、顧客の要求通り/要件通り/仕様通りといったものになります。
顧客の要求が要件とずれていることもありますが、それは今回は考えないでください。

例えば、ボタンを押した時に、気象データを取ってくるアプリケーションがあったとします。

①ボタンを押しました。

②サーバーから気象情報の取得を開始します。

③サーバーから気象情報の取得が完了しました。

このような処理が進んだとします。これをテストするには、どうすれば良いでしょうか？

テストの対象は、ボタンが押された時の関数です。

```
fun getWeatherDataFromServer()
{

}
```

どのような気象データを取得するのか？
ボタンを押して、データ取得中に、ボタンは押すことができるのか？

Aという地点から気象データを取る。
Bという地点から気象データを取る。
Cという地点から気象データを取る。
　　：
　　：
このように、複数の地点できちんとデータが取れるのかも確認が必要です。
つまり、どんどんテストする項目は増加し、テスト項数も増加します。形は違えど、多くの企業がテスト項数の増加に悩まされていくのは間違いないです。

その全てのテストを手動で行っているとキリがありません。
なので、テストを自動的に行っていくように実装をする必要があります。
そのために、エンジニアはテストコードを書き、それが毎日実行されて結果が合格しているか確認できるようにしなければなりません。
そうやって、自分たちが作っているアプリケーションの品質が落ちないようにしないといけません。


# Androidのテストの種類

Androidのテストコードには、2種類のフォルダの保存先があります。

* Testフォルダ
* AndroidTestフォルダ


# Androidのテスト用ライブラリの有効化

JUnit
いわずとしれたJava用のユニットテストライブラリです。

Mockito
テスト時に各クラスをMock可するためのライブラリです。
具体的には通信処理のように、テスト中に本番の動きをされたら困るコンポーネントの動きを差し替えるために使用します。

Espresso
Android用のUIテスト用のライブラリです。
JUnitのテストコードの中で、Activityを起動したり、Viewを操作（クリックやスワイプなど）したり、表示内容を確認する機能があります。

```
// ローカルの単体テスト(JUnit 4)に必要
testImplementation 'junit:junit:4.12'

// 実機でのテストに必要
androidTestImplementation 'com.android.support:support-annotations:24.0.0'
androidTestImplementation 'com.android.support.test:runner:0.5'
```

# テスト項目


# テストコード実装

```
@Test
public void check_start_activity() {
    /* ここにテストする内容を書く */
}
```
