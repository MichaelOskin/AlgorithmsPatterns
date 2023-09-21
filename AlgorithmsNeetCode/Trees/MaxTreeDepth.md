### [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

> Given the `root` of a binary tree, return *its maximum depth*. A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

### Код
```go
func maxDepth(root *TreeNode) int {
	if root == nil {
		return 0
	}

	left_depth := maxDepth(root.Left)
	right_depth := maxDepth(root.Right)
	return 1 + int(math.Max(float64(left_depth), float64(right_depth)))
}
```
> [!NOTE]
> В go1.21 последняя строка может выглядеть так: `return 1 + max(left_depth, right_depth)`

### Пояснение
 Для решения задачи используется простая рекурсия: необходимо рекурсивно найти максимальную глубину для правого и левого поддерева. Если узел nil, то его глубина равна 0. Результатом будет максимальное значение из двух +1 с учетом текущего узла.

Сложность алгоритма: **`O(N)`**
