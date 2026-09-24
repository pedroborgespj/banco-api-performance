# Bank API Performance Tests with K6

Repository with automated performance tests developed with the [Grafana K6](https://k6.io/) tool and written in JavaScript, targeting the banking system API.

🔗 Repository: [github.com/pedroborgespj/banco-api-performance](https://github.com/pedroborgespj/banco-api-performance)

---

## 📌 Introduction

This project aims to simulate different loads and usage scenarios for the bank's API, evaluating its performance and identifying potential bottlenecks. The tests are written focusing on modularity, organization by context, and data model reuse.

---

## ⚙️ Technologies Used

- [K6](https://k6.io/) – Open-source load and performance testing tool.
- JavaScript (ES6)
- [GJSON](https://github.com/tidwall/gjson) – For data extraction in JSON responses.
- Environment variables for dynamic configuration (e.g., `BASE_URL`).

---

## 📁 Repository Structure

```text
banco-api-performance/
├── fixtures/           # Input data for tests (e.g., users, payloads)
├── helpers/            # Reusable utility functions for API interaction
├── tests/              # Test cases organized by API module
├── utils/              # Reusable utility functions
├── config/             # Environment variable configuration files
└── README.md           # This document
```

---

## 🗂️ Purpose of Each File Group

- **`fixtures/`**: Input data for tests (e.g., users, payloads).
- **`helpers/`**: Reusable utility functions for API interaction.
- **`tests/`**: Test cases organized by API module.
- **`utils/`**: Reusable utility functions.
- **`config/`**: Environment variable configuration files.

---

## 💻 Installation and Execution

### 1. Clone the Repository

```bash
git clone [https://github.com/pedroborgespj/banco-api-performance.git](https://github.com/pedroborgespj/banco-api-performance.git)
cd banco-api-performance
```

### 2. Configure Environment Variables

Edit the `config.local.json` file and define the base URL of the API to be tested:

```json
{
    "baseUrl": "http://localhost:3000"
}
```

> 💡 These variables will be used dynamically in the tests to build the requests.

### 3. Run a Test

```bash
k6 run tests/login.test.js
```

Make sure to pass the `BASE_URL` environment variable if you are not using a `config.local.json` or an autoloading approach:

```bash
k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
```

### 4. Real-time Monitoring + Report Export

You can enable the K6 dashboard mode and export the report at the end of the test:

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run tests/login.test.js \
-e BASE_URL=http://localhost:3000
```

After execution, the report will be saved as `html-report.html`.