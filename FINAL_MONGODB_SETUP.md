# Final MongoDB Setup Guide - Connect to Your Local MongoDB

## The Issue
The web-based VSCode environment cannot directly connect to your local MongoDB due to network isolation. Here's how to solve this:

## Solution: Manual Data Transfer

### Step 1: Download the Export Files
The data has been exported to these files in your project:
- `users_export.json` (4 users)
- `bookings_export.json` (8 bookings)

You need to download these files to your local machine.

### Step 2: Import Data to Your Local MongoDB

**Option A: Using MongoDB Compass (Recommended)**
1. Open MongoDB Compass on your local machine
2. Connect to `mongodb://localhost:27017`
3. Create a new database called "CBT"
4. Create two collections: "users" and "bookings"
5. Import the JSON files:
   - Select "users" collection → "Add Data" → "Import JSON or CSV file" → Select `users_export.json`
   - Select "bookings" collection → "Add Data" → "Import JSON or CSV file" → Select `bookings_export.json`

**Option B: Using Command Line**
```bash
# Make sure MongoDB is running locally
mongod

# Import the data
mongoimport --db CBT --collection users --file users_export.json
mongoimport --db CBT --collection bookings --file bookings_export.json
```

### Step 3: Update Your Local Project

If you're running this project locally (not in web-based VSCode), update your `.env.local` file:

```env
MONGODB_URI=mongodb://localhost:27017/CBT
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
```

### Step 4: Verify the Setup

After importing, you should see in MongoDB Compass:

**Database: CBT**
- **users collection** (4 documents):
  - test@example.com
  - nileshsolidarity@gmail.com  
  - john.smith@company.com
  - alice@techcorp.com

- **bookings collection** (8 documents):
  - BK001: Flight (John Doe - American Airlines)
  - BK002: Hotel (Jane Smith - Grand Plaza Hotel)
  - BK003: Flight (Mike Johnson - Delta Airlines)
  - BK004: Hotel (Sarah Wilson - Ocean View Resort)
  - BK1752218230569: Flight (John Smith - Air India)
  - BK1752218604363: Flight (Alice Johnson - IndiGo)
  - Plus 2 additional bookings

## Alternative: Use MongoDB Atlas (Cloud)

If local setup is problematic, consider using MongoDB Atlas:

1. Go to https://cloud.mongodb.com
2. Create a free cluster
3. Get your connection string
4. Update `.env.local` with the Atlas connection string
5. Import the data using MongoDB Compass connected to Atlas

## Data Summary

The exported data includes:
- **4 Users** with authentication data (passwords are hashed)
- **8 Bookings** including both flights and hotels
- All data is properly structured for your application

## Next Steps

1. Download the export files from this environment
2. Import them to your local MongoDB
3. Run your Next.js application locally
4. Verify everything works in MongoDB Compass

Your application is fully configured and ready to work with MongoDB once the data is imported locally!
