# student-records

import sqlite3
conn = sqlite3.connect("school.db")  
cursor = conn.cursor()
cursor.execute("""
CREATE TABLE IF NOT EXISTS Students (
    StudentID INTEGER PRIMARY KEY AUTOINCREMENT,
    Name TEXT NOT NULL,
    Age INTEGER,
    Grade TEXT
)
""")
conn.commit()
students = [
    ("Alice", 20, "A"),
    ("Bob", 21, "B"),
    ("Charlie", 19, "A")
]
cursor.executemany("INSERT INTO Students (Name, Age, Grade) VALUES (?, ?, ?)", students)
conn.commit()
print("Records inserted successfully.\n")
print("All Students:")
cursor.execute("SELECT * FROM Students")
for row in cursor.fetchall():
    print(row)
conn.close()

Output:
Records inserted successfully.

All Students:
(1, 'Alice', 20, 'A')
(2, 'Bob', 21, 'B')
(3, 'Charlie', 19, 'A')
