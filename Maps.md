
Maps na Golang são HashTables, portanto é uma estrutura de dados que funciona com base em chave e valor.

```go
package main 

import "fmt"

func main() {
    salarios := map[string]int{"Lucas": 2200, "Fulano": 1500, "Ciclano": 3500}
    fmt.Println(salarios["Lucas"])
}
```

Na declaração, nós definimos o tipo da chave (entre colchetes) e após o colchete o tipo dos valores, que devem ser definidos dentro de chaves.

Podemos adicionar e remover valores de um map da seguinte forma:

```go
delete(salarios, "Ciclano") //Removendo a chave ciclano
salarios["Beltrano"] = 3200 //Adicionando a chave Beltrano com o salário de 3200
```

#### Função make
---
A função make na golang permite que a gente crie um map vazio. O que permite que possamos popular o map com valores ao longo da aplicação.

```go
sal := make(map[string]int) //Declarando um map vazio com a função make
sal["Fulano"] = 1412

sal1 := map[string]int{} //Declarando um map vazio sem função make
sal1["Lucas"] = 1500
```


#### Percorrendo um map
---
A forma de iterar sob um map é a mesma de sempre, utilizando um for loop

```go
salarios := map[string]int{"Lucas": 2200, "Fulano": 1500, "Ciclano": 3500}  

for nome, salario := range salarios {
  fmt.Printf("O salário de %s é %d\n", nome, salario)
}
```

No exemplo acima vai ser imprimido os três nomes (chaves) e seus salários correspondentes.

Nós podemos também ignorar as chaves e imprimir somente os salários, utilizando algo que é chamado de blank identifier, que é definido através de uma underline _

```go
salarios := map[string]int{"Lucas": 2200, "Fulano": 1500, "Ciclano": 3500}  

for _, salario := range salarios {
  fmt.Printf("O salário é %d\n", salario)
}
```