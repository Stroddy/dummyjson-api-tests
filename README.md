# DummyJSON API Tests - Auth Module

## Overview
API tests for the DummyJSON public API.  
Scope includes three Auth flows: Login, Me (current user), and Refresh Token.  
Tests are implemented in Postman and cover positive, negative, and (for Login) parametrized scenarios based on CSV datasets.

---

## Structure

```text
dummyjson-api-tests/
├─ 01-postman/
│  └─ DummyJSON_Auth.postman_collection.json
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


Word test scenario files are stored inside "Positive cases" and "Negative cases" folders for all modules.

CSV datasets are stored under:  
`03-auth/01-Login/Login CSV Data/`

---

## Postman Collection
`01-postman/DummyJSON_Auth.postman_collection.json`

Modules inside the collection:

- **Login** - positive tests, negative tests, and 3 parametrized requests (CSV in `01-Login/Login CSV Data`)  
- **Me** - positive and negative tests  
- **Refresh Token** - positive and negative tests  

---

## Running Tests (Postman)

### Standard execution  
1. Import collection  
2. Run any module folder (Login / Me / Refresh Token)

### Parametrized Login tests  
1. Open Collection Runner  
2. Select **Login**  
3. Load CSV from:  
   `03-auth/01-Login/Login CSV Data/`  
4. Run

---

## Notes

### Login
- covers valid/invalid credentials  
- boundaries and invalid types for `expiresInMins`  
- parametrized requests use CSV datasets  

### Me
- valid token  
- missing token  
- expired token  

### Refresh Token
- valid refresh  
- missing token  
- invalid/expired token  

---

## Future Scope
- Add simple positive/negative tests for other DummyJSON modules  
- Extend parametrized datasets where required  
- Optional: build a small Rest Assured example based on the same API 