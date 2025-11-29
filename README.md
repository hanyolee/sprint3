# 📌 Express Request Data 종류 정리 (`req.query`, `req.params`, `req.body`)

| 종류 | 데이터 위치 | 예시 | 용도 |
|------|-------------|-------|--------|
| **`req.query`** | URL `?` 뒤(Query String) | `/products?name=pc` | 검색 · 필터 · 정렬 |
| **`req.params`** | URL 경로(동적 파라미터) | `/products/3` | 특정 리소스 조회/삭제 |
| **`req.body`** | 요청 본문(Body) | `{ "name": "pc", "price": 20000 }` | 데이터 생성/수정 (POST, PUT, PATCH) |

## 🧠 완전히 이해되는 예시

- **검색(필터)**
  - 요청: `GET /products?keyword=pc`
  - 사용: `req.query.keyword`

- **특정 상품 조회**
  - 요청: `GET /products/12`
  - 사용: `req.params.id = 12`

- **상품 등록**
  - 요청: `POST /products`
  - Body 예시:
    ```json
    { "name": "...", "price": 20000 }
    ```
  - 사용:
    - `req.body.name`
    - `req.body.price`

