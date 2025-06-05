## Introdução

<p>O SQL é uma lingaugem declarativa não procedural desenvolvida e implementada pelo laboratório de pesquisa da IBM em San Jose nos anos 70, inicialmente chamada de SEQUEL (Structured English QUEry Language), criada como interface entre usuários e o primeiro SGBDR - SYSTEM R. Hoje é um padrão industrial que atinge grande parte do mercado de SGBDs, suas principais qualidades e atrativos são: Pequena qunatidade de comandos para realizar uma grande quantidade de operações, simplicidade, grande poder de consultas, e o seu padrão facilita migração.</p>

## Alguns tipos de dado no SQL:

- INTEGER | SMALLINT | NUMBER
- DECIMAL [precision, scale]
    - precision: Número total de dígitos
    - scale: Número de dígitos depois do ponto
- DOUBLE PRECISION | FLOAT | REAL
- CHAR(n)
    - Tamanho fixo 
    - n = Quantidade de caracteres
- VARCCHAR(n)
    - Tamanho variável
    - n = Número máximo de caracteres
- BLOB
    - Binary Large Object
- DATE | TIME | TIMESTAP

<p>Na linguagem SQL temos dois principais comandos, sçao eles:</p>

- **DDL - Data Definition Language:** Especificação do esquema da base de dados.
- **DML - Data Manipulation Language:** Inserção, remoção, alteração e consultas na instância da base de dados.

## DDL e DML

- **DDL: CREATE, DROP e ALTER**
    - TABLE, DATABASE, DOMAIN, EXCEPTION, GENERATOR, INDEX, PROCEDURE, ROLE, SHADOW, TRIGGER e VIEW.
- **DML: SELECT (FROM), DELETE (FROM), INSERT (INTO), UPDATE**

<p>Existem variações entre os fabricantes sobre o conjunto de funcionalidades e como essas funcionalidades operam</p>

## Comandos DDL: 

- **CREATE TABLE -** Criar uma tabela, deefinir colunas e restrições

```SQL
CREATE TABLE tabela(
    atrib1 tipo [<restrições da coluna 1>],
    atrib2 tipo [<restrições da coluna 2>],
    ....
    atribn tio [<restrições da coluna n>],
    
    <restrições da tabela>
);
```
