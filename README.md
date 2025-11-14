# Pipeline_API

A Python-based pipeline that extracts real-time weather data from the OpenWeather API, transforms it, and loads it into a PostgreSQL database using SQL for analysis.

# Setup Instructions

## 1. Create your .env file

Paste the following into a new .env file (same folder as main.py):

```bash
API_KEY=your_api_key_here
```
## 2. Install Dependencies

Run this in your WSL Ubuntu terminal:
```bash
pip install requests pandas python-dotenv psycopg2-binary matplotlib seaborn
```

## 3.PostgreSQL Database

Paste the SQL query:
```bash
SELECT "DateTime", "Temperature"
FROM weather_table
ORDER BY "Temperature" DESC;
```
## 4. Run the Pipeline
Step 1: Run the extraction + transformation
python main.py
This creates the dataframe df.

Step 2: Load into PostgreSQL

Update connection string in load.py:
```bash
conn = "dbname=yourdb user=youruser password=yourpassword host=localhost port=5432"
```

Run this in your WSL Ubuntu terminal:
```bash
python load.py
```
## 5. Verify in PostgreSQL

Run this inside your terminal:
```bash
psql -U youruser -d yourdb -c "SELECT * FROM weather_table LIMIT 10;"
