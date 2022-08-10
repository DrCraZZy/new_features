Help for [PL/SQL](https://oracleplsql.ru/)


- Search for table name in the pool of sys-tables
    ```sql
    -- all tables
    select * from sys.all_tables

    -- user tables
    select * from sys.user_tables

    -- search for code in own PAs
    SELECT * FROM ALL_source WHERE UPPER(text) LIKE '%WRITE_DEBUG%'
    ```
- Grant Privileges on tables
    ```sql
    GRANT [privileges] ON [object] TO [user];
    ```
    - privileges:
        - SELECT - possibility to select
        - INSERT - possibility to insert
        - UPDATE - possibility to update
        - DELETE - possibility to delete
        - REFERENCES - possibility to crate constraint, that refer to the table
        - ALTER - possibility to do the ALTER TABLE operation, to change description of table
        - INDEX - possibility CREATE INDEX in the table
        - ALL - all privileges for the table

    - object - name of object. In the case of a table it will be a table name.

    - user - user name 

    ```sql
    -- Examples
    GRANT SELECT, INSERT, UPDATE, DELETE ON suppliers TO trizor;

    GRANT ALL ON suppliers TO trizor;

    -- public is a group of all users	
    GRANT SELECT ON suppliers TO public;
    ```

- Revoke privileges for tables
    - with this command is it possible to cancel/revoke privileges
    ```sql
    REVOKE [privileges] ON [object] TO [user];
    ```
    - privileges:
        - SELECT - possibility to select
        - INSERT - possibility to insert
        - UPDATE - possibility to update
        - DELETE - possibility to delete
        - REFERENCES - possibility to crate constraint, that refer to the table
        - ALTER - possibility to do the ALTER TABLE operation, to change description of table
        - INDEX - possibility CREATE INDEX in the table
        - ALL - all privileges for the table

    - object - name of object. In the case of a table it will be a table name.

    - user - user name

    ```sql
    -- Examples
    REVOKE DELETE ON suppliers FROM anzor;

    REVOKE ALL ON suppliers FROM anzor;

    -- public is a group of all users	
    REVOKE SELECT ON suppliers TO public;
    ```

- GRANT/REVOKE privileges on function/procedure
    ```sql
    GRANT/REVOKE EXECUTE ON object TO user
    ```
    - object - name of object. In the case of a table it will be a table name.

    - user - user name

    ```sql
    -- Examples
    -- GRANT
    GRANT EXECUTE ON Get_Value TO trizor;

    GRANT EXECUTE ON Get_Value TO public;

    -- REVOKE
    REVOKE execute ON Get_Value FROM maximus;

    REVOKE execute ON Get_Value FROM maximus;
    ```