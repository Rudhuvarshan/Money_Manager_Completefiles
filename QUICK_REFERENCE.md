# Money Manager - Quick Reference Guide

## 🚀 Quick Start (5 Minutes)

### Terminal 1 - Backend
```bash
cd backend
npm install
npm start
# Should show: Server running on port 5000
#            MongoDB Connected Successfully
```

### Terminal 2 - Frontend
```bash
cd my-app
npm install
npm run dev
# Should show: Local: http://localhost:5173
```

Open browser to `http://localhost:5173` ✅

---

## 📋 Project Structure at a Glance

```
money-manager/
├── backend/          → Node.js + Express + MongoDB
├── my-app/          → React + Vite + Tailwind
├── README.md        → Project overview
├── SETUP_GUIDE.md   → Detailed setup
└── API_DOCUMENTATION.md → API reference
```

---

## 🔑 Key Files

### Backend
| File | Purpose |
|------|---------|
| `src/server.js` | Main server entry point |
| `src/models/Transaction.js` | Transaction schema |
| `src/routes/transactions.js` | API endpoints |
| `src/controllers/transactionController.js` | Business logic |

### Frontend
| File | Purpose |
|------|---------|
| `src/App.jsx` | Root component |
| `src/components/Dashboard.jsx` | Main dashboard |
| `src/services/api.js` | API client |
| `src/index.css` | Tailwind initialization |

---

## 💻 Commands

### Backend
```bash
npm start           # Run server
npm test           # Run tests
```

### Frontend
```bash
npm run dev         # Dev server
npm run build       # Production build
npm run preview     # Preview build
npm run lint       # Check code quality
```

---

## 🌐 API Endpoints

```
GET  /api/transactions                    # List all
POST /api/transactions                    # Create
GET  /api/transactions/:id               # Get one
PUT  /api/transactions/:id               # Update (12hr limit)
DELETE /api/transactions/:id             # Delete
GET  /api/transactions/summary/category  # Category summary
GET  /api/transactions/stats/monthly     # Monthly stats
```

---

## 📊 Features Checklist

### Dashboard
- [ ] Balance summary card
- [ ] Income/Expense cards
- [ ] Weekly charts
- [ ] Monthly charts
- [ ] Yearly charts

### Transactions
- [ ] Add Income
- [ ] Add Expense
- [ ] Edit (within 12 hours)
- [ ] Delete
- [ ] View history
- [ ] Expand details

### Filtering
- [ ] By type
- [ ] By category
- [ ] By division
- [ ] By date range
- [ ] Reset filters

---

## 🎯 Categories

**Income**: Salary, Bonus, Investment, Other

**Expense**: Fuel, Food, Movie, Loan, Medical, Entertainment, Shopping, Utilities, Transport, Other

**Divisions**: Personal, Office

---

## 🔧 Troubleshooting

### Backend won't start
```bash
# Check if port 5000 is in use
# Change PORT in .env or kill the process

# Check MongoDB connection
# Edit MONGO_URI in .env
```

### Frontend won't load
```bash
# Check if backend is running
# Clear npm cache: npm cache clean --force
# Reinstall: rm -rf node_modules && npm install
```

### No styles showing
```bash
# Rebuild Tailwind: npm run dev
# Clear browser cache (Ctrl+Shift+Delete)
```

---

## 📦 Dependencies

### Backend
- express, mongoose, cors, dotenv

### Frontend
- react, react-dom, axios, tailwindcss, lucide-react

---

## ⏱️ 12-Hour Edit Window

- ✅ Edit within 12 hours of creation
- ❌ Edit blocked after 12 hours
- ✅ Delete always available

---

## 🎨 UI Colors

| Component | Color |
|-----------|-------|
| Balance | Blue |
| Income | Green |
| Expense | Red |
| Background | Dark Slate |
| Text | White |

---

## 📝 Sample Transaction

```json
{
  "type": "Expense",
  "amount": 500,
  "category": "Food",
  "description": "Lunch at restaurant",
  "division": "Personal",
  "date": "2024-01-15"
}
```

---

## 🚀 Deploy

### Backend (Heroku)
1. `git push heroku main`
2. Set env vars on Heroku dashboard
3. Done!

### Frontend (Vercel)
1. `npm run build`
2. Push to GitHub
3. Connect to Vercel
4. Auto-deploys!

---

## 🔗 Important Links

- React Docs: https://react.dev
- Tailwind: https://tailwindcss.com
- Vite: https://vitejs.dev
- Express: https://expressjs.com
- MongoDB: https://docs.mongodb.com
- Axios: https://axios-http.com

---

## ✨ Pro Tips

1. **Quick Filter Reset**: Click "Reset" in filters section
2. **Expand Transaction**: Click eye icon to see details
3. **Check Edit Status**: Status shown when expanded
4. **Mobile Friendly**: Works on phone too!
5. **Multiple Filters**: Combine for precise results

---

## 📈 File Sizes (Approx)

```
Backend:
- server.js          ~2KB
- models/            ~3KB
- controllers/       ~5KB
- routes/            ~1KB

Frontend:
- Dashboard.jsx      ~4KB
- TransactionHistory ~6KB
- Charts.jsx         ~3KB
- Others             ~8KB
```

---

## 🎓 Learning Path

1. Start with Dashboard.jsx
2. Understand data flow (api → state → UI)
3. Check components folder
4. Study controllers for business logic
5. Review routes for endpoints

---

## 🐛 Debug Mode

### Browser DevTools
- Network tab: Check API calls
- Console: Check JavaScript errors
- Elements: Check CSS classes

### Backend Logs
- Check terminal for MongoDB errors
- Verify CORS headers
- Check request/response logs

---

## 📋 Checklist Before Deployment

- [ ] Backend .env configured
- [ ] MongoDB connection tested
- [ ] Frontend API URL correct
- [ ] Build successful: `npm run build`
- [ ] No console errors
- [ ] All features tested
- [ ] Mobile responsive checked

---

## 🎉 You're All Set!

Now you have a fully functional Money Manager application!

**Next**: Share it with friends, collect feedback, and deploy!

---

For detailed information, see:
- [SETUP_GUIDE.md](./SETUP_GUIDE.md)
- [API_DOCUMENTATION.md](./API_DOCUMENTATION.md)
- [README.md](./README.md)

Happy coding! 💻✨
