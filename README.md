

This is an e-commerce platform designed for small business owners to easily manage online product listings, orders, and user interactions. It offers a feature-rich client and admin dashboard to streamline digital retail operations.

---

## ✨ Features

### 👥 Client

- 🔐 Authentication with Google Firebase
- 💳 Secure payments via Stripe
- 🧑‍🎨 Profile customization (username & profile image)
- 🔍 Product filtering by price, name, etc.
- 🛒 Cart management
- 📦 Order placement with real-time status tracking
- ✍️ Product reviews (create & update)
- 📬 Feedback submission
- 📱 Responsive design for all screen sizes

### 🧑‍💼 Admin Panel

#### Admin Roles & Privileges

| Role          | Admins                          | Products                            | Orders                                  |
|---------------|----------------------------------|-------------------------------------|-----------------------------------------|
|               | view | create | update | delete | view | create | update | delete | view | update | delete |
| **Admin**     | ✔    | ✔      | ✔      | ✔      | ✔    | ✔      | ✔      | ✔      | ✔    | ✔      | ✔      |
|**Prestataire**| ✔    | ✔      | ✔      | ✔      | ✔    | ✔      | ✔      | ✔      | ✔    | ✔      | ✔      |
| **Low**       | ✔    | ✔      | ✔      | ✔      | ✔    | ✔      | ✔      | ✔      | ✔    | ✔      | -      |

---

## 🗂️ Database Schemas

### 🛠️ Admin

| Field      | Type    | Required | Unique | Default |
|------------|---------|----------|--------|---------|
| name       | String  | ✅        | ❌      | -       |
| email      | String  | ✅        | ✅      | -       |
| password   | String  | ✅        | ❌      | -       |
| privilege  | String  | ❌        | ❌      | `"low"` |

---

### 📦 Product

| Field            | Type                          | Required | Default     |
|------------------|-------------------------------|----------|-------------|
| name             | String                        | ✅        | -           |
| description      | String                        | ✅        | -           |
| price            | Number                        | ✅        | -           |
| rating           | Number                        | ❌        | `0`         |
| images           | Object { public_id, url }     | ✅        | -           |
| colors           | Array\<String>                | ✅        | -           |
| sizes            | Array\<String>                | ✅        | -           |
| company          | String                        | ✅        | -           |
| stock            | Number                        | ✅        | -           |
| numberOfReviews  | Number                        | ❌        | `0`         |
| reviews          | Array { name, email, rating, comment } | ❌ | - |
| shipping         | Boolean                       | ❌        | `true`      |
| featured         | Boolean                       | ❌        | `false`     |
| admin            | Ref to Admin Schema           | ✅        | -           |
| createdAt        | Date                          | ❌        | `Date.now()`|

---

### 🧾 Order

| Field         | Type                               | Required | Default     |
|---------------|------------------------------------|----------|-------------|
| shippingInfo  | Object { address, city, state, country, pinCode, phoneNumber } | ✅ | - |
| orderItems    | Array { name, price, quantity, image, color, size, product (ref) } | ✅ | - |
| user          | Object { name, email }             | ✅        | -           |
| paymentInfo   | Object { id, status }              | ✅        | -           |
| paidAt        | Date                               | ✅        | -           |
| itemsPrice    | Number                             | ✅        | `0`         |
| shippingPrice | Number                             | ✅        | `0`         |
| totalPrice    | Number                             | ✅        | `0`         |
| orderStatus   | String                             | ✅        | `"processing"` |
| createdAt     | Date                               | ❌        | `Date.now()`|
| deliveredAt   | Date                               | ❌        | -           |

---

## 🌍 API Endpoints

### 🔸 Products

| Method | Route                            | Description                         |
|--------|----------------------------------|-------------------------------------|
| GET    | `/api/products/`                 | Get all products                    |
| POST   | `/api/products/` `?id`           | Get single product by ID           |
| POST   | `/api/admin/product/new`         | Create new product                  |
| PUT    | `/api/admin/product/` `?id`      | Update product by ID                |
| DELETE | `/api/admin/product/` `?id`      | Delete product by ID                |
| GET    | `/api/products/reviews/` `?id`   | Get product reviews by product ID   |
| POST   | `/api/products/reviews/`         | Create or update a product review   |
| DELETE | `/api/admin/product/review/` `?id` | Delete a product review by review ID |

---

### 📦 Orders

| Method | Route                        | Description                          |
|--------|------------------------------|--------------------------------------|
| GET    | `/api/admin/order/`          | Get all orders                       |
| POST   | `/api/orders/`               | Get orders by user email             |
| GET    | `/api/orders/` `?id`         | Get order by ID                      |
| POST   | `/api/orders/new/`           | Create a new order                   |
| PUT    | `/api/admin/order/` `?id`    | Update order status                  |
| DELETE | `/api/admin/order/` `?id`    | Delete an order                      |

---

### 🧑 Admin

| Method | Route                        | Description                          |
|--------|------------------------------|--------------------------------------|
| POST   | `/api/admin/register/`       | Register a new admin                 |
| POST   | `/api/admin/login/`          | Admin login                          |
| GET    | `/api/admin/users/`          | Get all admins                       |
| GET    | `/api/admin/users/` `?id`    | Get single admin by ID               |
| PUT    | `/api/admin/users/` `?id`    | Update admin privilege               |
| DELETE | `/api/admin/users/` `?id`    | Delete an admin                      |

---

## ⚙️ Tech Stack

### 🖥️ Client
- React.js
- React-icons
- Styled-Components
- Firebase (Authentication)
- Stripe (Payments)
- Formspree (Feedback Forms)

### 🧑‍💼 Admin Panel
- React.js
- Chakra UI
- React-icons

### 🖥️ Backend
- Node.js
- Express.js
- MongoDB (Mongoose)
- JWT (Authentication)
- Cloudinary (Image Hosting)
- Bcrypt.js (Password Hashing)
- Stripe (Payment Processing)

---

## 📌 Project Purpose

The Project provides a comprehensive and scalable e-commerce solution tailored for small businesses aiming to expand their reach through an online presence, while maintaining simplicity and security for both customers and administrators.

---

## 📧 Contact

For feedback, questions, or contributions, please reach out via [bencharradamohamedamine@gmail.com] or submit a pull request.

---

