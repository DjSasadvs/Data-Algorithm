分治策略
============

摘要
------
* 步骤
  * 分解：将原问题分解为一些子问题，子问题的形式同原问题一样，只是规模较小
  * 解决：步骤递归的求解子问题，如果规模足够小，则停止递归，直接求解
  * 合并：合并子问题解组合成原问题的解
* 求解递归式方法
  * 代入法：猜测一个界，通过数学归纳法证明其正确性
  * 递归树法：将递归式转化为一棵树，其节点表示不同层次的递归调用产生的代价，采用边界和技术求解递归式
  * 求解形如下面公式的递归式：<br/>
          T(n) = aT(n/b) + f(n)

最大子数组问题
-----
* 暴力求解Ω(n*n)<br/>
* 简单优化O(n\*n)<br/>
  利用之前计算出的子数组和来计算当前子数组的和，使得每个子数组和的计算时间为O(1)，从而暴力求解方法所花费的时间仍为O(n\*n)
* 使用分治策略的方法求解
  * 完全位于子数组A[low, mid]中，因此low <= i <= j <= mid
  * 完全位于子数组A[mid+1……high]中，因此mid < i <= j <= high
  * 跨越了中点，因此low <= i < mid < j <= high<br/>
  T(n) = Θ(nlgn)
    ```
    FIND-MAX-CROSSING-SUBARRAY(A, low, mid, high)
      left-sum = -∞
      sum = 0
      for i = mid downto low
        sum = sum + A[i]
        if sum > left-sum
          left-sum = =sum
          max-left = i
      right-sum = -∞
      sum = 0
      for j = mid + 1 to high
        sum = sum + A[i]
        if sum > right-sum
          right-sum = sum
          max-right = j
      return (max-left, max-right, left-sum + right-sum)
      
    FIND-MAXIMUM-SUBARRAY(A, low, high)
      if high == low
        return (low, high, A[low])                     
        //base case: only one element
      else mid = ⌊(low + high)/2⌋
        (left-low, left-high, left-sum) = FIND-MAXIMUM-SUBARRAY(A, low, mid)
        (right-low, right-high, right-sum) = FIND-MAXIMUM-SUBARRAY(A, mid+1, high)
        (cross-low, cross-high, cross-sum) = FIND-MAXIMUM-SUBARRAY(A, low, mid, high)
        if left-sum >= right-sum and left-sum >= cross-sum
          return (left-low, left-high, left-sum)
        else if right-sum >= left-sum and right-sum >= cross-sum
          return (right-low, right-high, right-sum)
        else return (cross-low, cross-high, cross-sum)
    ```

矩阵乘法的Strassen算法
----------------------
* 三重for循环:Θ(n\*n\*n)<br/>
  
  ```
  SQUARE-MATRIX-MULTIPLY(A, B)
    n = A.rows
    let C be a new n*n matrix
    for i = 0 to n
      for j = 1 to n
        c[i][j] = 0
        for k = 1 to n
          c[i][j] = c[i][j] + a[i][k] * b[k][j]
    return C
   ```
* 一个简单的分治算法 - 可以通过拆分矩阵为子矩阵来进行计算
* Strassen算法 - 总体是通过数学方法来降低了复杂度变为: Θ(n^lg7)
  * 拆分A、B为子矩阵，通过加减运算创建10个矩阵S[1……10]
  * 递归计算7次n/2 \* n/2矩阵的乘法，利用A、B、S计算P[1……7]
  * 对上述的P[i]矩阵进行加减法运算，计算出4个n/2 \* n/2的子矩阵

求解递归式
----------------
* 代入法
* 递归树
* 主方法
  * 主定理 定理4.1 令 a>=1 和 b>= 是常数，f(n)是一个函数，T(n)是定义在非负整数上的递归式：<br/>
  * T(n) = aT(n/b) + f(n)
  * 其中我们将 n/b 解释为⌈n/b⌉或 ⌊n/b⌋。那么T(n)有如下渐进界：
    * 若对某个常数 ε>0 有 f(n)=
    * not yet
[总目录-Back](https://github.com/DjSasadvs/Data-Algorithm/blob/master/README.md)
