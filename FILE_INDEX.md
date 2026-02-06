# Money Manager - Complete File Index

## 📁 Project File Structure with Descriptions

### Root Directory (`/guvi`)
```
guvi/
├── README.md                    ← Main project overview
├── SETUP_GUIDE.md              ← Complete installation guide
├── API_DOCUMENTATION.md        ← REST API reference
├── QUICK_REFERENCE.md          ← Quick start guide
├── IMPLEMENTATION_SUMMARY.md   ← What was built
├── FILE_INDEX.md               ← This file
├── backend/                    ← Backend service
└── my-app/                     ← Frontend application
```

---

## 🔙 Backend Directory (`/backend`)

### Configuration & Setup
```
backend/
├── .env                        ← Environment variables (PORT, MONGO_URI)
├── .gitignore                  ← Git ignore rules
├── package.json                ← Dependencies & scripts
│   └── Scripts: npm start      ← Start the server
└── README.md                   ← Backend documentation
```

### Source Code (`/backend/src`)
```
src/
├── server.js              ← Main server entry point
│   ├── Express app setup
│   ├── CORS configuration
│   ├── Database connection
│   └── Router mounting
│
├── config/
│   └── db.js             ← MongoDB connection
│       ├── Uses Mongoose
│       ├── Error handling
│       └── Connection logging
│
├── models/               ← Data schemas
│   ├── Transaction.js    ← Transaction data structure
│   │   ├── type (Income/Expense)
│   │   ├── amount (number)
│   │   ├── category (string)
│   │   ├── description (string)
│   │   ├── division (Personal/Office)
│   │   ├── date (timestamp)
│   │   ├── createdAt (auto)
│   │   └── updatedAt (auto)
│   │
│   └── Account.js        ← Account data structure
│       ├── name (string)
│       ├── balance (number)
│       ├── accountType (enum)
│       └── timestamps
│
├── routes/               ← API endpoints
│   └── transactions.js   ← Transaction routes
│       ├── GET /          ← List all transactions
│       ├── POST /         ← Create transaction
│       ├── GET /:id       ← Get specific transaction
│       ├── PUT /:id       ← Update transaction
│       ├── DELETE /:id    ← Delete transaction
│       ├── GET /summary/category  ← Category summary
│       └── GET /stats/monthly     ← Monthly statistics
│
├── controllers/          ← Business logic
│   └── transactionController.js
│       ├── getTransactions()      ← Fetch with filters
│       ├── addTransaction()       ← Create new
│       ├── getTransactionById()   ← Get by ID
│       ├── updateTransaction()    ← Edit (12hr check)
│       ├── deleteTransaction()    ← Remove
│       ├── getSummary()          ← Category breakdown
│       └── getMonthlyStats()     ← Monthly data
│
└── EXTRA/ (Optional)
    ├── SAMPLE_DATA.js     ← Sample test data
```

---

## 🖥️ Frontend Directory (`/my-app`)

### Configuration & Setup
```
my-app/
├── index.html               ← HTML entry point
├── .gitignore               ← Git ignore rules
├── package.json             ← Dependencies & scripts
│   ├── "npm run dev"        ← Start dev server
│   ├── "npm run build"      ← Build for production
│   ├── "npm run preview"    ← Preview build
│   └── "npm run lint"       ← Check code quality
├── vite.config.js           ← Vite configuration
├── tailwind.config.js       ← Tailwind CSS config
├── postcss.config.js        ← PostCSS plugins
└── README.md                ← Frontend documentation
```

### Source Code (`/my-app/src`)
```
src/
├── main.jsx                 ← Application entry point
│   ├── React initialization
│   └── Root mounting
│
├── App.jsx                  ← Root component
│   └── Renders Home page
│
├── index.css                ← Global styles
│   ├── @tailwind directives
│   ├── Base reset CSS
│   └── Font configuration
│
├── App.css                  ← (Empty/Optional)
│
├── components/              ← Reusable components
│   ├── Dashboard.jsx       ← Main dashboard container
│   │   ├── Fetches transactions
│   │   ├── Manages state
│   │   ├── Handles filters
│   │   ├── Opens modal
│   │   └── Displays child components
│   │
│   ├── Summary.jsx          ← Summary cards (3x1 grid)
│   │   ├── Balance card (blue)
│   │   ├── Income card (green)
│   │   └── Expense card (red)
│   │
│   ├── Charts.jsx           ← Data visualization
│   │   ├── Weekly view
│   │   ├── Monthly view
│   │   ├── Yearly view
│   │   ├── Bar charts
│   │   └── Legend
│   │
│   ├── Filters.jsx          ← Filtering controls
│   │   ├── Type dropdown
│   │   ├── Category select
│   │   ├── Division select
│   │   ├── Date range pickers
│   │   ├── Active filter pills
│   │   └── Reset button
│   │
│   ├── TransactionHistory.jsx  ← Transaction list
│   │   ├── Data table
│   │   ├── Expand row feature
│   │   ├── Inline editing
│   │   ├── Edit/Delete buttons
│   │   ├── 12-hour check logic
│   │   └── Timestamp display
│   │
│   └── AddTransactionModal.jsx  ← Add transaction form
│       ├── Modal wrapper
│       ├── Income/Expense tabs
│       ├── Form fields
│       ├── Category dropdown
│       ├── Division select
│       ├── Date picker
│       ├── Validation
│       └── Submit handler
│
├── pages/                   ← Page components
│   └── Home.jsx            ← Home page
│       └── Renders Dashboard
│
├── services/                ← API utilities
│   └── api.js              ← Axios instance
│       └── baseURL configuration
│
└── assets/                  ← Static files
    └── (Images, fonts, etc)
```

---

## 📊 Data Models

### Transaction Object
```javascript
{
  _id: ObjectId,
  type: "Income" | "Expense",
  amount: number,
  category: string,
  description: string,
  division: "Personal" | "Office",
  date: Date,
  createdAt: Date,
  updatedAt: Date
}
```

### Account Object
```javascript
{
  _id: ObjectId,
  name: string,
  balance: number,
  accountType: "Checking" | "Savings" | "Credit Card",
  createdAt: Date,
  updatedAt: Date
}
```

---

## 📚 Documentation Files

### In Root Directory
| File | Purpose | Audience |
|------|---------|----------|
| README.md | Project overview | Everyone |
| SETUP_GUIDE.md | Step-by-step setup | Developers |
| API_DOCUMENTATION.md | API reference | Backend devs |
| QUICK_REFERENCE.md | Quick commands | Everyone |
| IMPLEMENTATION_SUMMARY.md | What was built | Project managers |
| FILE_INDEX.md | This guide | Developers |

### In Subdirectories
| File | Location | Purpose |
|------|----------|---------|
| README.md | backend/ | Backend specifics |
| README.md | my-app/ | Frontend specifics |
| SAMPLE_DATA.js | backend/ | Test data |

---

## 🔄 Data Flow

```
User Input
    ↓
[AddTransactionModal.jsx] → Form submission
    ↓
[api.js] → POST /transactions
    ↓
[server.js] → Route handler
    ↓
[transactionController.js] → Create in DB
    ↓
[Transaction.js] → Schema validation
    ↓
[MongoDB] → Store data
    ↓
[Dashboard.jsx] → Refetch transactions
    ↓
[Summary.jsx] + [Charts.jsx] → Display updates
```

---

## 🎯 Component Relationships

```
App.jsx
  └── Home.jsx
      └── Dashboard.jsx
          ├── Summary.jsx (props: transactions)
          ├── Charts.jsx (props: transactions, timeframe)
          ├── Filters.jsx (props: filters, onFilterChange)
          ├── TransactionHistory.jsx (props: transactions)
          └── AddTransactionModal.jsx (props: onClose, onAdd)
```

---

## 🔑 Important Directories

| Directory | Contains | Purpose |
|-----------|----------|---------|
| backend/src/models/ | Database schemas | Define data structure |
| backend/src/routes/ | API endpoints | Define HTTP routes |
| backend/src/controllers/ | Business logic | Handle requests |
| backend/src/config/ | Configuration | Database connection |
| my-app/src/components/ | UI components | User interface |
| my-app/src/pages/ | Page components | Page structure |
| my-app/src/services/ | API client | Backend communication |

---

## 📦 Key Dependencies

### Backend
```json
{
  "express": "Web framework",
  "mongoose": "MongoDB ODM",
  "cors": "Cross-origin requests",
  "dotenv": "Environment variables"
}
```

### Frontend
```json
{
  "react": "UI library",
  "react-dom": "React DOM rendering",
  "axios": "HTTP client",
  "tailwindcss": "CSS framework",
  "lucide-react": "Icon library"
}
```

---

## 🚀 Build Artifacts

### Backend
- Entry: `backend/src/server.js`
- Output: Runs on http://localhost:5000
- No build step required

### Frontend
- Entry: `my-app/src/main.jsx`
- BuildOutput: `my-app/dist/`
- Dev Server: http://localhost:5173
- Prod URL: (After deployment)

---

## 🔗 Key Routes

### API Routes (Backend)
```
GET    /api/transactions
POST   /api/transactions
GET    /api/transactions/:id
PUT    /api/transactions/:id
DELETE /api/transactions/:id
GET    /api/transactions/summary/category
GET    /api/transactions/stats/monthly
GET    /api/health
```

### Page Routes (Frontend)
```
/ → Home → Dashboard
```

(No routing library used; single page app)

---

## 📝 File Size Reference

```
Small files (<2KB):
  - routes/transactions.js
  - config/db.js
  - services/api.js

Medium files (2-5KB):
  - models/Transaction.js
  - server.js
  - Summary.jsx
  - Charts.jsx

Large files (5-10KB):
  - controllers/transactionController.js
  - TransactionHistory.jsx
  - Dashboard.jsx

Extra large (>10KB):
  - package.json files with node_modules
```

---

## 🎓 How to Navigate Code

### To understand data flow:
1. Start in Dashboard.jsx
2. Follow the useState and useEffect
3. Check api.js for API calls
4. Look at server.js for endpoint handling
5. Check transactionController.js for logic

### To understand UI:
1. Start in App.jsx
2. Go to Home.jsx
3. Check Dashboard.jsx
4. Explore individual components
5. Check Tailwind classes in JSX

### To understand database:
1. Check Transaction.js schema
2. Look at transactionController.js methods
3. Check routes/transactions.js mappings
4. Review MongoDB documentation

---

## ✅ File Checklist

### Essential Files (Must have)
- [ ] backend/src/server.js
- [ ] backend/src/models/Transaction.js
- [ ] backend/src/routes/transactions.js
- [ ] backend/src/controllers/transactionController.js
- [ ] backend/package.json
- [ ] my-app/src/App.jsx
- [ ] my-app/src/components/Dashboard.jsx
- [ ] my-app/package.json

### Configuration Files (Should have)
- [ ] backend/.env
- [ ] my-app/tailwind.config.js
- [ ] my-app/postcss.config.js

### Documentation Files (Nice to have)
- [ ] README.md (all levels)
- [ ] API_DOCUMENTATION.md
- [ ] SETUP_GUIDE.md

---

## 🔍 Finding Things

| Looking for... | Check... |
|----------------|----------|
| Add transaction logic | controllers/transactionController.js |
| Filter logic | components/Filters.jsx |
| Edit restriction | components/TransactionHistory.jsx |
| Styling | src/index.css, tailwind.config.js |
| API calls | services/api.js |
| Data fetching | components/Dashboard.jsx |
| Component props | component JSX files |
| Database schema | models/*.js |
| Routes | routes/*.js |

---

## 📋 Summary

```
Total Backend Files: 6 main source files + config
Total Frontend Files: 7 component files + 1 config
Total Documentation: 6 markdown files
Total Configuration: 5 config files
Total Package Files: 2 package.json files
```

**Total Lines of Code: ~1500 (plus node_modules)**

---

**Happy coding!** 🚀

For detailed guides, see:
- SETUP_GUIDE.md - Installation
- API_DOCUMENTATION.md - API details
- README.md - Project overview
