*Allows you to use a SQL-like syntax to query and manipulate DynamoDB tables*

- $ Allows users to use SQL to use a universal language to work with PartiQL
- ^ Does not allow all SQL statements

# versus SQL command

| **SQL Command**         | **Supported in PartiQL** | **Notes**                                                                                                 |
| ----------------------- | ------------------------ | --------------------------------------------------------------------------------------------------------- |
| **SELECT**          | Yes                  | PartiQL supports `SELECT` for querying data from DynamoDB, including filters and projections.         |
| **INSERT**              | Yes                      | Insert functionality is supported via `INSERT INTO`, similar to traditional SQL.                          |
| **UPDATE**              | Yes                      | `UPDATE` is supported, allowing you to modify existing items in DynamoDB.                                 |
| **DELETE**              | Yes                      | You can delete items using `DELETE FROM`, similar to SQL.                                                 |
| **JOIN**                | No                       | PartiQL does not support SQL-style joins; DynamoDB is a NoSQL database, so joins aren't feasible.         |
| **GROUP BY**            | No                       | PartiQL doesn’t support `GROUP BY` for aggregation. You need to handle aggregation differently.           |
| **ORDER BY**            | No                       | PartiQL does not support sorting results with `ORDER BY`. Sorting needs to be handled in the application. |
| **HAVING**              | No                       | PartiQL does not support the `HAVING` clause for filtering aggregated data.                               |
| **LIMIT**               | Yes                      | You can limit the number of results returned in a query with `LIMIT`.                                     |
| **DISTINCT**            | No                       | PartiQL does not support `DISTINCT`, so you cannot retrieve distinct values directly.                     |
| **WHERE**               | Yes                      | PartiQL supports the `WHERE` clause for filtering data, similar to SQL.                                   |
| **COUNT**               | Yes                      | You can use `SELECT COUNT` to return the count of matching items.                                         |
| **AGGREGATE FUNCTIONS** | No                       | PartiQL does not support complex aggregate functions like `SUM` or `AVG`.                                 |