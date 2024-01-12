Arrays na golang são declarados com um número fixo de valores, que não pode ser alterado após a sua declaração.
```go
func main() {
    var array [3]int
    array[0] = 1
    array[1] = 2
    array[2] = 3
    fmt.Println(len(array) - 1)
}
```

No exemplo acima declaramos um array com 3 posições e depois atribuímos valores a cada uma das posições.
No `Println()` nós utilizamos o método `len()` que é utilizado para checar o tamanho do array passado para ele. Após isso, **subtraímos** um dos valores pois o array começa do **zero** e assim ele vai considerar as posições de **0 a 2** (no exemplo, claro)

#### Iterando sob um array
---
A forma com a qual podemos iterar (percorrer) os valores de um array é através de um for loop.

A sintaxe do for na golang é um pouco diferente, sendo da seguinte forma:

```go
func main() {
    var array [3]int
    array[0] = 10
    array[1] = 20
    array[2] = 30
    fmt.Println(array[0])

    for i, v := range array {
        fmt.Printf("O índice %d contém o valor %d\n", i, v)
    }
}
```

Como vemos, não é utilizado **parênteses** na declaração desse **for**. Além do mais, não usamos nenhum método "`length`". No lugar dele utilizamos o `range`

Além do mais, utilizamos dois valores para controlar esse for: `i` (index, índice) e `v` (value, valor).
Nesse caso, ao rodar a primeira vez o `i` (index) vai ser 0, e o `v` (value) no index 0 é 10 e assim por diante.