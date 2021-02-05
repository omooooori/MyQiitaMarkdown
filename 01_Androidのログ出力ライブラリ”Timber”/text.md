どうも”おもり”です。

今年はOSS活動に精を出していこうと考えています。
Android開発のOSS活動。力不足の自分でもやっていけそうなissueを探している中、
以下のようなissueを見つけた。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/276053/740e7726-d41d-ab53-11ff-20d8c9a3246a.png)

[https://github.com/uhooi/UhooiPicBook-Android](https://github.com/uhooi/UhooiPicBook-Android)より


"good first issue"のタグが付いているので、いざやってみようと思ったのですが、
Timberとは何ぞや状態だったので、色々ネットを調べあさりました。
調べた情報をまとめて、Timberの良いところをサクッと学べるような記事を書きます。

# Timberとは？

Timberとは、Androidのログ出力ライブラリです。

Androidのログ出力機能といえば、Androidのログ標準ライブラリ（Log）があります。

```Logライブラリ
Log.v("MainActivity", "verbose")
Log.d("MainActivity", "debug")
Log.i("MainActivity", "info")
Log.w("MainActivity", "warn")
Log.e("MainActivity", "error")
```

※各ロギングの意味合い
Log.v：VERVOSE（すべてのログ情報）
Log.d：DEBUG(デバッグ情報）
Log.i：INFO(情報）
Log.w：WARN(警告）
Log.e：ERROR（致命的な問題）

しかし、ログ標準ライブラリを使うと問題があります。

* リリースビルドなのにでバックログが出力される
* デバックビルドなのにCrashlyticsに出力される

特に、リリースビルドでもでバックログが出力されることが大きな問題です。

# Timberを使って嬉しいこと

* デバックとリリースでログ出力を切り替えることができる。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/276053/c2cc754d-1696-007a-7144-71c06b8e4f5b.png)
※リリースの場合は、自分でロギングクラスを作成する必要がある。

* Logクラスの薄いラッパークラスなので導入が簡単

```
public class MyApplication extends Application {
  @Override
  public void onCreate() {
    super.onCreate();

    Timber.plant(new DebugTree());
  }
}
簡単に導入できる。TreeをPlantして、初期化をする。
```

* 書きやすい

```
Timber.tag("hoge").i("piyo=%s", "fuga");
```
Logライブラリの使い方と使用方法がそこまで違わないので、使うのが簡単。

* リリース後のクラッシュログの収集ができる。

Crashlytics等を使ってリリース後のクラッシュログを収集することができるらしい。
自分のアプリを作る時に試してみよう。


# 参考資料

[Androidのログ出力をいい感じにする](https://speakerdeck.com/cutmail/androidfalseroguchu-li-woiigan-zinisuru-number-potatotips-9)
[AndroidのTimber(ログ系)とFabric/Crashlytics(クラッシュレポート)を使ってみた。](https://araiyusuke.hatenadiary.com/entry/2015/11/01/182339)
[[Android] Timber で debug ビルド時のみにログを出力する](https://qiita.com/hkusu/items/d4f24141d11e05f57451)
[（Android）ログ出力ライブラリ"Timber"を使ってみる](https://iyemon018.hatenablog.com/entry/2017/09/12/170201)
[Logcatのソースへ飛ぶ機能をTimberに盛り込んでみた。](https://qiita.com/shiraji/items/5815bfe667d042051119)
[TimberをLogの代わりに使用して快適ログ確認](https://archive-blog.yagi2.dev/2016/12/06/how-to-use-timber.html)どうも”おもり”です。

今年はOSS活動に精を出していこうと考えています。
Android開発のOSS活動。力不足の自分でもやっていけそうなissueを探している中、
以下のようなissueを見つけた。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/276053/740e7726-d41d-ab53-11ff-20d8c9a3246a.png)

[https://github.com/uhooi/UhooiPicBook-Android](https://github.com/uhooi/UhooiPicBook-Android)より


"good first issue"のタグが付いているので、いざやってみようと思ったのですが、
Timberとは何ぞや状態だったので、色々ネットを調べあさりました。
調べた情報をまとめて、Timberの良いところをサクッと学べるような記事を書きます。

# Timberとは？

Timberとは、Androidのログ出力ライブラリです。

Androidのログ出力機能といえば、Androidのログ標準ライブラリ（Log）があります。

```Logライブラリ
Log.v("MainActivity", "verbose")
Log.d("MainActivity", "debug")
Log.i("MainActivity", "info")
Log.w("MainActivity", "warn")
Log.e("MainActivity", "error")
```

※各ロギングの意味合い
Log.v：VERVOSE（すべてのログ情報）
Log.d：DEBUG(デバッグ情報）
Log.i：INFO(情報）
Log.w：WARN(警告）
Log.e：ERROR（致命的な問題）

しかし、ログ標準ライブラリを使うと問題があります。

* リリースビルドなのにでバックログが出力される
* デバックビルドなのにCrashlyticsに出力される

特に、リリースビルドでもでバックログが出力されることが大きな問題です。

# Timberを使って嬉しいこと

* デバックとリリースでログ出力を切り替えることができる。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/276053/c2cc754d-1696-007a-7144-71c06b8e4f5b.png)
※リリースの場合は、自分でロギングクラスを作成する必要がある。

* Logクラスの薄いラッパークラスなので導入が簡単

```
public class MyApplication extends Application {
  @Override
  public void onCreate() {
    super.onCreate();

    Timber.plant(new DebugTree());
  }
}
簡単に導入できる。TreeをPlantして、初期化をする。
```

* 書きやすい

```
Timber.tag("hoge").i("piyo=%s", "fuga");
```
Logライブラリの使い方と使用方法がそこまで違わないので、使うのが簡単。

* リリース後のクラッシュログの収集ができる。

Crashlytics等を使ってリリース後のクラッシュログを収集することができるらしい。
自分のアプリを作る時に試してみよう。


# 参考資料

[Androidのログ出力をいい感じにする](https://speakerdeck.com/cutmail/androidfalseroguchu-li-woiigan-zinisuru-number-potatotips-9)
[AndroidのTimber(ログ系)とFabric/Crashlytics(クラッシュレポート)を使ってみた。](https://araiyusuke.hatenadiary.com/entry/2015/11/01/182339)
[[Android] Timber で debug ビルド時のみにログを出力する](https://qiita.com/hkusu/items/d4f24141d11e05f57451)
[（Android）ログ出力ライブラリ"Timber"を使ってみる](https://iyemon018.hatenablog.com/entry/2017/09/12/170201)
[Logcatのソースへ飛ぶ機能をTimberに盛り込んでみた。](https://qiita.com/shiraji/items/5815bfe667d042051119)
[TimberをLogの代わりに使用して快適ログ確認](https://archive-blog.yagi2.dev/2016/12/06/how-to-use-timber.html)