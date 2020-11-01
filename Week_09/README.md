# 第九周学习笔记

## 高级动态规划

递归：

``` java
public void recur(int level, int param) {
     // terminator
     if (level > MAX_LEVEL) {
        // process result
        return; 
    }
    // process current logic
    process(level, param);
    // drill down
    recur(level: level + 1, newParam);
    // restore current status
}
```

分治：

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

动态规划和递归或者分治没有根本的区别，都是通过找到重复子问题来解决问题。

高阶的 DP 问题，通常状态拥有更多的维度，状态方程更加复杂。