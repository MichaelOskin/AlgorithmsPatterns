### [572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)

> Given the roots of two binary trees root and subRoot, return true if there is a subtree of root with the same structure and node values of subRoot and false otherwise. A subtree of a binary tree tree is a tree that consists of a node in tree and all of this node's descendants. The tree tree could also be considered as a subtree of itself.

### Код
```go
func isSameTree(p *TreeNode, q *TreeNode) bool {
	if p == nil && q == nil {
		return true
	}
	if p == nil || q == nil {
		return false
	}

	return p.Val == q.Val && isSameTree(p.Left, q.Left) && isSameTree(p.Right, q.Right)
}

func isSubtree(root *TreeNode, subRoot *TreeNode) bool {
	if subRoot == nil {
		return true
	}

	if root == nil {
		return false
	}

	if isSameTree(root, subRoot) {
		return true
	}
	return isSubtree(root.Left, subRoot) || isSubtree(root.Right, subRoot)
}
```

### Пояснение
 Для решения задачи можно использовать функцию из задачи №100 `isSameTree`. После надо добавить рекурсивные вызовы для левого и правого узлов и необходимые проверки.

Сложность алгоритма: **`O(N*M)`**, где N - кол-во узлов дерева, а M - кол-во узлов поддерева.
