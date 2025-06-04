# Exchange API

A **Exchange API** é um serviço REST desenvolvido em **Python**, utilizando o framework **FastAPI**. Ela permite realizar conversões entre diferentes moedas de forma segura e eficiente.

Para obter as taxas de câmbio, a aplicação consulta uma API externa. A API utilizada pode ser encontrada em: [AwesomeAPI](https://github.com/awesomeapibrasil/economy-api){target="\_blank"}.

## Endpoint Disponível

!!! info "GET /exchange/{from\_currency}/{to\_currency}"

````
Retorna a cotação atual entre duas moedas.  
Exemplo de uso: `GET /exchange/USD/EUR`.

=== "Response"

    ```json
    {
        "sell": 0.82,
        "buy": 0.80,
        "date": "2021-09-01 14:23:42",
        "account_id": "0195ae95-5be7-7dd3-b35d-7a7d87c404fb"
    }
    ```

    ```bash
    Response code: 200 (OK)
    ```
````

## Repositório

O código-fonte da API está disponível em:
[store-exchange-service](https://github.com/iancdesponds/store-exchange-service){target="\_blank"}.

## Estrutura do Projeto

```
app.py
requirements.txt
Dockerfile
```

## Código-fonte

\=== "app.py"

```python
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-exchange-service/refs/heads/main/app.py"
```

\=== "requirements.txt"

```text
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-exchange-service/main/requirements.txt"
```

\=== "Dockerfile"

```dockerfile
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-exchange-service/refs/heads/main/Dockerfile"
```
