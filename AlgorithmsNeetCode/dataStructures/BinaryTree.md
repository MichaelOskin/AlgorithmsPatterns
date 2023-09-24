# Binary Tree 🌱

>`Двоичное дерево` — это структура данных, в которой под каждым узлом располагается
не более двух других узлов. Это означает, что узел может быть связан
с одним или максимум двумя другими узлами. Первый узел дерева называется
`корнем` дерева. `Глубина дерева`, которую также называют высотой дерева,
определяется как самый длинный путь от корня до узла, тогда как `глубина узла` — это
количество ребер, соединяющих узел с корнем дерева. Узел дерева без дочерних
узлов называется `листом`.
Дерево является `сбалансированным`, если наибольшая длина от корневого узла
до листа не более чем на единицу превышает самую короткую длину. Иначе дерево
является `несбалансированным`. Балансировка дерева может быть сложной и медленной
операцией, поэтому лучше сохранять сбалансированность дерева с самого
начала, а не пытаться сбалансировать уже созданное дерево, особенно если оно
состоит из большого числа узлов.

**Пример бинарного дерева**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/2038a326-edda-4130-ad48-5d99a1e00976)

### Реализация бинарного дерева

```go

// Binary Tree left<root>right
type Tree struct {
	Left *Tree
	Value int
	Right *Tree
}

func traverse(t *Tree) {
	if t == nil {
		return
	}
	traverse(t.Left)
	fmt.Print(t.Value, " ")
	traverse(t.Right)
}

func insert(t *Tree, v int) *Tree {
	if t == nil {
		return &Tree{nil, v, nil}
	}
	if v == t.Value {
		return t
	}
	if v < t.Value {
		t.Left = insert(t.Left, v)
		return t
	}
	t.Right = insert(t.Right, v)
	return t
}

```

**using**

```go
package main

import (
	"fmt"
	"math/rand"
	"time"
)

func main() {
	tree := create(10)
	fmt.Println("The value of the root of the tree is", tree.Value)
	traverse(tree)
	fmt.Println()
	tree = insert(tree, -10)
	tree = insert(tree, -2)
	traverse(tree)
	fmt.Println()
	fmt.Println("The value of the root of the tree is", tree.Value)
}

func create(n int) *Tree {
	var t *Tree
	rand.Seed(time.Now().Unix())
	for i := 0; i < 2*n; i++ {
		temp := rand.Intn(n * 2)
		t = insert(t, temp)
	}
	return t
}
```