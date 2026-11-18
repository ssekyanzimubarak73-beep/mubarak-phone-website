# Mubarak Phone Accessories and Repair - Website (Next.js + MongoDB + REST API)

## 1. Install MongoDB
- Easiest: free cloud database at https://www.mongodb.com/atlas (copy the connection string)
- Or install locally: https://www.mongodb.com/try/download/community

## 2. Setup
```bash
npm install
cp .env.example .env.local    # then edit the values
npm run dev                   # http://localhost:3000
```

## 3. REST API
| Method | Endpoint | Access | Purpose |
|---|---|---|---|
| GET | /api/items | public | list items |
| POST | /api/items | key | add item |
| GET | /api/items/:id | public | one item |
| PUT | /api/items/:id | key | update item |
| DELETE | /api/items/:id | key | delete item |
| POST | /api/contact | public | save customer message |
| GET | /api/contact | key | read messages |

"key" = send header `x-api-key: <ADMIN_API_KEY from .env.local>`

### Examples
```bash
curl -X POST http://localhost:3000/api/items \
  -H "Content-Type: application/json" -H "x-api-key: YOUR_KEY" \
  -d '{"name":"Product 1","description":"Great quality","price":50000,"image":"https://..."}'

curl -X PUT http://localhost:3000/api/items/ID -H "Content-Type: application/json" \
  -H "x-api-key: YOUR_KEY" -d '{"price":45000}'

curl -X DELETE http://localhost:3000/api/items/ID -H "x-api-key: YOUR_KEY"
```

## 4. Deploy
Push to GitHub and deploy on Vercel; add the same environment variables there.

## Customize
Edit the top of `app/page.js` to change the WhatsApp number, email, and add your second call number (`CALL`).
