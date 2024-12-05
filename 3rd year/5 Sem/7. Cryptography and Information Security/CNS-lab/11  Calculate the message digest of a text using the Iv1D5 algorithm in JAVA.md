# 11 Calculate the message digest of a text using the Iv1D5 algorithm in JAVA.

```java
import java.math.BigInteger;
import java.security.MessageDigest;

public class MD5Example {
    public static void main(String[] args) throws Exception {
        String message = "Hello, MD5!";
        MessageDigest md = MessageDigest.getInstance("MD5");
        byte[] messageDigest = md.digest(message.getBytes());

        // Convert byte array into signum representation
        BigInteger no = new BigInteger(1, messageDigest);

        // Convert message digest into hex value
        String hashtext = no.toString(16);

        // Add preceding 0s to make it 32 bit
        while (hashtext.length() < 32) {
            hashtext = "0" + hashtext;
        }

        System.out.println("MD5 Hash: " + hashtext);
    }
}


```
# Output
```
MD5 Hash: 5d41402abc4b2a76b9719d911017c592

```
