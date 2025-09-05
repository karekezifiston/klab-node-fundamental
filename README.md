🛒 E-commerce Cart Backend API

A TypeScript-powered RESTful API for handling products, carts, and orders in an e-commerce platform.

🚀 Key Features

Products – Create, read, update, and delete items.

Cart – Add, update, or remove products with quantity management.

Orders – Place and manage orders with validation.

Validation – Robust input checks using Zod.

Type Safety – Fully written in TypeScript.

Database – Persistent storage with MongoDB (Mongoose ODM).

🛠️ Tech Stack

Runtime: Node.js

Framework: Express.js

Language: TypeScript

Database: MongoDB + Mongoose

Validation: Zod

Dev Tools: Nodemon, ts-node

📋 Requirements

Node.js v16+

MongoDB v4.4+

npm or yarn

⚡ Installation

Clone the repo

git clone <repository-url>
cd backend


Install dependencies

npm install


Run MongoDB

# Ubuntu/Debian
sudo systemctl start mongod  

# macOS (Homebrew)
brew services start mongodb-community  

# Windows
net start MongoDB


Setup environment
Create a .env file in the root folder:

MONGODB_URI=mongodb://127.0.0.1:27017/cart-app
PORT=4000


Start the dev server

npm run dev


API runs on http://localhost:4000

📚 API Routes
Products (/products)
Method	Endpoint	Description	Validation
GET	/products	Fetch all products	–
GET	/products/:id	Fetch product by ID	ObjectId
POST	/products	Add new product	Name, desc, price, category
PUT	/products/:id	Update product	ObjectId + fields
DELETE	/products/:id	Remove product	ObjectId
Cart (/cart)
Method	Endpoint	Description	Validation
GET	/cart	View cart	–
POST	/cart	Add product to cart	ProductId + quantity
PUT	/cart/:productId	Update quantity	ProductId + quantity
DELETE	/cart/:productId	Remove product	ProductId
Orders (/orders)
Method	Endpoint	Description	Validation
GET	/orders	List all orders	–
GET	/orders/:id	Fetch order by ID	ObjectId
POST	/orders	Place order from cart	Non-empty cart
DELETE	/orders/:id	Cancel order	ObjectId
📝 Example Requests

Create Product

POST /products
Content-Type: application/json

{
  "name": "Laptop",
  "description": "High-performance laptop",
  "price": 999.99,
  "category": "Electronics",
  "imageUrl": "https://example.com/laptop.jpg"
}


Add Item to Cart

POST /cart
Content-Type: application/json

{
  "productId": "64f1a2b3c4d5e6f7g8h9i0j1",
  "quantity": 2
}


Place Order

POST /orders


Response:

{
  "success": true,
  "data": {
    "_id": "64f1a2b3c4d5e6f7g8h9i0j2",
    "items": [
      {
        "productId": "64f1a2b3c4d5e6f7g8h9i0j1",
        "quantity": 2,
        "price": 999.99,
        "subtotal": 1999.98
      }
    ],
    "totalPrice": 1999.98,
    "createdAt": "2023-09-01T10:00:00.000Z"
  },
  "message": "Order placed successfully"
}

⚠️ Error Response Example
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    {
      "field": "body.price",
      "message": "Price must be a positive number"
    }
  ]
}

🏗️ Project Layout
backend/
├── src/
│   ├── controllers/    # Business logic
│   ├── models/         # MongoDB schemas
│   ├── routes/         # Express routes
│   ├── validation/     # Zod schemas
│   ├── middleware/     # Custom middlewares
│   ├── interfaces/     # TypeScript interfaces
│   ├── db/             # DB connection
│   └── index.ts        # App entry
├── package.json
├── tsconfig.json
└── README.md

🔧 Useful Scripts
npm run dev     # Start dev server
npm run start   # Start with nodemon
npm run build   # Compile TypeScript
npm run watch   # Watch for changes

🚦 Validation Rules

Product: name (1–100 chars), desc (1–500), price > 0, category (1–50), optional image URL.

Cart: productId (valid ObjectId), quantity (1–100).

Order: valid ObjectId, cart must not be empty, product prices checked at order time.

🔒 Security

Input validation via Zod.

ObjectId checks for MongoDB queries.

Product existence and price verification before orders.

🚀 Deployment
npm run build
node dist/index.js


Set environment:

MONGODB_URI=mongodb://<production-db>
PORT=4000
NODE_ENV=production
