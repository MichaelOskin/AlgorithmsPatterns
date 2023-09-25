### [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

> Given the `root` of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

### Код
```go
func rightSideView(root *TreeNode) []int {
	rs_view := []int{}
	queue := Queue[*TreeNode]{}
	queue.push(root)

	for queue.len() > 0 {
		var right_node *TreeNode
		qLen := queue.len()
		for i := 0; i < qLen; i++ {
			node := queue.pop()
			if node != nil {
				right_node = node
				queue.push(node.Left)
				queue.push(node.Right)
			}
		}

		if right_node != nil {
			rs_view = append(rs_view, right_node.Val)
		}
	}
	return rs_view
}
```
### Пояснение
Алгоритм решения этой задачи эквивалентен обходу дерева по уровням (задача №102). Во время каждой итерации необходимо следить за крайним правым ненулевым узлом, затем добавить его в результат.
Сложность алгоритма: **`O(N)`**.
