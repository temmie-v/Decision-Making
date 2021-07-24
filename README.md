意思決定論B/Cで課された演習問題を解く際に用いたプログラムを、課題締切後にこのリポジトリに残す。

---

# 意思決定論B
## 演習問題03

意思決定論Bで課された**演習問題03**では、78個の2×2ゲームについて、各主体の支配戦略(DS)、支配戦略均衡(DSE)、ナッシュ均衡(NE)、パレート最適(PO)な結果を求める必要があった。今回作成した`solver.cpp`ではこの問題を自動的に解くことを考えた。

78個の2×2ゲームは`ex03question.dat`に入力してあり、それを処理して結果を`ex03ans.dat`に出力する形式を取っている。
入力形式は次の通り：
```
Game 01 (01-21 ... Class I: Each player has a dominating strategy.)
4,4 3,3 
2,2 1,1

Game 02
4,4 3,3
1,2 2,1
```
上の段では各々が(a1, a2), (a1, b2)を選んだ時の利得を(主体1の利得:1～4),(主体2の利得:1～4)の順に、下の段では(b1, a2), (b1, b2)の時の利得を表している。ここに新たにゲームを追加することも可能だが、その場合はゲームとゲームの間の改行が必須である。

出力形式は次の通り：
```
Game 01 (01-21 ... Class I: Each player has a dominating strategy.)
(1,2)  a2  b2
  a1  4,4 3,3
  b1  2,2 1,1
1's DS: a1
2's DS: a2
DSE: (a1, a2)
NE:  (a1, a2)
PO:  (a1, a2)

Game 02
(1,2)  a2  b2
  a1  4,4 3,3
  b1  1,2 2,1
1's DS: a1
2's DS: a2
DSE: (a1, a2)
NE:  (a1, a2)
PO:  (a1, a2)
```
表として整形してある。


---

# 意思決定論C
## 演習問題 01, 02, 03

演習問題01から03では、シンプルゲームに関する問題が出題された。それぞれ、
- 01：主体が3人のときの proper シンプルゲーム
- 02：主体が3人のときの non-proper シンプルゲーム
- 03：主体が4人のときの proper シンプルゲーム

これをまとめて解くプログラムを、それぞれ`ex01.c`・`ex02.c`・`ex03.c`として作成した。
3つのコードに相違点はほとんどなく、あるのは3行目の主体の人数`N`の違い：
```c
#define N 3 // number of player (less than 5)
```
及び64行目の出力条件：
```c
if (isSimple(w) && isProper(w)) {
```
のみである。

入力は要求せず、全てのシンプルゲームWを出力する。`ex01.c`を例として、出力形式を次に示す：
```c
 N = {1,2,3}
 1 : {{1,2,3}}
 2 : {{1,2}, {1,2,3}}
...
11 : {{3}, {1,3}, {2,3}, {1,2,3}}
```

## 演習問題 09

演習問題09では、会議のコアに関する問題が出題された。主体を3人、代替案を3個として各選好・各シンプルゲームに関してコアを求める問題であった。

これを自動的に解くプログラムを`ex09.c`として作成した。各関数の機能は
- `sort`：配列のソート
- `printW`：シンプルゲームの出力
- `printCore`：コアの出力
- `printPref`：シンプルゲームと選好の組の出力
- `Core`：コアの導出(この解法のメインの部分)
- `solve`：上記機能のまとめ
である。入力は要求せず、表形式で解答を出力する。形式は次の通り：
```c
 N = {1,2,3}
 A = {a,b,c}

                 |Pref- 0|Pref- 1|Pref- 2|Pref- 3|Pref- 4|Pref- 5|
 1.{1,12,13,123} |{a}    |{a}    |{a}    |{a}    |{a}    |{a}    |
 2.{2,12,23,123} |{a}    |{a}    |{a}    |{a}    |{a}    |{a}    |
...
11.{12,13,23,123}|{a}    |{a}    |{a}    |{a}    |{a}    |{a}    |

                 |Pref- 6|Pref- 7|Pref- 8|Pref- 9|Pref-10|Pref-11|
 1.{1,12,13,123} |{a}    |{a}    |{a}    |{a}    |{a}    |{a}    |
...
                 |Pref-30|Pref-31|Pref-32|Pref-33|Pref-34|Pref-35|
...
11.{12,13,23,123}|{a}    |{a}    |{b}    |{b}    |{c}    |{c}    |


Cases that the core is empty:
Pref-22, W={12,13,23,123}
Pref-27, W={12,13,23,123}

Cases that the core is A:
Pref- 5, W={13,23,123}
...
Pref-35, W={123}
```
