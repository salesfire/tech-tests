# Event & Segment API

Welcome! 👋🏻 You’re about to embark on a technical assessment that reflects the real-world challenges our engineering team tackles every day. This tech test should take you **about 60 minutes** to complete.

In this exercise, you’ll work with **PHP 8.x** and **Laravel**, using **Eloquent** for your data layer and **PHPUnit** for automated tests. Good luck—and enjoy the process!

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

## 🛠️ What You’ll Build (~60 min)

1. **Core Functionality Only**  
   - **Profiles**: Register a user by email & name.  
   - **Events**: Record an event (name + JSON payload + timestamp) against a profile.  
   - **“Abandoned Cart” Segment**: Return all profiles who have at least one `cart.added` event and **no** `order.completed` event.  

2. **Minimal Endpoints**  
   1. `POST /api/profiles` → create profile  
   2. `POST /api/profiles/{id}/events` → ingest event  
   3. `GET  /api/segments/abandoned-cart` → list matching profiles  

3. **Database Schema**  
   - `profiles` table:  
     - `id` (PK)  
     - `email` (string, unique)  
     - `name` (string)  
     - `created_at` / `updated_at`  
   - `events` table:  
     - `id` (PK)  
     - `profile_id` (FK → profiles.id)  
     - `name` (string)  
     - `properties` (JSON)  
     - `created_at` / `updated_at`  

4. **Segment Logic**  
   Implement a single scope or static method, e.g. `Profile::abandonedCart()`, which returns all profiles matching the abandoned-cart criteria.

5. **Testing (PHPUnit)**  
   - **Model test**: Verify that `Profile::abandonedCart()` returns the correct set of profiles.  
   - **Controller tests**:  
     - Creating profiles returns HTTP 201 with the created JSON.  
     - Ingesting events returns HTTP 201.  
     - Querying `/api/segments/abandoned-cart` returns HTTP 200 with the expected profiles array.  

6. **Deliverables**  
   - **README.md** with prerequisites, install/migrate/test/run instructions  
   - Laravel application code:  
     - Migrations  
     - Models  
     - Controllers  
     - Routes  
     - FormRequests  
     - API Resources  
   - PHPUnit tests (4–6 assertions total)  
   - PSR-12–compliant, well-structured code  

---
