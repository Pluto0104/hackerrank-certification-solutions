### Youngest Employees

There are two data tables with employee information: EMPLOYEE and EMPLOYEE_UIN. Query the tables to generate a list of all employees who are less than 25 years old first in order of NAME, then of ID, both ascending. The result should include the UIN followed by the NAME.
Note: While the secondary sort is by ID, the result includes UIN but not ID.

#### EMPLOYEE table

![Screenshot 2023-11-08 082210](https://github.com/Pluto0104/hackerrank-role-certification-solutions-javascript/assets/136573674/6026d60f-5416-48e3-8fd7-f168bbbba84b)

#### EMPLOYEE_UIN table

![Screenshot 2023-11-08 082214](https://github.com/Pluto0104/hackerrank-role-certification-solutions-javascript/assets/136573674/8108d0e5-9101-4e4e-b9ed-8c3dd621d025)

#### Sample Data Tables

- Sample Input

  - EMPLOYEE
    
    ![Screenshot 2023-11-08 082222](https://github.com/Pluto0104/hackerrank-role-certification-solutions-javascript/assets/136573674/061d966c-cc0f-4cc9-9daf-fbfbcf52cfca)

  - EMPLOYEE_UIN
    
    ![Screenshot 2023-11-08 082228](https://github.com/Pluto0104/hackerrank-role-certification-solutions-javascript/assets/136573674/0d09595e-bd0f-405b-aed3-adf3e5e63f18)

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
