
# Data Catalog for Gold Layer

## Overview
The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

---

### 1. **gold.dim_clients**
- **Purpose:** Stores clients details enriched with demographic and geographic data.
- **Columns:**

| Column Name      | Data Type     | Description                                                                                   |
|------------------|---------------|-----------------------------------------------------------------------------------------------|
| client_key       | INT           | Surrogate key uniquely identifying each client record in the dimension table.               |
| client_id        | INT           | Unique numerical identifier assigned to each client.                                        |
| first_name       | NVARCHAR(50)  | The client's first name, as recorded in the system.                                         |
| last_name        | NVARCHAR(50)  | The client's last name or family name.                                                     |
| State            | NVARCHAR(20)  | The state of residence for the client (e.g., 'FLorida').                               |
| marital_status   | NVARCHAR(20)  | The marital status of the client (e.g., 'Married', 'Single').                              |
| create_date      | DATE          | The date and time when the client record was created in the system|

---

### 2. **gold.dim_policies**
- **Purpose:** Provides information about the insurance policies and their attributes.
- **Columns:**

| Column Name         | Data Type     | Description                                                                                   |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|
| policy_key          | INT           | Surrogate key uniquely identifying each policy record in the product dimension table.         |
| policy_id           | INT           | A unique identifier assigned to the policy for internal tracking and referencing.            |
| policy_number       | NVARCHAR(20)  | A structured alphanumeric code representing the policy, often used for identifies a unique value. |
| policy_type         | NVARCHAR(20)  | A unique identifier for the policies categories.    |
| start_date          | DATE          | The date when the insurance policy start.
| expiration_date     | DATE          | The date when the policy expires.


---

### 3. **gold.fact_sales**
- **Purpose:** Stores transactional sales data for analytical purposes.
- **Columns:**

| Column Name     | Data Type     | Description                                                                                   |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|
| order_number    | NVARCHAR(50)  | A unique alphanumeric identifier for each sales order (e.g., 'SO54496').                      |
| policy_key      | INT           | Surrogate key linking the order to the insurance policy dimension table.                               |
| client_key      | INT           | Surrogate key linking the order to the client dimension table.                              |
| order_date      | DATE          | The date when the order was placed.                                                           |
| shipping_date   | DATE          | The date when the order was shipped to the customer.                                          |
| due_date        | DATE          | The date when the order payment was due.                                                      |
| sales_amount    | INT           | The total monetary value of the sale for the line item, in whole currency units (e.g., 25).   |
| quantity        | INT           | The number of units of the product ordered for the line item (e.g., 1).                       |
| price           | INT           | The price per unit of the product for the line item, in whole currency units (e.g., 25).      |
