# Danira WooCommerce AI Product Advisor + RAG

An AI-powered pre-sales assistant for WooCommerce stores, built with **n8n**, **Gemini**, **Supabase**, and live **WooCommerce product data**.

The assistant helps customers find the right products based on their needs, budget, preferences, and store policies without relying on hard-coded product information.

---

## What It Does

The workflow can:

- Understand a customer's shopping request in natural language
- Search the live WooCommerce product catalog
- Recommend up to 3 relevant products
- Return real product data such as:
  - Product name
  - Price
  - Stock status
  - Product URL
- Explain why each product matches the customer's needs
- Answer store-related questions using a RAG knowledge base
- Handle topics such as:
  - Shipping
  - Returns
  - Warranty
  - Payment methods
  - Size guides
  - Frequently asked questions
- Reply in the same language used by the customer
- Ask one useful follow-up question when more information is required
- Avoid inventing products, prices, availability, or store policies

---

## Architecture

This project contains two separate workflow paths.

### 1. Customer Product Advisor

This is the customer-facing workflow.

```text
Customer
   ↓
AI Agent
   ↓
┌─────────────────────┬─────────────────────┐
│ WooCommerce Catalog │ Supabase Knowledge  │
│ Live Product Data   │ Base / RAG          │
└─────────────────────┴─────────────────────┘
   ↓
Product Recommendation
```

The AI Agent uses live WooCommerce data for product recommendations and the Supabase knowledge base for store policies and FAQ-related questions.

### 2. Knowledge Base Ingestion

This is the admin-side workflow.

```text
Store FAQ / Policies / Guides
            ↓
       Text Processing
            ↓
        Embeddings
            ↓
  Supabase Vector Store
```

This workflow is used to add approved store information such as shipping policies, return rules, warranty details, payment information, and product guides.

Keeping these two workflows separate makes the system easier to maintain, test, and extend.

---

## Screenshots

### Customer Product Advisor

Add your first workflow screenshot here:

```text
/docs/product-advisor-workflow.png
```

### Knowledge Base Pipeline

Add your second workflow screenshot here:

```text
/docs/knowledge-base-workflow.png
```

---

## Tech Stack

- n8n
- WooCommerce REST API
- Google Gemini
- Supabase
- Vector Search / RAG
- AI Agent
- Embeddings

---

## Example Customer Requests

```text
I need a gift under $100. What do you recommend?
```

```text
Which of these products is better for everyday use?
```

```text
Is this product currently in stock?
```

```text
What is your return policy?
```

```text
How long does shipping usually take?
```

---

## Setup

### 1. Import the Workflow

Import the provided JSON file into n8n.

### 2. Configure WooCommerce

Create a WooCommerce credential in n8n.

Replace:

```text
YOUR-STORE.com
```

with your WooCommerce store domain.

Configure the WooCommerce credentials for the product-related nodes.

### 3. Configure Gemini

Create a Google Gemini credential in n8n and connect it to:

- Gemini Chat Model
- Knowledge Embeddings
- Knowledge Insert Embeddings

Use the same embedding model for both storing and retrieving knowledge.

### 4. Configure Supabase

Create a Supabase Vector Store compatible with n8n.

Configure the Supabase credentials for:

- Store Knowledge Base
- Insert Knowledge to Supabase

The default knowledge table can be named:

```text
documents
```

### 5. Add Store Knowledge

Use the admin knowledge workflow to add approved store information such as:

- Shipping policy
- Return policy
- Warranty information
- Payment methods
- Size guides
- Frequently asked questions

---

## Suggested Test Scenarios

After configuring the credentials, test the assistant with different types of requests.

### Product Discovery

```text
I need a lightweight product for daily use under $150.
```

### Product Comparison

```text
What is the difference between these two products?
```

### Availability

```text
Is this product currently available?
```

### Store Policy

```text
Can I return a product after delivery?
```

---

## Project Scope

This version is intentionally designed as a **pre-sales product advisor**.

It does **not**:

- Create orders
- Cancel orders
- Process refunds
- Modify prices
- Modify inventory
- Perform administrative WooCommerce actions

Keeping the scope focused makes the workflow safer, easier to demonstrate, and more suitable as a reusable business automation asset.

---

## Security

This repository should not contain:

- API keys
- Access tokens
- Private webhook URLs
- Real customer data
- Production credentials
- Private store information

Use n8n credentials or environment variables for all secrets.

---

## Use Cases

This workflow can be adapted for:

- Fashion stores
- Electronics stores
- Bookstores
- Beauty and cosmetics stores
- Home and furniture stores
- Specialty e-commerce stores
- B2B product catalogs

---

## Possible Improvements

Future versions could include:

- Product comparison tables
- Customer preference memory
- Lead capture
- WhatsApp or Telegram integration
- Human handoff
- Cart creation
- Conversation analytics
- Recommendation tracking
- Multilingual store support

---

## About Danira

**Danira** builds practical AI agents, automations, workflows, and operational systems for WordPress, WooCommerce, and online businesses.

The goal is to reduce repetitive operational work and turn useful automations into reusable business assets.

---

## License

Add the license that matches how you want others to use this repository.
