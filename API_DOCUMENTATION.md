# Money Manager - API Documentation

Complete API reference for Money Manager Backend

## Base URL
```
http://localhost:5000/api
```

## Authentication
Currently, the API does not require authentication. In a production environment, implement JWT authentication.

## Response Format

All responses are in JSON format.

### Success Response
```json
{
  "_id": "...",
  "type": "Income|Expense",
  "amount": 1000,
  "category": "...",
  "description": "...",
  "division": "Personal|Office",
  "date": "2024-01-01T10:00:00.000Z",
  "createdAt": "2024-01-01T10:00:00.000Z",
  "updatedAt": "2024-01-01T10:00:00.000Z"
}
```

### Error Response
```json
{
  "message": "Error description"
}
```

## Endpoints

### 1. Get All Transactions

**URL:** `GET /transactions`

**Query Parameters:**
- `type` (string): "Income" or "Expense" (optional)
- `category` (string): Filter by category (optional)
- `division` (string): "Personal" or "Office" (optional)
- `startDate` (string): ISO date format, e.g., "2024-01-01" (optional)
- `endDate` (string): ISO date format, e.g., "2024-12-31" (optional)

**Example Request:**
```bash
curl "http://localhost:5000/api/transactions?type=Income&division=Personal"
```

**Example Response:**
```json
[
  {
    "_id": "660f1d8c9a7b2c3d4e5f6a7b",
    "type": "Income",
    "amount": 50000,
    "category": "Salary",
    "description": "Monthly salary",
    "division": "Personal",
    "date": "2024-04-01T09:00:00.000Z",
    "createdAt": "2024-04-01T09:00:00.000Z",
    "updatedAt": "2024-04-01T09:00:00.000Z"
  }
]
```

---

### 2. Create Transaction

**URL:** `POST /transactions`

**Request Body:**
```json
{
  "type": "Income|Expense",
  "amount": 1000,
  "category": "Salary",
  "description": "Transaction description",
  "division": "Personal|Office",
  "date": "2024-01-01"
}
```

**Required Fields:**
- `type` (string): "Income" or "Expense"
- `amount` (number): Transaction amount
- `category` (string): Category name
- `description` (string): Description
- `division` (string, optional): "Personal" or "Office" (defaults to "Personal")
- `date` (string, optional): ISO date format (defaults to today)

**Example Request:**
```bash
curl -X POST http://localhost:5000/api/transactions \
  -H "Content-Type: application/json" \
  -d '{
    "type": "Expense",
    "amount": 500,
    "category": "Food",
    "description": "Lunch at restaurant",
    "division": "Personal",
    "date": "2024-01-15"
  }'
```

**Status Code:** 201 Created

**Example Response:**
```json
{
  "_id": "660f1d8c9a7b2c3d4e5f6a7c",
  "type": "Expense",
  "amount": 500,
  "category": "Food",
  "description": "Lunch at restaurant",
  "division": "Personal",
  "date": "2024-01-15T00:00:00.000Z",
  "createdAt": "2024-01-15T10:30:00.000Z",
  "updatedAt": "2024-01-15T10:30:00.000Z"
}
```

---

### 3. Get Transaction by ID

**URL:** `GET /transactions/:id`

**URL Parameters:**
- `id` (string): Transaction ID

**Example Request:**
```bash
curl http://localhost:5000/api/transactions/660f1d8c9a7b2c3d4e5f6a7c
```

**Example Response:**
```json
{
  "_id": "660f1d8c9a7b2c3d4e5f6a7c",
  "type": "Expense",
  "amount": 500,
  "category": "Food",
  "description": "Lunch at restaurant",
  "division": "Personal",
  "date": "2024-01-15T00:00:00.000Z",
  "createdAt": "2024-01-15T10:30:00.000Z",
  "updatedAt": "2024-01-15T10:30:00.000Z"
}
```

**Status Code:** 200 OK or 404 Not Found

---

### 4. Update Transaction

**URL:** `PUT /transactions/:id`

**URL Parameters:**
- `id` (string): Transaction ID

**Request Body:**
```json
{
  "amount": 600,
  "category": "Food",
  "description": "Updated description",
  "division": "Personal",
  "date": "2024-01-15"
}
```

**Note:** Transaction can only be updated within 12 hours of creation.

**Example Request:**
```bash
curl -X PUT http://localhost:5000/api/transactions/660f1d8c9a7b2c3d4e5f6a7c \
  -H "Content-Type: application/json" \
  -d '{
    "amount": 600,
    "category": "Food",
    "description": "Updated lunch expense"
  }'
```

**Status Code:**
- 200 OK (Success)
- 403 Forbidden (12 hours passed)
- 404 Not Found (Transaction not found)

**Example Response (Success):**
```json
{
  "_id": "660f1d8c9a7b2c3d4e5f6a7c",
  "type": "Expense",
  "amount": 600,
  "category": "Food",
  "description": "Updated lunch expense",
  "division": "Personal",
  "date": "2024-01-15T00:00:00.000Z",
  "createdAt": "2024-01-15T10:30:00.000Z",
  "updatedAt": "2024-01-15T11:00:00.000Z"
}
```

**Example Response (Edit window expired):**
```json
{
  "message": "Cannot edit transaction after 12 hours"
}
```

---

### 5. Delete Transaction

**URL:** `DELETE /transactions/:id`

**URL Parameters:**
- `id` (string): Transaction ID

**Example Request:**
```bash
curl -X DELETE http://localhost:5000/api/transactions/660f1d8c9a7b2c3d4e5f6a7c
```

**Status Code:**
- 200 OK (Success)
- 404 Not Found (Transaction not found)

**Example Response:**
```json
{
  "message": "Transaction deleted successfully"
}
```

---

### 6. Get Category Summary

**URL:** `GET /transactions/summary/category`

Returns total amount for each category split by Income and Expenses.

**Example Request:**
```bash
curl http://localhost:5000/api/transactions/summary/category
```

**Example Response:**
```json
{
  "income": [
    {
      "_id": "Salary",
      "total": 50000
    },
    {
      "_id": "Bonus",
      "total": 5000
    }
  ],
  "expenses": [
    {
      "_id": "Food",
      "total": 2500
    },
    {
      "_id": "Fuel",
      "total": 5000
    }
  ]
}
```

---

### 7. Get Monthly Statistics

**URL:** `GET /transactions/stats/monthly`

Returns monthly income and expense totals.

**Example Request:**
```bash
curl http://localhost:5000/api/transactions/stats/monthly
```

**Example Response:**
```json
[
  {
    "_id": {
      "year": 2024,
      "month": 1,
      "type": "Income"
    },
    "total": 55000
  },
  {
    "_id": {
      "year": 2024,
      "month": 1,
      "type": "Expense"
    },
    "total": 15000
  }
]
```

---

## Categories

### Income Categories
- Salary
- Bonus
- Investment
- Other

### Expense Categories
- Fuel
- Food
- Movie
- Loan
- Medical
- Entertainment
- Shopping
- Utilities
- Transport
- Other

---

## Error Codes

| Code | Message | Description |
|------|---------|-------------|
| 400 | Bad Request | Invalid request data |
| 403 | Forbidden | Cannot edit after 12 hours |
| 404 | Not Found | Resource not found |
| 500 | Internal Server Error | Server error |

---

## Validation Rules

### Amount
- Must be a positive number
- Can have up to 2 decimal places

### Category
- Must be from predefined list
- Case-sensitive

### Description
- Must be a non-empty string
- Maximum 500 characters

### Date
- Must be a valid ISO date string
- Cannot be in the future

### Division
- Must be either "Personal" or "Office"

---

## Rate Limiting

Currently, there is no rate limiting. For production, implement:
- Rate limiting per IP
- Rate limiting per user (after authentication)
- Max requests per minute: 100

---

## Pagination

Future enhancement. Currently, all results are returned. To implement:
```
GET /transactions?page=1&limit=20
```

---

## Examples Using Different Tools

### Using cURL
```bash
# Get all transactions
curl http://localhost:5000/api/transactions

# Create transaction
curl -X POST http://localhost:5000/api/transactions \
  -H "Content-Type: application/json" \
  -d '{"type":"Income","amount":1000,"category":"Salary","description":"Test","division":"Personal"}'
```

### Using Postman
1. Set request type to GET/POST/PUT/DELETE
2. Enter URL: `http://localhost:5000/api/transactions`
3. For POST/PUT, add JSON body in "raw" tab
4. Click "Send"

### Using JavaScript (Axios)
```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: 'http://localhost:5000/api'
});

// Get all transactions
api.get('/transactions').then(res => console.log(res.data));

// Create transaction
api.post('/transactions', {
  type: 'Income',
  amount: 1000,
  category: 'Salary',
  description: 'Monthly salary',
  division: 'Personal'
}).then(res => console.log(res.data));
```

---

## Support

For API issues, check:
1. Backend is running on port 5000
2. MongoDB is connected
3. Request body is valid JSON
4. Headers include `Content-Type: application/json`
