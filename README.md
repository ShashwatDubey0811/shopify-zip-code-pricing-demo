# shopify-zip-code-pricing-demo

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Dynamic ZIP-code based pricing demo for Shopify. Features a zero-setup static `index.html` file for instant frontend/UX previewing, plus a full decoupled Express API backend and Shopify liquid snippet structure.

---

## Architecture Overview

The production architecture is designed to cleanly separate the client interface from business and pricing logic:

* **Storefront Snippet (`/shopify-snippet`):** Injects a user-facing zip code lookup directly into the Shopify product details template.
* **Backend API (`/backend`):** An Express-based server application that evaluates custom pricing rules securely against backend tables, keeping custom margins or logic hidden safely away from client-side tampering.

---

## Instant Frontend Preview (index.html)

For rapid prototyping, user experience evaluation, or quick demos, use the self-contained **`index.html`** file located in the root directory. 

Unlike a production environment, **`index.html`** completely simulates the backend API calls entirely client-side. It features an intentional artificial network delay (450ms) so that the frontend loading states, validation parameters, and live user interactions feel exactly like a live server deployment without needing any local development dependencies.

### Mock Evaluation Rules

The simulated backend in **`index.html`** utilizes a target dataset to demonstrate matching states:

| Evaluated ZIP Code | Scenario Profile | Simulated Price Outcome |
| :--- | :--- | :--- |
| **`75028`** | Regional Rate Drop (Matched) | **$1,499.00** |
| **`10001`** | Logistics/High-Cost Area (Matched) | **$1,699.00** |
| **`90210`** | Logistics/High-Cost Area (Matched) | **$1,799.00** |
| *Any other valid 5-digit* | Standard Delivery Rate (Fallback) | **$1,599.00** |

---

## Quick Start Guide

### Method 1: Instant UX Demo (Zero Setup)

1. Locate the **`index.html`** file in the root of the project.
2. Open **`index.html`** directly in any modern web browser.
3. Test custom lookups or use the pre-configured quick buttons (e.g., *Try 75028*) to check application states immediately.

### Method 2: Launching the Decoupled Server Environment

To execute the runtime build using actual HTTP API requests:

1. **Start the Express API Server:**
```bash
   cd backend
   npm install
   npm run dev
