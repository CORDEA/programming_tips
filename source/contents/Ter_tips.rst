Terminal
*********

tee コマンドで途中経過を出力する
================================

pipeでつないでいるコマンドの出力を確認したい場合、teeコマンドを用いれば可能。
teeの出力をファイルではなくTerminalに表示させる。

.. code:: sh

    % mkfifo /tmp/pipe
    % # 別のterminalで/tmp/pipeの中身をcatで見る
    % while true; do; cat /tmp/pipe; done
    % echo "aaa" | tee /tmp/pipe
    aaa

while文を実行しているterminalでも"aaa"と表示されているはず。

もしコマンド実行後もwhileが回り続けるのが気持ち悪ければ

.. code:: sh

    % mkfifo /tmp/pipe
    % while true;do;if [ -e /tmp/pipe ];then;cat /tmp/pipe 2> /dev/null;else;break;fi;done
    % echo "aaa" | tee /tmp/pipe; rm /tmp/pipe
    aaa

あまりおすすめはしない...
