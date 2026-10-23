# Lost Item Matching Platform

## Project Description
The **Lost Item Matching Platform** is a full-stack web application designed to help individuals report lost and found items and automatically identify potential matches using an in-memory, Java-based weighted matching algorithm.

---

## Problem Statement
Misplacing personal belongings or finding unclaimed items in public spaces often leads to confusion, manual search friction, and fraudulent claim attempts. Conventional bulletin boards lack automated verification, attribute scoring, and lifecycle tracking.

## Solution
Our platform automates lost-and-found reconciliation through:
1. **Weighted Matching Engine:** Evaluates candidate lost and found reports across 9 weighted attributes to produce a match percentage score (0-100%).
2. **Side-by-Side Comparison & Attribute Breakdown:** Displays detailed attribute match indicators (Category, Brand, Model, Color, Location, Date, Unique Marks).
3. **Verification Protocol:** Forces claimants to answer specific verification questions (unique marks, wallpaper, item contents) before claim approval.
4. **Double Confirmation Return Lifecycle:** Ensures items are only marked as `RETURNED` when both claimant and finder confirm physical handover.

---

## Key Features
- **User Authentication:** Registration, login, session management, and role-based permissions (USER, ADMIN).
- **Lost & Found Reporting:** Detailed attribute submission forms with categories, location, date, and unique marks.
- **Automated Matching Engine:** Pure Java scoring engine evaluating candidate items immediately upon report creation.
- **Match Explanation:** Side-by-side comparison tables explaining matched and mismatched attributes.
- **Claim System & Security:** Private verification answers to prevent fraudulent claims.
- **In-App Notifications:** Real-time notifications for strong matches (Score >= 70%), claim requests, approvals, and returns.
- **Admin Management Console:** User activation/deactivation, report moderation, category administration, and claim oversight.
- **Responsive Frontend:** Plain HTML5, CSS3, and Vanilla JavaScript UI (No external JS/CSS frameworks used).

---

## Technology Stack

### Frontend
- HTML5
- CSS3 (Custom Responsive CSS grid & cards, no Bootstrap/Tailwind)
- Vanilla JavaScript (ES6 `fetch` API, no jQuery/React/Angular/Vue/Node)

### Backend
- Java 21
- Spring Boot 3.2.5
- Spring MVC & REST API

### Persistence & Data Access
- JPA (Java Persistence API)
- Hibernate ORM
- Spring Data JPA
- PostgreSQL (Primary production DB) / H2 (Zero-config local fallback DB)

### Build & Testing
- Maven (`mvnw`)
- Postman (API Testing via Postman Collection)

---

## Application Architecture

```text
com.lostitemplatform
├── controller          # Spring REST Controllers
├── service             # Core Business Logic Services
├── repository          # Spring Data JPA Repositories
├── entity              # JPA Database Entities
├── dto                 # Data Transfer Objects & API Wrappers
├── exception           # Global Exception Handling & Advice
├── config              # Database & Seed Configuration
├── enums               # Business Enums (Roles, Statuses)
└── matching            # Weighted Matching Algorithm Engine
```

---

## PostgreSQL Database Setup

1. Create PostgreSQL database:
```sql
CREATE DATABASE lostitemdb;
```

2. Configure environment variables or `application.properties`:
```properties
DB_URL=jdbc:postgresql://localhost:5432/lostitemdb
DB_USERNAME=postgres
DB_PASSWORD=yourpassword
```

*(Note: If environment variables are omitted, the application automatically runs using H2 in-memory mode for zero-config testing).*

---

## How to Build & Run

### Prerequisites
- JDK 21
- Maven Wrapper (included)

### Build Application
```powershell
.\mvnw clean compile
```

### Launch Server
```powershell
.\mvnw spring-boot:run
```

Once launched, access the web application at:
`http://localhost:8080`

H2 Console (if using fallback mode):
`http://localhost:8080/h2-console`

---

## Sample Credentials

| Role | Email | Password |
| :--- | :--- | :--- |
| **Admin** | `admin@example.com` | `admin123` |
| **User 1** | `user1@example.com` | `user123` |
| **User 2** | `user2@example.com` | `user234` |

---

## Postman API Testing

Import the Postman collection located at:
`postman/Lost Item Matching Platform.postman_collection.json`

Collection includes pre-configured requests for:
- User Registration & Login
- Lost & Found Item Management
- Automatic Matching & Match Explanation
- Claim Submission & Verification Answers
- Claim Approval & Double Confirmation Return
- Admin User & Report Moderation

---

## Project Documentation
Detailed documentation is available in the `docs/` directory:
- [`docs/project-flow.md`](docs/project-flow.md) - Full application lifecycle diagram & rules
- [`docs/database-design.md`](docs/database-design.md) - Entity schemas & relationships
- [`docs/api-documentation.md`](docs/api-documentation.md) - Complete REST endpoint reference
- [`docs/matching-algorithm.md`](docs/matching-algorithm.md) - Matching engine scoring matrix & rules
- [`docs/postman-testing.md`](docs/postman-testing.md) - Postman testing walkthrough

---

## Future Enhancements
- Image file upload integration (Amazon S3 / local storage).
- Geolocation proximity radius search.
- Multi-language localization (i18n).
