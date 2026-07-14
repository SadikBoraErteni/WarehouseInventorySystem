# Warehouse Inventory System

A warehouse inventory and order management web app built with Flask. Covers products, warehouses,
suppliers, customer orders, a shopping cart, and role-based user accounts.

## Features

- **Product management** — add, update, delete, and list products
- **Warehouse management** — track stock across multiple warehouse locations
- **Supplier management** — store and manage supplier records
- **Order management** — create and track customer orders, including order line items
- **Cart** — add products to a cart before placing an order
- **Authentication** — user login/roles via Flask-Login
- **Seed data** — `populate_db.py` fills the database with realistic fake data (via Faker) for local testing

## Data model

Six SQLAlchemy models in `app/models.py`: `User`, `Supplier`, `WarehouseLocation`, `Product`, `Order`, `OrderItem`.

## Tech stack

| Layer | Technology |
|---|---|
| Framework | Flask, Flask-Login, Flask-WTF |
| ORM / Migrations | Flask-SQLAlchemy, Alembic (Flask-Migrate) |
| Database | Microsoft SQL Server (via `pyodbc`) |
| Templates | Jinja2 |

## Running locally

```bash
git clone https://github.com/SadikBoraErteni/WarehouseInventorySystem.git
cd WarehouseInventorySystem

python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

Set `DATABASE_URL` and `SECRET_KEY` in a `.env` file (read by `config.py`), then:

```bash
python populate_db.py   # optional: seed with fake data
python run.py
```

## Project structure

Flask blueprint per domain area:

- `app/admin/`, `app/auth/`, `app/cart/`, `app/main/`, `app/orders/`, `app/products/`, `app/suppliers/`, `app/warehouses/`
- `app/templates/` — Jinja2 templates
- `app/models.py`, `config.py`, `run.py`, `populate_db.py` at the project root/`app` level
