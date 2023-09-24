## [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/2c7d6622-32db-4eff-8b84-49704cba0678)


Write a function that takes the binary representation of an unsigned integer and returns the number of '1' bits it has (also known as the [Hamming weight](http://en.wikipedia.org/wiki/Hamming_weight)).

**Note:**

- Note that in some languages, such as Java, there is no unsigned integer type. In this case, the input will be given as a signed integer type. It should not affect your implementation, as the integer's internal binary representation is the same, whether it is signed or unsigned.
- In Java, the compiler represents the signed integers using [2's complement notation](https://en.wikipedia.org/wiki/Two%27s_complement). Therefore, in **Example 3**, the input represents the signed integer. `-3`.

&nbsp;

**Example 1:**

**Input:** n = 00000000000000000000000000001011
**Output:** 3
**Explanation:** The input binary string **00000000000000000000000000001011** has a total of three '1' bits.

**Example 2:**

**Input:** n = 00000000000000000000000010000000
**Output:** 1
**Explanation:** The input binary string **00000000000000000000000010000000** has a total of one '1' bit.

**Example 3:**

**Input:** n = 11111111111111111111111111111101
**Output:** 31
**Explanation:** The input binary string **11111111111111111111111111111101** has a total of thirty one '1' bits.

&nbsp;

**Constraints:**

- The input must be a **binary string** of length `32`.

&nbsp;

**Follow up:** If this function is called many times, how would you optimize it?

**Visual**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/c43a0f91-7913-4462-80c1-4e54345c213f)

## Решение
>Если сравнить биты текущего числа с  его предыдущим оператором `&`, мы избавимся от 1ой  последней единицы в числе `uint32`.



**code**

```go
func hammingWeight(num uint32) int {
    res := 0
    for num > 0 {
        num &= num - 1 // 
        res += 1
    }
    return res
}
```


**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/1ff75c04-2df8-438d-a25b-0e37b2497e2b)

## Сложность
* Speed *O(1)*
* Capacity *O(1)*
