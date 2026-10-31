# 🍋 Little Lemon Restaurant — Web Application

> **A modern, responsive full-stack web application for Little Lemon Mediterranean Restaurant in Chicago, Illinois. Built with Django 5, RESTful APIs, and an elevated Mediterranean design system.**

---

## 📖 Overview

**Little Lemon** is a family-owned Mediterranean restaurant based in Chicago, Illinois, focused on traditional Italian, Greek, and Turkish recipes served with a modern twist. 

This repository features the complete web application including a seasonal food menu, online table booking system, reservations dashboard, and REST API integrations, styled with a Mediterranean design system.

---

## ✨ Features & Highlights

### 🎨 Modern UI/UX Redesign
- **Brand Palette:** Authentic Mediterranean Olive Green (`#495E57`), Lemon Yellow (`#F4CE14`), Warm Peach (`#EE9972`), and off-white porcelain cards.
- **Typography:** Google Fonts pairing of **Markazi Text** (headings) and **Karla** (body & UI).
- **Responsive Layout:** Responsive design across mobile, tablet, laptop, and 4K desktop screens.
- **Micro-Interactions:** Smooth button transitions, card elevation on hover, and active navigation indicators.

### 🍽️ Interactive Features
- **Seasonal Menu:** Food cards with category filter pills (*All Dishes, Starters & Salads, Mains, Desserts*), high-resolution dish photography, price tags, and detailed descriptions.
- **Dish Detail Pages:** Breadcrumb navigation, culinary attributes, sommelier wine pairing notes, and direct reservation triggers.
- **Online Table Booking:** 
  - Dynamic date selector with real-time slot availability checking (`11:00 AM – 7:00 PM`).
  - Automatic disabling of already-reserved time slots for the chosen date.
  - Client-side validation with feedback alert banners upon reservation confirmation.
- **Reservations Dashboard:**
  - Visual ticket cards with guest avatar initials, confirmed status badges, and booking timestamps.
  - Real-time guest name and date search filter.
  - Interactive Google Maps integration for the Chicago Hyde Park dining location.
  - Collapsible raw JSON API developer inspector.

### ⚙️ Backend & Architecture
- **Framework:** Django 5.x (Python 3.11+).
- **Dual Database Support:** Smart database connector that links with MySQL when available and gracefully defaults to SQLite for local development.
- **RESTful Endpoints:** Serialized JSON endpoints for booking retrieval and table slot reservation.

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- Python 3.10+ installed
- Git installed

### 2. Clone the Repository
```bash
git clone https://github.com/Mervin-droid/littlelemon_web_app.git
cd littlelemon_web_app
```

### 3. Create and Activate a Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 4. Install Dependencies
```bash
pip install -r requirements.txt
```

### 5. Apply Migrations
```bash
python manage.py migrate
```

### 6. Load Initial Sample Menu & Reservations Data
```bash
python manage.py loaddata LittleLemonAPI/fixtures/initial_data.json
```

### 7. Run the Development Server
```bash
python manage.py runserver
```

Open your browser and navigate to: **[http://127.0.0.1:8000/](http://127.0.0.1:8000/)**

---

## 🗺️ Application Routes

| Route | View Name | Description |
| :--- | :--- | :--- |
| `/` | `home` | Landing page featuring hero promotion, value pillars, specials cards, and chef quote |
| `/about/` | `about` | Founder story (Mario & Adrian), culinary heritage, kitchen photography, and restaurant statistics |
| `/menu/` | `menu` | Seasonal menu grid with interactive category filters and dish cards |
| `/menu_item/<id>/` | `menu_item` | Detailed view for individual menu items with sommelier pairings |
| `/book/` | `book` | Online table reservation form with real-time slot checking |
| `/reservations/` | `reservations` | Reservations dashboard with search, tickets, and location map |
| `/bookings/` | `bookings` | REST API: `GET` (filter by date) & `POST` (create new reservation) |

---

## 📡 REST API Usage

### 1. Get Bookings by Date
- **Endpoint:** `GET /bookings/?date=YYYY-MM-DD`
- **Response:**
```json
[
  {
    "model": "LittleLemonAPI.booking",
    "pk": 1,
    "fields": {
      "first_name": "Sophia Taylor",
      "reservation_date": "2026-11-01",
      "reservation_slot": 12
    }
  }
]
```

### 2. Create a New Reservation
- **Endpoint:** `POST /bookings/`
- **Payload:**
```json
{
  "first_name": "Alexander Ross",
  "reservation_date": "2026-11-02",
  "reservation_slot": 18
}
```
- **Response:**
  - `HTTP 200` with the updated JSON bookings list for that date.
  - If the slot is already taken: `{"error": 1}`.

---

## 📁 Project Structure

```
littlelemon_web_app/
├── LittleLemon/               # Django project configuration
│   ├── __init__.py            # PyMySQL integration hook
│   ├── asgi.py
│   ├── settings.py            # Settings with smart MySQL/SQLite fallback
│   ├── urls.py                # Root URL router
│   └── wsgi.py
├── LittleLemonAPI/            # Core Little Lemon application
│   ├── fixtures/
│   │   └── initial_data.json  # Pre-seeded menu items & bookings
│   ├── migrations/            # Django database migrations
│   ├── static/
│   │   ├── css/style.css      # Design system & stylesheet
│   │   └── img/               # Brand assets & dish photography
│   ├── templates/             # HTML templates
│   │   ├── partials/          # _header.html, _footer.html
│   │   ├── base.html          # Global base layout
│   │   ├── index.html         # Home page
│   │   ├── about.html         # About Us page
│   │   ├── menu.html          # Menu grid page
│   │   ├── menu_item.html     # Dish detail page
│   │   ├── book.html          # Table booking page
│   │   └── bookings.html      # Reservations dashboard
│   ├── admin.py
│   ├── forms.py
│   ├── models.py              # Booking and Menu models
│   ├── urls.py                # App URL routes
│   └── views.py               # View controllers & API handlers
├── .gitignore                 # Standard Python/Django ignore rules
├── manage.py                  # Django management script
├── Pipfile                    # Pipenv configuration
├── Pipfile.lock
├── README.md                  # Project documentation
└── requirements.txt           # Python package requirements
```

---

## 📄 License & Attribution

- Built as part of the **Meta Back-End Developer Professional Certificate Capstone**.
- Visual design, UX overhaul, responsive layouts, and enhancements crafted by the engineering team.
