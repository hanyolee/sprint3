# 📌 Express Request Data 종류 정리 (`req.query`, `req.params`, `req.body`)

| 종류 | 데이터 위치 | 예시 | 용도 |
|------|-------------|-------|--------|
| **`req.query`** | URL `?` 뒤(Query String) | `/products?name=pc` | 검색 · 필터 · 정렬 |
| **`req.params`** | URL 경로(동적 파라미터) | `/products/3` | 특정 리소스 조회/삭제 |
| **`req.body`** | 요청 본문(Body) | `{ "name": "pc", "price": 20000 }` | 데이터 생성/수정 (POST, PUT, PATCH) |

