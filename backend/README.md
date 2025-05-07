# Event & Segment API

Welcome! 👋🏻 You’re about to embark on a technical assessment that reflects the real-world challenges our engineering team tackles every day. This tech test should take you **about 1–2 hours** to complete.

In this exercise, you’ll work with **PHP 8.x** and **Laravel**, using **Eloquent** for your data layer, **PHPUnit** for automated tests, and (optional) **Docker Compose** to containerize your service. Good luck—and enjoy the process!

## 🎯 Background & Context

At Salesfire, we deliver real-time, personalized experiences powered by event streams:

- **Profiles** track each user or visitor (by email or anonymous ID).  
- **Events** record every meaningful interaction (page view, cart add, purchase, etc.), along with metadata (product ID, source, timestamp).  
- **Segments** define dynamic audiences (“browsers of women’s shoes ≥ 3 times last week,” “abandoned cart but no purchase”) so our marketing tools can fire exactly the right pop-up or email.

This test mimics a slice of that system—you’ll design and build a minimal API that ingests events, models relationships, and computes simple segments on demand.

## 🎬 User Journey Example

1. **Signup**  
   - A new user registers with their email and name, creating a **Profile**.  
2. **Browsing**  
   - The user views a product, resulting in an **Event** named `product.viewed` with associated metadata.  
3. **Cart Abandonment**  
   - The user adds an item to their cart but does not complete checkout, generating a `cart.added` event.  
4. **Segmentation**  
   - You define an “Abandoned Cart” **Segment** that includes any profile with at least one `cart.added` event and no subsequent `order.completed` event.  
5. **Follow-Up**  
   - When your segment endpoint is queried, it returns the user’s profile, enabling the marketing service to send a reminder email.

---

## 🛠️ What You’ll Build

### 1. Database Schema

- A **profiles** table to store user identities.  
- An **events** table to capture named events plus arbitrary JSON properties and a timestamp.  
- A **segments** table to define a rule: event name + minimum count threshold.

### 2. JSON API Endpoints

Implement a RESTful JSON API that supports:

- Create a new profile  
- Record (ingest) an event for an existing profile  
- Retrieve a profile’s events, with optional filters by event name or date  
- Define a new segment rule  
- Retrieve all profiles matching a given segment’s criteria  

### 3. Segment Logic

Segment membership should return **only** those profiles that have generated the segment’s target event **at least** the configured minimum number of times.

### 4. Testing

Demonstrate reliability with PHPUnit:

- **Model tests**  
- **Controller tests**  

---

## 📦 Deliverables

- **README.md** with prerequisites, install/migrate/test/run instructions  
- Laravel application code: models, controllers, FormRequests, API Resources  
- Migrations and factory definitions  
- PHPUnit tests  
- PSR-12–compliant, well-structured code  

---

## 🌟 Bonus Points

- **Pagination & Filtering**: Cursor- or key-set pagination; multi-field filters (date range, event types).  
- **Authentication & Security**: Implement a simple API token guard or middleware; demonstrate best practices.  
- **Error Handling**: Standardize JSON error format and global exception handling.  
- **API Documentation**: Provide an OpenAPI/Swagger spec or Postman collection, with examples for success and error cases.  
- **Idempotency**: Handle duplicate event submissions safely (e.g. idempotency keys or unique constraints).  
- **Performance & Indexing**: Suggest indexing strategies or query optimizations for high-volume data.  
- **CI/CD Integration**: Outline or stub a basic GitHub Actions (or similar) workflow for linting, migrations, and test runs.  
- **Code Quality**: Include configuration for PHPStan/PSalm or PHP-CS-Fixer to enforce standards.  
- **Data Retention & GDPR**: Briefly describe a strategy for archival or soft-deletion and compliance with “right to be forgotten.”  
- **Diagrams & Visuals**: Add a simple ER diagram or sequence diagram to illustrate data flows.  

---

Good luck, and we look forward to reviewing your solution!  
