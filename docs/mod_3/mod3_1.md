# Transação:

Transação é uma unidade lógica de trabalho, a mesma abrange um conjunto de operações de manipulação de dados que executam apenas uma única tarefa:
<br>

```Exemplo
Conecta ao Banco de dados
    Começa a tranzação
        Operações de consulta/atualização
        ...
    Finaliza a transação
    Começa a tranzação
        Operações de consulta/atualização
        ...
    Finaliza a transação
Desconecta
```
- As transações são orientadas a dois tipos de problema:
    - O que acontece se a energia acabar no meio de uma transação, ou se houver um problema no disco?
    - O que acontece quando duas transações executam simultaneamente manipulando o mesmo dado?

O bando de dados pode ser levado a um estado *inconsistente*...

<p align="center" style="font-size: 16px;">Tabela de tipos de falhas</p>

|    | Tipo de falha | Abrangência | Como evitar/recuperar |
| -- | ------------- | ----------- | --------------------- |
| Local | Local | Apenas a transação corrente | Registro de log/controle de concorrência |
| Global | De sisitema (doft cash) | Todas as transações em andamento | Registro de log |
| Global | De meio físico (hard cash) | Todas as transações em andamento | Backup |

- Propriedades das transações (ACID)
    - Atomicidade: Todas as operações de uma transação devem ser efetivadas, ou na ocorrência de uma falha, nada deve ser efetivado.
        - "Tudo ou nada" - Não se admite parte de uma operação.
        - Recuperação de falhas via log.
    - Consistência: Transações preservam a consistência da base.
        - Estado inicial consistente -> Estado final consistente.
        - Controle de concorrência via Locks.
    - Isolamento: A maneira como várias transações em paralelo interagem (o que pode ser lido e o que pode ser escrito por cada uma) deve ser bem definido.
        - Controle de concorrência via Locks.
    - Durabilidade: Uma vez consolidada (commited) a transação, suas alterações permanecem no banco até que outras transações aconteçam.
        - Recuperação de falhas via log.

## Controle de concorrência

<div style="text-align: center;">
    <p style="font-size: 16px;">Imagem X: Tipos de execução</p>
    <img src="../../assets/Controle_concorrencia.png" alt="imagem">
    <p style="font-size: 16px;">Fonte - Slides do professor Maurício</p>
</div>

- **Execução serial (sequencial):** Diversas transações executadas em sequência.
    - Deixa a base de dados em estado correto e consistente.
- **Execução intercalada:** Comandos de diversas transações são intercalados.
    - Pode levar a inconsistências.

### Execução serial X Execução intercalada
  
<p style="text-align: center; font-size: 16px;">Tabela X: Execução serial x Execução intercalada</p>

|    | Isolamento | Concorrência | Chance de inconsistências |
| -- | ---------- | ------------ | ------------------------- |
| Serial | Maior | Menor | Menor |
| Intercalada | Menor | Maior | Maior |

<p style="text-align: center; font-size: 16px;">Fonte - Autor</p>

- Execução serial:
    - Estado inicial correto e consistente -> estado final correto e consistente.
- Execução intercalada:
    - Toda execução serial é consistente.
    - Mas uma execução intercalada só é consistente se for igual ao resultado de uma execução em sequência (ordem conhecida).
        - Esta execução é dita **serializável**.

### Problemas de execução intercalada

Ocorrência de anomalias, como:

1. Leitura inválida (Dirty Read):
    - Transação T escreve um dado,
    - Transação T' lê o memso dado (mesmo antes do término de T),
    - Permite que outras transações possam ver os dados que ainda não foram consolidados (commited), isto é, mudanças que podem ser descartadas em seguida, por causa de uma instrução ROLLBACK por exemplo.
    - Exemplo de leitura inválida:

<div style="text-align: center;">
    <p style="font-size: 16px;">Imagem X: Tipos de execução</p>
    <img src="../../assets/Exemplo_leitura_invalida_1.png" alt="imagem">
    <img src="../../assets/Exemplo_leitura_invalida_2.png" alt="imagem">
    <img src="../../assets/Exemplo_leitura_invalida_3.png" alt="imagem">
    <img src="../../assets/Exemplo_leitura_invalida_4.png" alt="imagem">
    <img src="../../assets/Exemplo_leitura_invalida_5.png" alt="imagem">
    <img src="../../assets/Exemplo_leitura_invalida_6.png" alt="imagem">
    <p style="font-size: 16px;">Fonte - Slides do professor Maurício</p>
</div>
  



