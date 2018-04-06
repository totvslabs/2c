# Queue table structure

Table: CAROL_3C_QUEUE

## Fields
1. pk_auto
    - bigint
    - Table's primay key
1. table_name
    - varchar(250)
1. id_type
    - varchar(250)
1. id_columns
    - varchar(250)
1. id
    - varchar(650)
1. status
    - smallint
1. op_type
    - smallint

## Data format
1. pk_auto
    - Auto-increment sequencial number.
1. table_name
    - table name in database schema. `schema.table` on Oracle, SQLServer and PostgreSQL databases and `table` on MySQL databases.
1. id_type
    - Type of the following id for record indentification. Should be `pk`.
1. id_columns
    - Names of the columns forming the primary key. Should be in YAML array format.
1. id
    - Primary key values separated by character [New Line](https://unicode-table.com/pt/000A/) (`char(10)`)
1. status
    - Internal status code of a record batch. Should be `0`.
       - **0** ready to send
       - **1** sending
1. op_type
    - Operation type code
        - **0** Insert or update
        - **1** Delete
        - **9** Initial load

## Examples
Inserting a new record on Order table with two fields in the primary key:
- SQL Server
    ```sql
    insert into carol_3c_queue (table_name, id_type, id_columns, id, status, op_type)
    values ('order', 'pk', '[order_id, order_batch]', '123' + char(10) + 'A', 0, 0)
    ```
- Oracle
    ```sql
    insert into carol_3c_queue (table_name, id_type, id_columns, id, status, op_type)
    values ('order', 'pk', '[order_id, order_batch]', '123'||chr(10)||'A', 0, 0)
    ```
- PostgreSQL
    ```sql
    insert into carol_3c_queue (table_name, id_type, id_columns, id, status, op_type)
    values ('order', 'pk', '[order_id, order_batch]', '123'||chr(10)||'A', 0, 0)
    ```
- MySQL
    ```sql
    insert into carol_3c_queue (table_name, id_type, id_columns, id, status, op_type)
    values ('order', 'pk', '[order_id, order_batch]', concat('123', char(10), 'A'), 0, 0)
    ```
*Note: If the above operation is deletion, just change the op_type value from 0 to 1.*