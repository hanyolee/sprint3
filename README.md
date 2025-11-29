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

## curl TEST example

- 전체조회
curl localhost:3000/product

- 상세조회 (id 값으로)
curl localhost:3000/product/3

- 상세조회 (name, price 값으로)
* 둘 다 일치, 하나만 일치 해도 가져옴
curl localhost:3000/product/search?name=keyboard&price=3000
curl localhost:3000/product/search?name=keyboard
curl localhost:3000/product/search?price=3000

- 삭제 (id 값으로)
curl -X DELETE localhost:3000/products/3

- 수정 (
curl -X PATCH localhost:3000/products/4 \
  -H "Content-Type: application/json" \
  -d '{
    "name": "수정이름",
    "price": 990000,
    "description": "수정 메모",
    "tags": ["수정1", "수정2", "수정3"],
  }'


- 생성
curl -X POST localhost:3000/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "노트북",
    "price": 1290000,
    "description": "고성능 노트북",
    "tags": ["computer","laptop"]
  }'
