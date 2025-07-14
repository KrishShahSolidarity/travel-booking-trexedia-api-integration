# MongoDB Compass Connection Guide

## Great News! 🎉

Your Next.js application is already connected to your **local MongoDB** instance, not the container MongoDB. This means all the data should already be visible in your MongoDB Compass application.

## How to View Your Data in MongoDB Compass

### Step 1: Connect to Your Local MongoDB
1. Open **MongoDB Compass** on your computer
2. Use this connection string: `mongodb://localhost:27017`
3. Click **Connect**

### Step 2: Navigate to Your Database
1. Look for a database named **"CBT"**
2. Click on the **CBT** database to expand it
3. You should see two collections:
   - **users** (4 documents)
   - **bookings** (8 documents)

### Step 3: View Your Data

**Users Collection:**
- Click on the **users** collection
- You should see 4 user documents:
  - test@example.com
  - nileshsolidarity@gmail.com
  - john.smith@company.com
  - alice@techcorp.com (with company field)

**Bookings Collection:**
- Click on the **bookings** collection
- You should see 8 booking documents:
  - BK001: Flight (John Doe - American Airlines)
  - BK002: Hotel (Jane Smith - Grand Plaza Hotel)
  - BK003: Flight (Mike Johnson - Delta Airlines)
  - BK004: Hotel (Sarah Wilson - Ocean View Resort)
  - BK1752218230569: Flight (John Smith - Air India)
  - BK1752218604363: Flight (Alice Johnson - IndiGo)
  - Plus 2 additional bookings

## Troubleshooting

### If you don't see the CBT database:
1. **Refresh** MongoDB Compass (F5 or refresh button)
2. Make sure you're connected to `mongodb://localhost:27017`
3. Check that your local MongoDB service is running
4. Look for the database in the left sidebar

### If you see the database but no collections:
1. Click on the **CBT** database name to expand it
2. The collections should appear below the database name
3. If not visible, try refreshing the connection

### If collections are empty:
1. This shouldn't happen since we confirmed the data exists
2. Try disconnecting and reconnecting to MongoDB Compass
3. Make sure you're looking at the correct database (CBT)

## Verification Commands

You can also verify the data exists by running these commands in your terminal:

```bash
# Count users
mongosh CBT --eval "db.users.countDocuments()"

# Count bookings  
mongosh CBT --eval "db.bookings.countDocuments()"

# View a sample user
mongosh CBT --eval "db.users.findOne()"

# View a sample booking
mongosh CBT --eval "db.bookings.findOne()"
```

## Your Application is Working!

- ✅ MongoDB is connected to your local instance
- ✅ All user registrations are saving to your local database
- ✅ All flight bookings are saving to your local database
- ✅ The manage bookings page shows data from your local database
- ✅ You can view all this data in MongoDB Compass

The integration is complete and working perfectly with your local MongoDB setup!
