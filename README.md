# Projeto-Neo4j
Criatividade

// CONSULTA 1: listar todas as pessoas
MATCH (p:Pessoa)
RETURN p.nome AS Nome, p.idade AS Idade
ORDER BY Nome;

// CONSULTA 2: descobrir as amizades
MATCH (p1:Pessoa)-[:AMIGO_DE]->(p2:Pessoa)
RETURN p1.nome AS Pessoa, p2.nome AS Amigo;

// CONSULTA 3: descobrir quem gosta de programacao
MATCH (p:Pessoa)-[:GOSTA_DE]->(i:Interesse {nome: 'Programacao'})
RETURN p.nome AS Pessoa, i.nome AS Interesse;

// CONSULTA 4: encontrar interesses em comum entre pessoas
MATCH (p1:Pessoa)-[:GOSTA_DE]->(i:Interesse)<-[:GOSTA_DE]-(p2:Pessoa)
WHERE p1.nome < p2.nome
RETURN p1.nome AS Pessoa1,
       p2.nome AS Pessoa2,
       collect(i.nome) AS InteressesEmComum;

// CONSULTA 5: encontrar amigos dos amigos da Ana
MATCH (ana:Pessoa {nome: 'Ana'})-[:AMIGO_DE*2]-(p:Pessoa)
WHERE p <> ana
RETURN DISTINCT p.nome AS PessoaEncontrada;

// CONSULTA 6: visualizar pessoas, amizades e interesses
MATCH (p:Pessoa)-[r]->(destino)
RETURN p, r, destino;

Provas que o código funciona:


// CONSULTA 1: listar todas as pessoas
MATCH (p:Pessoa)
RETURN p.nome AS Nome, p.idade AS Idade
ORDER BY Nome;

// CONSULTA 2: descobrir as amizades
MATCH (p1:Pessoa)-[:AMIGO_DE]->(p2:Pessoa)
RETURN p1.nome AS Pessoa, p2.nome AS Amigo;

// CONSULTA 3: descobrir quem gosta de programacao
MATCH (p:Pessoa)-[:GOSTA_DE]->(i:Interesse {nome: 'Programacao'})
RETURN p.nome AS Pessoa, i.nome AS Interesse;

// CONSULTA 4: encontrar interesses em comum entre pessoas
MATCH (p1:Pessoa)-[:GOSTA_DE]->(i:Interesse)<-[:GOSTA_DE]-(p2:Pessoa)
WHERE p1.nome < p2.nome
RETURN p1.nome AS Pessoa1,
       p2.nome AS Pessoa2,
       collect(i.nome) AS InteressesEmComum;

// CONSULTA 5: encontrar amigos dos amigos da Ana
MATCH (ana:Pessoa {nome: 'Ana'})-[:AMIGO_DE*2]-(p:Pessoa)
WHERE p <> ana
RETURN DISTINCT p.nome AS PessoaEncontrada;

// CONSULTA 6: visualizar pessoas, amizades e interesses
MATCH (p:Pessoa)-[r]->(destino)
RETURN p, r, destino;

Estrutura do repósito:

dio-desafio-neo4j/
├── README.md
├── cypher/
│   ├── 01_criar_grafo.cypher
│   └── 03_consultas.cypher
├── imagens/
│   └── modelo-grafo.png
└── evidencias/
    ├── amizades.png
    └── interesses-comuns.png
