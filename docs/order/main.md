# Order API

A **Order API** é uma API REST desenvolvida em **Java** com **Spring Boot**. Ela permite aos usuários autenticados criar, consultar e visualizar detalhes de pedidos.

## Endpoints Disponíveis

!!! info "POST /order"

````
Cria um novo pedido para o usuário atual.

=== "Request"

```json
{
    "items": [
        {
            "idProduct": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
            "quantity": 2
        },
        {
            "idProduct": "0195abfe-e416-7052-be3b-27cdaf12a984",
            "quantity": 1
        }
    ]
}
```

=== "Response"

```json
{
    "id": "0195ac33-73e5-7cb3-90ca-7b5e7e549569",
    "date": "2025-09-01T12:30:00",
    "items": [
        {
            "id": "01961b9a-bca2-78c4-9be1-7092b261f217",
            "product": {
                "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8"
            },
            "quantity": 2,
            "total": 20.24
        },
        {
            "id": "01961b9b-08fd-76a5-8508-cdb6cd5c27ab",
            "product": {
                "id": "0195abfe-e416-7052-be3b-27cdaf12a984"
            },
            "quantity": 10,
            "total": 6.2
        }
    ],
    "total": 26.44
}
```

```bash
Response code: 201 (created)
Response code: 400 (bad request), se o produto não existir.
```
````

---

!!! info "GET /order"

````
Lista todos os pedidos do usuário atual.

=== "Response"

```json
[
    {
        "id": "0195ac33-73e5-7cb3-90ca-7b5e7e549569",
        "date": "2025-09-01T12:30:00",
        "total": 26.44
    },
    {
        "id": "0195ac33-cbbd-7a6e-a15b-b85402cf143f",
        "date": "2025-10-09T03:21:57",
        "total": 18.6
    }
]
```

```bash
Response code: 200 (ok)
```
````

---

!!! info "GET /order/{id}"

````
Retorna os detalhes de um pedido específico. O pedido **deve pertencer ao usuário atual**, caso contrário retorna `404`.

=== "Response"

```json
{
    "id": "0195ac33-73e5-7cb3-90ca-7b5e7e549569",
    "date": "2025-09-01T12:30:00",
    "items": [
        {
            "id": "01961b9a-bca2-78c4-9be1-7092b261f217",
            "product": {
                "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8"
            },
            "quantity": 2,
            "total": 20.24
        },
        {
            "id": "01961b9b-08fd-76a5-8508-cdb6cd5c27ab",
            "product": {
                "id": "0195abfe-e416-7052-be3b-27cdaf12a984"
            },
            "quantity": 10,
            "total": 6.2
        }
    ],
    "total": 26.44
}
```

```bash
Response code: 200 (ok)
Response code: 404 (not found), se o pedido não pertencer ao usuário.
```
````

---

## Repositórios

* [store-order (interface)](https://github.com/iancdesponds/store-order){target="\_blank"}
* [store-order-service (implementação)](https://github.com/iancdesponds/store-order-service){target="\_blank"}

---

## Estrutura do Projeto

### Interface da API

```bash
store-order/
├── src/main/java/store/order/
│   ├── OrderController.java
│   ├── OrderIn.java
│   ├── OrderItemIn.java
│   ├── OrderItemOut.java
│   └── OrderOut.java
├── Jenkinsfile
├── pom.xml
└── README.md
```

### Implementação da API

```bash
store-order-service/
├── k8s/
│   └── k8s.yaml
├── src/main/java/store/order/
│   ├── Order.java
│   ├── OrderApplication.java
│   ├── OrderItem.java
│   ├── OrderItemModel.java
│   ├── OrderItemRepository.java
│   ├── OrderModel.java
│   ├── OrderParser.java
│   ├── OrderRepository.java
│   ├── OrderResource.java
│   ├── OrderService.java
│   └── StoreExceptionHandler.java
├── Dockerfile
├── Jenkinsfile
├── pom.xml
└── README.md
```

---

## Código-fonte

### Interface da API

\=== "OrderController.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order/main/src/main/java/store/order/OrderController.java"
```

\=== "OrderIn.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order/main/src/main/java/store/order/OrderIn.java"
```

\=== "OrderItemIn.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order/main/src/main/java/store/order/OrderItemIn.java"
```

\=== "OrderItemOut.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order/main/src/main/java/store/order/OrderItemOut.java"
```

\=== "OrderOut.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order/main/src/main/java/store/order/OrderOut.java"
```

\=== "pom.xml"

```xml
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order/main/pom.xml"
```

---

### Implementação da API

\=== "OrderApplication.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderApplication.java"
```

\=== "Order.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/Order.java"
```

\=== "OrderItem.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderItem.java"
```

\=== "OrderItemModel.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderItemModel.java"
```

\=== "OrderItemRepository.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderItemRepository.java"
```

\=== "OrderModel.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderModel.java"
```

\=== "OrderParser.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderParser.java"
```

\=== "OrderRepository.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderRepository.java"
```

\=== "OrderResource.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderResource.java"
```

\=== "OrderService.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/OrderService.java"
```

\=== "StoreExceptionHandler.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/src/main/java/store/order/StoreExceptionHandler.java"
```

\=== "pom.xml"

```xml
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-order-service/main/pom.xml"
```
