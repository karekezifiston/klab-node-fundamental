
# 🛒 E-commerce Cart Backend API

![Node.js](https://img.shields.io/badge/Node.js-16+-green?logo=node.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?logo=typescript)
![Express](https://img.shields.io/badge/Express.js-4.x-black?logo=express)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-green?logo=mongodb)
![License](https://img.shields.io/badge/License-ISC-lightgrey)

A **TypeScript-based REST API** for managing products, shopping carts, and orders in an e-commerce application.

---

## 🚀 Features

* **Product Management**: CRUD operations for products
* **Shopping Cart**: Add, update, and remove items with quantity control
* **Order Processing**: Place and manage orders from the cart
* **Validation**: Input validation with **Zod**
* **Type Safety**: Written in **TypeScript**
* **Database**: Persistent storage with **MongoDB + Mongoose**

---

## 🛠️ Tech Stack

* **Runtime**: Node.js
* **Framework**: Express.js
* **Language**: TypeScript
* **Database**: MongoDB (Mongoose ODM)
* **Validation**: Zod
* **Dev Tools**: Nodemon, ts-node

---

## 📋 Prerequisites

* Node.js (v16 or higher)
* MongoDB (v4.4 or higher)
* npm or yarn

---

## ⚙️ Installation

```bash
# Clone repository
git clone <repository-url>
cd backend

# Install dependencies
npm install

# Start MongoDB
sudo systemctl start mongod   # Linux
brew services start mongodb-community   # macOS
net start MongoDB   # Windows

# Environment setup
echo "MONGODB_URI=mongodb://127.0.0.1:27017/cart-app
PORT=4000" > .env

# Start development server
npm run dev
```

Server runs at **[http://localhost:4000](http://localhost:4000)**

---

## 📚 API Endpoints

### Products `/products`

| Method | Endpoint        | Description          |
| ------ | --------------- | -------------------- |
| GET    | `/products`     | Get all products     |
| GET    | `/products/:id` | Get product by ID    |
| POST   | `/products`     | Create new product   |
| PUT    | `/products/:id` | Update product by ID |
| DELETE | `/products/:id` | Delete product by ID |

### Cart `/cart`

| Method | Endpoint           | Description           |
| ------ | ------------------ | --------------------- |
| GET    | `/cart`            | Get cart contents     |
| POST   | `/cart`            | Add item to cart      |
| PUT    | `/cart/:productId` | Update item quantity  |
| DELETE | `/cart/:productId` | Remove item from cart |

### Orders `/orders`

| Method | Endpoint      | Description           |
| ------ | ------------- | --------------------- |
| GET    | `/orders`     | Get all orders        |
| GET    | `/orders/:id` | Get order by ID       |
| POST   | `/orders`     | Place order from cart |
| DELETE | `/orders/:id` | Cancel order by ID    |

---

## 📝 Example Requests

### Create Product

```http
POST /products
Content-Type: application/json

{
  "name": "Laptop",
  "description": "High-performance laptop",
  "price": 999.99,
  "category": "Electronics",
  "imageUrl": "https://example.com/laptop.jpg"
}
```

### Add to Cart

```http
POST /cart
Content-Type: application/json

{
  "productId": "64f1a2b3c4d5e6f7g8h9i0j1",
  "quantity": 2
}
```

### Place Order

```http
POST /orders
```

---

## ⚠️ Error Handling

```json
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
```

---

## 🏗️ Project Structure

```
backend/
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── validation/
│   ├── middleware/
│   ├── interfaces/
│   ├── db/
│   └── index.ts
├── package.json
├── tsconfig.json
└── README.md
```

---

## 🔧 Scripts

```bash
npm run dev     # Start dev server
npm start       # Start with nodemon
npm run build   # Build TypeScript
npm run watch   # Watch mode
```

---

## 🚦 Deployment

```bash
npm run build
NODE_ENV=production node dist/index.js
```

---

## 🤝 Contributing

1. Fork this repo
2. Create a new branch (`git checkout -b feature/new-feature`)
3. Commit changes (`git commit -m "Add feature"`)
4. Push branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📄 License

Licensed under the **ISC License**.

---

✅ Now your README is **GitHub-ready** with badges and a clean structure.

Do you want me to also **add a screenshot or API flow diagram** section (for visuals) before you publish it?
