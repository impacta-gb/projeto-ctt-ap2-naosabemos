# 8. Concorrência II: Channels

Canais (`channels`) são as tubulações que conectam as goroutines concorrentes, permitindo que elas compartilhem dados e se sincronizem de forma segura.

## Enviando e Recebendo Dados com Canais

```go
package main

import "fmt"

func enviarDados(canal chan string) {
    canal <- "Dados enviados da goroutine!" // Envia dados para o canal
}

func main() {
    // Criando um canal de strings
    meuCanal := make(chan string)

    // Disparando a goroutine
    go enviarDados(meuCanal)

    // Recebendo o dado do canal (bloqueia a execução até que o dado chegue)
    mensagem := <-meuCanal
    fmt.Println(mensagem)
}
```

!!! danger "ALERTA DE SEGURANÇA"

  Cuidado ao usar Goroutines sem controle de concorrência! Se a função `main` terminar sua execução antes que as Goroutines finalizem suas tarefas, o programa fechará abruptamente e os dados em segundo plano serão perdidos.


---
