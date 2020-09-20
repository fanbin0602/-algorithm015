# 第四周学习笔记

## 深度优先搜索和广度优先搜索

遍历搜索，是在图/树中通过遍历所有的节点，寻找特定的节点。特点是每个节点都要访问一次，且只访问一次。根据对节点的访问顺序不同，分为：

- 深度优先遍历（Depth First Search，DFS）
- 广度优先遍历（Breadth First Search，BFS）

深度优先遍历代码：

``` java
class Solution {
    List<Integer> result = new ArrayList<>();
    Set<Node> visited = new HashSet<>();
    public List<Integer> dfs(Node node) {
        if (node != null && !visited.contains(node)) {
            visited.add(node);
            result.add(node.val);
            for (Node child : node.children) {
                dfs(child);
            }
        }
        return result;
    }
}
```

广度优先遍历代码：

``` java
class Solution {
    List<Integer> result = new ArrayList<>();
    Set<Node> visited = new HashSet<>();
    public List<Integer> dfs(Node node) {
        Queue<Node> queue = new LinkedList<>();
        if (node != null) {
            queue.add(node);
        }
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                Node curr = queue.poll();
                if (visited.contains(curr)) {
                    continue;
                }
                result.add(curr.val);
                visited.add(curr);
                queue.addAll(curr.children);
            }
        }
        return result;
    }
}
```

## 贪心算法

贪心算法是一种在每一步选择中都采取在当前状态下最有的算则，从而导致结果是全剧最优的算法。

贪心算法和动态规划的区别：

- 贪心算法对每一个子问题的解决方案都做出选择不能回退
- 动态规划会保存以前的运算结果，并根据之前结果对当前进行算则，可以回退。

使用贪心算法的条件是：问题可以分解成子问题来解决，并且子问题的最优解能递推到最终问题的最优解。这种子问题最优解也称为最优子结构。

## 二分查找

使用二分查找需要满足三个条件：

- 目标函数单调性（单调递增或递减）。
- 存在上下边界。
- 能够通过索引访问。

代码：

``` java
// Java
public int binarySearch(int[] array, int target) {
    int left = 0, right = array.length - 1, mid;
    while (left <= right) {
        mid = (right - left) / 2 + left;
        if (array[mid] == target) {
            return mid;
        } else if (array[mid] > target) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    return -1;
}
```