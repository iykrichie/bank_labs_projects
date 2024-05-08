## Product and Channel Adoption by Bank Customers.ipynb

This Jupyter Notebook analyzes client channel and product usage patterns in a bank's database.

**Objective**

The script aims to analyze how clients use different channels (mobile, USSD, chatbot, wallet) and products (bill payments, airtime, cardless transactions, etc.)

**Code Structure**

The notebook is divided into the following sections:

1. **Libraries Used:**
    - `sqlalchemy`: Creates a connection engine for databases.
    - `pandas`: Used for data manipulation and analysis.
    - `numpy` (optional): Used for numerical computations with Pandas.

2. **Code Details:**
    - Import statements for the mentioned libraries.
    - `create_engine` function from SQLAlchemy establishes a connection to the database.
    - Pandas handles data manipulation tasks.

3. **Data Handling:**
    - This section sets up the necessary libraries but doesn't perform specific data operations.

4. **Loading Database Credentials:**
    - Imports the `json` module.
    - Loads credentials from a JSON file located at `/Workspace/Credentials/db_data.json`.
    - Extracts database connection details (host, user, password, database) from the JSON file.
    - Creates a connection engine using SQLAlchemy.

5. **Query Details:**
    - The script defines Common Table Expressions (CTEs) to categorize clients based on channel usage and product ownership.
    - The main query joins these CTEs with relevant tables to generate a report containing:
        - `client_id`: Unique client identifier.
        - `client_category`: Category of the client (based on demographics).
        - Flags indicating if the client uses a specific channel (mobile, USSD, etc.)
        - Flags indicating if the client uses a specific product (bill payments, airtime, etc.)
        - Flags indicating if the client has a specific account type (savings, current, etc.)
        - `has_credit`: Flag indicating if the client has an active loan.
        - `run_date`: Date when the script was executed.
    - The resulting dataset (`rcadop`) provides insights into client behavior regarding channels and products.

6. **Execution Time:**
    - The `%%time` magic command at the beginning measures the script's execution time.

7. **Writing Data to Redshift:**
    - The script writes the DataFrame (`df`) containing the results to a Redshift table named `dwh_client_prod_chan_adoption`.

**Additional Notes**

- The script excludes Point-of-Sale (POS) transactions from the analysis.

