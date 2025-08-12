# SQLSpeak

## Overview
**SQLSpeak** is a Jupyter Notebook project that uses **LangChain** and a **Mistral AI** language model to:
- Convert natural language questions into SQL queries.
- Execute the queries on a **MySQL** database .
- Provide **natural language answers** based on query results.

The application is built for **interactive development and testing** in Jupyter Notebook.

---

## Features
- 🔹 Converts natural language questions into SQL queries using a large language model.
- 🔹 Executes SQL queries on a MySQL database .
- 🔹 Generates natural language responses from query results.
- 🔹 Runs entirely inside a Jupyter Notebook.

---

## Prerequisites
- **Python** 3.8+
- **Jupyter Notebook** or **JupyterLab**
- **MySQL server** with the Chinook database installed
- **Mistral AI API key** (set as an environment variable)
- Required Python packages (see [Dependencies](#dependencies) below)

---

## Installation

1. **Clone the repository** :
   ```bash
   git clone https://github.com/Druva4444/SQLspeack.git
   cd SQLspeack
   ```

2. **Install the required Python packages**:
   ```bash
   pip install langchain langchain-community mysql-connector-python jupyter
   ```

3. **Set up the MySQL database**:
   - Ensure the **Chinook** database is installed.
   - Update the database connection string in the notebook if needed:
     ```python
     db = '<your database link>'
     ```

4. **Set the Mistral AI API key**:
   - **Option 1: Environment variable**  
     ```bash
     export MISTRAL_API_KEY='your-api-key-here'
     ```
   - **Option 2: Inside the notebook**  
     ```python
     os.environ["MISTRAL_API_KEY"] = "your-api-key-here"
     ```

5. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```
   Open the `.ipynb` file in your browser.

---

## Usage

1. Open the Jupyter Notebook in your browser.
2. Run the cells sequentially to:
   - Import dependencies.
   - Set up the database connection and LangChain components.
   - Process a sample question:
     ```python
     user_question = "How many albums are there in the database?"
     result = final_chain.invoke({"question": user_question})
     print(result)
     ```
3. Modify the `user_question` variable to ask different questions:
   ```python
   user_question = "your-custom-question-here"
   result = final_chain.invoke({"question": user_question})
   print(result)
   ```
4. Execute the cells to see:
   - The generated SQL query.
   - The natural language response.

---

## Notebook Structure
1. **Imports** – Loads required libraries (`os`, `langchain`, etc.).
2. **Environment Setup** – Configures the Mistral AI API key and database connection.
3. **SQL Chain** – Generates SQL queries from natural language input.
4. **Final Chain** – Executes queries and generates natural language answers.
5. **Example** – Demonstrates workflow with `"How many albums are there in the database?"`

---

## Dependencies
- `langchain` – For building query and response chains.
- `langchain-community` – Database utilities and extra features.
- `mysql-connector-python` – MySQL database connectivity.
- `jupyter` – Notebook environment.
- **Mistral AI API** – Language model (`mistral-large-latest`).

Install all dependencies:
```bash
pip install langchain langchain-community mysql-connector-python jupyter
```

---

## Example

**Question**:  
```
How many albums are there in the database?
```

**Generated SQL Query**:  
```sql
SELECT COUNT(*) FROM Album;
```

**Sample Response**:  
```
There are 347 albums in the database.
```

---

## Notes
- Ensure the MySQL database is running and accessible.
- The `get_schema` function is assumed to be defined for retrieving the database schema—update it for your database.
- The notebook assumes **Chinook** database structure; modify prompts if using another schema.
- The Mistral AI API key must be valid with proper permissions.
- Always run cells in order to avoid dependency issues.

---

## License
This project is licensed under the **MIT License**.
