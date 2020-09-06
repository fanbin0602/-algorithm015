# 剑指 Offer 49. 丑数

``` java
class Ugly {
    int[] nums = new int[1690];
    Ugly() {
        nums[0] = 1;
        int p2 = 0, p3 = 0, p5 = 0;
        for (int i = 1; i < 1690; i++) {
            int ugly = Math.min(Math.min(nums[p2] * 2, nums[p3] * 3), nums[p5] * 5);
            nums[i] = ugly;
            if (nums[p2] * 2 == ugly) p2++;
            if (nums[p3] * 3 == ugly) p3++;
            if (nums[p5] * 5 == ugly) p5++;
        }
    }
}
class Solution {
    static Ugly ugly = new Ugly();
    public int nthUglyNumber(int n) {
        return ugly.nums[n - 1];
    }
}
```

解题思路：

预生成所有的丑数。

初始化 nums 数组，第一个元素的值为 1。初始化三个指针索引`p3`、`p3`、`p5`，值均为0，循环生成数组中的值，每次循环比较`nums[p2]`、`nums[p3] * 3`、`nums[p5] * 5`，取最小者，放入数组，并将与之对应的指针向后一步。

又一个需要注意的地方是，参数 n 为序号，并非索引，因此作为索引取值的时候需要 -1。