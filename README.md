# shopify-zip-code-pricing-demoDynamic ZIP-code based pricing demo for Shopify. Features a zero-setup static index.html file for instant frontend/UX previewing, plus a full decoupled Express API backend and Shopify liquid snippet structure.## Architecture OverviewThe production architecture is designed to cleanly separate the client interface from business and pricing logic:Storefront Snippet (/shopify-snippet): Injects a user-facing zip code lookup directly into the Shopify product details template.Backend API (/backend): An Express-based server application that evaluates custom pricing rules securely against backend tables, keeping custom margins or logic hidden safely away from client-side tampering.## Instant Frontend Preview (index.html)For rapid prototyping, user experience evaluation, or quick demos, use the self-contained index.html file located in the root directory.Unlike a production environment, index.html completely simulates the backend API calls entirely client-side. It features an intentional artificial network delay ($450\text{ ms}$) so that the frontend loading states, validation parameters, and live user interactions feel exactly like a live server deployment without needing any local development dependencies.### Mock Evaluation RulesThe simulated backend in index.html utilizes a target dataset to demonstrate matching states:Evaluated ZIP CodeScenario ProfileSimulated Price Outcome75028Regional Rate Drop (Matched)$1,499.0010001Logistics/High-Cost Area (Matched)$1,699.0090210Logistics/High-Cost Area (Matched)$1,799.00Any other valid 5-digitStandard Delivery Rate (Fallback)$1,599.00## Quick Start Guide### Method 1: Instant UX Demo (Zero Setup)Locate the index.html file in the root of the project.Open index.html directly in any modern web browser.Test custom lookups or use the pre-configured quick buttons (e.g., Try 75028) to check application states immediately.### Method 2: Launching the Decoupled Server EnvironmentTo execute the runtime build using actual HTTP API requests:Start the Express API Server:Bashcd backend
npm install
npm run dev
2. **Mount the Storefront Mock:**
   Configure your Shopify development theme using the elements provided inside `/shopify-snippet` pointing to your local endpoint (`http://localhost:3000`), or launch the production-mimicking `demo-product-page.html`.

---

## ## Core Implementation Features

* **Strict Input Sanitation:** Client-side filters prevent non-numeric entry and safely isolate inputs to a maximum 5-character length.
* **Asynchronous State Updates:** Disables buttons and presents dynamic processing labels smoothly while operations execute.
* **Aria Accessibility Compliance:** Implements live region attributes (`aria-live="polite"`) ensuring real-time calculation changes are seamlessly announced by assistive technologies.

---

## ## Contributing

1. Fork the repository.
2. Implement your pricing rule extensions or database connectors in `/backend/pricingRules.js`.
3. If changing frontend behavior or lookups, please mirror structural logic changes inside **`index.html`** to ensure the zero-setup preview remains functionally accurate.
4. Submit a detailed Pull Request.

---

## ## License

Distributed under the MIT License. See `LICENSE` for details.
