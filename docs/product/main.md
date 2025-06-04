# Product API

A **Product API** é um serviço REST desenvolvido em **Java**, utilizando o framework **Spring Boot**. Sua função é gerenciar produtos, permitindo criação, consulta e exclusão de registros.

## Endpoints Disponíveis

!!! info "POST /product"

````
Cria um novo produto.

=== "Request"
```json
{
    "name": "Tomato",
    "price": 10.12,
    "unit": "kg"
}
```

=== "Response"
```json
{
    "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
    "name": "Tomato",
    "price": 10.12,
    "unit": "kg"
}
```

```bash
Response code: 201 (created)
```
````

---

!!! info "GET /product"

````
Retorna todos os produtos cadastrados.

=== "Response"
```json
[
    {
        "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
        "name": "Tomato",
        "price": 10.12,
        "unit": "kg"
    },
    {
        "id": "0195abfe-e416-7052-be3b-27cdaf12a984",
        "name": "Cheese",
        "price": 0.62,
        "unit": "slice"
    }
]
```

```bash
Response code: 200 (ok)
```
````

---

!!! info "GET /product/{id}"

````
Retorna os dados de um produto específico por ID.

=== "Response"
```json
{
    "id": "0195abfb-7074-73a9-9d26-b4b9fbaab0a8",
    "name": "Tomato",
    "price": 10.12,
    "unit": "kg"
}
```

```bash
Response code: 200 (ok)
```
````

---

!!! info "DELETE /product/{id}"

````
Remove um produto com base no seu ID.

```bash
Response code: 204 (no content)
```
````

---

## Repositórios

* [store-product (interface)](https://github.com/iancdesponds/store-product){target="\_blank"}
* [store-product-service (implementação)](https://github.com/iancdesponds/store-product-service){target="\_blank"}

---

## Estrutura do Projeto

### Interface da API

```bash
store-product/
├── src/main/java/store/product/
│   ├── ProductController.java
│   ├── ProdutoIn.java
│   └── ProdutoOut.java
├── Jenkinsfile
├── pom.xml
└── README.md
```

### Implementação da API

```bash
store-product-service/
├── k8s/
│   └── k8s.yaml
├── src/main/java/store/product/
│   ├── Product.java
│   ├── ProductApplication.java
│   ├── ProductModel.java
│   ├── ProductParser.java
│   ├── ProductRepository.java
│   ├── ProductResource.java
│   ├── ProductService.java
│   └── StoreExceptionHandler.java
├── src/main/resources/
│   ├── application.yaml
│   └── db/migration/
│       ├── V2025.02.21.001__create_schema_account.sql
│       └── V2025.02.21.002__create_table_account.sql
├── Dockerfile
├── Jenkinsfile
├── pom.xml
└── README.md
```

---

## Código-fonte

### Interface da API

\=== "ProductController.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product/main/src/main/java/store/product/ProductController.java"
```

\=== "ProdutoIn.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product/main/src/main/java/store/product/ProdutoIn.java"
```

\=== "ProdutoOut.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product/main/src/main/java/store/product/ProdutoOut.java"
```

\=== "pom.xml"

```xml
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product/main/pom.xml"
```

---

### Implementação da API

\=== "Product.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/Product.java"
```

\=== "ProductApplication.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/ProductApplication.java"
```

\=== "ProductModel.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/ProductModel.java"
```

\=== "ProductParser.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/ProductParser.java"
```

\=== "ProductRepository.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/ProductRepository.java"
```

\=== "ProductResource.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/ProductResource.java"
```

\=== "ProductService.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/ProductService.java"
```

\=== "StoreExceptionHandler.java"

```java
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/src/main/java/store/product/StoreExceptionHandler.java"
```

\=== "pom.xml"

```xml
--8<-- "https://raw.githubusercontent.com/iancdesponds/store-product-service/main/pom.xml"
```
