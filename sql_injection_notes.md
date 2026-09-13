# SQL Injection on DVWA — Notes

## 1. Introduction

SQL Injection is a web application vulnerability that occurs when an application includes untrusted user input directly in an SQL query.

An attacker may manipulate the input so that the database executes unintended SQL commands.

For this task, SQL Injection was tested only on **DVWA (Damn Vulnerable Web Application) running locally** in a controlled Kali Linux lab environment.

---

## 2. Objective

The objectives of this task were:

* Understand the basic concept of SQL Injection.
* Configure DVWA with Low security.
* Test SQL Injection using controlled payloads.
* Observe how the application responds to manipulated input.
* Understand the security risks of SQL Injection.
* Learn how parameterized queries can prevent SQL Injection.

---

## 3. Lab Environment

| Item                | Details                 |
| ------------------- | ----------------------- |
| Operating System    | Kali Linux              |
| Application         | DVWA                    |
| Web Server          | Apache                  |
| Database            | MySQL/MariaDB           |
| Browser             | Firefox                 |
| DVWA Security Level | Low                     |
| Target              | Localhost (`127.0.0.1`) |

All testing was performed on the local DVWA installation for educational purposes.

---

## 4. SQL Injection Testing

### DVWA Configuration

Before testing:

1. Open DVWA in the browser.
2. Log in to DVWA.
3. Open **DVWA Security**.
4. Set the security level to **Low**.
5. Open **SQL Injection** from the left-side menu.

The SQL Injection module allows a user to enter a User ID and displays information retrieved from the database.

---

## 5. Payload 1

### Payload

```text
' OR '1'='1
```

### Explanation

The condition `'1'='1'` is always true.

When an application directly places the input into an SQL query without proper validation or parameterization, the injected condition can change the intended logic of the query.

### Expected Observation

On a vulnerable DVWA SQL Injection page, the application may return multiple database records instead of only the record associated with the intended User ID.

### Security Impact

If a real application were vulnerable, an attacker could potentially access information that they should not be authorized to view.

---

## 6. Payload 2

### Payload

```text
1
```

### Explanation

1

The second test used the simple input value 1. This was used as a comparison with the first SQL Injection payload.


### Expected Observation

On a vulnerable DVWA installation, the application may return multiple records.

The exact output depends on the DVWA version and database configuration.

---

## 7. What Was Exposed

During testing, the SQL Injection vulnerability can cause the application to display database records that should not necessarily be returned for a single User ID.

The information displayed by DVWA may include fields such as:

* User ID
* First name
* Surname

The exact records and output should be documented from the screenshots captured during the test.

---

## 8. Why the Vulnerability Exists

The vulnerability occurs when user input is directly included in an SQL query without proper protection.

For example, an insecure application might construct a query conceptually like:

```text
SELECT * FROM users WHERE id = '<user_input>';
```

If the application does not safely handle the input, SQL syntax can be inserted into the query.

This allows the user input to affect the logic of the SQL statement.

---

## 9. Security Risks

SQL Injection can potentially result in:

* Unauthorized access to database information
* Authentication bypass
* Modification of database records
* Deletion of data
* Disclosure of sensitive information
* In serious cases, compromise of the application or underlying system

The actual impact depends on the application's database permissions and implementation.

---

## 10. Prevention

### 1. Use Parameterized Queries

Applications should use parameterized queries or prepared statements instead of directly concatenating user input into SQL queries.

Conceptually:

```text
SELECT * FROM users WHERE id = ?
```

The user input is treated as data rather than SQL code.

### 2. Input Validation

Applications should validate user input according to the expected format.

For example, if a User ID should contain only numbers, the application should reject unexpected characters.

### 3. Least-Privilege Database Accounts

The application's database account should have only the permissions it actually requires.

This limits the damage if the application is compromised.

### 4. Secure Error Handling

Applications should avoid displaying detailed database error messages to users because error messages can reveal information about the database and application.

---

## 11. Testing Summary

| Test   | Payload       | Purpose                                         | Expected Result                   |
| ------ | ------------- | ----------------------------------------------- | --------------------------------- |
| Test 1 | `' OR '1'='1` | Test whether the query logic can be manipulated | Multiple records may be displayed |
| Test 2 | `1`  |used the simple input value 1       | Test whether the query logic can be manipulated |

---

## 12. Screenshots

The following screenshots should be included as evidence:

### Screenshot 1 — DVWA Login

**File:** `01-dvwa-login.png`

**Description:**
DVWA login page running on the local Kali Linux environment.

### Screenshot 2 — DVWA Security Level

**File:** `02-security-low.png`

**Description:**
DVWA Security page showing that the security level is set to Low.

### Screenshot 3 — First SQL Injection

**File:** `03-sql-injection-1.png`

**Description:**
DVWA SQL Injection page showing the first test payload and its result.

### Screenshot 4 — Second SQL Injection

**File:** `04-sql-injection-2.png`

**Description:**
DVWA SQL Injection page showing the second test payload and its result.
---

## 13. Conclusion

The DVWA SQL Injection lab demonstrated how improper handling of user input can allow SQL query logic to be manipulated.

The testing was performed only against a locally hosted DVWA application. The exercise demonstrated the importance of secure coding practices such as parameterized queries, input validation, least-privilege database accounts, and secure error handling.

SQL Injection is preventable when applications properly separate user-supplied data from SQL commands.

---

## 14. Ethical Considerations

This SQL Injection testing was performed only against a deliberately vulnerable DVWA application running locally.

SQL Injection payloads should never be tested against websites, applications, servers, or databases without explicit authorization.

The purpose of this exercise is cybersecurity education and understanding defensive security practices.

