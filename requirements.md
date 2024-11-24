Backend Requirement Specifications
1. User Authentication
Description:
Handles user registration, login, and secure access control.

API Endpoints:
POST /api/auth/signup
Input: { "name": "string", "email": "string", "password": "string" }
Output: { "message": "User registered successfully", "userId": "string" }
POST /api/auth/login
Input: { "email": "string", "password": "string" }
Output: { "token": "string", "userId": "string" }
Validation Rules:
Name: Required, minimum 3 characters.
Email: Required, valid email format, unique.
Password: Required, minimum 8 characters, must include letters and numbers.
Performance Criteria:
API response time: ≤ 300ms.
Password hashing: Use bcrypt with a minimum of 10 salt rounds.
2. Property Management
Description:
Allows hosts to create, update, and delete property listings.

API Endpoints:
POST /api/properties
Input: { "title": "string", "description": "string", "price": "number", "location": "string", "amenities": ["string"], "availability": "boolean" }
Output: { "message": "Property created successfully", "propertyId": "string" }
PUT /api/properties/:id
Input: { "title": "string", "price": "number" } (fields to update)
Output: { "message": "Property updated successfully" }
DELETE /api/properties/:id
Output: { "message": "Property deleted successfully" }
Validation Rules:
Title: Required, minimum 5 characters.
Price: Required, must be a positive number.
Location: Required, minimum 3 characters.
Performance Criteria:
API response time: ≤ 400ms.
Image upload and storage must not exceed 5MB per file.
3. Booking System
Description:
Handles the creation, cancellation, and tracking of property bookings.

API Endpoints:
POST /api/bookings
Input: { "propertyId": "string", "startDate": "string", "endDate": "string" }
Output: { "message": "Booking created successfully", "bookingId": "string" }
DELETE /api/bookings/:id
Output: { "message": "Booking canceled successfully" }
Validation Rules:
StartDate and EndDate: Required, valid date format (YYYY-MM-DD), EndDate must be after StartDate.
Prevent overlapping bookings for the same property.
Performance Criteria:
API response time: ≤ 500ms.
Ensure atomic transactions for booking creation to prevent double bookings.
