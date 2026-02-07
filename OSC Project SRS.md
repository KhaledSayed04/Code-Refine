> **Digital Marketplace with Wallet System**
> Backend System (Go or NodeJS)

---

# Software Requirements Specification (SRS)

## Project Title

Digital Marketplace with Wallet System

## Version

1.0

## Authors
* Sara
* Shahd
* Khaled


---

# 1. Introduction

## 1.1 Purpose

This document specifies the functional and non-functional requirements of a backend system that provides a digital marketplace where users can buy and sell products using an internal wallet system.

## 1.2 Scope

The system provides REST APIs for:

* User authentication and authorization
* Product management
* Order processing
* Wallet and transaction management
* Payment abstraction
* Notifications and audit logging

The system does **not** include frontend implementation. (May be added later)

## 1.3 Definitions

| Term        | Description                       |
| ----------- | --------------------------------- |
| API         | Application Programming Interface |
| JWT         | JSON Web Token                    |
| CRUD        | Create, Read, Update, Delete      |
| Wallet      | Internal user balance             |
| Transaction | Wallet balance change             |

---

# 2. Overall Description

## 2.1 Product Perspective

The system is a standalone backend service accessible through HTTP REST APIs.

## 2.2 User Classes

| User Type | Description           |
| --------- | --------------------- |
| Admin     | Full system access    |
| Seller    | Can list products     |
| Buyer     | Can purchase products |

## 2.3 Operating Environment

* Linux Server
* Go or NodeJS runtime
* Relational Database (PostgreSQL / MySQL)

## 2.4 Constraints

* JWT-based authentication
* RESTful architecture
* ACID database transactions

---

# 3. Functional Requirements

---

## 3.1 Authentication & Users

**FR-1** User registration
**FR-2** User login
**FR-3** Role-based authorization

---

## 3.2 Products

**FR-4** Seller can create product
**FR-5** Seller can update product
**FR-6** User can view products

---

## 3.3 Orders

**FR-7** Buyer can create order
**FR-8** System validates product availability
**FR-9** Order status tracking (Pending, Paid, Shipped, Cancelled)

---

## 3.4 Wallet

**FR-10** Each user has wallet
**FR-11** User can add balance
**FR-12** Wallet balance deducted on purchase
**FR-13** Wallet balance refunded on cancellation

---

## 3.5 Transactions

**FR-14** Every wallet change is recorded
**FR-15** Transactions are immutable
**FR-16** Payment operations shall be idempotent (Repeating the same payment request shall not result in duplicate charges)

---

## 3.6 Notifications

**FR-17** User receives notification after order placement
**FR-18** User receives notification on refund

---

# 4. Non-Functional Requirements

## 4.1 Performance

* The system shall be designed for efficient API response times (Performance testing using load-testing tools is recommended as future work)

## 4.2 Security

* Password hashing
* JWT authentication
* Input validation

## 4.3 Reliability

* The system shall handle failures using proper error handling and logging

## 4.4 Scalability

* Horizontal scaling supported

## 4.5 Maintainability

* Modular architecture
* Critical business logic shall be covered by unit tests

---

# 5. External Interface Requirements

## 5.1 API Interface

* JSON over HTTP
* REST endpoints

## 5.2 Database Interface

* SQL-based relational DB

---

# 6. Data Model (High Level)

### User

* id
* email
* password_hash
* role

### Product

* id
* name
* price
* stock
* seller_id

### Order

* id
* buyer_id
* status

### Wallet

* user_id
* balance

### Transaction

* id
* wallet_id
* amount
* type (credit/debit)

---

# 7. Acceptance Criteria (Sample)

**FR-7:**
Given a buyer with sufficient balance,
When creating an order,
Then order is created and wallet balance decreases.

---

# 8. Assumptions

* All payments handled internally
* External payment gateway may be added later

---

# 9. Future Enhancements

* Coupons
* Multi-currency
* Escrow payments
* Webhooks

---
