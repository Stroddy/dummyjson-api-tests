# DummyJSON API Tests

API tests for the DummyJSON public API.  
Project is focused on practicing REST API testing with Postman and organizing tests in a clean, portfolio-ready structure.

Covered modules:

- **Auth** – login / current user / refresh token  
- **Products** – basic CRUD + negative cases  
- **Carts** – basic CRUD + negative cases  
- **Users** – update/delete + negative cases  

---

## Structure

```text
dummyjson-api-tests/
├─ 01-postman/
│  ├─ DummyJson-01 Auth.postman_collection.json
│  ├─ DummyJson-02 Products.postman_collection.json
│  ├─ DummyJson-03 Carts.postman_collection.json
│  └─ DummyJson-04 Users.postman_collection.json
├─ 02-data/
├─ 03-auth/
│  ├─ 01-Login/
│  │  ├─ Login CSV Data/
│  │  ├─ Positive cases/
│  │  └─ Negative cases/
│  ├─ 02-Get current User/
│  │  ├─ Positive cases/
│  │  └─ Negative cases/
│  └─ 03-Refresh Token/
│     ├─ Positive cases/
│     └─ Negative cases/
└─ README.md
```

Word test scenario files are stored inside **“Positive cases”** and **“Negative cases”** folders for Auth module.  
CSV datasets for parametrized Login tests are stored under:  
`03-auth/01-Login/Login CSV Data/`

---

## Postman Collections

All collections are stored in:

```text
01-postman/
    DummyJson-01 Auth.postman_collection.json
    DummyJson-02 Products.postman_collection.json
    DummyJson-03 Carts.postman_collection.json
    DummyJson-04 Users.postman_collection.json
```

Each collection is focused on one DummyJSON module and contains grouped folders for positive and negative scenarios.

---

## Module Details

### 1. Auth (`DummyJson-01 Auth`)

**Scope:**

- `POST /auth/login` – positive, negative, parametrized (CSV)  
- `GET /auth/me` – current user, positive/negative  
- `POST /auth/refresh` – refresh token, positive/negative  

**Checks:**

- Status codes  
- Token presence  
- Current user fields  
- Negative cases:
  - invalid credentials  
  - missing/invalid token  

---

### 2. Products (`DummyJson-02 Products`)

**Scope:**

- `GET /products`  
- `GET /products/{id}` – valid/invalid  
- `POST /products/add` – valid + invalid JSON  
- `PUT /products/{id}` – valid/invalid  
- `DELETE /products/{id}` – valid/invalid  

**Checks:**

- Status codes (200/201/404)  
- Basic product fields  
- Matching request/response on create/update  
- Negative: invalid id, invalid JSON  

---

### 3. Carts (`DummyJson-03 Carts`)

**Scope:**

- `GET /carts`  
- `GET /carts/{id}` – valid/invalid  
- `POST /carts/add` – positive, missing fields, invalid id, empty products  
- `PUT /carts/{id}` – valid update, empty array, invalid id  
- `DELETE /carts/{id}` – valid/invalid  

**Checks:**

- 200/201/400/404  
- `id` matches URL  
- `products` array type  
- Matching quantities  
- Delete: `isDeleted=true` and `deletedOn` exists  

---

### 4. Users (`DummyJson-04 Users`)

**Scope:**

- `POST /users/add` – simple positive create  
- `PUT /users/{id}` – valid/invalid id  
- `DELETE /users/{id}` – valid/invalid id  

**Checks:**

- Status codes  
- Updated fields match request  
- Error message contains correct id  
- Delete: `isDeleted=true` + timestamp  

---

## Running Tests in Postman

### 1. Import collections

```
Postman → Import → select collection from 01-postman/
```

### 2. Run tests

```
Right-click collection → Run collection
```

### 3. Parametrized Login tests

In **Collection Runner**:

- Collection: *Auth*  
- Folder: *Login*  
- Data: choose CSV from:  
  `03-auth/01-Login/Login CSV Data/`

---


## Notes

- This repository contains structured Postman test collections for the DummyJSON API.
- All tests are based strictly on the real behavior of the service (no imaginary or invented checks).
- Collections include clear positive and negative scenarios for each covered module.
- The Auth module also includes CSV-driven parametrized login tests.
- A Rest Assured automation project may be added later.