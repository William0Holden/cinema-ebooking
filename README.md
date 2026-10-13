# Cinema E-Booking System

A full-stack cinema e-booking web app built as a team project for **CSCI 4050 (Software Engineering) at the University of Georgia, Fall 2024**.

Users can browse current and coming-soon movies, watch trailers, pick a showtime, choose seats and ticket ages, and check out with Stripe. Admins can manage movies and promotions.

## Features

- **Movie browsing** – movie list with search, trailer modal, and "coming soon" movies
- **Showtimes** – per-movie showing selection
- **Seat selection** – seat map per showing with ticket age selection
- **Checkout** – Stripe Checkout sessions, saved payment methods, payment confirmation emails
- **Accounts** – registration with email activation, login/logout, profile editing, password reset by email, booking history ("My Bookings")
- **Admin** – admin home, manage movies, manage promotions (backed by Stripe coupons / promotion codes, emailed to users)

## Stack

- **Frontend:** React 18 (Create React App), React Router, Axios, Reactstrap / Bootstrap, Stripe.js
- **Backend:** Django 5 + Django REST Framework, django-cors-headers, django-rest-passwordreset, Stripe Python SDK
- **Database:** SQL via the Django ORM (SQLite by default)

## Project layout

```
backend/          Django project (apps: user_api, movie)
frontend-cebs/    React frontend
```

## Running locally

### 1. Backend

```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install django django-cors-headers djangorestframework django-rest-passwordreset stripe six

# Configuration comes from environment variables (see .env.example)
export DJANGO_SECRET_KEY='any-long-random-string'
export EMAIL_HOST_USER='you@example.com'           # SMTP (Gmail) account used for emails
export EMAIL_HOST_PASSWORD='your-app-password'
export STRIPE_SECRET_KEY='sk_test_...'             # Stripe test-mode keys
export STRIPE_PUBLIC_KEY='pk_test_...'
export STRIPE_WEBHOOK_SECRET='whsec_...'

python manage.py migrate
python manage.py createsuperuser
python manage.py runserver                          # http://localhost:8000
```

### 2. Frontend

```bash
cd frontend-cebs
cp .env.example .env    # set REACT_APP_STRIPE_PUBLISHABLE_KEY
npm install
npm start               # http://localhost:3000
```

The frontend expects the API at `http://localhost:8000`.

## Team

- Morgan McGrath
- William Holden
- Garrett Baird
- Conner Evans
- Zach Fader

Contact: williamhold02@gmail.com
