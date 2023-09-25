### [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

> Given the `root` of a binary tree, return the *level order traversal of its nodes' values*. (i.e., from left to right, level by level).

### Код
```go
type Queue[T any] struct {
	slice []T
}

func (q *Queue[T]) push(val T) {
	q.slice = append(q.slice, val)
}

func (q *Queue[T]) pop() T {
	node := q.slice[0]
	q.slice = q.slice[1:]
	return node
}

func (q *Queue[T]) len() int {
	return len(q.slice)
}

func levelOrder(root *TreeNode) [][]int {
	all_levels := [][]int{}
	queue := Queue[*TreeNode]{}
	queue.push(root)

	for queue.len() > 0 {
		level_nodes := []int{}
		qLen := queue.len()
		for i := 0; i < qLen; i++ {
			node := queue.pop()
			if node != nil {
				level_nodes = append(level_nodes, node.Val)
				queue.push(node.Left)
				queue.push(node.Right)
			}
		}

		if len(level_nodes) > 0 {
			all_levels = append(all_levels, level_nodes)
		}
	}
	return all_levels
}
```
### Пояснение
 Во-первых для решения задачи необходимо реализовать FIFO стркуктуру - Queue[T any]. Алгоритм заключается в том, чтобы каждый ненулевой узел "развернуть", т.е. снять его из очереди и добавить в очередь его потомков.
 
 ![levelOrderTraversal](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/45241991/e1926610-2257-4989-8c2e-b29c4f75c069)

Сложность алгоритма: **`O(N)`**, так как каждый узел мы посещаем один раз.
