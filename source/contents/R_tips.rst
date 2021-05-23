R言語
******

ナンバリングされた複数のファイルを読み込む
==========================================

例えば"0000.txt"から"9999.txt"のようなファイル名であった場合

.. code:: r

    files <- "0000.txt"
    v     <- 1:9999
    v     <- formatC(v, width=4, format="d", flag="0")
    files <- append(files, paste(v, ".txt", sep=""))

    for (i in 1:10000) {
        file <- read.table(files[i])

        ...
    }

ある列で重複している要素を取り出す
===================================

下の例ではエラーが出る

.. code:: r

    file[duplicated(file$V1]

　 このようにしないとダメなようです

.. code:: r

    file[duplicated(file[,c("V1")]),]

　

この例では重複している2番目の要素からしか取り出されないので注意
