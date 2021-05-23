Python
*******

Terminalへのprintを同じ行にする
================================

例えば、プログラムの進捗状況を表示したいような場合。

.. code:: python

    import sys

    for i in range(1000000):
        sys.stdout.write("progress: %.2f%%\r\b" % (i/float(1000000)))
        sys.stdout.flush()

``\r\b`` は環境によって ``\r`` で良かったり、良くなかったり。

Homebrewのようなprogress barを作成する
======================================

次のようにすれば出来る

.. code:: python

    import sys

    bar_char = '#'
    bar_len  = 72
    loop_cnt = 1000000
    bar_cnt  = loop_cnt/float(bar_len)

    progress = ""
    c = 1
    for i in range(loop_cnt):
        if bar_cnt * c <= i:
            progress = bar_char * c + ' ' * (bar_len - c)
            c += 1
        sys.stdout.write(progress + " %.2f%%\r\b" % (i/float(loop_cnt)*100))
        sys.stdout.flush()
