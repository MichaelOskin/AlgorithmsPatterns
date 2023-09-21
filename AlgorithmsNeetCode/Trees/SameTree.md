### [100. Same Tree](https://leetcode.com/problems/same-tree/)

> Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not. Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

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
```

### Пояснение
 Для решения задачи также используется простая рекурсия: необходимо сравнить значения данных узлов и  рекурсивно проверить идентичность левых и правых узлов. Результат будет положительным только если все три компонента равны.

Сложность алгоритма: **`O(N*M)`**, где N - кол-во узлов дерева, а M - кол-во узлов поддерева.
