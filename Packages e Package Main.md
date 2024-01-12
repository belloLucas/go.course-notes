No Go nós temos o package e o arquivo main que funciona de forma similar ao Java, onde nós temos uma classe Main que vai conter o método main() para inicializar a aplicação.

No caso do Go, além de ter o arquivo `main.go` é preciso que declaremos no topo desse arquivo que ele faz parte do `package main`.

Apesar disso, nós podemos ter também outros pacotes que vão conter outros arquivos para compor a aplicação. E em relação a isso, o package também deve ser declarado no início de cada um desses arquivos. A diferença aqui é que em arquivos de outros pacotes, nós vamos definir o nome daquele package com o nome do diretório onde o arquivo está, exemplo:

![[Pasted image 20240111101543.png]]
Na estrutura de pastas acima, temos a pasta raiz sendo a `curso-go`, dentro dela temos a pasta `01` que dentro contém o arquivo `main.go` (onde vai conter o `package main`) e também o diretório `routes`, que dentro possui um arquivo `route.go`. Esse arquivo `route.go` vai ter a declaração de `package routes`, pois é o diretório onde ele se encontra.

Agora, caso tenha mais de um arquivo no mesmo diretório, todos eles precisam ser declarados como estando no mesmo package.

Exemplo: no diretório `01` temos além do `main.go` um outro arquivo chamado `a.go`.
Com o exemplo acima, todos os dois arquivos precisam ser declarados como sendo parte do package main, pois estão no mesmo diretório.

##### "Compartilhamento" de recursos
---
No Go, todos os arquivos que estejam no mesmo diretório (e consequentemente no mesmo package) conseguem enxergar as variáveis e até funções que foram declaradas nos arquivos "vizinhos" de pacote.

Exemplo:

`main.go`
```go
package main

func main() {
	println(a)
}
```

`a.go`
```go
package main

const a = "Hello World!"
```

Ao executar o arquivo `main.go` junto com o `a.go`, ele vai executar o `println()` com o valor que foi declarado em uma variável do arquivo `a.go`.