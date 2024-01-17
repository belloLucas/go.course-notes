
Uma Struct é uma estrutura de dados da Golang. Ela remete a uma classe, onde nós podemos definir atributos e depois "instanciar" aquela classe e atribuir valores aos atributos definidos anteriormente.

Sua sintaxe é simples, para criarmos uma struct nós começamos criando um novo tipo que o nome vai ser o nome daquela struct, por exemplo, Cliente:
```go
type Client struct {
  Name   string
  Age    int
  Active bool
}
```

Na parte de "instanciar" é bem simples, criamos uma variável e atribuímos ela como se fosse uma instância de classe:

```go
func main() {
  lucas := Client{
    Name:   "Lucas",
    Age:    21,
    Active: true,
  }
  fmt.Printf("O nome do cliente é %s, a idade dele é %v. Está ativo? %v\n", lucas.Name, lucas.Age, lucas.Active)

}
```

Como visto, a atribuição de valores aos atributos da struct é bem simples. Nós podemos também alterar os valores definidos, bastanto dizer o nome da "instância" da struct seguido por um .NomeDoAtributo, exemplo: `lucas.Active = false`
