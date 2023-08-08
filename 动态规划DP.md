### 最大子数组和
---
[53. 最大子数组和](https://leetcode.cn/problems/maximum-subarray/)
可以转换为前置和的问题
用 pre 来记录前置和，并且实时更新ans
```java
public int maxSubArray(int[] nums) {
	int ans = nums[0], pre = nums[0];

	for (int i = 1; i < nums.length; i++) {
		pre = Math.max(pre + nums[i], nums[i]);
		ans = Math.max(ans, pre);
	}

	return ans;
}
```

### 任意子数组和的绝对值的最大值
---
[1749. 任意子数组和的绝对值的最大值](https://leetcode.cn/problems/maximum-absolute-sum-of-any-subarray/)
#### 解法一：动态规划 + 分情况讨论
按照 53. 最大子数组和的思路，我们可以找到最大子数组和最小子数组和的值，然后比较他们的绝对值大小。
```java
public int maxAbsoluteSum(int[] nums) {
    int maxSum = 0, currentMax = 0;
    int minSum = 0, currentMin = 0;

    for (int num : nums) {
        // 更新当前最大和最小和
        currentMax = Math.max(num, currentMax + num);
        currentMin = Math.min(num, currentMin + num);
        
        // 更新全局最大和最小和
        maxSum = Math.max(maxSum, currentMax);
        minSum = Math.min(minSum, currentMin);
    }

    return Math.max(Math.abs(maxSum), Math.abs(minSum));
}
```
#### 解法二：根据前缀和解决问题-- [[前缀和]]


