
A declaração de uma função na golang é bem simples:

```go
func sum(a, b int) int {
  return a + b
}
```

Como visto, usamos primeiro a palavra reservada func, seguido pelo nome da função e dentro dos parênteses os valores que ela vai (ou não) receber. Após isso nós definimos o tipo de retorno que aquela função vai ter, caso ela não retorne nada, vai ser vazio e vai seguir direto para as chaves.

#### Funções que retornam múltiplos valores
---
Em Go nós temos a possibilidade de uma única função retornar mais de 1 valor:

```go
func sum(a, b int) (int, error){
  if a + b >= 20 {
     return a + b, errors.New("a soma é maior que 50!")
  }
  return a + b, nil
}
```

Como visto, o tanto de retornos que nós teremos vem dentro de outros parênteses após os valores de input da função.
Nesse caso, fizemos algo comum em go: uma função que retorna os seus devidos valores e também um erro, caso aconteça algum durante sua execução.

No exemplo, caso o valor da suma seja maior ou igual a vinte, ele vai retornar o valor da soma e também o erro (que nesse caso não é bem um erro, mas funciona igual).
Caso o valor seja menor que 20, ele vai retornar apenas o valor da soma, visto que o `nil` equivale a um `null`.

#### Lidando com funções que podem (ou não) retornar erros
---
Uma estrutura bem comum quando lidamos com funções que podem retornar erros, é a seguinte:
```go
func main() {
  valor, err := sum(50, 10)
  if err != nil {
      fmt.Println(err)
  }
  fmt.Println(valor)
}
```

Nesse exemplo, nós declaramos duas **variáveis** e atribuímos a elas a chamada da função: `Valor`, recebe o valor da soma, `err`, recebe o possível erro.

Depois, fazemos uma verificação: se o valor de `err` for diferente de `nil`, que significa nulo, é porque ocorreu um erro. E se ocorreu, ele vai imprimir o erro.
Do contrário, vai imprimir o valor da soma.

#### Funções variádicas
---
Funções variádicas no Go são funções que recebem um único parâmetro que esse parâmetro pode receber 0 ou N valores.

Exemplo: Uma função de soma que recebe um único parâmetro chamado `numeros`. Pode ser atribuído a esse parâmetro 2 números ou então 50 números ou até mais.

A sintaxe de declaração é simples, definimos o parâmetro da função e na parte do tipo daquele parâmetro usamos `...`:
```go
func sum(numeros ...int) int {
  total := 0
  for _, numero := range numeros {
    total += numero
  }
  return total
}
```

A chamada dessa função pode ser da seguinte forma:
```go
func main() {
  fmt.Println(sum(1, 3, 6, 9, 12, 15, 18, 21, 23, 29, 38, 42))
}
```

Note que nesse caso o parâmetro números recebe 12 números diferentes, mas essa mesma função poderia receber apenas 1 ou até apenas 2 números. Bem como poderia receber mais 500, ou 1000.


#### Closures
---
Closures em Go são funções anônimas que nós podemos definir e usar dentro de outras funções. Sua sintaxe é simples: 
```go
func main() {
	func() int {
		//Bloco da função anônima
	}()
}
```

Essas funções podem ser atribuídas a uma variável, para que a variável guarde o valor de retorno delas:

```go
func main() {
  total := func() int {
    return sum(1,3,6,9,12,15,18,21,23, 29, 38, 42) * 2
  }()
  fmt.Println(total)
}
```
