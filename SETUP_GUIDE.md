# Money Manager - Complete Setup & Running Guide

## Project Overview

Money Manager is a full-stack web application for managing personal finances, built with:
- **Frontend**: React 19 + Vite + Tailwind CSS
- **Backend**: Node.js + Express + MongoDB
- **Database**: MongoDB Atlas (Cloud) or Local MongoDB

## Quick Start

### Prerequisites
- Node.js v16+ installed
- MongoDB (local or Atlas account)
- npm or yarn package manager
- Git for version control

### Step 1: Clone or Extract the Project

If you have the project files, navigate to the project root directory.

### Step 2: Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create .env file with MongoDB connection
# Edit .env with your MongoDB URI
PORT=5000
MONGO_URI=mongodb://localhost:27017/money-manager
NODE_ENV=development

# Test the server
npm start
```

The backend should start on `http://localhost:5000`

### Step 3: Frontend Setup

```bash
# Navigate to frontend directory (in a new terminal)
cd my-app

# Install dependencies
npm install

# Start the development server
npm run dev
```

The frontend should start on `http://localhost:5173`

## Full Installation Instructions

### Backend Installation

1. **Navigate to backend folder**
   ```bash
   cd backend
   ```

2. **Install Node dependencies**
   ```bash
   npm install
   ```

3. **Create .env file**
   ```bash
   # Create a file named .env in the backend directory
   ```

4. **Configure MongoDB**
   - For local MongoDB:
     ```
     MONGO_URI=mongodb://localhost:27017/money-manager
     ```
   - For MongoDB Atlas (Cloud):
     ```
     MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/money-manager
     ```

5. **Start the backend server**
   ```bash
   npm start
   ```
   
   You should see:
   ```
   Server running on port 5000
   MongoDB Connected Successfully
   ```

### Frontend Installation

1. **Navigate to frontend folder** (in a new terminal/tab)
   ```bash
   cd my-app
   ```

2. **Install Node dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```
   
   You should see:
   ```
   VITE v... ready in ... ms
   ➜  Local:   http://localhost:5173/
   ```

4. **Open in browser**
   - Navigate to `http://localhost:5173/`
   - You should see the Money Manager dashboard

## Environment Setup

### MongoDB Setup

#### Option 1: Local MongoDB (Windows)

1. Download MongoDB Community Server
2. Install with default settings
3. MongoDB will run as a service automatically
4. Use connection string: `mongodb://localhost:27017/money-manager`

#### Option 2: MongoDB Atlas (Cloud - Recommended)

1. Go to https://www.mongodb.com/cloud/atlas
2. Sign up for free account
3. Create a cluster
4. Get connection string
5. Replace username:password with your credentials
6. Use in .env: `MONGO_URI=mongodb+srv://...`

### Node.js Setup

1. Download from https://nodejs.org/
2. Install LTS version (v18 or v20)
3. Verify installation:
   ```bash
   node --version
   npm --version
   ```

## Project Structure

```
guvi/
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   └── db.js
│   │   ├── controllers/
│   │   │   └── transactionController.js
│   │   ├── models/
│   │   │   ├── Transaction.js
│   │   │   └── Account.js
│   │   ├── routes/
│   │   │   └── transactions.js
│   │   └── server.js
│   ├── .env
│   ├── package.json
│   └── README.md
│
└── my-app/
    ├── src/
    │   ├── components/
    │   │   ├── AddTransactionModal.jsx
    │   │   ├── Charts.jsx
    │   │   ├── Dashboard.jsx
    │   │   ├── Filters.jsx
    │   │   ├── Summary.jsx
    │   │   └── TransactionHistory.jsx
    │   ├── pages/
    │   │   └── Home.jsx
    │   ├── services/
    │   │   └── api.js
    │   ├── App.jsx
    │   ├── index.css
    │   └── main.jsx
    ├── package.json
    ├── tailwind.config.js
    ├── postcss.config.js
    └── README.md
```

## Available Commands

### Backend Commands
```bash
npm start          # Start the server
npm test          # Run tests (if configured)
```

### Frontend Commands
```bash
npm run dev       # Start development server
npm run build     # Build for production
npm run preview   # Preview production build
npm run lint      # Check code quality
```

## Testing the Application

### 1. Add a Transaction
- Click "Add Transaction" button
- Select Income or Expense tab
- Fill in the form:
  - Amount
  - Category
  - Description
  - Division (Personal/Office)
  - Date
- Click "Add Transaction"

### 2. View Transactions
- Navigate to "Transaction History"
- See all your transactions listed
- Click eye icon to expand transaction details

### 3. Filter Transactions
- Use the filters section:
  - Select Type (Income/Expense)
  - Choose Category
  - Pick Division
  - Set date range
- Filters apply automatically

### 4. Edit Transaction
- Click edit icon on a transaction (within 12 hours)
- Modify the details
- Click "Save"

### 5. Delete Transaction
- Click delete (trash) icon
- Confirm deletion
- Transaction will be removed

### 6. View Charts
- Select timeframe (Weekly/Monthly/Yearly)
- View income and expenses visualization

## Common Issues & Fixes

### Issue: "Cannot connect to MongoDB"
**Solution**:
1. Check if MongoDB is running
2. Verify connection string in .env
3. For Atlas, check IP whitelist
4. Ensure credentials are correct

### Issue: "Port 5000 already in use"
**Solution**:
1. Change PORT in .env to a different port
2. Or kill the process using port 5000:
   ```bash
   # Windows
   netstat -ano | findstr :5000
   taskkill /PID <PID> /F
   
   # Linux/Mac
   lsof -i :5000
   kill -9 <PID>
   ```

### Issue: "Frontend can't connect to backend"
**Solution**:
1. Ensure backend is running on port 5000
2. Check API base URL in `src/services/api.js`
3. CORS must be enabled in backend (already is)

### Issue: "Module not found errors"
**Solution**:
1. Delete `node_modules` folder
2. Delete `package-lock.json`
3. Run `npm install` again

### Issue: "Styles not showing (no Tailwind CSS)"
**Solution**:
1. Ensure Tailwind CSS is installed:
   ```bash
   npm install -D tailwindcss postcss autoprefixer
   ```
2. Restart dev server
3. Clear browser cache

## Development Workflow

### Adding a New Feature

1. **Backend**:
   - Add model if needed in `src/models/`
   - Add route in `src/routes/transactions.js`
   - Add controller method in `src/controllers/transactionController.js`
   - Test with API client (Postman/Insomnia)

2. **Frontend**:
   - Create new component in `src/components/`
   - Import and use in Dashboard or other components
   - Update state and pass props
   - Style with Tailwind CSS

### Testing Workflow

1. Backend: Test API endpoints with Postman
2. Frontend: Test UI components in browser
3. E2E: Test complete workflow (add → view → filter → edit → delete)

## Performance Tips

### Frontend Optimization
- Use React.memo for expensive components
- Implement lazy loading for routes
- Minimize bundle size with tree-shaking
- Use production build for deployment

### Backend Optimization
- Add database indexes for common queries
- Implement caching strategies
- Use pagination for large datasets
- Add request rate limiting

## Deployment

### Deploy Backend (Heroku/Railway/Render)
```bash
# Ensure .env has production MongoDB URI
# Push to Git
# Connect to platform
# Auto-deploys on push
```

### Deploy Frontend (Vercel/Netlify)
```bash
npm run build
# Upload dist/ folder to Vercel/Netlify
# Or connect Git repo for auto-deployment
```

## Additional Resources

### Documentation
- React: https://react.dev
- Vite: https://vitejs.dev
- Tailwind CSS: https://tailwindcss.com
- Express: https://expressjs.com
- MongoDB: https://docs.mongodb.com
- Axios: https://axios-http.com

### Tools
- Postman: https://www.postman.com (API testing)
- MongoDB Atlas: https://www.mongodb.com/cloud/atlas
- VS Code: https://code.visualstudio.com (Editor)

## Support & Troubleshooting

For detailed information, refer to:
- [Backend README](./backend/README.md)
- [Frontend README](./my-app/README.md)

## Next Steps

1. ✅ Start both servers
2. ✅ Create sample transactions
3. ✅ Test filtering and editing
4. ✅ Customize categories/divisions as needed
5. ✅ Deploy to production
6. ✅ Share with team

Happy Money Managing! 💰
