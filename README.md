# 🚀 Auto_connect_mongo

A Python package for easily connecting to MongoDB databases (including MongoDB Atlas 🌎), performing CRUD operations, and bulk data inserts from CSV or Excel files! 

---

## ✨ Features

- 🧩 Simple MongoDB client and database/collection management
- 📥 Insert single or multiple records
- 📊 Bulk insert from CSV or Excel files
- ☁️ Designed for both local and cloud (Atlas) MongoDB
- 🏷️ Type-annotated and ready for static analysis

---

## 📦 Installation

Clone and install from source:

```bash
# 🐙 Clone the repo
$ git clone https://github.com/AnandVadgama/my-py-package.git
$ cd my-py-package

# 📦 Install dependencies
$ pip install -r requirements.txt
```

Or install as a package (if published):

```bash
pip install Auto_connect_mongo
```

---

## 🛠️ Usage

### 1️⃣ Connect to MongoDB

```python
from Auto_connect_mongo.mongo_crud import mongo_operation

# Use your MongoDB Atlas URI or local URI
client_url = "mongodb+srv://<username>:<password>@cluster0.mongodb.net/"
database_name = "my_database"
collection_name = "my_collection"

mongo_op = mongo_operation(client_url, database_name, collection_name)
```

### 2️⃣ Insert a single record

```python
record = {"name": "Alice", "age": 30}
mongo_op.insert_record(record, collection_name)
```

### 3️⃣ Insert multiple records

```python
records = [
    {"name": "Bob", "age": 25},
    {"name": "Charlie", "age": 35}
]
mongo_op.insert_record(records, collection_name)
```

### 4️⃣ Bulk insert from CSV or Excel

```python
# CSV (make sure your CSV is properly formatted)
mongo_op.bulk_insert("data.csv", collection_name)

# Excel
mongo_op.bulk_insert("data.xlsx", collection_name)
```

### 5️⃣ Find records

```python
query = {"age": {"$gt": 25}}
results = mongo_op.find_record(query, collection_name)
for doc in results:
    print(doc)
```

### 6️⃣ Update a record

```python
query = {"name": "Alice"}
update = {"$set": {"age": 31}}
mongo_op.update_record(query, update, collection_name)
```

### 7️⃣ Delete a record

```python
query = {"name": "Bob"}
mongo_op.delete_record(query, collection_name)
```

### 8️⃣ Delete multiple records

```python
query = {"age": {"$lt": 30}}
mongo_op.delete_many_record(query, collection_name)
```

### 9️⃣ Delete all records in a collection

```python
mongo_op.delete_all_record(collection_name)
```

---

## 🧑‍💻 Development & Testing

### 📝 Requirements
- Python 3.7+
- See `requirements.txt` and `requirements_dev.txt` for dependencies

### 🧪 Run tests

```bash
pip install -r requirements_dev.txt
tox
```

### 🎨 Lint and type check

```bash
flake8 src/
mypy src/
```

---

## 🗂️ Project Structure

```
📦 my-py-package/
├── 🗂️ src/
│   ├── 📄 __init__.py
│   └── 🗂️ Auto_connect_mongo/
│       ├── 📄 __init__.py
│       └── 📄 mongo_crud.py
├── 🧪 tests/
│   ├── 📄 __init__.py
│   ├── 🗂️ unit/
│   │   ├── 📄 __init__.py
│   │   └── 🧪 test_unit.py
│   └── 🗂️ integration/
│       ├── 📄 __init__.py
│       └── 🧪 test_int.py
├── 🧪 experiments/
│   └── 📓 experiments.ipynb
├── ⚙️ .github/
│   └── 🔄 workflows/
│       ├── 🤖 ci.yaml
│       └── 🚀 python-publish.yaml
├── 📄 LICENSE
├── 📄 README.md
├── 🛠️ init_setup.sh
├── 📝 pyproject.toml
├── 📄 requirements.txt
├── 🧪 requirements_dev.txt
├── ⚙️ setup.cfg
├── 🛠️ setup.py
├── 📝 template.py
├── 🧪 test.py
├── ⚙️ tox.ini
└── 📄 .gitignore
```

---

_Note: All methods expect the correct types for arguments (e.g., `record` as dict or list of dicts, `query` as dict, etc.). For bulk insert, ensure your CSV/Excel files are well-formatted. For more details, see the source code!_

---

## 🤝 Contributing

1. 🍴 Fork the repository
2. 🌱 Create your feature branch (`git checkout -b feature/YourFeature`)
3. 💾 Commit your changes (`git commit -am 'Add some feature'`)
4. 🚀 Push to the branch (`git push origin feature/YourFeature`)
5. 📝 Open a pull request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

- **AnandVadgama** - [GitHub](https://github.com/AnandVadgama)

---

> Made with ❤️ for MongoDB fans and Pythonistas everywhere!

# requirements_dev.txt we use for the testing
It makes it easier to install and manage dependencies for development and testing, separate from the dependencies required for production.

# difference between requirements_dev.txt and requirements.txt

requirements.txt is used to specify the dependencies required to run the production code of a Python project, while requirements_dev.txt is used to specify the dependencies required for development and testing purposes.

# tox.ini
We use if for the testing in the python package testing against different version of the python 

## how tox works tox enviornment creation
1. Install depedencies and packages 
2. Run commands
3. Its a combination of the (virtualenvwrapper and makefile)
4. It creates a .tox


# pyproject.toml
it is being used for configuration the python project it is a alternative of the setup.cfg file. its containts configuration related to the build system
such as the build tool used package name version author license and dependencies

# setup.cfg
In summary, setup.cfg is used by setuptools to configure the packaging and installation of a Python projec

# Testing python application
*types of testing*
1. Automated testing 
2. Manual testing

*Mode of testing*
1. Unit testing
2. Integration tests

*Testing frameworks*

1. pytest
2. unittest
3. robotframework
4. selenium
5. behave
6. doctest

# check with the code style formatting and syntax(coding standard)

1. pylint
2. flake8(it is best because it containt 3 library pylint pycodestyle mccabe)
3. pycodestyle