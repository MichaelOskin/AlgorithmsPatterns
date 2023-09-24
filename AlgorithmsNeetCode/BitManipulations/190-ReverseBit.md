## [190\. Reverse Bit](https://leetcode.com/problems/reverse-bits/description/)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/377164b5-2b43-4dcb-9cc4-9d38357b0975)


Reverse bits of a given 32 bits unsigned integer.

**Note:**

- Note that in some languages, such as Java, there is no unsigned integer type. In this case, both input and output will be given as a signed integer type. They should not affect your implementation, as the integer's internal binary representation is the same, whether it is signed or unsigned.
- In Java, the compiler represents the signed integers using [2's complement notation](https://en.wikipedia.org/wiki/Two%27s_complement). Therefore, in **Example 2** above, the input represents the signed integer `-3` and the output represents the signed integer `-1073741825`.

&nbsp;

**Example 1:**

**Input:** n = 00000010100101000001111010011100
**Output:**    964176192 (00111001011110000010100101000000)
**Explanation:** The input binary string **00000010100101000001111010011100** represents the unsigned integer 43261596, so return 964176192 which its binary representation is **00111001011110000010100101000000**.

**Example 2:**

**Input:** n = 11111111111111111111111111111101
**Output:**   3221225471 (10111111111111111111111111111111)
**Explanation:** The input binary string **11111111111111111111111111111101** represents the unsigned integer 4294967293, so return 3221225471 which its binary representation is **10111111111111111111111111111111**.

&nbsp;

**Constraints:**

- The input must be a **binary string** of length `32`

&nbsp;

**Follow up:** If this function is called many times, how would you optimize it?

* Операция `| (OR)` (побитовое или) заменяет соответсвующий бит одного числа к другому числу (представленных двоично) если среди них имеется хотя бы 1 бит.
**Пример:** `6: 110 | 9: 1001 -> 15: 1111`
* Операция `&` (побитовое И): принимает два числа в качестве операндов и выполняет И с каждым битом двух чисел. Результат И равен 1, только если оба бита равны 1
**Пример:** `6: 110 & 9: 1001 -> 15: 0000` (бит старшего разряда  обнуляется)

**code**

```go
func reverseBits(num uint32) uint32 {
	var cpnm uint32 = 0
	for i := 0; i < 32; i++ {
		bit := (num >> i) | 1 // сдвиг с конца
		cpnm = cpnm | (bit << (31 - i)) // восстанавливаем правую часть битов -
		// (31 - i) с помощью cpnm
	}
	return cpnm
}

```

**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/70b36e53-1723-4ed7-97ba-504837a1b06a)
