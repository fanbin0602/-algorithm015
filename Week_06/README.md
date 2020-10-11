# 第六周学习笔记

动态规划与分治、回溯、递归，本质上都是通过找到重复的子问题，来解决问题。

递归代码模版：

``` py
public void recur(int level, int param) {
     // terminator
     if (level > MAX_LEVEL) {
       // process result
return; }
     // process current logic
     process(level, param);
     // drill down
     recur( level: level + 1, newParam);
     // restore current status
}
```

分治代码模版：

``` py
def divide_conquer(problem, param1, param2, ...):
  # recursion terminator
  if problem is None:
    print_result
return
  # prepare data
  data = prepare_data(problem)
  subproblems = split_problem(problem, data)
  # conquer subproblems
  subresult1 = self.divide_conquer(subproblems[0], p1, ...)
  subresult2 = self.divide_conquer(subproblems[1], p1, ...)
  subresult3 = self.divide_conquer(subproblems[2], p1, ...)
  ...
  # process and generate the final result
  result = process_result(subresult1, subresult2, subresult3, ...)
  # revert the current level states
```

- 利用数学归纳法的思维，切忌人肉递归。
- 找到最近最简单方法，拆解成可重复解决的子问题。
- 动态规划的关键点在于：找到最优子结构、存储中间状态、总结递推公式。
- 动态规划问题要注重实战，多多练习。