# Full stack setup guide

## Backend
### Setup
###### https://www.digitalocean.com/community/tutorials/how-to-make-a-url-shortener-with-flask-and-sqlite 
1. Create a Backend folder
- `mkdir Backend`

1. Create a virtual environment
- `python -m venv env`

1. Activate the virtual environment
- `source env/bin/activate` # Unix
- `./env/Scripts/activate` # Windows

1. Upgrade pip
- `python -m pip install --upgrade pip`

1. Install flask
- `pip install flask`

1. Create database name: `schema.sql`
```
DROP TABLE IF EXISTS urls;

CREATE TABLE urls (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    clicks INTEGER NOT NULL DEFAULT 0
);
```

1. Initialise the database `python init_db.py` with this file
```
import sqlite3

connection = sqlite3.connect('database.db')

with open('schema.sql') as f:
    connection.executescript(f.read())

connection.commit()
connection.close()
```

1. Create a `app.py` as the main app
```
import sqlite3
from hashids import Hashids
from flask import Flask, render_template, request, flash, redirect, url_for


def get_db_connection():
    conn = sqlite3.connect('database.db')
    conn.row_factory = sqlite3.Row
    return conn

@app.route('/', methods=('GET', 'POST'))
def index():
    conn = get_db_connection()

    url_data = conn.execute('INSERT INTO urls (original_url) VALUES (?)',(url,))
        conn.commit()
        conn.close()

    return render_template('index.html')

```

### Run on initialization
```
cd Backend
python -m venv env
source env/bin/activate # Linux
./env/Scripts/activate # For Windows
python -m pip install --upgrade pip
pip install -r requirements.txt
python init_db.py
```

### To start backend
```
cd Backend
# Activate env
flask run
```

Helpful commands
```
pip install <Package Name>
pip freeze > requirements.txt
```

## Frontend
### Setup
###### https://auth0.com/blog/using-python-flask-and-angular-to-build-modern-apps-part-1/

1. Install angular
`npm install @angular/cli`

1.To create Frontend
`ng new Frontend`

1. Tell angular the location of the Backend Server, put it `Frontend/src/app/env.ts`
- `export const API_URL = 'http://localhost:5000';`

1. Maybe cors
- `pip install flask-cors`
- `from flask_cors import CORS`
- `CORS(app)`



To start Frontend
```
npm install
ng serve // Goto http://localhost:4200/
```

## Database
Initialise a new database
`python init_db.py`


## Deployment
###### https://devcenter.heroku.com/articles/getting-started-with-python?singlepage=true

1. Create heroku instance
`heroku create`

2. Update `Frontend/env.ts` to use the new link

3. `ng build`
- Move dist/Frontend `index.html` into `/templates` and the rest into `/static`
- Rename all src and href in `index.html` to `../static`

4. Commit and push the changes to heroku
`git subtree push --prefix Backend/ heroku main`

5. Use dyno
`heroku ps:scale web=1`



