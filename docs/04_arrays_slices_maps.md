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
