```java
import java.math.BigInteger;
import java.security.KeyPair;
import java.security.KeyPairGenerator;
import java.security.PrivateKey;
import java.security.PublicKey;
import javax.crypto.Cipher;

public class RSAExample {
    public static void main(String[] args) throws Exception {
        // Generate RSA key pair
        KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
        keyGen.initialize(2048);
        KeyPair pair = keyGen.generateKeyPair();
        PublicKey publicKey = pair.getPublic();
        PrivateKey privateKey = pair.getPrivate();

        // Encrypt the message
        String message = "Hello, RSA!";
        Cipher encryptCipher = Cipher.getInstance("RSA");
        encryptCipher.init(Cipher.ENCRYPT_MODE, publicKey);
        byte[] encryptedMessage = encryptCipher.doFinal(message.getBytes());
        System.out.println("Encrypted Message: " + new BigInteger(1, encryptedMessage).toString(16));

        // Decrypt the message
        Cipher decryptCipher = Cipher.getInstance("RSA");
        decryptCipher.init(Cipher.DECRYPT_MODE, privateKey);
        byte[] decryptedMessage = decryptCipher.doFinal(encryptedMessage);
        System.out.println("Decrypted Message: " + new String(decryptedMessage));
    }
}

```



# output
```
Encrypted Message: 4b8e8b7a5d3f2e1c...
Decrypted Message: Hello, RSA!

```












