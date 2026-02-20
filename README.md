# 🍯 Honey Site – Full-Stack Hybrid E-commerce Application

## 📌 Project Overview

**Honey Site** is a full-stack organic honey e-commerce web application developed using **Django** with a **Hybrid Database Architecture**.

The system integrates:

- 🎨 Front-End (HTML, CSS, Bootstrap, Django Templates)  
- ⚙ Back-End (Django Framework – MVT Architecture)  
- 🗄 SQLite (Relational Database)  
- 📦 MongoDB (Document-Oriented Database)  

This project demonstrates not only a complete e-commerce workflow but also the integration of relational and document-based databases within a scalable architecture.

---

# 🎨 1️⃣ Front-End Architecture

## 🧰 Technologies Used

- HTML5 – Structure  
- CSS3 – Styling  
- Bootstrap 5 – Responsive design  
- Django Template Engine – Dynamic rendering  

---

## 📁 Template Structure

```
templates/
 ├── base.html
 ├── index.html
 ├── products.html
 │     └── product_detail.html
 ├── cart.html
 ├── checkout.html
 ├── login.html
 ├── register.html
 └── profile.html
```

### 🔹 Base Template Design

All pages extend `base.html`, ensuring:

- Unified layout  
- Consistent navigation bar  
- Reusable template blocks  
- Clean and modular structure  

The UI is fully responsive and optimized for desktop, tablet, and mobile devices.

---

## 🛒 Front-End Features

- Home page with featured products  
- Product listing page  
- Product detail page  
- Shopping cart interface  
- Checkout page  
- Login & registration pages  
- User profile management  

The front-end focuses on usability, visual clarity, and smooth navigation.

---

# ⚙ 2️⃣ Back-End Architecture (Django)

The backend is built using Django following the **MVT (Model-View-Template)** pattern.

## 📂 Backend Structure

```
backend/
│── core/                # SQLite Models (User, Address)
│   ├── models.py
│   ├── views.py
│   ├── serializers.py
│
│── honey_api/           # MongoDB Managers & Business Logic
│   ├── mongo_models.py
│   ├── utils.py
│
│── mongodb_connector.py
│── manage.py
```

---

# 🗄 3️⃣ Hybrid Database Architecture

The project combines two database systems for optimized performance and flexibility.

---

## 🟢 SQLite (Relational Database)

Used for structured relational data requiring integrity and constraints.

### Stored Entities:
- User (custom Django model with validation)  
- Address (multiple addresses per user, default selection supported)  

### Why SQLite?
- Strong relational integrity  
- Foreign key constraints  
- Suitable for authentication and identity data  

---

## 🔵 MongoDB (Document Database)

Used for flexible and nested data structures.

### Stored Collections:
- Category  
- Product  
- Review  
- Cart  
- Order  

### Why MongoDB?
- Schema flexibility  
- Efficient nested document storage  
- Scalable handling of cart and order data  

---

# 🔄 4️⃣ System Data Flow

1. User registers → stored in SQLite  
2. User browses products → retrieved from MongoDB  
3. User adds product to cart → stored in MongoDB  
4. User checks out →  
   - Address retrieved from SQLite  
   - Order stored in MongoDB  
5. User submits review → stored in MongoDB referencing SQLite user  

This architecture shows how relational and document databases cooperate within one system.

---

# 🛒 5️⃣ Core Functional Modules

## 👤 User & Authentication (SQLite)
- Registration  
- Login / Logout  
- Profile management  
- Multiple saved addresses  
- Default address auto-handling  

---

## 🛍 Product Catalog (MongoDB)
- Categories (hierarchical support)  
- Products (title, slug, description, price, images, timestamps)  
- Availability status  

---

## 🛒 Cart Management (MongoDB)
- Add/remove products  
- Quantity updates  
- Automatic total price calculation  

---

## 💳 Checkout & Orders (Hybrid)
- Order creation in MongoDB  
- Reference to relational user and address  
- Payment status tracking  
- Unique order number generation  

---

## ⭐ Review System (Hybrid)
- Product rating  
- User comments  
- Timestamp recording  
- Cross-database linking (User from SQLite → Product in MongoDB)  

---

# 🧠 6️⃣ Design Patterns Implemented

This project applies several software engineering design patterns:

### 1️⃣ Singleton Pattern  
Implemented in `mongodb_connector.py` to ensure only one MongoDB connection instance exists.

### 2️⃣ Observer Pattern  
Used through Django signals (e.g., automatic handling of default addresses).

### 3️⃣ Decorator Pattern  
Used in authentication and request handling:
- `@login_required`
- `@csrf_exempt`

### 4️⃣ Command Pattern  
Implemented via Django’s `manage.py` commands:
- migrate  
- runserver  
- createsuperuser  

### 5️⃣ Factory Method Pattern  
Used in managers and serializers for structured object creation.

### 6️⃣ Template Method Pattern  
Implemented in base classes and generic views where workflows are defined and extended.

---

# 🏗 Architecture Summary

The system follows:

- Clear Separation of Concerns  
- Hybrid database integration  
- Scalable document handling  
- Secure relational authentication  
- Modular front-end architecture  

---

# 🚀 Running the Project

```bash
python -m venv venv
venv\Scripts\activate   # Windows
pip install -r requirements.txt
python manage.py migrate
python seed_data.py
python manage.py runserver
```

Access the application at:

```
http://127.0.0.1:8000/
```

---

# 👨‍💻 Author

**Mehdi Rezanezhad**  
Bachelor’s Project – University of Bonab  
Instructor: Dr. Alipour  
2025  

---

## 📜 License

This project is open-source and available under the MIT License.
