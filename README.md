
# PostgreSQL Movie Data Analysis

This project connects to a PostgreSQL database, fetches movie-related data using a SQL query, and performs basic data analysis and visualization using `pandas` and `matplotlib`.

---

## Requirements

Install the required packages using:

```bash
pip install pandas matplotlib sqlalchemy psycopg2-binary
```

---

### 1. Database Connection
Uses **SQLAlchemy** and **psycopg2** to connect to a local PostgreSQL database:

```python
from sqlalchemy import create_engine

engine = create_engine('postgresql+psycopg2://postgres:root@localhost:5432/greencycle')
```

### 2. SQL Query
Fetches data by joining `film` and `film_actor` tables:

```sql
SELECT fa.actor_id, *  
FROM film f 
LEFT JOIN film_actor fa ON fa.film_id = f.film_id
```

### 3. Data Handling
Loads the query result into a pandas DataFrame and prints the first 100 rows and all column names (numbered):

```python
df = pd.read_sql(query, engine)
print(df.head(100))

for i, col in enumerate(df.columns, start=1):
    print(f"{i}. {col}")
```

---

##  Visualizations

### 1. Count of Movies by Rating

A vertical bar chart showing the number of movies in each rating category:

```python
df['rating'].value_counts().plot(kind='bar', color='teal')
```

### 2.  Distribution of Movie Lengths

A histogram showing how movie durations are spread:

```python
plt.hist(df['length'].dropna(), bins=10, color='orange', edgecolor='black')
```

---



##  Output Example

The script outputs:

- Head of the DataFrame
- Numbered column list
- Two matplotlib charts

---

## File Structure

```
.
├── script.py
└── README.md
```

---

##  Author

 by Merlin.R
