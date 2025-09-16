# 📦 MediBox API (Protótipo Acadêmico)

Esta é uma API simples em **PHP (core)** para gerenciamento e
rastreamento de insumos hospitalares.\
O objetivo é registrar autenticação de usuários e operações de
**retirada** ou **adição** de itens em caixas monitoradas.

Todos os arquivos da API estarão dentro do diretório `/api`.

------------------------------------------------------------------------

## 🔑 Autenticação

### `POST /api/auth.php`

Verifica se a senha existe.

#### Parâmetros (Body JSON)

``` json
{
  "senha": "123456"
}
```

#### Respostas

-   **200 OK**

``` json
{
  "success": true,
  "user_id": 1,
  "name": "João Silva"
}
```

-   **401 Unauthorized**

``` json
{
  "success": false,
  "message": "Usuário ou senha inválidos."
}
```

------------------------------------------------------------------------

## 📦 Retirada / Adição de Itens

### `POST /api/transaction.php`

Registra a retirada (`get`) ou adição (`put`) de itens em uma caixa.

#### Parâmetros (Body JSON)

``` json
{
  "user_id": 1,
  "box_id": 2,
  "qtn": 5,
  "type": "get"
}
```

-   **user_id** → ID do usuário que realizou a operação\
-   **box_id** → ID da caixa onde ocorreu a movimentação\
-   **qtn** → Quantidade de itens movimentados\
-   **type** → Tipo de operação (`get` = retirada, `put` = adição)

#### Respostas

-   **200 OK**

``` json
{
  "success": true,
  "message": "Operação registrada com sucesso."
}
```

-   **400 Bad Request**

``` json
{
  "success": false,
  "message": "Parâmetros inválidos."
}
```

------------------------------------------------------------------------

## 📂 Estrutura de Diretórios

    /api
     ├── auth.php          # Rota de autenticação
     ├── transaction.php   # Rota de retirada/adição de itens
     ├── db.php            # Conexão com o banco de dados

------------------------------------------------------------------------

📌 Observação: Esta API é apenas um protótipo acadêmico, feita para
rodar em **localhost** sem mecanismos avançados de segurança.
