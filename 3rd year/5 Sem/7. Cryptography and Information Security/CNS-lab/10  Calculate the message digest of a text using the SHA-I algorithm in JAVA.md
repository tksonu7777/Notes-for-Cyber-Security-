



# 10  Calculate the message digest of a text using the SHA-I algorithm in JAVA.

```java
import java.math.BigInteger;
import java.security.MessageDigest;

public class SHA1Example {
    public static void main(String[] args) throws Exception {
        String message = "Hello, SHA-1!";
        MessageDigest md = MessageDigest.getInstance("SHA-1");
        byte[] messageDigest = md.digest(message.getBytes());

        // Convert byte array into signum representation
        BigInteger no = new BigInteger(1, messageDigest);

        // Convert message digest into hex value
        String hashtext = no.toString(16);

        // Add preceding 0s to make it 32 bit
        while (hashtext.length() < 32) {
            hashtext = "0" + hashtext;
        }

        System.out.println("SHA-1 Hash: " + hashtext);
    }
}


```
# Output
```
SHA-1 Hash: 2ef7bde608ce5404e97d5f042f95f89f1c232871

```
