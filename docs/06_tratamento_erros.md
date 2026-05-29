# 6. Tratamento de Erros (Error Handling)

Em Go, os erros não são tratados através de blocos `try-catch`. Em vez disso, os erros são tratados como valores de retorno comuns das funções.

## Padrão de Tratamento de Erro

```go
package main

import (
    "errors"
    "fmt"
)

func dividir(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("não é possível dividir por zero")
    }
    return a / b, nil
}

func main() {
    resultado, err := dividir(10, 0)
    if err != nil {
        fmt.Println("Erro encontrado:", err)
        return
    }
    fmt.Println("Resultado:", resultado)
}
```

---
