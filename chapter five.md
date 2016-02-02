概率分析和随机算法
------------------
### 雇佣问题
* HIRE-ASSISTANT策略
  ```
  HIRE-ASSISTANT(n)
    best = 0
    for i = 1 to n
      interview candidate i
      if candidate is better than candidate best
        best = i
        hire candidate i
  ```
  分析：O(ci\*n+ch\*m)
  
### 指示器随机变量
  * 引理5.1   给定一个样本空间S和S中的一个事件A，设XA=I{A}，那么E[XA]=Pr{A}
  * 用指示器随机变量分析雇佣问题<br/>

      >  E[Xi] = Pr{应聘者i被雇佣} = 1/i  
      >  E[X] = E[Σ{i:1……n}Xi] = Σ{i:1……n}1/i = lnn + O(1)

  * 引理5.2   假设应聘者以随机次序出现，算法 HIRE-ASSISTANT 总的雇佣费用平军情形下为 O(ch lnn) 

### 随机算法
  * RANDOMIZE-IN-PLACE - 可计算出一个均匀随机排列
```
RANDOMIZE-IN-PLACE(A)
  n = A.length
  for i = 1 to n
    swap A[i] with A[RANDOM(i, n)]
```
  * PERMUTE-BY-SORTING - 可产生输入的均匀随机排列
```
PERMUTE-BY-SORTING(A)
  n = A.length
  let P[1……n] be a new array
  for i = 1 to n
    P[i] = RANDOM(1, n^3)
  sort A, using P as sort keys
```
### 概率分析和指示器随机变量的进一步使用

* 生日悖论
* 球与箱子
* 特征序列
* 在线雇佣问题

[总目录-Back](https://github.com/DjSasadvs/Data-Algorithm/blob/master/README.md)
