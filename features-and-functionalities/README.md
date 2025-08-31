# Airbnb Clone - Features and Functionalities

This document outlines the core features and functionalities that the Airbnb Clone backend must support.

## Core Features

### 1. **User Authentication & Management**
- User registration (guests and hosts)
- Login and logout
- Password hashing (using bcrypt)
- JWT-based session management
- Profile update (name, phone, etc.)
- Role-based access (guest, host, admin)

### 2. **Property Management**
- Hosts can create, read, update, and delete (CRUD) property listings
- Fields: name, description, location, price per night, images (URLs), availability
- Search and filter properties by location, price, dates

### 3. **Booking System**
- Guests can book available properties for specific dates
- Date validation (no overlapping bookings)
- Booking status: pending, confirmed, canceled
- View booking history

### 4. **Payment Processing**
- Integration with Stripe (or PayPal) for secure payments
- Record payment status (success, failed, refunded)
- Generate payment receipts
- Idempotency keys to prevent duplicate charges

### 5. **Review & Ratings**
- Guests can leave reviews and star ratings after stay
- Average rating calculated per property
- Prevent multiple reviews per booking

### 6. **Messaging System**
- In-app messaging between guests and hosts
- Real-time or polling-based (future: WebSockets)
- Message history and timestamps

### 7. **Search & Filtering**
- Full-text search on property names/descriptions
- Filter by: location, price range, dates, amenities
- Paginated results

### 8. **Admin Dashboard (Future-Proofing)**
- View all users, properties, bookings
- Suspend accounts, remove listings
- Monitor payments and disputes

---

