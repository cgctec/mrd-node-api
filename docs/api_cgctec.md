
FORMAT: 1A
HOST: http://api.cgctec.com.br/v1

# Documentação da API

Esta documentação descreve de maneira geral o funcionamento e os parâmetros da API que alimenta o site.

# API

## Sobre [/]

Aqui podemos descrever detalhes que são comuns a todos os serviços como formatos, headers, tipos de erros, etc

# Group Usuários

## UserLogin [/login]

### Fazer login [POST]

+ Request login

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (Login)

+ Response 201 (application/json)
    + Attributes (Loged)

## UserPassword [/password]

### Alterar a senha [POST]

+ Request alterar password

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (Password)

+ Response 201 (application/json)
    + Attributes (Id)

## UserForgotPassword [/forgotpassword]

### Resetar a senha [POST]

+ Request reset password

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (ResetPassword)

+ Response 201 (application/json)
    + Attributes (Id)


## User [/user]

### Criar um usuário [POST]

+ Request Criar um usuário

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (user)

+ Response 201 (application/json)
    + Attributes (Created)


### Listar usuarios [GET]

+ Request listar usuários

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (none)

+ Response 200 (application/json)
    + Attributes (array[user])

+ Response 404 (application/json)
    + Attributes (Error)

## UserId [/user/{id_user}]

    + Parameters
     + id_user: 1 (number, required) - ID do usuário


### Listar um Usuário [GET]

+ Request listar um usuário

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (Id)

+ Response 200 (application/json)
    + Attributes (Id)

+ Response 404 (application/json)
    + Attributes (Error)

### Excluir usuário [DELETE]
+ Request excluir usuário

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (Id)

+ Response 200 (application/json)
    + Attributes (Id)

+ Response 404 (application/json)
    + Attributes (Error)


### Alterar usuário [POST]
+ Request Alterar um usuário

    + Headers

            Accept: application/json
            Content-Type: application/json

    + Attributes (user)

+ Response 200 (application/json)
    + Attributes (Created)

+ Response 400 (application/json)
    + Attributes (Error)


# Data Structures

## user (object)
+ id: (number) - auto incremento - Código do usuário
+ name: (string) - Nome do usuário
+ email: (string) - Email do usuário
+ password: (string) - criptografada MD5 gerado pela API - Senha do usuário
+ password_token: (string) - gerenciado pela API - Usado para gerar a password
+ password_reset_token: (string) - gerenciado pela API - Controle de alteração da password
+ password_reset_token_expired: (string) - gerenciado pela API - Tempo de expiração do token
+ date_create: (string) - gerenciado pela API - Data da criação do usuário
+ date_update: (string) - gerenciado pela API - Data da última alteração do usuário
+ user_type_id: (number) - FK do Tipo de Usuário
+ user_status_id: (number) - FK do Status do Usuário

## Login (object)

+ email (string)
+ password (string)

## Loged (object)
+ token (string) - Token gerado

## Password (object)
+ email (string)
+ password (string)
+ newpassword (string)

## ResetPassword (object)
+ email (string)
+ password (string)
+ token (string)

## Created (object)
+ id (number) - Id gerado

## Id (object)
+ id (number) - Id a ser processado

## Error (object)
+ code: (number) - Status code
+ message (string) - Mensagem do status
+ description (string) - Descrição do status