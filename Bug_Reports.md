# Sample Bug Reports - Jira Style Documentation

This document showcases standardized defect reporting for logged bugs during test execution, structured for clear collaboration with development teams.

---

## 🐛 Bug Report 01: Checkout Total Calculation Discrepancy

* **Bug ID:** `BUG-SHOP-010`
* **Severity:** High
* **Priority:** High
* **Environment:** Staging (Chrome v122.0, Windows 11)
* **Component:** E-commerce / Checkout Module

### 📌 Summary
Cart summary total price does not update correctly when applying a valid 10% discount coupon code.

### 📝 Steps to Reproduce
1. Navigate to the shopping cart page with items total equal to `$100.00`.
2. Enter valid promo code `SAVE10` in the coupon input field.
3. Click the **"Apply Coupon"** button.
4. Observe the **Total Price** field.

### 🎯 Expected Result
The system applies a 10% discount ($10.00), updating the Total Price to **$90.00**.

### ❌ Actual Result
The system displays "Coupon Applied Successfully", but the Total Price remains unchanged at **$100.00**.

### 📎 Attachments & Logs
* **Console Logs:** `HTTP 200 OK` received, payload missing updated `final_price` parameter.
* **Screenshot:** Attached in ticket Jira-010.

---

## 🐛 Bug Report 02: Password Reset Link Expiration Issue

* **Bug ID:** `BUG-AUTH-005`
* **Severity:** Medium
* **Priority:** Medium
* **Environment:** Production Test (Firefox v123.0)
* **Component:** User Management / Password Reset

### 📌 Summary
Password reset token remains valid after the stated 15-minute expiration window.

### 📝 Steps to Reproduce
1. Request a password reset email for `user@example.com`.
2. Wait 20 minutes (exceeding the 15-minute expiration limit).
3. Click the password reset link received in email.
4. Enter a new password and submit.

### 🎯 Expected Result
User is redirected to an error page stating: *"Reset link has expired. Please request a new one."*

### ❌ Actual Result
User is able to successfully update their password using the expired link.
