# 💰 Money Manager - Personal Finance Management Application

A comprehensive full-stack web application for managing personal finances with income and expense tracking, categorization, filtering, and detailed analytics.

##  Project Overview

Money Manager is a hackathon project that helps users:
- Track income and expenses with detailed categorization
- Filter transactions by type, category, division, and date range
- View financial data in multiple timeframes (weekly, monthly, yearly)
- Edit and manage transactions with time-based restrictions
- Visualize spending patterns with interactive charts
- Maintain separate tracking for Personal and Office expenses

## 🏗️ Project Structure

```
money-manager/
├── backend/                    # Node.js + Express backend
│   ├── src/
│   │   ├── config/db.js       # MongoDB connection
│   │   ├── models/            # Data schemas
│   │   ├── controllers/       # Business logic
│   │   ├── routes/            # API endpoints
│   │   └── server.js          # Main server file
│   ├── .env                   # Environment variables
│   ├── package.json           # Dependencies
│   └── README.md              # Backend documentation
│
├── my-app/                    # React frontend
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── pages/             # Page components
│   │   ├── services/          # API client
│   │   ├── App.jsx            # Root component
│   │   └── main.jsx           # Entry point
│   ├── package.json           # Dependencies
│   ├── tailwind.config.js     # Tailwind CSS config
│   └── README.md              # Frontend documentation
│
├── SETUP_GUIDE.md             # Complete setup instructions
├── API_DOCUMENTATION.md       # API reference
└── README.md                  # This file
```

##  Quick Start

### Prerequisites
- Node.js v16+ and npm
- MongoDB (local or Atlas)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd money-manager
   ```

2. **Setup Backend**
   ```bash
   cd backend
   npm install
   # Create .env file with MONGO_URI and PORT
   npm start
   ```

3. **Setup Frontend** (in a new terminal)
   ```bash
   cd my-app
   npm install
   npm run dev
   ```

4. **Open in browser**
   - Frontend: `http://localhost:5173`
   - Backend: `http://localhost:5000`

## ✨ Features

### Core Features ✅
- ✅ Add Income and Expense transactions
- ✅ Categorize transactions (10+ predefined categories)
- ✅ Divide expenses (Personal/Office)
- ✅ Track date and time of transactions
- ✅ One-line description for transactions
- ✅ Edit transactions within 12 hours of creation
- ✅ Delete transactions
- ✅ View transaction history with details

### Dashboard ✅
- ✅ Summary cards (Balance, Income, Expenses)
- ✅ Weekly income/expense charts
- ✅ Monthly income/expense charts
- ✅ Yearly income/expense charts
- ✅ Category-wise summary
- ✅ Real-time updates

### Filtering ✅
- ✅ Filter by transaction type (Income/Expense)
- ✅ Filter by category
- ✅ Filter by division (Personal/Office)
- ✅ Filter by date range
- ✅ Combine multiple filters

### User Interface ✅
- ✅ Modern, responsive design with Tailwind CSS
- ✅ Dark theme for comfortable viewing
- ✅ Mobile-friendly layout
- ✅ Interactive modals and forms
- ✅ Clear visual feedback

## 📋 Transaction Categories

### Income
- Salary
- Bonus
- Investment
- Other

### Expense
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

## 🔧 Technology Stack

### Frontend
- **React 19** - UI framework
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **Axios** - HTTP client
- **Lucide React** - Icons

### Backend
- **Node.js** - Runtime
- **Express** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **CORS** - Cross-origin requests

## 📊 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/transactions` | Get all transactions |
| POST | `/api/transactions` | Create transaction |
| GET | `/api/transactions/:id` | Get transaction by ID |
| PUT | `/api/transactions/:id` | Update transaction (12hr limit) |
| DELETE | `/api/transactions/:id` | Delete transaction |
| GET | `/api/transactions/summary/category` | Category-wise summary |
| GET | `/api/transactions/stats/monthly` | Monthly statistics |

See [API_DOCUMENTATION.md](./API_DOCUMENTATION.md) for complete API reference.

## 🔐 Key Features

### 12-Hour Edit Window
- Transactions can only be edited within 12 hours of creation
- After 12 hours, transactions become read-only
- Full delete access is always available

### Dual Division Support
- **Personal**: Personal expenses and income
- **Office**: Work-related expenses and income
- Easy tracking separation for better financial management

### Advanced Filtering
- Combine multiple filters for precise data retrieval
- Filter by date range for period analysis
- Quick reset of all filters

## 📈 Charts & Analytics

### Weekly View
- Week-wise income and expense distribution
- Visual comparison with horizontal bars
- Easy trend identification

### Monthly View
- Month-wise transaction summary
- Detailed income vs expense breakdown
- Perfect for monthly budget analysis

### Yearly View
- Annual financial overview
- Year-to-date tracking
- Long-term trend analysis

## 🎨 User Interface

- **Dashboard**: Main hub with overview and controls
- **Add Transaction Modal**: Clean form for data entry
- **Transaction History**: Sortable table with actions
- **Filters**: Advanced filtering panel
- **Charts**: Visual data representation
- **Summary Cards**: Quick statistics overview

## 🔄 Workflow

1. **Add Transaction**
   - Click "Add Transaction" button
   - Choose Income or Expense tab
   - Fill in details (amount, category, description, etc.)
   - Select division and date
   - Submit

2. **View & Filter**
   - See all transactions in history
   - Apply filters as needed
   - Transactions update in real-time

3. **Edit or Delete**
   - Click expand icon to see details
   - Edit (within 12 hours) or delete
   - Confirm changes
   - Automatically updates dashboard

4. **Analyze**
   - Check charts for patterns
   - Review category summary
   - Monitor balance trends

## 🛠️ Development

### Backend Development
```bash
cd backend
npm install      # Install dependencies
npm start        # Start server
npm test         # Run tests (if configured)
```

### Frontend Development
```bash
cd my-app
npm install      # Install dependencies
npm run dev      # Start dev server
npm run build    # Build for production
npm run lint     # Check code quality
```

## 📚 Documentation

- [SETUP_GUIDE.md](./SETUP_GUIDE.md) - Detailed setup instructions
- [API_DOCUMENTATION.md](./API_DOCUMENTATION.md) - Complete API reference
- [backend/README.md](./backend/README.md) - Backend specific documentation
- [my-app/README.md](./my-app/README.md) - Frontend specific documentation

## 🚢 Deployment

### Backend Deployment
1. Push code to GitHub
2. Deploy to Heroku/Railway/Render
3. Set environment variables (MONGO_URI, PORT)
4. Obtain backend URL

### Frontend Deployment
1. Build the project: `npm run build`
2. Deploy to Vercel/Netlify
3. Update API base URL in frontend
4. Obtain frontend URL

## 🔍 Testing

### Manual Testing
1. Add multiple transactions
2. Apply various filters
3. Edit transactions (within 12 hours)
4. Delete transactions
5. Verify charts update correctly

### API Testing
- Use Postman/Insomnia for API endpoints
- Test with sample data
- Verify filtering capabilities
- Check error handling

## ⚠️ Important Notes

1. **MongoDB Connection**: Ensure MongoDB is running or Atlas is accessible
2. **CORS**: Backend has CORS enabled for frontend access
3. **Time Zone**: All times are in UTC
4. **Edit Window**: 12 hours calculated from transaction creation time
5. **Data Format**: Amounts in rupees (₹), dates in ISO format

## 📱 Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## 🐛 Troubleshooting

### Backend Issues
- **Port 5000 in use**: Change port in .env or kill process
- **MongoDB connection failed**: Check connection string and credentials
- **CORS errors**: Verify backend is running and CORS is enabled

### Frontend Issues
- **Cannot connect to backend**: Ensure backend is running on port 5000
- **Styles not loading**: Clear cache and reinstall dependencies
- **API errors**: Check network tab in browser DevTools

See [SETUP_GUIDE.md](./SETUP_GUIDE.md) for more troubleshooting.

## 📝 Sample Data

Sample test data is available in [backend/SAMPLE_DATA.js](./backend/SAMPLE_DATA.js).

To populate MongoDB with sample data:
```bash
# In MongoDB Compass or mongosh
// Copy content of SAMPLE_DATA.js and run
```

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📜 License

This project is open source and available under MIT License.

## ❓ FAQ

**Q: Can I edit transactions after 12 hours?**
A: No, transactions can only be edited within 12 hours of creation. After that, you can only delete and recreate them.

**Q: Can I change the categories?**
A: Categories are predefined. You can add custom categories by modifying the CATEGORIES object in components.

**Q: Is user authentication required?**
A: Currently, no authentication is implemented. Each instance tracks one user's data. For multi-user support, implement JWT.

**Q: Can I export transaction data?**
A: Not in the current version. This can be added as a future feature.

**Q: How is data stored?**
A: Data is stored in MongoDB with Mongoose schemas.

## 🚀 Future Enhancements

- [ ] User authentication & multi-user support
- [ ] Budget planning and alerts
- [ ] Recurring transactions
- [ ] Data export (CSV, PDF)
- [ ] Mobile app
- [ ] Voice input for transactions
- [ ] Receipt attachment
- [ ] AI-powered spending insights
- [ ] Bank integration
- [ ] Multi-currency support

## 📞 Support

For issues and questions:
1. Check [SETUP_GUIDE.md](./SETUP_GUIDE.md)
2. Review [API_DOCUMENTATION.md](./API_DOCUMENTATION.md)
3. Check browser console for errors
4. Review backend logs

## 🎓 Learning Resources

- React: https://react.dev
- Tailwind CSS: https://tailwindcss.com
- Express: https://expressjs.com
- MongoDB: https://docs.mongodb.com
- Vite: https://vitejs.dev

---

**Built with ❤️ for personal finance management**

Last Updated: December 2024
Version: 1.0.0
