# 🏪 Kamel-Deep Mega Mart

> A full-stack E-Commerce Web Application built with **Django** & **PostgreSQL**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-4.2-092E20?style=for-the-badge&logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

---

## 📌 About the Project

**Kamel-Deep Mega Mart** is a fully functional e-commerce web application developed for a local retail store in Kotputli, Rajasthan. The platform allows customers to browse products, manage a shopping cart, place orders with home delivery scheduling, and pay via UPI or Cash on Delivery.

**Owner:** Rajeev Swami
**Location:** Pipli Stand, Antela, Kotputli
**Contact:** +91 7073574211
**UPI:** 7073574211rajeev@ibl

---

## ✨ Features

- 🔐 **User Authentication** — Register, Login, Logout, Profile Management
- 🛍️ **Product Catalog** — Browse by category, search products, detailed product pages
- 🛒 **Shopping Cart** — Add, update quantity, remove items with live badge counter
- 📅 **Delivery Scheduling** — Customer selects preferred delivery date & address
- 📦 **Order Management** — Full order history with status tracking (Pending → Delivered)
- 💳 **Payment Options** — UPI Payment + Cash on Delivery
- ⚙️ **Admin Dashboard** — Manage products, categories, orders, users via Django Admin
- 📱 **Responsive Design** — Works on mobile, tablet, and desktop

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python 3.10+, Django 4.2 |
| **Database** | PostgreSQL (SQLite for development) |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Styling** | Custom CSS with Inter + Poppins fonts |
| **Icons** | Font Awesome 6 |
| **Auth** | Django built-in authentication |
| **Media** | Pillow (image uploads) |
| **Deployment** | Gunicorn + WhiteNoise |

---

## 📁 Project Structure

```
ecommerce_project/
│
├── ecommerce/               # Core project settings & URLs
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── store/                   # Products & Cart app
│   ├── models.py            # Category, Product, Cart, CartItem
│   ├── views.py
│   ├── urls.py
│   ├── admin.py
│   ├── context_processors.py
│   └── templates/store/
│       ├── home.html
│       ├── product_list.html
│       ├── product_detail.html
│       └── cart.html
│
├── orders/                  # Checkout & Order management app
│   ├── models.py            # Order, OrderItem
│   ├── views.py
│   ├── forms.py             # CheckoutForm with delivery + payment
│   ├── urls.py
│   ├── admin.py
│   └── templates/orders/
│       ├── checkout.html
│       ├── order_list.html
│       └── order_detail.html
│
├── accounts/                # User auth app
│   ├── views.py
│   ├── forms.py
│   ├── urls.py
│   └── templates/accounts/
│       ├── register.html
│       └── profile.html
│
├── templates/               # Shared base templates
│   ├── base.html
│   └── registration/login.html
│
├── media/                   # Uploaded product images
├── static/                  # Static files (CSS, JS, images)
├── requirements.txt
└── manage.py
```

---

## 🚀 Local Setup

### Prerequisites
- Python 3.10 or higher
- pip
- Git

### Step 1 — Clone the repository
```bash
git clone https://github.com/your-username/kamel-deep-mega-mart.git
cd kamel-deep-mega-mart
```

### Step 2 — Create virtual environment
```bash
python3 -m venv venv

# macOS / Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### Step 3 — Install dependencies
```bash
pip install -r requirements.txt
```

### Step 4 — Run migrations
```bash
python manage.py makemigrations store
python manage.py makemigrations orders
python manage.py makemigrations accounts
python manage.py migrate
```

### Step 5 — Create admin superuser
```bash
python manage.py createsuperuser
```

### Step 6 — Start development server
```bash
python manage.py runserver
```

### Step 7 — Open in browser
| URL | Description |
|-----|-------------|
| http://127.0.0.1:8000 | Main website |
| http://127.0.0.1:8000/admin | Admin dashboard |

---

## 🐘 PostgreSQL Setup (Production)

1. Create database in PostgreSQL:
```sql
CREATE DATABASE ecommerce_db;
CREATE USER ecommerce_user WITH PASSWORD 'yourpassword';
GRANT ALL PRIVILEGES ON DATABASE ecommerce_db TO ecommerce_user;
```

2. Update `ecommerce/settings.py`:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'ecommerce_db',
        'USER': 'ecommerce_user',
        'PASSWORD': 'yourpassword',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

3. Run migrations again:
```bash
python manage.py migrate
```

---

## ⚙️ Admin Panel Usage

1. Go to `/admin` and login with superuser credentials
2. Add **Categories** first (e.g. Grocery, Electronics, Clothing)
3. Add **Products** under each category with price, stock, image
4. Manage **Orders** — update status from Pending → Confirmed → Shipped → Delivered
5. Toggle **Payment Done** once UPI payment is verified

---

## 🌐 Deployment

### Option 1 — Render.com (Recommended)

1. Push code to GitHub
2. Go to [render.com](https://render.com) → New Web Service
3. Connect GitHub repo
4. Set build command:
```
pip install -r requirements.txt && python manage.py migrate && python manage.py collectstatic --noinput
```
5. Set start command:
```
gunicorn ecommerce.wsgi:application
```
6. Add environment variables: `SECRET_KEY`, `DEBUG=False`, `DATABASE_URL`

### Option 2 — PythonAnywhere

1. Sign up at [pythonanywhere.com](https://pythonanywhere.com)
2. Open Bash console and clone the repo
3. Set up virtualenv and install requirements
4. Configure WSGI file to point to Django project
5. Set up static files under the Web tab

### Option 3 — Railway.app

```bash
npm install -g @railway/cli
railway login
railway init
railway up
```

---

## 📸 Screenshots

> Add screenshots of your website here after deployment.

| Page | Description |
|------|-------------|
| Home | Hero banner, product grid, store info |
| Products | Category filter, search, product cards |
| Cart | Item list, quantity update, order summary |
| Checkout | Delivery address, date picker, UPI/COD payment |
| Orders | Order history with status badges |
| Admin | Product & order management dashboard |

---

## 📝 Resume Line

> **Developed a full-stack E-Commerce Web Application** for Kamel-Deep Mega Mart using **Python (Django)** and **PostgreSQL**, featuring user authentication, product catalog with search & category filtering, shopping cart, delivery scheduling, UPI & COD payment integration, order management with real-time status tracking, and a complete Django Admin dashboard — deployed on cloud infrastructure.

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---

## 📄 License

This project is licensed under the MIT License.

---

## 👤 Developer Contact

Built for **Kamel-Deep Mega Mart**
Owner: **Rajeev Swami**
📞 +91 7073574211
📍 Pipli Stand, Antela, Kotputli, Rajasthan


---

⭐ **If you found this project helpful, please give it a star on GitHub!**
