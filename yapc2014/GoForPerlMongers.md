* Cに近い構文でかつLLっぽい
    * でもLLのノリで使おうとすると、Go嫌いになると思う。
    * そもそも、Goは静的片付け言語。コンパイルが必要。

* Goに「例外」なんて存在しない。「エラー型」を使え。
    * 複数の戻り値が使えるので、戻り値にエラー型を含めるのがGo流
    * panic() と recover() は使わない。強制終了するしかないような、どうしようもない場合にだけ、使うもの。


* GoroutineはPOSIXスレッドではない
    * プロセスモデルではない
    * Goroutineは何百万五生成しても大丈夫！

* Goの構造体設計
    * Cと同じような構造体が定義できる
    * オブジェクト指向なんてない。それっぽく書くことが出来るだけ。
　　* 継承ができない。
    * 無名埋め込み
        * 継承したかのように見えるが違う
        * 「継承」ではなく「委譲」。Traitに近い。
        * メソッドのオーバーライトができない
    * Go の 考え方
        * オブジェクト指向のような階層は作らない
        * 継承ではなく、小さい部品を作って埋め込むイメージ
    * Generics はない


* 並列処理
    * Goroutine の特徴
        * 別スレッドで任意の関数を実行
        * Gorutine がいつどのスレッドで実行されるかはわからない
        * POSIXスレッドとは違う
　　　　* fork/pthread のように回収をする必要はない
        * GoroutineのIDは取れない
            * 従って、killできない
        * SIGCHLD も発生しない
        * チャンネルを使ってGoroutineが終わるのを待つ。同期を取る。
