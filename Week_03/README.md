# 第三周学习笔记

## 泛型递归、树的递归

递归是通过函数题来进行的循环。

递归的 Java 代码模版：

``` java
public void recursive(int level, int param) {
    // 递归终止条件
    if (level > MAX_LEVEL) {
        // 返回当前层结果
        return; 
    }
    // 执行当前层的逻辑
    process(level, param);
    // 调用下一层递归
    recursive(level + 1, newParam);
    // 还原当前层状态
}
```

## 分治、回溯

分治和回溯本质上都是递归，它们是两种解题思路。

- 分治是指将复杂问题拆解成子问题
- 回溯是指通过递归试错找到正确的解