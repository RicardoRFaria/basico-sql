# Básico de SQL

## Iniciando o postgres

```bash 
docker run --name basico-sql-postgres -p 5432:5432 -e POSTGRES_PASSWORD=minhasenha -d postgres
```

## Acessando o postgres

Você vai precisar se conectar com alguma ferramenta qualquer, dbeaver, datagrip, etc. No endereço:

```bash
Endereço: localhost
Porta: 5432
Usuário: postgres
Senha: minhasenha
```

## Criando o banco de dados

```sql
CREATE TABLE empresa(
    id           SERIAL PRIMARY KEY,
    nome         VARCHAR(255) NOT NULL,
    setor        VARCHAR(255) NOT NULL,
    ano_fundacao INT          NOT NULL
);

CREATE TABLE funcionarios(
    id         SERIAL PRIMARY KEY,
    nome       VARCHAR(255)   NOT NULL,
    salario    DECIMAL(10, 2) NOT NULL,
    idade      INT            NOT NULL,
    empresa_id INT,
    FOREIGN KEY (empresa_id) REFERENCES empresa (id)
);
```

## Dados do nosso exemplo

```sql
INSERT INTO empresa (id, nome, setor, ano_fundacao)
VALUES (1, 'Padaria do seu João', 'Alimentação', 2000),
       (2, 'Metalúrgica da Mariana', 'Indústria', 2001),
       (3, 'Sorveteria do Pedro', 'alimentação', 2002),
       (4, 'Papelaria da Flávia', 'Vendas', 2003),
       (5, 'Chocolate do Paulo', 'Alimentação', 2003);

INSERT INTO funcionarios (nome, salario, idade, empresa_id)
VALUES ('João Silva', 1000.00, 30, 1),
       ('Maria Santos', 2000.00, 31, 1),
       ('Pedro Oliveira', 3000.00, 32, 2),
       ('Ana Pereira', 4000.00, 33, 2),
       ('Carlos Souza', 5000.00, 34, 3),
       ('Julia Costa', 6000.00, 35, 3),
       ('Roberto Almeida', 7000.00, 36, 4),
       ('Fernanda Lima', 8000.00, 37, 4),
       ('Ricardo Faria', 9000.00, 38, 5),
       ('Patricia Rocha', 10000.00, 39, 5),
       ('Mario desempregado', 0, 18, null),
       ('Paula dempresada', 0, 19, null);
```

## Exercícios

### 1. Selecione todos os funcionários

Espere 12 resultados

### 2. Selecione todos os funcionários com salário maior que 5000

Espere 5 resultados

### 3. Selecione todos os funcionários com salário maior que 5000 e idade maior que 30

Espere 0 resultados

### 4. Selecione todos os dados de empresa

Espere 5 resultados

### 5. Selecione todos os dados de empresa com setor igual a Alimentação

Espere 2 resultados

### 6. Selecione todos os dados de empresa com setor igual a alimentação independente da case escrita

Espere 3 resultados

### 7. Selecione os dados de funcionário mas trazendo o nome da empresa

Empresa 10 resultados

### 8. Selecione os dados de funcionário mas trazendo o nome da empresa mas também trazendo quem não tem empresa
