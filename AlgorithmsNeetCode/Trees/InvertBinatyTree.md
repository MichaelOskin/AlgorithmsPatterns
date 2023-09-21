### [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

> Given the `root` of a binary tree, invert the tree, and return its root.

### Код
```go
func invertTree(root *TreeNode) *TreeNode {
	if root == nil {
		return nil
	}
	root.Left, root.Right = invertTree(root.Right), invertTree(root.Left)
	return root
}
```

### Пояснение
 Для решения задачи используется простая рекурсия: необходимо поменять местами рекурсивно инвертированные левый и правый узлы. Nil - точка выхода из рекурсии.

Сложность алгоритма: **`O(N)`**
