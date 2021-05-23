AWK
****

float型からint型への変換
========================
Pythonと同じです。

.. code:: awk

    BEGIN {
        c=3.0;
        print int(c)
    }

.. code:: bash

    % awk 'BEGIN{c=3.0;print int(c)}'
    3


AWKでもTerminalへのprintを同じ行にする
======================================

Pythonと同じで、プログラムの進捗状況を表示したいような場合。

.. code:: awk

    awk 'BEGIN{for(i=0;i<1000000;i++){printf("progress: %.2f%%\b\r",i/1000000)}}'

ファイルとして書くならこんな感じ

.. code:: awk

    BEGIN {
        for(i=0;i<1000000;i++) {
            printf("progress: %.2f%%\b\r", i/1000000)
        }
    }

