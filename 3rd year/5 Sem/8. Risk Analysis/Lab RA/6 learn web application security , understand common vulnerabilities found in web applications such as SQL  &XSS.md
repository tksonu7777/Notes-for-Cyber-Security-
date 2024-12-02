## **Experiment Title:**  
### **Understanding Common Vulnerabilities in Web Applications: SQL Injection and Cross-Site Scripting (XSS)**  

---

### **Objective:**  
To learn about web application security and understand how common vulnerabilities like SQL Injection and Cross-Site Scripting (XSS) can affect web applications.

---

### **Requirements:**  
1. A computer with a modern web browser  
2. A local development environment (e.g., XAMPP/WAMP/LAMP) or an online sandbox environment like [PortSwigger’s Web Security Academy](https://portswigger.net/web-security)  
3. A vulnerable web application for testing (e.g., [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/) or DVWA)  

---

### **Theory:**  

#### **Web Application Security:**  
Web application security focuses on protecting websites and online services from vulnerabilities that malicious actors might exploit. Some common vulnerabilities include SQL Injection and XSS.  

#### **SQL Injection:**  
SQL Injection occurs when an attacker inserts or manipulates SQL queries through input fields in a web application. This can lead to unauthorized access to a database, data theft, or modification.  

##### **Example:**  
A vulnerable login form:  
```sql
SELECT * FROM users WHERE username = 'admin' AND password = 'password';
```

An attacker could input:  
```sql
Username: admin' OR '1'='1  
Password: anything
```

Resulting in:  
```sql
SELECT * FROM users WHERE username = 'admin' OR '1'='1' AND password = 'anything';
```

#### **Cross-Site Scripting (XSS):**  
XSS attacks allow an attacker to inject malicious scripts into web pages viewed by other users. This can steal user sessions, deface websites, or redirect users.  

##### **Example:**  
A vulnerable comment box:  
```html
<input type="text" name="comment" />
```

An attacker could input:  
```html
<script>alert('XSS');</script>
```

---

### **Experiment Steps:**  

#### **Part 1: SQL Injection**  
1. Set up a vulnerable web application (e.g., DVWA).  
2. Navigate to the login page.  
3. Enter the SQL payload:  
   - Username: `admin' OR '1'='1`  
   - Password: `anything`  
4. Observe the behavior of the application.  
5. Mitigation: Modify the backend code to use prepared statements or parameterized queries.  

#### **Part 2: Cross-Site Scripting (XSS)**  
1. Open a vulnerable page (e.g., a comment section).  
2. Enter the script: `<script>alert('XSS');</script>`  
3. Submit the input and observe if the script executes.  
4. Mitigation: Use input sanitization, output encoding, and a Content Security Policy (CSP).  

---

### **Observations:**  
- Record the behavior of the application when an SQL Injection or XSS payload is introduced.  
- Note the potential impact on data security and user experience.  

---

### **Conclusion:**  
This experiment demonstrates how SQL Injection and XSS vulnerabilities can compromise web application security. It also highlights the importance of implementing secure coding practices such as input validation, parameterized queries, and proper output encoding.  

---

### **References:**  
1. OWASP Top 10 Vulnerabilities: [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)  
2. Web Security Academy: [https://portswigger.net/web-security](https://portswigger.net/web-security)  
3. SQL Injection Wiki: [https://en.wikipedia.org/wiki/SQL_injection](https://en.wikipedia.org/wiki/SQL_injection)  

--- 

This structured format can be adapted for RA (Research and Applications) assignments or laboratory manuals.






## **Experiment Title:**  
**Understanding Web Application Vulnerabilities: SQL Injection and XSS**

---

### **Objective:**  
Learn about web application security and understand common vulnerabilities like SQL Injection and Cross-Site Scripting (XSS).

---

### **Requirements:**  
1. A vulnerable web app (e.g., DVWA, Juice Shop).  
2. Local server setup (XAMPP, WAMP) or online sandbox (e.g., PortSwigger Web Academy).  

---

### **Theory:**  

#### **SQL Injection (SQLi):**  
- Exploits input fields to inject malicious SQL queries.  
- **Example:**  
  Input: `admin' OR '1'='1`  
  Results in unauthorized database access.  
- **Mitigation:** Use prepared statements or parameterized queries.  

#### **Cross-Site Scripting (XSS):**  
- Injects malicious scripts into web pages.  
- **Example:** `<script>alert('XSS');</script>` steals data or disrupts user sessions.  
- **Mitigation:** Input sanitization, output encoding, and CSP.  

---

### **Steps:**  

1. **SQL Injection Test:**  
   - Enter `admin' OR '1'='1` in a vulnerable login form and observe unauthorized access.  

2. **XSS Test:**  
   - Inject `<script>alert('XSS');</script>` into input fields and check if it executes.  

3. **Apply Fixes:**  
   - Use secure coding practices like input validation and parameterized queries.  

---

### **Conclusion:**  
SQL Injection and XSS highlight critical web security flaws. Secure coding practices are vital to protect applications from such attacks.  

---

### **References:**  
1. OWASP Top 10: [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)  
2. PortSwigger Academy: [https://portswigger.net/web-security](https://portswigger.net/web-security)  
