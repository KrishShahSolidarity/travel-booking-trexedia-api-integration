# Import Data to Your Local MongoDB

## Quick Setup Instructions

### Option 1: Command Line Import (Fastest)

Open your terminal/command prompt on your local machine and run:

```bash
# Navigate to your project directory where the export files are located
cd /path/to/your/project

# Import users collection
mongoimport --db CBT --collection users --file users_export.json

# Import bookings collection
mongoimport --db CBT --collection bookings --file bookings_export.json
```

### Option 2: MongoDB Compass Import

1. **Open MongoDB Compass** on your local machine
2. **Connect** to `mongodb://localhost:27017`
3. **Create Database:**
   - Click "Create Database"
   - Database Name: `CBT`
   - Collection Name: `users`
4. **Import Users:**
   - Select the `users` collection
   - Click "Add Data" → "Import JSON or CSV file"
   - Select `users_export.json`
   - Click "Import"
5. **Create Bookings Collection:**
   - In the CBT database, click "Create Collection"
   - Collection Name: `bookings`
6. **Import Bookings:**
   - Select the `bookings` collection
   - Click "Add Data" → "Import JSON or CSV file"
   - Select `bookings_export.json`
   - Click "Import"

## Verify Import

After importing, you should see in MongoDB Compass:

**Database: CBT**
- **users collection**: 4 documents
  - test@example.com
  - nileshsolidarity@gmail.com
  - john.smith@company.com
  - alice@techcorp.com (with company field)

- **bookings collection**: 8 documents
  - BK001: Flight (John Doe - American Airlines)
  - BK002: Hotel (Jane Smith - Grand Plaza Hotel)
  - BK003: Flight (Mike Johnson - Delta Airlines)
  - BK004: Hotel (Sarah Wilson - Ocean View Resort)
  - BK1752218230569: Flight (John Smith - Air India)
  - BK1752218604363: Flight (Alice Johnson - IndiGo)
  - Plus 2 additional bookings

## Next Steps

1. **Import the data** using one of the methods above
2. **Verify in MongoDB Compass** that you can see the CBT database with both collections
3. **Your Next.js app should automatically connect** to your local MongoDB since the connection string is already set to `mongodb://localhost:27017/CBT`
4. **Test the application** to ensure it's working with your local database

## Troubleshooting

If you don't see the data:
- Make sure MongoDB is running locally on port 27017
- Check that the import completed without errors
- Refresh MongoDB Compass
- Verify the connection string in your `.env.local` file is `mongodb://localhost:27017/CBT`

## Files to Import

The export files are in your project directory:
- `users_export.json` (4 users)
- `bookings_export.json` (8 bookings)
