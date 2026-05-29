# 10. Testes Automatizados em Go

O suporte para testes automatizados é embutido na ferramenta padrão do Go, sem a necessidade de instalar frameworks de terceiros.

## Regras para Criar Testes
1. O arquivo de teste deve obrigatoriamente terminar com `_test.go` (ex: `calculadora_test.go`).
2. A função de teste deve começar com a palavra `Test` em maiúsculo e receber o ponteiro `(t *testing.T)`.

## Exemplo de Código de Teste

```go
package main

import "testing"

func TestSoma(t *testing.T) {
    resultadoEsperado := 5
    resultadoObtido := Soma(2, 3)

    if resultadoObtido != resultadoEsperado {
        t.Errorf("Erro no teste! Esperava %d, mas obtive %d", resultadoEsperado, resultadoObtido)
    }
}
```

### Como Executar os Testes
Para rodar a bateria de testes automatizados do seu projeto, basta executar no terminal:
```bash
go test -v
```
