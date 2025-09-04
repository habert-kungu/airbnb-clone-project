---
# StayBnb: The Airbnb Clone

## 📌 Overview

StayBackend is a backend system designed to power an **Airbnb-like booking platform**. It provides core functionality for **user management, property listings, bookings, payments, and reviews**, with a strong emphasis on **scalability, security, and performance**.

This project  simulates a real-world production system by integrating modern tools, frameworks, and best practices.
---

## 🎯 Project Goals

1. **User Management** – Secure registration, authentication, and profile management.
2. **Property Management** – Add, update, retrieve, and manage property listings.
3. **Booking System** – Enable users to reserve properties and manage booking details.
4. **Payment Processing** – Handle secure payment transactions and records.
5. **Review System** – Allow users to leave ratings and reviews on properties.
6. **Data Optimization** – Use caching, indexing, and database optimizations for performance.

---

## 🛠️ Features

- **API Documentation**: OpenAPI for clarity and integration.
- **Authentication & Authorization**: Secure endpoints with JWT or OAuth.
- **CRUD APIs** for Users, Properties, Bookings, Payments, and Reviews.
- **GraphQL Support**: Flexible queries for clients.
- **Database Optimizations**: Indexing + caching for high performance.
- **CI/CD Pipelines**: Automated testing, builds, and deployment.

---

## ⚙️ Technology Stack

- **Django** – High-level Python web framework.
- **Django REST Framework (DRF)** – RESTful APIs for CRUD operations.
- **PostgreSQL** – Relational database for persistent storage.
- **GraphQL** – Flexible query layer.
- **Celery + Redis** – Asynchronous tasks and caching.
- **Docker** – Containerized development and deployment.
- **GitHub Actions** – CI/CD automation.

---

## 🗄️ Database Design

**Entities**:

- **Users**: `id, name, email, password, role`
- **Properties**: `id, owner_id, title, description, price, location`
- **Bookings**: `id, user_id, property_id, start_date, end_date, status`
- **Payments**: `id, booking_id, amount, status, timestamp`
- **Reviews**: `id, user_id, property_id, rating, comment`

**Relationships**:

- A user can own multiple properties.
- A property can have multiple bookings.
- A booking is linked to one payment.
- A property can have multiple reviews.

---

<details>
<summary>This is the Entity Relationship Diagram </summary>
<summary>Paste this in <[Eraser.io](https://app.eraser.io/)  </summary>

```
// pk == primary key
// uuid == unique id
// idx == indexed
users{
  userId uuid  pk idx
  firstName string not_null
  lastName string not_null
  email string unique not_null
  passwordHash string unique not_null
  phoneNumber string not_null
  role enum(guest, host , admin) not_null
}
property [icon: home,color: purple]{
  propertyId uuid  pk idx
  hostId
  name string not_null
  description text not_null
  location string not_null
  pricePerNight decimal not_null
  createdAt  timestamp  timestamp
  updatedAt timestamp timestamp

}

booking[icon: wallet, color: red] {
  bookingId uuid pk idx
  propertyId
  userId string fk
  startDate date not_null
  endDate date not_null
  totalPrice decimal not_null
  status  enum(pending, confirmed)
  createdAt timestamp timestamp
}
payment[icon: money, color: green]{
  paymentId uuid pk idx
  bookingId string fk
  amount decimal not_null
  paymentDate timestamp timestamp
  paymentMethod enum(stripe, card)
}
review [icon: star, color: yellow]{
  reviewId uuid pk idx
  propertyId string fk
  userId string fk
  rating integer not_null
  comment  text  not_null
  createdAt timestamp timestamp
}
message[icon: message-circle, color: orange]{
  messageId uuid pk idx
  senderId string fk
  receipientId string fk
  messageBody string fk
  sentAt timestamp timestamp
}
property.hostId  - users.userId
booking.propertyId - property.propertyId
booking.userId - users.userId
payment.bookingId - booking.bookingId
review.propertyId - property.propertyId
review.userId - users.userId
message.senderId - users.userId
message.receipientId - users.userId

```

## </details>

## 🔑 API Endpoints (REST)

### Users

- `GET /users/` – List all users
- `POST /users/` – Create user
- `GET /users/{id}/` – Get user
- `PUT /users/{id}/` – Update user
- `DELETE /users/{id}/` – Delete user

### Properties

- `GET /properties/` – List properties
- `POST /properties/` – Create property
- `GET /properties/{id}/` – Get property
- `PUT /properties/{id}/` – Update property
- `DELETE /properties/{id}/` – Delete property

### Bookings

- `GET /bookings/` – List bookings
- `POST /bookings/` – Create booking
- `GET /bookings/{id}/` – Get booking
- `PUT /bookings/{id}/` – Update booking
- `DELETE /bookings/{id}/` – Delete booking

### Payments

- `POST /payments/` – Process payment

### Reviews

- `GET /reviews/` – List reviews
- `POST /reviews/` – Create review
- `GET /reviews/{id}/` – Get review
- `PUT /reviews/{id}/` – Update review
- `DELETE /reviews/{id}/` – Delete review

---

## 🛡️ API Security

- **Authentication & Authorization** – JWT or OAuth2.
- **Rate Limiting** – Prevent API abuse.
- **Data Protection** – Secure storage of sensitive data (hashed passwords, encrypted payments).
- **Input Validation & Sanitization** – Protect against injection attacks.

---

## 🚀 CI/CD Pipeline

- **CI**: Automated testing of APIs, models, and integrations.
- **CD**: Dockerized deployment with GitHub Actions.
- **Monitoring**: Integration with logging/monitoring tools for stability.

---

## 👥 Team Roles

- **Backend Developer** – APIs, business logic, models.
- **Database Administrator (DBA)** – Schema design, indexing, optimizations.
- **DevOps Engineer** – CI/CD, deployment, scaling.
- **QA Engineer** – Testing and quality assurance.

---

## 📚 Additional Resources

- \[System Design for Hotel Booking Apps]
- \[Software Development Team Structures]

---

✅ **Status**: Ongoing Development (Backend Blueprint Phase)

---
