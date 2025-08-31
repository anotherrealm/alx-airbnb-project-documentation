# Use Case Diagram - Airbnb Clone

This diagram visualizes the interactions between actors (users) and the system.

## Actors
- **Guest**
- **Host**
- **Admin**
- **Payment Gateway** (external system)

## Key Use Cases

### Guest
- Register Account
- Login
- Search Properties
- View Property Details
- Book Property
- Make Payment
- Leave Review
- Send Message to Host

### Host
- Register Account
- Login
- List Property
- Update/Delete Property
- View Bookings
- Reply to Messages

### Admin
- View All Users
- View All Bookings
- Manage Listings
- Resolve Disputes

### System
- Send Booking Confirmation Email
- Validate Dates
- Process Payment (via Stripe)

> See `use-case-diagram.png` for the visual representation.