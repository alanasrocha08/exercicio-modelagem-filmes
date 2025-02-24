# Exercício - modelagem física

## catálogos de filmes 

```sql
CREATE DATABASE catalogo_de_filmes CHARACTER SET utf8mb4;
```

### Criar tabela de gêneros

```sql
CREATE TABLE generos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL
);
```

### Visualizar detalhes estruturais da tabela
```sql
DESC generos;
```

### Criar tabela filme

```sql
CREATE TABLE filme(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL, 
    titulo TEXT(50) NOT NULL,
    data_de_lancamento DATE NOT NULL,
    generos_id INT NOT NULL -- será chave estrangeira
);
```

### Criar tabela detalhes do filme

```sql
CREATE TABLE detalhes_do_filme(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    id_filme INT NOT NULL, 
    duracao_minutos INT NOT NULL,
    sinopse TEXT NOT NULL,
    bilheteria DECIMAL(15,2) NULL, 
    orcamento DECIMAL(15,2) NULL
);
```



### Criar relacionamento entre as tabelas e configurar a chave estrangeira

```sql
ALTER TABLE filmes
    ADD CONSTRAINT fk_generos_filme
    FOREIGN KEY (generos_id) REFERENCES generos(id);
```

ALTER TABLE detalhes_do_filme
    ADD CONSTRAINT fk_detalhes_filme
    FOREIGN KEY (id_filme) REFERENCES filme(id);