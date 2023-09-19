[338\. Counting Bits](https://leetcode.com/problems/counting-bits/)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/d0293853-a4c8-465c-af01-e17adecf87d0)

Given an integer `n`, return *an array* `ans` *of length* `n + 1` *such that for each* `i` 

(`0 <= i <= n`)*,* `ans[i]` *is the **number of*** `1`***'s** in the binary representation of* `i`.

&nbsp;

**Example 1:**

**Input:** n = 2
**Output:** \[0,1,1\]
**Explanation:**
0 --> 0
1 --> 1
2 --> 10

**Example 2:**

**Input:** n = 5
**Output:** \[0,1,1,2,1,2\]
**Explanation:**
0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101

&nbsp;

**Constraints:**

- `0 <= n <= 10<sup>5</sup>`

&nbsp;

**Follow up:**

- It is very easy to come up with a solution with a runtime of `O(n log n)`. Can you do it in linear time `O(n)` and possibly in a single pass?
- Can you do it without using any built-in function (i.e., like `__builtin_popcount` in C++)?



>Задача решается через формулу: `dp[i] = 1 + dp[i-4]`

Задачу можно было решить используя предыдущую: [example](), однако нам порядок необязателен, если мы можем узнать по формуле кол-во единиц.

**Визуальное представление**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/836b423b-17e4-42fb-b683-92a332081d99)

Т.е. мы можем сдвинуть закономерность `offsetом`, который с каждым шагом увеличивается на `2`. 
*Sequence offset* `1, 2, 4, 8, 16, 32...`

**code**

```go
func countBits(n int) []int {
    sl, ofst := make([]int, n+1), 1
    
    for i := 1; i < len(sl); i++ {
        if i == ofst*2 {
            ofst = i
        }
        sl[i] = 1 + sl[i-ofst]
    }
    return sl
}
```

**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/23d373be-9512-4973-90d8-ebf3e681c523)
