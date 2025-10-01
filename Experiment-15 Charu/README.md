# Experiment-15 — Node.js + Express + MongoDB (Mongoose)

E-commerce catalog API with nested documents (variants) using Mongoose. Matches the requested schema and endpoints.

## Quickstart

```bash
cd Experiment-15
npm i
# Start Mongo locally in another terminal if needed: mongod
npm run seed     # inserts the three products (default: random ObjectIds)
npm run dev      # starts the API at http://localhost:3000
```

- To seed with fixed ObjectIds (identical every run):

```bash
# Option 1: via env var
SEED_MODE=B npm run seed
# Option 2: via argv
node src/seed/seed-fixed.js B
```

## Environment (.env)

If using MongoDB Atlas:

```
MONGO_URI=mongodb+srv://<username>:<password>@<cluster>/<db>?retryWrites=true&w=majority
```

When `.env` is present, the app will prefer `process.env.MONGO_URI`. Otherwise it falls back to `mongodb://127.0.0.1:27017/ecommerceDB`.

## Endpoints

- `POST /products` — create a product (send full JSON as body)
- `GET /products` — list all products
- `GET /products/category/:cat` — filter by category (case-sensitive)

## Product Schema

```json
{
  "name": { "type": "String", "required": true },
  "price": { "type": "Number", "required": true },
  "category": { "type": "String", "required": true },
  "variants": [{ "color": "String", "size": "String", "stock": "Number" }]
}
```

## Postman

Use `postman_collection.json` which includes:

- GET `http://localhost:3000/products`
- GET `http://localhost:3000/products/category/Apparel`
- GET `http://localhost:3000/products/category/Electronics`

## Screenshots

Add screenshots here for the three responses (placeholders):

- All products (3 docs)
- Category: Footwear (Running Shoes)
- Category: Electronics (Smartphone, variants: [])

## Notes

- Helpful logs are printed for server start and DB connection.
- Clear error messages for failed DB connection or invalid request bodies.
