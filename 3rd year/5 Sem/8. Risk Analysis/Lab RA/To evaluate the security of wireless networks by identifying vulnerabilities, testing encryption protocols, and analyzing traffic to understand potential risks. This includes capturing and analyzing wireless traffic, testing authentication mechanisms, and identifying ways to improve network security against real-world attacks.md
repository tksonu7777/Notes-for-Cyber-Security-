# To evaluate the security of wireless networks by identifying vulnerabilities, testing encryption protocols, and analyzing traffic to understand potential risks. This includes capturing and analyzing wireless traffic, testing authentication mechanisms, and identifying ways to improve network security against real-world attacks.

## **Experiment Title:**  
**Wireless Network Security Evaluation**

---

### **Objective:**  
To evaluate wireless network security by identifying vulnerabilities, testing encryption protocols, analyzing traffic, and proposing ways to improve security against real-world attacks.

---

### **Requirements:**  
1. Wireless adapter supporting monitor mode (e.g., Alfa AWUS036ACH).  
2. Tools: Wireshark, Aircrack-ng, Kismet.  
3. Test wireless network or lab environment.  

---

### **Theory:**  

#### **Wireless Security Vulnerabilities:**  
Wireless networks are susceptible to attacks such as unauthorized access, traffic interception, and brute-forcing. Weak encryption protocols (e.g., WEP) and misconfigured authentication mechanisms increase these risks.  

#### **Steps to Secure Wireless Networks:**  
1. Use strong encryption protocols (e.g., WPA3).  
2. Monitor network traffic for anomalies.  
3. Regularly update firmware and configure firewalls.  

---

### **Experiment Steps:**  

#### **Step 1: Traffic Capture and Analysis**  
1. Enable monitor mode on the wireless adapter.  
2. Use Wireshark to capture packets on the target network.  
3. Analyze captured traffic for patterns, unencrypted data, or anomalies.  

#### **Step 2: Encryption Protocol Testing**  
1. Identify the encryption protocol used (e.g., WPA2).  
2. Test for vulnerabilities like weak passwords using Aircrack-ng.  
3. Attempt to crack WEP-encrypted networks to understand its insecurity.  

#### **Step 3: Authentication Mechanism Testing**  
1. Simulate authentication attacks (e.g., dictionary or brute force) using tools like Hydra.  
2. Analyze the effectiveness of multi-factor authentication if implemented.  

#### **Step 4: Suggest Improvements**  
1. Recommend transitioning to WPA3.  
2. Enable strong passwords and multi-factor authentication.  
3. Implement network segmentation to limit unauthorized access.  

---

### **Observations:**  
- Note any unencrypted data or weak encryption methods.  
- Record the effectiveness of authentication mechanisms.  

---

### **Conclusion:**  
This experiment demonstrates the risks wireless networks face, including weak encryption and vulnerable authentication. Strengthening encryption protocols, using secure authentication mechanisms, and regular traffic analysis are essential for enhancing network security.  

---

### **References:**  
1. Wireshark User Guide: [https://www.wireshark.org/docs/](https://www.wireshark.org/docs/)  
2. Aircrack-ng Documentation: [https://www.aircrack-ng.org/](https://www.aircrack-ng.org/)  
3. OWASP Wireless Security: [https://owasp.org/](https://owasp.org/)  
