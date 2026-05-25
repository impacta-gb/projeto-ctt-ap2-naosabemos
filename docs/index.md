# 1. Introdução e Instalação do Go

Go (ou Golang) é uma linguagem de programação de código aberto desenvolvida pelo Google, focada em simplicidade, eficiência e concorrência nativa.

## Como Instalar o Go

Para instalar o Go no seu ambiente Linux/Ubuntu (WSL), siga os comandos abaixo no terminal:

```bash
# Atualize a lista de pacotes
sudo apt update

# Instale o compilador do Go
sudo apt install golang-go
```

### Verificando a Instalação
Após o término, verifique se a instalação foi bem-sucedida:
```bash
go version
```

::: info NOTA
Recomenda-se utilizar o VS Code com a extensão oficial da linguagem Go para ter suporte a auto-complete e formatação automática no seu ambiente de desenvolvimento.
:::

---

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
```

::: warning ATENÇÃO
Na linguagem Go, **toda variável declarada DEVE ser utilizada**. Se você declarar uma variável e não usá-la no código, o compilador gerará um erro e impedirá a execução do programa!
:::

---

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

::: info CURIOSIDADE
Para criar um laço infinito em Go (o equivalente a um `while(true)`), basta usar a palavra-chave `for` sem nenhuma condição!
:::

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

# 4. Arrays, Slices e Maps

Essas são as estruturas de dados fundamentais em Go para armazenar coleções de elementos.

## Arrays
Possuem tamanho fixo que deve ser definido no momento da sua criação.

```go
var numeros [5]int
numeros[0] = 10
```

## Slices
São segmentos dinâmicos e muito mais comuns no dia a dia do que os arrays.

```go
// Criando um slice com valores iniciais
sabores := []string{"Calabresa", "Mussarela", "Frango"}

// Adicionando novos elementos dinamicamente
sabores = append(sabores, "Portuguesa")
```

## Maps
São coleções indexadas por chaves (estruturas do tipo Chave-Valor).

```go
// Criando um mapa de notas por nome do aluno
notas := make(map[string]float64)
notas["Gabriel"] = 9.5
notas["Refboni"] = 10.0
```

---

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

::: danger ALERTA DE SEGURANÇA
Cuidado ao usar Goroutines sem controle de concorrência! Se a função `main` terminar sua execução antes que as Goroutines finalizem suas tarefas, o programa fechará abruptamente e os dados em segundo plano serão perdidos.
:::

---

# 9. Gerenciamento de Pacotes (Go Modules)

O Go possui um gerenciador de dependências nativo chamado Go Modules, eliminando a necessidade antiga de configurar variáveis complexas no sistema operacional.

## Comandos Principais do Go Modules

| Comando | Descrição |
| :--- | :--- |
| `go mod init <nome>` | Inicializa um novo módulo de projeto e cria o arquivo `go.mod`. |
| `go get <pacote>` | Faz o download de uma dependência externa e a adiciona ao projeto. |
| `go mod tidy` | Remove dependências não utilizadas e adiciona as que estão faltando automaticamente. |

---

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