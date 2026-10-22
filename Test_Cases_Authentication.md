# Test Cases - Authentication Module (Login & Registration)

This document contains manual test cases for user authentication, applying **Boundary Value Analysis (BVA)** and **Equivalence Partitioning (EP)** techniques.

---

## 🔑 Test Suite: Login Functionality

| Test Case ID | Test Scenario | Pre-conditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_AUTH_001** | Valid User Login | User registered | 1. Navigate to /login<br>2. Enter valid email<br>3. Enter valid password<br>4. Click Login | Email: `user@example.com`<br>Pass: `ValidPass123!` | User redirected to Dashboard; 200 OK | High |
| **TC_AUTH_002** | Invalid Password (EP) | User registered | 1. Navigate to /login<br>2. Enter valid email<br>3. Enter invalid password<br>4. Click Login | Email: `user@example.com`<br>Pass: `WrongPass!` | Error: "Invalid username or password" displayed | High |
| **TC_AUTH_003** | Empty Credentials Validation | On login page | 1. Leave email & password empty<br>2. Click Login | None | Validation errors: "Field required" | Medium |

---

## 🔒 Test Suite: Password Field Validation (BVA)
*Requirement: Password length must be between 8 and 20 characters.*

| Test Case ID | Technique | Input Length | Test Data | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_PASS_001** | BVA (Below Min) | 7 chars | `Pass12!` | Error: Password must be at least 8 characters | Pass |
| **TC_PASS_002** | BVA (Min Boundary) | 8 chars | `Pass123!` | Password accepted successfully | Pass |
| **TC_PASS_003** | BVA (Max Boundary) | 20 chars | `Pass123456789012345!` | Password accepted successfully | Pass |
| **TC_PASS_004** | BVA (Above Max) | 21 chars | `Pass1234567890123456!` | Error: Password cannot exceed 20 characters | Pass |
