import sqlite3
import pandas as pd

conn = sqlite3.connect("test.db")
cursor=conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT,
    age INTEGER
)
""")
conn.commit()

cursor.execute("INSERT INTO users (name, age) VALUES (?, ?)", ("John", 25))
conn.commit()

cursor.execute("Select * from users")
rows=cursor.fetchall()

for row in rows:
    print(row)
    
    conn.close()

import sqlite3
import pandas as pd

conn = sqlite3.connect("test.db")

# Read data
df = pd.read_sql_query("SELECT * FROM users", conn)

# Analyze
print(df.describe())

conn.close()


#mongodb

from pymongo import MongoClient
import pandas as pd

client = MongoClient("mongodb://localhost:27017/")
db = client["mydatabase"]
collection = db["users"]

# Insert
collection.insert_one({"name": "John", "age": 25})
print("Data inserted successfully!")

# Read and print raw data
for doc in collection.find():
    print(doc)

# Convert to DataFrame
data = list(collection.find())
df = pd.DataFrame(data)

# Remove _id column
df.drop(columns=["_id"], inplace=True)

print("\nDataFrame:")
print(df)
