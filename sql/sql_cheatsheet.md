# SQL 

Alguns comandos e conceitos de SQL para auxiliar no dia a dia.

## 1. Conceitos básicos

### Tipos de dados:

    - Integer: números inteiros, positivos ou negativos 
    - Varchar: texto, até 255 caracteres
    - Blob: uma grande quantidade de dados textuais
    - Decimal: números decimais
    - Date: apenas data, sem hora
    - Datetime: data e hora 

### Tipos de chaves:

    - Chave Primária/Primary Key: é definida como uma chave ou uma coluna da tabela que identifica unicamente cada linha da tabela.
    - Chave Composta/Composite Key: é definida como um conjunto de chaves que, juntas, identificam unicamente cada registro.
    - Chave Estrangeira/Foreign Key: é definida como uma chave em alguma tabela que identifica unicamente linhas em outras tabelas. De forma simples, uma chave que rastreia uma chave primária em outra tabela.

### Funções SQL:

    - SUM
    - AVG
    - MAX
    - MIN
    - COUNT
    - DISTINCT

## 2. Criando/manipulando bases e tabelas:

### Criando uma base:
```
CREATE DATABASE <nome_da_base>;
```
```
USE DATABASE <nome_da_base>;
```

### Criando uma tabela:
```
CREATE TABLE <nome_da_tabela>
    {
        <nome_da_coluna> tipoDado(tam),
        <nome_da_coluna> tipoDado(tam),
        <nome_da_coluna> tipoDado(tam),
        <nome_da_coluna> tipoDado(tam),
        ...
    }; 
```

### Descrevendo uma tabela:
```
 DESC TableName;   -> Função para descrever a tabela (Coluna, Tipo, Null, Key, Default)
```
### Inserindo dados em uma tabela:
```
 INSERT INTO <nome_da_tabela> (<nome_da_coluna_1>, <nome_da_coluna_2>, <nome_da_coluna_3>)
    VALUES ('valor1', 'valor2', 'valor3');   
```

### Comandos básicos de alteração de usuário:

- Comando para desbloquear usuário:
```
ALTER USER <nome_do_usuário> ACCOUNT UNLOCK;
```
- Comando para bloquear usuário:
```
ALTER USER <nome_do_usuário> ACCOUNT LOCK;
```
- Comando para redefinir/atribuir uma senha ao usuário:
```
ALTER USER <nome_do_usuário> IDENTIFIED BY <senha_do_usuario>;
```
- Comando para redefinir a senha de um usuário e desbloqueá-lo:  
```
ALTER USER <nome_do_usuário> IDENTIFIED BY <senha_do_usuario> ACCOUNT UNLOCK; 
```
- Comando para verificar a próxima data de expiração (EXPIRY_DATE):
```
SELECT USERNAME, ACCOUNT_STATUS, EXPIRY_DATE FROM DBA_USERS 
WHERE USERNAME='<nome_do_usuário>';
```
Para que as contas de usuário nunca mais expirem, execute os comandos a seguir (com usuário SYS e atribuição SYSDBA):	
- Alterando perfil para não expirar mais
```
ALTER PROFILE DEFAULT LIMIT PASSWORD_REUSE_TIME UNLIMITED;
ALTER PROFILE DEFAULT LIMIT PASSWORD_LIFE_TIME  UNLIMITED;
``` 
- Exibindo a lista de usuários do banco e seu status atual:
```
SELECT 
    USERNAME AS USUARIO,
    ACCOUNT_STATUS AS STATUS,
    CREATED AS DATA_DE_CRIACAO,
    DEFAULT_TABLESPACE AS TABLESPACE
FROM DBA_USERS
ORDER BY USERNAME
```

### Referências:
    1. http://devfacil.blogspot.com/2016/04/banco-oracle-desbloquear-usuarios-com.html
    2. http://jeff-dba.blogspot.com/2012/01/desbloqueio-de-usuario-oracle-e-mudanca.html

