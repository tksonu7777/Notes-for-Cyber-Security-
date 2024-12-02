 
### **Understanding Common Vulnerabilities in Web Applications: SQL Injection and Cross-Site Scripting (XSS)**  

 

 
 
 
### **Requirements:**  
1. A vulnerable web app (e.g., DVWA, Juice Shop).  
2. Local server setup (XAMPP, WAMP) or online sandbox (e.g., PortSwigger Web Academy).  

---

  

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

 
