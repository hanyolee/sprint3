# 📌 Express Request Data 종류 정리 (`req.query`, `req.params`, `req.body`)

| 종류 | 데이터 위치 | 예시 | 용도 |
|------|-------------|-------|--------|
| **`req.query`** | URL `?` 뒤(Query String) | `/api/products?name=pc` | 검색 · 필터 · 정렬 |
| **`req.params`** | URL 경로(동적 파라미터) | `/api/products/3` | 특정 리소스 조회/삭제 |
| **`req.body`** | 요청 본문(Body) | `{ "name": "pc", "price": 20000 }` | 데이터 생성/수정 (POST, PUT, PATCH) |

## 🧠 완전히 이해되는 예시

- **검색(필터)**
  - 요청: `GET /api/products?keyword=pc`
  - 사용: `req.query.keyword`

- **특정 상품 조회**
  - 요청: `GET /api/products/12`
  - 사용: `req.params.id = 12`

- **상품 등록**
  - 요청: `POST /api/products`
  - Body 예시:
    ```json
    { "name": "...", "price": 20000 }
    ```
  - 사용:
    - `req.body.name`
    - `req.body.price`

## curl TEST SAMPLE 

- **전체조회**
  - (정렬(create_at 기준) ?orderBy=desc(내림차순)  or ?dorderBy=asc(오름차순))
  ```bash
  curl localhost:3000/api/products
  curl localhost:3000/api/products?orderBy=desc
  curl localhost:3000/api/products?orderBy=asc
  ```

- **상세조회** (id 값으로)
  - (정렬(create_at 기준) ?orderBy=desc(내림차순)  or ?dorderBy=asc(오름차순))
  ```bash
  curl localhost:3000/api/products/4
  ```

- **상세조회** (name, price 값으로)
  - 둘 다 일치, 하나만 일치 해도 가져옴
  ```bash
  curl localhost:3000/api/products/search?name=keyboard&price=3000
  curl localhost:3000/api/products/search?name=keyboard
  curl localhost:3000/api/products/search?price=3000
  ```

- **삭제** (id 값으로)
  ```bash
  curl -X DELETE localhost:3000/api/products/3
  ```

- **수정** (
  ```bash
  curl -X PATCH localhost:3000/api/products/4 \
  -H "Content-Type: application/json" \
  -d '{
    "name": "수정이름",
    "price": 990000,
    "description": "수정 메모",
    "tags": ["수정1", "수정2", "수정3"]
  }'
  ```


- **생성**
  ```bash
  curl -X POST localhost:3000/api/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "노트북",
    "price": 1290000,
    "description": "고성능 노트북",
    "tags": ["computer","laptop"]
  }'
  ```


*** article ***

- **전체조회**
  - (정렬 default: desc, next: asc 로 설정돼 있음 직접 조작 불가)
  ```bash
  curl localhost:3000/api/articles
  ```

- **상세조회** (id 값으로)
  ```bash
  curl localhost:3000/api/articles/14
  ```

- **삭제** (id 값으로)
  ```bash
  curl -X DELETE localhost:3000/api/articles/14
  ```

- **수정** (
  ```bash
  curl -X PATCH localhost:3000/api/articles/14 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "수정이름",
    "content": "수정내용",
  }'
  ```


- **생성**
  ```bash
  curl -X POST localhost:3000/api/articles \
  -H "Content-Type: application/json" \
  -d '{
    "title": "새로생성 제목",
    "content": "새로생성 내용",
  }'
  ```
