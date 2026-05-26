# 3. Estruturas de Controle (If, For, Switch)

Go possui poucas palavras-chave para controle de fluxo, o que torna a leitura do código muito mais rápida.

## Condicional `if`
Em Go, não é necessário envolver a condição do `if` entre parênteses.

```go
if idade >= 18 {
    fmt.Println("Maior de idade")
} else {
    fmt.Println("Menor de idade")
}
```

## O Único Laço: `for`
Em Go, não existe laço `while` ou `do-while`. Tudo é resolvido usando o `for`.

```go
// For clássico
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

!!! info "CURIOSIDADE"
    Para criar um laço infinito em Go (o equivalente a um `while(true)`), basta usar a palavra-chave `for` sem nenhuma condição!

## Estrutura `switch`
O `switch` em Go é inteligente e não precisa da palavra-chave `break` ao final de cada caso.

```go
switch sistema {
case "darwin":
    fmt.Println("Mac OS")
case "linux":
    fmt.Println("Linux")
default:
    fmt.Println("Outro sistema")
}
```

---
