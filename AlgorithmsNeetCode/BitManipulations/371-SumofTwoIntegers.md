## [371. Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/description/)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/e69e4b6c-86d4-412b-9bce-66bbd64b16bc)

Given two integers `a` and `b`, return *the sum of the two integers without using the operators* `+` *and* `-`.

&nbsp;

**Example 1:**

**Input:** a = 1, b = 2
**Output:** 3

**Example 2:**

**Input:** a = 2, b = 3
**Output:** 5

&nbsp;

**Constraints:**

- `-1000 <= a, b <= 1000`

## Решение

>В двоичном представлении сумма выглядит следующим образом:
> 5 + 6 = 11 :  `101 + 110 = 1011` . Логику можно представить (сдвигом `>>` c оператором `&`) и `xor ^`, который определяет сумму битов.
> Пример: Определяем сдвиг: `1000`, определяем сумму до сдвига `5 ^ 6 = 011`, суммируем последующим *xor* -> `1011: 11`

**code**

```go
func getSum(a int, b int) int {
    for b != 0 { 
		temp := (a & b) << 1 // сдвиг числа (100+0)
        a = a ^ b // sum xor
        b = temp
    }
    return a
}
```


**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/da0316b1-babc-467e-b97f-45bb219b3a61)

## Сложность
* Speed *O(1)*
* Capacity *O(1)*
