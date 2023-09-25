## [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/10fe40b1-c98f-436c-9482-4fad7a113670)

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1.  Open brackets must be closed by the same type of brackets.
2.  Open brackets must be closed in the correct order.
3.  Every close bracket has a corresponding open bracket of the same type.

&nbsp;

**Example 1:**

**Input:** s = "()"
**Output:** true

**Example 2:**

**Input:** s = "()\[\]{}"
**Output:** true

**Example 3:**

**Input:** s = "(\]"
**Output:** false

&nbsp;

**Constraints:**

- `1 <= s.length <= 10<sup>4</sup>`
- `s` consists of parentheses only `'()[]{}'`.


## Решение
>Используя структуру данных `Stack`(первым вошел - первым вышел)  и хэш `pairs` мы можем удалять базовые случаи `"()[]{}"`. Простым условием будет проверка предыдущей противоположной скобки, а также условие длины стека в конце

**visual**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/fbd9e405-3bff-4842-9d97-7a0fbb18ff8b)

**code**

```go
func isValid(s string) bool {
	pairs := map[byte]byte{
		'}': '{',
		']': '[',
		')': '(',
	}

	stack := make([]byte, 0)

	for _, char := range []byte(s) {
		pair, ok := pairs[char]
		if !ok {
			stack = append(stack, char)
			continue
		}

		if len(stack) == 0 {
			return false
		}

		if stack[len(stack) - 1] != pair {
			return false
		}

		stack = stack[:len(stack) - 1]
	}

	return len(stack) == 0
}
```

**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/609409c1-791d-45c9-88fa-7fe150c3123e)

## Сложность
* Speed *O(n)*
* Capacity *O(n)*
