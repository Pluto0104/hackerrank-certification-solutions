### Youngest Employees

There are two data tables with employee information: EMPLOYEE and EMPLOYEE_UIN. Query the tables to generate a list of all employees who are less than 25 years old first in order of NAME, then of ID, both ascending. The result should include the UIN followed by the NAME.
Note: While the secondary sort is by ID, the result includes UIN but not ID.

#### EMPLOYEE table

#### EMPLOYEE_UIN table

#### Sample Data Tables

- Sample Input

  - EMPLOYEE

  - EMPLOYEE_UIN

- Sample Output

```
63868-453 Dave
63550-194 Mary
57520-0440 Sherrie
```

#### Explanation

- Sherrie is 23 years old and has UIN 57520-0440. This record is printed.
- Paul is 30 years old and has UIN 49638-001. This record is not printed.
- A similar analysis is done on the remaining records.

None of the three names of people less than 25 years old is repeated, so print them in alphabetical order. There is no additional sorting by ID in this case.

### Solutions

```sql
SELECT EU.UIN, E.NAME
FROM EMPLOYEE E
JOIN EMPLOYEE_UIN EU ON E.ID = EU.ID
WHERE E.AGE < 25
ORDER BY E.NAME ASC, E.ID ASC;
```
