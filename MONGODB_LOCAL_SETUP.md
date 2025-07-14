# MongoDB Local Setup Guide

## Current Situation
Your Next.js application is currently connected to a MongoDB instance running inside the web-based VSCode container. To see the data in your local MongoDB Compass, we need to:

1. Import the existing data to your local MongoDB
2. Update the connection string to use your local MongoDB

## Step 1: Import Data to Your Local MongoDB

I've exported the current data from the container MongoDB. You have two options:

### Option A: Import via Command Line (Recommended)
If you have MongoDB tools installed locally, run these commands on your local machine:

```bash
# Import users collection
mongoimport --db CBT --collection users --file users_export.json

# Import bookings collection  
mongoimport --db CBT --collection bookings --file bookings_export.json
```

### Option B: Import via MongoDB Compass
1. Open MongoDB Compass on your local machine
2. Connect to `mongodb://localhost:27017`
3. Create a new database called "CBT"
4. Create collections "users" and "bookings"
5. Import the JSON files using Compass's import feature

## Step 2: Update Connection String

The application is currently using this connection string:
```
MONGODB_URI=mongodb://localhost:27017/CBT
```

This should work for your local MongoDB, but we need to ensure the application connects to your local instance instead of the container instance.

## Step 3: Verify Connection

After importing the data, you should see in MongoDB Compass:
- Database: CBT
- Collections: users (4 documents), bookings (8 documents)

## Data Summary

**Users Collection (4 documents):**
- test@example.com
- nileshsolidarity@gmail.com  
- john.smith@company.com
- alice@techcorp.com

**Bookings Collection (8 documents):**
- 4 seed bookings (flights and hotels)
- 2 new flight bookings created during testing
- 2 additional bookings

## Next Steps

1. Import the data to your local MongoDB
2. Restart your Next.js application
3. Verify the connection works
4. Check MongoDB Compass to see all data

The exported files are available in your project directory:
- `users_export.json`
- `bookings_export.json`
