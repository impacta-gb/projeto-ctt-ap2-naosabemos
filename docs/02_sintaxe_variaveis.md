# 2. Sintaxe Básica e Variáveis

A sintaxe de Go é limpa e direta, fortemente influenciada por C, mas com melhorias significativas em legibilidade.

## Declarando Variáveis

Em Go, temos duas formas principais de declarar variáveis: utilizando a palavra-chave `var` ou o operador de inferência curta (`:=`).

```go
package main

import "fmt"

func main() {
    // Declaração formal com tipo explícito
    var nome string = "Impacta"
    
    // Declaração curta (infere o tipo automaticamente)
    idade := 20
    
    fmt.Printf("Nome: %s, Idade: %d\n", nome, idade)
}

!!! warning "ATENÇÃO"
Na linguagem Go, toda variável declarada DEVE ser utilizada. Se você declarar uma variável e não usá-la no código, o compilador gerará um erro e impedirá a execução do programa!
