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

これをまとめて解くプログラムを、それぞれ`ex01.c`・`ex02.c`・`ex03.c`として作成した。入力は要求せず、全てのシンプルゲームWを出力する。
`ex01.c`を例として、出力形式を次に示す：
```
 N = {1,2,3}
 1 : {{1,2,3}}
 2 : {{1,2}, {1,2,3}}
...
11 : {{3}, {1,3}, {2,3}, {1,2,3}}
```
