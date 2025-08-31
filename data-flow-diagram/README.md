# Data Flow Diagram (DFD) - Airbnb Clone

This diagram illustrates how data moves through the system during key operations.

## Level 0 (Context Diagram) Overview

### External Entities
- **User (Guest/Host)**
- **Payment Gateway (e.g., Stripe)**
- **Email Service (e.g., SendGrid)**

### Main Process: **Airbnb Backend API**

### Data Flows
1. **User → API**: Register, Login, Search, Book, Pay, Review
2. **API → Payment Gateway**: Charge request with token
3. **Payment Gateway → API**: Success/failure response
4. **API → Email Service**: Send confirmation email
5. **API → Database**: Store user, property, booking, payment
6. **Database → API**: Return search results, booking history

> See `data-flow.png` for the visual DFD.