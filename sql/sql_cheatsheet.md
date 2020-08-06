# SQL 

## 1. Comandos básicos de usuários:

- COMANDO PARA DESBLOUEAR USUARIO BLOOUEADO:
```
ALTER USER <nome_do_usuário> ACCOUNT UNLOCK;
```
- COMANDO PARA REDEFINIR SENHA DE UM USUÁRIO:  
```
ALTER USER <nome_do_usuário> IDENTIFIED BY <senha_do_usuario> ACCOUNT UNLOCK; 
```
- COMANDO PARA DESBLOQUEAR UM USUÁRIO:
```
ALTER USER <nome_do_usuário> ACCOUNT UNLOCK;
```
- COMANDO PARA ATRIBUIR UMA NOVA SENHA AO USUÁRIO:
```
ALTER USER <nome_do_usuário> IDENTIFIED BY <senha_do_usuario>;
``` 
- COMANDO PARA VERIFICAR A PRÓXIMA DATA DE EXPIRAÇÃO (EXPIRY_DATE):
```
SELECT USERNAME, ACCOUNT_STATUS, EXPIRY_DATE FROM DBA_USERS 
WHERE USERNAME='<nome_do_usuário>';
```
Se for de seu desejo que as contas de usuário nunca mais expirem, execute os comandos a seguir, também com usuário SYS, e atribuição SYSDBA:
	
- Alterando perfil para não expirar mais
```
ALTER PROFILE DEFAULT LIMIT PASSWORD_REUSE_TIME UNLIMITED;
ALTER PROFILE DEFAULT LIMIT PASSWORD_LIFE_TIME  UNLIMITED;
``` 
 
- Verifique se não há mais data de expiração (EXPIRY_DATE)
```
SELECT USERNAME, ACCOUNT_STATUS, EXPIRY_DATE FROM DBA_USERS
WHERE USERNAME='<nome_do_usuário>';
```

- EXIBINDO A LISTA DE USUÁRIOS DO BANCO E O STATUS ATUAL:
```
SELECT 
    USERNAME AS USUARIO,
    ACCOUNT_STATUS AS STATUS,
    CREATED AS DATA_DE_CRIACAO,
    DEFAULT_TABLESPACE AS TABLESPACE
FROM DBA_USERS
ORDER BY USERNAME
```

## Referências:
    1. http://devfacil.blogspot.com/2016/04/banco-oracle-desbloquear-usuarios-com.html
    2. http://jeff-dba.blogspot.com/2012/01/desbloqueio-de-usuario-oracle-e-mudanca.html

