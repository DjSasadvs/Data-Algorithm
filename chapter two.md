算法基础
=============
问题背景：对于一串序列{4，6，8，2，-3，68，9，0}，进行排序，形成有序序列，满足规则 an < an+1

插入排序
-----
* 思想：从序列第二个坐标起，依次与前面的比较，形成有序序列，然后坐标后移，重复动作，直至结束。
* 模型：扑克牌
* 复杂度：时间Θ(n*n)
* 实现c++
```
for j=1 to A.length-1
   key = A[j]
   i = j - 1
   while i >= 0 and A[i] > key
      A[i+1] = A[i]
      i--;
   A[i+1] = key
```

<br>
分治算法
---------
* 思想
  * 分解：将原问题分解为若干个自问题，分解成较小的实例
  * 解决：针对小问题进行分析、递归求解
  * 合并：合并子问题解成原问题的解
* 模型：组装高达，将每一部分零件分别组装，然后合并拼接
* 复杂度：时间-Θ(n*lgn)
* 实现：c++
```
merge_Sort(A, begin, end)
   if begin < end
      mid = ⌊(begin + end)/2⌋
      merge_Sort(A, begin, mid)
      merge_Sort(A, mid + 1, end)
      merge(A, begin, mid, end)
      
merge(A, begin, mid, end)
   n1 = mid - begin + 1
   n2 = end - mid
   let L[0..n1] and R[0..n2] be new arrays
   for i = 0 to n1-1
      L[i] = A[begin + 1]
   for j = 0 to n2-1
      R[j] = A[mid + 1 + j]
   L[n1] = R[n2] = ∞
   i = j = 1
   for k = begin to end
      if L[i] <= R[j]
         A[k] = L[i]
         i = i + 1
      else
         A[k] = R[j]
         j = j + 1
```
