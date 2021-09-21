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
MATCH (c:Categoria{id:"Serviços"})
MATCH (b:Categoria)
WHERE (b)-[:Superior]->(c)
MATCH (a:Marcador) 
WHERE (a)-[:Pertence]->(b) OR (a)-[:Pertence]->(c)
RETURN a
```
