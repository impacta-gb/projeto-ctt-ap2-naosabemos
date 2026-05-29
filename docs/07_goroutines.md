# 7. Concorrência I: Goroutines

A concorrência em Go é um dos pontos mais fortes da linguagem, implementada de forma extremamente leve diretamente pelo runtime.

## O que é uma Goroutine?
Uma `goroutine` é uma thread leve gerenciada pelo próprio compilador do Go. Para disparar uma execução concorrente, basta colocar a palavra-chave `go` antes da chamada de uma função.

```go
package main

import (
    "fmt"
    "time"
)

func exibirMensagem(texto string) {
    for i := 0; i < 3; i++ {
        fmt.Println(texto)
        time.Sleep(100 * time.Millisecond)
    }
}

func main() {
    // Executa concorrentemente em segundo plano
    go exibirMensagem("Executando de forma assíncrona!")
    
    // Executa na thread principal
    exibirMensagem("Executando na main!")
}
```

---
