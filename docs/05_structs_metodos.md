# 5. Structs e Métodos

Go não é uma linguagem totalmente orientada a objetos (não possui herança clássica), mas utiliza `structs` e `métodos` para alcançar encapsulamento e organização de dados.

## Definindo uma Struct
Uma `struct` é uma coleção de campos digitados.

```go
type Aluno struct {
    Nome  string
    Idade int
    Nota  float64
}
```

## Definindo Métodos
Um método é uma função que possui um argumento "receptor" especial associado a uma struct.

```go
// O receptor (a Aluno) conecta a função diretamente à struct
func (a Aluno) ExibirPerfil() {
    fmt.Printf("Aluno: %s | Idade: %d\n", a.Nome, a.Idade)
}
```

---
