
Na golang, como visto anteriormente, arrays possuem tamanho fixo que não pode ser alterado após sua declaração.

Os slices vão em outra direção e possuem um tamanho dinâmico. Portanto, o tamanho do slice vai depender única e exclusivamente de quantos elementos nós **adicionamos** ou **removemos** dele.

A forma de declarar um slice é usando a base da declaração de um array mas sem definir um tamanho do array, seguido pelo **tipo** do slice e **chaves** { } onde podemos (ou não) definir os valores iniciais daquele slice.
```go
slice := []int{1, 2, 3, 4} //slice com os valores iniciais definidos

slice2 := []int{} //slice sem valores iniciais
```

Exemplo da dinamicidade dos slices:

```go
slice := []int{10, 20, 30, 40, 50, 60, 70, 80, 90, 100}

fmt.Printf("len=%d cap=%d %v\n", len(slice[:0]), cap(slice[:0]), slice[:0])
```

No código acima, ao `Printf()` ser executado, estamos dizendo no `len`, `cap` e no `slice` (valores do slice) que só queremos que sejam exibidos valores que estejam antes daquele índice, nesse caso, o índice 0.

Como bem sabemos, índice 0 é o primeiro índice de um array e consequentemente um slice, que por baixo dos panos é praticamente um array. Então ao executar aquilo, vai ser exibido que o tamanho é zero e os valores não serão exibidos, entretanto, o `cap` (que diz respeito a capacidade do slice) vai ser considerado 10.

Isso acontece porque apesar de dizermos que o slice não tem mais dez itens que a capacidade vai ser alterada da original, que era dez.

Nós podemos também exibir somente os itens presentes após até o índice que indicarmos, bastando alterar a ordem dos dois pontos e o índice:

```go
fmt.Printf("len=%d cap=%d %v\n", len(s[2:]), cap(s[2:]), s[2:])
```

Nesse caso, vão ser exibidos todos os itens que vêm após o segundo item do slice. Porém, a capacidade do slice vai ser alterada, nesse caso descendo de 10 para 8.

Nós podemos adicionar itens ao nosso slice, levando em conta que ele é dinâmico. Entretanto, a forma como o slice funciona é que por baixo do pano ele aponta para um array de tamanho fixo (tamanho esse definido quando declaramos o slice).

Então quando nós adicionamos um novo item no nosso slice, o mesmo vai por baixo dos panos criar um novo array com um tamanho maior. Com isso nós pensamos que se antes tínhamos um slice com 10 itens e consequentemente 10 de tamanho, ao adicionar um novo item nele, o tamanho deveria ir para 11, correto?

Mas não é o que acontece. Ao adicionar um novo item no slice o mesmo vai notar se ele tem ou não capacidade para ter aquele item. Caso não tenha, ele vai criar um novo array e o tamanho desse array vai ser o tamanho do slice anterior duplicado.

Então, se o slice anterior tinha 10 de tamanho, ao adicionar um 11º item, ele vai passar a ter 20 de tamanho, mesmo que contenha apenas 11 itens.

```go
s := []int{10, 20, 30, 40, 50, 60, 70, 80, 90, 100}

s = append(s, 110)
fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
```

No código acima nós tínhamos um slice que inicialmente possuía 10 itens e consequentemente 10 de tamanho.

Ao usarmos o método `append()` (utilizado para adicionar itens ao slice) foi adicionado um 11º item e acontece o que foi dito acima, de o tamanho do slice passar de 10 para 20.