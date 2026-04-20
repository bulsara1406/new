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
