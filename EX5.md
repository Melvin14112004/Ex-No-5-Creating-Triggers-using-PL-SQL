# Ex. No: 5 Creating Triggers using PL/SQL

## DATE:1.9.23

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:

### Create employee table
```
CREATE TABLE employee (empid NUMBER,empname VARCHAR2(10),dept VARCHAR2(10),salary NUMBER);
```


### Create salary_log table
```
CREATE TABLE salary_log (log_id NUMBER GENERATED ALWAYS AS IDENTITY,empid NUMBER,empname VARCHAR2(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
```

### PLSQL Trigger code
```
CREATE OR REPLACE TRIGGER log_update_salary
BEFORE UPDATE ON employee2
FOR EACH ROW
DECLARE
    v_old_salary NUMBER;
BEGIN
    IF :OLD.salary <> :NEW.salary THEN
        v_old_salary := :OLD.salary;
        INSERT INTO salary_log (empid, empname, old_salary, new_salary, update_date)
        VALUES (:OLD.empid, :OLD.empname, v_old_salary, :NEW.salary, SYSDATE);
    END IF;
END;
/


UPDATE employee2
SET salary = 55000
WHERE empid = 1;
```
### Output:
![Screenshot 2023-10-08 150857](https://github.com/Melvin14112004/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/129204995/7d951459-7284-4dc4-88e4-5ef95d9cb207)

## AIM:

Therefore,Creating Triggers using PL/SQL Executed Successfully

