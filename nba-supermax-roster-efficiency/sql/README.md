# Original MySQL relational database

`NBASalary.sql` is the author's **original MySQL export**, retained as supplied, not a database reconstructed from a CSV. It contains both schema definitions and records for:

| Table | Rows in dump | Primary key | Role |
| --- | ---: | --- | --- |
| `Teams` | 270 | `(Year, Team)` | Team-season results and financial fields |
| `Player` | 3,760 | `(Player, Year)` | Player-season box-score / demographic fields |
| `Contracts` | 3,760 | `(Player, Year)` | Player/team/season salary records |

**Relationships defined in the source SQL:**
- `Player.(Year, Team)` → `Teams.(Year, Team)`
- `Contracts.(Year, Team)` → `Teams.(Year, Team)`
- `Contracts.(Player, Year)` → `Player.(Player, Year)`

## Optional local restoration

The dump was exported from MySQL Server **9.5.0** using `mysqldump` 8.0.44. It contains `CREATE DATABASE NBA`, `CREATE TABLE`, and `INSERT INTO` statements. Import only into a disposable/local database environment: it contains `DROP TABLE IF EXISTS` statements and will replace any pre-existing `NBA` tables with the same names.

If you have a compatible MySQL server and client:

```bash
mysql -u root -p < sql/NBASalary.sql
```

The import requires a MySQL account with appropriate database/table privileges. Compatibility may depend on your MySQL server version. The raw dump should be reviewed before importing into an existing environment.

The analysis notebook does **not** need MySQL; it runs directly from the base CSV so anyone can reproduce the paper's primary regressions.
