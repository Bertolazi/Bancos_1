# Introdução a sistemas de bancos de dados

## Sistemas de informação

Para a alta evolução dos sistemas de bancos de dados tivemos antes um avanço dos próprios sistemas de informação, a partir desse ponto temos sistemas de informação baseados em gerenciamento de arquivos, onde:

- Cada unidade da organização possui seus programas e arquivos;
- Temos programas curtos para tarefas específicas;
- Dados armazenados em disco;
- Cada arquivo usa uma estrutura de dados.

<p style="text-align: center">Figura 1 - Esquemograma sistemas de informações</p>

<center>

![imagem aplicação](../assets/cap_1.png)

</center>

<p style="text-align: center">Fonte - Slides do professor Maurício</p>

<br>

<p style="text-align: center">Figura 2 - Redundância e inconsistência nos sistemas de informações</p>

<center>

![imagem redundância e inconsistência](../assets/cap_2.png)

</center>

<p style="text-align: center">Fonte - Slides do professor Maurício</p>

## Consistência de dados

- **Consistência** é o "estado ou caráter do que é coerente, do que tem solidez, veracidade, credibilidade, estabilidade, **realidade**";
- Se determinada que a informação é replicada (redundância), seu valor deve ser sempre o mesmo.

## Sistemas da informação (SIs) baseados em arquivos

Como tudo no mundo da tecnologia podemos ver claramente alguns problemas nesses tipos de sistemas, alguns deles são:

- Redundância e inconsistência de de dados;
- Dificuldade de acesso aos dados;
- Isolamento de dados;
- Anomalias no acesso concorrente;
- Segurança.

Nesses tipos de sistemas de informação temos os dados gravados em disco usando **estrutura de dados**, ou seja, o acesso demanda conhecimento dessas estruturas de dados, chamamos isso de dependência de dados.

## Dependência de dados

- Vários programas compartilhando os mesmos dados;
- Todos devem estudar e conhecer as mesmas estruturas;
- **Acoplamento forte**;
- Se houver uma alteração na estrutura de dados **todos os programas devem ser alterados**.

Mas como podemos fazer com que não tenhamos essa dependência de dados? A resposta é simples, criando um sistema que gerencie a estrutura. Veja com com as imagens abaixo, uma ilustração simplificada do funcionamento.

<p style="text-align: center">Figura 3 - Funcionamento do sistema gerenciador de dados</p>

<center>

![Sistema gerenciador de dados](../assets/cap_3.png)

</center>

<p style="text-align: center">Fonte - Slides do professor Maurício</p>

<br>

<p style="text-align: center">Figura 4 - SGBD (Sistema gerenciador de banco de dados)</p>

<center>

![SGBD](../assets/cap_4.png)

</center>

<p style="text-align: center">Fonte - Slides do professor Maurício</p>

## Sistema gerenciador de banco de dados (SGBD)

- Composto por:
    - Conjunto de dados
        - Base de dados;
        - Tabelas e índices;
        - Tuplas.
    - Conjunto de programas
        - Acesso dos dados;
        - Manipulação dos dados.
- É um sistema de propósito geral
    - Mantém um conjunto lógico e organizado de dados;
    - Armazena grande volume de dados;
    - Permite busca e atualização dos dados;
    - É eficiente;
    - É autônomo em relação às aplicações

<p style="text-align: center">Figura 5 - SGBD aplicado</p>

<center>

![SGBD_1](../assets/cap_5.png)

</center>

<p style="text-align: center">Fonte - Slides do professor Maurício</p>

- Requisitos fundamentais
  - Segurança
    - Física (mais comum no passado)
    - Lógica
        - Usernames e passwords;
        - Perfis de usuário.
    - Integridade
        - Consistência;
        - Validade. 
    - Recuperação e tolerância a falhas
        - Transações atômicas
        - Registros de log
        - Backup
    - Controle da concorrência
  
Temos dentro do mundo de bancos de dados restrições de integridade. Essas restrições definem o que é válido e o que não é válido para nós dentro desse contexto, alguns exemplos de restrições de integridade são:

- Um funcionário não pode pertencer a mais de um departamento;
- O preço de venda de um produto não pode ser superior ao seu custo;
- O código de cada produto deve ser único.

