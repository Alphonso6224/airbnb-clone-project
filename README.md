# airbnb-clone-project

Welcome to the Airbnb clone project !

## Objective

This is a backend project whose aim is to manage user interactions, property listings, bookings and payments, while guaranteeing a smooth user experience.

## Project Goals
 1. **User Management:** Implement a secure system for user registration, authentication, and profile mangement.
 2. **Property Management:** Develop features for property listing creation, updated, and retrieval.
 3. **Booking System:** Create a booking mechanism for users to reserve properties and manage booking details.
 4. **Payment Processing:** Integrate a payment system to handle transactions and record payment details
 5. **Review System:** Allow users to leave reviews and ratings for properties.
 6. **Data Optimization:** Ensure efficient data retrieval and storage through database optimizations.

## Technology Stack
- **Django:** A high-level Python web framework used for building the RESTful API.
- **Django REST Framework:** Provides tools for creating and managing RESTful APIs.
- **PostgreSQL:** A powerful relational database used for data storage
- **GraphQL:** Allows for flexible and efficient querying of data.
- **Celery:** For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis:** Used for caching and session management.
- **Docker:** Conatainerization tool for consistent development and deployment environments.
- **CI/CD Pipelines:** Automated pipelines for testing and deploying code changes.

## Team Roles
- **Backend Developer:** Responsible for implementing the core of the app (API endpoints, database schemas, and business logic).
- **Database Administrator:** Manages database design, indexing, and optimizations.
- **DevOps Engineer:** Builds continuous integration and continuous delivery (CI/CD) pipelines for faster delivery.
- **QA Engineer:** Ensures the backend functionalities are thoroughly tested and meet quality standards.

## Technology Stack
- **Django:** Python web framework for building the RESTful API.
- **Django REST Framework:** Provides tools for creating and managing RESTful APIs.
- **PostgreSql:** A powerful relational database used for data storage.
- **GraphQL:** Allows for flexible and efficient querying  of data.
- **Celery:** For handling asynchronous tasks such as sending notifications of processing payments.
- **Redis:** Used for caching and session management.
- **Docker:** Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines:** Automated pipelines for testing and deploying code changes.

## Database Design

### Main Entities

The project is based on five main entites: **User**, **Property**, **Booking**, **Payment**, **Review**.

---

### 1. User

Represents the platform users.

**Key fields:**
- `id` : unique identifier for the user
- `firstname` : first name
-  `lastname` : last name
-  `email` : unique email address
-  `password` : hashed password
-  `created_at` : account creation date

---

### 2. Property

Represents the listings available for booking.

**Key fields:**
- `id`: unique property identifier
- `title`: listing title
- `description`: property details
- `start_date` / `end_date`: availability period
- `price_per_night`: nightly rate
- `location`: location of the property
- `user_id`: owner ID (reference to a `User`)

---

### 3. Booking

Represents user reservations.

**Key fields:**
- `id`: unique booking identifier
- `user_id`: user who made the booking
- `property_id`: booked property
- `start_date` / `end_date`: booking dates
- `status`: booking status (`confirmed`, `pending`, `cancelled`)
- `total_price`: total cost (`price_per_night * number of nights`)
- `created_at`: creation date

---

### 4. Payment

Handles transactions related to bookings.

**Key fields:**
- `id`: unique payment ID
- `booking_id`: related booking
- `montant`: amount paid
- `payment_status`: payment state (e.g., paid, pending)
- `payment_method`: card, bank transfer, etc.
- `created_at`: payment date

---

### 5. Review

Allows users to leave feedback about properties.

**Key fields:**
- `user_id`: reviewer
- `property_id`: property being reviewed
- `rating`: score (e.g., from 1 to 5)
- `comment`: written feedback
- `created_at`: date of submission

---

### Entity Relationships

- A **User** can have multiple **Bookings** (1:N).
- A **User** can post multiple **Reviews** (1:N).
- A **Property** can have multiple **Bookings** (1:N).
- A **Property** can receive multiple **Reviews** (1:N).
- Each **Booking** is associated with one **Payment** (1:1).
- A **Review** is unique for each **(User, Property)** pair.

## Feature Breakdown

### 1. User Management
Users can create an account, log in, and access their personal dashboard. This ensures secure authentication and allows linking of bookings, payments, reviews to individual users.

---

### 2. Property Management
Users can list their properties by providing a title, description, location, availability dates, and a price per night. This allows hosts to manage their listings and availability on the platform.

---

### 3. Booking System
Users can book a property for a specific date range, provided it is available. The system checks availability and calculates the total price based on the number of nights.

---

### 4. Payments
Each booking must be accompanied by a payment. This feature records the amount, payment status (e.g., paid, pending), and the payment method used, ensuring financial tracking.

---

### 5. Reviews and Ratings
After completing a stay, users can leave a review for a property. This feature promotes transparency and helps other users make informed booking decisions.
