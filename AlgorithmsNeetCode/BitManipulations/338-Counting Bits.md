[LeetCode]()

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/d0293853-a4c8-465c-af01-e17adecf87d0)

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/83849673-7fe7-4e88-a265-bdcac7fcd973)


![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/38c4ecad-f30b-49fe-80d2-ac0a140622b9)


>Задача решается через формулу: `dp[i] = 1 + dp[i-4]`

Задачу можно было решить используя предыдущую: [example](), однако нам порядок необязателен, если мы можем узнать по формуле кол-во единиц.

**Визуальное представление**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/836b423b-17e4-42fb-b683-92a332081d99)

Т.е. мы можем сдвинуть закономерность `offsetом`, который с каждым шагом увеличивается на `2`. 
*Sequence offset* `1, 2, 4, 8, 16, 32...`

**code**

```go
func countBits(n int) []int {
    sl, ofst := make([]int, n+1), 1
    
    for i := 1; i < len(sl); i++ {
        if i == ofst*2 {
            ofst = i
        }
        sl[i] = 1 + sl[i-ofst]
    }
    return sl
}
```

**result**

![image](https://github.com/MichaelOskin/AlgorithmsPatterns/assets/139218970/23d373be-9512-4973-90d8-ebf3e681c523)
