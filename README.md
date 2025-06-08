#  Resilient Email Sending Service (Node.js + Express)

A fault-tolerant, scalable, and testable email sending service built with JavaScript. Designed for reliability using:

* Retry logic
* Provider fallback
* Circuit breakers
* Rate limiting
* Queue processing
* Idempotency
* Full unit test coverage



## ✨ Features

-  Retry mechanism with exponential backoff
-  Fallback between multiple email providers
-  Idempotency to prevent duplicate sends
-  Rate limiting middleware
-  Status tracking of email attempts
-  Circuit breaker for both providers
-  In-memory job queue with:

* FIFO processing
* Pause/Resume capability
* Failed job retry
* Queue size limit
   Logging via Winston
   Unit tests with Jest & Supertest



##  Folder Structure

```
src/
├── app.js
├── controllers/
│   └── email.controller.js
├── services/
│   └── email.service.js
├── providers/
│   ├── providerA.js
│   └── providerB.js
├── utils/
│   ├── circuitBreaker.js
│   ├── emailQueue.js
│   ├── idempotency.js
│   ├── logger.js
│   ├── rateLimiter.js
│   └── statusTracker.js
tests/
├── email.test.js
└── queue.test.js
```



##  Getting Started

### 1️⃣ Clone & Install

```bash
git clone https://github.com/rohitramteke1/pearlthoughts-email-service-challenge
cd pearlthoughts-email-service-challenge
npm install
```

### 2️⃣ Run the Server

```bash
npm start
```

### 3️⃣ Run Tests

```bash
npm test
```



##  API Endpoint

### POST `/api/email`

**Body:**

```json
{
  "to": "recipient@example.com",
  "subject": "Hello",
  "body": "This is a test email",
  "idempotencyKey": "unique-key-123"
}
```

**Responses:**

* `200 OK` — Email job added to queue
* `400 Bad Request` — Missing fields
* `500 Internal Server Error` — Server failure



## 🥪 Testing

* `email.test.js`: Validates API behaviors
* `queue.test.js`: Validates queue retry, pause, and failure handling



## 🛠 Design Principles

* Clean code using SOLID principles
* Zero external email APIs — mock-based providers
* Minimal dependencies
* Fully ESM-compatible using Jest



##  Author

Built with  as part of the PearlThoughts Backend Developer Trainee challenge.



##  License

MIT



##  Live API URL

Use the following live URL to send emails (via POST):

```
https://zkmvf4vzs8.execute-api.ap-south-1.amazonaws.com/Prod/api/email
```