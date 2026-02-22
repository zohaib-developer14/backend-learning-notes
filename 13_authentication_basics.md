# Authentication, Authorization, Validation, Verification (Sequence Notes)

## Correct Execution Sequence in Backend

1. Validation
2. Verification (if required)
3. Authentication
4. Authorization

---

## 1. Validation

Validation checks whether the incoming data is structurally correct.

Examples:

* Is email in correct format?
* Is password at least 8 characters?
* Is required field missing?

Validation happens at the beginning of the request.
If validation fails → request is rejected immediately.

---

## 2. Verification

Verification confirms ownership of identity.

Examples:

* Email verification link
* OTP verification
* Phone number confirmation

Verification usually happens after registration.
It ensures the user actually owns the email or phone.

---

## 3. Authentication

Authentication checks who the user is.

Examples:

* Login using email and password
* JWT token verification

If credentials are correct → user is authenticated.
If not → 401 Unauthorized response.

---

## 4. Authorization

Authorization checks what the authenticated user is allowed to do.

Examples:

* Only admin can delete users
* User can edit only their own posts

If permission is missing → 403 Forbidden response.

---

## Simple Understanding

Validation → Is the data correct?
Verification → Is the identity confirmed?
Authentication → Who are you?
Authorization → What are you allowed to do?

---

## Complete Request Flow Example

Client Request
→ Validation Middleware
→ Authentication Middleware
→ Authorization Check
→ Controller Logic
→ Response

This is the standard secure backend request pipeline.
