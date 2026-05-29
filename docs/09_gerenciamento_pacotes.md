# 9. Gerenciamento de Pacotes (Go Modules)

O Go possui um gerenciador de dependências nativo chamado Go Modules, eliminando a necessidade antiga de configurar variáveis complexas no sistema operacional.

## Comandos Principais do Go Modules

| Comando | Descrição |
| :--- | :--- |
| `go mod init <nome>` | Inicializa um novo módulo de projeto e cria o arquivo `go.mod`. |
| `go get <pacote>` | Faz o download de uma dependência externa e a adiciona ao projeto. |
| `go mod tidy` | Remove dependências não utilizadas e adiciona as que estão faltando automaticamente. |

---
