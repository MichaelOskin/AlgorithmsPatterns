[268. Missing Number](https://leetcode.com/problems/missing-number/)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/2075d7fb-84bb-4d2c-ba47-854e11c80a78)


Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return *the only number in the range that is missing from the array.*

&nbsp;

**Example 1:**

**Input:** nums = \[3,0,1\]
**Output:** 2
**Explanation:** n = 3 since there are 3 numbers, so all numbers are in the range \[0,3\]. 2 is the missing number in the range since it does not appear in nums.

**Example 2:**

**Input:** nums = \[0,1\]
**Output:** 2
**Explanation:** n = 2 since there are 2 numbers, so all numbers are in the range \[0,2\]. 2 is the missing number in the range since it does not appear in nums.

**Example 3:**

**Input:** nums = \[9,6,4,2,3,5,7,0,1\]
**Output:** 8
**Explanation:** n = 9 since there are 9 numbers, so all numbers are in the range \[0,9\]. 8 is the missing number in the range since it does not appear in nums.

&nbsp;

**Constraints:**

- `n == nums.length`
- `1 <= n <= 10<sup>4</sup>`
- `0 <= nums[i] <= n`
- All the numbers of `nums` are **unique**.

&nbsp;

**Follow up:** Could you implement a solution using only `O(1)` extra space complexity and `O(n)` runtime complexity?

**solution**

> Задача схожа c [SingleNumber](https://leetcode.com/problems/single-number/)  и имеет идентичное решение за исключением того, что мы сами определяем дублицирование последовательностью `0 - i+1`. *Xor ^* может использоваться без упорядочивания, его проход будет *O(n)*

**code**

```
func missingNumber(nums []int) int {
    el, length := 0, len(nums)
    for i := 0; i < length; i++ {
        el ^= i ^ nums[i]
    }
    return el ^ length
}
```

**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/ce42d740-6de8-4c13-b4be-19cde8a12378)
