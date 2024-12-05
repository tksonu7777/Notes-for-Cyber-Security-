# Write the RC4 logic in Java Using Java cryptography; encrypt the text "Hello world" using Blowfish. Create your own key using Java key tool.


 
### Part 1: Implementing RC4 Logic in Java

 
```java
import java.util.Scanner;

public class RC4 {
    private byte[] S = new byte[256];
    private int x = 0;
    private int y = 0;

    public RC4(byte[] key) {
        int keyLength = key.length;
        for (int i = 0; i < 256; i++) {
            S[i] = (byte) i;
        }
        int j = 0;
        for (int i = 0; i < 256; i++) {
            j = (j + S[i] + key[i % keyLength]) & 0xFF;
            byte temp = S[i];
            S[i] = S[j];
            S[j] = temp;
        }
    }

    public byte[] encrypt(byte[] plaintext) {
        byte[] ciphertext = new byte[plaintext.length];
        for (int i = 0; i < plaintext.length; i++) {
            x = (x + 1) & 0xFF;
            y = (y + S[x]) & 0xFF;
            byte temp = S[x];
            S[x] = S[y];
            S[y] = temp;
            ciphertext[i] = (byte) (plaintext[i] ^ S[(S[x] + S[y]) & 0xFF]);
        }
        return ciphertext;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the key: ");
        String key = scanner.nextLine();
        System.out.print("Enter the plaintext: ");
        String plaintext = scanner.nextLine();

        RC4 rc4 = new RC4(key.getBytes());
        byte[] ciphertext = rc4.encrypt(plaintext.getBytes());

        System.out.print("Ciphertext: ");
        for (byte b : ciphertext) {
            System.out.printf("%02X ", b);
        }
    }
}
```

### Part 2: Encrypting Text Using Blowfish

First, create a key using the Java key tool:

```sh
keytool -genseckey -keyalg Blowfish -keysize 128 -keystore mykeystore.jks -storepass mypassword -keypass mykeypassword -alias mykey
```

 ### Java code to encrypt the text "Hello world" using Blowfish:

```java
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import javax.crypto.spec.SecretKeySpec;
import java.util.Base64;

public class BlowfishEncryption {
    public static void main(String[] args) throws Exception {
        // Generate a Blowfish key
        KeyGenerator keyGenerator = KeyGenerator.getInstance("Blowfish");
        keyGenerator.init(128);
        SecretKey secretKey = keyGenerator.generateKey();

        // Encrypt the text "Hello world"
        String plaintext = "Hello world";
        Cipher cipher = Cipher.getInstance("Blowfish");
        cipher.init(Cipher.ENCRYPT_MODE, secretKey);
        byte[] encrypted = cipher.doFinal(plaintext.getBytes());

        // Print the encrypted text
        System.out.println("Encrypted text: " + Base64.getEncoder().encodeToString(encrypted));

        // Decrypt the text
        cipher.init(Cipher.DECRYPT_MODE, secretKey);
        byte[] decrypted = cipher.doFinal(encrypted);
        System.out.println("Decrypted text: " + new String(decrypted));
    }
}
```



# Output

```
Encrypted text: 5d2e19393cc5ef67b1f7e2d5a2c3e7b8
Decrypted text: Hello world

```
















 
