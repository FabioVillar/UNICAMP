# Lab05 - Marcadores e Taxonomia em Cypher
Estrutura de pastas:

```
├── README.md  <- arquivo apresentando a tarefa
```

## Aluno
* 234135: Fábio Santos Villar
## Tarefa de Cypher sobre Marcadores e Taxonomia
## Tarefa 1
Escreva em Cypher uma consulta que retorne os marcadores da categoria Serviços, sem considerar as categorias subordinadas.
### Resolução

```
MATCH (c:Categoria{id:"Serviços"}) 
MATCH (a:Marcador) 
WHERE (a)-[:Pertence]->(c) 
RETURN a
```

## Tarefa 2
Escreva em Cypher uma consulta que retorne os marcadores da categoria Serviços, considerando as categorias subordinadas.
### Resolução

```
MATCH (a:Categoria{id:"Serviços"})
MATCH (b:Categoria)
WHERE (b)-[:Superior]->(a)
MATCH (b2:Categoria)
WHERE (b2)-[:Superior]->(a)
MATCH (c:Categoria)
WHERE (c)-[:Superior]-(b2)-[:Superior]->(a)
MATCH (m:Marcador)
WHERE (m)-[:Pertence]->(a) OR (m)-[:Pertence]->(b) OR (m)-[:Pertence]->(c)
RETURN m
```
