# Airbnb Clone - Backend Requirement Specifications

This document defines technical and functional requirements for core backend features.

---

## 1. User Authentication

### API Endpoints
- `POST /api/v1/auth/register`  
- `POST /api/v1/auth/login`  
- `GET /api/v1/auth/me` (protected)  
- `PUT /api/v1/auth/update` (protected)

### Input Validation
- Email: must be valid format
- Password: min 8 chars, 1 number, 1 special char
- Role: auto-assigned (guest/host)

### Output
- On login: returns `{ user, token }` (JWT)

### Security
- Passwords hashed with **bcrypt**
- JWT expiration: 24 hours
- Refresh tokens (optional)

### Status Codes
- `201 Created` – on registration
- `200 OK` – on login
- `400 Bad Request` – invalid input
- `401 Unauthorized` – invalid credentials
- `409 Conflict` – email already exists

---

## 2. Property Management

### API Endpoints
- `GET /api/v1/properties` (filter by location, price, dates)
- `GET /api/v1/properties/:id`
- `POST /api/v1/properties` (protected, host-only)
- `PUT /api/v1/properties/:id` (owner-only)
- `DELETE /api/v1/properties/:id` (owner-only)

### Request Body (Create/Update)
```json
{
  "name": "Cozy Apartment",
  "description": "Fully furnished...",
  "location": "Nairobi, Kenya",
  "pricepernight": 5000,
  "images": ["url1.jpg", "url2.jpg"]
}

# Validation
- **Host must own property** to edit/delete.
- **Required fields**: `name`, `description`, `location`, `price`.
- **Status Codes**:
  - `201 Created`
  - `403 Forbidden` – if not owner
  - `404 Not Found` – if property doesn't exist

# Booking System

## API Endpoints
- `POST /api/v1/bookings`
- `GET /api/v1/bookings/my` – guest’s bookings
- `GET /api/v1/bookings/host` – host’s bookings
- `DELETE /api/v1/bookings/:id` – cancel if pending

## Request Body (JSON)
```json
{
  "property_id": "uuid",
  "start_date": "2025-09-05",
  "end_date": "2025-09-10"
}
````

# Business Logic

* Check for **overlapping bookings** on the same property.
* Calculate `total_price = price_per_night × (end_date - start_date)`.
* Set **status**: pending → confirmed after payment.

## Validation

* `start_date < end_date`
* Dates must be in the **future**
* Property must exist and be **available**

## Status Codes

* `201 Created` – booking created
* `400 Bad Request` – invalid dates
* `409 Conflict` – dates not available

# Non-Functional Requirements

* **Performance**: API response < 500ms under normal load
* **Security**: All endpoints use HTTPS
* **Scalability**: Designed for PostgreSQL + Node.js + Redis (future)
* **Logging**: Log all errors and payment events
* **Rate Limiting**: 100 requests/hour per IP (unauthenticated)

```


